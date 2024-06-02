+++
title = 'Sử dụng Amazon QuickSight để tạo dataset từ Athena'
date = 2024-05-28T22:01:17+07:00
weight = 6
pre = "<b>6.1.2. </b>"
+++

#### Sử dụng Amazon QuickSight để tạo dataset từ Athena
**Bước 1: Đăng ký dịch vụ Amazon QuickSight**
1. Truy cập Amazon QuickSight Console.
2. Nhấn vào Sign up for QuickSight và điền thông tin cần thiết để đăng ký tài khoản QuickSight.

**Bước 2: Kết nối Amazon QuickSight với Athena**
1. Mở Amazon QuickSight: Sau khi đăng ký, mở QuickSight console.
2. Chọn Manage data từ thanh điều hướng trên cùng.
3. Nhấn vào New data set và chọn Athena làm nguồn dữ liệu.
4. Điền thông tin kết nối:
   - Data source name: AthenaDataSource
   - Athena workgroup: Để mặc định là primary
   - Nhấn vào Create data source.

**Bước 3: Tạo dataset từ Athena**
1. Chọn database và table từ Athena mà bạn muốn tạo dataset.
2. Chọn Edit/Preview data để xem trước dữ liệu và thực hiện các chỉnh sửa cần thiết.
3. Nhấn Save & publish để lưu dataset.

**Bước 4: Tạo trực quan hóa dữ liệu**
1. Tạo một analysis mới: Trong QuickSight, nhấn vào New analysis.
2. Chọn dataset mà bạn đã tạo từ Athena.
3. Tạo các biểu đồ: Sử dụng các công cụ trực quan hóa của QuickSight để tạo các biểu đồ và bảng điều khiển (dashboard) theo yêu cầu của bạn.