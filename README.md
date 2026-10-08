# Bài 4: Cấu hình Reverse Proxy Nginx cho ứng dụng Spring Boot

## 1. Quá trình cấu hình

### Tạo trang index.html
```bash
sudo mkdir -p /var/www/html/
echo "<h1>Dao Trong Tri - PTIT062</h1>" | sudo tee /var/www/html/index.html
```

### Kích hoạt cấu hình Nginx
```bash
# Tạo symlink
sudo ln -s /etc/nginx/sites-available/spring-proxy.conf /etc/nginx/sites-enabled/

# Reload Nginx sau khi test thành công
sudo systemctl reload nginx
```

## 2. Kết quả kiểm tra

### Kiểm tra cú pháp Nginx
Kết quả lệnh `sudo nginx -t`:
```text
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```
*(Chụp ảnh màn hình terminal)*

### Truy xuất trang tĩnh
Kết quả lệnh `curl -I http://localhost/` hoặc `curl http://localhost/`:
*(Chụp ảnh màn hình terminal trả về 200 OK và thông tin học viên)*

### Truy xuất backend Spring Boot
Kết quả lệnh `curl -I http://localhost/api/health` hoặc truy cập qua web:
*(Chụp ảnh màn hình hiển thị trạng thái kết nối thành công, không bị lỗi 502)*
