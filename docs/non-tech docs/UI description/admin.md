# 🛠️ GIAO DIỆN QUẢN TRỊ (ADMIN DASHBOARD)

Giao diện dành cho Admin và đội ngũ phát triển được thiết kế theo phong cách **Tối giản (Minimalist)**, loại bỏ các thành phần thừa để tập trung hoàn toàn vào việc quản lý hệ thống.

---

## 🏗️ 1. CẤU TRÚC CHUNG (LAYOUT)
* **Header/Footer:** Loại bỏ hoàn toàn để tối ưu không gian làm việc.
* **Body:** Trang trung tâm chứa các lối tắt quản lý chính:
    * [Quản lý sự kiện](#)
    * [Quản lý nạp tiền](#)

---

## 📋 2. CHI TIẾT CÁC PHÂN HỆ QUẢN TRỊ

### **A. Quản lý sự kiện (Event Management)**
Trang này cho phép Admin điều phối các thị trường dự đoán trên hệ thống, admin được một list sự kiện hiện có kèm icon tạo sự kiện hay chốt kết quả sự kiện, không có chức năng chỉnh sửa hay xóa sự kiện đã tạo.

#### **Danh sách sự kiện:**
* Hiển thị tất cả các sự kiện hiện có trong hệ thống.
* Trạng thái (Đang diễn ra/Đã kết thúc/Chờ chốt kết quả).

#### **Tạo sự kiện mới:**
Khi nhấn nút **"Tạo sự kiện mới"**, một Form nhập liệu sẽ xuất hiện với các trường:
* **Tên sự kiện:** Câu hỏi Yes/No cho người dùng.
* **Mô tả sự kiện:** Chi tiết quy tắc hoặc thông tin liên quan.
* **Thời gian kết thúc:** Thời điểm đóng pool và dừng giao dịch.
* **Thanh khoản tham chiếu:** Số tiền khởi tạo từ phía Developer để tạo Pool ban đầu cho cả hai phe Yes và No ( ví dụ: Dev bỏ 50 Yes + 50 No = $100 vào pool, HOẶC 100 Yes + 50 No = $150 vào pool với kèo lệch ).
* **Thao tác:** Nhấn "Tạo" để đưa sự kiện lên giao diện chính của người dùng.

### **Chốt kết quả sự kiện:**
* Khi sự kiện kết thúc, Admin sẽ có quyền chốt kết quả bằng cách chọn **YES** hoặc **NO**.
* Hệ thống sẽ tự động phân phối tiền thưởng cho người chơi dựa trên kết quả đã chốt.
* Admin có thể xem lại kết quả và thống kê sau khi chốt để đảm bảo tính minh bạch.

---

### **B. Quản lý nạp tiền (Deposit Management)**
Hệ thống xử lý phê duyệt thủ công các giao dịch nạp tiền để đảm bảo tính xác thực trong bản Demo.

#### **Danh sách chờ xác nhận:**
Hiển thị danh sách các yêu cầu nạp tiền từ người dùng theo bảng:
| Email User | Ảnh xác nhận (Bill) | Thời gian nạp | Thao tác |
| :--- | :--- | :--- | :--- |
| user@gmail.com | [Xem ảnh] | 20/04/2026 14:30 | **Nút Xác nhận** |

* **Logic xử lý:** Khi Admin nhấn nút **"Xác nhận"**, hệ thống sẽ tự động cộng số tiền ảo tương ứng vào tài khoản của User ( số tiền do admin nhập vào popup xác nhận ) và chuyển yêu cầu này từ trạng thái "Chờ xác nhận" sang "Đã xác nhận".
* **Lưu ý:** Cần pop-up để xác nhận và nhập số tiền tương ứng với yêu cầu nạp tiền, sau khi xác nhận thì hệ thống sẽ tự động cộng tiền vào tài khoản user.
---

### **C. Cơ chế rút tiền (Withdrawal - Demo Logic)**
Nhằm tối giản quy trình cho bản Demo, cơ chế rút tiền được thiết lập như sau:
* **Tự động hóa:** Khi User thực hiện lệnh rút tiền, hệ thống sẽ tự động trừ số dư trong tài khoản User.
* **Phê duyệt:** Admin **không cần thực hiện thao tác xác nhận**. Yêu cầu rút tiền được coi là thành công ngay lập tức trên hệ thống.

---

## 🎨 TIÊU CHUẨN THIẾT KẾ (DESIGN PHILOSOPHY)
* **Tối giản:** Sử dụng các bảng (table) và danh sách (list) phẳng.
* **Tốc độ:** Ưu tiên tải dữ liệu nhanh, không sử dụng hiệu ứng chuyển cảnh phức tạp.
* **Tiện lợi:** Các nút chức năng quan trọng (Xác nhận, Tạo mới) được đặt tại vị trí dễ quan sát nhất.