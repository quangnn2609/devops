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

### Bước 4: Hiển thị tệp ansible.cfg mặc định

Tệp **ansible.cfg** được Ansible sử dụng để đặt các giá trị mặc định nhất định. Các giá trị này có thể được sửa đổi.

Sử dụng đường dẫn mặc định được hiển thị trong lệnh **ansible --version**, hiển thị tệp cấu hình mặc định. Lưu ý rằng đây là một tập tin rất dài. Bạn có thể chuyển đầu ra của lệnh **cat** sang **more** để nó hiển thị từng trang một. Đánh dấu là các mục nhập sẽ có trong tệp **ansible.cfg** của bạn cho phòng thí nghiệm này.

![image](https://user-images.githubusercontent.com/83932775/132978984-dcb688dc-87c6-448c-b6d1-4d902c936d47.png)

Lưu ý rằng Ansible cho thấy rằng tệp **hosts** inventory mà nó sẽ sử dụng theo mặc định là **/etc/ansible/hosts**. Trong bước trước, bạn đã chỉnh sửa tệp **hosts** trong thư mục **ansible-csr1000v**. Trong bước tiếp theo, bạn sẽ chỉnh sửa tệp **ansible.cfg** mới sử dụng tệp **hosts** mà bạn đã tạo.

### Bước 5: Thay đổi vị trí của tệp ansible.cfg.

a. Ansible sẽ sử dụng tệp cấu hình nằm trong **/etc/ansible/ansible.cfg** trừ khi có tệp **ansible.cfg** trong thư mục hiện tại. Thay đổi trở lại thư mục **ansible-csr1000v**. Đã có tệp **ansible.cfg** trong thư mục này. Hiển thị vị trí hiện tại của **ansible.cfg** bằng lệnh **ansible --version**.

![image](https://user-images.githubusercontent.com/83932775/132985514-e96e4254-94cc-4a9d-9dc7-d434d09d0ab1.png)

b. Hiển thị tệp để thấy rằng tệp trống, ngoại trừ một nhận xét. Bạn sẽ chỉnh sửa tệp này trong bước tiếp theo.

### Bước 6: Chỉnh sửa tệp ansible.cfg.
Bây giờ, bạn cần chỉnh sửa tệp **/ansible-csr1000v/ansible.cfg** của mình để bao gồm vị trí của tệp **hosts** của bạn. Hãy nhớ rằng, tệp cấu hình mặc định trong **/etc/ansible/ansible.cfg** sử dụng tệp **hosts** trong **/etc/ansible/hosts**.

a. Mở tệp **/ansible-csr1000v/ansible.cfg** trong VS Code.

b. Bạn có thể xóa comment. Thêm các dòng sau vào tệp và lưu nó.

![image](https://user-images.githubusercontent.com/83932775/132985721-e881c908-e55e-40b6-99df-39734e8bc771.png)

Giống như Python, # được sử dụng cho các nhận xét trong tệp **ansible.cfg**. Nếu mục nhập đề cập đến tên tệp như **inventory=./hosts** thì comment không thể xuất hiện sau mục nhập. Ansible xử lý # và chú thích theo sau như một phần của tên tệp. Do đó, trong những trường hợp này, chú thích # phải nằm trên một dòng riêng biệt. Tuy nhiên, các biến có thể có **comment** trên cùng một dòng như được hiển thị cho **host_key_checking** và **retry_files_enabled**.

Tệp **ansible.cfg** cho Ansible biết nơi tìm tệp inventory và đặt các thông số mặc định nhất định. Thông tin bạn đã nhập vào tệp ansible.cfg của mình là:

* inventory=./hosts - Tệp inventory của bạn là tệp **hosts** trong thư mục hiện tại.
* host_key_checking = False - Môi trường phát triển cục bộ không có khóa SSH được thiết lập. Bạn đã đặt **host_key_checking** được đặt thành **False**, đây là giá trị mặc định. Trong mạng sản xuất, **host_key_checking** sẽ được đặt thành **True**.
* retry_files_enabled = False - Khi Ansible gặp sự cố khi chạy playbook cho một máy chủ, nó sẽ xuất tên của máy chủ đó thành một tệp trong thư mục hiện tại kết thúc bằng **.retry**. Để tránh lộn xộn, thông thường, bạn nên tắt cài đặt này.
* deprecation_warnings = False - Cảnh báo ngừng sử dụng cho biết việc sử dụng các tính năng cũ dự kiến sẽ bị loại bỏ trong bản phát hành Ansible trong tương lai. Bạn đã tắt cảnh báo này.

### Bước 7: TÓM TẮT: Tệp cấu hình Ansible của bạn.

Trong Phần này, bạn đã cấu hình Ansible để chạy trong thư mục **ansible-csr1000v**. Theo mặc định, Ansible sử dụng các tệp trong thư mục **/etc/ansible**. Tệp **/etc/ansible/ansible.cfg** mặc định cho biết tệp inventory mặc định là **/etc/ansible/hosts**.

Tuy nhiên, trong lab này, bạn cần tệp **hosts** và tệp **ansible.cfg** trong thư mục **ansible-csr1000v** của bạn.

* Bạn đã chỉnh sửa tệp **hosts** để chứa thông tin đăng nhập và địa chỉ IP cho bộ định tuyến CSR1000v.
* Bạn đã chỉnh sửa tệp **ansible.cfg** để sử dụng tệp **hosts** cục bộ làm tệp inventory (**iventory=./hosts**)

Trong Phần tiếp theo, bạn sẽ tạo một playbook để cho Ansible biết phải làm gì.
## Phần 3: Sử dụng Ansible để sao lưu cấu hình.
Trong Phần này, bạn sẽ tạo một playbook Ansible sẽ tự động hóa quá trình sao lưu cấu hình của CSR1000v. Playbook là trung tâm của Ansible. Khi bạn muốn Ansible nhận được thông tin hoặc thực hiện một hành động trên một thiết bị hoặc nhóm thiết bị, bạn chạy một playbook để hoàn thành công việc.

Một playbook Ansible là một tệp YAML chứa một hoặc nhiều plays. Mỗi plays là một tập hợp các nhiệm vụ - task.
* Một **play** là một tập hợp các nhiệm vụ phù hợp với một thiết bị hoặc một nhóm thiết bị.
* **Task** là một hành động đơn lẻ tham chiếu đến một **module** để chạy cùng với bất kỳ đối số và hành động đầu vào nào. Các **task** có thể đơn giản hoặc phức tạp tùy thuộc vào nhu cầu cấp quyền, thứ tự chạy các tác vụ, v.v.

Một playbook cũng có thể chứa các **roles**. **Role** là một cơ chế để playbook thành nhiều thành phần hoặc tệp, đơn giản hóa playbook và giúp việc sử dụng lại dễ dàng hơn. Ví dụ: **common** role được sử dụng để lưu trữ các tác vụ có thể được sử dụng trên tất cả các playbook của bạn. Các role nằm ngoài phạm vi của phòng thí nghiệm này.

Playbook Ansible YAML bao gồm các **objects**, **lists** và **modules**
*  YAML object là một hoặc nhiều cặp giá trị khóa. Các cặp giá trị khóa được phân tách bằng dấu hai chấm mà không sử dụng dấu ngoặc kép, ví dụ: **hosts:CSR1kv**
*  Một object có thể chứa các object khác như là một list. YAML sử dụng list hoặc mảng. Dấu gạch nối “-“ được sử dụng cho mỗi phần tử trong list.
*  Ansible cung cấp một module (được gọi là thư viện mô-đun) có thể được thực thi trực tiếp trên máy chủ từ xa hoặc thông qua playbook. Một ví dụ là module **ios_command** được sử dụng để gửi lệnh đến thiết bị IOS và trả về kết quả. Mỗi task thường bao gồm một hoặc nhiều module Ansible

Bạn chạy một playbook Ansible bằng lệnh **ansible-playbook**, ví dụ:

ansible-playbook backup_cisco_router_playbook.yaml -i hosts

Lệnh **ansible-playbook** sử dụng các tham số để chỉ định:

* Playbook bạn muốn chạy (**backup_cisco_router_playbook.yaml**)
* Tệp inventory và vị trí của nó (**-i hosts**).

### Bước 1: Tạo playbook Ansible của bạn.
Sách chơi Ansible là một tệp YAML. Đảm bảo rằng bạn sử dụng thụt lề YAML thích hợp. Mọi khoảng trống và dấu gạch ngang đều có ý nghĩa. Bạn có thể mất một số định dạng nếu bạn sao chép và dán mã trong lab này.

a. Trong VS Code, tạo một tệp mới trong thư mục **ansible-csr1000v** với tên sau: **backup_cisco_router_playbook.yaml**

![image](https://user-images.githubusercontent.com/83932775/132987179-112f593f-8357-4c81-a308-d4b1959ce3c8.png)

### Bước 2: Kiểm tra playbook Ansible của bạn.

Playbook bạn đã tạo chứa một play với hai task. Sau đây là phần giải thích về playbook của bạn:

* **---** Đây là phần đầu của mỗi tệp YAML, điều này cho YAML biết rằng đây là một tài liệu riêng biệt. Mỗi tệp có thể chứa nhiều tài liệu được phân tách bằng **---**.
* **name: AUTOMATIC BACKUP OF RUNNING-CONFIG** - Đây là tên của play.
* **hosts: CSR1kv** - Đây là bí danh của tệp **hosts** đã được định cấu hình trước đó. Bằng cách đề cập đến bí danh này trong playbook của bạn, playbook có thể sử dụng tất cả các thông số được liên kết với inventory này, bao gồm tên người dùng, mật khẩu và địa chỉ IP của thiết bị.
* **gather_facts: false** - Ansible ban đầu được thiết kế để hoạt động với các máy chủ Linux, sao chép các module Python vào các máy chủ để tự động hóa tác vụ. Điều này là không cần thiết khi làm việc với các thiết bị mạng.
* **connection: local** - Chỉ định rằng bạn không sử dụng SSH, do đó kết nối là cục bộ.
* **tasks:** - Từ khóa này cho biết một hoặc nhiều task sẽ được thực hiện.

Task vụ đầu tiên là hiển thị cấu hình đang chạy
* - name: DISPLAYING THE RUNNING-CONFIG - Tên của task
*  **ios_command:** - Đây là một **module** Ansible được sử dụng để gửi lệnh đến thiết bị IOS và trả về kết quả đọc được từ thiết bị. Tuy nhiên, nó không hỗ trợ các lệnh cấu hình. Mô-đun **ios_config** được sử dụng cho mục đích này, như bạn sẽ thấy trong Phần tiếp theo của phòng thí nghiệm này
*  Lưu ý: Trong terminal Linux, bạn có thể sử dụng lệnh **ansible-doc** *module_name* để xem các trang hướng dẫn sử dụng cho bất kỳ mô-đun nào và các tham số liên quan đến mô-đun đó. (ví dụ: **ansible-doc ios_command**)
*  **commands:** - Tham số này được liên kết với mô-đun **ios_command**. Nó được sử dụng để liệt kê các lệnh IOS trong playbook sẽ được gửi đến thiết bị IOS từ xa. Kết quả đầu ra từ lệnh được trả về.
*  **- show running-config** - Đây là lệnh Cisco IOS được gửi bằng module **ios_command**
*  **register: config** - Ansible bao gồm các register được sử dụng để bắt đầu ra của một tác vụ thành một biến. Mục nhập này chỉ định rằng đầu ra từ lệnh **running-config** của chương trình trước đó sẽ được lưu trữ trong  biến **config**

