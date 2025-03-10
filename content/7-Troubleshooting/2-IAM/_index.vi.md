+++
title = "Tạo quyền IAM"
date = 2024
weight = 2
chapter = false
pre = "<b>7.2. </b>"
+++



{{% notice tip %}}
Khi ta muốn sử dụng đăng nhập vào ECR thì ta cần phải sử dụng lệnh “aws configure” và nhập access key vào nó mới có thể sài được, vì thế nên ta có thể tạo một quyền để cho các EC2 instance được cấp quyền sẽ tự động đăng nhập giúp nhanh hơn và bảo mật hơn.
{{% /notice %}}


#### Các bước tạo quyền IAM

- Tìm kiêm IAM trong AWS console, chọn vào Roles và chọn tạo.

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img1.png?width=50pc)

- Chọn service là EC2

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img2.png?width=50pc)

- Thêm quyền truy cập vào ECR

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img3.png?width=50pc)

- Nhập tên: `ECR-Access-Role`

- Mô tả: `Allow EC2 instance to all ECR`

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img4.png?width=50pc)

- Kiểm tra kĩ lại và ấn tạo.

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img5.png?width=50pc)

- Tạo thành công.

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img6.png?width=50pc)

- Tiếp theo ta sẽ vào EC2 và gán role vào cho nó.

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img7.png?width=50pc)

- Tìm đúng tên quyền đã tạo và chọn update

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img8.png?width=50pc)

{{% notice note %}}
Tương tự như vậy mình sẽ cần gán hết cho các instance đang chạy các nodes.
{{% /notice %}}