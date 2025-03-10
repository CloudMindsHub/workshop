+++
title = "Kết nối các nodes"
date = 2024
weight = 2
chapter = false
pre = "<b>5.2. </b>"
+++



#### Các bước kết nối các nodes

- Mình sẽ dùng VSCode để kết nối chúng tương tự như kết nối VSCode trong phần **Chuẩn bị** đã thực hiện để kết nối 2 node worker này, sau đó ping thử cả 2 ra internet.
```js
ping -c5 amazon.com
```

![ImageVPC](/images/5-DockerSwarm/2-ConnectVS/DockerSwarm-VSCode-img1.png?width=50pc)

- Tiếp theo mình sẽ tải docker cho cả 2 nodes để có thể dùng được các lệnh của docker.

```js
sudo amazon-linux-extras install docker
sudo service docker start
sudo usermod -a -G docker ec2-user
```

![ImageVPC](/images/5-DockerSwarm/2-ConnectVS/DockerSwarm-VSCode-img2.png?width=50pc)

- Sau đó mình đăng nhập vào ECR và kéo image đã build từ trước xuống để có thể chạy nó.

{{% notice tip %}}
 Có thể dùng IAM để có thể tự động đăng nhập cho các máy ảo mà không cần dùng đến lệnh “aws configure”. Điều này sẽ giúp mình có thể làm nhanh hơn, hiệu quả hơn, bảo mật hơn. (Tham khảo ở phần Troubleshooting)
{{% /notice %}}

```js
aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin <Account_ID>.dkr.ecr.ap-southeast-1.amazonaws.com
docker pull <URI_image>
```

![ImageVPC](/images/5-DockerSwarm/2-ConnectVS/DockerSwarm-VSCode-img3.png?width=50pc)

- Tạo docker cluster cho node manage
- Dùng lệnh token để paste và 2 nodes còn lại

```js
docker swarm init --advertise-addr <MANAGER-IP-PUBLIC-EC2>
docker swarm join --token <Token_Manage>
```

![ImageVPC](/images/5-DockerSwarm/2-ConnectVS/DockerSwarm-VSCode-img4.png?width=50pc)

- Để kiểm tra kết nối mình sẽ dùng lệnh sau ở bên node manage.

```js
docker node ls
```

![ImageVPC](/images/5-DockerSwarm/2-ConnectVS/DockerSwarm-VSCode-img5.png?width=50pc)

