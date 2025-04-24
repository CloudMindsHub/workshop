+++
title = "Upload dữ liệu"
date = 2025
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++


### S3 bucket

Sau khi đã tạo được thư mục chứa **hình ảnh** cùng với file **.jsonl** từ bước xử lý dữ liệu trước đó, bước tiếp theo là upload toàn bộ dữ liệu lên **Amazon S3**. Đây là một bước quan trọng để chuẩn bị cho quá trình **fine-tuning** mô hình trên **AWS Bedrock**, vì mô hình sẽ cần truy cập trực tiếp các tệp tin từ **S3** trong suốt quá trình huấn luyện.

- Tạo cấu trúc thư mục như sau:

![S3-Dataset](/images/2-dataset/s3_dataset.png)

- Upload folder chứa image của dữ liệu **train** và **test**.

![S3-Dataset](/images/2-dataset/s3_train.png)

- Upload file .jsonl của dữ liệu **train** và **test**. 

![S3-Dataset](/images/2-dataset/s3_train_js.png)
