+++
title = "Tạo EC2"
date = 2024
weight = 4
chapter = false
pre = "<b>2.4. </b>"
+++



#### Các bước tạo EC2

- Vào EC2 trong AWS console và ấn Launch instance để tạo

![ImageVPC](/images/2-Preparetion/4-EC2/Preparation-EC2-img1.png?width=50pc)

- Nhập tên: **DockerSwarm-Instance**
- Sử dụng linux 2

![ImageVPC](/images/2-Preparetion/4-EC2/Preparation-EC2-img2.png?width=40pc)

- Sài t2.micro
- Key pair chọn key mình đã tạo

{{% notice note %}}
Nếu chưa có key pair thì mình phải tạo mới và lưu lại dùng để đăng nhập khi Ssh.
{{% /notice %}}

![ImageVPC](/images/2-Preparetion/4-EC2/Preparation-EC2-img3.png?width=40pc)

- Chọn **VPC** đã tạo.
- Chọn **Subnet public 1** để có thể ping ra internet
- Chọn **Security group** đã tạo cho EC2

![ImageVPC](/images/2-Preparetion/4-EC2/Preparation-EC2-img4.png?width=40pc)

- Kiểm tra lại và chọn Launch instance để tạo

![ImageVPC](/images/2-Preparetion/4-EC2/Preparation-EC2-img5.png?width=50pc)

- Kiểm tra trạng thái

![ImageVPC](/images/2-Preparetion/4-EC2/Preparation-EC2-img6.png?width=50pc)

- Kết nối bằng cách sao chép lệnh để Ssh.

![ImageVPC](/images/2-Preparetion/4-EC2/Preparation-EC2-img7.png?width=50pc)
