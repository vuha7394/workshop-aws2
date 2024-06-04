+++
title = 'Truy cập Cổng thông tin sự kiện AWS'
date = 2024-05-28T22:01:17+07:00
weight = 2
pre = "<b>1.2. </b>"
+++

**Truy cập Cổng thông tin sự kiện AWS:**    
Chỉ theo dõi phần này nếu bạn đang tham gia một sự kiện do AWS tổ chức (chẳng hạn như AWS Summits, Immersion Day, hoặc bất kỳ sự kiện nào khác do nhân viên AWS tổ chức). Thực hiện theo hướng dẫn của người quản lý hội thảo về cách đăng nhập vào tài khoản AWS được cung cấp cho hội thảo này. Không sử dụng tài khoản cá nhân hoặc tài khoản công việc của bạn, vì các tài nguyên được xây dựng sẵn cần thiết sẽ không có sẵn. 
Hướng dẫn đăng nhập:  
Sự kiện này yêu cầu một Tài khoản AWS và quyền truy cập vào Hướng dẫn Phòng thí nghiệm. Vui lòng thực hiện theo các bước sau:  
1. Kết nối với Workshop Studio bằng cách truy cập [Nhấp vào đây](https://catalog.workshops.aws/join).
2. Nhấp vào nút "Email One-Time Password (OTP)".
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/17.png)
1. Nhập email của bạn và nhấp vào nút "Send passcode"
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/18.png)
4.	Kiểm tra hộp thư đến của bạn để tìm email có tiêu đề "Your one-time passcode email". Sao chép mã passcode và dán vào như hình dưới đây, sau đó nhấn nút "Sign in".  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/19.png)
5.	Nhập "Mã Truy cập Sự kiện" gồm 12 ký tự nhận được từ người tổ chức sự kiện và nhấp vào "Next".
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/20.png)
6.	Đọc "Điều khoản và Điều kiện", chọn "Tôi đồng ý với Điều khoản và Điều kiện", và nhấp vào "Tham gia sự kiện". 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/21.png)
7.	Trên trang tiếp theo, nhấp vào liên kết URL "Open AWS Console".
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/22.png)
_Ô màu xanh chứa hướng dẫn từng bước, trong khi ô màu hồng cung cấp quyền truy cập tài khoản. Hãy đảm bảo rằng bạn đang ở đúng khu vực, chẳng hạn như us-west-2 (Oregon)._
8.	Mở AWS Console trong một cửa sổ trình duyệt mới. 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/23.png)
9.	Nếu bạn thấy thông báo sau, điều này có nghĩa là trình duyệt của bạn đã đăng nhập vào một tài khoản AWS khác trước đó. Nhấp vào liên kết "here" để đăng xuất khỏi tài khoản AWS Console này, và quay lại nhấp vào liên kết "Open AWS Console (region)". 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/24.png)
Chúc mừng! Bạn đã đăng nhập thành công vào AWS Console.  
10.	Thêm phần yêu cầu cho workshop của bạn  

**Thêm một quy tắc inbound vào Nhóm Bảo mật**  
Đi tới "Security groups" trong VPC để thêm một quy tắc inbound:
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/25.png)
Nhấp vào nhóm bảo mật có tên "c360view-RDS-Source" và thêm một quy tắc inbound mới:  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/26.png)
Nhấp vào "Edit inbound rules" -> "add rule" -> tìm "All TCP" -> nguồn là nhóm bảo mật "c360view-RDS-Source":  
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/27.png)
Kiểm tra kiến trúc này để xem bạn sẽ sử dụng gì trong workshop này. 
![360 customer view](/images/assets/28.png)
Bấm nút "Next" để sang phần tiếp theo  