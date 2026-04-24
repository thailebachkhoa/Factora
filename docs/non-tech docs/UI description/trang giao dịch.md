# 📈 TRANG CHI TIẾT GIAO DỊCH (EVENT TRADING PAGE)

Trang này hiển thị thông tin chi tiết về một sự kiện cụ thể và cho phép người dùng thực hiện đặt lệnh giao dịch.

---

## 🏗️ 1. HEADER & NAVIGATION
* **Header:** Giữ nguyên cấu trúc theo trạng thái (Guest hoặc User).
* **Nút quay lại:** Cung cấp link hoặc nút thao tác nhanh để trở về **Giao diện chính**.

---

## 📊 2. BODY (NỘI DUNG CHÍNH)

Phần thân trang bao gồm Thanh điều hướng ngang (Tabs) và bố cục chia làm hai phần chính (Thông tin bên trái & Khung đặt lệnh bên phải).

### **A. Các Tab Điều hướng**
1.  **Tổng quan (Mặc định):** Hiển thị chi tiết về sự kiện và bảng đặt lệnh.
2.  **Phân tích:**
    * Biểu đồ tỷ lệ Yes/No theo khung thời gian 1 phút.
    * Biểu đồ khối lượng giao dịch (Volume) theo thời gian thực.
    * *Các chỉ số phân tích khác (Đang phát triển).*
3.  **Thảo luận:**
    * Khung Chat Box thời gian thực để người dùng trao đổi về sự kiện.
    * *Tính năng hiện tại: Placeholder (Đang phát triển).*

### **B. Tab Tổng quan (Chi tiết nội dung)**

#### **Khối thông tin sự kiện (Bên trái)**
* **Tên sự kiện:** Tiêu đề câu hỏi dự đoán.
* **Mô tả:** Thông tin chi tiết, quy tắc hoặc bối cảnh của sự kiện.
* **Khối lượng giao dịch:** Tổng số tiền/lượt đã giao dịch.
* **Khả năng thắng:** Tỷ lệ % hiện tại của cả hai cửa Yes và No.
* **Thời gian còn lại:** Đồng hồ đếm ngược đến khi đóng sự kiện.

#### **Khung Đặt lệnh (Sidebar bên phải)**
Đây là nơi người dùng thực hiện thao tác tài chính:
* **Lựa chọn:** Nút chọn **Yes** hoặc **No**.
* **Số tiền:** Ô nhập số tiền (Quy ước: $1 tương ứng với 1 Share).
* **Dự toán:** Hiển thị tổng tiền nhận được nếu thắng (Tính toán dựa trên việc cộng thêm số tiền đặt vào Pool hiện tại). *Lưu ý: Cập nhập theo thời gian thực*
* **Nút Đặt lệnh:** * Sau khi nhấn, hiển thị **Pop-up thông báo thành công**.
    * Pop-up có nút dẫn nhanh đến trang **Lịch sử giao dịch**.

> 💡 **Tính năng cho User đã tham gia:**
> Nếu người dùng đã sở hữu cổ phần trong sự kiện này, một khung nhỏ sẽ hiện ra bên dưới khung đặt lệnh:
> * Hiển thị số tiền đã đặt & lựa chọn (Yes/No).
> * Số tiền dự kiến nhận được theo tỷ lệ Pool hiện tại.
> * **Nút "Đóng vị thế sớm":** Cho phép bán lại cổ phần trước khi sự kiện kết thúc.

---

## 👣 3. FOOTER
* Giữ nguyên thông tin tĩnh tương tự như Giao diện chính (Thông tin Founder, Liên hệ, Địa chỉ và Copyright 2026).

---

Tiêu chuẩn thiết kế:
* Người dùng được cập nhập thông tin sự kiện và tỷ lệ thắng thua theo thời gian thực ( độ trễ tối đa 1 phút ).
* Giao diện đặt lệnh đơn giản, dễ hiểu, với các nút thao tác rõ ràng và dễ tiếp cận.
* Biểu đồ phân tích được thiết kế trực quan, dễ đọc, với màu sắc phân biệt rõ ràng giữa các lựa chọn Yes/No.
* Tính năng thảo luận được phát triển sau, hiện tại chỉ hiển thị placeholder để người dùng biết sẽ có tính năng này trong tương lai.
