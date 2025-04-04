+++
title = "Giới thiệu"
date = 2025
weight = 1
chapter = false
pre = "<b>1. </b>"
+++



### Khái Niệm

Trong phần này, chúng tôi giới thiệu các khái niệm và kỹ thuật chính được sử dụng để tùy chỉnh mô hình Amazon Nova, bao gồm **Fine-tuning**, **Distillation**, và **Continued Pre-training**. Mỗi phương pháp đều có ưu điểm và phù hợp với các yêu cầu cụ thể khác nhau.

#### Fine-tuning

**Khái niệm:**
Fine-tuning là quá trình huấn luyện thêm một mô hình ngôn ngữ đã được huấn luyện trước đó (pre-trained) trên một tập dữ liệu nhỏ hơn, chuyên biệt cho một tác vụ cụ thể. Điều này giúp mô hình hiểu rõ hơn về ngữ cảnh cụ thể của lĩnh vực ứng dụng.

**Hình minh họa:**
![Fine-tuning illustration](/images/fine-tune-example.png)

**Ưu điểm:**
- Cải thiện hiệu suất trên các tác vụ chuyên biệt
- Không cần nhiều dữ liệu như huấn luyện từ đầu
- Nhanh chóng và tiết kiệm chi phí

**Nhược điểm:**
- Dễ bị overfitting nếu dữ liệu quá ít
- Có thể làm mất đi kiến thức tổng quát của mô hình (catastrophic forgetting)

**Use case thực tế:**
1. Chatbot chăm sóc khách hàng được fine-tune trên dữ liệu hội thoại nội bộ của công ty để trả lời chính xác hơn.
2. Hệ thống phân loại email spam được tinh chỉnh với dữ liệu từ tổ chức cụ thể để tăng độ chính xác.
3. Ứng dụng nhận dạng thực thể trong văn bản y tế (Medical NER) được fine-tune từ mô hình gốc để xử lý hồ sơ bệnh án.

#### Distillation

**Khái niệm:**
Distillation (chưng cất mô hình) là kỹ thuật chuyển giao tri thức từ một mô hình lớn, phức tạp (teacher) sang một mô hình nhỏ, nhẹ hơn (student), giúp giảm kích thước và tăng tốc độ suy luận.

**Hình minh họa:**
![Distillation illustration](/images/distillation-example.png)

**Ưu điểm:**
- Giảm kích thước mô hình và độ trễ
- Dễ triển khai trên thiết bị có tài nguyên hạn chế (mobile, edge)

**Nhược điểm:**
- Có thể giảm hiệu suất so với mô hình gốc
- Cần thêm một bước huấn luyện phụ

**Use case thực tế:**
1. Tạo phiên bản nhẹ của mô hình chatbot để triển khai trên thiết bị IoT trong nhà thông minh.
2. Rút gọn mô hình phân tích cảm xúc để tích hợp vào hệ thống hỗ trợ khách hàng trên ứng dụng di động.
3. Triển khai phiên bản student của mô hình kiểm tra đạo văn cho các trường đại học có tài nguyên hạn chế.

#### Continued Pre-training

**Khái niệm:**
Continued pre-training là quá trình huấn luyện tiếp tục một mô hình ngôn ngữ đã được huấn luyện trước đó trên một tập dữ liệu lớn không có nhãn, chuyên biệt theo lĩnh vực trước khi thực hiện fine-tuning.

**Hình minh họa:**
![Continued Pre-training illustration](/images/continued-pretraining.png)

**Ưu điểm:**
- Giúp mô hình hấp thụ thêm kiến thức chuyên ngành
- Cải thiện khả năng tổng quát hoá khi fine-tune

**Nhược điểm:**
- Tốn nhiều tài nguyên tính toán
- Yêu cầu tập dữ liệu lớn và phù hợp với lĩnh vực

**Use case thực tế:**
1. Tiền huấn luyện mô hình với hàng triệu bài báo khoa học trước khi fine-tune cho hệ thống trích xuất thông tin học thuật.
2. Sử dụng dữ liệu từ các diễn đàn công nghệ để tiếp tục huấn luyện mô hình, sau đó tinh chỉnh cho trợ lý kỹ thuật.
3. Huấn luyện tiếp mô hình trên tập tin tài chính doanh nghiệp để cải thiện hệ thống phân tích báo cáo tài chính.

### So sánh các kỹ thuật tùy chỉnh mô hình

| Tiêu chí                     | Fine-tuning                           | Distillation                            | Continued Pre-training                     |
|-----------------------------|----------------------------------------|------------------------------------------|--------------------------------------------|
| **Dữ liệu đầu vào**         | Có nhãn                                | Có nhãn và mô hình teacher               | Không nhãn                                  |
| **Mục tiêu chính**          | Tùy chỉnh mô hình theo tác vụ cụ thể  | Nén mô hình, tăng tốc suy luận          | Mở rộng kiến thức chuyên ngành              |
| **Yêu cầu tài nguyên**      | Trung bình                             | Thấp                                     | Cao                                         |
| **Khả năng triển khai**     | Dễ triển khai với mô hình có sẵn       | Phù hợp thiết bị giới hạn tài nguyên     | Yêu cầu pipeline huấn luyện phức tạp hơn    |
| **Độ phức tạp**             | Vừa phải                                | Thấp đến trung bình                      | Cao                                         |
| **Nguy cơ overfitting**     | Cao nếu ít dữ liệu                     | Thấp                                     | Thấp                                        |
| **Ưu điểm nổi bật**         | Cá nhân hóa mạnh mẽ cho tác vụ cụ thể | Nhẹ, nhanh, dễ triển khai                | Học sâu hơn theo lĩnh vực, tăng khả năng generalization |
| **Nhược điểm**              | Có thể làm mất kiến thức tổng quát    | Hiệu suất kém hơn mô hình gốc            | Tốn tài nguyên, cần dữ liệu lớn             |
| **Ví dụ ứng dụng**          | Chatbot doanh nghiệp, phân loại văn bản | Ứng dụng mobile, IoT, hệ thống nhúng    | Trích xuất thông tin chuyên ngành, phân tích tài chính |

### Tổng kết

Trong phần giới thiệu này, chúng tôi đã làm rõ ba phương pháp chính để tùy chỉnh mô hình Amazon Nova: **Fine-tuning**, **Distillation** và **Continued Pre-training**. Mỗi phương pháp có những điểm mạnh, điểm yếu và yêu cầu khác nhau, phục vụ những mục tiêu triển khai cụ thể:

- Nếu cần mô hình phản hồi chính xác cho một tác vụ cụ thể, **Fine-tuning** là lựa chọn tối ưu.
- Nếu cần triển khai trên thiết bị tài nguyên thấp, **Distillation** là giải pháp phù hợp.
- Khi cần mô hình hiểu sâu hơn về ngữ cảnh ngành nghề, **Continued Pre-training** là hướng đi hiệu quả.

{{% notice note %}}
Trong các phần tiếp theo, chúng tôi sẽ trình bày chi tiết cách áp dụng từng kỹ thuật vào quy trình huấn luyện mô hình Nova, cùng các công cụ và kiến trúc hỗ trợ.
{{% /notice %}}