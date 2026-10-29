# HYBRID WORKFLOW – SỐ HÓA BẢO TÀNG PTIT

## 1\. Sơ đồ luồng dữ liệu

```text
Thiết kế 3D → Ctrl + S → Local SSD → Ứng dụng đồng bộ → Cloud
                                      |
                          Mất mạng: xếp hàng chờ
                                      |
                         Có mạng lại: tải lên Cloud
```

* Lưu Local trước; chỉ xác nhận sao lưu khi Cloud báo **Synced/Up to date**.
* Cloud lưu bản sao và Version History nếu dịch vụ, loại tệp hỗ trợ.

## 2\. Xử lý xung đột và khôi phục

**File Version Conflict:** Giữ các bản xung đột, so sánh và chọn bản ổn định nhất; không ghi đè trước khi kiểm tra.

**Khôi phục:** Dừng chỉnh sửa → mở Version History trên Cloud → chọn phiên bản ổn định trước khi lỗi → khôi phục/tải xuống → kiểm tra tệp 3D → xác nhận đồng bộ.

## 3\. Khi mất mạng hoặc sập nguồn

* **Mất mạng:** Lưu trên Local; ứng dụng giữ thay đổi trong hàng đợi và tải lên khi có mạng lại.
* **Sập nguồn:** Thay đổi chưa lưu có thể mất. Khởi động lại, kiểm tra bản Local/Cloud và xử lý xung đột.
* Không thể đồng bộ tức thời khi mất mạng. Không tắt ứng dụng khi đang tải lên; chờ xác nhận hoàn tất. Duy trì bản sao lưu độc lập cho tệp quan trọng.

## 4\. Ba bước thiết lập

1. **Cài đặt:** Cài ứng dụng Cloud chính thức, đăng nhập và bật tự khởi động.
2. **Chọn thư mục:** Đưa thư mục bản vẽ 3D vào vùng đồng bộ; kiểm tra dung lượng và quyền truy cập.
3. **Kiểm thử:** Lưu bằng `Ctrl + S`, chờ báo đồng bộ thành công, rồi kiểm tra trên Cloud/thiết bị khác. Thử mất mạng với tệp mẫu.

**Hybrid Workflow kết hợp Local, Cloud và Version History giúp giảm nguy cơ mất dữ liệu. Luôn kiểm tra trạng thái đồng bộ và giữ thêm bản sao lưu độc lập.**

