# Objectives
  **Phần 1: Thu thập tài liệu API cần thiết**
  
  **Phần 2: Code một Bot Webex Teams**
  
# Background/Scenario
Python có thể được sử dụng để tích hợp các lệnh gọi API từ các dịch vụ khác nhau. Trong Đánh giá kỹ năng này, bạn sẽ chỉnh sửa và sửa đổi mã Python cho một bot Webex Teams tích hợp API Webex, MapQuest và ISS. Mã liên tục kiểm tra các tin nhắn trong phòng Webex Teams do người dùng chỉ định bắt đầu bằng dấu gạch chéo lên (/) theo sau là tên thành phố (ví dụ: / Washington, DC). Khi tìm thấy thông báo như vậy, tên thành phố sẽ được trích xuất và sử dụng với dịch vụ API MapQuest để lấy tọa độ GPS cho thành phố được chỉ định. Tiếp theo, các tọa độ này được sử dụng với API ISS để tìm ngày và giờ của lần tiếp theo ISS sẽ bay qua. Cuối cùng, một tin nhắn được gửi lại phòng Webex Teams thông báo cho người dùng về lần vượt tiếp theo của ISS cho thành phố được truy vấn.

Khi hoàn thành, bot của Webex Teams sẽ:
* Yêu cầu người dùng cung cấp mã thông báo truy cập của họ hoặc sử dụng mã thông báo truy cập được mã hóa cứng.
* Hiển thị danh sách các phòng Webex Teams của người dùng.
* Hỏi người dùng phòng Webex Teams nào để giám sát các truy vấn bắt đầu bằng “/”.
* Trích xuất tên thành phố của tin nhắn bắt đầu bằng “/” (ví dụ: / Washington, DC -> Washington, DC).
* Yêu cầu vĩ độ và kinh độ của một thành phố cụ thể bằng cách sử dụng API MapQuest.
* Yêu cầu ngày và giờ bay tiếp theo bằng cách sử dụng API ISS.
* Gửi thông tin cầu vượt ISS tiếp theo trở lại phòng Webex Teams đã chỉ định.

# Required Resources
* 1 PC với hệ điều hành bạn chọn
* Quyền truy cập của nhà phát triển MapQuest và Webex Teams và khóa API
* Hộp ảo hoặc VMWare
* Máy ảo DEVASC
* Tập lệnh sinh viên **devasc-sa.py**.

**Lưu ý**: Để bảo vệ các môi trường ứng dụng như Webex Teams khỏi bot hoặc các nỗ lực truy cập độc hại, hầu hết các API đều giới hạn tính khả dụng. Nếu bạn thực hiện một số lượng lớn lệnh gọi API giống nhau, lệnh gọi API của bạn có thể bị chặn trong một khoảng thời gian cụ thể. Thời gian chờ thường ít hơn 5 phút.

# Instructions
## Phần 1: Thu thập tài liệu API cần thiết.
Trong Phần này, bạn sẽ thu thập thông tin từ tài liệu API của Webex, MapQuest và ISS. Thông tin này sẽ được yêu cầu trong Phần 2 khi bạn mã hóa bot Webex Teams. Bạn cũng sẽ điều tra thư viện time Python mà bạn sẽ sử dụng để chuyển đổi dấu thời gian của kỷ nguyên thành ngày và giờ có thể đọc được của con người.
### Step 1: Launch the DEVASC VM.
### Bước 2: Điều tra tài liệu về các phòng Webex Teams và API tin nhắn.
a.	Login to your developer account for Webex. 

b.	Locate and copy your personal access token. What is the lifetime for your token? 12 hours


c.	Find the URL that will list all the rooms to which you belong. Record the HTTP method and URL:

d.	Find the URL that list all the messages for a specified room. Record the HTTP method and URL:

e.	Find the URL that will create a message for a specified room. Record the HTTP method and URL

