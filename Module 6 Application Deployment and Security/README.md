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

Thứ nhất, các container được thiết kế để khởi động nhanh chóng và do đó, chúng không bao gồm nhiều cơ sở hạ tầng phần mềm cơ bản. Một máy ảo chứa toàn bộ hệ điều hành khách (guest OS), nhưng một container chia sẻ hệ điều hành của máy chủ (host OS) và sử dụng các mã nhị phân và thư viện dành riêng cho container.

![image](https://user-images.githubusercontent.com/83932775/128988062-4b9c23e2-0f3e-444c-9288-f7e5035a589e.png)
* Các container chia sẽ tài nguyên từ máy host bao gồm cả kernel

Trong trường hợp các máy ảo mô phỏng toàn bộ máy tính, một vùng chứa thường chỉ đại diện cho một ứng dụng hoặc một nhóm ứng dụng. Giá trị của việc sử dụng vùng chứa là tất cả các thư viện và mã nhị phân bạn cần để chạy ứng dụng đều được bao gồm, vì vậy người dùng không phải thực hiện bước cài đặt bổ sung đó.

Một điểm khác biệt quan trọng giữa Docker container và VM là mỗi VM có hệ điều hành hoàn chỉnh của riêng nó. Vùng chứa chỉ chứa một phần của hệ điều hành. Ví dụ: bạn có thể có một máy tính chủ Ubuntu Linux chạy một máy ảo CentOS Linux, một máy ảo Ubuntu Linux và một máy ảo Windows 10. Mỗi máy ảo này có hệ điều hành hoàn chỉnh của riêng nó. Điều này có thể rất tốn tài nguyên cho máy tính chủ.

Với Docker, các vùng chứa chia sẻ cùng một nhân của máy tính chủ của chúng. Ví dụ: trên máy chủ Ubuntu Linux, bạn có thể có một bộ chứa Ubuntu Linux và một bộ chứa Centos Linux. Cả hai vùng chứa này đều chia sẻ cùng một nhân Linux. Tuy nhiên, bạn không thể có một vùng chứa chạy Windows 10 trên cùng một máy tính chủ Ubuntu Linux này, vì Windows sử dụng một nhân khác. Chia sẻ cùng một nhân yêu cầu ít tài nguyên hơn nhiều so với việc sử dụng các máy ảo riêng biệt, mỗi máy có một nhân riêng. 

Vùng chứa cũng giải quyết vấn đề phát sinh khi nhiều ứng dụng cần các phiên bản khác nhau của cùng một thư viện để chạy. Bởi vì mỗi ứng dụng nằm trong vùng chứa riêng của nó, nó được cách ly khỏi bất kỳ thư viện và tệp nhị phân xung đột nào.

Các thùng chứa cũng rất hữu ích vì có hệ sinh thái các công cụ xung quanh chúng. Các công cụ như Kubernetes có thể thực hiện điều phối các vùng chứa khá phức tạp và thực tế là các vùng chứa thường được thiết kế để không có trạng thái và khởi động nhanh chóng có nghĩa là bạn có thể tiết kiệm tài nguyên bằng cách không chạy chúng trừ khi bạn cần.

Các vùng chứa cũng là nền tảng của điện toán tự nhiên đám mây, trong đó các ứng dụng nói chung là không trạng thái. Tính không trạng thái này làm cho bất kỳ trường hợp nào của một vùng chứa cụ thể có thể xử lý một yêu cầu. Khi bạn thêm điều này vào một khía cạnh khác của điện toán đám mây nhấn mạnh đến các dịch vụ, thì tính năng serverless computing sẽ trở nên khả thi. 

**Serverless computing**

Hãy bắt đầu với điểm quan trọng này: nói rằng các ứng dụng “không có máy chủ” là rất tốt cho tiếp thị, nhưng về mặt kỹ thuật thì điều đó không đúng. Tất nhiên ứng dụng của bạn đang chạy trên một máy chủ. Nó chỉ đang chạy trên một máy chủ mà bạn không kiểm soát và không cần phải suy nghĩ về nó. Do đó tên "serverless".

Serverless computing tận dụng xu hướng hiện đại đối với các ứng dụng được xây dựng xung quanh các dịch vụ. Nghĩa là, ứng dụng thực hiện cuộc gọi đến một chương trình hoặc khối lượng công việc khác để hoàn thành một tác vụ cụ thể, để tạo ra một môi trường nơi các ứng dụng được cung cấp trên cơ sở “khi cần thiết”. 

Nó hoạt động như thế này:

Nó hoạt động như thế này:

Bước 1. Bạn tạo ứng dụng của mình.

Bước 2. Bạn triển khai ứng dụng của mình như một vùng chứa, để nó có thể chạy dễ dàng trong bất kỳ môi trường thích hợp nào.

Bước 3. Bạn triển khai vùng chứa đó cho một nhà cung cấp serverless computing, chẳng hạn như AWS Lambda, các chức năng của Google Cloud hoặc thậm chí là một chức năng nội bộ dưới dạng Function as a Service. Việc triển khai này bao gồm thông số kỹ thuật về khoảng thời gian chức năng sẽ không hoạt động trước khi nó bị chia nhỏ.

Bước 4. Khi cần thiết, ứng dụng của bạn sẽ gọi hàm.

Bước 5. Trình cung cấp quay một thể hiện của vùng chứa, thực hiện tác vụ cần thiết và trả về kết quả.

![image](https://user-images.githubusercontent.com/83932775/129039095-fb308f28-86d7-45a5-8906-65216b74ab61.png)
* Serverlesss computing chịu trách nhiệm cấp tài nguyên cho nhà phát triển và chỉ khi ứng dụng chạy.

Điều quan trọng cần lưu ý ở đây là nếu ứng dụng không máy chủ không cần thiết, nó sẽ không chạy và bạn sẽ không bị tính phí cho nó. Mặt khác, nếu bạn thường gọi nó nhiều lần, nhà cung cấp có thể tạo ra nhiều phiên bản để xử lý lưu lượng truy cập. Bạn không phải lo lắng về bất kỳ điều đó.

Bởi vì sức chứa tăng và giảm theo nhu cầu, nó thường được gọi là “co giãn” hơn là “có thể mở rộng”.

Mặc dù có một lợi thế rất lớn trên thực tế là bạn chỉ trả tiền cho các tài nguyên đang thực sự được sử dụng, trái ngược với một máy ảo có thể chạy mọi lúc, ngay cả khi dung lượng của nó không cần thiết. Mô hình serverless computing có nghĩa là bạn không có quyền kiểm soát máy chủ, vì vậy nó có thể không phù hợp từ góc độ bảo mật. 

## Types of Infrastructure

**On-Premises**

Nói về mặt kỹ thuật, "On-Premisses(tại chỗ)" có nghĩa là bất kỳ hệ thống nào nằm trong phạm vi giới hạn của tòa nhà của bạn theo đúng nghĩa đen. Trong trường hợp này, chúng ta đang nói về các trung tâm dữ liệu truyền thống chứa các máy riêng lẻ được cung cấp cho các ứng dụng, thay vì các đám mây, bên ngoài hoặc cách khác.

Các cơ sở hạ tầng truyền thống này là các trung tâm dữ liệu với các máy chủ dành riêng cho các ứng dụng riêng lẻ hoặc cho các máy ảo, về cơ bản cho phép một máy tính hoạt động giống như nhiều máy tính.

Việc vận hành một trung tâm dữ liệu tại chỗ truyền thống yêu cầu các máy chủ, thiết bị lưu trữ và thiết bị mạng phải được đặt hàng, nhận, lắp ráp trong các giá đỡ ("giá đỡ và xếp chồng lên nhau"), di chuyển đến một vị trí, được kết nối với nguồn điện và dữ liệu. Thiết bị này phải được cung cấp các dịch vụ môi trường như bảo vệ nguồn điện, làm mát và phòng chống cháy nổ. Sau đó, các máy chủ cần được cấu hình hợp lý cho các vai trò của chúng, hệ điều hành và phần mềm phải được cài đặt, và tất cả chúng cần được bảo trì và giám sát.

Tất cả các công việc cơ sở hạ tầng này cần thời gian và công sức. Các yêu cầu về tài nguyên cần phải thông qua nhóm vận hành, điều này có thể dẫn đến sự chậm trễ hàng ngày, hàng tuần hoặc thậm chí hàng tháng trong khi phần cứng mới được lấy, chuẩn bị và cung cấp.

Ngoài ra, mở rộng một ứng dụng thường có nghĩa là chuyển nó sang một máy chủ lớn hơn, điều này làm cho việc mở rộng quy mô trở thành một sự kiện lớn. Điều đó có nghĩa là một ứng dụng gần như luôn lãng phí tiền bạc với dung lượng dư thừa không được sử dụng hoặc hoạt động kém hiệu quả vì nó không có đủ tài nguyên.

Những vấn đề này có thể được giải quyết bằng cách chuyển sang giải pháp dựa trên đám mây. 

**Private Cloud**

Nhược điểm của cơ sở hạ tầng tại chỗ có thể được giải quyết dễ dàng bằng điện toán đám mây. Đám mây là một hệ thống cung cấp khả năng tự phục vụ cho tài nguyên máy tính, mạng và lưu trữ.

![image](https://user-images.githubusercontent.com/83932775/129086440-0b202679-3701-494d-9931-0c5245985d44.png)
* Trong cơ sở hạ tầng đám mây riêng, tổ chức kiểm soát tất cả các tài nguyên

Đám mây bao gồm một mặt phẳng điều khiển (control plane), cho phép bạn thực hiện các yêu cầu. Bạn có thể tạo một máy ảo mới, đính kèm một khối lượng lưu trữ, thậm chí tạo một mạng mới và tính toán tài nguyên.

Các đám mây cung cấp quyền truy cập tự phục vụ vào các tài nguyên máy tính, chẳng hạn như máy ảo, thùng chứa và thậm chí cả bare metal. Điều này có nghĩa là người dùng có thể đăng nhập vào trang tổng quan hoặc sử dụng dòng lệnh để tự tạo ra các tài nguyên mới, thay vì đợi CNTT giải quyết khi nhận ticket. Những nền tảng này đôi khi được gọi là Infrastructure-as-a-Service Cơ sở hạ tầng như một dịch vụ (IaaS). Các nền tảng private cloud phổ biến bao gồm VMware (độc quyền), OpenStack (mã nguồn mở) và Kubernetes (một khung điều phối vùng chứa). Cơ sở hạ tầng phần cứng cơ bản cho đám mây có thể được cung cấp bởi các máy chủ bare metal được nối mạng thông thường hoặc bởi các giải pháp cơ sở hạ tầng vật lý "hyperconverged-siêu hội tụ" hoặc bare metal tiên tiến hơn, được quản lý, chẳng hạn như Cisco UCS và Cisco HyperFlex, tương ứng.

Điều phân biệt đám mây riêng với các loại đám mây khác là tất cả các tài nguyên trong đám mây đều nằm dưới sự kiểm soát của tổ chức của bạn. Trong hầu hết các trường hợp, một đám mây riêng sẽ được đặt trong trung tâm dữ liệu của bạn, nhưng đó không phải là yêu cầu về mặt kỹ thuật để được gọi là “riêng tư”. Phần quan trọng là tất cả các tài nguyên chạy trên phần cứng đều thuộc về tổ chức chủ sở hữu.

Lợi thế của private cloud là bạn có toàn quyền kiểm soát vị trí đặt nó, điều này rất quan trọng trong các tình huống có các quy định tuân thủ cụ thể và bạn thường không phải lo lắng về các khối lượng công việc khác trên hệ thống.

Mặt khác, bạn phải có một nhóm vận hành có thể quản lý đám mây và giữ cho nó hoạt động. 

**Public Cloud**

Public Cloud - Đám mây công cộng về cơ bản giống như Private Cloud - đám mây riêng tư , nhưng nó được quản lý bởi một nhà cung cấp đám mây công cộng. Các đám mây công cộng cũng có thể chạy các hệ thống như OpenStack hoặc Kubernetes hoặc chúng có thể là các đám mây độc quyền cụ thể như Amazon Web Services hoặc Azure.

Khách hàng của đám mây công cộng có thể chia sẻ tài nguyên với các tổ chức khác: máy ảo của bạn có thể chạy trên cùng một máy chủ lưu trữ như một máy ảo của người khác. Ngoài ra, các nhà cung cấp đám mây công cộng có thể cung cấp cho khách hàng cơ sở hạ tầng chuyên dụng. Hầu hết cung cấp một số 'khu vực' đám mây riêng biệt về mặt địa lý, trong đó khối lượng công việc có thể được lưu trữ. Điều này cho phép khối lượng công việc được đặt gần với người dùng (giảm thiểu độ trễ), hỗ trợ dự phòng địa lý (các khu vực Bờ Đông và Bờ Tây không có khả năng ngoại tuyến cùng một lúc) và cho phép kiểm soát theo khu vực pháp lý đối với nơi dữ liệu được lưu trữ.

![image](https://user-images.githubusercontent.com/83932775/129240139-89758685-b00e-4f44-8343-e49d16146d6c.png)
* Với đám mây công cộng, tổ chức không kiểm soát tài nguyên

Các đám mây công cộng có thể hữu ích vì bạn không phải trả tiền cho phần cứng mà bạn sẽ không sử dụng, vì vậy bạn có thể mở rộng quy mô hầu như vô thời hạn miễn là tải yêu cầu, sau đó giảm quy mô khi lưu lượng truy cập chậm. Bởi vì bạn chỉ trả tiền cho những tài nguyên bạn đang thực sự sử dụng, giải pháp này có thể tiết kiệm nhất vì ứng dụng của bạn không bao giờ hết tài nguyên và bạn không phải trả tiền cho những tài nguyên bạn không sử dụng. Bạn cũng không phải lo lắng về việc bảo trì hoặc vận hành phần cứng; nhà cung cấp đám mây công cộng xử lý điều đó. Tuy nhiên, trên thực tế, khi đám mây của bạn có kích thước nhất định, các lợi thế về chi phí có xu hướng biến mất và tốt hơn hết bạn nên sử dụng một đám mây riêng.

Có một nhược điểm của đám mây công cộng. Bởi vì bạn đang chia sẻ đám mây với những người dùng khác, bạn có thể phải đối mặt với các tình huống trong đó khối lượng công việc khác chiếm nhiều hơn tỷ lệ chia sẻ tài nguyên của họ.

Vấn đề này tồi tệ hơn khi nhà cung cấp đám mây chấp nhận overcommitting. Nhà cung cấp giả định rằng không phải tất cả tài nguyên sẽ được sử dụng cùng một lúc và phân bổ nhiều tài nguyên "ảo" hơn tài nguyên "vật lý". Ví dụ, không có gì lạ khi thấy tỷ lệ vượt quá 16: 1 cho các CPU, có nghĩa là đối với mỗi CPU vật lý, có thể có 16 CPU ảo được phân bổ cho các máy ảo. Bộ nhớ cũng có thể được truyền quá mức. Với tỷ lệ 2: 1 cho bộ nhớ, máy chủ có RAM 128GB có thể lưu trữ 256GB khối lượng công việc. Với đám mây công cộng, bạn không có quyền kiểm soát điều đó (tiết kiệm khi trả nhiều tiền hơn cho các phiên bản chuyên dụng hoặc các dịch vụ khác giúp đảm bảo mức độ dịch vụ). 

**Hybrid Cloud**

Như bạn có thể đoán, đám mây lai là sự kết hợp của hai loại đám mây khác nhau. Thông thường, đám mây lai được sử dụng để làm cầu nối giữa đám mây riêng và đám mây công cộng trong một ứng dụng.

![image](https://user-images.githubusercontent.com/83932775/129249438-6e1a7097-b494-4ed1-b604-e254bbf77af5.png)
* Đám mây lai kết hợp đám mây công cộng và đám mây riêng để cung cấp tài nguyên và bảo mật bổ sung khi cần thiết.

Ví dụ: bạn có thể có một ứng dụng chạy trên đám mây riêng của mình, nhưng sẽ "bùng nổ" lên đám mây công cộng nếu nó hết tài nguyên. Bằng cách này, bạn có thể tiết kiệm tiền bằng cách không mua quá nhiều cho đám mây riêng của mình, nhưng vẫn có tài nguyên khi bạn cần.

Bạn cũng có thể đi theo hướng khác và có một ứng dụng chủ yếu chạy trên đám mây công cộng, nhưng sử dụng tài nguyên trong đám mây riêng để bảo mật hoặc kiểm soát. Ví dụ: bạn có thể có một ứng dụng web phục vụ hầu hết nội dung của nó từ đám mây công cộng, nhưng lưu trữ thông tin người dùng trong cơ sở dữ liệu trong đám mây riêng.

Đám mây lai thường bị nhầm lẫn với đa đám mây, trong đó một tổ chức sử dụng nhiều đám mây cho các mục đích khác nhau. Điều phân biệt đám mây lai là việc sử dụng nhiều hơn một đám mây trong một ứng dụng duy nhất. Do đó, một ứng dụng đám mây lai phải nhận thức rõ hơn nhiều về môi trường của nó so với một ứng dụng sống trong một đám mây duy nhất.

Một ứng dụng đám mây không lai và đám mây của nó giống như một con cá và đại dương; con cá không cần nhận thức về đại dương bởi vì đại dương chỉ ở đó, xung quanh con cá. Khi bạn bắt đầu thêm các khả năng đám mây kết hợp vào một ứng dụng, ứng dụng đó phải biết tài nguyên nào có sẵn và từ đâu.

Tốt nhất là bản thân ứng dụng không phải xử lý những việc này trực tiếp. Cách tốt hơn là có một số loại giao diện mà ứng dụng có thể gọi khi nó cần thêm tài nguyên và giao diện đó đưa ra quyết định về nơi chạy các tài nguyên đó và chuyển chúng trở lại ứng dụng. Bằng cách này, logic ánh xạ tài nguyên có thể được kiểm soát độc lập với chính ứng dụng và bạn có thể điều chỉnh nó cho các tình huống khác nhau. Ví dụ: bạn có thể giữ tất cả tài nguyên bên trong trong giai đoạn thử nghiệm và gỡ lỗi, sau đó từ từ tăng cường sử dụng đám mây công cộng.

Một cách để thực hiện điều này là thông qua một công cụ như Cisco Hybrid Cloud Platform dành cho Google Cloud, công cụ này quản lý mạng, bảo mật, quản lý, trung tâm dữ liệu, phần mềm và công cụ mã nguồn mở và API. Điều này cung cấp cho bạn một môi trường duy nhất, nhất quán, an toàn cho ứng dụng của bạn, cho phép ứng dụng hoạt động trên cả trung tâm dữ liệu tại chỗ và Google Cloud.

Ngoài ra, bộ điều phối vùng chứa đã trở nên rất phổ biến với các công ty sử dụng triển khai đám mây lai. Các bộ điều phối cung cấp một lớp bất khả tri của nhà cung cấp đám mây mà ứng dụng có thể sử dụng để yêu cầu các tài nguyên cần thiết, làm giảm nhận thức về môi trường cần thiết trong chính ứng dụng


**Edge Cloud**

Loại đám mây mới nhất là đám mây cạnh. Điện toán đám mây Edge đang trở nên phổ biến nhờ sự phát triển của Internet vạn vật (IoT). Những thiết bị được kết nối này, chẳng hạn như máy ảnh được kết nối, xe tự hành và thậm chí cả điện thoại thông minh, ngày càng được hưởng lợi từ sức mạnh tính toán tồn tại gần chúng hơn trên mạng.

Hai lý do chính mà khả năng tính toán gần hơn giúp các thiết bị IoT là tốc độ và băng thông. Ví dụ: nếu bạn đang chơi một trò chơi bắn súng góc nhìn thứ nhất, ngay cả nửa giây độ trễ giữa thời điểm bạn bóp cò và khi cảnh quay được đăng ký là không thể chấp nhận được. Một trường hợp khác mà độ trễ có thể gây tử vong, theo nghĩa đen là với các phương tiện tự lái. Với vận tốc 55 dặm một giờ, một chiếc ô tô đi được hơn 40 feet chỉ trong 500 mili giây. Nếu người đi bộ bước ra lề đường, chiếc xe sẽ không thể chờ hướng dẫn về việc phải làm.

Có một vấn đề thứ hai. Điển hình là xe tự lái ngăn chặn vấn đề độ trễ bằng cách tự quyết định, nhưng điều đó lại dẫn đến các vấn đề của chính nó. Những chiếc xe này sử dụng công nghệ máy học, đòi hỏi một lượng lớn dữ liệu được truyền đến và đi từ chiếc xe. Người ta ước tính rằng những phương tiện này tạo ra hơn 4 TB dữ liệu mỗi giờ và hầu hết các mạng không thể xử lý loại lưu lượng đó (đặc biệt là với sự tăng trưởng dự kiến ​​của những phương tiện này trên thị trường).

Để giải quyết cả hai vấn đề này, một đám mây cạnh di chuyển điện toán đến gần nơi cần thiết. Thay vì các giao dịch được thực hiện từ một người dùng cuối ở Cleveland, đến đám mây chính ở Oregon, có thể có một đám mây trung gian, một đám mây cạnh, ở Cleveland. Đám mây biên xử lý dữ liệu hoặc giao dịch. Sau đó, nó sẽ gửi phản hồi lại cho khách hàng hoặc thực hiện phân tích sơ bộ dữ liệu và gửi kết quả tới một đám mây khu vực có thể ở xa hơn. 

![image](https://user-images.githubusercontent.com/83932775/129251423-c7e50114-956b-4a1c-b5f9-92b5ec139a93.png)
* Điện toán đám mây cạnh cho phép các tài nguyên đến gần hơn với nơi chúng cần thiết

Điện toán đám mây biên bao gồm một hoặc nhiều đám mây trung tâm hoạt động như một trung tâm cho chính các đám mây biên. Phần cứng cho các đám mây cạnh được đặt càng gần người dùng càng tốt. Ví dụ: bạn có thể có phần cứng cạnh trên tháp di động thực tế xử lý các tín hiệu đến và đi từ điện thoại di động của người dùng.

Một lĩnh vực khác mà bạn có thể thấy điện toán biên là bán lẻ, nơi bạn có nhiều cửa hàng. Mỗi cửa hàng có thể có đám mây nội bộ của riêng mình. Đây là một đám mây rìa ăn vào đám mây khu vực, đến lượt nó có thể đưa vào một đám mây trung tâm. Kiến trúc này mang lại cho các văn phòng địa phương những lợi ích khi có đám mây của riêng họ (chẳng hạn như triển khai nhất quán các API để đảm bảo mỗi cửa hàng có thể được quản lý, cập nhật và giám sát một cách hiệu quả).

Không có gì "đặc biệt" về các đám mây cạnh. Chúng chỉ là những đám mây điển hình. Điều khiến chúng trở nên "cạnh tranh" là chúng đang ở đâu và chúng được kết nối với nhau. Tuy nhiên, có một điều nữa về các đám mây cạnh. Vì chúng thường chạy trên phần cứng nhỏ hơn nhiều so với các đám mây "điển hình", chúng có thể bị hạn chế tài nguyên hơn. Ngoài ra, phần cứng đám mây cạnh phải đáng tin cậy, hiệu quả về mặt sử dụng năng lượng và tốt nhất là có thể quản lý từ xa, vì nó có thể nằm ở khu vực hẻo lánh, chẳng hạn như tháp di động ở giữa sa mạc, nơi khó bảo dưỡng phần cứng. . 

# Creating and Deploying a Sample Application

## What is Docker?

Cách phổ biến nhất để chứa một ứng dụng là triển khai nó dưới dạng một vùng chứa Docker. Vùng chứa là một cách đóng gói mọi thứ bạn cần để chạy ứng dụng của mình, để nó có thể dễ dàng được triển khai trong nhiều môi trường khác nhau. Docker là một cách tạo và chạy vùng chứa đó. Cụ thể, Docker là một định dạng kết hợp một số công nghệ khác nhau để tạo ra thứ mà chúng ta biết ngày nay là vùng chứa. Các công nghệ này là:
- Namespaces: Những không gian này cô lập các phần khác nhau của vùng chứa đang chạy. Ví dụ: bản thân tiến trình bị cô lập trong không gian tên pid (Process ID), hệ thống tệp bị cô lập trong không gian tên **mnt** (mount) và mạng được cách ly trong không gian tên mạngCác nhóm này là một khái niệm linux tiêu chuẩn cho phép hệ thống giới hạn tài nguyên, chẳng hạn như RAM hoặc bộ nhớ, được sử dụng bởi một ứng dụng.
- Control groups: Các nhóm **cgroups** một khái niệm linux tiêu chuẩn cho phép hệ thống giới hạn tài nguyên, chẳng hạn như RAM hoặc bộ nhớ, được sử dụng bởi một ứng dụng.
- Union File Systems: Các hệ thống tệp **UnionFS** này là hệ thống tệp được xây dựng theo từng lớp, kết hợp các tài nguyên. 

Docker image là một tập hợp các tệp chỉ đọc không có trạng thái. Docker Image chứa mã nguồn, thư viện và các phụ thuộc khác cần thiết để chạy một ứng dụng. Vùng chứa Docker là phiên bản thời gian chạy của Docker image. Bạn có thể có nhiều vùng chứa đang chạy của cùng một Docker image. Docker image giống như một công thức làm bánh và bạn có thể làm bao nhiêu chiếc bánh (Docker container) tùy thích.

Image lần lượt có thể được lưu trữ trong registries - các cơ quan đăng ký như Docker Hub. Nhìn chung, hệ thống trông như thế này:

![image](https://user-images.githubusercontent.com/83932775/129319372-4670b881-0a4f-47da-9f5c-81c988faa0d7.png)
* Tạo vùng chứa bao gồm việc kéo image hoặc mẫu từ kho lưu trữ, sau đó sử dụng nó để tạo vùng chứa

Vì vậy, một phiên bản đơn giản của quy trình tạo vùng chứa sẽ trông như thế này:

**Step 1.** Tạo một image mới bằng cách sử dụng **docker build** hoặc kéo một bản sao của một hình ảnh hiện có từ sổ đăng ký bằng cách sử dụng **docker pull**. (Tùy thuộc vào trường hợp, bước này là tùy chọn. Xem bước 3.)

**Step 2.** Chạy một vùng chứa dựa trên image bằng cách sử dụng **docker run** hoặc **docker container create**.

**Step 3.** Daemon Docker kiểm tra xem nó có bản sao cục bộ của image hay không. Nếu không, nó sẽ kéo hình ảnh từ registry.

**Step 4.** Daemon Docker tạo một vùng chứa dựa trên hình ảnh và nếu sử dụng **docker run**, hãy đăng nhập vào nó và thực hiện lệnh được yêu cầu.

Như bạn có thể thấy, nếu bạn định tạo một triển khai dựa trên vùng chứa của ứng dụng mẫu, bạn sẽ phải tạo một image. Để làm điều đó, bạn cần một Dockerfile. 

## What is a Dockerfile?

Nếu bạn đã sử dụng một ngôn ngữ mã hóa như C, bạn biết rằng nó yêu cầu bạn biên dịch mã của mình. Nếu vậy, bạn có thể quen với khái niệm “makefile”. Đây là tệp mà tiện ích make sử dụng để biên dịch và xây dựng tất cả các phần của ứng dụng.

Đó là những gì một **Dockerfile** làm cho Docker. Nó là một tệp văn bản đơn giản, có tên là **Dockerfile**. Nó xác định các bước mà lệnh xây dựng docker cần thực hiện để tạo một hình ảnh sau đó có thể được sử dụng để tạo vùng chứa đích.

Bạn có thể tạo một **Dockerfile** rất đơn giản để tạo một vùng chứa Ubuntu. Sử dụng lệnh **cat** để tạo **Dockerfile**, sau đó thêm **FROM ubuntu** vào tệp. Nhập **Ctrl + D** để lưu và thoát khỏi tệp với văn bản sau và lưu nó trong thư mục hiện tại của bạn: 

![image](https://user-images.githubusercontent.com/83932775/129372252-682dd486-f3c5-4667-85fd-064cc0bb7f0e.png)

Đó là tất cả những gì nó cần, chỉ một dòng. Bây giờ bạn có thể sử dụng lệnh **docker build** để xây dựng image như trong ví dụ sau. Tùy chọn **-t** được sử dụng để đặt tên cho bản dựng. Lưu ý dấu chấm (**.**) Ở cuối lệnh chỉ định rằng image sẽ được tạo trong thư mục hiện tại. Sử dụng **docker build --help** để xem tất cả các tùy chọn có sẵn.

![image](https://user-images.githubusercontent.com/83932775/129373139-282486a8-d934-4bb0-b4f2-7c41f2615edd.png)
Nhập **docker images** để xem image của bạn trong danh sách image trên máy ảo DEVASC:
![image](https://user-images.githubusercontent.com/83932775/129374168-ec0cabce-ae26-4e1c-a350-1802366a3b56.png)

Bây giờ bạn đã có image, hãy sử dụng lệnh **docker run** để chạy nó. Bây giờ bạn đang ở trong bash shell BÊN TRONG docker image mà bạn đã tạo. Thay đổi thư mục chính và nhập **ls** để thấy rằng nó trống và sẵn sàng để sử dụng. Nhập **exit** để rời khỏi vùng chứa Docker và quay lại hệ điều hành chính của máy ảo DEVASC của bạn.
![image](https://user-images.githubusercontent.com/83932775/129375202-1bfd3068-63b8-4303-a39d-e16be633a0a4.png)

## Anatomy of a Dockerfile

Tất nhiên, nếu tất cả những gì bạn có thể làm với **Dockerfile** là khởi động một hệ điều hành sạch, điều đó sẽ hữu ích, nhưng những gì bạn cần là cách bắt đầu với một mẫu và xây dựng từ đó.

Lưu ý: Các bước hiển thị trong phần còn lại của chủ đề này chỉ dành cho mục đích hướng dẫn. Các chi tiết bổ sung mà bạn cần để hoàn thành các lệnh này trong máy ảo DEVASC của bạn không được cung cấp. Tuy nhiên, bạn sẽ hoàn thành các bước tương tự trong phòng thí nghiệm Build a Sample Web App in a Docker Container ở phần sau của chủ đề.

Hãy xem xét tệp **Dockerfile** sau chứa một ứng dụng Python: 

![image](https://user-images.githubusercontent.com/83932775/129440469-593df859-963c-46bb-97ee-5837d17b61c9.png)

Trong **Dockerfile** ở trên, giải thích về các lệnh như sau:

* Lệnh **FROM** cài đặt Python trong Docker image. Nó gọi một image mặc định dựa trên Debian Linux từ Docker Hub, với phiên bản Python mới nhất được cài đặt.
* Lệnh **WORKDIR** yêu cầu Docker sử dụng **/home/ubuntu** làm thư mục làm việc.
* Lệnh **COPY** yêu cầu Docker sao chép tệp sample-app.py từ thư mục hiện tại của Dockerfile vào **/home/ubuntu.**
* Lệnh **RUN** cho phép bạn chạy trực tiếp các lệnh trên vùng chứa. Trong ví dụ này, Flask đã được cài đặt. Flask là một nền tảng để hỗ trợ ứng dụng của bạn dưới dạng ứng dụng web.
* Lệnh **CMD** sẽ khởi động máy chủ khi bạn chạy vùng chứa thực. Tại đây, bạn sử dụng lệnh python để chạy sample-app.py bên trong vùng chứa.
* Lệnh **EXPOSE** cho Docker biết rằng bạn muốn để public cổng 8080. Lưu ý rằng đây là cổng mà Flask đang lắng nghe. Nếu bạn đã định cấu hình máy chủ web của mình để lắng nghe ở một nơi khác (chẳng hạn như yêu cầu https trên cổng 443) thì đây là nơi cần lưu ý.

Sử dụng lệnh **docker build** để xây dựng image. Trong đầu ra sau, image đã được xây dựng trước đó. Do đó, Docker tận dụng những gì được lưu trữ trong bộ nhớ cache để tăng tốc quá trình.

![image](https://user-images.githubusercontent.com/83932775/129449066-96c1fe08-9750-4f92-9275-73baf2597660.png)

Như bạn có thể thấy, Docker đi qua từng bước trong Dockerfile, bắt đầu với image base, Python. Nếu hình image này không tồn tại trên hệ thống của bạn, Docker sẽ kéo nó từ registry. Cơ quan registry mặc định là Docker Hub. Tuy nhiên, trong một môi trường an toàn, bạn có thể thiết lập registry image vùng chứa đáng tin cậy của riêng mình. Lưu ý rằng image thực sự là một số image khác nhau được xếp chồng lên nhau, giống như bạn đang xếp các lệnh của riêng mình lên trên hình ảnh cơ sở.

Lưu ý rằng giữa các bước như thực hiện một lệnh, Docker thực sự tạo một vùng chứa mới và xây dựng một hình ảnh trung gian, một lớp mới, bằng cách lưu vùng chứa đó. Trên thực tế, bạn có thể tự mình làm điều đó bằng cách tạo vùng chứa, thực hiện các thay đổi bạn muốn, sau đó lưu vùng chứa đó dưới dạng hình ảnh mới.

Trong ví dụ trước, chỉ một số lượng nhỏ lệnh Dockerfile có sẵn được sử dụng. Danh sách đầy đủ có sẵn trong tài liệu Docker trong tham chiếu Dockerfile. Hiện tại, một danh sách các lệnh có sẵn trông giống như sau:

FROM
MAINTAINER
RUN
CMD
EXPOSE
ENV
COPY
ENTRYPOINT
VOLUME
USER
WORKDIR
ARG
ONBUILD
STOPSIGNAL
LABEL

Nhập **docker images** để xem danh sách các image. Lưu ý rằng thực tế có hai image hiện đã được lưu vào bộ nhớ đệm trên máy. Đầu tiên là image Python, mà bạn đã sử dụng làm cơ sở của mình. Docker đã lưu trữ nó để nếu bạn muốn xây dựng lại image của mình, bạn sẽ không phải tải xuống lại.

## Start a Docker Container Locally

Bây giờ image đó đã được tạo, hãy sử dụng nó để tạo một vùng chứa mới và thực sự thực hiện một số công việc bằng cách nhập lệnh **docker run**, như được hiển thị trong kết quả sau. Trong trường hợp này, một số tham số được chỉ định. Tham số **-d** là viết tắt của **--detach** và cho biết bạn muốn chạy nó ở chế độ nền. Tham số **-P** yêu cầu Docker xuất bản nó trên các cổng mà bạn đã tiếp xúc (trong trường hợp này là 8080).
![image](https://user-images.githubusercontent.com/83932775/129450576-38c4283e-bf7d-43cd-981f-a4274b254853.png)
Bạn có thể thấy vùng chứa bằng cách liệt kê các processes:
![image](https://user-images.githubusercontent.com/83932775/129451161-46431874-6d85-428c-a1f0-e7f3539ddc71.png)

Có một số điều cần lưu ý ở đây. Làm việc ngược lại, lưu ý rằng Docker đã gán tên cho vùng chứa, **jovial_sammet**. Bạn cũng có thể tự đặt tên cho nó bằng tùy chọn **--name**. Ví dụ:

**docker run -d -P --name pythontest sample-app-image**

Cũng lưu ý rằng, mặc dù container đang lắng nghe trên cổng 8080, đó chỉ là một cổng nội bộ. Docker đã chỉ định một cổng bên ngoài, trong trường hợp này là 32774, sẽ chuyển tiếp đến cổng bên trong đó. Điều này cho phép bạn chạy nhiều vùng chứa lắng nghe trên cùng một cổng mà không xảy ra xung đột. Nếu bạn muốn tải lên trang web ứng dụng mẫu của mình, bạn có thể sử dụng địa chỉ IP công cộng cho máy chủ lưu trữ và cổng đó. Ngoài ra, nếu bạn gọi nó từ chính máy chủ, bạn vẫn sẽ sử dụng cổng bên ngoài đó, như được hiển thị với lệnh curl sau đây.
![image](https://user-images.githubusercontent.com/83932775/129451357-50270209-08bb-4fe3-bea4-81b35daa003b.png)

Docker cũng cho phép bạn chỉ định một cổng cụ thể để chuyển tiếp, để bạn có thể tạo một hệ thống dễ đoán hơn:
![image](https://user-images.githubusercontent.com/83932775/129451382-a1ca126a-6cb8-4480-8f64-1f154e0861af.png)

Khi vùng chứa của bạn đang chạy, bạn có thể đăng nhập vào nó giống như bạn đăng nhập vào bất kỳ máy chủ vật lý hoặc ảo nào bằng cách sử dụng lệnh thực thi từ máy chủ mà vùng chứa đang chạy:
![image](https://user-images.githubusercontent.com/83932775/129451401-ab431d64-93d7-43a4-aae8-20085b02f01c.png)

Để dừng và loại bỏ một vùng chứa đang chạy, bạn có thể gọi nó bằng tên của nó:
![image](https://user-images.githubusercontent.com/83932775/129451419-85d81236-31d2-45b1-ace1-8e21fe13f7c1.png)
Bây giờ nếu bạn nhìn lại các tiến trình đang chạy, bạn có thể thấy rằng nó đã biến mất.
![image](https://user-images.githubusercontent.com/83932775/129451434-7e750488-df74-4315-abd6-1b4e8e917335.png)

## Save a Docker Image to a Registry

Bây giờ bạn đã biết cách tạo và sử dụng hình ảnh của mình, đã đến lúc bạn nên cung cấp cho người khác sử dụng. Một cách để làm điều này là lưu trữ nó trong sổ đăng ký hình ảnh.

Theo mặc định, Docker sử dụng sổ đăng ký Docker Hub, mặc dù bạn có thể tạo và sử dụng sổ đăng ký của riêng mình. Bạn sẽ cần bắt đầu bằng cách đăng nhập vào sổ đăng ký:
![image](https://user-images.githubusercontent.com/83932775/129453343-75d739f7-7424-4b19-85ed-4785de7410e4.png)
Tiếp theo, bạn commit một phiên bản vùng chứa đang chạy của image của bạn. Ví dụ: thùng chứa trăn đang chạy trong ví dụ này. Commit vùng chứa bằng lệnh commit của docker.
![image](https://user-images.githubusercontent.com/83932775/129454810-edb0a0d0-d70f-4d40-8be8-1b9ffcef4072.png)

Tiếp theo, sử dụng lệnh **docker tag** để gắn thẻ cho image mà bạn đã commit. Thẻ có dạng sau:

**\<repository>/\<imagename>:\<tag>**

Phần đầu tiên, kho lưu trữ, thường là tên người dùng của tài khoản lưu trữ hình ảnh. Trong ví dụ này, nó là **devnetstudent**. Tiếp theo là tên hình ảnh, và cuối cùng là thẻ tùy chọn. (Hãy nhớ rằng, nếu bạn không chỉ định nó, nó sẽ xuất hiện muộn nhất.)

Trong ví dụ này, thẻ có thể là v1, như được hiển thị ở đây:

![image](https://user-images.githubusercontent.com/83932775/129455029-9c81e3bc-b914-47e1-8b2f-432193685378.png)

