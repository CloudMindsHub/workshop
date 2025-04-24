+++
title = "Handle dataset"
date = 2025
weight = 1
chapter = false
pre = "<b>2.1. </b>"
+++


### Data Preprocessing

After downloading the dataset from **Hugging Face** as instructed, or using your own custom dataset, the next step is to **process and reformat the data** to match the input requirements for **fine-tuning** on **AWS Bedrock**.

- Import necessary libraries:

```
import os
import ast
import csv
import json
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
```

- Install the required packages:

```
pip install pandas numpy scikit-learn pyarrow pillow
```

- Load the parquet file into a DataFrame (adjust the file name accordingly):

```
df = pd.read_parquet('train-00000-of-00034.parquet', engine="pyarrow")

df['conversations'] = df['conversations'].apply(
    lambda x: json.dumps(x.tolist(), ensure_ascii=False) if isinstance(x, np.ndarray) else json.dumps(x, ensure_ascii=False)
)

df = df.head(100)
```

- Split the dataset into training (90%) and testing (10%) sets:

```
train_df, test_df = train_test_split(df, test_size=0.1)

train_df.to_csv("viet_vqa_train.csv", index=False, encoding='utf-8')
test_df.to_csv("viet_vqa_test.csv", index=False, encoding='utf-8')

df_train = pd.read_csv('viet_vqa_train.csv')
df_test = pd.read_csv('viet_vqa_test.csv')
```

After running the above code, you will have two .csv files containing split data from the .parquet file:

![Fine-tuning illustration](/images/2-dataset/data-csv.png)

### Reformat Data for AWS Bedrock Format

- Example data format for AWS Bedrock (update with appropriate paths and IDs):

```
item = {
    "schemaVersion": "bedrock-conversation-2024",
    "system": [
        {
            "text": (
                "You are an AI assistant specialized in Q&A based on Vietnamese images. "
                "You can analyze image content, recognize text (OCR), understand context, "
                "and answer questions based on extracted information. "
                "Behavior Guidelines Text Recognition: Use OCR to extract textual content from images. "
                "Context Understanding: Identify the meaning of the extracted text and image to provide accurate answers. "
                "Concise Responses: Provide clear, precise, and natural Vietnamese responses. "
                "Image Analysis Support: If a question requires more than text extraction, analyze the visual content as well. "
                "Professional & Objective: Respond factually based on the image, avoiding assumptions beyond the given data."
            )
        }
    ],
    "messages": [
        {
            "role": "user",
            "content": [
                {"text": ""},
                {
                    "image": {
                        "format": "png",
                        "source": {
                            "s3Location": {
                                "uri": "s3://test-fineture-novalite/data-fineture/image_sample_1.jpg",
                                "bucketOwner": "536*********"
                            }
                        }
                    }
                }
            ]
        },
        {
            "role": "assistant",
            "content": [
                {"text": ""}
            ]
        }
    ]
}
```

- Formatting function: the first user message includes an image, combined with conversation entries to form a dialogue:

```
def create_jsonl_item(row):
    try:
        conversations = row.get("conversations")
        json_conversation = json.loads(conversations)

        for item in json_conversation:
            if isinstance(item["content"], str):
                item["content"] = [{"text": item["content"]}]

        message_id = row.get("id")
        if isinstance(conversations, str):
            conversations = json.loads(conversations)
            
        if not isinstance(conversations, list):
            raise ValueError("Invalid JSON format in conversations column")

        if len(json_conversation) > 0 and json_conversation[0]["role"] == "user":
            image_info = {
                "image": {
                    "format": "png",
                    "source": {
                        "s3Location": {
                            "uri": f"s3://data-vqa-fine-tune-nova/train/image_{message_id}.png",
                            "bucketOwner": "536*********"
                        }
                    }
                }
            }
            content_user = json_conversation[0]["content"]
            content_user.append(image_info)
            json_conversation[0]["content"] = content_user
        print(json_conversation)
        return {
            "schemaVersion": "bedrock-conversation-2024",
            "system": [
                {
                    "text": (
                        "You are an AI assistant specialized in Q&A based on Vietnamese images. "
                        "You can analyze image content, recognize text (OCR), understand context, "
                        "and answer questions based on extracted information. "
                        "Behavior Guidelines Text Recognition: Use OCR to extract textual content from images. "
                        "Context Understanding: Identify the meaning of the extracted text and image to provide accurate answers. "
                        "Concise Responses: Provide clear, precise, and natural Vietnamese responses. "
                        "Image Analysis Support: If a question requires more than text extraction, analyze the visual content as well. "
                        "Professional & Objective: Respond factually based on the image, avoiding assumptions beyond the given data."
                    )
                }
            ],
            "messages": json_conversation
        }
    except Exception as e:
        print(f"Error processing conversations: {e}, row conversation: {conversations}")
        return None
```

- Read training data from viet_vqa_train.csv:

```
df_train = pd.read_csv('viet_vqa_train.csv')
df_train
```

- Convert image bytes to PNG files and save them in a folder (e.g., train_images) to upload to the S3 bucket:

```
output_folder = 'train_images'

if not os.path.exists(output_folder):
    os.makedirs(output_folder)

for idx, row in df_train.iterrows():
    try:
        image_bytes = eval(row['image'])
        image_data = image_bytes['bytes'] if isinstance(image_bytes, dict) else image_bytes

        img = Image.open(io.BytesIO(image_data))

        file_path = os.path.join(output_folder, f'image_{idx}.png')

        img.save(file_path, format='PNG')

        print(f"Đã lưu ảnh: {file_path}")
    except Exception as e:
        print(f"Lỗi khi xử lý ảnh ở dòng {idx}: {e}")
```

- Apply the formatting function to the entire DataFrame:


```
jsonl_data = df_train.apply(create_jsonl_item, axis=1).tolist()
```

- Save to JSONL file: **data_train_90.jsonl** for training, **data_test_10.jsonl** for testing:

```
jsonl_data = [item for item in jsonl_data if item is not None]

with open("data_train_90.jsonl", "w", encoding="utf-8") as f:
    for item in jsonl_data:
        json.dump(item, f, ensure_ascii=False)
        f.write("\n")
```

- Final output:

![Fine-tuning illustration](/images/2-dataset/data-json.png)


{{% notice note %}}
The same procedure used for training data should also be applied to the test dataset, following the instructions above.{{% /notice %}}

