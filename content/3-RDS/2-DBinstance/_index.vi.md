+++
title = "Tạo DB instance"
date = 2024
weight = 2
chapter = false
pre = "<b>3.2. </b>"
+++



#### Các bước tạo DB instance (RDS)

- Truy cập và phần database trong RDS và ấn Create database

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img1.png?width=50pc)

- Chọn MySQL để lưu trữ dữ liệu.

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img2.png?width=50pc)

- Chọn template Free tier vì đây chỉ là môi trường thử nghiệm.

{{% notice note %}}
Bởi vì ta chỉ sài Free tier nên bị hạn chế khá nhiều thứ như: Giới hạn về kích thước cơ sở dữ liệu, hạn chế về loại instance, tính năng giới hạn, giới hạn về số lượng cơ sở dữ liệu, chỉ có một số loại database được hỗ trợ, không có hỗ trợ kỹ thuật, hạn chế về hiệu suất và thời gian sử dụng có giới hạn.
{{% /notice %}}

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img3.png?width=50pc)

- Nhập định danh: **`fcj-management-db-instance`**
- Username: `admin`
- Password: `123Vodanhphai`

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img4.png?width=50pc)

- Chọn cấu hình mặc định

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img5.png?width=50pc)

- Chọn VPC và Subnet group đã tạo từ trước

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img6.png?width=50pc)

- Chọn Security group đã tạo cho DB

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img7.png?width=50pc)

- Kiểm tra và ấn tạo

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img8.png?width=50pc)

- Quá trình tạo sẽ mất khoảng 10-15 phút để đợi RDS được tạo hoàn tất

![ImageVPC](/images/3-RDS/2-RDS/RDS-Instance-img9.png?width=50pc)