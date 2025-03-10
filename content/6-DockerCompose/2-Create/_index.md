+++
title = "Create file docker compose"
date = 2024
weight = 2
chapter = false
pre = "<b>6.2. </b>"
+++



#### Steps to Create the docker-compose.yaml File

- Now we need to configure the docker-compose.yaml file so that it can automatically create services more easily. First, we'll clear the contents inside it.

```js
truncate -s 0 docker-compose.yaml
```

- Then we'll use the command to open the file and configure it.

```js
vi docker-compose.yaml
```

![ImageVPC](/images/6-DockerCompose/2-CreateFile/DockerCompose-Create-img1.png?width=50pc)

- Inside the file, we need to configure it as follows:

```js
version: "3.9"
services:
  app:
    image: ${IMAGE}             # URI image tren ECR 
    environment:                # enviroment database
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
  When selecting the mode: - "Host" mode allows only one container corresponding to one replica to run on a node on a certain port, for example, port 5000. To run more, manual configuration is needed. - "Ingress" mode allows running multiple replicas on one node. However, since we are using the RDS free tier, it limits running on multiple nodes and replicas. Therefore, I chose the above mode for this example.
{{% /notice %}}

- Use the command to check the file again.

```js
cat docker-compose.yaml
```

![ImageVPC](/images/6-DockerCompose/2-CreateFile/DockerCompose-Create-img2.png?width=50pc)

- The .env file cannot be passed into Docker Swarm, so we need to pass it manually.

```js
export IMAGE=<Image_URI>       //Change image on ECR your
export DB_HOST=<Endpoint_RDS>  //Change endpoin on RDS your 
export DB_NAME=<db_name>       //Change name database your
export DB_USER=<User_name>     //Change name user on RDS your 
export DB_PASS=<password>      //Change passwork on RDS your 
```
