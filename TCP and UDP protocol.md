## 1. Giao thức TCP
- Giao thức TCP nằm ở tầng Transport trong mô hình OSI.
- TCP là một giao thức đáng tin cậy (Reliable)
- Đây là một giao thức hướng kết nối, trước khi truyền tải dữ liệu cần phải thiết lập kết nối 2 bên bằng Three Way Handshake.
- Sau khi gửi dữ liệu thành công bên nhận sẽ gửi ACK để xác nhận tin cậy.
- Trước khi gửi dữ liệu bên gửi sẽ nhận được gói ACK nhằm xác định Window Size hay kích thước gói tin để đảm bảo xử lý giữa bên gửi và bên nhận.
- Giao thức TCP hỗ trợ truyền lại các gói dữ liệu bị mất hay hỏng trong quá trình tới bên nhận.

## 2. Giao thức UDP
- Giao thức UDP nằm ở tầng Transport trong mô hình OSI
- Đây là một giao thứ phi kết nối, có thể truyền tải dữ liệu ngay mà không cần thiết lập bất cứ kết nối nào
- Sửa lỗi bị hạn chế do đã có Checksum
- Là một giao thức Best-effort, truyền dữ liệu không tin cậy (Unreliable)
- Không có chức năng khôi phục dữ liệu hay yêu cầu gửi lại dữ liệu bị mất

## 3. So sánh giao thức UDP và TCP
- TCP là giao thức hướng kết nối còn UDP là giao thức phi kết nối
- Giao thức TCP khi truyền các gói tin sẽ có đánh số thứ tự SEQ cho các gói tin còn UDP thì không có đánh số thứ tự các gói tin truyền tải.
- Nếu gói tin truyền đi trong giao thức TCP bị mất thì gói tin đó sẽ được truyền lại đảm bảo thông tin được bảo toàn, trong giao thức UDP gói tin có thể bị mất hoặc thất lạc gây ra mất tín bảo toàn thông tin.
- TCP là giao thức đảm bảo việc truyền dữ liệu tin cậy còn UDP thì không.
- Tốc độ truyền tin của TCP thấp hơn UDP nên thường được dùng trong download, chia sẻ file còn UDP thường được trong VoIP, stream...

## 4. Tham khảo
https://tailamblog.wordpress.com/2017/08/09/giao-thuc-udp/
https://tailamblog.wordpress.com/2017/08/09/giao-thuc-tcp/
https://cuongquach.com/tu-hoc-ccna-tim-hieu-giao-thuc-tcp-udp.html
