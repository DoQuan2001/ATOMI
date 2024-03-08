# GIỚI THIỆU KAFKA.

## I. KAFKA LÀ GÌ?

Kafka là gì? Là một nền tảng streaming phân tán sự kiện

MỤC ĐÍCH CỦA NÓ LÀ Real-time data lấy dữ liệu theo thời gian thực. Chủ yếu được áp dụng làm hệ thống phân tán, “vận chuyển” tin nhắn và thu thập, xử lý, lưu trữ và phân tích dữ liệu ở quy mô lớn.


![hinh ](../Kafka/images/1.png)


## II. KIẾN TRÚC CỦA KAFKA.


![hinh ](../Kafka/images/2.png)


- PRODUCER: Kafka lưu, phân loại message theo topic, sử dụng producer để publish message vào các topic. Dữ liệu được gửi đển partition của topic lưu trữ trên Broker.

- CONSUMER: Kafka sử dụng consumer để subscribe vào topic, các consumer được định danh bằng các group name. Nhiều consumer có thể cùng đọc một topic.

- TOPIC: Dữ liệu truyền trong Kafka theo topic, khi cần truyền dữ liệu cho các ứng dụng khác nhau thì sẽ tạo ra cá topic khác nhau.

- PARTITION (hàng đợi, gần giống hàng đợi ): Đây là nơi dữ liệu cho một topic được lưu trữ. Một topic có thể có một hay nhiều partition. Trên mỗi partition thì dữ liệu lưu trữ cố định và được gán cho một ID gọi là offset. Trong một Kafka cluster thì một partition có thể replicate (sao chép) ra nhiều bản. Trong đó có một bản leader chịu trách nhiệm đọc ghi dữ liệu và các bản còn lại gọi là follower. Khi bản leader bị lỗi thì sẽ có một bản follower lên làm leader thay thế. Nếu muốn dùng nhiều consumer đọc song song dữ liệu của một topic thì topic đó cần phải có nhiều partition.

- BROKER: Kafka cluster là một set các server, mỗi một set này được gọi là 1 broker

- ZOOKEEPER: được dùng để quản lý và bố trí các broker.





