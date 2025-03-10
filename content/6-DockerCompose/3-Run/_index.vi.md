+++
title = "Chạy file docker compose"
date = 2024
weight = 3
chapter = false
pre = "<b>6.3. </b>"
+++



#### Các bước chạy file docker compose

{{% notice note %}}
Ở phần này ta dùng docker compose để cấu hình và chạy các dịch vụ Docker Swarm, vì thế ta cần chú ý chi tiết về các cấu hình phải chính xác như: Security group phải chính xác, IAM đầy đủ quyền, RDS có kết nói được không. Kiểm tra kỹ các cấu hình từ trước và xử lý lỗi để chạy được thành công.
{{% /notice %}}

- Chạy file docker-compose.
 
```js
docker stack deploy -c docker-compose.yaml <STACK_NAME>
```

- Kiểm tra service đã chạy.
  
```js
docker service ls
```

![ImageVPC](/images/6-DockerCompose/3-Build/DockerCompose-Build-img1.png?width=50pc)

- Kiểm tra logs xem có phát hiện lỗi không.

![ImageVPC](/images/6-DockerCompose/3-Build/DockerCompose-Build-img2.png?width=50pc)

- Kiểm tra các container được chia trên các nodes.

![ImageVPC](/images/6-DockerCompose/3-Build/DockerCompose-Build-img3.png?width=50pc)

- Kiểm tra các container ở trên từng node xem đã hoạt động chưa.

![ImageVPC](/images/6-DockerCompose/3-Build/DockerCompose-Build-img4.png?width=50pc)