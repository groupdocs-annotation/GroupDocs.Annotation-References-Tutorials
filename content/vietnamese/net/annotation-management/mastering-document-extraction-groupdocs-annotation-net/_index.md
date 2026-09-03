---
categories:
- Document Processing
date: '2026-06-01'
description: Tìm hiểu cách trích xuất số trang pdf c#, lấy loại tệp và đọc thuộc tính
  tệp c# bằng GroupDocs.Annotation .NET. Bao gồm mã thực tế và các mẹo.
keywords:
- c# pdf page count
- c# get file type
- read file properties c#
- c# read document size
lastmod: '2026-06-01'
linktitle: Trích xuất thông tin tài liệu C#
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract c# pdf page count, get file type, and read file
    properties c# using GroupDocs.Annotation .NET. Includes practical code and tips.
  headline: c# pdf page count – Extract Document Info with GroupDocs
  type: TechArticle
- description: Learn how to extract c# pdf page count, get file type, and read file
    properties c# using GroupDocs.Annotation .NET. Includes practical code and tips.
  name: c# pdf page count – Extract Document Info with GroupDocs
  steps:
  - name: '**Start with the Free Trial**: Download from the [GroupDocs website](https://releases.groupdocs.com/annotation/net/)
      – no strings attached.'
    text: '**Start with the Free Trial**: Download from the [GroupDocs website](https://releases.groupdocs.com/annotation/net/)
      – no strings attached.'
  - name: '**Need More Time?** Get a [temporary license](https://purchase.groupdocs.com/temporary-license/)
      for extended evaluation.'
    text: '**Need More Time?** Get a [temporary license](https://purchase.groupdocs.com/temporary-license/)
      for extended evaluation.'
  - name: '**Ready to Go Live?** [Purchase a full license](https://purchase.groupdocs.com/buy)
      when you''re ready to deploy.'
    text: '**Ready to Go Live?** [Purchase a full license](https://purchase.groupdocs.com/buy)
      when you''re ready to deploy.'
  - name: Clone the sample project and run the provided placeholders with real files.
    text: Clone the sample project and run the provided placeholders with real files.
  - name: Explore additional GroupDocs.Annotation features like annotation rendering
      and document comparison.
    text: Explore additional GroupDocs.Annotation features like annotation rendering
      and document comparison.
  - name: Integrate the metadata extraction into your existing upload pipeline to
      automate classification and validation.
    text: Integrate the metadata extraction into your existing upload pipeline to
      automate classification and validation.
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation supports over 50 document formats, including PDF,
      DOCX, XLSX, PPTX, JPEG, PNG, TIFF, CAD files, and many more.
    question: What document formats does GroupDocs.Annotation support for information
      extraction?
  - answer: '`GetDocumentInfo()` provides core metadata like file type, page count,
      and size. For custom properties such as author or creation date, combine GroupDocs.Annotation
      with GroupDocs.Metadata or use the native file format’s property APIs.'
    question: Can I extract custom metadata or properties from documents?
  - answer: Provide the password when creating the `Annotator` instance, e.g., `new
      Annotator("secure.pdf", new LoadOptions { Password = "pwd" })`.
    question: How do I handle password‑protected documents?
  - answer: Yes—`GetDocumentInfo()` reads only the file header, so memory consumption
      stays low even for multi‑hundred‑page PDFs.
    question: Is there a way to extract document information without loading the entire
      file into memory?
  - answer: Absolutely. GroupDocs.Annotation is thread‑safe; just create a new `Annotator`
      per request and dispose of it promptly.
    question: Can I use this in a web application or multi‑threaded environment?
  type: FAQPage
tags:
- csharp
- document-extraction
- groupdocs
- dotnet
title: đếm số trang pdf c# – Trích xuất thông tin tài liệu với GroupDocs
type: docs
url: /vi/net/annotation-management/mastering-document-extraction-groupdocs-annotation-net/
weight: 1
---

# đếm trang pdf c# – Trích xuất thông tin tài liệu với GroupDocs.Annotation

## Giới thiệu

Bạn đã bao giờ nhìn chằm chằm vào một đống tài liệu, tự hỏi bên trong chúng thực sự có gì mà không cần mở từng tệp? Bạn chắc chắn không phải là người duy nhất gặp khó khăn này. Dù bạn đang xây dựng hệ thống quản lý tài liệu, xử lý các tệp pháp lý, hay chỉ đơn giản là cố gắng sắp xếp tài sản kỹ thuật số của công ty, việc biết cách **trích xuất thông tin tài liệu trong C#**—bao gồm **đếm trang pdf c#**—có thể là một yếu tố thay đổi cuộc chơi thực sự.

Kiểm tra thuộc tính tệp một cách thủ công tốn thời gian và dễ gây lỗi. Với **GroupDocs.Annotation cho .NET**, bạn có thể tự động hoá toàn bộ quá trình và lấy loại tệp, số trang, kích thước tài liệu và hơn thế nữa chỉ trong vài dòng mã. Hướng dẫn này sẽ cho bạn thấy tại sao điều này quan trọng, cách thiết lập thư viện, và mã từng bước hoạt động ngay từ đầu.

## Câu trả lời nhanh
- **GroupDocs.Annotation trích xuất gì?** Loại tệp, số trang, kích thước và siêu dữ liệu cơ bản.  
- **Có bao nhiêu định dạng được hỗ trợ?** Hơn 50 định dạng đầu vào và đầu ra, bao gồm PDF, DOCX, XLSX, PPTX và các loại ảnh phổ biến.  
- **Tôi có thể lấy đếm trang pdf c# mà không tải toàn bộ tệp không?** Có—`GetDocumentInfo()` chỉ đọc thông tin tiêu đề cần thiết cho số trang.  
- **Tôi có cần giấy phép cho việc phát triển không?** Bản dùng thử miễn phí đủ cho việc thử nghiệm; giấy phép đầy đủ cần thiết cho môi trường sản xuất.  
- **API có an toàn đa luồng cho các ứng dụng web không?** Hoàn toàn—chỉ cần giải phóng các đối tượng `Annotator` một cách đúng đắn.

## Đếm trang pdf c# là gì?
**Đếm trang pdf c#** là tổng số trang mà một tệp PDF báo cáo khi được truy vấn qua API. Sử dụng GroupDocs.Annotation, bạn nhận được giá trị này ngay lập tức qua phương thức `GetDocumentInfo()` mà không cần render toàn bộ tài liệu. Số này được lấy từ cấu trúc nội bộ của PDF, cho phép bạn đưa ra quyết định về xử lý, lưu trữ hoặc hiển thị mà không mở tệp trong trình xem. Nó đặc biệt hữu ích cho việc kiểm tra hàng loạt, kiểm tra tuân thủ và xem trước UI nơi giới hạn số trang quan trọng.

## Tại sao nên trích xuất thông tin tài liệu với GroupDocs.Annotation?
GroupDocs.Annotation hỗ trợ **hơn 50 định dạng tài liệu** và có thể xử lý các tệp hàng trăm trang mà không tải toàn bộ tệp vào bộ nhớ, cung cấp siêu dữ liệu trong dưới 200 ms trên máy chủ tiêu chuẩn. Tốc độ và độ bao phủ định dạng này làm cho nó trở thành lựa chọn lý tưởng cho tự động hoá quy mô lớn, kiểm tra tuân thủ, và phân loại nội dung thông minh.

## Yêu cầu trước và Cài đặt

### Những gì bạn cần
- Visual Studio 2019 hoặc mới hơn (phiên bản Community hoạt động tốt)  
- .NET Framework 4.6.1+ **hoặc** .NET Core 2.0+  
- Kiến thức cơ bản về C# và quen thuộc với NuGet  

### Cài đặt GroupDocs.Annotation
Việc đưa thư viện vào dự án của bạn rất đơn giản. Chọn phương pháp bạn ưa thích:

**Tùy chọn 1: Package Manager Console (Được đề xuất)**
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**Tùy chọn 2: .NET CLI**
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

**Tùy chọn 3: Giao diện Package Manager**  
Nếu bạn thích nhấp chuột hơn là gõ lệnh, chỉ cần tìm kiếm "GroupDocs.Annotation" trong giao diện NuGet Package Manager và cài đặt phiên bản mới nhất.

### Nhận giấy phép của bạn
1. **Bắt đầu với bản dùng thử miễn phí**: Tải xuống từ [trang web GroupDocs](https://releases.groupdocs.com/annotation/net/) – không ràng buộc gì.  
2. **Cần thêm thời gian?** Nhận một [giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/) để đánh giá kéo dài.  
3. **Sẵn sàng triển khai?** [Mua giấy phép đầy đủ](https://purchase.groupdocs.com/buy) khi bạn đã sẵn sàng đưa vào hoạt động.  

> **Mẹo chuyên nghiệp:** Bản dùng thử miễn phí có chứa watermark, nhưng nó hoàn hảo cho việc học và thử nghiệm mã của bạn.

Đối với các thay đổi mới nhất, xem [release notes](https://releases.groupdocs.com/annotation/net/).

## Cách lấy đếm trang pdf c# với GroupDocs.Annotation?

**Annotator** là lớp chính tải tài liệu và cung cấp các chức năng chú thích và siêu dữ liệu.  
Tải PDF của bạn bằng `new Annotator("file.pdf")` và gọi `GetDocumentInfo()` – thuộc tính `PageCount` trả về số trang chính xác chỉ trong hai dòng mã. **GetDocumentInfo()** trả về một đối tượng **DocumentInfo** chứa siêu dữ liệu như số trang, loại tệp và kích thước. Phương thức này chỉ đọc dữ liệu tiêu đề cần thiết, vì vậy ngay cả các PDF lớn cũng được xử lý hiệu quả.

### Cài đặt cơ bản và tải tài liệu
```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main(string[] args)
    {
        // Initialize the annotator with a document path
        using (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf"))
        {
            Console.WriteLine("Document loaded successfully!");
            // We'll add the extraction code here next
        }
    }
}
```  

### Trích xuất siêu dữ liệu tài liệu
**DocumentInfo** đóng gói các thuộc tính đã được trích xuất của tệp, giúp chúng dễ đọc và sử dụng trong ứng dụng của bạn.  
```csharp
using (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf"))
{
    // Extract document info
    IDocumentInfo info = annotator.Document.GetDocumentInfo();
    
    // Always check if info was retrieved successfully
    if (info == null || info.PageCount == 0)
    {
        throw new Exception("Unexpected document information!");
    }

    // Display the extracted information
    Console.WriteLine($"\
File type: {info.FileType}\
Number of pages: {info.PageCount}\
Document size: {info.Size} bytes.");
    
    // Convert size to more readable format
    string readableSize = FormatFileSize(info.Size);
    Console.WriteLine($"Document size (formatted): {readableSize}");
}

// Helper method to format file size
static string FormatFileSize(long bytes)
{
    string[] suffixes = { "B", "KB", "MB", "GB", "TB" };
    int counter = 0;
    decimal number = bytes;
    
    while (Math.Round(number / 1024) >= 1)
    {
        number /= 1024;
        counter++;
    }
    
    return string.Format("{0:n1}{1}", number, suffixes[counter]);
}
```  

### Hiển thị thông tin nâng cao
Nếu bạn cần ngữ cảnh bổ sung—chẳng hạn như tài liệu có vượt quá ngưỡng kích thước hay không—bạn có thể mở rộng ví dụ cơ bản với các kiểm tra và logic nghiệp vụ thêm.

```csharp
using (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf"))
{
    IDocumentInfo info = annotator.Document.GetDocumentInfo();
    
    if (info == null)
    {
        Console.WriteLine("Could not retrieve document information.");
        return;
    }

    // Comprehensive info display
    Console.WriteLine("=== Document Information ===");
    Console.WriteLine($"File Type: {info.FileType}");
    Console.WriteLine($"Page Count: {info.PageCount}");
    Console.WriteLine($"Size: {FormatFileSize(info.Size)}");
    
    // Additional checks you might want to perform
    if (info.PageCount > 100)
    {
        Console.WriteLine("⚠️  Large document detected - consider batch processing");
    }
    
    if (info.Size > 10 * 1024 * 1024) // 10MB
    {
        Console.WriteLine("⚠️  Large file size - may impact processing time");
    }
    
    Console.WriteLine("=== Analysis Complete ===");
}
```  

## Các vấn đề thường gặp và giải pháp

### Vấn đề 1: Lỗi “File Not Found”
**Direct answer:** Xác minh rằng đường dẫn tệp là tuyệt đối hoặc được gốc đúng tới thư mục gốc của ứng dụng, và đảm bảo tiến trình có quyền đọc.  

```csharp
string documentPath = @"C:\Documents\test.pdf";

// Always check if file exists first
if (!File.Exists(documentPath))
{
    Console.WriteLine($"File not found: {documentPath}");
    return;
}

try
{
    using (Annotator annotator = new Annotator(documentPath))
    {
        // Your code here
    }
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```  

### Vấn đề 2: Định dạng tệp không được hỗ trợ
**Direct answer:** Xác nhận rằng phần mở rộng của tệp khớp với một trong hơn 50 định dạng được hỗ trợ; nếu không, hãy chuyển đổi sang kiểu được hỗ trợ trước khi gọi `GetDocumentInfo()`.  

```csharp
try
{
    using (Annotator annotator = new Annotator(documentPath))
    {
        IDocumentInfo info = annotator.Document.GetDocumentInfo();
        
        if (info == null)
        {
            Console.WriteLine("Unsupported file format or corrupted document");
            return;
        }
        
        // Process the info
    }
}
catch (UnsupportedFileTypeException ex)
{
    Console.WriteLine($"File type not supported: {ex.Message}");
}
```  

### Vấn đề 3: Vấn đề bộ nhớ với tài liệu lớn
**Direct answer:** Thực hiện kiểm tra kích thước trước khi tải và sử dụng câu lệnh `using` để đảm bảo giải phóng đối tượng `Annotator`, tránh rò rỉ bộ nhớ.  

```csharp
const long MAX_FILE_SIZE = 50 * 1024 * 1024; // 50MB limit

FileInfo fileInfo = new FileInfo(documentPath);
if (fileInfo.Length > MAX_FILE_SIZE)
{
    Console.WriteLine("File too large for processing");
    return;
}

// Use proper disposal patterns
using (Annotator annotator = new Annotator(documentPath))
{
    // Process quickly and dispose
    IDocumentInfo info = annotator.Document.GetDocumentInfo();
    // Handle info immediately
}
// Annotator is automatically disposed here
```  

## Các trường hợp sử dụng thực tế

### Tích hợp hệ thống quản lý tài liệu
Khi người dùng tải lên một tệp, trích xuất siêu dữ liệu trước để quyết định vị trí lưu trữ, chiến lược lập chỉ mục, hoặc quy trình phê duyệt cần thiết.

```csharp
public class DocumentProcessor
{
    public DocumentMetadata ProcessUpload(string filePath)
    {
        using (Annotator annotator = new Annotator(filePath))
        {
            IDocumentInfo info = annotator.Document.GetDocumentInfo();
            
            return new DocumentMetadata
            {
                FileName = Path.GetFileName(filePath),
                FileType = info.FileType.ToString(),
                PageCount = info.PageCount,
                FileSizeBytes = info.Size,
                ProcessedDate = DateTime.UtcNow,
                Category = DetermineCategory(info)
            };
        }
    }
    
    private string DetermineCategory(IDocumentInfo info)
    {
        // Business logic for automatic categorization
        if (info.FileType.ToString().Contains("Pdf"))
        {
            return info.PageCount > 20 ? "Legal Document" : "Standard Document";
        }
        
        return "Other";
    }
}
```  

### Phân tích tài liệu hàng loạt
Xử lý một thư mục các tệp trong công việc nền, ghi lại số trang và loại của mỗi tài liệu để báo cáo.

```csharp
public void AnalyzeDocumentFolder(string folderPath)
{
    string[] supportedExtensions = { ".pdf", ".docx", ".xlsx", ".pptx" };
    
    foreach (string file in Directory.GetFiles(folderPath))
    {
        if (!supportedExtensions.Contains(Path.GetExtension(file).ToLower()))
            continue;
            
        try
        {
            using (Annotator annotator = new Annotator(file))
            {
                IDocumentInfo info = annotator.Document.GetDocumentInfo();
                Console.WriteLine($"{Path.GetFileName(file)}: {info.FileType}, {info.PageCount} pages");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to process {file}: {ex.Message}");
        }
    }
}
```  

### Tuân thủ và xác thực
Các ngành công nghiệp được quy định thường yêu cầu tài liệu phải dưới một số trang hoặc kích thước nhất định. Sử dụng siêu dữ liệu đã trích xuất để tự động từ chối các tệp tải lên không tuân thủ.

```csharp
public bool ValidateDocument(string filePath, DocumentRequirements requirements)
{
    using (Annotator annotator = new Annotator(filePath))
    {
        IDocumentInfo info = annotator.Document.GetDocumentInfo();
        
        // Check file type
        if (requirements.AllowedTypes != null && 
            !requirements.AllowedTypes.Contains(info.FileType.ToString()))
        {
            return false;
        }
        
        // Check page count limits
        if (info.PageCount < requirements.MinPages || 
            info.PageCount > requirements.MaxPages)
        {
            return false;
        }
        
        // Check file size
        if (info.Size > requirements.MaxSizeBytes)
        {
            return false;
        }
        
        return true;
    }
}
```  

## Mẹo tối ưu hoá hiệu suất

### 1. Triển khai bộ nhớ đệm
Lưu trữ kết quả `DocumentInfo` cho các tệp được truy cập thường xuyên để tránh các thao tác I/O lặp lại.

```csharp
private static readonly Dictionary<string, IDocumentInfo> _infoCache = 
    new Dictionary<string, IDocumentInfo>();

public IDocumentInfo GetDocumentInfoCached(string filePath)
{
    string fileHash = GetFileHash(filePath);
    
    if (_infoCache.ContainsKey(fileHash))
    {
        return _infoCache[fileHash];
    }
    
    using (Annotator annotator = new Annotator(filePath))
    {
        IDocumentInfo info = annotator.Document.GetDocumentInfo();
        _infoCache[fileHash] = info;
        return info;
    }
}
```  

### 2. Sử dụng xử lý bất đồng bộ cho nhiều tài liệu
Tận dụng `Task.Run` hoặc async streams để xử lý nhiều tệp đồng thời mà không chặn luồng chính.

```csharp
public async Task<List<DocumentMetadata>> ProcessDocumentsAsync(string[] filePaths)
{
    var tasks = filePaths.Select(async path =>
    {
        return await Task.Run(() =>
        {
            using (Annotator annotator = new Annotator(path))
            {
                IDocumentInfo info = annotator.Document.GetDocumentInfo();
                return new DocumentMetadata(path, info);
            }
        });
    });
    
    return (await Task.WhenAll(tasks)).ToList();
}
```  

### 3. Thực hành tốt quản lý bộ nhớ
- Luôn bao bọc `Annotator` trong một khối `using`.  
- Xử lý tài liệu theo lô, không xử lý tất cả cùng một lúc.  
- Đối với các tệp lớn hơn 100 MB, hãy cân nhắc stream tệp ra đĩa trước rồi mới đọc siêu dữ liệu.  

## Hướng dẫn khắc phục sự cố

### Các vấn đề liên quan đến giấy phép
**License** là đối tượng đăng ký tệp kích hoạt sản phẩm của bạn với thư viện GroupDocs. Đảm bảo tệp giấy phép được đặt trong thư mục gốc của ứng dụng và đối tượng `License` được khởi tạo trước bất kỳ lời gọi nào khác của GroupDocs.  

```csharp
// Set license before using any GroupDocs functionality
License license = new License();
license.SetLicense("path/to/your/license.lic");

// Or use stream for embedded licenses
using (Stream stream = Assembly.GetExecutingAssembly().GetManifestResourceStream("YourApp.license.lic"))
{
    license.SetLicense(stream);
}
```  

### Vấn đề hiệu suất
**Direct answer:** Đánh giá hiệu năng ứng dụng, giới hạn kích thước tệp dưới 100 MB cho xử lý thời gian thực, và bật bộ nhớ đệm cho các lần đọc lặp lại.  

### Các vấn đề đặc thù nền tảng
**Direct answer:** Sử dụng `Path.Combine` để xây dựng đường dẫn đa nền tảng; Windows dùng dấu gạch ngược (\) trong khi Linux dùng dấu gạch chéo (/).  

```csharp
// Use Path.Combine for cross-platform compatibility
string documentPath = Path.Combine(baseDirectory, "documents", fileName);
```  

### Xử lý tài liệu có mật khẩu
**Direct answer:** Truyền mật khẩu vào hàm khởi tạo `Annotator`, ví dụ `new Annotator("secure.pdf", new LoadOptions { Password = "pwd" })`.  

```csharp
LoadOptions loadOptions = new LoadOptions() { Password = "your-password" };
using (Annotator annotator = new Annotator("protected-document.pdf", loadOptions))
{
    // Extract information normally
}
```  

### Cập nhật GroupDocs.Annotation
**Direct answer:** Chạy `dotnet add package GroupDocs.Annotation --version <latest>` hoặc sử dụng giao diện NuGet Package Manager để tải phiên bản mới nhất.  

```shell
Update-Package GroupDocs.Annotation
```  

## Câu hỏi thường gặp

**Q: GroupDocs.Annotation hỗ trợ những định dạng tài liệu nào để trích xuất thông tin?**  
A: GroupDocs.Annotation hỗ trợ hơn 50 định dạng tài liệu, bao gồm PDF, DOCX, XLSX, PPTX, JPEG, PNG, TIFF, các tệp CAD và nhiều hơn nữa.

**Q: Tôi có thể trích xuất siêu dữ liệu hoặc thuộc tính tùy chỉnh từ tài liệu không?**  
A: `GetDocumentInfo()` cung cấp siêu dữ liệu cốt lõi như loại tệp, số trang và kích thước. Đối với các thuộc tính tùy chỉnh như tác giả hoặc ngày tạo, bạn có thể kết hợp GroupDocs.Annotation với GroupDocs.Metadata hoặc sử dụng API thuộc tính gốc của định dạng tệp.

**Q: Làm thế nào để xử lý tài liệu có mật khẩu?**  
A: Cung cấp mật khẩu khi tạo đối tượng `Annotator`, ví dụ `new Annotator("secure.pdf", new LoadOptions { Password = "pwd" })`.

**Q: Có cách nào để trích xuất thông tin tài liệu mà không tải toàn bộ tệp vào bộ nhớ không?**  
A: Có—`GetDocumentInfo()` chỉ đọc phần tiêu đề của tệp, vì vậy mức tiêu thụ bộ nhớ vẫn thấp ngay cả với các PDF hàng trăm trang.

**Q: Tôi có thể sử dụng điều này trong ứng dụng web hoặc môi trường đa luồng không?**  
A: Chắc chắn—GroupDocs.Annotation an toàn đa luồng; chỉ cần tạo một `Annotator` mới cho mỗi yêu cầu và giải phóng nó kịp thời.

## Kết luận và các bước tiếp theo

Bạn hiện đã có một cách tiếp cận hoàn chỉnh, sẵn sàng cho môi trường sản xuất để trích xuất **đếm trang pdf c#**, loại tệp và kích thước bằng GroupDocs.Annotation. Bạn đã học cách thiết lập thư viện, lấy siêu dữ liệu, xử lý các vấn đề thường gặp, và tối ưu hoá hiệu suất cho các kịch bản quy mô lớn.

**Các hành động tiếp theo:**  
1. Sao chép dự án mẫu và chạy các placeholder với các tệp thực tế.  
2. Khám phá các tính năng bổ sung của GroupDocs.Annotation như render chú thích và so sánh tài liệu.  
3. Tích hợp việc trích xuất siêu dữ liệu vào quy trình tải lên hiện có để tự động hoá phân loại và xác thực.

Nhớ rằng, xử lý tài liệu mạnh mẽ bắt đầu từ siêu dữ liệu đáng tin cậy. Với GroupDocs.Annotation, bạn có thể xây dựng các giải pháp thông minh, nhanh hơn và mở rộng hơn.

**Cập nhật lần cuối:** 2026-06-01  
**Kiểm tra với:** GroupDocs.Annotation 25.4.0 (latest)  
**Tác giả:** GroupDocs  

**Liên kết quan trọng:**  
- **[Tài liệu](https://docs.groupdocs.com/annotation/net/)**  
- **[Tham chiếu API](https://reference.groupdocs.com/annotation/net/)**  
- **[Tải phiên bản mới nhất](https://releases.groupdocs.com/annotation/net/)**  
- **[Mua giấy phép](https://purchase.groupdocs.com/buy)**  
- **[Tải bản dùng thử](https://releases.groupdocs.com/annotation/net/)**  
- **[Yêu cầu giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/)**  
- **[Diễn đàn hỗ trợ cộng đồng](https://forum.groupdocs.com/c/annotation/)**  

## Các hướng dẫn liên quan

- [Trích xuất siêu dữ liệu tài liệu .NET - Hướng dẫn đầy đủ về GroupDocs.Annotation](/annotation/net/document-information/)  
- [Kích thước trang PDF .NET - Trích xuất chiều rộng & chiều cao với C#](/annotation/net/document-information/groupdocs-annotation-net-retrieve-pdf-page-dimensions/)  
- [Hướng dẫn GroupDocs.Annotation .NET: Trích xuất & Lưu các trang PDF cụ thể](/annotation/net/annotation-management/groupdocs-annotation-dotnet-page-range-management/)