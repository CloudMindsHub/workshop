+++
title = "Create DB instance"
date = 2024
weight = 2
chapter = false
pre = "<b>3.2. </b>"
+++



#### Steps to Create a DB Instance (RDS)

- Access the Databases section in RDS and click Create Database.

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img1.png?width=50pc)

- Select MySQL for data storage.

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img2.png?width=50pc)

- Choose the Free Tier template since this is just a test environment.

{{% notice note %}}
Since we are using the Free Tier, there are many limitations such as: restrictions on database size, instance type limitations, limited features, restrictions on the number of databases, support for only certain database types, no technical support, performance limitations, and a limited usage period.
{{% /notice %}}

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img3.png?width=50pc)

- Enter the identifier: **`fcj-management-db-instance`**
- Username: `admin`
- Password: `123Vodanhphai`

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img4.png?width=50pc)

- Choose the default configuration.

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img5.png?width=50pc)

- Select the VPC and Subnet Group created earlier.

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img6.png?width=50pc)

- Choose the Security Group created for the DB.

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img7.png?width=50pc)

- Review and click Create.

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img8.png?width=50pc)

- The creation process will take about 10-15 minutes to complete the RDS setup.

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img9.png?width=50pc)