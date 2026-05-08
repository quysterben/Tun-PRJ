
# ĐỀ BÀI: HỆ THỐNG QUẢN LÝ SÀN THƯƠNG MẠI ĐIỆN TỬ ĐA CẤP (MULTIVENDOR E-COMMERCE)

## 1. Giới thiệu
Xây dựng một nền tảng Web cho phép nhiều cửa hàng đăng ký kinh doanh, người mua có thể tìm kiếm sản phẩm và Quản trị viên (Super Admin) kiểm soát toàn bộ hoạt động của hệ thống.

## 2. Yêu cầu công nghệ
*   **Backend:** ExpressJS, Sequelize ORM (Service Pattern).
*   **Database:** MySQL.
*   **Frontend:** ReactJS (Material UI hoặc Tailwind CSS).
*   **Authentication:** JWT (JSON Web Token) & Bcrypt.

---

## 3. Phân quyền và Tính năng yêu cầu

### A. Vai trò: Người mua (Customer)
*   **Tài khoản:** Đăng ký, đăng nhập và cập nhật hồ sơ cá nhân.
*   **Mua sắm:** 
    *   Xem danh sách sản phẩm (có phân trang).
    *   Tìm kiếm sản phẩm theo tên và lọc theo danh mục.
    *   Xem chi tiết sản phẩm và các đánh giá.
*   **Giỏ hàng:** Thêm, sửa số lượng, xóa sản phẩm khỏi giỏ hàng.
*   **Đơn hàng:** Đặt hàng và theo dõi lịch sử đơn hàng cá nhân.

### B. Vai trò: Cửa hàng (Vendor/Store)
*   **Quản lý Shop:** Cập nhật thông tin cửa hàng (Tên, địa chỉ, hotline).
*   **Quản lý Sản phẩm:** 
    *   Thêm mới sản phẩm (Tên, giá, số lượng tồn kho, hình ảnh).
    *   Chỉnh sửa thông tin hoặc ẩn sản phẩm khi hết hàng.
*   **Quản lý Đơn hàng:** 
    *   Tiếp nhận đơn hàng mới từ khách.
    *   Cập nhật trạng thái vận chuyển (Chờ xác nhận -> Đang giao -> Đã giao).
*   **Báo cáo:** Thống kê doanh thu theo tháng của cửa hàng.

### C. Vai trò: Quản trị viên hệ thống (Super Admin)
*   **Danh mục:** Quản lý cây danh mục toàn hệ thống (Điện tử, Gia dụng, Thời trang...).
*   **Kiểm soát:** Phê duyệt yêu cầu mở gian hàng hoặc khóa các gian hàng vi phạm.
*   **Người dùng:** Xem danh sách toàn bộ người dùng và lịch sử hoạt động.
*   **Tổng quan:** Xem báo cáo tổng doanh thu và biểu đồ tăng trưởng toàn sàn.

---

## 4. Chi tiết kỹ thuật (Implementation Details)

### Backend (BE)
*   **Cấu trúc thư mục:** Áp dụng **Service Layer** (Controller -> Service -> Model).
*   **Database:** 
    *   Sử dụng **Migration** để quản lý cấu trúc bảng (Users, Stores, Products, Orders, Categories).
    *   Sử dụng **Seeder** để tạo dữ liệu mẫu.
*   **Logging:** 
    *   Ghi lại toàn bộ HTTP requests bằng `Morgan`.
    *   Ghi lại lỗi hệ thống vào file `logs/error.log` bằng `Winston`.

### Frontend (FE)
*   **Quản lý State:** Sử dụng  `Redux` để quản lý.
*   **Phân quyền Route:** 
    *   Public Routes: Trang chủ, Chi tiết sản phẩm.
    *   Private Routes: Dashboard cho Store và Admin (Yêu cầu Token).
*   **Giao diện:** 
    *   Sử dụng Component-based architecture.
    *   Đảm bảo UI sạch sẽ, chuyên nghiệp, hỗ trợ Responsive (Mobile/Desktop).
