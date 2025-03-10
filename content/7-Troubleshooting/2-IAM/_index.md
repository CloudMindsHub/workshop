+++
title = "Creating IAM Role"
date = 2024
weight = 2
chapter = false
pre = "<b>7.2. </b>"
+++



{{% notice tip %}}
When you want to log into ECR, you typically need to use the aws configure command and enter your access key to proceed. To simplify and enhance security, you can create an IAM role for EC2 instances, allowing them to automatically log in to ECR without manual configuration.
{{% /notice %}}


#### Steps to Create an IAM Role

- In the AWS console, search for IAM, go to Roles, and select Create role.

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img1.png?width=50pc)

- Choose the EC2 service.

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img2.png?width=50pc)

- Add the required permission to access ECR.

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img3.png?width=50pc)

- Name the role: `ECR-Access-Role`

- Description: `Allow EC2 instance to all ECR`

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img4.png?width=50pc)

- Review your configuration and click Create.

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img5.png?width=50pc)

- Role created successfully.

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img6.png?width=50pc)

- Next, go to your EC2 instance and assign the newly created role to it.

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img7.png?width=50pc)

- Find the correct role and select Update.

![ImageVPC](/images/7-Troubleshooting/2-IAM/Troubleshooting-IAM-img8.png?width=50pc)

{{% notice note %}}
Make sure to assign this role to all running instances in your cluster to allow each node to access ECR.
{{% /notice %}}