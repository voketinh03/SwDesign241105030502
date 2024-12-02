# Lab 4
## 1. Login:**
#### Mô tả:** Ca sử dụng này cho phép người dùng hệ thống đăng nhập bằng cách nhập tên đăng nhập và mật khẩu.
#### Thiết kế:**
  + Thành phần tham gia:
      **LoginForm (boundary):** giao diện nhập tên đăng nhập và mật khẩu.
      **User (actor):** người dùng của hệ thống.
      **AuthenticationSystem (control):** kiểm tra thông tin xác thực.
  + Luồng chính:
      B1: Người dùng nhập tên đăng nhập và mật khẩu vào **LoginForm.**
      B2: **LoginForm** gửi thông tin đến **AuthenticationSystem** để xác thực.
      B3: **AuthenticationSystem** xác thực thông tin với cơ sở dữ liệu.
      B4: Nếu thông tin hợp lệ, cho phép truy cập vào hệ thống.
#### Lý do thiết kế:**
  + Tuân thủ mô hình boundary-control-entity để đảm bảo tính độc lập giữa giao diện, xử lý nghiệp vụ và dữ liệu.
  + Giao diện **LoginForm** nằm trong gói **Security:GUI Framework** để đảm bảo tích hợp chặt chẽ với hệ thống bảo mật.
## 2. Maintain timecard - Basic Flow
#### Mô tả sự tương tác giữa các đối tượng thiết kế
Tác nhân: Nhân viên, người quản trị hệ thống

#### Đơn giản hóa sơ đồ trình tự bằng hệ thống con
1. `TimecardController`: Quản lý việc gửi và lấy dữ liệu thẻ chấm công.
2. `ProjectManagementDatabase`: Lưu trữ
3. `Timecard`: Chứa dữ liệu số giờ làm việc.

   ![Senquence Diagram](https://www.planttext.com/api/plantuml/png/Z59BJWCn3Dtd5Bu05vW5gbH6ObKgsXx0IWoAb4cYs5EQitN1aRW2QGk4WKmXIp-_Jso_7LyNB9Xa79n2BI51FqGNya1UL2o0rJQY5zZQWJGciyaiD4oWDUOKd5kYqwD3iS6tcqwQ7uYgBd1p-qEyWuT8_gkefcYh_v4aMTeJz0VBOlrp9QEhsIymAoZlj-YEANLmPpawp0qbSaomefSgjqo4GkPVUj-9Py89RlrbW_kfZI9lr5ntxwK0zs5Ct9ZJt6Ows4LJebUFgsckR6BUuSoys9W_5EfXTB0AOf_oPnNMAMXYBaDUb36KAtq7003__mC0)
   
#### Mô tả hành vi lưu trữ
Hệ thống thẻ chấm công sẽ lưu trữ những thông tin sau cho mỗi nhân viên:
+ ID nhân viên
+ Ngày và giờ vào và ra
+ Tổng số giờ làm việc
+ Yêu cầu nghỉ phép và trạng thái
#### Tinh chỉnh mô tả luồng sự kiện
1. Một nhân viên đang chấm công vào đầu ca làm việc của mình.
2. Hệ thống ghi lại thời gian làm việc và ID nhân viên.
3. Nhân viên sẽ tan làm vào cuối ca làm việc của mình.
4. Hệ thống tính tổng số giờ làm việc và ghi lại thời gian ra về.
5. Nhân viên có thể xem thẻ chấm công của mình bất cứ lúc nào.
6. Nhân viên có thể gửi yêu cầu nghỉ phép, sau đó yêu cầu này sẽ được chuyển đến người quản trị hệ thống để phê duyệt hoặc từ chối.
#### Hợp nhất các lớp và hệ thống con
1. Hệ thống thẻ chấm công sẽ tích hợp với hệ thống quản lý nhân viên để truy cập thông tin nhân viên.
2. Hệ thống thẻ chấm công sẽ tích hợp với hệ thống quản lý thời gian nghỉ để xử lý các yêu cầu nghỉ phép.
3. Hệ thống thẻ chấm công sẽ tích hợp với hệ thống bảng lương để tính lương cho nhân viên.
### 3. Ca sử dụng: RunPayroll
#### Mô tả sự tương tác giữa các đối tượng thiết kế
1. Tác nhân:
+ Người quản trị hệ thống: Là người thực hiện quy trình trả lương.
2. Các đối tượng thiết kế liên quan:
+ PayrollController: Lớp điều khiển chính, chịu trách nhiệm khởi động quy trình trả lương.
+ IBankSystem: Interface để tương tác với hệ thống ngân hàng.
+ BankSystem: Lớp cụ thể thực hiện việc gửi tiền lương vào tài khoản ngân hàng.
+ Paycheck: Thực thể chứa thông tin chi tiết về phiếu lương của nhân viên.
+ Employee: Thực thể chứa thông tin về nhân viên, bao gồm thông tin ngân hàng và mức lương.
3. Quy trình tương tác:
+ Người quản trị đăng nhập vào hệ thống và chọn tùy chọn "Chạy quy trình trả lương".
+ PayrollController được gọi để thực hiện quy trình trả lương.
+ PayrollController lấy thông tin lương từ các thực thể Employee và tạo ra các thực thể Paycheck.
+ PayrollController gọi IBankSystem để gửi tiền lương cho nhân viên.
+ IBankSystem chuyển yêu cầu đến BankSystem, nơi thực hiện giao dịch gửi tiền.
#### Đơn giản hóa sơ đồ trình tự bằng hệ thống con
1.  `PayRollController`: Quản lý việc tính toán lương
2.  `Paycheck`: Thể hiện chi tiết tiền lương sau khi tính toán.

![Senquence Diagram](https://www.planttext.com/api/plantuml/png/Z5BBQWCn3BphAqGkEONSUoXfanPo2qdx0S8h4X4_jfQsPR-jXtvIVw5UQ3RTJGC1Wn6QyMX6_lxyMgXHjYPuqAD4p4aPmCGyusH3RKxUuoOdnwguuxU6esDS2UqpXGd055yEebWEeKhSUvvvYOmkXS3H0EPJE2D2uqs6WEaSW9obZ0zLa2XgcKe5TPbAdDGK3N_dMAPetSt3xYF5uwvLum3bGR6smxi3k-EfVWgrJoqNOmCDdDrVFertkEiImP5vk4HUeM_Pil0xzxAu8gFR-Klohl5atFku8hu-Eo-qqv8Aj0jMuMzxLk03z7FA7vIh4xeCNLQh1YFEIA87QrdaKE1_BoF6pHcyrbKNG9_WbbtAbG8iE5Rbi_u0003__mC0)
#### Mô tả hành vi lưu trữ
1. Employee Information:Name, Salary, Bank Account Information
2. Payroll Information:Paycheck ID, Employee ID, Amount, Date of Issue,
3. Bank Transactions:Transaction ID, Amount, Transaction Time, Employee ID
#### Tinh chỉnh mô tả luồng sự kiện
Luồng sự kiện:
+ Người quản trị đăng nhập vào hệ thống.
+ Người quản trị chọn "Chạy quy trình trả lương".
+ Hệ thống xác thực quyền truy cập của người quản trị.
+ PayrollController lấy thông tin từ cơ sở dữ liệu.
+ PayrollController tạo các thực thể Paycheck cho từng nhân viên.
+ PayrollController gọi IBankSystem để gửi tiền lương.
+ Hệ thống ngân hàng xử lý giao dịch và gửi thông báo thành công.
#### Hợp nhất các lớp và hệ thống con
1. PayrollController: Là lớp điều khiển trung tâm, quản lý toàn bộ quy trình trả lương.
2. IBankSystem và BankSystem: để tương tác với hệ thống ngân hàng
3. Paycheck và Employee: Các thực thể này được định nghĩa rõ ràng, giúp việc truy xuất và xử lý thông tin trở nên dễ dàng hơn.
## 4. Giao dịch với hệ thống ngân hàng (BankSystem Subsystem):**
**- Mô tả:** Hệ thống tương tác với các ngân hàng bên ngoài để thực hiện các giao dịch, như chuyển khoản lương qua tài khoản.
**- Thiết kế:**
  + Thành phần tham gia:
      **PayrollController** (control): điều khiển quá trình thực hiện giao dịch.
      **IBankSystem** (interface): đại diện giao tiếp với hệ thống ngân hàng.
      **BankSystem** (subsystem): hiện thực giao tiếp với hệ thống ngân hàng bên ngoài.
      **Paycheck, BankInformation** (entity): thông tin cần thiết cho giao dịch.
  + Luồng chính: 
      B1: **PayrollController** gọi **IBankSystem** với thông tin phiếu lương **(Paycheck)** và thông tin ngân hàng **(BankInformation)**.
      B2: **IBankSystem** chuyển yêu cầu đến **BankSystem.**
      B3: **BankSystem** thực hiện giao dịch với ngân hàng.
      B4: Hệ thống trả kết quả về cho **PayrollController.**
**- Lý do thiết kế:**
  + Encapsulation: Interface **IBankSystem** đóng vai trò trung gian, giúp giảm phụ thuộc vào các thay đổi trong hệ thống ngân hàng.
  + Mô hình client-subsystem: Tương tác giữa **PayrollController** và **BankSystem** qua interface chuẩn hóa.
## 5. In phiếu lương (PrintService Subsystem):**
**- Mô tả:** Hệ thống tạo và in các phiếu lương để cung cấp cho nhân viên.
**- Thiết kế:**
  + Thành phần tham gia:
      **PayrollController** (control): điều phối quá trình in phiếu lương.
      **IPrintService** (interface): giao diện với dịch vụ in.
      **PrintService** (subsystem): hiện thực giao tiếp với máy in.
      **Paycheck** (entity): thông tin phiếu lương cần in.
  + Luồng chính:
      B1: **PayrollController** gửi thông tin phiếu lương **(Paycheck)** và chỉ định máy in qua **IPrintService.**
      B2: **IPrintService** gọi **PrintService** để in phiếu lương.
      B3: **PrintService** thực hiện in và trả thông báo trạng thái.
**- Lý do thiết kế:**
  + Interface **IPrintService** giúp đảm bảo khả năng mở rộng, cho phép tích hợp với nhiều loại máy in khác nhau.
  + Subsystem **PrintService** tách biệt logic in ấn khỏi phần điều phối chính **(PayrollController).**
## 6. Quản lý mã dự án (ProjectManagementDatabase Subsystem):**
**- Mô tả:** Cung cấp thông tin mã dự án (charge numbers) từ cơ sở dữ liệu quản lý dự án.
**- Thiết kế:**
  + Thành phần tham gia:
      **TimecardController** (control): điều phối việc lấy mã dự án.
      **IProjectManagementDatabase** (interface): giao diện với hệ thống quản lý dự án.
      **ProjectManagementDatabase** (subsystem): hiện thực giao tiếp với cơ sở dữ liệu.
  + Luồng chính:
      B1: **TimecardController** gửi yêu cầu đến **IProjectManagementDatabase** với tiêu chí lọc.
      B2: **IProjectManagementDatabase** chuyển yêu cầu đến **ProjectManagementDatabase.**
      B3: **ProjectManagementDatabase** truy xuất dữ liệu và trả danh sách mã dự án.
**- Lý do thiết kế:**
  + Encapsulation: Interface **IProjectManagementDatabase** cung cấp một điểm truy cập duy nhất, giảm sự phụ thuộc vào cấu trúc cơ sở dữ liệu.
  + Hỗ trợ khả năng tích hợp: Subsystem **ProjectManagementDatabase** cho phép tích hợp liền mạch với các hệ thống kế thừa.

