+++
title = 'Chạy bước chuyển đổi'
date = 2024-05-28T22:01:17+07:00
weight = 2
chapter = true
pre = "<b>4.3.2. </b>"
+++

#### Chạy bước chuyển đổi

Bước 1: Đến [EMR console](https://us-west-2.console.aws.amazon.com/elasticmapreduce/home?region=us-west-2).
![360 customer view](/images/assets/144.png) 
Bước 2: Bấm vào c360cluster ID.
![360 customer view](/images/assets/145.png) 
Bước 3: Bấm vào tab Steps.  
![360 customer view](/images/assets/146.png) 
Bước 4: Thêm bước.  
+ Step type: Spark application
+ Name: denormalization
+ Deploy mode: Cluster
+ Spark-submit option: leave blank
+ Application location: s3://**your_stage_bucket**/library/c360_analytics.py  
Sử dụng trình duyệt bucket để chọn vị trí ứng dụng.  
+ Arguments: --BucketName **your analytics bucket** Chọn tên từ bảng điều khiển Amazon S3 và để lại một khoảng trống giữa chúng --bucketName .VD: --BucketName c360view---analytics
![360 customer view](/images/assets/147.png) 
Sau đó, bấm Add.  
Bước 5: Kiểm tra trạng thái công việc, từ đang chờ xử lý (pending) đến đang chạy (running).  
![360 customer view](/images/assets/148.png) 
Sau khi hoàn thành, công việc đã tạo ra một bảng không chuẩn hóa bằng cách sử dụng PySpark.  
![360 customer view](/images/assets/149.png) 
Bước 6: Đến [Lake formation console](https://us-west-2.console.aws.amazon.com/lakeformation/home?region=us-west-2#tables) chọn bảng c360denormalized c360view_analytics.  
![360 customer view](/images/assets/150.png) 
Bước 7: Cấp quyền truy cập cho user or role.
![360 customer view](/images/assets/151.png) 
Bước 8: Đi đến bảng [Athena console](https://us-west-2.console.aws.amazon.com/athena/home?region=us-west-2#query) và kiểm tra bảng c360denormalized mới trong cơ sở dữ liệu c360view_analytics.  
![360 customer view](/images/assets/152.png) 