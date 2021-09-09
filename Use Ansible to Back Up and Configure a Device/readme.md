# Objectives
  **Phần 1: Khởi chạy máy ảo DEVASC và máy ảo CSR1000v**
  
  **Phần 2: Cấu hình Ansible**
  
  **Phần 3: Sử dụng Ansible để sao lưu cấu hình**
  
  **Phần 4: Sử dụng Ansible để định cấu hình thiết bị**
  
# Background / Scenario
Trong phòng thí nghiệm này, bạn sẽ khám phá các nguyên tắc cơ bản về cách sử dụng Ansible để tự động hóa một số tác vụ quản lý thiết bị cơ bản. Đầu tiên, bạn sẽ cấu hình Ansible trong máy ảo DEVASC của mình. Tiếp theo, bạn sẽ sử dụng Ansible để kết nối với CSR1000v và sao lưu cấu hình của nó. Cuối cùng, bạn sẽ định cấu hình CSR1000v với địa chỉ IPv6.

# Required Resources
* 1 PC with operating system of your choice
* Virtual Box or VMWare
* DEVASC Virtual Machine
* CSR1000v Virtual Machine

# Instructions

## Phần 1: Khởi chạy máy ảo DEVASC và máy ảo CSR1000v
Trong phần này, bạn sẽ cấu hình Ansible để chạy từ một thư mục cụ thể.
### Bước 1: Mở thư mục Ansible trong VS Code.
a. Open **VS Code**.

b. Nhấp vào **File > Open Folder...** và điều hướng đến thư mục **/labs/devnet-src/ansible**.

c. Bấm **OK**.

d. Hai thư mục con cho phòng thí nghiệm Ansible hiện đã được tải trong  VS Code **EXPLORER** để thuận tiện cho bạn. Trong lab này, bạn sẽ làm việc với thư mục **ansible-csr1000v**.

### Bước 2: Chỉnh sửa Ansible inventory file
Ansible sử dụng tệp kiểm kê - inventory file được gọi là **hosts** chứa thông tin thiết bị được sử dụng bởi sách phát Ansible. Vị trí mặc định cho tệp kiểm kê Ansible là **/etc/ansible/hosts** như được chỉ định trong **ansible.cfg** mặc định trong cùng thư mục **/etc/ansible**. Các tệp mặc định này được sử dụng khi Ansible được chạy global. Tuy nhiên, trong lab bạn sẽ chạy Ansible từ thư mục **ansible-csr1000v**. Do đó, bạn cần các tệp **hosts** và **ansible.cfg** riêng biệt cho mỗi phòng thí nghiệm.

**Lưu ý**: Các thuật ngữ **hosts file** và **inventory file** đồng nghĩa và sẽ được sử dụng thay thế cho nhau trong các phòng thí nghiệm Ansible.

Tệp kiểm kê Ansible xác định các thiết bị và nhóm thiết bị được sử dụng bởi Ansible playbook . Tệp có thể ở một trong nhiều định dạng, bao gồm YAML và INI, tùy thuộc vào môi trường Ansible của bạn. Tệp kiểm kê có thể liệt kê các thiết bị theo địa chỉ IP hoặc fully qualified domain name (FQDN) và cũng có thể bao gồm các thông số cụ thể của máy chủ.

a. Mở tệp **hosts** trong thư mục **ansible-csr1000v**

b. Thêm các dòng sau vào tệp **hosts** và lưu.

![image](https://user-images.githubusercontent.com/83932775/132676137-dddff2d7-139e-4190-93f2-a42d397bf473.png)

Sau comment (#), tệp **hosts** bắt đầu bằng bí danh, **CSR1kv**. Bí danh được sử dụng từ playbook Ansible để tham chiếu thiết bị. Sau bí danh, tệp **hosts** chỉ định ba biến sẽ được sử dụng bởi Ansible playbook để truy cập thiết bị. Đây là các thông tin đăng nhập SSH mà Ansible cần để truy cập một cách an toàn vào CSR1000v VM.

* **ansible_user** là một biến chứa tên người dùng được sử dụng để kết nối với thiết bị từ xa. Nếu không có điều này, người dùng đang chạy ansible-playbook sẽ được sử dụng.
* **ansible_password** là một biến chứa mật khẩu tương ứng cho ansible_user. Nếu không được chỉ định, khóa SSH sẽ được sử dụng.
* **ansible_host** là một biến chứa địa chỉ IP hoặc FQDN của thiết bị.

### Bước 3: Hiển thị phiên bản Ansible và vị trí ansible.cfg mặc định
a. Để xem nơi Ansible lưu trữ tệp ansible.cfg mặc định, hãy mở cửa terminal và điều hướng lên một thư mục đến thư mục parent ansible.

![image](https://user-images.githubusercontent.com/83932775/132725510-70e1e676-92ac-488e-8578-8ebee639dcf2.png)

b. Nhập **ansible** để nhận danh sách các lệnh có thể trả lời. Lưu ý tùy chọn --version.

![image](https://user-images.githubusercontent.com/83932775/132725700-b0e83838-b6df-4888-b09e-9292a5df6078.png)

c. Sử dụng lệnh **ansible --version** để hiển thị thông tin phiên bản. Lưu ý rằng phòng thí nghiệm này đang sử dụng phiên bản 2.9.6. Ansible bao gồm các tệp mặc định nhất định, bao gồm tệp cấu hình mặc định, ansible.cfg.

![image](https://user-images.githubusercontent.com/83932775/132725908-612dc0bb-fa98-4a22-9082-e0a5c3c73371.png)

### 
