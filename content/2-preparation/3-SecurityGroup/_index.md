+++
title = "Create Security Group"
date = 2024
weight = 3
chapter = false
pre = "<b>2.3. </b>"
+++



#### Steps to create Security Group EC2

- Go to AWS console, search for VPC and select Security Group

![ImageVPC](/images//2-Preparetion/3-SG/Preparation-SecurityGroup-img1.png?width=50pc)

- Name: **DockerSwarm-WS-SG**
- Describe: **Allow SSH for EC2**
- Select the created VPC

![ImageVPC](/images//2-Preparetion/3-SG/Preparation-SecurityGroup-img2.png?width=50pc)

- Add inbound rules as follows:
  
![ImageVPC](/images//2-Preparetion/3-SG/Preparation-SecurityGroup-img3.png?width=50pc)

- Then click create new

![ImageVPC](/images//2-Preparetion/3-SG/Preparation-SecurityGroup-img4.png?width=50pc)

#### Steps to create a Security Group for RDS

- Enter name: **DockerSwarm-WS-DB-SG**
- Description: **Security Group for DB instance**
- Select the created VPC
- Inbound rule: select the previously configured Security Group.

![ImageVPC](/images//2-Preparetion/3-SG/Preparation-SecurityGroup-img5.png?width=50pc)

- Then click create new

![ImageVPC](/images//2-Preparetion/3-SG/Preparation-SecurityGroup-img6.png?width=50pc)

- Check 2 created Security Groups

![ImageVPC](/images//2-Preparetion/3-SG/Preparation-SecurityGroup-img7.png?width=50pc)
