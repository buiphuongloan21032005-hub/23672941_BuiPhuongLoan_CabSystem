# BƯỚC 1. BUSINESS CONTEXT – BỐI CẢNH KINH DOANH

## 1.1. Business Context

Công ty ABC là doanh nghiệp cung cấp dịch vụ đặt xe trực tuyến. Hiện tại, khách hàng có thể yêu cầu xe thông qua tổng đài hoặc một ứng dụng đơn giản.

Tuy nhiên, hệ thống hiện tại còn nhiều hạn chế. Việc tìm và phân công tài xế chủ yếu được thực hiện thủ công, khách hàng khó theo dõi trạng thái chuyến đi, thông tin thanh toán chưa được quản lý tập trung và bộ phận vận hành gặp khó khăn khi số lượng khách hàng, tài xế và chuyến đi tăng.

Công ty ABC mong muốn xây dựng **CAB System** hỗ trợ các nhóm người dùng:

- Khách hàng.
- Tài xế.
- Nhân viên vận hành.
- Quản lý.

Ngoài ra, hệ thống có sự tham gia của **Nhà cung cấp thanh toán** đối với thanh toán điện tử (được giả lập trong phiên bản đầu).

Quy trình nghiệp vụ chính:

**Khách hàng tạo yêu cầu đặt xe → hệ thống tự động gán tài xế phù hợp → tài xế thực hiện chuyến → hệ thống tính cước → khách hàng thanh toán → khách hàng đánh giá tài xế.**

Do thời gian xây dựng và triển khai sản phẩm là **7 tuần** và nguồn lực triển khai là **1 người**, phiên bản đầu của CAB System tập trung vào các chức năng cốt lõi, được đơn giản hóa tối đa về mặt kỹ thuật và loại bỏ các cơ chế bất đồng bộ phức tạp như chờ phản hồi tài xế hoặc xử lý sự cố nhiều bước.

## 1.2. Business Problem – Vấn đề kinh doanh

Hệ thống hiện tại tồn tại các vấn đề:

- Việc tìm và phân công tài xế chủ yếu được thực hiện thủ công.
- Khi số lượng yêu cầu chuyến tăng, việc điều phối tài xế trở nên khó khăn.
- Khách hàng khó theo dõi trạng thái hiện tại của chuyến đi.
- Khách hàng khó biết tài xế nào đã nhận chuyến.
- Thông tin thanh toán chưa được quản lý tập trung.
- Bộ phận vận hành gặp khó khăn trong việc theo dõi chuyến đi.
- Bộ phận vận hành gặp khó khăn trong việc xử lý chuyến gặp sự cố.
- Hệ thống khó mở rộng khi số lượng người dùng và chuyến đi tăng.

### Vấn đề chính cần giải quyết

Công ty ABC cần xây dựng CAB System nhằm:

- Tự động hóa quá trình gán tài xế.
- Hỗ trợ khách hàng đặt xe.
- Hỗ trợ khách hàng theo dõi chuyến.
- Hỗ trợ tài xế thực hiện chuyến.
- Quản lý thanh toán theo chuyến.
- Hỗ trợ nhân viên vận hành tra cứu thông tin.
- Hỗ trợ nhân viên vận hành theo dõi chuyến.
- Cung cấp báo cáo cơ bản cho quản lý.

## 1.3. Trả lời các câu hỏi Business Context

### 1. Công ty ABC đang gặp vấn đề gì?

- Phân công tài xế chủ yếu thủ công.
- Khách hàng khó theo dõi chuyến.
- Thanh toán chưa được quản lý tập trung.
- Bộ phận vận hành khó theo dõi hoạt động.
- Hệ thống khó mở rộng khi quy mô tăng.

### 2. Vì sao hệ thống cũ không đáp ứng được?

- Chưa hỗ trợ tự động gán tài xế phù hợp.
- Chưa hỗ trợ đầy đủ việc cập nhật trạng thái chuyến.
- Chưa quản lý tập trung thông tin thanh toán.
- Khả năng mở rộng còn hạn chế.

### 3. Mục tiêu của hệ thống mới là gì?

- Tự động gán tài xế phù hợp, không cần chờ tài xế phản hồi.
- Cho phép khách hàng đặt xe.
- Cho phép khách hàng theo dõi chuyến.
- Cho phép tài xế cập nhật trạng thái chuyến.
- Quản lý thanh toán bằng tiền mặt và điện tử giả lập.
- Hỗ trợ nhân viên vận hành.
- Cung cấp báo cáo cơ bản cho quản lý.

### 4. Ai sử dụng hoặc tương tác với hệ thống?

| Đối tượng | Vai trò chính |
|---|---|
| Khách hàng | Đăng ký tài khoản, cập nhật thông tin, đặt xe, theo dõi chuyến, hủy chuyến, xem lịch sử, thanh toán, đánh giá |
| Tài xế | Cập nhật hồ sơ, cập nhật phương tiện, cập nhật trạng thái tài xế, cập nhật trạng thái chuyến |
| Nhân viên vận hành | Tạo tài khoản tài xế, tra cứu khách hàng, tra cứu tài xế, tra cứu phương tiện, theo dõi chuyến, hủy chuyến gặp sự cố, tra cứu giao dịch |
| Quản lý | Xem báo cáo cơ bản |
| Nhà cung cấp thanh toán (giả lập) | Trả kết quả thanh toán điện tử |

---

# BƯỚC 2. STAKEHOLDER – CÁC BÊN LIÊN QUAN

## 2.1. Danh sách Stakeholder

| STT | Stakeholder | Vai trò |
|---:|---|---|
| 1 | Ban lãnh đạo | Đưa ra định hướng và xác nhận mục tiêu của CAB System |
| 2 | Khách hàng | Sử dụng dịch vụ đặt xe |
| 3 | Tài xế | Nhận và thực hiện chuyến |
| 4 | Nhân viên vận hành | Theo dõi hoạt động vận hành |
| 5 | Quản lý | Theo dõi báo cáo hoạt động |
| 6 | Nhà cung cấp thanh toán (giả lập) | Trả kết quả giao dịch thanh toán điện tử |
| 7 | Business Analyst / Developer | Thu thập, phân tích, làm rõ yêu cầu và trực tiếp xây dựng hệ thống |

## 2.2. Power – Interest

| Stakeholder | Power | Interest |
|---|---|---|
| Ban lãnh đạo | Cao | Cao |
| Quản lý | Cao | Cao |
| Business Analyst / Developer | Trung bình | Cao |
| Nhân viên vận hành | Trung bình | Cao |
| Khách hàng | Thấp | Cao |
| Tài xế | Thấp | Cao |
| Nhà cung cấp thanh toán | Trung bình | Thấp |

## 2.3. Stakeholder Matrix

- **Manage Closely:** Ban lãnh đạo, Quản lý.
- **Keep Satisfied:** Nhà cung cấp thanh toán.
- **Keep Informed:** Business Analyst / Developer, Nhân viên vận hành, Khách hàng, Tài xế.
- **Monitor:** Chưa xác định stakeholder phù hợp.

---

# BƯỚC 3. BUSINESS GOAL – MỤC TIÊU KINH DOANH

> **Note:** Nên đặt tên là BG01... ví dụ BG01 tăng hiệu quả thanh toán thì mục đích → cho phép thanh toán bằng tiền mặt, chuyển khoản, online.
>
> VD: **BG01: Giảm thời gian tìm tài xế → cho phép tìm tài xế tự động.**

| Mã | Business Goal | Mô tả |
|---|---|---|
| BG01 | Giảm thời gian tìm tài xế | Hệ thống tự động gán tài xế phù hợp, không cần chờ phản hồi thủ công |
| BG02 | Nâng cao trải nghiệm đặt xe | Khách hàng có thể đặt xe và theo dõi chuyến |
| BG03 | Nâng cao hiệu quả thanh toán | Quản lý số tiền và kết quả thanh toán theo từng chuyến |
| BG04 | Nâng cao hiệu quả vận hành | Hỗ trợ nhân viên vận hành tra cứu và theo dõi hoạt động |
| BG05 | Hỗ trợ quản lý | Cung cấp báo cáo cơ bản về hoạt động |
| BG06 | Hỗ trợ phát triển hệ thống | Cho phép các chức năng chính được phát triển tương đối độc lập, dễ mở rộng ở Phase 2 |

---

# BƯỚC 4. SCOPE – PHẠM VI

## 4.1. In-Scope

| STT | Hạng mục | Mô tả |
|---:|---|---|
| 1 | Tài khoản khách hàng | Khách hàng đăng ký tài khoản |
| 2 | Thông tin khách hàng | Khách hàng cập nhật thông tin cá nhân |
| 3 | Tài khoản tài xế | Nhân viên vận hành tạo tài khoản cho tài xế |
| 4 | Hồ sơ tài xế | Tài xế cập nhật hồ sơ |
| 5 | Phương tiện | Tài xế cập nhật phương tiện |
| 6 | Trạng thái tài xế | Tài xế cập nhật trạng thái sẵn sàng |
| 7 | Đặt xe | Khách hàng tạo yêu cầu đặt xe |
| 8 | Gán tài xế tự động | Hệ thống tự động gán tài xế sẵn sàng, phù hợp phương tiện; không có bước tài xế chấp nhận hoặc từ chối |
| 9 | Theo dõi chuyến | Khách hàng theo dõi trạng thái chuyến |
| 10 | Hủy chuyến | Khách hàng hủy chuyến theo chính sách |
| 11 | Lịch sử chuyến | Khách hàng xem lịch sử chuyến |
| 12 | Thực hiện chuyến | Tài xế cập nhật trạng thái chuyến |
| 13 | Thanh toán | Khách hàng thanh toán chuyến bằng tiền mặt hoặc điện tử giả lập |
| 14 | Đánh giá | Khách hàng đánh giá tài xế |
| 15 | Tra cứu khách hàng | Nhân viên vận hành tra cứu khách hàng |
| 16 | Tra cứu tài xế | Nhân viên vận hành tra cứu tài xế |
| 17 | Tra cứu phương tiện | Nhân viên vận hành tra cứu phương tiện |
| 18 | Theo dõi chuyến | Nhân viên vận hành theo dõi chuyến |
| 19 | Hủy chuyến gặp sự cố | Nhân viên vận hành hủy chuyến kèm lý do khi có sự cố |
| 20 | Tra cứu giao dịch | Nhân viên vận hành tra cứu giao dịch |
| 21 | Báo cáo cơ bản | Quản lý xem báo cáo số lượng chuyến và doanh thu |

## 4.2. Out-of-Scope

| STT | Hạng mục |
|---:|---|
| 1 | Tài xế tự đăng ký tài khoản |
| 2 | Theo dõi GPS liên tục trên bản đồ |
| 3 | Thuật toán AI điều phối tài xế |
| 4 | Cơ chế tài xế chấp nhận hoặc từ chối yêu cầu chuyến, chuyển sang Phase 2 |
| 5 | Xây dựng cổng thanh toán riêng hoặc tích hợp cổng thanh toán thật |
| 6 | Kết nối ngân hàng hoặc thẻ thật trong phiên bản demo |
| 7 | Lưu thông tin nhạy cảm của thẻ |
| 8 | Gửi SMS hoặc push notification thực tế |
| 9 | Quản lý tuyển dụng, hợp đồng lao động, lương tài xế |
| 10 | Quy trình xử lý sự cố nhiều bước, chuyển sang Phase 2 |
| 11 | Báo cáo phân tích nâng cao như tỷ lệ hoàn thành, tỷ lệ hủy, hoạt động tài xế, chuyển sang Phase 2 |

---

# BƯỚC 5. BUSINESS REQUIREMENTS – YÊU CẦU NGHIỆP VỤ

> **Note:**
>
> VD: **BR02: Đặt xe:** Khách hàng có thể tạo yêu cầu đặt xe.
>
> VD: **BR03: Theo dõi chuyến đi:** Khách hàng có thể theo dõi chuyến đi trong quá trình di chuyển.

| Mã | Business Requirement | Mô tả |
|---|---|---|
| BR01 | Quản lý tài khoản | Hệ thống hỗ trợ tài khoản của các nhóm người dùng |
| BR02 | Đặt xe | Khách hàng có thể tạo yêu cầu đặt xe |
| BR03 | Gán tài xế tự động | Hệ thống tự động gán tài xế phù hợp với chuyến, không cần bước phản hồi thủ công |
| BR04 | Quản lý hoạt động tài xế | Tài xế cập nhật thông tin phục vụ hoạt động |
| BR05 | Theo dõi chuyến đi | Khách hàng theo dõi trạng thái chuyến |
| BR06 | Hủy chuyến | Khách hàng có thể hủy chuyến theo chính sách |
| BR07 | Thanh toán | Khách hàng có thể thanh toán chuyến |
| BR08 | Đánh giá tài xế | Khách hàng có thể đánh giá tài xế |
| BR09 | Quản lý vận hành | Nhân viên vận hành tra cứu và theo dõi hoạt động |
| BR10 | Hủy chuyến gặp sự cố | Nhân viên vận hành hủy chuyến kèm lý do khi có sự cố |
| BR11 | Báo cáo | Quản lý xem báo cáo cơ bản về hoạt động |
| BR12 | Bảo mật | Hệ thống xác thực và phân quyền người dùng |
| BR13 | Khả năng phát triển | Hệ thống hỗ trợ mở rộng trong tương lai ở Phase 2 |

---

# BƯỚC 6. QUY TRÌNH NGHIỆP VỤ

## 6.1. Quy trình tạo tài khoản tài xế

1. Nhân viên vận hành đăng nhập.
2. Nhân viên vận hành chọn chức năng **Tạo tài khoản tài xế**.
3. Nhân viên vận hành nhập thông tin tài xế.
4. Hệ thống kiểm tra thông tin.
5. Hệ thống tạo tài khoản tài xế.
6. Tài xế sử dụng tài khoản được tạo để đăng nhập.

## 6.2. Quy trình đặt và thực hiện chuyến

1. Khách hàng đăng nhập.
2. Khách hàng nhập điểm đón.
3. Khách hàng nhập điểm đến.
4. Khách hàng chọn loại xe.
5. Khách hàng gửi yêu cầu đặt xe.
6. Hệ thống kiểm tra thông tin đặt xe.
7. Hệ thống tạo chuyến với trạng thái **Đang tìm tài xế**.
8. Hệ thống tìm tài xế đang sẵn sàng.
9. Hệ thống tìm tài xế có phương tiện phù hợp.
10. Hệ thống **tự động gán** tài xế phù hợp đầu tiên cho chuyến.
11. Nếu không có tài xế phù hợp, hệ thống cập nhật trạng thái **Không tìm được tài xế**.
12. Hệ thống thông báo cho khách hàng.
13. Nếu gán thành công, hệ thống cập nhật trạng thái **Đã có tài xế**.
14. Hệ thống hiển thị thông tin tài xế cho khách hàng.
15. Tài xế cập nhật trạng thái **Đã đến điểm đón**.
16. Tài xế cập nhật trạng thái **Đã đón khách**.
17. Tài xế cập nhật trạng thái **Đang thực hiện chuyến**.
18. Tài xế cập nhật trạng thái **Đã hoàn thành**.
19. Hệ thống tính số tiền phải trả.
20. Khách hàng chọn phương thức thanh toán.
21. Nếu chọn tiền mặt, hệ thống ghi nhận thanh toán.
22. Nếu chọn thanh toán điện tử, hệ thống gửi yêu cầu đến Nhà cung cấp thanh toán giả lập.
23. Nhà cung cấp thanh toán giả lập trả kết quả thành công.
24. Hệ thống ghi nhận kết quả thanh toán.
25. Khách hàng có thể đánh giá tài xế.
26. Hệ thống lưu đánh giá.

> **Lưu ý:** So với bản gốc, quy trình đã bỏ các bước "gửi yêu cầu chuyến cho tài xế → chờ tài xế chấp nhận/từ chối/không phản hồi → tìm tài xế khác". Việc gán tài xế được thực hiện tự động và tức thời ở bước 10.

## 6.3. Trạng thái chuyến

```text
Đang tìm tài xế
→ Đã có tài xế
→ Đã đến điểm đón
→ Đã đón khách
→ Đang thực hiện chuyến
→ Đã hoàn thành
```

Trạng thái khác:

```text
Đã hủy
Không tìm được tài xế
```

## 6.4. Trường hợp thay thế và ngoại lệ

- **Thông tin đặt xe không hợp lệ:** Khách hàng chỉnh sửa thông tin.
- **Không tìm được tài xế phù hợp:** Hệ thống thông báo cho khách hàng.
- **Khách hàng hủy chuyến:** Hệ thống xử lý theo chính sách hủy.
- **Thanh toán điện tử thất bại:** Hệ thống ghi nhận kết quả thất bại.
- **Chuyến gặp sự cố:** Nhân viên vận hành hủy chuyến kèm lý do.

---

# BƯỚC 7. FUNCTIONAL REQUIREMENTS – YÊU CẦU CHỨC NĂNG

## 7.1. Tài khoản

| Mã | Yêu cầu chức năng |
|---|---|
| FR01 | Hệ thống cho phép khách hàng đăng ký tài khoản |
| FR02 | Hệ thống cho phép người dùng đăng nhập |
| FR03 | Hệ thống cho phép khách hàng cập nhật thông tin cá nhân |
| FR04 | Hệ thống cho phép nhân viên vận hành tạo tài khoản tài xế |
| FR05 | Hệ thống cho phép tài xế cập nhật hồ sơ |
| FR06 | Hệ thống cho phép tài xế cập nhật phương tiện |
| FR07 | Hệ thống cho phép tài xế cập nhật trạng thái tài xế |

## 7.2. Đặt xe

| Mã | Yêu cầu chức năng |
|---|---|
| FR08 | Hệ thống cho phép khách hàng tạo yêu cầu đặt xe |
| FR09 | Hệ thống tìm tài xế đang sẵn sàng |
| FR10 | Hệ thống tìm tài xế có phương tiện phù hợp |
| FR11 | Hệ thống tự động gán tài xế phù hợp đầu tiên cho chuyến |
| FR12 | Hệ thống thông báo khi không tìm được tài xế |

## 7.3. Chuyến đi

| Mã | Yêu cầu chức năng |
|---|---|
| FR13 | Hệ thống cho phép khách hàng theo dõi chuyến |
| FR14 | Hệ thống cho phép khách hàng hủy chuyến |
| FR15 | Hệ thống cho phép khách hàng xem lịch sử chuyến |
| FR16 | Hệ thống cho phép tài xế cập nhật trạng thái chuyến theo đúng trình tự |

## 7.4. Thanh toán

| Mã | Yêu cầu chức năng |
|---|---|
| FR17 | Hệ thống tính số tiền phải trả |
| FR18 | Hệ thống cho phép khách hàng chọn phương thức thanh toán |
| FR19 | Hệ thống ghi nhận thanh toán tiền mặt |
| FR20 | Hệ thống gửi yêu cầu thanh toán điện tử tới bộ giả lập |
| FR21 | Hệ thống ghi nhận kết quả thanh toán |

## 7.5. Đánh giá

| Mã | Yêu cầu chức năng |
|---|---|
| FR22 | Hệ thống cho phép khách hàng đánh giá tài xế |
| FR23 | Hệ thống lưu đánh giá |

## 7.6. Nhân viên vận hành

| Mã | Yêu cầu chức năng |
|---|---|
| FR24 | Hệ thống cho phép nhân viên vận hành tra cứu khách hàng |
| FR25 | Hệ thống cho phép nhân viên vận hành tra cứu tài xế |
| FR26 | Hệ thống cho phép nhân viên vận hành tra cứu phương tiện |
| FR27 | Hệ thống cho phép nhân viên vận hành theo dõi chuyến |
| FR28 | Hệ thống cho phép nhân viên vận hành hủy chuyến kèm lý do khi có sự cố |
| FR29 | Hệ thống cho phép nhân viên vận hành tra cứu giao dịch |

## 7.7. Báo cáo

| Mã | Yêu cầu chức năng |
|---|---|
| FR30 | Hệ thống cho phép quản lý xem báo cáo số lượng chuyến |
| FR31 | Hệ thống cho phép quản lý xem báo cáo doanh thu |

## 7.8. Phân quyền

| Mã | Yêu cầu chức năng |
|---|---|
| FR32 | Hệ thống xác thực người dùng |
| FR33 | Hệ thống kiểm tra quyền truy cập |

---

# BƯỚC 8. BUSINESS RULES & BUSINESS EXCEPTIONS

## 8.1. Business Rules

| Mã | Business Rule |
|---|---|
| BRL01 | Khách hàng có thể tự đăng ký tài khoản |
| BRL02 | Tài khoản tài xế do nhân viên vận hành tạo |
| BRL03 | Người dùng phải đăng nhập trước khi sử dụng chức năng yêu cầu xác thực |
| BRL04 | Chỉ tài xế sẵn sàng mới được gán vào chuyến |
| BRL05 | Phương tiện của tài xế phải phù hợp với yêu cầu đặt xe |
| BRL06 | Một chuyến tại một thời điểm chỉ được gán cho một tài xế |
| BRL07 | Hệ thống tự động gán tài xế phù hợp đầu tiên, không cần tài xế xác nhận |
| BRL08 | Tài xế chỉ cập nhật trạng thái chuyến được phân công |
| BRL09 | Trạng thái chuyến phải được cập nhật theo đúng trình tự |
| BRL10 | Chuyến hoàn thành mới được tính số tiền cuối cùng |
| BRL11 | Khách hàng có thể thanh toán tiền mặt hoặc điện tử giả lập |
| BRL12 | Thanh toán điện tử được xử lý qua bộ giả lập, mặc định trả kết quả thành công |
| BRL13 | Chuyến hoàn thành mới được đánh giá |
| BRL14 | Khách hàng hủy chuyến theo chính sách hủy |
| BRL15 | Người dùng chỉ được truy cập chức năng phù hợp với vai trò |

## 8.2. Business Exceptions

| Mã | Ngoại lệ | Xử lý |
|---|---|---|
| BE01 | Thông tin đặt xe không hợp lệ | Thông báo để khách hàng chỉnh sửa |
| BE02 | Không có tài xế phù hợp | Thông báo cho khách hàng |
| BE03 | Thanh toán điện tử giả lập thất bại | Ghi nhận thất bại |
| BE04 | Thông tin đăng nhập không đúng | Từ chối đăng nhập |
| BE05 | Trạng thái chuyến không hợp lệ | Không cập nhật trạng thái |
| BE06 | Khách hàng yêu cầu hủy chuyến | Xử lý theo chính sách hủy |
| BE07 | Chuyến gặp sự cố | Nhân viên vận hành hủy chuyến kèm lý do |

## 8.3. Các vấn đề TBD

- Công thức tính cước.
- Tiêu chí chọn tài xế khi có nhiều tài xế cùng phù hợp, ví dụ thứ tự tạo tài khoản hoặc ngẫu nhiên.
- Chính sách hủy chuyến.
- Chính sách xử lý thanh toán thất bại.

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
    role,
    status
)
```

Các giá trị `role`:

```text
CUSTOMER
DRIVER
STAFF
MANAGER
```

## 9.2. Driver

```text
Driver(
    driver_id PK,
    user_id FK,
    availability_status
)
```

## 9.3. Vehicle

```text
Vehicle(
    vehicle_id PK,
    driver_id FK,
    vehicle_type,
    license_plate,
    vehicle_name,
    status
)
```

## 9.4. Trip

```text
Trip(
    trip_id PK,
    customer_id FK,
    driver_id FK NULL,
    pickup_address,
    destination_address,
    vehicle_type,
    trip_status,
    fare_amount,
    cancel_reason NULL,
    created_at,
    completed_at,
    cancelled_at
)
```

Các trạng thái:

```text
SEARCHING_DRIVER
DRIVER_ASSIGNED
DRIVER_ARRIVED
PICKED_UP
IN_PROGRESS
COMPLETED
NO_DRIVER
CANCELLED
```

## 9.5. Payment

```text
Payment(
    payment_id PK,
    trip_id FK,
    amount,
    payment_method,
    payment_status
)
```

Phương thức:

```text
CASH
ELECTRONIC
```

Trạng thái:

```text
PENDING
SUCCESS
FAILED
```

## 9.6. Rating

```text
Rating(
    rating_id PK,
    trip_id FK,
    customer_id FK,
    driver_id FK,
    score,
    comment
)
```

## 9.7. Quan hệ chính

```text
User 1 --- 0..1 Driver

Driver 1 --- N Vehicle

User 1 --- N Trip
Driver 1 --- N Trip

Trip 1 --- 0..1 Payment
Trip 1 --- 0..1 Rating
```

> **Lưu ý:** So với bản gốc, bảng **DriverRequest** đã được loại bỏ do không còn cơ chế gửi yêu cầu/chờ phản hồi tài xế. Việc gán tài xế được ghi nhận trực tiếp qua trường `driver_id` trong bảng `Trip`.

---

# BƯỚC 10. NON-FUNCTIONAL REQUIREMENTS

| Mã | Nhóm | Non-Functional Requirement |
|---|---|---|
| NFR01 | Performance | Hệ thống phản hồi các thao tác thông thường trong thời gian hợp lý |
| NFR02 | Scalability | Hệ thống có khả năng mở rộng khi số lượng người dùng tăng, ở mức thiết kế, chưa cần kiểm thử tải trong phiên bản đầu |
| NFR03 | Authentication | Người dùng phải được xác thực trước khi sử dụng chức năng yêu cầu đăng nhập |
| NFR04 | Authorization | Người dùng chỉ được truy cập chức năng phù hợp với vai trò |
| NFR05 | Security | Mật khẩu phải được băm trước khi lưu |
| NFR06 | Payment Security | Hệ thống không lưu thông tin thanh toán nhạy cảm |
| NFR07 | Reliability | Lỗi thanh toán không được làm mất thông tin chuyến |
| NFR08 | Maintainability | Các nhóm chức năng chính được tổ chức thành các module tương đối độc lập để dễ bảo trì với 1 developer |
| NFR09 | Extensibility | Hệ thống có thể mở rộng thêm chức năng trong tương lai như cơ chế chấp nhận/từ chối chuyến, cổng thanh toán thật và báo cáo nâng cao |

---

# BƯỚC 11. USE CASE DIAGRAM
<img width="1538" height="1176" alt="image" src="https://github.com/user-attachments/assets/524bc5f1-6cce-4e32-a990-ce9dfc7c610e" />

## 11.1. Actor

| Actor | Vai trò |
|---|---|
| Khách hàng | Đăng ký tài khoản, cập nhật thông tin cá nhân, đặt xe, theo dõi chuyến, hủy chuyến, xem lịch sử chuyến, đánh giá tài xế, thanh toán chuyến |
| Tài xế | Cập nhật hồ sơ, cập nhật phương tiện, cập nhật trạng thái tài xế, cập nhật trạng thái chuyến |
| Nhân viên vận hành | Tra cứu khách hàng, tra cứu tài xế, tra cứu phương tiện, theo dõi chuyến, hủy chuyến gặp sự cố, tra cứu giao dịch, tạo tài khoản tài xế |
| Quản lý | Xem báo cáo cơ bản |
| Nhà cung cấp thanh toán (giả lập) | Trả kết quả thanh toán điện tử |

## 11.2. Danh sách Use Case

### A. Use Case dùng chung

| Mã | Use Case | Actor |
|---|---|---|
| UC01 | Đăng nhập | Khách hàng, Tài xế, Nhân viên vận hành, Quản lý |

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
| UC10 | Cập nhật hồ sơ |
| UC11 | Cập nhật phương tiện |
| UC12 | Cập nhật trạng thái tài xế |
| UC13 | Cập nhật trạng thái chuyến đi |

### D. Nhân viên vận hành

| Mã | Use Case |
|---|---|
| UC14 | Tra cứu khách hàng |
| UC15 | Tra cứu tài xế |
| UC16 | Tra cứu phương tiện |
| UC17 | Theo dõi chuyến |
| UC18 | Hủy chuyến gặp sự cố |
| UC19 | Tra cứu giao dịch |
| UC20 | Tạo tài khoản tài xế |

### E. Quản lý

| Mã | Use Case |
|---|---|
| UC21 | Xem báo cáo |

> **Lưu ý:** So với bản gốc, Use Case **"Phản hồi yêu cầu chuyến" (UC13 cũ)** đã được loại bỏ vì hệ thống tự động gán tài xế. Toàn bộ mã Use Case phía sau được đánh số lại liên tục.

## 11.3. Quan hệ `<<include>>`

Theo sơ đồ Use Case:

- Cập nhật thông tin cá nhân `<<include>>` Đăng nhập.
- Đặt xe `<<include>>` Đăng nhập.
- Theo dõi chuyến đi `<<include>>` Đăng nhập.
- Hủy chuyến `<<include>>` Đăng nhập.
- Xem lịch sử chuyến đi `<<include>>` Đăng nhập.
- Đánh giá tài xế `<<include>>` Đăng nhập.
- Thanh toán chuyến `<<include>>` Đăng nhập.
- Cập nhật hồ sơ `<<include>>` Đăng nhập.
- Cập nhật phương tiện `<<include>>` Đăng nhập.
- Cập nhật trạng thái tài xế `<<include>>` Đăng nhập.
- Cập nhật trạng thái chuyến đi `<<include>>` Đăng nhập.
- Tra cứu khách hàng `<<include>>` Đăng nhập.
- Tra cứu tài xế `<<include>>` Đăng nhập.
- Tra cứu phương tiện `<<include>>` Đăng nhập.
- Theo dõi chuyến `<<include>>` Đăng nhập.
- Hủy chuyến gặp sự cố `<<include>>` Đăng nhập.
- Tra cứu giao dịch `<<include>>` Đăng nhập.
- Tạo tài khoản tài xế `<<include>>` Đăng nhập.
- Xem báo cáo `<<include>>` Đăng nhập.

**Đăng ký tài khoản khách hàng không `<<include>>` Đăng nhập.**

Nhà cung cấp thanh toán giả lập liên kết với **Thanh toán chuyến**.

---

# BƯỚC 12. ĐẶC TẢ USE CASE CHÍNH

## UC04. Đặt xe

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC04 |
| Tên Use Case | Đặt xe |
| Actor chính | Khách hàng |
| Tiền điều kiện | Khách hàng đã đăng nhập |
| Hậu điều kiện thành công | Chuyến được tạo và có tài xế được gán tự động |
| Hậu điều kiện thất bại | Chuyến không được tạo hoặc không tìm được tài xế |

### Basic Flow

| Actor | Hệ thống |
|---|---|
| 1. Chọn chức năng đặt xe | 2. Hiển thị giao diện đặt xe |
| 3. Nhập điểm đón | |
| 4. Nhập điểm đến | |
| 5. Chọn loại xe | |
| 6. Gửi yêu cầu đặt xe | 7. Kiểm tra thông tin đặt xe |
| | 8. Tạo chuyến với trạng thái **Đang tìm tài xế** |
| | 9. Tìm tài xế đang sẵn sàng, có phương tiện phù hợp |
| | 10. Tự động gán tài xế phù hợp đầu tiên cho chuyến |
| | 11. Cập nhật trạng thái **Đã có tài xế** |
| | 12. Hiển thị thông tin tài xế |

### Exception Flow – Thông tin không hợp lệ

1. Tại bước 7, hệ thống xác định thông tin không hợp lệ.
2. Hệ thống thông báo thông tin cần chỉnh sửa.
3. Khách hàng chỉnh sửa thông tin.
4. Luồng quay lại bước 6.

### Exception Flow – Không tìm được tài xế

1. Tại bước 9, hệ thống không tìm thấy tài xế phù hợp.
2. Hệ thống cập nhật trạng thái **Không tìm được tài xế**.
3. Hệ thống thông báo cho khách hàng.
4. Use Case kết thúc.

> **Lưu ý:** Các Alternative Flow "Tài xế từ chối" và "Tài xế không phản hồi" trong bản gốc đã được loại bỏ do cơ chế gán tự động.

---

## UC13. Cập nhật trạng thái chuyến đi

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC13 |
| Tên Use Case | Cập nhật trạng thái chuyến đi |
| Actor chính | Tài xế |
| Tiền điều kiện | Tài xế đã đăng nhập và được phân công chuyến |
| Hậu điều kiện thành công | Trạng thái chuyến được cập nhật |
| Hậu điều kiện thất bại | Trạng thái chuyến được giữ nguyên |

### Basic Flow

| Actor | Hệ thống |
|---|---|
| 1. Chọn chuyến được phân công | 2. Hiển thị trạng thái chuyến |
| 3. Chọn **Đã đến điểm đón** | 4. Cập nhật trạng thái |
| 5. Chọn **Đã đón khách** | 6. Cập nhật trạng thái |
| 7. Chọn **Đang thực hiện chuyến** | 8. Cập nhật trạng thái |
| 9. Chọn **Đã hoàn thành** | 10. Cập nhật trạng thái |
| | 11. Tính số tiền phải trả |

### Exception Flow – Trạng thái không hợp lệ

1. Tài xế chọn trạng thái không đúng trình tự.
2. Hệ thống từ chối cập nhật và thông báo lỗi.
3. Trạng thái chuyến giữ nguyên.

---

## UC09. Thanh toán chuyến

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC09 |
| Tên Use Case | Thanh toán chuyến |
| Actor chính | Khách hàng |
| Actor phụ | Nhà cung cấp thanh toán giả lập |
| Tiền điều kiện | Chuyến đã hoàn thành |
| Hậu điều kiện thành công | Kết quả thanh toán được ghi nhận |
| Hậu điều kiện thất bại | Giao dịch thất bại được ghi nhận |

### Basic Flow – Thanh toán điện tử giả lập

| Actor | Hệ thống |
|---|---|
| 1. Chọn thanh toán chuyến | 2. Hiển thị số tiền phải trả |
| 3. Chọn thanh toán điện tử | |
| 4. Xác nhận thanh toán | 5. Gửi yêu cầu tới bộ giả lập thanh toán |
| | 6. Nhận kết quả, mặc định thành công |
| | 7. Ghi nhận kết quả thanh toán |
| | 8. Thông báo cho khách hàng |

### Alternative Flow – Tiền mặt

1. Khách hàng chọn thanh toán tiền mặt.
2. Hệ thống ghi nhận phương thức thanh toán.
3. Hệ thống ghi nhận kết quả thanh toán thành công.

### Exception Flow – Thanh toán thất bại giả lập

1. Bộ giả lập trả kết quả thất bại.
2. Hệ thống ghi nhận giao dịch thất bại.
3. Hệ thống thông báo cho khách hàng.

---

## UC18. Hủy chuyến gặp sự cố

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC18 |
| Tên Use Case | Hủy chuyến gặp sự cố |
| Actor chính | Nhân viên vận hành |
| Tiền điều kiện | Nhân viên vận hành đã đăng nhập; chuyến đang ở trạng thái chưa hoàn thành |
| Hậu điều kiện thành công | Chuyến được cập nhật sang trạng thái **Đã hủy** kèm lý do |
| Hậu điều kiện thất bại | Chuyến không được hủy |

### Basic Flow

| Actor | Hệ thống |
|---|---|
| 1. Chọn chuyến gặp sự cố | 2. Hiển thị thông tin chuyến |
| 3. Nhập lý do hủy | |
| 4. Xác nhận hủy | 5. Cập nhật trạng thái chuyến sang **Đã hủy** |
| | 6. Lưu lý do hủy |
| | 7. Thông báo cho khách hàng |

> **Lưu ý:** So với bản gốc (UC19 – Xử lý chuyến gặp sự cố với quy trình chi tiết), Use Case này đã được đơn giản hóa thành thao tác hủy chuyến kèm lý do, phù hợp với năng lực triển khai trong 7 tuần. Quy trình xử lý sự cố đầy đủ như điều tra, chuyển tài xế khác hoặc bồi thường được chuyển sang Phase 2.

---

## UC20. Tạo tài khoản tài xế

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC20 |
| Tên Use Case | Tạo tài khoản tài xế |
| Actor chính | Nhân viên vận hành |
| Tiền điều kiện | Nhân viên vận hành đã đăng nhập |
| Hậu điều kiện thành công | Tài khoản tài xế được tạo |
| Hậu điều kiện thất bại | Tài khoản tài xế không được tạo |

### Basic Flow

| Actor | Hệ thống |
|---|---|
| 1. Chọn chức năng tạo tài khoản tài xế | 2. Hiển thị giao diện tạo tài khoản |
| 3. Nhập thông tin tài xế | |
| 4. Gửi yêu cầu tạo tài khoản | 5. Kiểm tra thông tin |
| | 6. Tạo tài khoản tài xế |
| | 7. Thông báo tạo tài khoản thành công |

### Exception Flow – Thông tin không hợp lệ

1. Tại bước 5, hệ thống xác định thông tin không hợp lệ.
2. Hệ thống thông báo thông tin cần chỉnh sửa.
3. Nhân viên vận hành chỉnh sửa thông tin.
4. Luồng quay lại bước 4.

---

# BƯỚC 13. ACCEPTANCE CRITERIA – TIÊU CHÍ CHẤP NHẬN

> **Note:** Nhờ Acceptance Criteria mà dự án mới được nghiệm thu, cho biết khi nào chức năng được xem là hoàn thành và có thể nghiệm thu.

## 13.1. Tài khoản

| Mã | Chức năng | Tiêu chí chấp nhận |
|---|---|---|
| AC01 | Đăng ký khách hàng | Khách hàng nhập thông tin hợp lệ thì tài khoản được tạo |
| AC02 | Đăng nhập | Người dùng nhập đúng thông tin thì đăng nhập thành công |
| AC03 | Đăng nhập | Người dùng nhập sai thông tin thì hệ thống thông báo lỗi |
| AC04 | Cập nhật thông tin cá nhân | Thông tin hợp lệ thì dữ liệu mới được lưu |
| AC05 | Tạo tài khoản tài xế | Nhân viên vận hành nhập thông tin hợp lệ thì tài khoản tài xế được tạo |
| AC06 | Cập nhật hồ sơ | Tài xế cập nhật được thông tin hồ sơ |
| AC07 | Cập nhật phương tiện | Tài xế cập nhật được thông tin phương tiện |
| AC08 | Cập nhật trạng thái tài xế | Tài xế cập nhật được trạng thái sẵn sàng |

## 13.2. Đặt xe

| Mã | Chức năng | Tiêu chí chấp nhận |
|---|---|---|
| AC09 | Đặt xe | Thông tin hợp lệ thì chuyến được tạo |
| AC10 | Gán tài xế | Hệ thống tìm và tự động gán tài xế đang sẵn sàng, có phương tiện phù hợp |
| AC11 | Gán tài xế | Không có tài xế phù hợp thì khách hàng được thông báo |

## 13.3. Chuyến đi

| Mã | Chức năng | Tiêu chí chấp nhận |
|---|---|---|
| AC12 | Theo dõi chuyến | Khách hàng xem được trạng thái chuyến |
| AC13 | Hủy chuyến | Khách hàng hủy được chuyến khi thỏa chính sách |
| AC14 | Lịch sử chuyến | Khách hàng xem được lịch sử chuyến |
| AC15 | Cập nhật trạng thái | Tài xế cập nhật được trạng thái **Đã đến điểm đón** |
| AC16 | Cập nhật trạng thái | Tài xế cập nhật được trạng thái **Đã đón khách** |
| AC17 | Cập nhật trạng thái | Tài xế cập nhật được trạng thái **Đang thực hiện chuyến** |
| AC18 | Cập nhật trạng thái | Tài xế cập nhật được trạng thái **Đã hoàn thành** |

## 13.4. Thanh toán và đánh giá

| Mã | Chức năng | Tiêu chí chấp nhận |
|---|---|---|
| AC19 | Tính tiền | Chuyến hoàn thành thì hệ thống tính được số tiền phải trả |
| AC20 | Thanh toán | Khách hàng chọn được phương thức thanh toán |
| AC21 | Thanh toán tiền mặt | Hệ thống ghi nhận được thanh toán tiền mặt |
| AC22 | Thanh toán điện tử | Hệ thống gửi được yêu cầu tới bộ giả lập và ghi nhận kết quả |
| AC23 | Đánh giá | Chuyến hoàn thành thì khách hàng có thể đánh giá tài xế |
| AC24 | Đánh giá | Đánh giá hợp lệ được lưu |

## 13.5. Nhân viên vận hành

| Mã | Chức năng | Tiêu chí chấp nhận |
|---|---|---|
| AC25 | Tra cứu khách hàng | Nhân viên vận hành tra cứu được khách hàng |
| AC26 | Tra cứu tài xế | Nhân viên vận hành tra cứu được tài xế |
| AC27 | Tra cứu phương tiện | Nhân viên vận hành tra cứu được phương tiện |
| AC28 | Theo dõi chuyến | Nhân viên vận hành xem được trạng thái chuyến |
| AC29 | Hủy chuyến gặp sự cố | Nhân viên vận hành hủy được chuyến kèm lý do |
| AC30 | Tra cứu giao dịch | Nhân viên vận hành tra cứu được giao dịch |

## 13.6. Báo cáo

| Mã | Chức năng | Tiêu chí chấp nhận |
|---|---|---|
| AC31 | Báo cáo | Quản lý xem được số lượng chuyến |
| AC32 | Báo cáo | Quản lý xem được doanh thu |

## 13.7. Bảo mật

| Mã | Chức năng | Tiêu chí chấp nhận |
|---|---|---|
| AC33 | Phân quyền | Người dùng chỉ truy cập được chức năng phù hợp với vai trò |
| AC34 | Bảo mật | Người dùng không đủ quyền bị từ chối truy cập |

---

# BƯỚC 14. REQUIREMENT TRACEABILITY MATRIX – RTM

> **Note:** Truy xuất nguồn gốc yêu cầu (**Traceability Requirements**) – RTM (**Requirement Traceability Matrix**) dùng để kiểm tra một yêu cầu nghiệp vụ được liên kết từ Business Goal → Business Requirement → Functional Requirement → Use Case → Acceptance Criteria.

| Business Goal | Business Requirement | Functional Requirement | Use Case | Acceptance Criteria |
|---|---|---|---|---|
| BG02 | BR01 | FR01–FR07 | UC01, UC02, UC03, UC10–UC12, UC20 | AC01–AC08 |
| BG02 | BR02 | FR08 | UC04 | AC09 |
| BG01 | BR03 | FR09–FR12 | UC04 | AC10–AC11 |
| BG01 | BR04 | FR05–FR07, FR16 | UC10–UC13 | AC06–AC08, AC15–AC18 |
| BG02 | BR05 | FR13 | UC05 | AC12 |
| BG02 | BR06 | FR14 | UC06 | AC13 |
| BG03 | BR07 | FR17–FR21 | UC09 | AC19–AC22 |
| BG02 | BR08 | FR22–FR23 | UC08 | AC23–AC24 |
| BG04 | BR09 | FR24–FR27, FR29 | UC14–UC17, UC19 | AC25–AC28, AC30 |
| BG04 | BR10 | FR28 | UC18 | AC29 |
| BG05 | BR11 | FR30–FR31 | UC21 | AC31–AC32 |
| BG06 | BR12 | FR32–FR33, NFR03–NFR07 | UC01–UC21 | AC33–AC34 |
| BG06 | BR13 | NFR02, NFR08–NFR09 | Toàn hệ thống | Kiểm tra trong quá trình triển khai |

---
