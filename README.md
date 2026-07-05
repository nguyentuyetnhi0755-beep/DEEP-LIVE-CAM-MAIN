# 🎭 Deep-Live-Cam

<p align="center">
  <b>Real-Time Face Swapping Tool using AI | Ứng dụng hoán đổi khuôn mặt thời gian thực với AI</b>
</p>

---

## 🌟 Giới thiệu (Overview)

**Deep-Live-Cam** là ứng dụng hoán đổi khuôn mặt (Face Swap) và tạo video Deepfake thời gian thực mạnh mẽ. Chỉ với một hình ảnh duy nhất và một cú nhấp chuột, bạn có thể hoán đổi khuôn mặt trực tiếp trên Webcam hoặc video.
---

## ✨ Tính năng nổi bật (Features)

- 📸 **Hoán đổi chỉ với 1 ảnh:** Dễ dàng thay đổi khuôn mặt trong thời gian thực chỉ với duy nhất một ảnh đầu vào.
- 🎥 **Hỗ trợ Webcam & Video Live:** Tích hợp trực tiếp với webcam máy tính để livestream hoặc thực hiện cuộc gọi video.
- ⚡ **Tối ưu hóa phần cứng:** Hỗ trợ tăng tốc xử lý qua GPU NVIDIA (CUDA), AMD (DirectML) hoặc CPU.
- 👄 **Mouth Mask & Face Mapping:** Giữ nguyên chuyển động khuôn miệng tự nhiên và hỗ trợ hoán đổi nhiều khuôn mặt cùng lúc.
- 🎯 **Giao diện thân thiện:** Giao diện đồ họa (GUI) đơn giản, dễ thao tác và điều chỉnh tham số.

---

## 🚀 Hướng dẫn Cài đặt (Installation)

### 1. Yêu cầu hệ thống (Prerequisites)
- **Python:** 3.10 hoặc 3.11 (khuyên dùng Python 3.10 / 3.11).
- **Git** & **Pip**.
- **FFmpeg:** Đã được cài đặt và thêm vào biến môi trường PATH của hệ thống.
- **Visual Studio 2022 C++ Runtimes** (dành cho Windows).

### 2. Tải mô hình AI (Models Setup)
Bạn cần tải các file mô hình AI cần thiết và đặt vào thư mục `models/` của dự án:
1. **GFPGANv1.4:** Tải file `GFPGANv1.4.pth` (hoặc `.onnx`) đặt vào thư mục `models/`.
2. **Inswapper:** Tải file `inswapper_128.onnx` (hoặc `inswapper_128_fp16.onnx`) đặt vào thư mục `models/`.

### 3. Khởi tạo môi trường & Cài đặt thư viện
Mở Terminal/PowerShell tại thư mục dự án và chạy các lệnh sau:

```bash
# Tạo và kích hoạt môi trường ảo venv
python -m venv venv

# Trên Windows:
venv\Scripts\activate

# Trên Linux/macOS:
# source venv/bin/activate

# Cài đặt các thư viện phụ thuộc
pip install -r requirements.txt
```

---

## 💻 Hướng dẫn Sử dụng (Usage)

Sau khi cài đặt xong thư viện và chuẩn bị đầy đủ các file mô hình trong thư mục `models/`, bạn có thể khởi chạy ứng dụng:

### 1. Chạy trên CPU (Mặc định)
```bash
python run.py
```

### 2. Tăng tốc bằng GPU NVIDIA (CUDA)
Dành cho máy tính có card đồ họa NVIDIA:
```bash
# Cài đặt onnxruntime-gpu nếu chưa có
pip uninstall onnxruntime onnxruntime-gpu
pip install onnxruntime-gpu==1.21.0

# Khởi chạy ứng dụng với CUDA
python run.py --execution-provider cuda
```
*Hoặc trên Windows, bạn có thể chạy trực tiếp file `run-cuda.bat`.*

### 3. Tăng tốc bằng GPU AMD / Intel (DirectML)
Dành cho card đồ họa AMD hoặc Intel trên Windows:
```bash
python run.py --execution-provider directml
```
*Hoặc trên Windows, bạn có thể chạy trực tiếp file `run-directml.bat`.*

---

## ⚠️ Tuyên bố miễn trừ trách nhiệm (Disclaimer)

- **Sử dụng hợp pháp & đạo đức:** Phần mềm này được phát triển cho mục đích học tập, nghiên cứu và sáng tạo nội dung nghệ thuật hợp pháp.
- **Tôn trọng quyền riêng tư:** Nếu sử dụng khuôn mặt của người khác, hãy đảm bảo đã nhận được sự đồng ý của họ và dán nhãn minh bạch rằng đây là sản phẩm công nghệ AI / Deepfake.
- **Nghiêm cấm hành vi xấu:** Không sử dụng công cụ này vào các mục đích lừa đảo, mạo danh, tạo nội dung khiêu dâm hoặc xâm phạm danh dự, uy tín của cá nhân/tổ chức khác.

---
<p align="center">
</p>
