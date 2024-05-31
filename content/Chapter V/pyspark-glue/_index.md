+++
title = 'PySpark - Glue'
date = 2024-05-28T22:01:17+07:00
weight = 1
chapter = true
pre = "<b>4.1. </b>"
+++

### PySpark - Glue

Bây giờ bạn sẽ thực hiện các chuyển đổi nâng cao hơn bằng cách sử dụng các công việc AWS Glue.  
Bước 1: Đi đến [AWS Glue jobs console](https://us-west-2.console.aws.amazon.com/glue/home?region=us-west-2#etl:tab=jobs), chọn n1_c360_dispositions, công việc Pyspark.  
![360 customer view](/images/assets/123.png) 
Chuyển đổi bên trong công việc này thực hiện một phép nối giữa 3 bảng, ngân hàng chung, tài khoản và thẻ, để tính toán loại giao dịch và thông tin thu nhận.  
Bước 2: Nhấp vào Chỉnh sửa công việc.  
+ Nếu sử dụng giao diện điều khiển mới, bạn có thể chọn công việc và đi đến tab Chi tiết công việc.
+ Đảm bảo bạn chọn ngôn ngữ Python 3, nếu sử dụng giao diện điều khiển mới.
+ Thư mục tạm thời sẽ được thiết lập trong các thuộc tính nâng cao.
![360 customer view](/images/assets/124.png) 
Bước 3: Thay đổi Glue version sang Glue Version 4.0 - Supports spark 3.3, Python 3.  
![360 customer view](/images/assets/125.png) 
Bước 4: Nhấp vào thuộc tính nâng cao, chọn bucket S3 stage của bạn c360view-us-west-2-your_account_id-log + '/tmp/' làm thư mục tạm thời.  
![360 customer view](/images/assets/126.png) 
Bước 5: Bấm Save n1_c360_dispositions và chạy công việc.
![360 customer view](/images/assets/127.png) 
Bước 6: Chờ hoàn thành. Quá trình này mất từ 2-5 phút để hoàn thành.
![360 customer view](/images/assets/128.png) 
Bước 7: Kiểm tra kịch bản và nhật ký.
![360 customer view](/images/assets/129.png)
Lưu ý rằng trong kịch bản Python này, kết quả truy vấn từ Amazon Athena được chuyển đổi thành khung dữ liệu Pandas và sau đó kết quả từ chuyển đổi Pandas thành các tệp parquet trong Amazon S3 bằng cách sử dụng hoạt động ghi của spark.  
Bước 8: Bây giờ chọn công việc Jobcust360etlmftrans, một công việc Pyspark khác, Hành động và Chỉnh sửa công việc.  
![360 customer view](/images/assets/130.png) 
Bước 9: Thay đổi phiên bản Glue thành Glue Version 4.0 - Hỗ trợ spark 3.3, Python 3 và chọn bucket S3 stage của bạn c360view-us-west-2-your_account_id-log + '/tmp/' làm thư mục tạm thời.  
![360 customer view](/images/assets/131.png) 
Lưu.  
Bước 10: Trong công việc Jobcust360etlmftrans, nhấp vào lưu, sau đó nhấp vào Chạy công việc.  
![360 customer view](/images/assets/132.png) 
Bước 11: Nhấp vào Chạy và chờ hoàn thành. Quá trình này sẽ mất từ 2-5 phút.  
![360 customer view](/images/assets/133.png) 
![360 customer view](/images/assets/134.png) 
Trong kịch bản pyspark này, chúng ta đang thực hiện một số phép tổng hợp với các giao dịch từ cơ sở dữ liệu quan hệ theo account_id trong 3 tháng gần đây và 6 tháng gần đây. Để thực hiện điều này, chúng ta đã sử dụng khung động AWS Glue.  