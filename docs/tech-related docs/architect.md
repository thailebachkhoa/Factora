event-driven + microservice architecture
ưu tiên real time -> web socket

Services phân chia
1. API Gateway — Nginx hoặc Kong
Điểm vào duy nhất, xử lý auth token, rate limiting, route đến các service. Không có business logic.
2. Auth Service

Tech: Node.js + Express
DB: PostgreSQL (users, sessions)
Cache: Redis (JWT blacklist, remember-me sessions)
Nhiệm vụ: đăng ký, đăng nhập, xác thực email, refresh token

3. Event Service — service quan trọng nhất

Tech: Node.js
DB: PostgreSQL (events, event_status, pool_snapshots)
Nhiệm vụ: CRUD sự kiện, quản lý vòng đời sự kiện (active → closed → settled)

4. Trading Service — service nhạy cảm nhất

Tech: Node.js
DB: PostgreSQL với row-level locking để tránh race condition
Message Queue: RabbitMQ — mọi lệnh đặt/đóng vị thế đều đi qua queue, xử lý tuần tự per-event để đảm bảo atomic
Nhiệm vụ: mua shares, đóng vị thế sớm, tính toán pool, settlement khi sự kiện kết thúc

5. Realtime Service

Tech: Node.js + Socket.IO
DB: không có DB riêng
Subscribe: lắng nghe events từ RabbitMQ do Trading Service publish
Nhiệm vụ: push pool updates, tỉ lệ yes/no, volume xuống client qua WebSocket
Đây là lý do tách riêng — scale ngang độc lập với Trading Service

6. Wallet Service

Tech: Node.js
DB: PostgreSQL (balances, deposit_requests, transactions)
Nhiệm vụ: quản lý số dư, xử lý yêu cầu nạp tiền, admin duyệt

7. Notification Service (placeholder, chưa làm nhưng nên thiết kế slot sẵn)

Tech: Node.js
Subscribe RabbitMQ
Gửi email khi sự kiện kết thúc, lệnh được khớp