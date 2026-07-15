---
categories:
- PDF Processing
date: '2026-05-21'
description: Tìm hiểu cách tạo chú thích PDF trong .NET bằng GroupDocs. Hướng dẫn
  từng bước với cài đặt, mã C#, các thực tiễn tốt nhất và khắc phục sự cố.
keywords:
- create pdf annotations .net
- groupdocs annotation c# tutorial
- add highlights to pdf c#
- pdf markup library .net
- annotate pdf programmatically
lastmod: '2026-05-21'
linktitle: Hướng dẫn .NET về chú thích PDF
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to create PDF annotations in .NET using GroupDocs. Step-by-step
    guide with setup, C# code, best practices, and troubleshooting.
  headline: Create PDF Annotations .NET Tutorial - Complete GroupDocs Guide
  type: TechArticle
- description: Learn how to create PDF annotations in .NET using GroupDocs. Step-by-step
    guide with setup, C# code, best practices, and troubleshooting.
  name: Create PDF Annotations .NET Tutorial - Complete GroupDocs Guide
  steps:
  - name: Loading Your PDF Document
    text: The `Annotator` class is the primary gateway to a PDF file. *The `Annotator`
      class represents a PDF document and provides methods to read, write, and manipulate
      its annotations.* *The `Annotator` class represents a single PDF in memory and
      exposes methods for reading, writing, and manipulating annot
  - name: Creating Your First Annotation
    text: 'A `HighlightAnnotation` marks text with a semi‑transparent color. *The
      `HighlightAnnotation` class defines a highlight region, its color, and the page
      on which it appears.* *`HighlightAnnotation` inherits from `AnnotationBase`
      and defines the visual appearance of a highlight region.* **Tip:** Start '
  - name: Adding the Annotation
    text: After constructing the annotation object, add it to the `Annotator` instance.
      *The `Add` method inserts the annotation into the current page’s annotation
      collection.* *The `Add` method inserts the annotation into the current page’s
      annotation collection.*
  - name: Saving Your Annotated Document
    text: Persist the changes by calling `Save` with a new file name. *The `Save`
      method writes the modified PDF to disk, optionally allowing you to specify a
      different output format.* *Saving to a different filename prevents accidental
      overwrites and lets you compare before/after versions.*
  type: HowTo
- questions:
  - answer: Yes. GroupDocs.Annotation supports **50+ formats**, including DOCX, XLSX,
      PPTX, and common image types, using the same API.
    question: Can I annotate file types other than PDF?
  - answer: 'Pass the password to the `Annotator` constructor:'
    question: How do I open a password‑protected PDF?
  - answer: No hard limit, but performance degrades after roughly **1,000 annotations**;
      consider splitting large files.
    question: Is there a limit to the number of annotations per document?
  - answer: 'Use the `Get` method to retrieve a collection of all annotations:'
    question: Can I extract existing annotations programmatically?
  - answer: 'Each annotation type exposes appearance properties; for example, set
      `BackgroundColor` and `Font` on a `TextAnnotation`:'
    question: How do I customize annotation colors and fonts?
  type: FAQPage
tags:
- groupdocs
- pdf-annotation
- dotnet-tutorial
- csharp-guide
title: Tạo chú thích PDF .NET - Hướng dẫn đầy đủ của GroupDocs
type: docs
url: /vi/net/annotation-management/annotate-pdf-groupdocs-annotation-net/
weight: 1
---

# Hướng dẫn tạo chú thích PDF .NET: Hướng dẫn đầy đủ GroupDocs

## Giới thiệu

Trong hướng dẫn này, bạn sẽ học cách **tạo chú thích PDF .NET** bằng thư viện GroupDocs.Annotation. Dù bạn đang xây dựng cổng thông tin xem xét hợp đồng, nền tảng e‑learning, hay một tiện ích desktop đơn giản, các bước dưới đây sẽ đưa bạn từ dự án trống tới một PDF đã được chú thích đầy đủ chỉ trong vài phút. Chúng tôi sẽ đề cập đến cài đặt, cấp phép, cách sử dụng API cốt lõi, các lỗi thường gặp, mẹo tối ưu hiệu năng, và các kịch bản thực tế để bạn có thể triển khai tính năng chú thích đáng tin cậy ngay hôm nay.

## Câu trả lời nhanh
- **Thư viện nào tôi có thể dùng?** GroupDocs.Annotation cho .NET là giải pháp được khuyến nghị, cấp doanh nghiệp.  
- **Cần bao nhiêu dòng mã để thêm một highlight?** Chỉ hai dòng: tạo một `HighlightAnnotation` và gọi `Add`.  
- **Có cần giấy phép trả phí không?** Bản dùng thử miễn phí đủ cho phát triển; giấy phép đầy đủ sẽ loại bỏ watermark cho môi trường production.  
- **Có thể chú thích các PDF lớn hơn 100 MB không?** Có – xử lý từng trang và sử dụng streaming để giảm bộ nhớ.  
- **Có hỗ trợ async không?** API có thể được bọc trong `Task.Run` hoặc sử dụng I/O async cho các ứng dụng web.

## create pdf annotations .net là gì?
`create pdf annotations .net` đề cập đến quá trình thêm các ghi chú trực quan—như highlight, comment, shape hoặc stamp—vào file PDF từ một ứng dụng .NET bằng SDK chuyên dụng. Điều này cho phép tự động hoá quy trình xem xét, chỉnh sửa cộng tác và đánh dấu tùy chỉnh mà không cần người dùng thao tác thủ công.

## Tại sao chọn GroupDocs cho chú thích PDF?

GroupDocs.Annotation cung cấp **hiệu năng cấp doanh nghiệp cho hơn 50 định dạng tài liệu** và xử lý các PDF hàng trăm trang mà không cần tải toàn bộ file vào bộ nhớ. Thư viện có API sạch, linh hoạt, giúp giảm thời gian phát triển tới 70 % so với các thư viện PDF cấp thấp. Thư viện đã được kiểm chứng trong hàng ngàn triển khai sản xuất trên toàn thế giới, đảm bảo độ ổn định và bảo mật.

## Yêu cầu trước và thiết lập môi trường

### Tôi cần gì trước khi bắt đầu?
- **IDE:** Visual Studio 2019+ (phiên bản Community cũng đủ)  
- **Framework mục tiêu:** .NET Framework 4.6.2+ **hoặc** .NET Core 2.0+  
- **GroupDocs.Annotation:** phiên bản 25.4.0 hoặc mới hơn (bản dùng thử hoặc có giấy phép)  
- **Kiến thức C# cơ bản:** khả năng tạo dự án console hoặc web

## Cài đặt GroupDocs.Annotation cho .NET

### Làm sao để cài gói NuGet?
Chạy lệnh sau trong Package Manager Console:

```shell
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Cài đặt qua giao diện UI?
1. Nhấp chuột phải vào dự án → **Manage NuGet Packages**  
2. Tìm **GroupDocs.Annotation**  
3. Nhấn **Install** (phiên bản ổn định mới nhất)

### Cài đặt bằng .NET CLI?
Thực thi lệnh này trong terminal:

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

**Khắc phục lỗi cài đặt:** Nếu gặp xung đột phụ thuộc, nâng cấp phiên bản .NET hoặc xóa cache NuGet bằng `dotnet nuget locals all --clear`.

## Cấu hình giấy phép (Đừng bỏ qua!)

### Làm sao để áp dụng file giấy phép?
Lớp `License` tải file XML giấy phép để mở khóa toàn bộ chức năng:

```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main()
    {
        // Initialize the annotator with your document path
        string inputFilePath = "YOUR_DOCUMENT_DIRECTORY\input.pdf";
        
        using (Annotator annotator = new Annotator(inputFilePath))
        {
            Console.WriteLine("GroupDocs.Annotation for .NET is ready to use.");
        }
    }
}
```

*Lớp `License` là điểm vào của GroupDocs.Annotation để đăng ký giấy phép dùng thử hoặc thương mại. Nó phải được gọi trước bất kỳ thao tác SDK nào khác.*

## Hướng dẫn triển khai từng bước

### Quy trình chú thích hoạt động như thế nào?
Quy trình chú thích gồm bốn bước rõ ràng: tải PDF, tạo đối tượng chú thích, thêm các đối tượng này vào tài liệu, và cuối cùng lưu file đã sửa. Quy trình tuyến tính này giống như vòng đời chỉnh sửa trong một trình soạn thảo văn bản, giúp code dễ đọc, dễ bảo trì và đảm bảo mỗi thao tác được thực hiện đúng thứ tự.

### Bước 1: Tải tài liệu PDF của bạn

Lớp `Annotator` là cổng chính tới file PDF.  
*Lớp `Annotator` đại diện cho một tài liệu PDF và cung cấp các phương thức để đọc, ghi và thao tác các chú thích.*

```csharp
using (Annotator annotator = new Annotator(inputFilePath))
{
    // Your annotation magic happens here
}
```

*Lớp `Annotator` đại diện cho một PDF duy nhất trong bộ nhớ và cung cấp các phương thức đọc, ghi và thao tác chú thích.*

**Tại sao cần kiểm tra đường dẫn trước?** Vì nếu file không tồn tại sẽ ném `FileNotFoundException`, làm dừng quy trình. Sử dụng đoạn guard sau:

```csharp
if (!File.Exists(inputFilePath))
{
    throw new FileNotFoundException($"PDF file not found: {inputFilePath}");
}
```

### Bước 2: Tạo chú thích đầu tiên

`HighlightAnnotation` đánh dấu văn bản bằng màu bán trong suốt.  
*Lớp `HighlightAnnotation` định nghĩa vùng highlight, màu sắc và trang hiển thị.*

```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // x, y coordinates and width & height
    BackgroundColor = 65535, // ARGB color format for transparency
};
```

*`HighlightAnnotation` kế thừa từ `AnnotationBase` và xác định giao diện hiển thị của vùng highlight.*

**Mẹo:** Bắt đầu với tọa độ lớn (ví dụ 200 × 200) để kiểm tra vị trí trước khi tinh chỉnh.

### Bước 3: Thêm chú thích

Sau khi khởi tạo đối tượng chú thích, thêm nó vào thể hiện `Annotator`.  
*Phương thức `Add` chèn chú thích vào bộ sưu tập chú thích của trang hiện tại.*

```csharp
annotator.Add(area);
```

*Phương thức `Add` chèn chú thích vào bộ sưu tập chú thích của trang hiện tại.*

### Bước 4: Lưu tài liệu đã chú thích

Ghi lại các thay đổi bằng cách gọi `Save` với tên file mới.  
*Phương thức `Save` ghi PDF đã sửa lên đĩa, tùy chọn cho phép chỉ định định dạng đầu ra khác.*

```csharp
string outputPath = "YOUR_OUTPUT_DIRECTORY\result.pdf";
annotator.Save(outputPath);
```

*Lưu với tên file khác giúp tránh ghi đè vô tình và cho phép so sánh phiên bản trước/sau.*

### Ví dụ hoàn chỉnh

Kết hợp tất cả các phần lại sẽ cho ra một ứng dụng console có thể chạy:

```csharp
using System;
using System.IO;
using GroupDocs.Annotation;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

class Program
{
    static void Main()
    {
        try
        {
            string inputFilePath = @"C:\Documents\input.pdf";
            string outputPath = @"C:\Documents\result.pdf";
            
            // Validate input file exists
            if (!File.Exists(inputFilePath))
            {
                Console.WriteLine("Input PDF file not found!");
                return;
            }
            
            using (Annotator annotator = new Annotator(inputFilePath))
            {
                // Create a highlight annotation
                AreaAnnotation area = new AreaAnnotation()
                {
                    Box = new Rectangle(100, 100, 200, 100),
                    BackgroundColor = 65535, // Yellow highlight
                };
                
                // Add annotation to document
                annotator.Add(area);
                
                // Save the annotated document
                annotator.Save(outputPath);
                
                Console.WriteLine($"Success! Annotated PDF saved to: {outputPath}");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

## Các lỗi thường gặp và cách tránh

### Làm sao ngăn vấn đề đường dẫn file trong production?
Sử dụng đường dẫn tuyệt đối hoặc kết hợp các đoạn đường dẫn tương đối với `Path.Combine` và `AppDomain.BaseDirectory` để đảm bảo vị trí file được giải quyết đúng bất kể thư mục làm việc hiện tại. Cách này cũng giúp tránh lỗi do ký tự phân tách đường dẫn khác nhau trên các hệ điều hành.

```csharp
string inputFilePath = Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Documents", "input.pdf");
```

### Làm sao tránh rò rỉ bộ nhớ với PDF lớn?
Bao bọc thể hiện `Annotator` trong khối `using` để giải phóng tài nguyên không quản lý ngay khi thao tác hoàn tất. Mẫu này đảm bảo các handle file và bộ đệm bộ nhớ được giải phóng kịp thời, ngăn ngừa rò rỉ trong các dịch vụ chạy lâu dài.

```csharp
using (Annotator annotator = new Annotator(inputFilePath))
{
    // Work with annotations
} // Automatically disposed here
```

### Làm sao khắc phục sai lệch tọa độ?
GroupDocs sử dụng gốc tọa độ góc trên‑trái, trong khi các công cụ PDF gốc thường bắt đầu từ góc dưới‑trái. Kiểm tra với các giá trị rõ ràng (ví dụ 50, 50) và điều chỉnh bằng công thức `PageHeight - y` nếu cần. Hiểu sự khác biệt này và áp dụng công thức chuyển đổi đơn giản sẽ giữ cho chú thích của bạn luôn nằm đúng vị trí trên mọi trang.

### Làm sao đảm bảo giấy phép hoạt động sau khi triển khai?
Triển khai file `GroupDocs.Annotation.lic` cùng thư mục thực thi, sau đó gọi lớp `License` ngay trong khởi động ứng dụng. Kiểm tra trạng thái giấy phép bằng cách kiểm tra `License.IsValid` (nếu có) hoặc bắt các ngoại lệ liên quan đến giấy phép trong lần gọi SDK đầu tiên.

```csharp
// Set license before creating Annotator
License license = new License();
license.SetLicense("path/to/your/GroupDocs.Annotation.lic");
```

## Kỹ thuật chú thích nâng cao

### Làm sao thêm nhiều loại chú thích trong một lần?
GroupDocs.Annotation hỗ trợ đa dạng loại chú thích, cho phép bạn tạo note, arrow, stamp và hơn thế nữa trong một thao tác. Bằng cách khởi tạo mỗi đối tượng chú thích và thêm chúng tuần tự trước khi lưu, bạn có thể batch‑process các kịch bản markup phức tạp một cách hiệu quả.

**Chú thích văn bản (comment):**

```csharp
TextAnnotation textAnnotation = new TextAnnotation()
{
    Box = new Rectangle(200, 200, 100, 30),
    Message = "This needs review",
    FontColor = 16777215, // White text
    BackgroundColor = 255 // Red background
};
```

**Chú thích mũi tên để chỉ hướng:**

```csharp
ArrowAnnotation arrow = new ArrowAnnotation()
{
    Box = new Rectangle(300, 300, 100, 100),
    Message = "Important section"
};
```

### Làm sao xử lý nhiều PDF trong batch?
Duyệt qua một thư mục, khởi tạo một `Annotator` cho mỗi file, áp dụng các chú thích mong muốn, và lưu kết quả từng file. Mẫu này mở rộng tốt vì mỗi thể hiện `Annotator` được cô lập, ngăn chéo dữ liệu giữa các file và cho phép xử lý song song nếu cần.

```csharp
string[] pdfFiles = Directory.GetFiles(@"C:\InputFolder", "*.pdf");

foreach (string pdfFile in pdfFiles)
{
    string outputFile = Path.Combine(@"C:\OutputFolder", 
        Path.GetFileNameWithoutExtension(pdfFile) + "_annotated.pdf");
    
    using (Annotator annotator = new Annotator(pdfFile))
    {
        // Add your annotations
        // Save to output folder
        annotator.Save(outputFile);
    }
}
```

## Mẹo tối ưu hiệu năng

### Làm sao quản lý bộ nhớ cho tài liệu khổng lồ?
Xử lý từng trang riêng lẻ và giải phóng mỗi `Annotator` ngay khi hoàn thành trang. Bằng cách giới hạn footprint bộ nhớ chỉ còn một trang, bạn giữ mức sử dụng bộ nhớ thấp ngay cả với các PDF có kích thước hàng trăm megabyte.

```csharp
// Good: Dispose immediately after use
using (Annotator annotator = new Annotator(inputFilePath))
{
    // Do your work
    annotator.Save(outputPath);
} // Disposed here

// Bad: Keeping references longer than needed
Annotator annotator = new Annotator(inputFilePath);
// ... lots of other code ...
annotator.Save(outputPath);
annotator.Dispose(); // Too late for efficient memory management
```

### Làm sao làm cho các lời gọi chú thích không chặn trong Web API?
Bọc lời gọi đồng bộ trong `Task.Run` hoặc sử dụng async stream I/O để tránh chặn luồng yêu cầu. Kỹ thuật này cải thiện khả năng mở rộng của các endpoint ASP.NET Core thực hiện chú thích PDF như một phần của quy trình lớn hơn.

```csharp
public async Task<string> AnnotatePdfAsync(string inputPath, string outputPath)
{
    return await Task.Run(() =>
    {
        using (Annotator annotator = new Annotator(inputPath))
        {
            // Add annotations
            annotator.Save(outputPath);
            return outputPath;
        }
    });
}
```

### Làm sao cache các PDF đã được chú thích thường xuyên?
Lưu mảng byte đã được chú thích vào cache phân tán (ví dụ Redis) và trả về trực tiếp khi có yêu cầu. Caching loại bỏ việc thực hiện lại các thao tác chú thích và giảm độ trễ cho các kịch bản lưu lượng cao.

```csharp
private static readonly Dictionary<string, byte[]> AnnotationCache = 
    new Dictionary<string, byte[]>();

private byte[] GetCachedAnnotation(string documentHash)
{
    return AnnotationCache.ContainsKey(documentHash) 
        ? AnnotationCache[documentHash] 
        : null;
}
```

## Các trường hợp sử dụng thực tế

### Doanh nghiệp sử dụng chú thích PDF như thế nào?
Doanh nghiệp tích hợp chú thích PDF vào nhiều quy trình kinh doanh: đội pháp lý thêm comment và stamp phê duyệt vào hợp đồng; giáo viên cung cấp phản hồi trên tài liệu giảng dạy; kỹ sư đánh dấu bản vẽ kỹ thuật; và công ty bảo hiểm highlight các mục hợp đồng để xử lý yêu cầu nhanh hơn. Những ví dụ này chứng tỏ tính linh hoạt và giá trị của việc đánh dấu PDF bằng lập trình.

## Khắc phục các vấn đề thường gặp

### Tại sao tôi gặp lỗi “File not found”?
Lỗi này thường xuất hiện khi đường dẫn cung cấp không đúng, file bị khóa bởi tiến trình khác, hoặc ứng dụng thiếu quyền truy cập. Kiểm tra xem đường dẫn có sử dụng đúng dấu gạch chéo cho hệ điều hành, xác nhận file tồn tại, và cấp quyền đọc/ghi cho người dùng chạy ứng dụng.

### Tại sao chú thích xuất hiện sai vị trí?
Sự không khớp tọa độ xảy ra vì GroupDocs dùng gốc góc trên‑trái trong khi nhiều công cụ PDF dùng gốc góc dưới‑trái. Kiểm tra kích thước trang (`PageWidth`, `PageHeight`) và áp dụng công thức chuyển đổi `PageHeight - y` khi cần. Thử nghiệm với các tọa độ đơn giản sẽ giúp bạn hiệu chỉnh logic vị trí.

### Tại sao ứng dụng hết bộ nhớ?
Xử lý PDF lớn mà không streaming có thể làm cạn kiệt bộ nhớ của tiến trình. Chia công việc thành các batch nhỏ, bật `AnnotatorOptions.UseMemoryCache = false` để stream dữ liệu, và chạy ứng dụng ở chế độ 64‑bit để tăng không gian địa chỉ khả dụng.

### Tại sao xuất hiện watermark trong production?
Watermark được tự động thêm khi giấy phép dùng thử đang hoạt động. Triển khai file giấy phép đầy đủ, gọi lớp `License` trước bất kỳ thao tác SDK nào, và xác nhận file giấy phép được đặt đúng vị trí để loại bỏ overlay watermark.

## Câu hỏi thường gặp

**H: Tôi có thể chú thích các loại file khác ngoài PDF không?**  
Đ: Có. GroupDocs.Annotation hỗ trợ **hơn 50 định dạng**, bao gồm DOCX, XLSX, PPTX và các loại ảnh phổ biến, bằng cùng một API.

**H: Làm sao mở PDF được bảo vệ bằng mật khẩu?**  
Đ: Truyền mật khẩu vào constructor của `Annotator`:

```csharp
using (Annotator annotator = new Annotator(inputFilePath, new LoadOptions { Password = "your_password" }))
{
    // Your annotation code
}
```

**H: Có giới hạn số lượng chú thích trên một tài liệu không?**  
Đ: Không có giới hạn cứng, nhưng hiệu năng sẽ giảm sau khoảng **1.000 chú thích**; nên chia file lớn thành các phần.

**H: Tôi có thể trích xuất các chú thích hiện có bằng mã không?**  
Đ: Sử dụng phương thức `Get` để lấy tập hợp tất cả các chú thích:

```csharp
List<AnnotationBase> annotations = annotator.Get();
```

**H: Làm sao tùy chỉnh màu và phông chữ của chú thích?**  
Đ: Mỗi loại chú thích đều có thuộc tính hiển thị; ví dụ, đặt `BackgroundColor` và `Font` trên một `TextAnnotation`:

```csharp
TextAnnotation text = new TextAnnotation()
{
    FontColor = 16777215, // White
    FontSize = 12,
    FontFamily = "Arial",
    BackgroundColor = 255 // Red
};
```

**H: SDK có an toàn cho các ứng dụng web đa luồng không?**  
Đ: Các thể hiện `Annotator` **không thread‑safe**; tạo một thể hiện mới cho mỗi yêu cầu hoặc triển khai cơ chế đồng bộ.

**H: Làm sao xóa một chú thích cụ thể?**  
Đ: Tìm chú thích theo ID và gọi `Delete`:

```csharp
List<AnnotationBase> annotations = annotator.Get();
annotator.Remove(annotations[0]); // Remove first annotation
```

## Kết luận

Bạn đã có một lộ trình hoàn chỉnh, sẵn sàng cho production để **tạo chú thích PDF .NET** với GroupDocs.Annotation. Từ việc cài đặt và cấp phép, tới xây dựng highlight, note, arrow và pipeline batch, xử lý file lớn và khắc phục lỗi, mọi phần quan trọng đã được bao phủ. Hãy bắt đầu với một trường hợp sử dụng đơn giản, triển khai các đoạn mã ở trên, và dần mở rộng tới các workflow phức tạp hơn như review cộng tác hoặc đánh dấu dựa trên AI.

---

**Cập nhật lần cuối:** 2026-05-21  
**Kiểm thử với:** GroupDocs.Annotation 25.4.0 cho .NET  
**Tác giả:** GroupDocs  

**Tài nguyên bổ sung**  
- [Tài liệu GroupDocs.Annotation](https://docs.groupdocs.com/annotation/net/)  
- [Hướng dẫn API đầy đủ](https://reference.groupdocs.com/annotation/net/)  
- [Bản phát hành mới nhất](https://releases.groupdocs.com/annotation/net/)  
- [Diễn đàn GroupDocs](https://forum.groupdocs.com/c/annotation)  
- [Trang mua hàng](https://purchase.groupdocs.com/buy)

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}

## Hướng dẫn liên quan

- [Load PDF from URL .NET - Hướng dẫn đầy đủ với GroupDocs.Annotation](/annotation/net/document-loading-essentials/load-document-from-url/)
- [Add Form Fields to PDF .NET - Hướng dẫn đầy đủ GroupDocs.Annotation](/annotation/net/form-field-annotations/)
- [How to Save Annotated Documents in .NET - Hướng dẫn đầy đủ GroupDocs.Annotation](/annotation/net/annotation-management/mastering-document-annotation-dotnet-groupdocs/)