---
categories:
- Document Processing
date: '2026-05-21'
description: Tìm hiểu cách chú thích các tệp PDF bằng GroupDocs Annotation .NET trong
  C#. Hướng dẫn từng bước này bao gồm cài đặt, thêm, cập nhật và quản lý chú thích
  PDF cho các trường hợp sử dụng trong lĩnh vực pháp lý, giáo dục và doanh nghiệp.
keywords:
- how to annotate pdf
- legal document annotation
- collaborative pdf markup
- create document review system
lastmod: '2026-05-21'
linktitle: Hướng dẫn GroupDocs Annotation .NET
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to annotate PDF files with GroupDocs Annotation .NET in C#.
    This step‑by‑step guide covers setup, adding, updating, and managing PDF annotations
    for legal, education, and enterprise use cases.
  headline: How to Annotate PDF using GroupDocs Annotation .NET (C#) Guide
  type: TechArticle
- questions:
  - answer: Yes, the free trial provides full functionality for 30 days but adds evaluation
      watermarks to every output file. For any production deployment you must apply
      a temporary or full license to remove those watermarks.
    question: Can I use GroupDocs.Annotation .NET without a license?
  - answer: The library works with .NET Framework 4.6.1+, .NET Core 2.0+, .NET 5,
      .NET 6, and .NET 7, making it suitable for both legacy Windows services and
      modern cross‑platform containers.
    question: Which .NET versions are supported by GroupDocs.Annotation?
  - answer: Pricing starts around $1,999 for a developer license and scales with the
      number of deployed applications. Check the [GroupDocs pricing page](https://purchase.groupdocs.com/buy)
      for the latest rates and volume discounts.
    question: How much does GroupDocs.Annotation .NET cost?
  - answer: Over **50 formats** are supported, including PDF, DOC/DOCX, PPT/PPTX,
      XLS/XLSX, JPEG, PNG, TIFF, and many more. PDF receives the most comprehensive
      feature set, including vector‑based shapes and OCR‑ready redaction.
    question: What document formats can I annotate with GroupDocs.Annotation?
  - answer: 'Yes. Provide the password when constructing the `Annotator`:'
    question: Can I annotate password‑protected PDFs?
  type: FAQPage
tags:
- GroupDocs
- Annotation
- C#
- PDF
- Document Management
title: Cách chú thích PDF bằng GroupDocs Annotation .NET (C#) Hướng dẫn
type: docs
url: /vi/net/annotation-management/annotate-documents-groupdocs-dotnet/
weight: 1
---

# Cách Ghi chú PDF với GroupDocs Annotation .NET (C#)

Bạn đã bao giờ cần **cách annotate pdf** một cách lập trình và tự hỏi thư viện nào cung cấp cả sức mạnh và sự đơn giản? Dù bạn đang xây dựng nền tảng xem xét pháp lý, hệ thống e‑learning, hay quy trình làm việc tài liệu hợp tác, GroupDocs.Annotation .NET cung cấp API sẵn sàng cho sản xuất cho phép bạn thêm, chỉnh sửa và xóa các ghi chú PDF trực tiếp từ mã C#. Trong hướng dẫn này, bạn sẽ học mọi thứ cần thiết để triển khai một engine ghi chú đầy đủ tính năng, từ cài đặt ban đầu đến tối ưu hiệu năng cho thư viện tài liệu quy mô lớn.

## Câu trả lời nhanh
- **Cách nhanh nhất để thêm ghi chú văn bản vào PDF là gì?** Tải tài liệu bằng `Annotator`, tạo một `TextAnnotation`, đặt `Box` và `Message`, sau đó gọi `Add()` – tất cả trong vòng chưa đầy một giây cho các trang thông thường.  
- **Các phiên bản .NET nào được hỗ trợ?** .NET Framework 4.6.1+, .NET Core 2.0+, .NET 5, .NET 6 và .NET 7.  
- **Tôi có cần giấy phép cho môi trường sản xuất không?** Có – giấy phép đầy đủ hoặc tạm thời sẽ loại bỏ watermark và mở khóa tất cả các tính năng.  
- **Tôi có thể xử lý PDF 200 trang trên máy chủ 4 GB không?** Có, bằng cách sử dụng xử lý batch và các mẫu giải phóng tài nguyên đúng cách được trình bày sau.  
- **GroupDocs.Annotation có phù hợp cho việc ghi chú tài liệu pháp lý không?** Hoàn toàn – nó hỗ trợ hơn 50 định dạng, kiểm soát quyền chi tiết và siêu dữ liệu sẵn sàng cho kiểm toán.

## “how to annotate pdf” là gì?
**“How to annotate pdf”** đề cập đến quá trình thêm đánh dấu một cách lập trình—như bình luận, tô sáng, hình dạng hoặc che dấu—vào các tệp PDF. Sử dụng GroupDocs.Annotation .NET, bạn có thể tự động hoá quy trình này, lưu trữ dữ liệu ghi chú trong cơ sở dữ liệu và hiển thị kết quả ngay lập tức trong trình xem web hoặc desktop.

## Tại sao nên sử dụng GroupDocs.Annotation cho việc đánh dấu PDF?
GroupDocs.Annotation hỗ trợ **hơn 50 định dạng đầu vào và đầu ra**, có thể xử lý các PDF lên tới **500 MB** mà không cần tải toàn bộ tệp vào bộ nhớ, và cung cấp các thao tác **thread‑safe** khi mỗi yêu cầu tạo một thể hiện `Annotator` riêng. So với các thư viện nhẹ chỉ hỗ trợ PDF, nó còn cho phép bạn ghi chú các tệp Word, PowerPoint và hình ảnh bằng cùng một API, giúp giảm đáng kể công sức phát triển cho các nền tảng đa định dạng.

## Ứng dụng thực tế: Nơi ghi chú tài liệu tỏa sáng

Hiểu bối cảnh kinh doanh giúp bạn chọn loại ghi chú phù hợp.

- **Đánh giá tài liệu pháp lý** – Luật sư thêm bình luận, tô sáng các điều khoản và đính kèm lịch sử sửa đổi. GroupDocs.Annotation theo dõi mỗi thay đổi với ID người dùng, dấu thời gian và chữ ký số tùy chọn để tuân thủ kiểm toán.  
- **Nền tảng giáo dục** – Giảng viên có thể chấm điểm bài tập bằng cách vẽ hình, thêm ghi chú dán, hoặc nhúng phản hồi âm thanh trực tiếp lên PDF của sinh viên.  
- **Tài liệu y tế** – Bác sĩ ghi chú báo cáo hình ảnh hoặc biểu đồ bệnh nhân trong khi bảo vệ siêu dữ liệu tuân thủ HIPAA.  
- **Tài liệu phần mềm** – Các nhà viết kỹ thuật hợp tác trên các spec API, chèn các hộp chú thích và ghi chú sửa đổi mà không rời khỏi PDF nguồn.  
- **Dịch vụ tài chính** – Nhân viên tuân thủ đánh dấu các hợp đồng vay, đánh giá rủi ro và chuỗi kiểm toán, sau đó xuất phiên bản đã ghi chú để lưu trữ.

## Yêu cầu và Cài đặt: Chuẩn bị môi trường của bạn

### Yêu cầu hệ thống

- **IDE**: Visual Studio 2019 hoặc mới hơn (bản Community hoạt động tốt).  
- **Runtime**: .NET Framework 4.6.1+ **hoặc** .NET Core 2.0+ (khuyến nghị 8 GB RAM cho các PDF lớn).  
- **Quyền**: Quyền ghi vào thư mục nơi các PDF đã ghi chú sẽ được lưu.

### Kiến thức tiên quyết

- Cú pháp C# cơ bản và các khái niệm hướng đối tượng.  
- Quen thuộc với quản lý gói NuGet.  
- Hiểu về I/O tệp (đọc/ghi luồng).

### Cài đặt GroupDocs.Annotation .NET

Bạn có thể thêm thư viện qua NuGet. Chọn phương pháp phù hợp với quy trình làm việc của bạn.

**Sử dụng NuGet Package Manager Console**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**Sử dụng .NET CLI** (được ưu tiên cho các pipeline CI/CD)  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

> **Mẹo chuyên nghiệp:** Luôn cố định phiên bản (ví dụ, `Install-Package GroupDocs.Annotation -Version 23.12`). Điều này ngăn ngừa các thay đổi gây lỗi không mong muốn khi gói tự động cập nhật. Xem các bản phát hành mới nhất trên [trang phát hành GroupDocs](https://releases.groupdocs.com/annotation/net/).

### Các tùy chọn giấy phép: Chọn giải pháp phù hợp cho dự án của bạn

- **Dùng thử miễn phí** – Tính năng đầy đủ với watermark đánh giá trong 30 ngày.  
- **Giấy phép tạm thời** – Loại bỏ watermark trong 30 ngày, lý tưởng cho proof‑of‑concept. Xem [trang giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/).  
- **Giấy phép đầy đủ** – Sử dụng không giới hạn trong sản xuất, hỗ trợ ưu tiên và không có watermark. Mua qua [cửa hàng GroupDocs](https://purchase.groupdocs.com/buy).

### Cài đặt dự án cơ bản

Tạo một dự án console C# mới hoặc dự án ASP.NET và thêm các câu lệnh using sau khi đã cài đặt gói:  
```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System.IO;
using System.Collections.Generic;

// Initialize Annotator with an input document path
string inputPath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pdf");
```

> **Quan trọng:** Thay thế `YOUR_DOCUMENT_DIRECTORY` bằng đường dẫn tuyệt đối tới các PDF của bạn. Sử dụng `Path.Combine` đảm bảo dấu phân cách đường dẫn đúng trên Windows và Linux.

## Hướng dẫn từng bước: Thêm ghi chú đầu tiên của bạn

### Làm thế nào để tải tài liệu PDF để ghi chú?

Lớp `Annotator` là thành phần cốt lõi tải tài liệu và quản lý tất cả các thao tác ghi chú. Việc tải PDF đúng cách đảm bảo thư viện có thể đọc kích thước trang, siêu dữ liệu và các ghi chú hiện có trước khi áp dụng bất kỳ thay đổi nào. Tải PDF bằng constructor `Annotator`, truyền đường dẫn tệp và tùy chọn tải tùy chọn. Bước này xác thực tệp và chuẩn bị một biểu diễn trong bộ nhớ mà bạn có thể sửa đổi an toàn, đồng thời cũng xử lý các tệp được mã hóa nếu cung cấp mật khẩu.  
```csharp
try 
{
    using (Annotator annotator = new Annotator(inputPath))
    {
        // Your annotation code goes here
        Console.WriteLine("Document loaded successfully!");
    }
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

Khối `try‑catch` bảo vệ khỏi các tệp bị thiếu, PDF hỏng hoặc định dạng không hỗ trợ, đảm bảo ứng dụng của bạn thất bại một cách nhẹ nhàng thay vì bị sập.

### Làm thế nào để thêm ghi chú văn bản vào PDF?

`TextAnnotation` đại diện cho bình luận kiểu ghi chú dán có thể đặt trên một trang PDF. Thêm một ghi chú bao gồm tạo đối tượng, xác định vị trí, đặt thông điệp hiển thị, và cuối cùng chèn vào tài liệu qua `Annotator`. Tạo một đối tượng `TextAnnotation`, định nghĩa hình chữ nhật bao quanh bằng thuộc tính `Box`, đặt `Message` hiển thị, sau đó gọi `Add()` trên `Annotator`. Ghi chú sẽ xuất hiện ngay lập tức trên trang đã chỉ định, và bạn có thể tùy chỉnh giao diện bằng màu và độ trong suốt nếu cần.  
```csharp
// Create a highlight annotation
HighlightAnnotation highlight = new HighlightAnnotation
{
    Box = new Rectangle(100, 100, 200, 20), // x, y, width, height
    CreatedOn = DateTime.Now,
    Message = "This section needs review",
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "Please verify these numbers",
            RepliedOn = DateTime.Now
        }
    }
};

// Add the annotation to the document
annotator.Add(highlight);
```

> **Tại sao thuộc tính `Box` quan trọng:** Hình chữ nhật sử dụng đơn vị point (1 point = 1/72 inch) đo từ góc dưới‑trái của trang. Tọa độ chính xác cho phép bạn đặt ghi chú đúng nơi người xem mong đợi.

### Làm thế nào để lưu PDF đã ghi chú mà không ghi đè lên nguồn?

Lưu vào tệp mới bảo tồn tài liệu gốc cho các chuỗi kiểm toán và kịch bản khôi phục. Phương thức `Save` ghi tất cả các thay đổi, bao gồm các ghi chú mới và siêu dữ liệu, vào đường dẫn đã chỉ định trong khi giữ nguyên nguồn.  
```csharp
string outputPath = Path.Combine("YOUR_OUTPUT_DIRECTORY", "annotated_document.pdf");
annotator.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

> **Thực hành tốt:** Lưu trữ các phiên bản gốc và đã ghi chú trong các thư mục được kiểm soát phiên bản riêng biệt. Chiến lược này đơn giản hoá việc tuân thủ quy định và theo dõi thay đổi.

## Kỹ thuật ghi chú nâng cao

### Làm thế nào để thêm nhiều loại ghi chú trong một thao tác?

GroupDocs.Annotation cung cấp một tập hợp phong phú các lớp ghi chú—`HighlightAnnotation`, `StrikeoutAnnotation`, `PolylineAnnotation`, `RedactionAnnotation`, và nhiều hơn nữa. Bằng cách tạo mỗi thể hiện, cấu hình các thuộc tính và thêm chúng vào cùng một `Annotator` trước khi lưu, bạn giảm thiểu I/O và giữ trạng thái tài liệu nhất quán.  
```csharp
// Text annotation for comments
TextAnnotation textNote = new TextAnnotation
{
    Box = new Rectangle(300, 200, 100, 30),
    Message = "Review required",
    CreatedOn = DateTime.Now,
    FontColor = 16711680, // Red color in RGB
    BackgroundColor = 16777215 // White background
};

// Arrow annotation to point out specific elements
ArrowAnnotation pointer = new ArrowAnnotation
{
    Box = new Rectangle(150, 150, 50, 50),
    Message = "Important calculation here",
    CreatedOn = DateTime.Now
};

// Add all annotations at once
annotator.Add(textNote);
annotator.Add(pointer);
```

### Làm thế nào để cập nhật màu hoặc bình luận của một ghi chú hiện có?

Phương thức `GetById` lấy một ghi chú cụ thể bằng định danh duy nhất của nó, cho phép bạn chỉ sửa đổi các trường cần thiết. Sau khi lấy đối tượng, bạn có thể thay đổi các thuộc tính như `Color` hoặc `Message` và sau đó lưu các thay đổi bằng `Update`.  
```csharp
// Get all annotations from the document
List<AnnotationBase> annotations = annotator.Get();

// Find and update a specific annotation
foreach (var annotation in annotations)
{
    if (annotation.Message.Contains("Review required"))
    {
        annotation.Message = "Review completed ✓";
        annotator.Update(annotation);
        break;
    }
}
```

> **Lưu ý về hiệu năng:** Đối với tài liệu có hàng nghìn ghi chú, hãy lưu trữ ID ghi chú trong một dictionary để tránh tìm kiếm tuyến tính.

## Các vấn đề thường gặp và khắc phục

### Vấn đề 1 – “Định dạng tài liệu không được hỗ trợ”

**Câu trả lời trực tiếp:** Kiểm tra xem phần mở rộng của tệp có nằm trong danh sách định dạng được hỗ trợ của GroupDocs.Annotation không; nếu không, chuyển tệp sang PDF trước hoặc sử dụng sản phẩm GroupDocs khác hỗ trợ định dạng đó.  
**Giải pháp:**  
- Kiểm tra [danh sách định dạng được hỗ trợ](https://docs.groupdocs.com/annotation/net/supported-document-formats/)  
- Sử dụng GroupDocs.Conversion để chuyển các tệp không được hỗ trợ sang PDF trước khi ghi chú.  
```csharp
// Check if format is supported before processing
string extension = Path.GetExtension(inputPath).ToLower();
if (extension != ".pdf" && extension != ".docx" && extension != ".pptx")
{
    throw new NotSupportedException($"File format {extension} is not supported");
}
```

### Vấn đề 2 – Ghi chú xuất hiện ở vị trí sai

**Câu trả lời trực tiếp:** Đảm bảo bạn đang sử dụng hệ tọa độ đúng (gốc ở góc dưới‑trái) và metadata xoay trang được tôn trọng. Điều chỉnh giá trị `Box` cho phù hợp.  
**Giải pháp:**  
```csharp
// Always validate coordinates before adding annotations
private bool IsValidCoordinate(Rectangle box, double pageWidth, double pageHeight)
{
    return box.X >= 0 && box.Y >= 0 && 
           (box.X + box.Width) <= pageWidth && 
           (box.Y + box.Height) <= pageHeight;
}
```

### Vấn đề 3 – Vấn đề bộ nhớ với tài liệu lớn

**Câu trả lời trực tiếp:** Xử lý các PDF lớn theo lô, giải phóng `Annotator` sau mỗi lô, và bật chế độ streaming để tránh tải toàn bộ tệp vào RAM.  
**Giải pháp:**  
```csharp
// Process large documents in chunks
using (Annotator annotator = new Annotator(inputPath))
{
    // Set memory-friendly options
    LoadOptions loadOptions = new LoadOptions
    {
        PreviewPageCount = 1 // Load pages on demand
    };
    
    // Process annotations in batches
    const int batchSize = 10;
    for (int i = 0; i < annotations.Count; i += batchSize)
    {
        var batch = annotations.Skip(i).Take(batchSize);
        foreach (var annotation in batch)
        {
            annotator.Add(annotation);
        }
        
        // Force garbage collection between batches for large documents
        if (i % 50 == 0)
        {
            GC.Collect();
            GC.WaitForPendingFinalizers();
        }
    }
}
```

## Mẹo tối ưu hiệu năng

### Làm thế nào để xử lý hàng ngàn PDF theo batch một cách hiệu quả?

Thu thập các yêu cầu ghi chú vào một danh sách, mở một `Annotator` duy nhất cho mỗi tài liệu, áp dụng tất cả các thay đổi, sau đó gọi `Save()` một lần. Điều này giảm tải I/O, tận dụng bộ đệm nội bộ, và giữ mức sử dụng bộ nhớ dự đoán được trong các khối lượng công việc lớn.  
Thu thập các yêu cầu ghi chú vào một danh sách, mở một `Annotator` duy nhất cho mỗi tài liệu, áp dụng tất cả các thay đổi, sau đó gọi `Save()` một lần. Điều này giảm tải I/O và tận dụng bộ đệm nội bộ.  
```csharp
// Inefficient approach (don't do this)
foreach (var annotation in annotations)
{
    annotator.Add(annotation);
    annotator.Save(outputPath); // Saving after each annotation is expensive
}

// Efficient approach
foreach (var annotation in annotations)
{
    annotator.Add(annotation);
}
annotator.Save(outputPath); // Save once at the end
```

### Làm thế nào để quản lý bộ nhớ khi làm việc với PDF có hàng trăm trang?

Bật cờ `LoadOptions` `MemoryOptimization = true` và xử lý các trang một cách tuần tự. Điều này yêu cầu thư viện chỉ giữ trang đang hoạt động trong bộ nhớ, giảm đáng kể dung lượng RAM cho các tệp rất lớn.  
```csharp
// Use using statements to ensure proper disposal
using (var annotator = new Annotator(inputPath))
{
    // Your annotation code here
} // Annotator is automatically disposed, freeing memory
```

### Làm thế nào để cache các tài liệu được truy cập thường xuyên?

Lưu trữ JSON ghi chú đã được tuần tự hoá trong cache phân tán (ví dụ, Redis) với khóa là ID tài liệu. Khi người dùng yêu cầu cùng một PDF, lấy bộ ghi chú đã cache thay vì đọc lại tệp từ đĩa, giảm độ trễ và tải I/O.  
```csharp
// Cache document metadata to avoid reloading
private static readonly Dictionary<string, DocumentInfo> _documentCache = 
    new Dictionary<string, DocumentInfo>();

private DocumentInfo GetDocumentInfo(string path)
{
    if (!_documentCache.ContainsKey(path))
    {
        using (var annotator = new Annotator(path))
        {
            _documentCache[path] = annotator.GetDocumentInfo();
        }
    }
    return _documentCache[path];
}
```

## Thực hành tốt cho ứng dụng sản xuất

### Làm thế nào để triển khai xử lý lỗi và ghi log mạnh mẽ?

Bao bọc mọi thao tác `Annotator` trong khối `try‑catch`, ghi log ngoại lệ bằng logger có cấu trúc (Serilog, NLog), và bao gồm đường dẫn tài liệu, ID người dùng và stack trace. Điều này giúp việc khắc phục sự cố dễ dàng hơn trong môi trường sản xuất và hỗ trợ bạn đáp ứng yêu cầu kiểm toán tuân thủ.  
```csharp
public async Task<bool> AddAnnotationSafely(string documentPath, AnnotationBase annotation)
{
    try
    {
        using (var annotator = new Annotator(documentPath))
        {
            annotator.Add(annotation);
            annotator.Save(documentPath.Replace(".pdf", "_annotated.pdf"));
            return true;
        }
    }
    catch (Exception ex)
    {
        // Log the error (use your preferred logging framework)
        Console.WriteLine($"Annotation failed for {documentPath}: {ex.Message}");
        return false;
    }
}
```

### Làm thế nào để xác thực dữ liệu ghi chú do người dùng cung cấp?

Kiểm tra các trường JSON đầu vào (số trang, tọa độ hình chữ nhật, loại ghi chú) nằm trong phạm vi cho phép trước khi tạo các đối tượng ghi chú. Từ chối các tọa độ vượt giới hạn bằng phản hồi HTTP 400 rõ ràng và cung cấp thông báo lỗi hữu ích.  
```csharp
public bool ValidateAnnotationInput(AnnotationBase annotation)
{
    if (annotation == null)
        return false;
    
    if (string.IsNullOrWhiteSpace(annotation.Message))
        return false;
    
    if (annotation.Box.Width <= 0 || annotation.Box.Height <= 0)
        return false;
    
    return true;
}
```

### Làm thế nào để đảm bảo an toàn luồng trong dịch vụ web đa người dùng?

Tạo một `Annotator` mới cho mỗi yêu cầu; không bao giờ chia sẻ một thể hiện duy nhất giữa các luồng. Nếu cần phối hợp truy cập vào tệp chung, sử dụng `SemaphoreSlim` hoặc khóa cấp tệp để ngăn ghi đồng thời.  
```csharp
private readonly object _annotationLock = new object();

public void AddAnnotationThreadSafe(string documentPath, AnnotationBase annotation)
{
    lock (_annotationLock)
    {
        using (var annotator = new Annotator(documentPath))
        {
            annotator.Add(annotation);
            annotator.Save(documentPath);
        }
    }
}
```

## Khi nào nên sử dụng GroupDocs.Annotation so với các giải pháp thay thế

**Chọn GroupDocs.Annotation khi** bạn cần:
- Hỗ trợ đa định dạng (PDF, DOCX, PPTX, hình ảnh).  
- Các loại ghi chú nâng cao như che dấu, vẽ tự do và siêu dữ liệu tùy chỉnh.  
- Giấy phép cấp doanh nghiệp, hỗ trợ dựa trên SLA và cập nhật bảo mật thường xuyên.  

**Xem xét các giải pháp nhẹ hơn khi** bạn chỉ làm việc với PDF, có hạn chế ngân sách nghiêm ngặt, hoặc cần một stack mã nguồn mở.

## Câu hỏi thường gặp

**H: Tôi có thể sử dụng GroupDocs.Annotation .NET mà không có giấy phép không?**  
Đ: Có, bản dùng thử miễn phí cung cấp đầy đủ tính năng trong 30 ngày nhưng sẽ thêm watermark đánh giá vào mọi tệp đầu ra. Đối với bất kỳ triển khai sản xuất nào, bạn phải áp dụng giấy phép tạm thời hoặc đầy đủ để loại bỏ các watermark đó.

**H: Các phiên bản .NET nào được GroupDocs.Annotation hỗ trợ?**  
Đ: Thư viện hoạt động với .NET Framework 4.6.1+, .NET Core 2.0+, .NET 5, .NET 6 và .NET 7, phù hợp cho cả dịch vụ Windows legacy và các container đa nền tảng hiện đại.

**H: GroupDocs.Annotation .NET có giá bao nhiêu?**  
Đ: Giá bắt đầu khoảng $1,999 cho giấy phép nhà phát triển và tăng lên tùy theo số lượng ứng dụng triển khai. Kiểm tra [trang giá của GroupDocs](https://purchase.groupdocs.com/buy) để biết mức giá mới nhất và các ưu đãi theo khối lượng.

**H: Tôi có thể ghi chú những định dạng tài liệu nào với GroupDocs.Annotation?**  
Đ: Hơn **50 định dạng** được hỗ trợ, bao gồm PDF, DOC/DOCX, PPT/PPTX, XLS/XLSX, JPEG, PNG, TIFF và nhiều hơn nữa. PDF nhận được bộ tính năng toàn diện nhất, bao gồm các hình dạng dựa trên vector và khả năng che dấu sẵn sàng cho OCR.

**H: Tôi có thể ghi chú các PDF được bảo vệ bằng mật khẩu không?**  
Đ: Có. Cung cấp mật khẩu khi khởi tạo `Annotator`:  
```csharp
LoadOptions loadOptions = new LoadOptions { Password = "your_password" };
using (Annotator annotator = new Annotator(inputPath, loadOptions))
{
    // Your annotation code here
}
```

**H: Tại sao các ghi chú của tôi lại xuất hiện ở vị trí sai?**  
Đ: GroupDocs sử dụng hệ tọa độ Cartesian trong đó (0,0) là góc dưới‑trái và các đo lường bằng point. Vị trí sai thường xuất phát từ việc sử dụng giá trị dựa trên pixel hoặc bỏ qua thông tin xoay trang. Chuyển đổi giá trị pixel sang point (1 pixel ≈ 0.75 point ở 96 DPI) và điều chỉnh cho bất kỳ metadata xoay nào.  
```csharp
// Correct approach - validate coordinates
private bool ValidateCoordinates(Rectangle box, double pageWidth, double pageHeight)
{
    return box.X >= 0 && box.Y >= 0 && 
           (box.X + box.Width) <= pageWidth && 
           (box.Y + box.Height) <= pageHeight;
}
```

**H: Làm thế nào để lấy các ghi chú hiện có từ PDF?**  
Đ: Gọi phương thức `Get()` trên thể hiện `Annotator`; nó trả về một tập hợp các đối tượng ghi chú với ID, loại và siêu dữ liệu của chúng.  
```csharp
using (Annotator annotator = new Annotator(inputPath))
{
    List<AnnotationBase> annotations = annotator.Get();
    foreach (var annotation in annotations)
    {
        Console.WriteLine($"Annotation: {annotation.Message}");
    }
}
```

**H: Tôi có thể xóa các ghi chú cụ thể bằng lập trình không?**  
Đ: Có. Sử dụng `Delete(id)` để xóa một ghi chú duy nhất hoặc `DeleteAll()` để xóa toàn bộ tài liệu. Bạn cũng có thể lọc theo loại trước khi xóa.  
```csharp
List<AnnotationBase> annotationsToDelete = annotator.Get()
    .Where(a => a.Message.Contains("obsolete"))
    .ToList();

foreach (var annotation in annotationsToDelete)
{
    annotator.Remove(annotation);
}
```

**H: Làm thế nào để cập nhật các thuộc tính ghi chú như màu hoặc tin nhắn?**  
Đ: Lấy ghi chú, sửa đổi `Color` hoặc `Message`, sau đó gọi `Update()`. Thay đổi sẽ được lưu lại ở lần gọi `Save()` tiếp theo.  
```csharp
var annotations = annotator.Get();
var targetAnnotation = annotations.FirstOrDefault(a => a.Id == specificId);
if (targetAnnotation != null)
{
    targetAnnotation.Message = "Updated message";
    annotator.Update(targetAnnotation);
}
```

**H: Tôi có thể thêm siêu dữ liệu tùy chỉnh vào các ghi chú không?**  
Đ: Chắc chắn. Hầu hết các lớp ghi chú cung cấp một collection `Replies` nơi bạn có thể lưu các cặp khóa‑giá trị, cho phép đính kèm ID người đánh giá, dấu thời gian hoặc trạng thái quy trình.  
```csharp
var annotation = new HighlightAnnotation
{
    // ... other properties
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "Custom metadata: priority=high, category=legal",
            RepliedOn = DateTime.Now
        }
    }
};
```

**H: GroupDocs.Annotation có hỗ trợ chữ ký số trên PDF đã ghi chú không?**  
Đ: Mặc dù thư viện Annotation tập trung vào đánh dấu, bạn có thể kết hợp nó với GroupDocs.Signature .NET để áp dụng chữ ký mật mã sau khi đã thêm ghi chú, đảm bảo cả tính trực quan và tính pháp lý.

**H: Tôi có thể xuất các ghi chú ra JSON hoặc XML để xử lý bên ngoài không?**  
Đ: Thư viện không có trình xuất tích hợp, nhưng bạn có thể tự tuần tự hoá các đối tượng ghi chú bằng `System.Text.Json` hoặc `XmlSerializer`. Điều này giúp dễ dàng tích hợp với các hệ thống kiểm toán bên ngoài.  
```csharp
List<AnnotationBase> annotations = annotator.Get();
string jsonAnnotations = JsonConvert.SerializeObject(annotations, Formatting.Indented);
File.WriteAllText("annotations.json", jsonAnnotations);
```

---

**Cập nhật lần cuối:** 2026-05-21  
**Được kiểm tra với:** GroupDocs.Annotation 23.12 cho .NET  
**Tác giả:** GroupDocs  

## Hướng dẫn liên quan

- [Hướng dẫn GroupDocs Annotation .NET - Hướng dẫn đầy đủ cho Quản lý Tài liệu](/annotation/net/annotation-management/)
- [Lưu Ghi chú PDF .NET - Hướng dẫn lưu tài liệu đầy đủ](/annotation/net/document-saving/)
- [Tải PDF từ URL .NET - Hướng dẫn đầy đủ với GroupDocs.Annotation](/annotation/net/document-loading-essentials/load-document-from-url/)