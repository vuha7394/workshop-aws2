+++
title = "Kết nối tới Database"
date = 2024-05-28T22:01:17+07:00
weight = 3
pre = "<b>2.3. </b>"
+++

### Kết nối tới Database

Tạo một kết nối cho cơ sở dữ liệu quan hệ làm nguồn.  
Bạn sẽ cần kết nối này để tạo một công việc AWS Glue và chúng tôi sẽ sử dụng thông tin đăng nhập từ AWS Secrets Manager để kiểm tra tên người dùng/mật khẩu.  
Vì vậy, hãy vào AWS Secrets Manager và nhấp vào "c360view-secret".  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/49.png) 
Nhấp vào "Retrieve secret value" để lấy thông tin đăng nhập  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/50.png) 
Lưu thông tin đăng nhập vào trình soạn thảo văn bản của bạn, bạn sẽ cần mật khẩu này trong các bước tiếp theo:  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/51.png) 
Bước 1: Đến [AWS Glue](https://us-west-2.console.aws.amazon.com/glue/home?region=us-west-2#catalog:tab=connections) -> Data catalog -> Connections, và kiểm tra xem có kết nối tên "sourcemf" tồn tại hay không. Nếu có, chuyển đến bước 7 để kiểm tra kết nối
:  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/52.png) 
Nếu bạn không thấy tên kết nối "sourcemf", nhấp vào "create connection", chọn "Amazon Aurora" và sau đó nhấp vào "Next".  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/53.png) 
Bước 2: Thiết lập quyền truy cập, chọn Instance sourcemf của bạn:  
+ Instance: Giống như trong secrets manager -> username
+ Database name: Giống như trong secrets manager -> username
+ Credential type: Username and Password
+ Username: Giống như trong secrets manager -> username
+ Password: Giống như trong secrets manager -> password
Network Options:  
VPC: Giống như cơ sở dữ liệu
+ Subnet: Giống như cơ sở dữ liệu
+ Security Group: Tên: c360view-c360-Access và c360view-RDS-Source
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/54.png) 
Bấm Next.  
Bước 3: Đặt tên kết nối của bạn là "sourcemf"   
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/55.png) 
Bấm Next.  
Bước 4: Kiểm tra lại các thông số và bấm tạo kết nối  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/56.png) 
Bước 5: Kiểm tra nếu kết nối của bạn xuất hiện  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/57.png) 
Bước 6: Bấm vào kết nối theo mũi tên  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/58.png) 
Bước 7: Kiểm tra kết nối: Chọn "sourcemf" -> bấm Test Connection  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/59.png) 
Chọn IAM Role and xác nhận  
IAM role: Glue-role-c360view  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/60.png) 
Bước 8: Bạn sẽ thấy kết nối sourcemf thành công:  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/61.png) 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/62.png) 
Nếu có lỗi hãy kiểm tra kỹ lại 1 lần nữa.  
Bấm nút "Next" để sang phần tiếp theo  