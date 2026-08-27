# Bản đồ nền Việt Nam

WebGIS tối giản sử dụng trực tiếp lớp WMS `vietnam_2026` từ `https://cache.bando.com.vn/service`, không cần dựng backend riêng.

## Chức năng hiện có

- Bản đồ nền Việt Nam dạng WMS 1.1.1, EPSG:3857.
- Cơ chế single-image WMS + buffer + retry để tránh lỗi thiếu tile.
- Thanh công cụ dọc bên trái theo kiểu WebGIS:
  - Toàn quốc
  - Phóng to / thu nhỏ
  - Toàn màn hình
  - Quản lý lớp
  - Thông tin bản đồ
  - Vẽ tạm điểm / tuyến / vùng
  - Đo khoảng cách / diện tích
  - Định vị GPS
- Thước tỷ lệ động ở góc trái dưới.
- Tọa độ WGS84 cập nhật theo vị trí rê chuột.
- Tỷ lệ xích ước tính dạng `1:n` cập nhật theo vị trí con trỏ và mức zoom.
- Nhãn địa danh hiển thị theo đúng lớp raster `vietnam_2026`.

## Lưu ý về lớp nhãn

Trong mã nguồn trang được phân tích, `vietnam_2026` được trả về dưới dạng ảnh raster WMS. Tên địa danh, sông, đường và chữ chú thích hiện đang được render cùng ảnh bản đồ. Chưa có bằng chứng trong mã HTML được cung cấp rằng máy chủ công bố một layer nhãn độc lập để bật/tắt riêng.

Vì vậy giao diện hiện ghi rõ **Nhãn địa danh – Tích hợp** thay vì giả lập một layer không tồn tại.

## Triển khai

Repo dùng trực tiếp GitHub Pages:

`https://vietflexmap.github.io/mapVN2/`

Không cần Node.js, Python, GeoServer hay PostGIS. Trang vẫn cần Internet để tải WMS và thư viện Leaflet từ CDN.
