+++
title = "Installing Node.js and Npm"
date = 2024
weight = 5
chapter = false
pre = "<b>3.5. </b>"
+++



#### Steps to Install Node.js and Npm

{{% notice note %}}
Note: Before proceeding with this section, make sure you’ve navigated to the directory of the repository you cloned earlier. Then, install the necessary dependencies based on the operating system you configured for your virtual machine (currently using Amazon Linux 2).
{{% /notice %}}

- Install Node Version Manager (nvm):
    
```js
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
```
- Activate the installed nvm:

```js
. ~/.nvm/nvm.sh
```
- Use nvm to install Node.js:

```js
nvm install 16
```

- Verify the installation using the following commands:
```js
node -v
npm -v
```
![ImageVPC](/images/3-RDS/5-Npm/RDS-Npm-img1.png?width=50pc)

- Install npm dependencies:
```js
npm install
```

- Install dotenv:
  
```js
npm install dotenv
```
![ImageVPC](/images/3-RDS/5-Npm/RDS-Npm-img2.png?width=50pc)

- Since there might be some errors, run the following command to fix them:

```js
npm audit fix
```
![ImageVPC](/images/3-RDS/5-Npm/RDS-Npm-img3.png?width=50pc)
