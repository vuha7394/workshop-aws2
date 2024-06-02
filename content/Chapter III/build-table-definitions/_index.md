+++
title = 'Định nghĩa Bảng'
date = 2024-05-28T22:01:17+07:00
weight = 1
pre = "<b>2.1. </b>"
+++

### Xây dựng Định nghĩa Bảng  
Chạy trình thu thập dữ liệu (crawler) trong AWS Glue Console để lấy định nghĩa bảng từ bucket raw của bạn. Trình thu thập dữ liệu truy cập kho dữ liệu, trích xuất siêu dữ liệu và tạo định nghĩa bảng trong AWS Glue Data Catalog. Bảng điều khiển Crawlers trong AWS Glue hiển thị trạng thái và số liệu từ lần chạy cuối của trình thu thập dữ liệu.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/31.png)
Bước 1: Đến AWS [Glue Crawlers](https://us-west-2.console.aws.amazon.com/glue/home?region=us-west-2#catalog:tab=crawlers) :  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/32.png)
Tạo cơ sở dữ liệu và định nghĩa bảng với Glue Crawler  
Bước 2: Nhấp vào 1-Crawler360rawdata và chạy trình thu thập dữ liệu (Run crawler). Trình thu thập dữ liệu này sẽ đọc các tệp trong bucket raw của bạn và tạo các định nghĩa bảng cho từng lược đồ bảng cho cơ sở dữ liệu c360view-raw.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/33.png)  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/34.png)  
Khi hoàn thành bạn sẽ thấy 5 bảng được tạo ra.  
Bước 3: Chọn 2-Crawlerc360visitorid và chạy.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/35.png)  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/36.png)  
Bước 4: Bạn sẽ thấy 5 bảng được thêm bởi trình thu thập dữ liệu 1-Crawler360rawdata.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/37.png)  
Bạn sẽ thấy một bảng được thêm bởi trình thu thập dữ liệu 2-Crawlerc360visitorid.
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/38.png)  
Bước 5: Bạn có thể xác minh định nghĩa bảng bằng cách vào Database -> Tables trong cùng bảng điều khiển.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/39.png)  
Glue Crawler đã tạo cơ sở dữ liệu c360view_raw và c360view_stage cùng 6 định nghĩa bảng..  
Bấm nút "Next" để sang phần tiếp theo  