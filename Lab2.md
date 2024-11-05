# Lab2 
I. Tiến hành phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System.
 1. Phân tích ca sử dụng Create Administrative Report
   - Xác định lớp phân tích ca sử dụng Create Administrative Report
     - PayrollAdministrator: Đại diện cho nhân viên quản lý tiền lương.
       - Nhiệm vụ:
           + Yêu cầu tạo báo cáo.
           + Cung cấp tiêu chí báo cáo (loại báo cáo, ngày bắt đầu và kết thúc, tên nhân viên).
       - Thuộc tính: id, name, role
       - Quan hệ:
           + Có thể tạo báo cáo thông qua lớp System.
    - ReportGenerator: Chịu trách nhiệm tạo báo cáo dựa trên các tiêu chí đã được chỉ định.
         - Nhiệm vụ:
           + Nhận tiêu chí báo cáo từ hệ thống.
           + Tạo báo cáo dựa trên tiêu chí và gửi kết quả trở lại hệ thống.
           + Thông báo lỗi nếu tiêu chí không hợp lệ.
       - Thuộc tính: reportType, startDate, endDate, employeeNames
       - Quan hệ:
           + Kết nối với lớp Report để tạo báo cáo và gửi thông tin trở lại lớp System.
    - Report: Đối tượng đại diện cho báo cáo, lưu trữ thông tin báo cáo đã được tạo.
         - Nhiệm vụ:
           + Đại diện cho báo cáo đã tạo.
           + Lưu trữ thông tin báo cáo và hỗ trợ lưu báo cáo vào vị trí chỉ định.
       - Thuộc tính: reportID, content, createdDate
       - Quan hệ:
           + Được tạo ra bởi lớp ReportGenerator và lưu trữ thông tin báo cáo.
    - System: Đại diện cho hệ thống, nơi mà các yêu cầu từ nhân viên quản lý được xử lý.
         - Nhiệm vụ:
           + Xử lý yêu cầu từ nhân viên quản lý.
           + Giao tiếp với các lớp khác để tạo báo cáo và xử lý thông tin.
       - Thuộc tính: currentUser, reports
       - Quan hệ:
           + Giao tiếp với tất cả các lớp để xử lý yêu cầu.
    - ErrorHandler: Xử lý các tình huống lỗi.
       - Nhiệm vụ:
           + Yêu cầu tạo báo cáo.
           + Cung cấp tiêu chí báo cáo (loại báo cáo, ngày bắt đầu và kết thúc, tên nhân viên).
       - Thuộc tính: errorMessage
       - Quan hệ:
           + Giao tiếp với lớp System để thông báo lỗi.
  - Biểu đồ sequence
    ![ClassSequence](https://planttext.com/api/plantuml/png/f5JFQi8m6B_dANBKmrwWXo7pieC8Wo9UkrfiM1TBJSKTnmuolEZ9qmv5na0eUDYfOUmGyJto17k5VMctBksgKrT88ScNtv_l-v8F_juOCYjWuQs7B9iD0dmLocH9pK3oQOU85JM9vFUqjLrl8zf7FiGIc_WMPVXIyedfIZulhRVxsxNaJyIKIJIu4D6W2QCGKRdObJnkYRUMv0k2q5uP-EnSPpVmdLY5s9R9IrWWhTMLAJAoc5DGYxI9mjfBPc0R8XytCzYbhWdxOTCLiSPnd5OxfFscJ9xzAgYIiCfK6fWLJ3AIkWSWpMvr4P3bCMpcyHYObZxsW1HX-2eFAHs7KEy5A6I01P2lN9CwTrmzN9W-K1K_pPLSAo8RVdNaU4D7DtdZYbV0FTIhteS67ckpMcPI3wZsPgQCcndedFXPG__BvM-y6ijCRURfchAr862TzX3gEOTq0V24ECzQgk_KEwUWj1u-tgf-mJhARo1Y1Ve5TkBzga0goVffQq-tC8A3KCZlfjxPnsCHsMrN9Z7TJV67ywoCYg5R1YlNKd_06h2fdknF0000__y30000)
  - Biểu đồ lớp mô tả lớp phân tích
    ![ClassDiagrams](https://planttext.com/api/plantuml/png/V5EnQiCm4Dtz5JUcWt_0GmbDXWuXK6fAryG9ji2LWoELbjAXT0WbIpAL3XrCAOL084CdYz11mV-XB-WlL98TMt6I3WRftjszTq_dN_RJ79DUJEXDQ7bXRpo62ohI3-p6Wasl45zW5mdsX3lPAakm3myMW0sN94RoGYHitj50tW3k-OAsHFf5NP4cqHbFefRy6YSQz2Zs9VWvSf5A2_Yobb1MIqfgO8zM8V1Si8aR23O_9CS0SpfvVjdCv30uECOOo0cViQgQbaY_E3Ym3UtbkW7_nlvc9YEJKKUmLzGWPiWfT1dIktws4kmTxHYZXm0WEsQHhTQoIwL4fzy9jkpmTSvhKEnqBQt1WhsXDjMcbC7DNDlIbiI5Mw5f-QsQCJOKvBmyyRg1I9Tg9MX3okf7KJZiuKh2jI6jza9xbXsPvVybjErJSmiS80L0f3ZBt0-LUT1qH-yPU6hHSkj1FJbuoj_3pwHwLUNrcZghQOAZ9uIGho7KGpU7UA3-k3y0003__mC0)
 2. Phân tích ca sử dụng Create Employee Report
  - Xác định lớp phân tích ca sử dụng Create Employee Report
    - PayrollAdministrator: Đại diện cho cá nhân chịu trách nhiệm quản lý thông tin nhân viên và tạo các báo cáo tiền lương trong hệ thống.
       - Nhiệm vụ:
           + Tương tác với hệ thống để yêu cầu tạo báo cáo và cung cấp thông tin cần thiết.
           + Đảm bảo rằng các tiêu chí báo cáo được chỉ định đúng và đầy đủ.
       - Thuộc tính:
           + tên:Tên của quản trị viên tiền lương
           + id: Mã định danh duy nhất của quản trị viên tiền lương
       - Quan hệ:
           + Quan hệ với HệThống (System)
    - System: Tạo điều kiện cho việc tạo báo cáo và quản lý các tương tác giữa các thành phần khác nhau.
       - Nhiệm vụ:
           + Quản lý quy trình tạo báo cáo và các tương tác của người dùng.
           + Đảm bảo thông tin được xử lý chính xác và kịp thời.
       - Thuộc tính:
           + tênHệThống: Tên của hệ thống tiền lương
       - Quan hệ:
           + Quan hệ với NgườiTạoBáoCáoNhânViên (ReportGenerator)
    - ReportGenerator: Chịu trách nhiệm tạo báo cáo dựa trên tiêu chí đã chỉ định và trả về báo cáo đã tạo cho hệ thống.
       - Nhiệm vụ:
           + Tiến hành quy trình tạo báo cáo dựa trên các tiêu chí được cung cấp từ quản trị viên tiền lương.
           + Đảm bảo rằng báo cáo được tạo ra chính xác và đầy đủ.
       - Thuộc tính:
           + tênHệThống: Tên của hệ thống tiền lương
       - Quan hệ:
           +Quan hệ với BáoCáo (Report)
 3. Phân tích ca sử dụng 
 4. Phân tích ca sử dụng
 5. Phân tích ca sử dụng
 6. Phân tích ca sử dụng
II. Viết code Java mô phỏng ca sử dụng Maintain Timecard.
