+++
title = "Giới thiệu"
date = 2024-05-28T22:01:17+07:00
weight = 1
+++

### Giới thiệu

Một trường hợp rất phổ biến là các tổ chức thường xem xét khách hàng của mình từ các góc độ khác nhau, chẳng hạn như góc độ trung thành, xem xét các chỉ số như: số năm lịch sử mua hàng, tần suất tương tác, hoặc góc độ nhân khẩu học như giá trị vòng đời khách hàng hoặc thu nhập. Chúng tôi gọi chúng là các chiều dữ liệu, và chúng tôi sẽ kết hợp nhiều chiều về khách hàng của bạn để cung cấp cho bạn khả năng hiển thị nhiều góc độ cùng một lúc.

![360 customer view](/images/assets/1.png)

**Sơ đồ cấu trúc workshop:** 

![360 customer view](/images/assets/2.png)

**Kiến trúc Data Lake:**
+ **Truy xuất dữ liệu:** AWS Lake Formation tự động di chuyển dữ liệu từ cơ sở dữ liệu quan hệ sang Amazon S3 bằng trình kết nối và tác vụ Glue.
+ **Lưu trữ:** Hồ dữ liệu trên Amazon S3 với các bucket Raw, Stage và Analytics.
+ **Xử lý dữ liệu:** Step Functions điều phối các hàm Lambda sử dụng Athena để truy vấn. Glue jobs với Spark/Python và EMR với Spark/Hive giúp chuyển đổi và tổng hợp dữ liệu.
+ **Truy cập dữ liệu:** Truy cập dữ liệu qua bảng điều khiển/API truy vấn Athena hoặc bảng điều khiển/API DynamoDB.


| Domain | Data source | Source Format | Source column name |
| ------ | ----------- | ------------- | ------------------ |
| Customer info   | CRM | API - json | client_id |
| | | | age |
| | | | date_Of_Birth |
| | | | home_ownserhip_status |
| | | | occupation |
| | | | marital_Status |
| | | | head_of_household_flag |
| | | | client_created_date |
| Transactions   | Mainframe sources | Relational Database | trans_id |
| | | | account_id |
| | | | date |
| | | | type |
| | | | operation |
| | | | amount |
| | | | balance |
| Credit Card   | Card origination system | Text file - from Mainframe | card_id |
| | | | disp_id |
| | | | type |
| | | | issued_datetime |
| General banking   | Dispositions Database | Text file - from Mainframe | disp_id |
| | | | client_id |
| | | | account_id |
| | | | type |
| Web_analytics   | Google Analytics | json with nested fields | client_id |
| | | | visitNumber |
| | | | visitId |
| | | | visitStartTime |
| | | | Date |
| | | | Totals |
| | | | trafficSource |
| | | | device |
| | | | geoNetwork |
| | | | customDimensions |
| | | | Hits |
| | | | fullVisitorId |
| | | | userId |
| WebVisitor map   | Map web visitors to client_id | Text file | visitorId hash |
| | | | client_id |
| Shopping History   | Retail Sales - Orders | CSV file from SaaS App | row id |
| | | | order_id |
| | | | order_date |
| | | | date_key |
| | | | contact_name |
| | | | country |
| | | | city |
| | | | region |
| | | | subregion |
| | | | customer |
| | | | client_id |
| | | | industry |
| | | | segment |
| | | | product |
| | | | license |
| | | | sales |
| | | | quantity |
| | | | discount |
| | | | profit |

Trong tài khoản này, bạn sẽ đảm bảo các tài nguyên sau được cung cấp:
+ Bốn bucket Amazon S3: RawDataS3Bucket, StageDataS3Bucket, AnalyticsDataS3Bucket, và LogDataS3Bucket.
+ Một instance RDS với cơ sở dữ liệu Aurora PostgreSQL để mô phỏng cơ sở dữ liệu giao dịch của bạn, được đặt tên là RDSSource – sourcemf.
+ Các hàm Lambda để tạo dữ liệu từ nhiều nguồn khác nhau, mô phỏng một ứng dụng:
    - c360viewCRMApi - CRM
    - c360viewGetCRMApi - Tích hợp với CRM của chúng tôi
    - c360viewGetGaTables - Dữ liệu Google Analytics
    - c360viewMFgenAccount - Dữ liệu ngân hàng chung từ mainframe
    - c360viewMFgenCard - Trích xuất thông tin thẻ ra các tệp
    - c360viewMFgenGBank - Dữ liệu từ mainframe

Các nguồn của chúng tôi:
+ Trong giải pháp của chúng tôi, chúng tôi sử dụng các hàm Lambda để lấy dữ liệu từ bên ngoài, chẳng hạn như từ BigQuery với các bảng GA (Google Analytics) có sẵn tại Mẫu Google Analytics trên Kaggle, và tạo nhiều bộ dữ liệu tổng hợp khác.
+ Các quy tắc EventBridge để lập lịch và kích hoạt các hàm Lambda, mô phỏng các tích hợp của chúng tôi.
+ Các nhóm bảo mật và tường lửa cho instance EC2, các instance sao chép, và các hàm Lambda.
+ Một vai trò cho các hàm AWS Lambda và một vai trò cho AWS Glue.
+ Một cụm Amazon EMR.

Bấm nút "Next" để sang phần tiếp theo

## 1. Làm thế nào để bắt đầu workshop?

Các bước thiết lập:  
a) Đối với sự kiện AWS: vào "Required setup - [AWS event on workshop studio](https://catalog.workshops.aws/join)".  
b) Đối với tài khoản riêng: vào "Self Paced Labs - [Do on your own AWS Account](https://portal.aws.amazon.com/gp/aws/developer/registration/index.html?refid=em_127222)".  

Tạo cặp khóa và điểm cuối VPC.  
+ Triển khai CloudFormation để thiết lập các thành phần và trình tạo dữ liệu.
+ Thêm các bước bổ sung trước khi thực hiện hội thảo.
+ Bấm nút "Next" để sang phần tiếp theo

### Self Paced Labs - Do on your own account

## 2. Tải dữ liệu và Điều phối

### Thiết lập Lake Formation

### Kết nối tới Database

### Truy xuất dữ liệu từ các nguồn

### Sử dụng Glue Jobs

## 3. Chuẩn bị dữ liệu (Data Preparation)

### Step Functions

#### Thực hiện chuyển đổi từ định dạng CSV sang định dạng parquet cho các bảng gbank (ngân hàng chung), account (tài khoản) và card (thẻ), và từ định dạng JSON sang định dạng parquet cho bảng customer (CRM).

#### Thực hiện chuyển đổi với các bảng dữ liệu thô nguồn từ cơ sở dữ liệu quan hệ và chuyển đổi chúng thành các tệp parquet.

### Truy vấn với Athena

## 4. Chuyển đổi nâng cao

### PySpark - Glue

### Glue Crawler

### Amazon EMR

#### Cấp quyền Lake cho vai trò EMR đối với cơ sở dữ liệu Lake Formation.

#### Chạy bước chuyển đổi

### Amazon DynamoDB

## 5. Trực quan hoá với Quicksight

## 6. Độ trễ thấp trong việc cung cấp cái nhìn 360 độ cho API và ứng dụng  

### Khám phá dữ liệu với Amazon SageMaker và QuickSight
#### Sử dụng Amazon SageMaker để chạy truy vấn SQL trên Amazon Athena



#### Sử dụng Amazon QuickSight để tạo dataset từ Athena



## 7. Cleanup - Chỉ áp dụng nếu bạn sử dụng tài khoản của riêng bạn

































