---
categories:
- Document Processing
date: '2026-08-19'
description: Tìm hiểu cách download PDF từ S3 và annotate PDF bằng C# sử dụng GroupDocs.Annotation
  cho .NET. Mã mẫu từng bước, performance tips và troubleshooting.
keywords:
- download pdf from s3
- c# annotate pdf
- groupdocs.annotation .net
lastmod: '2026-08-19'
linktitle: Hướng dẫn PDF Annotation AWS S3 .NET
og_description: Download PDF từ S3 và annotate nó trong C# bằng GroupDocs.Annotation
  cho .NET. Hướng dẫn này đưa bạn qua streaming, các loại annotation, và best‑practice
  performance optimizations.
og_image_alt: Guide showing how to download a PDF from AWS S3 and add annotations
  using GroupDocs.Annotation .NET
og_title: Download PDF từ S3 và annotate với GroupDocs .NET
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn how to download PDF from S3 and c# annotate PDF using GroupDocs.Annotation
    for .NET. Step-by-step code, performance tips, and troubleshooting.
  headline: How to download PDF from S3 and annotate with GroupDocs .NET
  type: TechArticle
- description: Learn how to download PDF from S3 and c# annotate PDF using GroupDocs.Annotation
    for .NET. Step-by-step code, performance tips, and troubleshooting.
  name: How to download PDF from S3 and annotate with GroupDocs .NET
  steps:
  - name: '**Free trial** – evaluate all features without a license key.'
    text: '**Free trial** – evaluate all features without a license key.'
  - name: '**Temporary license** – request a short‑term key from the GroupDocs website.'
    text: '**Temporary license** – request a short‑term key from the GroupDocs website.'
  - name: '**Commercial license** – purchase for unlimited production processing.'
    text: '**Commercial license** – purchase for unlimited production processing.'
  type: HowTo
- questions:
  - answer: Save the annotated document to a `MemoryStream`, then create a `PutObjectRequest`
      and call `PutObjectAsync`. `PutObjectRequest` is the AWS SDK class that defines
      the bucket, key, and content to upload, allowing you to write the file directly
      to S3 without a local copy. This approach keeps the data in memory and reduces
      I/O latency.
    question: How do I upload annotated PDFs back to Amazon S3?
  - answer: Use IAM roles attached to EC2/ECS instances or AWS Lambda execution roles.
      For local development, rely on the AWS CLI credential file or environment variables.
      Never embed keys in source code.
    question: What's the best way to handle AWS credentials in production applications?
  - answer: Yes. GroupDocs.Annotation supports over **50** formats—including DOCX,
      XLSX, PPTX, and common image types. The S3 download code stays identical; only
      the file extension changes.
    question: Can I annotate other document formats besides PDF using this same approach?
  - answer: Implement optimistic locking with S3 version IDs or use a separate S3
      key per user session. Merge annotations server‑side before persisting the final
      file. This prevents lost updates and ensures each user sees a consistent view
      of the document.
    question: How do I handle concurrent annotations from multiple users on the same
      document?
  - answer: Wrap the download in a retry policy (e.g., Polly) with exponential back‑off.
      `Polly` is a .NET resilience library that simplifies retries, circuit‑breaker,
      and timeout handling. Log the exception and surface a clear error to the caller
      so the client can react appropriately.
    question: What happens if the S3 download fails or times out?
  type: FAQPage
tags:
- download pdf
- GroupDocs.Annotation
- .NET PDF processing
- AWS S3
- cloud document annotation
title: Cách download PDF từ S3 và annotate với GroupDocs .NET
type: docs
url: /vi/net/document-loading/download-annotate-pdfs-s3-groupdocs-dotnet/
weight: 1
---

# Cách tải PDF từ S3 và chú thích bằng GroupDocs .NET

Trong các ứng dụng cloud‑native hiện đại, bạn thường cần **download pdf from s3**, áp dụng các chú thích và lưu kết quả trở lại mà không cần chạm tới hệ thống tệp cục bộ. Hướng dẫn này chỉ cho bạn cách truyền luồng PDF trực tiếp từ Amazon S3, sử dụng GroupDocs.Annotation cho .NET để thêm các vùng đánh dấu, bình luận hoặc dấu, và sau đó lưu tệp đã chú thích một cách hiệu quả. Khi hoàn thành, bạn sẽ có một mẫu sẵn sàng cho sản xuất, có khả năng mở rộng và bảo mật dữ liệu.

## Câu trả lời nhanh
- **Bước đầu tiên là gì?** Tạo một `AmazonS3Client` với thông tin xác thực AWS của bạn và yêu cầu đối tượng dưới dạng luồng.  
- **Làm thế nào để thêm một chú thích?** Khởi tạo `Annotator` với luồng PDF và gọi phương thức `Add...` phù hợp.  
- **Có cần tệp tạm thời không?** Không – toàn bộ quy trình hoạt động chỉ với các luồng trong bộ nhớ.  
- **Có thể xử lý các PDF lớn không?** Có, sử dụng truyền luồng và giải phóng đối tượng kịp thời; GroupDocs.Annotation hỗ trợ các tệp > 200 MB.  
- **Cần giấy phép không?** Giấy phép sản xuất là bắt buộc; bản dùng thử miễn phí hoạt động cho phát triển và kiểm thử.

## download pdf from s3 là gì?
`download pdf from s3` đề cập đến việc lấy một đối tượng PDF lưu trong bucket Amazon S3 và đọc các byte của nó vào một luồng .NET mà không lưu tệp cục bộ. Cách tiếp cận này giảm tải I/O và cải thiện bảo mật cho các ứng dụng cloud‑first. Bằng cách giữ tệp trong bộ nhớ, bạn cũng tránh độ trễ đĩa không cần thiết và đơn giản hoá việc dọn dẹp.

## Tại sao nên sử dụng GroupDocs.Annotation với S3?
GroupDocs.Annotation hỗ trợ **hơn 50 loại chú thích** và có thể xử lý **các PDF hàng trăm trang** trong khi giữ mức sử dụng bộ nhớ dưới 2 × kích thước tệp. So với các thư viện PDF thủ công, nó giảm thời gian phát triển tới **70 %** và đảm bảo độ chính xác khi hiển thị trên mọi trình duyệt và thiết bị. Thư viện cũng cung cấp hỗ trợ tích hợp cho tuân thủ PDF/A và chữ ký số, điều này rất quan trọng cho các ngành công nghiệp chịu quy định.

## Các điều kiện tiên quyết cho việc tích hợp chú thích PDF trên AWS S3
Trước khi bắt đầu viết mã, hãy xác nhận rằng các mục sau đã sẵn sàng:

- **AWS SDK for .NET** – bộ công cụ chính thức cho các thao tác S3.  
- **GroupDocs.Annotation for .NET** – phiên bản 25.4.0 (hoặc mới hơn).  
- **Development IDE** – Visual Studio 2022 hoặc VS Code với phần mở rộng C#.  
- **AWS credentials** có quyền `s3:GetObject` và `s3:PutObject` trên bucket mục tiêu.  
- **.NET 6.0** hoặc runtime mới hơn.

### Thư viện và phiên bản yêu cầu
- AWS SDK for .NET (gói NuGet mới nhất).  
- GroupDocs.Annotation for .NET 25.4.0 (bản phát hành ổn định mới nhất).

### Kiến thức tiên quyết
- Quen thuộc với async/await và câu lệnh `using` trong C#.  
- Hiểu biết cơ bản về các khái niệm S3 như bucket, key và chính sách IAM.  
- Kinh nghiệm xử lý `MemoryStream`.

## Cài đặt GroupDocs.Annotation cho tích hợp đám mây .NET

### Các bước cài đặt gói
Cài đặt gói GroupDocs.Annotation bằng phương pháp bạn ưa thích:

**Console quản lý gói NuGet:**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**.NET CLI:**  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Cách lấy giấy phép cho môi trường sản xuất
1. **Free trial** – đánh giá tất cả tính năng mà không cần khóa giấy phép.  
2. **Temporary license** – yêu cầu khóa ngắn hạn từ trang web GroupDocs.  
3. **Commercial license** – mua để xử lý sản xuất không giới hạn.

### Khởi tạo và cấu hình cơ bản
Đoạn mã sau cho thấy cách tạo đối tượng `License` và cấu hình annotator để xử lý dựa trên luồng:

```csharp
using GroupDocs.Annotation;

// Initialize the annotator with a file stream from S3
Annotator annotator = new Annotator(s3DocumentStream);
```

> **Lưu ý:** Sự khác biệt chính khi làm việc với tài liệu S3 là bạn sẽ luôn xử lý các luồng thay vì đường dẫn tệp.

## Làm thế nào để tải PDF từ S3?
Tải PDF trực tiếp vào một `MemoryStream` bằng cách cấu hình `AmazonS3Client` và gửi `GetObjectRequest`. Điều này loại bỏ các tệp tạm thời và giữ thao tác trong bộ nhớ, nhanh hơn và an toàn hơn cho các tải công việc đám mây.

`AmazonS3Client` là lớp trong AWS SDK cung cấp các phương thức để tương tác với lưu trữ Amazon S3.  
`GetObjectRequest` đại diện cho một yêu cầu lấy một đối tượng (như PDF) từ một bucket và key cụ thể.

**Tải từng bước**

**Bước 1: cấu hình client**  
```csharp
using Amazon.S3;
using Amazon.S3.Model;

// Create a client instance (uses default credential chain)
AmazonS3Client client = new AmazonS3Client();
string bucketName = "my-bucket"; // Replace with your actual S3 bucket name
```

**Bước 2: tạo yêu cầu**  
```csharp
GetObjectRequest request = new GetObjectRequest
{
    Key = "your-file-key.pdf",
    BucketName = bucketName
};
```

**Bước 3: truyền luồng phản hồi**  
```csharp
using (GetObjectResponse response = client.GetObject(request))
{
    // Create a memory stream to store the PDF content
    MemoryStream stream = new MemoryStream();
    
    // Copy the S3 response directly to our memory stream
    response.ResponseStream.CopyTo(stream);
    
    // Reset position for annotation processing
    stream.Position = 0;
    
    // Return the stream for GroupDocs processing
    return stream;
}
```

## Làm thế nào để thêm chú thích vào luồng PDF?
Tạo một thể hiện `Annotator` từ `MemoryStream` của PDF, sau đó gọi các phương thức `Add...` phù hợp. Annotator hoạt động hoàn toàn trong bộ nhớ, vì vậy bạn có thể nối chuỗi nhiều loại chú thích trước khi lưu. Mẫu này đảm bảo không có tệp trung gian nào được ghi ra đĩa, cải thiện hiệu năng và bảo mật.

`Annotator` là lớp cốt lõi của GroupDocs.Annotation, tải luồng tài liệu và cung cấp các phương thức để tạo, chỉnh sửa và xuất chú thích.

**Bước 1: khởi tạo annotator**  
```csharp
// Initialize the annotator with the S3-downloaded document
using (Annotator annotator = new Annotator(downloadedStream))
{
    // All annotation operations happen here
}
```

**Bước 2: thêm chú thích highlight (area)**  
`AreaAnnotation` đại diện cho một vùng đánh dấu hình chữ nhật trên một trang PDF.  
```csharp
// Create an area annotation for highlighting
AreaAnnotation area = new AreaAnnotation()
{
    // Define the position and dimensions
    Box = new Rectangle(100, 100, 100, 100),
    
    // Set a yellow background color for visibility
    BackgroundColor = 65535,
};

// Add the annotation to the document
annotator.Add(area);
```

**Bước 3: lưu PDF đã chú thích trở lại luồng**  
```csharp
// Define output path for the processed document
string outputPath = Path.Combine("output-directory", "annotated-document.pdf");

// Save the document with all applied annotations
annotator.Save(outputPath);
```

## Triển khai hoàn chỉnh chú thích PDF trên AWS S3
Kết hợp các phần lại với nhau sẽ cho bạn một quy trình ngắn gọn, sẵn sàng cho sản xuất:

```csharp
using System;
using System.IO;
using Amazon.S3;
using Amazon.S3.Model;
using GroupDocs.Annotation;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

namespace GroupDocs.Annotation.Examples
{
    class DocumentAnnotationFromS3Example
    {
        public static void Run()
        {
            Console.WriteLine("Starting document annotation from S3...");
            
            // Define your output path
            string outputPath = Path.Combine("output-directory", "annotated-document.pdf");
            
            // Define the key of the file to download from S3
            string key = "sample.pdf";
            
            // Download and annotate the document
            using (Annotator annotator = new Annotator(DownloadFileFromS3(key)))
            {
                // Create an area annotation
                AreaAnnotation area = new AreaAnnotation()
                {
                    Box = new Rectangle(100, 100, 100, 100),
                    BackgroundColor = 65535, // Yellow color
                };
                
                // Add the annotation to the document
                annotator.Add(area);
                
                // Save the annotated document
                annotator.Save(outputPath);
            }
            
            Console.WriteLine($"Document successfully annotated and saved to: {outputPath}");
        }
        
        private static Stream DownloadFileFromS3(string key)
        {
            // Initialize S3 client (assumes AWS credentials are configured)
            AmazonS3Client client = new AmazonS3Client();
            string bucketName = "my-bucket"; // Replace with your actual bucket name
            
            // Create request to get object from S3
            GetObjectRequest request = new GetObjectRequest
            {
                Key = key,
                BucketName = bucketName
            };
            
            // Download the file from S3
            using (GetObjectResponse response = client.GetObject(request))
            {
                MemoryStream stream = new MemoryStream();
                response.ResponseStream.CopyTo(stream);
                stream.Position = 0;
                return stream;
            }
        }
    }
}
```

## Ứng dụng thực tế cho chú thích PDF trên S3
- **Cloud‑native review portals** – cho phép người dùng chú thích các hợp đồng lưu trong S3 mà không cần tải xuống cục bộ.  
- **Automated processing pipelines** – kích hoạt các hàm Lambda để thêm watermark hoặc dấu phê duyệt ngay khi PDF được đưa vào bucket.  
- **Multi‑tenant SaaS platforms** – cô lập tệp của mỗi tenant trong các prefix S3 riêng biệt trong khi tái sử dụng một dịch vụ chú thích duy nhất.  
- **Compliance audit trails** – tự động nhúng dấu thời gian và ID người xem xét dưới dạng chú thích cho hồ sơ tuân thủ.  
- **Collaborative editing suites** – cho phép chú thích đồng thời từ nhiều người dùng, lưu thay đổi trở lại S3 trong thời gian thực.

## Tối ưu hoá hiệu năng cho xử lý PDF trên đám mây
Khi mở rộng tới hàng chục hoặc hàng trăm PDF mỗi phút, các biện pháp này giữ độ trễ thấp và việc sử dụng tài nguyên dự đoán được.

### Tối ưu hoá mẫu truy cập S3
**Use regional endpoints** – cấu hình client tới cùng vùng AWS với tài nguyên tính toán của bạn để tránh độ trễ xuyên vùng.

```csharp
// Configure client for specific region
AmazonS3Client client = new AmazonS3Client(Amazon.RegionEndpoint.USEast1);
```

**Intelligent caching** – lưu các PDF thường truy cập trong Redis hoặc bộ nhớ cache trong tối đa 5 phút.  
**Transfer acceleration** – bật tính năng này cho các ứng dụng toàn cầu cần thời gian tải xuống dưới một giây.

### Các thực hành tốt về quản lý bộ nhớ
**Stream processing** – luôn làm việc với `MemoryStream` thay vì tải toàn bộ tệp vào mảng byte.

```csharp
// Good: Direct stream processing
using (var s3Stream = DownloadFileFromS3(key))
using (var annotator = new Annotator(s3Stream))
{
    // Process annotations
}
```

**Dispose resources** – bọc các phản hồi S3 và thể hiện annotator trong khối `using` để đảm bảo dọn dẹp.  
**Monitor memory** – thiết lập cảnh báo Application Insights cho mức sử dụng bộ nhớ > 80 %.

### Chiến lược xử lý đồng thời
**Parallel S3 downloads** – khi xử lý một lô, khởi chạy nhiều lời gọi `GetObjectAsync` bị giới hạn bởi semaphore.

```csharp
var downloadTasks = pdfKeys.Select(key => 
    Task.Run(() => DownloadAndAnnotateFromS3(key))
).ToArray();

await Task.WhenAll(downloadTasks);
```

**Batch annotation** – nhóm các hành động chú thích liên quan và gọi `Save` một lần cho mỗi tài liệu để giảm I/O.

## Các vấn đề thường gặp và khắc phục
| Vấn đề | Nguyên nhân thường gặp | Cách khắc phục |
|-------|------------------------|----------------|
| Lỗi xác thực AWS | Thiếu hoặc thông tin xác thực không đúng | Xác minh biến môi trường, tệp thông tin xác thực chia sẻ, hoặc cấu hình IAM role. |
| Lỗi vị trí luồng | Luồng không được đặt lại trước khi tái sử dụng | Gọi `stream.Seek(0, SeekOrigin.Begin)` sau mỗi lần sao chép. |
| Thiếu bộ nhớ khi xử lý PDF lớn | Tải toàn bộ tệp vào bộ nhớ | Chuyển sang chế độ truyền luồng và xử lý các trang theo từng phần. |
| Lỗi truy cập bị từ chối S3 | Chính sách IAM không đủ | Thêm `s3:GetObject` và `s3:PutObject` vào role. |
| Thiếu chú thích sau khi lưu | Sử dụng `SaveOptions` sai | Đảm bảo `SaveOptions.PreserveAnnotations = true`. |

### Các ví dụ chi tiết về khắc phục sự cố
**Vấn đề xác thực AWS**  
```csharp
// For explicit credential configuration
var awsOptions = new AWSOptions
{
    Credentials = new BasicAWSCredentials("access-key", "secret-key"),
    Region = RegionEndpoint.USEast1
};
```

**Vấn đề vị trí luồng**  
```csharp
stream.Position = 0; // Always reset before passing to GroupDocs
```

**Xử lý tệp lớn**  
```csharp
// Use buffered streams for large files
using (var bufferedStream = new BufferedStream(s3ResponseStream))
{
    // Process in manageable chunks
}
```

**Lỗi quyền S3**  
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": ["s3:GetObject"],
            "Resource": "arn:aws:s3:::your-bucket/*"
        }
    ]
}
```

**Vấn đề hiển thị chú thích**  
```csharp
// Save with explicit options
annotator.Save(outputPath, new SaveOptions 
{ 
    AnnotationTypes = AnnotationType.All 
});
```

## Các tùy chọn cấu hình nâng cao

### Cấu hình S3 tùy chỉnh
Trong môi trường sản xuất, bạn có thể muốn điều chỉnh thời gian chờ, chính sách thử lại và cài đặt proxy HTTP:

```csharp
var config = new AmazonS3Config
{
    RegionEndpoint = Amazon.RegionEndpoint.USWest2,
    Timeout = TimeSpan.FromMinutes(5),
    UseAccelerateEndpoint = true, // For global applications
    ForcePathStyle = false
};

using var client = new AmazonS3Client(config);
```

### Cài đặt GroupDocs Annotation
Tinh chỉnh việc sử dụng bộ nhớ và chất lượng hiển thị chú thích:

```csharp
// Initialize with specific load options
var loadOptions = new LoadOptions
{
    Password = documentPassword, // If PDF is password-protected
};

using var annotator = new Annotator(stream, loadOptions);
```

## Câu hỏi thường gặp

**Q: Làm thế nào để tải lên các PDF đã chú thích trở lại Amazon S3?**  
A: Lưu tài liệu đã chú thích vào một `MemoryStream`, sau đó tạo một `PutObjectRequest` và gọi `PutObjectAsync`. `PutObjectRequest` là lớp trong AWS SDK định nghĩa bucket, key và nội dung để tải lên, cho phép bạn ghi tệp trực tiếp vào S3 mà không cần bản sao cục bộ. Cách tiếp cận này giữ dữ liệu trong bộ nhớ và giảm độ trễ I/O.

```csharp
using var outputStream = new MemoryStream();
annotator.Save(outputStream);
outputStream.Position = 0;

var putRequest = new PutObjectRequest
{
    BucketName = bucketName,
    Key = "annotated-" + originalKey,
    InputStream = outputStream,
    ContentType = "application/pdf"
};

await client.PutObjectAsync(putRequest);
```

**Q: Cách tốt nhất để xử lý thông tin xác thực AWS trong các ứng dụng sản xuất là gì?**  
A: Sử dụng IAM role gắn vào các instance EC2/ECS hoặc role thực thi AWS Lambda. Đối với phát triển cục bộ, dựa vào tệp thông tin xác thực AWS CLI hoặc biến môi trường. Không bao giờ nhúng khóa vào mã nguồn.

```csharp
// Production: Uses IAM role automatically
var client = new AmazonS3Client();

// Development: Uses environment variables
Environment.SetEnvironmentVariable("AWS_ACCESS_KEY_ID", "your-key");
Environment.SetEnvironmentVariable("AWS_SECRET_ACCESS_KEY", "your-secret");
```

**Q: Tôi có thể chú thích các định dạng tài liệu khác ngoài PDF bằng cùng cách tiếp cận này không?**  
A: Có. GroupDocs.Annotation hỗ trợ hơn **50** định dạng — bao gồm DOCX, XLSX, PPTX và các loại ảnh phổ biến. Mã tải xuống S3 vẫn giống nhau; chỉ phần mở rộng tệp thay đổi.

```csharp
string userVersionKey = $"{originalKey}-user-{userId}-{timestamp}";
```

**Q: Làm thế nào để xử lý các chú thích đồng thời từ nhiều người dùng trên cùng một tài liệu?**  
A: Triển khai khóa lạc quan với ID phiên bản S3 hoặc sử dụng một key S3 riêng cho mỗi phiên người dùng. Gộp các chú thích phía máy chủ trước khi lưu tệp cuối cùng. Điều này ngăn ngừa mất cập nhật và đảm bảo mỗi người dùng nhìn thấy một view nhất quán của tài liệu.

```csharp
string userVersionKey = $"{originalKey}-user-{userId}-{timestamp}";
```

**Q: Điều gì sẽ xảy ra nếu việc tải xuống S3 thất bại hoặc hết thời gian?**  
A: Bao bọc việc tải xuống trong một chính sách thử lại (ví dụ, Polly) với back‑off tăng dần. `Polly` là thư viện .NET giúp tăng cường độ bền, đơn giản hoá việc thử lại, circuit‑breaker và xử lý timeout. Ghi lại ngoại lệ và trả về lỗi rõ ràng cho người gọi để client có thể phản hồi thích hợp.

```csharp
var retryPolicy = Policy
    .Handle<AmazonS3Exception>()
    .WaitAndRetryAsync(3, retryAttempt => 
        TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));

await retryPolicy.ExecuteAsync(async () =>
{
    return await DownloadFileFromS3(key);
});
```

**Q: Xử lý một PDF 150 MB thường cần bao nhiêu bộ nhớ?**  
A: GroupDocs.Annotation sử dụng khoảng 2–3 × kích thước tệp nguồn trong quá trình xử lý, vì vậy hãy dự kiến ~350 MB RAM cho PDF 150 MB. Đối với tệp lớn hơn, cân nhắc xử lý theo phần hoặc tăng bộ nhớ của instance.

## Tài nguyên bổ sung
- [Trang web GroupDocs](https://purchase.groupdocs.com/temporary-license/)
- [Tài liệu GroupDocs.Annotation](https://docs.groupdocs.com/annotation/net/)
- [Tham chiếu API](https://reference.groupdocs.com/annotation/net/)
- [Tải GroupDocs.Annotation cho .NET](https://releases.groupdocs.com/annotation/net/)
- [Mua giấy phép](https://purchase.groupdocs.com/buy)
- [Dùng thử miễn phí](https://releases.groupdocs.com/annotation/net/)
- [Giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/)
- [Diễn đàn hỗ trợ GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation)

---

**Cập nhật lần cuối:** 2026-08-19  
**Đã kiểm tra với:** GroupDocs.Annotation 25.4.0 cho .NET  
**Tác giả:** GroupDocs

## Các hướng dẫn liên quan

- [GroupDocs.Annotation .NET Tải tài liệu](/annotation/net/document-loading-essentials/)
- [Cài đặt giấy phép GroupDocs Annotation .NET - Hướng dẫn triển khai đầy đủ](/annotation/net/applying-licenses/set-license-from-file/)
- [Hướng dẫn chú thích PDF .NET - Hướng dẫn đầy đủ của GroupDocs](/annotation/net/annotation-management/annotate-pdf-groupdocs-annotation-net/)