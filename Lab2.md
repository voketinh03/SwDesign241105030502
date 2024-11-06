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
           + Quan hệ với NgườiTạoBáoCáoNhânViên (ReportGenerator).
           + Quan hệ với BáoCáo (Report).
           + Quan hệ với XửLýLỗi (ErrorHandler)
    - ReportGenerator: Chịu trách nhiệm tạo báo cáo dựa trên tiêu chí đã chỉ định và trả về báo cáo đã tạo cho hệ thống.
       - Nhiệm vụ:
           + Tiến hành quy trình tạo báo cáo dựa trên các tiêu chí được cung cấp từ quản trị viên tiền lương.
           + Đảm bảo rằng báo cáo được tạo ra chính xác và đầy đủ.
        - Thuộc tính:
           + tênHệThống: Tên của hệ thống tiền lương
        - Quan hệ:
           + Quan hệ với BáoCáo (Report)
     - Report: Đại diện cho báo cáo đã tạo chứa thông tin nhân viên, có thể được lưu hoặc hiển thị.
         - Nhiệm vụ:
            + Lưu trữ nội dung báo cáo và cung cấp các phương thức để lưu hoặc hiển thị báo cáo.
            + Đảm bảo báo cáo có thể được lưu một cách hiệu quả.
         - Thuộc tính:
            + nộiDung: Nội dung của báo cáo.
            + địnhDạng: Định dạng của báo cáo.
          - Quan hệ:
             + Quan hệ với HệThống (System).
       - ErrorHandler: Quản lý các điều kiện lỗi xảy ra trong quá trình tạo báo cáo và gửi lỗi cho hệ thống.
       - Nhiệm vụ:
           + Theo dõi và xử lý các lỗi xảy ra trong hệ thống.
           + Cung cấp thông điệp lỗi cho quản trị viên tiền lương khi cần thiết.
         - Thuộc tính:
            + thôngĐiệpLỗi: Mô tả lỗi đã xảy ra.
         - Quan hệ:
            + Quan hệ với HệThống (System).
 - Biểu đồ sequence
    ![ClassSequence](https://planttext.com/api/plantuml/png/f5M_Qi907DxlAMwiO5_0eKZjq464GX3N60zpD5v2l4WTImSfBdRgr24jfI083fqIIeSJt-EUeA_GtqMhbnZJQWE6k_FxVT_t--Fv5NzM-zpqUT1pa6bnryTNWOnUcE7BUDoaOieCAkDRLb_Ebo7h8W-mrAAUoJY-bF78i6Nya3blT9Tp6JzHGqQXUov2jmQV52Bti2NZMLryr6NyI14gj85FptJr2XwAQL2JqLkGqcpOufabqISbbHqTc9oaR2DjeqWBLNKPgbQscFr8WS1XZgs0TO7grTkXqbpxn7DzRWmzKiP9couWWJ8chBDUz3p77HBIC7kaNyecazk72kRwzb29JHNpcunCX-Ca8sn1IXZCl7ZO0Ly8mvCRfApkSrSg3ajLbFjGVz2AGehR2c0fHoh-i2RRiBrZ2Z_U-6Yl5oi_oKjb2Z51HaizHywkOijaVhXx2v3tYmbyo-mcl0rVp1InHdZaeEvXozZRTj9HkC4wQ8lVsxyR4LeDMqOpLgpmIm6uBTvPTp61qv7NokE4sKR4wHDzKA-Jg3_FgtvNWNDjjzRG0OMJchAxkll-DRB63j_9haG9gHgW3ldbvwm1z5kp2j7g3-CR003__mC0)
 - Biểu đồ lớp mô tả lớp phân tích
    ![ClassDiagrams](https://planttext.com/api/plantuml/png/V5InRjim4Dtr5RVL6V836eAWzj31C53KABhIb20Uef2AJ1esYWwTCWG1agaeCYH6aI53q0u50fWeEiZ8V_0ByWibBLCLLQ42956dT--zEnxuedyVpoKffJhDerUmlJBwWZFW6Ti-4A3Lca9kz4q12_j4a4mP_PM2h1ujQb7TGS6UVpolUMP_6Vr0euZcP3w7juhmQOdlCULJUu-Li92F4RXBfZo6Tx94djK1J690BkkFLQg6HBqcOaZ4X17kA0O7CIm49ZM2AfuDIM5vrP1XZMmGdxo3D-cKXQBxIAYT86UJZ249wFg5cQkcKPpjNZ646Nq9EzaHfiLOu43w3-_Z7-UJJ0cS4b4JDmNuGEDDrevRF27WBsCOzunSu4ZrzMD4kj5SxNTai42xhLthEyoIKASmLifrRIP4dfAMXmzglBBrD-MqUX9gBMjWUqVx1_FKw6k4CpjfO6Vl738q-djxQAFUAJmyF6g68uQvqO-G67rlvNtK8JgR44Dcz2K6a4vNOv1cinO1n1UzJuSJXixQ5uIbsNnRGKcYZj1_Y3lXi8upPGavvDKlc1bz6phjxOEbPTLFkvXLQ-7MTxQ_T1TXmcoUQEqqyZM4UhAqUkvK-EnfjjUs_-V5FYiwJddY3fK_0000__y30000)
 3. Phân tích ca sử dụng Login
  - Xác định lớp phân tích ca sử dụng Login
    - User: Đại diện cho một nhân viên của công ty, có khả năng đăng nhập vào hệ thống.
       - Nhiệm vụ:
           + Cung cấp thông tin xác thực (tên và mật khẩu) cho hệ thống để đăng nhập.
       - Thuộc tính:
           + userName: Tên đăng nhập của người dùng.
           + password: Mật khẩu của người dùng.
       - Quan hệ:
           + Tương tác với lớp LoginSystem để gửi thông tin xác thực.
     - LoginSystem : Chịu trách nhiệm xử lý quá trình đăng nhập cho người dùng.
       - Nhiệm vụ:
           + Nhận thông tin đăng nhập từ User, xác thực thông tin và quyết định cho phép hoặc từ chối truy cập.
       - Thuộc tính:
           + loginState: Trạng thái đăng nhập hiện tại
       - Quan hệ:
           + Nhận thông tin từ User và xác thực với AuthenticationService
    - AuthenticationService : Một dịch vụ xác thực, kiểm tra tên đăng nhập và mật khẩu với dữ liệu người dùng hợp lệ.
       - Nhiệm vụ:
           + Xác thực tên và mật khẩu từ LoginSystem, trả về trạng thái xác thực thành công hoặc thất bại.
        - Quan hệ:
           + Nhận yêu cầu xác thực từ LoginSystem
     - ErrorHandler : Quản lý thông báo lỗi khi có lỗi xác thực xảy ra.
         - Nhiệm vụ:
            + Cung cấp thông báo lỗi cho người dùng khi tên đăng nhập hoặc mật khẩu không hợp lệ.
         - Thuộc tính:
            + nộiDung: Nội dung của báo cáo.
            + địnhDạng: Định dạng của báo cáo.
          - Quan hệ:
             + Kết nối với LoginSystem để hiển thị thông báo lỗi khi đăng nhập thất bại.
 - Biểu đồ sequence
    ![ClassSequence](https://planttext.com/api/plantuml/png/P9AnQiCm48PtFSMHAO6MxXbAF9WQQhAuXgwg8Y9HMpQod3PZoT2XKwUkDHbA0naAXO8zT71UH4_GL-Z92IL9DGZfrtV_VmVwQRv7XQ7Qb6b2A3EPXhZW6cW1CSbHbqpcL1deXTbKgcXU69xst7CO7RvxfH5SuPqQcQc8wvbal2Ez8zBNEjC1LPE4wmxm0q9YE3r7po6CXQtNEPJOnPYc_0HoMXHtcPwGC7ACXyo5RTOIvksg16RhjnBksug14RRvOD3_NpeW7jRk0gwqhPSmiyq363nMQegLRIKFJGBRB7D8RFC8Pt0fsa_4n9ys88Gc1iQs_YxtP0Aujct6GxXsVigDes3pl5cWWzeEXtclIW1pheGd1TyvtHxdx1dwmH02QPk5wdfySYOElcchpB4lieFzO9SUEkaejnzH2QPTAH2PhRyOf2WRZBNrUpaWN4q86U7kFiCl0000__y30000)
 - Biểu đồ lớp mô tả lớp phân tích
    ![ClassDiagrams](https://planttext.com/api/plantuml/png/Z58zJiCm5DvzYZUs4hr01bI4a1Y09U80hlr8BHoxs4uWGWoSWhbYPa0mDKE7dCGdu0hOeI49L0XFpzzxx_kn_55lvzPHuufS4YQfjN1fqS0zWNYAK5_G71D8dH4g-q9NOUnM6pv6KJaqnmPvA0ILTZ9DeDI2amUoOpxJcL1fPHtcdO1i8KVT3mbQk6NaOQ4J3Kqw9mVVwe5-eRL4gdg5etvDQ9MYAGN3Jgj48wwgeSF_aPuOeyqfLLps3yE5NKbQjQrpj9PcECpRlk5iTZYAd43cwnS1RjcygmoSK73Nh5cu-_gLaU5eNDsV9Hdjx9_vBUoCtpn3wUj7kFQRhOER8W9_oOzI9vtfHRFM87tz962Y0bC1h7cR4Z97nUCN-WG00F__0m00)
 4. Phân tích ca sử dụng Maintain Employee Information
 - Xác định lớp phân tích ca sử dụng Maintain Employee Information
    - PayrollAdministrator : Đại diện cho người quản trị có quyền duy trì và quản lý thông tin nhân viên.
       - Nhiệm vụ:
           + Thực hiện các tác vụ như thêm mới, cập nhật và xóa thông tin nhân viên.
       - Thuộc tính:
           + adminId: Mã quản trị viên.
           + name: Tên quản trị viên.
       - Quan hệ:
           + Tương tác với lớp EmployeeManagementSystem để gửi các yêu cầu quản lý nhân viên.
     - EmployeeManagementSystem: Chịu trách nhiệm xử lý các yêu cầu liên quan đến quản lý thông tin nhân viên như thêm, cập nhật, và xóa thông tin.
       - Nhiệm vụ:
           + Nhận và thực thi các yêu cầu quản lý từ PayrollAdministrator.
       - Thuộc tính:
           + employeeList: Danh sách tất cả các nhân viên hiện có trong hệ thống.
       - Quan hệ:
           + Nhận yêu cầu từ PayrollAdministrator.
           + Gọi lớp EmployeeDatabase để lưu trữ và quản lý dữ liệu nhân viên.
    - Employee: Đại diện cho thông tin của từng nhân viên trong công ty.
       - Nhiệm vụ:
           + Lưu trữ và cung cấp thông tin chi tiết của nhân viên.
       - Thuộc tính:
           + employeeId: Mã nhân viên (được hệ thống tự động tạo).
           + name: Tên nhân viên.
           + employeeType: Loại nhân viên (theo giờ, lương cố định, có hoa hồng).
           + address: Địa chỉ nhận thư.
           + socialSecurityNumber: Số an sinh xã hội.
           + taxDeductions: Khấu trừ thuế tiêu chuẩn.
           + otherDeductions: Các khấu trừ khác (401k, bảo hiểm y tế).
           + hourlyRate: Lương theo giờ (dành cho nhân viên theo giờ).
           + salary: Lương cố định (dành cho nhân viên hưởng lương cố định và có hoa hồng).
           + commissionRate: Tỷ lệ hoa hồng (dành cho nhân viên có hoa hồng).
        - Quan hệ:
           + Được quản lý bởi EmployeeManagementSystem.
     - EmployeeDatabase: Chứa dữ liệu nhân viên và quản lý truy cập đến dữ liệu đó.
         - Nhiệm vụ:
            + Lưu trữ và cung cấp dữ liệu nhân viên theo yêu cầu từ EmployeeManagementSystem.
          - Quan hệ:
             + Cung cấp dữ liệu cho EmployeeManagementSystem.
 - Biểu đồ sequence
    ![ClassSequence](https://planttext.com/api/plantuml/png/r9InIiD07CRtUue_dNGetJj8GzD1i19eXpgUbwC99DUGN8ePfRDWPnUhY5WG19sQeSC5toDFu2jurrHpnhRKqGmvkFjz_tpVbv2FTDcAE0vvx7i84puAmS99EF8ym_PTvaOyn6eJHs0PA92WIzm0CmwrZXzueuJIBcPuI7tAU2-9EFLh2kvqUvjf4tDyZYDQKEPcg3X4o3AWVgHcDQ7jvEaL0oAN9m8icx0X7FGTCVSRqCuNpm4mHowy0GFnYWyHzZYiZkM-k6CmTiMS8P2N7AUcMaOJpiGy1f8l7kD27G1tn9kSp5tsIwURYIKZTGyx1Ui7TSmcdBo_n3jH4-fVmmTYHWex3BorxfOvG9Iwca1pGjVb7TlWv-cDYwWNqH_T_AsASbur_kb6G8yh3INxvks7-U8UndbwkM_xUgHIKZMn1TkxUrBHb-zWLQpwpFvpePfLFNLIshwG2QjETVJxN3EQNOkPxCcMVcF8fdawqR0jHMTJJREYARDHIzxKJ-aJ003__mC0)
 - Biểu đồ lớp mô tả lớp phân tích
    ![ClassDiagrams](https://planttext.com/api/plantuml/png/Z9CxJWCn48RxFOLBA7A124L12aKaG42um6Gzx5ho8xB74HQYvXxGqK11HOGeLk8UEG5Nm9ja8xp92bou-FvvU_oz-1mw0ajUoIoNu1oxW62DbCTS2IqSMI1ZsLt6wWCr7FC-cv0LkbX33GfJea13WITg9ar07EiRSt2OtMUR10q_Mrafr3G9Zb0rIN2ZdyRiVLRVHutBe2c3DoG6NY4_uq3OfXmb9dIdY7RIlvjhBA_3hAN4iYmwbq9dSW5oWhctWiAvLrEqgGN1xGYvpqaO7Pr7naybhYL39TekiJJUod0Lsqwv0masf2mtIWddOf34VcSS8o2OWjkEnS6y_OuhRZ4sW2rjTuPxdw7JDbQpT_bwlK7tqlJPfL--Fsacgmz6PVMc2qP2PvqElwDjsurxzlNg6TdbueNn-f9YkNZm_mkJ5g7Bwb6pkQYUTJP4pUklzGC00F__0m00)
 5. Phân tích ca sử dụng Maintain Purchase Order
 - Xác định lớp phân tích ca sử dụng Maintain Purchase Order
    - CommissionedEmployee: Đại diện cho một nhân viên làm việc theo hoa hồng, có thể tạo, cập nhật hoặc xóa đơn hàng mua.
       - Nhiệm vụ:
           + Xác thực và cấp quyền truy cập vào đơn hàng mua, khởi tạo các thao tác liên quan đến đơn hàng.
       - Thuộc tính:
           + employeeId: Mã định danh duy nhất cho nhân viên
           + name: Tên của nhân viên
           + commissionRate: Tỷ lệ hoa hồng của nhân viên
       - Quan hệ:
           + Quan hệ một-nhiều với PurchaseOrder (Đơn Hàng Mua).
     - PurchaseOrder: Đại diện cho một đơn hàng mua do nhân viên hoa hồng tạo, chứa thông tin về việc mua hàng của khách hàng.
       - Nhiệm vụ:
           + Lưu trữ thông tin về mỗi đơn hàng, cho phép tạo, chỉnh sửa và xóa đơn hàng khi cần.
       - Thuộc tính:
           + purchaseOrderId: Mã định danh duy nhất cho đơn hàng
           + date: Ngày tạo đơn hàng
           + status: Trạng thái hiện tại của đơn hàng (ví dụ: "open" - mở, "closed" - đóng)
           + customerContact: Người liên hệ từ phía khách hàng
           + billingAddress: Địa chỉ thanh toán cho đơn hàng
           + productDetails: Chi tiết sản phẩm được mua
       - Quan hệ:
           + Quan hệ nhiều-một với CommissionedEmployee.
    - SystemInterface: Đại diện cho giao diện mà nhân viên sử dụng để tương tác với hệ thống lương để duy trì các đơn hàng mua.
       - Nhiệm vụ:
           + Nhận đầu vào từ nhân viên, hiển thị thông tin, và gửi lệnh đến lớp PurchaseOrder để thực hiện các thao tác.
       - Thuộc tính:
           + currentUser: Nhân viên hiện đang đăng nhập.
        - Quan hệ:
           + Quan hệ một-một với CommissionedEmployee trong phiên đăng nhập.
     - PurchaseOrderController:  Là trung gian giữa giao diện hệ thống và lớp PurchaseOrder, xử lý và xác nhận yêu cầu.
         - Nhiệm vụ:
            + Quản lý logic cho việc tạo, cập nhật, và xóa đơn hàng, bao gồm xác thực và kiểm tra quyền hạn.
         - Thuộc tính:
            + purchaseOrderId
         - Quan hệ:
             + Quan hệ tập hợp với PurchaseOrder.
 - Biểu đồ sequence
    ![ClassSequence](https://planttext.com/api/plantuml/png/x5VBQjj05DthAoxPTDKVoA84d904Gbge5yboB4sheTB8Z4R5NeOiInPTTT5DJIY5ba0XNKcKB2RaF-OB-WkzafDQCtfOibtQGhqmM3Ftp9rpppbOFxARdLWI8PCmS8Wh8m63A0nP7BE8Ksyl70VHb59dZ5kOoyQ4ItW-ZIKD3xcauWLnpRLdYN1z4jEdmgDY474feY2WedcFiR9B91dXYl5mJuX8713kvJZE8nZgT1R1xTkx6GTVVU0l8TJPU-RKzGsFdzZjmZOCV9rTSDXgGDfox99Qb0EcitCE4i7Um2Z_aM1z-YM1gVgSWAlJJmbmNwTNOzoalY6yPBmEkxRpRJXTm2pgo-tskFAntOU1KzDJmo0HQbzdLwm9gQdCHaISfZcQ-seAznLMXEeI3dV1IwO5nnzbjUv1JLXoTFSrCVhyjTPwrHCrS-SZv13O42rNhV9VHfB5nMMEueERqzX358RgxaceSeWs6HG3BuwKAuhcmITDK1sDSbgnWzdpQfQeX-hjYEMjB7D2oUrk4-SjMYcfT2XGpPCaLxCnK-dJ21ljADgXqEablDRPsGPCQiYjUtfq4U_QcMR8yhSaMtcU7MVOQBl-YTFrzFQqSIsMrWwTUtv6oWun39qJTKtM31iRud_8M24piJd-Py9boN-elonUoYQgSFv7HbXnL_zCoKzUFKkAlZUT8LNGF4YGCWZKTmXqzeu1r-aDagUk7H98E2gUlV8ng-j5xG1-McvPVgMOp-U2mSGuie0mzdKMS76h1SW6A9g3KUuvpWv-v-zgFm400F__0m00)
 - Biểu đồ lớp mô tả lớp phân tích
    ![ClassDiagrams](https://planttext.com/api/plantuml/png/f5LBRjim4Dth5DpL1H9ahqMH8avGBueMS2z0YwEO03_ApCY1KVHaNVH8lK8fKb95cp6CrWj29D_ytXkEV__yTKyiaNjhgdTY3Qrs81eZYO34g-QzaCoeTps7lNHAME2zLrHL4IGUlBMQI7i7wj5snXy1nFTA33yOzvjrBRJZTEYaXLfiWq_td4uQ1CdmjSTcBmc-e09SlQ_5mMkL07sdpW1-M4V76LY1WMl0FwOAjaTYi1l7WArivkILfix8uvD7ksh3yktOpNbd0H5UUY3UkDRdQHCu5KzrM8gcOum7xrgDLd9WSMM1I3wNGutuHqIFdnDk1OlDgT5SOqP72CVeZG6SQYqf43bRIvOBfndYEcrkHCdHVyYLGQS2bXPZIJsnjwbOsN3USJjjJDXyL0e3SVbTXrxr3Q-1fJOdTrCfWUXX7MMMXxzDk_FUW7HZ3adNRG2ipkeO6Dc5EgOIGhfOuk64zTCO224_E5nciA3R5RndSVvDvyd5N7LitKzXZYowhzJ1wMOVWT5cIU0yfn1CV3Iqrns97V0hW9kcLrKSJRUt7yvUV2tw0NzwF43VUZYrQAGnLBrrVsOxMCHNHZV2UgLRFNmb5IwxcHkbJZqIp2RHmsVIPU5gXbzEFxZeqT7Kev76kwX4aOTCjx5uuLtIhifkomnFyQA168TSCLHHjbeupv6q8IhrJHCyX9OR4wZkmwmT_iB-0000__y30000)
 6. Phân tích ca sử dụng Run Payroll
 - Xác định lớp phân tích ca sử dụng Run Payroll
    - PayrollSystem: Lớp chính quản lý quá trình chạy lương và xử lý tất cả các tác vụ liên quan đến việc tính toán và phân phối tiền lương cho nhân viên.
       - Nhiệm vụ:
           + Quản lý quá trình trả lương cho nhân viên, tính toán và tạo giao dịch thanh toán (séc hoặc chuyển khoản).
           + Xử lý sự cố hệ thống ngân hàng (nếu có).
       - Thuộc tính:
           + payrollDate: Date
           + employeesToPay: List<Employee>
       - Quan hệ:
           + PayrollSystem giao tiếp với BankSystem
           + PayrollSystem có thể liên kết với PayrollAdministrator
           + PayrollSystem sử dụng Employee, Timecard, PurchaseOrder, Paycheck, BankTransaction để thực hiện các tác vụ tính toán và trả lương.
     - Employee: Lớp đại diện cho các nhân viên trong hệ thống trả lương, chứa thông tin về lương, các khoản khấu trừ, và phương thức thanh toán.
       - Nhiệm vụ:
           + Cung cấp thông tin về thời gian làm việc, đơn hàng và phương thức thanh toán.
       - Thuộc tính:
           + employeeId: int
           + name: String
           + paymentMethod: PaymentMethod
           + salary: Decimal
           + hourlyRate: Decimal
           + commissionRate: Decimal
       - Quan hệ:
           + Employee có thể có nhiều Timecard và PurchaseOrder
    - Timecard:  Lớp lưu trữ thông tin về thời gian làm việc của nhân viên theo ngày và dựa trên các dự án.
       - Nhiệm vụ:
           + Ghi nhận số giờ làm việc và tính toán lương.
       - Thuộc tính:
           + employeeId: int
           + dateWorked: Date
           + hoursWorked: Decimal
           + chargeNumber: String
        - Quan hệ:
           + 
     - PurchaseOrder: Lớp quản lý thông tin về các đơn hàng được tạo bởi nhân viên có hoa hồng để tính toán hoa hồng.
         - Nhiệm vụ:
            + Ghi nhận đơn hàng và tính toán hoa hồng cho nhân viên có hoa hồng.
         - Thuộc tính:
            + purchaseOrderId: int
            + customerName: String
            + totalAmount: Decimal
            + saleDate: Date
         - Quan hệ:
      - Paycheck: Lớp lưu trữ thông tin về các séc trả lương cho nhân viên.
         - Nhiệm vụ:
            + Tạo séc trả lương hoặc giao dịch ngân hàng cho nhân viên.
         - Thuộc tính:
            + paycheckId: int
            + employeeId: int
            + amount: Decimal
            + paymentDate: Date
            + paymentMethod: PaymentMethod
         - Quan hệ:
       - BankTransaction: Lớp đại diện cho giao dịch ngân hàng liên quan đến việc chuyển tiền cho nhân viên qua hình thức chuyển khoản.
         - Nhiệm vụ:
            + Xử lý giao dịch chuyển tiền cho nhân viên qua ngân hàng.
         - Thuộc tính:
            + transactionId: int
            + employeeId: int
            + amount: Decimal
            + bankAccount: String
         - Quan hệ:
      - BankSystem: Lớp xử lý các giao dịch với hệ thống ngân hàng, bao gồm việc chuyển tiền cho nhân viên qua chuyển khoản.
         - Nhiệm vụ:
            + Thực hiện các giao dịch chuyển tiền cho nhân viên qua chuyển khoản ngân hàng.
         - Thuộc tính:
            + bankStatus: String
         - Quan hệ:
      - PayrollAdministrator: Lớp đại diện cho người quản lý hệ thống trả lương, có nhiệm vụ giám sát và đảm bảo quá trình trả lương diễn ra suôn sẻ.
         - Nhiệm vụ:
            + Quản lý quá trình trả lương và xử lý báo cáo.
         - Thuộc tính:
            + adminId: int
            + name: String
         - Quan hệ:
             + 
 - Biểu đồ sequence
    ![ClassSequence](https://planttext.com/api/plantuml/png/d9J1Qjj048RlUefvWRv03oNGG19QGWCczAfkZ7UfkbBabKdEEUJGItpCeJIk2OMsfcwJ4D0ISbZZzzWdo2lq7rN4acAP93winUxED__yCzATlLthcp0rsQSe28M9Kzh9V3xMdTJRpxlA_T1lvzFvIFU21BUKK4ce3MrwUzoHtWvr3nVpyR8xsz9zqmMXjesmt7Bi5xMXmlhPx0IKJNVM8BsJokUtMMicSE9ro1LokuUS3m4LkPKRGKkbzE9LMu7qajvWzwkYsT3RKspiPuTaKlTBI_pX8aMbm3R2IdWd1Uu0iiuDQVQF1YoCXC-_wySdM5ZVO1esdrUuJptOJmDtXbeGIB8mfH8AKADPeBtEa09opXFQy_OtHGeoieVW1cZHsNP6LSRpt7CJRaFiW2bT8Y5ZCjx-n6F5q5Ny9TF6R9-FOah-dzKxKUIemiC8qr_S4p8xzFP8qqSPywnneFqZo30c2GY_5KgMpVMz59WSitqu9St7fNFCN1fOjwv6tF1segh4fh8wfaNNUpSIyC7d4rrJDnkwCJTtwkrOq05oKUHkWcxKxvOsxMSXPcS-9NRf-XvYKAYYmGp-9TBzBOjxSkksz2FxrjLxgmQZxNE1ZaXtYOSF3dsHCUn0DLXb-zU1HuHJ5Q_Ca8TpqK8CIu4JxeBwFh_Ip-efxy7emi9gPxd8DIpymVy7003__mC0)
 - Biểu đồ lớp mô tả lớp phân tích
    ![ClassDiagrams](https://planttext.com/api/plantuml/png/h5RDRXCn4BxdANni9KhlArIrz0-aqfOs4bnThrbRsRM3xGr4Y0FYq0EdYWCdf0RK0nMLg0H2IeGuRDNts2VW5HZl_sws3Qt88PiTVsDdllbcF7yclvUrmSg4WTyXFjOQxUAXahw_FzI61kXL1zbFFpMkOKCTPBzJCmtwlXnIghiIt1oqnRMvjvuPbrAC2aMsvToyWmQIkvcT6iNfWEPmlI4L00Cgp9nRd3FVlYd1FWbzM0UFkVnVE2X7WTSQ9Jp0VWhtgA0gHHD6IQ_T9L_DZb0KFEvZqUigB3GcXalHxjW0fVuC2zTF_5CgDp3tGqLh92mi98_5HRJDU3mv3D0WdfmukV5n68y_2-H7lz3pC1eXewAlWi43pCY__7Ov4XuYJ28JZqyC8jOiMFH9e06FJiNTV9zkT6RTP3I2bUZOmaSIaMX4aCUnH6uyUKS007yvWztjlEvaUiZZpAMGC_3GTH0N9ZKA700b-v1HuHMAiQbyH0sJRi9j-PeYDFQn6ZOonMIe_E5Ucl_g0f51mBK6UbiMFMgwqc3_0NZh9rBrg3ithG6pMkon4iWGTDQ2sLHIQwkgnjgCLAs6DXMGXZxG67s75yC5_8md7xabsMRn67oiAqcIS744wKCiEivo2D33nE4831T7yUGjCadUiaHNKjBb0ILOkTUcnDPGIaMrObd9K9DWXfL7jyFWWAfwAejYsnbGPU3i5dfAq1xruAbkJk4cuw3UU7nsFM-c8cO3vZUYA0NGyJcsLN8ga0OYOGFOfxf3XSJTK478ckuebwgYprMDDJf9g8qCgDgUKhgnoai5rU0454wRBRFWgHJZxNbAIhWgf2P1J68hhFUPnchDeMGYwtkLPf-yr-9lrHXkYpgh_6RWinj2tgLlqYAxIIlJqHVIQ8jCnkEVzVucF1jzMN7jR3IQUKwAAKstvEK0DbuX95sf2aXJuNQbFVScaJ-D9sV9rL0DaR1m29sZg8n6c72Du1BJinp1_LBXfS53VGYm0UmRR4BTQFLA4gfrzPgii3LrFKvD0SFRUCxI1QZ-dA1aIKnVTKsUB2__9ezibbbn0ovWC06zog9xO6kSSI-Muz0UxKkLt44rGmeRSFfYNIcfjgIdBIP_-LzpmnreiXJuY7vmT12buu1C-iVBN5W9Qtuy-S1HdqKZWpGNBA6YFYCkB2oLKu9J37Qw1LRSN0uATIkYtfQlXkKzoodQHXkiMSnEDjRfJaNUxS1CrLUTFYq21mbf-3CE7ijGqNQY_Wi00F__0m00)
7. Phân tích ca sử dụng Select Payment Method
 - Xác định lớp phân tích ca sử dụng Select Payment Method
    - Employee : Lớp này đại diện cho thông tin của một nhân viên trong hệ thống
       - Nhiệm vụ:
           + Cung cấp thông tin nhân viên, bao gồm phương thức thanh toán mà nhân viên chọn.
       - Thuộc tính:
           + employeeId: int: Mã định danh nhân viên.
           + name: String: Tên nhân viên.
           + paymentMethod: PaymentMethod: Phương thức thanh toán của nhân viên (pick-up, mail, direct deposit).
           + address: String: Địa chỉ nhận lương nếu phương thức thanh toán là mail.
           + bankAccount: String: Số tài khoản ngân hàng nếu phương thức thanh toán là direct deposit.
           + bankName: String: Tên ngân hàng nếu phương thức thanh toán là direct deposit.
       - Quan hệ:
           + Employee - PaymentMethod
     - PaymentMethod: Lớp này đại diện cho các phương thức thanh toán mà nhân viên có thể chọn: pick-up, mail, hoặc direct deposit.
       - Nhiệm vụ:
           + Lưu trữ thông tin về phương thức thanh toán mà nhân viên chọn.
       - Thuộc tính:
           + method: String: Phương thức thanh toán (pick-up, mail, direct deposit).
           + address: String: Địa chỉ nhận lương khi phương thức là mail.
           + bankAccount: String: Số tài khoản ngân hàng khi phương thức là direct deposit.
           + bankName: String: Tên ngân hàng khi phương thức là direct deposit.
       - Quan hệ:
           + 
    - System:  Lớp này đại diện cho hệ thống quản lý các phương thức thanh toán, giúp người dùng chọn và thay đổi phương thức thanh toán.
       - Nhiệm vụ:
           + Quản lý giao diện người dùng để nhân viên chọn phương thức thanh toán và cập nhật thông tin vào hệ thống.
       - Thuộc tính:
           + Không có thuộc tính riêng biệt trong lớp này.
        - Quan hệ:
           + System - Employee
           + System - PaymentMethod
 - Biểu đồ sequence
    ![ClassSequence](https://planttext.com/api/plantuml/png/Z99DJWCn34RtEOMN8BKNw09LGYoHAYeEO183LlD7uY3DsLXm9Av0CieCcWgcPEcyptwHy_NnkS-2IOgp2hM417SksZ0GgLZBh3cY5pWEMSWjIWSS77cv9taDHgaf1jkRJiCEZcH9poXqjbzNS0xju87U2kLp5guYwzEsn0quPBi1mwbrD1H3PhbMQ0Kweg2UDOs98s_6NEjuCJH3gzQDOly2Q4oYdF_kUaZXdGtDuEIoVDT5gr_mLRydz2T0hKFnBILLzn-IOsgYc-dFZCNsQ-Gn6XI2sBVdLZPz6_mp9tV6GXaxg7sTqpxZDm000F__0m00)
 - Biểu đồ lớp mô tả lớp phân tích
    ![ClassDiagrams](https://planttext.com/api/plantuml/png/f58xRiCm3Drr2et9u0jeA9oXGuSM0Nm2rY9SenRbcbG18yZ9CkH8kKBYsZ8i1-aIRUHxr7lyN4xdd0Kw2QvHPGFC-jMrZUyHzK7fuU4KlrcZQv8nIU3Gw4AwcgenqqBlaEGTvSlVcFjbE3B0sWwPqx9FeEzTMVf0SWzyh5MoR0H3Qq4mqTZyPs1hzA-lhJgggSa4ZPswgNHfuqdJis3Hiw2BIXt-16H9N1JOO2crfqsSk9bt4VqlcezGEeJ7fJSdysQpx6Kr0QFvJvxLP7IWp7oZ7H1KcA3h3o8bHxB3DLq1003__mC0)
II. Viết code Java mô phỏng ca sử dụng Maintain Timecard.
 1. Employee 
    import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

class Employee {
    private String employeeId;
    private String name;
    private Map<String, Timecard> timecards; 

    public Employee(String employeeId, String name) {
        this.employeeId = employeeId;
        this.name = name;
        this.timecards = new HashMap<>();
    }
    public String getEmployeeId() {
        return employeeId;
    }
    public String getName() {
        return name;
    }
    public Timecard getCurrentTimecard(String payPeriod) {
        return timecards.getOrDefault(payPeriod, new Timecard(payPeriod));
    }
    public void addTimecard(Timecard timecard) {
        timecards.put(timecard.getPayPeriod(), timecard);
    }
    public boolean isTimecardSubmitted(String payPeriod) {
        return timecards.containsKey(payPeriod) && timecards.get(payPeriod).isSubmitted();
    }
}
2. Timecard
    import java.util.ArrayList;
    import java.util.HashMap;
    import java.util.List;
    import java.util.Map;
   class Timecard {
    private String payPeriod;
    private Map<String, Integer> chargeNumbers; 
    private boolean submitted;
    private String submittedDate;

    public Timecard(String payPeriod) {
        this.payPeriod = payPeriod;
        this.chargeNumbers = new HashMap<>();
        this.submitted = false;
    }

    public String getPayPeriod() {
        return payPeriod;
    }

    public boolean isSubmitted() {
        return submitted;
    }

    public void enterHours(String chargeNumber, int hours) {
        chargeNumbers.put(chargeNumber, hours);
    }

    public void submit(String date) {
        this.submitted = true;
        this.submittedDate = date;
    }

    public Map<String, Integer> getChargeNumbers() {
        return chargeNumbers;
    }
}

 3. TimecardController
    import java.util.Scanner;
    public class TimecardController {
    private Map<String, Employee> employees; 
    public TimecardController() {
        this.employees = new HashMap<>();
        // Initialize with some employees
        employees.put("E001", new Employee("E001", "John Doe"));
    }

    public void maintainTimecard(String employeeId, String payPeriod) {
        Employee employee = employees.get(employeeId);
        if (employee == null) {
            System.out.println("Employee not found.");
            return;
        }
        Timecard timecard = employee.getCurrentTimecard(payPeriod);
        if (employee.isTimecardSubmitted(payPeriod)) {
            System.out.println("Timecard for this period is already submitted. No changes allowed.");
            return;
        }

        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.println("Enter charge number (or type 'submit' to submit): ");
            String chargeNumber = scanner.nextLine();
            if (chargeNumber.equalsIgnoreCase("submit")) {
                if (validateTimecard(timecard)) {
                    timecard.submit("2024-10-05"); 
                    employee.addTimecard(timecard);
                    System.out.println("Timecard submitted successfully.");
                } else {
                    System.out.println("Invalid timecard. Please check hours.");
                }
                break;
            }
            System.out.println("Enter hours worked for charge number " + chargeNumber + ": ");
            int hours = Integer.parseInt(scanner.nextLine());
            if (isValidHours(hours)) {
                timecard.enterHours(chargeNumber, hours);
                System.out.println("Hours updated successfully.");
            } else {
                System.out.println("Invalid number of hours. Please enter a valid number.");
            }
        }
        scanner.close();
    }
    private boolean validateTimecard(Timecard timecard) {
        int totalHours = timecard.getChargeNumbers().values().stream().mapToInt(Integer::intValue).sum();
        return totalHours <= 40; 
    }
    private boolean isValidHours(int hours) {
        return hours >= 0 && hours <= 24; 
    }
    public static void main(String[] args) {
        TimecardController controller = new TimecardController();
        controller.maintainTimecard("E001", "2024-10-01 to 2024-10-07");
    }
}
