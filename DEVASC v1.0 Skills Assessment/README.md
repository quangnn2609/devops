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

b.	Locate and copy your personal access token. What is the lifetime for your token? 

12 hours

c.	Find the URL that will list all the rooms to which you belong. Record the HTTP method and URL:

https://webexapis.com/v1/rooms GET

d.	Find the URL that list all the messages for a specified room. Record the HTTP method and URL:

https://webexapis.com/v1/messages GET

e.	Find the URL that will create a message for a specified room. Record the HTTP method and URL

https://webexapis.com/v1/messages POST

### Bước 3: Điều tra khóa vị trí cho API địa chỉ MapQuest.

a.	Login to your developer account for MapQuest.

b.	Locate and copy your Consumer Key. When does your key expire? 

Never

The Webex Teams bot will use location data returned by a call to the MapQuest address API. 

c.	Open Chromium and paste in the following URL, replacing your_api_key with your MapQuest key:

https://www.mapquestapi.com/geocoding/v1/address?key=jPQyskdG6120exKDXl602AAshQBgL###&location=Washington,DC

d.	Notice that the MapQuest locations key includes keys for latitude and longitude for the location you entered. Record the lat and lng values returned by MapQuest for Washington, D.C in the code below.

![image](https://user-images.githubusercontent.com/83932775/131456144-1fba6b34-df2f-44aa-b1d8-5edddafa10db.png)

### Bước 4: Điều tra tài liệu cho API số lần vượt qua ISS.
a.	Search for “ISS API documentation” on the internet. 

b.	On the ISS API documentation website, click the API documentation for ISS Pass Times.

The IIS Pass Times API has been removed in document.

![image](https://user-images.githubusercontent.com/83932775/131461515-9434f7fd-66f0-420a-b25c-8f495c2f0c47.png)

But we can still use IIS Current Location

http://api.open-notify.org/iss-now.json returns a longitude and latitude with a timestamp. We can feed that into mapquest reverse geocoding API.

c.	What are the two required parameters (called query strings on the website) for the ISS pass times API?

This API takes no inputs.

d.	What are the optional parameters for the ISS pass times API?

There are none, the api just returns the current location latidue and longitude for the current time.
{
iss_position: {
longitude: "49.0568",
latitude: "-6.2759"
},
message: "success",
timestamp: 1630398534
}

e.	What is the URL for the ISS pass times API?

The IIS Pass Times API has been removed in document.

### Bước 5: Điều tra khóa phản hồi cho API số lần vượt qua ISS.
### Bước 6: Điều tra epouch time và cách chuyển đổi chúng sang định dạng con người có thể đọc được.

Trong Phần 2, bạn sẽ sử dụng hàm **ctime** của thư viện **time** Python để chuyển đổi epouch time thành ngày và giờ có thể đọc được của con người. Ngày và giờ đó sau đó sẽ được kết hợp trong một thông báo mà bot của Webex Teams đăng lên một phòng.

Tìm kiếm trên internet tài liệu về thư viện **time** Python để trả lời các câu hỏi sau. Tốt hơn là bạn nên xem lại tài liệu từ python.org mặc dù câu trả lời có thể được tìm thấy ở những nơi khác.

a.	In relation to computer time, what does the term “epoch” mean?

The epoch is the point where the time starts, and is platform dependent. For Unix, the epoch is January 1, 1970, 00:00:00 (UTC).

b.	What function of the time library will return the epoch time on a given platform?

To find out what the epoch is on a given platform, look at time.gmtime(0)

c.	You can see the year, month, day, hour, and so on for the start of the epoch with the following Python code. Open a terminal, start Python 3, import the time library, and then replace <function> with the function you found above.
devasc@labvm:~$ python3
Python 3.8.2 (default, Apr 27 2020, 15:53:34) 
[GCC 9.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import time
>>> print(str(time.gmtime(0)))
time.struct_time(tm_year=1970, tm_mon=1, tm_mday=1, tm_hour=0, tm_min=0, tm_sec=0, tm_wday=3, tm_yday=1, tm_isdst=0)
>>>
 
 ![image](https://user-images.githubusercontent.com/83932775/131474343-7f0a90e6-1298-43e2-9ea2-05fa485b3ff6.png)

d.	The DEVASC VM epoch start time is the same as for Unix. When does the epoch start?

For Unix, the epoch is January 1, 1970, 00:00:00 (UTC)
 
e.	The risetime in Step 4 is expressed in the number of seconds since the epoch time. What time function will convert the risetime to a human readable format?
 
>>> time.strftime("%d-%m-%Y %H:%M:%S", time.gmtime(1630400908))
 
 ![image](https://user-images.githubusercontent.com/83932775/131475947-4a7f303a-9e75-4938-b702-fa53182ae6b4.png)

 
f.	What is the date for the first risetime in Step 4? 
>>> print(str(time.strftime("%d-%m-%Y %H:%M:%S", time.gmtime(1630400908)))))
<Date and Time is printed here>
>>>
 
 ![image](https://user-images.githubusercontent.com/83932775/131476756-9cd248b5-ee09-4916-a3b3-e77258dcc33f.png)

 

