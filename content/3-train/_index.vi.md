+++
title = "Fine-tuning"
date = 2025
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

### Các giới hạn

### Custom model bedrock

- Chọn region **us-east-1 (N. Virginia)**

- Chọn mục **Custom models (fine tuning, dist,...)** 

![Train1](/images/3-train/train_1.png)

- Chọn **Create Fine-tuning job**

![Train2](/images/3-train/train_2.png)

- Chọn mô hình muốn fine-tuning, ở đây mình chọn Nova Lite.

![Train3](/images/3-train/train_3.png)

- Điền tên mô hình fine-tuning và tên job.

![Train4](/images/3-train/train_4.png)

- Phần input data, ô đầu tiên các bạn chọn tới đường dẫn file **train_jsonl**. Hiện nay, với các bài toán fine-tuning, chúng ta cũng không cần thiết phải có dữ liệu val, tại vì...

![Train5](/images/3-train/train_5.png)

- Các siêu thông số  huấn luyện mình chọn như hình bên dưới

![Train6](/images/3-train/train_6.png)

- Chọn đường dẫn lưu mô hình đầu ra sau khi fine tune, chọn service role cấp quyền bedrock truy cập tới S3.

![Train7](/images/3-train/train_7.png)

- Chọn **Create Fine-tuning job**

- Nếu tất cả các format đều đúng và không có lỗi gì xảy ra. Bạn ra màn tab Jobs bên ngoài sẽ thấy Fine-tuning job đang trong quá trình In Progress. Thời gian phụ thuộc vào số lượng mẫu dữ liệu và epochs. Trường hợp của mình tầm 10 phút.

![Train8](/images/3-train/train_8.png)