# Hướng dẫn CI/CD cho AI Agent 🚀

Thư mục này được thiết lập để minh họa cách CI/CD hoạt động trong một dự án thực tế.

## 1. CI (Continuous Integration) - Tích hợp liên tục
Chúng ta sử dụng **GitHub Actions** để tự động kiểm tra code.
- **File cấu hình:** [.github/workflows/ci.yml](.github/workflows/ci.yml)
- **Hoạt động:** Mỗi khi bạn `git push` lên GitHub, một máy chủ ảo sẽ được khởi tạo, cài đặt Python và chạy file `check_production_ready.py`.
- **Lợi ích:** Nếu file `check_production_ready.py` trả về lỗi (exit code 1), GitHub sẽ đánh dấu ❌ đỏ cho commit đó, báo hiệu cho bạn biết code chưa sẵn sàng để deploy.

## 2. CD (Continuous Deployment) - Triển khai liên tục
Chúng ta có thể tận dụng cấu hình có sẵn cho **Render** hoặc **Railway**.
- **Render:** File `render.yaml` đã có `autoDeploy: true`. Khi GitHub Action (CI) vượt qua, Render sẽ tự động kéo code mới nhất về và build Docker image để chạy.
- **Railway:** Sử dụng file `railway.toml` để tối ưu hóa quá trình deploy trên nền tảng Railway.

## 3. Cách thử nghiệm
1. Đẩy thư mục này lên một Repository GitHub mới.
2. Vào tab **Actions** trên GitHub để xem quá trình kiểm tra tự động đang diễn ra.
3. Thử sửa code làm cho `check_production_ready.py` bị lỗi (ví dụ: xóa file `Dockerfile`) và push lên để xem CI báo lỗi thế nào.

---
*Chúc bạn triển khai thành công!*
