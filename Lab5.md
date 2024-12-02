# Lab 5:
## 1. Authentication Subsystem.
- Mô tả: Hệ thống xác thực chịu trách nhiệm quản lý việc đăng nhập và xác thực người dùng
- Thành phần chính:
    + LoginForm (boundary): Giao diện người dùng cho phép nhập thông tin đăng nhập.
    + AuthenticationSystem (control): Xử lý nghiệp vụ xác thực và quản lý quyền truy cập.
    + UserDatabase (entity): Lưu trữ thông tin người dùng
- Chức năng chính:
    + Kiểm tra thông tin đăng nhập
    + Quản lý phiên làm việc (sessions)
## 2. Maintain Timecard
#### Chức năng chính:
- Quản lý thời gian làm việc của nhân viên và trạng thái thẻ chấm công

#### Thành phần chính:
1. **`TimecardController`**:
   - Quản lý logic nghiệp vụ liên quan đến thẻ chấm công, bao gồm: 
     - Nhận thông tin giờ vào/ra từ giao diện người dùng.
     - Tính toán tổng số giờ làm việc hàng ngày.
2. **`Timecard`**:
   - Thực thể lưu trữ thông tin giờ làm việc, gồm:
     - ID nhân viên, ngày giờ vào/ra, tổng giờ làm việc.
3. **`ProjectManagementDatabase`**:
   - Lưu trữ thông tin danh sách dự án liên quan.
   - Thông tin thẻ chấm công theo từng dự án.

#### Mô tả chi tiết
  - Nhân viên sử dụng hệ thống để chấm công vào và ra.
  - Thông tin giờ làm việc được tính toán tự động và lưu trữ trong cơ sở dữ liệu.
  - Hệ thống hỗ trợ nhân viên gửi yêu cầu nghỉ phép, đồng thời cập nhật trạng thái thẻ chấm công khi cần.

---

## 3. Payroll Processing Subsystem
#### Chức năng chính
  - Tính toán lương cho nhân viên dựa trên dữ liệu từ hệ thống chấm công và thực hiện thanh toán lương.

#### Thành phần chính
1. **`PayrollController`**:
   - Quản lý logic nghiệp vụ tính toán lương dựa trên thông tin giờ làm việc và các yếu tố khác.
2. **`Paycheck`**:
   - Thực thể chứa thông tin phiếu lương:
     - ID phiếu lương, ID nhân viên, số lương, ngày phát hành.
3. **`BankSystemProxy`**:
   - Kết nối với hệ thống ngân hàng để thực hiện thanh toán.
4. **`PayrollDatabase`**:
   - Lưu trữ thông tin chi tiết về lương, hỗ trợ cho báo cáo và tra cứu.

#### Mô tả chi tiết
  - PayrollController lấy dữ liệu từ Timecard Subsystem và Employee Management Subsystem để tính toán lương.
  - Lương được gửi qua ngân hàng hoặc in phiếu lương tùy thuộc vào cấu hình.
  - Dữ liệu phiếu lương được lưu trữ trong PayrollDatabase để hỗ trợ cho các báo cáo tài chính.
## 4. Bank Interaction Subsystem .
####  Mô tả: 
  - Tích hợp với các hệ thống ngân hàng để thực hiện giao dịch.
####  Thành phần chính:
  - IBankSystem (interface): Định nghĩa giao diện giao tiếp ngân hàng.
  - BankSystem (subsystem): Hiện thực giao tiếp với ngân hàng.
  - BankInformation, Paycheck (entities): Dữ liệu cần thiết cho giao dịch.
#### Chức năng chính:
  - Thực hiện chuyển khoản lương.
  - Kiểm tra trạng thái giao dịch.
## 5. Printing Subsystem .
#### Mô tả: Quản lý in ấn cho phiếu lương nhân viên 
####  Thành phần chính:
   - IPrintService (interface): Giao diện chuẩn hóa cho dịch vụ in.
   - PrintService (subsystem): Hiện thực logic in phiếu lương.
   -  Paycheck (entity): Dữ liệu phiếu lương.
#### Chức năng chính:
   - In hoặc xuất phiếu lương dưới dạng tệp.
   - Quản lý trạng thái và kết quả in.
## 6. Project Management Subsystem .
####  Mô tả: 
     - Cung cấp mã dự án cho các hoạt động chấm công.
#### Thành phần chính:
      - IProjectManagementDatabase (interface): Giao diện với hệ thống quản lý dự án.
      - ProjectManagementDatabase (subsystem): Hiện thực việc lấy dữ liệu dự án.
#### Chức năng chính:
      - Lấy danh sách mã dự án từ cơ sở dự liệu.
      - Tích hợp với hệ thống quản lý dự án kế thừa.

