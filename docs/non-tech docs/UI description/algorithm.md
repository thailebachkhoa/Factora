Lưu ý: Đây là tài liệu liên kết với trang thuật toán giao dịch của Factora. Nội dung mô tả chi tiết cách thức hoạt động của thuật toán, cơ chế tính toán tiền thưởng và các tính năng liên quan đến việc đóng vị thế sớm.

# THUẬT TOÁN GIAO DỊCH FACTORA

Factora là nền tảng giao dịch dự đoán theo mô hình Pool thanh khoản. Tiền thưởng được tính dựa trên tỉ lệ đóng góp của người chơi vào phe chiến thắng.
Sự cảm hứng được lấy từ mô hình Parimutuel Betting
---

## 1. CÁCH THỨC HOẠT ĐỘNG

### Bước 1: Chọn vị thế
- Bạn phân tích một sự kiện (Ví dụ: Việt Nam thắng Thái Lan).
- Chọn **YES** (Đồng ý) hoặc **NO** (Không đồng ý).
- Mỗi "cổ phần" (share) dự đoán có giá cố định là **1 USD**.

### Bước 2: Biến động tỷ lệ
- Ban đầu, đội ngũ Dev sẽ nạp sẵn một lượng Shares để tạo thanh khoản (Ví dụ: 50 Yes - 50 No).
- Khi có nhiều người mua **YES**, tỷ lệ thắng của Yes sẽ tăng lên và ngược lại.
- **Giá trị của bạn = (Số lượng bạn mua) / (Tổng số lượng phe đó đang có).**

### Bước 3: Nhận thưởng khi kết thúc
Khi sự kiện kết thúc, toàn bộ số tiền trong Pool (tổng tiền cả 2 bên Yes và No) sẽ được chia hết cho những người ở phe thắng.

**Công thức tính tiền nhận về:**
> Tiền nhận được = (Số Shares bạn giữ / Tổng số Shares phe thắng) * Tổng tiền trong Pool

---

## 2. VÍ DỤ MINH HỌA

Sự kiện: **Việt Nam thắng Thái Lan?**

1. **Khởi tạo:** Dev bỏ vào 50 Yes và 50 No. (Tổng tiền trong Pool là 100 USD).
2. **Giao dịch:**
   - Bạn mua **10 Shares YES** (tốn 10 USD).
   - Người khác mua **20 Shares NO** (tốn 20 USD).
   - Lúc này Pool có: 60 Yes và 70 No. (Tổng Pool = 130 USD).

3. **Kết quả:** Nếu Việt Nam thắng (Phe YES thắng):
   - Bạn đang giữ 10 trong tổng số 60 Shares của phe Yes.
   - Tiền bạn nhận về: (10 / 60) * 130 = **21.67 USD**.
   - Lợi nhuận: **11.67 USD** (Gần x2 tài khoản).

---

## 3. CƠ CHẾ ĐÓNG VỊ THẾ SỚM (CHỐT LỜI/CẮT LỖ)

Bạn không nhất thiết phải chờ đến khi sự kiện kết thúc. Factora cho phép bạn "lướt sóng" dựa trên sự biến động của niềm tin thị trường.

### Nguyên lý hoạt động:
Khi bạn đóng vị thế sớm, bạn đang bán lại số Shares mình nắm giữ cho hệ thống dựa trên **Giá trị thực tế** tại thời điểm đó.

**Công thức tính Giá trị rút về:**
> Số tiền rút về = (Số Shares bạn giữ / Tổng số Shares phe đó) * Tổng tiền trong Pool hiện tại

### Quy trình hệ thống xử lý:
1. **Xác nhận giá trị:** Hệ thống tính toán số tiền bạn nhận được dựa trên tỉ lệ hiện tại của Pool.
2. **Cập nhật Shares:** Số Shares bạn vừa bán sẽ được trừ khỏi tổng số Shares của phe đó.
3. **Cập nhật Pool:** Số tiền tương ứng sẽ được rút khỏi Tổng Pool để trả về ví cho bạn.

---

### Ví dụ minh họa chi tiết:

**Giai đoạn 1: Bạn mua vào**
* Giả sử Pool đang cân bằng: **50 Yes - 50 No** (Tổng Pool = $100).
* Bạn mua **10 Shares Yes** với giá **10 USD**.
* Pool sau khi bạn mua: **60 Yes - 50 No** (Tổng Pool = $110).

**Giai đoạn 2: Thị trường biến động (Tin tốt cho phe Yes)**
* Nhiều người khác đổ xô vào mua Yes, đẩy Pool lên thành: **100 Yes - 50 No** (Tổng Pool = $150).
* Lúc này, giá trị 10 Shares của bạn đã tăng lên vì phe Yes đang chiếm ưu thế lớn trong Pool.

**Giai đoạn 3: Bạn thực hiện Đóng vị thế sớm**
* **Tính toán:** Bạn sở hữu 10 trên tổng 100 Shares của phe Yes.
* **Số tiền nhận về:** (10 / 100) * $150 = **15 USD**.
* **Kết quả:** Bạn lãi **5 USD** (tăng 50% vốn) mà không cần chờ trận đấu diễn ra.

**Giai đoạn 4: Hệ thống cập nhật lại Pool sau khi bạn rút**
* **Số Shares Yes còn lại:** 100 - 10 = **90 Shares**.
* **Tổng Pool còn lại:** $150 - $15 = **135 USD**.
* Tỉ lệ mới của sàn sẽ là: **90 Yes - 50 No**.

## 4. ƯU ĐIỂM
- **Minh bạch:** Hệ thống tự động chia tiền, không ai can thiệp được.
- **Dễ chơi:** Chỉ có 2 lựa chọn Yes hoặc No.
- **Thanh khoản:** Có thể rút vốn hoặc chốt lời bất cứ lúc nào.

---
*Phát triển bởi Factora Team*