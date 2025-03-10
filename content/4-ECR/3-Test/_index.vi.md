+++
title = "Chạy thử image trên ECR"
date = 2024
weight = 3
chapter = false
pre = "<b>4.3. </b>"
+++



#### Các bước chạy thử image trên ECR

- Khi image đã được đẩy lên ECR thì ta sẽ chạy thử xem image đó hoạt động có tốt hay không.
```js
docker run --env-file .env -p 5000:5000 <Image_URI_ECR>
```

![ImageVPC](/images/4-ECR/3-Test/ECR-Test-img1.png?width=50pc)

- Sử dụng public IP trong EC2 và gắn với port 5000 để kiểm tra trên web.
```js
http://<public_ip_EC2>:5000
```

![ImageVPC](/images/4-ECR/3-Test/ECR-Test-img2.png?width=50pc)
