+++
title = "Connect the nodes"
date = 2024
weight = 2
chapter = false
pre = "<b>5.2. </b>"
+++



#### Steps to connect the nodes

- I will use VSCode to connect them similarly to how we connected in the **Preparation** section to link these two worker nodes, then ping both to check internet connectivity.

```js
ping -c5 amazon.com
```

![ImageVPC](/images/5-DockerSwarm/2-ConnectVS/DockerSwarm-VSCode-img1.png?width=50pc)

- Next, I will install Docker on both nodes so that we can use Docker commands.

```js
sudo amazon-linux-extras install docker
sudo service docker start
sudo usermod -a -G docker ec2-user
```

![ImageVPC](/images/5-DockerSwarm/2-ConnectVS/DockerSwarm-VSCode-img2.png?width=50pc)

- After that, I will log in to ECR and pull down the previously built image to be able to run it.

{{% notice tip %}}
You can use IAM to automatically log in for the virtual machines without needing to use the “aws configure” command. This will help you work faster, more efficiently, and securely. (Refer to the Troubleshooting section)
{{% /notice %}}

```js
aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin <Account_ID>.dkr.ecr.ap-southeast-1.amazonaws.com
docker pull <URI_image>
```

![ImageVPC](/images/5-DockerSwarm/2-ConnectVS/DockerSwarm-VSCode-img3.png?width=50pc)

- Create a Docker cluster for the manager node.
- Use the token command to paste into the other two nodes.

```js
docker swarm init --advertise-addr <MANAGER-IP-PUBLIC-EC2>
docker swarm join --token <Token_Manage>
```

![ImageVPC](/images/5-DockerSwarm/2-ConnectVS/DockerSwarm-VSCode-img4.png?width=50pc)

- To check the connection, I will use the following command on the manager node.

```js
docker node ls
```

![ImageVPC](/images/5-DockerSwarm/2-ConnectVS/DockerSwarm-VSCode-img5.png?width=50pc)

