+++
title = "Tạo các nodes worker"
date = 2024
weight = 1
chapter = false
pre = "<b>5.1. </b>"
+++



#### Các bước tạo các nodes worker

{{% notice note %}}
Ở phần này mình sẽ phải tạo thêm 2 instance EC2 để làm 2 nodes còn lại, còn instance đang sài sẽ làm node manage. Vì thế nên bước này sẽ gần giống như bước tạo EC2 ở phần chuẩn bị.
{{% /notice %}}

- Đầu tiên mình sẽ tạo node 1.
- Nhập tên: **`DockerSwarm-Instance-Node1`**.

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img1.png?width=50pc)

- Chọn Type:  **t2.micro** (free tier).
- Key pair: Chọn key pair giống phần tạo EC2 instace.

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img2.png?width=50pc)

- Chọn VPC đã chuẩn bị.
- Subnet: Chọn Subnet public 2.
- Chọn SG đã tạo cho EC2.

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img3.png?width=50pc)

- Tạo node 2.
- Nhập tên: **`DockerSwarm-Instance-Node2`**.

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img4.png?width=50pc)

- Chọn Type:  **t2.micro** (free tier).
- Key pair: Chọn key pair giống phần tạo EC2 instace.

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img5.png?width=50pc)

- Chọn VPC đã chuẩn bị.
- Subnet: Chọn Subnet public 3.
- Chọn SG đã tạo cho EC2.

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img6.png?width=50pc)

- Kiểm tra lại và chọn Launch instance để tạo.

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img7.png?width=50pc)

- Kiểm tra trạng thái của 2 nodes vừa tạo.

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img8.png?width=50pc)
