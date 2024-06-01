+++
title = "Sử dụng Glue Jobs"
date = 2024-05-28T22:01:17+07:00
weight = 5
pre = "<b>2.5. </b>"
chapter = true
+++

### Sử dụng Glue Jobs
 
Tạo một Glue Job để lấy dữ liệu từ cơ sở dữ liệu quan hệ giao dịch của bạn.  
Kiểm tra trong các [Eventbridge Rules](https://us-west-2.console.aws.amazon.com/events/home?region=us-west-2#/rules) của bạn xem bạn đã khởi động c360-ScheduledIngestionPostgresql- chưa, vì nó được tạo sau nên có thể bạn chưa khởi động nó.  
Bước 1: Nếu Quy tắc này chưa được bật (“màu xanh”), vui lòng bật nó ngay bằng cách nhấp vào Actions.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/70.png) 
Đi tới Glue Console, tạo và chạy một JDBC Crawler cho cơ sở dữ liệu.  
Bước 1: Thêm định nghĩa bảng [Create Crawler](https://us-west-2.console.aws.amazon.com/glue/home?region=us-west-2#catalog:tab=crawlers) 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/71.png) 
Bước 2: Nhập thuộc tính của trình thu thập dữ liệu (crawler)  
Crawler name: 3-sourcemf  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/72.png) 
Bấm next  
Bước 3: Chọn nguồn data, click "not yet" và "add a data source"  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/73.png) 
Bước 4: Thêm một nguồn dữ liệu mới  
+ Chọn kho dữ liệu: JDBC
+ Kết nối cơ sở dữ liệu: sourcemf
+ Đường dẫn nguồn: sourcemf/% 
+ Sau đó click  "Thêm 1 JDBC nguồn data":
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/74.png) 
Bước 5: Chọn nguồn data được tạo và bấm next  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/75.png) 
Step 6: Chọn Glue-role-c360view cho IAM role  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/76.png) 
Bước 7: Thiết lập đầu ra và lập lịch trình  
Database: c360view_raw Frequency: Run on Demand
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/77.png) 
Bước 8: Kiểm tra lại và tạo crawler  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/78.png) 
Bấm create crawler  
Bước 9: Kiểm tra nếu tạo thành công crawler Finish  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/79.png) 
Bước 10: Chạy crawler  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/80.png) 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/81.png) 
Chờ cho trình thu thập dữ liệu hoàn thành. Quá trình này sẽ mất từ 2-5 phút để hoàn tất và thêm một bảng mới:  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/82.png) 
**Tạo một Glue Job**  
Bước 1: Tạo một Glue Job để nhập dữ liệu từ cơ sở dữ liệu quan hệ. Đi tới [Glue -> ETL jobs -> Visual ETL](https://us-west-2.console.aws.amazon.com/gluestudio/home?region=us-west-2#/jobss) và chọn "Visual ETL":  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/83.png) 
Chọn nguồn: Relational DB  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/84.png) 
Bước 2: Thiết lập tên Job và Data Source  
+ Name: 1-sourcemf
+ JDBC Source: JDBC Connection details
+ Connection Name: sourcemf
+ Table: transactions
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/85.png) 
Sau đó click: IAM Role: Glue-role-c360view và chờ Data preview  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/86.png) 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/87.png) 
Giữ nguyên tùy chọn visual dag.  
Bước 3: Thiết lập chuyển đổi  
Nhấp vào + -> Transforms -> Change schema  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/88.png) 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/89.png) 
Thay đổi loại ngày data:  
+ date: Target key - date sang Data type - string (thay ngày từ  timestamp sang string)
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/90.png) 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/91.png) 
Bấm nút +  
Bước 4: Thiết lập Data target  
Chọn Targets:  
Target: Amazon S3  
+ Format: JSON
+ Compression Type: None
+ S3 Target Location ( Browse S3)
  - s3://c360view-us-west-2-< Account ID >-raw/sourcemf_sourcemf_public_transactions/
+ Data Catalog - Tạo một bảng trong Data Catalog và trong các lần chạy tiếp theo, cập nhật lược đồ và thêm các phân vùng mới.
+ Database: c360view_raw
+ Table name: sourcemf_sourcemf_public_transactions
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/92.png) 
Bước 5: Thay tên công việc thành 1-sourcemf. Đặt tên công việc là sourcemf  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/93.png) 
Bước 6: Lưu lại công việc  
Bấm Save, sau đó bấm Job details 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/94.png) 
Bước 7: Job Details Đưa thông tin này vào công việc:
IAM Role: Glue-role-c360view
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/95.png) 
Sau đó lưu lại, bấm Save  
Bước 8: Chạy công việc  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/96.png) 
Bước 9: Chờ công việc hoàn thành  
Quá trình này mất từ 2-5 phút để hoàn tất. Kiểm tra trạng thái công việc, nó cần ở trạng thái "Ready":  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/97.png) 
Bấm nút "Next" để sang phần tiếp theo  