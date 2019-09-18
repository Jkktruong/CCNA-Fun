## 1.Default route
- Default route được dùng để định tuyến các traffic, các gói tin tới bất kì một mạng nào đó không nằm trong bảng định tuyến trên router của bạn
- Nếu không khai báo một default route thì bất kì một traffic nào không được khai báo trên bảng định tuyến đều sẽ bị router drop
- Thông thường, default route sẽ trỏ mạng đến internet
- Một default route sẽ đặt trách nhiệm định tuyến lên hop tiếp theo mà nó kết nối
- Phần lớn các default route là các đường định tuyến ngược dòng
- Default route sẽ xác định gateway mà router dùng để gửi toàn bộ các gói tin IP khi mà không có tuyến đã học hoặc các tuyến tĩnh.
- Một default route đơn giản là một định tuyến tĩnh với 0.0.0.0/0 được coi như một địa chỉ IP đích
- Một định tuyến với một địa chỉ IP đích xác định sẽ được router cấp quyền ưu tiên hơn một default route
- Khai báo default route: `ip route 0.0.0.0 0.0.0.0 (đối với IPv4)` or `ipv6 route ::/0 (đối với IPv6)`

## 2.Network route
- Là một đường định tuyến đến một mạng cụ thể
- Cần phải add thêm nhiều mạng khác nhau vào bảng định tuyến
- Nếu không có network route thì các gói tin sẽ được định tuyến thông qua default route nếu default route tồn tại
- Network route được sử dụng cho các mạng mà không phải là các kết nối trực tiếp đến router hay các kết nối cục bộ trên router
- Một định tuyến mạng sẽ xác định mạng, subnet của mạng và địa chỉ IP của next hop gửi gói tin. Các định tuyến mạng cụ thể sẽ được ưu tiên hơn các định tuyến mạng ít cụ thể (thường dựa vào subnet mask)
- Khai báo các network route: `ip route <network to route> <subnet mask> <exit interface on router>` or `ip route <network to route> <subnet mask> <IP next hop>`. Đối với IPv6 `ip route <network to route>/<subnet mask> <exit interface>` hoặc `ip route <network to route>/<subnet mask> <ipv6 next hop>`

## 3.Host route
- Định tuyến host là sử dụng các đường định tuyến đưa các gói tin đến một host cụ thể.
- Subnet mask trong định tuyến host đối với IPv4 luôn là /32 và đối với IPv6 luôn là /128.
- Các host route được tự động thêm vào bảng định tuyến khi cấu hình trên router, mục đích của host route là tạo một CEF truy cập tương ứng giống như việc nhận truy cập các gói tin đã được trù định từ trước có thể được xử lý bởi chính router
- Cổng loopback thường được tạo với subnet mask là /32 và vì thế nó xuất hiện giống như một host route trên bảng định tuyến
- Host route phần lớn là các định tuyến cụ thể có khả thi vì thế nó được ưu tiên hơn các đường định tuyến khác.
- Khai báo các host route: `ip router <host to route> 255.255.255.255 <exit interface>` hoặc `ip route <ip route <host to route> 255.255.255.255 <ip next hop>`


## 4.Floating static route
- Thường được dùng trong các giải pháp dial-backup, khi đường routing chính bị mất khổi bảng routing thì đường floating static route sẽ được đưa vào bảng routing của router
- Đường floating static route thường được cấu hình dự phòng với chỉ số AD lớn hơn chỉ số AD của đường route chính.
- Khai báo một floating static route: `ip route <network to route> <subnet mask> <ipv4 next hop> <chosen AD>`
