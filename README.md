# Bản đồ nền Việt Nam — mapVN2

WebGIS một trang, chạy trực tiếp trên GitHub Pages và sử dụng lớp WMS `vietnam_2026` từ `https://cache.bando.com.vn/service` mà không cần backend riêng.

## Giao diện 2026

Thanh công cụ được thiết kế lại theo dạng website, nằm ngang cố định ở phía trên:

- icon màu đỏ, chữ màu vàng;
- Toàn quốc;
- Phóng to / Thu nhỏ;
- Toàn màn hình;
- Lớp bản đồ;
- Thông tin;
- Vẽ dữ liệu;
- Đo đạc;
- Tìm đường;
- Định vị GPS.

Mỗi công cụ có panel riêng và tại một thời điểm chỉ mở một panel để tránh che bản đồ.

## Lớp bản đồ

### Lớp nền tùy chọn

- ESRI Terrain;
- ESRI World Imagery;
- Không dùng lớp nền.

### Lớp phủ chính

- **Bản đồ nền Việt Nam** — WMS `vietnam_2026`;
- điều chỉnh opacity;
- bật/tắt lớp;
- nhãn địa danh được ghi nhận là nhãn raster tích hợp trong WMS hiện tại;
- dữ liệu người dùng vẽ trong phiên có thể bật/tắt.

## Chống lỗi WMS

Không dùng `TileWMS` 256×256 làm lớp chính. Trang sử dụng single-image WMS theo viewport, có vùng buffer, giữ ảnh cũ đến khi ảnh mới tải xong và tự retry ở độ phân giải thấp hơn nếu máy chủ trả lỗi. Cách này hạn chế hiện tượng bản đồ bị thủng thành các ô vuông.

## Đo đạc

- Đo chiều dài;
- Đo diện tích;
- cập nhật kết quả trong lúc rê chuột;
- kết thúc bằng double-click hoặc nút **Kết thúc đo**;
- xóa toàn bộ kết quả đo.

## Tìm đường

- nhập tọa độ `lat,lon` hoặc địa chỉ;
- có thể chọn điểm A/B trực tiếp trên bản đồ;
- đổi điểm đầu / điểm cuối;
- tuyến lái xe dùng OSRM public demo;
- địa chỉ văn bản dùng Nominatim;
- hiển thị khoảng cách và thời gian dự kiến.

> OSRM và Nominatim là dịch vụ bên ngoài; khả năng hoạt động phụ thuộc dịch vụ công cộng tại thời điểm sử dụng.

## Vẽ dữ liệu

Hỗ trợ vẽ tạm:

- Point;
- LineString;
- Polygon.

Dữ liệu chỉ tồn tại trong phiên trình duyệt hiện tại.

## Tọa độ và tỷ lệ

Góc dưới phải hiển thị:

- tọa độ WGS84 theo vị trí con trỏ;
- tỷ lệ xích động dạng `1:n`;
- có thể nhập mẫu số tỷ lệ để đưa bản đồ tới mức zoom gần tương ứng.

Góc dưới trái có thước tỷ lệ mét/km.

## Triển khai

GitHub Pages:

`https://vietflexmap.github.io/mapVN2/`
