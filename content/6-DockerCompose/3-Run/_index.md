+++
title = "Run file docker compose"
date = 2024
weight = 3
chapter = false
pre = "<b>6.3. </b>"
+++



#### Steps to Run the Docker Compose File

{{% notice note %}}
In this section, we use Docker Compose to configure and run Docker Swarm services. Therefore, we need to pay close attention to the details of the configurations, such as ensuring the security group is correct, IAM permissions are sufficient, and that RDS can connect properly. Carefully check all previous configurations and troubleshoot any errors to run successfully.
{{% /notice %}}

- Run the docker-compose file.
 
```js
docker stack deploy -c docker-compose.yaml <STACK_NAME>
```

- Check if the service is running.
  
```js
docker service ls
```

![ImageVPC](/images/6-DockerCompose/3-Build/DockerCompose-Build-img1.png?width=50pc)

- Check the logs for any errors.

![ImageVPC](/images/6-DockerCompose/3-Build/DockerCompose-Build-img2.png?width=50pc)

- Check the containers distributed across the nodes.

![ImageVPC](/images/6-DockerCompose/3-Build/DockerCompose-Build-img3.png?width=50pc)

- Verify that the containers on each node are operational.

![ImageVPC](/images/6-DockerCompose/3-Build/DockerCompose-Build-img4.png?width=50pc)