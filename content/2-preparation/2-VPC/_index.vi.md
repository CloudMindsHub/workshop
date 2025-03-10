+++
title = "Tạo VPC"
date = 2024
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++


#### Các bước tạo VPC

- Vào AWS console tìm và tạo VPC.

![ImageVPC](/images//2-Preparetion/2-VPC/Preparation-VPC-img1.png?width=50pc)

- Chọn **VPC and more**
- Nhập tên: **Docker-WS**
- Ipv4: **10.0.0.0/16**

![ImageVPC](/images//2-Preparetion/2-VPC/Preparation-VPC-img2.png?width=50pc)

- Mình sẽ cấu hình như sau:

![ImageVPC](/images//2-Preparetion/2-VPC/Preparation-VPC-img3.png?width=40pc)

- Sau đó kiểm tra lại và ấn tạo

![ImageVPC](/images//2-Preparetion/2-VPC/Preparation-VPC-img4.png?width=40pc)

- Tạo thành công

![ImageVPC](/images//2-Preparetion/2-VPC/Preparation-VPC-img5.png?width=40pc)

#### Cấu hình Subnet

- Public ipv4 các subnet public ta vừa tạo để có thể ping ra được internet

![ImageVPC](/images//2-Preparetion/2-VPC/Preparation-VPC-img6.png?width=50pc)

- Chọn **Auto-assign IP** và lưu lại

![ImageVPC](/images//2-Preparetion/2-VPC/Preparation-VPC-img7.png?width=45pc)

{{% notice note %}}
  Tương tự mình làm với 2 Subnet public còn lại
{{% /notice %}}