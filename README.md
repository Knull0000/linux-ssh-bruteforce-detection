# SSH Brute Force Detection

## Giới thiệu

Dự án cá nhân nhằm phát hiện hành vi tấn công dò mật khẩu SSH (SSH Brute Force)  
thông qua việc phân tích log xác thực trên hệ thống Linux.

---

## Môi trường

- Hệ điều hành: Linux (Ubuntu)
- Attacker: Kali Linux
- Dịch vụ: SSH
- Tool tấn công: Hydra
- Nguồn log: /var/log/auth.log
- Môi trường thực hiện: Lab mô phỏng (Personal Lab)

### Network

- Attacker IP: 192.168.233.130  
- Target IP: 192.168.233.26  

---

## Phát hiện

Trong quá trình phân tích log phát hiện:

- Nhiều lần đăng nhập SSH thất bại
- Dấu hiệu: `Failed password`
- Tài khoản bị tấn công: user1
- IP nguồn: 192.168.233.130

Ví dụ log:

```
Failed password for user1 from 192.168.233.130 port 51432 ssh2
```

---

## Phân tích

Các đặc điểm cho thấy đây là hành vi SSH Brute Force:

- Các lần đăng nhập thất bại xảy ra liên tục trong thời gian ngắn
- Cùng một địa chỉ IP thực hiện nhiều lần thử mật khẩu
- Nhắm vào cùng một tài khoản người dùng

Hành vi này phù hợp với pattern của **SSH Brute Force Attack**.

---

## Hướng xử lý & khuyến nghị

Một số biện pháp giảm thiểu:

- Chặn địa chỉ IP có hành vi đăng nhập bất thường
- Triển khai **Fail2Ban** để tự động block IP
- Sử dụng **SSH key authentication** thay vì password
- Giới hạn số lần login thất bại

---

## Mục tiêu học tập

Thông qua project này có thể hiểu:

- Cách hoạt động của brute force attack
- Cách phân tích log trên hệ thống Linux
- Cách phát hiện dấu hiệu tấn công SSH
- Các phương pháp phòng chống brute force

---

## Lưu ý

Project chỉ phục vụ **mục đích học tập và nghiên cứu trong môi trường lab**.
Không sử dụng các kỹ thuật này để tấn công hệ thống thực tế.
