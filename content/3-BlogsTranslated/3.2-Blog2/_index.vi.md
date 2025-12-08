---
title: "Blog 2"
date: 2025-09-30
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---



# **Cách tiếp cận dựa trên dữ liệu: Tối ưu chi phí ondemand của AWS Elemental MediaLive**

Bởi **Krutarth Doshi** , ngày 08 THÁNG 5, 2025 | trong [Amazon QuickSight](https://aws.amazon.com/blogs/media/category/analytics/amazon-quicksight/), [Analytics](https://aws.amazon.com/blogs/media/category/analytics/), [AWS Elemental MediaLive](https://aws.amazon.com/blogs/media/category/media-services/aws-elemental-medialive/), [Data Science & Analytics for Media](https://aws.amazon.com/blogs/media/category/industries/entertainment/data-science/), [Industries](https://aws.amazon.com/blogs/media/category/industries/), [Media & Entertainment,](https://aws.amazon.com/blogs/media/category/industries/entertainment/) [Media Services](https://aws.amazon.com/blogs/media/category/media-services/), [Monetization](https://aws.amazon.com/blogs/media/category/industries/entertainment/monetization/) | [Liên kết cố định](https://aws.amazon.com/blogs/media/data-driven-approach-optimizing-on-demand-cost-of-aws-elemental-medialive/)

Trong thế giới phát trực tiếp video luôn biến động, tối ưu chi phí đồng thời duy trì chất lượng dịch vụ cao là thách thức thường trực với các công ty truyền thông. Amazon Web Services [(AWS) Elemental MediaLive](https://aws.amazon.com/medialive/), dịch vụ xử lý video trực tiếp trên đám mây, cung cấp các [tùy chọn giá](https://aws.amazon.com/medialive/pricing/) linh hoạt để giúp giải quyết thách thức này. Tuy nhiên, xác định sự cân bằng phù hợp giữa ondemand và reserved đòi hỏi phải phân tích cẩn thận các mẫu hình sử dụng.

Chúng tôi sẽ hướng dẫn bạn cách tiếp cận dựa trên dữ liệu để quản lý đặt chỗ [(reservations) của MediaLive](https://docs.aws.amazon.com/medialive/latest/ug/reservations.html). Tận dụng sức mạnh của [AWS Cost and Usage Reports (AWS CUR)](https://aws.amazon.com/aws-cost-management/aws-cost-and-usage-reporting/) và [Amazon QuickSight,](https://sunnycloudvn.com/kham-pha-aws-amazon-quicksight-khai-thac-tiem-nang-du-lieu-cho-doanh-nghiep/) bạn sẽ có được thông tin chuyên sâu về mức sử dụng MediaLive. Điều này sẽ giúp bạn đưa ra quyết định sáng suốt về đặt chỗ và có thể giảm chi phí.

Trước khi đi sâu vào phân tích, hãy điểm lại các tùy chọn giá cho AWS Elemental MediaLive:

1. **OnDemand pricing**: Chỉ trả tiền cho tài nguyên bạn dùng; bạn trả theo giờ cho việc chạy [inputs](https://aws.amazon.com/medialive/pricing/#Input_pricing), [outputs](https://aws.amazon.com/medialive/pricing/#Output_pricing) và [các tính năng bổ sung](https://aws.amazon.com/medialive/pricing/#Add-on_features). Tùy chọn này mang lại sự linh hoạt tối đa nhưng có thể dẫn đến chi phí cao hơn khi sử dụng ổn định.  
2. **Reserved pricing**: Cam kết dùng MediaLive trong kỳ hạn 12 tháng để đổi lấy mức chiết khấu lên đến 70% so với giá ondemand. Tùy chọn này có thể mang lại tiết kiệm đáng kể cho khối lượng công việc dự đoán được.

Chìa khóa để tối ưu chi phí là tìm được tỷ lệ phù hợp giữa ondemand và reserved dựa trên mẫu hình sử dụng cụ thể của bạn.

## **Điều kiện tiên quyết**

Những điều sau cần có sẵn trước khi thử nghiệm giải pháp:

* Để trực quan hóa chi tiêu MediaLive, bạn cần quyền phù hợp để truy cập [AWS CUR](https://docs.aws.amazon.com/cur/latest/userguide/cur-s3.html), [Amazon Athena](https://aws.amazon.com/athena/) và [QuickSight](https://docs.aws.amazon.com/quicksight/latest/user/athena.html). Bạn nên tuân theo mô hình đặc quyền tối thiểu khi dùng [AWS Identity and Access Management (IAM)](https://aws.amazon.com/iam/), tham khảo tài liệu thực hành [bảo mật tốt nhất của IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) và tự tiến hành thẩm định khi thiết lập.

* Bật AWS CUR nếu chưa bật. Hướng dẫn: [Creating Cost and Usage Reports](https://docs.aws.amazon.com/cur/latest/userguide/creating-cur.html).  
  * Độ phân giải (granularity) của AWS CUR phải ở mức theo giờ để triển khai giải pháp này. Dữ liệu báo cáo chi phí và sử dụng theo giờ là cần thiết để phân tích chính xác mẫu hình sử dụng và đưa ra quyết định đặt chỗ sáng suốt cho khối lượng công việc MediaLive của bạn.  
      
* Thiết lập Athena để phân tích dữ liệu từ S3 bucket đang lưu dữ liệu AWS CUR của bạn. Hướng dẫn: [Querying Cost and Usage Reports using Amazon Athena](https://docs.aws.amazon.com/cur/latest/userguide/cur-query-athena.htmlhttps://docs.aws.amazon.com/cur/latest/userguide/cur-query-athena.htmlhttps://docs.aws.amazon.com/cur/latest/userguide/cur-query-athena.htmlhttps://docs.aws.amazon.com/cur/latest/userguide/cur-query-athena.htmlhttps://docs.aws.amazon.com/cur/latest/userguide/cur-query-athena.htmlhttps://docs.aws.amazon.com/cur/latest/userguide/cur-query-athena.html).  
    
* Thiết lập QuickSight để trực quan hóa dữ liệu từ chế độ xem (view) Athena của bạn. Hướng dẫn: [Setting up for Amazon QuickSight](https://docs.aws.amazon.com/quicksight/latest/user/setting-up.html).

## **Giải pháp**

### 

### **Tạo cơ sở dữ liệu Amazon Athena cho dữ liệu AWS CUR**

Nếu đây là lần đầu bạn dùng dữ liệu AWS CUR với Athena, bạn sẽ cần tạo cơ sở dữ liệu và bảng Athena với dữ liệu AWS CUR. Để làm điều này, hãy thực hiện một trong các bước sau:

* Dùng [AWS CloudFormation](https://docs.aws.amazon.com/cur/latest/userguide/use-athena-cf.html) (khuyến nghị) để tích hợp AWS CUR với Athena.

Hoặc

* Thực hiện cách tạo bảng Athena [thủ công](https://docs.aws.amazon.com/cur/latest/userguide/cur-ate-manual.html). Bạn sẽ cần lặp lại bước này ít nhất mỗi tháng một lần, vì bảng chỉ bao gồm dữ liệu từ bản AWS CUR hiện tại.

### **Tạo một view Amazon Athena từ dữ liệu AWS CUR để truy vấn thông tin**

[Athena view](https://docs.aws.amazon.com/athena/latest/ug/views.html) là một bảng logic, cho phép người dùng lưu truy vấn SQL dưới dạng bảng ảo, mỗi lần truy vấn sẽ lấy dữ liệu mới nhất từ các nguồn bên dưới.

1. Để tạo view eml_od_usage, sao chép truy vấn SQL từ [CUR Query Library (MediaLive OnDemand Usage)](https://catalog.workshops.aws/cur-query-library/en-US/queries/media_services#medialive-ondemand-usage-optimization) vào trình soạn thảo Athena.  
     
2. Truy vấn chứa ${table_name} là placeholder cần được thay thế trước khi chạy. Ví dụ, nếu bảng AWS CUR của bạn tên là cur_table và nằm trong cơ sở dữ liệu cur_db, bạn sẽ thay **${table_name}** bằng **cur_db.cur_table.**  
     
3. Thêm câu lệnh sau vào đầu truy vấn rồi chạy:   
   CREATE OR REPLACE VIEW "eml_od_usage" AS  
   ![][image1]

   *Hình 1: Tạo một view Amazon Athena.*

View này sẽ cung cấp dữ liệu cần thiết để xây dựng bảng điều khiển (dashboard) QuickSight và trực quan hóa chi tiêu của MediaLive theo thời gian.

### **Cấu hình Amazon QuickSight để truy cập view Amazon Athena**

Tiếp theo, để truy cập view Athena trong Amazon QuickSight, hãy [tạo một QuickSight datase](https://docs.aws.amazon.com/quicksight/latest/user/create-a-data-set-athena.html)t sử dụng các Athena views.

1.Thêm view eml_od_usage từ các Athena views vào Amazon QuickSight làm dataset

![][image2]

*Hình 2: Thêm Amazon Athena view vào dataset của Amazon QuickSight*

2.Chọn "Chế độ truy vấn" là **SPICE**. Nhấp vào **PUBLISH & VISUALIZE**, thao tác này sẽ tạo một [Phân tích QuickSight](https://docs.aws.amazon.com/quicksight/latest/user/creating-an-analysis.html) mới.  
![][image3]  
*Hình 3: Xem trước (Preview) dataset Amazon QuickSight trước khi trực quan hóa*

3. Sau khi thêm tập dữ liệu, hãy [thêm lịch làm mới](https://docs.aws.amazon.com/quicksight/latest/user/refreshing-imported-data.html#schedule-data-refresh) để tập dữ liệu nhận dữ liệu mới từ AWS CUR. Khuyến nghị nên làm mới tập dữ liệu hàng ngày hoặc hàng tuần để có trải nghiệm trực quan tốt hơn.

![][image4]  
*Hình 4: Thêm calculated fields (trường tính toán) vào dataset Amazon QuickSight*

### **Tạo trực quan hóa cho đặt chỗ (reservation) AWS Elemental MediaLiv**e

Sau khi đã thêm tập dữ liệu, chúng ta sẽ [thêm hình ảnh trực quan](https://docs.aws.amazon.com/quicksight/latest/user/creating-a-visual.html) vào phân tích mới mở. Phân tích QuickSight là một tính năng trong Amazon QuickSight cho phép người dùng tạo hình ảnh trực quan tương tác và thực hiện phân tích dữ liệu trên các tập dữ liệu. Tính năng này cho phép người dùng khám phá dữ liệu thông qua biểu đồ, bảng và bảng thông tin, cung cấp thông tin chi tiết với tính năng lọc, tính toán và chế độ xem tùy chỉnh.

 Làm theo các bước dưới đây:

1.Bắt đầu từ trang phân tích, chúng ta sẽ thêm hình ảnh trực quan "Chi tiêu theo yêu cầu theo ID tài khoản".

* Trong thanh bên trái, nhấp vào nút **Thêm** trong phần "Hình ảnh trực quan".  
* Chọn **Biểu đồ hình tròn** làm loại hình ảnh trực quan.  
* Trong cột "Dữ liệu", hãy đảm bảo bạn đã chọn **eml_od_usage** (Hình 5).  
* Trong danh sách trường, chọn **line_item_usage_account_id** và sum_line_item_unblended_cost.  
* Thay đổi "sum_line_item_unblended_cost" thành **Tổng** bằng cách [sử dụng một trường.](https://docs.aws.amazon.com/quicksight/latest/user/changing-field-aggregation.html#change-field-aggregation-field-wells)

  *![][image5]*


   *Hình 5: Bảng QuickSight hiển thị chi phí OnDemand theo Account ID và Input Usage Type.*

2.Vẫn trên trang phân tích, chúng ta sẽ thêm hình ảnh trực quan "Chi phí theo yêu cầu theo ID tài khoản và Loại sử dụng".

* Trong thanh bên trái, nhấp vào nút **Thêm** trong phần "Hình ảnh trực quan".  
* Chọn Bảng làm loại hình trực quan.  
* Trong cột "Dữ liệu", hãy đảm bảo bạn có **eml_od_usage.**  
* Trong danh sách trường, hãy chọn line_item_usage_account_id, line_item_usage_type, round_sum_line_item_usage_amount và **sum_line_item_unblended_cost**.  
* Thay đổi "round_sum_line_item_usage_amount" và "sum_line_item_unblended_cost" thành **Tổng** bằng cách sử dụng một trường.

  ![][image6]

  *Hình  6: Bảng QuickSight hiển thị số lượng khuyến nghị đặt chỗ theo tài khoản và loại sử dụng.*

3.Tiếp tục trên trang phân tích của bạn, chúng tôi sẽ thêm hình ảnh trực quan "Đề xuất Đặt phòng theo Loại Sử dụng".

* Trong thanh bên trái, nhấp vào nút **Thêm** trong phần "Hình ảnh trực quan".  
* Chọn **Bảng** làm loại hình trực quan.  
* Trong cột "Dữ liệu", hãy đảm bảo bạn có **eml_od_usage**.  
* Trong danh sách trường, hãy chọn **line_item_usage_type, round_sum_line_item_usage_amount, sum_line_item_unblended_cost** và **Số lượng đặt phòng được đề xuất.**  
* Thay đổi "round_sum_line_item_usage_amount" và "sum_line_item_unblended_cost" thành **Tổng** bằng cách sử dụng ô trường.  
* Thay đổi "số lượng đặt phòng được đề xuất" thành **Trung bình** bằng cách sử dụng ô trường.

  ![][image7]

 *Hình 7 : Biểu đồ QuickSight thể hiện phân bố chi tiêu On‑Demand.*

4.Trên cùng trang phân tích, chúng tôi sẽ thêm hình ảnh trực quan "Số lượng đặt chỗ được đề xuất và Chi tiêu theo yêu cầu".

* Trong thanh bên trái, nhấp vào nút **Thêm** trong phần "Hình ảnh trực quan".  
* Chọn **Biểu đồ đường** làm loại hình ảnh.  
* Trong cột "Dữ liệu", hãy đảm bảo bạn có **eml_od_usage.**  
* Trong danh sách trường, chọn **line_item_usage_end_date**, **số lượng đặt chỗ được đề xuất** và **sum_line_item_unblended_cost.**  
* Tổng hợp "line_item_usage_end_date" theo **TUẦN**.  
* Thay đổi "số lượng đặt chỗ được đề xuất" thành **Trung bình** bằng cách sử dụng ô trường.  
* Thay đổi "sum_line_item_unblended_cost" thành **Tổng** bằng cách sử dụng ô trường.

  ![][image8]

*Hình 8: Biểu đồ/Bảng QuickSight cho Recommended reservations vs OnDemand Spend.*

Sau khi hoàn thành các bước trên  
- Bạn sẽ có một trang phân tích (analysis) như Hình 9. Phân tích này cung cấp cái nhìn tổng hợp về chi tiêu OnDemand của AWS Elemental MediaLive, đồng thời cho biết các đề xuất đặt chỗ (reservations) được phân tách theo tài khoản và loại sử dụng.

- Bạn có [thể xuất bản dưới dạng dashboard](https://docs.aws.amazon.com/quicksight/latest/user/creating-a-dashboard.html), [chia sẻ với nhóm phụ trách](https://docs.aws.amazon.com/quicksight/latest/user/sharing-a-dashboard.html) để theo dõi mức chi tiêu và sử dụng của MediaLive theo thời gian.

![][image9]  
*Hình 9: Dashboard Amazon QuickSight cho phân tích chi phí và khuyến nghị đặt chỗ của AWS Elemental MediaLive*

## **Ra quyết định đặt chỗ dựa trên dữ liệu**

- Với kết quả này, bạn có thể đánh giá một cách định lượng các quyết định đặt chỗ MediaLive. Bắt đầu bằng cách xác định tài khoản có chi phí OnDemand cao nhất, sau đó xem các mẫu hình sử dụng (usage patterns). Kết hợp số lượng đề xuất đặt chỗ với xu hướng chi tiêu để quyết định quy mô đặt chỗ phù hợp.

- Khi xây dựng luận cứ kinh doanh, hãy xem xét cả các thành phần có chi tiêu OnDemand ổn định và tiềm năng tăng trưởng. Dữ liệu theo giờ từ AWS CUR giúp bạn đo lường độ đều đặn của việc sử dụng, từ đó cân nhắc thời điểm mua đặt chỗ để tối đa hóa tiết kiệm. Với các tải không đều hoặc chiến dịch ngắn hạn, cân nhắc giữ linh hoạt để tránh bị ràng buộc quá mức.

## 

## **Triển khai và giám sát chiến lược đặt chỗ**

-Sau khi hoàn thiện chiến lược đặt chỗ MediaLive, hãy bắt đầu bằng cách mua các đặt chỗ đã chọn thông qua [AWS Management Console](https://docs.aws.amazon.com/medialive/latest/ug/purchasing-reservations.html) hoặc [API](https://docs.aws.amazon.com/medialive/latest/apireference/offerings-offeringid-purchase.html). Để duy trì hiệu quả tối ưu, hãy triển khai một hệ thống giám sát mạnh mẽ sử dụng dữ liệu AWS CUR và bảng điều khiển QuickSight để theo dõi mức sử dụng đặt chỗ của bạn.

[Hãy chủ động bằng cách thiết lập cảnh báo](https://docs.aws.amazon.com/quicksight/latest/user/subscriber-alerts.html) để thông báo cho bạn về bất kỳ đặt chỗ nào chưa được sử dụng hết hoặc mức sử dụng theo yêu cầu tăng đột biến. Hãy nhớ rằng mô hình sử dụng tự nhiên thay đổi theo thời gian, vì vậy hãy ưu tiên việc thường xuyên xem xét và điều chỉnh chiến lược đặt chỗ của bạn. Việc đánh giá liên tục này sẽ xác minh cơ sở hạ tầng MediaLive của bạn tiếp tục mang lại giá trị tối đa và hiệu quả chi phí cho tổ chức của bạn.

## **Kết luận**

Bằng cách tận dụng dữ liệu Báo cáo Chi phí và Mức sử dụng AWS cùng khả năng hiển thị trực quan của Amazon QuickSight, bạn có thể tối ưu hóa chi phí AWS Elemental MediaLive thông qua việc sử dụng các tùy chọn đặt chỗ một cách chiến lược. Phương pháp tiếp cận dựa trên dữ liệu này khẳng định rằng bạn đang đưa ra những quyết định sáng suốt, cân bằng giữa việc tiết kiệm chi phí với tính linh hoạt cần thiết cho khối lượng công việc xử lý phương tiện của mình.

Hãy nhớ rằng, chìa khóa để tối ưu hóa chi phí thành công là phân tích và điều chỉnh liên tục. Hãy thường xuyên xem lại dữ liệu AWS CUR, bảng thông tin QuickSight và chiến lược đặt chỗ để đảm bảo bạn luôn nhận được giá trị cao nhất từ việc sử dụng MediaLive.

Để tìm hiểu thêm về AWS Elemental MediaLive và các tùy chọn giá, hãy truy cập trang giá của AWS Elemental MediaLive.  
 Liên hệ với [Đại diện AWS](https://pages.awscloud.com/Media-and-Entertainment-Contact-Us.html) để biết cách chúng tôi có thể giúp thúc đẩy hoạt động kinh doanh của bạn.  
**Krutarth Doshi** 

**Krutarth Doshi là Quản lý Tài khoản Kỹ thuật Cấp cao tại AWS với hơn 10 năm kinh nghiệm, chuyên hỗ trợ khách hàng là Nhà cung cấp Phần mềm Độc lập (ISV) trong hai năm qua. Anh ấy nổi trội trong việc phát triển các giải pháp tùy chỉnh cho các truy vấn Báo cáo Chi phí và Sử dụng (CUR) và trực quan hóa chúng bằng QuickSight, tập trung giải quyết các thách thức kỹ thuật phức tạp.**

[image1]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-1.jpg
[image2]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-2.jpg
[image3]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-3.jpg
[image4]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-4.jpg
[image5]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-5.jpg
[image6]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-6.jpg
[image7]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-7.jpg
[image8]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-8.jpg
[image9]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-9.jpg
