+++
title = "Test Deployment on EC2 Public IP"
date = 2024
weight = 6
chapter = false
pre = "<b>3.6. </b>"
+++



#### Steps for Deployment on EC2 Public IP

- Install Docker Engine:
```js
sudo amazon-linux-extras install docker
```

- Start Docker:
```js
sudo service docker start
sudo usermod -a -G docker ec2-user
```
![ImageRDS](/images/3-RDS/6-Deploy/RDS-Deploy-img1.png?width=50pc)

- Configure the .env file:

```js
touch .env
vi .env
```

- Configure the content inside .env (you will replace the values in parentheses to match the configurations you created earlier):

```js
DB_HOST= "Endpoint RDS"
DB_NAME= "db name"
DB_USER= "db user"
DB_PASS= "db password"
```
![ImageRDS](/images/3-RDS/6-Deploy/RDS-Deploy-img2.png?width=50pc)

- Use the following command to check the file:

```js
cat .env
```
![ImageVPC](/images/3-RDS/6-Deploy/RDS-Deploy-img3.png?width=50pc)

- Use this command to check the code:

```js
npm start
```
{{% notice warning %}}
Use this command to verify if the new libraries you downloaded are working fine before building the image. This part is prone to errors, so you might need to check the Troubleshooting section or look for solutions online.
{{% /notice %}}

![ImageRDS](/images/7-Troubleshooting/1-%20Npm/Troubleshooting-Npm-img3.png?width=40pc)

- If the test is successful, you can manually build an image using:

```js
docker build -t awsfcj .
docker images
```
![ImageRDS](/images/3-RDS/6-Deploy/RDS-Deploy-img4.png?width=50pc)

- Run the image with this command:

```js
docker run --env-file .env -p 5000:5000 awsfcj
```
![ImageRDS](/images/3-RDS/6-Deploy/RDS-Deploy-img5.png?width=50pc)

- Use the public IP of your EC2 instance along with port 5000 to check the application on the web:

```js
http://<public_ip_EC2>:5000
```
![ImageRDS](/images/3-RDS/6-Deploy/RDS-Deploy-img6.png?width=50pc)
