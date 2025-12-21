# Linux SSH Brute Force Detection (SOC Project)

## Giới thiệu
Dự án cá nhân nhằm phát hiện hành vi tấn công dò mật khẩu SSH (SSH Brute Force)
thông qua việc phân tích log xác thực trên hệ thống Linux.

## Môi trường
- Hệ điều hành: Linux (Ubuntu)
- Dịch vụ: SSH
- Nguồn log: /var/log/auth.log
- Môi trường thực hiện: Lab mô phỏng (Personal Lab)

## Phát hiện
- Ghi nhận nhiều lần đăng nhập SSH thất bại
- Dấu hiệu: `Failed password`
- Tài khoản bị tấn công: user1
- IP nguồn: 127.0.0.1

## Phân tích
- Các lần đăng nhập thất bại xảy ra liên tục trong thời gian ngắn
- Cùng một tài khoản và địa chỉ IP
- Mẫu hành vi phù hợp với tấn công SSH Brute Force

## Hướng xử lý & khuyến nghị
- Chặn địa chỉ IP có hành vi đăng nhập bất thường
- Triển khai Fail2Ban
- Sử dụng xác thực SSH bằng key
