+++
title = "Test deploy image on ECR"
date = 2024
weight = 3
chapter = false
pre = "<b>4.3. </b>"
+++



#### Steps to test the image on ECR

- Once the image has been pushed to ECR, we will test to see if the image is working properly:
```js
docker run --env-file .env -p 5000:5000 <Image_URI_ECR>
```

![ImageVPC](/images/4-ECR/3-Test/ECR-Test-img1.png?width=50pc)

- Use the public IP of the EC2 instance along with port 5000 to check it on the web:
```js
http://<public_ip_EC2>:5000
```

![ImageVPC](/images/4-ECR/3-Test/ECR-Test-img2.png?width=50pc)
