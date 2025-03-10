+++
title = "Lỗi npm start"
date = 2024
weight = 1
chapter = false
pre = "<b>7.1. </b>"
+++



#### Lỗi khi kiểm tra lệnh npm start

- Khi ta chạy lệnh sau

```js
npm start
```

- Lỗi sẽ hiện ra như sau

![ImageVPC](/images/7-Troubleshooting/1-%20Npm/Troubleshooting-Npm-img1.png?width=50pc)

- Nguyên nhân là vì nó đang bị lỗi nodemon khi ta install  về vì thế nên ta sẽ phải tải lại và cấp quyền  lại cho nó

```js
//cap quyen
chmod +x /home/ec2-user/AWS-FCJ-Management/node_modules/.bin/nodemon

//xoa di tai lai
npm uninstall nodemon
npm install nodemon --save-dev
```

![ImageVPC](/images/7-Troubleshooting/1-%20Npm/Troubleshooting-Npm-img2.png?width=50pc)

- Sau khi thành công thì ta chạy lại lệnh npm start

```js
npm start
```

![ImageVPC](/images/7-Troubleshooting/1-%20Npm/Troubleshooting-Npm-img3.png?width=50pc)
