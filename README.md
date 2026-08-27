# Bản đồ nền Việt Nam

Trang GitHub Pages tối giản dùng trực tiếp lớp WMS `vietnam_2026` từ:

- Endpoint: `https://cache.bando.com.vn/service`
- Service: WMS 1.1.1
- Layer: `vietnam_2026`
- CRS: EPSG:3857
- Format: PNG

## Cách tải mới

Phiên bản trước dùng `TileWMS` 256×256. Trình duyệt phải phát nhiều request đồng thời; khi một số request rớt, bản đồ xuất hiện các mảng vuông trắng hoặc bị chia thành nhiều khối.

Phiên bản hiện tại chuyển sang **single-image WMS theo toàn viewport**:

1. Tính BBOX EPSG:3857 từ vùng đang nhìn.
2. Yêu cầu một ảnh WMS lớn bao phủ toàn viewport và thêm vùng đệm xung quanh.
3. Giữ ảnh cũ trong lúc tải ảnh mới để tránh chớp trắng.
4. Chỉ thay ảnh khi request mới tải hoàn chỉnh.
5. Nếu request lỗi, tự thử lại với kích thước ảnh nhỏ hơn và tiếp tục retry.
6. Giới hạn cạnh ảnh tối đa để tránh tạo request quá lớn cho máy chủ.

Cách này giảm mạnh số request và khắc phục hiện tượng thiếu tile khi xem trên GitHub Pages.

## Giao diện

Chỉ giữ:

- **Bản đồ nền Việt Nam**
- bản đồ toàn màn hình
- nút zoom

Không sao chép header, footer, popup hoặc giao diện của trang nguồn.

## Chạy

Có thể mở `index.html` hoặc dùng GitHub Pages tại repository này.

> Không cần backend riêng. Trình duyệt vẫn cần Internet để tải ảnh WMS từ `cache.bando.com.vn`.
