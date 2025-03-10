+++
title = "Create nodes worker"
date = 2024
weight = 1
chapter = false
pre = "<b>5.1. </b>"
+++



#### Steps to create worker nodes

{{% notice note %}}
In this section, we will need to create two additional EC2 instances to serve as the remaining nodes, while the current instance will act as the manager node. Therefore, this step will be quite similar to creating an EC2 instance in the preparation section.
{{% /notice %}}

- First, we will create node 1.
- Enter the name: **`DockerSwarm-Instance-Node1`**.

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img1.png?width=50pc)

- Select Type:  **t2.micro** (free tier).
- Key pair: Choose the same key pair as used when creating the EC2 instance.

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img2.png?width=50pc)

- Select the prepared VPC.
- Subnet: Choose public Subnet 2.
- Select the security group (SG) that was created for EC2.

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img3.png?width=50pc)

- Now create node 2.
- Enter the name: **`DockerSwarm-Instance-Node2`**.

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img4.png?width=50pc)

- Select Type:  **t2.micro** (free tier).
- Key pair: Choose the same key pair as used when creating the EC2 instance.

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img5.png?width=50pc)

- Select the prepared VPC.
- Subnet: Choose public Subnet 3.
- Select the security group (SG) that was created for EC2.

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img6.png?width=50pc)

- Review the details and select Launch instance to create.

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img7.png?width=50pc)

- Let me know if you need any additional changes!

![ImageVPC](/images/5-DockerSwarm/1-CreateNodes/DockerSwarm-Instance-img8.png?width=50pc)
