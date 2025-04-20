+++
title = "Chuẩn bị dataset"
date = 2025
weight = 2
chapter = false
pre = "<b>2. </b>"
+++


### Tổng quan về bộ dữ liệu

Bộ dữ liệu này là phần mở rộng của dự án Viet-Doc VAQ, được xây dựng từ 64.765 trang tài liệu giáo dục tiếng Việt 🇻🇳, bao gồm: sách bài tập, sách chuyên đề, giáo án từ các nhà xuất bản chính thống như Bộ Giáo dục & Đào tạo, Cánh Diều, Chân Trời Sáng Tạo, Kết Nối Tri Thức,... phủ rộng tất cả các môn học từ lớp 1 đến lớp 12.

Mỗi trang tài liệu đã được xử lý và chú thích kỹ lưỡng bằng các kỹ thuật Visual Question Answering (VQA), tạo nên một bộ dữ liệu có chất lượng cao và giàu thông tin.

Bộ dữ liệu bao gồm 388.277 cặp mô tả chi tiết và câu hỏi - trả lời theo ngữ cảnh, được tự động tạo ra bởi Gemini 1.5 Flash – mô hình AI hàng đầu của Google, đang dẫn đầu bảng xếp hạng WildVision Arena. Nhờ đó, đây là nguồn tài nguyên lý tưởng cho các mục tiêu nghiên cứu và ứng dụng giáo dục hiện đại.

Các môn học bao gồm: Toán học 📐, Ngữ văn 📚, Tiếng Anh 🇬🇧, Vật lý ⚛️, Hóa học 🧪, Sinh học 🌱, Lịch sử 📜, Địa lý 🌍, Giáo dục công dân 🏫, Tin học 💻, Công nghệ 🛠️, Âm nhạc 🎵, Mỹ thuật 🎨, Thể dục ⚽,...

Chỉ để thử nghiệm việc fine-tuning mô hình trên AWS Bedrock, trong workshop này chỉ dùng 1 file parquet của để huấn luyện.

### Tiền xử lý dữ liệu

- Tải dữ liệu từ Hugging Face: https://huggingface.co/datasets/5CD-AI/Viet-Doc-VQA-II/tree/main/data

![Architecture](/static/images/2-dataset/data-hf.png)

- Nhập thư viện cần thiết

```
import os
import ast
import json
import pandas as pd
```

- Đọc file parquet thành Dataframe

```
df = pd.read_parquet('train-00000-of-00034.parquet', engine="pyarrow")

df['conversations'] = df['conversations'].apply(
    lambda x: json.dumps(x.tolist(), ensure_ascii=False) if isinstance(x, np.ndarray) else json.dumps(x, ensure_ascii=False)
)
```

- Chia dữ liệu thành 3 bộ train (80%), val (10%), test (10%)

```
# Chia tập train (80%) và tập val_test (20%)
train_df, val_test_df = train_test_split(df, test_size=0.2)

# Chia tiếp val_test thành validation (10%) và test (10%)
val_df, test_df = train_test_split(val_test_df, test_size=0.5)

train_df.to_csv("viet_vqa_train.csv", index=False, encoding='utf-8')
val_df.to_csv("viet_vqa_val.csv", index=False, encoding='utf-8')
test_df.to_csv("viet_vqa_test.csv", index=False, encoding='utf-8')

df_train = pd.read_csv('viet_vqa_train.csv')
df_val = pd.read_csv('viet_vqa_val.csv')
df_test = pd.read_csv('viet_vqa_test.csv')
```


### Định dạng dữ liệu theo format AWS Bedrock

- Định dạng mẫu của AWS Bedrock
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
                                "bucketOwner": "590******512"
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

- Hàm định dạng dữ liệu
```
def create_jsonl_item(row):
    try:
        conversations = row.get("conversations")
        message_id = row.get("id")
        if isinstance(conversations, str):
            conversations = json.loads(conversations)
            
        if not isinstance(conversations, list):
            raise ValueError("Invalid JSON format in conversations column")

        if len(conversations) > 0 and conversations[0]["role"] == "user":
            original_text = conversations[0]["content"]
            image_info = {
                "image": {
                    "format": "png",
                    "source": {
                        "s3Location": {
                            "uri": f"s3://data-vqa-fine-tune-nova/train/image_{message_id}.png",
                            "bucketOwner": "536697245883"
                        }
                    }
                }
            }
            conversations[0]["content"] = [
                {"text": original_text},
                image_info
            ]

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
            "messages": conversations
        }
    except Exception as e:
        print(f"Lỗi khi xử lý conversations: {e}, row ID: {row['id']}, {conversations}")
        return None  # Trả về None nếu có lỗi
```

- Apply cho cả Dataframe
```
jsonl_data = df_sample.apply(create_jsonl_item, axis=1).tolist()
```

- Lưu lại thành file jsonl
```
jsonl_data = [item for item in jsonl_data if item is not None]

with open("data_finetune_100.jsonl", "w", encoding="utf-8") as f:
    for item in jsonl_data:
        json.dump(item, f, ensure_ascii=False)
        f.write("\n")
```

{{% notice note %}}
Tương tự như cách làm của file jsonl train, ta sẽ áp dụng cho file jsonl của val và test.
{{% /notice %}}