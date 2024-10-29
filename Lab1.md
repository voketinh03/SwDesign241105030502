#Lab1
 # 1. Phân tích kiến trúc
- Kiến trúc dịch vụ: kiến trúc 4 lớp
  + Giai thích lý do lựa chọn:
     + Tính tách biệt mỗi lớp, giúp quản lý và phát triển hệ thống dễ dàng.
     + Khả năng mở rộng dễ dàng bổ sung các tính năng mới mà không làm gián đoạn các phần khác của hệ thống.
     + Bảo trì và kiểm soát lỗi tốt.
     + Hệ thống dễ dàng tích hợp với các dịch vụ và hệ thống bên ngoài.
   + Định nghĩa:
     + Presentation Layer: Chứa các thành phần giao diện người dùng, quản lý hiển thị và tương tác giữa người dùng và ứng dụng.
     + Business Services: Lớp Business Services chứa các thành phần nghiệp vụ chung được sử dụng trong nhiều ứng dụng.
     + Service Layer: Lớp Application chứa các thành phần thiết kế đặc thù của ứng dụng.
     + Data Access Layer: Chứa các thành phần truy cập dữ liệu, chịu trách nhiệm kết nối và thao tác với cơ sở dữ liệu.
   + Ý nghĩa:
     + Presentation Layer: Kết nối giữa người dùng và hệ thống, cung cấp giao diện thân thiện.
     + Business Layer: Thực hiện quy trình nghiệp vụ chính, đảm bảo tính chính xác và đáng tin cậy trong việc tính toán lương và xử lý hoa hồng.
     + Service Layer: Quản lý giao tiếp giữa lớp nghiệp vụ và lớp truy cập dữ liệu
     + Data Access Layer: Gíup truy cập và quản lý cơ sở dữ liệu, thực hiện lưu trữ và truy xuất thông tin.
   + Biểu đồ package mô tả kiến trúc.
 ![package](https://planttext.com/api/plantuml/png/P951YW9134NtEKNm07q05s8xin5S23AhmKMeoMXXMIr9McXaJZOBZ-GLhB8LhJQhokCb_52N__DKZSJQVG3GdOyeZJAOjy2uf4wQ473LgV4UQt5RR-oi5GOuaDlH9ad2oj78V1CNrB7W2J3LzvUczpmQooyvNiFVSsRMge-iMlWFY8jcurtXhrYEtd6XtndUO65_ab7jt71_njZpbw7t-5Kr6GGSuoWTeoCeSHQBPCdxe12IME3i3JCbjM_pMfXo_Ca_S0K00F__0m00)
# 2.  Cơ chế phân tích
- Đề xuất cơ chế và giải thích lý do
  + User authentication
    + Giari thích: Đảm bảo nhân viên hợp lệ mới có quyền truy cập vào hệ thống và thục hiện quyền chỉnh sửa.
  + Decentralization
    + Giari thích: Đảm bảo nhân viên chỉ có quyền truy cập và chỉnh sửa thông tin mà họ có quyền.
  + Employee data management
    + Giai thích: Quản lý thông tin nhân viên.
  + Salary calculation
    + Giai thích:Cần có cơ chế tự động tính toán lương cho từng nhân viên dựa trên giờ làm việc và doanh số bán hàng và hoa hồng.
   + Data synchronization
     + Giai thích:Đảm bảo rằng dữ liệu trên các máy tính cá nhân của nhân viên được đồng bộ với cơ sở dữ liệu trung tâm.
 # 3. Phân tích ca sử dụng Payment
 + Xác định các lớp phân tích cho ca sử dụng Payment
    + Employee: Quản lý thông tin nhân viên.
        + Nhiệm vụ:
            + Quản lý thông tin cá nhân của nhân viên.
            + Lưu trữ và cập nhật các loại thanh toán mà nhân viên nhận.
        + Thuộc tính:
            + name: Tên nhân viên.
            + employeeType: Loại nhân viên (theo giờ, cố định, hoa hồng).
            + paymentClassification: Đối tượng PaymentClassification.
            + paymentMethod: Đối tượng PaymentMethod.
        + Quan hệ:
            + Tương tác với PaymentClassification và PaymentMethod để xác định cách thức và phương thức thanh toán của từng nhân viên.
    + PaymentClassification: Định nghĩa các loại thanh toán mà nhân viên.
         + Nhiệm vụ:
             + Định nghĩa các loại thanh toán mà nhân viên có thể nhận.
             + Tính toán số tiền lương dựa trên loại thanh toán.
         + Thuộc tính:
             + type: Loại thanh toán (Hourly, Salary, Commissioned).
             + rate: Tỷ lệ lương.
         + Quan hệ: Được liên kết với Employee, để nhân viên có thể được phân loại theo loại thanh toán 
    + PaymentMethod: Xác định các phương thức thanh toán, giúp dễ dàng thay đổi cách thức thanh toán cho từng nhân viên.
         + Nhiệm vụ:
             + Xác định phương thức thanh toán cho từng nhân viên.
             + Cung cấp khả năng thay đổi phương thức thanh toán khi cần.
         + Thuộc tính:
             + methodType: Loại phương thức thanh toán (chuyển khoản, tiền mặt, bưu điện).
             + accountDetails: Thông tin tài khoản nhận tiền.
         + Quan hệ: Liên kết với Employee để mỗi nhân viên có thể được gán một phương thức thanh toán
    + PaymentTransaction: Lớp xử lý logic liên quan đến việc tạo và thực hiện giao dịch thanh toán.
         + Nhiệm vụ:
             + Xử lý logic tạo và thực hiện giao dịch thanh toán.
             + Theo dõi các giao dịch thanh toán theo thời gian và phương thức đã chỉ định.
         + Thuộc tính:
             + transactionID: Mã giao dịch.
             + amount: Số tiền thanh toán.
             + date: Ngày thực hiện giao dịch.
         + Quan hệ:
             + Liên kết với Employee, để xác định nhân viên nào đã nhận thanh toán.
             + Tương tác với PaymentClassification để tính toán số tiền thanh toán chính xác dựa trên loại thanh toán.
 + Biểu đồ sequence
 ![package](https://planttext.com/api/plantuml/png/V98nQiCm58Ptdq9ZE_G27KgWXHPgGW8ckr1A94YVWYj3Se8EcN84fuIGWA539ucIGP1xl1Fq2drkKsG7kQlVz_tw-V6NE_HU3CzDyJnDk30wPyC2xHka_ZCzlXzBc9m-zwLVmqZvFIGpufLGCmw6FQ1xpIIw5Kp--ERvNd5zXsufP2Ovo4pxikqFwjXKeorL9_6RMx-o4mqeEM_AhcuYVTWrM_XzSOjsMmJxuZA9e1GGQqmHXXhgS2Cz2b9068gqAThD8fF-W_eh22Vo6nnPqHtgTtq5ybIFf3ZsJ-sS9df4Up0_OuMWhlPTQrFM75r5OxSsxCJFXvZxKlGbsWfQVky9nlMlzmq00F__0m00)
 + Biểu đồ lớp mô tả lớp phân tích
    ![package](https://planttext.com/api/plantuml/png/T5J1IiD04BtdAvOSXHQz1YcbBRI788gXznXhTY7PIBCzY7ZmvA6N5iz2O_6W9mL1o59wsDB_s2_m5zmaJR9haboQlfbvC_Dc9hzqsms9FIKptzCSpmv3S0RPAnuZze71lGQInsVh4ZG0mYJ3IVhtaamHTZFa5ku_zn5sBSZfksD16qChO97mEc-mv762tWnu724rg0RE8gvulCPk7_BupU-pR-mQm4GXEUtznpkP_sufie_Ogd3SBNAWepreXzuhqRa4s6MhEmCCR3B901Tn-cAobJyMBq-Ef8fGQy3f5tiyI5MGbnaLrbxQgipC8clAwTm0DrvWImIrSkHSNeghu_0JhSrS-4amJ8hEQREepDZdTBbRY9mOAcR2wOyf-Xi5zeZJvqIyIatrSrNBKhtK8Xs8BCJZBIdWWlnYbip3P9j33z925gQcVIn8XiWEn43c3gnMbmwWT93740f9H5qq6QEaICqjY4pIpUWdEcYrW7xSRX_frOLgTYtNeyv7_DHVGvDlmxbL95MBg1DBwqxmTV9z-0C00F__0m00)
# 4. Phân tích ca sử dụng Maintain Timecard
# 5. Hợp nhất kết quả phân tích
   
