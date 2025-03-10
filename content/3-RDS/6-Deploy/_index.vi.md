+++
title = "Triển khai thử trên IP Public EC2"
date = 2024
weight = 6
chapter = false
pre = "<b>3.6. </b>"
+++



#### Các bước triển khai trên IP Public EC2

- Cài đặt Docker Engine.
```js
sudo amazon-linux-extras install docker
```

- Khởi động Docker.
```js
sudo service docker start
sudo usermod -a -G docker ec2-user
```
![ImageRDS](/images/3-RDS/6-Deploy/RDS-Deploy-img1.png?width=50pc)

- Cấu hình file .env.

```js
touch .env
vi .env
```

- Cấu hình bên trong .env (ta sẽ sửa các giá trị trong ngoặc sao cho phù hợp với các cấu hình mà ta đã tạo từ trước đó).

```js
DB_HOST= "Endpoint RDS"
DB_NAME= "db name"
DB_USER= "db user"
DB_PASS= "db password"
```
![ImageRDS](/images/3-RDS/6-Deploy/RDS-Deploy-img2.png?width=50pc)

- Dùng lệnh để kiểm tra lại.

```js
cat .env
```
![ImageVPC](/images/3-RDS/6-Deploy/RDS-Deploy-img3.png?width=50pc)

- Dùng lệnh để kiểm tra code.

```js
npm start
```
{{% notice warning %}}
Dùng lệnh để kiểm tra các thư viện mới tải về có chạy ổn không trước khi build image. Phần này rất dễ lỗi nên ta cần phải xem lại trong phần Troubleshooting hoặc có thể tham khảo trên mạng.
{{% /notice %}}

![ImageRDS](/images/7-Troubleshooting/1-%20Npm/Troubleshooting-Npm-img3.png?width=40pc)

- Nếu đã kiểm tra thành công thì mình sẽ thử build một image bằng thủ công.

```js
docker build -t awsfcj .
docker images
```
![ImageRDS](/images/3-RDS/6-Deploy/RDS-Deploy-img4.png?width=50pc)

- Dùng lệnh chạy image đó.

```js
docker run --env-file .env -p 5000:5000 awsfcj
```
![ImageRDS](/images/3-RDS/6-Deploy/RDS-Deploy-img5.png?width=50pc)

- Sử dụng public IP trong EC2 và gắn với port 5000 để kiểm tra trên web 

```js
http://<public_ip_EC2>:5000
```
![ImageRDS](/images/3-RDS/6-Deploy/RDS-Deploy-img6.png?width=50pc)
