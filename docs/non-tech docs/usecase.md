# 📋 USE CASE SPECIFICATION — FACTORA

> **Phiên bản:** 1.0  
> **Ngày:** 24/04/2026  
> **Hệ thống:** Factora — Nền tảng giao dịch dự đoán theo mô hình Pool thanh khoản

---

## 🎭 DANH SÁCH ACTOR

| Actor | Mô tả |
|---|---|
| **Guest** | Người dùng chưa đăng nhập |
| **User** | Người dùng đã đăng nhập |
| **Admin** | Quản trị viên hệ thống |
| **Hệ thống** | Hệ thống Factora (xử lý tự động) |

---

## 📑 DANH SÁCH USE CASE

| Mã | Tên Use Case | Actor |
|---|---|---|
| UC-01 | Đăng ký tài khoản | Guest |
| UC-02 | Đăng nhập | Guest |
| UC-03 | Đăng xuất | User |
| UC-04 | Xem danh sách sự kiện | Guest, User |
| UC-05 | Tìm kiếm sự kiện | Guest, User |
| UC-06 | Xem chi tiết sự kiện | Guest, User |
| UC-07 | Đặt lệnh giao dịch | User |
| UC-08 | Đóng vị thế sớm | User |
| UC-09 | Xem lịch sử giao dịch | User |
| UC-10 | Nạp tiền | User |
| UC-11 | Rút tiền | User |
| UC-12 | Cài đặt Stoploss / Take Profit | User |
| UC-13 | Xem hồ sơ cá nhân | User |
| UC-14 | Chỉnh sửa thông tin cá nhân | User |
| UC-15 | Xem thông báo | User |
| UC-16 | Xem danh mục sự kiện đã tham gia | User |
| UC-17 | Tạo sự kiện mới | Admin |
| UC-18 | Chốt kết quả sự kiện | Admin |
| UC-19 | Xác nhận nạp tiền | Admin |
| UC-20 | Phân phối thưởng tự động | Hệ thống |

---

## 📄 CHI TIẾT USE CASE

---

### UC-01: Đăng ký tài khoản

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-01 |
| **Tên** | Đăng ký tài khoản |
| **Actor chính** | Guest |
| **Mục tiêu** | Tạo tài khoản mới để tham gia giao dịch |
| **Tiền điều kiện** | Guest chưa có tài khoản, đang ở giao diện Guest |
| **Hậu điều kiện** | Tài khoản được tạo, hệ thống gửi email xác nhận |

**Luồng chính:**
1. Guest nhấn nút "Tham gia ngay" trên Header.
2. Hệ thống hiển thị Pop-up Auth với 2 tab: Đăng nhập / Đăng ký.
3. Guest chọn tab "Đăng ký".
4. Guest nhập Email, Mật khẩu, Xác nhận mật khẩu.
5. Guest nhấn nút "Đăng ký".
6. Hệ thống kiểm tra dữ liệu đầu vào.
7. Hệ thống tạo tài khoản và gửi email xác nhận.
8. Hệ thống hiển thị thông báo "Đăng ký thành công, vui lòng kiểm tra email".

**Luồng thay thế:**

- **3a.** Guest đã có tài khoản → chọn tab "Đăng nhập" → chuyển sang UC-02.

**Luồng ngoại lệ:**

- **6a.** Email đã tồn tại trong hệ thống → hiển thị lỗi "Email đã được sử dụng".
- **6b.** Mật khẩu và Xác nhận mật khẩu không khớp → hiển thị lỗi "Mật khẩu không khớp".
- **6c.** Định dạng email không hợp lệ → hiển thị lỗi "Email không hợp lệ".
- **6d.** Thiếu trường bắt buộc → hiển thị lỗi tương ứng từng trường.

---

### UC-02: Đăng nhập

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-02 |
| **Tên** | Đăng nhập |
| **Actor chính** | Guest |
| **Mục tiêu** | Xác thực danh tính và truy cập tài khoản |
| **Tiền điều kiện** | Guest đã có tài khoản, đang ở giao diện Guest |
| **Hậu điều kiện** | Guest trở thành User, giao diện chuyển sang trạng thái User |

**Luồng chính:**
1. Guest nhấn nút "Tham gia ngay" trên Header.
2. Hệ thống hiển thị Pop-up Auth.
3. Guest chọn tab "Đăng nhập".
4. Guest nhập Email và Mật khẩu. Tùy chọn tích "Ghi nhớ đăng nhập".
5. Guest nhấn nút "Đăng nhập".
6. Hệ thống xác thực thông tin.
7. Hệ thống chuyển giao diện sang trạng thái User, đóng Pop-up.

**Luồng thay thế:**

- **4a.** Guest tích "Ghi nhớ đăng nhập" → hệ thống lưu phiên, lần sau không cần nhập lại.

**Luồng ngoại lệ:**

- **6a.** Email không tồn tại → hiển thị lỗi "Email hoặc mật khẩu không đúng".
- **6b.** Mật khẩu sai → hiển thị lỗi "Email hoặc mật khẩu không đúng".
- **6c.** Thiếu trường bắt buộc → hiển thị lỗi tương ứng.

---

### UC-03: Đăng xuất

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-03 |
| **Tên** | Đăng xuất |
| **Actor chính** | User |
| **Mục tiêu** | Kết thúc phiên làm việc, quay về giao diện Guest |
| **Tiền điều kiện** | User đang đăng nhập |
| **Hậu điều kiện** | Phiên đăng nhập bị xóa, giao diện trở về trạng thái Guest |

**Luồng chính:**
1. User nhấn vào Icon tài khoản trên Header.
2. Hệ thống hiển thị Dropdown Menu.
3. User chọn "Đăng xuất".
4. Hệ thống hiển thị Pop-up xác nhận: "Bạn có chắc chắn muốn đăng xuất?".
5. User nhấn "Đồng ý".
6. Hệ thống xóa phiên đăng nhập.
7. Hệ thống chuyển về giao diện Guest.

**Luồng thay thế:**

- **5a.** User nhấn "Hủy" → đóng Pop-up, giữ nguyên phiên đăng nhập.

---

### UC-04: Xem danh sách sự kiện

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-04 |
| **Tên** | Xem danh sách sự kiện |
| **Actor chính** | Guest, User |
| **Mục tiêu** | Xem tổng quan các sự kiện đang diễn ra trên hệ thống |
| **Tiền điều kiện** | Actor đang ở trang chính |
| **Hậu điều kiện** | Danh sách sự kiện được hiển thị |

**Luồng chính:**
1. Actor truy cập trang chính của Factora.
2. Hệ thống tải danh sách sự kiện từ cơ sở dữ liệu.
3. Hệ thống hiển thị danh sách sắp xếp theo Tổng tiền Pool giảm dần.
4. Mỗi sự kiện hiển thị: Tên sự kiện, nút YES/NO, tỷ lệ thắng cửa Yes, Tổng Pool.

**Luồng thay thế:**

- **3a.** Không có sự kiện nào → hiển thị thông báo "Hiện chưa có sự kiện nào".

---

### UC-05: Tìm kiếm sự kiện

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-05 |
| **Tên** | Tìm kiếm sự kiện |
| **Actor chính** | Guest, User |
| **Mục tiêu** | Tìm nhanh sự kiện theo tên |
| **Tiền điều kiện** | Actor đang ở bất kỳ trang nào có Header |
| **Hậu điều kiện** | Hiển thị kết quả tìm kiếm hoặc thông báo không tìm thấy |

**Luồng chính:**
1. Actor nhập từ khóa vào thanh tìm kiếm trên Header.
2. Hệ thống tìm kiếm các sự kiện có tên liên quan theo thời gian thực.
3. Hệ thống hiển thị danh sách gợi ý bên dưới thanh tìm kiếm.
4. Actor nhấn vào sự kiện mong muốn.
5. Hệ thống chuyển đến trang giao dịch của sự kiện đó.

**Luồng ngoại lệ:**

- **3a.** Không tìm thấy sự kiện phù hợp → hiển thị "Không tìm thấy sự kiện".

---

### UC-06: Xem chi tiết sự kiện

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-06 |
| **Tên** | Xem chi tiết sự kiện |
| **Actor chính** | Guest, User |
| **Mục tiêu** | Xem thông tin đầy đủ về một sự kiện cụ thể |
| **Tiền điều kiện** | Actor đang ở trang chính hoặc kết quả tìm kiếm |
| **Hậu điều kiện** | Trang giao dịch sự kiện được hiển thị |

**Luồng chính:**
1. Actor nhấn vào tên sự kiện hoặc nút YES/NO trên danh sách.
2. Hệ thống chuyển đến trang giao dịch của sự kiện.
3. Hệ thống hiển thị: Tên, mô tả, tỷ lệ Yes/No, tổng Pool, đồng hồ đếm ngược, biểu đồ phân tích.
4. Với **Guest**: hiển thị thông tin sự kiện và nút "Đăng nhập để tham gia" tại khung đặt lệnh.
5. Với **User**: hiển thị đầy đủ khung đặt lệnh.

---

### UC-07: Đặt lệnh giao dịch

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-07 |
| **Tên** | Đặt lệnh giao dịch |
| **Actor chính** | User |
| **Mục tiêu** | Mua Shares để tham gia dự đoán sự kiện |
| **Tiền điều kiện** | User đã đăng nhập, sự kiện đang ở trạng thái "Đang diễn ra", User có đủ số dư |
| **Hậu điều kiện** | Shares được ghi nhận, số dư User giảm, Pool cập nhật |

**Luồng chính:**
1. User đang ở trang giao dịch sự kiện (trạng thái "Đang diễn ra").
2. User chọn vị thế **YES** hoặc **NO**.
3. User nhập số tiền muốn đặt (tối thiểu $1).
4. Hệ thống tính toán và hiển thị dự toán tiền nhận được nếu thắng theo Pool hiện tại.
5. User nhấn nút "Đặt lệnh".
6. Hệ thống kiểm tra số dư tài khoản.
7. Hệ thống thêm lệnh vào queue xử lý.
8. Hệ thống xử lý lệnh theo thứ tự: trừ số dư User, cộng Shares vào phe tương ứng, cập nhật Pool.
9. Hệ thống hiển thị Pop-up "Đặt lệnh thành công" kèm nút dẫn đến Lịch sử giao dịch.

**Luồng thay thế:**

- **2a.** User đã có Shares trong sự kiện này → hệ thống hiển thị thêm khung "Vị thế hiện tại" bên dưới khung đặt lệnh, User vẫn có thể đặt thêm.

**Luồng ngoại lệ:**

- **6a.** Số dư không đủ → hiển thị lỗi "Số dư không đủ, vui lòng nạp thêm tiền".
- **1a.** Sự kiện không còn ở trạng thái "Đang diễn ra" → ẩn khung đặt lệnh, hiển thị trạng thái sự kiện hiện tại.

---

### UC-08: Đóng vị thế sớm

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-08 |
| **Tên** | Đóng vị thế sớm |
| **Actor chính** | User |
| **Mục tiêu** | Bán lại Shares để chốt lời hoặc cắt lỗ trước khi sự kiện kết thúc |
| **Tiền điều kiện** | User đang giữ Shares trong sự kiện, sự kiện đang ở trạng thái "Đang diễn ra" |
| **Hậu điều kiện** | Shares bị xóa, số dư User tăng theo giá trị thực tế, Pool cập nhật |

**Luồng chính:**
1. User vào trang giao dịch sự kiện hoặc trang Danh mục sự kiện.
2. Hệ thống hiển thị khung "Vị thế hiện tại" với số Shares đang giữ và giá trị hiện tại.
3. User nhấn nút "Đóng vị thế sớm".
4. Hệ thống tính toán số tiền nhận về: `(Shares User / Tổng Shares phe đó) × Tổng Pool hiện tại`.
5. Hệ thống hiển thị Pop-up xác nhận với số tiền sẽ nhận về.
6. User nhấn "Xác nhận".
7. Hệ thống thêm lệnh vào queue xử lý.
8. Hệ thống xử lý: trừ Shares khỏi pool, trừ tiền tương ứng khỏi Pool, cộng tiền vào số dư User.
9. Hệ thống cập nhật lịch sử giao dịch với tag "Đóng vị thế sớm" và trạng thái Thắng/Thua tương ứng.
10. Hệ thống hiển thị thông báo "Đóng vị thế thành công".

**Luồng thay thế:**

- **6a.** User nhấn "Hủy" → đóng Pop-up, giữ nguyên vị thế.

**Luồng ngoại lệ:**

- **1a.** Sự kiện chuyển sang "Chờ chốt kết quả" hoặc "Đã kết thúc" → ẩn nút "Đóng vị thế sớm".

---

### UC-09: Xem lịch sử giao dịch

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-09 |
| **Tên** | Xem lịch sử giao dịch |
| **Actor chính** | User |
| **Mục tiêu** | Xem lại toàn bộ các lệnh đã tham gia |
| **Tiền điều kiện** | User đã đăng nhập |
| **Hậu điều kiện** | Danh sách giao dịch được hiển thị |

**Luồng chính:**
1. User nhấn Icon tài khoản → chọn "Lịch sử giao dịch".
2. Hệ thống tải danh sách giao dịch của User.
3. Hệ thống hiển thị theo thứ tự: lệnh "Đang chờ kết quả" trên đầu, sau đó theo thời gian mới nhất đến cũ nhất.
4. Mỗi lệnh hiển thị: Tên sự kiện, lựa chọn (Yes/No), số tiền đặt, thời gian đặt, trạng thái, tag "Đóng vị thế sớm" nếu có.

**Luồng thay thế:**

- **3a.** User chưa có giao dịch nào → hiển thị "Bạn chưa có giao dịch nào".

---

### UC-10: Nạp tiền

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-10 |
| **Tên** | Nạp tiền |
| **Actor chính** | User |
| **Mục tiêu** | Gửi yêu cầu nạp tiền vào tài khoản |
| **Tiền điều kiện** | User đã đăng nhập |
| **Hậu điều kiện** | Yêu cầu nạp tiền được ghi nhận, chờ Admin xác nhận |

**Luồng chính:**
1. User nhấn Icon tài khoản → chọn "Chuyển tiền".
2. Hệ thống hiển thị trang Chuyển tiền với 2 tab: Nạp tiền / Rút tiền.
3. User chọn tab "Nạp tiền".
4. Hệ thống hiển thị thông tin chuyển khoản: QR Code, Số tài khoản, Tên tài khoản, Ngân hàng.
5. User thực hiện chuyển khoản thực tế, sau đó tải ảnh bill lên hệ thống.
6. Hệ thống ghi nhận yêu cầu, lưu vào danh sách chờ xác nhận của Admin.
7. Hệ thống hiển thị thông báo "Yêu cầu nạp tiền đã được gửi, vui lòng chờ Admin xác nhận".

**Luồng ngoại lệ:**

- **5a.** Upload ảnh thất bại (sai định dạng, quá dung lượng) → hiển thị lỗi "Tải ảnh thất bại, vui lòng thử lại".

---

### UC-11: Rút tiền

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-11 |
| **Tên** | Rút tiền |
| **Actor chính** | User |
| **Mục tiêu** | Rút tiền từ tài khoản Factora |
| **Tiền điều kiện** | User đã đăng nhập, có số dư > 0 |
| **Hậu điều kiện** | Số dư User giảm tương ứng (đã trừ phí 0.025%) |

**Luồng chính:**
1. User nhấn Icon tài khoản → chọn "Chuyển tiền" → tab "Rút tiền".
2. User nhập số tiền muốn rút.
3. Hệ thống kiểm tra số dư.
4. Hệ thống hiển thị Pop-up xác nhận với thông tin: số tiền rút, phí 0.025%, số tiền thực nhận.
5. User nhấn "Đồng ý".
6. Hệ thống tự động trừ số tiền (gốc + phí) khỏi số dư User.
7. Hệ thống hiển thị thông báo "Yêu cầu rút tiền thành công".

**Luồng thay thế:**

- **5a.** User nhấn "Hủy" → đóng Pop-up, không thực hiện rút tiền.

**Luồng ngoại lệ:**

- **3a.** Số tiền rút > số dư hiện tại → hiển thị lỗi "Số dư không đủ".
- **2a.** User nhập số tiền ≤ 0 → hiển thị lỗi "Số tiền không hợp lệ".

---

### UC-12: Cài đặt Stoploss / Take Profit

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-12 |
| **Tên** | Cài đặt Stoploss / Take Profit |
| **Actor chính** | User |
| **Mục tiêu** | Thiết lập ngưỡng cảnh báo để nhận thông báo qua Gmail |
| **Tiền điều kiện** | User đã đăng nhập |
| **Hậu điều kiện** | Ngưỡng cảnh báo được lưu, hệ thống sẽ gửi Gmail khi đạt ngưỡng |

**Luồng chính:**
1. User nhấn Icon tài khoản → chọn "Cài đặt giao dịch".
2. Hệ thống hiển thị trang cài đặt với 2 phần: cài đặt chung và cài đặt theo sự kiện.
3. User nhập ngưỡng Stoploss (% lỗ tối đa) và/hoặc Take Profit (% lời mục tiêu).
4. User chọn phạm vi áp dụng: toàn bộ sự kiện hoặc sự kiện cụ thể.
5. User nhấn "Lưu".
6. Hệ thống lưu cài đặt.
7. Hệ thống hiển thị thông báo "Cài đặt đã được lưu".

**Luồng thay thế:**

- **4a.** User chọn sự kiện cụ thể → hệ thống hiển thị danh sách sự kiện User đang tham gia để chọn.

> **Lưu ý:** Hệ thống chỉ gửi cảnh báo Gmail, không tự động đóng vị thế. User tự quyết định hành động.

---

### UC-13: Xem hồ sơ cá nhân

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-13 |
| **Tên** | Xem hồ sơ cá nhân |
| **Actor chính** | User |
| **Mục tiêu** | Xem thông tin tài khoản cá nhân |
| **Tiền điều kiện** | User đã đăng nhập |
| **Hậu điều kiện** | Thông tin hồ sơ được hiển thị |

**Luồng chính:**
1. User nhấn Icon tài khoản → chọn "Hồ sơ cá nhân".
2. Hệ thống hiển thị: Email (chỉ đọc), Mật khẩu (có thể đổi), Số dư tài khoản, Thông tin ngân hàng.

---

### UC-14: Chỉnh sửa thông tin cá nhân

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-14 |
| **Tên** | Chỉnh sửa thông tin cá nhân |
| **Actor chính** | User |
| **Mục tiêu** | Cập nhật mật khẩu hoặc thông tin ngân hàng |
| **Tiền điều kiện** | User đang ở trang Hồ sơ cá nhân |
| **Hậu điều kiện** | Thông tin được cập nhật trong hệ thống |

**Luồng chính (Đổi mật khẩu):**
1. User nhấn "Chỉnh sửa" tại trường Mật khẩu.
2. User nhập mật khẩu cũ, mật khẩu mới, xác nhận mật khẩu mới.
3. User nhấn "Lưu".
4. Hệ thống xác thực mật khẩu cũ.
5. Hệ thống cập nhật mật khẩu mới.

**Luồng chính (Cập nhật thông tin ngân hàng):**
1. User nhấn "Chỉnh sửa" tại khối Thông tin ngân hàng.
2. User nhập/sửa: Tên ngân hàng, Số tài khoản, Tên chủ tài khoản.
3. User nhấn "Lưu".
4. Hệ thống cập nhật thông tin.

**Luồng ngoại lệ:**

- **4a** (Đổi mật khẩu). Mật khẩu cũ không đúng → hiển thị lỗi "Mật khẩu cũ không chính xác".
- **2b** (Đổi mật khẩu). Mật khẩu mới và xác nhận không khớp → hiển thị lỗi "Mật khẩu không khớp".

---

### UC-15: Xem thông báo

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-15 |
| **Tên** | Xem thông báo |
| **Actor chính** | User |
| **Mục tiêu** | Xem các thông báo từ hệ thống |
| **Tiền điều kiện** | User đã đăng nhập |
| **Hậu điều kiện** | Danh sách thông báo được hiển thị |

**Luồng chính:**
1. User nhấn Icon tài khoản → chọn "Thông báo".
2. Hệ thống hiển thị danh sách thông báo theo thứ tự mới nhất.
3. Các loại thông báo bao gồm: kết quả sự kiện đã tham gia, sự kiện sắp kết thúc, nhắc nhở hoàn thiện hồ sơ (lần đầu đăng ký).

**Luồng thay thế:**

- **3a.** Chưa có thông báo nào → hiển thị "Bạn chưa có thông báo nào".

---

### UC-16: Xem danh mục sự kiện đã tham gia

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-16 |
| **Tên** | Xem danh mục sự kiện đã tham gia |
| **Actor chính** | User |
| **Mục tiêu** | Xem danh sách sự kiện User đang hoặc đã tham gia |
| **Tiền điều kiện** | User đã đăng nhập |
| **Hậu điều kiện** | Danh sách sự kiện được hiển thị |

**Luồng chính:**
1. User nhấn Icon tài khoản → chọn "Danh mục sự kiện".
2. Hệ thống tải danh sách tất cả sự kiện User đã từng tham gia (bao gồm cả đã đóng vị thế sớm).
3. Mỗi sự kiện hiển thị: Tên, trạng thái, vị thế (Yes/No), nút "Đóng vị thế sớm" (nếu sự kiện đang diễn ra và User còn giữ Shares).
4. User nhấn vào sự kiện → chuyển đến trang giao dịch của sự kiện đó.

**Luồng thay thế:**

- **2a.** User chưa tham gia sự kiện nào → hiển thị "Bạn chưa tham gia sự kiện nào".
- **3a.** Sự kiện ở trạng thái "Chờ chốt kết quả" hoặc "Đã kết thúc" → ẩn nút "Đóng vị thế sớm".
- **3b.** User đã đóng vị thế sớm (không còn Shares) → ẩn nút "Đóng vị thế sớm".

---

### UC-17: Tạo sự kiện mới

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-17 |
| **Tên** | Tạo sự kiện mới |
| **Actor chính** | Admin |
| **Mục tiêu** | Đưa sự kiện dự đoán mới lên hệ thống |
| **Tiền điều kiện** | Admin đã đăng nhập vào trang Admin |
| **Hậu điều kiện** | Sự kiện được tạo với trạng thái "Đang diễn ra", Pool được khởi tạo |

**Luồng chính:**
1. Admin vào trang Quản lý sự kiện.
2. Admin nhấn nút "Tạo sự kiện mới".
3. Hệ thống hiển thị Form nhập liệu.
4. Admin nhập: Tên sự kiện, Mô tả, Thời gian kết thúc, Thanh khoản tham chiếu (số Shares Yes và No ban đầu).
5. Admin nhấn "Tạo".
6. Hệ thống kiểm tra dữ liệu đầu vào.
7. Hệ thống tạo sự kiện với trạng thái "Đang diễn ra", khởi tạo Pool với số Shares Dev đã nhập.
8. Sự kiện xuất hiện trên giao diện chính của User/Guest.

**Luồng ngoại lệ:**

- **6a.** Thiếu trường bắt buộc → hiển thị lỗi tương ứng.
- **6b.** Thời gian kết thúc ở quá khứ → hiển thị lỗi "Thời gian kết thúc không hợp lệ".
- **6c.** Thanh khoản tham chiếu ≤ 0 → hiển thị lỗi "Thanh khoản phải lớn hơn 0".

---

### UC-18: Chốt kết quả sự kiện

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-18 |
| **Tên** | Chốt kết quả sự kiện |
| **Actor chính** | Admin |
| **Mục tiêu** | Xác định phe thắng và kích hoạt phân phối thưởng |
| **Tiền điều kiện** | Sự kiện đang ở trạng thái "Chờ chốt kết quả" |
| **Hậu điều kiện** | Sự kiện chuyển sang "Đã kết thúc", tiền thưởng được phân phối tự động |

**Luồng chính:**
1. Admin vào trang Quản lý sự kiện.
2. Admin thấy sự kiện ở trạng thái "Chờ chốt kết quả".
3. Admin nhấn icon "Chốt kết quả" bên cạnh sự kiện.
4. Hệ thống hiển thị Pop-up yêu cầu Admin chọn kết quả: YES hoặc NO.
5. Admin chọn kết quả và xác nhận.
6. Hệ thống chuyển trạng thái sự kiện sang "Đã kết thúc".
7. Hệ thống kích hoạt UC-20 (Phân phối thưởng tự động).
8. Hệ thống gửi thông báo đến tất cả User đã tham gia sự kiện.

**Luồng ngoại lệ:**

- **2a.** Sự kiện chưa đến trạng thái "Chờ chốt kết quả" → nút chốt kết quả bị ẩn/disabled.

---

### UC-19: Xác nhận nạp tiền

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-19 |
| **Tên** | Xác nhận nạp tiền |
| **Actor chính** | Admin |
| **Mục tiêu** | Duyệt yêu cầu nạp tiền của User và cộng số dư |
| **Tiền điều kiện** | Có yêu cầu nạp tiền đang chờ xác nhận |
| **Hậu điều kiện** | Số dư User được cộng, yêu cầu chuyển sang "Đã xác nhận" |

**Luồng chính:**
1. Admin vào trang Quản lý nạp tiền.
2. Hệ thống hiển thị danh sách yêu cầu nạp tiền đang chờ xác nhận.
3. Admin xem ảnh bill của yêu cầu.
4. Admin nhấn nút "Xác nhận" bên cạnh yêu cầu.
5. Hệ thống hiển thị Pop-up yêu cầu Admin nhập số tiền cần cộng.
6. Admin nhập số tiền và nhấn "Xác nhận".
7. Hệ thống cộng số tiền vào tài khoản User.
8. Hệ thống chuyển trạng thái yêu cầu từ "Chờ xác nhận" sang "Đã xác nhận".
9. Hệ thống gửi thông báo đến User: "Tài khoản của bạn đã được nạp [số tiền]".

**Luồng thay thế:**

- **6a.** Admin nhấn "Hủy" trong Pop-up → đóng Pop-up, yêu cầu vẫn ở trạng thái "Chờ xác nhận".

**Luồng ngoại lệ:**

- **6b.** Admin nhập số tiền ≤ 0 → hiển thị lỗi "Số tiền không hợp lệ".

---

### UC-20: Phân phối thưởng tự động

| Trường | Nội dung |
|---|---|
| **Mã UC** | UC-20 |
| **Tên** | Phân phối thưởng tự động |
| **Actor chính** | Hệ thống |
| **Mục tiêu** | Tự động tính toán và phân phối tiền thưởng cho phe thắng sau khi Admin chốt kết quả |
| **Tiền điều kiện** | Admin vừa chốt kết quả (UC-18 hoàn thành) |
| **Hậu điều kiện** | Số dư của tất cả User phe thắng được cộng thưởng, lịch sử giao dịch cập nhật |

**Luồng chính:**
1. Hệ thống nhận tín hiệu kết quả từ UC-18.
2. Hệ thống lấy danh sách tất cả User đang giữ Shares phe thắng (không bao gồm Shares Dev seed và Shares đã đóng vị thế sớm).
3. Với mỗi User phe thắng, hệ thống tính: `Tiền thưởng = (Shares User / Tổng Shares phe thắng) × Tổng Pool`.
4. Hệ thống cộng tiền thưởng vào số dư từng User.
5. Hệ thống cập nhật trạng thái lịch sử giao dịch: `Đã thắng` hoặc `Đã thua`.
6. Hệ thống gửi thông báo kết quả đến tất cả User đã tham gia sự kiện.

---

## 📊 MA TRẬN ACTOR — USE CASE

| Use Case | Guest | User | Admin | Hệ thống |
|---|:---:|:---:|:---:|:---:|
| UC-01 Đăng ký | ✅ | | | |
| UC-02 Đăng nhập | ✅ | | | |
| UC-03 Đăng xuất | | ✅ | | |
| UC-04 Xem danh sách sự kiện | ✅ | ✅ | | |
| UC-05 Tìm kiếm sự kiện | ✅ | ✅ | | |
| UC-06 Xem chi tiết sự kiện | ✅ | ✅ | | |
| UC-07 Đặt lệnh giao dịch | | ✅ | | |
| UC-08 Đóng vị thế sớm | | ✅ | | |
| UC-09 Xem lịch sử giao dịch | | ✅ | | |
| UC-10 Nạp tiền | | ✅ | | |
| UC-11 Rút tiền | | ✅ | | |
| UC-12 Cài đặt Stoploss/TP | | ✅ | | |
| UC-13 Xem hồ sơ cá nhân | | ✅ | | |
| UC-14 Chỉnh sửa thông tin | | ✅ | | |
| UC-15 Xem thông báo | | ✅ | | |
| UC-16 Xem danh mục sự kiện | | ✅ | | |
| UC-17 Tạo sự kiện mới | | | ✅ | |
| UC-18 Chốt kết quả | | | ✅ | |
| UC-19 Xác nhận nạp tiền | | | ✅ | |
| UC-20 Phân phối thưởng | | | | ✅ |

---

*© 2026 FACTORA — Phát triển bởi Factora Team*
