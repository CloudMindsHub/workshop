+++
title = "Create EC2"
date = 2024
weight = 4
chapter = false
pre = "<b>2.4. </b>"
+++



#### Steps to Create an EC2 Instance

- Go to EC2 in the AWS console and click Launch instance to create one.

![ImageVPC](/images/2-Preparetion/4-EC2/Preparation-EC2-img1.png?width=50pc)

- Enter the name: **DockerSwarm-Instance**
- Use Amazon Linux 2

![ImageVPC](/images/2-Preparetion/4-EC2/Preparation-EC2-img2.png?width=40pc)

- Choose t2.micro
- Select the key pair you have created.

{{% notice note %}}
If you do not have a key pair, you need to create a new one and save it for SSH.
{{% /notice %}}

![ImageVPC](/images/2-Preparetion/4-EC2/Preparation-EC2-img3.png?width=40pc)

- Choose the **VPC** you have created.
- Choose the **Subnet public 1** to enable internet access.
- Choose the **Security group** you created for the EC2 instance.

![ImageVPC](/images/2-Preparetion/4-EC2/Preparation-EC2-img4.png?width=40pc)

- Review the settings and click Launch instance to create it.

![ImageVPC](/images/2-Preparetion/4-EC2/Preparation-EC2-img5.png?width=50pc)

- Check the status.

![ImageVPC](/images/2-Preparetion/4-EC2/Preparation-EC2-img6.png?width=50pc)

- Connect by copying the command for SSH.

![ImageVPC](/images/2-Preparetion/4-EC2/Preparation-EC2-img7.png?width=50pc)
