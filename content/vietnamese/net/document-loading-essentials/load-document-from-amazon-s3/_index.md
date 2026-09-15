---
categories:
- Document Management
date: '2026-07-06'
description: Tìm hiểu cách cấu hình thông tin xác thực AWS và tích hợp GroupDocs Annotation
  với Amazon S3 bằng C#. Hướng dẫn từng bước để tải, chú thích và quản lý tài liệu.
keywords:
- configure aws credentials
- document management s3
- read file s3 c#
lastmod: '2026-07-06'
linktitle: Tải tài liệu từ Amazon S3
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to configure AWS credentials and integrate GroupDocs Annotation
    with Amazon S3 using C#. Step-by-step guide for loading, annotating, and managing
    documents.
  headline: Configure AWS Credentials for GroupDocs Annotation S3 Integration
  type: TechArticle
- description: Learn how to configure AWS credentials and integrate GroupDocs Annotation
    with Amazon S3 using C#. Step-by-step guide for loading, annotating, and managing
    documents.
  name: Configure AWS Credentials for GroupDocs Annotation S3 Integration
  steps:
  - name: Define Output Path
    text: 'This creates a local path where your annotated document will be saved.
      The `Path.Combine` method ensures cross‑platform compatibility, and we''re preserving
      the original file extension to maintain document type integrity. **Pro Tip**:
      Consider using a timestamp in your output filename to avoid overwr'
  - name: Specify Document Key
    text: This is your document's unique identifier in the S3 bucket. In real‑world
      scenarios, you'll typically get this from user input, a database record, or
      an API parameter. Make sure the key exactly matches the S3 object name, including
      any folder prefixes (e.g., `documents/2025/sample.pdf`).
  - name: Initialize Annotator
    text: '`Annotator` is the core class in GroupDocs.Annotation that represents an
      editable document session. It provides methods to add, modify, and delete annotations.
      By wrapping the S3 download stream in a `using` block, we ensure proper disposal
      of both the stream and the annotator instance.'
  - name: Create Area Annotation
    text: This creates a rectangular annotation on your document. The `Rectangle(100,
      100, 100, 100)` parameters represent X‑position, Y‑position, width, and height
      respectively. The `BackgroundColor` value `65535` creates a yellow highlight
      – you can customize this using standard RGB color codes. **Common Us
  - name: Add Annotation to Document
    text: This method adds our area annotation to the document. You can call `Add()`
      multiple times to include different annotation types such as text comments,
      arrows, or stamps. The annotations exist in memory until you explicitly save
      the document.
  - name: Save Annotated Document
    text: Now we're saving the annotated document to our specified output path. This
      creates a new file with all annotations embedded. If you need to store the result
      back in S3—a common production scenario—simply upload the file using the S3
      SDK after this step.
  - name: Display Success Message
    text: A simple confirmation message that helps with debugging and provides user
      feedback. In a real application you would replace this with proper logging or
      UI notification.
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation supports 50+ input and output formats—including PDF,
      DOCX, PPTX, and HTML—though annotation types may vary by format.
    question: Is GroupDocs.Annotation for .NET compatible with all document formats?
  - answer: Yes, you can explore the features of GroupDocs.Annotation for .NET by
      accessing the free trial version available [here](https://releases.groupdocs.com/).
      This lets you test S3 integration and annotation capabilities risk‑free.
    question: Can I try GroupDocs.Annotation for .NET before purchasing?
  - answer: Comprehensive documentation for GroupDocs.Annotation for .NET is available
      [here](https://tutorials.groupdocs.com/annotation/net/). The docs include API
      references, advanced examples, and integration guides.
    question: Where can I find documentation for GroupDocs.Annotation for .NET?
  - answer: You can obtain a temporary license for evaluation purposes from [here](https://purchase.groupdocs.com/temporary-license/).
      This removes trial limitations and gives you full access to test production
      scenarios.
    question: Do I need a temporary license to evaluate GroupDocs.Annotation for .NET?
  - answer: For any queries or support‑related issues, you can visit the GroupDocs.Annotation
      forum [here](https://forum.groupdocs.com/c/annotation/10). The community and
      support team are active and helpful for troubleshooting integration problems.
    question: Where can I seek assistance or support for GroupDocs.Annotation for
      .NET?
  type: FAQPage
tags:
- groupdocs
- s3-integration
- document-annotation
- cloud-storage
title: Cấu hình thông tin xác thực AWS cho tích hợp GroupDocs Annotation S3
type: docs
url: /vi/net/document-loading-essentials/load-document-from-amazon-s3/
weight: 10
---

# Cấu hình thông tin xác thực AWS cho tích hợp GroupDocs Annotation S3

Trong hướng dẫn này, bạn sẽ học cách **cấu hình thông tin xác thực AWS** và tích hợp liền mạch GroupDocs.Annotation với Amazon S3 bằng C#. Chúng tôi sẽ hướng dẫn tải tài liệu từ bucket S3, thêm chú thích và lưu kết quả trở lại đám mây, đồng thời đề cập đến các mẹo bảo mật và hiệu suất tốt nhất.

## Câu trả lời nhanh
- **Làm thế nào để cấu hình thông tin xác thực AWS?** Sử dụng hàm khởi tạo `AmazonS3Client` với `BasicAWSCredentials` hoặc dựa vào IAM roles để tự động giải quyết thông tin xác thực.  
- **Các gói NuGet nào cần thiết?** `GroupDocs.Annotation` và `AWSSDK.S3`.  
- **Tôi có thể chú thích các tệp PDF lớn hơn 100 MB không?** Có – sử dụng streaming và async API để tránh tải toàn bộ tệp vào bộ nhớ.  
- **Việc tích hợp có an toàn với đa luồng không?** Tạo một thể hiện `Annotator` riêng cho mỗi yêu cầu; SDK tự nó là không trạng thái.  
- **Tôi có cần mã hoá tài liệu trong S3 không?** Kích hoạt mã hoá phía máy chủ (SSE‑S3 hoặc SSE‑KMS) để tuân thủ và bảo vệ dữ liệu.

## Tại sao nên dùng S3 cho việc chú thích tài liệu?

Sử dụng S3 cho việc chú thích tài liệu cung cấp cho bạn một giải pháp lưu trữ có khả năng mở rộng cao, chi phí hiệu quả và có thể truy cập toàn cầu đồng thời giữ an toàn cho các tệp của bạn.  
- **Khả năng mở rộng**: S3 xử lý gần như không giới hạn các đối tượng, hỗ trợ lên tới 5 TB mỗi tệp và hàng triệu yêu cầu mỗi giây.  
- **Hiệu quả chi phí**: Bạn chỉ trả tiền cho dung lượng lưu trữ thực tế sử dụng, với việc tự động chuyển sang lớp lưu trữ chi phí thấp hơn.  
- **Khả năng truy cập toàn cầu**: Truy cập độ trễ thấp từ bất kỳ khu vực AWS nào đảm bảo tài liệu đã chú thích luôn sẵn sàng.  
- **Bảo mật**: Mã hoá tích hợp (SSE‑S3, SSE‑KMS) và các chính sách IAM chi tiết bảo vệ dữ liệu nhạy cảm.  
- **Tích hợp**: Hoạt động một cách tự nhiên với các dịch vụ AWS hiện có như CloudFront, Lambda và IAM.

## Yêu cầu trước

1. **Môi trường phát triển C#** – Visual Studio hoặc VS Code với hỗ trợ .NET.  
2. **GroupDocs.Annotation cho .NET** – Tải xuống từ [trang web chính thức](https://releases.groupdocs.com/annotation/net/).  
3. **Quyền truy cập AWS S3** – Thông tin xác thực AWS hợp lệ với quyền đọc/ghi trên bucket mục tiêu.  
4. **Kiến thức cơ bản về C#** – Hiểu về lớp, async/await và streams.  
5. **Amazon S3 SDK** – Cài đặt qua NuGet (`AWSSDK.S3`).  

## Cách cấu hình thông tin xác thực AWS để truy cập S3?

`BasicAWSCredentials` là một lớp chứa AWS access key ID và secret access key.  
`AmazonS3Client` là client của AWS SDK dùng để tương tác với dịch vụ S3.

Tải khóa AWS của bạn một lần và để SDK tái sử dụng chúng cho mỗi yêu cầu. Cách đơn giản nhất là tạo một đối tượng `BasicAWSCredentials` và truyền nó vào hàm khởi tạo `AmazonS3Client`. Đối với môi trường sản xuất, nên ưu tiên IAM roles hoặc biến môi trường để tránh mã hoá cứng các bí mật.

**Mẹo**: Khi chạy trên EC2, ECS hoặc Lambda, bỏ qua việc cung cấp thông tin xác thực rõ ràng và để SDK tự động lấy thông tin tạm thời từ instance profile.

## Nhập các namespace

Hãy bắt đầu bằng việc nhập tất cả các namespace cần thiết cho tích hợp S3 của chúng ta:

```csharp
using Amazon.S3;
using Amazon.S3.Model;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
```

Các import này cho phép chúng ta truy cập các thao tác AWS S3 và chức năng chú thích của GroupDocs. Namespace `Amazon.S3` xử lý các tương tác lưu trữ đám mây, trong khi `GroupDocs.Annotation.Models` cung cấp khung chú thích.

## Triển khai từng bước

Bây giờ chúng ta sẽ đi qua quy trình đầy đủ để tải tài liệu từ S3 và thêm chú thích. Chúng tôi sẽ chia thành các bước dễ quản lý để bạn có thể theo dõi.

### Bước 1: Xác định đường dẫn đầu ra

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

Điều này tạo ra một đường dẫn cục bộ nơi tài liệu đã chú thích sẽ được lưu. Phương thức `Path.Combine` đảm bảo khả năng tương thích đa nền tảng, và chúng tôi giữ nguyên phần mở rộng tệp gốc để duy trì tính toàn vẹn của loại tài liệu.

**Mẹo**: Xem xét sử dụng dấu thời gian trong tên tệp đầu ra để tránh ghi đè các chú thích trước đó: `"result_" + DateTime.Now.ToString("yyyyMMdd_HHmmss") + Path.GetExtension("input.pdf")`.

### Bước 2: Xác định khóa tài liệu

```csharp
string key = "sample.pdf";
```

Đây là định danh duy nhất của tài liệu trong bucket S3. Trong thực tế, bạn thường nhận được giá trị này từ đầu vào của người dùng, bản ghi trong cơ sở dữ liệu hoặc tham số API. Đảm bảo khóa khớp chính xác với tên đối tượng S3, bao gồm cả tiền tố thư mục (ví dụ, `documents/2025/sample.pdf`).

### Bước 3: Khởi tạo Annotator

`Annotator` là lớp cốt lõi trong GroupDocs.Annotation đại diện cho một phiên làm việc tài liệu có thể chỉnh sửa. Nó cung cấp các phương thức để thêm, sửa đổi và xóa chú thích.

```csharp
using (Annotator annotator = new Annotator(DownloadFile(key)))
{
```

Bằng cách bao bọc luồng tải xuống S3 trong một khối `using`, chúng ta đảm bảo việc giải phóng đúng cách cả luồng và thể hiện `annotator`.

### Bước 4: Tạo chú thích vùng

```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
```

Điều này tạo một chú thích hình chữ nhật trên tài liệu của bạn. Các tham số `Rectangle(100, 100, 100, 100)` lần lượt đại diện cho vị trí X, vị trí Y, chiều rộng và chiều cao. Giá trị `BackgroundColor` `65535` tạo ra một vùng tô sáng màu vàng – bạn có thể tùy chỉnh bằng các mã màu RGB tiêu chuẩn.

**Các trường hợp sử dụng phổ biến cho chú thích vùng**:
- Làm nổi bật các phần quan trọng trong hợp đồng  
- Đánh dấu các khu vực xem xét trong tài liệu kỹ thuật  
- Thêm các chú thích trực quan vào các slide trình chiếu  

### Bước 5: Thêm chú thích vào tài liệu

```csharp
annotator.Add(area);
```

Phương thức này thêm chú thích vùng của chúng ta vào tài liệu. Bạn có thể gọi `Add()` nhiều lần để bao gồm các loại chú thích khác nhau như bình luận văn bản, mũi tên hoặc dấu. Các chú thích tồn tại trong bộ nhớ cho đến khi bạn lưu tài liệu một cách rõ ràng.

### Bước 6: Lưu tài liệu đã chú thích

```csharp
annotator.Save(outputPath);
```

Bây giờ chúng ta đang lưu tài liệu đã chú thích vào đường dẫn đầu ra đã chỉ định. Điều này tạo ra một tệp mới với tất cả các chú thích được nhúng. Nếu bạn cần lưu kết quả trở lại S3 — một kịch bản sản xuất phổ biến — chỉ cần tải tệp lên bằng S3 SDK sau bước này.

### Bước 7: Hiển thị thông báo thành công

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

Một thông báo xác nhận đơn giản giúp việc gỡ lỗi và cung cấp phản hồi cho người dùng. Trong một ứng dụng thực tế, bạn sẽ thay thế điều này bằng việc ghi log thích hợp hoặc thông báo giao diện người dùng.

## Triển khai phương thức tải xuống S3

Bạn sẽ nhận thấy chúng tôi đã tham chiếu tới phương thức `DownloadFile(key)` mà chưa triển khai. Dưới đây là cách tạo helper quan trọng này:

```csharp
private static Stream DownloadFile(string key)
{
    var client = new AmazonS3Client("your-access-key", "your-secret-key", Amazon.RegionEndpoint.USEast1);
    var request = new GetObjectRequest
    {
        BucketName = "your-bucket-name",
        Key = key
    };
    
    var response = client.GetObjectAsync(request).Result;
    return response.ResponseStream;
}
```

**Lưu ý bảo mật**: Không bao giờ mã hoá cứng thông tin xác thực AWS trong mã sản xuất. Sử dụng IAM roles, biến môi trường, hoặc tệp credentials chia sẻ để giữ bí mật khỏi việc kiểm soát nguồn.

## Cách tải tài liệu từ Amazon S3?

`GetObjectAsync` là một phương thức bất đồng bộ lấy một đối tượng từ S3 và trả về phản hồi chứa một luồng.  
`MemoryStream` là một luồng .NET lưu dữ liệu trong bộ nhớ, cho phép đọc/ghi nhanh mà không cần I/O đĩa.  
`Annotator` (như đã định nghĩa ở trên) là lớp tải tài liệu để chú thích.

Tải PDF trực tiếp từ S3 bằng phương thức `GetObjectAsync`, bao bọc luồng phản hồi trong một `MemoryStream`, và truyền nó vào hàm khởi tạo `Annotator`. Cách này tránh việc ghi tệp gốc ra đĩa, giảm tải I/O và cho phép bạn làm việc với các tệp lớn một cách hiệu quả trong khi kiểm soát mức sử dụng bộ nhớ.

```csharp
using (var response = await s3Client.GetObjectAsync(bucketName, key))
using (var memoryStream = new MemoryStream())
{
    await response.ResponseStream.CopyToAsync(memoryStream);
    memoryStream.Position = 0;
    using (var annotator = new Annotator(memoryStream))
    {
        // Add annotations here
    }
}
```

## Các vấn đề tích hợp thường gặp & Giải pháp

Dựa trên kinh nghiệm thực tế, dưới đây là các vấn đề thường gặp và cách giải quyết chúng:

### Vấn đề 1: Lỗi "Access Denied"

**Vấn đề**: Ứng dụng của bạn không thể truy cập các đối tượng S3.  
**Giải pháp**: Kiểm tra xem IAM user hoặc role của bạn có quyền `s3:GetObject` cho bucket và các đối tượng cụ thể không.

### Vấn đề 2: Hết thời gian khi xử lý tệp lớn

**Vấn đề**: Tài liệu lớn hơn 50 MB gây lỗi timeout.  
**Giải pháp**: Triển khai các hoạt động bất đồng bộ và tăng giá trị timeout:

```csharp
var client = new AmazonS3Client();
client.Config.Timeout = TimeSpan.FromMinutes(10);
```

### Vấn đề 3: Vấn đề bộ nhớ khi xử lý nhiều tài liệu

**Vấn đề**: Xử lý nhiều tài liệu gây ra ngoại lệ hết bộ nhớ.  
**Giải pháp**: Giải phóng luồng kịp thời và xử lý tài liệu theo lô.

### Vấn đề 4: Lỗi không khớp khu vực

**Vấn đề**: Client S3 không thể tìm thấy bucket của bạn.  
**Giải pháp**: Đảm bảo `RegionEndpoint` khớp với khu vực thực tế của bucket.

## Thực hành tốt về hiệu suất & bảo mật

### Tối ưu hoá hiệu suất
- **Sử dụng phương thức Async**: Ưu tiên `GetObjectAsync()` thay vì các lời gọi đồng bộ.  
- **Triển khai caching**: Lưu các tài liệu thường truy cập cục bộ trong thời gian ngắn.  
- **Thao tác batch**: Xử lý nhiều tệp đồng thời khi thích hợp.  
- **Xử lý bằng stream**: Tránh tải toàn bộ tài liệu lớn vào bộ nhớ; làm việc với stream.

### Các cân nhắc bảo mật
- **Sử dụng IAM Roles**: Loại bỏ việc mã hoá cứng thông tin xác thực.  
- **Kích hoạt mã hoá S3**: Kích hoạt mã hoá phía máy chủ (SSE‑S3 hoặc SSE‑KMS).  
- **Triển khai ghi log truy cập**: Theo dõi ai truy cập tài liệu nào.  
- **Xác thực loại tệp**: Kiểm tra phần mở rộng và MIME type trước khi xử lý.

## Các trường hợp sử dụng thực tế

Mẫu tích hợp S3 này tỏa sáng trong nhiều ngành công nghiệp:
1. **Đánh giá tài liệu pháp lý** – Các công ty luật chú thích hợp đồng lưu trữ trên S3.  
2. **Nền tảng giáo dục** – Giáo viên đánh dấu bài nộp của học sinh được lưu trữ trên đám mây.  
3. **Quản lý xây dựng** – Kiến trúc sư chú thích bản vẽ kỹ thuật trên nhiều khu vực.  
4. **Hồ sơ y tế** – Nhà cung cấp dịch vụ y tế thêm ghi chú vào tài liệu bệnh nhân một cách an toàn.  
5. **Dịch vụ tài chính** – Kiểm toán viên hợp tác trên các tài liệu tuân thủ lưu trữ trong S3.

## Hướng dẫn khắc phục sự cố

**Không thể tải tài liệu từ S3**
- Kiểm tra thông tin xác thực AWS và quyền bucket.  
- Kiểm tra lại tên bucket và chính tả của khóa đối tượng.  
- Đảm bảo tài liệu không bị hỏng trong S3.

**Chú thích không hiển thị**
- Xác nhận bạn đã gọi `annotator.Save()` sau khi thêm chú thích.  
- Kiểm tra định dạng tài liệu có hỗ trợ loại chú thích bạn đã dùng không.  
- Đảm bảo tọa độ chú thích nằm trong giới hạn trang.

**Vấn đề hiệu suất**
- Giám sát tần suất yêu cầu S3 và triển khai back‑off theo cấp số nhân.  
- Sử dụng CloudFront CDN cho các tệp thường truy cập.  
- Xem xét S3 Transfer Acceleration cho các ứng dụng toàn cầu.

## Câu hỏi thường gặp

**Q: GroupDocs.Annotation cho .NET có tương thích với tất cả các định dạng tài liệu không?**  
A: GroupDocs.Annotation hỗ trợ hơn 50 định dạng đầu vào và đầu ra — bao gồm PDF, DOCX, PPTX và HTML — mặc dù các loại chú thích có thể khác nhau tùy theo định dạng.

**Q: Tôi có thể dùng thử GroupDocs.Annotation cho .NET trước khi mua không?**  
A: Có, bạn có thể khám phá các tính năng của GroupDocs.Annotation cho .NET bằng cách truy cập phiên bản dùng thử miễn phí có sẵn [tại đây](https://releases.groupdocs.com/). Điều này cho phép bạn thử nghiệm tích hợp S3 và khả năng chú thích mà không rủi ro.

**Q: Tôi có thể tìm tài liệu cho GroupDocs.Annotation cho .NET ở đâu?**  
A: Tài liệu đầy đủ cho GroupDocs.Annotation cho .NET có sẵn [tại đây](https://tutorials.groupdocs.com/annotation/net/). Tài liệu bao gồm tham chiếu API, các ví dụ nâng cao và hướng dẫn tích hợp.

**Q: Tôi có cần giấy phép tạm thời để đánh giá GroupDocs.Annotation cho .NET không?**  
A: Bạn có thể nhận giấy phép tạm thời để đánh giá từ [đây](https://purchase.groupdocs.com/temporary-license/). Điều này loại bỏ các hạn chế của bản dùng thử và cho phép bạn truy cập đầy đủ để thử nghiệm các kịch bản sản xuất.

**Q: Tôi có thể tìm trợ giúp hoặc hỗ trợ cho GroupDocs.Annotation cho .NET ở đâu?**  
A: Đối với bất kỳ câu hỏi hoặc vấn đề hỗ trợ nào, bạn có thể truy cập diễn đàn GroupDocs.Annotation [tại đây](https://forum.groupdocs.com/c/annotation/10). Cộng đồng và đội ngũ hỗ trợ hoạt động tích cực và hữu ích trong việc khắc phục các vấn đề tích hợp.

**Q: Tôi có thể lưu tài liệu đã chú thích trở lại S3 thay vì lưu cục bộ không?**  
A: Chắc chắn! Sau khi gọi `annotator.Save(localPath)`, bạn có thể tải tệp đã chú thích lên S3 bằng phương thức `PutObjectAsync()`. Điều này tạo ra một quy trình làm việc hoàn toàn đám mây‑đến‑đám mây, lý tưởng cho các ứng dụng web.

**Q: Kích thước tệp tối đa được hỗ trợ cho việc chú thích tài liệu trên S3 là bao nhiêu?**  
A: Mặc dù GroupDocs.Annotation có thể xử lý các tệp lớn, giới hạn thực tế phụ thuộc vào bộ nhớ máy chủ và thời gian chờ truyền tải S3. Đối với các tệp lớn hơn 100 MB, hãy triển khai streaming hoặc xử lý theo khối để tránh cạn kiệt bộ nhớ.

---

**Cập nhật lần cuối:** 2026-07-06  
**Kiểm tra với:** GroupDocs.Annotation 23.12 cho .NET  
**Tác giả:** GroupDocs  

```csharp
var credentials = new BasicAWSCredentials("YOUR_ACCESS_KEY", "YOUR_SECRET_KEY");
var s3Client = new AmazonS3Client(credentials, RegionEndpoint.USEast1);
```

## Các hướng dẫn liên quan

- [Tải tài liệu GroupDocs.Annotation .NET](/annotation/net/document-loading-essentials/)
- [Cách tải tài liệu từ FTP .NET - Hướng dẫn đầy đủ của GroupDocs](/annotation/net/document-loading/groupdocs-annotation-net-load-from-ftp/)
- [Xem trước tài liệu .NET - Hướng dẫn đầy đủ của GroupDocs.Annotation](/annotation/net/document-preview/)
