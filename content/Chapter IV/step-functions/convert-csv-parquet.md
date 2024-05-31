+++
title = 'Thực hiện chuyển đổi từ định dạng CSV'
date = 2024-05-28T22:01:17+07:00
weight = 1
chapter = true
pre = "<b>3.1.1. </b>"
+++

#### Thực hiện chuyển đổi từ định dạng CSV sang định dạng parquet cho các bảng gbank (ngân hàng chung), account (tài khoản) và card (thẻ), và từ định dạng JSON sang định dạng parquet cho bảng customer (CRM).
Bước 1: Nhấp vào chuyển đổi song song “2MyStateMachineToParquet-” và bắt đầu thực thi.  
![360 customer view](/images/assets/106.png) 
Bước 2: Không thay đổi các tham số, và bắt đầu thực thi.  
![360 customer view](/images/assets/107.png) 
Bước 3: Xác minh quy trình làm việc để thấy rằng trong trường hợp này, chúng ta đang thực hiện 4 chuyển đổi song song. Bạn cũng có thể chỉnh sửa để kiểm tra các truy vấn được thực hiện bằng cách sử dụng hàm Lambda để thực thi chúng trong Amazon Athena.  
Làm mới trình duyệt của bạn để kiểm tra hoàn thành.  
![360 customer view](/images/assets/108.png) 