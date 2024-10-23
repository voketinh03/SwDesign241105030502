#Lab1
 # 1. Phân tích kiến trúc
- Kiến trúc dịch vụ: kiến trúc 4 lớp
  + Giai thích lý do lựa chọn:
     + Tính tách biệt mỗi lớp, giúp quản lý và phát triển hệ thống dễ dàng.
     + Khả năng mở rộng dễ dàng bổ sung các tính năng mới mà không làm gián đoạn các phần khác của hệ thống.
     + Bảo trì và kiểm soát lỗi tốt.
     + Hệ thống dễ dàng tích hợp với các dịch vụ và hệ thống bên ngoài.
   + Ý nghĩa:
     + Presentation Layer: Kết nối giữa người dùng và hệ thống, cung cấp giao diện thân thiện.
     + Business Layer: Thực hiện quy trình nghiệp vụ chính, đảm bảo tính chính xác và đáng tin cậy trong việc tính toán lương và xử lý hoa hồng.
     + Service Layer: Quản lý giao tiếp giữa lớp nghiệp vụ và lớp truy cập dữ liệu
     + Data Access Layer: Gíup truy cập và quản lý cơ sở dữ liệu, thực hiện lưu trữ và truy xuất thông tin.
   + Biểu đồ package mô tả kiến trúc.
 ![package](https://planttext.com/api/plantuml/png/P951YW9134NtEKNm07q05s8xin5S23AhmKMeoMXXMIr9McXaJZOBZ-GLhB8LhJQhokCb_52N__DKZSJQVG3GdOyeZJAOjy2uf4wQ473LgV4UQt5RR-oi5GOuaDlH9ad2oj78V1CNrB7W2J3LzvUczpmQooyvNiFVSsRMge-iMlWFY8jcurtXhrYEtd6XtndUO65_ab7jt71_njZpbw7t-5Kr6GGSuoWTeoCeSHQBPCdxe12IME3i3JCbjM_pMfXo_Ca_S0K00F__0m00)
# 2.  Cơ chế phân tích
- Đề xuất cơ chế và giải thích lý do
  + Xác thực người dùng
    + Giari thích: Đảm bảo nhân viên hợp lệ mới có quyền truy cập vào hệ thống và thục hiện quyền chỉnh sửa.
  + Phân quyền
    + Giari thích: Đảm bảo nhân viên chỉ có quyền truy cập và chỉnh sửa thông tin mà họ có quyền.
  + Quản lý dữ liệu nhân viên
    + Giai thích: Quản lý thông tin nhân viên.
  + Tính toán lương
    + Giai thích:Cần có cơ chế tự động tính toán lương cho từng nhân viên dựa trên giờ làm việc và doanh số bán hàng.
   + Đồng bộ hóa dữ liệu
     + Giai thích:Đảm bảo rằng dữ liệu trên các máy tính cá nhân của nhân viên được đồng bộ với cơ sở dữ liệu trung tâm.
