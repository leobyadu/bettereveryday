---
title: "Day 4 | Ngày thứ 4"
description: "Ngày thứ 4"
date: 2024-09-06
image: "/images/posts/20240906_thumb.png"
categories: ["Hành trình tốt hơn mỗi ngày"]
authors: ["Le Bao"]
tags: ["Code","DevOps"]
draft: false
---

Nginx là một web server mạnh mẽ và phổ biến được sử dụng làm server HTTP, reverse proxy, load balancer, và proxy email. Dưới đây là tổng hợp các lệnh Nginx cơ bản và cách sử dụng chúng:

### 1. **Lệnh quản lý dịch vụ Nginx (systemctl)**

Trên các hệ thống Linux hiện đại sử dụng `systemd`, bạn sẽ dùng `systemctl` để quản lý Nginx. Dưới đây là một số lệnh quan trọng:

- **Khởi động Nginx:**
    
    ```bash
    sudo systemctl start nginx
    ```
    
    Lệnh này sẽ khởi động Nginx trên hệ thống.
    
- **Dừng Nginx:**
    
    ```bash
    sudo systemctl stop nginx
    ```
    
    Lệnh này sẽ dừng Nginx ngay lập tức.
    
- **Khởi động lại Nginx:**
    
    ```bash
    sudo systemctl restart nginx
    ```
    
    Lệnh này sẽ dừng và khởi động lại Nginx.
    
- **Tải lại cấu hình mà không dừng dịch vụ:**
    
    ```bash
    sudo systemctl reload nginx
    ```
    
    Lệnh này chỉ tải lại file cấu hình mà không dừng dịch vụ. Thích hợp khi bạn thay đổi cấu hình.
    
- **Kiểm tra trạng thái của Nginx:**
    
    ```bash
    sudo systemctl status nginx
    ```
    
    Lệnh này sẽ hiển thị trạng thái hiện tại của Nginx.
    
- **Bật Nginx khởi động cùng hệ thống:**
    
    ```bash
    sudo systemctl enable nginx
    ```
    
    Lệnh này đảm bảo Nginx sẽ khởi động tự động khi máy chủ khởi động.
    
- **Tắt Nginx khỏi khởi động cùng hệ thống:**
    
    ```bash
    sudo systemctl disable nginx
    ```
    
    Lệnh này sẽ tắt việc khởi động Nginx tự động khi hệ thống khởi động.
    

### 2. **Lệnh quản lý cấu hình Nginx**

- **Kiểm tra cấu hình Nginx:**
    
    ```bash
    sudo nginx -t
    ```
    
    Lệnh này sẽ kiểm tra tính hợp lệ của file cấu hình Nginx. Nó rất hữu ích trước khi tải lại hoặc khởi động lại Nginx để tránh lỗi cấu hình.
    
    - **Kiểm tra cấu hình kèm theo chi tiết:**Lệnh này hiển thị toàn bộ cấu hình Nginx hiện tại, rất hữu ích để xem chi tiết cấu hình mà không cần truy cập trực tiếp vào file cấu hình.
        
        ```bash
        sudo nginx -T
        ```
        

### 3. **Lệnh khởi động Nginx thủ công**

Nếu bạn không sử dụng `systemctl`, bạn có thể sử dụng các lệnh sau để quản lý Nginx:

- **Khởi động Nginx:**
    
    ```bash
    sudo nginx
    ```
    
- **Dừng Nginx:**
    
    ```bash
    sudo nginx -s stop
    ```
    
- **Tắt Nginx một cách an toàn (dừng các tiến trình hiện tại một cách an toàn):**
    
    ```bash
    sudo nginx -s quit
    ```
    
- **Tải lại cấu hình Nginx:**
    
    ```bash
    sudo nginx -s reload
    ```
    

### 4. **Các file cấu hình Nginx chính**

- **Cấu hình chính của Nginx:**
File cấu hình chính thường nằm ở `/etc/nginx/nginx.conf`. Đây là file điều khiển mọi hoạt động của Nginx.
- **Cấu hình trang web (server block):**
Các file cấu hình trang web thường nằm trong thư mục `/etc/nginx/sites-available/` và `/etc/nginx/sites-enabled/`. Để kích hoạt một trang web, bạn cần tạo một symlink từ `sites-available` sang `sites-enabled`:
    
    ```bash
    sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/
    ```
    
- **Kiểm tra và sửa lỗi cấu hình Nginx:**
Sau khi chỉnh sửa file cấu hình, bạn nên chạy lệnh kiểm tra:
    
    ```bash
    sudo nginx -t
    ```
    

### 5. **Lệnh khác liên quan đến Nginx**

- **Xem phiên bản Nginx:**
    
    ```bash
    nginx -v
    ```
    
    Hiển thị phiên bản hiện tại của Nginx.
    
- **Xem phiên bản kèm chi tiết cấu hình:**
    
    ```bash
    nginx -V
    ```
    
    Lệnh này sẽ hiển thị phiên bản và các thông tin liên quan đến cấu hình biên dịch của Nginx.
    
- **Xem các tiến trình của Nginx:**
    
    ```bash
    ps aux | grep nginx
    ```
    
    Lệnh này sẽ liệt kê các tiến trình đang chạy của Nginx trên hệ thống.
    

### 6. **Các tùy chọn cấu hình phổ biến trong `nginx.conf`**

- **Cấu hình số lượng worker process:**
    
    ```
    worker_processes auto;
    ```
    
    Tùy chọn này xác định số lượng tiến trình worker của Nginx. Sử dụng `auto` để Nginx tự động quyết định dựa trên số lượng CPU của hệ thống.
    
- **Cấu hình lưu log:**
    
    ```
    access_log /var/log/nginx/access.log;
    error_log /var/log/nginx/error.log;
    ```
    
    Đây là nơi các bản ghi truy cập và lỗi sẽ được lưu trữ.
    
- **Cấu hình tối ưu kết nối keep-alive:**
    
    ```
    keepalive_timeout 65;
    ```
    
    Tùy chọn này xác định thời gian chờ của các kết nối keep-alive (kết nối được giữ sống sau khi phản hồi xong).