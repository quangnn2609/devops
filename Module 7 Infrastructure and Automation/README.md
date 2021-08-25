# Cisco Automation Solutions

Có một số trường hợp sử dụng để tự động hóa mạng. Tùy thuộc vào mô hình hoạt động bạn muốn tuân theo, bạn có các lựa chọn về cách kiểm soát lập trình cấu hình mạng và cơ sở hạ tầng của mình. Hãy cùng xem xét quá trình tự động hóa của Cisco thông qua DevNet Automation Exchange để hiểu mức độ phức tạp và các lựa chọn có sẵn.

**Walk: Read-only automation**

Sử dụng các công cụ tự động hóa, bạn có thể thu thập thông tin về cấu hình mạng của mình. Kịch bản này đưa ra câu trả lời cho câu hỏi cơ bản và phổ biến nhất mà bạn có thể hỏi, đó là "Điều gì đã thay đổi?"

Bằng cách thu thập dữ liệu chỉ đọc, bạn giảm thiểu nguy cơ gây ra thay đổi có thể phá vỡ môi trường mạng của bạn. Sử dụng các yêu cầu GET cũng là một cách tuyệt vời để bắt đầu, bằng cách viết các giải pháp mã cho các tác vụ thu thập dữ liệu. Ngoài ra, bạn có thể sử dụng một kịch bản đã đọc để kiểm tra cấu hình và thực hiện bước tự nhiên tiếp theo, đó là đưa cấu hình trở lại tuân thủ. Trong Trao đổi Tự động hóa, sự thay đổi này được phân loại như một quá trình đi bộ-chạy-bay.

**Run: Activate policies and provide self-service across multiple domains**

Với các kịch bản tự động hóa "Giai đoạn chạy" này, bạn có thể cho phép người dùng cung cấp các bản cập nhật mạng của riêng họ một cách an toàn. Bạn cũng có thể tự động hóa quy trình làm việc tại chỗ, quản lý cấu hình mạng hàng ngày và chạy qua các kịch bản Ngày 0, Ngày 1 và hàng ngày (Ngày n).

**Fly: Deploy applications, network configurations, and more through CI/CD**

Để có các ví dụ về tự động hóa và lập trình phức tạp hơn, bạn muốn chuyển đến giai đoạn Fly của DevNet Automation Exchange. Tại đây, bạn có thể đáp ứng nhu cầu bằng cách theo dõi và chủ động quản lý người dùng và thiết bị của mình đồng thời có được thông tin chi tiết về dữ liệu đo từ xa.

Có nhiều trường hợp sử dụng cho tự động hóa cơ sở hạ tầng và bạn có thể thêm vào bộ sưu tập trong DevNet Automation Exchange.

## Why Do We Need Automation?

Doanh nghiệp cạnh tranh và kiểm soát chi phí bằng cách vận hành nhanh chóng và có thể mở rộng quy mô hoạt động. Tốc độ và sự nhanh nhẹn cho phép doanh nghiệp khám phá, thử nghiệm và khai thác các cơ hội trước sự cạnh tranh của họ. Hoạt động mở rộng quy mô cho phép doanh nghiệp nắm bắt thị phần một cách hiệu quả và phù hợp năng lực với nhu cầu.

Các nhà phát triển cần đẩy nhanh mọi giai đoạn xây dựng phần mềm: viết mã và lặp lại, thử nghiệm và dàn dựng. Thực tiễn DevOps yêu cầu các nhà phát triển triển khai và quản lý ứng dụng trong quá trình sản xuất, vì vậy các nhà phát triển cũng nên tự động hóa các hoạt động đó.

Dưới đây là một số rủi ro có thể phát sinh trong môi trường được quản lý và triển khai theo cách thủ công.

**Disadvantages of manual operations**

Việc xây dựng một máy chủ ứng dụng web nguyên khối, đơn giản có thể mất 30 phút trở lên của một nhà điều hành CNTT thực hành, đặc biệt là khi chuẩn bị cho môi trường sản xuất. Khi quá trình này được nhân lên với hàng chục hoặc hàng trăm ứng dụng doanh nghiệp, nhiều địa điểm thực, trung tâm dữ liệu và / hoặc đám mây; các quy trình thủ công, tại một số điểm, sẽ gây ra sự cố hoặc thậm chí là lỗi mạng. Điều này làm tăng thêm chi phí và làm chậm hoạt động kinh doanh.

Các quy trình thủ công như chờ đợi tính khả dụng của cơ sở hạ tầng, cấu hình và triển khai ứng dụng thủ công cũng như bảo trì hệ thống sản xuất, rất chậm và rất khó mở rộng quy mô. Chúng có thể ngăn nhóm của bạn cung cấp các khả năng mới cho đồng nghiệp và khách hàng. Các quy trình thủ công luôn có lỗi của con người và tài liệu dành cho con người thường không đầy đủ và mơ hồ, khó kiểm tra và nhanh chóng lỗi thời. Điều này gây khó khăn cho việc mã hóa và tận dụng kiến ​​thức khó có thể giành được về các cấu hình tốt đã biết và các phương pháp hay nhất trong các tổ chức lớn và cơ sở hạ tầng khác nhau của họ.

**Financial costs**

Sự cố và vi phạm thường xảy ra nhất khi hệ thống được định cấu hình sai. Điều này thường do lỗi của con người trong khi thực hiện các thay đổi thủ công. Một thống kê thường được trích dẫn của Gartner (từ năm 2014) cho thấy chi phí trung bình của một sự cố CNTT lên tới $ 5,600 USD mỗi phút hoặc hơn $ 300,000 USD mỗi giờ. Chi phí cho một vi phạm an ninh thậm chí có thể lớn hơn; trong trường hợp xấu nhất, nó đại diện cho một mối đe dọa hiện hữu đối với tính mạng con người, tài sản, danh tiếng kinh doanh và / hoặc sự tồn tại của tổ chức.

## Financial Costs of Server Outages

![image](https://user-images.githubusercontent.com/83932775/130484149-6c365382-db1e-4471-9685-7e64e86d8ed5.png)

**Dependency risks**

Hệ sinh thái phần mềm ngày nay được phân cấp. Các nhà phát triển không còn cần phải xây dựng và quản lý các giải pháp nguyên khối, đầy đủ. Thay vào đó, họ chuyên môn hóa bằng cách xây dựng các thành phần riêng lẻ theo nhu cầu và sở thích của họ. Các nhà phát triển có thể kết hợp và kết hợp các thành phần, cơ sở hạ tầng và dịch vụ khác cần thiết để tạo ra các giải pháp hoàn chỉnh và vận hành chúng hiệu quả trên quy mô lớn.

Hệ sinh thái phần mềm hiện đại này tập hợp công việc của hàng trăm nghìn cộng tác viên độc lập, tất cả đều chia sẻ lợi ích khi tham gia vào sự hợp tác rộng lớn này. Người tham gia có thể tự do cập nhật công việc của mình khi có nhu cầu và cơ hội, cho phép họ nhanh chóng đưa các tính năng mới ra thị trường, sửa lỗi và cải thiện bảo mật.

Các nhà phát triển có trách nhiệm cố gắng dự đoán và giảm thiểu tác động của các bản cập nhật và bản phát hành mới đối với người dùng bằng cách tuân thủ chặt chẽ các tiêu chuẩn, cố ý thiết kế khả năng tương thích ngược, cam kết cung cấp hỗ trợ lâu dài cho các phiên bản sản phẩm chính (ví dụ: phiên bản "LTS" của Ubuntu Linux distribution) và các phương pháp hay nhất khác.

Hệ sinh thái này đưa ra các yêu cầu mới và rủi ro mới:

* Các thành phần cần có khả năng hoạt động cùng với nhiều thành phần khác trong nhiều tình huống khác nhau ( flexibly configurable - điều này được gọi là có thể cấu hình linh hoạt) cho thấy không có nhiều ưu tiên cho các thành phần hoặc kiến trúc đồng hành cụ thể hơn mức thực sự cần thiết (being unopinionated - điều này được gọi là chưa được khai thác).

* Các nhà phát triển thành phần có thể từ bỏ hỗ trợ cho các tính năng lỗi thời và các tích hợp hiếm khi gặp phải. Điều này làm gián đoạn các quy trình phụ thuộc vào các tính năng đó. Cũng khó hoặc không thể kiểm tra toàn bộ một bản phát hành, tính đến mọi cấu hình.

* Các thiết lập ứng dụng bị phụ thuộc có xu hướng bị khóa vào các ngăn xếp triển khai mỏng manh và ngày càng không an toàn. Chúng thực sự trở thành những khối nguyên khối không thể dễ dàng quản lý, cải tiến, mở rộng quy mô hoặc chuyển sang cơ sở hạ tầng mới, có lẽ tiết kiệm chi phí hơn. Các bản cập nhật và bản vá có thể bị hoãn lại vì các thay đổi có nguy cơ áp dụng và khó quay lại.

## Why Do We Need Full-Stack Automation?

**Why do we need full-stack automation?**

Tự động hóa cơ sở hạ tầng có thể mang lại nhiều lợi ích. Chúng được tóm tắt là tốc độ, khả năng lặp lại và khả năng làm việc trên quy mô lớn, giảm thiểu rủi ro.

Tự động hóa là một thành phần quan trọng của cơ sở hạ tầng chức năng do phần mềm xác định và các ứng dụng động và phân tán. Dưới đây là các lợi ích bổ sung của tự động hóa toàn bộ ngăn xếp.

**Self-service**

Các frameworks tự phục vụ tự động cho phép người dùng trưng dụng cơ sở hạ tầng theo yêu cầu, bao gồm:

* Các thành phần cơ sở hạ tầng tiêu chuẩn như phiên bản cơ sở dữ liệu và điểm cuối VPN
* Nền tảng phát triển và thử nghiệm
* Máy chủ web cứng và các phiên bản ứng dụng khác, cùng với các mạng bị cô lập và truy cập internet được bảo mật giúp chúng trở nên hữu ích, an toàn và có khả năng chống lỗi
* Các nền tảng phân tích như Apache Hadoop, Elastic Stack, InfluxData và Splunk

**Scale on demand**

Các ứng dụng và nền tảng cần có khả năng mở rộng quy mô để đáp ứng các yêu cầu về lưu lượng và khối lượng công việc cũng như sử dụng dung lượng không đồng nhất. Một ví dụ là mở rộng quy mô liên tục từ đám mây riêng tư sang đám mây công cộng và định hình lưu lượng truy cập thích hợp. Nền tảng đám mây có thể cung cấp khả năng tự động mở rộng quy mô (tự động tỷ lệ) máy ảo, vùng chứa hoặc khối lượng công việc trên một framework serverless.

**Observability**

Một hệ thống có thể quan sát cho phép người dùng suy ra trạng thái bên trong của một hệ thống phức tạp từ các đầu ra của nó. Khả năng quan sát (đôi khi được viết tắt là o11y) có thể đạt được thông qua giám sát nền tảng và ứng dụng. Khả năng quan sát cũng có thể đạt được thông qua thử nghiệm sản xuất chủ động đối với các chế độ lỗi và các vấn đề về hiệu suất. Tuy nhiên, trong một hoạt động động bao gồm tính năng tự động thay đổi tỷ lệ và các hành vi ứng dụng khác, độ phức tạp tăng lên và các thực thể trở nên phù du. Một báo cáo gần đây của nhà cung cấp khung khả năng quan sát DataDog, nói rằng tuổi thọ trung bình của một vùng chứa dưới sự điều phối chỉ là 12 giờ; microservices và chức năng có thể chỉ tồn tại trong vài giây. Việc làm cho các thực thể phù du có thể quan sát được và thử nghiệm trong quá trình sản xuất chỉ có thể thực hiện được với tự động hóa.

**Giảm thiểu sự cố tự động**

Một số nhà sản xuất phần mềm và các chuyên gia về khả năng quan sát đề xuất cái được gọi là Chaos Engineering - Kỹ thuật hỗn loạn. Triết lý này dựa trên khẳng định rằng thất bại là bình thường: khi ứng dụng mở rộng, một số bộ phận luôn thất bại. Do đó, các ứng dụng và nền tảng phải được thiết kế để:

