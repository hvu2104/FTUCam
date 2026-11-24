# FTUCam — Nhận diện khách gọi phục vụ

Web tĩnh (một file `index.html`), AI chạy ngay trong trình duyệt bằng MediaPipe Pose Landmarker. Không cần server, không lưu dữ liệu.

## Chạy trên máy
```
npx http-server -p 5173 -c-1
```
Mở http://localhost:5173 (camera chỉ chạy trên `localhost` hoặc `https`, ví dụ GitHub Pages).

## Điện thoại làm camera qua USB
- Android 14+: cắm cáp, chọn **Webcam** trong thông báo USB.
- Máy khác / iPhone: cài DroidCam hoặc Iriun (cả điện thoại và máy tính), chọn kết nối USB.
- Trên web bấm **Làm mới danh sách camera** rồi chọn camera của điện thoại.

## Điện thoại không dây qua mã QR (không cần cài app)
- Trên máy tính mở tab **Điện thoại (QR)** → **Tạo mã QR**.
- Điện thoại quét mã, mở trang, bấm **Bắt đầu gửi hình** và cho phép camera.
- Hình truyền bằng WebRTC (PeerJS) sang máy tính, AI chạy trên máy tính.
- Điện thoại chỉ mở được camera trên https, nên dùng bản GitHub Pages: https://hvu2104.github.io/FTUCam/

## Điện thoại làm camera không dây (DroidCam / Iriun)
- Điện thoại và máy tính vào cùng một mạng Wi-Fi.
- Mở DroidCam / Iriun, trên máy tính chọn kết nối Wi-Fi (nhập IP điện thoại nếu được hỏi).
- Trên web bấm **Làm mới danh sách camera** rồi chọn camera "DroidCam" / "Iriun".

## Quy tắc mức độ (lấy mức cao hơn của hai tiêu chí)
| Mức | Thời lượng giơ tay | Số lần trong 60s |
|---|---|---|
| Mới (xanh) | ≤ 10s | ≤ 2 |
| Trung bình (vàng) | 11–15s | 3 |
| Cao (đỏ) | > 15s | ≥ 4 |
