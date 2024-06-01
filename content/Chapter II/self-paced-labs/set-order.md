+++
title = "Thiết lập yêu cầu"
date = 2024-05-28T22:01:17+07:00
weight = 1
pre = "<b>1.1.1. </b>"
+++

**Thiết lập yêu cầu**  
Thực hiện các bước sau trước khi khởi chạy mẫu CloudFormation nếu bạn muốn thiết lập trên tài khoản của riêng mình. Bỏ qua bước tiếp theo nếu bạn đang ở sự kiện AWS.  
Tạo cặp khóa trong khu vực đã được cung cấp:  
Cặp khóa, bao gồm khóa riêng và khóa công khai, là một bộ thông tin xác thực bảo mật dùng để chứng minh danh tính của bạn khi kết nối với một instance. Nhấp vào [Tài liệu về cặp khóa](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html) để tìm hiểu thêm.  

Các bước tạo cặp khóa:  
+ Đăng nhập vào bảng điều khiển AWS bằng thông tin đăng nhập tài khoản của bạn.
+ Chọn khu vực nơi bạn đã triển khai hội thảo (ví dụ: us-west-2). Kiểm tra góc trên bên phải của bảng điều khiển để đảm bảo bạn đang ở đúng khu vực.
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/3.png)
Đến [Key pairs console](https://us-east-1.console.aws.amazon.com/ec2/v2/home?region=us-east-1#KeyPairs) và tạo 1 cặp khoá ở vùng sau:  
Key pair name: c360view-oregon  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/4.png)  
Click on Create key pair button.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/5.png)  
Tải về cặp khoá.  

Nếu bạn sử dụng máy tính hệ điều hành Windows, tải khoá dưới định dạng file  ppk. Nếu là máy Mac hoặc Linux tải dưới định dạng file pem.  

**Tạo điểm cuối VPC cho Amazon S3**
Điểm cuối VPC cho phép bạn kết nối riêng tư VPC của mình với các dịch vụ AWS được hỗ trợ và các dịch vụ điểm cuối VPC do AWS PrivateLink cung cấp mà không cần cổng internet, thiết bị NAT, kết nối VPN, hoặc kết nối AWS Direct Connect. Để biết thêm thông tin, nhấp vào [tài liệu về điểm cuối VPC](https://docs.aws.amazon.com/vpc/latest/privatelink/concepts.html).  

Các bước tạo điểm cuối VPC cho Amazon S3:  
Bước 1: Truy cập vào bảng điều khiển Amazon VPC và chọn "Endpoints" từ menu bên trái.  
Bước 2: Nhấp vào "Create Endpoint" và sau đó chọn "AWS Services".  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/6.png)  
+ Service Name: com.amazonaws.us-east-1.s3
+ Type Gateway
+ Sử dụng Search Bar vì nó có thể ở trang thứ 2 của “AWS services”.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/7.png) 
Bước 3: Chọn VPC mặc định.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/8.png) 
Bước 4: Kiểm tra ID bảng định tuyến như trên.  
Bước 5: Giữ nguyên chính sách Full access và không thay đổi chính sách.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/9.png) 
Bước 6: Tạo điểm cuối.  
Bước 7: Bây giờ tạo một điểm cuối khác  
Bước 8: Chọn  
+ Dịch vụ: điểm cuối com.amazonaws.us-east-1.secretsmanager
+ Loại: Giao diện
Bước 9: Chọn VPC mặc định.  
Bước 10: Bao gồm TẤT CẢ các mạng con, bằng cách chọn hộp Mạng con chính.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/10.png) 
Bước 11: Chọn nhóm bảo mật mặc định.  
Bước 12: Giữ nguyên lựa chọn Full Access  
Bước 13: Tạo điểm cuối.  
Bước 14: Bây giờ hãy chuyển đến bảng điều khiển Security Group console để cho phép lưu lượng truy cập gửi đến từ VPC của bạn ở cổng 443.  
Bước 15: Kiểm tra nhóm bảo mật mặc định và nhấp vào -> Hành động -> Chỉnh sửa quy tắc gửi đến  
(Add Rule) Type: HTTPS  
Protocol: TCP  
Port: 443  
Source : Custom  
IP Range : (Kiểm tra dải IP VPC của bạn), ví dụ ở case của tôi là 172.31.0.0/16.  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/11.png) 
Save rules  