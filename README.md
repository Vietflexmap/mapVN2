# Bản đồ nền Việt Nam — mapVN2

WebGIS một trang chạy trực tiếp trên GitHub Pages.

## Kiến trúc lớp bản đồ đã xác định từ mã nguồn gốc

Phân tích `4_map.js` trong bộ mã nguồn cho thấy website nguồn **tách riêng lớp bản đồ và lớp nhãn**:

- `vietnam_2026` — lớp bản đồ nền;
- `vietnam_label_2026` — lớp nhãn bản đồ;
- cả hai được tải từ `https://cache.bando.com.vn/service` bằng WMS 1.1.1, EPSG:3857.

Website gốc tạo đồng thời `vn1tr` và `vn1trLabel`; khi bật/tắt `vn1tr` thì bật/tắt cả hai. Vì vậy mapVN2 cũng triển khai hai lớp riêng thay vì giả định nhãn đã nằm hoàn toàn trong `vietnam_2026`.

## Nhãn bản đồ

`vietnam_label_2026` được bật mặc định và nằm phía trên `vietnam_2026`. Đây là nguồn nhãn gốc dùng để bổ sung tên tỉnh/thành, xã/phường, sông suối, địa danh và các nhãn cartography khác theo tỷ lệ do máy chủ quy định.

mapVN2 tải lớp nhãn theo toàn viewport, không chia lớp nhãn thành các tile nhỏ, nhằm giảm tình trạng rớt từng ô nhãn. Kích thước request bám sát viewport để giữ scale denominator gần với màn hình thực tế.

## Chú giải

Bảng chú giải từ `https://cosodulieu.bando.com.vn/static/map/images/cg6.jpg` được hiển thị cố định ở góc phải. Có thể thu gọn bằng nút `−/+` hoặc ẩn/hiện bằng nút **Chú giải** trên thanh công cụ.

Chú giải bao gồm biên giới quốc gia, địa giới cấp tỉnh, địa giới cấp xã, tên vùng kinh tế xã hội, tên tỉnh, thủ đô, thành phố trực thuộc trung ương, điểm dân cư, công trình văn hóa/tôn giáo, khu du lịch, cảng hàng không, cảng biển, san hô và các dạng đá ven biển.

## Công cụ

- ESRI Terrain / ESRI World Imagery;
- bật/tắt và opacity Bản đồ nền Việt Nam;
- bật/tắt và opacity Nhãn bản đồ đầy đủ;
- chú giải góc phải;
- tọa độ WGS84 theo con trỏ;
- tỷ lệ xích và thước tỷ lệ;
- phóng to / thu nhỏ / toàn quốc / toàn màn hình;
- vẽ điểm, tuyến, vùng;
- đo chiều dài và diện tích;
- định vị GPS;
- tìm đường A → B bằng OSRM public demo và geocoding Nominatim.

## Triển khai

GitHub Pages: `https://vietflexmap.github.io/mapVN2/`

> Dữ liệu/nhãn WMS vẫn phụ thuộc máy chủ nguồn và quy tắc hiển thị theo tỷ lệ phía server. Những lớp hoặc mức chi tiết yêu cầu đăng nhập/PRO của website nguồn không được vượt qua bằng frontend này.
