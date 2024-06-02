+++
title = 'Cleanup'
date = 2024-05-28T22:01:17+07:00
weight = 8
pre = "<b>7. </b>"
+++

## 7. Cleanup tài khoản

Sau khi tương tác với môi trường, để dọn dẹp các tài nguyên:  
+ Tắt hoặc xóa tất cả các [CloudWatch schedules](https://us-west-2.console.aws.amazon.com/cloudwatch/home?region=us-west-2#cw:dashboard=Home) đã tạo để tránh tạo dữ liệu mới;
+ Làm trống các [S3 buckets](https://s3.console.aws.amazon.com/s3/home?region=us-west-2)  của bạn c360view;
+ Điều hướng đến [CloudFormation console](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2) để xóa toàn bộ ngăn xếp c360view, điều này sẽ xóa cơ sở dữ liệu giao dịch RDS, cụm EMR và tất cả các tài nguyên khác.  
Để hủy đăng ký Quicksight, chỉ nếu bạn không có ý định sử dụng nó trong tài khoản của bạn:  
+ Đi đến [Quicksight](https://us-east-1.quicksight.aws.amazon.com/sn/admin)
+ Cài đặt tài khoản -> Chấm dứt tài khoản