# Understanding Deployment Choices with Different Models
## Introduction to Deployment Choices
Ngay khi bạn là một solo developer xây dựng ứng dụng cho chính mình, khi triển khai ứng dụng, bạn phải tính đến một số yếu tố khác nhau, từ việc tạo một môi trường thích hợp, đến việc xác định đúng cơ sở hạ tầng, các khái niệm bảo mật cơ bản. Điều này có nghĩa là các nhà phát triển ứng dụng cần làm nhiều việc hơn là chỉ viết code: họ cần quan tâm đến cách ứng dụng được triển khai, bảo mật, vận hành, giám sát và duy trì.

Trong khí đó, cơ sở hạ tầng vật lý và ảo hóa và nền tảng mà các ứng dụng đang được phát triển và triển khai ngày càng phát triển nhanh chóng. Một phần của việc phát triển nhanh chóng này là giúp công việc của các nhà phát triển trở nên dễ dàng hơn. Ví dụ: Các mô hình như Containers as a Service và Serverless được thiết kế để cho phép các phát triển xây dựng các chức năng cốt lỗi của ứng dụng mà không cần quan tâm đến việc cấu hình các nền tảng cơ bản, cơ chế, khả năng mở rộng, và các hoạt động khác.

Nhưng không phải tất cả các sự phát triển ứng dụng hiện tại điều diễn ra trên các nên tảng này. Các nhà phát triển phái đối mặt với một "đống" các tùy chọn về nền tảng như: Bare-metal (Máy chủ vật lý), máy ảo, container và những thứ khác tất cả đều được lưu trữ trên cơ sở hạ tầng và các framework ngày càng linh hoạt và phức tạp.
## Deployment Environments
Một số hỗn loạn trong giai đoạn đầu của quá trình phát triển là bình thường, nhưng code cần được kiểm tra kỹ lưỡng trước khi nó đến tay người dùng. Để điều đó xảy ra, code cần phải trải qua một loạt các bước để cải thiện độ tin cậy của nó. Code đi qua một số môi trường, và như vậy, chất lượng và độ tin cậy của nó tăng lên. Các môi trường này là độc lập và nhằm mục đích bắt chước môi trường cuối cùng mà mã sẽ "sống".

Thông thường, các tổ chức lớn sử dụng cấu trúc bốn cấp: development, testing, staging, và production.

**Development environment**

The development environment (Môi trường phát triển) là nơi bạn viết code của mình. Thông thường, môi trường phát triển của bạn ít giống với môi trường cuối cùng. Môi trường phát triển thường chỉ đủ để bạn quản lý các khía cạnh cơ bản của cơ sở hạ tầng của mình, chẳng hạn như container hoặc mạng đám mây. Bạn có thể sử dụng Integrated Development Environment (Môi trường phát triển tích hợp - IDE) hoặc công cụ khác để triển khai dễ dàng hơn.

Môi trường này cũng có thể bao gồm các tài nguyên “mock (giả)” cung cấp hình thức của các tài nguyên thực, nhưng không bao gồm nội dung. Ví dụ: bạn có thể có một cơ sở dữ liệu với số lượng bản ghi thử nghiệm tối thiểu hoặc một ứng dụng bắt chước đầu ra của một dịch vụ từ xa. Mỗi nhà phát triển thường có môi trường phát triển riêng của họ.

**Testing environment**

Sau khi bạn đã viết code xong, bạn phải chuyển code của mình sang môi trường thứ hai được dành riêng cho việc kiểm thử code (testing), mặc dù khi làm việc trên các dự án nhỏ môi trường kiểm phát triển và môi trường kiểm tra thường kết hợp với nhau. Ở môi trường kiểm thử này phải có cấu trúc tương tự như môi trường production ở bước cuối cùng, ngay cả khi nó ở quo mô nhỏ hơn nhiều.

Môi trường kiểm tra thường bao gồm các công cụ kiểm tra tự động như Jenkins, CicrleCI, hoặc Travis CI cũng như tích hợp với hệ thống kiểm soát phiên bản (version control system). Nó được chia sẽ với toàn bộ các team. Nó cũng bao gồm các công cụ preview code như Gerrit.

**Staging environment**

Sau khi code được kiểm thử, nó sẽ được chuyển sang môi trường Staging (một bản sau gần chính xác của môi trường production). staging càng gần với môi trường sản xuất thực tế thì càng tốt. Thay vì sử dụng môi trường staging ở quy mô nhỏ, một số tổ chức sử dũng hai môi trường sàn xuất, một trong số đó lưu trữ bản phát hành hiện tại của ứng dụng, môi trường còn lại chờ nhận bản phát hành mới. Trong trường hợp này, khi phiển bản mới được triển khai lưu lượng truy cập sẽ được chuyển (từ từ hoặc đột ngột nhầm mục đích cắt giảm) từ môi trường sản xuất hiện tại tới môi trường sản xuất còn lại. Với bản phát hành tiếp theo, qui trình sẽ được thực hiện ngược lại.

Tất nhiên chi phí sẽ phải chăng hơn nhiều trong cloud, nơi một môi trường ảo hóa không được sử dụng có được chia nhỏ và tự động xây dựng lại khi cần thiết.

**Production environment**

Cuối cùng code sẽ được đưa tới môi trường Production (môi trường sản xuất), nơi người dùng cuối tương tác. Tại thời điểm này code đã được kiểm thử nhiều lần và nó không nên xuất hiện lỗi. Môi trường sản xuất phải có đủ kích cỡ và xây dựng để xử lý các lưu lượng truy cập dự kiến, bao gồm các đợt tăng đột biến theo mùa hoặc theo một sự kiện cụ thể.

Xử lý lượng gia tặng đó là điều bạn phải lên kế hoạch khi xây dựng cơ sở hạ tầng của mình. Tuy nhiên, trước khi xem xét cơ sở hạ tầng bạn cần biết với các mô hình khác nhau mà bạn có thể sủ dụng để triển khai phần phần mềm.

## Deployment Models

**Bare metal**

Cách quen thuộc và cơ bản nhất để triển khai phần mềm đó là cài đặt nó trực tiếp trên máy tính, hay con gọi là "bare metal". Ngoài việc đây là phương pháp đơn giản nhất, việc triển khai bare metal còn có những ưu điểm khác, chẳng hạn như phần mềm có thể truy cập trực tiếp vào hệ điều hành và phần cứng. Điều này hữu ích trong các tình huống mà bạn cần truy cập vào phần cứng chuyên dụng hoặc là cho các ứng dụng Hight Perfomance Computing trong đó mỗi bit tốc độ đều được tính.
![image](https://user-images.githubusercontent.com/83932775/128640233-fb5c95e0-73ab-479b-b2f3-ff3cc2514893.png)
* Bare metal deployment bản chất là triển khai trên một máy tính thực tế.

Tuy nhiên việc bất lợi đối với triển khai bare metal nằm ở chỗ cô lập các khối lượng công việc khác với nhau. Đối với bare metal mọi ứng dụng trên máy điều sử dụng một kernal, hệ điều hành, bộ nhớ,... Ngoài ra bare metal không linh hoạt về mặt tài nguyên, một máy có RAM 64 GB sẽ không thể điều chỉnh lớn hơn hoặc nhỏ hơn trừ khi có người tháo hoặc lắp thêm RAM.

Thông thường, bare metal được sử dụng để làm cơ sở hạ tầng lưu trữ cho việc ảo hóa (trình giám sát - hypervisors) và cloud framework (trình điều phối các tài nguyên máy tính, lưu trữ và network). Cisco đi tiên phong trong việc phát triển các nền tảng Software-defined hardware (ví dụ như cisco UCS) giúp cơ sở hạ tầng bare metal dễ dàng cấu hình để phục vụ cả nhu cầu ứng dụng và Infrastructure-as-a-Service.


**Virtual machines**

Một cách giải quyết các vấn đề về tình linh hoạt và cô lập là sử dụng Virtual Machines (VMs). Máy ảo giống như một máy tính bên trong máy tính của bạn, có sức mạnh tính toán, network interface, và bộ nhớ riêng.

Hypervisor là một phần mềm dùng để tạo và quản lý các máy ảo. Các hypervisor có sẵn dưới dạng mã nguồn mở (OpenStack, Linux KVM, XEN), và từ các nhà cung cấp thương mại như Oracle (VirtualBox), VMware(Horizon, vSphere, Fusion), Microsoft (Hyper-V) và các nhà cung cấp khác. Hypervisor thường được phân thành 2 loại:
* Type 1: chạy trực tiếp trên phần cứng vật lý (bare metal)
* Type 2: chạy dưới dạng một ứng dụng trong hệ điều hành

Việc sử dụng cac máy ảo có thể khắc phục được một số hạn chế. Ví dụ: Nếu bạn có ba workload muốn tách biệt với nhau, bạn có thể tạo ra 3 máy ảo riêng biệt trên bare metal.
![image](https://user-images.githubusercontent.com/83932775/128830419-6b993c3a-4334-4b0b-9abb-5ea941abf8cb.png)
* Virtual machine nhận các tài nguyên được chia sẽ từ máy host

Có một vài điểm lưu ý sau đây:
1. Các ứng dụng chạy trên máy ảo sẽ phụ thuộc vào máy ảo đó. Truy cập tài nguyên bên ngoài máy ảo cần thông qua mạng ảo - virtual network.
2. Mặc dù các máy ảo đang chạy trên cùng một máy tính, chúng có thể chạy các hệ điều hành khác nhau (được gọi là "guest operation system"), và hệ điều hành mà bare metal đang chạy (được gọi là "host operation system").
3. Tổng dung lượng bộ nhớ ảo được phân bổ trên 3 máy ảo lớn hơn dung lượng RAM có sẵn trên máy chủ. Điều nay được gọi là "overcommitting". Điều này có thể xảy ra bởi vì không chắc chắn rằng cả ba máy áo sẻ cần sử dụng tất cả bộ nhớ ảo của chúng cùng một lúc và hypervisor có thể chia sẻ thời gian các máy ảo khi cần thiết. Overcommitting có thể dẫn đến các vần đề về hiệu suất nếu mức tiêu thụ tài nguyên quá lớn.

Các máy ảo chạy trên một hypervisor như KVM, QEMU, hoặc VMware, cung cấp việc mô phỏng phần cứng hoặc quyền truy cập có kiểm soát vào phần cứng vật lý ở dưới. Hypervisor nằm trên hệ điều hành và quản lý các máy ảo.

Máy ảo có thể thuận tiện vì một số lý do, trong đó không ít lý do là một Image VM có thể được lưu để sử dụng trong tương lai hoặc để những người khác có thể tạo và sử dụng. Điều này cho phép bạn phân phối một máy ảo, hoặc ít nhất, là phương tiện để sử dụng nó. Các ứng dụng chạy máy ảo, chẳng hạn như VirtualBox và VMware, cũng có thể chụp nhanh (snapshot) hoặc sao lưu một máy ảo để bạn có thể đưa nó về trạng thái trước đó, nếu cần.

Bởi vì máy ảo rất giống máy vật lý, máy ảo có thể lưu trữ nhiều loại phần mềm, thậm chí cả phần mềm cũ. Môi trường ứng dụng mới hơn, chẳng hạn như container, có thể không đủ "giống như máy thật" để lưu trữ các ứng dụng không được viết với các giới hạn của chúng. 

**Container-based infrastructure**

Di chuyển lên bậc thang trừu tượng từ các máy ảo, bạn sẽ tìm thấy các container. Phần mềm để tạo và quản lý hoặc sắp xếp các container có sẵn từ Docker, AWS (Elasticized Container Service), Microsoft (Azure Container Service) và các phần mềm khác.

Các container được thiết kế để cung cấp nhiều lợi ích giống như máy ảo, chẳng hạn như cô lập khối lượng công việc và khả năng chạy nhiều khối lượng công việc trên một máy duy nhất, nhưng chúng được kiến trúc hơi khác một chút.

Thứ nhất, các container được thiết kế để khởi động nhanh chóng và do đó, chúng không bao gồm nhiều cơ sở hạ tầng phần mềm cơ bản. Một máy ảo chứa toàn bộ hệ điều hành khách, nhưng một vùng chứa chia sẻ hệ điều hành của máy chủ và sử dụng các mã nhị phân và thư viện dành riêng cho vùng chứa. 

**Serverless computing**

