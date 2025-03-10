+++
title = "Cài đặt Node.js và Npm"
date = 2024
weight = 5
chapter = false
pre = "<b>3.5. </b>"
+++



#### Các bước cài đặt Node.js và Npm

{{% notice note %}}
Lưu ý: Trước khi làm phần này, mình cần phải truy cập vào trong thư mục mình đã git clone về trước. Sau đó mình sẽ cần phải cài đặt theo tùy loại hệ điều hành mà mình đã cấu hình cho máy ảo. (Hiện đang sài Amazon linux 2)
{{% /notice %}}

- Cài đặt node version manager (nvm).
    
```js
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
```
- Kích hoạt nvm đã cài.

```js
. ~/.nvm/nvm.sh
```
- Dùng nvm này để cài đặt node.js.

```js
nvm install 16
```

- Kiểm tra bằng lệnh sau:
```js
node -v
npm -v
```
![ImageVPC](/images/3-RDS/5-Npm/RDS-Npm-img1.png?width=50pc)

- Cài đặt npm 
```js
npm install
```

- Cài đặt dotenv
  
```js
npm install dotenv
```
![ImageVPC](/images/3-RDS/5-Npm/RDS-Npm-img2.png?width=50pc)

Vì nó có một vài lỗi nên cần phải chạy lệnh để chỉnh sửa.

```js
npm audit fix
```
![ImageVPC](/images/3-RDS/5-Npm/RDS-Npm-img3.png?width=50pc)
