+++
title = "Install Docker Compose"
date = 2024
weight = 1
chapter = false
pre = "<b>6.1. </b>"
+++



#### Steps to Install Docker Compose

- Since Docker has already been installed, there is no need to download it again.
- Enable Docker to start automatically.

```js
sudo chkconfig docker on
```

- Install the latest version of Docker Compose.

```js
sudo curl -L https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
```

- Add it to the path.

```js
export PATH=$PATH:/usr/local/bin
```

- Grant permissions to Docker Compose.

```js
sudo chmod +x /usr/local/bin/docker-compose
```

- Check the installation.

```js
docker-compose --version
```

![ImageVPC](/images/6-DockerCompose/1-Install/DockerCompose-Install-img1.png?width=70pc)
