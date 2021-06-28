+++
title = "Tạo Security Group"
date = 2020
weight = 1
chapter = false
pre = "<b>1.1. </b>"
+++

Chúng ta sẽ bắt đầu bằng việc tạo một Security Group cho tất cả các thành phần trong [**kiến trúc**](../) của bài lab này.

**Nội dung:**
- [Tạo Security Group](#tạo-security-group)

Để xác định các rule Inbound cần có, chúng ta liệt kê ra các yêu cầu như sau:
- Người dùng truy cập từ ngoài vào ứng dụng ShareNote thông qua cổng 80 bằng giao thức HTTP với Source IP bất kì.
- Load Balancer sẽ điều phối các yêu cầu này đến các server thông qua cổng 8080 với Source IP trong VPC.
- Các Application server sẽ giao tiếp với Database thông qua cổng 3306 với Source IP trong VPC.
- Chúng ta sẽ mở truy cập SSH để có thể kết nối đến instance để triển khai ứng dụng.

{{% notice note %}}
Trên thực tế, chúng ta nên tạo các security group riêng biệt cho từng thành phần. Tuy nhiên trong khuôn khổ bài thực hành này, chúng ta sẽ sử dụng một security group (Các rule không trùng lẫn nhau).
{{% /notice %}}

#### Tạo Security Group

1. Truy cập vào **EC2 Management Console** bằng cách gõ và chọn dịch vụ **EC2** trong thanh tìm kiếm.
![Find EC2](../../../images/1/1.1_FindEC2.png?width=90pc)
2. Ở thanh điều hướng bên trái, chọn **Security Groups**.
3. Ở trang **Security Groups**, chọn **Create Security Group**.
4. Ở trang **Create security group**, thiết lập các thông số như sau:
   - Mục **Basic details**:
     - Security group name: Nhập vào tên security group (VD: **sharenote-sg**)
     - Description: Nhập vào diễn giải của security group.
     - VPC: Chọn Default VPC. *Bạn sẽ xây dựng bài lab này bên trong Default VPC*.
{{% notice note %}}
Trên thực tế, AWS khuyến cáo rằng bạn không không nên sử dụng Default VPC cho mục dích sản xuất. Tuy nhiên, bạn sẽ sử dụng Default VPC để được thuận tiện trong khuôn khổ bài thực hành này.
{{% /notice %}}
   - Mục **Inbound rules**: Thêm các **Inbound rule** như đề cập ở trên. Chọn **Add rule** để thêm một rule.
     - Type: **HTTP** | Source: **Anywhere**
     - Type: **Custom TCP** | Port range: **8080** | Source: Custom **172.31.0.0/16** (Default VPC CIDR block)
     - Type: **MySQL/Aurora** | Source: Custom **172.31.0.0/16** (Default VPC CIDR block)
     - Type: **SSH** | Source: **My IP**
![Security Group](../../../images/1/1.1_ConfigureSG.png?width=90pc)
5. Chọn **Create security group**.

Đến đây, chúng ta đã hoàn thành việc tạo Security Group.