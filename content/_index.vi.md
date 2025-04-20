+++
title = "Customizing Amazon Nova models"
date = 2025
weight = 1
chapter = false
+++

# Fine-tuning Amazon Nova models trên AWS Bedrock

### Tổng quan
Trong những năm gần đây, trí tuệ nhân tạo (AI) đã trở thành một công cụ mạnh mẽ, được ứng dụng rộng rãi trong nhiều lĩnh vực như y tế, giáo dục, kinh doanh, và công nghệ. Tuy nhiên, để AI thật sự hiểu và giải quyết tốt một vấn đề cụ thể, chúng ta thường cần "dạy lại" nó bằng dữ liệu riêng của mình. Việc này gọi là fine-tuning, hay còn gọi là tinh chỉnh mô hình. Nói đơn giản, đây là cách giúp một mô hình AI đã được huấn luyện sẵn trở nên phù hợp hơn với nhu cầu và dữ liệu của từng cá nhân hoặc tổ chức. Thay vì phải xây dựng một mô hình từ đầu – vừa tốn thời gian, công sức và chi phí – thì fine-tuning giúp ta tận dụng sức mạnh có sẵn, rồi điều chỉnh lại để AI hoạt động hiệu quả hơn trong bối cảnh thực tế của mình. Đây là một bước quan trọng giúp đưa AI vào ứng dụng thật, sát với nhu cầu sử dụng hàng ngày.

-----> giới thiệu bedrock

### Kiến trúc

Quá trình fine-tuning một mô hình AI thường trải qua các bước sau:
![Architecture](https://www.solulab.com/wp-content/uploads/2024/12/Fine-Tuning-Process.jpg)

### Nội dung chính

1. [Giới thiệu](1-introduce/)
2. [Chuẩn bị dữ liệu](2-dataset)
3. [Huấn luyện tinh chỉnh mô hình](3-train)
4. [Đánh giá mô hình](4-evaluation)
5. [Clean up resources](5-clean)