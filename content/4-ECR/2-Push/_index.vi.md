+++
title = "Đẩy image lên ECR"
date = 2024
weight = 2
chapter = false
pre = "<b>4.2. </b>"
+++



#### Các bước đẩy image lên ECR

- Giờ chúng ta sẽ build image nhưng chúng ta cần phải đăng nhập access key đã tạo trước để nó có thể dùng đăng nhập vào AWS.

{{% notice note %}}
Access key là một phần rất bảo mật vì thế nên bạn không được lộ bất kì thông tin gì về nó. Nếu chưa rõ cách tạo bạn có thể xem thêm ở tra amazon hoặc bất cứ nơi đâu về cách “**Tạo một access key như thế nào**”.
{{% /notice %}}

![ImageVPC](/images/4-ECR/2-Push/ECR-Push-img1.png?width=50pc)

- Khi lưu file về rồi ta sẽ truy cập nó bằng cách vào lại VScode nãy ta đã ssh trong EC2 ở phần chuẩn bị. Sau đó dùng lệnh để kết nối và nhập những thông tin về access key.

```js
aws configure
```

![ImageVPC](/images/4-ECR/2-Push/ECR-Push-img2.png?width=50pc)

- Để push image lên ECR bằng các lệnh đã show ở phần ECR repository (ta sẽ copy hết vào)
- Login vào ECR

```js
aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin <AWS_Account_ID>.dkr.ecr.ap-southeast-1.amazonaws.com
```
- Build một image

```js
docker build -t aws-fcj-management .
```

![ImageVPC](/images/4-ECR/2-Push/ECR-Push-img3.png?width=50pc)

- Gắn tag cho nó và push lên ECR

```js
docker tag aws-fcj-management:latest <AWS_Account_ID>.dkr.ecr.ap-southeast-1.amazonaws.com/aws-fcj-management:latest
docker push <AWS_Account_ID>.dkr.ecr.ap-southeast-1.amazonaws.com/aws-fcj-management:latest
```

![ImageVPC](/images/4-ECR/2-Push/ECR-Push-img4.png?width=50pc)

- Vào lại ECR để kiểm tra image đã tồn tại chưa.

![ImageVPC](/images/4-ECR/2-Push/ECR-Push-img5.png?width=50pc)
