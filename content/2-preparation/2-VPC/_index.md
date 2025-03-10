+++
title = "Create VPC"
date = 2024
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++


#### Steps to create VPC

- Go to AWS console, find and create VPC.

![ImageVPC](/images//2-Preparetion/2-VPC/Preparation-VPC-img1.png?width=50pc)

- Select **VPC and more**
- Name: **Docker-WS**
- Ipv4: **10.0.0.0/16**

![ImageVPC](/images//2-Preparetion/2-VPC/Preparation-VPC-img2.png?width=50pc)

- I will configure as follows:

![ImageVPC](/images//2-Preparetion/2-VPC/Preparation-VPC-img3.png?width=40pc)

- Then check again and press create

![ImageVPC](/images//2-Preparetion/2-VPC/Preparation-VPC-img4.png?width=40pc)

- Create success

![ImageVPC](/images//2-Preparetion/2-VPC/Preparation-VPC-img5.png?width=40pc)

#### Configure Subnet

- Public ipv4 public subnets we just created to be able to ping the internet

![ImageVPC](/images//2-Preparetion/2-VPC/Preparation-VPC-img6.png?width=50pc)

- Select **Auto-assign IP** and save

![ImageVPC](/images//2-Preparetion/2-VPC/Preparation-VPC-img7.png?width=45pc)

{{% notice note %}}
  You do it myself with the remaining 2 public Subnets.
{{% /notice %}}