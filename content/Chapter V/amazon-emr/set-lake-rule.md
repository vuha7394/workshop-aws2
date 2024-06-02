+++
title = 'Cấp quyền Lake cho vai trò EMR'
date = 2024-05-28T22:01:17+07:00
weight = 1
pre = "<b>4.3.1. </b>"
+++

#### Cấp quyền Lake cho vai trò EMR đối với cơ sở dữ liệu Lake Formation.

Bước 1: Đến [Lake Formation console](https://us-west-2.console.aws.amazon.com/lakeformation/home?region=us-west-2).
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/140.png) 
Bước 2: Cấp quyền cơ sở dữ liệu cho vai trò EMR  
+ Chọn c360view_stage
+ Hành động -> Cấp quyền
+ Chọn c360vEMRExecutionRole
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/141.png)
+ Databases: c360view_stage
+ Chọn: Create Table, Alter, Drop, Describe, Super 
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/142.png) 
Bước 3: Cấp quyền bảng cho tất cả các bảng của cơ sở dữ liệu stage cho vai trò EMR.  
+ Select c360view_stage database
+ Actions -> Grant
+ Choose c360vEMRExecutionRole
+ Databases c360view_stage
+ Tables All tables
+ Table Permissions: Select, Insert, Delete, Super, Describe, Alter, Drop
![360 customer view](https://vuha7394.github.io/workshop-aws2/images/assets/143.png) 
add c360view_raw and c360view_analytics  