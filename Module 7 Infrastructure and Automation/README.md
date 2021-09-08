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

## Sự phát triển của DevOps

DevOps phát triển và tiếp tục phát triển ở nhiều nơi song song. Một số sự kiện quan trọng đã định hình kỷ luật như chúng ta biết ngày nay.

**Xác định khoảnh khắc 1: Kỹ sư độ tin cậy trang web (Site Reliability Engineering-SRE)**

Đến năm 2003, các công ty internet lớn nhất và tiên tiến nhất thế giới đã áp dụng ảo hóa đáng kể. Họ đã đối phó với các trung tâm dữ liệu lớn và các ứng dụng hoạt động trên quy mô lớn. Có những thất bại dẫn đến Dev vs. Ops chỉ tay, phát triển nhanh và liên tục không đủ số lượng nhân viên tổ chức, và căng thẳng trực tiếp.

Google là một trong những công ty đầu tiên hiểu và thể chế hóa một loại mô tả công việc Dev + Ops lai mới. Đây là kỹ sư độ tin cậy trang web (SRE). Vai trò của SRE nhằm hợp nhất các ngành và kỹ năng của Dev và Ops, tạo ra một cuốn sách chơi đặc biệt và thực hành tốt nhất mới để thực hiện Ops với các phương pháp phần mềm.

Cách tiếp cận SRE đã được nhiều công ty khác áp dụng. Cách tiếp cận này dựa trên:

* Trách nhiệm chung
* Chấp nhận rủi ro
* Thừa nhận thất bại như bình thường
* Cam kết sử dụng tự động hóa để giảm hoặc loại bỏ "vất vả"
* Đo lường mọi thứ
* Đủ điều kiện thành công trong việc đáp ứng các mục tiêu cấp dịch vụ định lượng

**Xác định khoảnh khắc 2: Debois và "Cơ sở hạ tầng agile"**

Tại Agile 2008, nhà phát triển người Bỉ Patrick Debois đã có một bài thuyết trình có tên Agile Infrastructure and Operations. Bài thuyết trình của ông đã thảo luận về cách áp dụng các phương pháp nhà phát triển cho Ops trong khi vẫn duy trì rằng Dev và Ops nên tách biệt. Tuy nhiên, năm sau, Debois tiếp tục thành lập chuỗi sự kiện DevOpsDays.

Bài thuyết trình của Debois có ảnh hưởng trong việc thúc đẩy các cuộc thảo luận xung quanh việc tự động hóa cơ sở hạ tầng ảo (và vật lý), sử dụng điều khiển phiên bản (như Git) để lưu trữ mã triển khai cơ sở hạ tầng (thủ tục hoặc tuyên bố) và áp dụng các phương pháp Agile để phát triển và duy trì các giải pháp cấp cơ sở hạ tầng.

**Khoảnh khắc xác định 3: Allspaw và Hammond**

Vào cuối những năm 2000, DevOps ngày càng phổ biến. Trong số những minh họa hấp dẫn đầu tiên về giá trị của nó là một bài thuyết trình của John Allspaw và Paul Hammond tại VelocityConf vào năm 2009. Trong bài thuyết trình này, các tác giả phác thảo một tập hợp các thực tiễn tốt nhất của DevOps được thành lập dựa trên ý tưởng rằng cả Dev và Ops đều hợp tác cho phép kinh doanh. Những thực hành tốt nhất này bao gồm:
* Cơ sở hạ tầng tự động
* Điều khiển phiên bản dùng chung
* Xây dựng và triển khai một bước

Bài thuyết trình cũng mô tả tự động hóa, làm việc theo nhóm, chia sẻ trách nhiệm, minh bạch, tin tưởng, trách nhiệm giải trình lẫn nhau và thực tiễn truyền thông đã trở nên phổ biến trong số các học viên DevOps / SRE. Những thực tiễn này bao gồm CI / CD, kiểm tra tự động, số liệu, SLOs / SLAs và nắm lấy rủi ro không đổ lỗi và thất bại không thể tránh khỏi.

DevOps/SRE có nhiều nguyên tắc cốt lõi và thực tiễn tốt nhất:

* Tập trung vào tự động hóa
* Ý tưởng rằng "thất bại là bình thường"
* Một khúc xạ của "sự sẵn có" về những gì một doanh nghiệp có thể chịu đựng

Cũng giống như Agile Development có thể được coi là một phương pháp để xác định và kiểm soát kỳ vọng quản lý cho các dự án phần mềm, DevOps có thể được xem như một cách cấu trúc văn hóa làm việc lành mạnh cho các bộ phận dựa trên công nghệ của doanh nghiệp. Nó cũng có thể được xem như là một cách để giảm chi phí. Bằng cách làm cho thất bại trở nên bình thường và giảm thiểu tự động hóa, công việc có thể tránh xa giờ làm việc đắt tiền và căng thẳng và vào lịch trình ngày làm việc theo kế hoạch.

**Tự động hóa, tránh vất vả và giữ chân nhân tài**

Tự động hóa cung cấp tốc độ và khả năng lặp lại trong khi loại bỏ lao động thủ công, lặp đi lặp lại. Điều này cho phép tài năng kỹ thuật dành thời gian giải quyết các vấn đề mới, tăng giá trị cho doanh nghiệp trong thời gian dành cho doanh nghiệp.

Các học viên DevOps / SRE thường dự kiến sẽ dành một phần đáng kể thời gian làm việc (50% trở lên trong một số tình huống) để cung cấp khả năng hoạt động mới và mở rộng đáng tin cậy kỹ thuật, bao gồm phát triển công cụ tự động hóa. Điều này làm giảm giờ làm việc trực và can thiệp thủ công để hiểu và khắc phục sự cố.

Việc mua lại và duy trì tài năng kỹ thuật đòi hỏi các tổ chức phải hợp tác với các nhà đổi mới của họ để giảm thiểu sự nhàm chán và căng thẳng của lao động có giá trị thấp và công việc trực tuyến, và nguy cơ phải đối mặt với những thất bại công nghệ không thể tránh khỏi trong chế độ "khoan lửa".

Điều này đặc biệt quan trọng đối với các doanh nghiệp có lợi nhuận thấp, lợi nhuận bằng sự tăng trưởng nhanh chóng và quy mô lớn và cần kiểm soát chặt chẽ chi tiêu, đặc biệt là đối với số lượng nhân viên lành nghề. Tuy nhiên, đối với tất cả các loại tổ chức, điều quan trọng là công việc công nghệ thông tin phải được coi là một trung tâm lợi nhuận, chứ không phải là một trung tâm chi phí.

**Thất bại là bình thường**

Giả định rằng thất bại sẽ xảy ra ảnh hưởng đến phương pháp thiết kế phần mềm. DevOps phải xây dựng các sản phẩm và nền tảng có khả năng phục hồi cao hơn, khả năng chịu độ trễ cao hơn nếu có thể, tự giám sát tốt hơn, ghi nhật ký, nhắn tin lỗi người dùng cuối và tự phục hồi.

Khi thất bại xảy ra và DevOps phải can thiệp, các hoạt động kết quả nên được xem không chỉ đơn giản là công việc sửa chữa, mà còn là nghiên cứu để xác định và xếp hạng các ứng cử viên thủ tục cho các vòng tự động hóa mới.

**SLOs, SLIs và ngân sách lỗi**

Quan trọng đối với văn hóa DevOps / SRE là hai ý tưởng liên kết: 1. DevOps phải cung cấp giá trị kinh doanh có thể đo lường được, thỏa thuận và 2. Thực tế thống kê của việc làm như vậy một cách hoàn hảo là không thể. Những ý tưởng này được hệ thống hóa trong Mục tiêu cấp dịch vụ (SLO) được xác định theo các số liệu thực được gọi là Chỉ số mức dịch vụ (SLIs).

SLIs được thiết kế để lập bản đồ cho thực tế thực tế của việc cung cấp dịch vụ cho khách hàng: họ có thể đại diện cho một ngưỡng duy nhất hoặc cung cấp ngoặc tinh vi hơn để phân loại hơn nữa kết quả ngoại lệ. Ví dụ: SLI có thể tuyên bố rằng 99% yêu cầu sẽ được phục vụ trong vòng 50 mili giây và cũng có thể yêu cầu nắm bắt thông tin như liệu một yêu cầu >50msec có hoàn thành hay không, hoặc liệu một yêu cầu cụ thể có thất bại đối với khách hàng lớn nhất của bạn hay không.

Phương pháp SLO / SLI cho phép phân phối giá trị kinh doanh rẻ hơn, nhanh hơn bằng cách loại bỏ nghĩa vụ tìm kiếm sự hoàn hảo để xây dựng những gì "đủ tốt". Nó cũng có thể ảnh hưởng đến tốc độ, phạm vi và các khía cạnh khác của phát triển để đảm bảo và cải thiện tính đầy đủ.

Một cách để mô hình hóa kết quả SLO / SLI đòi hỏi phải thiết lập cái gọi là "ngân sách lỗi" cho một dịch vụ trong một khoảng thời gian nhất định (ngày, tuần, tháng, quý, v.v.), và sau đó trừ đi các thất bại để đạt được SLO từ giá trị này. Nếu ngân sách lỗi vượt quá, các quyết định hợp lý có thể được đưa ra, chẳng hạn như làm chậm tốc độ phát hành cho đến khi các nguồn lỗi được xác định và các bản sửa lỗi cụ thể được thực hiện và thử nghiệm.

![image](https://user-images.githubusercontent.com/83932775/132305735-47880554-7c50-487d-b419-269e9147cee0.png)


Đối với một dịch vụ nhất định, nó có ý nghĩa để cam kết cung cấp tốt trong khả năng, nhưng sau đó overdeliver. SLAs (thỏa thuận bên ngoài) được thiết lập tốt nhất đến nơi chúng sẽ dễ thực hiện. SLOs (mục tiêu cho hiệu suất thực tế) có thể được đặt cao hơn. Ngân sách lỗi là sự khác biệt giữa SLO và 100% tính khả dụng.

**Tóm tắt DevOps và SRE**

Bạn đã thấy DevOps / SRE đang cùng phát triển với các công nghệ như ảo hóa và container hóa, cho phép một cách tiếp cận thống nhất và bộ công cụ thống nhất để hỗ trợ ứng dụng phối hợp và kỹ thuật cơ sở hạ tầng.

Tiếp theo, bạn sẽ tìm hiểu về một số cơ chế tự động hóa cơ sở hạ tầng.

# Kịch bản tự động hóa cơ bản
## Giới thiệu về Kịch bản tự động hóa cơ bản

Các công cụ tự động hóa mạnh mẽ như Ansible, Puppet và Chef mang lại sự dễ sử dụng, khả năng dự đoán, kỷ luật và khả năng làm việc ở quy mô lớn cho công việc của DevOps. Nhưng điều đó không có nghĩa là bạn không thể thực hiện một số tự động hóa với các công cụ cơ bản hơn như Bash và Python. Công cụ tự động hóa hoạt động một phần bằng cách bọc chức năng shell, tiện ích hệ điều hành, chức năng API và các yếu tố mặt phẳng điều khiển khác để đơn giản, đồng nhất, làm giàu tính năng và khả năng tương thích trong các tình huống DevOps. Nhưng các công cụ vẫn không giải quyết được mọi vấn đề về triển khai và cấu hình.

Đó là lý do tại sao mỗi công cụ tự động hóa có một hoặc nhiều chức năng thực hiện các lệnh và tập lệnh cơ bản trên các mục tiêu và trả về kết quả. Ví dụ, trong Ansible, các chức năng này bao gồm , và .command,shell,raw

Đôi khi nó có thể nhanh hơn và đơn giản hơn để sử dụng các lệnh hoặc script shell. Thông thường, điều này là do nhiều triển khai công cụ bắt đầu bằng cách dịch tự động hóa ban đầu được viết bằng Bash, Python hoặc các ngôn ngữ khác và bạn muốn chuyển chức năng đó một cách nhanh chóng và chính xác vào công cụ trước khi chuyển và tái cấu trúc.

Tóm lại, rất hiếm khi nhìn sâu vào các repos cơ sở hạ tầng được duy trì bởi công cụ mà không tìm thấy một số kịch bản. Vì vậy, có những kỹ năng này là rất quan trọng!

## Công cụ cơ bản để viết kịch bản tự động hóa

Shell có mặt khắp nơi, vì vậy kịch bản shell trong lịch sử là nền tảng của tự động hóa.

**Bash**

Trong Linux (và các hệ điều hành khác), shell tương tác với I / O tương tác, hệ thống tệp và giao tiếp liên xử lý. Điều này cung cấp các cách để ban hành lệnh, cung cấp đầu vào cho đầu ra xử lý và đường ống cho các chuỗi các tiện ích mạnh mẽ.

Bourne Again Shell (BASH) là mặc định trên hầu hết các bản phân phối Linux. Do sự phổ biến của nó, các thuật ngữ "Bash" và "shell" thường được sử dụng thay thế cho nhau.

Sử dụng các lệnh trong một tập lệnh Bash cũng giống như sử dụng chúng trực tiếp từ dòng lệnh. Phát triển kịch bản rất cơ bản có thể chỉ đơn giản là vấn đề sao chép các biểu thức dòng lệnh vào một tập tin sau khi kiểm tra các lệnh CLI để xem chúng có hoạt động hay không.

Ngược lại, Python hoặc một ngôn ngữ cấp cao, tinh vi khác cho tự động hóa thủ tục đơn giản thường khó khăn hơn và có thể không đáng giá cho các dự án đơn giản.

**Ngôn ngữ lập trình ngoài Bash**

Ngôn ngữ tinh vi cải thiện trên Bash khi sự phức tạp và yêu cầu quy mô tăng lên. Chúng đặc biệt hữu ích khi xây dựng và vận hành cơ sở hạ tầng ảo hóa trong môi trường đám mây, sử dụng các SDK như AWS SDK cho Python hoặc AWS SDK cho javascript trong Node.js. Mặc dù Bash có thể được sử dụng để truy cập kịch bản vào AWS CLI, bạn có thể sử dụng các tính năng và thư viện tích hợp của các ngôn ngữ tinh vi hơn để phân tích các bộ dữ liệu trả về phức tạp (như JSON), quản lý nhiều thao tác song song, lỗi quy trình, xử lý phản hồi không đồng bộ đối với các lệnh và hơn thế nữa.

Để phát triển và thực thi các tập lệnh bằng ngôn ngữ mong muốn của bạn, bạn có thể cần cài đặt và cấu hình ngôn ngữ đó trên hệ thống phát triển của mình và trên bất kỳ máy nhắm mục tiêu từ xa nào. Truy cập các chức năng tiện ích cấp hệ thống có thể yêu cầu gọi các thư viện (chẳng hạn như thư viện trong Python), sau đó gói các lệnh Bash CLI theo cú pháp bổ sung để thực thi. Bạn cũng cần xử lý mã trả về, thời gian chờ và các điều kiện khác trong môi trường ngôn ngữ ưa thích của bạn .os

## Tự động hóa thủ tục

Sử dụng Bash, Python hoặc các ngôn ngữ thông thường khác để tự động hóa thường có nghĩa là viết một quy trình bắt buộc. Một thủ tục bắt buộc là một chuỗi các lệnh có trật tự nhằm đạt được mục tiêu. Trình tự có thể bao gồm kiểm soát dòng chảy, điều kiện, cấu trúc chức năng, lớp và hơn thế nữa.

Tự động hóa thủ tục như vậy có thể rất mạnh mẽ. Nhưng nó chỉ đơn giản nếu bạn am hiểu về cách các tiện ích hệ thống, CLIs / SDK và các giao diện khác hoạt động. Bạn cũng phải biết về trạng thái hệ thống mục tiêu.

**Phát triển quy trình**

Như bạn đã biết, nếu bạn tạo một tập lệnh nhỏ để cài đặt và cấu hình một phần mềm trên hệ thống mục tiêu từ xa, lần đầu tiên nó có thể chạy ổn. Chạy nó lần thứ hai tuy nhiên; Và kịch bản đơn giản của bạn có thể làm cho một mớ hỗn độn. Nó có thể ném lỗi và dừng lại khi nó tìm thấy ứng dụng đã được cài đặt, hoặc tệ hơn, bỏ qua một lỗi như vậy và tiếp tục thực hiện các thay đổi dư thừa trong các tệp cấu hình.

Để làm cho kịch bản này an toàn hơn, dễ sử dụng hơn, linh hoạt hơn và có thể tái sử dụng, bạn cần làm cho nó thông minh hơn và phức tạp hơn. Ví dụ, bạn có thể nâng cao nó để:

* Xác định xem nó đang chạy trong môi trường Debian hoặc CentOS và sử dụng trình quản lý gói chính xác (hoặc) và cú pháp.aptyum
* Xác định xem ứng dụng mục tiêu của bạn đã được cài đặt trong một phiên bản thích hợp và chỉ thử cài đặt nó nếu nó không có mặt, dừng lại nếu không và không thực hiện thêm thay đổi nào.
* Xác định xem nó đã thực hiện một bản sao của mỗi tệp cấu hình trước khi thay đổi nó và sử dụng trình soạn thảo luồng (, v.v.) để thực hiện các thay đổi chính xác, thay vì bất cẩn phụ lục văn bản vào các tệp cấu hình và hy vọng các ứng dụng tiêu thụ các tệp này sẽ không bị hỏng. awk sed

Khi bạn phát triển và tinh chỉnh các kịch bản hơn nữa, bạn sẽ muốn chúng hoàn thành một số nhiệm vụ sau:

* Khám phá, kiểm kê và biên soạn thông tin về các hệ thống mục tiêu và đảm bảo các tập lệnh thực hiện điều này theo mặc định.
* Gói gọn sự phức tạp của việc cài đặt các ứng dụng một cách an toàn. Thực hiện sao lưu và thay đổi tệp cấu hình và khởi động lại các dịch vụ thành các biểu mẫu có thể tái sử dụng, chẳng hạn như các tập lệnh con có chứa tham số, thư viện chức năng và các thông tin khác.

Để đảm bảo các kịch bản hiệu quả và có thể tái sử dụng, bạn sẽ:

* Chuẩn hóa việc đặt hàng và trình bày các tham số, cờ và lỗi.
* Tạo một hệ thống phân cấp mã phân chia nhiệm vụ một cách hợp lý và hiệu quả.
* Tạo kịch bản cấp cao cho toàn bộ triển khai và kịch bản cấp thấp hơn cho các giai đoạn triển khai.
* Dữ liệu cụ thể triển khai riêng biệt từ mã, làm cho mã chung chung và có thể tái sử dụng càng tốt.

![image](https://user-images.githubusercontent.com/83932775/132317962-31a56dc5-0924-4c55-b023-d011372d883f.png)

Loại kịch bản này có xu hướng nguy hiểm nếu trạng thái bắt đầu không hoàn toàn được biết đến và kiểm soát. Áp dụng các thay đổi tương tự một lần nữa cho một hệ thống được cấu hình chính xác thậm chí có thể phá vỡ nó.

**Idempotency: một chủ đề định kỳ trong tự động hóa**

Cuối cùng, mục tiêu của hầu hết mọi kịch bản là đạt được trạng thái mong muốn trong một hệ thống, bất kể điều kiện bắt đầu. Các kịch bản thủ tục được viết cẩn thận và các công cụ cấu hình khai báo kiểm tra các mục tiêu trước khi thực hiện các nhiệm vụ trên chúng, chỉ thực hiện các nhiệm vụ cần thiết để đạt được trạng thái mong muốn.

Chất lượng phần mềm này được gọi là idempotency. Có một vài nguyên tắc cơ bản của sự gia tăng cần tuân theo:

![image](https://user-images.githubusercontent.com/83932775/132319091-91944e7a-a4cb-4269-9417-ff91db42c0ba.png)

## Thực thi Script cục bộ và từ xa

Để cấu hình các hệ thống từ xa, bạn cần truy cập và thực thi các tập lệnh trên chúng. Có nhiều cách để làm điều này:

* Bạn có thể lưu trữ các tập lệnh cục bộ, truyền chúng đến các máy nhắm mục tiêu với một tiện ích vỏ như , sau đó đăng nhập vào máy từ xa bằng cách sử dụng và thực thi chúng.scpssh
* Bạn có thể ống các tập lệnh đến một máy từ xa bằng cách sử dụng và thực hiện chúng theo trình tự với các lệnh khác, chụp và trả kết quả cho thiết bị đầu cuối của bạn, tất cả trong một lệnh.cat | ssh
* Bạn có thể cài đặt một máy khách truyền tệp an toàn đa năng như SFTP, sau đó sử dụng tiện ích đó để kết nối với máy từ xa, chuyển, đặt quyền thích hợp, sau đó thực hiện tệp tập lệnh của bạn.
* Bạn có thể lưu trữ các tập lệnh trên webserver, đăng nhập vào máy từ xa và truy xuất chúng bằng , hoặc các tiện ích khác hoặc lưu trữ các tập lệnh trong kho lưu trữ Git. Cài đặt git trên máy từ xa, nhân bản repo vào nó, kiểm tra một nhánh và thực hiện các tập lệnh được tìm thấy ở đó.wgetcurl
* Bạn có thể cài đặt một giải pháp hoạt động từ xa đầy đủ như VNC hoặc NoMachine cục bộ, cài đặt máy chủ của nó trên mục tiêu (điều này thường đòi hỏi cũng yêu cầu cài đặt môi trường máy tính để bàn đồ họa), truyền / sao chép và sau đó thực thi các tập lệnh.
* Nếu các thiết bị mục tiêu của bạn được cung cấp trên khung đám mây, thường có một cách để tiêm một tập lệnh cấu hình thông qua cùng một lệnh CLI hoặc hành động WebUI thể hiện nền tảng.

![image](https://user-images.githubusercontent.com/83932775/132319623-82f3928a-e2a2-4d06-8889-9f69e14a4ac9.png)

Hầu hết các dịch vụ đám mây công cộng cho phép bạn tiêm các tập lệnh cấu hình trực tiếp vào các phiên bản VM để thực hiện tại thời điểm khởi động

## Tự động hóa đám mây

Các framework điện toán đám mây cơ sở hạ tầng như một dịch vụ (IaaS) là một mục tiêu điển hình cho tự động hóa. Tự động hóa đám mây cho phép bạn cung cấp máy chủ ảo hóa, cấu hình mạng ảo và các kết nối khác, các dịch vụ trưng dụng và sau đó triển khai các ứng dụng trên cơ sở hạ tầng này.

Các nhà cung cấp đám mây và cộng đồng nguồn mở thường cung cấp các hệ thống con chuyên biệt cho các công cụ triển khai phổ biến. Các hệ thống con này trích xuất một kho tài nguyên hoàn chỉnh từ framework đám mây và giữ cho nó được cập nhật trong thời gian thực trong khi tự động hóa thực hiện thay đổi, cho phép bạn dễ dàng viết tự động hóa hơn để quản lý các tài nguyên này.

Bạn cũng có thể quản lý tài nguyên đám mây bằng cách sử dụng các tập lệnh được viết bằng Bash, Python hoặc các ngôn ngữ khác. Các tập lệnh như vậy được giúp đỡ bởi nhiều công cụ đơn giản hóa quyền truy cập vào các mục tiêu tự động hóa. Chúng bao gồm:

* CLIs và SDK bao bọc REST và các giao diện khác của phần cứng, thực thể cơ sở hạ tầng ảo, higher-order control planes và API đám mây. Điều này làm cho các tính năng của chúng có thể truy cập từ shell (và thông qua các kịch bản Bash) và trong các chương trình Python.
* Các công cụ dòng lệnh và các phân tích tích hợp của Python có thể trích xuát đầu ra JSON và YAML được clIs và SDK trả lại thành các định dạng đẹp, dễ đọc và thành các cấu trúc dữ liệu Python gốc để dễ thao tác.

## Cloud CLIs and SDKs

IaaS và các loại đám mây cơ sở hạ tầng khác cũng cung cấp CLIs và SDK cho phép kết nối dễ dàng với các giao diện cơ bản của chúng, thường dựa trên REST.

**Cisco UCS - một bare metal cloud**

Nếu bạn đã quen thuộc với các sản phẩm của Cisco Compute, bao gồm Unified Computing System (UCS), Hyperflex, UCS Manager và hệ thống quản lý cơ sở hạ tầng Intersight, bạn biết đây thực sự là một cửa ngõ để quản lý SaaS toàn cầu về cơ sở hạ tầng UCS / Hyperflex của một tổ chức.

API chính của Cisco cho cơ sở hạ tầng này là API ResTful Của Cisco Intersight. Đây là một API tương thích OpenAPI có thể được thẩm vấn với Swagger và các công cụ OpenAPI nguồn mở khác. Điều này cho phép bạn tạo các SDK chuyên dụng cho các ngôn ngữ và môi trường tùy ý và đơn giản hóa nhiệm vụ ghi lại API (và duy trì SDK).

Cisco cung cấp và duy trì một loạt các SDK cho API Intersight RESTful, bao gồm cả các SDK cho Python và Microsoft PowerShell. Họ cũng cung cấp một loạt các mô-đun Ansible.

**VMware**

CLI chính của VMware bây giờ là Datacenter CLI, cho phép hoạt động dòng lệnh của API vCenter Server và VMware Cloud trên AWS. Nó được viết bằng Python và chạy trên Linux, Mac và Windows.

VMware cũng cung cấp vSphere CLI cho Linux và Windows, cho phép bạn quản lý máy chủ ảo hóa ESXi, máy chủ vCenter và cung cấp một tập hợp con các lệnh DCLI. Nó cũng cung cấp PowerCLI cho Windows PowerShell, cung cấp lệnh ghép ngắn cho môi trường vSphere, vCloud, vRealize Operations Manager, vSAN, NSX-T, VMware Cloud trên AWS, VMware HCX, VMware Site Recovery Manager và môi trường VMware Horizon.

VMware cũng cung cấp một loạt các SDK cho các ngôn ngữ phổ biến (bao gồm Python), nhằm vào vSphere Automation, vCloud Suite, vSAN và các sản phẩm khác.

**OpenStack**

Dự án OpenStack cung cấp OpenStack Client (OSC), được viết bằng Python. OSC cho phép bạn truy cập OpenStack Compute, Identity, Image, Object Storage và Block Storage API.

Cài đặt các máy khách dòng lệnh cũng cài đặt OpenStack Python SDK đi kèm, cho phép một loạt các lệnh OpenStack trong Python.

OpenStack Toolkits cũng có sẵn cho nhiều ngôn ngữ phổ biến khác.

## Tóm tắt kịch bản tự động hóa cơ bản


Các kỹ thuật viết kịch bản tự động hóa cơ bản là tuyệt vời để có trong hộp công cụ của bạn và hiểu chúng sẽ cải thiện cơ sở của bạn như một nhà điều hành và người sử dụng các nền tảng tự động hóa trưởng thành.

