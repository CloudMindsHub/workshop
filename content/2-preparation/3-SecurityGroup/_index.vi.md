+++
title = "Tạo Security Group"
date = 2024
weight = 3
chapter = false
pre = "<b>2.3. </b>"
+++



#### Các bước tạo Security Group EC2

- Vào AWS console tìm kiếm VPC và chọn vào Security Group

![ImageVPC](/images//2-Preparetion/3-SG/Preparation-SecurityGroup-img1.png?width=50pc)

- Nhập tên: **DockerSwarm-WS-SG**
- Mô tả: **Allow SSH for EC2**
- Chọn VPC đã tạo

![ImageVPC](/images//2-Preparetion/3-SG/Preparation-SecurityGroup-img2.png?width=50pc)

- Thêm các inbound rules như sau:

![ImageVPC](/images//2-Preparetion/3-SG/Preparation-SecurityGroup-img3.png?width=50pc)

- Sau đó ấn vào tạo mới

![ImageVPC](/images//2-Preparetion/3-SG/Preparation-SecurityGroup-img4.png?width=50pc)

#### Các bước tạo Security Group RDS

- Nhập tên: **DockerSwarm-WS-DB-SG**
- Mô tả: **Security Group for DB instance**
- Chọn VPC đã tạo
- Inbound rule chọn lại Security group mình đã cấu hình từ trước.

![ImageVPC](/images//2-Preparetion/3-SG/Preparation-SecurityGroup-img5.png?width=50pc)

- Sau đó ấn vào tạo mới

![ImageVPC](/images//2-Preparetion/3-SG/Preparation-SecurityGroup-img6.png?width=50pc)

- Kiểm tra lại 2 Security group mình vừa tạo đã hoành thành

![ImageVPC](/images//2-Preparetion/3-SG/Preparation-SecurityGroup-img7.png?width=50pc)
