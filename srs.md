# CAB SYSTEM – PHÂN TÍCH YÊU CẦU HỆ THỐNG

# BƯỚC 1. BUSINESS CONTEXT – BỐI CẢNH KINH DOANH

## 1.1. Business Context

Công ty ABC là doanh nghiệp cung cấp dịch vụ đặt xe trực tuyến. Hiện tại, khách hàng có thể yêu cầu xe thông qua tổng đài hoặc một ứng dụng đơn giản.

Tuy nhiên, hệ thống hiện tại còn nhiều hạn chế. Việc tìm và phân công tài xế chủ yếu được thực hiện thủ công, khách hàng khó theo dõi trạng thái chuyến đi, thông tin thanh toán chưa được quản lý tập trung và bộ phận vận hành gặp khó khăn khi số lượng khách hàng, tài xế và chuyến đi tăng.

Công ty ABC mong muốn xây dựng **CAB System** thành một nền tảng đặt xe mới hỗ trợ ba nhóm người dùng chính:

- Khách hàng.
- Tài xế.
- Nhân viên vận hành.

Ngoài ra, hệ thống có sự tham gia của nhà cung cấp thanh toán bên ngoài và người được phân quyền xem báo cáo.

Quy trình nghiệp vụ chính:

**Khách hàng tạo yêu cầu đặt xe → hệ thống tìm và phân công tài xế → tài xế thực hiện chuyến → hoàn thành chuyến → hệ thống tính cước → khách hàng thanh toán → khách hàng đánh giá tài xế.**

Ngoài các chức năng nghiệp vụ, hệ thống cần hỗ trợ quản lý vận hành, báo cáo, bảo mật, phân quyền, lưu vết và khả năng mở rộng.

Doanh nghiệp mong muốn các thành phần của hệ thống có thể phát triển và triển khai tương đối độc lập để trong tương lai có thể bổ sung loại dịch vụ, phương thức thanh toán hoặc kênh thông báo mới mà không phải xây dựng lại toàn bộ hệ thống.

## 1.2. Business Problem – Vấn đề kinh doanh

Hệ thống hiện tại tồn tại các vấn đề:

- Việc tìm và phân công tài xế chủ yếu được thực hiện thủ công.
- Khi số lượng yêu cầu chuyến tăng, việc điều phối tài xế trở nên khó khăn.
- Khách hàng khó theo dõi trạng thái hiện tại của chuyến đi.
- Khách hàng khó biết tài xế nào đã nhận chuyến và thời gian dự kiến tài xế đến.
- Thông tin thanh toán chưa được quản lý tập trung.
- Bộ phận vận hành gặp khó khăn trong việc theo dõi chuyến đi và xử lý sự cố.
- Hệ thống khó mở rộng khi số lượng người dùng và giao dịch tăng.
- Việc bổ sung chức năng mới có thể ảnh hưởng đến các chức năng đang hoạt động.

### Vấn đề chính cần giải quyết

Công ty ABC cần xây dựng CAB System nhằm:

- Tự động hóa quá trình tìm và phân công tài xế.
- Hỗ trợ khách hàng theo dõi chuyến đi.
- Quản lý thanh toán tập trung.
- Hỗ trợ hoạt động quản lý vận hành.
- Cung cấp báo cáo phục vụ quản lý.
- Đảm bảo khả năng mở rộng và phát triển lâu dài.

## 1.3. Trả lời các câu hỏi Business Context

### 1. Công ty ABC đang gặp vấn đề gì?

- Phân công tài xế chủ yếu thủ công.
- Khách hàng khó theo dõi chuyến.
- Thanh toán chưa được quản lý tập trung.
- Bộ phận vận hành khó theo dõi toàn bộ hoạt động.
- Hệ thống khó mở rộng khi quy mô tăng.
- Việc bổ sung chức năng mới còn khó khăn.

### 2. Vì sao hệ thống cũ không đáp ứng được?

- Chưa hỗ trợ tự động tìm tài xế phù hợp.
- Chưa hỗ trợ đầy đủ quá trình cập nhật trạng thái chuyến.
- Chưa quản lý tập trung thông tin thanh toán.
- Khả năng mở rộng còn hạn chế.

> Yêu cầu ban đầu không mô tả chi tiết kiến trúc của hệ thống cũ, vì vậy không kết luận hệ thống cũ sử dụng kiến trúc cụ thể nào.

### 3. Mục tiêu của hệ thống mới là gì?

- Tự động hóa tìm và phân công tài xế.
- Cho phép khách hàng theo dõi chuyến đi.
- Quản lý tập trung cước và thanh toán.
- Hỗ trợ quản lý vận hành.
- Cung cấp dữ liệu báo cáo.
- Bảo vệ dữ liệu người dùng và giao dịch.
- Hoạt động ổn định khi nhu cầu tăng.
- Cho phép mở rộng chức năng trong tương lai.

### 4. Ai sử dụng hoặc tương tác với hệ thống?

| Đối tượng | Vai trò chính |
|---|---|
| Khách hàng | Quản lý tài khoản, đặt xe, theo dõi chuyến, xem lịch sử, thanh toán, đánh giá |
| Tài xế | Quản lý hồ sơ, phương tiện, trạng thái hoạt động, phản hồi chuyến, cập nhật trạng thái chuyến |
| Nhân viên vận hành | Quản lý khách hàng, tài xế, phương tiện, chuyến, sự cố và giao dịch |
| Quản lý / Người được phân quyền | Xem báo cáo hoạt động |
| Nhà cung cấp thanh toán | Xử lý thanh toán điện tử |

---

# BƯỚC 2. STAKEHOLDER – CÁC BÊN LIÊN QUAN

## 2.1. Danh sách Stakeholder

| STT | Stakeholder | Vai trò |
|---:|---|---|
| 1 | Ban lãnh đạo | Đưa ra định hướng, xác nhận mục tiêu và theo dõi hiệu quả hoạt động của CAB System |
| 2 | Khách hàng | Sử dụng dịch vụ đặt xe, theo dõi chuyến, thanh toán và đánh giá |
| 3 | Tài xế | Nhận và thực hiện chuyến đi |
| 4 | Nhân viên vận hành | Quản lý và giám sát hoạt động vận hành |
| 5 | Nhà cung cấp thanh toán bên ngoài | Xử lý giao dịch thanh toán điện tử |
| 6 | Business Analyst | Thu thập, phân tích và làm rõ yêu cầu |

> Business Analyst là stakeholder của dự án nhưng không phải actor nghiệp vụ của CAB System.

## 2.2. Power – Interest

| Stakeholder | Power | Interest |
|---|---|---|
| Ban lãnh đạo | Cao | Cao |
| Business Analyst | Trung bình | Cao |
| Nhân viên vận hành | Trung bình | Cao |
| Khách hàng | Thấp | Cao |
| Tài xế | Thấp | Cao |
| Nhà cung cấp thanh toán | Trung bình | Thấp |

## 2.3. Stakeholder Matrix

- **Manage Closely:** Ban lãnh đạo.
- **Keep Satisfied:** Nhà cung cấp thanh toán.
- **Keep Informed:** Business Analyst, Nhân viên vận hành, Khách hàng, Tài xế.
- **Monitor:** Chưa xác định stakeholder phù hợp.

---

# BƯỚC 3. BUSINESS GOAL – MỤC TIÊU KINH DOANH

| Mã | Business Goal | Mô tả |
|---|---|---|
| BG01 | Nâng cao hiệu quả đặt xe | Giảm phụ thuộc vào quá trình phân công tài xế thủ công |
| BG02 | Nâng cao trải nghiệm khách hàng | Giúp khách hàng theo dõi chuyến và sử dụng dịch vụ thuận tiện |
| BG03 | Nâng cao hiệu quả quản lý thanh toán | Quản lý tập trung cước và thông tin thanh toán theo chuyến |
| BG04 | Nâng cao hiệu quả vận hành | Hỗ trợ nhân viên theo dõi và xử lý hoạt động của hệ thống |
| BG05 | Hỗ trợ quản lý và ra quyết định | Cung cấp báo cáo về chuyến, doanh thu và tài xế |
| BG06 | Hỗ trợ phát triển lâu dài | Đảm bảo khả năng mở rộng, bảo mật, ổn định và dễ thay đổi |

---

# BƯỚC 4. SCOPE – PHẠM VI

## 4.1. In-Scope

| STT | Hạng mục | Mô tả |
|---:|---|---|
| 1 | Quản lý tài khoản khách hàng | Đăng ký, đăng nhập, cập nhật thông tin cá nhân |
| 2 | Quản lý tài khoản tài xế | Tài xế đăng ký hoặc được nhân viên vận hành tạo tài khoản |
| 3 | Quản lý phương tiện | Tài xế cập nhật thông tin phương tiện |
| 4 | Quản lý trạng thái tài xế | Tài xế cập nhật trạng thái sẵn sàng |
| 5 | Đặt xe | Nhập điểm đón, điểm đến, chọn loại dịch vụ và tạo yêu cầu |
| 6 | Điều phối tài xế | Tìm, lọc, ưu tiên, gửi yêu cầu và phân công tài xế |
| 7 | Tìm tài xế thay thế | Tiếp tục tìm khi tài xế từ chối hoặc không phản hồi |
| 8 | Quản lý vị trí tài xế | Ghi nhận vị trí phục vụ điều phối và ETA |
| 9 | Theo dõi chuyến đi | Theo dõi tài xế, ETA và trạng thái chuyến |
| 10 | Thực hiện chuyến đi | Tài xế cập nhật trạng thái chuyến |
| 11 | Tính cước | Xác định số tiền khách hàng phải trả |
| 12 | Thanh toán | Hỗ trợ tiền mặt và thanh toán điện tử |
| 13 | Thông báo | Thông báo các sự kiện liên quan đến chuyến và thanh toán |
| 14 | Lịch sử chuyến | Khách hàng xem các chuyến đã thực hiện |
| 15 | Đánh giá tài xế | Khách hàng đánh giá sau khi chuyến hoàn thành |
| 16 | Quản lý vận hành | Quản lý khách hàng, tài xế, phương tiện, chuyến và giao dịch |
| 17 | Xử lý sự cố | Hỗ trợ xử lý chuyến có vấn đề |
| 18 | Báo cáo | Báo cáo chuyến, doanh thu, tỷ lệ hoàn thành/hủy và hiệu quả tài xế |
| 19 | Phân quyền | Kiểm soát quyền đối với chức năng quản trị |
| 20 | Audit Log | Lưu vết các thao tác quan trọng |

## 4.2. Out-of-Scope

| STT | Hạng mục |
|---:|---|
| 1 | Xây dựng cổng thanh toán riêng |
| 2 | Quản lý tuyển dụng tài xế |
| 3 | Quản lý hợp đồng lao động tài xế |
| 4 | Quản lý lương tài xế |
| 5 | Các loại dịch vụ tương lai chưa xác định |
| 6 | Các phương thức thanh toán tương lai chưa xác định |
| 7 | Các kênh thông báo tương lai chưa xác định |

---

# BƯỚC 5. BUSINESS REQUIREMENTS – YÊU CẦU NGHIỆP VỤ

| Mã | Business Requirement | Mô tả |
|---|---|---|
| BR01 | Quản lý tài khoản | Hỗ trợ tài khoản khách hàng, tài xế và nhân viên vận hành |
| BR02 | Quản lý yêu cầu đặt xe | Khách hàng tạo yêu cầu theo điểm đón, điểm đến và loại dịch vụ |
| BR03 | Điều phối tài xế | Hệ thống tự động tìm và phân công tài xế phù hợp |
| BR04 | Quản lý hoạt động tài xế | Tài xế quản lý trạng thái hoạt động và cập nhật quá trình thực hiện chuyến |
| BR05 | Theo dõi chuyến đi | Khách hàng theo dõi trạng thái và thông tin chuyến |
| BR06 | Tính cước | Hệ thống xác định số tiền khách hàng phải trả sau chuyến |
| BR07 | Thanh toán | Hỗ trợ tiền mặt và thanh toán điện tử |
| BR08 | Thông báo | Thông báo các sự kiện quan trọng cho khách hàng và tài xế |
| BR09 | Quản lý vận hành | Nhân viên vận hành theo dõi và quản lý hoạt động CAB System |
| BR10 | Báo cáo | Cung cấp báo cáo phục vụ quản lý |
| BR11 | Bảo mật và kiểm soát | Xác thực, phân quyền, bảo vệ dữ liệu và lưu vết |
| BR12 | Khả năng phát triển | Hỗ trợ mở rộng và thay đổi các thành phần trong tương lai |
| BR13 | Đánh giá tài xế | Khách hàng đánh giá tài xế sau khi chuyến hoàn thành |

---

# BƯỚC 6. BUSINESS PROCESS – QUY TRÌNH NGHIỆP VỤ

## 6.1. Quy trình chính

1. Khách hàng đăng nhập.
2. Khách hàng nhập điểm đón.
3. Khách hàng nhập điểm đến.
4. Khách hàng chọn loại dịch vụ.
5. Khách hàng gửi yêu cầu đặt xe.
6. Hệ thống kiểm tra thông tin.
7. Hệ thống tạo chuyến.
8. Hệ thống chuyển trạng thái chuyến thành `SEARCHING_DRIVER`.
9. Hệ thống tìm tài xế phù hợp.
10. Hệ thống ưu tiên tài xế phù hợp.
11. Hệ thống gửi yêu cầu chuyến cho tài xế.
12. Tài xế chấp nhận hoặc từ chối.
13. Nếu tài xế từ chối hoặc không phản hồi, hệ thống tiếp tục tìm tài xế khác.
14. Nếu không còn tài xế phù hợp, hệ thống chuyển chuyến sang `NO_DRIVER` và thông báo khách hàng.
15. Nếu tài xế chấp nhận, hệ thống gán tài xế cho chuyến.
16. Hệ thống chuyển trạng thái thành `DRIVER_ASSIGNED`.
17. Hệ thống hiển thị thông tin tài xế và ETA.
18. Tài xế di chuyển đến điểm đón.
19. Tài xế cập nhật `DRIVER_ARRIVED`.
20. Tài xế đón khách.
21. Tài xế cập nhật `PICKED_UP`.
22. Tài xế bắt đầu chuyến.
23. Tài xế cập nhật `IN_PROGRESS`.
24. Tài xế hoàn thành chuyến.
25. Tài xế cập nhật `COMPLETED`.
26. Hệ thống tính cước.
27. Khách hàng chọn phương thức thanh toán.
28. Hệ thống xử lý hoặc ghi nhận thanh toán.
29. Hệ thống thông báo kết quả thanh toán.
30. Khách hàng có thể đánh giá tài xế.
31. Hệ thống lưu chuyến vào lịch sử.

## 6.2. Trạng thái chuyến

```text
SEARCHING_DRIVER
→ DRIVER_ASSIGNED
→ DRIVER_ARRIVED
→ PICKED_UP
→ IN_PROGRESS
→ COMPLETED
```

Trạng thái kết thúc khác:

```text
CANCELLED
NO_DRIVER
```

> Chính sách hủy chuyến chi tiết vẫn cần được khách hàng xác nhận.

---

# BƯỚC 7. FUNCTIONAL REQUIREMENTS – YÊU CẦU CHỨC NĂNG

## 7.1. Identity & Account

| Mã | Functional Requirement |
|---|---|
| FR01 | Hệ thống cho phép khách hàng đăng ký tài khoản |
| FR02 | Hệ thống cho phép tài xế đăng ký tài khoản |
| FR03 | Hệ thống cho phép người dùng đăng nhập |
| FR04 | Hệ thống cho phép người dùng đăng xuất |
| FR05 | Hệ thống cho phép khách hàng cập nhật thông tin cá nhân |
| FR06 | Hệ thống cho phép tài xế cập nhật hồ sơ |
| FR07 | Hệ thống cho phép nhân viên vận hành tạo tài khoản tài xế |
| FR08 | Hệ thống cho phép tài xế cập nhật thông tin phương tiện |

## 7.2. Booking

| Mã | Functional Requirement |
|---|---|
| FR09 | Hệ thống cho phép khách hàng nhập điểm đón |
| FR10 | Hệ thống cho phép khách hàng nhập điểm đến |
| FR11 | Hệ thống cho phép khách hàng chọn loại dịch vụ |
| FR12 | Hệ thống cho phép khách hàng tạo yêu cầu đặt xe |
| FR13 | Hệ thống cho phép khách hàng hủy chuyến theo chính sách |
| FR14 | Hệ thống cho phép khách hàng xem lịch sử chuyến |
| FR15 | Hệ thống cho phép khách hàng xem chi tiết chuyến |

## 7.3. Driver & Location

| Mã | Functional Requirement |
|---|---|
| FR16 | Hệ thống cho phép tài xế cập nhật trạng thái sẵn sàng |
| FR17 | Hệ thống ghi nhận vị trí hiện tại của tài xế |
| FR18 | Hệ thống cho phép tài xế cập nhật trạng thái chuyến |

## 7.4. Dispatch – Tìm và phân công tài xế

| Mã | Functional Requirement |
|---|---|
| FR19 | Hệ thống xác định vị trí điểm đón |
| FR20 | Hệ thống lấy danh sách tài xế sẵn sàng |
| FR21 | Hệ thống lọc tài xế theo loại dịch vụ |
| FR22 | Hệ thống tính khoảng cách giữa tài xế và điểm đón |
| FR23 | Hệ thống xếp hạng tài xế theo tiêu chí ưu tiên |
| FR24 | Hệ thống gửi yêu cầu chuyến cho tài xế được chọn |
| FR25 | Hệ thống ghi nhận phản hồi của tài xế |
| FR26 | Hệ thống gán tài xế cho chuyến |
| FR27 | Hệ thống tìm tài xế khác khi tài xế từ chối |
| FR28 | Hệ thống tìm tài xế khác khi tài xế không phản hồi |
| FR29 | Hệ thống thông báo khi không tìm được tài xế |

### Logic xử lý Dispatch

```text
Xác định điểm đón
        ↓
Lấy tài xế sẵn sàng
        ↓
Lọc theo loại dịch vụ
        ↓
Tính khoảng cách
        ↓
Xếp hạng tài xế
        ↓
Chọn tài xế
        ↓
Gửi yêu cầu chuyến
        ↓
Tài xế phản hồi
   ┌───────────────┐
 Chấp nhận     Từ chối/Timeout
    ↓                ↓
Gán tài xế      Tìm tài xế khác
```

## 7.5. Trip

| Mã | Functional Requirement |
|---|---|
| FR30 | Hệ thống hiển thị thông tin tài xế cho khách hàng |
| FR31 | Hệ thống hiển thị thời gian dự kiến tài xế đến |
| FR32 | Hệ thống cho phép khách hàng theo dõi trạng thái chuyến |
| FR33 | Hệ thống ghi nhận trạng thái chuyến |
| FR34 | Hệ thống ghi nhận thời gian hoàn thành chuyến |

## 7.6. Fare & Payment

| Mã | Functional Requirement |
|---|---|
| FR35 | Hệ thống tính cước chuyến đi |
| FR36 | Hệ thống cho phép khách hàng chọn phương thức thanh toán |
| FR37 | Hệ thống ghi nhận thanh toán tiền mặt |
| FR38 | Hệ thống gửi yêu cầu thanh toán điện tử đến nhà cung cấp |
| FR39 | Hệ thống nhận kết quả thanh toán điện tử |
| FR40 | Hệ thống ghi nhận trạng thái giao dịch |
| FR41 | Hệ thống cho phép xử lý lại giao dịch thất bại theo chính sách |

## 7.7. Notification

| Mã | Functional Requirement |
|---|---|
| FR42 | Hệ thống thông báo khi yêu cầu đặt xe được tiếp nhận |
| FR43 | Hệ thống thông báo chuyến mới cho tài xế |
| FR44 | Hệ thống thông báo khi tài xế nhận chuyến |
| FR45 | Hệ thống thông báo khi tài xế đến điểm đón |
| FR46 | Hệ thống thông báo khi chuyến hoàn thành |
| FR47 | Hệ thống thông báo kết quả thanh toán |

## 7.8. Rating

| Mã | Functional Requirement |
|---|---|
| FR48 | Hệ thống cho phép khách hàng đánh giá tài xế sau chuyến |

## 7.9. Operation

| Mã | Functional Requirement |
|---|---|
| FR49 | Hệ thống cho phép nhân viên vận hành tra cứu khách hàng |
| FR50 | Hệ thống cho phép nhân viên vận hành tra cứu tài xế |
| FR51 | Hệ thống cho phép nhân viên vận hành cập nhật trạng thái tài xế theo quyền |
| FR52 | Hệ thống cho phép nhân viên vận hành tra cứu phương tiện |
| FR53 | Hệ thống cho phép nhân viên vận hành cập nhật trạng thái phương tiện theo quyền |
| FR54 | Hệ thống cho phép nhân viên vận hành xem chuyến đang diễn ra |
| FR55 | Hệ thống cho phép nhân viên vận hành xem trạng thái tài xế |
| FR56 | Hệ thống cho phép nhân viên vận hành xử lý chuyến gặp sự cố |
| FR57 | Hệ thống cho phép nhân viên vận hành tra cứu giao dịch |

## 7.10. Reporting

| Mã | Functional Requirement |
|---|---|
| FR58 | Hệ thống tạo báo cáo số lượng chuyến |
| FR59 | Hệ thống tạo báo cáo doanh thu |
| FR60 | Hệ thống tạo báo cáo tỷ lệ chuyến hoàn thành |
| FR61 | Hệ thống tạo báo cáo tỷ lệ chuyến hủy |
| FR62 | Hệ thống tạo báo cáo hiệu quả hoạt động tài xế |

## 7.11. Security & Audit

| Mã | Functional Requirement |
|---|---|
| FR63 | Hệ thống xác thực người dùng |
| FR64 | Hệ thống kiểm tra quyền truy cập |
| FR65 | Hệ thống giới hạn thao tác quản trị nhạy cảm |
| FR66 | Hệ thống lưu vết thao tác quan trọng |

---

# BƯỚC 8. BUSINESS RULES & BUSINESS EXCEPTIONS

## 8.1. Business Rules

| Mã | Business Rule |
|---|---|
| BRL01 | Khách hàng và tài xế phải được xác thực trước khi sử dụng chức năng yêu cầu tài khoản |
| BRL02 | Chỉ tài xế có trạng thái sẵn sàng mới được đưa vào quá trình tìm tài xế |
| BRL03 | Tài xế phải có phương tiện phù hợp với loại dịch vụ |
| BRL04 | Việc ưu tiên tài xế dựa trên vị trí và các tiêu chí vận hành |
| BRL05 | Một chuyến tại một thời điểm chỉ được gán cho một tài xế |
| BRL06 | Khi tài xế chấp nhận, hệ thống gán tài xế cho chuyến |
| BRL07 | Khi tài xế từ chối, hệ thống tiếp tục tìm tài xế khác |
| BRL08 | Khi tài xế không phản hồi đúng thời hạn, hệ thống tiếp tục tìm tài xế khác |
| BRL09 | Khách hàng không cần tạo lại chuyến khi hệ thống tìm tài xế thay thế |
| BRL10 | Nếu không tìm được tài xế, khách hàng phải được thông báo |
| BRL11 | Tài xế cập nhật trạng thái chuyến theo tiến trình thực hiện |
| BRL12 | Chỉ chuyến hoàn thành mới thực hiện tính cước cuối cùng |
| BRL13 | Khách hàng có thể thanh toán tiền mặt hoặc thanh toán điện tử |
| BRL14 | Thanh toán điện tử phải được xử lý qua nhà cung cấp bên ngoài |
| BRL15 | CAB System không lưu trực tiếp thông tin thanh toán nhạy cảm |
| BRL16 | Chỉ chuyến hoàn thành mới được đánh giá |
| BRL17 | Các thao tác quản trị nhạy cảm yêu cầu quyền phù hợp |
| BRL18 | Các thao tác quan trọng phải được lưu vết |

## 8.2. Business Exceptions

| Mã | Ngoại lệ | Xử lý |
|---|---|---|
| BE01 | Thông tin đặt xe không hợp lệ | Thông báo và yêu cầu kiểm tra |
| BE02 | Không có tài xế phù hợp | Thông báo khách hàng |
| BE03 | Tài xế từ chối | Tìm tài xế tiếp theo |
| BE04 | Tài xế không phản hồi | Tìm tài xế tiếp theo |
| BE05 | Thanh toán thất bại | Ghi nhận, thông báo và cho phép xử lý lại |
| BE06 | Không kết nối nhà cung cấp thanh toán | Ghi nhận lỗi, không làm dừng chức năng đặt xe |
| BE07 | Chức năng thông báo gặp lỗi | Ghi nhận lỗi, không làm dừng nghiệp vụ chính |
| BE08 | Khách hàng hủy chuyến | Xử lý theo chính sách hủy |
| BE09 | Tài xế gặp sự cố | Nhân viên vận hành hỗ trợ xử lý |
| BE10 | Mất kết nối mạng | Xử lý theo chính sách đồng bộ TBD |
| BE11 | Không nhận được vị trí tài xế | Xử lý theo chính sách TBD |
| BE12 | Chuyến có trạng thái bất thường | Nhân viên vận hành xử lý |

## 8.3. Các vấn đề TBD

- Công thức tính cước.
- Bán kính tìm tài xế.
- Tiêu chí ưu tiên tài xế.
- Thời gian tài xế phản hồi.
- Cơ chế gửi yêu cầu cho một hoặc nhiều tài xế.
- Chính sách hủy chuyến.
- Số lần xử lý lại thanh toán.
- Xử lý khi mất kết nối.
- Thời gian lưu dữ liệu vị trí.
- Thời gian lưu dữ liệu giao dịch.
- Thời gian lưu Audit Log.

---

# BƯỚC 9. DATA MODEL – ERD

## 9.1. User

```text
User(
    user_id PK,
    full_name,
    email,
    phone,
    password_hash,
    user_type,
    status,
    created_at,
    updated_at
)
```

## 9.2. Customer

```text
Customer(
    customer_id PK,
    user_id FK
)
```

## 9.3. Driver

```text
Driver(
    driver_id PK,
    user_id FK,
    availability_status
)
```

## 9.4. Staff

```text
Staff(
    staff_id PK,
    user_id FK,
    role_id FK
)
```

## 9.5. Role

```text
Role(
    role_id PK,
    role_name,
    description
)
```

## 9.6. ServiceType

```text
ServiceType(
    service_type_id PK,
    service_name,
    description,
    status
)
```

## 9.7. Vehicle

```text
Vehicle(
    vehicle_id PK,
    driver_id FK,
    service_type_id FK,
    license_plate,
    vehicle_name,
    status
)
```

## 9.8. Trip

```text
Trip(
    trip_id PK,
    customer_id FK,
    driver_id FK NULL,
    service_type_id FK,

    pickup_address,
    pickup_latitude,
    pickup_longitude,

    destination_address,
    destination_latitude,
    destination_longitude,

    trip_status,
    estimated_arrival_time,
    fare_amount,

    created_at,
    assigned_at,
    arrived_at,
    picked_up_at,
    started_at,
    completed_at,
    cancelled_at
)
```

> `driver_id` cho phép `NULL` vì khi khách hàng vừa tạo chuyến thì hệ thống chưa phân công tài xế.

## 9.9. DriverRequest

```text
DriverRequest(
    request_id PK,
    trip_id FK,
    driver_id FK,
    request_status,
    requested_at,
    responded_at,
    expired_at
)
```

Các giá trị `request_status`:

```text
PENDING
ACCEPTED
REJECTED
TIMEOUT
```

## 9.10. DriverLocation

```text
DriverLocation(
    location_id PK,
    driver_id FK,
    latitude,
    longitude,
    recorded_at
)
```

## 9.11. Payment

```text
Payment(
    payment_id PK,
    trip_id FK,
    amount,
    payment_method,
    payment_status,
    external_transaction_id,
    created_at,
    paid_at
)
```

Các giá trị `payment_method`:

```text
CASH
ELECTRONIC
```

Các giá trị `payment_status`:

```text
PENDING
SUCCESS
FAILED
```

## 9.12. Rating

```text
Rating(
    rating_id PK,
    trip_id FK,
    customer_id FK,
    driver_id FK,
    score,
    comment,
    created_at
)
```

## 9.13. Notification

```text
Notification(
    notification_id PK,
    trip_id FK NULL,
    receiver_id,
    receiver_type,
    notification_type,
    content,
    status,
    created_at,
    sent_at
)
```

## 9.14. AuditLog

```text
AuditLog(
    log_id PK,
    actor_id,
    actor_type,
    action,
    entity_type,
    entity_id,
    created_at
)
```

## 9.15. Quan hệ chính

```text
User 1 --- 0..1 Customer
User 1 --- 0..1 Driver
User 1 --- 0..1 Staff

Role 1 --- N Staff

Driver 1 --- N Vehicle
ServiceType 1 --- N Vehicle

Customer 1 --- N Trip
Driver 1 --- N Trip
ServiceType 1 --- N Trip

Trip 1 --- N DriverRequest
Driver 1 --- N DriverRequest

Driver 1 --- N DriverLocation

Trip 1 --- N Payment
Trip 1 --- 0..1 Rating
```

---

# BƯỚC 10. NON-FUNCTIONAL REQUIREMENTS – YÊU CẦU PHI CHỨC NĂNG

| Mã | Nhóm | Non-Functional Requirement |
|---|---|---|
| NFR01 | Scalability | Hệ thống phải hỗ trợ tăng số lượng khách hàng, tài xế và chuyến |
| NFR02 | Scalability | Các thành phần chính phải có khả năng mở rộng độc lập |
| NFR03 | Availability | Hệ thống phải duy trì hoạt động ổn định trong thời điểm nhu cầu cao |
| NFR04 | Fault Tolerance | Lỗi ở chức năng thanh toán không được làm chức năng đặt xe ngừng hoạt động |
| NFR05 | Fault Tolerance | Lỗi ở chức năng thông báo không được làm chức năng đặt xe ngừng hoạt động |
| NFR06 | Deployability | Chức năng mới phải có thể triển khai từng phần với ảnh hưởng hạn chế |
| NFR07 | Authentication | Người dùng phải được xác thực trước khi truy cập chức năng yêu cầu tài khoản |
| NFR08 | Authorization | Chức năng quản trị phải được kiểm soát theo quyền |
| NFR09 | Data Security | Dữ liệu cá nhân phải được bảo vệ |
| NFR10 | Data Security | Dữ liệu vị trí và phương tiện phải được bảo vệ |
| NFR11 | Payment Security | Không lưu trực tiếp dữ liệu thanh toán nhạy cảm |
| NFR12 | Auditability | Hệ thống phải lưu vết thao tác quan trọng |
| NFR13 | Extensibility | Hệ thống phải cho phép thêm loại dịch vụ mới |
| NFR14 | Extensibility | Hệ thống phải cho phép thêm phương thức hoặc nhà cung cấp thanh toán |
| NFR15 | Extensibility | Hệ thống phải cho phép thêm kênh hoặc nhà cung cấp thông báo |
| NFR16 | Maintainability | Thay đổi một thành phần phải hạn chế ảnh hưởng đến thành phần khác |

### Các giá trị TBD

- Số lượng người dùng đồng thời.
- Thời gian phản hồi.
- Throughput.
- Uptime.
- Timeout.
- Retry Policy.

---

# BƯỚC 11. USE CASE DIAGRAM

## 11.1. Actor

| Actor | Vai trò |
|---|---|
| Khách hàng | Đăng ký, đăng nhập, đặt xe, theo dõi, hủy, thanh toán, đánh giá |
| Tài xế | Đăng ký, đăng nhập, cập nhật hồ sơ, phương tiện, trạng thái, phản hồi và thực hiện chuyến |
| Nhân viên vận hành | Đăng nhập, tạo tài khoản tài xế, quản lý và giám sát hoạt động |
| Quản lý  | Xem báo cáo |
| Nhà cung cấp thanh toán | Xử lý thanh toán điện tử |

> CAB System không phải actor của chính nó.

## 11.2. Danh sách Use Case

### A. Use Case dùng chung

| Mã | Use Case | Actor |
|---|---|---|
| UC01 | Đăng nhập | Khách hàng, Tài xế, Nhân viên vận hành |

### B. Khách hàng

| Mã | Use Case |
|---|---|
| UC02 | Đăng ký tài khoản khách hàng |
| UC03 | Cập nhật thông tin cá nhân |
| UC04 | Đặt xe |
| UC05 | Theo dõi chuyến đi |
| UC06 | Hủy chuyến |
| UC07 | Xem lịch sử chuyến đi |
| UC08 | Đánh giá tài xế |
| UC09 | Thanh toán chuyến |

### C. Tài xế

| Mã | Use Case |
|---|---|
| UC10 | Đăng ký tài khoản tài xế |
| UC11 | Cập nhật hồ sơ |
| UC12 | Cập nhật phương tiện |
| UC13 | Cập nhật trạng thái tài xế |
| UC14 | Phản hồi yêu cầu chuyến |
| UC15 | Cập nhật trạng thái chuyến đi |

### D. Nhân viên vận hành

| Mã | Use Case |
|---|---|
| UC16 | Tạo tài khoản tài xế |
| UC17 | Quản lý khách hàng |
| UC18 | Quản lý tài xế |
| UC19 | Quản lý phương tiện |
| UC20 | Theo dõi chuyến |
| UC21 | Kiểm tra trạng thái tài xế |
| UC22 | Xử lý chuyến gặp sự cố |
| UC23 | Tra cứu giao dịch |

### E. Quản lý

| Mã | Use Case |
|---|---|
| UC24 | Xem báo cáo |

## 11.3. Quy tắc khi vẽ Use Case

- Dùng một Use Case **Đăng nhập** cho Khách hàng, Tài xế và Nhân viên vận hành.
- Không nối mọi chức năng với Đăng nhập bằng `<<include>>`.
- Điều kiện “đã đăng nhập” được ghi trong tiền điều kiện của Use Case.
- Không dùng `Đăng ký <<extend>> Đăng nhập`.
- Nhà cung cấp thanh toán nối với `UC09 – Thanh toán chuyến`.
- “Tìm và phân công tài xế” được mô tả trong `UC04 – Đặt xe` và nhóm FR Dispatch để sơ đồ tổng thể không quá rối.

---
## Mô hình Usecase Diagram
<img width="1710" height="1244" alt="image" src="https://github.com/user-attachments/assets/673eaa42-a64d-46b0-89b7-8c73257041cc" />
--

# BƯỚC 12. ĐẶC TẢ USE CASE CHÍNH

## UC04. Đặt xe

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC04 |
| Tên Use Case | Đặt xe |
| Actor chính | Khách hàng |
| Tiền điều kiện | Khách hàng đã đăng nhập |
| Hậu điều kiện thành công | Chuyến được tạo và tài xế được phân công |
| Hậu điều kiện thất bại | Chuyến không được tạo hoặc chuyển sang `NO_DRIVER` |

### Basic Flow

| Actor | System |
|---|---|
| 1. Chọn chức năng đặt xe | 2. Hiển thị giao diện đặt xe |
| 3. Nhập điểm đón | |
| 4. Nhập điểm đến | |
| 5. Chọn loại dịch vụ | |
| 6. Xác nhận đặt xe | 7. Kiểm tra thông tin |
| | 8. Tạo chuyến |
| | 9. Cập nhật `SEARCHING_DRIVER` |
| | 10. Thông báo tiếp nhận yêu cầu |
| | 11. Tìm tài xế phù hợp |
| | 12. Gửi yêu cầu chuyến |
| | 13. Nhận phản hồi tài xế |
| | 14. Gán tài xế |
| | 15. Cập nhật `DRIVER_ASSIGNED` |
| | 16. Hiển thị thông tin tài xế và ETA |

### Alternative Flow – Tài xế từ chối

1. Tài xế từ chối yêu cầu.
2. Hệ thống ghi nhận `REJECTED`.
3. Hệ thống chọn tài xế tiếp theo.
4. Hệ thống gửi yêu cầu chuyến mới.
5. Luồng quay lại bước 13 của Basic Flow.

### Alternative Flow – Tài xế không phản hồi

1. Hết thời gian phản hồi.
2. Hệ thống ghi nhận `TIMEOUT`.
3. Hệ thống chọn tài xế tiếp theo.
4. Hệ thống gửi yêu cầu chuyến mới.
5. Luồng quay lại bước 13 của Basic Flow.

### Exception Flow – Không tìm được tài xế

1. Hệ thống không còn tài xế phù hợp.
2. Hệ thống cập nhật `NO_DRIVER`.
3. Hệ thống thông báo khách hàng.
4. Use Case kết thúc.

---

## UC14. Phản hồi yêu cầu chuyến

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC14 |
| Tên Use Case | Phản hồi yêu cầu chuyến |
| Actor chính | Tài xế |
| Tiền điều kiện | Tài xế đã đăng nhập, đang sẵn sàng và nhận được yêu cầu chuyến |
| Hậu điều kiện | Phản hồi của tài xế được ghi nhận |

### Basic Flow

| Actor | System |
|---|---|
| | 1. Gửi yêu cầu chuyến |
| 2. Xem thông tin chuyến | |
| 3. Chọn chấp nhận | 4. Ghi nhận `ACCEPTED` |
| | 5. Gán tài xế |
| | 6. Cập nhật `DRIVER_ASSIGNED` |
| | 7. Thông báo khách hàng |

### Alternative Flow – Từ chối

1. Tài xế chọn từ chối.
2. Hệ thống ghi nhận `REJECTED`.
3. Hệ thống tiếp tục tìm tài xế khác.

### Exception Flow – Không phản hồi

1. Tài xế không phản hồi trong thời hạn quy định.
2. Hệ thống ghi nhận `TIMEOUT`.
3. Hệ thống tiếp tục tìm tài xế khác.

---

## UC15. Cập nhật trạng thái chuyến đi

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC15 |
| Tên Use Case | Cập nhật trạng thái chuyến đi |
| Actor chính | Tài xế |
| Tiền điều kiện | Tài xế đã được gán cho chuyến |
| Hậu điều kiện | Trạng thái mới của chuyến được ghi nhận |

### Basic Flow

| Actor | System |
|---|---|
| 1. Xác nhận đã đến điểm đón | 2. Ghi nhận `DRIVER_ARRIVED` |
| | 3. Thông báo khách hàng |
| 4. Xác nhận đã đón khách | 5. Ghi nhận `PICKED_UP` |
| 6. Xác nhận bắt đầu chuyến | 7. Ghi nhận `IN_PROGRESS` |
| 8. Xác nhận hoàn thành | 9. Ghi nhận `COMPLETED` |
| | 10. Ghi nhận thời gian hoàn thành |
| | 11. Tính cước |
| | 12. Thông báo chuyến hoàn thành |

---

## UC09. Thanh toán chuyến

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC09 |
| Tên Use Case | Thanh toán chuyến |
| Actor chính | Khách hàng |
| Actor phụ | Nhà cung cấp thanh toán |
| Tiền điều kiện | Chuyến đã `COMPLETED` và hệ thống đã tính cước |
| Hậu điều kiện | Kết quả thanh toán được ghi nhận |

### Basic Flow – Thanh toán điện tử

| Actor | System |
|---|---|
| 1. Mở chức năng thanh toán | 2. Hiển thị số tiền |
| 3. Chọn thanh toán điện tử | |
| 4. Xác nhận thanh toán | 5. Tạo giao dịch `PENDING` |
| | 6. Gửi yêu cầu đến nhà cung cấp thanh toán |
| Nhà cung cấp xử lý giao dịch | |
| Nhà cung cấp trả kết quả | 7. Nhận kết quả |
| | 8. Cập nhật `SUCCESS` |
| | 9. Thông báo thành công |

### Alternative Flow – Tiền mặt

1. Khách hàng chọn tiền mặt.
2. Hệ thống ghi nhận phương thức `CASH`.
3. Hệ thống ghi nhận thông tin thanh toán.

### Exception Flow – Thanh toán thất bại

1. Nhà cung cấp trả kết quả thất bại.
2. Hệ thống ghi nhận `FAILED`.
3. Hệ thống thông báo khách hàng.
4. Khách hàng có thể thực hiện lại theo chính sách.

---

## UC08. Đánh giá tài xế

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC08 |
| Tên Use Case | Đánh giá tài xế |
| Actor chính | Khách hàng |
| Tiền điều kiện | Chuyến có trạng thái `COMPLETED` |
| Hậu điều kiện | Đánh giá được lưu |

### Basic Flow

1. Khách hàng mở chuyến đã hoàn thành.
2. Khách hàng chọn đánh giá.
3. Hệ thống hiển thị giao diện đánh giá.
4. Khách hàng nhập điểm đánh giá.
5. Khách hàng nhập nhận xét nếu có.
6. Khách hàng gửi đánh giá.
7. Hệ thống kiểm tra dữ liệu.
8. Hệ thống lưu đánh giá.
9. Hệ thống thông báo thành công.

---

# BƯỚC 13. ACCEPTANCE CRITERIA – TIÊU CHÍ CHẤP NHẬN

## 13.1. Account

| Mã | Tiêu chí chấp nhận |
|---|---|
| AC01 | Thông tin hợp lệ thì tài khoản khách hàng được tạo thành công |
| AC02 | Thông tin hợp lệ thì tài khoản tài xế được tạo thành công |
| AC03 | Email hoặc số điện thoại đã tồn tại thì hệ thống không tạo tài khoản trùng |
| AC04 | Thông tin đăng nhập đúng thì đăng nhập thành công |
| AC05 | Thông tin đăng nhập sai thì hệ thống thông báo lỗi |
| AC06 | Thông tin cập nhật hợp lệ thì dữ liệu mới được lưu |
| AC07 | Nhân viên vận hành có quyền phù hợp thì tạo được tài khoản tài xế |

## 13.2. Booking & Dispatch

| Mã | Tiêu chí chấp nhận |
|---|---|
| AC08 | Thông tin đặt xe hợp lệ thì hệ thống tạo được chuyến |
| AC09 | Chuyến mới có trạng thái `SEARCHING_DRIVER` |
| AC10 | Chỉ tài xế `AVAILABLE` được đưa vào danh sách tìm kiếm |
| AC11 | Tài xế phải có phương tiện phù hợp loại dịch vụ |
| AC12 | Hệ thống xác định khoảng cách phục vụ xếp hạng tài xế |
| AC13 | Tài xế được chọn nhận được yêu cầu chuyến |
| AC14 | Tài xế chấp nhận thì được gán cho chuyến |
| AC15 | Tài xế từ chối thì hệ thống tiếp tục tìm tài xế khác |
| AC16 | Tài xế không phản hồi thì hệ thống tiếp tục tìm tài xế khác |
| AC17 | Không còn tài xế phù hợp thì chuyển `NO_DRIVER` và thông báo khách hàng |

## 13.3. Trip

| Mã | Tiêu chí chấp nhận |
|---|---|
| AC18 | Sau khi gán tài xế, khách hàng xem được thông tin tài xế |
| AC19 | Khách hàng xem được ETA |
| AC20 | Tài xế cập nhật được `DRIVER_ARRIVED` |
| AC21 | Tài xế cập nhật được `PICKED_UP` |
| AC22 | Tài xế cập nhật được `IN_PROGRESS` |
| AC23 | Tài xế cập nhật được `COMPLETED` |
| AC24 | Khách hàng xem được trạng thái hiện tại của chuyến |

## 13.4. Payment

| Mã | Tiêu chí chấp nhận |
|---|---|
| AC25 | Chuyến hoàn thành thì hệ thống tính được cước theo quy tắc được cấu hình |
| AC26 | Khách hàng chọn được tiền mặt hoặc thanh toán điện tử |
| AC27 | Thanh toán điện tử được gửi đến nhà cung cấp |
| AC28 | Thanh toán thành công thì Payment chuyển `SUCCESS` |
| AC29 | Thanh toán thất bại thì Payment chuyển `FAILED` |
| AC30 | Thanh toán thất bại thì khách hàng được thông báo |
| AC31 | CAB System không lưu trực tiếp dữ liệu thanh toán nhạy cảm |

## 13.5. Rating

| Mã | Tiêu chí chấp nhận |
|---|---|
| AC32 | Chỉ chuyến `COMPLETED` mới được đánh giá |
| AC33 | Đánh giá hợp lệ được lưu thành công |

## 13.6. Operation & Security

| Mã | Tiêu chí chấp nhận |
|---|---|
| AC34 | Nhân viên chỉ truy cập chức năng phù hợp quyền |
| AC35 | Nhân viên vận hành tra cứu được khách hàng |
| AC36 | Nhân viên vận hành xem được chuyến đang thực hiện |
| AC37 | Nhân viên vận hành xem được trạng thái tài xế |
| AC38 | Nhân viên vận hành tra cứu được giao dịch |
| AC39 | Thao tác quản trị quan trọng được lưu Audit Log |
| AC40 | Người không đủ quyền bị từ chối thao tác nhạy cảm |

## 13.7. Reporting

| Mã | Tiêu chí chấp nhận |
|---|---|
| AC41 | Người có quyền xem được báo cáo số lượng chuyến |
| AC42 | Người có quyền xem được báo cáo doanh thu |
| AC43 | Người có quyền xem được tỷ lệ chuyến hoàn thành |
| AC44 | Người có quyền xem được tỷ lệ chuyến hủy |
| AC45 | Người có quyền xem được báo cáo hiệu quả tài xế |

## 13.8. Fault Tolerance

| Mã | Tiêu chí chấp nhận |
|---|---|
| AC46 | Lỗi thanh toán không làm chức năng đặt xe dừng hoạt động |
| AC47 | Lỗi thông báo không làm chức năng đặt xe dừng hoạt động |

---

# BƯỚC 14. REQUIREMENT TRACEABILITY MATRIX – RTM

| Business Goal | Business Requirement | FR / NFR | Use Case | Acceptance Criteria |
|---|---|---|---|---|
| BG01, BG06 | BR01 | FR01–FR08, FR63–FR64 | UC01, UC02, UC03, UC10, UC11, UC12, UC16 | AC01–AC07 |
| BG01 | BR02 | FR09–FR15 | UC04, UC06, UC07 | AC08–AC09 |
| BG01 | BR03 | FR19–FR29 | UC04, UC14 | AC10–AC17 |
| BG02 | BR04 | FR16–FR18 | UC13, UC14, UC15 | AC20–AC23 |
| BG02 | BR05 | FR30–FR34 | UC05, UC15 | AC18–AC24 |
| BG03 | BR06 | FR35 | UC09 | AC25 |
| BG03 | BR07 | FR36–FR41 | UC09 | AC26–AC31 |
| BG02 | BR08 | FR42–FR47 | UC04, UC14, UC15, UC09 | AC13, AC18, AC20, AC23, AC30 |
| BG04 | BR09 | FR49–FR57 | UC17–UC23 | AC34–AC40 |
| BG05 | BR10 | FR58–FR62 | UC24 | AC41–AC45 |
| BG06 | BR11 | FR63–FR66, NFR07–NFR12 | UC01, UC17–UC24 | AC34, AC39, AC40 |
| BG06 | BR12 | NFR01–NFR06, NFR13–NFR16 | Không áp dụng trực tiếp | AC46–AC47 |
| BG02 | BR13 | FR48 | UC08 | AC32–AC33 |
