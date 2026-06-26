---
categories:
- .NET Development
date: '2026-06-26'
description: Tìm hiểu cách lấy các định dạng với GroupDocs.Annotation cho .NET, khắc
  phục các vấn đề về định dạng tệp không được hỗ trợ, và áp dụng kiểm tra thực tiễn
  tốt nhất.
keywords:
- how to retrieve formats
- troubleshoot unsupported file format
- GroupDocs.Annotation .NET
lastmod: '2026-06-26'
linktitle: Lấy các định dạng tệp được hỗ trợ .NET
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  headline: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete
    Guide
  type: TechArticle
- description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  name: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete Guide
  steps:
  - name: Verify installation
    text: Run `dotnet list package` or check the NuGet console output for any warnings.
  - name: Check license status
    text: Ensure `License.SetLicense("path/to/license.json")` executes before any
      API call.
  - name: Diagnose environment constraints
    text: '- Confirm .NET runtime version matches the library’s requirements. - Verify
      the process has read/write permissions for the temporary folder used by GroupDocs.Annotation.'
  type: HowTo
- questions:
  - answer: The library supports **over 50 formats**, including PDF, DOCX, XLSX, PPTX,
      JPEG, PNG, TIFF, and many others. Run the sample code to retrieve the exact
      list for your license.
    question: What file formats does GroupDocs.Annotation actually support?
  - answer: This usually points to a licensing issue—either an expired trial or an
      incorrectly loaded license file. Re‑apply a valid license and restart the app.
    question: Why am I getting fewer supported formats than expected?
  - answer: No direct “IsSupported” method exists; the recommended approach is to
      cache the full list once and query it locally for fast lookups.
    question: Can I check a single format without pulling the whole list?
  - answer: Initialise the format cache at application startup (e.g., in `ConfigureServices`)
      and store it in a static or singleton service. This eliminates per‑request overhead.
    question: How should I handle format checking in a high‑traffic web app?
  - answer: Exceptions typically stem from licensing or corrupted installations. Verify
      the package integrity, re‑install if needed, and ensure the license file is
      accessible.
    question: What if GetSupportedFileTypes() throws an exception?
  type: FAQPage
tags:
- GroupDocs.Annotation
- file-formats
- document-processing
- dotnet-tutorial
title: Cách lấy các định dạng trong .NET bằng GroupDocs.Annotation – Hướng dẫn đầy
  đủ
type: docs
url: /vi/net/document-information/retrieve-supported-file-formats-groupdocs-annotation-net/
weight: 1
---

# Cách lấy các định dạng trong .NET bằng GroupDocs.Annotation

## Giới thiệu

Bạn đã bao giờ tự hỏi những định dạng tệp nào ứng dụng .NET của bạn thực sự có thể xử lý cho việc chú thích tài liệu? **How to retrieve formats** là câu hỏi mà nhiều nhà phát triển đặt ra khi họ cần xác thực tải lên của người dùng hoặc xây dựng bộ lọc UI động. Biết chính xác những định dạng tệp nào mà triển khai GroupDocs.Annotation của bạn hỗ trợ không chỉ hữu ích—mà còn thiết yếu để xây dựng các ứng dụng vững chắc không bị crash vì một loại tệp không mong đợi.

Trong hướng dẫn này bạn sẽ học cách lập trình để lấy và xác thực các định dạng tệp được hỗ trợ bằng GroupDocs.Annotation cho .NET. Chúng tôi sẽ hướng dẫn qua triển khai cơ bản, chỉ cho bạn cách chuyển danh sách thô thành một dropdown sạch sẽ cho người dùng cuối, và cung cấp các mẹo khắc phục sự cố thực tế để bạn có thể xử lý bất kỳ kịch bản định dạng tài liệu nào một cách tự tin.

**Bạn sẽ nhận được**

- Hiểu biết rõ ràng về khả năng định dạng tệp của GroupDocs.Annotation  
- Mã sẵn sàng chạy để lấy và hiển thị mọi định dạng được hỗ trợ  
- Chiến lược đã được chứng minh cho việc cache, xử lý lỗi và các trường hợp đặc biệt về giấy phép  
- Khuyến nghị thực tiễn tốt nhất cho việc xác thực loại tệp ở môi trường production  

Hãy bắt đầu và giải quyết câu đố định dạng tệp này một lần và mãi mãi.

## Câu trả lời nhanh
- **Câu hỏi “how to retrieve formats” có nghĩa là gì?** Đó là cách lập trình để hỏi GroupDocs.Annotation những phần mở rộng nào nó có thể chú thích.  
- **Các định dạng chính nào được hỗ trợ mặc định?** Hơn 50, bao gồm PDF, DOCX, XLSX, PPTX, JPEG, PNG và TIFF.  
- **Tôi có cần giấy phép để nhận danh sách đầy đủ không?** Có—một giấy phép thương mại hoặc dùng thử đang hoạt động sẽ mở khóa toàn bộ danh mục.  
- **Có nên cache danh sách định dạng không?** Chắc chắn; cache giúp tránh các cuộc gọi không cần thiết và cải thiện thời gian phản hồi.  
- **Làm sao tôi có thể xác thực một tải lên so với danh sách?** So sánh phần mở rộng của tệp với bộ sưu tập các phần mở rộng được hỗ trợ đã được cache.

## “how to retrieve formats” là gì?
**How to retrieve formats** đề cập đến quá trình gọi API của GroupDocs.Annotation để lấy một bộ sưu tập tất cả các loại tệp mà thư viện có thể chú thích. Thao tác này trả về một danh sách chỉ‑đọc các đối tượng `FileType` bao gồm cả phần mở rộng tệp và mô tả thân thiện.

## Tại sao sử dụng GroupDocs.Annotation để phát hiện định dạng?
GroupDocs.Annotation hỗ trợ **hơn 50 định dạng đầu vào và đầu ra**—bao gồm PDF, Microsoft Office (Word, Excel, PowerPoint), và các loại ảnh phổ biến—trong khi xử lý tài liệu hàng trăm trang mà không cần tải toàn bộ tệp vào bộ nhớ. Khả năng định lượng này khiến nó trở thành lựa chọn đáng tin cậy cho các pipeline chú thích quy mô doanh nghiệp.

## Yêu cầu trước và Cấu hình môi trường

### Những gì bạn cần
- **IDE:** Visual Studio 2019 hoặc mới hơn (bản Community hoạt động tốt)  
- **Framework mục tiêu:** .NET Framework 4.6.1+ hoặc .NET Core 2.0+  
- **C# cơ bản:** Nếu bạn có thể viết một ứng dụng “Hello World”, bạn đã sẵn sàng  

### Cài đặt GroupDocs.Annotation
Cách đơn giản nhất là qua NuGet. Chọn phương pháp phù hợp với quy trình làm việc của bạn:

**Tùy chọn 1: Package Manager Console**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**Tùy chọn 2: .NET CLI**  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

**Mẹo:** Trong môi trường doanh nghiệp hạn chế, tải gói thủ công từ [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/) và tham chiếu DLL cục bộ.

### Cấp phép đơn giản
- **Phát triển & thử nghiệm:** Bắt đầu với bản dùng thử miễn phí để có đầy đủ chức năng.  
- **Đánh giá mở rộng:** Lấy một [temporary license](https://purchase.groupdocs.com/temporary-license/) (cấp trong khoảng 5 phút).  
- **Sản xuất:** Mua giấy phép thương mại từ [GroupDocs Purchase](https://purchase.groupdocs.com/buy); một giấy phép bao phủ mọi kịch bản triển khai.

## Cách lấy các định dạng tệp được hỗ trợ bằng lập trình?

Tải các định dạng được hỗ trợ bằng một lời gọi duy nhất tới `FileType.GetSupportedFileTypes()` và sau đó chuyển đổi kết quả thành một danh sách thân thiện với người dùng có thể hiển thị trong các điều khiển UI hoặc dùng để xác thực. Phương thức này trả về một bộ sưu tập chỉ‑đọc các đối tượng `FileType`, mỗi đối tượng chứa phần mở rộng và mô tả, giúp việc xử lý trở nên dễ dàng.

```csharp
var supported = FileType.GetSupportedFileTypes()
                         .OrderBy(f => f.Extension)
                         .Select(f => new { f.Extension, f.Description })
                         .ToList();
```

Mã trên truy vấn siêu dữ liệu nội bộ của GroupDocs.Annotation, sắp xếp các phần mở rộng theo thứ tự bảng chữ cái, và trả về một bộ sưu tập nhẹ mà bạn có thể bind vào các điều khiển UI hoặc dùng để xác thực.

### Định nghĩa: lớp FileType
Lớp `FileType` là cách GroupDocs.Annotation biểu diễn một định dạng tài liệu duy nhất, cung cấp các thuộc tính như `Extension` và `Description`.  

### Hướng dẫn từng bước
1. **Thêm namespace** – `using GroupDocs.Annotation;` ở đầu file của bạn.  
2. **Gọi phương thức tĩnh** – `FileType.GetSupportedFileTypes()` trả về một `IEnumerable<FileType>`.  
3. **Sắp xếp và chuyển đổi** – Sử dụng `OrderBy` và `Select` của LINQ để định dạng dữ liệu cho hiển thị.  
4. **Hiển thị** – Lặp qua danh sách trong console, view MVC, hoặc dropdown WinForms.

```csharp
using System;
using System.Linq;
using GroupDocs.Annotation; // This is where the FileType class lives
```  

## Cách cache danh sách định dạng cho môi trường production?

Cache loại bỏ các lần tra cứu siêu dữ liệu lặp lại và đảm bảo thời gian phản hồi dưới một mili giây cho mỗi yêu cầu, điều này quan trọng trong các ứng dụng có lưu lượng cao. Bằng cách lưu danh sách định dạng trong một trường tĩnh và tải nó một cách lười biếng khi lần đầu sử dụng, bạn đảm bảo dữ liệu chỉ được lấy một lần và sau đó được tái sử dụng hiệu quả trong suốt vòng đời ứng dụng.

```csharp
public static class FormatCache
{
    private static IReadOnlyList<FileType> _cachedFormats;

    public static IReadOnlyList<FileType> SupportedFormats =>
        _cachedFormats ??= FileType.GetSupportedFileTypes()
                                    .OrderBy(f => f.Extension)
                                    .ToList();
}
```

```csharp
public static void RunGetSupportedFileFormats()
{
    // Retrieve collection of supported file types, ordered by their extension
    IEnumerable<FileType> fileTypes = FileType.GetSupportedFileTypes().OrderBy(fileType => fileType.Extension);

    // Iterate through each FileType object and output its details to the console
    foreach (FileType fileType in fileTypes)
        Console.WriteLine($"{fileType.Extension} - {fileType.Name}");
}
```  

**Tại sao cần cache?** Bộ định dạng được hỗ trợ không bao giờ thay đổi trong thời gian chạy, vì vậy việc tải một lần khi khởi động ứng dụng giúp tiết kiệm chu kỳ CPU và tránh các kiểm tra giấy phép tiềm năng ở mỗi lần gọi.

## Các vấn đề thường gặp và giải pháp

### Vấn đề 1: Lỗi biên dịch “GroupDocs.Annotation not found”
**Câu trả lời trực tiếp:** Kiểm tra gói NuGet đã được cài đặt đúng, làm sạch và xây dựng lại solution, và đảm bảo framework mục tiêu của bạn khớp với các phiên bản được hỗ trợ của gói.  

**Phân tích nguyên nhân** – Thiếu tham chiếu, framework không tương thích, hoặc hạn chế nguồn gói trong công ty.

### Vấn đề 2: Danh sách định dạng rỗng hoặc không đầy đủ
**Câu trả lời trực tiếp:** Giấy phép hết hạn hoặc cấu hình sai thường cắt ngắn danh sách; áp dụng lại file giấy phép hợp lệ và khởi động lại ứng dụng.  

**Nguyên nhân có thể:**  
- File giấy phép chưa được tải (`License.SetLicense("license.json")` thiếu)  
- Gói NuGet bị hỏng  
- Thiếu các phụ thuộc native  

**Cách khắc phục nhanh:**  
```csharp
public static void DiagnoseFormatIssues()
{
    try
    {
        var formats = FileType.GetSupportedFileTypes();
        Console.WriteLine($"Found {formats.Count()} supported formats");
        
        if (formats.Count() < 10) // GroupDocs supports many more formats
        {
            Console.WriteLine("Warning: Fewer formats than expected. Check your license.");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Cannot retrieve formats: {ex.Message}");
        // This usually indicates a licensing or installation issue
    }
}
```  

### Vấn đề 3: Giảm hiệu năng do gọi thường xuyên
**Câu trả lời trực tiếp:** Cache kết quả như đã mô tả trong phần “How to cache”; các lần gọi tiếp theo trở thành O(1).  

**Mẹo triển khai:** Lưu danh sách trong `MemoryCache` hoặc trường tĩnh, và chỉ làm mới khi bạn nâng cấp thư viện.

```csharp
public static class FileFormatCache
{
    private static List<FileType> _cachedFormats;
    
    public static IEnumerable<FileType> GetSupportedFormats()
    {
        if (_cachedFormats == null)
        {
            _cachedFormats = FileType.GetSupportedFileTypes().ToList();
        }
        return _cachedFormats;
    }
}
```  

## Ứng dụng thực tế và các trường hợp sử dụng

### Cách xác thực tải lên tệp bằng danh sách đã cache?
Khi người dùng gửi tài liệu, trích xuất phần mở rộng tệp và so sánh với bộ sưu tập đã cache:

```csharp
bool IsSupported(string fileName)
{
    var ext = Path.GetExtension(fileName).ToLowerInvariant();
    return FormatCache.SupportedFormats.Any(f => f.Extension.Equals(ext, StringComparison.OrdinalIgnoreCase));
}
```

```csharp
public bool IsFileSupported(string fileName)
{
    var extension = Path.GetExtension(fileName).ToLowerInvariant();
    var supportedExtensions = GetSupportedExtensions();
    return supportedExtensions.Contains(extension);
}
```  

### Cách tạo bộ lọc tệp động cho OpenFileDialog?
Điền chuỗi filter của dialog từ các phần mở rộng đã cache, đảm bảo UI luôn phản ánh khả năng của thư viện:

```csharp
var filter = string.Join(";", FormatCache.SupportedFormats.Select(f => $"*{f.Extension}"));
openFileDialog.Filter = $"Supported Files ({filter})|{filter}";
```

```csharp
public string GenerateFileFilter()
{
    var extensions = GetSupportedExtensions();
    var filterParts = extensions.Select(ext => $"*{ext}");
    return $"Supported Documents|{string.Join(";", filterParts)}";
}
```  

### Cách bỏ qua các tệp không được hỗ trợ trong quét thư mục hàng loạt?
Duyệt qua một thư mục, kiểm tra mỗi tệp bằng `IsSupported`, và chỉ xử lý những tệp hợp lệ:

```csharp
foreach (var file in Directory.EnumerateFiles(folderPath))
{
    if (IsSupported(file))
    {
        // Process with GroupDocs.Annotation
    }
}
```

```csharp
public void ProcessDirectory(string directoryPath)
{
    var supportedExtensions = GetSupportedExtensions();
    var files = Directory.GetFiles(directoryPath)
        .Where(file => supportedExtensions.Contains(Path.GetExtension(file).ToLowerInvariant()));
    
    foreach (var file in files)
    {
        // Process each supported file
        ProcessAnnotationFile(file);
    }
}
```  

## Các cân nhắc về hiệu năng và thực tiễn tốt nhất

- **Cache một lần, tái sử dụng mọi nơi** – Khởi tạo `FormatCache` khi khởi động ứng dụng (ví dụ, trong `Program.cs` hoặc `Startup.cs`).  
- **Lazy loading** – Thuộc tính tĩnh đảm bảo danh sách chỉ được tải khi cần lần đầu, tránh tải khởi động không cần thiết.  
- **An toàn đa luồng** – Toán tử null‑coalescing (`??=`) an toàn cho hầu hết các kịch bản đơn luồng; đối với ứng dụng có độ đồng thời cao, bọc cache trong `Lazy<IReadOnlyList<FileType>>`.  
- **Giải phóng đối tượng annotation** – Mặc dù danh sách định dạng không cần giải phóng, bất kỳ instance `Annotation` nào bạn tạo nên được bọc trong câu lệnh `using` để giải phóng tài nguyên native.  

### Mẫu xử lý lỗi cho các vấn đề giấy phép
Bọc việc lấy danh sách định dạng trong khối try‑catch đặc biệt kiểm tra `LicenseException` và ghi lại thông báo rõ ràng:

```csharp
try
{
    var formats = FileType.GetSupportedFileTypes();
}
catch (LicenseException ex)
{
    // Log and fallback to a hard‑coded minimal list
}
```

```csharp
public static class RobustFormatRetrieval
{
    public static IEnumerable<FileType> GetSupportedFormatsWithFallback()
    {
        try
        {
            return FileType.GetSupportedFileTypes();
        }
        catch (LicenseException)
        {
            // Handle licensing issues gracefully
            LogWarning("License issue detected. Using basic format list.");
            return GetBasicFormatList();
        }
        catch (Exception ex)
        {
            LogError($"Unexpected error retrieving formats: {ex}");
            return Enumerable.Empty<FileType>();
        }
    }
    
    private static IEnumerable<FileType> GetBasicFormatList()
    {
        // Return a hardcoded list of common formats as fallback
        // This ensures your app doesn't break completely
        return new[] { FileType.Pdf, FileType.Docx, FileType.Xlsx };
    }
}
```  

## Hướng dẫn khắc phục sự cố

### Bước 1: Xác minh cài đặt
Chạy `dotnet list package` hoặc kiểm tra đầu ra console NuGet để xem có cảnh báo nào không.  

```csharp
public static void VerifyInstallation()
{
    try
    {
        var version = typeof(FileType).Assembly.GetName().Version;
        Console.WriteLine($"GroupDocs.Annotation version: {version}");
        
        var formatCount = FileType.GetSupportedFileTypes().Count();
        Console.WriteLine($"Supported formats: {formatCount}");
        
        if (formatCount > 50) // Expected range
        {
            Console.WriteLine("✓ Installation looks good!");
        }
        else
        {
            Console.WriteLine("⚠ Possible installation or licensing issue");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"✗ Installation problem: {ex.Message}");
    }
}
```  

### Bước 2: Kiểm tra trạng thái giấy phép
Đảm bảo `License.SetLicense("path/to/license.json")` được thực thi trước bất kỳ lời gọi API nào.  

### Bước 3: Chẩn đoán các ràng buộc môi trường
- Xác nhận phiên bản .NET runtime phù hợp với yêu cầu của thư viện.  
- Đảm bảo tiến trình có quyền đọc/ghi cho thư mục tạm được GroupDocs.Annotation sử dụng.  

## Câu hỏi thường gặp

**H: GroupDocs.Annotation thực sự hỗ trợ những định dạng tệp nào?**  
Thư viện hỗ trợ **hơn 50 định dạng**, bao gồm PDF, DOCX, XLSX, PPTX, JPEG, PNG, TIFF và nhiều định dạng khác. Chạy mã mẫu để lấy danh sách chính xác cho giấy phép của bạn.

**H: Tại sao tôi nhận được ít định dạng hỗ trợ hơn mong đợi?**  
Điều này thường chỉ ra vấn đề giấy phép—hoặc là bản dùng thử đã hết hạn hoặc file giấy phép được tải không đúng. Áp dụng lại giấy phép hợp lệ và khởi động lại ứng dụng.

**H: Tôi có thể kiểm tra một định dạng duy nhất mà không tải toàn bộ danh sách không?**  
Không có phương thức “IsSupported” trực tiếp; cách tiếp cận được đề xuất là cache toàn bộ danh sách một lần và truy vấn cục bộ để tra cứu nhanh.

**H: Tôi nên xử lý kiểm tra định dạng như thế nào trong ứng dụng web có lưu lượng cao?**  
Khởi tạo cache định dạng khi khởi động ứng dụng (ví dụ, trong `ConfigureServices`) và lưu nó trong một service tĩnh hoặc singleton. Điều này loại bỏ overhead cho mỗi yêu cầu.

**H: Nếu GetSupportedFileTypes() ném ngoại lệ thì sao?**  
Các ngoại lệ thường xuất phát từ vấn đề giấy phép hoặc cài đặt bị hỏng. Kiểm tra tính toàn vẹn của gói, cài đặt lại nếu cần, và đảm bảo file giấy phép có thể truy cập.

## Kết luận

Bạn giờ đã có một chiến lược hoàn chỉnh, sẵn sàng cho production để **cách lấy các định dạng** với GroupDocs.Annotation trong .NET. Từ lời gọi API một dòng đến cache mạnh mẽ, xử lý lỗi, và tích hợp UI, bạn có thể tự tin xác thực tải lên, tạo bộ lọc tệp động, và xây dựng các pipeline chú thích có khả năng mở rộng.

**Bước tiếp theo:**  
- Khám phá [GroupDocs.Annotation API Reference](https://reference.groupdocs.com/annotation/net/) để tìm hiểu sâu hơn về các tính năng chú thích.  
- Tham gia cộng đồng trên [Support Forum](https://forum.groupdocs.com/c/annotation/) nếu gặp các trường hợp đặc biệt.  
- Thử nghiệm kết hợp xác thực định dạng với các quy tắc kinh doanh tùy chỉnh (ví dụ: giới hạn kích thước, quét bảo mật) để tăng cường quy trình tài liệu của bạn.

## Tài nguyên
- [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/)
- [Download Latest Version](https://releases.groupdocs.com/annotation/net/)
- [Free Trial](https://releases.groupdocs.com/annotation/net/)
- [temporary license](https://purchase.groupdocs.com/temporary-license/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [GroupDocs Purchase](https://purchase.groupdocs.com/buy)
- [Purchase Licensing](https://purchase.groupdocs.com/buy)
- [Documentation](https://docs.groupdocs.com/annotation/net/)
- [API Reference](https://reference.groupdocs.com/annotation/net/)
- [GroupDocs.Annotation API Reference](https://reference.groupdocs.com/annotation/net/)
- [Support Forum](https://forum.groupdocs.com/c/annotation/)
- [Community Support](https://forum.groupdocs.com/c/annotation/)

---

**Cập nhật lần cuối:** 2026-06-26  
**Kiểm tra với:** GroupDocs.Annotation 25.4.0 for .NET  
**Tác giả:** GroupDocs  

---

```csharp
public static List<string> GetSupportedExtensions()
{
    try
    {
        var supportedExtensions = FileType.GetSupportedFileTypes()
            .Select(ft => ft.Extension.ToLowerInvariant())
            .OrderBy(ext => ext)
            .ToList();
        
        return supportedExtensions;
    }
    catch (Exception ex)
    {
        // Log the error appropriately in your application
        Console.WriteLine($"Error retrieving supported formats: {ex.Message}");
        return new List<string>();
    }
}
```

## Hướng dẫn liên quan

- [Document Metadata Extraction .NET - Complete Guide to GroupDocs.Annotation](/annotation/net/document-information/)
- [Load PDF from URL .NET - Complete Guide with GroupDocs.Annotation](/annotation/net/document-loading-essentials/load-document-from-url/)
- [Document Preview .NET Tutorials - Complete GroupDocs.Annotation Guide](/annotation/net/document-preview/)