# Tổng hợp các công cụ remote và stream PC/Laptop/Android/iOS

## Remote Desktop

- ⭐ [Sunshine](https://app.lizardbyte.dev/Sunshine/) hoặc [Apollo](https://github.com/ClassicOldSong/Apollo) - Remote server cho Moonlight / Windows / macOS / Linux / Android / iOS
- ⭐ [Parsec](https://parsec.app/) / Windows / macOS / Linux / Android / Web
- [RustDesk](https://rustdesk.com/) / Windows / macOS / Linux
- [Aspia](https://aspia.org/) / Windows / macOS / Linux

> Theo tôi thì nên dùng Sunshine + Moonlight, vì nó là mã nguồn mở, không cần đăng ký tài khoản và có thể stream chất lượng cao với codec AV1. Điểm trừ là bước setup ban đầu hơi quằn. Parsec thì phải đăng ký tài khoản mới stream được, bù lại cài là chạy ngay. Chất lượng stream không bằng Sunshine + Moonlight nhưng vẫn ổn.

## Hướng dẫn setup stream PC của bạn ở mọi nơi (Apollo + Artemis/Moonlight)

**Cập nhật:** 16/04/2026  
**Video hướng dẫn:** [Here](https://youtu.be/Xib0JK1IhVk?si=Q68hH-vbb7b7Hnps)

### Bước 1 - Bắt đầu sạch sẽ

> Quan trọng nếu trước đó bạn đã dùng Sunshine.

Nếu bạn từng dùng Sunshine, hãy gỡ cài đặt Sunshine trước.

Vào **Control Panel** → gỡ Sunshine, sau đó xóa các script cũ liên quan đến đổi độ phân giải, điều khiển màn hình hoặc các thiết lập tương tự.

Việc này giúp tránh lỗi xung đột lạ về sau. Mất khoảng 2 phút nhưng rất đáng làm.

### Bước 2 - Cài Apollo trên PC host

Apollo là phần mềm chạy trên PC của bạn.

Tải Apollo từ [GitHub](https://github.com/ClassicOldSong/Apollo), cài như một phần mềm bình thường rồi mở lên. Giao diện Apollo sẽ mở trong trình duyệt.

Bạn sẽ được yêu cầu tạo **username** và **password**. Hãy ghi nhớ thông tin này.

Sau khi đăng nhập, giao diện Apollo nhìn khá giống Sunshine nếu bạn từng dùng trước đó. Lý do là Apollo về cơ bản là một bản fork của Sunshine, nhưng được tích hợp thêm nhiều tính năng tốt hơn.

#### Lưu ý nhanh

Nếu thấy lỗi màu đỏ báo **VGenBus** chưa được cài, hãy tải từ [trang release ViGEmBus](https://github.com/nefarius/ViGEmBus/releases), cài đặt rồi khởi động lại Apollo.

Sau đó mọi trạng thái nên chuyển sang màu xanh và sẵn sàng sử dụng.

### Bước 3 - Cài Moonlight hoặc Artemis trên thiết bị client

Bây giờ bạn cần cài app trên thiết bị dùng để stream.

- **Steam Deck / Windows / iOS:** dùng Moonlight.
- **Android:** dùng Artemis hoặc Moonlight, cả hai đều hoạt động.

#### Cài nhanh trên Steam Deck

1. Vào **Desktop Mode**.
2. Mở **Discover Store**.
3. Tìm **Moonlight** rồi cài đặt.
4. Nhấp chuột phải vào Moonlight → chọn **Add to Steam**.
5. Sau đó bạn có thể mở Moonlight từ **Gaming Mode** như một game bình thường.

#### Cài nhanh trên Android

1. Vào [trang GitHub của Artemis](https://github.com/ClassicOldSong/moonlight-android).
2. Chọn **Releases** rồi tải file APK của bản mới nhất.
3. Cài APK trên thiết bị Android. Có thể cần bật tùy chọn cho phép cài app từ nguồn không xác định.

### Bước 4 - Pair thiết bị với PC

Mở Moonlight hoặc Artemis. Ban đầu bạn sẽ chưa thấy thiết bị nào, điều này là bình thường.

Thêm PC thủ công bằng địa chỉ IP của PC.

Bạn có thể lấy IP public từ trang <https://www.whatismyip.com>.

Khi bắt đầu kết nối:

1. Moonlight/Artemis sẽ hiện mã PIN 4 chữ số.
2. Vào Apollo → tab **PIN**.
3. Nhập mã PIN thật nhanh, vì mã sẽ hết hạn sau khoảng 30 giây.

Sau bước này, thiết bị của bạn đã được kết nối với PC.

#### Lỗi nhiều người hay gặp

Sau khi pair xong, bạn phải bật quyền thủ công cho thiết bị.

Trong Apollo:

1. Tìm thiết bị vừa pair.
2. Nhấn biểu tượng cây bút.
3. Bật toàn bộ quyền.
4. Lưu lại.

Nếu bỏ qua bước này, stream có thể không hoạt động đúng.

### Bước 5 - Thiết lập độ phân giải và bitrate

Trước khi mở game hoặc desktop, vào **Moonlight Settings** → **Resolution & Refresh Rate**. Thiết lập thông số này khớp chính xác với thiết bị của bạn.

Ví dụ:

- **Steam Deck OLED:** 1280×800 @ 90Hz
- **Máy handheld 1080p:** 1920×1080 @ 60/120Hz

Thiết lập này quan trọng hơn nhiều người nghĩ. Sai độ phân giải có thể gây mờ hình, scale sai, frame pacing kém, giật hình hoặc lag.

Tiếp theo, thiết lập **Bitrate**. Đây là thông số quyết định chất lượng stream và phụ thuộc vào đường truyền mạng.

Hãy bắt đầu với **30 Mbps**, sau đó:

- Tăng lên nếu mạng đủ khỏe.
- Giảm xuống nếu thấy giật, khựng hoặc có cảnh báo kết nối.

Mốc tham khảo:

- **30 Mbps:** chất lượng tốt, có nén nhẹ.
- **50+ Mbps:** hình ảnh sạch và rõ hơn nhiều.

### Bước 6 - Bật màn hình ảo

Quay lại Apollo → tab **Applications**.

Bạn sẽ thấy hai mục:

- **Desktop**
- **Steam Big Picture**

Chỉnh sửa cả hai mục và bật tùy chọn **Always Use Virtual Display**.

Đây là lý do lớn nhất để dùng Apollo.

#### Vì sao tùy chọn này quan trọng?

Thông thường, PC sẽ stream nội dung đang hiển thị trên màn hình thật.

Nếu bạn dùng màn hình ultrawide, hình ảnh khi stream sang thiết bị handheld thường sẽ bị sai tỉ lệ. Trên Steam Deck, lỗi thường gặp là có viền đen trên và dưới do tỉ lệ màn hình khác nhau.

Với tùy chọn này, Apollo có thể tạo một màn hình ảo riêng cho từng thiết bị, khớp với độ phân giải và tần số quét của thiết bị đó.

Ví dụ:

- Steam Deck nhận màn hình ảo 1280×800.
- Điện thoại nhận màn hình ảo 1080p.

### Bước 7 - Tắt màn hình thật

> Bước này chỉ cần setup một lần. Không bắt buộc, nhưng rất nên làm.

Khi đang kết nối remote vào PC:

1. Mở **Windows Display Settings**.
2. Nhấn **Identify**.
3. Xác định số thứ tự của từng màn hình.
4. Đặt màn hình ảo của thiết bị đang remote làm màn hình chính.
5. Với từng màn hình thật còn lại, chọn **Disconnect this display**.

Sau đó chỉ còn màn hình ảo hoạt động.

Kết quả:

- Bắt đầu stream → màn hình thật tắt.
- Dừng stream → màn hình thật bật lại.
- Chỉ cần cấu hình một lần.

### Bước 8 - Stream ở mọi nơi, không chỉ trong mạng nhà

Đây là phần quan trọng nếu bạn muốn chơi ngoài nhà qua internet.

Bạn có 3 lựa chọn.

#### Lựa chọn 1 - Dùng Tailscale

> Khuyến nghị. Đây là cách dễ nhất và an toàn nhất.

Tailscale tạo một mạng riêng giữa các thiết bị của bạn. Nhờ vậy PC và Steam Deck/điện thoại hoạt động như đang cùng một mạng Wi-Fi, kể cả khi bạn đang ở nơi khác.

Cách setup:

1. Cài Tailscale trên PC.
2. Cài Tailscale trên thiết bị client.
3. Đăng nhập cùng một tài khoản trên cả hai thiết bị.

Sau đó:

1. Tìm IP Tailscale của PC, thường bắt đầu bằng `100.x.x.x`.
2. Thêm IP này thủ công trong Moonlight/Artemis.

#### Lựa chọn 2 - Port forwarding

> Nâng cao. Chỉ nên dùng nếu bạn biết cách cấu hình router.

Nếu không muốn dùng Tailscale và có quyền truy cập router, bạn có thể mở port thủ công.

Apollo sẽ cho biết cần mở các port nào. Bạn đăng nhập vào router, thêm rule port forwarding, rồi trỏ các port đó về máy host đang chạy Apollo.

#### Lựa chọn 3 - UPnP

UPnP cho phép Apollo tự cấu hình port trên router.

Cách này kém ổn định hơn và cũng kém an toàn nhất. Tôi không khuyến nghị dùng UPnP. Chỉ dùng khi bạn không còn lựa chọn nào khác.
