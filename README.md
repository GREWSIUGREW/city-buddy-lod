# CityBuddy
CityBuddy là người bạn đồng hành đô thị thông minh dựa trên nền tảng dữ liệu mở liên kết (LOD) mức độ 5, giúp đánh giá mức độ đáng sống của từng khu vực, hỗ trợ người dùng lựa chọn nơi sống phù hợp và cung cấp công cụ cho cơ quan quản lý trong việc giám sát, quy hoạch và nâng cao chất lượng đô thị.

# Mục lục (Table of contents)
- [Ý tưởng bài toán](#y-tuong-bai-toan)
- [Giải pháp kỹ thuật](#giai-phap-ky-thuat)
- [Đối tượng sử dụng](#doi-tuong-su-dung)
- [Nguồn dữ liệu & Liên kết](#nguon-du-lieu--lien-ket)
- [Kiến trúc hệ thống](#kien-truc-he-thong)
- [Yêu cầu hệ thống](#yeu-cau-he-thong)
- [Tính năng chính](#tinh-nang-chinh)
- [Công nghệ sử dụng](#cong-nghe-su-dung)
- [Hướng dẫn cài đặt](#huong-dan-cai-dat)
- [Lịch sử thay đổi](#lich-su-thay-doi)
- [Quản lý lỗi](#quan-ly-loi)
- [Giấy phép](#giay-phep)
- [Liên hệ](#lien-he)

## Ý tưởng bài toán
Hiện nay, chất lượng sống ngày càng được người dân quan tâm khi lựa chọn nơi sinh sống, đặc biệt về môi trường và sức khỏe tinh thần. 

- Thông tin về môi trường (AQI), hạ tầng (công viên) và thời tiết rời rạc, không có sự kết nối để đưa ra cái nhìn tổng thể về mức độ đáng sống của một khu vực.
- Thiếu công cụ hỗ trợ quyết định cá nhân hóa
- Chưa tối ưu hóa dữ liệu liên kết

Dự án đề xuất xây dựng một bản đồ số giúp tổng hợp và đánh giá chất lượng sống theo từng khu vực, hỗ trợ người dùng đưa ra lựa chọn phù hợp và góp phần cải thiện quy hoạch đô thị. 

## Giải pháp kỹ thuật
- Người dân: Tra cứu chỉ số đáng sống theo từng khu vực, tìm kiếm không gian xanh
- Nhà quản lý: Theo dõi toàn diện về hạ tầng kỹ thuật và môi trường để điều phối

 ## Nguồn dữ liệu & liên kết
 - Hạ tầng công cộng và tiện ích xung quanh (bệnh viện, trường học, cửa hàng tiện lợi, công viên, siêu thị,...). Sử dụng nguồn dữ liệu là OpenStreetMap Overpass.
 - Giao thông khu vực (mật độ giao thông, mức độ ùn tắc. Sử dụng GTFS datasets, các dịch vụ bản đồ)
 - Môi trường không khí (AQI, mức độ ô nhiễm). Nguồn sử dụng là OpenAQ và được mô tả bằng ontology SOSA/SSN
 - Mật độ dân cư và giá thành trung bình của khu vực. Sử dụng nguồn Wikidata,...


## Tính năng chính 



### A. Ứng dụng dành cho người dùng

| Tính năng | Mô tả |
|----------|------|
| Bản đồ Chất lượng sống | Hiển thị các lớp dữ liệu tích hợp gồm: AQI, không gian xanh, hạ tầng công cộng, tiện ích xung quanh, mật độ dân cư và chi phí sinh hoạt. |
| Điểm số Chất lượng sống | Tính toán và hiển thị điểm đánh giá tổng hợp dựa trên nhiều tiêu chí khác nhau. |
| Tiện ích xung quanh | Hiển thị khả năng tiếp cận đến bệnh viện, trường học, trung tâm mua sắm và dịch vụ công cộng. |
| Phân tích Không gian xanh | Đánh giá mật độ cây xanh, công viên và khoảng cách đến khu vực xanh gần nhất. |
| Giao thông & Mật độ | Hiển thị tình trạng giao thông và mật độ dân cư theo từng khu vực. |
| Chi phí sinh hoạt | Ước tính chi phí sống trung bình (thuê nhà, ăn uống, sinh hoạt). |
| So sánh khu vực | Cho phép so sánh nhiều khu vực theo các tiêu chí khác nhau. |
| Gợi ý cá nhân hóa | Đề xuất khu vực phù hợp dựa trên nhu cầu và ưu tiên của người dùng. |

---

### B. Dashboard dành cho quản lý

| Tính năng | Mô tả |
|----------|------|
| Trung tâm giám sát | Hiển thị tổng quan toàn thành phố với các lớp dữ liệu tích hợp. |
| Phân tích dữ liệu | Phân tích xu hướng về môi trường, giao thông, mật độ dân cư và chất lượng sống. |
| Tích hợp dữ liệu | Kết nối và chuẩn hóa dữ liệu từ nhiều nguồn (môi trường, y tế, giáo dục, bất động sản). |
| Hỗ trợ quy hoạch | Cung cấp dữ liệu và insight phục vụ ra quyết định trong quy hoạch đô thị. |
| Phát hiện vấn đề | Xác định các khu vực có rủi ro cao: ô nhiễm, quá tải dân cư, thiếu tiện ích. |
| Báo cáo & trực quan hóa | Xuất báo cáo, biểu đồ và bản đồ phục vụ phân tích và quản lý. |
