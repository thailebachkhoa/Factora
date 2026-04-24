# 📱 GIAO DIỆN CHÍNH (DÀNH CHO KHÁCH - GUEST) - FACTORA

Tài liệu mô tả chi tiết bố cục và tính năng của trang tổng hợp khi người dùng chưa đăng nhập.

---

## 🏗️ 1. HEADER (THANH ĐIỀU HƯỚNG)

Bao gồm các thành phần tĩnh để nhận diện thương hiệu và các thành phần động để tương tác.

### **🔹 Thành phần Tĩnh**
* **Logo:** Biểu tượng Jackpot 3 số 7.
* **Tên ứng dụng:** FACTORA.

### **🔸 Thành phần Động**
#### **A. Thanh tìm kiếm (Search Bar)**
* **Tính năng:** Nhập tên sự kiện để tìm kiếm.
* **Logic:** * Hiển thị danh sách các sự kiện có tên liên quan.
    * Chọn vào sự kiện sẽ dẫn đến trang giao dịch riêng của sự kiện đó.
    * Nếu không có kết quả: Hiển thị "Không tìm thấy sự kiện".

#### **B. Hướng dẫn sử dụng (Manual Modal)**
*Khi nhấn vào sẽ hiển thị Pop-up (Yêu cầu đọc hoặc nhấn icon X để tắt). Nội dung bao gồm:*
1.  **Chọn một giao dịch:** Mua cổ phần (shares) theo vị thế **Yes** hoặc **No**.
2.  **Đặt lệnh:** Nạp tiền vào tài khoản và sẵn sàng giao dịch.
3.  **Nhận thưởng:** Bán cổ phần "Có" hoặc "Không" bất cứ lúc nào hoặc chờ đáo hạn để nhận thưởng.
4.  **Xem thêm (Liên kết động):**
    * [Thuật toán giao dịch Parimutuel Betting](./algorithm.md) *(Dẫn đến trang chi tiết thuật toán - trang yêu cầu header và footer như giao diện chính, nội dung hightlight đầy đủ)*.
    * [Giới thiệu về Team] *(Dẫn đến footer)*.
    * [Liên hệ hỗ trợ] *(Dẫn đến footer)*.

#### **C. Tham gia ngay (Auth Modal)**
*Khi nhấn vào sẽ hiển thị Pop-up lựa chọn:*
* **Đăng nhập:** Nhập Email, Mật khẩu và tùy chọn "Ghi nhớ đăng nhập".
* **Đăng ký:** Nhập Email, Mật khẩu, Xác nhận mật khẩu. Hệ thống sẽ gửi xác nhận qua Email thực.

---

## 📊 2. BODY (DANH SÁCH SỰ KIỆN)

Hệ thống hiện tại chỉ hỗ trợ các câu hỏi dự đoán **Yes / No**. Danh sách được ưu tiên hiển thị theo **Thanh khoản** hoặc **Tổng tiền Pool**.

Mỗi dòng trong danh sách bao gồm:
* **Tên sự kiện:** Nội dung câu hỏi dự đoán.
* **Khung YES / NO:** Nội dung động. Khi nhấn vào nút **Yes** hoặc **No** đều sẽ dẫn đến trang giao dịch riêng của sự kiện đó.
* **Khả năng thắng:** Tỷ lệ phần trăm thắng dự kiến của cửa Yes.
* **Tổng tiền trong Pool:** Tổng giá trị tiền hiện có trong bể giao dịch của sự kiện.

---

## 👣 3. FOOTER (THÔNG TIN TĨNH)

Phần chân trang chứa các thông tin pháp lý và liên hệ cố định.

* **Founder:** Lê Quốc Thái.
* **Liên hệ:** * **Gmail:** thai.lebachkhoa@hcmut.edu.vn
    * **Số điện thoại:** 0787309225
* **Địa chỉ:** ĐH Bách Khoa Thành phố HCM.
* **Copyright:** © 2026 FACTORA.