# Mục tiêu
**Phần 1: Khởi chạy máy ảo DEVASC
Phần 2: Tạo một tập lệnh Bash đơn giản
Phần 3: Tạo một ứng dụng web mẫu
Phần 4: Định cấu hình ứng dụng web để sử dụng tệp trang web
Phần 5: Tạo tập lệnh Bash để xây dựng và chạy vùng chứa Docker
Phần 6: Xây dựng, chạy và xác minh vùng chứa Docker**

# Bối cảnh / Kịch bản

Trong phòng thí nghiệm này, bạn sẽ xem xét các kỹ thuật kịch bản bash cơ bản vì tập lệnh bash là điều kiện tiên quyết cho phần còn lại của phòng thí nghiệm. Sau đó, bạn sẽ xây dựng và sửa đổi một tập lệnh Python cho một ứng dụng web đơn giản. Tiếp theo, bạn sẽ tạo một tập lệnh bash để tự động hóa quy trình tạo Dockerfile, xây dựng vùng chứa Docker và chạy vùng chứa Docker. Cuối cùng, bạn sẽ sử dụng các lệnh docker để điều tra sự phức tạp của thể hiện vùng chứa Docker.

# Required Resources

* 1 PC với hệ điều hành bạn chọn
* Virtual Box hoặc VMWare
* Máy ảo DEVASC

# Instructions

## Part 1: Launch the DEVASC VM
## Part 2: Create a Simple Bash Script

Kiến thức Bash rất quan trọng để làm việc với tích hợp liên tục, triển khai liên tục, vùng chứa và với môi trường phát triển của bạn. Tập lệnh Bash giúp các lập trình viên tự động hóa nhiều tác vụ trong một tệp tập lệnh. Trong phần này, bạn sẽ xem xét ngắn gọn cách tạo bash script. Sau đó trong phòng thí nghiệm, bạn sẽ sử dụng tập lệnh bash để tự động tạo ứng dụng web bên trong vùng chứa Docker.

### Step 1: Create an empty bash script file
Thay đổi thư mục làm việc của bạn thành **~/labs/devnet-src/sample-app** và thêm một tệp mới có tên là **user-input.sh**.
![image](https://user-images.githubusercontent.com/83932775/129483398-a9ed8de4-f02c-4932-8d37-66e568a80dba.png)

### Step 2: Open the file in the text editor.
### Step 3: Add the ‘she-bang’ to the top of the script.
#!/bin/bash
### Step 4: Add simple bash commands to the script.

Nhập một số lệnh bash đơn giản cho tập lệnh của bạn. Các lệnh sau sẽ yêu cầu người dùng nhập tên, đặt tên cho một biến có tên là userName và hiển thị một chuỗi văn bản có tên của người dùng.
![image](https://user-images.githubusercontent.com/83932775/129484622-6e222c92-a598-4e68-893a-e50909b9b937.png)

### Step 5: Exit and save your script.
### Step 6: Run your script from the command line.
![image](https://user-images.githubusercontent.com/83932775/129484649-904524ca-f3a0-4e04-b16c-c84bb194fe35.png)
### Step 7: Change the mode of the script to an executable file for all users.
Thay đổi chế độ của tập lệnh thành tập lệnh thực thi bằng lệnh chmod. Đặt các tùy chọn thành a + x executable (x) có thể thực thi bởi tất cả người dùng all users (a). Sau khi sử dụng chmod, quyền đã được sửa đổi cho người dùng, nhóm và những người khác để bao gồm "x" (có thể thực thi).

![image](https://user-images.githubusercontent.com/83932775/129486475-b01eaebd-39f2-4462-843d-583aa657b854.png)
### Step 8: Rename the file to remove the .sh extension.
Bạn có thể đổi tên tệp để loại bỏ phần mở rộng để người dùng không phải thêm .sh vào lệnh để thực thi tập lệnh.

**mv user-input.sh user-input**
### Step 9: Execute the script from the command line.
Bây giờ tập lệnh có thể được chạy từ dòng lệnh mà không cần lệnh nguồn hoặc phần mở rộng. Để chạy tập lệnh bash mà không có lệnh nguồn, bạn phải mở đầu tập lệnh bằng "./".
![image](https://user-images.githubusercontent.com/83932775/129511286-36419651-13e3-458c-b10c-ee6cc756f564.png)
### Step 10: Investigate other bash scripts.
Nếu bạn có ít hoặc không có kinh nghiệm tạo tập lệnh bash, hãy dành chút thời gian để tìm kiếm trên internet các hướng dẫn về bash, ví dụ về bash và trò chơi bash.
## Part 3: Create a Sample Web App
Trước khi có thể khởi chạy ứng dụng trong vùng chứa Docker, trước tiên chúng ta cần có ứng dụng đó. Trong phần này, bạn sẽ tạo một script Python rất đơn giản, nó sẽ hiển thị địa chỉ IP của máy khách khi máy khách truy cập trang web.
### Step 1: Install Flask and open a port on the DEVASC VM firewall.
Các nhà phát triển ứng dụng web sử dụng Python thường sử dụng một framework. Framework là một thư viện mã để giúp các nhà phát triển dễ dàng hơn trong việc tạo các ứng dụng web đáng tin cậy, có thể mở rộng và có thể bảo trì. Flask là một framework ứng dụng web được viết bằng Python. Các framework khác bao gồm Tornado và Pyramid.

Bạn sẽ sử dụng framework này để tạo ứng dụng web mẫu. Flask nhận yêu cầu và sau đó cung cấp phản hồi cho người dùng trong ứng dụng web. Điều này rất hữu ích cho các ứng dụng web động vì nó cho phép người dùng tương tác và nội dung động. Điều làm cho ứng dụng web mẫu của bạn trở nên động là nó sẽ hiển thị địa chỉ IP của ứng dụng khách.

Lưu ý: Việc hiểu các hàm, phương thức và thư viện của Flask nằm ngoài phạm vi của khóa học này. Nó được sử dụng trong phòng thí nghiệm này để cho biết bạn có thể thiết lập và chạy một ứng dụng web nhanh như thế nào. Nếu bạn muốn tìm hiểu thêm, hãy tìm kiếm trên internet để biết thêm thông tin và hướng dẫn về khung công tác Flask. 

### Step 2: Open the sample_app.py file.
### Step 3: Add the commands to import methods from flask.
Thêm các lệnh sau để nhập các phương thức cần thiết từ thư viện flask.

![image](https://user-images.githubusercontent.com/83932775/129525938-ed755ff7-0abd-4141-8db2-9b795dbfd2c2.png)

### Step 4: Create an instance of the Flask class.
Tạo một instancecủa lớp Flask và đặt tên cho nó là **sample**. Đảm bảo sử dụng hai dấu gạch dưới trước và sau "name".

![image](https://user-images.githubusercontent.com/83932775/129526009-24e9f06e-0524-4fb9-a2b7-d862013cb7ee.png)
### Step 5: Define a method to display the client IP address.
Tiếp theo, cấu hình Flask để khi người dùng truy cập trang mặc định (root directoty), nó sẽ hiển thị một thông báo với địa chỉ IP của máy khách.

Lưu ý câu lệnh @sample.route("/"). Các framework như Flask sử dụng kỹ thuật định tuyến (.route) để tham chiếu đến một URL ứng dụng (điều này không bị nhầm lẫn với định tuyến mạng). Ở đây, "/" (thư mục gốc) được liên kết với hàm main(). Vì vậy, khi người dùng truy cập vào URL http://localhost:8080/ (thư mục gốc), kết quả của câu lệnh trả về sẽ được hiển thị trong trình duyệt.

![image](https://user-images.githubusercontent.com/83932775/129527052-2db3d95a-8cdf-4701-96a3-0d38fe56f575.png)

### Step 6: Configure the app to run locally.
Cuối cùng, định cấu hình Flask để chạy ứng dụng cục bộ tại http://0.0.0.0:8080, cũng là http://localhost:8080. Đảm bảo sử dụng hai dấu gạch dưới trước và sau "name", trước và sau "main".
![image](https://user-images.githubusercontent.com/83932775/129527411-1b066ec2-0738-4c2d-b029-9bbaf002d4af.png)

### Step 7: Save and run your sample web app.
Lưu tập lệnh của bạn và chạy nó từ command line. Bạn sẽ thấy kết quả sau cho biết máy chủ “sample-app” của bạn đang chạy. Nếu bạn không thấy kết quả sau hoặc nếu bạn nhận được thông báo lỗi, hãy kiểm tra kỹ tập lệnh sample_app.py của bạn.

![image](https://user-images.githubusercontent.com/83932775/129527610-b2d79664-17bd-4038-b8a6-d35349491594.png)

### Step 8: Verify the server is running.
Bạn có thể xác minh máy chủ đang chạy bằng một trong hai cách.
a. Mở web brower và truy cập vào 0.0.0.0:8080 bạn sẽ nhận được ouput như bên dưới:

![image](https://user-images.githubusercontent.com/83932775/129528514-f2a29d63-aeca-4c17-8814-ad4eab676fb0.png)

Nếu bạn nhận được phản hồi "HTTP 400 Bad Request", hãy kiểm tra kỹ tập lệnh sample_app.py của bạn.
b. Mở một terminal khác và sử dụng command-line URL tool (cURL) để xác minh phản hồi của máy chủ.
![image](https://user-images.githubusercontent.com/83932775/129534417-52c5f2b3-12a7-4c06-b8e9-395193aae688.png)
### Step 9: Stop the server.
Press CTRL+C to stop the server.
## Part 4: Configure the Web App to use Website Files.
Trong phần này, hãy xây dựng ứng dụng sample web app để bao gồm trang index.html và đặc tả style.css. index.html thường là trang đầu tiên được tải trong trình duyệt web của khách hàng khi truy cập trang web của bạn. style.css là một style sheet được sử dụng để tùy chỉnh giao diện của trang web.

### Step 1: Explore the directories that will be used by the web app.
Các mẫu thư mục và tĩnh đã có trong thư mục sample-app. Mở index.html và style.css để xem nội dung của chúng. Nếu bạn đã quen với HTML và CSS, hãy thoải mái tùy chỉnh các thư mục và tệp này tùy thích. Tuy nhiên, hãy đảm bảo rằng bạn giữ mã Python {{request.remote_addr}} được nhúng trong tệp index.html vì đây là khía cạnh động của ứng dụng web mẫu.

![image](https://user-images.githubusercontent.com/83932775/129561825-f684433b-b9f2-4152-a879-13ad0ad24b12.png)
![image](https://user-images.githubusercontent.com/83932775/129561888-7fdb187e-ed50-47fc-86f4-83f0bd454f8e.png)
### Step 2: Update the Python code for the sample web app.
Bây giờ bạn đã khám phá các tệp trang web cơ bản, bạn cần cập nhật tệp sample_app.py để nó hiển thị tệp index.html thay vì chỉ trả lại dữ liệu. Việc tạo nội dung HTML bằng mã Python có thể phức tạp, đặc biệt khi sử dụng các câu lệnh có điều kiện hoặc cấu trúc lặp lại. Tệp HTML có thể được hiển thị tự động trong Flask bằng cách sử dụng hàm render_template. Điều này yêu cầu nhập phương thức render_template từ thư flask và chỉnh sửa thành hàm trả về. Thực hiện các chỉnh sửa được đánh dấu cho tập lệnh của bạn.
![image](https://user-images.githubusercontent.com/83932775/129562322-52951f42-53bb-4051-992a-f7c47e145d8e.png)
### Step 3: Save and run your script.
Lưu và chạy tập lệnh sampe-app.py của bạn. Bạn sẽ nhận được đầu ra như sau:
![image](https://user-images.githubusercontent.com/83932775/129567809-08e23b48-b1d3-48fb-90ca-e41aa83b4188.png)

Lưu ý: Nếu bạn nhận được đầu ra Traceback và lỗi với thông báo có nội dung như OSError: OSError: [Errno 98] Address already in use, thì bạn đã không tắt máy chủ trước đó của mình. Quay lại cửa terminal nơi máy chủ đó đang chạy và nhấn CTRL + C để kết thúc quá trình máy chủ. Chạy lại tập lệnh của bạn.

### Step 4: Verify your program is running.
Một lần nữa, bạn có thể xác minh chương trình của mình đang chạy theo một trong hai cách.

a. Mở trình duyệt web Chromium và nhập 0.0.0.0:8080 vào trường URL. Bạn sẽ nhận được đầu ra tương tự như trước đây. Tuy nhiên, nền của bạn sẽ có màu xanh thép nhạt và văn bản sẽ được định dạng là H1.

![image](https://user-images.githubusercontent.com/83932775/129569719-a1dd60b0-1cbc-41ca-952f-2d11d69cf3e9.png)

b. Mở một terminal khác và sử dụng lệnh curl để xác minh phản hồi của máy chủ. Đây là nơi bạn sẽ thấy kết quả của mã HTML được hiển thị tự động bằng cách sử dụng hàm render_template. Trong trường hợp này, bạn sẽ nhận được tất cả nội dung HTML. Tuy nhiên, mã Python động sẽ được thay thế bằng giá trị cho {{request.remote_addr}}. Ngoài ra, hãy lưu ý lời nhắc của bạn sẽ nằm trên cùng dòng với dòng cuối cùng của đầu ra HMTL. Nhấn ENTER để nhận một dòng mới.

![image](https://user-images.githubusercontent.com/83932775/129570229-2d5bf1bf-43ba-44f9-844b-9fef77435bda.png)
### Step 5: Stop the server.
## Part 5: Tạo tập lệnh Bash để xây dựng và chạy vùng chứa Docker .
Một ứng dụng có thể được triển khai trên một máy chủ bare metal (máy chủ vật lý dành riêng cho môi trường một người thuê) hoặc trong một máy ảo, giống như bạn vừa làm trong Phần trước. Nó cũng có thể được triển khai trong một giải pháp chứa như Docker. Trong phần này, bạn sẽ tạo một tập lệnh bash và thêm các lệnh vào đó để hoàn thành các tác vụ sau để xây dựng và chạy vùng chứa Docker:

* Tạo thư mục tạm thời để lưu trữ các tập tin trang web.
* Sao chép các thư mục trang web và sample_app.py vào thư mục tạm thời.
* Xây dựng một Dockerfile.
* Xây dựng vùng chứa Docker.
* Khởi động vùng chứa và xác minh rằng nó đang chạy

### Bước 1: Tạo các thư mục tạm thời để lưu trữ các tập tin của trang web.
