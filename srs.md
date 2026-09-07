# CAB SYSTEM – PHÂN TÍCH YÊU CẦU HỆ THỐNG

# BƯỚC 1. BUSINESS CONTEXT – BỐI CẢNH KINH DOANH

## 1.1. Business Context

Công ty ABC là doanh nghiệp cung cấp dịch vụ đặt xe trực tuyến. Hiện tại, khách hàng có thể yêu cầu xe thông qua tổng đài hoặc một ứng dụng đơn giản.

Tuy nhiên, hệ thống hiện tại còn nhiều hạn chế. Việc tìm và phân công tài xế chủ yếu được thực hiện thủ công, khách hàng khó theo dõi trạng thái chuyến đi, thông tin thanh toán chưa được quản lý tập trung và bộ phận vận hành gặp khó khăn khi số lượng khách hàng, tài xế và chuyến đi tăng.

Công ty ABC mong muốn xây dựng **CAB System** thành một nền tảng đặt xe mới hỗ trợ ba nhóm người dùng chính:

* Khách hàng
* Tài xế
* Nhân viên vận hành

CAB System cần hỗ trợ quy trình nghiệp vụ xuyên suốt:

**Khách hàng tạo yêu cầu đặt xe → hệ thống tìm tài xế → tài xế nhận chuyến → thực hiện chuyến → hoàn thành chuyến → tính cước → thanh toán → đánh giá tài xế.**

Ngoài các chức năng nghiệp vụ, hệ thống phải hỗ trợ quản lý vận hành, báo cáo, bảo mật, phân quyền, lưu vết và khả năng mở rộng.

Doanh nghiệp cũng mong muốn các thành phần của hệ thống có thể phát triển và triển khai tương đối độc lập để trong tương lai có thể bổ sung loại dịch vụ, phương thức thanh toán hoặc kênh thông báo mới mà không phải xây dựng lại toàn bộ hệ thống.

---

## 1.2. Business Problem – Vấn đề kinh doanh

Hệ thống hiện tại của Công ty ABC tồn tại các vấn đề sau:

* Việc tìm và phân công tài xế chủ yếu được thực hiện thủ công.
* Khi số lượng yêu cầu chuyến tăng, việc điều phối tài xế trở nên khó khăn.
* Khách hàng khó theo dõi trạng thái hiện tại của chuyến đi.
* Khách hàng khó biết tài xế nào đã nhận chuyến và thời gian dự kiến tài xế đến.
* Thông tin thanh toán chưa được quản lý tập trung.
* Bộ phận vận hành gặp khó khăn trong việc theo dõi chuyến đi và xử lý sự cố.
* Hệ thống hiện tại khó mở rộng khi số lượng người dùng và giao dịch tăng.
* Việc bổ sung chức năng mới có thể ảnh hưởng đến các chức năng đang hoạt động.

### Vấn đề chính cần giải quyết

Công ty ABC cần xây dựng một nền tảng CAB mới nhằm:

* Tự động hóa quá trình tìm và phân công tài xế.
* Hỗ trợ khách hàng theo dõi chuyến đi.
* Quản lý thanh toán tập trung.
* Hỗ trợ hoạt động quản lý vận hành.
* Đảm bảo hệ thống có khả năng mở rộng và phát triển lâu dài.

---

## 1.3. Trả lời các câu hỏi Business Context

### 1. Công ty ABC đang gặp vấn đề gì?

* Việc phân công tài xế đang thực hiện chủ yếu bằng phương pháp thủ công.
* Khách hàng khó theo dõi tình trạng chuyến đi.
* Thông tin thanh toán chưa được quản lý tập trung.
* Bộ phận vận hành khó theo dõi toàn bộ hoạt động.
* Hệ thống khó mở rộng khi số lượng người dùng và chuyến đi tăng.
* Việc bổ sung chức năng mới còn khó khăn.

### 2. Vì sao hệ thống cũ không đáp ứng được?

* Chưa hỗ trợ tự động tìm tài xế phù hợp.
* Chưa hỗ trợ đầy đủ quá trình cập nhật trạng thái chuyến.
* Chưa quản lý tập trung thông tin thanh toán.
* Khả năng mở rộng còn hạn chế.
* Các chức năng chưa được tách biệt đủ để có thể thay đổi hoặc mở rộng độc lập.

> Yêu cầu ban đầu không mô tả chi tiết kiến trúc của hệ thống cũ, vì vậy không kết luận hệ thống cũ sử dụng kiến trúc cụ thể nào.

### 3. Mục tiêu của hệ thống mới là gì?

* Tự động hóa quá trình tìm và phân công tài xế.
* Cho phép khách hàng theo dõi chuyến đi.
* Quản lý tập trung cước và thanh toán.
* Hỗ trợ quản lý vận hành.
* Cung cấp dữ liệu báo cáo cho doanh nghiệp.
* Bảo vệ dữ liệu người dùng và giao dịch.
* Hoạt động ổn định khi nhu cầu tăng cao.
* Cho phép mở rộng chức năng trong tương lai.

### 4. Ai sử dụng hệ thống?

| Đối tượng                            | Chức năng chính                                                                           |
| ------------------------------------ | ----------------------------------------------------------------------------------------- |
| Khách hàng                           | Quản lý tài khoản, đặt xe, theo dõi chuyến, xem lịch sử, thanh toán, đánh giá             |
| Tài xế                               | Quản lý hồ sơ, phương tiện, trạng thái hoạt động, nhận chuyến, cập nhật trạng thái chuyến |
| Nhân viên vận hành                   | Quản lý khách hàng, tài xế, phương tiện, chuyến đi, sự cố và giao dịch                    |
| Ban lãnh đạo / Người được phân quyền | Xem báo cáo hoạt động                                                                     |
| Nhà cung cấp thanh toán              | Xử lý thanh toán điện tử                                                                  |

---

# BƯỚC 2. STAKEHOLDER – CÁC BÊN LIÊN QUAN

## 2.1. Danh sách Stakeholder

| STT | Stakeholder                       | Vai trò                                                                            |
| --- | --------------------------------- | ---------------------------------------------------------------------------------- |
| 1   | Ban lãnh đạo                      | Đưa ra định hướng, xác nhận mục tiêu và theo dõi hiệu quả hoạt động của CAB System |
| 2   | Khách hàng                        | Sử dụng dịch vụ đặt xe, theo dõi chuyến, thanh toán và đánh giá                    |
| 3   | Tài xế                            | Nhận và thực hiện chuyến đi                                                        |
| 4   | Nhân viên vận hành                | Quản lý và giám sát hoạt động vận hành của hệ thống                                |
| 5   | Nhà cung cấp thanh toán bên ngoài | Xử lý giao dịch thanh toán điện tử                                                 |
| 6   | Business Analyst                  | Thu thập, phân tích và làm rõ yêu cầu của dự án                                    |

> Business Analyst là stakeholder của dự án nhưng không phải actor nghiệp vụ của CAB System.

## 2.2. Power – Interest

| Stakeholder             | Power      | Interest | Căn cứ                                                       |
| ----------------------- | ---------- | -------- | ------------------------------------------------------------ |
| Ban lãnh đạo            | Cao        | Cao      | Quyết định định hướng, mục tiêu và các yêu cầu quan trọng    |
| Business Analyst        | Trung bình | Cao      | Phân tích và làm rõ yêu cầu nhưng không quyết định cuối cùng |
| Nhân viên vận hành      | Trung bình | Cao      | Sử dụng hệ thống thường xuyên để quản lý hoạt động           |
| Khách hàng              | Thấp       | Cao      | Sử dụng trực tiếp dịch vụ đặt xe                             |
| Tài xế                  | Thấp       | Cao      | Sử dụng trực tiếp hệ thống để nhận và thực hiện chuyến       |
| Nhà cung cấp thanh toán | Trung bình | Thấp     | Có ảnh hưởng trực tiếp đến chức năng thanh toán điện tử      |

## 2.3. Stakeholder Matrix

### Manage Closely

* Ban lãnh đạo

### Keep Satisfied

* Nhà cung cấp thanh toán bên ngoài

### Keep Informed

* Business Analyst
* Nhân viên vận hành
* Khách hàng
* Tài xế

### Monitor

Hiện tại chưa xác định stakeholder phù hợp từ thông tin đề bài.

---

# BƯỚC 3. BUSINESS GOAL – MỤC TIÊU KINH DOANH

| Mã   | Business Goal                        | Mô tả                                                         |
| ---- | ------------------------------------ | ------------------------------------------------------------- |
| BG01 | Nâng cao hiệu quả đặt xe             | Giảm phụ thuộc vào quá trình phân công tài xế thủ công        |
| BG02 | Nâng cao trải nghiệm khách hàng      | Giúp khách hàng theo dõi đầy đủ trạng thái của chuyến đi      |
| BG03 | Nâng cao hiệu quả quản lý thanh toán | Quản lý tập trung cước và thông tin thanh toán theo chuyến    |
| BG04 | Nâng cao hiệu quả vận hành           | Hỗ trợ nhân viên theo dõi và xử lý các hoạt động của hệ thống |
| BG05 | Hỗ trợ quản lý và ra quyết định      | Cung cấp báo cáo về chuyến đi, doanh thu và tài xế            |
| BG06 | Hỗ trợ phát triển lâu dài            | Đảm bảo hệ thống có khả năng mở rộng, bảo mật và ổn định      |

---

# BƯỚC 4. SCOPE – PHẠM VI

## 4.1. In-Scope – Trong phạm vi

| STT | Hạng mục                     | Mô tả                                                              |
| --- | ---------------------------- | ------------------------------------------------------------------ |
| 1   | Quản lý tài khoản khách hàng | Đăng ký, đăng nhập, cập nhật thông tin cá nhân                     |
| 2   | Quản lý tài khoản tài xế     | Đăng ký hoặc được tạo tài khoản, đăng nhập, cập nhật hồ sơ         |
| 3   | Quản lý phương tiện          | Tài xế cập nhật thông tin phương tiện                              |
| 4   | Quản lý trạng thái tài xế    | Tài xế chuyển trạng thái sẵn sàng hoặc không sẵn sàng              |
| 5   | Đặt xe                       | Nhập điểm đón, điểm đến, chọn loại dịch vụ và tạo yêu cầu          |
| 6   | Điều phối tài xế             | Tìm, ưu tiên, gửi yêu cầu và phân công tài xế                      |
| 7   | Tìm tài xế thay thế          | Tiếp tục tìm khi tài xế từ chối hoặc không phản hồi                |
| 8   | Quản lý vị trí tài xế        | Ghi nhận vị trí phục vụ điều phối và ETA                           |
| 9   | Theo dõi chuyến đi           | Theo dõi thông tin tài xế, ETA và trạng thái chuyến                |
| 10  | Thực hiện chuyến đi          | Tài xế cập nhật các trạng thái của chuyến                          |
| 11  | Tính cước                    | Xác định số tiền khách hàng phải trả                               |
| 12  | Thanh toán                   | Hỗ trợ tiền mặt và thanh toán điện tử                              |
| 13  | Thông báo                    | Thông báo các sự kiện liên quan đến chuyến và thanh toán           |
| 14  | Lịch sử chuyến               | Khách hàng xem các chuyến đã thực hiện                             |
| 15  | Đánh giá tài xế              | Khách hàng đánh giá sau khi hoàn thành chuyến                      |
| 16  | Quản lý vận hành             | Quản lý khách hàng, tài xế, phương tiện, chuyến và giao dịch       |
| 17  | Xử lý sự cố                  | Hỗ trợ xử lý các chuyến có vấn đề                                  |
| 18  | Báo cáo                      | Báo cáo chuyến, doanh thu, tỷ lệ hoàn thành/hủy và hiệu quả tài xế |
| 19  | Phân quyền                   | Kiểm soát quyền đối với chức năng quản trị                         |
| 20  | Audit Log                    | Lưu vết các thao tác quan trọng                                    |

## 4.2. Out-of-Scope – Ngoài phạm vi

| STT | Hạng mục                                           | Lý do                                                          |
| --- | -------------------------------------------------- | -------------------------------------------------------------- |
| 1   | Xây dựng cổng thanh toán riêng                     | CAB System sử dụng nhà cung cấp thanh toán bên ngoài           |
| 2   | Quản lý tuyển dụng tài xế                          | Không được đề cập trong yêu cầu                                |
| 3   | Quản lý hợp đồng lao động tài xế                   | Không thuộc phạm vi đặt xe                                     |
| 4   | Quản lý lương tài xế                               | Không được đề cập                                              |
| 5   | Xây dựng nền tảng bản đồ riêng                     | Có thể tích hợp dịch vụ bản đồ hoặc vị trí bên ngoài           |
| 6   | Các loại dịch vụ mới chưa xác định                 | Chỉ cần chuẩn bị khả năng mở rộng                              |
| 7   | Các phương thức thanh toán tương lai chưa xác định | Chỉ cần chuẩn bị khả năng mở rộng                              |
| 8   | Tất cả kênh thông báo trong tương lai              | Chỉ triển khai các kênh được lựa chọn trong phiên bản hiện tại |

---

# BƯỚC 5. BUSINESS REQUIREMENTS – YÊU CẦU NGHIỆP VỤ

| Mã   | Business Requirement     | Mô tả                                                                        |
| ---- | ------------------------ | ---------------------------------------------------------------------------- |
| BR01 | Quản lý tài khoản        | CAB System phải hỗ trợ tài khoản khách hàng, tài xế và nhân viên vận hành    |
| BR02 | Quản lý yêu cầu đặt xe   | Khách hàng có thể tạo yêu cầu đặt xe theo điểm đón, điểm đến và loại dịch vụ |
| BR03 | Điều phối tài xế         | Hệ thống tự động tìm và phân công tài xế phù hợp                             |
| BR04 | Quản lý hoạt động tài xế | Tài xế quản lý trạng thái hoạt động và thực hiện chuyến                      |
| BR05 | Theo dõi chuyến đi       | Khách hàng có thể theo dõi trạng thái và thông tin chuyến                    |
| BR06 | Tính cước                | Hệ thống xác định số tiền khách hàng phải trả sau chuyến                     |
| BR07 | Thanh toán               | Hệ thống hỗ trợ tiền mặt và thanh toán điện tử                               |
| BR08 | Thông báo                | Hệ thống thông báo các sự kiện quan trọng cho khách hàng và tài xế           |
| BR09 | Quản lý vận hành         | Nhân viên vận hành có thể theo dõi và quản lý hoạt động của CAB System       |
| BR10 | Báo cáo                  | Hệ thống cung cấp báo cáo phục vụ quản lý                                    |
| BR11 | Bảo mật và kiểm soát     | Hệ thống xác thực, phân quyền, bảo vệ dữ liệu và lưu vết                     |
| BR12 | Khả năng phát triển      | Hệ thống hỗ trợ mở rộng và thay đổi các thành phần trong tương lai           |

---

# BƯỚC 6. BUSINESS PROCESS – QUY TRÌNH NGHIỆP VỤ

## 6.1. Quy trình nghiệp vụ chính

1. Khách hàng đăng nhập.
2. Khách hàng nhập điểm đón.
3. Khách hàng nhập điểm đến.
4. Khách hàng chọn loại xe hoặc loại dịch vụ.
5. Khách hàng gửi yêu cầu đặt xe.
6. Hệ thống kiểm tra thông tin.
7. Hệ thống tạo chuyến.
8. Hệ thống chuyển trạng thái chuyến thành `SEARCHING_DRIVER`.
9. Hệ thống tìm các tài xế phù hợp.
10. Hệ thống ưu tiên tài xế.
11. Hệ thống gửi yêu cầu chuyến cho tài xế.
12. Tài xế chấp nhận hoặc từ chối.
13. Nếu tài xế từ chối hoặc không phản hồi, hệ thống tiếp tục tìm tài xế khác.
14. Nếu tài xế chấp nhận, hệ thống gán tài xế cho chuyến.
15. Hệ thống cung cấp thông tin tài xế và ETA cho khách hàng.
16. Tài xế di chuyển đến điểm đón.
17. Tài xế cập nhật trạng thái đã đến điểm đón.
18. Tài xế đón khách.
19. Tài xế cập nhật trạng thái đã đón khách.
20. Tài xế thực hiện chuyến đi.
21. Tài xế cập nhật trạng thái đang di chuyển.
22. Tài xế kết thúc chuyến.
23. Tài xế cập nhật trạng thái hoàn thành.
24. Hệ thống tính cước.
25. Khách hàng thực hiện thanh toán.
26. Hệ thống ghi nhận kết quả thanh toán.
27. Khách hàng có thể đánh giá tài xế.
28. Hệ thống lưu chuyến vào lịch sử.

## 6.2. Trạng thái chính của chuyến

```text
SEARCHING_DRIVER
→ DRIVER_ASSIGNED
→ DRIVER_ARRIVED
→ PICKED_UP
→ IN_PROGRESS
→ COMPLETED
```

Các trạng thái kết thúc bất thường:

```text
CANCELLED
NO_DRIVER
```

> Chính sách chuyển chuyến sang `CANCELLED` vẫn cần được khách hàng xác nhận.

---

# BƯỚC 7. FUNCTIONAL REQUIREMENTS – YÊU CẦU CHỨC NĂNG

## 7.1. Nhóm Identity & Account

| Mã   | Functional Requirement                                    |
| ---- | --------------------------------------------------------- |
| FR01 | Hệ thống cho phép khách hàng đăng ký tài khoản            |
| FR02 | Hệ thống cho phép người dùng đăng nhập                    |
| FR03 | Hệ thống cho phép người dùng đăng xuất                    |
| FR04 | Hệ thống cho phép khách hàng cập nhật thông tin cá nhân   |
| FR05 | Hệ thống cho phép tài xế cập nhật hồ sơ                   |
| FR06 | Hệ thống cho phép nhân viên vận hành tạo tài khoản tài xế |
| FR07 | Hệ thống cho phép tài xế cập nhật thông tin phương tiện   |

## 7.2. Nhóm Booking

| Mã   | Functional Requirement                                  |
| ---- | ------------------------------------------------------- |
| FR08 | Hệ thống cho phép khách hàng nhập điểm đón              |
| FR09 | Hệ thống cho phép khách hàng nhập điểm đến              |
| FR10 | Hệ thống cho phép khách hàng chọn loại dịch vụ          |
| FR11 | Hệ thống cho phép khách hàng tạo yêu cầu đặt xe         |
| FR12 | Hệ thống cho phép khách hàng hủy chuyến theo chính sách |
| FR13 | Hệ thống cho phép khách hàng xem lịch sử chuyến         |
| FR14 | Hệ thống cho phép khách hàng xem chi tiết chuyến        |

## 7.3. Nhóm Driver & Location

| Mã   | Functional Requirement                                |
| ---- | ----------------------------------------------------- |
| FR15 | Hệ thống cho phép tài xế cập nhật trạng thái sẵn sàng |
| FR16 | Hệ thống ghi nhận vị trí hiện tại của tài xế          |
| FR17 | Hệ thống cho phép tài xế cập nhật trạng thái chuyến   |

## 7.4. Nhóm Dispatch – Tìm và phân công tài xế

| Mã   | Functional Requirement                             |
| ---- | -------------------------------------------------- |
| FR18 | Hệ thống xác định vị trí điểm đón                  |
| FR19 | Hệ thống lấy danh sách tài xế sẵn sàng             |
| FR20 | Hệ thống lọc tài xế theo loại dịch vụ              |
| FR21 | Hệ thống tính khoảng cách giữa tài xế và điểm đón  |
| FR22 | Hệ thống xếp hạng tài xế theo tiêu chí ưu tiên     |
| FR23 | Hệ thống gửi yêu cầu chuyến cho tài xế được chọn   |
| FR24 | Hệ thống ghi nhận phản hồi của tài xế              |
| FR25 | Hệ thống gán tài xế cho chuyến                     |
| FR26 | Hệ thống tìm tài xế khác khi tài xế từ chối        |
| FR27 | Hệ thống tìm tài xế khác khi tài xế không phản hồi |
| FR28 | Hệ thống thông báo khi không tìm được tài xế       |

### Logic xử lý Dispatch

```text
Xác định điểm đón
        ↓
Lấy tài xế sẵn sàng
        ↓
Lọc loại dịch vụ
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
   ┌──────────────┐
 Chấp nhận     Từ chối/Timeout
    ↓                ↓
Gán tài xế      Tìm tài xế khác
```

## 7.5. Nhóm Trip

| Mã   | Functional Requirement                                  |
| ---- | ------------------------------------------------------- |
| FR29 | Hệ thống hiển thị thông tin tài xế cho khách hàng       |
| FR30 | Hệ thống hiển thị thời gian dự kiến tài xế đến          |
| FR31 | Hệ thống cho phép khách hàng theo dõi trạng thái chuyến |
| FR32 | Hệ thống ghi nhận trạng thái chuyến                     |
| FR33 | Hệ thống ghi nhận thời gian hoàn thành chuyến           |

## 7.6. Nhóm Fare & Payment

| Mã   | Functional Requirement                                              |
| ---- | ------------------------------------------------------------------- |
| FR34 | Hệ thống tính cước chuyến đi                                        |
| FR35 | Hệ thống cho phép khách hàng chọn phương thức thanh toán            |
| FR36 | Hệ thống ghi nhận thanh toán tiền mặt                               |
| FR37 | Hệ thống gửi yêu cầu thanh toán điện tử đến nhà cung cấp thanh toán |
| FR38 | Hệ thống nhận kết quả thanh toán điện tử                            |
| FR39 | Hệ thống ghi nhận trạng thái giao dịch                              |
| FR40 | Hệ thống cho phép xử lý lại giao dịch thất bại theo chính sách      |

## 7.7. Nhóm Notification

| Mã   | Functional Requirement                               |
| ---- | ---------------------------------------------------- |
| FR41 | Hệ thống thông báo khi yêu cầu đặt xe được tiếp nhận |
| FR42 | Hệ thống thông báo chuyến mới cho tài xế             |
| FR43 | Hệ thống thông báo khi tài xế nhận chuyến            |
| FR44 | Hệ thống thông báo khi tài xế đến điểm đón           |
| FR45 | Hệ thống thông báo khi chuyến hoàn thành             |
| FR46 | Hệ thống thông báo kết quả thanh toán                |

## 7.8. Nhóm Rating

| Mã   | Functional Requirement                                  |
| ---- | ------------------------------------------------------- |
| FR47 | Hệ thống cho phép khách hàng đánh giá tài xế sau chuyến |

## 7.9. Nhóm Operation

| Mã   | Functional Requirement                                       |
| ---- | ------------------------------------------------------------ |
| FR48 | Hệ thống cho phép nhân viên vận hành tra cứu khách hàng      |
| FR49 | Hệ thống cho phép nhân viên vận hành quản lý tài xế          |
| FR50 | Hệ thống cho phép nhân viên vận hành quản lý phương tiện     |
| FR51 | Hệ thống cho phép nhân viên vận hành xem chuyến đang diễn ra |
| FR52 | Hệ thống cho phép nhân viên vận hành xem trạng thái tài xế   |
| FR53 | Hệ thống cho phép nhân viên vận hành xử lý chuyến gặp sự cố  |
| FR54 | Hệ thống cho phép nhân viên vận hành tra cứu giao dịch       |

## 7.10. Nhóm Reporting

| Mã   | Functional Requirement                         |
| ---- | ---------------------------------------------- |
| FR55 | Hệ thống tạo báo cáo số lượng chuyến           |
| FR56 | Hệ thống tạo báo cáo doanh thu                 |
| FR57 | Hệ thống tạo báo cáo tỷ lệ chuyến hoàn thành   |
| FR58 | Hệ thống tạo báo cáo tỷ lệ chuyến hủy          |
| FR59 | Hệ thống tạo báo cáo hiệu quả hoạt động tài xế |

## 7.11. Nhóm Security & Audit

| Mã   | Functional Requirement                       |
| ---- | -------------------------------------------- |
| FR60 | Hệ thống xác thực người dùng                 |
| FR61 | Hệ thống kiểm tra quyền truy cập             |
| FR62 | Hệ thống giới hạn thao tác quản trị nhạy cảm |
| FR63 | Hệ thống lưu vết thao tác quan trọng         |

---

# BƯỚC 8. BUSINESS RULES & BUSINESS EXCEPTIONS

## 8.1. Business Rules

| Mã    | Business Rule                                                                         |
| ----- | ------------------------------------------------------------------------------------- |
| BRL01 | Khách hàng và tài xế phải được xác thực trước khi sử dụng chức năng yêu cầu tài khoản |
| BRL02 | Chỉ tài xế có trạng thái sẵn sàng mới được đưa vào quá trình tìm tài xế               |
| BRL03 | Tài xế phải có phương tiện phù hợp với loại dịch vụ được yêu cầu                      |
| BRL04 | Việc ưu tiên tài xế dựa trên vị trí và các tiêu chí vận hành                          |
| BRL05 | Một chuyến tại một thời điểm chỉ được gán cho một tài xế                              |
| BRL06 | Khi tài xế chấp nhận, hệ thống gán tài xế cho chuyến                                  |
| BRL07 | Khi tài xế từ chối, hệ thống tiếp tục tìm tài xế khác                                 |
| BRL08 | Khi tài xế không phản hồi đúng thời hạn, hệ thống tiếp tục tìm tài xế khác            |
| BRL09 | Khách hàng không cần tạo lại chuyến khi hệ thống tìm tài xế thay thế                  |
| BRL10 | Nếu không tìm được tài xế, khách hàng phải được thông báo                             |
| BRL11 | Tài xế cập nhật trạng thái chuyến theo tiến trình thực hiện                           |
| BRL12 | Chỉ chuyến hoàn thành mới thực hiện tính cước cuối cùng                               |
| BRL13 | Khách hàng có thể thanh toán tiền mặt hoặc thanh toán điện tử                         |
| BRL14 | Thanh toán điện tử phải được xử lý qua nhà cung cấp bên ngoài                         |
| BRL15 | CAB System không lưu trực tiếp thông tin thẻ hoặc tài khoản thanh toán nhạy cảm       |
| BRL16 | Chỉ chuyến hoàn thành mới được đánh giá                                               |
| BRL17 | Các thao tác quản trị nhạy cảm yêu cầu quyền phù hợp                                  |
| BRL18 | Các thao tác quan trọng phải được lưu vết                                             |

## 8.2. Business Exceptions

| Mã   | Ngoại lệ                        | Điều kiện                                         | Xử lý                                         |
| ---- | ------------------------------- | ------------------------------------------------- | --------------------------------------------- |
| BE01 | Thông tin đặt xe không hợp lệ   | Điểm đón, điểm đến hoặc loại dịch vụ không hợp lệ | Thông báo và yêu cầu kiểm tra                 |
| BE02 | Không có tài xế phù hợp         | Danh sách tài xế phù hợp rỗng                     | Thông báo khách hàng                          |
| BE03 | Tài xế từ chối                  | Tài xế trả về từ chối                             | Tìm tài xế tiếp theo                          |
| BE04 | Tài xế không phản hồi           | Quá thời gian phản hồi                            | Tìm tài xế tiếp theo                          |
| BE05 | Thanh toán thất bại             | Nhà cung cấp trả trạng thái thất bại              | Ghi nhận, thông báo và cho phép xử lý lại     |
| BE06 | Không kết nối Payment Provider  | Không nhận được kết quả thanh toán                | Ghi nhận lỗi, không làm dừng chức năng đặt xe |
| BE07 | Notification Provider gặp lỗi   | Không thể gửi thông báo                           | Ghi nhận lỗi, không làm dừng nghiệp vụ chính  |
| BE08 | Khách hàng hủy chuyến           | Khách hàng yêu cầu hủy                            | Xử lý theo chính sách hủy                     |
| BE09 | Tài xế gặp sự cố                | Không thể tiếp tục chuyến                         | Nhân viên vận hành hỗ trợ xử lý               |
| BE10 | Mất kết nối mạng                | Khách hàng hoặc tài xế mất mạng                   | Xử lý theo chính sách đồng bộ TBD             |
| BE11 | Không nhận được vị trí tài xế   | Vị trí thiếu hoặc không hợp lệ                    | Cách xử lý TBD                                |
| BE12 | Chuyến có trạng thái bất thường | Trạng thái không phù hợp với tiến trình           | Nhân viên vận hành xử lý                      |

## 8.3. Những vấn đề cần làm rõ với khách hàng

### Tính cước

* Công thức tính cước là gì?
* Cước cơ bản là bao nhiêu?
* Có tính theo khoảng cách không?
* Có tính theo thời gian không?
* Có phụ phí không?

### Điều phối tài xế

* Bán kính tìm tài xế là bao nhiêu?
* Các tiêu chí ưu tiên tài xế gồm những gì?
* Tiêu chí nào được ưu tiên cao nhất?
* Tài xế có bao nhiêu thời gian để phản hồi?
* Một yêu cầu được gửi cho một tài xế hay nhiều tài xế cùng lúc?

### Hủy chuyến

* Khách hàng được hủy ở trạng thái nào?
* Tài xế có được hủy chuyến sau khi đã nhận không?
* Trường hợp nào phải trả phí hủy?

### Thanh toán

* Thanh toán thất bại được thử lại bao nhiêu lần?
* Có cho phép chuyển sang thanh toán tiền mặt không?

### Mất kết nối

* Khi mất mạng có lưu trạng thái tạm thời không?
* Khi kết nối lại thì đồng bộ trạng thái như thế nào?

### Lưu trữ dữ liệu

* Dữ liệu vị trí lưu trong bao lâu?
* Dữ liệu giao dịch lưu trong bao lâu?
* Audit Log lưu trong bao lâu?

---

# BƯỚC 9. DATA MODEL – MÔ HÌNH DỮ LIỆU ERD

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

---

# BƯỚC 10. NON-FUNCTIONAL REQUIREMENTS – YÊU CẦU PHI CHỨC NĂNG

| Mã    | Nhóm             | Non-Functional Requirement                                                   |
| ----- | ---------------- | ---------------------------------------------------------------------------- |
| NFR01 | Scalability      | Hệ thống phải hỗ trợ tăng số lượng khách hàng, tài xế và chuyến đi           |
| NFR02 | Scalability      | Các thành phần chính phải có khả năng mở rộng độc lập khi cần                |
| NFR03 | Availability     | Hệ thống phải duy trì hoạt động ổn định trong thời điểm nhu cầu cao          |
| NFR04 | Fault Tolerance  | Lỗi Payment Service không được làm chức năng đặt xe ngừng hoạt động          |
| NFR05 | Fault Tolerance  | Lỗi Notification Service không được làm chức năng đặt xe ngừng hoạt động     |
| NFR06 | Deployability    | Các chức năng mới phải có thể triển khai từng phần với ảnh hưởng hạn chế     |
| NFR07 | Authentication   | Người dùng phải được xác thực trước khi truy cập chức năng yêu cầu tài khoản |
| NFR08 | Authorization    | Chức năng quản trị phải được kiểm soát theo quyền                            |
| NFR09 | Data Security    | Dữ liệu cá nhân phải được bảo vệ                                             |
| NFR10 | Data Security    | Dữ liệu vị trí và phương tiện phải được bảo vệ                               |
| NFR11 | Payment Security | Không lưu trực tiếp dữ liệu thanh toán nhạy cảm                              |
| NFR12 | Auditability     | Hệ thống phải lưu vết thao tác quan trọng                                    |
| NFR13 | Extensibility    | Hệ thống phải cho phép thêm loại dịch vụ mới                                 |
| NFR14 | Extensibility    | Hệ thống phải cho phép thêm phương thức hoặc nhà cung cấp thanh toán         |
| NFR15 | Extensibility    | Hệ thống phải cho phép thêm kênh hoặc nhà cung cấp thông báo                 |
| NFR16 | Maintainability  | Thay đổi một thành phần phải hạn chế ảnh hưởng đến thành phần khác           |

### Các giá trị TBD

Các giá trị sau chưa được đề bài xác định:

* Số lượng người dùng đồng thời.
* Thời gian phản hồi.
* Throughput.
* Uptime.
* Timeout giữa các service.
* Retry Policy.

---

# BƯỚC 11. USE CASE DIAGRAM

## 11.1. Xác định Actor

CAB System có 5 actor chính:

| STT | Actor | Vai trò |
|---|---|---|
| 1 | Khách hàng | Đăng ký, đăng nhập, cập nhật thông tin cá nhân, đặt xe, theo dõi chuyến, hủy chuyến, xem lịch sử chuyến, thanh toán và đánh giá tài xế. |
| 2 | Tài xế | Đăng nhập, cập nhật hồ sơ, cập nhật phương tiện, cập nhật trạng thái sẵn sàng, phản hồi yêu cầu chuyến và cập nhật trạng thái chuyến đi. |
| 3 | Nhân viên vận hành | Đăng nhập, quản lý khách hàng, tài xế, phương tiện, theo dõi chuyến, kiểm tra trạng thái tài xế, xử lý chuyến gặp sự cố, tra cứu giao dịch và tạo tài khoản tài xế. |
| 4 | Quản lý | Xem báo cáo hoạt động của hệ thống. |
| 5 | Nhà cung cấp thanh toán | Tham gia xử lý giao dịch thanh toán điện tử của khách hàng. |

> CAB System là hệ thống đang được mô hình hóa nên không được xem là actor của chính hệ thống.

---

## 11.2. Danh sách Use Case

### A. Use Case của Khách hàng

| Mã | Use Case | Mô tả ngắn |
|---|---|---|
| UC01 | Đăng ký | Cho phép khách hàng tạo tài khoản sử dụng CAB System. |
| UC02 | Đăng nhập | Cho phép khách hàng xác thực tài khoản trước khi sử dụng các chức năng yêu cầu đăng nhập. |
| UC03 | Cập nhật thông tin cá nhân | Cho phép khách hàng chỉnh sửa thông tin cá nhân. |
| UC04 | Đặt xe | Cho phép khách hàng nhập thông tin chuyến và gửi yêu cầu đặt xe. |
| UC05 | Theo dõi chuyến đi | Cho phép khách hàng theo dõi trạng thái hiện tại của chuyến. |
| UC06 | Hủy chuyến | Cho phép khách hàng yêu cầu hủy chuyến theo chính sách của doanh nghiệp. |
| UC07 | Xem lịch sử chuyến đi | Cho phép khách hàng xem lại các chuyến đã thực hiện. |
| UC08 | Đánh giá tài xế | Cho phép khách hàng đánh giá tài xế sau khi chuyến hoàn thành. |
| UC09 | Thanh toán chuyến | Cho phép khách hàng thanh toán chi phí chuyến đi. |

---

### B. Use Case của Tài xế

| Mã | Use Case | Mô tả ngắn |
|---|---|---|
| UC10 | Đăng nhập | Cho phép tài xế xác thực tài khoản để sử dụng hệ thống. |
| UC11 | Cập nhật hồ sơ | Cho phép tài xế chỉnh sửa thông tin cá nhân. |
| UC12 | Cập nhật phương tiện | Cho phép tài xế cập nhật thông tin phương tiện đang sử dụng. |
| UC13 | Cập nhật trạng thái tài xế | Cho phép tài xế chuyển trạng thái sẵn sàng hoặc không sẵn sàng nhận chuyến. |
| UC14 | Phản hồi yêu cầu chuyến | Cho phép tài xế chấp nhận hoặc từ chối yêu cầu chuyến được gửi đến. |
| UC15 | Cập nhật trạng thái chuyến đi | Cho phép tài xế cập nhật trạng thái trong quá trình thực hiện chuyến. |

> UC02 và UC10 đều là chức năng đăng nhập. Khi triển khai hệ thống thực tế có thể dùng chung một Use Case “Đăng nhập” cho nhiều actor.

---

### C. Use Case của Nhân viên vận hành

| Mã | Use Case | Mô tả ngắn |
|---|---|---|
| UC16 | Đăng nhập | Cho phép nhân viên vận hành xác thực tài khoản. |
| UC17 | Quản lý khách hàng | Cho phép nhân viên vận hành xem và xử lý thông tin khách hàng theo quyền được cấp. |
| UC18 | Quản lý tài xế | Cho phép nhân viên vận hành quản lý thông tin tài xế. |
| UC19 | Quản lý phương tiện | Cho phép nhân viên vận hành quản lý thông tin phương tiện. |
| UC20 | Theo dõi chuyến | Cho phép nhân viên vận hành theo dõi các chuyến đang diễn ra. |
| UC21 | Kiểm tra trạng thái tài xế | Cho phép nhân viên vận hành xem trạng thái hoạt động của tài xế. |
| UC22 | Xử lý chuyến gặp sự cố | Cho phép nhân viên vận hành hỗ trợ xử lý các chuyến phát sinh vấn đề. |
| UC23 | Tra cứu giao dịch | Cho phép nhân viên vận hành tìm kiếm và xem lịch sử giao dịch. |
| UC24 | Tạo tài khoản tài xế | Cho phép nhân viên vận hành tạo tài khoản cho tài xế. |

---

### D. Use Case của Quản lý

| Mã | Use Case | Mô tả ngắn |
|---|---|---|
| UC25 | Xem báo cáo | Cho phép quản lý xem các báo cáo hoạt động của CAB System. |

Các báo cáo có thể bao gồm:

- Số lượng chuyến.
- Doanh thu.
- Tỷ lệ chuyến hoàn thành.
- Tỷ lệ chuyến hủy.
- Hiệu quả hoạt động của tài xế.

---

### E. Use Case liên quan đến Nhà cung cấp thanh toán

Nhà cung cấp thanh toán bên ngoài tham gia vào:

**UC09 – Thanh toán chuyến**

Quan hệ:

Khách hàng → Thanh toán chuyến ← Nhà cung cấp thanh toán

Nhà cung cấp thanh toán chỉ tham gia khi khách hàng lựa chọn phương thức thanh toán điện tử.

Mô hình usecase
<img width="1710" height="1244" alt="image" src="https://github.com/user-attachments/assets/3e462b76-7d0d-49ce-b5f9-ca2f213af814" />

---
# BƯỚC 12. ĐẶC TẢ USE CASE CHÍNH

## UC04. Đặt xe

| Thuộc tính               | Nội dung                                             |
| ------------------------ | ---------------------------------------------------- |
| Mã Use Case              | UC04                                                 |
| Tên Use Case             | Đặt xe                                               |
| Actor chính              | Khách hàng                                           |
| Tiền điều kiện           | Khách hàng đã đăng nhập                              |
| Hậu điều kiện thành công | Chuyến được tạo và chuyển sang trạng thái tìm tài xế |
| Hậu điều kiện thất bại   | Không tạo chuyến                                     |

### Basic Flow

| Actor                    | System                                    |
| ------------------------ | ----------------------------------------- |
| 1. Chọn chức năng đặt xe | 2. Hiển thị giao diện đặt xe              |
| 3. Nhập điểm đón         |                                           |
| 4. Nhập điểm đến         |                                           |
| 5. Chọn loại dịch vụ     |                                           |
| 6. Xác nhận đặt xe       | 7. Kiểm tra thông tin                     |
|                          | 8. Tạo chuyến                             |
|                          | 9. Cập nhật trạng thái `SEARCHING_DRIVER` |
|                          | 10. Bắt đầu tìm tài xế phù hợp            |
|                          | 11. Thông báo đã tiếp nhận yêu cầu        |

### Alternative Flow

#### AF01 – Tài xế từ chối

1. Hệ thống ghi nhận trạng thái `REJECTED`.
2. Hệ thống lựa chọn tài xế tiếp theo.
3. Hệ thống gửi yêu cầu chuyến mới.

#### AF02 – Tài xế không phản hồi

1. Hết thời gian phản hồi.
2. Hệ thống ghi nhận trạng thái `TIMEOUT`.
3. Hệ thống lựa chọn tài xế tiếp theo.

### Exception Flow

#### EF01 – Dữ liệu đặt xe không hợp lệ

1. Hệ thống phát hiện thông tin không hợp lệ.
2. Hệ thống thông báo lỗi.
3. Khách hàng chỉnh sửa thông tin.

#### EF02 – Không tìm được tài xế

1. Hệ thống không còn tài xế phù hợp.
2. Hệ thống cập nhật trạng thái `NO_DRIVER`.
3. Hệ thống thông báo cho khách hàng.

---

## UC14. Phản hồi yêu cầu chuyến

| Thuộc tính               | Nội dung                                         |
| ------------------------ | ------------------------------------------------ |
| Actor chính              | Tài xế                                           |
| Tiền điều kiện           | Tài xế đang sẵn sàng và nhận được yêu cầu chuyến |
| Hậu điều kiện thành công | Tài xế được gán cho chuyến                       |
| Hậu điều kiện thay thế   | Hệ thống tiếp tục tìm tài xế khác                |

### Basic Flow

| Actor                   | System                                     |
| ----------------------- | ------------------------------------------ |
|                         | 1. Gửi yêu cầu chuyến                      |
| 2. Xem thông tin chuyến |                                            |
| 3. Chọn chấp nhận       | 4. Ghi nhận `ACCEPTED`                     |
|                         | 5. Gán tài xế cho chuyến                   |
|                         | 6. Cập nhật chuyến thành `DRIVER_ASSIGNED` |
|                         | 7. Thông báo cho khách hàng                |

### Alternative Flow – Từ chối

1. Tài xế chọn từ chối.
2. Hệ thống ghi nhận `REJECTED`.
3. Hệ thống tiếp tục tìm tài xế khác.

---

## UC15. Cập nhật trạng thái chuyến

| Thuộc tính     | Nội dung                                |
| -------------- | --------------------------------------- |
| Actor chính    | Tài xế                                  |
| Tiền điều kiện | Tài xế đã được gán cho chuyến           |
| Hậu điều kiện  | Trạng thái mới của chuyến được ghi nhận |

### Basic Flow

| Actor                         | System                            |
| ----------------------------- | --------------------------------- |
| 1. Cập nhật đã đến điểm đón   | 2. Ghi nhận `DRIVER_ARRIVED`      |
|                               | 3. Thông báo khách hàng           |
| 4. Xác nhận đã đón khách      | 5. Ghi nhận `PICKED_UP`           |
| 6. Xác nhận bắt đầu di chuyển | 7. Ghi nhận `IN_PROGRESS`         |
| 8. Xác nhận hoàn thành        | 9. Ghi nhận `COMPLETED`           |
|                               | 10. Ghi nhận thời gian hoàn thành |
|                               | 11. Thực hiện tính cước           |

---

## UC08. Thanh toán chuyến

| Thuộc tính     | Nội dung                           |
| -------------- | ---------------------------------- |
| Actor chính    | Khách hàng                         |
| Actor phụ      | Nhà cung cấp thanh toán bên ngoài  |
| Tiền điều kiện | Chuyến đã hoàn thành và đã có cước |
| Hậu điều kiện  | Kết quả thanh toán được ghi nhận   |

### Basic Flow – Thanh toán điện tử

| Actor                        | System                               |
| ---------------------------- | ------------------------------------ |
|                              | 1. Hiển thị số tiền                  |
| 2. Chọn thanh toán điện tử   |                                      |
| 3. Xác nhận thanh toán       | 4. Tạo giao dịch `PENDING`           |
|                              | 5. Gửi yêu cầu sang Payment Provider |
| Nhà cung cấp xử lý giao dịch |                                      |
| Nhà cung cấp trả kết quả     | 6. Nhận kết quả                      |
|                              | 7. Cập nhật `SUCCESS`                |
|                              | 8. Thông báo thành công              |

### Alternative Flow – Thanh toán tiền mặt

1. Khách hàng chọn tiền mặt.
2. Hệ thống ghi nhận phương thức `CASH`.
3. Hệ thống cập nhật thông tin thanh toán.

### Exception Flow – Thanh toán thất bại

1. Nhà cung cấp trả kết quả thất bại.
2. Hệ thống ghi nhận `FAILED`.
3. Hệ thống thông báo cho khách hàng.
4. Khách hàng có thể xử lý lại theo chính sách.

---

## UC09. Đánh giá tài xế

| Thuộc tính     | Nội dung                         |
| -------------- | -------------------------------- |
| Actor chính    | Khách hàng                       |
| Tiền điều kiện | Chuyến có trạng thái `COMPLETED` |
| Hậu điều kiện  | Đánh giá được lưu                |

### Basic Flow

1. Khách hàng mở chuyến đã hoàn thành.
2. Khách hàng chọn chức năng đánh giá.
3. Khách hàng nhập điểm đánh giá.
4. Khách hàng nhập nhận xét nếu có.
5. Khách hàng gửi đánh giá.
6. Hệ thống kiểm tra dữ liệu.
7. Hệ thống lưu đánh giá.
8. Hệ thống thông báo thành công.

---

# BƯỚC 13. ACCEPTANCE CRITERIA – TIÊU CHÍ CHẤP NHẬN

## 13.1. Account

| Mã   | Tiêu chí chấp nhận                                                         |
| ---- | -------------------------------------------------------------------------- |
| AC01 | Thông tin đăng ký hợp lệ thì tài khoản khách hàng được tạo thành công      |
| AC02 | Email hoặc số điện thoại đã tồn tại thì hệ thống không tạo tài khoản trùng |
| AC03 | Thông tin đăng nhập đúng thì người dùng đăng nhập thành công               |
| AC04 | Thông tin đăng nhập sai thì hệ thống thông báo lỗi                         |
| AC05 | Người dùng cập nhật thông tin hợp lệ thì dữ liệu mới được lưu              |

## 13.2. Booking & Dispatch

| Mã   | Tiêu chí chấp nhận                                                     |
| ---- | ---------------------------------------------------------------------- |
| AC06 | Điểm đón, điểm đến và loại dịch vụ hợp lệ thì hệ thống tạo được chuyến |
| AC07 | Chuyến mới có trạng thái `SEARCHING_DRIVER`                            |
| AC08 | Chỉ tài xế `AVAILABLE` được đưa vào danh sách tìm kiếm                 |
| AC09 | Tài xế phải có phương tiện phù hợp loại dịch vụ                        |
| AC10 | Hệ thống xác định khoảng cách phục vụ xếp hạng tài xế                  |
| AC11 | Tài xế được chọn nhận được yêu cầu chuyến                              |
| AC12 | Tài xế chấp nhận thì được gán cho chuyến                               |
| AC13 | Tài xế từ chối thì hệ thống tiếp tục tìm tài xế khác                   |
| AC14 | Tài xế không phản hồi thì hệ thống tiếp tục tìm tài xế khác            |
| AC15 | Không còn tài xế phù hợp thì khách hàng được thông báo                 |

## 13.3. Trip

| Mã   | Tiêu chí chấp nhận                                       |
| ---- | -------------------------------------------------------- |
| AC16 | Sau khi gán tài xế, khách hàng xem được thông tin tài xế |
| AC17 | Khách hàng xem được thời gian dự kiến tài xế đến         |
| AC18 | Tài xế cập nhật được trạng thái `DRIVER_ARRIVED`         |
| AC19 | Tài xế cập nhật được trạng thái `PICKED_UP`              |
| AC20 | Tài xế cập nhật được trạng thái `IN_PROGRESS`            |
| AC21 | Tài xế cập nhật được trạng thái `COMPLETED`              |
| AC22 | Khách hàng xem được trạng thái hiện tại của chuyến       |

## 13.4. Payment

| Mã   | Tiêu chí chấp nhận                                                  |
| ---- | ------------------------------------------------------------------- |
| AC23 | Chuyến hoàn thành thì hệ thống tính cước theo quy tắc được cấu hình |
| AC24 | Khách hàng chọn được tiền mặt hoặc thanh toán điện tử               |
| AC25 | Thanh toán điện tử được gửi đến nhà cung cấp thanh toán             |
| AC26 | Kết quả thành công thì Payment chuyển sang `SUCCESS`                |
| AC27 | Kết quả thất bại thì Payment chuyển sang `FAILED`                   |
| AC28 | Thanh toán thất bại thì khách hàng nhận được thông báo              |
| AC29 | CAB System không lưu trực tiếp thông tin thanh toán nhạy cảm        |

## 13.5. Rating

| Mã   | Tiêu chí chấp nhận                       |
| ---- | ---------------------------------------- |
| AC30 | Chỉ chuyến `COMPLETED` mới được đánh giá |
| AC31 | Đánh giá hợp lệ được lưu thành công      |

## 13.6. Operation & Security

| Mã   | Tiêu chí chấp nhận                                  |
| ---- | --------------------------------------------------- |
| AC32 | Nhân viên chỉ truy cập được chức năng phù hợp quyền |
| AC33 | Nhân viên vận hành xem được chuyến đang thực hiện   |
| AC34 | Nhân viên vận hành tra cứu được giao dịch           |
| AC35 | Các thao tác quản trị quan trọng được lưu Audit Log |
| AC36 | Người không đủ quyền bị từ chối thao tác nhạy cảm   |

## 13.7. Fault Tolerance

| Mã   | Tiêu chí chấp nhận                                                     |
| ---- | ---------------------------------------------------------------------- |
| AC37 | Payment Service gặp lỗi không làm chức năng đặt xe dừng hoạt động      |
| AC38 | Notification Service gặp lỗi không làm chức năng đặt xe dừng hoạt động |

---

# BƯỚC 14. REQUIREMENT TRACEABILITY MATRIX – RTM

| Business Goal | Business Requirement | FR / NFR                 | Use Case                | Acceptance Criteria            |
| ------------- | -------------------- | ------------------------ | ----------------------- | ------------------------------ |
| BG01          | BR02                 | FR08–FR14                | UC04, UC06, UC07        | AC06–AC07                      |
| BG01          | BR03                 | FR18–FR28                | UC04, UC14              | AC08–AC15                      |
| BG02          | BR04                 | FR15–FR17                | UC13, UC15              | AC18–AC21                      |
| BG02          | BR05                 | FR29–FR33                | UC05, UC15              | AC16–AC22                      |
| BG03          | BR06                 | FR34                     | UC08                    | AC23                           |
| BG03          | BR07                 | FR35–FR40                | UC08                    | AC24–AC29                      |
| BG02          | BR08                 | FR41–FR46                | UC04, UC14, UC15, UC08  | AC11, AC16, AC18, AC28         |
| BG04          | BR09                 | FR48–FR54                | UC17–UC23               | AC32–AC35                      |
| BG05          | BR10                 | FR55–FR59                | UC24                    | Tiêu chí báo cáo tương ứng     |
| BG06          | BR11                 | FR60–FR63, NFR07–NFR12   | UC02, UC17–UC24         | AC32, AC35, AC36               |
| BG06          | BR12                 | NFR01–NFR06, NFR13–NFR16 | Không áp dụng trực tiếp | AC37, AC38 và các tiêu chí TBD |


