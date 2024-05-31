+++
title = 'Chuyển đổi nâng cao'
date = 2024-05-28T22:01:17+07:00
weight = 5
chapter = true
pre = "<b>4. </b>"
+++

## 4. Chuyển đổi nâng cao
Bây giờ bạn sẽ thực hiện các chuyển đổi nâng cao hơn bằng cách sử dụng AWS Glue job, đầu tiên là sử dụng python shell, sau đó với Pyspark  
![360 customer view](/images/assets/115.png) 
AWS Glue là một dịch vụ trích xuất, chuyển đổi và tải (ETL) được quản lý hoàn toàn, giúp dễ dàng chuẩn bị và tải dữ liệu của bạn để phân tích. Bạn có thể tạo và chạy một công việc ETL chỉ với vài cú nhấp chuột trong trình chỉnh sửa trực quan của AWS Glue.  
Glue sẽ tạo mã ETL bằng Scala hoặc Python để trích xuất dữ liệu từ nguồn, chuyển đổi dữ liệu để khớp với lược đồ mục tiêu và tải nó vào mục tiêu. Bạn có thể chỉnh sửa, gỡ lỗi và kiểm tra mã này thông qua Console, trong IDE yêu thích của bạn hoặc bất kỳ sổ tay nào.  
![360 customer view](/images/assets/116.png) 
![360 customer view](/images/assets/117.png) 
Ngoài ra, bạn có thể thiết lập các đặc quyền cho các bảng sau thay vì cho tất cả các bảng trong cơ sở dữ liệu:  
+ visitors  
Bước 4: Đến [Amazon Athena](https://us-west-2.console.aws.amazon.com/athena/home?region=us-west-2) query bảng
![360 customer view](/images/assets/118.png) 
Bước 5: Trong Athena Query Editor, chọn c360view_raw.
![360 customer view](/images/assets/119.png) 
Bước 6: Nhấp vào 3 dấu chấm ở bên phải của bảng account, và chọn Preview table.
![360 customer view](/images/assets/120.png) 
Bước 7: Kiểm tra kết quả.
![360 customer view](/images/assets/121.png) 
Lưu ý rằng do chúng ta có tệp CSV không có tiêu đề nên tên của các cột được thu thập dưới dạng col0 đến col3 trong dữ liệu RAW. Bạn có thể chỉnh sửa điều này trên AWS Glue, nhưng các công việc của chúng ta để xử lý dữ liệu trong Step Functions đã nhận thức được điều này.  
Nếu bạn đi đến cơ sở dữ liệu c360view_stage, bạn sẽ thấy một kịch bản khác.  
Bước 8: Kiểm tra dữ liệu của các bảng khác và sau đó đi đến cơ sở dữ liệu c360view_stage.  
![360 customer view](/images/assets/122.png) 
Bấm nút "Next" để sang phần tiếp theo  