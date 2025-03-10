+++
title = "Giới thiệu"
date = 2024
weight = 1
chapter = false
pre = "<b>1. </b>"
+++



#### Bối cảnh

Công ty có một ứng dụng web gồm 2 container:

- **Web container**: Chạy ứng dụng web chính.
- **Database container**: Chứa cơ sở dữ liệu MySQL.

Công ty quyết định sử dụng Docker Swarm để triển khai các container này trên 3 máy chủ EC2 nhỏ trên AWS. Swarm giúp họ:

- **Tự động cân bằng tải** giữa các máy chủ để tránh tình trạng quá tải cho một node cụ thể.
- **Tự động khởi động lại** các container khi có lỗi.

Docker Swarm là giải pháp lý tưởng cho các công ty nhỏ hoặc các dự án không yêu cầu điều phối phức tạp, nơi mà Kubernetes hoặc ECS có thể trở nên thừa thãi và khó quản lý. Docker Swarm cung cấp đủ tính năng để tự động hóa và quản lý container một cách hiệu quả, đồng thời dễ sử dụng và tích hợp tốt với Docker.

#### Docker là gì?

**Docker** là một nền tảng mã nguồn mở cho phép bạn tự động hóa việc triển khai, quản lý, và chạy ứng dụng bên trong các containers. Docker giúp đơn giản hóa quá trình phát triển và triển khai bằng cách đảm bảo rằng ứng dụng của bạn sẽ chạy nhất quán trong mọi môi trường.

#### Docker Compose là gì?

**Docker Compose** là một công cụ giúp định nghĩa và chạy các ứng dụng Docker multi-container. Thay vì phải chạy các lệnh Docker riêng lẻ cho từng container, Docker Compose cho phép bạn quản lý tất cả các container liên quan trong một ứng dụng bằng cách sử dụng một tập tin cấu hình duy nhất.

#### Tại sao nên sử dụng Docker Swarm?

**Docker Swarm** là một công cụ điều phối container (container orchestration) được tích hợp sẵn trong Docker. Nó cho phép bạn triển khai và quản lý các container trên một hoặc nhiều máy chủ (nodes) dưới dạng một cụm (cluster). Docker Swarm giúp bạn dễ dàng điều khiển cách các container được triển khai, cân bằng tải, và quản lý tài nguyên trong cụm.

Nó một lựa chọn phù hợp cho các dự án vừa và nhỏ, nơi tính đơn giản và dễ dàng triển khai là ưu tiên hàng đầu.

Tuy Docker Swarm không được tích hợp với các dịch vụ để quản lý ở trên AWS như ECS hay EKS nhưng ta vẫn có thể thiết lập và quản lý một cụm Docker Swarm trên một vài tài nguyên của AWS như EC2 instances.

Điều này đặc biệt giúp những người đã quen dùng Docker hơn ECS quản lý các container dễ dàng hơn, ngay cả khi nó đang dùng trên AWS.

![Architecture](/images/1-Introduce/Introduce-img.jpeg?width=50pc)
