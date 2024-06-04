+++
title = 'Trực quan hoá với Quicksight'
date = 2024-05-28T22:01:17+07:00
weight = 6
chapter = true
pre = "<b>5. </b>"
+++

### Chương V

# Trực quan hoá với Quicksight
Để khám phá dữ liệu bằng các bảng điều khiển, bạn có thể sử dụng [Amazon Quicksight](https://aws.amazon.com/quicksight/?nc1=h_ls). Chúng ta sẽ sử dụng dữ liệu đã được xử lý trước đó. Dưới đây là kiến trúc: 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/160.png) 
Bước 1: Đăng ký dịch vụ Amazon Quicksight.  
Nếu bạn chưa có tài khoản Amazon Quicksight được kích hoạt trong tài khoản AWS của bạn, làm theo các bước sau [đây](https://www.google.com/url?q=https://docs.aws.amazon.com/quicksight/latest/user/setup-new-quicksight-account.html&sa=D&source=docs&ust=1716835727056335&usg=AOvVaw2jemETLlPbWH9UrXj9Ptfk).  
Bước 2: Đến [Quicksight console](https://quicksight.aws.amazon.com/sn/start) Bạn cần đến vùng của bạn để thiết lập này.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/161.png) 
Bước 3: Kiểm tra tài khoản của bạn và nhấp vào Sign UP for Quicksight  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/162.png) 
Bước 4: Nhập thông tin của bạn  
+ Thay đổi vùng của bạn (trong trường hợp của tôi là Oregon) - làm điều này đầu tiên
+ Email của bạn
+ Tên Tài khoản Quicksight: ví dụ tên của bạn.
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/163.png) 
Bước 5: Chọn S3
+ Chọn S3: các bucket log, Analytics, Stage và Raw
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/164.png) 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/165.png) 
Bước 6: Kiểm tra Athena.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/166.png) 
If you use another bucket for Athena results, please add it to your selection.  
Bước 7: Bấm Finish.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/167.png) 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/168.png) 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/169.png) 
Click in go quicksight and check the news about quicksight and then click in Close  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/170.png) 
P/S: Kiểm tra xem bạn có ở đúng vị trí không, trên người dùng ở góc trên bên phải.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/171.png) 
Bước 8: Click on Datasets -> New dataset.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/172.png) 
Bước 9: Chọn Athena cho nguồn Data.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/173.png) 
Bước 10: Tạo nguồn dữ liệu Athena mới.  
Tên nguồn dữ liệu: c360. Để Athena workgroup là primary, và nhấp vào Tạo nguồn dữ liệu.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/174.png) 
Bước 11: Chọn bảng.  
Cơ sở dữ liệu: chứa các bảng dữ liệu: c360view_analytics  
Bảng: chứa dữ liệu bạn có thể trực quan hóa: ví dụ như c360_analytics  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/175.png) 
Nhấp vào Chọn.  
Bước 12: Chọn Truy vấn trực tiếp dữ liệu của bạn -> Trực quan hóa.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/176.png) 
Bước 15: Chọn Bảng tương tác và đóng gợi ý của Amazon Q.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/177.png) 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/178.png) 
Bước 13: Xây dựng bảng điều khiển của riêng bạn  
Từ danh sách trường, chọn customer và ngành  
Từ loại trực quan, chọn biểu đồ tròn  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/179.png) 
Bước 14: Nhấp vào + Thêm, sau đó nhấp vào Thêm trực quan mới.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/180.png) 
Bước 15: Chọn các trường sau.  
+ khu vực
+ doanh số
+ Loại trực quan là biểu đồ thanh dọc
Bước 16: Nhấp vào Field wells để kiểm tra mọi thứ có ở đúng vị trí không.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/181.png) 
Bấm nút "Next" để sang phần tiếp theo  