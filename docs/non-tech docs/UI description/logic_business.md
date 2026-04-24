1. Về số tiền Dev seed thanh khoản:
Dev bỏ 50 Yes + 50 No = $100 vào pool. Khi sự kiện kết thúc và phe Yes thắng, $100 đó được chia hết cho người chơi phe Yes — bao gồm cả 50 share Yes của Dev. Vậy Dev có nhận lại phần của mình không, hay $100 đó là "phí tạo pool" bỏ đi hoàn toàn?
trả lời: vì đây chỉ là hệ thống demo, không cần trả lại, tất cả tiền là ảo, thậm chí người chơi cũng không cần phải nạp tiền thật, nên Dev bỏ vào pool bao nhiêu thì sẽ mất bấy nhiêu, không có chuyện nhận lại. 

2. Về phí hệ thống:
Tài liệu chỉ đề cập phí rút tiền 0.025%. Có phí giao dịch (mua/bán share) không? Hay chỉ có phí rút?
-> phí rút thôi, không chơi phí giao dịch, vì đây là hệ thống demo, không có tiền thật, nên không cần phí giao dịch.

3. Về cơ chế nạp tiền Demo:
Tài liệu nói "chỉ cần upload ảnh thành công là hệ thống ghi nhận" nhưng phần Admin lại có bảng chờ xác nhận và nút Xác nhận thủ công. Vậy thực tế là:

Admin phải bấm xác nhận → tiền mới vào tài khoản User? -> đúng, admin xác nhận đã
Hay upload ảnh xong là tự động cộng tiền, Admin chỉ xem để biết? -> không nhé.

4. Nếu sự kiện đã hết thời gian nhưng Admin chưa chốt kết quả, User có được đóng vị thế sớm không? Hay tính năng này chỉ hoạt động khi sự kiện còn Đang diễn ra?
-> chỉ hoạt động khi sự kiện còn Đang diễn ra, vì nếu đã hết thời gian rồi mà admin chưa chốt kết quả thì user vẫn phải chờ admin chốt kết quả, không thể đóng vị thế sớm được.

5. Thời hạn cho sự kiện có thể từ 1 phút đến 1 tháng nhé. 
6. Đóng vị thế sớm: user không còn tham gia quá trình sự kiện nữa, nên sẽ không nhận được thông báo khi sự kiện kết thúc, cũng không được chia tiền thưởng, mà chỉ nhận được số tiền tương ứng với giá trị thực tế của share tại thời điểm đóng vị thế sớm.
7. hệ thống giao dịch sẽ làm theo queue.
8. Lịch sử giao dịch với trường hợp đóng vị thế sớm: sẽ hiển thị như một giao dịch bình thường ( thắng hoặc thua) nhưng có thêm thông tin "đóng vị thế sớm" để phân biệt với giao dịch bình thường.
9. Trang giao dịch sự kiện dùng chung header cho cả Guest lẫn User. Nhưng khung đặt lệnh bên phải — Guest nhìn thấy gì? Hai hướng:

A) Ẩn hoàn toàn khung đặt lệnh, hiển thị nút "Đăng nhập để tham gia".
B) Hiển thị khung đặt lệnh bình thường, nhưng khi bấm "Đặt lệnh" thì pop-up yêu cầu đăng nhập.
-> 
10. lịch sử giao dịch: đóng vị thế sớm chỉ có thể dẫn đến đã thắng hoặc đã thua
11. trang chính của user hay guest nhấn vào đặt lệnh yes / no nó chỉ dẫn đến trang giao dịch thôi chứ không đặt lệnh trên đó. 
