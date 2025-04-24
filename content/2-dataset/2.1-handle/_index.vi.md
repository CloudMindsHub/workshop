+++
title = "Xử lý dữ liệu"
date = 2025
weight = 1
chapter = false
pre = "<b>2.1. </b>"
+++


### Tiền xử lý dữ liệu

Sau khi tải về bộ dữ liệu từ **Hugging Face** theo hướng dẫn, hoặc sử dụng bộ dữ liệu tùy chỉnh của riêng bạn, bước tiếp theo là tiến hành xử lý và định dạng lại dữ liệu sao cho phù hợp với yêu cầu đầu vào của mô hình **fine-tuning** trên **AWS Bedrock**.

- Nhập thư viện cần thiết

```
import os
import ast
import csv
import json
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
```

- Tải các thư viện cần thiết

```
pip install pandas numpy scikit-learn pyarrow pillow
```

- Đọc file **parquet** thành **Dataframe** (sửa lại **tên** file **.parquet** sao cho phù hợp với file bạn đã tải).

```
df = pd.read_parquet('train-00000-of-00034.parquet', engine="pyarrow")

df['conversations'] = df['conversations'].apply(
    lambda x: json.dumps(x.tolist(), ensure_ascii=False) if isinstance(x, np.ndarray) else json.dumps(x, ensure_ascii=False)
)

df = df.head(100)
```

- Chia dữ liệu thành 3 bộ train (90%), test (10%)

```
# Chia tập train (90%) và tập test (10%)
train_df, test_df = train_test_split(df, test_size=0.1)

train_df.to_csv("viet_vqa_train.csv", index=False, encoding='utf-8')
test_df.to_csv("viet_vqa_test.csv", index=False, encoding='utf-8')

df_train = pd.read_csv('viet_vqa_train.csv')
df_test = pd.read_csv('viet_vqa_test.csv')
```

- Kết quả khi chạy xong đoạn code trên, ta sẽ có 2 file **.csv** chứa các data được chia từ file **.parquet**.

![Fine-tuning illustration](/images/2-dataset/data-csv.png)


### Định dạng lại dữ liệu theo format AWS Bedrock

- Định dạng mẫu của **AWS Bedrock** (thay đường dẫn, cũng như ID phù hợp).

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

- Hàm định dạng dữ liệu, thông điêp đầu tiên của role user sẽ chứa thêm hình ảnh, kết hợp với các thông điệp trong mẫu dữ liệu tạo ra 1 conversation.
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
        print(f"Lỗi khi xử lý conversations: {e}, row conversation: {conversations}")
        return None
```

- Đọc dữ liệu train từ file **viet_vqa_train.csv** (sau đó tới file **viet_vqa_test.csv**).
```
df_train = pd.read_csv('viet_vqa_train.csv')
df_train
```

- Chuyển đổi hình ảnh dạng bytes thành file png và lưu trong một folder để upload lên s3 bucket.
- Tên folder hiện tại **train_images** cho file train và tên **test_images** cho file test.

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

- Apply cho cả Dataframe
```
jsonl_data = df_train.apply(create_jsonl_item, axis=1).tolist()
```

- Lưu lại thành file **data_train_90.jsonl** cho file train và **data_test_10.jsonl** cho file test.
```
jsonl_data = [item for item in jsonl_data if item is not None]

with open("data_train_90.jsonl", "w", encoding="utf-8") as f:
    for item in jsonl_data:
        json.dump(item, f, ensure_ascii=False)
        f.write("\n")
```

- Kết quả cuối cùng.

![Fine-tuning illustration](/images/2-dataset/data-json.png)


{{% notice note %}}
Tương tự như cách làm của bộ dữ liệu train, ta sẽ áp dụng cho file test như hướng dẫn trên.
{{% /notice %}}

