# Bước 1 Xác định  
## Business Context (Bối cảnh kinh doanh) : 
Công ty ABC là doanh nghiệp cung cấp dịch vụ đặt xe trực tuyến. Hiện tại, khách hàng có thể đặt xe thông qua tổng đài hoặc một ứng dụng đơn giản. Tuy nhiên, việc phân công tài xế vẫn chủ yếu được thực hiện thủ công, khách hàng gặp khó khăn trong việc theo dõi trạng thái chuyến đi và thông tin thanh toán chưa được quản lý tập trung.
Doanh nghiệp mong muốn xây dựng CAB System thành một nền tảng đặt xe mới, có khả năng phục vụ số lượng lớn người dùng và hỗ trợ ít nhất ba nhóm người dùng chính:
+Khách hàng
+Tài xế
+Nhân viên vận hành
Hệ thống cần có khả năng mở rộng và bổ sung các chức năng mới trong tương lai mà không phải xây dựng lại toàn bộ ứng dụng.
## business problem
Hệ thống hiện tại của Công ty ABC đang tồn tại một số vấn đề ảnh hưởng đến hoạt động kinh doanh:
Việc tìm kiếm và phân công tài xế chủ yếu được thực hiện thủ công, gây khó khăn khi số lượng chuyến tăng.
Khách hàng khó theo dõi trạng thái chuyến đi, chẳng hạn như hệ thống đang tìm tài xế, tài xế nào đã nhận chuyến hoặc thời gian tài xế dự kiến đến.
Thông tin thanh toán chưa được quản lý tập trung, gây khó khăn trong việc quản lý và tra cứu giao dịch.
Hệ thống hiện tại khó mở rộng khi số lượng khách hàng, tài xế và chuyến đi tăng.
Việc bổ sung các dịch vụ, phương thức thanh toán hoặc chức năng mới trong tương lai còn gặp nhiều hạn chế.
Vấn đề chính cần giải quyết: Công ty ABC cần một nền tảng CAB mới giúp tự động hóa quy trình đặt và điều phối xe, nâng cao khả năng theo dõi chuyến đi, quản lý tập trung thanh toán và hỗ trợ mở rộng hệ thống trong tương lai.

Trả lời các câu hỏi: 
## 1 .Khách hàng (công ty ABC) đang gặp vấn đề gì?
Công ty ABC hiện đang cho khách đặt xe qua tổng đài hoặc một app đơn giản. Nhưng cách làm này có mấy cái dở:
Xếp tài xế bằng tay – nhân viên phải tự chọn tài xế cho khách, không tự động.
Khách không biết chuyến đi của mình tới đâu rồi – không theo dõi được trạng thái.
Tiền bạc, thanh toán không quản lý tập trung – mỗi nơi một ít, khó kiểm soát.
Muốn mở rộng (thêm khách, thêm tài xế, thêm tính năng) thì rất khó vì hệ thống cũ không được thiết kế để "lớn lên".
## 2. Vì sao hệ thống cũ không đáp ứng được?
Vì nó thiếu những thứ mà một hệ thống hiện đại cần có:
Không có cách nào tự động tìm tài xế gần khách → phải làm thủ công.
Không có cơ chế cập nhật trạng thái chuyến đi theo thời gian thực → khách không biết tài xế đang ở đâu.
Không có chỗ quản lý thanh toán tập trung → tiền nong rời rạc.
Kiến trúc hệ thống cũ không tách rời từng phần → nếu một chỗ lỗi (VD thanh toán) có thể ảnh hưởng tới cả hệ thống, và không thể nâng cấp từng phần riêng lẻ.
## 3. Mục tiêu kinh doanh của công ty là gì?
Xây một nền tảng CAB mới phục vụ được số lượng lớn khách hàng và tài xế.
Có thể phát triển thêm tính năng trong tương lai mà không phải làm lại từ đầu.
Tự động hóa việc tìm và phân công tài xế thay vì làm thủ công.
Giúp khách hàng theo dõi được chuyến đi từ lúc đặt xe tới lúc hoàn thành.
Quản lý thanh toán tập trung, tích hợp với bên thanh toán ngoài nhưng không lưu thông tin thẻ nhạy cảm trong hệ thống.
Hệ thống phải chạy ổn định kể cả lúc đông khách, và một lỗi nhỏ (VD lỗi thanh toán) không được làm sập cả hệ thống.
Có báo cáo cho ban lãnh đạo: số chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy, hiệu quả tài xế.
Đảm bảo bảo mật: xác thực người dùng, phân quyền nhân viên, bảo vệ dữ liệu cá nhân/vị trí/giao dịch, lưu vết thao tác quan trọng.
## 4. Ai sẽ dùng hệ thống này?
Ai	Làm gì
Khách hàng	Đăng ký, đăng nhập, đặt xe (chọn điểm đón/đến, loại xe), theo dõi chuyến, xem lịch sử, thanh toán, đánh giá tài xế
Tài xế	Đăng ký/được tạo tài khoản, cập nhật hồ sơ + xe, bật trạng thái sẵn sàng nhận chuyến, nhận/từ chối chuyến, cập nhật tiến trình chuyến (đến điểm đón, đón khách, đang chạy, hoàn thành)
Nhân viên vận hành	Quản lý khách hàng, tài xế, xe, chuyến đi; xử lý sự cố; xem báo cáo; một số việc nhạy cảm cần phân quyền riêng
Ngoài ra còn có nhà cung cấp thanh toán bên ngoài – không phải người dùng, nhưng hệ thống phải kết nối với họ.
## 5. Hệ thống mới hơn hệ thống cũ ở điểm nào?
Việc	Trước đây	Sau khi có hệ thống mới
Tìm tài xế	Nhân viên chọn tay	Tự động tìm theo vị trí + trạng thái, nếu tài xế không nhận thì tự tìm người khác
Theo dõi chuyến	Không rõ ràng	Khách biết đang tìm tài xế, ai nhận, bao lâu tới, đang ở bước nào
Thanh toán	Rời rạc	Tập trung, có tích hợp thanh toán điện tử, báo lỗi nếu giao dịch thất bại
Thông báo	Hạn chế	Gửi thông báo cho khách và tài xế ở từng bước, có thể mở rộng thêm kênh thông báo sau này
Mở rộng hệ thống	Khó	Từng phần có thể mở rộng riêng, không ảnh hưởng lẫn nhau
Báo cáo	Thiếu	Có báo cáo doanh thu, tỷ lệ hoàn thành/hủy, hiệu quả tài xế

# Bước 2
## xác định stakeholder liên quan đến hệ thống
| TT | Stakeholder | Vai trò |
| 1 | Ban lãnh đạo | Đưa ra định hướng xây dựng nền tảng CAB mới; kỳ vọng hệ thống phục vụ số lượng lớn khách hàng và tài xế; theo dõi các báo cáo về số chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả hoạt động của tài xế. |
| 2 | Khách hàng | Đăng ký/đăng nhập, nhập điểm đón và điểm đến, chọn loại xe, gửi yêu cầu đặt xe, theo dõi trạng thái chuyến, xem lịch sử chuyến đi, thanh toán và đánh giá tài xế. |
| 3 | Tài xế | Đăng ký hoặc được nhân viên vận hành tạo tài khoản; cập nhật hồ sơ và phương tiện; bật trạng thái sẵn sàng; nhận hoặc từ chối chuyến; cập nhật trạng thái trong quá trình thực hiện chuyến. |
| 4 | Nhân viên vận hành | Quản lý khách hàng, tài xế, phương tiện và chuyến đi; theo dõi các chuyến đang diễn ra; hỗ trợ xử lý chuyến bị lỗi và tra cứu lịch sử giao dịch. |
| 5 | Nhà cung cấp thanh toán bên ngoài | Được tích hợp với CAB System để xử lý thanh toán điện tử. CAB System không trực tiếp lưu trữ các thông tin nhạy cảm của thẻ hoặc tài khoản thanh toán. |
| 6 | Business Analyst | Thu thập, phân tích và làm rõ các yêu cầu chưa được xác định như cách tính cước, tiêu chí ưu tiên tài xế, thời gian phản hồi, chính sách hủy chuyến, xử lý mất kết nối và thời gian lưu trữ dữ liệu trước khi nhóm phát triển xây dựng giải pháp. |
## lập bảng 1 những stake holder , 2 vai trò là gì
Stakeholder	Power	Interest	Căn cứ
Ban lãnh đạo	Cao	Cao	Định hướng dự án, xác định mục tiêu kinh doanh và quan tâm trực tiếp đến kết quả hoạt động.
Business Analyst	Trung bình	Cao	Phân tích và làm rõ yêu cầu nhưng không phải người quyết định cuối cùng về mục tiêu kinh doanh.
Nhân viên vận hành	Trung bình	Cao	Trực tiếp sử dụng hệ thống để quản lý và xử lý hoạt động hàng ngày.
Khách hàng	Thấp – Trung bình	Cao	Là người sử dụng trực tiếp dịch vụ nhưng không quyết định phạm vi dự án.
Tài xế	Thấp – Trung bình	Cao	Trực tiếp sử dụng hệ thống để nhận và thực hiện chuyến.
Nhà cung cấp thanh toán bên ngoài	Trung bình	Thấp	Có ảnh hưởng đến chức năng thanh toán nhưng không tham gia sâu vào nghiệp vụ đặt xe.
## ma trận stakeholder matric : cho biết mức ảnh hưỏng của các vai trò trong hệ thống
                         MỨC QUAN TÂM (INTEREST)

                      THẤP                         CAO
              ┌───────────────────────┬──────────────────────────────┐
              │                       │                              │
   CAO        │   GIỮ HÀI LÒNG        │   QUẢN LÝ CHẶT CHẼ           │
 (High Power) │   (Keep Satisfied)    │   (Manage Closely)           │
              │                       │                              │
              │   • Chưa xác định     │   • Ban lãnh đạo             │
              │     stakeholder       │                              │
              │     phù hợp           │                              │
              │                       │                              │
MỨC ẢNH HƯỞNG ├───────────────────────┼──────────────────────────────┤
   (POWER)    │                       │                              │
              │   GIÁM SÁT TỐI THIỂU  │   CUNG CẤP THÔNG TIN ĐẦY ĐỦ  │
 THẤP /       │   (Monitor)           │   (Keep Informed)            │
 TRUNG BÌNH   │                       │                              │
              │   • Nhà cung cấp      │   • Business Analyst         │
              │     thanh toán        │   • Nhân viên vận hành       │
              │     bên ngoài         │   • Khách hàng               │
              │                       │   • Tài xế                   │
              │                       │                              │
              └───────────────────────┴──────────────────────────────┘
Ban lãnh đạo – Manage Closely: Có mức ảnh hưởng và mức quan tâm cao, vì đưa ra định hướng, mục tiêu kinh doanh và theo dõi hiệu quả của CAB System. Cần tham gia vào việc xác nhận phạm vi, mục tiêu và các quyết định quan trọng.

Business Analyst – Keep Informed: Có mức quan tâm cao và mức ảnh hưởng trung bình. BA chịu trách nhiệm thu thập, phân tích và làm rõ các yêu cầu chưa chốt, nhưng không phải người có quyền quyết định kinh doanh cuối cùng.

Nhân viên vận hành, Khách hàng, Tài xế – Keep Informed: Là những đối tượng trực tiếp sử dụng hoặc chịu ảnh hưởng bởi hệ thống. Cần thường xuyên lấy ý kiến để xác định đúng quy trình đặt xe, nhận chuyến, theo dõi chuyến và xử lý sự cố.

Nhà cung cấp thanh toán bên ngoài – Monitor: Chủ yếu liên quan đến chức năng thanh toán điện tử và tích hợp với CAB System, không tham gia trực tiếp vào các quyết định nghiệp vụ chung của hệ thống.

Bản này hợp lý hơn bản cũ vì đã chuyển Business Analyst từ nhóm Power cao xuống Power trung bình, đồng thời tách đúng 4 chiến lược: Manage Closely – Keep Satisfied – Keep Informed – Monitor.
# Bước 3 
## Business Goal (mục tiêu kinh doanh) : 
BG01 Mở rộng quy mô phục vụ	:
Xây dựng nền tảng có khả năng phục vụ số lượng lớn khách hàng và tài xế
BG02	Giảm thời gian tìm tài xế	:
Cho phép tìm tài xế tự động
BG03	Giảm thao tác thủ công trong phân công tài xế:
Tự động hóa quy trình phân công, có cơ chế tìm tài xế khác khi tài xế đầu không phản hồi/từ chối
BG04	Tăng khả năng theo dõi chuyến đi cho khách hàng:
Cập nhật trạng thái chuyến đi theo thời gian thực (đang tìm tài xế, tài xế nhận chuyến, đang di chuyển, hoàn thành)
BG05	Tập trung hóa quản lý thanh toán:
Tích hợp với nhà cung cấp thanh toán ngoài, không lưu thông tin nhạy cảm của thẻ/tài khoản trong hệ thống
BG06	Duy trì hệ thống ổn định khi tải cao:
Thiết kế các thành phần có thể mở rộng (scale) độc lập
BG07	Giảm rủi ro khi triển khai tính năng mới:
Cho phép triển khai từng phần, hạn chế ảnh hưởng đến chức năng đang hoạt động
BG08	Hỗ trợ ra quyết định cho ban lãnh đạo:
Cung cấp báo cáo: số chuyến, doanh thu, tỷ lệ hoàn thành/hủy, hiệu quả tài xế
BG09	Bảo vệ dữ liệu và kiểm soát truy cập:
Xác thực người dùng, phân quyền thao tác, lưu vết (audit trail) các thao tác quan trọng
BG10	Sẵn sàng mở rộng dịch vụ trong tương lai:
Kiến trúc linh hoạt cho phép thêm loại dịch vụ, phương thức thanh toán, kênh thông báo mới mà không xây lại hệ thống
# Bước 4 : Phạm vi Scope
## 4.1. Trong phạm vi (In-Scope)

| STT | Hạng mục | Mô tả |
| 1 | Quản lý tài khoản khách hàng | Đăng ký, đăng nhập, cập nhật thông tin cá nhân. |
| 2 | Đặt xe | Nhập điểm đón, điểm đến, chọn loại xe và gửi yêu cầu đặt xe. |
| 3 | Theo dõi chuyến đi | Theo dõi trạng thái như đang tìm tài xế, tài xế nhận chuyến, thời gian dự kiến đến, đang di chuyển và hoàn thành. |
| 4 | Lịch sử và đánh giá | Xem lịch sử chuyến đi, số tiền phải trả và đánh giá tài xế sau chuyến. |
| 5 | Quản lý tài khoản tài xế | Đăng ký hoặc được tạo tài khoản, cập nhật hồ sơ, phương tiện và trạng thái sẵn sàng. |
| 6 | Nhận và xử lý chuyến | Tài xế nhận thông báo chuyến mới, chấp nhận hoặc từ chối và cập nhật trạng thái chuyến. |
| 7 | Quản lý vị trí tài xế | Lưu vị trí tài xế để hỗ trợ tìm tài xế gần khách hàng và ước tính thời gian đến. |
| 8 | Tìm và phân công tài xế | Tự động tìm tài xế phù hợp theo vị trí, trạng thái sẵn sàng và tiếp tục tìm tài xế khác khi tài xế từ chối hoặc không phản hồi. |
| 9 | Tính cước và thanh toán | Xác định số tiền dựa trên loại dịch vụ và thông tin chuyến; hỗ trợ tiền mặt và thanh toán điện tử. |
| 10 | Tích hợp thanh toán bên ngoài | Kết nối với nhà cung cấp thanh toán và không lưu trực tiếp thông tin thẻ hoặc tài khoản thanh toán nhạy cảm. |
| 11 | Hệ thống thông báo | Thông báo cho khách hàng và tài xế khi có các sự kiện liên quan đến chuyến đi và thanh toán. |
| 12 | Giao diện quản trị vận hành | Quản lý khách hàng, tài xế, phương tiện, chuyến đi; hỗ trợ xử lý chuyến lỗi và tra cứu lịch sử giao dịch. |
| 13 | Phân quyền quản trị | Giới hạn các thao tác nhạy cảm cho những nhân viên có quyền phù hợp. |
| 14 | Báo cáo và thống kê | Báo cáo số lượng chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả hoạt động của tài xế. |
| 15 | Bảo mật và xác thực | Xác thực người dùng, kiểm soát truy cập và lưu vết các thao tác quan trọng. |
| 16 | Khả năng mở rộng hệ thống | Cho phép các thành phần mở rộng độc lập và hỗ trợ triển khai tính năng mới từng phần. |

## 4.2. Ngoài phạm vi (Out-of-Scope)

| STT | Hạng mục | Lý do loại trừ |
| 1 | Xây dựng cổng thanh toán riêng | CAB System chỉ tích hợp với nhà cung cấp thanh toán bên ngoài, không trực tiếp xử lý hạ tầng thanh toán. |
| 2 | Quản lý nhân sự và hợp đồng lao động của tài xế | Thuộc phạm vi quản lý nhân sự, không được đề cập trong yêu cầu CAB System. |
| 3 | Triển khai tất cả các kênh thông báo trong tương lai | Giai đoạn hiện tại chỉ cần hỗ trợ các kênh được thống nhất; hệ thống cần có khả năng mở rộng thêm sau này. |
| 4 | Các loại dịch vụ mới chưa được xác định | Hệ thống chỉ cần thiết kế linh hoạt để có thể bổ sung các loại dịch vụ mới trong tương lai. |
| 5 | Các phương thức thanh toán mới chưa được xác định | Chỉ triển khai các phương thức được thống nhất trong phiên bản hiện tại. |
# Bước 5 chuyển đổi các Business Requirements (BR)
## 5. Business Requirements
| Mã | Tên | Mô tả |
| BR01 | Quản lý quy trình đặt xe | Hệ thống hỗ trợ toàn bộ quy trình từ khi khách hàng tạo yêu cầu đặt xe đến khi chuyến đi hoàn thành. |
| BR02 | Tìm tài xế tự động | Hệ thống tự động tìm tài xế phù hợp dựa trên vị trí, trạng thái sẵn sàng và các tiêu chí vận hành. |
| BR03 | Tự động tìm tài xế thay thế | Khi tài xế được đề xuất từ chối hoặc không phản hồi, hệ thống tiếp tục tìm tài xế khác mà khách hàng không cần tạo lại yêu cầu. |
| BR04 | Theo dõi chuyến đi | Khách hàng có thể theo dõi trạng thái chuyến từ lúc gửi yêu cầu đến khi chuyến hoàn thành. |
| BR05 | Quản lý hoạt động tài xế | Tài xế có thể cập nhật trạng thái sẵn sàng, nhận hoặc từ chối chuyến và cập nhật trạng thái trong quá trình thực hiện chuyến. |
| BR06 | Quản lý vị trí tài xế | Hệ thống lưu và sử dụng vị trí tài xế để hỗ trợ tìm tài xế gần khách hàng và ước tính thời gian đến. |
| BR07 | Tính cước chuyến đi | Hệ thống xác định số tiền khách hàng phải trả sau khi chuyến đi hoàn thành. |
| BR08 | Hỗ trợ thanh toán | Hệ thống hỗ trợ thanh toán bằng tiền mặt và thanh toán điện tử thông qua nhà cung cấp bên ngoài. |
| BR09 | Bảo vệ dữ liệu thanh toán | Hệ thống không lưu trực tiếp thông tin nhạy cảm của thẻ hoặc tài khoản thanh toán. |
| BR10 | Thông báo chuyến đi | Hệ thống gửi thông báo cho khách hàng và tài xế về các sự kiện quan trọng liên quan đến chuyến đi và thanh toán. 
| BR11 | Quản lý vận hành | Nhân viên vận hành có thể quản lý khách hàng, tài xế, phương tiện, chuyến đi và hỗ trợ xử lý các trường hợp phát sinh. |
| BR12 | Báo cáo và thống kê | Hệ thống cung cấp báo cáo về số chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả hoạt động của tài xế. 
| BR13 | Xác thực và phân quyền | Hệ thống xác thực người dùng và kiểm soát quyền truy cập đối với các chức năng quản trị. |
| BR14 | Lưu vết hoạt động | Hệ thống lưu lại các thao tác quan trọng để phục vụ kiểm tra khi có sự cố. |
| BR15 | Đảm bảo khả năng mở rộng | Hệ thống có khả năng phục vụ số lượng lớn khách hàng và tài xế, đồng thời các thành phần có thể mở rộng độc lập khi tải tăng. |
| BR16 | Đảm bảo tính ổn định | Lỗi ở chức năng thanh toán hoặc thông báo không được làm ngừng toàn bộ hệ thống đặt xe. |
| BR17 | Hỗ trợ mở rộng trong tương lai | Hệ thống cho phép bổ sung loại dịch vụ, phương thức thanh toán và nhà cung cấp thông báo mới mà không phải xây dựng lại toàn bộ hệ thống. |
# Bước 6 Business Process – Quy trình nghiệp vụ
# Bước 7 Functional Requirement(FR) phân rã yêu cầu về chức năng
VD:  FR01: xác định vị trí khách
FR02: tìm tài xế sẵn có 
FR03: Lọc theo loại xe
FR04 : Tính khoảng cách 
## 1. Nhóm Khách hàng
Mã	Yêu cầu chức năng
FR01	Hệ thống cho phép khách hàng đăng ký tài khoản.
FR02	Hệ thống cho phép khách hàng đăng nhập và đăng xuất.
FR03	Hệ thống cho phép khách hàng cập nhật thông tin cá nhân.
FR04	Hệ thống cho phép khách hàng nhập điểm đón và điểm đến.
FR05	Hệ thống cho phép khách hàng lựa chọn loại xe hoặc loại dịch vụ.
FR06	Hệ thống cho phép khách hàng gửi yêu cầu đặt xe.
FR07	Hệ thống cho phép khách hàng theo dõi trạng thái hiện tại của chuyến như đang tìm tài xế, đã có tài xế, đang di chuyển và hoàn thành.
FR08	Hệ thống hiển thị thông tin tài xế và thời gian dự kiến tài xế đến sau khi có tài xế nhận chuyến.
FR09	Hệ thống cho phép khách hàng hủy chuyến theo chính sách hủy chuyến của doanh nghiệp.
FR10	Hệ thống cho phép khách hàng xem lịch sử chuyến đi.
FR11	Hệ thống cho phép khách hàng xem số tiền phải trả và thông tin thanh toán của từng chuyến.
FR12	Hệ thống cho phép khách hàng đánh giá tài xế sau khi chuyến đi hoàn thành.
FR13	Hệ thống cho phép khách hàng lựa chọn phương thức thanh toán bằng tiền mặt hoặc thanh toán điện tử.
FR14	Hệ thống thông báo cho khách hàng khi giao dịch thanh toán thất bại và cho phép xử lý lại theo chính sách của doanh nghiệp.
## 2. Nhóm Tài xế
Mã	Yêu cầu chức năng
FR15	Hệ thống cho phép tài xế đăng ký tài khoản hoặc được nhân viên vận hành tạo tài khoản.
FR16	Hệ thống cho phép tài xế đăng nhập và đăng xuất.
FR17	Hệ thống cho phép tài xế cập nhật hồ sơ cá nhân và thông tin phương tiện.
FR18	Hệ thống cho phép tài xế bật hoặc tắt trạng thái sẵn sàng nhận chuyến.
FR19	Hệ thống cho phép tài xế chấp nhận hoặc từ chối yêu cầu chuyến.
FR20	Hệ thống cho phép tài xế cập nhật trạng thái chuyến: đã đến điểm đón, đã đón khách, đang di chuyển và hoàn thành.
FR21	Hệ thống ghi nhận và cập nhật vị trí của tài xế trong quá trình hoạt động.
FR22	Hệ thống thông báo cho tài xế về các thay đổi liên quan đến chuyến đang thực hiện.
## 3. Nhóm Tìm và Phân công tài xế
Mã	Yêu cầu chức năng
FR23	Hệ thống xác định vị trí điểm đón của khách hàng.
FR24	Hệ thống tìm danh sách tài xế đang ở trạng thái sẵn sàng nhận chuyến.
FR25	Hệ thống lọc tài xế theo loại xe hoặc loại dịch vụ mà khách hàng lựa chọn.
FR26	Hệ thống lọc tài xế dựa trên vị trí so với điểm đón của khách hàng.
FR27	Hệ thống ưu tiên tài xế phù hợp dựa trên khoảng cách và các tiêu chí vận hành khác.
FR28	Hệ thống gửi yêu cầu chuyến đến tài xế được lựa chọn.
FR29	Hệ thống ghi nhận phản hồi chấp nhận, từ chối hoặc không phản hồi của tài xế.
FR30	Hệ thống tự động tìm tài xế khác nếu tài xế được đề xuất từ chối hoặc không phản hồi trong thời gian quy định.
FR31	Hệ thống gán tài xế cho chuyến khi tài xế chấp nhận yêu cầu.
FR32	Hệ thống thông báo cho khách hàng khi không tìm được tài xế phù hợp.
## 4. Nhóm Thanh toán và Tính cước
Mã	Yêu cầu chức năng
FR33	Hệ thống tính số tiền khách hàng phải trả dựa trên loại dịch vụ và thông tin chuyến đi.
FR34	Hệ thống ghi nhận việc thanh toán bằng tiền mặt.
FR35	Hệ thống gửi yêu cầu thanh toán điện tử đến nhà cung cấp thanh toán bên ngoài.
FR36	Hệ thống nhận kết quả giao dịch từ nhà cung cấp thanh toán.
FR37	Hệ thống ghi nhận trạng thái giao dịch thành công hoặc thất bại.
FR38	Hệ thống cho phép xử lý lại giao dịch thanh toán thất bại theo chính sách của doanh nghiệp.
## 5. Nhóm Thông báo
Mã	Yêu cầu chức năng
FR39	Hệ thống gửi thông báo cho khách hàng khi yêu cầu đặt xe được tiếp nhận.
FR40	Hệ thống gửi thông báo chuyến mới cho tài xế được lựa chọn.
FR41	Hệ thống gửi thông báo cho khách hàng khi có tài xế nhận chuyến.
FR42	Hệ thống gửi thông báo cho khách hàng khi tài xế đến điểm đón.
FR43	Hệ thống gửi thông báo khi chuyến đi hoàn thành.
FR44	Hệ thống gửi thông báo về kết quả thanh toán.
## 6. Nhóm Vận hành
Mã	Yêu cầu chức năng
FR45	Hệ thống cho phép nhân viên vận hành tìm kiếm và quản lý thông tin khách hàng.
FR46	Hệ thống cho phép nhân viên vận hành tìm kiếm và quản lý thông tin tài xế.
FR47	Hệ thống cho phép nhân viên vận hành quản lý thông tin phương tiện.
FR48	Hệ thống cho phép nhân viên vận hành xem các chuyến đang diễn ra.
FR49	Hệ thống cho phép nhân viên vận hành kiểm tra trạng thái tài xế.
FR50	Hệ thống cho phép nhân viên vận hành hỗ trợ xử lý các chuyến gặp sự cố.
FR51	Hệ thống cho phép nhân viên vận hành tra cứu lịch sử giao dịch.
## 7. Nhóm Báo cáo
Mã	Yêu cầu chức năng
FR52	Hệ thống tạo báo cáo số lượng chuyến theo khoảng thời gian.
FR53	Hệ thống tạo báo cáo doanh thu.
FR54	Hệ thống tạo báo cáo tỷ lệ chuyến hoàn thành và tỷ lệ chuyến hủy.
FR55	Hệ thống tạo báo cáo hiệu quả hoạt động của tài xế.
## 8. Nhóm Bảo mật và Xác thực
Mã	Yêu cầu chức năng
FR56	Hệ thống xác thực người dùng trước khi cho phép sử dụng các chức năng yêu cầu tài khoản.
FR57	Hệ thống kiểm soát quyền truy cập dựa trên vai trò của người dùng.
FR58	Hệ thống giới hạn các thao tác quản trị nhạy cảm cho nhân viên có quyền phù hợp.
FR59	Hệ thống ghi lại các thao tác quan trọng để phục vụ kiểm tra khi xảy ra sự cố.
# Bước 8 Business Rules & Business Exceptions( quy tắc nghiệp vụ , ngoại lệ)
## 8.1. Business Rules – Quy tắc nghiệp vụ
| Mã | Tên quy tắc | Mô tả |
|---|---|---|
| BRL01 | Xác thực người dùng | Khách hàng và tài xế phải được xác thực trước khi sử dụng các chức năng yêu cầu tài khoản. |
| BRL02 | Tài xế sẵn sàng nhận chuyến | Chỉ tài xế đang ở trạng thái sẵn sàng mới được hệ thống xem xét để phân công chuyến. |
| BRL03 | Lựa chọn tài xế phù hợp | Hệ thống lựa chọn tài xế dựa trên vị trí, trạng thái sẵn sàng và các tiêu chí vận hành khác. |
| BRL04 | Gán tài xế cho chuyến | Khi tài xế chấp nhận yêu cầu, hệ thống gán tài xế đó cho chuyến đi. |
| BRL05 | Tìm tài xế thay thế | Nếu tài xế từ chối hoặc không phản hồi, hệ thống tiếp tục tìm tài xế khác mà khách hàng không cần tạo lại yêu cầu. |
| BRL06 | Không tìm được tài xế | Nếu không tìm được tài xế phù hợp, hệ thống phải thông báo cho khách hàng. |
| BRL07 | Cập nhật trạng thái chuyến | Tài xế cập nhật trạng thái chuyến gồm: đã đến điểm đón, đã đón khách, đang di chuyển và hoàn thành. |
| BRL08 | Tính cước chuyến đi | Sau khi chuyến hoàn thành, hệ thống xác định số tiền khách hàng phải trả dựa trên loại dịch vụ và thông tin chuyến đi. |
| BRL09 | Phương thức thanh toán | Khách hàng có thể thanh toán bằng tiền mặt hoặc thanh toán điện tử. |
| BRL10 | Thanh toán điện tử | Thanh toán điện tử được xử lý thông qua nhà cung cấp thanh toán bên ngoài. |
| BRL11 | Bảo vệ dữ liệu thanh toán | CAB System không lưu trực tiếp thông tin nhạy cảm của thẻ hoặc tài khoản thanh toán. |
| BRL12 | Đánh giá tài xế | Khách hàng chỉ được đánh giá tài xế sau khi chuyến đi hoàn thành. |
| BRL13 | Phân quyền quản trị | Các thao tác quản trị nhạy cảm chỉ được thực hiện bởi nhân viên có quyền phù hợp. |
| BRL14 | Lưu vết hoạt động | Hệ thống phải lưu lại các thao tác quan trọng để phục vụ kiểm tra khi xảy ra sự cố. |
| BRL15 | Cô lập lỗi | Lỗi ở chức năng thanh toán hoặc thông báo không được làm toàn bộ hệ thống đặt xe ngừng hoạt động. |

## 8.2. Business Exceptions – Ngoại lệ nghiệp vụ

Business Exceptions là các tình huống bất thường có thể xảy ra trong quá trình thực hiện nghiệp vụ và cần được hệ thống xử lý.
| Mã | Ngoại lệ | Điều kiện xảy ra | Cách xử lý |
|---|---|---|---|
| BE01 | Thông tin đặt xe không hợp lệ | Điểm đón, điểm đến hoặc thông tin đặt xe không hợp lệ | Hệ thống thông báo lỗi và yêu cầu khách hàng kiểm tra hoặc nhập lại thông tin. |
| BE02 | Không tìm được tài xế | Không có tài xế phù hợp với yêu cầu chuyến | Hệ thống thông báo cho khách hàng rằng không tìm được tài xế phù hợp. |
| BE03 | Tài xế từ chối chuyến | Tài xế được đề xuất từ chối yêu cầu chuyến | Hệ thống tiếp tục tìm tài xế khác. |
| BE04 | Tài xế không phản hồi | Tài xế không phản hồi trong thời gian quy định | Hệ thống chuyển sang tìm tài xế khác. Thời gian cụ thể cần được xác nhận. |
| BE05 | Thanh toán điện tử thất bại | Nhà cung cấp thanh toán trả về kết quả thất bại | Hệ thống thông báo cho khách hàng và cho phép xử lý lại theo chính sách doanh nghiệp. |
| BE06 | Nhà cung cấp thanh toán gặp lỗi | Hệ thống không thể kết nối hoặc nhận kết quả từ nhà cung cấp thanh toán | Lỗi thanh toán không được làm ngừng toàn bộ hệ thống đặt xe. |
| BE07 | Dịch vụ thông báo gặp lỗi | Hệ thống không thể gửi thông báo | Lỗi thông báo không được làm ngừng toàn bộ quy trình đặt xe. |
| BE08 | Khách hàng hủy chuyến | Khách hàng yêu cầu hủy chuyến | Hệ thống xử lý theo chính sách hủy chuyến của doanh nghiệp. |
| BE09 | Tài xế không thể tiếp tục chuyến | Tài xế gặp sự cố sau khi đã nhận chuyến | Nhân viên vận hành hỗ trợ xử lý theo chính sách của doanh nghiệp. |
| BE10 | Mất kết nối mạng | Khách hàng hoặc tài xế mất kết nối khi đang sử dụng hệ thống | Cách lưu và đồng bộ lại trạng thái cần được doanh nghiệp làm rõ. |
| BE11 | Không nhận được vị trí tài xế | Hệ thống không nhận được dữ liệu vị trí hợp lệ của tài xế | Cách xử lý cụ thể cần được doanh nghiệp xác nhận. |
| BE12 | Chuyến đi gặp sự cố | Chuyến có trạng thái bất thường hoặc xảy ra lỗi | Nhân viên vận hành kiểm tra và hỗ trợ xử lý. |


## 8.3. Những ngoại lệ cần xác nhận thêm với khách hàng

Các trường hợp sau chưa có đủ quy tắc để xác định cách xử lý cuối cùng:
- Khách hàng được hủy chuyến ở những trạng thái nào?
- Tài xế có được phép hủy chuyến sau khi đã nhận chuyến không?
- Trường hợp nào phải trả phí hủy chuyến?
- Tài xế có bao nhiêu thời gian để phản hồi yêu cầu chuyến?
- Khi tài xế mất kết nối mạng trong lúc thực hiện chuyến thì xử lý trạng thái chuyến như thế nào?
- Nếu thanh toán điện tử thất bại thì khách hàng được thử lại bao nhiêu lần?
- Có cho phép chuyển từ thanh toán điện tử sang tiền mặt khi thanh toán thất bại không?
- Khi không nhận được vị trí tài xế thì hệ thống có tiếp tục xem tài xế đó là tài xế phù hợp hay không?

# Bước 9 mô hình hoá dữ liệu ERD (xác định các thực thể) 
1. Customer (customer_id, full_name, email, phone, password, status)
2. Driver (driver_id, full_name, email, phone, password, availability_status)
3. Vehicle (vehicle_id, driver_id, service_type_id, license_plate, vehicle_name, status)
4. ServiceType (service_type_id, service_name, description, status)
5. Trip (trip_id, customer_id, driver_id, service_type_id, pickup_location, destination, trip_status, estimated_arrival_time, fare_amount, created_at, completed_at)
6. DriverRequest (request_id, trip_id, driver_id, request_status, request_time, response_time)
7. DriverLocation (location_id, driver_id, latitude, longitude, recorded_at)
8. Payment (payment_id, trip_id, amount, payment_method, payment_status, external_transaction_id, paid_at)
9. Rating (rating_id, trip_id, customer_id, driver_id, score, comment, created_at)
10. Notification (notification_id, trip_id, receiver_id, receiver_type, notification_type, content, status, created_at)
11. Staff (staff_id, full_name, email, password, role_id, status)
12. Role (role_id, role_name, description)
13. AuditLog (log_id, actor_id, actor_type, action, created_at)
    
# Bước 10 None productional prequiment (Phi chức năng)
| Mã | Nhóm yêu cầu | Yêu cầu phi chức năng |
|---|---|---|
| NFR01 | Scalability | Hệ thống phải có khả năng phục vụ số lượng lớn khách hàng và tài xế khi nhu cầu tăng. |
| NFR02 | Scalability | Các thành phần của hệ thống phải có khả năng mở rộng độc lập khi tải tăng. |
| NFR03 | Availability / Stability | Hệ thống phải hoạt động ổn định trong các thời điểm có nhu cầu đặt xe cao. |
| NFR04 | Fault Tolerance | Lỗi xảy ra ở chức năng thanh toán không được làm ngừng toàn bộ hệ thống đặt xe. |
| NFR05 | Fault Tolerance | Lỗi xảy ra ở chức năng thông báo không được làm ngừng toàn bộ hệ thống đặt xe. |
| NFR06 | Deployability | Hệ thống phải hỗ trợ triển khai các chức năng mới từng phần và hạn chế ảnh hưởng đến các chức năng đang hoạt động. |
| NFR07 | Security | Khách hàng và tài xế phải được xác thực trước khi sử dụng các chức năng yêu cầu tài khoản. |
| NFR08 | Authorization | Các thao tác quản trị phải được kiểm soát quyền truy cập và chỉ người có quyền phù hợp mới được thực hiện các thao tác nhạy cảm. |
| NFR09 | Data Security | Hệ thống phải bảo vệ thông tin cá nhân của khách hàng và tài xế. |
| NFR10 | Data Security | Hệ thống phải bảo vệ thông tin phương tiện và dữ liệu vị trí của tài xế. |
| NFR11 | Data Security | Hệ thống phải bảo vệ dữ liệu giao dịch và không lưu trực tiếp thông tin nhạy cảm của thẻ hoặc tài khoản thanh toán. |
| NFR12 | Auditability | Hệ thống phải lưu vết các thao tác quan trọng để phục vụ kiểm tra khi xảy ra sự cố. |
| NFR13 | Extensibility | Hệ thống phải cho phép bổ sung các loại dịch vụ mới trong tương lai mà không cần xây dựng lại toàn bộ ứng dụng. |
| NFR14 | Extensibility | Hệ thống phải cho phép bổ sung phương thức hoặc nhà cung cấp thanh toán mới trong tương lai. |
| NFR15 | Extensibility | Hệ thống phải cho phép bổ sung các nhà cung cấp hoặc kênh thông báo mới mà không phải thay đổi toàn bộ hệ thống. |
| NFR16 | Maintainability | Hệ thống phải có kiến trúc linh hoạt để có thể thay đổi một số thành phần kỹ thuật mà hạn chế ảnh hưởng đến các thành phần khác. |
# Bước 11 Vẽ Usecase (UC)
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/0d0f2418-3ee1-4209-bfca-7f003673c617" />
# Bước 12 Đặc tả Usecase
## UC01. Đăng ký tài khoản khách hàng

| Thuộc tính     | Nội dung                                                      |
| -------------- | ------------------------------------------------------------- |
| Mã Use Case    | UC01                                                          |
| Tên Use Case   | Đăng ký tài khoản khách hàng                                  |
| Actor chính    | Khách hàng                                                    |
| Mô tả          | Cho phép khách hàng tạo tài khoản để sử dụng CAB System.      |
| Tiền điều kiện | Khách hàng chưa có tài khoản.                                 |
| Hậu điều kiện  | Tài khoản khách hàng được tạo thành công và lưu vào hệ thống. |

### Luồng chính

1. Khách hàng chọn chức năng đăng ký.
2. Hệ thống hiển thị thông tin cần nhập.
3. Khách hàng nhập thông tin tài khoản và thông tin cá nhân.
4. Khách hàng gửi yêu cầu đăng ký.
5. Hệ thống kiểm tra dữ liệu.
6. Hệ thống tạo tài khoản.
7. Hệ thống thông báo đăng ký thành công.

### Luồng ngoại lệ

* Thông tin không hợp lệ → hệ thống thông báo lỗi và yêu cầu nhập lại.
* Thông tin tài khoản đã tồn tại → hệ thống thông báo cho khách hàng.

---

## UC02. Đăng nhập

| Thuộc tính     | Nội dung                                                                           |
| -------------- | ---------------------------------------------------------------------------------- |
| Mã Use Case    | UC02                                                                               |
| Tên Use Case   | Đăng nhập                                                                          |
| Actor chính    | Khách hàng, Tài xế, Nhân viên vận hành                                             |
| Mô tả          | Cho phép người dùng xác thực tài khoản để sử dụng các chức năng yêu cầu đăng nhập. |
| Tiền điều kiện | Người dùng đã có tài khoản hợp lệ.                                                 |
| Hậu điều kiện  | Người dùng đăng nhập thành công và được cấp quyền theo vai trò.                    |

### Luồng chính

1. Người dùng chọn đăng nhập.
2. Hệ thống yêu cầu thông tin đăng nhập.
3. Người dùng nhập thông tin.
4. Hệ thống xác thực tài khoản.
5. Hệ thống xác định vai trò người dùng.
6. Hệ thống cho phép truy cập các chức năng phù hợp.

### Luồng ngoại lệ

* Thông tin đăng nhập không đúng → hệ thống thông báo đăng nhập thất bại.
* Tài khoản không hợp lệ hoặc không hoạt động → hệ thống từ chối truy cập.

---

## UC03. Đặt xe

| Thuộc tính     | Nội dung                                                |
| -------------- | ------------------------------------------------------- |
| Mã Use Case    | UC03                                                    |
| Tên Use Case   | Đặt xe                                                  |
| Actor chính    | Khách hàng                                              |
| Actor phụ      | Hệ thống CAB                                            |
| Mô tả          | Cho phép khách hàng tạo yêu cầu chuyến đi.              |
| Tiền điều kiện | Khách hàng đã đăng nhập.                                |
| Hậu điều kiện  | Yêu cầu đặt xe được tạo và hệ thống bắt đầu tìm tài xế. |

### Luồng chính

1. Khách hàng chọn chức năng đặt xe.
2. Khách hàng nhập điểm đón.
3. Khách hàng nhập điểm đến.
4. Khách hàng chọn loại xe hoặc loại dịch vụ.
5. Khách hàng gửi yêu cầu đặt xe.
6. Hệ thống kiểm tra thông tin.
7. Hệ thống tạo yêu cầu chuyến.
8. Hệ thống cập nhật trạng thái chuyến thành đang tìm tài xế.
9. Hệ thống thông báo đã tiếp nhận yêu cầu.
10. Hệ thống thực hiện UC04 – Tìm và phân công tài xế.

### Luồng ngoại lệ

* Điểm đón hoặc điểm đến không hợp lệ → hệ thống yêu cầu khách hàng kiểm tra lại.
* Thông tin yêu cầu không đầy đủ → hệ thống không tạo chuyến.

---

## UC04. Tìm và phân công tài xế

| Thuộc tính     | Nội dung                                                                             |
| -------------- | ------------------------------------------------------------------------------------ |
| Mã Use Case    | UC04                                                                                 |
| Tên Use Case   | Tìm và phân công tài xế                                                              |
| Actor chính    | Hệ thống CAB                                                                         |
| Actor phụ      | Tài xế                                                                               |
| Mô tả          | Hệ thống tìm tài xế phù hợp và gửi yêu cầu chuyến.                                   |
| Tiền điều kiện | Khách hàng đã tạo yêu cầu đặt xe hợp lệ.                                             |
| Hậu điều kiện  | Một tài xế được gán cho chuyến hoặc khách hàng được thông báo không tìm được tài xế. |

### Luồng chính

1. Hệ thống xác định điểm đón của khách hàng.
2. Hệ thống tìm các tài xế đang ở trạng thái sẵn sàng.
3. Hệ thống lọc tài xế theo loại xe hoặc loại dịch vụ.
4. Hệ thống xem xét vị trí của các tài xế.
5. Hệ thống ưu tiên tài xế phù hợp.
6. Hệ thống gửi yêu cầu chuyến cho tài xế được lựa chọn.
7. Tài xế nhận thông tin chuyến.
8. Tài xế chấp nhận chuyến.
9. Hệ thống ghi nhận phản hồi.
10. Hệ thống gán tài xế vào chuyến.
11. Hệ thống thông báo thông tin tài xế và thời gian dự kiến đến cho khách hàng.

### Luồng thay thế

#### A1. Tài xế từ chối

1. Tài xế từ chối yêu cầu.
2. Hệ thống ghi nhận kết quả từ chối.
3. Hệ thống tiếp tục tìm tài xế khác.
4. Quy trình quay lại bước 5 của luồng chính.

#### A2. Tài xế không phản hồi

1. Tài xế không phản hồi trong thời gian quy định.
2. Hệ thống ghi nhận trạng thái không phản hồi.
3. Hệ thống tiếp tục tìm tài xế khác.

Thời gian phản hồi cụ thể: TBD.

### Luồng ngoại lệ

* Không còn tài xế phù hợp → hệ thống thông báo cho khách hàng không tìm được tài xế.

---

## UC05. Chấp nhận hoặc từ chối chuyến

| Thuộc tính     | Nội dung                                                          |
| -------------- | ----------------------------------------------------------------- |
| Mã Use Case    | UC05                                                              |
| Tên Use Case   | Chấp nhận hoặc từ chối chuyến                                     |
| Actor chính    | Tài xế                                                            |
| Mô tả          | Cho phép tài xế phản hồi yêu cầu chuyến được hệ thống gửi đến.    |
| Tiền điều kiện | Tài xế đang ở trạng thái sẵn sàng và nhận được yêu cầu chuyến.    |
| Hậu điều kiện  | Hệ thống ghi nhận kết quả chấp nhận, từ chối hoặc không phản hồi. |

### Luồng chính

1. Hệ thống gửi yêu cầu chuyến cho tài xế.
2. Tài xế xem thông tin chuyến.
3. Tài xế chọn chấp nhận.
4. Hệ thống ghi nhận phản hồi.
5. Hệ thống gán tài xế cho chuyến.

### Luồng thay thế

* Tài xế chọn từ chối → hệ thống ghi nhận và tìm tài xế khác.
* Tài xế không phản hồi → sau thời gian quy định hệ thống tìm tài xế khác.

---

## UC06. Thực hiện chuyến đi

| Thuộc tính     | Nội dung                                                                        |
| -------------- | ------------------------------------------------------------------------------- |
| Mã Use Case    | UC06                                                                            |
| Tên Use Case   | Thực hiện chuyến đi                                                             |
| Actor chính    | Tài xế                                                                          |
| Actor phụ      | Khách hàng                                                                      |
| Mô tả          | Quản lý các trạng thái của chuyến từ khi tài xế nhận chuyến đến khi hoàn thành. |
| Tiền điều kiện | Tài xế đã chấp nhận và được gán cho chuyến.                                     |
| Hậu điều kiện  | Chuyến được cập nhật thành hoàn thành.                                          |

### Luồng chính

1. Tài xế di chuyển đến điểm đón.
2. Tài xế cập nhật trạng thái đã đến điểm đón.
3. Hệ thống thông báo cho khách hàng.
4. Tài xế đón khách.
5. Tài xế cập nhật trạng thái đã đón khách.
6. Tài xế cập nhật trạng thái đang di chuyển.
7. Hệ thống cho phép khách hàng theo dõi trạng thái chuyến.
8. Tài xế kết thúc chuyến.
9. Tài xế cập nhật trạng thái hoàn thành.
10. Hệ thống ghi nhận chuyến hoàn thành.
11. Hệ thống thực hiện tính cước.

### Luồng ngoại lệ

* Tài xế hoặc khách hàng mất kết nối → xử lý theo chính sách mất kết nối của doanh nghiệp. Chính sách cụ thể: TBD.
* Chuyến gặp sự cố → nhân viên vận hành hỗ trợ xử lý.

---

## UC07. Thanh toán chuyến đi

| Thuộc tính     | Nội dung                                                          |
| -------------- | ----------------------------------------------------------------- |
| Mã Use Case    | UC07                                                              |
| Tên Use Case   | Thanh toán chuyến đi                                              |
| Actor chính    | Khách hàng                                                        |
| Actor phụ      | Nhà cung cấp thanh toán bên ngoài                                 |
| Mô tả          | Cho phép khách hàng thanh toán số tiền của chuyến đi.             |
| Tiền điều kiện | Chuyến đi đã hoàn thành và hệ thống đã xác định số tiền phải trả. |
| Hậu điều kiện  | Kết quả thanh toán được ghi nhận.                                 |

### Luồng chính – Thanh toán điện tử

1. Hệ thống hiển thị số tiền phải trả.
2. Khách hàng chọn thanh toán điện tử.
3. Hệ thống gửi yêu cầu thanh toán đến nhà cung cấp thanh toán.
4. Nhà cung cấp xử lý giao dịch.
5. Nhà cung cấp trả kết quả giao dịch.
6. Hệ thống ghi nhận kết quả thành công.
7. Hệ thống thông báo thanh toán thành công cho khách hàng.

### Luồng thay thế – Thanh toán tiền mặt

1. Khách hàng chọn tiền mặt.
2. Chuyến được thanh toán bằng tiền mặt.
3. Hệ thống ghi nhận phương thức thanh toán tiền mặt.

### Luồng ngoại lệ

#### E1. Thanh toán điện tử thất bại

1. Nhà cung cấp trả về kết quả thất bại.
2. Hệ thống ghi nhận trạng thái thất bại.
3. Hệ thống thông báo cho khách hàng.
4. Hệ thống cho phép xử lý lại theo chính sách doanh nghiệp.

Chính sách retry thanh toán: TBD.

---

## UC08. Đánh giá tài xế

| Thuộc tính     | Nội dung                                                          |
| -------------- | ----------------------------------------------------------------- |
| Mã Use Case    | UC08                                                              |
| Tên Use Case   | Đánh giá tài xế                                                   |
| Actor chính    | Khách hàng                                                        |
| Mô tả          | Cho phép khách hàng đánh giá tài xế sau khi chuyến đi hoàn thành. |
| Tiền điều kiện | Chuyến đi đã hoàn thành.                                          |
| Hậu điều kiện  | Đánh giá được lưu trong hệ thống.                                 |

### Luồng chính

1. Khách hàng mở chuyến đã hoàn thành.
2. Khách hàng chọn chức năng đánh giá.
3. Khách hàng nhập điểm đánh giá và nhận xét.
4. Khách hàng gửi đánh giá.
5. Hệ thống lưu đánh giá.
6. Hệ thống thông báo đánh giá thành công.

### Luồng ngoại lệ

* Chuyến chưa hoàn thành → hệ thống không cho phép đánh giá.
* Dữ liệu đánh giá không hợp lệ → hệ thống yêu cầu nhập lại.

---

## UC09. Quản lý vận hành

| Thuộc tính     | Nội dung                                                         |
| -------------- | ---------------------------------------------------------------- |
| Mã Use Case    | UC09                                                             |
| Tên Use Case   | Quản lý vận hành                                                 |
| Actor chính    | Nhân viên vận hành                                               |
| Mô tả          | Cho phép nhân viên quản lý và theo dõi hoạt động của CAB System. |
| Tiền điều kiện | Nhân viên đã đăng nhập và có quyền phù hợp.                      |
| Hậu điều kiện  | Thông tin quản lý hoặc xử lý được cập nhật vào hệ thống.         |

### Luồng chính

1. Nhân viên đăng nhập hệ thống quản trị.
2. Nhân viên lựa chọn chức năng cần thực hiện.
3. Nhân viên có thể:

   * Quản lý khách hàng.
   * Quản lý tài xế.
   * Quản lý phương tiện.
   * Xem chuyến đang diễn ra.
   * Kiểm tra trạng thái tài xế.
   * Hỗ trợ xử lý chuyến gặp sự cố.
   * Tra cứu lịch sử giao dịch.
4. Hệ thống kiểm tra quyền của nhân viên.
5. Hệ thống thực hiện chức năng tương ứng.
6. Hệ thống lưu vết các thao tác quan trọng.

### Luồng ngoại lệ

* Nhân viên không có quyền phù hợp → hệ thống từ chối thao tác.
* Không tìm thấy dữ liệu → hệ thống thông báo kết quả phù hợp.

---

## UC10. Xem báo cáo và thống kê

| Thuộc tính     | Nội dung                                                  |
| -------------- | --------------------------------------------------------- |
| Mã Use Case    | UC10                                                      |
| Tên Use Case   | Xem báo cáo và thống kê                                   |
| Actor chính    | Ban lãnh đạo / Người có quyền phù hợp                     |
| Mô tả          | Cung cấp thông tin phục vụ theo dõi hoạt động kinh doanh. |
| Tiền điều kiện | Người dùng đã đăng nhập và có quyền xem báo cáo.          |
| Hậu điều kiện  | Báo cáo được hiển thị cho người dùng.                     |

### Luồng chính

1. Người dùng chọn chức năng báo cáo.
2. Người dùng chọn loại báo cáo.
3. Hệ thống tổng hợp dữ liệu.
4. Hệ thống hiển thị báo cáo.

Các báo cáo gồm:

* Số lượng chuyến.
* Doanh thu.
* Tỷ lệ chuyến hoàn thành.
* Tỷ lệ chuyến hủy.
* Hiệu quả hoạt động của tài xế.
  
# Bước 13. Acceptance Criteria (AC) – Tiêu chí chấp nhận

Acceptance Criteria là các tiêu chí dùng để xác định chức năng có đáp ứng yêu cầu và đủ điều kiện nghiệm thu hay không.

| Mã | Chức năng | Tiêu chí chấp nhận |
|---|---|---|
| AC01 | Đăng ký tài khoản khách hàng | Khách hàng nhập đầy đủ thông tin hợp lệ thì hệ thống tạo tài khoản thành công và thông báo kết quả. |
| AC02 | Đăng nhập | Người dùng nhập đúng thông tin tài khoản thì đăng nhập thành công; nếu thông tin không đúng thì hệ thống thông báo lỗi. |
| AC03 | Cập nhật thông tin cá nhân | Khách hàng hoặc tài xế có thể chỉnh sửa thông tin hợp lệ và hệ thống lưu thông tin mới thành công. |
| AC04 | Tạo yêu cầu đặt xe | Khách hàng nhập điểm đón, điểm đến, chọn loại xe và gửi yêu cầu thì hệ thống tạo chuyến và ghi nhận trạng thái đang tìm tài xế. |
| AC05 | Tìm tài xế sẵn sàng | Hệ thống chỉ đưa vào danh sách tìm kiếm các tài xế đang ở trạng thái sẵn sàng nhận chuyến. |
| AC06 | Lọc tài xế phù hợp | Hệ thống lọc tài xế dựa trên loại xe/dịch vụ, vị trí và các tiêu chí vận hành đã được xác định. |
| AC07 | Gửi yêu cầu chuyến | Tài xế được lựa chọn nhận được thông báo về yêu cầu chuyến mới. |
| AC08 | Tài xế chấp nhận chuyến | Khi tài xế chấp nhận, hệ thống ghi nhận phản hồi, gán tài xế cho chuyến và thông báo cho khách hàng. |
| AC09 | Tài xế từ chối chuyến | Khi tài xế từ chối, hệ thống không hủy yêu cầu của khách hàng mà tiếp tục tìm tài xế khác. |
| AC10 | Tài xế không phản hồi | Nếu tài xế không phản hồi trong thời gian quy định, hệ thống tiếp tục tìm tài xế khác. Thời gian cụ thể là TBD. |
| AC11 | Không tìm được tài xế | Khi không còn tài xế phù hợp, hệ thống thông báo rõ cho khách hàng rằng không tìm được tài xế. |
| AC12 | Hiển thị thông tin tài xế | Sau khi tài xế nhận chuyến, khách hàng xem được thông tin tài xế và thời gian dự kiến tài xế đến. |
| AC13 | Cập nhật trạng thái chuyến | Tài xế có thể cập nhật lần lượt các trạng thái: đã đến điểm đón, đã đón khách, đang di chuyển và hoàn thành. |
| AC14 | Theo dõi chuyến đi | Khách hàng có thể xem trạng thái hiện tại của chuyến trong quá trình thực hiện. |
| AC15 | Cập nhật vị trí tài xế | Hệ thống ghi nhận vị trí tài xế để hỗ trợ việc tìm tài xế và ước tính thời gian đến. |
| AC16 | Hoàn thành chuyến | Khi tài xế xác nhận hoàn thành, hệ thống cập nhật trạng thái chuyến thành hoàn thành và thực hiện tính cước. |
| AC17 | Tính cước | Sau khi chuyến hoàn thành, hệ thống xác định được số tiền khách hàng phải trả dựa trên loại dịch vụ và thông tin chuyến đi. Công thức cụ thể là TBD. |
| AC18 | Thanh toán tiền mặt | Khi khách hàng chọn tiền mặt, hệ thống ghi nhận phương thức và kết quả thanh toán của chuyến. |
| AC19 | Thanh toán điện tử | Khi khách hàng chọn thanh toán điện tử, hệ thống gửi giao dịch đến nhà cung cấp thanh toán bên ngoài và nhận kết quả trả về. |
| AC20 | Thanh toán thành công | Khi nhà cung cấp thanh toán trả kết quả thành công, hệ thống ghi nhận giao dịch thành công và thông báo cho khách hàng. |
| AC21 | Thanh toán thất bại | Khi giao dịch thất bại, hệ thống ghi nhận trạng thái thất bại, thông báo cho khách hàng và cho phép xử lý lại theo chính sách doanh nghiệp. |
| AC22 | Lịch sử chuyến đi | Khách hàng có thể xem lại danh sách các chuyến đã thực hiện và thông tin của từng chuyến. |
| AC23 | Đánh giá tài xế | Chỉ sau khi chuyến hoàn thành, khách hàng mới có thể gửi đánh giá tài xế và hệ thống lưu đánh giá thành công. |
| AC24 | Thông báo đặt xe | Khách hàng nhận được thông báo khi yêu cầu đặt xe được tiếp nhận. |
| AC25 | Thông báo tài xế nhận chuyến | Khách hàng nhận được thông báo khi có tài xế chấp nhận chuyến. |
| AC26 | Thông báo tài xế đến | Khách hàng nhận được thông báo khi tài xế cập nhật trạng thái đã đến điểm đón. |
| AC27 | Thông báo hoàn thành chuyến | Hệ thống gửi thông báo khi chuyến đi hoàn thành. |
| AC28 | Quản lý vận hành | Nhân viên vận hành có thể xem và quản lý khách hàng, tài xế, phương tiện, chuyến đi theo quyền được cấp. |
| AC29 | Xử lý chuyến gặp sự cố | Nhân viên vận hành có thể xem thông tin chuyến gặp lỗi và thực hiện các thao tác hỗ trợ được phân quyền. |
| AC30 | Tra cứu giao dịch | Nhân viên vận hành có thể tìm kiếm và xem lịch sử giao dịch. |
| AC31 | Phân quyền | Người dùng không có quyền phù hợp không thể thực hiện các thao tác quản trị nhạy cảm. |
| AC32 | Báo cáo số chuyến | Hệ thống có thể tổng hợp và hiển thị số lượng chuyến theo dữ liệu được lựa chọn. |
| AC33 | Báo cáo doanh thu | Hệ thống có thể tổng hợp và hiển thị thông tin doanh thu. |
| AC34 | Báo cáo tỷ lệ chuyến | Hệ thống có thể cung cấp tỷ lệ chuyến hoàn thành và tỷ lệ chuyến hủy. |
| AC35 | Báo cáo hiệu quả tài xế | Hệ thống có thể cung cấp dữ liệu phục vụ đánh giá hiệu quả hoạt động của tài xế. |
| AC36 | Lưu vết thao tác | Các thao tác quan trọng được hệ thống ghi lại để phục vụ kiểm tra khi có sự cố. |
| AC37 | Lỗi thanh toán | Khi chức năng thanh toán gặp lỗi, các chức năng đặt xe chính vẫn có thể tiếp tục hoạt động. |
| AC38 | Lỗi thông báo | Khi chức năng thông báo gặp lỗi, hệ thống đặt xe không bị ngừng toàn bộ. |

# Bước 14. Requirement Traceability Matrix (RTM) – Ma trận truy xuất nguồn gốc yêu cầu

Ma trận RTM giúp truy xuất mối liên hệ giữa mục tiêu kinh doanh, yêu cầu nghiệp vụ, yêu cầu chức năng/phi chức năng, Use Case và tiêu chí chấp nhận. RTM hỗ trợ quá trình thiết kế, phát triển và xây dựng các bộ kiểm thử.

## 14.1. Ma trận RTM

| Business Goal | Business Requirement | FR / NFR liên quan | Use Case | Acceptance Criteria |
|---|---|---|---|---|
| BG01 – Mở rộng quy mô phục vụ | BR15 – Đảm bảo khả năng mở rộng | NFR01, NFR02 | Không áp dụng trực tiếp | TBD – Cần xác định số người dùng và tải tối đa |
| BG02 – Giảm thời gian tìm tài xế | BR02 – Tìm tài xế tự động | FR23, FR24, FR25, FR26, FR27, FR28 | UC04 – Tìm và phân công tài xế | AC05, AC06, AC07 |
| BG03 – Giảm thao tác thủ công trong phân công tài xế | BR03 – Tự động tìm tài xế thay thế | FR29, FR30, FR31, FR32 | UC04, UC05 | AC08, AC09, AC10, AC11 |
| BG04 – Tăng khả năng theo dõi chuyến đi | BR04 – Theo dõi chuyến đi | FR07, FR08, FR20, FR21 | UC06 – Thực hiện chuyến đi | AC12, AC13, AC14, AC15, AC16 |
| BG03 – Giảm thao tác thủ công | BR05 – Quản lý hoạt động tài xế | FR15, FR16, FR17, FR18, FR19, FR20, FR22 | UC05, UC06 | AC03, AC07, AC08, AC13 |
| BG02 – Giảm thời gian tìm tài xế | BR06 – Quản lý vị trí tài xế | FR21, FR23, FR26, FR27 | UC04, UC06 | AC06, AC15 |
| BG05 – Tập trung hóa quản lý thanh toán | BR07 – Tính cước chuyến đi | FR33 | UC07 – Thanh toán chuyến đi | AC17 |
| BG05 – Tập trung hóa quản lý thanh toán | BR08 – Hỗ trợ thanh toán | FR13, FR14, FR34, FR35, FR36, FR37, FR38 | UC07 – Thanh toán chuyến đi | AC18, AC19, AC20, AC21 |
| BG05, BG09 | BR09 – Bảo vệ dữ liệu thanh toán | NFR11 | UC07 – Thanh toán chuyến đi | AC19, AC20 |
| BG04 – Tăng khả năng theo dõi chuyến đi | BR10 – Thông báo chuyến đi | FR22, FR39, FR40, FR41, FR42, FR43, FR44 | UC03, UC04, UC05, UC06, UC07 | AC24, AC25, AC26, AC27 |
| BG03 – Nâng cao hiệu quả vận hành | BR11 – Quản lý vận hành | FR45, FR46, FR47, FR48, FR49, FR50, FR51 | UC09 – Quản lý vận hành | AC28, AC29, AC30 |
| BG08 – Hỗ trợ ra quyết định | BR12 – Báo cáo và thống kê | FR52, FR53, FR54, FR55 | UC10 – Xem báo cáo và thống kê | AC32, AC33, AC34, AC35 |
| BG09 – Bảo vệ dữ liệu và kiểm soát truy cập | BR13 – Xác thực và phân quyền | FR02, FR16, FR56, FR57, FR58; NFR07, NFR08 | UC02, UC09 | AC02, AC31 |
| BG09 – Bảo vệ dữ liệu và kiểm soát truy cập | BR14 – Lưu vết hoạt động | FR59; NFR12 | UC09 – Quản lý vận hành | AC36 |
| BG06 – Duy trì hệ thống ổn định khi tải cao | BR16 – Đảm bảo tính ổn định | NFR03, NFR04, NFR05 | Không áp dụng trực tiếp | AC37, AC38 |
| BG07 – Giảm rủi ro khi triển khai tính năng mới | BR17 – Hỗ trợ mở rộng trong tương lai | NFR06, NFR16 | Không áp dụng trực tiếp | TBD – Cần tiêu chí triển khai cụ thể |
| BG10 – Sẵn sàng mở rộng dịch vụ trong tương lai | BR17 – Hỗ trợ mở rộng trong tương lai | NFR13, NFR14, NFR15, NFR16 | Không áp dụng trực tiếp | TBD – Cần tiêu chí mở rộng cụ thể |
