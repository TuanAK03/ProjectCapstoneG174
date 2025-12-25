# MMS - Material Management System

> Hệ thống quản lý vật tư toàn diện cho doanh nghiệp

## 📋 Giới thiệu

Material Management System (MMS) là hệ thống quản lý vật tư, hàng hóa, mua hàng, bán hàng và kho bãi tích hợp. Dự án được xây dựng với kiến trúc Full-stack hiện đại, phục vụ cho việc quản lý toàn bộ quy trình nghiệp vụ của doanh nghiệp.

### ✨ Tính năng chính

- 🔐 **Quản lý người dùng & Phân quyền**: Hệ thống xác thực JWT, phân quyền RBAC chi tiết
- 📦 **Quản lý sản phẩm**: Quản lý danh mục, sản phẩm, đơn vị tính
- 🛒 **Quản lý mua hàng**: Yêu cầu mua hàng, RFQ, báo giá nhà cung cấp, đơn đặt hàng
- 💰 **Quản lý bán hàng**: Báo giá, đơn hàng bán, hóa đơn, trả hàng
- 📊 **Quản lý công nợ**: Theo dõi công nợ khách hàng/nhà cung cấp theo thời gian
- 🏭 **Quản lý kho**: Nhập kho, xuất kho, tồn kho theo thời gian thực
- 📈 **Báo cáo & Thống kê**: Báo cáo tồn kho, doanh thu, biểu đồ dashboard
- 📄 **Xuất file Excel & PDF**: Xuất báo cáo, hóa đơn dưới nhiều định dạng
- 🔔 **Thông báo**: Hệ thống thông báo real-time cho các sự kiện quan trọng
- 📜 **Nhật ký hoạt động**: Ghi lại toàn bộ hành động của người dùng

## 🛠️ Công nghệ sử dụng

### Frontend
- **Framework**: React 19.1.1
- **Build Tool**: Vite 7.x
- **Styling**: Tailwind CSS 4.x + Ant Design 5.x
- **State Management**: Zustand
- **Routing**: React Router DOM 7.x
- **Form Handling**: React Hook Form
- **HTTP Client**: Axios
- **Icons**: FontAwesome, Lucide React
- **Date Handling**: date-fns, dayjs, React Datepicker
- **Export**: ExcelJS, html2pdf.js
- **Notifications**: React Toastify

### Backend
- **Framework**: Spring Boot 3.4.3
- **Java Version**: 21
- **Database**: MySQL 8.x
- **ORM**: Spring Data JPA (Hibernate)
- **Security**: Spring Security + JWT
- **Build Tool**: Maven
- **Development**: Spring DevTools

## 📁 Cấu trúc dự án

```
G174---MMS/
├── MMS-FE/                    # Frontend React Application
│   ├── src/
│   │   ├── api/              # API Services
│   │   ├── assets/           # Static assets
│   │   ├── compnents/        # React Components
│   │   │   ├── common/       # Common components (Pagination, etc.)
│   │   │   ├── layout/       # Layout components (Header, Sidebar)
│   │   │   └── pages/        # Page components
│   │   ├── hooks/            # Custom React Hooks
│   │   ├── store/            # Zustand stores
│   │   └── utils/            # Utility functions
│   ├── package.json
│   └── vite.config.js
│
├── mmssystem/                # Backend Spring Boot Application
│   ├── src/
│   │   └── main/
│   │       ├── java/
│   │       │   └── com/g174/mmssystem/
│   │       │       ├── config/       # Configuration classes
│   │       │       ├── controller/   # REST Controllers
│   │       │       ├── dto/          # Data Transfer Objects
│   │       │       ├── entity/       # JPA Entities
│   │       │       ├── repository/   # Data Repositories
│   │       │       ├── service/      # Business Logic
│   │       │       └── exception/    # Exception Handling
│   │       └── resources/
│   │           └── application.properties
│   ├── pom.xml
│   └── sql_scripts/          # Database scripts
│
└── uploads/                   # File upload directory
    ├── invoices/
    └── products/
```

## 🚀 Hướng dẫn cài đặt

### Yêu cầu hệ thống

- **Node.js**: ≥ 22.12.0 (khuyến nghị v24.x)
- **npm**: ≥ 11.x
- **Java**: JDK 21
- **MySQL**: ≥ 8.0
- **Maven**: 3.6+

### 1. Clone repository

```bash
git clone https://github.com/TuanAK03/ProjectCapstoneG174.git
cd G174---MMS
```

### 2. Cài đặt Database

```bash
# Tạo database
mysql -u root -p
CREATE DATABASE mms_database;

# Import database schema và data
mysql -u root -p mms_database < mmssystem/sql_scripts/Database
mysql -u root -p mms_database < mmssystem/sql_scripts/data
```

### 3. Cấu hình Backend

Chỉnh sửa file `mmssystem/src/main/resources/application.properties`:

```properties
# Database Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/mms_database?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=Asia/Ho_Chi_Minh
spring.datasource.username=root
spring.datasource.password=YOUR_PASSWORD

# JWT Configuration
jwt.secret=YOUR_SECRET_KEY_HERE_MAKE_IT_AT_LEAST_256_BITS_LONG
jwt.expiration=86400000
jwt.refresh-expiration=604800000
```

### 4. Cài đặt và chạy Backend

```bash
cd mmssystem

# Build project
mvn clean install

# Run application
mvn spring-boot:run
```

Backend sẽ chạy tại: `http://localhost:8080`

### 5. Cài đặt và chạy Frontend

```bash
cd MMS-FE

# Cài đặt dependencies
npm install

# Run development server
npm run dev
```

Frontend sẽ chạy tại: `http://localhost:5173`

## 📝 Hướng dẫn sử dụng

### Đăng nhập

1. Truy cập `http://localhost:5173`
2. Đăng nhập với tài khoản mặc định (xem trong database)
3. Hệ thống sẽ redirect về Dashboard

### Các module chính

- **Dashboard**: Tổng quan về hoạt động kinh doanh
- **Products**: Quản lý sản phẩm và danh mục
- **Purchase**: Quy trình mua hàng (PR → RFQ → PO)
- **Sales**: Quy trình bán hàng (Quotation → Order → Invoice)
- **Warehouse**: Quản lý kho hàng, nhập xuất tồn
- **Debt Management**: Theo dõi công nợ
- **Reports**: Báo cáo và thống kê
- **Admin**: Quản lý người dùng, phân quyền

## 🔧 Scripts có sẵn

### Frontend

```bash
npm run dev      # Chạy development server
npm run build    # Build production
npm run preview  # Preview production build
npm run lint     # Chạy ESLint
```

### Backend

```bash
mvn clean install       # Build project
mvn spring-boot:run    # Run application
mvn test               # Run tests
```

## 📚 API Documentation

API endpoint: `http://localhost:8080/api`

### Authentication
- `POST /api/auth/login` - Đăng nhập
- `POST /api/auth/logout` - Đăng xuất
- `POST /api/auth/refresh` - Refresh token

### Products
- `GET /api/products` - Lấy danh sách sản phẩm
- `POST /api/products` - Tạo sản phẩm mới
- `PUT /api/products/{id}` - Cập nhật sản phẩm
- `DELETE /api/products/{id}` - Xóa sản phẩm

*(Xem thêm chi tiết API trong source code)*

## 🤝 Đóng góp

Dự án này là Capstone Project của nhóm G174. Mọi đóng góp và góp ý xin gửi về:

- **Repository**: [TuanAK03/ProjectCapstoneG174](https://github.com/TuanAK03/ProjectCapstoneG174)

## 📄 License

Copyright © 2025 G174 Team. All rights reserved.

## 👥 Team Members

- Lộc (locddhe176242) - Team Lead
- Tuấn (TuanAK03) - Developer
- *[Thêm thành viên khác nếu có]*

## 📞 Liên hệ

Nếu có bất kỳ câu hỏi nào, vui lòng tạo issue trên GitHub hoặc liên hệ trực tiếp với team.

---

**⚠️ Lưu ý**: Đây là dự án học tập. Không sử dụng cho mục đích thương mại khi chưa có sự cho phép.
