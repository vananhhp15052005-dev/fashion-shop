# Xây dựng hệ thống bán quần áo Fashion Shop

## Nhóm sinh viên thực hiện

- **Họ và tên:** Huỳnh Chí Đạt - **MSSV:** 110123086 - **DA23TTB**
- Xây dựng chức năng quản lý sản phẩm và danh mục sản phẩm (thêm, sửa, xóa, xem).
- Xây dựng chức năng nhập hàng và quản lý tồn kho.
- Xây dựng dashboard thống kê.
- Xây dựng giao diện trang chủ.
- Xây dựng giao diện trang thông tin khách hàng (Thông tin cơ bản, lịch sử mua hàng)

- **Họ và tên:** Huỳnh Phan Vân Anh - **MSSV:** 110123065 - **DA23TTB**
- Phân tích và thiết kế cơ sở dữ liệu
- Mô hình thực thể kết hợp. 
- Xây dựng chức năng đặp nhập, đăng ký và đăng xuất.
- Xây dựng chức năng quản lý tài khoản và phân quyền người dùng.
- Xây dựng giao diện đăng ký, đăng nhập.
- Xây dựng giao diện trang sản phẩm theo danh mục và tìm kiếm sản phẩm.

- **Họ và tên:** Châu Tuyết Trân - **MSSV:** 110123189 - **DA23TTA**
- Xây dựng chức năng giỏ hàng.
- Xây dựng chức năng đặt hàng.
- Xây dựng chức năng quản lý và theo dõi đơn hàng.
- Xây dựng chức năng thanh toán.
- Xây dựng giao diện giỏ hàng và trang đặt hàng.

## Công nghệ sử dụng

| Công nghệ      | Mô tả                           |
| -------------- | ------------------------------- |
| PHP            | Ngôn ngữ lập trình phía máy chủ |
| CodeIgniter    | Framework phát triển ứng dụng   |
| MySQL          | Hệ quản trị cơ sở dữ liệu       |
| Apache         | Web Server                      |
| Docker         | Đóng gói và triển khai ứng dụng |
| Docker Compose | Quản lý các container           |

## Cài đặt và chạy dự án

### Bước 1: Clone repository

```bash
git clone https://github.com/vananhhp15052005-dev/fashion-shop
```

Di chuyển vào thư mục dự án:

```bash
cd fashion-Shop
```

### Bước 2: Cấu hình môi trường

Tạo file `.env` từ file mẫu:

```bash
cp .env.example .env
```

Cập nhật thông tin kết nối database theo cấu hình Docker Compose.

### Bước 3: Khởi động Docker

Build và chạy các container:

```bash
docker compose up -d --build
```

Kiểm tra trạng thái container:

```bash
docker compose ps
```

### Bước 4: Truy cập website

Mở trình duyệt và truy cập:

```text
http://localhost:8080
```

*Lưu ý: Cổng truy cập phụ thuộc vào cấu hình ports trong docker-compose.yml.*

## Cấu hình môi trường

### Database

Thông tin kết nối MySQL trong file `.env`:

```ini
database.default.hostname = db
database.default.database = fashion_shop
database.default.username = user
database.default.password = password
database.default.DBDriver = MySQLi
database.default.port = 3306
```

### Docker Compose

Các thông tin cấu hình database:

```yaml
db:
  image: mysql:8.0
  environment:
    TZ: Asia/Ho_Chi_Minh
    MYSQL_ROOT_PASSWORD: root
    MYSQL_DATABASE: fashion_shop
    MYSQL_USER: user
    MYSQL_PASSWORD: password
  volumes:
    - mysql_data:/var/lib/mysql
```

**Lưu ý:** Không commit file `.env` chứa thông tin cấu hình hoặc mật khẩu thực tế lên GitHub. Hãy sử dụng `.env.example` để cung cấp cấu hình mẫu.

## Cấu trúc thư mục

```text
Fashion-Shop/
├── app/                  # Mã nguồn ứng dụng
├── public/               # Thư mục public, chứa index.php và assets
├── writable/             # Cache, logs, sessions
├── tests/                # Các file kiểm thử
├── docker/
│   └── Dockerfile        # Cấu hình xây dựng Docker image
├── docker-compose.yml    # Cấu hình các dịch vụ Docker
├── .env.example          # File cấu hình môi trường mẫu
├── composer.json         # Quản lý thư viện PHP
└── README.md             # Tài liệu dự án
```
