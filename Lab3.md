# Lab3
# 1. Subsystem context diagrams
   -  Biểu đồ ngữ cảnh của hệ thống con BankSystem
     ![Diagram](https://planttext.com/api/plantuml/png/h5BBJiCm4BpxArQzK2JI3wYig6h58RUAdZWQPzjQSRoHxQX4m9Tnu9Fu1UpcWKivDeTai-FPcPta-_DhvRomlgqrh8MfTftpME_Q5tSkcAkKQOGLDLYKNfY3HdXZ4AwraDN1KclA3McodBkH18sbroxFuHcrfXFxOEmEDcIy9GqRBPnZCjvXAxhGqWEaqGBdidy9x5u6mBPcE3Y_xsSLngFT2ubCZHKKl-udPeaDEUNd8l3b4MK5InZB1mXSYgJGZ8_2xCdMmYioWyoK0cpZGeFfHEU_dM-a_MYyyWgJfFeXd6D4Wb9Y9w6d1yAO9zJdjZkgnh7hlBEIJYRBBz9RmgnKyMkFExWPIt7-lbWaALnWb6MJrolWZrMsGbE6_uxz0000__y30000)
       - Giari thích thành phần biểu đồ trên
          + Mục đích: Quản lý hệ thống trả lương, bao gồm việc gửi tiền lương vào tài khoản ngân hàng của nhân viên.
          + Thành phần:
             + PayrollController: Lớp điều khiển chính, gọi phương thức runPayroll() để bắt đầu quy trình trả lương.
             + IBankSystem: Một interface, đóng vai trò trung gian giữa PayrollController và hệ thống ngân hàng thực tế.
             + BankSystem: Lớp cụ thể thực hiện việc gửi tiền (proxy của hệ thống ngân hàng).
             + Paycheck và BankInformation: Các thực thể mô tả chi tiết về phiếu lương và thông tin ngân hàng.
          + Quy trình:
             + PayrollController gọi IBankSystem để gửi tiền.
             + IBankSystem chuyển yêu cầu đến BankSystem, sử dụng thông tin về phiếu lương và tài khoản ngân hàng.  
   -  Biểu đồ ngữ cảnh của hệ thống con PrintService
     ![Diagram](https://planttext.com/api/plantuml/png/b5AzJiCm4Dxz5ASkb25zW2gAAW93cH2T65td6gmwlc1VA1NmP0my4g_0XQGHYRhKW-NJtVTtyi_Nzogo3jnK3Xw2zRp1y6eDRffjF4R6IiMzzRKEkeA0XhKl7SAx0ZatskpBG8qlSd8KqZIUG507UZjc6JoXStHGdqfTGKwU0pd8dOvHcVQ6Mp9DXPxxdiC0QMgwGk2T3eZoIuEH_mpEhpkwjMSCEsrGsTCBrlyZ36YnLTaEV4_RUT5hmdAGxoc7qB8AyTzx776U2tcnpfrdonQdIn1oR3l2sKuzejDioSTdMqTrPbD9GGUVP9FKIvX5z0KCyZiAObKch2zdQZoSVYmMeu2JFYN9O4-jX5R-YVe5003__mC0)
  - Giari thích thành phần biểu đồ trên
          + Mục đích: Quản lý việc gửi tài liệu đến dịch vụ in.
          + Thành phần:
             + DocumentController: Lớp điều khiển yêu cầu in, thực hiện phương thức requestPrint().
             + IPrintService: Interface cho dịch vụ in, định nghĩa phương thức submitPrintJob(document).
             + PrintService: Lớp thực thi thực tế của dịch vụ in (proxy).
             + Document: Thực thể biểu diễn tài liệu cần in.
          + Quy trình:
             + DocumentController gửi yêu cầu đến IPrintService.
             + IPrintService chuyển tài liệu đến PrintService để xử lý.

   -  Biểu đồ ngữ cảnh của hệ thống con ProjectManagementDatabase subsystems
     ![Diagram](https://planttext.com/api/plantuml/png/n5DBRi8m4Dtx52Cs1QdX0CX22EWYYqfLMNKv94DmSUp8dWXGsvDrqIFr2dM8Gp-4TRsmRCzxC-_Do9_l7pFFwBWkDJmu-qmPtwF1Waeol4J6DNfQrMj_z4oby3jbAdHOWWj8D8KcU14GrXopNU5iRVA5rTP9wJiILCuUZjCfF97MTY_UXBY1XJNih8Q5Hkz5rknT_HZIv43AhBq4Tbi6e3p9YzZXg4sN6YQtmOo4wawGNlgPdxDiYBDj13GsXrLxJfSmwOIaor54rrMEtDLSCNBj-mctu4_HyBPYfqmHzPqxs40Fnz-6BniEVUtx9-btXXKh-ZEam9MIcb2G5aDjzf_lWVv86bbPuxUgyk9on4bkzoQPzazh0eEJM_A09ezUF8GT1wAN8L_7u-jzxUVO9FcsTHtIsXCpCdduBU8B003__mC0)
   - Giari thích thành phần biểu đồ trên
          + Mục đích: Quản lý dữ liệu và trạng thái của các dự án.
          + Thành phần:
             + ProjectController: Lớp điều khiển, thực thi phương thức manageProject() để quản lý dự án.
             + IProjectManagementDB: Interface kết nối đến cơ sở dữ liệu dự án, cung cấp các phương thức như:
                  + fetchProjectData(): Lấy thông tin dự án.
                  + updateProjectStatus(): Cập nhật trạng thái dự án.
             + ProjectManagementDatabase: Lớp thực thi (proxy) để thao tác với cơ sở dữ liệu thực.
             + ProjectID và Status: Các thực thể biểu diễn thông tin dự án và trạng thái của dự án.
          + Quy trình:
             + ProjectController gọi IProjectManagementDB để lấy hoặc cập nhật dữ liệu dự án.
             + Interface này tương tác với ProjectManagementDatabase để thực hiện công việc.
# 2. Analysis class to design element map
     Dưới đây là ánh xạ các lớp phân tích từ sơ đồ trên sang các phần tử thiết kế của hệ thống:
  ![image](https://github.com/user-attachments/assets/7244fa5f-2876-4a63-a838-1cfd56d520f6)
#3. Analysis class to design element map
### Mappings
- **LoginForm** -> `LoginForm`
- **MaintainTimecardForm** -> `MainEmployeeForm`
- **TimecardController** -> `TimecardController`
- **PayrollController** -> `PayrollController`
- **PayCheck** -> `PayCheck`
- **BankService** -> `BankService`
- **SystemClockInterface** -> `SystemClockInterface`
- **PayrollController** -> `PayrollControllerImpl`
- **Employee** -> `EmployeeEntity`
- **Timecard** -> `TimecardEntity`
- **Payroll** -> `PayrollProcessor`
- **BankTransaction** -> `BankTransactionProcessor`
- **PaymentUI** -> `PaymentUIComponent`
- **PrintService** -> `PrintServiceProcessor`
#4. Design element to owning package map

| Design Element         | "Owning" Package                          |
|-------------------------|-------------------------------------------|
| LoginForm              | Middleware::Security::GUI Framework       |
| MainEmployeeForm       | Applications::Employee Activities         |
| TimecardForm           | Applications::Employee Activities         |
| MainApplicationForm    | Middleware::Security::GUI Framework       |
| TimecardController     | Applications::Payroll                     |
| SystemClockInterface   | Applications::Payroll                     |
| PayrollController      | Applications::Payroll                     |
| Paycheck               | Business Services::Payroll Artifacts      |

#5. Architectural layers and their dependencies
![diagram](https://www.planttext.com/api/plantuml/png/V5HBJiGm3Dtd55OthBW02yHV804Q0HS8gHaYKZiuAQX2d8m5H-8AE4Ddffqfi-d7By_FzhFoy_LzbBALt3R1f1TFqOfj8EKke3x5kmqaUCBSHGIM_Cp6HEjUx1oXcWacf6opPu9hsw5Ky64073UHIH6uvhcd2vPc5BsndiwR6BX3N82VWwJ7CGRlTkISsKuuX5EcNDue8_J1D-Yir0DucFsaJTfDId2FykOTffqQ_Q4HTClPF_K5Jk5t67LEIsIeVSQDDhvJS2QiDIKUzxISrJbbdxjHpYjw4gkcjMgQu7JkCvljeqtuNxN9PvP5sZqu5k7t18BnprjFSwWn8jL8pcCoAqTXV_zmsmiuWEhIKXrqictIVrsYDbTcq_85Uzkh_-ZREWFrlg_2xUUdxFY7LMP2f70dR1oAqm1EA_tbmO7uoh72FcNre5U6e9DobPaIAlongOLzWTaz0_PngDMsoepMQK7SiBCmImXUMvHkLUgwhi9PsroEt-k7zkXAjMkL7jyXKKBA8a9NkgcCETB5A9V5Bm000F__0m00)
