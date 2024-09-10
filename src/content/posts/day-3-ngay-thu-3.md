---
title: "Day 3 | Ngày thứ 3"
description: "Ngày thứ 3"
date: 2024-09-04
image: "/images/posts/20240905_thumb.png"
categories: ["Hành trình tốt hơn mỗi ngày"]
authors: ["Le Bao"]
tags: ["Code","DevOps"]
draft: false
---

## Tổng hợp các lệnh GIT cần phải biết.

## 1. Cấu hình Git

Trước khi sử dụng Git, bạn cần cấu hình một số thông tin cơ bản:
```bash
git config --global user.name "Tên của bạn"
git config --global user.email "email của bạn"
```

## 2. Khởi tạo dự án mới

Để bắt đầu một dự án Git mới:
```bash
git init
```
Lệnh này sẽ khởi tạo một kho Git trống trong thư mục hiện tại.

## 3. Sao chép một dự án (Clone)

Nếu bạn muốn sao chép một dự án GitHub về máy tính của mình:
```bash
git clone URL_repository
```
Ví dụ:
```bash
git clone https://github.com/username/repo.git
```

## 4. Kiểm tra trạng thái dự án

Để kiểm tra trạng thái hiện tại của dự án (những file nào đã được thay đổi, thêm mới, hoặc chưa được thêm vào Git):
```bash
git status
```

## 5. Thêm tệp vào vùng staging

Khi bạn đã thực hiện thay đổi và muốn theo dõi chúng, sử dụng lệnh:
```bash
git add filename
```
Hoặc thêm toàn bộ thay đổi:
```bash
git add .
```

## 6. Lưu trữ thay đổi (Commit)

Sau khi thêm tệp vào vùng staging, bạn cần commit chúng để lưu lại trong lịch sử phiên bản:
```bash
git commit -m "Thông điệp commit mô tả thay đổi"
```

## 7. Đẩy thay đổi lên GitHub (Push)

Khi bạn muốn đẩy các thay đổi của mình lên kho lưu trữ trên GitHub:
```bash
git push origin branch_name
```
Ví dụ:
```bash
git push origin main
```

## 8. Kéo về thay đổi mới nhất (Pull)

Khi cần cập nhật dự án từ kho GitHub về máy tính:
```bash
git pull origin branch_name
```

## 9. Xem lịch sử commit

Để xem lịch sử các lần commit trong dự án:
```bash
git log
```

## 10. Tạo nhánh mới

Nếu bạn muốn tạo một nhánh mới để làm việc mà không ảnh hưởng đến nhánh chính:
```bash
git branch branch_name
```

## 11. Chuyển đổi giữa các nhánh

Để chuyển sang một nhánh khác:
```bash
git checkout branch_name
```

## 12. Gộp nhánh (Merge)

Sau khi làm việc trên nhánh mới, bạn muốn gộp thay đổi vào nhánh chính:
```bash
git checkout main
git merge branch_name
```

## 13. Xóa nhánh

Sau khi gộp, bạn có thể xóa nhánh:
```bash
git branch -d branch_name
```

## 14. Khôi phục tệp

Nếu bạn muốn khôi phục một tệp về trạng thái trước khi thay đổi:
```bash
git checkout -- filename
```

## 15. Xử lý xung đột

Khi gộp nhánh, có thể xảy ra xung đột nếu cùng một phần của tệp đã được thay đổi trên các nhánh khác nhau. Bạn cần chỉnh sửa thủ công các tệp bị xung đột, sau đó thêm lại vào vùng staging:
```bash
git add filename
git commit
```

## 16. Sử dụng GitHub với SSH

Để làm việc với GitHub qua SSH thay vì HTTPS, bạn cần cấu hình SSH key:
```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
Sau đó, thêm SSH key vào tài khoản GitHub và kết nối:
```bash
git remote set-url origin git@github.com:username/repository.git
```

## Hướng dẫn cơ bản sử dụng Git và GitHub

1. **Tạo repo mới trên GitHub**:
   - Vào [GitHub](https://github.com), tạo một repository mới.
   - Clone repo về máy bằng lệnh `git clone URL_repository`.
   
2. **Quản lý dự án**:
   - Sau khi thay đổi code, sử dụng `git add .` và `git commit` để lưu trữ.
   - Đẩy code lên GitHub với `git push`.

3. **Làm việc với nhánh**:
   - Tạo nhánh mới cho tính năng mới, sau đó merge nhánh khi hoàn tất.

4. **Cộng tác nhóm**:
   - Kéo thay đổi từ GitHub về bằng `git pull`, xử lý xung đột khi cần thiết.

Chỉ với các lệnh cơ bản này, bạn đã có thể sử dụng Git và GitHub một cách hiệu quả trong quản lý dự án.