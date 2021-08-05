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

