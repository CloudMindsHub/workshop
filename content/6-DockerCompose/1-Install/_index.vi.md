+++
title = "Cài đặt Docker Compose"
date = 2024
weight = 1
chapter = false
pre = "<b>6.1. </b>"
+++



#### Các bước cài đặt Docker Compose

- Vì đã tải docker rồi nên giờ ta không cần tải lại nữa.
- Tự động bật docker.

```js
sudo chkconfig docker on
```

- Cài bản docker compose mới nhất

```js
sudo curl -L https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
```

- Thêm vào đường dẫn

```js
export PATH=$PATH:/usr/local/bin
```

- Cấp quyền cho docker compose

```js
sudo chmod +x /usr/local/bin/docker-compose
```

- kiểm tra cài đặt

```js
docker-compose --version
```

![ImageVPC](/images/6-DockerCompose/1-Install/DockerCompose-Install-img1.png?width=70pc)
