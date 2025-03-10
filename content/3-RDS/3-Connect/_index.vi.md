+++
title = "Kết nối Cơ sở dữ liệu"
date = 2024
weight = 3
chapter = false
pre = "<b>3.3. </b>"
+++



#### Các bước kết nối Cơ sở dữ liệu

- Dùng bằng tài khoản root và bắt đầu tải sql

```js
    sudo su
    yum install mariadb
```
![ImageVPC](/images/3-RDS/3-Connect/RDS-Connect-img1.png?width=50pc)

- Sao chép endpoint của RDS dùng để kết nối.

![ImageVPC](/images/3-RDS/3-Connect/RDS-Connect-img2.png?width=50pc)

- Kiểm tra Sql và kết nối tới cơ sở dữ liệu (RDS đã tạo), sửa các thông tin (endpoint của RDS, tên đã tạo vd: admin, nhập mật khẩu đã tạo trong RDS)

```js
    mysql --version
    mysql -h mysql–instance1.123456789012.us-east-1.rds.amazonaws.com -P 3306 -u mymasteruser -p
```
![ImageVPC](/images/3-RDS/3-Connect/RDS-Connect-img3.png?width=50pc)

- Tạo một database và lưu trữ nó ở trên RDS

```js
    Create database usermgt;
    USE usermgt;
    CREATE TABLE `usermgt`.`user`
    (
        `id`         INT NOT NULL auto_increment,
        `first_name` VARCHAR(45) NOT NULL,
        `last_name`  VARCHAR(45) NOT NULL,
        `email`      VARCHAR(45) NOT NULL,
        `phone`      VARCHAR(45) NOT NULL,
        `comments`   TEXT NOT NULL,
        `status`     VARCHAR(10) NOT NULL DEFAULT 'active',
        PRIMARY KEY (`id`)
    )
    engine = innodb;
    INSERT INTO `user`
                (`id`,
                `first_name`,
                `last_name`,
                `email`,
                `phone`,
                `comments`,
                `status`)
    VALUES      (NULL,
                'Amanda',
                'Nunes',
                'anunes@ufc.com',
                '012345 678910',
                'I love AWS FCJ',
                'active'),
                (NULL,
                'Alexander',
                'Volkanovski',
                'avolkanovski@ufc.com',
                '012345 678910',
                'I love AWS FCJ',
                'active'),
                (NULL,
                'Khabib',
                'Nurmagomedov',
                'knurmagomedov@ufc.com',
                '012345 678910',
                'I love AWS FCJ',
                'active'),
                (NULL,
                'Kamaru',
                'Usman',
                'kusman@ufc.com',
                '012345 678910',
                'I love AWS FCJ',
                'active'),
                (NULL,
                'Israel',
                'Adesanya',
                'iadesanya@ufc.com',
                '012345 678910',
                'I love AWS FCJ',
                'active');    
```

- Kiểm tra database đã tạo bằng lệnh sau.

```js
    SELECT * FROM user;
```
![ImageVPC](/images/3-RDS/3-Connect/RDS-Connect-img4.png?width=50pc)
