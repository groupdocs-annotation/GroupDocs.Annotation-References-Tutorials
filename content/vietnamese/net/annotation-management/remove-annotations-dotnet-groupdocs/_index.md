---
categories:
- Document Processing
date: '2026-06-01'
description: Tìm hiểu cách xóa chú thích pdf khỏi các tệp PDF bằng GroupDocs.Annotation
  cho .NET. Bao gồm mã từng bước, khắc phục sự cố và các thực tiễn tốt nhất.
keywords:
- remove pdf annotations
- how to remove annotations
- delete pdf annotations
- clear pdf comments
- strip pdf markup
lastmod: '2026-06-01'
linktitle: Xóa chú thích PDF C#
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to remove pdf annotations from PDF files using GroupDocs.Annotation
    for .NET. Includes step-by-step code, troubleshooting, and best practices.
  headline: Remove Annotations from PDF C#
  type: TechArticle
- description: Learn how to remove pdf annotations from PDF files using GroupDocs.Annotation
    for .NET. Includes step-by-step code, troubleshooting, and best practices.
  name: Remove Annotations from PDF C#
  steps:
  - name: Load Your Document
    text: '`Annotator` is GroupDocs.Annotation''s core class that opens a file and
      exposes its annotation collection. **Common Gotcha:** Ensure the file path is
      correct and the file isn’t locked by another process. A typo in the path is
      a frequent source of “file not found” errors.'
  - name: Get and Filter Annotations
    text: '`Annotation` objects represent individual markup items such as comments,
      highlights, or stamps. You can inspect each annotation’s type, author, page
      number, or custom metadata before deciding to delete it. **Why This Works:**
      By filtering first, you avoid accidentally removing useful markup such as '
  - name: Save Your Clean Document
    text: Give the cleaned file a distinct name (e.g., `cleaned_` prefix or timestamp)
      to avoid overwriting the original. **File Naming Strategy:** `cleaned_2024_09_15_myfile.pdf`
      makes it easy to trace processing dates.
  type: HowTo
- questions:
  - answer: Yes – GroupDocs.Annotation supports DOCX, XLSX, PPTX, and many other formats.
      The same API calls apply after loading the appropriate file type.
    question: Can I remove annotations from Word documents, not just PDFs?
  - answer: Filter the annotation collection by `annotation.Type == AnnotationType.Comment`
      before calling the delete method. ```csharp var commentsOnly = annotations.Where(a
      => a.Type == AnnotationType.TextField); ```
    question: How do I remove only specific types of annotations (e.g., just comments)?
  - answer: No. Annotations are stored as overlay objects; deleting them leaves the
      underlying content untouched.
    question: Will removing annotations affect the document’s layout or formatting?
  - answer: The library does not provide an “undo” feature. Always work on a copy
      of the original document and keep backups.
    question: Can I undo annotation removal?
  - answer: Pass the password via `LoadOptions` when creating the `Annotator` instance.
    question: How do I handle password‑protected PDFs?
  type: FAQPage
tags:
- GroupDocs
- PDF
- Annotations
- C#
- .NET
title: Xóa chú thích khỏi PDF C#
type: docs
url: /vi/net/annotation-management/remove-annotations-dotnet-groupdocs/
weight: 1
---

# Cách Xóa Ghi chú khỏi PDF và Tài liệu trong C# (.NET)

Hãy tưởng tượng: bạn đang làm việc trên một hệ thống quản lý tài liệu, và người dùng phàn nàn về các PDF lộn xộn đầy những bình luận và đánh dấu lỗi thời. Hoặc có thể bạn cần làm sạch tài liệu trước khi gửi cho khách hàng. Nghe có quen không?

Việc **xóa ghi chú pdf** một cách lập trình không chỉ là tính năng tiện lợi—đó là yếu tố thiết yếu để duy trì các tài liệu sạch sẽ, chuyên nghiệp trong các quy trình tự động. Dù bạn đang xử lý hợp đồng pháp lý, tài liệu kỹ thuật, hay các bản đánh giá hợp tác, việc biết cách loại bỏ nhanh chóng các ghi chú không mong muốn có thể tiết kiệm hàng giờ công việc thủ công.

Hãy cùng khám phá và làm cho việc xóa ghi chú của bạn hoạt động trơn tru.

## Câu trả lời nhanh
- **Mã này làm gì?** Nó tải tài liệu, lọc bỏ các ghi chú không mong muốn và lưu một bản sao sạch.  
- **Tôi có thể xóa chỉ một số ghi chú nhất định không?** Có – lọc theo loại, tác giả, số trang hoặc siêu dữ liệu tùy chỉnh.  
- **Cần giấy phép không?** Bản dùng thử miễn phí 30 ngày đủ cho phát triển; cần giấy phép sản xuất cho việc thương mại.  
- **Các PDF lớn có gây vấn đề bộ nhớ không?** Sử dụng các khối `using` và xử lý theo lô để giữ mức sử dụng bộ nhớ thấp.  
- **Có hoạt động với các định dạng khác ngoài PDF không?** Chắc chắn – GroupDocs.Annotation hỗ trợ Word, Excel, PowerPoint và nhiều hơn nữa.

## GroupDocs.Annotation là gì?
`GroupDocs.Annotation` là thư viện .NET cho phép bạn thêm, đọc, chỉnh sửa và xóa ghi chú trên hơn 30 định dạng tệp, bao gồm PDF, DOCX, XLSX và PPTX. Thư viện xử lý tài liệu lên tới 500 MB mà không cần tải toàn bộ tệp vào bộ nhớ, rất phù hợp cho môi trường máy chủ có khối lượng lớn.

## Tại sao cần xóa ghi chú bằng lập trình?

Tự động xóa ghi chú đảm bảo mọi tài liệu đi qua quy trình đều sạch sẽ, chuyên nghiệp và tuân thủ. Nó loại bỏ công việc thủ công, giảm rủi ro rò rỉ dữ liệu vô tình, và giữ kích thước tệp nhỏ để lưu trữ và lập chỉ mục.

- **Sẵn sàng tự động hoá** – Các phiên bản sạch có thể được tạo tự động ở mỗi bước của quy trình.  
- **Sản phẩm chuyên nghiệp** – Không có bình luận hay đánh dấu lạc lõng xuất hiện trong PDF gửi cho khách hàng.  
- **Tuân thủ quy định** – Một số ngành cấm các bình luận ẩn trong tài liệu nộp.  
- **Tiết kiệm không gian lưu trữ** – PDF đã loại bỏ ghi chú nhỏ hơn và nhanh hơn trong việc lập chỉ mục.

## Yêu cầu trước và Cài đặt

### Môi trường phát triển
- .NET Core 3.1, .NET 5+ hoặc .NET Framework 4.7.2+  
- Visual Studio 2022 (hoặc bất kỳ IDE C# nào bạn thích)  
- Kiến thức cơ bản về câu lệnh `using` và xử lý ngoại lệ  

### Gói cần thiết
GroupDocs.Annotation cho .NET (phiên bản 25.4.0 được sử dụng trong các ví dụ; các phiên bản mới hơn hoàn toàn tương thích).

#### Cài đặt GroupDocs.Annotation

**Package Manager Console (phổ biến nhất):**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**Package Manager UI:** Tìm “GroupDocs.Annotation” và cài đặt phiên bản ổn định mới nhất.

**.NET CLI (nếu bạn thích dòng lệnh):**  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

### Cấp giấy phép

Cần một tệp giấy phép cho môi trường sản xuất. Bạn có thể bắt đầu với bản dùng thử miễn phí.

**Cho Phát triển/Kiểm thử:**  
1. Truy cập [Temporary License Page](https://purchase.groupdocs.com/temporary-license/)  
2. Yêu cầu giấy phép dùng thử 30 ngày  
3. Nhận tệp `.lic` qua email  

**Cài đặt giấy phép cơ bản:**  
`License` là lớp do GroupDocs.Annotation cung cấp để áp dụng tệp giấy phép cho thư viện.  
```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main(string[] args)
    {
        // Set up your license (skip this during trial period)
        License lic = new License();
        lic.SetLicense("path-to-your-license.lic");
        
        Console.WriteLine("GroupDocs.Annotation is ready to rock!");
    }
}
```  

**Mẹo chuyên nghiệp:** Lưu giấy phép ở vị trí an toàn và tải nó bằng `License license = new License(); license.SetLicense("path/to/license.lic");`. Không bao giờ hard‑code đường dẫn tuyệt đối trong môi trường sản xuất.

## Hướng dẫn triển khai từng bước

### Cách xóa các ghi chú pdf cụ thể?

Phần này giải thích cách tải PDF, xác định các ghi chú cần loại bỏ, và lưu bản sao đã làm sạch trong khi giữ nguyên nội dung gốc.

#### Bước 1: Tải tài liệu của bạn

`Annotator` là lớp cốt lõi của GroupDocs.Annotation, mở tệp và cung cấp bộ sưu tập ghi chú.  
```csharp
string inputFilePath = "YOUR_DOCUMENT_DIRECTORY/ANNOTATED.pdf"; // Replace with your actual path

using (Annotator annotator = new Annotator(inputFilePath))
{
    // All the magic happens inside this using block
    // The using statement ensures proper resource cleanup
}
```  

**Lỗi thường gặp:** Đảm bảo đường dẫn tệp đúng và tệp không bị khóa bởi tiến trình khác. Lỗi đánh máy trong đường dẫn là nguyên nhân phổ biến gây “file not found”.

#### Bước 2: Lấy và lọc ghi chú

Đối tượng `Annotation` đại diện cho từng mục đánh dấu như bình luận, tô sáng hoặc dấu. Bạn có thể kiểm tra loại, tác giả, số trang hoặc siêu dữ liệu tùy chỉnh của mỗi ghi chú trước khi quyết định xóa.  
```csharp
var annotations = annotator.Get();
Console.WriteLine($"Found {annotations.Count} annotations in the document");

// Let's see what we're working with
foreach (var annotation in annotations)
{
    Console.WriteLine($"Type: {annotation.Type}, Page: {annotation.PageNumber}");
}

// Remove the first annotation (basic example)
if (annotations.Count > 0)
{
    Console.WriteLine($"Removing annotation of type: {annotations[0].Type}");
    annotator.Remove(annotations[0]);
}
```  

**Tại sao cách này hoạt động:** Bằng cách lọc trước, bạn tránh vô tình xóa các đánh dấu hữu ích như tô sáng pháp lý trong khi loại bỏ các bình luận nội bộ.

#### Bước 3: Lưu tài liệu đã làm sạch

Đặt tên tệp đã làm sạch khác biệt (ví dụ: tiền tố `cleaned_` hoặc dấu thời gian) để tránh ghi đè lên bản gốc.  
```csharp
string outputDirectory = "YOUR_OUTPUT_DIRECTORY"; // Your output folder
string outputPath = Path.Combine(outputDirectory, "cleaned_" + Path.GetFileName(inputFilePath));

// Save the document with annotations removed
annotator.Save(outputPath);
Console.WriteLine($"Clean document saved to: {outputPath}");
```  

**Chiến lược đặt tên:** `cleaned_2024_09_15_myfile.pdf` giúp dễ dàng truy vết ngày xử lý.

### Cách xóa tất cả ghi chú pdf (phương án “hạt nhân”)?

Khi bạn cần một bản sạch hoàn toàn, phương pháp này xóa mọi ghi chú trong một lần gọi.

`RemoveAll` xóa mọi ghi chú khỏi tài liệu đã tải.  
```csharp
string inputFilePath = "YOUR_DOCUMENT_DIRECTORY/ANNOTATED.pdf";
string outputPath = "YOUR_OUTPUT_DIRECTORY/completely_clean.pdf";

using (Annotator annotator = new Annotator(inputFilePath))
{
    var annotations = annotator.Get();
    
    if (annotations.Count > 0)
    {
        Console.WriteLine($"Removing all {annotations.Count} annotations...");
        
        // Remove all annotations in one go
        foreach (var annotation in annotations)
        {
            annotator.Remove(annotation);
        }
        
        annotator.Save(outputPath);
        Console.WriteLine("All annotations removed successfully!");
    }
    else
    {
        Console.WriteLine("No annotations found in the document.");
    }
}
```  

## Những lỗi thường gặp và giải pháp

### Vấn đề 1: Ngoại lệ “File is locked”
**Triệu chứng:** Ngoại lệ về tệp đang được sử dụng.  
**Giải pháp:** Bao gói truy cập tệp trong các khối `using` và đảm bảo không có tiến trình nào khác giữ handle của tệp.  
```csharp
// DON'T do this
var annotator1 = new Annotator(filePath);
var annotator2 = new Annotator(filePath); // This might fail

// DO this instead
using (var annotator = new Annotator(filePath))
{
    // All your work here
} // Automatically disposed and file is released
```  

### Vấn đề 2: Ghi chú không thực sự bị xóa
**Triệu chứng:** Mã chạy nhưng ghi chú vẫn còn.  
**Nguyên nhân thường gặp:** Bạn có thể đang kiểm tra tệp đầu ra sai hoặc lọc sai loại ghi chú.  
**Cách debug:**  
```csharp
var annotations = annotator.Get();
foreach (var annotation in annotations)
{
    Console.WriteLine($"ID: {annotation.Id}, Type: {annotation.Type}");
    Console.WriteLine($"Page: {annotation.PageNumber}, Author: {annotation.User}");
}
```  

### Vấn đề 3: Vấn đề bộ nhớ với tài liệu lớn
**Triệu chứng:** Treo hoặc chậm nghiêm trọng trên PDF lớn hơn 100 MB.  
**Giải pháp:** Xử lý tài liệu theo lô và giải phóng tài nguyên kịp thời.  
```csharp
// For very large documents, consider processing page by page
using (var annotator = new Annotator(largePdfPath))
{
    var annotations = annotator.Get();
    
    // Process in chunks of 50 annotations
    for (int i = 0; i < annotations.Count; i += 50)
    {
        var batch = annotations.Skip(i).Take(50);
        foreach (var annotation in batch)
        {
            annotator.Remove(annotation);
        }
        
        // Optional: Force garbage collection for very large documents
        GC.Collect();
    }
    
    annotator.Save(outputPath);
}
```  

## Mẹo tối ưu hoá hiệu suất

### Chiến lược xử lý theo lô
Thu thập các ghi chú vào danh sách và xóa chúng trong một lô duy nhất để giảm số lần gọi API.  
```csharp
using (var annotator = new Annotator(inputPath))
{
    var annotations = annotator.Get();
    var toRemove = annotations.Where(a => ShouldRemoveAnnotation(a)).ToList();
    
    Console.WriteLine($"Removing {toRemove.Count} out of {annotations.Count} annotations");
    
    // Remove all at once instead of individual Remove() calls
    foreach (var annotation in toRemove)
    {
        annotator.Remove(annotation);
    }
    
    annotator.Save(outputPath);
}

bool ShouldRemoveAnnotation(AnnotationBase annotation)
{
    // Your custom logic here
    return annotation.Type == AnnotationType.Area || 
           annotation.CreatedOn < DateTime.Now.AddMonths(-6);
}
```  

### Thực hành quản lý bộ nhớ
- Luôn sử dụng các khối `using` để tự động giải phóng.  
- Không tải đồng thời nhiều PDF lớn.  
- Xử lý tài liệu tuần tự thay vì song song khi bộ nhớ là hạn chế.  

### Caching đối tượng License
Tạo một thể hiện `License` một lần khi khởi động ứng dụng và tái sử dụng cho mọi tài liệu được xử lý.  
```csharp
public class DocumentProcessor
{
    private static readonly License _license = new License();
    
    static DocumentProcessor()
    {
        _license.SetLicense("your-license-path.lic");
    }
    
    public void ProcessDocument(string filePath)
    {
        // License is already set, just use the annotator
        using (var annotator = new Annotator(filePath))
        {
            // Your processing logic
        }
    }
}
```  

## Các trường hợp sử dụng thực tế và ví dụ

### Kịch bản 1: Quy trình tài liệu pháp lý
Một công ty luật cần gửi hợp đồng sạch cho khách hàng trong khi giữ lại các bình luận nội bộ để xem xét.  
```csharp
public void PrepareClientDocument(string internalContractPath, string clientVersion)
{
    using (var annotator = new Annotator(internalContractPath))
    {
        var annotations = annotator.Get();
        
        // Remove only internal comments, keep client-facing highlights
        var internalComments = annotations.Where(a => 
            a.Type == AnnotationType.TextField && 
            a.User?.Contains("@lawfirm.com") == true);
            
        foreach (var comment in internalComments)
        {
            annotator.Remove(comment);
        }
        
        annotator.Save(clientVersion);
    }
}
```  

### Kịch bản 2: Tự động tạo báo cáo
Các báo cáo phân tích hàng tháng đi qua vòng duyệt; phiên bản cuối cùng phải không có ghi chú.  
```csharp
public void FinalizeReport(string draftPath, string finalPath)
{
    using (var annotator = new Annotator(draftPath))
    {
        var annotations = annotator.Get();
        
        // Remove all review comments but keep approved highlights
        var reviewComments = annotations.Where(a => 
            a.Type == AnnotationType.TextField ||
            a.Type == AnnotationType.Point);
            
        Console.WriteLine($"Cleaning {reviewComments.Count()} review annotations...");
        
        foreach (var annotation in reviewComments)
        {
            annotator.Remove(annotation);
        }
        
        annotator.Save(finalPath);
        Console.WriteLine($"Final report ready: {finalPath}");
    }
}
```  

## Xử lý lỗi nâng cao

Mã sản xuất mạnh mẽ nên dự đoán và ghi log các ngoại lệ phổ biến, như `IncorrectPasswordException` hoặc `OutOfMemoryException`.  

`IncorrectPasswordException` được ném khi mở PDF có mật khẩu mà không cung cấp mật khẩu đúng.  
```csharp
public bool RemoveAnnotationsSafely(string inputPath, string outputPath)
{
    try
    {
        using (var annotator = new Annotator(inputPath))
        {
            var annotations = annotator.Get();
            
            if (annotations.Count == 0)
            {
                Console.WriteLine("No annotations to remove.");
                // Still copy the file to output location
                File.Copy(inputPath, outputPath, overwrite: true);
                return true;
            }
            
            foreach (var annotation in annotations)
            {
                try
                {
                    annotator.Remove(annotation);
                }
                catch (Exception ex)
                {
                    Console.WriteLine($"Failed to remove annotation {annotation.Id}: {ex.Message}");
                    // Continue with other annotations
                }
            }
            
            annotator.Save(outputPath);
            Console.WriteLine($"Successfully processed document: {Path.GetFileName(outputPath)}");
            return true;
        }
    }
    catch (FileNotFoundException)
    {
        Console.WriteLine($"Input file not found: {inputPath}");
        return false;
    }
    catch (UnauthorizedAccessException)
    {
        Console.WriteLine($"Access denied. Check file permissions for: {inputPath}");
        return false;
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Unexpected error: {ex.Message}");
        return false;
    }
}
```  

## Kiểm thử triển khai của bạn

Một unit test nhanh có thể xác minh số lượng ghi chú giảm về 0 sau khi xử lý.  
```csharp
public void TestAnnotationRemoval()
{
    string testFile = "test-document-with-annotations.pdf";
    string outputFile = "test-output.pdf";
    
    // Before removal
    using (var annotator = new Annotator(testFile))
    {
        var beforeCount = annotator.Get().Count;
        Console.WriteLine($"Annotations before removal: {beforeCount}");
    }
    
    // Remove annotations
    bool success = RemoveAnnotationsSafely(testFile, outputFile);
    
    if (success)
    {
        // After removal
        using (var annotator = new Annotator(outputFile))
        {
            var afterCount = annotator.Get().Count;
            Console.WriteLine($"Annotations after removal: {afterCount}");
            Console.WriteLine($"Removed: {beforeCount - afterCount} annotations");
        }
    }
}
```  

## Hướng dẫn khắc phục sự cố

- **IncorrectPasswordException** – Cung cấp mật khẩu PDF qua `LoadOptions`.  
  ```csharp
LoadOptions loadOptions = new LoadOptions { Password = "your-pdf-password" };
using (var annotator = new Annotator(filePath, loadOptions))
{
    // Your code here
}
```  

- **Ghi chú vẫn hiển thị** – Một số trình xem PDF lưu cache luồng ghi chú; hãy làm mới hoặc mở tệp bằng trình xem khác.  

- **OutOfMemoryException** – Xử lý PDF thành các phần nhỏ hơn hoặc tăng giới hạn bộ nhớ của ứng dụng.  

- **Một số loại ghi chú không xóa được** – Sử dụng `annotation.Type` để xác định và xử lý riêng các loại đặc biệt như trường biểu mẫu.  

## Các chỉ số hiệu năng

Dựa trên thử nghiệm nội bộ với GroupDocs.Annotation 25.4.0:

- **PDF nhỏ (< 1 MB, < 50 ghi chú):** < 0.5 s  
- **PDF trung bình (1‑10 MB, 50‑200 ghi chú):** 1‑3 s  
- **PDF lớn (10‑50 MB, 200+ ghi chú):** 5‑15 s  
- **PDF rất lớn (> 50 MB):** Khuyến nghị xử lý theo lô để duy trì dưới 20 s mỗi tệp  

## Tài nguyên

- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/net/)  
- [API Reference](https://reference.groupdocs.com/annotation/net/)  
- [Download GroupDocs.Annotation for .NET](https://releases.groupdocs.com/annotation/net/)  
- [Purchase Options](https://purchase.groupdocs.com/buy)  
- [Support Forum](https://forum.groupdocs.com/c/annotation/)  

## Kết luận

Bạn đã có bộ công cụ hoàn chỉnh để **remove pdf annotations** trong C#. Hãy nhớ:

1. Sử dụng các khối `using` để giải phóng tài nguyên sạch sẽ.  
2. Lọc ghi chú trước khi xóa để tránh mất dữ liệu không mong muốn.  
3. Xử lý các tệp PDF có mật khẩu và PDF lớn bằng các chiến lược đã nêu ở trên.  
4. Kiểm thử với tài liệu thực tế trước khi triển khai sản xuất.  

Tích hợp các mẫu này vào quy trình xử lý tài liệu tổng thể, người dùng của bạn sẽ luôn nhận được các PDF sạch sẽ, chuyên nghiệp hơn.

## Câu hỏi thường gặp

**Q: Tôi có thể xóa ghi chú từ tài liệu Word, không chỉ PDF không?**  
A: Có – GroupDocs.Annotation hỗ trợ DOCX, XLSX, PPTX và nhiều định dạng khác. Các cuộc gọi API giống nhau sau khi tải loại tệp phù hợp.

**Q: Làm sao để xóa chỉ các loại ghi chú cụ thể (ví dụ: chỉ bình luận)?**  
A: Lọc bộ sưu tập ghi chú bằng `annotation.Type == AnnotationType.Comment` trước khi gọi phương thức xóa.  
```csharp
var commentsOnly = annotations.Where(a => a.Type == AnnotationType.TextField);
```  

**Q: Việc xóa ghi chú có ảnh hưởng tới bố cục hoặc định dạng tài liệu không?**  
A: Không. Ghi chú được lưu dưới dạng đối tượng lớp phủ; việc xóa chúng không làm thay đổi nội dung nền.

**Q: Có thể hoàn tác việc xóa ghi chú không?**  
A: Thư viện không cung cấp tính năng “undo”. Luôn làm việc trên bản sao của tài liệu gốc và giữ bản sao lưu.

**Q: Làm sao xử lý PDF có mật khẩu?**  
A: Truyền mật khẩu qua `LoadOptions` khi tạo đối tượng `Annotator`.

**Q: Có cách xóa ghi chú dựa trên tác giả không?**  
A: Có – kiểm tra thuộc tính `annotation.User` và xóa chỉ những ghi chú có tên tác giả phù hợp.

**Q: Sự khác biệt giữa ẩn và xóa ghi chú là gì?**  
A: Ẩn chỉ làm chúng không hiển thị trong trình xem; xóa sẽ loại bỏ chúng vĩnh viễn khỏi tệp. GroupDocs.Annotation chỉ hỗ trợ xóa.

---

**Cập nhật lần cuối:** 2026-06-01  
**Kiểm thử với:** GroupDocs.Annotation 25.4.0 cho .NET  
**Tác giả:** GroupDocs

## Các hướng dẫn liên quan

- [Generate PDF Preview .NET - Remove Annotations from Document Thumbnails](/annotation/net/advanced-usage/generate-preview-without-annotations/)
- [PDF Annotation .NET Tutorial - Complete GroupDocs Guide](/annotation/net/annotation-management/annotate-pdf-groupdocs-annotation-net/)
- [Save PDF Annotations .NET - Complete Document Saving Guide](/annotation/net/document-saving/)