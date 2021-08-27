# Mục tiêu

  **Phần 1: Khởi chạy máy ảo DEVASC**

  **Phần 2: Commit Sample App với Git**

  **Phần 3: Sửa đổi Sample App và đẩy các thay đổi lên Git**

  **Phần 4: Tải xuống và chạy hình ảnh Jenkins Docker**

  **Phần 5: Cấu hình Jenkins**

  **Phần 6: Sử dụng Jenkins để chạy bản dựng ứng dụng của bạn**

  **Phần 7: Sử dụng Jenkins để kiểm tra một bản dựng**

  **Phần 8: Tạo một đường ống trong Jenkins**
  
# Background / Scenario

Trong phòng thí nghiệm này, bạn sẽ commit mã Sample App vào kho lưu trữ GitHub, sửa đổi mã cục bộ và sau đó commit các thay đổi của bạn. Sau đó, bạn sẽ cài đặt một vùng chứa Docker bao gồm phiên bản Jenkins mới nhất. Bạn sẽ cấu hình Jenkins và sau đó sử dụng Jenkins để tải xuống và chạy chương trình Sample App của bạn. Tiếp theo, bạn sẽ tạo một công việc thử nghiệm bên trong Jenkins để xác minh chương trình Ứng dụng mẫu của bạn chạy thành công mỗi khi bạn xây dựng nó. Cuối cùng, bạn sẽ tích hợp Sample App và công việc thử nghiệm vào một đường dẫn Tích hợp liên tục / Phát triển liên tục sẽ xác minh Sample App của bạn đã sẵn sàng để triển khai mỗi khi bạn thay đổi mã.
 
# Part 1: Launch the DEVASC VM
# Part 2: Commit the Sample App to Git
# Part 3: Modify the Sample App and Push Changes to Git

Trong Phần 4, bạn sẽ cài đặt một image Jenkins Docker sẽ sử dụng cổng 8080. Nhớ lại rằng các tệp sample-app của bạn cũng đang chỉ định cổng 8080. Máy chủ Flask và máy chủ Jenkins không thể sử dụng 8080 cùng một lúc.

Trong phần này, bạn sẽ thay đổi số cổng được sử dụng bởi các tệp sample-app, chạy lại sample-app để xác minh nó hoạt động trên cổng mới, sau đó đẩy các thay đổi của bạn vào kho lưu trữ GitHub của bạn.

## Bước 1: Mở tệp sample-app.

Đảm bảo rằng bạn vẫn ở trong thư mục ~/labs/devnet-src/jenkins/sample-app vì đây là các tệp được liên kết với kho lưu trữ GitHub của bạn. Mở cả sample_app.py và sample-app.sh để chỉnh sửa.

## Bước 2: Chỉnh sửa tệp sample-app.

a. Trong sample_app.py, thay đổi một phiên bản của cổng 8080 thành 5050 như được hiển thị bên dưới.

![image](https://user-images.githubusercontent.com/83932775/131082634-9f312b75-746f-40c4-bc12-942046ac3fc1.png)

b. Trong sample_app.py, thay đổi một phiên bản của cổng 8080 thành 5050 như được hiển thị bên dưới.

![image](https://user-images.githubusercontent.com/83932775/131083011-061bbf86-fc03-47bc-b293-3d6c8642c394.png)

## Bước 3: Xây dựng và xác minh sample app.
a. Nhập lệnh bash để xây dựng ứng dụng của bạn bằng cổng mới 5050

![image](https://user-images.githubusercontent.com/83932775/131088379-9b992f38-5550-40c3-8459-2be15ee8dea2.png)

b. Mở tab trình duyệt và điều hướng đến localhost:5050. Bạn sẽ thấy thông báo **You are calling me from 172.17.0.1**.

![image](https://user-images.githubusercontent.com/83932775/131088574-fe7d3566-b9bb-4861-8fbf-3559eaa8afcd.png)

c. Tắt máy chủ khi bạn đã xác minh rằng nó đang hoạt động trên cổng 5050. Quay lại cửa sổ terminal nơi máy chủ đang chạy và nhấn CTRL + C để dừng máy chủ.

![image](https://user-images.githubusercontent.com/83932775/131089075-3f56c72b-940b-425e-bb85-4f9adcc2b182.png)

## Bước 4: Đẩy các thay đổi của bạn lên GitHub.

a. Bây giờ bạn đã sẵn sàng để đẩy các thay đổi của mình vào kho lưu trữ GitHub của mình. Nhập các lệnh sau.

![image](https://user-images.githubusercontent.com/83932775/131089214-d72dfe04-4d78-49dd-8dd2-f760c3e49998.png)

![image](https://user-images.githubusercontent.com/83932775/131089292-85d72e07-6f72-406d-b211-67eac69fc81b.png)

![image](https://user-images.githubusercontent.com/83932775/131089404-2ce69e86-0949-43a0-99e3-4a8902428afc.png)

b. Bạn có thể xác minh rằng kho lưu trữ GitHub của mình được cập nhật bằng cách truy cập https://github.com/githubuser/sample-app. Bạn sẽ thấy thông báo mới của mình (Đã thay đổi cổng từ 8080 thành 5050.) và dấu thời gian commit mới nhất đã được cập nhật.

![image](https://user-images.githubusercontent.com/83932775/131090220-9d76f405-8a33-4f79-afb4-52cc9555f36b.png)

# Part 4: Download and Run the Jenkins Docker Image

Trong phần này, bạn sẽ tải xuống hình ảnh Jenkins Docker. Sau đó, bạn sẽ bắt đầu một phiên bản của hình ảnh và xác minh rằng máy chủ Jenkins đang chạy.
## Step 1: Download the Jenkins Docker image.
Hình ảnh Jenkins Docker được lưu trữ tại đây: https://hub.docker.com/r/jenkins/jenkins. Tại thời điểm viết bài lab này, trang web đó chỉ định rằng bạn sử dụng lệnh docker pull jenkins/jenkins để tải xuống vùng chứa Jenkins mới nhất. Bạn sẽ nhận được đầu ra tương tự như sau:

![image](https://user-images.githubusercontent.com/83932775/131092264-a425b98e-32a6-4d23-8ba3-13297b2fe10e.png)

## Step 2: Start the Jenkins Docker container.
Nhập lệnh sau trên **một dòng**. Bạn có thể cần sao chép nó vào trình soạn thảo văn bản nếu bạn đang xem phiên bản PDF của lab này để tránh ngắt dòng. Lệnh này sẽ khởi động vùng chứa Jenkins Docker và sau đó cho phép các lệnh Docker được thực thi bên trong máy chủ Jenkins của bạn.

**docker run --rm -u root -p 8080:8080 -v jenkins-data:/var/jenkins_home -v $(which docker):/usr/bin/docker -v /var/run/docker.sock:/var/run/docker.sock -v "$HOME":/home --name jenkins_server jenkins/jenkins:lts**

Các tùy chọn được sử dụng trong lệnh chạy docker này như sau:

* **--rm** - Tùy chọn này tự động xóa vùng chứa Docker khi bạn ngừng chạy nó.
* **-u** - Tùy chọn này chỉ định người dùng. Bạn muốn vùng chứa Docker này chạy dưới dạng root để cho phép tất cả các lệnh Docker được nhập bên trong máy chủ Jenkins.
* **-p** - Tùy chọn này chỉ định cổng mà máy chủ Jenkins sẽ chạy cục bộ.
* **-v** - Các tùy chọn này ràng buộc khối lượng gắn kết cần thiết cho Jenkins và Docker. Đầu tiên -v chỉ định nơi dữ liệu Jenkins sẽ được lưu trữ. -V thứ hai chỉ định nơi lấy Docker để bạn có thể chạy Docker bên trong vùng chứa Docker đang chạy máy chủ Jenkins. -V thứ ba chỉ định biến PATH cho thư mục chính.

## Step 3: Verify the Jenkins server is running.
Máy chủ Jenkins bây giờ sẽ chạy. Sao chép mật khẩu quản trị hiển thị trong đầu ra, như được hiển thị trong hình sau. 

Không nhập bất kỳ lệnh nào trong cửa sổ máy chủ này. Nếu bạn vô tình dừng máy chủ Jenkins, bạn sẽ cần nhập lại lệnh chạy docker từ Bước 2 ở trên. Sau khi cài đặt ban đầu, mật khẩu quản trị được hiển thị như hình dưới đây.

![image](https://user-images.githubusercontent.com/83932775/131096092-be74199a-79a0-4168-acce-8c559a004f5e.png)

![image](https://user-images.githubusercontent.com/83932775/131096190-9ab99f59-2be1-4399-ba93-1e370b1f9f23.png)

**Lưu ý**: Nếu bạn mất mật khẩu hoặc nó không hiển thị như hình trên hoặc bạn cần khởi động lại máy chủ Jenkins, bạn luôn có thể lấy lại mật khẩu bằng cách truy cập vào dòng lệnh của vùng chứa Jenkins Docker. Tạo cửa sổ terminal thứ hai trong VS Code và nhập các lệnh sau để bạn không dừng máy chủ Jenkins.:

![image](https://user-images.githubusercontent.com/83932775/131096460-fbcff14c-1015-448a-96c0-05edda98123e.png)

**Lưu ý**: ID vùng chứa của bạn (19d2a847a54e được đánh dấu ở trên) và mật khẩu sẽ khác nhau.

## Bước 4: Điều tra mức độ trừu tượng hiện đang chạy trên máy tính của bạn.

Biểu đồ ASCII sau đây cho thấy các mức độ trừu tượng trong việc triển khai Docker-inside-Docker (dind) này. Mức độ phức tạp này không có gì lạ trong các mạng và cơ sở hạ tầng đám mây ngày nay.

![image](https://user-images.githubusercontent.com/83932775/131097652-a49fb083-88ae-4985-bba5-b704ce4473ca.png)

# Part 5: Cấu hình Jenkins.
Trong Phần này, bạn sẽ hoàn thành cấu hình ban đầu của máy chủ Jenkins.

## Bước 1: Mở tab trình duyệt web.
Điều hướng đến http://localhost:8080/ và đăng nhập bằng mật khẩu quản trị đã sao chép của bạn.

![image](https://user-images.githubusercontent.com/83932775/131097926-37d19a5f-68b3-4e36-b519-f16bb1bcfe50.png)

## Bước 2: Cài đặt các plugin Jenkins đề xuất.
Nhấp vào **Install suggested plugins** và đợi Jenkins tải xuống và cài đặt các plugin. Trong cửa sổ terminal, bạn sẽ thấy thông báo nhật ký khi quá trình cài đặt diễn ra. Đảm bảo rằng bạn không đóng cửa sổ terminal này. Bạn có thể mở một cửa sổ terminal khác để truy cập vào dòng lệnh.

![image](https://user-images.githubusercontent.com/83932775/131098264-6e40f9e5-6bf8-4305-9ce3-91499dd54c4a.png)

## Bước 3: Bỏ qua việc tạo người dùng quản trị mới.
Sau khi quá trình cài đặt kết thúc, bạn sẽ thấy cửa sổ **Create First Admin User**. Bây giờ, hãy nhấp vào **Skip and continue as admin** ở dưới cùng.

![image](https://user-images.githubusercontent.com/83932775/131098933-aa865818-4974-4e0e-b97e-769f6cc7e348.png)

## Step 4: Skip creating an instance configuration.
Trong cửa sổ **Instance Configuration**, không thay đổi bất kỳ điều gì. Nhấp vào **Save and Finish** ở dưới cùng.

![image](https://user-images.githubusercontent.com/83932775/131099172-839497ea-788f-4d75-b3c0-c0537adca5eb.png)

## Bước 5: Bắt đầu sử dụng Jenkins.
Trong cửa sổ tiếp theo, nhấp vào **Start using Jenkins**. Bây giờ bạn sẽ ở trên bảng điều khiển chính với thông điệp **Welcome to Jenkins!**.
# Phần 6: Sử dụng Jenkins để chạy bản dựng ứng dụng của bạn.
Đơn vị cơ bản của Jenkins là công việc - work  (còn được gọi là dự án - project). Bạn có thể tạo các công việc thực hiện nhiều nhiệm vụ khác nhau bao gồm:
* Lấy mã từ kho quản lý mã nguồn như GitHub.
* Xây dựng ứng dụng bằng cách sử dụng tập lệnh hoặc công cụ xây dựng - build tool.
* Đóng gói một ứng dụng và chạy nó trên một máy chủ.

Trong phần này, bạn sẽ tạo một công việc Jenkins đơn giản để truy xuất phiên bản mới nhất của ứng dụng mẫu của bạn từ GitHub và chạy tập lệnh xây dựng. Trong Jenkins, sau đó bạn có thể kiểm tra ứng dụng của mình (Phần 7) và thêm nó vào quy trình phát triển (Phần 8).
## Bước 1: Tạo một công việc mới.
a. Nhấp vào liên kết **Create a job** ngay bên dưới phần thông điệp **Welcome to Jenkins!**. Ngoài ra, bạn có thể nhấp vào **New Item** trong menu bên trái.
![image](https://user-images.githubusercontent.com/83932775/131102205-90034dc5-6b2b-4588-902d-8b70d07c52fb.png)

b. Trong trường **Enter an item name**, hãy điền tên **BuildAppJob**.
![image](https://user-images.githubusercontent.com/83932775/131102442-1020c166-6ad9-410a-9308-1bb44d6cbc6c.png)

c. Nhấp vào **Freestyle project** làm loại công việc. Trong mô tả, chữ viết tắt SCM là viết tắt của quản lý cấu hình phần mềm - stands for software, là một phân loại phần mềm có nhiệm vụ theo dõi và kiểm soát các thay đổi trong phần mềm.
![image](https://user-images.githubusercontent.com/83932775/131102632-10cf4257-1571-421d-affd-be24c2a186c8.png)

d. Cuộn xuống dưới cùng và nhấp vào OK.
## Bước 2: Định cấu hình Jenkins BuildAppJob.
Bây giờ bạn đang ở trong cửa sổ cấu hình, nơi bạn có thể nhập thông tin chi tiết về công việc của mình. Các tab trên cùng chỉ là lối tắt cho các phần bên dưới. Nhấp qua các tab để khám phá các tùy chọn bạn có thể định cấu hình. Đối với công việc đơn giản này, bạn chỉ cần thêm một vài chi tiết cấu hình.

a. Nhấp vào **General tab**, thêm mô tả cho công việc của bạn. Ví dụ: **"My first Jenkins job."**
![image](https://user-images.githubusercontent.com/83932775/131103043-ac857053-bced-4394-93aa-528c31223722.png)

b. Nhấp vào tab **Source Code Management** và chọn nút radio **Git**. Trong trường URL kho lưu trữ, hãy thêm liên kết kho lưu trữ GitHub của bạn để ứng dụng mẫu nhập tên người dùng phân biệt chữ hoa chữ thường của bạn. Đảm bảo thêm phần mở rộng .git vào cuối URL của bạn. Ví dụ:

![image](https://user-images.githubusercontent.com/83932775/131103516-d077a69d-c591-42e2-a4c8-cb30db3a3a25.png)

c. Đối với **Credentials**, hãy nhấp vào nút **Add** và chọn **Jenkins**.

d. Trong hộp thoại **Add Credentials**, hãy điền tên người dùng và mật khẩu GitHub của bạn, sau đó nhấp vào **Add**.
![image](https://user-images.githubusercontent.com/83932775/131103906-df9f7860-5a12-4ba9-abe4-793ef59d1be5.png)

**Lưu ý**: Bạn sẽ nhận được thông báo lỗi rằng kết nối không thành công. Điều này là do bạn chưa chọn thông tin đăng nhập.

e. Trong menu thả xuống dành cho **Credentials** hiện có thông **None**, hãy chọn thông tin đăng nhập bạn vừa định cấu hình.
![image](https://user-images.githubusercontent.com/83932775/131104350-0c41cd61-b67e-4bce-b989-865f5ccf8451.png)

f. Sau khi bạn đã thêm đúng URL và thông tin đăng nhập, Jenkins kiểm tra quyền truy cập vào kho lưu trữ. Bạn sẽ không có thông báo lỗi. Nếu bạn làm vậy, hãy xác minh URL và thông tin đăng nhập của bạn. Bạn sẽ cần phải Thêm lại chúng vì không có cách nào tại thời điểm này để xóa những cái bạn đã nhập trước đó.

g. Ở đầu cửa sổ cấu hình **BuildAppJob**, nhấp vào tab **Build**

![image](https://user-images.githubusercontent.com/83932775/131104620-4336475b-3233-4376-a2dd-19f2719db66d.png)

h. Đối với menu thả xuống **Add build step**, hãy chọn **Execute shell**.

i. Trong trường **Command**, nhập lệnh bạn sử dụng để chạy tập lệnh xây dựng cho sample-app.sh.
![image](https://user-images.githubusercontent.com/83932775/131105005-15c63417-3fec-4fc9-8296-8efeee26094f.png)

j. Nhấp vào nút **Save**. Bạn được quay lại bảng điều khiển Jenkins với **BuildAppJob** được chọn.

## Bước 3: Yêu cầu Jenkins xây dựng ứng dụng.
Ở phía bên trái, nhấp vào **Build Now** để bắt đầu công việc. Jenkins sẽ tải xuống kho lưu trữ Git của bạn và thực hiện lệnh xây dựng **bash ./sample-app.sh**. Quá trình xây dựng của bạn sẽ thành công vì bạn đã không thay đổi bất kỳ điều gì trong mã kể từ Phần 3 khi bạn sửa đổi mã.

![image](https://user-images.githubusercontent.com/83932775/131105409-61f74627-f701-4344-bfe5-024ddc60c351.png)

## Bước 4: Truy cập chi tiết bản dựng.
Ở bên trái, trong phần **Build History**, hãy nhấp vào số bản dựng của bạn, số bản dựng sẽ là **#1** trừ khi bạn đã tạo ứng dụng nhiều lần.

![image](https://user-images.githubusercontent.com/83932775/131105672-d4a2ed8a-f97a-4dfd-a37d-ea3bffbd73a5.png)

## Bước 5: Xem kết quả đầu ra của bảng điều khiển.
Ở bên trái, nhấp vào **Console Output**. Bạn sẽ thấy đầu ra tương tự như sau. Lưu ý các thông báo thành công ở dưới cùng cũng như đầu ra từ lệnh **docker ps -a**. Hai bộ chứa docker đang chạy: một cho sample-app của bạn đang chạy trên cổng cục bộ 5050 và một cho Jenkins trên cổng cục bộ 8080.

![image](https://user-images.githubusercontent.com/83932775/131106359-37ee9a74-18e6-4795-98f1-5dda13d6b882.png)

## Bước 6: Mở tab trình duyệt web khác và xác minh sample-app đang chạy.
Nhập địa chỉ cục bộ, **localhost:5050**. Bạn sẽ thấy nội dung của index.html của bạn được hiển thị bằng màu nền xanh thép nhạt với **You are calling me from 172.17.0.1** được hiển thị dưới dạng H1.
![image](https://user-images.githubusercontent.com/83932775/131106616-3b8c0b46-b763-4b98-82fe-103b3ead82ca.png)


