+++
title = 'Truy vấn với Athena'
date = 2024-05-28T22:01:17+07:00
weight = 2
chapter = true
pre = "<b>3.2. </b>"
+++

### Truy vấn với Athena
Truy cập vào bảng điều khiển Amazon Athena để kiểm tra các bảng raw và stage đã được tạo cho đến nay.  
Đầu tiên, với tư cách là quản trị viên Lake Formation, bạn cần cấp cho mình quyền truy vấn các bảng.  
Bước 1: Đi đến các bảng của [Lake Formation](https://us-west-2.console.aws.amazon.com/lakeformation/home?region=us-west-2#tables), chọn từng bảng và cấp tất cả các quyền cho  user hoặc role mà bạn đang sử dụng. Chọn một bảng và nhấp vào Hành động -> Cấp (quyền).  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/113.png) 
Bước 2: Chọn grant  
+ Thêm user hoặc role cho 'WSParticipantRole' với tư cách là quản trị viên nếu bạn tham gia sự kiện AWS (trên tài khoản của bạn, chọn người dùng mà bạn đang đăng nhập), chọn tất cả các đặc quyền cho tất cả các bảng từ cơ sở dữ liệu c360view_raw.
+ Databases: c360view_raw
+ Tables : All tables
+ Table Permission : Select
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/114.png) 
Ngoài ra, bạn có thể thiết lập các đặc quyền cho các bảng sau thay vì cho tất cả các bảng trong cơ sở dữ liệu:  
+ account
+ card
+ crm
+ data
+ gbank
+ sourcemf_sourcemf_public_transactions
Bước 3: Lặp lại việc cấp quyền cho cơ sở dữ liệu stage.  
+ Thêm user hoặc role của bạn, trong trường hợp của tôi là 'WSParticipantRole', với tư cách là quản trị viên, chọn tất cả các đặc quyền cho tất cả các bảng từ cơ sở dữ liệu c360view_stage.
+ Databases: c360view_stage
+ Tables : All tables
+ Table Permission : Select