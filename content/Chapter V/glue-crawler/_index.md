+++
title = 'Glue Crawler'
date = 2024-05-28T22:01:17+07:00
weight = 2
chapter = true
pre = "<b>4.2. </b>"
+++

### Glue Crawler

Chạy Glue crawler 4-Crawler360jobtables3m, 5-Crawler360jobtables6m và 6-CrawlerAnalyticsDenormalized để thu thập định nghĩa cho dữ liệu vừa được tạo bởi công việc cuối cùng.  
Bước 1: Đi đến [AWS Glue crawler console](https://us-west-2.console.aws.amazon.com/glue/home?region=us-west-2#catalog:tab=crawlers).  
Bước 2: Chọn 4-Crawler360jobtables3m và nhấp vào chạy crawler.  
![360 customer view](/images/assets/135.png) 
Bước 3: Chọn 5-Crawler360jobtables6m và nhấp vào chạy crawler.  
![360 customer view](/images/assets/136.png) 
Bước 4: Chọn 6-CrawlerAnalyticsDenormalized và nhấp vào chạy crawler.  
![360 customer view](/images/assets/137.png) 
Bước 5: Xác minh rằng mỗi lần chạy crawler mới đã thêm một định nghĩa bảng.  
![360 customer view](/images/assets/138.png) 
Bước 6: Đi đến Glue Databases -> tables, kiểm tra các bảng bạn có. Bạn có thể lọc theo cơ sở dữ liệu tại thanh tìm kiếm c360view_stage.  
![360 customer view](/images/assets/139.png) 