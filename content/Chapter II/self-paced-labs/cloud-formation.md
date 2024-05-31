+++
title = "Triển khai mẫu CloudFormation"
weight = 2
pre = "<b>1.1.2. </b>"
+++

**Triển khai mẫu CloudFormation để tạo cơ sở hạ tầng cơ bản nếu bạn xây dựng nó trên tài khoản của riêng mình.**  
Bước 1: Tải về mẫu Cloudformation cf-360view.yaml: [Bấm chuột phải vào đây](https://static.us-east-1.prod.workshops.aws/public/e5165b32-d039-4828-9e1c-2deec6e6a89a/static/files/cf-360view.yaml) và lưu như 1 file. 
![360 customer view](/images/assets/12.png) 
Bước 2: Mở [AWS Cloudformation stack creation](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/create/template) và upload file mẫu.
![360 customer view](/images/assets/13.png) 
Bước 3: Chọn Next và điền các thông số:
+ Stack name: c360view
+ Network Configuration:
+ Nên deploy đến VPC nào?: Default VPC (172.31.0.0/16)
+ SubnetAz1: (172.31.0.0/20) (Tìm địa chỉ  IP này)
+ SubnetAz2: (172.31.16.0/20) (Tìm địa chỉ  IP này)
+ InstanceKeyPairParameter: c360view-oregon
![360 customer view](/images/assets/14.png)
Bước 4: Nhấp vào "Next". Không cần thay đổi gì trên trang "Configure stack options", nhấp vào "Next" lần nữa.  
Bước 5: Cuộn xuống để tìm hộp kiểm và đánh dấu vào “I acknowledge that AWS CloudFormation might create IAM resources.” Sau đó, nhấp vào "Create stack".  
![360 customer view](/images/assets/15.png)
Bước 6: Truy cập vào tab "Resources" để kiểm tra trạng thái hoàn thành của các tài nguyên.
![360 customer view](/images/assets/16.png)
Mẫu đã tạo các tài nguyên sau để tối ưu hóa thời gian của bạn. Sau khi bạn thấy trạng thái "CREATE_COMPLETE" cho stack, tất cả các tài nguyên đã sẵn sàng và bạn có thể tiến hành bước tiếp theo: Tải dữ liệu.  
Bấm nút "Next" để sang phần tiếp theo  
