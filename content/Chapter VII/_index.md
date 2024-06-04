+++
title = 'Độ trễ thấp cho API và ứng dụng'
date = 2024-05-28T22:01:17+07:00
weight = 7
pre = "<b>6. </b>"
+++


Truy vấn bảng Amazon DynamoDB với kết quả để làm nguồn cho các truy vấn độ trễ thấp từ các ứng dụng hoặc APIs của bạn.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/182.png) 
Bước 1: Đến [Amazon DynamoDB console](https://us-west-2.console.aws.amazon.com/dynamodb/home?region=us-west-2#tables:selected=DDBc360view;tab=items).  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/183.png) 
Bước 2: Nhấp vào bảng DDBc360view mà bạn đã điền dữ liệu bằng một script Hive sử dụng cụm EMR của bạn, và nhấp vào nút Khám phá các mục bảng.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/184.png) 
Lưu ý rằng bảng điều khiển đã thực hiện một hoạt động quét (Scan), trả về tất cả dữ liệu, nhưng trong ứng dụng của bạn, bạn có thể muốn cụ thể hơn và sử dụng một id khách hàng hoặc/và chi nhánh ví dụ.  

Bước 3: Vì vậy, ghi chú một số khóa phân vùng (partition key), đó là "client_id" của bạn từ bảng không chuẩn hóa và khóa sắp xếp (sort key) của bạn, đó là "branch_id" của bạn, để bạn có thể thực hiện một số truy vấn cụ thể. Trong trường hợp của tôi, tôi có thể sử dụng 5002, 5006, 5014, 5021, 5025, 5035... và tiếp tục cho id khách hàng của mình (pk), và 198, 465, 236, 218, 109, 215, 394, 381, 225 cho chi nhánh. Các số của bạn sẽ khác nhau vì dữ liệu được tạo ra trong tài khoản của bạn là ngẫu nhiên.  

Bước 4: Cuộn xuống và sang phải để bạn có thể kiểm tra các trường khác cho các bản ghi.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/185.png) 
Bước 5: Bây giờ thay vì chọn Quét (Scan), chọn Truy vấn (Query) và nhập một giá trị của id khách hàng vào trường pk. Trong trường hợp của tôi là 5256, nhưng hãy chọn một trong số các giá trị đã lấy ở bước trước.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/186.png) 
Bước 6: Nhấp vào Bắt đầu tìm kiếm và xem kết quả hiển thị ngay lập tức.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/187.png) 
Bước 7: Nhấp vào liên kết pk cho id bạn đã chọn để bạn có thể xem toàn bộ dữ liệu.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/188.png) 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/189.png) 
Lặp lại điều này cho một số id khách hàng.  

Bạn đã thực hiện một truy vấn theo khóa phân vùng, bạn cũng có thể sử dụng chỉ mục để tìm trực tiếp cho mỗi khách hàng trong một chi nhánh bằng cách chọn chỉ mục GSI1 đã được tạo ra, đó là một chỉ mục phụ toàn cầu.  

Sử dụng GSIs, chúng ta có thể thay đổi khóa truy vấn bằng các trường khác mà chúng ta cần tìm dữ liệu rất nhanh chóng.  

Bước 1: Chọn chỉ mục GSI1 để truy vấn.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/190.png) 
Bước 2: Đặt một số chi nhánh, chẳng hạn như 5388 trong trường hợp của tôi.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/191.png) 
Bạn có thể nhập pk của khách hàng mong muốn và xem hồ sơ đầy đủ.  

Bảng DynamoDB này được sử dụng để truy cập nhanh chóng dữ liệu khi cần tương tác trực tiếp với khách hàng. Ví dụ về việc sử dụng bao gồm ứng dụng quản lý chi nhánh di động hoặc ứng dụng trung tâm liên hệ để kiểm tra hồ sơ khách hàng hoặc các chiều khác. Các ví dụ khác để tiết lộ bảng DynamoDB với một API có thể sử dụng Amazon API Gateway. Nếu ứng dụng của bạn đặt trong tài khoản AWS, bạn có thể sử dụng cuộc gọi trực tiếp đến DynamoDB SDK và API. Để kiểm tra các mã khác sử dụng trong hội thảo này, hãy xem trong thư mục "library" trong bucket stage của bạn trên S3.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/192.png)
Bạn cũng có thể kiểm tra mã của các hàm lambda trên bảng điều khiển Lambda của AWS bằng cách nhấp vào bất kỳ hàm nào.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/193.png)  
Đối với Data scientists và người dùng là Doanh nghiệp, bạn cũng có thể sử dụng [Amazon Sagemaker](https://aws.amazon.com/sagemaker/?nc1=h_ls) và [Amazon Quicksight](https://aws.amazon.com/quicksight/?nc1=h_ls) để khám phá dữ liệu thay vì sử dụng Athena. Chi tiết hơn, xem thêm [creating data set from Athena on Quicksight](https://docs.aws.amazon.com/quicksight/latest/user/create-a-data-set-athena.html) và [Run SQL queries from your Sagemaker notebooks using Amazon Athena](https://aws.amazon.com/Workshops/machine-learning/run-sql-queries-from-your-sagemaker-notebooks-using-amazon-athena/).  
Cụ thể như sau:  