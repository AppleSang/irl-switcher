<div align="center">

<img src="res/irl-switcher.svg" alt="IRL Switcher" width="320" />

# IRL SWITCHER

**Tự động chuyển scene OBS theo trạng thái tín hiệu SRT / RTMP khi livestream IRL**

</div>

---

## Giới thiệu

IRL Switcher là một công cụ giao diện web chạy trực tiếp bên trong OBS (qua **Browser Source**), kết nối với OBS thông qua **obs-websocket** để giám sát các media source phát trực tiếp (SRT / RTMP) và tự động điều khiển scene:

- Khi nguồn tín hiệu **LIVE** → tự chuyển sang scene **IRL** để lên sóng hình ảnh từ hiện trường.
- Khi nguồn tín hiệu **MẤT** (rỗng, đen, đứng yên, ngắt kết nối) → tự chuyển về scene **Disconnected** (màn chờ) thay vì để khung hình chết trên sóng.

Toàn bộ hoạt động ngay trên máy streaming, không cần dịch vụ trung gian.

## Mục đích sử dụng

Dành cho streamer IRL (di chuyển ngoài trời, phát sóng qua 4G/5G bằng SRT) — những người thường xuyên gặp tình huống tín hiệu lúc có lúc mất và muốn:

- Tự động giữ sóng "sống" liên tục: mất tín hiệu là lập tức có màn hình chờ chuyên nghiệp thay thế.
- Giám sát tình trạng nguồn phát theo thời gian thực (badge **LIVE / DEAD** trên từng nguồn, cập nhật mỗi giây).
- Giảm thiểu thao tác tay khi đang di chuyển: cấu hình một lần, bật chế độ tự động và quên đi.

## Tính năng chính

- **Tự động đăng nhập** OBS WebSocket — lưu thông tin kết nối cục bộ trên trình duyệt.
- **Giám sát tín hiệu thông minh**: kết hợp trạng thái media input, timecode và so khớp khung hình (frame-delta) để phân biệt *đang nhận sóng*, *mất kết nối* và *khung hình bị treo/đen*.
- **Auto-switch**: tự chuyển scene IRL / Disconnected theo tín hiệu, có chống nhiễu (edge-triggered, không chuyển lặp).
- **An toàn vận hành**: tự tắt auto-switch khi bạn chuyển scene tay trong OBS, tự bật lại khi quay về scene đã cấu hình.
- **Kiểm tra cấu hình**: cảnh báo ngay khi media source chưa được thêm vào scene IRL / Disconnected, kèm đề xuất copy tự động.

## Yêu cầu

- [OBS Studio](https://obsproject.com/) với **WebSocket Server** bật sẵn (`Tools → WebSocket Server Settings`).
- Một media source (Media Source) nhận sóng `srt://` hoặc `rtmp://`.
- Trình duyệt / Browser Source có kết nối mạng đến OBS WebSocket.

## Sử dụng nhanh

1. Mở `apple.html` trong Browser Source của OBS (hoặc trình duyệt để cấu hình trước).
2. Nhập IP, Port, Password của OBS WebSocket → **Connect**.
3. Chọn **media source** cần giám sát, chọn **scene IRL** và **scene Disconnected**.
4. Bấm **Enable auto-switch** — phần còn lại để tool lo.

## Ghi chú

- Thông tin kết nối (bao gồm mật khẩu) được lưu trong `localStorage` của chính trình duyệt/Browser Source đó, không gửi đi đâu khác.
- Hai trang đi kèm: `apple.html` (auto-switch watchdog) và `index.html` (bảng giám sát nguồn phát đơn giản).

---

<div align="center">

`OBS WEBSOCKET` · `SRT` · `RTMP` · `IRL STREAMING`

</div>
