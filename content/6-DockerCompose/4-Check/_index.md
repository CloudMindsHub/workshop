+++
title = "Check nodes"
date = 2024
weight = 4
chapter = false
pre = "<b>6.4. </b>"
+++



#### Steps to Check Containers on Each Node

- Run and check the web on port 5000 of all three nodes to see if they are functioning well.
- First, check the manager node:

```js
http://<public_ip_EC2>:5000
```

![ImageVPC](/images/6-DockerCompose/4-Check/DockerCompose-Check-NodeManage.png?width=50pc)

- Next, check worker node 1:
  
```js
http://<public_ip_EC2>:5000
```

![ImageVPC](/images/6-DockerCompose/4-Check/DockerCompose-Check-Node1.png?width=50pc)

- Finally, check worker node 2:

```js
http://<public_ip_EC2>:5000
```

![ImageVPC](/images/6-DockerCompose/4-Check/DockerCompose-Check-Node2.png?width=50pc)