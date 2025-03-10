+++
title = "Connecting to the Database"
date = 2024
weight = 3
chapter = false
pre = "<b>3.3. </b>"
+++



#### Steps to Connect to the Database

- Log in as the root user and begin installing SQL:

```js
    sudo su
    yum install mariadb
```
![ImageVPC](/images/3-RDS/3-Connect/RDS-Connect-img1.png?width=50pc)

- Copy the RDS endpoint to use for the connection.

![ImageVPC](/images/3-RDS/3-Connect/RDS-Connect-img2.png?width=50pc)

- Check SQL version and connect to the database (the RDS you created). Adjust the details (RDS endpoint, user name such as admin, and the password you set in RDS):

```js
    mysql --version
    mysql -h mysql–instance1.123456789012.us-east-1.rds.amazonaws.com -P 3306 -u mymasteruser -p
```
![ImageVPC](/images/3-RDS/3-Connect/RDS-Connect-img3.png?width=50pc)

- Create a database and store it on RDS:

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

- Check the created database using the following command:

```js
    SELECT * FROM user;
```
![ImageVPC](/images/3-RDS/3-Connect/RDS-Connect-img4.png?width=50pc)
