+++
title = "Npm Start Error"
date = 2024
weight = 1
chapter = false
pre = "<b>7.1. </b>"
+++



#### Error when running the npm start command

- When running the following command:

```js
npm start
```

- The error appears as follows:

![ImageVPC](/images/7-Troubleshooting/1-%20Npm/Troubleshooting-Npm-img1.png?width=50pc)

- The issue is caused by a problem with nodemon during installation. To fix it, you need to reinstall and grant the necessary permissions.

```js
//cap quyen
chmod +x /home/ec2-user/AWS-FCJ-Management/node_modules/.bin/nodemon

//xoa di tai lai
npm uninstall nodemon
npm install nodemon --save-dev
```

![ImageVPC](/images/7-Troubleshooting/1-%20Npm/Troubleshooting-Npm-img2.png?width=50pc)

- After successfully reinstalling, run the npm start command again.

```js
npm start
```

![ImageVPC](/images/7-Troubleshooting/1-%20Npm/Troubleshooting-Npm-img3.png?width=50pc)
