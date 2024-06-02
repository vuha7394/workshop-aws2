+++
title = 'Step Functions'
date = 2024-05-28T22:01:17+07:00
weight = 1
pre = "<b>3.1. </b>"
+++

### Step Functions
Step Functions thực hiện chuyển đổi các bảng dữ liệu thô từ nguồn, làm phẳng chúng và chuyển đổi thành các tệp Parquet..  
Tài khoản của bạn đã tạo 3 công việc chuyển đổi khác nhau dựa trên AWS Step Functions, AWS Lambda Functions và Amazon Athena.  
+ Một để chuyển đổi các bảng GA thành một bảng phẳng không chuẩn hóa;
+ Một cái thứ hai để chuyển đổi các bảng dữ liệu thô khác thành các bảng phân vùng parquet;
+ Và cái cuối cùng để phân tích dữ liệu từ dữ liệu thô của cơ sở dữ liệu quan hệ.
Kiểm tra [AWS Step Functions State machine console](https://us-west-2.console.aws.amazon.com/states/home?region=us-west-2#/statemachines).  

Bước 1:  Bấm vào link GA transformation “1MyStateMachineGA-”.
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/100.png) 
Bước 2: Bạn sẽ bắt đầu thực thi cho State Machine này.
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/101.png) 
Bước 3: Bắt đầu thực thi State machine.
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/102.png) 
Bước 4: Bạn không cần thay đổi gì, chấp nhận payload được đề xuất và bắt đầu thực thi.  
Bước 5: Kiểm tra quy trình làm việc.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/103.png) 
Trong máy trạng thái Step Functions này, chúng ta đang thực hiện chuyển đổi cho các bảng GA. Lược đồ GA có các trường lồng nhau đang được làm phẳng bằng cách sử dụng các hàm CROSS JOIN UNNEST và xác định các kiểu dữ liệu struct và array lồng nhau.  
+ Máy trạng thái này sử dụng một hàm lambda để thực hiện chuyển đổi bằng cách sử dụng thực thi truy vấn Amazon Athena.
+ Một hàm lambda khác được sử dụng để kiểm tra sự kết thúc của truy vấn trước đó, sau đó chờ hoặc chuyển sang các bước chuyển đổi tiếp theo.
Bạn có thể kiểm tra từng mã chuyển đổi dữ liệu trong bảng điều khiển máy trạng thái Step Functions của bạn.  

Bước 1: Chỉnh sửa máy trạng thái GA của bạn.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/104.png) 
Bước 2: Đi đến tab định nghĩa.  
Bạn có thể kiểm tra trong trường “query” của “Payload” trong mỗi tác vụ, các truy vấn nào được thực thi trong mỗi bước.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/105.png) 