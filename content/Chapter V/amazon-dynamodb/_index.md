+++
title = 'Amazon DynamoDB'
date = 2024-05-28T22:01:17+07:00
weight = 4
chapter = true
pre = "<b>4.4. </b>"
+++

### Amazon DynamoDB

Điền dữ liệu vào bảng Amazon DynamoDB với kết quả để làm nguồn cho các truy vấn độ trễ thấp từ ứng dụng hoặc API của bạn.  
Amazon DynamoDB là một cơ sở dữ liệu key-value và document cung cấp hiệu suất trong khoảng mili giây đơn lẻ ở bất kỳ quy mô nào. Đây là một cơ sở dữ liệu được quản lý hoàn toàn, đa vùng, đa chủ, bền vững với bảo mật tích hợp, sao lưu và khôi phục, và bộ nhớ đệm trong bộ nhớ cho các ứng dụng quy mô internet. DynamoDB có thể xử lý hơn 10 nghìn tỷ yêu cầu mỗi ngày và có thể hỗ trợ đỉnh điểm hơn 20 triệu yêu cầu mỗi giây.  
![360 customer view](/images/assets/153.png) 
Chúng ta sẽ sử dụng một script Hive để thực hiện truy vấn trên bảng nguồn và lưu nó vào DynamoDB.  
Bước 1: Đến [EMR console](https://us-west-2.console.aws.amazon.com/elasticmapreduce/home?region=us-west-2).
![360 customer view](/images/assets/154.png) 
Bước 2: Bấm c360cluster.  
![360 customer view](/images/assets/155.png) 
Bước 3: Bấm tab Steps.  
![360 customer view](/images/assets/156.png) 
Bước 4: Bấm thêm bước.  
+ Step type: Hive program
+ Name: loadtodynamodb
+ Hive script location: s3://**your_stage_bucket**/library/c360dynamodbload.q
Sử dụng trình duyệt bucket để chọn vị trí ứng dụng.  
![360 customer view](/images/assets/157.png) 
+ Input S3 location: leave blank
+ Output s3 location: leave blank
+ Arguments: leave blank
+ Action on failure: continue  
Bấm Add Step  
![360 customer view](/images/assets/158.png) 
Bước 5: Kiểm tra trạng thái công việc, từ đang chờ xử lý (pending) đến đang chạy (running).  
![360 customer view](/images/assets/159.png)
![360 customer view](/images/assets/160.png)  