+++
title = "Truy xuất dữ liệu từ các nguồn"
date = 2024-05-28T22:01:17+07:00
weight = 4
pre = "<b>2.4. </b>"
chapter = true
+++

### Truy xuất dữ liệu từ các nguồn
 
Trong phần này, chúng ta sẽ kích hoạt các bộ lập lịch (quy tắc) để tạo dữ liệu từ các nguồn khác nhau.  
Bước 1: Đi tới [Amazon Eventbridge](https://us-west-2.console.aws.amazon.com/events/home?region=us-west-2#/rules) -> Buses -> Rules, và bật từng quy tắc c360v-Schedule
![360 customer view](/images/assets/63.png) 
Bước 2: Chọn từng mục của c360v-Schedule và bật nó. Lưu ý quan trọng: bật từng cái một. Không bật tất cả cùng một lúc.  

Order:
  - ScheduledIngestionGetCRMApi
  - ScheduledIngestionCard
  - ScheduledIngestionBank
  - ScheduledIngestionAccount
  - ScheduledGetGATables
  - ScheduledIngestionPostgresql

![360 customer view](/images/assets/64.png) 
Bước 3: Lặp lại bước 2 cho từng mục c360v-Schedule từ trên xuống dưới, cho đến khi tất cả đều chuyển sang màu xanh.  
![360 customer view](/images/assets/65.png) 
Amazon S3 là dịch vụ trung tâm của kiến trúc Data Lake trong AWS. Trong giải pháp của chúng tôi, chúng tôi sử dụng các hàm Lambda để lấy dữ liệu bên ngoài như BigQuery từ nguồn GA (Google Analytics):  
[https://www.kaggle.com/bigquery/google-analytics-sample](https://www.kaggle.com/bigquery/google-analytics-sample) các bảng và cũng tạo ra nhiều dữ liệu tổng hợp khác cho các tập dữ liệu khác.  
Để bạn biết thêm, dưới đây là mã AWS Lambda gốc được sử dụng để trích xuất dữ liệu BigQuery, nhưng bây giờ bạn có thể sử dụng [Amazon Appflow](https://aws.amazon.com/appflow/) cùng tài khoản GA của bạn  

    python  
    from google.cloud import bigquery  
    import json  
    import boto3  
    import os  
    s3 = boto3.resource('s3')  
    client = bigquery.Client.from_service_account_json('./bqfile.json')  
    datasets = list(client.list_datasets())  
    project = client.project  
    table = os.environ['table']  
    PATH_TO = os.environ['path_to']  
    BUCKET_NAME = os.environ['bucket']  
    QUERY = ('SELECT '' TO_JSON_STRING(g) jsonfield '' FROM ` bigquery-public-data\:google_analytics_sample..ga_sessions_'+table+'` g ')  
    query_job = client.query(QUERY)  # API request  
    
    
    def lambda_handler(event, context):  
        tofile=''
        rows = query_job.result()  
        for row in rows:  
            newfield=row.jsonfield+'\n'  
           tofile += newfield  
        s3.Object(BUCKET_NAME, PATH_TO+'/ga_sessions_' + table+'/ga_sessions_'+table+'.json').put(Body=tofile)  

Nếu bạn muốn sử dụng mã này, bạn phải cài đặt thư viện gcloud python sdk trực tiếp và tạo một tệp bqfile.json với thông tin đăng nhập tài khoản dịch vụ gcloud của bạn, sau đó nén thư mục thư viện, bqfile.json, và lambda.py của bạn để triển khai nó lên các hàm AWS Lambda. Thiết lập ba biến môi trường để sử dụng nó hoặc gọi bảng, đường dẫn đến và bucket.  
Xác minh dữ liệu được tạo bởi các hàm Lambda mà bạn đã bật bằng EventBridge.  
Bước 1: Đi tới bảng điều khiển Amazon S3 để kiểm tra dữ liệu trong bucket raw của bạn. Tìm kiếm các bucket c360view.  
![360 customer view](/images/assets/66.png) 
Bước 2: Nhấp vào bucket c360view--<YOUR_ACCOUNT_ID>-raw.  
Làm mới bucket trong khi các mã Lambda đang chạy.  
![360 customer view](/images/assets/67.png)
Nếu sau 1 đến 5 phút bạn không thấy tất cả các thư mục: account, card, crm, data và gbank, quay lại [CloudWatch -> Events -> Rules](https://us-west-2.console.aws.amazon.com/cloudwatch/home?region=us-west-2#rules:) , và đánh dấu bộ lập lịch bạn thiếu dữ liệu, Tắt nó, và Bật lại.  
Bước 3: Vào bên trong từng thư mục để kiểm tra các tệp được tạo bên trong.  
![360 customer view](/images/assets/68.png) 
Account data, tại account folder.  
![360 customer view](/images/assets/69.png) 
GA sessions data, at data/GA/ga_session_20YYMMDD folders.  
Bấm nút "Next" để sang phần tiếp theo  