+++
title = "Chuẩn bị dataset"
date = 2025
weight = 2
chapter = false
pre = "<b>2. </b>"
+++


### Tổng quan về bộ dữ liệu

- Bộ dữ liệu này là phần mở rộng của dự án Viet-Doc VAQ, được xây dựng từ 64.765 trang tài liệu giáo dục tiếng Việt 🇻🇳, bao gồm: sách bài tập, sách chuyên đề, giáo án từ các nhà xuất bản chính thống như Bộ Giáo dục & Đào tạo, Cánh Diều, Chân Trời Sáng Tạo, Kết Nối Tri Thức,... phủ rộng tất cả các môn học từ lớp 1 đến lớp 12.

- Mỗi trang tài liệu đã được xử lý và chú thích kỹ lưỡng bằng các kỹ thuật Visual Question Answering (VQA), tạo nên một bộ dữ liệu có chất lượng cao và giàu thông tin.

- Bộ dữ liệu bao gồm 388.277 cặp mô tả chi tiết và câu hỏi - trả lời theo ngữ cảnh, được tự động tạo ra bởi Gemini 1.5 Flash – mô hình AI hàng đầu của Google, đang dẫn đầu bảng xếp hạng WildVision Arena. Nhờ đó, đây là nguồn tài nguyên lý tưởng cho các mục tiêu nghiên cứu và ứng dụng giáo dục hiện đại.

- Các môn học bao gồm: Toán học 📐, Ngữ văn 📚, Tiếng Anh 🇬🇧, Vật lý ⚛️, Hóa học 🧪, Sinh học 🌱, Lịch sử 📜, Địa lý 🌍, Giáo dục công dân 🏫, Tin học 💻, Công nghệ 🛠️, Âm nhạc 🎵, Mỹ thuật 🎨, Thể dục ⚽,...

Vì chi phí có giới hạn, chỉ để thử nghiệm việc fine-tuning mô hình trên AWS Bedrock, trong workshop này chỉ dùng 100 mẫu dữ liệu để huấn luyện (số lượng mẫu tối thiểu theo yêu cầu của Bedrock ). 

![Architecture](/images/2-dataset/data-hf.png)

{{% notice tip %}}
Tải dữ liệu từ Hugging Face: https://huggingface.co/datasets/5CD-AI/Viet-Doc-VQA-II/tree/main/data
{{% /notice %}}

### Nội dung chính

1. [Xử lý dữ liệu](2.1-handle/)
2. [Upload dữ liệu](2.2-upload/)
