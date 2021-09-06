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

## Software-Defined Infrastructure: A Case for Automation
Cơ sở hạ tầng được xác định bằng phần mềm, còn được gọi là điện toán đám mây, cho phép các nhà phát triển và nhà khai thác sử dụng phần mềm để trưng dụng, cấu hình, triển khai và quản lý tài nguyên máy tính, lưu trữ và mạng bằng kim loại trần và ảo hóa.

* Điện toán đám mây cũng cho phép các nền tảng và dịch vụ trừu tượng hơn, chẳng hạn như Database-as-a-Service (DaaS), Platform-as-a-Service (PaaS), máy tính không máy chủ, phối hợp container và hơn thế nữa.
* Các đám mây riêng cho phép các doanh nghiệp sử dụng phần cứng đắt tiền tại chỗ hiệu quả hơn nhiều.
* Các đám mây tư nhân công cộng và được lưu trữ cho phép các doanh nghiệp thuê công suất khi cần, cho phép họ di chuyển và phát triển (hoặc thu hẹp) nhanh hơn, đơn giản hóa quy hoạch và tránh đầu tư vốn cố định.

**Lợi ích của mô hình đám mây**
* **Tự phục vụ (nền tảng theo yêu cầu)** - Tài nguyên đám mây có thể có sẵn trong vòng vài giờ hoặc vài phút sau khi cần chúng. Do đó đẩy nhanh tất cả các giai đoạn phát triển và cho phép * mở rộng nhanh chóng năng lực sản xuất. Các ứng dụng có thể được mở rộng trong khu vực đám mây công cộng, bộ dịch vụ hoặc nhà cung cấp có hiệu quả nhất về chi phí.
* **Đóng đặc điểm kỹ thuật, tính nhất quán, khả năng lặp lại** - Các nhà phát triển có thể nắm bắt và chuẩn hóa các cấu hình độc đáo, duy trì tính nhất quán cấu hình của các nền tảng thông qua phát triển, thử nghiệm, dàn dựng và sản xuất. Triển khai một ứng dụng và cấu hình được biết đến tốt ngăn chặn các lỗi có thể được giới thiệu trong quá trình thay đổi cấu hình nền tảng thủ công.
* **Trừu tượng hóa nền tảng - Container** công nghệ trừu tượng các ứng dụng và nền tảng cách xa nhau, bằng cách đóng gói các phụ thuộc ứng dụng và cho phép ứng dụng container của bạn chạy trên môi trường máy chủ được chỉ định chung.

**Những thách thức của mô hình đám mây**

Các nhà phát triển phải chú ý đến thiết kế nền tảng, kiến trúc và bảo mật. Môi trường đám mây tạo ra nhu cầu mới cho các ứng dụng. Khung đám mây công cộng hoặc riêng tư có các GIAO DỊCH NGƯỜI DÙNG, API và quirks khác nhau. Điều này có nghĩa là người dùng không thể luôn luôn coi tài nguyên đám mây là hàng hóa mà họ thực sự nên có, đặc biệt là khi cố gắng quản lý đám mây theo cách thủ công.

Kiểm soát truy cập là rất quan trọng, bởi vì người dùng đám mây có quyền sai có thể gây ra rất nhiều thiệt hại cho tài sản của tổ chức của họ. Quyền đám mây cũng có thể là thách thức để quản lý, đặc biệt là trong các tình huống được vận hành thủ công.

Khi tài nguyên đám mây có thể được tự phục vụ nhanh chóng thông qua các thao tác thủ công, mức tiêu thụ có thể khó quản lý và chi phí rất khó tính toán. Các đám mây riêng đòi hỏi kiểm toán thường xuyên và các thủ tục để nghỉ hưu cơ sở hạ tầng ảo không sử dụng. Người dùng đám mây công cộng có thể ngạc nhiên bởi chi phí bất ngờ khi tài nguyên trả tiền theo sử dụng bị bỏ rơi, nhưng không bị phá hủy.

Nhiều trong số những thách thức này có thể được giải quyết thông qua tự động hóa.

## Các ứng dụng phân tán và động: Một trường hợp khác cho tự động hóa
Các ứng dụng doanh nghiệp và công cộng quy mô lớn có thể cần phải quản lý tải trọng lưu lượng truy cập, tính toán và lưu trữ nặng và thay đổi.

* Các ứng dụng cần cung cấp trải nghiệm tốt cho cơ sở người dùng của họ.
* Họ cần phải có khả năng phục hồi, có sẵn cao, bảo vệ tính toàn vẹn và bảo mật dữ liệu người dùng và tuân thủ các quy định của địa phương về nơi và cách lưu trữ dữ liệu.
* Họ cần phát triển (và thu nhỏ) hiệu quả để đáp ứng nhu cầu kinh doanh, khai thác xu hướng và điều hành hiệu quả chi phí.

Kiến trúc ứng dụng đơn máy chủ, "nguyên khối", trong khi khái niệm đơn giản, không phục vụ rất tốt những nhu cầu này. Một máy chủ là một điểm thất bại duy nhất, giới hạn hiệu suất và dung lượng, và có khả năng nâng cấp hạn chế. Sao chép máy chủ duy nhất có thể tăng dung lượng cho các ứng dụng rất đơn giản, nhưng không hoạt động cho các ứng dụng yêu cầu tính nhất quán dữ liệu trên tất cả các phiên bản. Và nó sẽ không bảo vệ dữ liệu người dùng nếu có lỗi trên máy chủ nơi dữ liệu của họ cư trú.

Vì những lý do này và các lý do khác, kiến trúc ứng dụng hiện đại ngày càng được phân phối. Chúng được xây dựng từ các thành phần nhỏ và tương đối nhẹ đôi khi được gọi là microservices. Các thành phần này có thể được cô lập trong các container, được kết nối thông qua các dịch vụ khám phá và nhắn tin (kết nối mạng trừu tượng) và được hỗ trợ bởi các cơ sở dữ liệu có khả năng mở rộng, có thể mở rộng (duy trì trạng thái).

![image](https://user-images.githubusercontent.com/83932775/132239621-2deb624c-f8aa-4dbc-9fc9-9e4c4c3c03f1.png)

Các ứng dụng dựa trên microservices có thể (về lý thuyết) được mở rộng theo dịch vụ, khi cần thiết để đáp ứng nhu cầu lưu lượng truy cập hoặc hiệu suất. Kiến trúc này giúp có được lợi ích lớn nhất từ cơ sở hạ tầng siêu hội tụ, cho phép tinh chỉnh kết nối và dịch vụ điện toán, lưu trữ và mạng để phù hợp với yêu cầu tải ứng dụng động.

## Ứng dụng dựa trên microservices

![image](https://user-images.githubusercontent.com/83932775/132241082-eb745501-03dd-4ef3-b27e-87d9c99dd211.png)

**Lợi ích của microservices**

* **Khả năng mở rộng** - Microservices có thể được thu nhỏ và cân bằng tải khi cần thiết trên nhiều máy chủ được kết nối mạng hoặc thậm chí nhiều trung tâm dữ liệu riêng biệt về mặt địa lý hoặc các khu vực đám mây công cộng. Điều này loại bỏ các điểm thất bại duy nhất và cung cấp nhiều loại công suất cụ thể theo từng nhiệm vụ như nhu cầu điều kiện, bất cứ nơi nào cần thiết, loại bỏ tắc nghẽn.
* **Công cụ tự động hóa cơ sở hạ tầng** - Càng ngày, sự năng động của các ứng dụng dựa trên microservice được cung cấp bởi cơ sở hạ tầng. Những "dàn nhạc" container này như Kubernetes hoặc Mesos, tự động hóa việc mở rộng theo yêu cầu, tự phục hồi và hơn thế nữa.


**Thách thức của microservices**
* **Tăng độ phức tạp** - Microservices có nghĩa là có nhiều bộ phận chuyển động để cấu hình và triển khai. Có nhiều hoạt động đòi hỏi khắt khe hơn, bao gồm mở rộng quy mô theo yêu cầu, tự phục hồi và các tính năng khác.
* **Tự động hóa là một yêu cầu** - Các phương pháp thủ công không thể đối phó thực tế với sự phức tạp của việc triển khai và quản lý các ứng dụng động và nền tảng dàn nhạc của chúng, với các hoạt động tốc độ cao, tự trị và các bit và mảnh tạm thời và các mảnh nhỏ của chúng.

## Tự động hóa tóm tắt cơ sở hạ tầng

Những nhu cầu kinh doanh và kỹ thuật này, xu hướng và động lực học này, khuyến khích các nhà phát triển và nhà khai thác sử dụng tự động hóa ở khắp mọi nơi cho các nhiệm vụ sau:

* Quản lý tất cả các giai đoạn xây dựng ứng dụng, cấu hình, triển khai và quản lý vòng đời. Điều này bao gồm mã hóa, thử nghiệm, dàn dựng và sản xuất.
* Quản lý cơ sở hạ tầng được xác định bằng phần mềm thay mặt cho các ứng dụng bạn xây dựng.
* Bên cạnh các ứng dụng của bạn, để bảo tồn, cập nhật và liên tục cải thiện mã tự động hóa. Mã này giúp bạn phát triển, kiểm tra, giai đoạn, giám sát và vận hành các ứng dụng của chúng tôi ở quy mô sản xuất và trong các môi trường khác nhau. Bạn ngày càng có thể coi tất cả các mã này như một sản phẩm làm việc.

# DevOps và SRE
## Giới thiệu về DevOps và SRE
Để tự động hóa full-stack thực sự hiệu quả, nó đòi hỏi những thay đổi đối với văn hóa tổ chức, bao gồm phá vỡ sự phân chia lịch sử giữa Phát triển (Dev) và Hoạt động (Ops).

Chủ đề này thảo luận về lịch sử của phương pháp DevOps và các nguyên tắc cốt lõi của các tổ chức DevOps thành công.

## Phân chia DevOps

Trong lịch sử, tạo ứng dụng là công việc của các nhà phát triển phần mềm (Dev), và đảm bảo rằng các ứng dụng hoạt động cho người dùng và doanh nghiệp đã là tỉnh chuyên ngành hoạt động CNTT (Ops).
![image](https://user-images.githubusercontent.com/83932775/132241861-f67d3867-0f3f-4d88-81ad-e36d975130d8.png)

Trong hệ sinh thái CNTT doanh nghiệp truyền thống, trước ảo hóa, việc tách Dev khỏi Ops có vẻ hợp lý. Miễn là cơ sở hạ tầng được dựa trên đầu tư vào thiết bị vốn (cài đặt thủ công, cung cấp, cấu hình và quản lý phần cứng), nó yêu cầu người gác cổng. Những người gác cổng Ops đã làm việc trên một khoảng thời gian khác với người dùng và nhà phát triển, và có các ưu đãi và mối quan tâm khác nhau.

**Nút thắt cổ chai di sản**

Theo truyền thống, việc cung cấp năng lượng dự án hoặc mở rộng quy mô hệ thống sẽ được định hướng theo kế hoạch, thay vì theo nhu cầu. Trưng dụng, mua, cài đặt, cung cấp và cấu hình máy chủ hoặc dung lượng mạng và dịch vụ cho một dự án có thể mất vài tháng. Với nguồn lực vật chất hạn chế, chia sẻ tài nguyên là phổ biến.

Việc thiếu những cách đơn giản để thiết lập và phá hủy các môi trường và kết nối bị cô lập có nghĩa là các tổ chức có xu hướng tạo ra các hệ thống lâu dài trở thành điểm thất bại duy nhất. Các mạng lưới sử dụng hỗn hợp rất khó bảo mật và đòi hỏi sự quản lý liên tục tỉ mỉ.

Thông tục, các hệ thống lâu dài, phức tạp như vậy được gọi là "thú cưng" bởi vì mọi người sẽ đặt tên cho chúng và chăm sóc cho một hệ thống đó. Giải pháp thay thế là "gia súc", được rút gọn, khối lượng công việc phù du và cơ sở hạ tầng ảo được xây dựng và phá hủy bởi tự động hóa. Phương pháp này đảm bảo rằng có một hệ thống mới (hoặc "bò") có sẵn để tiếp quản công việc.

**Hợp nhất Dev và Ops**

Các tổ chức công nghệ tinh vi đã di chuyển ra khỏi những thái cực lịch sử này trong nhiều thế hệ. Quá trình này tăng tốc với việc áp dụng rộng rãi ảo hóa máy chủ, đám mây và phát triển phần mềm Agile. Vào đầu những năm 2000, đã bắt đầu một phong trào để đối xử với Dev và Ops như một thực thể duy nhất:

* Làm cho lập trình viên chịu trách nhiệm triển khai và bảo trì
* Coi cơ sở hạ tầng ảo hóa như mã
