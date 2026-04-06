# Quy tắc dòng trống cuối file

Mỗi file code nên có một dòng trống ở cuối file vì:
- Giúp các công cụ quản lý mã nguồn (như Git) hoạt động chính xác hơn, tránh lỗi khi so sánh (diff) giữa các phiên bản.
- Một số trình biên dịch hoặc công cụ kiểm tra mã nguồn sẽ cảnh báo nếu thiếu dòng trống cuối file.
- Đảm bảo tính nhất quán và chuyên nghiệp trong codebase.

<br />
<img alt="Lỗi thiếu dòng trống cuối file" src="../../assets/style/error_last_line.png" style="max-height: 400px; width: auto;">

## Cách cấu hình Android Studio tự động thêm dòng trống cuối file

Bạn có thể cấu hình Android Studio để tự động thêm dòng trống ở cuối mỗi file khi lưu:

1. Mở **Preferences** (hoặc **Settings** trên Windows/Linux).
2. Vào mục **Editor** → **General**.
3. Tìm và bật tùy chọn **Ensure every saved file ends with a line break** (Đảm bảo mỗi file được lưu đều kết thúc bằng một dòng trống).

<br />
<img alt="Cài đặt tự động thêm dòng trống cuối file" src="../../assets/style/setting_end_file_line_break.png" style="max-height: 500px; width: auto;">

---

## Lưu ý bổ sung

- Quy tắc này áp dụng cho tất cả các loại file: Java, Kotlin, XML, Markdown, v.v.
- Nếu bạn dùng các IDE khác (VSCode, IntelliJ, v.v.), hãy tìm các tùy chọn tương tự hoặc cài đặt extension hỗ trợ.
- Đảm bảo kiểm tra lại trước khi commit/push code.

---

## Tại sao lại cần thiết?

- **Tránh lỗi merge:** Khi thiếu dòng trống, Git có thể nhận diện sự thay đổi không cần thiết ở cuối file.
- **Đồng nhất codebase:** Giúp code của team luôn sạch sẽ, chuyên nghiệp.
- **Tương thích với nhiều công cụ:** Một số công cụ CI/CD hoặc linter sẽ báo lỗi nếu thiếu dòng trống cuối file.

==> Luôn đảm bảo mỗi file code kết thúc bằng một dòng trống để tránh lỗi không đáng có và giữ cho codebase chuyên nghiệp!
