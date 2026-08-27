# Bản đồ nền Việt Nam

Trang bản đồ tối giản sử dụng trực tiếp lớp WMS:

- Endpoint: `https://cache.bando.com.vn/service`
- Service: WMS 1.1.1
- Layer: `vietnam_2026`
- CRS hiển thị: EPSG:3857
- Format: PNG
- Kiểu tải: tiled WMS

## Giao diện

Chỉ hiển thị:

- **Bản đồ nền Việt Nam**
- bản đồ
- nút zoom

Không sao chép header, footer, popup hoặc giao diện của `cosodulieu.bando.com.vn`.

## Chạy

Có thể mở trực tiếp `index.html` hoặc triển khai bằng GitHub Pages.

> Lưu ý: trang không cần backend riêng, nhưng vẫn cần Internet để lấy tile WMS từ `cache.bando.com.vn`.
