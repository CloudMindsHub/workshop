+++
title = "Kiểm tra nodes"
date = 2024
weight = 4
chapter = false
pre = "<b>6.4. </b>"
+++



#### Các bước kiểm tra container trên từng nodes

- Chạy và kiểm tra web trên port 5000 của cả 3 nodes xem hoạt động có được tốt không 
- Đầu tiên là node manage

```js
http://<public_ip_EC2>:5000
```

![ImageVPC](/images/6-DockerCompose/4-Check/DockerCompose-Check-NodeManage.png?width=50pc)

- Tiếp theo là node worker 1
  
```js
http://<public_ip_EC2>:5000
```

![ImageVPC](/images/6-DockerCompose/4-Check/DockerCompose-Check-Node1.png?width=50pc)

- Cuối cùng là node worker 2

```js
http://<public_ip_EC2>:5000
```

![ImageVPC](/images/6-DockerCompose/4-Check/DockerCompose-Check-Node2.png?width=50pc)