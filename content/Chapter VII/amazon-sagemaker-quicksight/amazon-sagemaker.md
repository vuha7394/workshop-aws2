+++
title = 'Sử dụng Amazon SageMaker'
date = 2024-05-28T22:01:17+07:00
weight = 1
pre = "<b>6.1.1. </b>"
+++

#### Sử dụng Amazon SageMaker để chạy truy vấn SQL trên Amazon Athena
**Bước 1: Thiết lập quyền truy cập**
1. Tạo IAM Role: Đảm bảo bạn có một IAM Role với các quyền cần thiết để truy cập Amazon Athena và SageMaker. Bạn có thể tạo một IAM Role mới hoặc sử dụng một role hiện có với các quyền AmazonAthenaFullAccess, AmazonS3FullAccess, và AmazonSageMakerFullAccess.  
2. Đính kèm IAM Role: Đính kèm IAM Role này vào notebook instance của SageMaker.  

**Bước 2: Tạo một SageMaker Notebook Instance**  
1. Truy cập Amazon SageMaker Console.
2. Chọn Notebook Instances và nhấn vào Create notebook instance.
3. Điền thông tin:
    - Notebook instance name: AthenaSageMaker
    - Notebook instance type: ml.t2.medium (hoặc loại phù hợp với yêu cầu của bạn)
    - IAM role: Chọn IAM Role mà bạn đã tạo ở bước trên.  

**Bước 3: Cài đặt và cấu hình các thư viện cần thiết**  
1. Mở Jupyter Notebook: Khi notebook instance đã sẵn sàng, nhấn vào Open Jupyter.
2. Cài đặt thư viện PyAthena: Chạy các lệnh sau trong một ô của notebook:python
  !pip install pyathena  

**Bước 4: Kết nối và chạy truy vấn Athena**  

1.Kết nối với Athena: Sử dụng mã Python sau để kết nối và chạy truy vấn Athena:  

    from pyathena import connect
    import pandas as pd

    conn = connect(s3_staging_dir='s3://your-athena-query-results/',
                region_name='us-west-2')

    query = 'SELECT * FROM your_table_name LIMIT 10;'
    df = pd.read_sql(query, conn)
    print(df.head())
Thay thế s3://your-athena-query-results/ bằng bucket S3 của bạn để lưu trữ kết quả truy vấn.  
Thay thế your_table_name bằng tên bảng trong Athena mà bạn muốn truy vấn. 