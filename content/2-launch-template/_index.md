+++
title = "Khởi tạo Launch Template"
date = 2020
weight = 2
chapter = false
pre = "<b>2. </b>"
+++
Ở phần này, bạn sẽ tạo một Launch Template sử dụng AMI bạn đã tạo từ Ubuntu Instance ở bước trước.

**Nội dung:**
- [Tạo Launch Template](#tạo-launch-template)

#### Tạo Launch Template

Để tạo Launch Template, chúng ta thực hiện như sau:
1. Truy cập vào **EC2 Management Console**.
2. Ở thanh điều hướng bên trái, chọn **Launch Templates**.
3. Ở trang khởi đầu, chọn **Create launch template**.
4. Ở trang **Create launch template**, thiết lập launch template với các thông số như sau:
   - Launch template name and description:
     - Launch template name - required: **sharenote-template** (Tên do bạn chọn)
   - Amazon machine image (AMI):
     - AMI: Lựa chọn **sharenote-image** mà chúng ta đã tạo ở bước trước.
![Launch Template](../../../images/2/2_LaunchTemplate&AMI.png?width=90pc)
   - Instance type:
     - Instance type: Lựa chọn **t2.micro** (Đây là lựa chọn cho bài thực hành, thực tế sẽ có yêu cầu cấu hình lớn hơn)
   - Key pair (login)
     - Key pair name: Lựa chọn key pair đang sử dụng của bạn.
   - Network settings:
     - Networking platform: Chọn **Virtual Private Cloud (VPC)**
     - Security groups: Lựa chọn Security Group mà bạn đã tạo ra và phù hợp. (VD: sharenote-sg)
![Launch Template](../../../images/2/2_Type&Key&Network.png?width=90pc)
5. Chọn **Create launch template** để tạo template.
6. Chọn **View lauch template** để xem template vừa được khởi tạo.
