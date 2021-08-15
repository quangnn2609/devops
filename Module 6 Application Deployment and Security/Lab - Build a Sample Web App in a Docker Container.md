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


