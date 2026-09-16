# CAB SYSTEM – SOFTWARE REQUIREMENTS SPECIFICATION (BẢN RÚT GỌN 7 TUẦN)

> Mục tiêu của bản này: giữ đúng nghiệp vụ cốt lõi của hệ thống đặt xe, giảm số màn hình/Use Case/bảng dữ liệu không cần thiết và ưu tiên các chức năng có thể triển khai thực tế bằng Node.js trong thời gian 7 tuần.
>
> Các thay đổi chính so với bản trước:
> - Bỏ vai trò **Quản lý** và toàn bộ chức năng **Báo cáo**.
> - Bỏ toàn bộ chức năng **Đánh giá tài xế** và bảng `Rating`.
> - Gộp các chức năng tra cứu của nhân viên vận hành thành **Tra cứu dữ liệu hệ thống**.
> - Gộp **lịch sử chuyến** vào chức năng **xem/theo dõi chuyến**.
> - Gộp cập nhật thông tin khách hàng và cập nhật hồ sơ tài xế thành **Cập nhật hồ sơ người dùng**.
> - Giữ chức năng khách hàng hủy chuyến nhưng áp dụng chính sách đơn giản: chỉ được hủy khi chuyến đang tìm tài xế hoặc đã có tài xế nhưng tài xế chưa đến điểm đón.
> - Không có bước tài xế chấp nhận/từ chối chuyến. Hệ thống tự động gán tài xế phù hợp.

---

# BƯỚC 1. BUSINESS CONTEXT – BỐI CẢNH KINH DOANH

## 1.1. Business Context

Công ty ABC là doanh nghiệp cung cấp dịch vụ đặt xe trực tuyến. Hiện tại, khách hàng có thể yêu cầu xe thông qua tổng đài hoặc một ứng dụng đơn giản.

Hệ thống hiện tại còn một số hạn chế:
- Việc tìm và phân công tài xế còn phụ thuộc nhiều vào thao tác thủ công.
- Khách hàng khó theo dõi trạng thái chuyến.
- Thông tin thanh toán chưa được quản lý tập trung.
- Nhân viên vận hành khó theo dõi và xử lý các chuyến gặp sự cố.

CAB System được xây dựng cho các nhóm người dùng:
- Khách hàng.
- Tài xế.
- Nhân viên vận hành.

Ngoài ra, hệ thống có Nhà cung cấp thanh toán giả lập để mô phỏng thanh toán điện tử.

Quy trình nghiệp vụ chính:

**Khách hàng đặt xe → Hệ thống tự động gán tài xế → Tài xế thực hiện chuyến → Hệ thống tính cước → Khách hàng thanh toán.**

Do thời gian triển khai là **7 tuần** và nguồn lực phát triển hạn chế, phiên bản đầu chỉ tập trung vào các chức năng cốt lõi. Các chức năng báo cáo, đánh giá tài xế, GPS thời gian thực và quy trình xử lý sự cố phức tạp được chuyển ra ngoài phạm vi.

## 1.2. Business Problem – Vấn đề kinh doanh

Hệ thống hiện tại tồn tại các vấn đề:
- Phân công tài xế chủ yếu được thực hiện thủ công.
- Khi số lượng yêu cầu tăng, việc điều phối tài xế trở nên khó khăn.
- Khách hàng khó biết trạng thái hiện tại của chuyến.
- Khách hàng khó biết tài xế nào đã được gán.
- Thông tin thanh toán chưa được quản lý tập trung.
- Nhân viên vận hành khó theo dõi các chuyến đang hoạt động.
- Việc xử lý chuyến gặp sự cố chưa có cơ chế đơn giản và thống nhất.

### Vấn đề chính cần giải quyết

CAB System cần:
- Tự động hóa việc gán tài xế.
- Hỗ trợ khách hàng đặt xe.
- Hỗ trợ khách hàng xem chuyến hiện tại và các chuyến đã thực hiện.
- Hỗ trợ tài xế cập nhật trạng thái thực hiện chuyến.
- Quản lý thanh toán theo chuyến.
- Hỗ trợ nhân viên vận hành tra cứu dữ liệu, theo dõi chuyến và hủy chuyến khi có sự cố.

## 1.3. Trả lời các câu hỏi Business Context

### 1. Công ty ABC đang gặp vấn đề gì?

- Phân công tài xế còn thủ công.
- Khách hàng khó theo dõi chuyến.
- Thanh toán chưa được quản lý tập trung.
- Nhân viên vận hành khó theo dõi và xử lý chuyến gặp sự cố.

### 2. Vì sao hệ thống cũ không đáp ứng được?

- Chưa hỗ trợ tự động gán tài xế phù hợp.
- Chưa hỗ trợ đầy đủ cập nhật trạng thái chuyến.
- Chưa quản lý tập trung thông tin thanh toán.
- Chưa có màn hình vận hành đơn giản để theo dõi dữ liệu cần thiết.

### 3. Mục tiêu của hệ thống mới là gì?

- Tự động gán tài xế phù hợp, không cần chờ tài xế phản hồi.
- Cho phép khách hàng đặt xe.
- Cho phép khách hàng xem chuyến hiện tại và lịch sử chuyến.
- Cho phép khách hàng hủy chuyến trong điều kiện cho phép.
- Cho phép tài xế cập nhật trạng thái sẵn sàng và trạng thái chuyến.
- Quản lý thanh toán tiền mặt và thanh toán điện tử giả lập.
- Hỗ trợ nhân viên vận hành theo dõi và xử lý chuyến gặp sự cố.

### 4. Ai sử dụng hoặc tương tác với hệ thống?

| Đối tượng | Vai trò chính |
|---|---|
| Khách hàng | Đăng ký, đăng nhập, cập nhật hồ sơ, đặt xe, xem chuyến, hủy chuyến, thanh toán |
| Tài xế | Đăng nhập, cập nhật hồ sơ, phương tiện, trạng thái sẵn sàng và trạng thái chuyến |
| Nhân viên vận hành | Tạo tài khoản tài xế, tra cứu dữ liệu, theo dõi chuyến, hủy chuyến gặp sự cố |
| Nhà cung cấp thanh toán giả lập | Trả kết quả thanh toán điện tử |

---

# BƯỚC 2. STAKEHOLDER – CÁC BÊN LIÊN QUAN

## 2.1. Danh sách Stakeholder

| STT | Stakeholder | Vai trò |
|---|---|---|
| 1 | Ban lãnh đạo | Đưa ra định hướng và xác nhận mục tiêu hệ thống |
| 2 | Khách hàng | Sử dụng dịch vụ đặt xe |
| 3 | Tài xế | Nhận chuyến được hệ thống gán và thực hiện chuyến |
| 4 | Nhân viên vận hành | Theo dõi và hỗ trợ hoạt động vận hành |
| 5 | Nhà cung cấp thanh toán giả lập | Trả kết quả giao dịch điện tử |
| 6 | Business Analyst / Developer | Phân tích yêu cầu và trực tiếp xây dựng hệ thống |

## 2.2. Power – Interest

| Stakeholder | Power | Interest |
|---|---|---|
| Ban lãnh đạo | Cao | Cao |
| Business Analyst / Developer | Trung bình | Cao |
| Nhân viên vận hành | Trung bình | Cao |
| Khách hàng | Thấp | Cao |
| Tài xế | Thấp | Cao |
| Nhà cung cấp thanh toán giả lập | Trung bình | Thấp |

## 2.3. Stakeholder Matrix

- **Manage Closely:** Ban lãnh đạo.
- **Keep Satisfied:** Nhà cung cấp thanh toán giả lập.
- **Keep Informed:** Business Analyst / Developer, Nhân viên vận hành, Khách hàng, Tài xế.

---

# BƯỚC 3. BUSINESS GOAL – MỤC TIÊU KINH DOANH

| Mã | Business Goal | Mô tả |
|---|---|---|
| BG01 | Giảm thời gian tìm tài xế | Hệ thống tự động gán tài xế phù hợp, không cần chờ phản hồi thủ công |
| BG02 | Nâng cao trải nghiệm đặt xe | Khách hàng có thể đặt xe, xem trạng thái và lịch sử chuyến |
| BG03 | Nâng cao hiệu quả thanh toán | Quản lý số tiền và kết quả thanh toán theo từng chuyến |
| BG04 | Nâng cao hiệu quả vận hành | Nhân viên vận hành có thể tra cứu dữ liệu, theo dõi và hủy chuyến gặp sự cố |
| BG05 | Hỗ trợ phát triển hệ thống | Các nhóm chức năng được tổ chức tương đối độc lập, dễ mở rộng ở Phase 2 |

---

# BƯỚC 4. SCOPE – PHẠM VI

## 4.1. In-Scope

| STT | Hạng mục | Mô tả |
|---|---|---|
| 1 | Tài khoản khách hàng | Khách hàng tự đăng ký tài khoản |
| 2 | Đăng nhập | Khách hàng, tài xế và nhân viên vận hành đăng nhập |
| 3 | Hồ sơ người dùng | Khách hàng và tài xế cập nhật thông tin cá nhân |
| 4 | Tài khoản tài xế | Nhân viên vận hành tạo tài khoản cho tài xế |
| 5 | Phương tiện | Tài xế cập nhật phương tiện |
| 6 | Trạng thái tài xế | Tài xế cập nhật trạng thái sẵn sàng |
| 7 | Đặt xe | Khách hàng tạo yêu cầu đặt xe |
| 8 | Gán tài xế tự động | Hệ thống gán tài xế sẵn sàng có phương tiện phù hợp |
| 9 | Xem chuyến | Khách hàng xem chuyến hiện tại và lịch sử chuyến |
| 10 | Hủy chuyến | Khách hàng hủy chuyến trước khi tài xế đến điểm đón |
| 11 | Thực hiện chuyến | Tài xế cập nhật trạng thái chuyến |
| 12 | Thanh toán | Khách hàng thanh toán bằng tiền mặt hoặc điện tử giả lập |
| 13 | Tra cứu dữ liệu hệ thống | Nhân viên vận hành tra cứu khách hàng, tài xế, phương tiện hoặc giao dịch trên cùng một chức năng |
| 14 | Theo dõi chuyến vận hành | Nhân viên vận hành xem danh sách và trạng thái chuyến |
| 15 | Hủy chuyến gặp sự cố | Nhân viên vận hành hủy chuyến chưa hoàn thành và lưu lý do |
| 16 | Xác thực và phân quyền | Người dùng chỉ truy cập chức năng phù hợp vai trò |

## 4.2. Out-of-Scope

| STT | Hạng mục |
|---|---|
| 1 | Tài xế tự đăng ký tài khoản |
| 2 | Theo dõi GPS liên tục trên bản đồ |
| 3 | Thuật toán AI điều phối tài xế |
| 4 | Tài xế chấp nhận/từ chối yêu cầu chuyến |
| 5 | Tích hợp cổng thanh toán thật |
| 6 | Kết nối ngân hàng/thẻ thật |
| 7 | Lưu thông tin nhạy cảm của thẻ |
| 8 | Gửi SMS hoặc push notification thật |
| 9 | Quản lý tuyển dụng, hợp đồng, lương tài xế |
| 10 | Quy trình xử lý sự cố nhiều bước như điều tra, đổi tài xế hoặc bồi thường |
| 11 | Đánh giá tài xế |
| 12 | Báo cáo quản trị và biểu đồ |
| 13 | Báo cáo phân tích nâng cao |
| 14 | Các màn hình tra cứu riêng biệt cho từng loại dữ liệu |

---

# BƯỚC 5. BUSINESS REQUIREMENTS – YÊU CẦU NGHIỆP VỤ

| Mã | Business Requirement | Mô tả |
|---|---|---|
| BR01 | Quản lý tài khoản và hồ sơ | Hệ thống hỗ trợ đăng ký, đăng nhập và cập nhật hồ sơ người dùng |
| BR02 | Đặt xe | Khách hàng có thể tạo yêu cầu đặt xe |
| BR03 | Gán tài xế tự động | Hệ thống tự động gán tài xế phù hợp |
| BR04 | Quản lý hoạt động tài xế | Tài xế cập nhật phương tiện, trạng thái sẵn sàng và trạng thái chuyến |
| BR05 | Xem chuyến | Khách hàng xem chuyến hiện tại và lịch sử chuyến |
| BR06 | Hủy chuyến | Khách hàng hủy chuyến khi còn trong trạng thái cho phép |
| BR07 | Thanh toán | Khách hàng thanh toán cho chuyến đã hoàn thành |
| BR08 | Quản lý vận hành | Nhân viên vận hành tra cứu dữ liệu và theo dõi chuyến |
| BR09 | Hủy chuyến gặp sự cố | Nhân viên vận hành hủy chuyến chưa hoàn thành và lưu lý do |
| BR10 | Bảo mật | Hệ thống xác thực và phân quyền người dùng |
| BR11 | Khả năng phát triển | Hệ thống có thể mở rộng chức năng ở Phase 2 |

---

# BƯỚC 6. QUY TRÌNH NGHIỆP VỤ

## 6.1. Quy trình tạo tài khoản tài xế

1. Nhân viên vận hành đăng nhập.
2. Chọn chức năng **Tạo tài khoản tài xế**.
3. Nhập thông tin tài xế.
4. Hệ thống kiểm tra dữ liệu.
5. Hệ thống tạo tài khoản tài xế.
6. Tài xế sử dụng tài khoản được cấp để đăng nhập.

## 6.2. Quy trình đặt và thực hiện chuyến

1. Khách hàng đăng nhập.
2. Nhập điểm đón.
3. Nhập điểm đến.
4. Chọn loại xe.
5. Gửi yêu cầu đặt xe.
6. Hệ thống kiểm tra thông tin.
7. Hệ thống tạo chuyến với trạng thái **Đang tìm tài xế**.
8. Hệ thống tìm tài xế đang **Sẵn sàng**.
9. Hệ thống lọc tài xế có phương tiện phù hợp loại xe.
10. Hệ thống tự động gán tài xế phù hợp đầu tiên.
11. Nếu không có tài xế phù hợp, hệ thống cập nhật trạng thái **Không tìm được tài xế** và thông báo cho khách hàng.
12. Nếu gán thành công, hệ thống cập nhật trạng thái **Đã có tài xế**.
13. Hệ thống hiển thị thông tin tài xế cho khách hàng.
14. Tài xế cập nhật **Đã đến điểm đón**.
15. Tài xế cập nhật **Đã đón khách**.
16. Tài xế cập nhật **Đang thực hiện chuyến**.
17. Tài xế cập nhật **Đã hoàn thành**.
18. Hệ thống tính số tiền phải trả.
19. Khách hàng chọn phương thức thanh toán.
20. Nếu chọn tiền mặt, hệ thống ghi nhận thanh toán.
21. Nếu chọn điện tử, hệ thống gửi yêu cầu tới bộ giả lập thanh toán.
22. Bộ giả lập trả kết quả.
23. Hệ thống lưu kết quả thanh toán.
24. Quy trình kết thúc.

## 6.3. Quy trình khách hàng hủy chuyến

1. Khách hàng mở chuyến hiện tại.
2. Hệ thống hiển thị trạng thái chuyến.
3. Khách hàng chọn **Hủy chuyến**.
4. Hệ thống kiểm tra trạng thái.
5. Chỉ cho phép hủy khi trạng thái là:
   - **Đang tìm tài xế**, hoặc
   - **Đã có tài xế**.
6. Khách hàng xác nhận hủy.
7. Hệ thống cập nhật chuyến thành **Đã hủy**.
8. Nếu chuyến đã có tài xế, hệ thống chuyển tài xế về trạng thái **Sẵn sàng**.
9. Hệ thống thông báo hủy thành công.

> Phiên bản đầu không tính phí hủy chuyến.

## 6.4. Quy trình nhân viên vận hành hủy chuyến gặp sự cố

1. Nhân viên vận hành đăng nhập.
2. Mở danh sách chuyến.
3. Chọn chuyến gặp sự cố.
4. Hệ thống hiển thị thông tin chuyến.
5. Nhân viên nhập lý do hủy.
6. Xác nhận hủy.
7. Hệ thống cập nhật chuyến thành **Đã hủy**.
8. Nếu chuyến đã có tài xế, hệ thống chuyển tài xế về trạng thái **Sẵn sàng**.
9. Hệ thống lưu lý do hủy.

## 6.5. Trạng thái chuyến

Luồng chính:

`Đang tìm tài xế → Đã có tài xế → Đã đến điểm đón → Đã đón khách → Đang thực hiện chuyến → Đã hoàn thành`

Trạng thái kết thúc khác:
- `Không tìm được tài xế`
- `Đã hủy`

## 6.6. Trường hợp thay thế và ngoại lệ

- Thông tin đặt xe không hợp lệ → thông báo để khách hàng chỉnh sửa.
- Không tìm được tài xế → thông báo cho khách hàng.
- Khách hàng yêu cầu hủy sau khi tài xế đã đến điểm đón → từ chối hủy.
- Thanh toán điện tử giả lập thất bại → ghi nhận giao dịch thất bại.
- Tài xế cập nhật trạng thái sai trình tự → từ chối cập nhật.
- Chuyến gặp sự cố → nhân viên vận hành hủy chuyến kèm lý do.

---

# BƯỚC 7. FUNCTIONAL REQUIREMENTS – YÊU CẦU CHỨC NĂNG

## 7.1. Tài khoản và hồ sơ

| Mã | Yêu cầu chức năng |
|---|---|
| FR01 | Hệ thống cho phép khách hàng đăng ký tài khoản |
| FR02 | Hệ thống cho phép người dùng đăng nhập |
| FR03 | Hệ thống cho phép khách hàng và tài xế cập nhật hồ sơ cá nhân |
| FR04 | Hệ thống cho phép nhân viên vận hành tạo tài khoản tài xế |

## 7.2. Hoạt động tài xế

| Mã | Yêu cầu chức năng |
|---|---|
| FR05 | Hệ thống cho phép tài xế cập nhật phương tiện |
| FR06 | Hệ thống cho phép tài xế cập nhật trạng thái sẵn sàng |

## 7.3. Đặt xe và gán tài xế

| Mã | Yêu cầu chức năng |
|---|---|
| FR07 | Hệ thống cho phép khách hàng tạo yêu cầu đặt xe |
| FR08 | Hệ thống tìm tài xế đang sẵn sàng |
| FR09 | Hệ thống lọc tài xế có phương tiện phù hợp với loại xe khách hàng chọn |
| FR10 | Hệ thống tự động gán tài xế phù hợp đầu tiên |
| FR11 | Hệ thống thông báo khi không tìm được tài xế |

## 7.4. Chuyến đi

| Mã | Yêu cầu chức năng |
|---|---|
| FR12 | Hệ thống cho phép khách hàng xem chuyến hiện tại và lịch sử chuyến |
| FR13 | Hệ thống cho phép khách hàng hủy chuyến khi trạng thái còn cho phép |
| FR14 | Hệ thống cho phép tài xế cập nhật trạng thái chuyến theo đúng trình tự |

## 7.5. Thanh toán

| Mã | Yêu cầu chức năng |
|---|---|
| FR15 | Hệ thống tính số tiền phải trả khi chuyến hoàn thành |
| FR16 | Hệ thống cho phép khách hàng chọn phương thức thanh toán |
| FR17 | Hệ thống ghi nhận thanh toán tiền mặt |
| FR18 | Hệ thống gửi yêu cầu thanh toán điện tử tới bộ giả lập |
| FR19 | Hệ thống ghi nhận kết quả thanh toán |

## 7.6. Nhân viên vận hành

| Mã | Yêu cầu chức năng |
|---|---|
| FR20 | Hệ thống cho phép nhân viên vận hành tra cứu dữ liệu khách hàng, tài xế, phương tiện hoặc giao dịch trong cùng chức năng |
| FR21 | Hệ thống cho phép nhân viên vận hành theo dõi danh sách và trạng thái chuyến |
| FR22 | Hệ thống cho phép nhân viên vận hành hủy chuyến gặp sự cố và lưu lý do |

## 7.7. Xác thực và phân quyền

| Mã | Yêu cầu chức năng |
|---|---|
| FR23 | Hệ thống xác thực người dùng |
| FR24 | Hệ thống kiểm tra quyền truy cập theo vai trò |

---

# BƯỚC 8. BUSINESS RULES & BUSINESS EXCEPTIONS

## 8.1. Business Rules

| Mã | Business Rule |
|---|---|
| BRL01 | Khách hàng có thể tự đăng ký tài khoản |
| BRL02 | Tài khoản tài xế do nhân viên vận hành tạo |
| BRL03 | Người dùng phải đăng nhập trước khi sử dụng chức năng yêu cầu xác thực |
| BRL04 | Chỉ tài xế ở trạng thái Sẵn sàng mới được gán chuyến |
| BRL05 | Phương tiện của tài xế phải phù hợp loại xe khách hàng chọn |
| BRL06 | Một chuyến tại một thời điểm chỉ được gán cho một tài xế |
| BRL07 | Hệ thống tự động gán tài xế phù hợp đầu tiên, không cần tài xế xác nhận |
| BRL08 | Tài xế chỉ được cập nhật trạng thái của chuyến được phân công |
| BRL09 | Trạng thái chuyến phải cập nhật theo đúng trình tự |
| BRL10 | Chuyến hoàn thành mới được tính số tiền cuối cùng |
| BRL11 | Khách hàng có thể thanh toán tiền mặt hoặc điện tử giả lập |
| BRL12 | Thanh toán điện tử được xử lý qua bộ giả lập và có thể trả kết quả thành công hoặc thất bại |
| BRL13 | Khách hàng chỉ được hủy khi chuyến ở trạng thái Đang tìm tài xế hoặc Đã có tài xế |
| BRL14 | Nếu chuyến bị hủy sau khi đã gán tài xế thì tài xế được chuyển lại trạng thái Sẵn sàng |
| BRL15 | Nhân viên vận hành chỉ được hủy chuyến chưa hoàn thành và phải nhập lý do |
| BRL16 | Người dùng chỉ được truy cập chức năng phù hợp với vai trò |

## 8.2. Business Exceptions

| Mã | Ngoại lệ | Xử lý |
|---|---|---|
| BE01 | Thông tin đặt xe không hợp lệ | Thông báo để khách hàng chỉnh sửa |
| BE02 | Không có tài xế phù hợp | Cập nhật chuyến thành Không tìm được tài xế và thông báo |
| BE03 | Thanh toán điện tử giả lập thất bại | Ghi nhận giao dịch thất bại |
| BE04 | Thông tin đăng nhập không đúng | Từ chối đăng nhập |
| BE05 | Trạng thái chuyến không hợp lệ | Không cập nhật trạng thái |
| BE06 | Khách hàng hủy chuyến sau khi tài xế đã đến điểm đón | Từ chối hủy |
| BE07 | Chuyến gặp sự cố | Nhân viên vận hành hủy chuyến kèm lý do |

## 8.3. Các vấn đề TBD

- Công thức tính cước.
- Tiêu chí chọn tài xế khi có nhiều tài xế cùng phù hợp.

> Chính sách hủy chuyến không còn để TBD trong phiên bản này: chỉ cho phép khách hàng hủy ở trạng thái `SEARCHING_DRIVER` hoặc `DRIVER_ASSIGNED`, không tính phí hủy.

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
```

## 9.2. Driver

```text
Driver(
    driver_id PK,
    user_id FK,
    availability_status
)
```

Giá trị trạng thái đề xuất:

```text
AVAILABLE
BUSY
OFFLINE
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
    completed_at NULL,
    cancelled_at NULL
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

## 9.6. Quan hệ chính

```text
User 1 --- 0..1 Driver
Driver 1 --- N Vehicle
User 1 --- N Trip
Driver 1 --- N Trip
Trip 1 --- 0..1 Payment
```

> Bảng `Rating` được loại bỏ vì phiên bản đầu không triển khai chức năng đánh giá tài xế.

---

# BƯỚC 10. NON-FUNCTIONAL REQUIREMENTS

| Mã | Nhóm | Non-Functional Requirement |
|---|---|---|
| NFR01 | Performance | Các thao tác thông thường phản hồi trong thời gian hợp lý |
| NFR02 | Scalability | Thiết kế cho phép mở rộng số lượng người dùng và chuyến ở mức cơ bản |
| NFR03 | Authentication | Người dùng phải được xác thực trước khi dùng chức năng yêu cầu đăng nhập |
| NFR04 | Authorization | Người dùng chỉ truy cập chức năng phù hợp vai trò |
| NFR05 | Security | Mật khẩu phải được băm trước khi lưu |
| NFR06 | Payment Security | Không lưu thông tin thanh toán nhạy cảm |
| NFR07 | Reliability | Lỗi thanh toán không được làm mất thông tin chuyến |
| NFR08 | Maintainability | Các chức năng chính được tổ chức thành module tương đối độc lập |
| NFR09 | Extensibility | Có thể mở rộng thêm GPS, đánh giá, báo cáo, cổng thanh toán thật ở Phase 2 |

---

# BƯỚC 11. USE CASE DIAGRAM

## 11.1. Actor

| Actor | Vai trò |
|---|---|
| Khách hàng | Đăng ký, đăng nhập, cập nhật hồ sơ, đặt xe, xem chuyến, hủy chuyến, thanh toán |
| Tài xế | Đăng nhập, cập nhật hồ sơ, phương tiện, trạng thái sẵn sàng, trạng thái chuyến |
| Nhân viên vận hành | Đăng nhập, tạo tài khoản tài xế, tra cứu dữ liệu, theo dõi chuyến, hủy chuyến gặp sự cố |
| Nhà cung cấp thanh toán giả lập | Trả kết quả thanh toán điện tử |

## 11.2. Danh sách Use Case

### A. Use Case dùng chung

| Mã | Use Case | Actor |
|---|---|---|
| UC01 | Đăng nhập | Khách hàng, Tài xế, Nhân viên vận hành |
| UC03 | Cập nhật hồ sơ người dùng | Khách hàng, Tài xế |

### B. Khách hàng

| Mã | Use Case |
|---|---|
| UC02 | Đăng ký tài khoản khách hàng |
| UC04 | Đặt xe |
| UC05 | Xem chuyến |
| UC06 | Hủy chuyến |
| UC07 | Thanh toán chuyến |

### C. Tài xế

| Mã | Use Case |
|---|---|
| UC08 | Cập nhật phương tiện |
| UC09 | Cập nhật trạng thái tài xế |
| UC10 | Cập nhật trạng thái chuyến |

### D. Nhân viên vận hành

| Mã | Use Case |
|---|---|
| UC11 | Tạo tài khoản tài xế |
| UC12 | Tra cứu dữ liệu hệ thống |
| UC13 | Theo dõi chuyến |
| UC14 | Hủy chuyến gặp sự cố |

## 11.3. Quan hệ `<<include>>`

Các Use Case sau yêu cầu người dùng đã đăng nhập:
- UC03 Cập nhật hồ sơ người dùng.
- UC04 Đặt xe.
- UC05 Xem chuyến.
- UC06 Hủy chuyến.
- UC07 Thanh toán chuyến.
- UC08 Cập nhật phương tiện.
- UC09 Cập nhật trạng thái tài xế.
- UC10 Cập nhật trạng thái chuyến.
- UC11 Tạo tài khoản tài xế.
- UC12 Tra cứu dữ liệu hệ thống.
- UC13 Theo dõi chuyến.
- UC14 Hủy chuyến gặp sự cố.

UC02 Đăng ký tài khoản khách hàng không yêu cầu đăng nhập.

Nhà cung cấp thanh toán giả lập liên kết với UC07 Thanh toán chuyến.

---

# BƯỚC 12. ĐẶC TẢ USE CASE CHÍNH

## UC04. Đặt xe

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC04 |
| Tên Use Case | Đặt xe |
| Actor chính | Khách hàng |
| Tiền điều kiện | Khách hàng đã đăng nhập |
| Hậu điều kiện thành công | Chuyến được tạo và có tài xế được gán |
| Hậu điều kiện thất bại | Chuyến không được tạo hoặc không tìm được tài xế |

### Basic Flow

| Actor | Hệ thống |
|---|---|
| 1. Chọn chức năng đặt xe | 2. Hiển thị giao diện đặt xe |
| 3. Nhập điểm đón | |
| 4. Nhập điểm đến | |
| 5. Chọn loại xe | |
| 6. Gửi yêu cầu đặt xe | 7. Kiểm tra thông tin |
| | 8. Tạo chuyến trạng thái Đang tìm tài xế |
| | 9. Tìm tài xế Sẵn sàng và phương tiện phù hợp |
| | 10. Tự động gán tài xế phù hợp đầu tiên |
| | 11. Cập nhật trạng thái Đã có tài xế |
| | 12. Hiển thị thông tin tài xế |

### Exception Flow – Thông tin không hợp lệ

1. Tại bước 7, hệ thống xác định dữ liệu không hợp lệ.
2. Hệ thống thông báo nội dung cần chỉnh sửa.
3. Khách hàng chỉnh sửa.
4. Quay lại bước 6.

### Exception Flow – Không tìm được tài xế

1. Tại bước 9, không có tài xế phù hợp.
2. Hệ thống cập nhật trạng thái **Không tìm được tài xế**.
3. Hệ thống thông báo cho khách hàng.
4. Use Case kết thúc.

---

## UC05. Xem chuyến

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC05 |
| Tên Use Case | Xem chuyến |
| Actor chính | Khách hàng |
| Tiền điều kiện | Khách hàng đã đăng nhập |
| Hậu điều kiện thành công | Thông tin chuyến được hiển thị |
| Hậu điều kiện thất bại | Không thay đổi dữ liệu |

### Basic Flow

1. Khách hàng chọn chức năng **Chuyến của tôi**.
2. Hệ thống hiển thị chuyến hiện tại nếu có.
3. Hệ thống hiển thị danh sách các chuyến trước đó.
4. Khách hàng chọn một chuyến.
5. Hệ thống hiển thị chi tiết chuyến.

> Lịch sử chuyến được gộp vào UC05, không tạo Use Case riêng.

---

## UC06. Hủy chuyến

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC06 |
| Tên Use Case | Hủy chuyến |
| Actor chính | Khách hàng |
| Tiền điều kiện | Khách hàng đã đăng nhập; chuyến thuộc về khách hàng |
| Hậu điều kiện thành công | Chuyến chuyển sang Đã hủy |
| Hậu điều kiện thất bại | Trạng thái chuyến giữ nguyên |

### Basic Flow

1. Khách hàng mở chuyến hiện tại.
2. Chọn **Hủy chuyến**.
3. Hệ thống kiểm tra trạng thái chuyến.
4. Trạng thái hiện tại là **Đang tìm tài xế** hoặc **Đã có tài xế**.
5. Hệ thống yêu cầu xác nhận.
6. Khách hàng xác nhận.
7. Hệ thống cập nhật chuyến thành **Đã hủy**.
8. Nếu đã gán tài xế, hệ thống chuyển tài xế về **Sẵn sàng**.
9. Hệ thống thông báo hủy thành công.

### Exception Flow – Không được phép hủy

1. Tại bước 3, trạng thái chuyến từ **Đã đến điểm đón** trở đi.
2. Hệ thống từ chối hủy.
3. Hiển thị thông báo: **Chuyến không còn được phép hủy**.

---

## UC07. Thanh toán chuyến

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC07 |
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
| 4. Xác nhận thanh toán | 5. Gửi yêu cầu tới bộ giả lập |
| | 6. Nhận kết quả |
| | 7. Ghi nhận kết quả thanh toán |
| | 8. Thông báo cho khách hàng |

### Alternative Flow – Tiền mặt

1. Khách hàng chọn thanh toán tiền mặt.
2. Hệ thống ghi nhận phương thức.
3. Hệ thống ghi nhận thanh toán thành công.

### Exception Flow – Thanh toán điện tử thất bại

1. Bộ giả lập trả kết quả thất bại.
2. Hệ thống lưu trạng thái `FAILED`.
3. Hệ thống thông báo cho khách hàng.

---

## UC10. Cập nhật trạng thái chuyến

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC10 |
| Tên Use Case | Cập nhật trạng thái chuyến |
| Actor chính | Tài xế |
| Tiền điều kiện | Tài xế đã đăng nhập và được phân công chuyến |
| Hậu điều kiện thành công | Trạng thái chuyến được cập nhật |
| Hậu điều kiện thất bại | Trạng thái chuyến giữ nguyên |

### Basic Flow

| Actor | Hệ thống |
|---|---|
| 1. Chọn chuyến được phân công | 2. Hiển thị trạng thái hiện tại |
| 3. Chọn Đã đến điểm đón | 4. Cập nhật trạng thái |
| 5. Chọn Đã đón khách | 6. Cập nhật trạng thái |
| 7. Chọn Đang thực hiện chuyến | 8. Cập nhật trạng thái |
| 9. Chọn Đã hoàn thành | 10. Cập nhật trạng thái |
| | 11. Tính số tiền phải trả |

### Exception Flow – Sai trình tự

1. Tài xế chọn trạng thái không đúng trình tự.
2. Hệ thống từ chối cập nhật.
3. Hệ thống thông báo lỗi.
4. Trạng thái chuyến giữ nguyên.

---

## UC11. Tạo tài khoản tài xế

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC11 |
| Tên Use Case | Tạo tài khoản tài xế |
| Actor chính | Nhân viên vận hành |
| Tiền điều kiện | Nhân viên vận hành đã đăng nhập |
| Hậu điều kiện thành công | Tài khoản tài xế được tạo |
| Hậu điều kiện thất bại | Tài khoản không được tạo |

### Basic Flow

| Actor | Hệ thống |
|---|---|
| 1. Chọn chức năng tạo tài khoản tài xế | 2. Hiển thị biểu mẫu |
| 3. Nhập thông tin tài xế | |
| 4. Gửi yêu cầu | 5. Kiểm tra thông tin |
| | 6. Tạo tài khoản tài xế |
| | 7. Thông báo thành công |

### Exception Flow – Thông tin không hợp lệ

1. Tại bước 5, hệ thống phát hiện dữ liệu không hợp lệ.
2. Hệ thống thông báo nội dung cần chỉnh sửa.
3. Nhân viên chỉnh sửa.
4. Quay lại bước 4.

---

## UC12. Tra cứu dữ liệu hệ thống

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC12 |
| Tên Use Case | Tra cứu dữ liệu hệ thống |
| Actor chính | Nhân viên vận hành |
| Tiền điều kiện | Nhân viên vận hành đã đăng nhập |
| Hậu điều kiện thành công | Dữ liệu phù hợp được hiển thị |
| Hậu điều kiện thất bại | Hệ thống hiển thị danh sách rỗng hoặc thông báo không có dữ liệu |

### Basic Flow

1. Nhân viên vận hành mở chức năng **Tra cứu dữ liệu**.
2. Hệ thống cho chọn loại dữ liệu: **Khách hàng / Tài xế / Phương tiện / Giao dịch**.
3. Nhân viên chọn loại dữ liệu.
4. Nhập từ khóa tìm kiếm nếu cần.
5. Hệ thống hiển thị danh sách phù hợp.

> Không xây bốn Use Case và bốn màn hình riêng cho bốn nhóm dữ liệu.

---

## UC13. Theo dõi chuyến

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC13 |
| Tên Use Case | Theo dõi chuyến |
| Actor chính | Nhân viên vận hành |
| Tiền điều kiện | Nhân viên vận hành đã đăng nhập |
| Hậu điều kiện thành công | Danh sách và trạng thái chuyến được hiển thị |
| Hậu điều kiện thất bại | Không thay đổi dữ liệu |

### Basic Flow

1. Nhân viên vận hành mở danh sách chuyến.
2. Hệ thống hiển thị các chuyến và trạng thái hiện tại.
3. Nhân viên chọn một chuyến.
4. Hệ thống hiển thị chi tiết chuyến.

---

## UC14. Hủy chuyến gặp sự cố

| Thuộc tính | Nội dung |
|---|---|
| Mã Use Case | UC14 |
| Tên Use Case | Hủy chuyến gặp sự cố |
| Actor chính | Nhân viên vận hành |
| Tiền điều kiện | Nhân viên vận hành đã đăng nhập; chuyến chưa hoàn thành |
| Hậu điều kiện thành công | Chuyến chuyển sang Đã hủy và lưu lý do |
| Hậu điều kiện thất bại | Chuyến giữ nguyên |

### Basic Flow

| Actor | Hệ thống |
|---|---|
| 1. Chọn chuyến gặp sự cố | 2. Hiển thị thông tin chuyến |
| 3. Nhập lý do hủy | |
| 4. Xác nhận hủy | 5. Cập nhật trạng thái Đã hủy |
| | 6. Lưu lý do hủy |
| | 7. Nếu có tài xế, chuyển tài xế về Sẵn sàng |
| | 8. Thông báo kết quả |

---

# BƯỚC 13. ACCEPTANCE CRITERIA – TIÊU CHÍ CHẤP NHẬN

## 13.1. Tài khoản và hồ sơ

| Mã | Chức năng | Tiêu chí chấp nhận |
|---|---|---|
| AC01 | Đăng ký khách hàng | Nhập thông tin hợp lệ thì tài khoản khách hàng được tạo |
| AC02 | Đăng nhập | Nhập đúng thông tin thì đăng nhập thành công |
| AC03 | Đăng nhập | Nhập sai thông tin thì hệ thống từ chối và thông báo lỗi |
| AC04 | Cập nhật hồ sơ | Khách hàng hoặc tài xế cập nhật dữ liệu hợp lệ thì thông tin mới được lưu |
| AC05 | Tạo tài khoản tài xế | Nhân viên vận hành nhập thông tin hợp lệ thì tài khoản tài xế được tạo |

## 13.2. Tài xế

| Mã | Chức năng | Tiêu chí chấp nhận |
|---|---|---|
| AC06 | Cập nhật phương tiện | Tài xế lưu được thông tin phương tiện hợp lệ |
| AC07 | Trạng thái tài xế | Tài xế cập nhật được trạng thái Sẵn sàng/Không sẵn sàng |

## 13.3. Đặt xe và gán tài xế

| Mã | Chức năng | Tiêu chí chấp nhận |
|---|---|---|
| AC08 | Đặt xe | Thông tin hợp lệ thì chuyến được tạo |
| AC09 | Gán tài xế | Hệ thống chỉ gán tài xế Sẵn sàng có phương tiện phù hợp |
| AC10 | Không có tài xế | Không có tài xế phù hợp thì chuyến chuyển sang Không tìm được tài xế và khách hàng được thông báo |

## 13.4. Chuyến đi

| Mã | Chức năng | Tiêu chí chấp nhận |
|---|---|---|
| AC11 | Xem chuyến | Khách hàng xem được chuyến hiện tại |
| AC12 | Lịch sử chuyến | Khách hàng xem được danh sách các chuyến trước đó trong cùng chức năng |
| AC13 | Hủy chuyến | Khách hàng hủy được chuyến khi trạng thái là Đang tìm tài xế hoặc Đã có tài xế |
| AC14 | Hủy chuyến | Nếu chuyến đã có tài xế thì sau khi hủy tài xế trở lại trạng thái Sẵn sàng |
| AC15 | Cập nhật trạng thái | Tài xế cập nhật được Đã đến điểm đón |
| AC16 | Cập nhật trạng thái | Tài xế cập nhật được Đã đón khách |
| AC17 | Cập nhật trạng thái | Tài xế cập nhật được Đang thực hiện chuyến |
| AC18 | Cập nhật trạng thái | Tài xế cập nhật được Đã hoàn thành |

## 13.5. Thanh toán

| Mã | Chức năng | Tiêu chí chấp nhận |
|---|---|---|
| AC19 | Tính tiền | Chuyến hoàn thành thì hệ thống tính được số tiền phải trả |
| AC20 | Phương thức thanh toán | Khách hàng chọn được tiền mặt hoặc điện tử |
| AC21 | Tiền mặt | Hệ thống ghi nhận được thanh toán tiền mặt |
| AC22 | Điện tử giả lập | Hệ thống gửi yêu cầu tới bộ giả lập và ghi nhận kết quả |

## 13.6. Nhân viên vận hành

| Mã | Chức năng | Tiêu chí chấp nhận |
|---|---|---|
| AC23 | Tra cứu dữ liệu | Nhân viên vận hành chọn loại dữ liệu và tra cứu được khách hàng, tài xế, phương tiện hoặc giao dịch |
| AC24 | Theo dõi chuyến | Nhân viên vận hành xem được danh sách và trạng thái chuyến |
| AC25 | Hủy chuyến gặp sự cố | Nhân viên vận hành hủy được chuyến chưa hoàn thành và hệ thống lưu lý do |

## 13.7. Bảo mật

| Mã | Chức năng | Tiêu chí chấp nhận |
|---|---|---|
| AC26 | Phân quyền | Người dùng chỉ truy cập được chức năng đúng vai trò |
| AC27 | Từ chối truy cập | Người dùng không đủ quyền bị hệ thống từ chối |

---

# BƯỚC 14. REQUIREMENT TRACEABILITY MATRIX – RTM

| Business Goal | Business Requirement | Functional Requirement | Use Case | Acceptance Criteria |
|---|---|---|---|---|
| BG02 | BR01 | FR01–FR04 | UC01, UC02, UC03, UC11 | AC01–AC05 |
| BG02 | BR02 | FR07 | UC04 | AC08 |
| BG01 | BR03 | FR08–FR11 | UC04 | AC09–AC10 |
| BG01 | BR04 | FR05–FR06, FR14 | UC08–UC10 | AC06–AC07, AC15–AC18 |
| BG02 | BR05 | FR12 | UC05 | AC11–AC12 |
| BG02 | BR06 | FR13 | UC06 | AC13–AC14 |
| BG03 | BR07 | FR15–FR19 | UC07 | AC19–AC22 |
| BG04 | BR08 | FR20–FR21 | UC12–UC13 | AC23–AC24 |
| BG04 | BR09 | FR22 | UC14 | AC25 |
| BG05 | BR10 | FR23–FR24, NFR03–NFR07 | UC01–UC14 | AC26–AC27 |
| BG05 | BR11 | NFR02, NFR08–NFR09 | Toàn hệ thống | Kiểm tra trong quá trình triển khai |

---
