# 👤 GIAO DIỆN NGƯỜI DÙNG (DÀNH CHO USER - ĐÃ ĐĂNG NHẬP)

Khi người dùng đăng nhập thành công, giao diện chính sẽ thay đổi các thành phần tương tác tại Header để phù hợp với việc quản lý tài khoản cá nhân.

---

## 🏗️ 1. HEADER (CẬP NHẬT)

Các thành phần tĩnh và thanh tìm kiếm giữ nguyên. Riêng nút **"Tham gia ngay"** được thay thế bằng:

### **🔸 Icon Người dùng & Dropdown Menu**
Khi nhấn vào Icon sẽ hiển thị menu thả xuống với các lựa chọn:
* **Hồ sơ cá nhân:** Quản lý thông tin tài khoản.
* **Danh mục sự kiện:** Xem danh sách sự kiện đã tham gia.
* **Lịch sử giao dịch:** Xem lại các lệnh đã đặt.
* **Cài đặt giao dịch:** Thiết lập thông số hỗ trợ.
* **Thông báo:** Các tin nhắn hệ thống.
* **Chuyển tiền:** Nạp/Rút tiền vào hệ thống.
* **Đăng xuất:** Thoát khỏi phiên làm việc.

---

## 📄 2. CHI TIẾT CÁC TRANG CHỨC NĂNG

### **A. Hồ sơ cá nhân (Personal Profile)**
Trang hiển thị thông tin chi tiết của người dùng:
* **Email:** Hiển thị mặc định (Không thể chỉnh sửa).
* **Mật khẩu:** Có chức năng chỉnh sửa/thay đổi.
* **Số dư tài khoản:** Hiển thị tổng số tiền hiện có.
* **Thông tin ngân hàng:** Bao gồm Tên ngân hàng, Số tài khoản, Tên chủ tài khoản (Cho phép chỉnh sửa).

### **B. Lịch sử giao dịch (Transaction History)**
Hiển thị danh sách tất cả giao dịch đã tham gia theo thứ tự ưu tiên:
1.  **Sắp xếp:** Các lệnh **"Đang chờ kết quả"** hiển thị trên đầu. Tiếp theo là các lệnh đã kết thúc theo thời gian từ mới nhất đến cũ nhất.
2.  **Thông tin hiển thị:**
    * Tên sự kiện.
    * Lựa chọn (Yes/No).
    * Số tiền đã đặt.
    * Thời gian đặt lệnh.
    * Trạng thái: `Đang chờ kết quả` / `Đã thắng` / `Đã thua`.

### **C. Cài đặt giao dịch (Trading Settings)**
Trang cấu hình các thông số hỗ trợ người dùng:
* **Tính năng:** Cài đặt **Stoploss** (Cắt lỗ) và **Take Profit** (Chốt lời).
* **Cơ chế:** Hệ thống không tự động xử lý lệnh mà sẽ **gửi thông báo về Gmail** khi đạt ngưỡng cài đặt ( cảnh báo thuần túy, người dùng tự quyết định)
* **Phạm vi:** Có thể cài đặt riêng cho từng sự kiện cụ thể hoặc cài đặt chung cho tất cả sự kiện.

### **D. Chuyển tiền (Money Transfer)**
Gồm hai phân hệ chính (Phục vụ mục đích Demo):

#### **1. Nạp tiền:**
* Hiển thị thông tin chuyển khoản: Mã QR Code, Số tài khoản, Tên tài khoản, Ngân hàng.
* Chức năng: Người dùng tải ảnh xác nhận giao dịch (Bill) từ máy tính lên hệ thống.
* *Lưu ý: Chỉ cần upload ảnh thành công là hệ thống ghi nhận (Demo).*

#### **2. Rút tiền:**
* Người dùng nhập số tiền muốn rút.
* Hiển thị Pop-up xác nhận và lưu ý: phí hệ thống tự động lấy 0.025% số tiền rút. Sau khi đồng ý, hệ thống gửi yêu cầu rút tiền thành công.
* Nếu số dư không đủ: Hiển thị thông báo lỗi "Số dư không đủ để rút tiền."
### **E. Đăng xuất (Logout)**
* Khi nhấn sẽ hiện Pop-up xác nhận: "Bạn có chắc chắn muốn đăng xuất?".
* Nếu đồng ý: Hệ thống xóa phiên đăng nhập và quay về giao diện **Guest** (Khách).

### **F. Danh mục sự kiện (Event List)**
* Hiển thị danh sách các sự kiện mà người dùng đã tham gia ( bao gồm cả đóng vị thế sớm)
* Mỗi sự kiện có thể nhấn vào để xem trang giao dịch của sự kiện đó.
* Nếu chưa tham gia sự kiện nào, hiển thị thông báo: "Bạn chưa tham gia sự kiện nào."
* Có nút đóng vị thế sớm (nếu sự kiện đang diễn ra) để người dùng có thể rút tiền trước khi kết thúc sự kiện, ẩn nút này nếu sự kiện đã kết thúc hoặc sự kiện đang chờ chốt kết quả.

### **G. Thông báo (Notifications)**
* Hiển thị các thông báo liên quan đến tài khoản và giao dịch của người dùng.
* Các thông báo có thể bao gồm: cập nhật kết quả sự kiện đã tham gia, kết thúc thời gian sự kiện, nhắc nhở cài đặt giao dịch - hồ sơ cá nhân ( nếu tạo tài khoản lần đầu).
---