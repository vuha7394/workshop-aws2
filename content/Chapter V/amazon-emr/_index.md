+++
title = 'Amazon EMR'
date = 2024-05-28T22:01:17+07:00
weight = 3
chapter = true
pre = "<b>4.3. </b>"
+++

### Amazon EMR

Để tạo một bảng không chuẩn hóa, chúng ta sẽ chạy một công việc trên [Amazon EMR](https://aws.amazon.com/emr/?nc1=h_ls)  
Amazon EMR là một cụm mạnh mẽ, bạn có thể thiết lập với vài máy như trong Hội thảo này hoặc hàng chục đến hàng nghìn máy. Hãy cân nhắc sử dụng [spot instances](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-instance-purchasing-options.html) cho xử lý hàng loạt và kết thúc các cụm của bạn khi bạn không sử dụng chúng. Ngoài ra, cũng nên lưu trữ kết quả công việc trên Amazon S3. .