+++
title = 'Thiết lập Lake Formation'
date = 2024-05-28T22:01:17+07:00
weight = 2
pre = "<b>2.2. </b>"
+++

### Thiết lập Lake Formation
**Thiết lập Data Lake với Lake Formation**  
Bước 1: Đến [Lake Formation console](https://us-west-2.console.aws.amazon.com/lakeformation/home?region=us-west-2) , chọn Get Started:
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/40.png) 
Bước 2:Kiểm tra xem các bucket bắt đầu bằng “c360view” (raw, stage và analytics) có nằm trong vị trí Lake Formation hay không.  
Thêm các bucket bắt đầu bằng “c360view” [data lake locations](https://us-west-2.console.aws.amazon.com/lakeformation/home?region=us-west-2#register-list) cho Lake Formation, chỉ ra rằng chúng là một phần của hồ dữ liệu của bạn:  
+ c360view-us-west-2-your_account_id-raw
+ c360view-us-west-2-your_account_id-stage
+ c360view-us-west-2-your_account_id-analytics
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/41.png) 
Nếu bạn không thấy 3 bucket này, bạn có thể thêm chúng bằng cách nhấp vào Dashboard -> "Data Lake Setup" -> "Stage 1".  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/42.png) 
Thêm 3 buckets and nhấn "Register location":
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/43.png) 
Bước 3: Trên bảng điều khiển Lake Formation, vào Permissions -> Administrative roles and tasks, sau đó cấp quyền Data Lake Administrators và database creators cho người dùng hoặc vai trò của bạn.  
+ Thêm người dùng hoặc vai trò (nếu bạn sử dụng một vai trò giả định để đăng nhập) bạn đang sử dụng làm quản trị viên data lake, để người dùng của bạn có thể quản lý các khu vực lưu trữ, cơ sở dữ liệu và bảng.
+ Khi sử dụng AWS Event trong Workshop Studio, cấp quyền Quản trị viên cho WSParticipantRole.
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/44.png) 
Thêm người dùng WSParticipantRole của bạn làm quản trị viên data lake  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/45.png) 
Cấp cho người dùng WSParticipantRole, Glue-role-c360view và c360vEMRExecutionRole quyền tạo cơ sở dữ liệu với các quyền có thể cấp:  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/46.png) 
Và cấp quyền tạo database creator cho các vai trò sau:  
+ Glue-role-c360view
+ c360vEMRExecutionRole
+ WSParticipantRole
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/47.png) 
Bước 4: Chọn tất cả các quyền (All privileges)
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/48.png) 
Bấm nút "Next" để sang phần tiếp theo  