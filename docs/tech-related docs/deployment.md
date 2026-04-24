User đặt lệnh
    → Trading Service nhận request
    → Validate + lock row + update pool (atomic)
    → Publish event "pool_updated" lên RabbitMQ
    → Realtime Service nhận, broadcast qua Socket.IO
    → Tất cả client đang xem sự kiện đó nhận update tức thì