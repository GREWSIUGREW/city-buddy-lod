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
| Bản đồ chất lượng sống | Hiển thị các lớp dữ liệu tích hợp gồm: AQI, không gian xanh, hạ tầng công cộng, tiện ích xung quanh, mật độ dân cư và chi phí sinh hoạt. |
| Điểm số chất lượng sống | Tính toán và hiển thị điểm đánh giá tổng hợp dựa trên nhiều tiêu chí khác nhau. |
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

## Kiến trúc hệ thống 

### A. Lớp tích hợp dữ liệu 
Đây là nơi thu thập và chuẩn hóa dữ liệu từ các nguồn mở khác nhau:
- Dữ liệu môi trường: Thu thập từ OpenAQ thông qua API. Các quan sát về AQI được mô hình hóa theo ontology SOSA/SSN để mô tả chi tiết các cảm biến và kết quả quan sát
- Dữ liệu hạ tầng & Tiện ích: Khai thác từ OpenStreetMap (OSM) Overpass API. Các thực thể địa lý (công viên, bệnh viện...) được định danh bằng mã URI duy nhất
- Dữ liệu kinh tế - Xã hội: Truy vấn từ Wikidata qua SPARQL endpoint để lấy thông tin về mật độ dân cư và giá thành khu vực
- Dữ liệu giao thông: Tích hợp các bộ dữ liệu GTFS thực tế

### B. Lớp tri thức và lưu trữ 
- Chuẩn hóa dữ liệu: Sử dụng định dạng JSON-LD/RDF để lưu trữ. Mọi dữ liệu đều tuân thủ các mô hình chuẩn từ FiWARE Smart Data Models
- Cơ chế liên kết (Linking): Thiết lập các mối quan hệ ngữ nghĩa giữa các nguồn dữ liệu (Ví dụ: Liên kết một tọa độ từ OSM với trạm đo AQI gần nhất từ OpenAQ và thông tin dân cư từ Wikidata) để đạt LOD mức độ 5

- API Giao tiếp: Xây dựng cổng chia sẻ dữ liệu dựa trên tiêu chuẩn NGSI-LD của ETSI, cho phép truy xuất dữ liệu đô thị theo ngữ cảnh thời gian thực

### C. Lớp ứng dụng  
- Mobile app: Giao diện tương tác cho Người dân (Bản đồ xanh, Gợi ý cá nhân hóa) và Dashboard cho Nhà quản lý (Phân tích xu hướng, Hỗ trợ quy hoạch)
- Cổng truy vấn SPARQL: Cung cấp điểm cuối (endpoint) cho phép các Nhà phát triển thực hiện các truy vấn tri thức phức tạp liên miền

## Yêu cầu hệ thống

### A. Môi trường vận hành
- Hệ điều hành: Hỗ trợ đa nền tảng (Windows 10/11, macOS, hoặc Linux Ubuntu 22.04 trở lên)
- Nền tảng ảo hóa: Docker & Docker Compose để đóng gói đồng bộ các dịch vụ, giúp việc cài đặt và triển khai nhanh chóng thông qua các script tự động
- Kết nối Internet: Cần thiết để truy xuất dữ liệu thời gian thực từ các nguồn dữ liệu liên kết như OpenAQ, OpenStreetMap và Wikidata

### B. Hạ tầng kỹ thuật & Cơ sở dữ liệu
- Context Broker: Orion-LD (hỗ trợ tiêu chuẩn NGSI-LD của ETSI) để quản lý dữ liệu đô thị theo ngữ cảnh thời gian thực
- Semantic Storage: GraphDB hoặc Apache Jena Fuseki để lưu trữ bộ ba RDF và thực hiện các truy vấn SPARQL liên nguồn
- Cấu trúc dữ liệu: Mô hình hóa dữ liệu cảm biến (AQI, nhiệt độ) dựa trên ontology SOSA/SSN của W3C

### C. Yêu cầu về mã nguồn và công cụ xây dựng
- Ngôn ngữ & Framework: Node.js (v18+), Python (v3.10+)
- Quản lý phụ thuộc: Sử dụng các công cụ chuẩn như npm/yarn hoặc pip
- Đóng gói sản phẩm: Ứng dụng hỗ trợ đóng gói phân phối theo phiên bản (v1.0.0) giúp việc thiết lập lại trên môi trường mới dễ dàng

### D. Giao diện người dùng 
Trải nghiệm dành cho cư dân:
- Mục tiêu là cung cấp một công cụ hỗ trợ quyết định cá nhân hóa về chất lượng sống ngay trên lòng bàn tay
- Bản đồ nhiệt chất lượng sống (Livability Heatmap): Tích hợp dịch vụ bản đồ số của bên thứ ba để hiển thị các lớp dữ liệu trực quan về AQI, mật độ cây xanh và tiện ích công cộng theo thời gian thực

Thẻ thông tin: 
- Khi người dùng chạm vào một địa điểm (ví dụ: một di tích hoặc công viên), ứng dụng sẽ truy xuất dữ liệu từ Wikidata/DBpedia để hiển thị thông tin chi tiết về lịch sử và văn hóa thông qua định danh URI

Bộ lọc tìm kiếm thông minh: 
- Cho phép người dùng lọc các khu vực theo nhu cầu sức khỏe (ví dụ: "Tìm nơi có AQI < 50 và có sân chơi trẻ em") dựa trên các truy vấn SPARQL ngầm định

Thông báo khẩn: 
- Cảnh báo tức thời khi chất lượng không khí tại vị trí hiện tại của người dùng chuyển sang mức nguy hại dựa trên dữ liệu từ OpenAQ



