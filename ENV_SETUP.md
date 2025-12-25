# Hướng dẫn cấu hình môi trường

## Backend (mmssystem)

1. Copy file `.env.example` thành `.env`:
   ```bash
   cd mmssystem
   cp .env.example .env
   ```

2. Chỉnh sửa file `.env` với thông tin của bạn:
   - `DATABASE_*`: Thông tin kết nối MySQL
   - `JWT_SECRET`: Secret key cho JWT (tối thiểu 256 bits)
   - `MAIL_*`: Thông tin Gmail SMTP (cần bật App Password)

## Frontend (MMS-FE)

File `.env` đã có sẵn với cấu hình mặc định:
```bash
VITE_API_BASE_URL=http://localhost:8080/api
VITE_ENV=development
```

## Lưu ý quan trọng

- ⚠️ **KHÔNG commit file `.env`** lên Git (đã được ignore)
- ✅ Chỉ commit file `.env.example` để team khác tham khảo
- 🔐 Thay đổi `JWT_SECRET` và các thông tin nhạy cảm trong production
- 📧 Để sử dụng email, cần tạo [App Password](https://myaccount.google.com/apppasswords) cho Gmail
