+++
title = "Clear Resources"
date = 2024
weight = 8
chapter = false
pre = "<b>8. </b>"
+++



#### Clear ECR

- Delete the previously created images.

![ImageVPC](/images/8-ClearResources/Clear-ECR-img1.png?width=50pc)

- Delete the repository.

![ImageVPC](/images/8-ClearResources/Clear-ECR-img2.png?width=50pc)

#### Clear RDS

- Delete the DB instance first.

![ImageVPC](/images/8-ClearResources/Clear-RDS-img1.png?width=50pc)

- Check the option shown in the image to completely remove the instance (this process takes around 10–15 minutes).

![ImageVPC](/images/8-ClearResources/Clear-RDS-img2.png?width=50pc)

- Once the deletion is complete, you can then proceed to delete the subnet group.

![ImageVPC](/images/8-ClearResources/Clear-RDS-img3.png?width=50pc)

#### Clear EC2 instance

- Delete all three EC2 instances that were created.

![ImageVPC](/images/8-ClearResources/Clear-ECS-img1.png?width=50pc)

#### Clear VPC

- Delete the VPC that was created.

![ImageVPC](/images/8-ClearResources/Clear-VPC-img1.png?width=50pc)

{{% notice note %}}
Make sure to double-check that all resources have been successfully deleted to complete the cleanup process.
{{% /notice %}}