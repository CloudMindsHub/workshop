+++
title = "Giới thiệu"
date = 2025
weight = 1
chapter = false
pre = "<b>1. </b>"
+++


Trong phần này, chúng ta sẽ cùng tìm hiểu ba phương pháp chính để cá nhân hóa và tối ưu hóa mô hình ngôn ngữ Amazon Nova:

- **Fine‑tuning**: Huấn luyện lại trên tập dữ liệu có nhãn chuyên biệt cho một nhiệm vụ cụ thể.

- **Distillation**: Chưng cất kiến thức từ mô hình lớn (teacher) sang mô hình nhỏ (student).

- **Continued Pre‑training**: Tiếp tục huấn luyện mô hình trên tập dữ liệu không nhãn có quy mô lớn, tập trung vào một lĩnh vực chuyên ngành trước khi fine‑tuning.

Mỗi phương pháp đều có đặc điểm riêng biệt và phù hợp với các yêu cầu ứng dụng khác nhau trong thực tiễn.


### Amazon Bedrock

![Fine-tuning illustration](/images/1-introduce/amazon-bedrock.jpeg)

Để thực hiện các phương pháp tùy chỉnh như **Fine-tuning**, **Distillation**, và **Continued Pre-training** một cách nhanh chóng và hiệu quả, **Amazon Bedrock** chính là dịch vụ lý tưởng.

Amazon Bedrock là nền tảng mạnh mẽ cho phép bạn xây dựng và triển khai các ứng dụng AI tạo sinh (generative AI) mà **không cần phải quản lý cơ sở hạ tầng phức tạp**. Với Bedrock, bạn có thể dễ dàng truy cập vào nhiều mô hình ngôn ngữ lớn (LLMs) hàng đầu từ các nhà cung cấp nổi tiếng như AI21 Labs, Anthropic, Cohere, Meta, Stability AI, và Amazon, đồng thời thực hiện **fine-tuning** trực tiếp trên dữ liệu riêng của mình.

Thông qua Bedrock, việc cá nhân hóa mô hình trở nên cực kỳ đơn giản:
- Không cần tự xây dựng hạ tầng GPU tốn kém.
- Hỗ trợ tùy chỉnh mô hình bằng dữ liệu nội bộ chỉ với vài bước cấu hình.
- Đảm bảo tính bảo mật cao, khi dữ liệu huấn luyện và dữ liệu inference đều được bảo vệ trên AWS.
- Dễ dàng tích hợp vào các ứng dụng hiện có thông qua API đơn giản và mạnh mẽ.

Nhờ đó, **Amazon Bedrock** giúp rút ngắn thời gian phát triển, giảm chi phí vận hành và tăng tính linh hoạt khi triển khai các giải pháp AI chuyên biệt theo nhu cầu thực tế của từng doanh nghiệp.


#### Fine-tuning

**Khái niệm:**
Fine-tuning là quá trình huấn luyện lại một mô hình ngôn ngữ đã được pre-trained trên một tập dữ liệu chuyên biệt có nhãn. Quá trình này điều chỉnh các tham số của mô hình để tối ưu hóa hiệu suất cho một tác vụ hoặc miền cụ thể, giúp mô hình thích nghi với ngữ cảnh và đặc thù của lĩnh vực ứng dụng.

**Ưu điểm:**
- Cải thiện hiệu suất đáng kể trên các tác vụ chuyên biệt so với mô hình gốc
- Tiết kiệm tài nguyên tính toán vì không cần huấn luyện lại từ đầu
- Yêu cầu ít dữ liệu hơn so với pre-training (thường chỉ vài nghìn đến vài trăm nghìn mẫu)
- Thời gian huấn luyện ngắn hơn, từ vài giờ đến vài ngày tùy quy mô mô hình
- Linh hoạt trong việc điều chỉnh cho nhiều tác vụ khác nhau

**Nhược điểm:**
- Nguy cơ overfitting cao nếu tập dữ liệu quá nhỏ hoặc thiếu đa dạng
- Catastrophic forgetting: có thể làm mất đi kiến thức tổng quát của mô hình gốc
- Mất cân bằng trong hiệu suất giữa các tác vụ khác nhau

**Use case thực tế:**
1. Chatbot chăm sóc khách hàng: Fine-tune để hiểu chính sách, sản phẩm và phong cách giao tiếp của doanh nghiệp, tăng độ chính xác trong trả lời theo quy trình nội bộ.
2. Hệ thống phân loại văn bản chuyên ngành: Như phân loại email spam theo đặc thù của tổ chức, hoặc phân loại tài liệu luật pháp theo các danh mục cụ thể.
3. Y tế: Fine-tune mô hình để nhận dạng thực thể y tế (Medical NER) trong hồ sơ bệnh án, giúp trích xuất thông tin bệnh lý, thuốc và chẩn đoán chính xác hơn.

#### Distillation

**Khái niệm:**
Distillation (chưng cất mô hình) là kỹ thuật chuyển giao tri thức từ một mô hình lớn, phức tạp (teacher model) sang một mô hình nhỏ, nhẹ hơn (student model). Phương pháp này sử dụng output phân phối xác suất từ mô hình teacher để huấn luyện mô hình student, giúp mô hình nhỏ hơn có thể bắt chước khả năng của mô hình lớn.

**Ưu điểm:**
- Giảm đáng kể kích thước mô hình (có thể giảm 50-90% tham số)
- Tăng tốc độ suy luận (inference) và giảm độ trễ (latency)
- Giảm yêu cầu bộ nhớ và năng lượng khi triển khai
- Bảo tồn phần lớn khả năng của mô hình gốc trong một kiến trúc nhỏ gọn hơn
- Cho phép triển khai trên thiết bị có tài nguyên hạn chế như điện thoại, thiết bị IoT

**Nhược điểm:**
- Giảm hiệu suất so với mô hình teacher gốc, đặc biệt trên các tác vụ phức tạp
- Yêu cầu quy trình huấn luyện phức tạp hơn, cần tối ưu nhiều hyperparameter
- Cần cân bằng giữa kích thước và hiệu suất để đạt kết quả tối ưu
- Phụ thuộc vào chất lượng của mô hình teacher và dữ liệu chuyển giao

**Use case thực tế:**
1. Trợ lý ảo trên thiết bị di động: Tạo phiên bản nhẹ của mô hình chat để chạy trực tiếp trên smartphone, giảm độ trễ và bảo vệ quyền riêng tư.
2. Hệ thống nhà thông minh: Triển khai mô hình nhỏ gọn trên các thiết bị IoT để xử lý ngôn ngữ tự nhiên và ra quyết định mà không cần kết nối cloud.

#### Continued Pre-training

**Khái niệm:**
Continued Pre-training (tiếp tục tiền huấn luyện) là quá trình huấn luyện tiếp một mô hình ngôn ngữ lớn đã được pre-trained trên một tập dữ liệu mới, không có nhãn, thường chuyên biệt cho một lĩnh vực. Phương pháp này giúp mô hình hấp thụ thêm kiến thức chuyên ngành trước khi thực hiện fine-tuning cho các tác vụ cụ thể.

**Ưu điểm:**
- Mở rộng kiến thức chuyên ngành của mô hình về lĩnh vực cụ thể
- Cải thiện đáng kể hiệu suất khi kết hợp với fine-tuning sau đó
- Tăng khả năng tổng quát hóa (generalization) khi xử lý dữ liệu mới
- Giảm thiểu vấn đề catastrophic forgetting so với chỉ fine-tuning
- Hiệu quả đặc biệt cho các lĩnh vực chuyên sâu như y tế, luật, tài chính

**Nhược điểm:**
- Đòi hỏi tài nguyên tính toán lớn, thường cần GPU/TPU mạnh và thời gian dài
- Yêu cầu tập dữ liệu lớn và chất lượng từ lĩnh vực mục tiêu
- Quy trình huấn luyện phức tạp, khó tối ưu hóa và theo dõi
- Có nguy cơ bias từ dữ liệu huấn luyện nếu không được lọc kỹ
- Chi phí cao cho cả dữ liệu và tài nguyên tính toán

**Use case thực tế:**
1. Y tế: Tiếp tục pre-train mô hình trên kho dữ liệu y khoa (hàng triệu bài báo PUBMED, hồ sơ bệnh án) trước khi fine-tune cho chẩn đoán, tư vấn điều trị.
2. Tài chính: Huấn luyện trên báo cáo tài chính, tin tức kinh tế và dữ liệu thị trường trước khi fine-tune cho phân tích đầu tư, dự báo thị trường.
3. Pháp lý: Pre-train liên tục trên văn bản luật, án lệ và tài liệu pháp lý trước khi fine-tune cho hệ thống hỗ trợ soạn thảo, phân tích hợp đồng.
4. Nghiên cứu khoa học: Tiếp tục huấn luyện trên corpus bài báo khoa học ngành cụ thể trước khi fine-tune cho hệ thống trích xuất thông tin, tổng hợp nghiên cứu.

### So sánh các kỹ thuật tùy chỉnh mô hình

| Tiêu chí | Fine-tuning | Distillation | Continued Pre-training |
|---------|------------|-------------|-------------------------|
| **Loại dữ liệu đầu vào** | Có nhãn, theo tác vụ | Có nhãn và dự đoán từ mô hình teacher | Không nhãn, theo miền/lĩnh vực |
| **Khối lượng dữ liệu cần thiết** | Từ vài nghìn đến vài trăm nghìn mẫu | Vừa phải, phụ thuộc vào tác vụ | Lớn (hàng triệu văn bản) |
| **Thời gian huấn luyện** | Vài giờ đến vài ngày | Trung bình | Vài ngày đến vài tuần |
| **Mục tiêu chính** | Tối ưu hóa cho tác vụ cụ thể | Giảm kích thước, tăng tốc suy luận | Bổ sung kiến thức chuyên ngành |
| **Yêu cầu tài nguyên tính toán** | Trung bình | Thấp đến trung bình | Rất cao |
| **Độ phức tạp triển khai** | Đơn giản | Trung bình | Phức tạp |
| **Khả năng mở rộng** | Giới hạn ở tác vụ được huấn luyện | Tốt cho triển khai quy mô lớn | Linh hoạt cho nhiều tác vụ sau đó |
| **Nguy cơ overfitting** | Cao nếu ít dữ liệu | Thấp đến trung bình | Thấp |
| **Ảnh hưởng đến kiến thức ban đầu** | Có thể làm mất kiến thức tổng quát | Duy trì được phần lớn | Mở rộng và bổ sung |
| **Chi phí vận hành** | Thấp đến trung bình | Rất thấp | Cao |
| **Thích hợp cho** | Tác vụ cụ thể, dữ liệu có nhãn sẵn có | Môi trường giới hạn tài nguyên | Các lĩnh vực đặc thù, phức tạp |
| **Phương pháp đánh giá** | Metrics cụ thể của tác vụ | So sánh với mô hình teacher | Perplexity và đánh giá downstream |


Mỗi phương pháp tùy chỉnh mô hình Amazon Nova đều có vai trò riêng trong việc thích nghi mô hình ngôn ngữ lớn vào các ứng dụng thực tế:

- **Fine-tuning**: Lựa chọn tối ưu khi cần mô hình phản hồi chính xác cho một tác vụ cụ thể, đặc biệt khi có sẵn dữ liệu có nhãn chất lượng.
- **Distillation**: Giải pháp hiệu quả khi cần triển khai mô hình trên các thiết bị có tài nguyên hạn chế, ưu tiên tốc độ phản hồi và hiệu quả chi phí.
- **Continued Pre-training**: Hướng đi phù hợp khi cần mô hình thấu hiểu sâu sắc về một lĩnh vực chuyên môn cụ thể, đặc biệt trong các ngành như y tế, luật pháp hay tài chính.

Việc lựa chọn và kết hợp các phương pháp này cần căn cứ vào yêu cầu cụ thể về hiệu suất, tài nguyên sẵn có và đặc thù ứng dụng.

{{% notice info %}}
Vì **Distillation** trên AWS Bedrock đang ở tình trạng preview, **Continued Pre-training** thì quá phức tạp và tốn chi phí cao, các bài toán thực tế ở các doanh nghiệp, **Fine-tuning** là một sự lụa chọn phổ biến hơn. Sau khi đã sử dụng và đánh giá thử mô hình Nova Lite, chúng tôi nhận ra Nova Lite chưa hoạt động tốt trên bài toán hỏi đáp dựa trên hình ảnh tiếng việt. Do đó, trong phạm vi workshop này, chúng tôi sẽ fine-tuning lại dựa trên bộ dữ liệu hỏi đáp trên hình ảnh tiếng việt.
{{% /notice %}}