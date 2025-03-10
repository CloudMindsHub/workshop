+++
title = "Tạo file docker compose"
date = 2024
weight = 2
chapter = false
pre = "<b>6.2. </b>"
+++



#### Các bước tạo file docker-compose.yaml

- Bây giờ ta cần phải cấu hình file docker-compose.yaml để nó có thể tự động tạo service một cách dễ dàng hơn. Đầu tiên ta sẽ xóa nội dung bên trong nó trước.
```js
truncate -s 0 docker-compose.yaml
```

- Sau đó ta dùng lệnh để vào file và cấu hình.

```js
vi docker-compose.yaml
```

![ImageVPC](/images/6-DockerCompose/2-CreateFile/DockerCompose-Create-img1.png?width=50pc)

- Bên trong file ta phải cấu hình như sau:

```js
version: "3.9"
services:
  app:
    image: ${IMAGE}             # URI image tren ECR
    environment:                # Bien moi truong cua database
      - DB_HOST=${DB_HOST}
      - DB_NAME=${DB_NAME}
      - DB_USER=${DB_USER}
      - DB_PASS=${DB_PASS}
    deploy:
      replicas: 3
      update_config:
        parallelism: 1
        order: stop-first
      restart_policy:
        condition: on-failure
    ports:
      - target: 5000
        published: 5000
        protocol: tcp
        mode: host       #ingress
    networks:
      - app-network

networks:
  app-network:
    driver: overlay
```

{{% notice warning %}}
  Khi chọn chế độ:
    “**Host**” thì ta chỉ có thể chạy được một container tương ứng với một replicas ở trên một node khi chạy trên một port nào đó ví dụ như: port 5000, nếu như muốn chạy được nhiều hơn thì ta phải cấu hình bằng tay cho nó.
    “**Ingress**” thì ta có thể chạy được nhiều replicas hơn trên một node, tuy nhiên vì đang sử dụng RDS free tier nó hạn chế chạy được trên nhiều nodes và replicas. Vì thế nên bài này mình chọn chế độ trên.
{{% /notice %}}

- Dùng lệnh để kiểm tra lại file.

```js
cat docker-compose.yaml
```

![ImageVPC](/images/6-DockerCompose/2-CreateFile/DockerCompose-Create-img2.png?width=50pc)

- File .env sẽ không truyền được vào docker swarm nên ta phải truyền bằng tay.

```js
export IMAGE=<Image_URI>       //Change image on ECR your
export DB_HOST=<Endpoint_RDS>  //Change endpoin on RDS your 
export DB_NAME=<db_name>       //Change name database your
export DB_USER=<User_name>     //Change name user on RDS your 
export DB_PASS=<password>      //Change passwork on RDS your 
```
