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
 ![sequence](https://planttext.com/api/plantuml/png/V98nQiCm58Ptdq9ZE_G27KgWXHPgGW8ckr1A94YVWYj3Se8EcN84fuIGWA539ucIGP1xl1Fq2drkKsG7kQlVz_tw-V6NE_HU3CzDyJnDk30wPyC2xHka_ZCzlXzBc9m-zwLVmqZvFIGpufLGCmw6FQ1xpIIw5Kp--ERvNd5zXsufP2Ovo4pxikqFwjXKeorL9_6RMx-o4mqeEM_AhcuYVTWrM_XzSOjsMmJxuZA9e1GGQqmHXXhgS2Cz2b9068gqAThD8fF-W_eh22Vo6nnPqHtgTtq5ybIFf3ZsJ-sS9df4Up0_OuMWhlPTQrFM75r5OxSsxCJFXvZxKlGbsWfQVky9nlMlzmq00F__0m00)
 + Biểu đồ lớp mô tả lớp phân tích
    ![package](https://planttext.com/api/plantuml/png/T5J1IiD04BtdAvOSXHQz1YcbBRI788gXznXhTY7PIBCzY7ZmvA6N5iz2O_6W9mL1o59wsDB_s2_m5zmaJR9haboQlfbvC_Dc9hzqsms9FIKptzCSpmv3S0RPAnuZze71lGQInsVh4ZG0mYJ3IVhtaamHTZFa5ku_zn5sBSZfksD16qChO97mEc-mv762tWnu724rg0RE8gvulCPk7_BupU-pR-mQm4GXEUtznpkP_sufie_Ogd3SBNAWepreXzuhqRa4s6MhEmCCR3B901Tn-cAobJyMBq-Ef8fGQy3f5tiyI5MGbnaLrbxQgipC8clAwTm0DrvWImIrSkHSNeghu_0JhSrS-4amJ8hEQREepDZdTBbRY9mOAcR2wOyf-Xi5zeZJvqIyIatrSrNBKhtK8Xs8BCJZBIdWWlnYbip3P9j33z925gQcVIn8XiWEn43c3gnMbmwWT93740f9H5qq6QEaICqjY4pIpUWdEcYrW7xSRX_frOLgTYtNeyv7_DHVGvDlmxbL95MBg1DBwqxmTV9z-0C00F__0m00)
# 4. Phân tích ca sử dụng Maintain Timecard
  + Xác định các lớp phân tích cho ca sử dụng Maintain Timecard
     + Timecard:Lớp đại diện cho thông tin về thời gian làm việc của nhân viên
       + Nhiệm vụ:
             + Quản lý thông tin về thời gian làm việc của từng nhân viên.
         + Thuộc tính:
             + employeeId: ID của nhân viên.
             + date: Ngày làm việc.
             + hoursWorked: Số giờ làm việc trong ngày.
             + overtimeHours: Số giờ làm thêm.
             + chargeNumber: Mã số công việc (charge number).
         + Quan hệ:
             + Employee: Nhiều thẻ cho một nhân viên.
             + Project: Nhiều thẻ cho nhiều dự án.
             + Payroll: Một thẻ có thể tính lương.
     + Employee: Lớp chứa thông tin về nhân viên
       + Nhiệm vụ:Quản lý thông tin của nhân viên liên quan đến thẻ chấm công, bao gồm loại hình nhân viên 
         + Thuộc tính:
             + employeeId: ID của nhân viên.
             + name: Tên của nhân viên.
             + position: Vị trí công việc của nhân viên.
             + paymentType: Loại hình trả lương của nhân viên (theo giờ, lương cố định hoặc hoa hồng).
             
         + Quan hệ:
             + Timecard: Nhiều thẻ cho một nhân viên.
             + Payroll: Nhiều phiếu lương cho một nhân viên.
             + Authorization: Một quyền truy cập cho mỗi nhân viên.
     + Payroll:Lớp quản lý và tính toán lương cho nhân viên dựa trên dữ liệu thẻ chấm công và quy tắc thanh toán.
       + Nhiệm vụ:
             + Quản lý và xử lý các thông tin liên quan đến thanh toán, bao gồm thông tin về số giờ làm và tiền lương.
         + Thuộc tính:
             + payrollDate: Ngày thanh toán.
             + totalHours: Tổng số giờ làm việc.
             + totalEarnings: Tổng thu nhập.
         + Quan hệ:
             + Timecard: Một hệ thống lương có thể tính từ nhiều thẻ.
             + Employee: Nhiều phiếu lương cho nhiều nhân viên.
     + Project:Lớp quản lý các dự án và mã số công việc
       + Nhiệm vụ:
             + Quan hệ: Quản lý thông tin về các dự án hoặc mã số công việc mà nhân viên có thể được phân công.
         + Thuộc tính:
             + projectId: ID của dự án.
             + chargeNumber: Mã số công việc.
             + projectName: Tên dự án.
         + Quan hệ:
             + Timecard: Nhiều thẻ có thể liên quan đến nhiều dự án.
     + TimecardManager:Lớp chịu trách nhiệm tạo, chỉnh sửa, xóa và truy xuất thẻ chấm công của nhân viên.
       + Nhiệm vụ:
             + Quản lý việc tạo, chỉnh sửa, lưu trữ và truy xuất các thẻ chấm công.
         + Thuộc tính:
             + timecardList: Danh sách các thẻ chấm công.
         + Quan hệ:
             + Timecard: Một trình quản lý có thể quản lý nhiều thẻ.
             + Employee: Quản lý thẻ của nhiều nhân viên.

     + Authorization:Lớp kiểm tra và đảm bảo rằng nhân viên chỉ có quyền truy cập, chỉnh sửa thẻ chấm công của mình.
       + Nhiệm vụ:
             + Xác thực quyền truy cập của nhân viên
         + Thuộc tính:
             + userId: ID của người dùng.
             + role: Vai trò của người dùng.
         + Quan hệ:
             + Employee: Một quyền truy cập cho mỗi nhân viên.
 + Mô tả được hành vi thông qua biểu đồ sequence
     + Tính luong - Basic Flow
    ![sequence](https://planttext.com/api/plantuml/png/d9EzJiCm58NtFCLLTrw00LMb28OA8RLYjrAhiUeu9N4YPKGC34nz04GBGaYLAXYOug63KT_3Jz1Nu2RzSwY545cy-7ptd7ETbLeq4qbYcORS8xwCOcXS67KFlS2eiHWqW2JGpHD9Gs-4rvZFHaJ8-YLecU85ZyxoOpdTQAv87aUSkwIdoobqZNg2jb7lq658Ik4SZqVew4bOoNiif3w9--tM7xINWNuMSCtqJ5JYit34evnI57jh0t1qKdS4nv3hMGg-ATvIa7ek0f2HdWhWwn3W1n682foLuB8SbX59VoJpwbYSixUEGxWfNdEGWVv4f6G21bLEZZcHY-xzFTZAR34SpcMCVKDcrAq3rwSkuA7DVKakcyxaLg-M-dU35dFRRAOdC4IpTsbjZ6NSNY3XShFWwXe2QRIExG5-1xaEl5IxtSwsr9Gdj4RURHuVDNoDZNeGmNzcrFHKz1tbxvG3e-OCXgPOIBX9ozOSRz6kflxwceWl_znl0000__y30000)
     + Maintain Timecard - Basic Flow
       ![sequence](https://planttext.com/api/plantuml/png/j5InIWD14EtzYYcro0-a24452wCWYltbBcGNBviZsGrO1eiKDeALY9Wpf5632e9mYrYiv3_s2_m5PzUOt2LwbnFS9hcPjs_UpEpCXtmhjxdJugBXhm2U0FzJbmOEux1Br0qxfEgMBRXsT7Gd3eYMLtIBEel-TIqlti-ebbsnJV3dXAM0KrmRut1Vo-jDBHygIDCJUq970rPHhsXwKbssOgyuBgSTXzVc9Sy-2wLIcgOYUE8OU4lTpsohQqdkp9pCIGEXXdX4NqT3Z6ajK4SJc0iz1bn78Pr4jmfyde0T4VNCwWYJvnFm56fE8c1wqho5rOGEUe49tq_GvCZ4Q6Wc93Qql8odK6FUiYMQUrf5-C9O-jDua1Xz1cNcA_fkHaCDm2KK0g96CVhC-uKybOu7cOQOopgJZn4TZGAi0vgGhGck2jsVgNCqqhMabfl_hTI91pv-5B-mv6wFeUgeFkOv3g6DQF0G3hx5_rEZE55zHh2oPjf8KqSlhaad6dAeJgVEgos_839gDzjM2u_UIgWgEsNvHCKsOXcdqEpvJm000F__0m00)
      + Maintain Timecard - Basic Flow
         ![sequence](https://planttext.com/api/plantuml/png/b5F1IiD04BtdAuQUL6YgLn4HMwZGA9K6xp4jsSLq0-skKCI3UF3WnOi73s9h4K6KrfEG83riwN_i5_WBJjBO9BKgddPttioyjszsFuBHLfjRBIwQhcQxLhiD9b71BIrJYy691f276czHva1JzlU8l6S7L3wn22XPl07CaTtEjl87V7ob_4SnXrIKF-8caRuT0NLF7BeDu2guPawP8fCXkyqqv8H1StpEdA8rL_9cgE2YEEaXMvyjmXQKkPFXfCSSaqo6s9SvYx25PAZFcE8Q8W1SlZ0IHvQMr-FC2C8-ua1slMAjP8JGeUUv3OjffrfiQU9RrbB-vMHyflNeL2Y0hkjWovuDd0WLtDXJUZWY68joLdLz9JqgFjlke84Np5H-ZqwLrqK7U4i-9zcXo6CFsMOAjv5aV8MLPw92S3bdSyy0RwdyXqwsHtBwRb4YA9sNDIvXkgpYtX-9Fwkpil4nr5HmLrB1m0YlBVP5-3OC-OwXLtcMqRuh-qL2gqI-XDeDskORKzytPrDCNUz71QdffZpAhUKWduSSpWLtgO6l_p2QNnsFsuGDSKdP_8-gFxtHjAq6guSV_nC00F__0m00)
# 5. Hợp nhất kết quả phân tích
  + Giới thiệu:
     + Select Payment Method: Cho phép nhân viên chọn phương thức thanh toán, bao gồm nhận trực tiếp, qua bưu điện, hoặc chuyển khoản ngân hàng.
     + Maintain Timecard: Cho phép nhân viên nhập và quản lý bảng chấm công, bao gồm thông tin số giờ làm việc và dự án tương ứng.
   + Phân tích yêu cầu:
    - Ca sử dụng 1: Select Payment Method
      + Mô tả:
        - Nhân viên có thể chọn phương thức thanh toán bao gồm nhận phiếu lương trực tiếp, qua bưu điện hoặc chuyển khoản trực tiếp vào tài khoản ngân hàng.
      + Yêu cầu chức năng:
        - Nhân viên chọn một trong ba phương thức thanh toán.
        - Hệ thống yêu cầu thông tin bổ sung tùy vào lựa chọn (địa chỉ hoặc tài khoản ngân hàng).
        - Hệ thống cập nhật phương thức thanh toán vào hồ sơ nhân viên.
    - Ca sử dụng 2: Maintain Timecard
      + Mô tả:
        - Nhân viên có thể nhập và quản lý bảng chấm công cho kỳ lương hiện tại, bao gồm việc ghi nhận số giờ làm việc theo từng dự án.
      + Yêu cầu chức năng:
        - Hệ thống hiển thị bảng chấm công hiện tại hoặc tạo bảng chấm công mới nếu chưa có.
        - Nhân viên nhập số giờ làm việc theo từng dự án và ngày tương ứng.
        - Hệ thống xác thực tổng số giờ làm việc và lưu lại bảng chấm công.
  + Phân tích lớp:
    - Các lớp phân tích chính:
      + Employee (Nhân viên): Đại diện cho nhân viên sử dụng hệ thống. Nhân viên có thể chọn phương thức thanh toán và nhập bảng chấm công.
      + PaymentMethod (Phương thức thanh toán): Đại diện cho các phương thức thanh toán nhân viên có thể chọn, bao gồm thông tin về nhận trực tiếp, qua bưu điện hoặc chuyển         khoản ngân hàng.
      + BankAccount (Tài khoản ngân hàng) và Address (Địa chỉ): Lưu trữ thông tin bổ sung nếu phương thức thanh toán yêu cầu.
      + Timecard (Bảng chấm công): Lưu trữ thông tin về số giờ làm việc của nhân viên trong kỳ lương hiện tại.
      + Project (Dự án): Lưu trữ thông tin về các dự án mà nhân viên làm việc và liên kết với số giờ làm việc trong bảng chấm công.
      + TimecardManager và PaymentManager: Quản lý các thao tác liên quan đến bảng chấm công và phương thức thanh toán.
    - Biểu đồ lớp tổng hợp:
      ![ClassDiagram](https://planttext.com/api/plantuml/png/V5HBJiCm4Dtd55PNi6W5MrOjBH98j69HYRKRZrfJVoBRgHGXJiQ28t459edjnav4DXFFFC-Rpqj-lt-Mrb7ZQYcAeXJKMl8aAw4R0F9P47pc1BpZXP47mfNpRaKbeCCwmzKnGYaNgPCG2m9AzqOR2SfjmPqqkxb5q4LpvY4O0FEiQsFpYAqFahizbr1ICxZt5SfDyiQQPNVSDnNarTGLemxoCcAwHwhEgxBKjN8nsG5zkubkQO_RrV809kSvWcjpRS3XIFgsV3nohHWpW3RmO1p0vImbTqtkgpHkJQmr6xM7j3xj96MO5bNqY3K7vceun5Tkso9QuvFA3kxlvXj2ndLjJBhRP2jN-h37GSielWqk1E-q9kX8iR7prEhZNPipj4BSqYhPwBHww0McD6Fq1qhosdv_pWJklUFDTptx73rbDwjHb_cKdVUF1rmQm1OIbOU3Hroeu2p77BGMG5NB7B_QsVsCpEUTIPUGVYW1ThTOuDj0zV_YlBIAJ4O8IBacouaTHHNCL1z4uyTPvBF3SBnNB54NxP_g3m00__y30000)
  + Biểu đồ tuần tự hợp nhất:
    - Biểu đồ tuần tự cho quy trình duy trì bảng chấm công (Select Payment Method):
      ![Sequence Diagram](https://planttext.com/api/plantuml/png/f9FDIWCn58NtynJd1GpMVxkGOXSA_k12n9t4T9W4EkamJOKknQMuSE5Ii4eH2qKNhZABBaRw7da2Ny4x0vMsL6lhAeJaV3dttfFFf5Ug6nwRHbZrk32r68SoVTHd9ohjQ2-Y4oLKnBN14M-6lZO7NFF0ZoSU-KRMAfutHC32rfYmY0B3jhEl1X-tpZut44W5BPtjQWJA9VUefW_XDCWI8wEaYM1a-gu363MBV9bXnoLTzODwzFeam0h3SThL4gQMjZICI-u8CnDYbM7VsNOJ5KwSUjeI4f7il_LRcI7faXT12n-yyGinxtiHQmoxPE1Av-hhFy5owIHtwrHWxEmJBbnoER_5eJaKiJ63mIa3t6Gea-X6_mTIM6GufQ86yPkl-zyq2dOvZsIECpYdzX5CqAuTGcH16tSqqfu2XNhFsPx9Kcc5L_9r9VkNNm000F__0m00)
    - Biểu đồ tuần tự cho quy trình ghi nhận giờ làm việc (Maintain Timecard):
      ![Sequence Diagram](https://planttext.com/api/plantuml/png/b9CzImCn7CRt-nJFg8F1-cu7AJee-8A3Y9k4zBW4UkbnJOMEukZau2XOfOY5eeDJCdI8z7la4_WLp1qeVRDdbuJmv_db-UV_vClqAmr5KzMCQm5bgfxYXDidUNakR5S6YQy89X8g5KvfAmwbEgQIHc4wjHGgNgy6mH01IpjZmZ9A1BjElobytZdzqaJ41IHtkYSH2MSUKBEFSJ2goZX3s39MY3zxJGB5xOUCeCI8lC33Ai6-CptnXthoyd706i6PxKaELRTj2UNClSVCXLWdE7AwqqALUax3jXb7mWVlWtPcY3lpoln6V-zOa4xtcs3-qUJY37u-XJ8s20wydHkPisvdeOCHwJIlcxxTrEbdN3bp_K_3HIFSciDWmJYt2IwydPyOpMTg8f_B17jvj7ASoYZQWFcr4uDbUIbghUGpVkYdbMcjPa4bbDNiXtq3003__mC0)
  e. Mối quan hệ giữa các lớp:
    - Employee: Lớp Employee tương tác với cả hai chức năng Select Payment Method và Maintain Timecard. Nhân viên có thể chọn phương thức thanh toán hoặc quản lý bảng chấm        công của họ.
    - PaymentMethod: Lớp PaymentMethod lưu trữ thông tin về cách thức nhân viên nhận lương và tương tác với lớp PaymentManager để cập nhật thông tin thanh toán.
    - Timecard: Lớp Timecard lưu trữ thông tin về số giờ làm việc và dự án tương ứng, tương tác với lớp TimecardManager để xác nhận và lưu bảng chấm công.
    - PaymentManager và TimecardManager: Cả hai lớp này quản lý các hoạt động chính của hệ thống liên quan đến thanh toán và bảng chấm công.
