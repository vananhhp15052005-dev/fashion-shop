# Xây dựng hệ thống bán quần áo Fashion Shop

## Nhóm sinh viên thực hiện

## 👨‍💻 Thành viên thực hiện

| STT | Họ và tên | MSSV | Lớp | Công việc thực hiện |
|:---:|---|:---:|:---:|---|
| 1 | Huỳnh Chí Đạt | 110123086 | DA23TTB | - Quản lý sản phẩm và danh mục sản phẩm (thêm, sửa, xóa, xem).<br>- Quản lý nhập hàng và tồn kho.<br>- Xây dựng dashboard thống kê.<br>- Xây dựng giao diện trang chủ.<br>- Xây dựng giao diện thông tin khách hàng (thông tin cơ bản, lịch sử mua hàng). |
| 2 | Huỳnh Phan Vân Anh | 110123065 | DA23TTB | - Phân tích và thiết kế cơ sở dữ liệu.<br>- Xây dựng mô hình thực thể kết hợp (ERD).<br>- Xây dựng chức năng đăng nhập, đăng ký và đăng xuất.<br>- Quản lý tài khoản và phân quyền người dùng.<br>- Xây dựng giao diện đăng ký, đăng nhập.<br>- Xây dựng giao diện sản phẩm theo danh mục và tìm kiếm sản phẩm. |
| 3 | Châu Tuyết Trân | 110123189 | DA23TTA | - Xây dựng chức năng giỏ hàng.<br>- Xây dựng chức năng đặt hàng.<br>- Quản lý và theo dõi đơn hàng.<br>- Xây dựng chức năng thanh toán.<br>- Xây dựng giao diện giỏ hàng và trang đặt hàng. |

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
