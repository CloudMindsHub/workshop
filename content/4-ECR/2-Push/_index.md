+++
title = "Push image on ECR"
date = 2024
weight = 2
chapter = false
pre = "<b>4.2. </b>"
+++



#### Steps to push an image to ECR

- Now we will build the image, but first, we need to log in using the previously created access key so that it can be used to log in to AWS.

{{% notice note %}}
The access key is very sensitive information, so make sure not to expose any details about it. If you are unsure how to create one, you can refer to Amazon's documentation or other sources on "**How to create an access key**".
{{% /notice %}}

![ImageVPC](/images/4-ECR/2-Push/ECR-Push-img1.png?width=50pc)

- Once the file is saved, access it again by returning to VS Code where we previously SSHed into EC2 during the preparation step. Then, use the command to connect and enter the access key information.

```js
aws configure
```

![ImageVPC](/images/4-ECR/2-Push/ECR-Push-img2.png?width=50pc)

- To push the image to ECR, use the commands shown in the ECR repository section (copy them all).
- Log in to ECR:

```js
aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin <AWS_Account_ID>.dkr.ecr.ap-southeast-1.amazonaws.com
```
- Build an image:

```js
docker build -t aws-fcj-management .
```

![ImageVPC](/images/4-ECR/2-Push/ECR-Push-img3.png?width=50pc)

- Tag the image and push it to ECR:

```js
docker tag aws-fcj-management:latest <AWS_Account_ID>.dkr.ecr.ap-southeast-1.amazonaws.com/aws-fcj-management:latest
docker push <AWS_Account_ID>.dkr.ecr.ap-southeast-1.amazonaws.com/aws-fcj-management:latest
```

![ImageVPC](/images/4-ECR/2-Push/ECR-Push-img4.png?width=50pc)

- Go back to ECR to check if the image exists.

![ImageVPC](/images/4-ECR/2-Push/ECR-Push-img5.png?width=50pc)
