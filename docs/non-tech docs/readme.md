hệ thống giao dịch dựa trên dự đoán sự kiện:
đây là kiến trúc microservices gồm service: 

1. xác thực người dùng (authentication service)
2. quản lí tài khoản người dùng (user account service)
3. quản lý sự kiện (event management service)
4. dự đoán sự kiện (event prediction service)
5. nạp tiền và rút tiền (payment service)


bắt đầu hệ thống là hệ thống xác thực người dùng:
stakeholders: user

- người dùng đăng nhập vào hệ thống bằng tài khoản của họ, cần 2 input:
1. gmail
2. mật khẩu (password)

- nếu chưa có tài khoản, dẫn người dùng đến trang đăng ký, cần 3 input:
1. gmail
2. mật khẩu (password)
3. xác nhận mật khẩu (confirm password) 
( không thực hiện firebase mà chỉ dùng nodemailer + gmail app password để gửi email xác nhận đăng ký)
người dùng xác nhận thì lưu thông tin vào database.


- sau khi đăng nhập thành công 

