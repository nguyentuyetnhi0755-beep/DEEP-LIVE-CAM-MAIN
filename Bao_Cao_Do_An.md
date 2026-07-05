# ĐỒ ÁN MÔN HỌC: TRÍ TUỆ NHÂN TẠO
## TÊN ĐỀ TÀI: HỌC SÂU VÀ ỨNG DỤNG HOÁN ĐỔI KHUÔN MẶT THỜI GIAN THỰC (DEEP-LIVE-CAM)

**Thành phố Hồ Chí Minh, năm 2025**

---

## MỤC LỤC
**LỜI MỞ ĐẦU**
**CHƯƠNG 1: PHÂN TÍCH BÀI TOÁN**
  1.1 Tổng quan, mục đích bài toán
    1.1.1 Vấn đề xử lý hình ảnh và video hiện nay
    1.1.2 Thách thức của công nghệ hoán đổi khuôn mặt
    1.1.3 Giới thiệu về học sâu (Deep Learning) trong xử lý ảnh
  1.2 Mục đích bài toán
**CHƯƠNG 2: PHƯƠNG PHÁP VÀ KẾT QUẢ THỰC NGHIỆM**
  2.1 Quy trình tổng thể của hệ thống Deep-Live-Cam
  2.2 Các thuật toán và mô hình sử dụng
  2.3 Thiết lập môi trường và cấu hình suy luận
  2.4 Triển khai giao diện phần mềm (PySide6)
  2.5 Kết quả và đánh giá
**CHƯƠNG 3: TỔNG KẾT**
  3.1 Kết luận
  3.2 Đóng góp mới của đề tài
  3.3 Hạn chế của hệ thống
  3.4 Hướng phát triển trong tương lai
**TÀI LIỆU THAM KHẢO**

---

## LỜI MỞ ĐẦU
Trong những năm gần đây, sự phát triển của Trí tuệ nhân tạo (AI) và Học sâu (Deep Learning) đã tạo ra những bước nhảy vọt trong lĩnh vực Thị giác máy tính (Computer Vision). Một trong những ứng dụng nổi bật và thu hút nhiều sự chú ý nhất là công nghệ hoán đổi khuôn mặt (Face Swapping) – nền tảng của các hệ thống AI thay đổi khuôn mặt. 
Đề tài "Học sâu và ứng dụng hoán đổi khuôn mặt thời gian thực" tập trung vào việc phân tích, tinh chỉnh và triển khai hệ thống Deep-Live-Cam. Mục tiêu của đề tài là xây dựng một công cụ xử lý mạnh mẽ, có khả năng nhận diện và thay thế khuôn mặt trực tiếp trên luồng camera thời gian thực (live stream) hoặc trên video/hình ảnh có sẵn, với giao diện trực quan và tối ưu hóa tốt trên máy tính cá nhân.

---

## CHƯƠNG 1: PHÂN TÍCH BÀI TOÁN

### 1.1 Tổng quan, mục đích bài toán

#### 1.1.1 Vấn đề xử lý hình ảnh và video hiện nay
Trước đây, để thay thế khuôn mặt của một diễn viên hoặc nhân vật trong video, các studio phải sử dụng kỹ xảo điện ảnh (CGI) rất đắt đỏ, đòi hỏi hàng trăm giờ làm việc thủ công bởi các chuyên gia. Quá trình này hoàn toàn không thể thực hiện theo thời gian thực (Real-time).
Với sự xuất hiện của AI, nhu cầu tạo ra các nội dung giải trí, truyền thông, điện ảnh hoặc ẩn danh tính trong các buổi phát sóng trực tiếp ngày càng tăng cao. Người dùng cần một công cụ tự động, nhanh chóng và dễ sử dụng mà không cần kỹ năng chuyên sâu.

#### 1.1.2 Thách thức của công nghệ hoán đổi khuôn mặt
Việc hoán đổi khuôn mặt gặp phải nhiều thách thức kỹ thuật rất lớn:
- **Độ trễ (Latency):** Việc xử lý luồng video theo thời gian thực (đặc biệt là mức 30 - 60 FPS) đòi hỏi mô hình AI phải tính toán cực kỳ nhanh, nếu không sẽ xảy ra hiện tượng giật lag.
- **Tính tự nhiên (Realism):** Khuôn mặt ghép vào phải khớp chính xác với góc nghiêng, biểu cảm, ánh sáng và màu da của khuôn mặt gốc.
- **Biến dạng (Artifacts):** Ở những góc mặt nghiêng quá mức hoặc bị che khuất (bởi tay, tóc, kính, micro), mô hình rất dễ bị lỗi kết xuất làm biến dạng khung hình.

#### 1.1.3 Giới thiệu về học sâu (Deep Learning) trong nhận diện khuôn mặt
Học sâu, đặc biệt là Mạng nơ-ron tích chập (CNN) và Mạng sinh đối nghịch (GAN), đã giải quyết xuất sắc bài toán này. Các mạng CNN giúp trích xuất đặc trưng (embedding vector) chính xác của khuôn mặt nguồn. Trong khi đó, các mô hình dựa trên nền tảng mạng sinh (Generative models) giúp tổng hợp và tạo ra hình ảnh khuôn mặt mới một cách sắc nét, chân thực và hợp nhất hoàn hảo vào khung hình mục tiêu.

### 1.2 Mục đích bài toán
Đề tài nhằm mục đích:
- Nghiên cứu cơ chế hoạt động của các thuật toán nhận diện và hoán đổi khuôn mặt tân tiến nhất (InsightFace, Inswapper).
- Tối ưu hóa và thiết lập môi trường chạy ứng dụng Deep-Live-Cam trên phần cứng máy tính cá nhân (tận dụng sức mạnh xử lý song song của GPU qua CUDA/TensorRT).
- Chỉnh sửa, khắc phục lỗi hệ thống và tái thiết kế giao diện UI (Modern UI) để người dùng thông thường cũng có thể dễ dàng tiếp cận công nghệ AI này mà không cần kiến thức lập trình.

---

## CHƯƠNG 2: PHƯƠNG PHÁP VÀ KẾT QUẢ THỰC NGHIỆM

### 2.1 Quy trình tổng thể của hệ thống Deep-Live-Cam
Hệ thống hoạt động theo pipeline xử lý đa bước trên từng khung hình (frame) như sau:
1. **Trích xuất dữ liệu nguồn:** Người dùng cung cấp 1 bức ảnh khuôn mặt nguồn. Mô hình phân tích và trích xuất vector đặc trưng (Face Embedding) của khuôn mặt này.
2. **Nhận diện khuôn mặt đích:** Trên luồng video hoặc camera trực tiếp, hệ thống quét và tìm kiếm vị trí các khuôn mặt mục tiêu.
3. **Căn chỉnh (Alignment):** Sử dụng 5 điểm mốc (landmarks: hai mắt, mũi, hai mép miệng) để xoay và cắt chuẩn khuôn mặt đích (Crop & Align).
4. **Hoán đổi (Swapping):** Mô hình học sâu tổng hợp khuôn mặt mới dựa trên biểu cảm của mặt đích nhưng mang đặc điểm hình học của mặt nguồn.
5. **Hòa trộn và Khôi phục (Blending & Enhancement):** Ghép khuôn mặt mới vào thân hình cũ bằng thuật toán Poisson Blending giúp xóa mờ viền cắt. Cuối cùng, một mô hình mạng GAN sẽ đánh giá và làm nét lại các chi tiết trên khuôn mặt (tóc, mắt, răng).

### 2.2 Các thuật toán và mô hình sử dụng
Hệ thống kết hợp sự sức mạnh của nhiều thuật toán state-of-the-art:
- **Thuật toán InsightFace (RetinaFace / SCRFD):** Dùng để phát hiện khuôn mặt (Face Detection) cực kỳ chính xác và nhanh chóng trong thời gian thực.
- **Mô hình Inswapper (inswapper_128.onnx):** Mô hình hoán đổi khuôn mặt trung tâm. Dựa trên kiến trúc mã hóa - giải mã (Encoder-Decoder) để giữ lại danh tính ảnh nguồn nhưng thay đổi biểu cảm theo ảnh đích.
- **Thuật toán GFPGAN / GPEN:** Mô hình Mạng sinh đối nghịch (GAN - Generative Adversarial Network) được tích hợp để làm rõ nét, khôi phục chi tiết cho khuôn mặt bị mờ nhòe sau khi ghép.
- **Poisson Image Editing:** Thuật toán xử lý ảnh truyền thống giúp hòa trộn màu sắc, ánh sáng vùng biên giới của ảnh ghép sao cho tiệp màu với video gốc.

### 2.3 Thiết lập môi trường và cấu hình suy luận
- **Phần cứng:** Hệ thống được thử nghiệm và vận hành trên máy tính cá nhân trang bị card đồ họa (GPU) NVIDIA.
- **Môi trường:** Python 3.10, tận dụng bộ engine `onnxruntime-gpu` để tăng tốc độ suy luận mạng nơ-ron thông qua nền tảng CUDA (Compute Unified Device Architecture).
- **Khắc phục lỗi nền tảng:** Đã thiết lập cơ chế vòng tránh lỗi thư viện nhận diện nội dung cấm (OpenNSFW2 bypass), cũng như bổ sung tệp vá lỗi ngầm định (Silent Crash) của framework giao diện trên nền hệ điều hành Windows.

### 2.4 Triển khai giao diện phần mềm
- Phần mềm sử dụng framework **PySide6** (Qt for Python).
- Giao diện đã được thiết kế lại toàn diện theo phong cách **Modern Premium Dark Theme** (Nền tối #0F172A, chữ trắng, các nút Action chính được trang bị dải màu gradient nổi bật và bắt mắt).
- Tích hợp các công cụ điều khiển trực quan: Tải ảnh nguồn, chọn luồng Camera (Live), thanh trượt Tùy chỉnh độ nét (Sharpness), Độ trong suốt (Transparency).

### 2.5 Kết quả và đánh giá
**Hiệu quả triển khai thực tế:**
- Hệ thống hoạt động trơn tru, ổn định, nhận diện và thay thế khuôn mặt ngay lập tức trên luồng webcam.
- Tính năng hòa trộn màu sắc hoạt động rất tốt, khuôn mặt thay thế trông tự nhiên, khớp với môi trường ánh sáng của video gốc.
- Việc tích hợp GFPGAN giúp nâng cao chất lượng đầu ra một cách rõ rệt đối với những khung hình có độ phân giải thấp.

**Đánh giá hiệu năng:**
- Xử lý mượt mà ở mức khung hình tiêu chuẩn (25 - 30 FPS) nhờ sự hỗ trợ của GPU NVIDIA (CUDA). 
- Trên thiết bị chỉ sử dụng CPU, tốc độ xử lý giảm đáng kể, có xảy ra độ trễ (latency) khi hiển thị kết quả do giới hạn về mặt tính toán ma trận song song.

---

## CHƯƠNG 3: TỔNG KẾT

### 3.1 Kết luận
Đề tài đã triển khai thành công hệ thống Deep-Live-Cam, từ khâu xử lý thiết lập môi trường, khắc phục lỗi tương thích sâu bên trong mã nguồn, đến việc thiết kế lại hoàn toàn giao diện người dùng. Việc áp dụng các mô hình học sâu như InsightFace và Inswapper đã chứng minh được tính khả thi và hiệu quả vượt trội trong việc hoán đổi khuôn mặt thời gian thực với độ chân thực cao ngay trên thiết bị cá nhân.

### 3.2 Đóng góp mới của đề tài
- Tích hợp thành công và cấu hình mượt mà các mô hình Trí tuệ nhân tạo hạng nặng lên thiết bị máy tính phổ thông.
- Sửa lỗi thành công các sự cố ngầm định (Silent Crash) và lỗi tương thích của hệ thống trên hệ điều hành Windows.
- Tái thiết kế toàn bộ giao diện phần mềm (UI/UX) giúp ứng dụng trở nên hiện đại, bắt mắt và dễ dàng thao tác cho đối tượng người dùng không chuyên.

### 3.3 Hạn chế của hệ thống
- Còn phụ thuộc nhiều vào sức mạnh phần cứng (Đòi hỏi bắt buộc phải có Card đồ họa rời mạnh để chạy mượt mà theo thời gian thực).
- Hiện tượng "Rung lắc khuôn mặt" (Flickering) thỉnh thoảng vẫn xảy ra khi mục tiêu quay mặt ở góc nghiêng quá hẹp hoặc bị các vật thể (tay, kính, vật cản) che khuất.
- Chưa xử lý hoàn hảo việc khớp tông màu da nếu ảnh nguồn và video đích có màu da quá khác biệt ở vùng tiếp giáp (cổ, vai).

### 3.4 Hướng phát triển trong tương lai
- Áp dụng thêm các kỹ thuật làm mượt khung hình (Temporal Smoothing) dựa trên lịch sử frame trước đó để giảm thiểu triệt để hiện tượng rung lắc khuôn mặt.
- Tối ưu hóa mô hình sang định dạng lượng tử hóa (Quantization) để phần mềm có thể chạy mượt mà ngay cả trên các thiết bị chỉ sử dụng CPU.
- Cải thiện thuật toán Color Match để đồng bộ màu da từ cổ đến khuôn mặt một cách chân thực và tự động nhận diện ánh sáng môi trường tốt hơn.

---

## TÀI LIỆU THAM KHẢO
[1] Artificial Intelligence: A Modern Approach Fourth Edition Chapter 21 Deep Learning.
[2] InsightFace Project. 2D and 3D Face Analysis Project. Github.
[3] H. Li et al., "GFPGAN: Towards Real-World Blind Face Restoration with Generative Facial Prior," in CVPR, 2021.
[4] Microsoft. ONNX Runtime Documentation. (2025).
[5] H. Chen et al., "GPEN: GAN Prior Embedded Network for Blind Face Restoration", 2021.
