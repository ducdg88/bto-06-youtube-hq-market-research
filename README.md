**🇻🇳 Tiếng Việt** · [🇬🇧 English](README.en.md)

# BTO-06: Hồ sơ thị trường YOUTUBE HQ

Hoàng Văn Đức · Build to Own, Cohort 01 · 27/09/2026

## Kết luận nhanh

YOUTUBE HQ là bảng vận hành chung cho các studio YouTube nhỏ ở Việt Nam đang chạy 5 đến 20 kênh cho thị trường nước ngoài: một màn hình thấy số liệu thật, doanh thu và thưởng của đội, mỗi kênh tách riêng đăng nhập.

- **Build cho ai:** chủ studio YouTube Việt Nam có 5 đến 20 kênh và đội 2 đến 6 người (dựng, quay, phân tích), không rành kỹ thuật. Người dùng đầu tiên là chính mình: 10 kênh, đội 4 người.
- **Khác gì cái đang có:** công cụ YouTube phổ biến (vidIQ, TubeBuddy, Viewstats) tính tiền theo từng kênh và chỉ nhìn một kênh; công cụ gộp nhiều kênh (AgencyAnalytics, Coupler.io, Metricool) làm báo cáo cho agency, không lo vận hành đội. Không công cụ nào trong danh sách gộp được số liệu, doanh thu và thưởng đội trong một chỗ, bằng tiếng Việt, giá cố định theo gói thay vì nhân theo kênh.
- **Build chính xác cái gì:** bản đầu gồm kết nối Google từng kênh, tự đồng bộ số liệu, bảng tổng 10 kênh có giờ cập nhật, đánh dấu kênh tụt hoặc mất kết nối, và hỏi số liệu bằng lời qua AI (MCP). Chưa làm đăng video, theo dõi đối thủ hay app điện thoại.

## Phần 1. Market Research

### Tổng quan thị trường

Thị trường công cụ số liệu YouTube chia 4 nhóm, và cả 4 đều giả định hoặc một kênh, hoặc một agency lớn có người dựng báo cáo. YouTube Studio miễn phí nhưng mỗi lần chỉ xem được một kênh, nên ai chạy 10 kênh phải chuyển tài khoản 10 lần.

![Bản đồ thị trường: 4 nhóm công cụ và khoảng trống](images/ban-do-thi-truong.png)

Studio nhỏ nhiều kênh rơi vào giữa: quá nhiều kênh cho công cụ một kênh, quá nhỏ và quá thiếu người kỹ thuật cho công cụ agency và ống dữ liệu.

### Đối thủ chính và giá

Với 10 kênh, công cụ phổ biến nhất tốn khoảng 166 đến 200 USD mỗi tháng, hoặc bắt phải gọi sales để mua gói doanh nghiệp. Giá lấy từ trang giá và bài rà soát giá kiểm lại tháng 7 và 8/2026.

| Đối thủ | Nhóm | Giá (USD) | Nhiều kênh | Ước chi phí cho 10 kênh |
| --- | --- | --- | --- | --- |
| [vidIQ](https://1of10.com/blog/vidiq-pricing/) | Tăng trưởng 1 kênh | Boost 39/tháng hoặc 199/năm; Max 468/năm | Mỗi gói 1 kênh; nhiều kênh phải mua Enterprise, giá liên hệ | 10 gói Boost năm: khoảng 166/tháng |
| [TubeBuddy](https://1of10.com/blog/tubebuddy-pricing-review/) | Tăng trưởng 1 kênh | Pro 43,20/năm; Legend 278,28/năm | 1 license = 1 kênh; Legend có 2 chỗ người dùng | 10 gói Legend: khoảng 232/tháng |
| [Viewstats](https://outlierkit.com/resources/viewstats-pricing/) | Tăng trưởng, nghiên cứu | Pro 49,99/tháng; Business từ 249/tháng | Business cho team và agency, phải đặt lịch gọi | Business: từ 249/tháng |
| [AgencyAnalytics](https://agencyanalytics.com/pricing) | Báo cáo agency | 20 mỗi khách/tháng (trả năm) | Nhiều khách, dashboard white-label | 10 kênh tính là 10 khách: khoảng 200/tháng |
| [Metricool](https://metricool.com/pricing/) | Báo cáo đa nền tảng | Starter 16 đến 29 EUR/tháng (5 đến 10 brand) | Theo số brand | Starter 10 brand: khoảng 29 EUR/tháng |
| [Coupler.io](https://www.coupler.io/pricing) | Ống dữ liệu tự dựng | Starter 24, Active 99, Pro 199/tháng (trả năm) | Theo số tài khoản nguồn | Active (15 tài khoản): 99/tháng, còn phải tự dựng bảng |
| YouTube Studio + Looker Studio | Miễn phí | 0 | Studio xem từng kênh; Looker cần tự nối | 0 USD nhưng mất giờ dựng và sửa |

Cột chi phí 10 kênh là phép nhân từ giá công bố, chưa tính giảm giá theo vùng. [OverseerOS](https://www.overseeros.com/blog/best-multi-channel-youtube-analytics-tools) liệt kê thêm ChannelMeter, Tubular Labs, Sprout Social, Whatagraph và DashThis trong nhóm nhiều kênh.

### Teardown 4 cách làm đang có

Cả 4 đều giải được một mảnh, nhưng không cách nào trả lời được câu hỏi hằng ngày của chủ studio: 10 kênh hôm nay thế nào, kênh nào tụt, ai trong đội được thưởng bao nhiêu.

**1. vidIQ (công cụ tăng trưởng một kênh)**

- **Giải vấn đề gì:** giúp một creator tìm ý tưởng, từ khoá và tối ưu video để kênh lớn nhanh hơn.
- **Tính năng chính:** nghiên cứu từ khoá, theo dõi kênh khác, AI gợi ý tiêu đề và ý tưởng; gói trả phí tính bằng AI credit (Boost 2.000, Max 6.000 credit/tháng).
- **Cách hoạt động:** đăng nhập bằng một kênh, dùng qua web và tiện ích trình duyệt. Gói Boost, Max chỉ 1 kênh; nhiều kênh phải lên Enterprise.
- **Yếu với studio nhiều kênh:** không có bảng gộp nhiều kênh ở gói tự mua, không có vai trò cho đội, tập trung tăng trưởng chứ không vận hành.

**2. AgencyAnalytics (báo cáo cho agency)**

- **Giải vấn đề gì:** agency marketing phải gửi báo cáo định kỳ cho nhiều khách hàng mà không làm tay.
- **Tính năng chính:** hơn 85 nguồn dữ liệu (có YouTube), dashboard và báo cáo không giới hạn, white-label, không giới hạn người dùng nhân viên và khách.
- **Cách hoạt động:** mỗi khách hàng là một "client", nối tài khoản nguồn vào client đó, tính 20 USD mỗi client mỗi tháng.
- **Yếu với studio nhiều kênh:** dựng cho việc báo cáo gửi khách, không có thưởng đội, việc trong ngày hay cảnh báo kênh tụt theo kiểu studio cần; 10 kênh tốn khoảng 200 USD/tháng.

**3. Coupler.io + Looker Studio (ống dữ liệu tự dựng)**

- **Giải vấn đề gì:** kéo dữ liệu từ hơn 400 nguồn vào Google Sheets, Looker Studio hay BI để tự làm báo cáo.
- **Tính năng chính:** lịch làm mới theo ngày (gói Pro theo giờ), tính tiền theo số tài khoản nguồn.
- **Cách hoạt động:** mỗi kênh là một tài khoản nguồn, dữ liệu đổ vào bảng, rồi người dùng tự vẽ dashboard.
- **Yếu với studio nhiều kênh:** cần người biết dựng bảng; khi một kênh mất quyền thì số đứng im mà bảng không báo.

**4. Cách mình đang tự làm (đối thủ thật sự: làm tay)**

- **Hiện tại:** mở YouTube Studio từng kênh, bot Telegram báo doanh thu 3 giờ một lần, tiện ích ghi Google Sheet, khoảng 30 phút mỗi ngày.
- **Yếu:** số nằm rải rác ở Telegram, Sheet và app; bot từng báo đang chạy mà không ra kết quả; biết kênh tụt muộn vài ngày. Ngày 27/09/2026 mới 1 trên 10 kênh được nối vào YOUTUBE HQ.

### Market Gap Matrix

Khoảng trống lớn nhất nằm ở phần vận hành đội: thưởng theo view, cảnh báo kênh tụt và tiếng Việt. Phần "gộp số liệu nhiều kênh" thì đã có người làm, nhưng đắt hoặc phải tự dựng.

| Nhu cầu của studio 10 kênh | vidIQ | TubeBuddy | AgencyAnalytics | Coupler + Looker | YouTube Studio | YOUTUBE HQ |
| --- | --- | --- | --- | --- | --- | --- |
| Gộp nhiều kênh mà không cần gói doanh nghiệp | Không | Không | Có | Có, tự dựng | Không | Có |
| Mỗi kênh đăng nhập riêng, không dùng chung token | Chưa thấy | Chưa thấy | Chưa thấy | Chưa thấy | Có | Có |
| Vai trò đội, doanh thu chỉ quản trị thấy | Chưa thấy | 2 chỗ người dùng | Có người dùng nhân viên | Phụ thuộc người dựng | Theo quyền kênh | Có |
| Thưởng đội theo mốc view từng video | Chưa thấy | Chưa thấy | Chưa thấy | Chưa thấy | Không | Có |
| Cảnh báo kênh tụt hoặc mất kết nối | Chưa thấy | Chưa thấy | Chưa thấy | Không | Không | Đang làm |
| Hỏi số liệu bằng lời qua AI (MCP) | Chưa thấy | Chưa thấy | Chưa thấy | Không | Không | Có |
| Tiếng Việt, giá VND | Không | Không | Không | Không | Tiếng Việt | Có |
| Chi phí cho 10 kênh mỗi tháng (USD) | khoảng 166 | khoảng 232 | khoảng 200 | từ 99 + công dựng | 0 | khoảng 20 (đề xuất) |

"Chưa thấy" nghĩa là không thấy trong trang giá và bài rà soát đã mở, chưa dùng thử trực tiếp. Cột YOUTUBE HQ ghi theo app đang có trên máy (trang Thưởng, vai trò, MCP youtube-hq) và ticket HOA-8 cho cảnh báo.

## Phần 2. Product Direction

Hướng đã chốt: bảng vận hành cho studio YouTube Việt Nam nhiều kênh, bán theo gói cố định bằng VND, rẻ hơn khoảng 8 lần so với mua vidIQ cho từng kênh.

### ICP: khách hàng lý tưởng

- **Ai:** chủ studio YouTube ở Việt Nam, chạy 5 đến 20 kênh cho thị trường Mỹ, châu Âu; đội 2 đến 6 người gồm dựng, quay, phân tích.
- **Đặc điểm:** không có lập trình viên; trả lương hoặc thưởng cho đội theo view; sợ các kênh bị liên kết với nhau nên tách tài khoản Google cho từng kênh.
- **Không phải ICP:** creator một kênh (đã có vidIQ, TubeBuddy), agency marketing nhiều nền tảng (đã có AgencyAnalytics), MCN hàng trăm kênh.
- **Người dùng đầu tiên:** chính mình, 10 kênh, đội 4 người, đang mất khoảng 30 phút mỗi ngày.

### Họ đang gặp vấn đề gì

1. Phải mở YouTube Studio từng kênh, đổi tài khoản liên tục, không có một màn hình chung.
2. Kênh tụt view hoặc mất quyền truy cập thì biết muộn vài ngày.
3. Tính thưởng cho đội theo view làm tay trên Sheet, dễ sai và dễ cãi nhau.
4. Công cụ nước ngoài tính tiền theo kênh bằng USD: 10 kênh đã là 166 đến 232 USD mỗi tháng.

### Giá dự kiến (đề xuất, chưa kiểm bằng khách thật)

| Gói | Kênh | Người dùng | Giá/tháng |
| --- | --- | --- | --- |
| Miễn phí | 2 | 1 | 0 đ |
| Studio | 10 | 5 | 499.000 đ (khoảng 19 USD) |
| Team | 30 | 15 | 1.290.000 đ (khoảng 50 USD) |

Lý do: gói Studio cho 10 kênh bằng khoảng 1/8 chi phí mua vidIQ Boost cho 10 kênh và 1/10 AgencyAnalytics. Quy đổi theo tỷ giá khoảng 26.000 đ/USD.

### USP

**Một bảng cho cả studio: số liệu thật của mọi kênh, doanh thu và thưởng đội, mỗi kênh đăng nhập tách biệt, bằng tiếng Việt, giá theo gói chứ không nhân theo kênh.**

### Vì sao chọn YOUTUBE HQ thay vì cái đang có

1. **Rẻ khi nhiều kênh:** thêm kênh không nhân tiền; 10 kênh khoảng 19 USD so với 166 đến 232 USD.
2. **Lo vận hành, không chỉ báo cáo:** thưởng theo mốc view, vai trò đội, doanh thu chỉ quản trị thấy.
3. **An toàn cho nhiều kênh:** mỗi kênh chỉ đọc bằng đăng nhập của chính nó, quyền chỉ đọc, token nằm trên máy mình.
4. **Hỏi bằng lời:** hỏi Claude "kênh nào tụt tuần này" qua MCP, không cần biết dựng bảng.

Cần kiểm trước khi build tiếp: phỏng vấn 5 chủ studio để xác nhận vấn đề thưởng đội và mức giá 499.000 đ.

## Phần 3. Product Spec ban đầu

Bản đầu chỉ làm một việc cho tròn: chủ studio mở app là thấy 10 kênh hôm nay thế nào, và thấy ngay kênh nào bất thường. Spec 7 mục đầy đủ nằm trong repo sản phẩm (Private): `spec.md`.

### Các flow chính

**Flow 1. Luồng hằng ngày: số liệu tự về bảng**

![Flow 1: từ kết nối kênh tới thưởng đội](images/flow-chinh.png)

Nhánh lỗi quan trọng nhất là token hết hạn: kênh đó chuyển sang "mất kết nối" ngay trên bảng, không hiện số cũ như số mới.

**Flow 2. Kết nối kênh mới**

![Flow 2: kết nối kênh mới bằng đăng nhập Google riêng](images/flow-ket-noi-kenh.png)

Admin mở link kết nối trong hồ sơ Chrome riêng của từng kênh, để các tài khoản Google không đăng nhập chung một trình duyệt. Chọn nhầm tài khoản không có kênh hoặc huỷ quyền thì không lưu gì.

**Flow 3. Duyệt thưởng cuối tháng**

![Flow 3: duyệt thưởng theo mốc view](images/flow-duyet-thuong.png)

Thưởng chỉ thành tiền sau khi admin duyệt; thành viên thấy thưởng của mình nhưng không thấy doanh thu kênh.

### User story chính

1. Là chủ studio, tôi muốn kết nối mỗi kênh bằng đúng tài khoản Google của nó, để các kênh không dùng chung đăng nhập.
2. Là chủ studio, tôi muốn mở một màn hình thấy view, giờ xem, sub ròng, doanh thu 28 ngày của cả 10 kênh, để không phải mở Studio 10 lần.
3. Là chủ studio, tôi muốn kênh tụt, số cũ quá 12 giờ hoặc mất kết nối được đánh dấu ngay trên bảng, để xử lý trong ngày (báo qua Telegram là bước sau).
4. Là thành viên đội dựng, tôi muốn thấy video của mình đạt mốc view nào và thưởng bao nhiêu, nhưng không thấy doanh thu kênh.
5. Là chủ studio, tôi muốn hỏi Claude "kênh nào tụt tuần này" và nhận số thật, không cần tự dựng báo cáo.

### Tính năng người dùng và admin

| Tính năng | Ai dùng | Bản đầu |
| --- | --- | --- |
| Bảng tổng mọi kênh, giờ cập nhật cuối từng dòng | Quản trị, phân tích | Có |
| Chi tiết kênh: số liệu Studio, 10 video gần nhất | Quản trị, phân tích | Có |
| Thưởng của tôi theo mốc view | Dựng, quay | Có |
| Hỏi số liệu bằng lời qua MCP | Quản trị | Có |
| Kết nối, ngắt kết nối kênh Google | Admin | Có |
| Mời thành viên, gán vai trò, ẩn doanh thu với nhân viên | Admin | Có |
| Đặt mốc thưởng, duyệt thưởng cuối tháng | Admin | Có |
| Đặt ngưỡng cảnh báo, nơi nhận tin (Telegram) | Admin | Làm sau |
| Xem nhật ký đồng bộ và lỗi từng kênh | Admin | Có |
| Đăng, sửa, xoá video; theo dõi đối thủ; app điện thoại | Ai cũng không | Không làm đợt này |

### Kiến trúc

App chạy trên máy chủ studio (Electron), backend local giữ token từng kênh và chỉ trả lời chính máy đó, gọi YouTube Data API và Analytics API với quyền chỉ đọc. Sơ đồ kiến trúc đầy đủ có nhánh lỗi nằm trong repo sản phẩm (`docs/architecture.html`). Việc build đã chia thành 8 ticket trên Linear (HOA-5 đến HOA-12), mốc 04/10/2026.

## Nguồn

Các trang đã mở ngày 27/09/2026; giá có thể khác theo vùng.

- [vidIQ Pricing 2026, 1of10](https://1of10.com/blog/vidiq-pricing/) (kiểm giá tháng 7/2026)
- [TubeBuddy Pricing and Review, 1of10](https://1of10.com/blog/tubebuddy-pricing-review/) (kiểm giá tháng 7/2026)
- [ViewStats Pricing, OutlierKit](https://outlierkit.com/resources/viewstats-pricing/) (kiểm giá 06/08/2026)
- [AgencyAnalytics Pricing](https://agencyanalytics.com/pricing)
- [Metricool Pricing](https://metricool.com/pricing/)
- [Coupler.io Pricing](https://www.coupler.io/pricing)
- [10 Best Multi-Channel YouTube Analytics Tools, OverseerOS](https://www.overseeros.com/blog/best-multi-channel-youtube-analytics-tools)
- Số liệu nội bộ: bản nháp BTO-02 và BTO-04, MCP youtube-hq ngày 27/09/2026.
