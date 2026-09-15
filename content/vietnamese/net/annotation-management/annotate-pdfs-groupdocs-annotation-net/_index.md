---
categories:
- PDF Processing
date: '2026-05-26'
description: Tìm hiểu cách tạo hệ thống đánh giá tài liệu bằng GroupDocs Annotation
  cho .NET. Hướng dẫn step‑by‑step bao gồm cài đặt, các loại annotation, tối ưu hiệu
  năng và khắc phục sự cố cho các nhà phát triển C#.
keywords:
- create document review system
- PDF annotation .NET
- GroupDocs annotation tutorial
lastmod: '2026-05-26'
linktitle: Hướng Dẫn PDF Annotation .NET
schemas:
- author: GroupDocs
  dateModified: '2026-05-26'
  description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  headline: 'Create Document Review System: PDF Annotation .NET Guide'
  type: TechArticle
- description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  name: 'Create Document Review System: PDF Annotation .NET Guide'
  steps:
  - name: Create an AreaAnnotation
    text: '`AreaAnnotation` represents a rectangular highlight area on a PDF page.'
  - name: Create an EllipseAnnotation
    text: '`EllipseAnnotation` represents an elliptical shape annotation on a PDF
      page.'
  - name: Add Annotations in Bulk
    text: '**Pro Tip:** Adding annotations in a list and calling `Add` once reduces
      I/O overhead, especially when you need to insert dozens of marks across many
      pages.'
  type: HowTo
- questions:
  - answer: GroupDocs automatically reads each page’s dimensions. When positioning
      annotations, always query `annotator.GetPageInfo(pageNumber)` and calculate
      coordinates based on that page’s width and height.
    question: How do I handle PDFs with different page sizes?
  - answer: Yes. Use the `LoadOptions` constructor that accepts a password string,
      e.g., `new LoadOptions { Password = "secret" }`, and pass it to the `Annotator`
      constructor.
    question: Can I annotate password‑protected PDFs?
  - answer: There is no hard limit, but performance degrades after a few thousand
      annotations. For very large annotation sets, group them into logical sections
      and process each section separately.
    question: What is the maximum number of annotations I can add to a single PDF?
  - answer: Retrieve the annotation’s `Id` via `GetAnnotations()`, then call `Delete(id)`
      or create a `SaveOptions` instance that excludes the unwanted `AnnotationType`.
    question: How do I remove specific annotations programmatically?
  - answer: Absolutely. You can set opacity, border thickness, dash style, and even
      embed custom SVG icons for stamp annotations.
    question: Can I customize annotation appearance beyond colors?
  type: FAQPage
tags:
- pdf-annotation
- groupdocs
- dotnet
- csharp
- document-processing
title: 'Tạo Hệ Thống Đánh Giá Tài Liệu: Hướng Dẫn PDF Annotation .NET'
type: docs
url: /vi/net/annotation-management/annotate-pdfs-groupdocs-annotation-net/
weight: 1
---

# Tạo Hệ thống Đánh giá Tài liệu: Hướng dẫn Ghi chú PDF .NET

Nếu bạn cần **tạo hệ thống đánh giá tài liệu** cho phép người dùng thêm bình luận, đánh dấu và các hình dạng vào PDF trực tiếp từ một ứng dụng .NET, bạn đã đến đúng nơi. GroupDocs.Annotation for .NET loại bỏ rắc rối của việc xử lý PDF ở mức thấp đồng thời cung cấp cho bạn khả năng kiểm soát chi tiết từng loại ghi chú. Trong hướng dẫn này, bạn sẽ thấy cách thiết lập thư viện, thêm các ghi chú vùng, hình elip và văn bản, lọc những gì được lưu, và giữ hiệu năng nhanh chóng ngay cả với các tệp hàng trăm trang.

## Câu trả lời nhanh
- **Thư viện nào xử lý ghi chú PDF trong .NET?** GroupDocs.Annotation for .NET.  
- **Tôi có thể thêm đánh dấu, vòng tròn và bình luận bằng mã không?** Có – sử dụng các đối tượng AreaAnnotation, EllipseAnnotation và TextAnnotation.  
- **Cần giấy phép cho môi trường sản xuất không?** Một giấy phép GroupDocs hợp lệ là bắt buộc cho bất kỳ triển khai sản xuất nào.  
- **Kích thước PDF tối đa có thể xử lý là bao nhiêu?** Có thể xử lý tới 500 MB mà không cần tải toàn bộ tệp vào bộ nhớ.  
- **Điều này có giúp tôi tạo hệ thống đánh giá tài liệu không?** Chắc chắn – bạn có thể lưu hàng loạt, lọc và tạo phiên bản cho các người xem.

## Hệ thống đánh giá tài liệu là gì?
Một **hệ thống đánh giá tài liệu** là giải pháp phần mềm cho phép nhiều bên liên quan ghi chú, bình luận và phê duyệt các tệp PDF trong một quy trình làm việc phối hợp. Nó tập trung phản hồi, theo dõi thay đổi và thường xuất ra một phiên bản sạch để phê duyệt cuối cùng.

## Tại sao sử dụng GroupDocs Annotation cho .NET để tạo hệ thống đánh giá tài liệu?
GroupDocs Annotation hỗ trợ **hơn 30 loại ghi chú**, xử lý các PDF lên tới **500 MB**, và chạy trên **.NET Framework 4.6.1+**, **.NET Core 2.0+**, và **.NET 6+**. API của nó cho phép bạn thêm, xóa và lọc ghi chú mà không cần chạm vào cấu trúc nội bộ của PDF, giúp tăng tốc phát triển và giảm lỗi.

## Yêu cầu trước và Cài đặt Môi trường

Trước khi viết bất kỳ mã nào, hãy đảm bảo môi trường phát triển của bạn đáp ứng các tiêu chí sau:

- **IDE:** Visual Studio 2019 hoặc mới hơn, hoặc VS Code với tiện ích mở rộng C#.  
- **Framework mục tiêu:** .NET Framework 4.6.1 + hoặc .NET Core 2.0 + (đề xuất .NET 6 cho các dự án mới).  
- **Truy cập NuGet:** Khả năng cài đặt gói từ nuget.org.  
- **PDF mẫu:** Ít nhất một PDF đa trang để kiểm tra vị trí ghi chú.  
- **Bộ nhớ & Đĩa:** Tối thiểu 4 GB RAM và đủ không gian đĩa trống cho các tệp tạm thời (quá trình ghi chú có thể tạo các luồng tạm).

### Thực hành Phát triển Được Đề xuất
- Giữ dự án của bạn dưới kiểm soát phiên bản (Git) để có thể quay lại các thay đổi liên quan đến ghi chú.  
- Sử dụng thư mục **Annotations** riêng trong dự án để lưu các tệp cấu hình và khóa giấy phép.  
- Bật **nullable reference types** (`<Nullable>enable</Nullable>`) để phát hiện sớm các lỗi tham chiếu null tiềm năng.

## Bắt đầu: Cài đặt GroupDocs.Annotation

### Các phương pháp Cài đặt

**Tùy chọn 1: NuGet Package Manager Console**  
Chạy lệnh sau trong Package Manager Console:  

`Install-Package GroupDocs.Annotation`

**Tùy chọn 2: .NET CLI (được khuyến nghị cho phát triển đa nền tảng)**  
Thực thi trong terminal:  

`dotnet add package GroupDocs.Annotation`

**Tùy chọn 3: Giao diện Người dùng Trình quản lý Gói Visual Studio**  
- Nhấp chuột phải vào dự án → **Manage NuGet Packages**  
- Tìm kiếm **GroupDocs.Annotation**  
- Nhấn **Install** trên phiên bản ổn định mới nhất  

Cả ba phương pháp đều cài đặt cùng một binary; chọn phương pháp phù hợp với quy trình làm việc của bạn.

### Cấu hình Giấy phép
GroupDocs yêu cầu giấy phép hợp lệ cho bất kỳ việc sử dụng trong môi trường sản xuất nào. Bạn có ba lựa chọn:

- **Dùng thử miễn phí:** Đánh giá 30 ngày với đầy đủ tính năng.  
- **Giấy phép tạm thời:** Đánh giá mở rộng cho phát triển và kiểm thử.  
- **Giấy phép thương mại:** Sử dụng không giới hạn trong môi trường sản xuất.  

`License` class tải và áp dụng tệp giấy phép GroupDocs để kích hoạt đầy đủ chức năng. Bạn có thể lấy giấy phép từ [trang mua GroupDocs](https://purchase.groupdocs.com/buy). Sau khi nhận được tệp `.lic`, đặt nó vào thư mục mà ứng dụng của bạn có thể đọc và chỉ định cho lớp `License` tại thời điểm khởi động.

### Xác minh Cài đặt Ban đầu
Tạo một chương trình console nhỏ tải một PDF và ghi số trang ra console. Nếu chương trình chạy mà không ném ngoại lệ, thư viện đã được cài đặt và cấp giấy phép đúng cách.

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;

var annotator = new Annotator("sample.pdf");
var info = annotator.GetDocumentInfo();
Console.WriteLine($"Pages: {info.PageCount}");
```

> **Lưu ý:** Đoạn mã trên chỉ để minh họa; bạn **không** cần thêm khối mã được bao quanh trong bài viết cuối cùng, nhưng đoạn mã nội tuyến cho thấy cách sử dụng API chính xác.

Nếu bạn thấy số lượng trang được in ra, bạn đã sẵn sàng để bắt đầu thêm các ghi chú thực tế.

## Triển khai Cốt lõi: Thêm Ghi chú vào PDF

### Định nghĩa Neo – Annotator
Lớp `Annotator` là điểm vào cho tất cả các thao tác ghi chú PDF trong GroupDocs.Annotation cho .NET. Nó tải PDF vào bộ nhớ, cung cấp các phương thức để thêm, chỉnh sửa và truy xuất ghi chú, và xử lý việc lưu tài liệu đã chỉnh sửa.

### Cách thêm ghi chú vùng và elip?
Tải PDF bằng `new Annotator(...)`, tạo các đối tượng `AreaAnnotation` và `EllipseAnnotation`, đặt tọa độ của chúng, và thêm vào bộ sưu tập của annotator. Cuối cùng, gọi `Save` để lưu các thay đổi. Quy trình này cho phép bạn lập trình làm nổi bật các phần (vùng) hoặc khoanh tròn các đồ họa quan trọng trong một thao tác nguyên tử.

#### Bước 1: Khởi tạo Annotator
```csharp
var annotator = new Annotator("input.pdf");
```

#### Bước 2: Tạo AreaAnnotation
`AreaAnnotation` đại diện cho một vùng đánh dấu hình chữ nhật trên một trang PDF.  
```csharp
var area = new AreaAnnotation
{
    PageNumber = 0,
    Box = new RectangleF(100, 150, 200, 50),
    Color = Color.Yellow,
    Opacity = 0.4f,
    Text = "Review this paragraph"
};
```

#### Bước 3: Tạo EllipseAnnotation
`EllipseAnnotation` đại diện cho một ghi chú dạng hình elip trên một trang PDF.  
```csharp
var ellipse = new EllipseAnnotation
{
    PageNumber = 2,
    Box = new RectangleF(300, 400, 120, 80),
    Color = Color.Red,
    Opacity = 0.6f,
    Text = "Check this figure"
};
```

#### Bước 4: Thêm Ghi chú Hàng loạt
```csharp
annotator.Add(new List<AnnotationBase> { area, ellipse });
annotator.Save("output.pdf");
```

**Mẹo chuyên nghiệp:** Thêm ghi chú vào một danh sách và gọi `Add` một lần giảm tải I/O, đặc biệt khi bạn cần chèn hàng chục dấu trên nhiều trang.

### Cách lưu các ghi chú được chọn?
`SaveOptions` cấu hình cách PDF đã ghi chú được lưu, bao gồm các loại ghi chú sẽ bao gồm. GroupDocs.Annotation cho phép bạn lọc các loại ghi chú sẽ được ghi vào tệp đầu ra. Tạo một thể hiện `SaveOptions`, đặt bộ sưu tập `AnnotationTypes` thành các loại bạn muốn giữ, và truyền các tùy chọn này vào `Save`. Điều này hoàn hảo để tạo PDF chỉ dành cho người xem hoặc loại bỏ các ghi chú tạm thời trước khi lưu trữ.

```csharp
var saveOptions = new SaveOptions
{
    AnnotationTypes = new[] { AnnotationType.Text, AnnotationType.Area }
};
annotator.Save("filtered.pdf", saveOptions);
```

## Các kịch bản triển khai thực tế

### Kịch bản 1: Quy trình Đánh giá Tài liệu
Nhiều người xem thêm các ghi chú **Area**, **Ellipse**, và **Text**. Sau vòng đánh giá, bạn tạo ba PDF:
1. Phiên bản đầy đủ với mọi bình luận.  
2. Phiên bản chỉ dành cho người xem (lọc bỏ các ghi chú nội bộ).  
3. Phiên bản sạch cho phê duyệt cuối cùng (chỉ giữ các đánh dấu).

### Kịch bản 2: Tự động tạo báo cáo
Backend của bạn xử lý các báo cáo bán hàng hàng ngày, tự động làm nổi bật các chỉ số quan trọng bằng ghi chú vùng và khoanh tròn các biểu đồ ngoại lệ bằng ghi chú elip. Các PDF được tạo ra sau đó được gửi email cho các bên liên quan mà không cần can thiệp thủ công.

### Kịch bản 3: Tài liệu pháp lý hợp tác
Các công ty luật thường cần tách biệt bình luận của đối tác với ghi chú của cộng sự cấp dưới. Bằng cách gắn thẻ ghi chú với siêu dữ liệu tùy chỉnh và sử dụng lưu chọn lọc, bạn có thể tạo PDF dành cho đối tác xem xét mà ẩn các ghi chú của người cấp dưới, đơn giản hoá việc kiểm soát phiên bản.

## Tối ưu hoá hiệu năng cho môi trường sản xuất

### Cách quản lý bộ nhớ khi ghi chú các PDF lớn?
`LoadOptions` cho phép bạn chỉ định cách PDF được tải, chẳng hạn như phạm vi trang hoặc mật khẩu. Khi một PDF vượt quá 100 MB, tránh tải toàn bộ tệp bằng cách sử dụng hàm khởi tạo `LoadOptions` chấp nhận phạm vi trang. Xử lý các trang theo lô, giải phóng mỗi thể hiện `Annotator` bằng khối `using`, và dọn dẹp các tệp tạm sau mỗi lô. Cách tiếp cận này giữ mức sử dụng bộ nhớ tối đa dưới 200 MB ngay cả với tài liệu 500 trang.

```csharp
using (var annotator = new Annotator("large.pdf", new LoadOptions { PageNumbers = new[] { 0, 1, 2 } }))
{
    // annotate first three pages
}
```

### Các thực hành tốt nhất về quản lý bộ nhớ
- **Luôn bao bọc `Annotator` trong một câu lệnh `using`** để đảm bảo giải phóng các tài nguyên không quản lý.  
- **Xử lý ghi chú theo lô**: thu thập tất cả ghi chú cho một tài liệu, sau đó gọi `Add` một lần.  
- **Tránh tải toàn bộ PDF** khi bạn chỉ cần chỉnh sửa một tập hợp các trang; sử dụng `LoadOptions.PageNumbers`.

### Chiến lược xử lý tệp lớn
1. **Xử lý theo trang** – Tải, ghi chú và lưu một trang tại một thời điểm.  
2. **Xuất luồng** – Chuyển hướng phương thức `Save` tới một `MemoryStream` để tránh ghi tạm thời vào đĩa.  
3. **Dọn dẹp tệp tạm** – Xóa bất kỳ tệp tạm nào do annotator tạo ra sau mỗi thao tác.

### Các lưu ý khi xử lý đồng thời
- **An toàn luồng:** Các thể hiện `Annotator` không an toàn với đa luồng. Tạo một thể hiện riêng cho mỗi luồng.  
- **Kiểm soát tài nguyên:** Giới hạn số công việc đồng thời bằng số lõi CPU để tránh quá tải CPU.  
- **API bất đồng bộ:** `SaveAsync` lưu tài liệu đã ghi chú một cách bất đồng bộ, trả về một Task, hữu ích trong môi trường ASP.NET Core.

## Khắc phục các vấn đề thường gặp

### Vấn đề 1: Lỗi “File Not Found”
**Câu trả lời trực tiếp:** Kiểm tra rằng đường dẫn tệp bạn truyền vào `new Annotator(...)` là tuyệt đối hoặc tương đối đúng so với assembly đang chạy, và đảm bảo tiến trình ứng dụng có quyền đọc đối với vị trí đó. Nếu tệp nằm trên một chia sẻ mạng, hãy ánh xạ chia sẻ hoặc sử dụng đường dẫn UNC.

**Cách khắc phục thường gặp:**  
- Sử dụng `Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Docs", "sample.pdf")`.  
- Cấp quyền đọc/ghi cho danh tính pool ứng dụng IIS trên thư mục.

### Vấn đề 2: Ghi chú xuất hiện ở vị trí sai
**Câu trả lời trực tiếp:** Đảm bảo bạn đang sử dụng cùng một hệ tọa độ (gốc trên‑trái) và DPI của trang khớp với các giá trị bạn cung cấp. Lấy kích thước trang qua `annotator.GetPageInfo(pageNumber)` và tính toán tọa độ dựa trên kích thước đó.

**Cách khắc phục thường gặp:**  
- Nhân tọa độ với hệ số tỷ lệ của trang nếu PDF được tạo với DPI không chuẩn.  
- Kiểm tra lại rằng bạn không trộn lẫn điểm (1/72 inch) với pixel.

### Vấn đề 3: Vấn đề hiệu năng với tệp lớn
**Câu trả lời trực tiếp:** Chuyển sang tải theo phạm vi trang, xử lý ghi chú theo lô, và giải phóng nhanh mỗi thể hiện `Annotator`. Ngoài ra bật tùy chọn `MemoryCache` trong `LoadOptions` để tái sử dụng bộ đệm giữa các thao tác.

**Cách khắc phục thường gặp:**  
- Đặt `LoadOptions.UseMemoryCache = true`.  
- Xử lý tệp bất đồng bộ với `await annotator.SaveAsync(...)`.

### Vấn đề 4: Lỗi liên quan đến giấy phép
**Câu trả lời trực tiếp:** Đặt tệp `.lic` vào một thư mục mà ứng dụng có thể đọc, và gọi `License license = new License(); license.SetLicense("path/to/license.lic");` trước bất kỳ lời gọi GroupDocs nào khác. Kiểm tra phiên bản giấy phép khớp với phiên bản thư viện bạn đang sử dụng.

**Cách khắc phục thường gặp:**  
- Kiểm tra tệp giấy phép không bị hỏng (so sánh kích thước tệp).  
- Đảm bảo bạn không trộn lẫn giấy phép dùng thử với giấy phép thương mại trong cùng môi trường.

## Mẹo nâng cao và Thực hành tốt nhất

### Quản lý màu sắc
Màu sắc nhất quán cải thiện khả năng đọc cho người xem. Định nghĩa một bảng màu (ví dụ, Vàng cho đánh dấu, Đỏ cho vấn đề quan trọng) và lưu nó trong một lớp trợ giúp tĩnh. Nhớ sử dụng màu tương phản cao để hỗ trợ khả năng truy cập và thêm một trang chú giải trong PDF để tham khảo.

### Mẫu xử lý lỗi
Bao bọc tất cả các lời gọi ghi chú trong khối try‑catch đặc biệt bắt `GroupDocs.Annotation.Exceptions.AnnotationException`. Ghi lại thông báo ngoại lệ, stack trace và tên PDF để hỗ trợ gỡ lỗi.

### Chiến lược kiểm thử
- **Kiểm thử đơn vị:** Sử dụng một PDF nhỏ với kích thước đã biết, thêm một ghi chú, và khẳng định `GetAnnotations()` trả về tọa độ mong đợi.  
- **Kiểm thử tích hợp:** Chạy toàn bộ quy trình trên các PDF từ 1 trang đến 200 trang, và xác minh thời gian xử lý dưới 5 giây cho các tệp dưới 50 MB.  
- **Kiểm thử tải:** Mô phỏng 50 yêu cầu ghi chú đồng thời bằng công cụ như k6 hoặc Apache JMeter và giám sát CPU/bộ nhớ.

## Câu hỏi thường gặp

**H: Làm thế nào để tôi xử lý các PDF có kích thước trang khác nhau?**  
Đ: GroupDocs tự động đọc kích thước của mỗi trang. Khi định vị ghi chú, luôn truy vấn `annotator.GetPageInfo(pageNumber)` và tính toán tọa độ dựa trên chiều rộng và chiều cao của trang đó.

**H: Tôi có thể ghi chú các PDF được bảo vệ bằng mật khẩu không?**  
Đ: Có. Sử dụng hàm khởi tạo `LoadOptions` chấp nhận một chuỗi mật khẩu, ví dụ `new LoadOptions { Password = "secret" }`, và truyền nó vào hàm khởi tạo `Annotator`.

**H: Số lượng ghi chú tối đa tôi có thể thêm vào một PDF là bao nhiêu?**  
Đ: Không có giới hạn cứng, nhưng hiệu năng giảm sau vài nghìn ghi chú. Đối với bộ ghi chú rất lớn, hãy nhóm chúng thành các phần logic và xử lý từng phần riêng biệt.

**H: Làm sao tôi có thể xóa các ghi chú cụ thể bằng mã?**  
Đ: Lấy `Id` của ghi chú qua `GetAnnotations()`, sau đó gọi `Delete(id)` hoặc tạo một thể hiện `SaveOptions` loại trừ `AnnotationType` không mong muốn.

**H: Tôi có thể tùy chỉnh giao diện ghi chú ngoài màu sắc không?**  
Đ: Chắc chắn. Bạn có thể đặt độ trong suốt, độ dày viền, kiểu gạch đứt, và thậm chí nhúng các biểu tượng SVG tùy chỉnh cho ghi chú dấu.

**H: Điều gì sẽ xảy ra nếu tôi cố gắng ghi chú một PDF đã quét (dựa trên hình ảnh)?**  
Đ: Các ghi chú sẽ được hiển thị như các đối tượng lớp phủ trên hình ảnh trang. Chúng không thay đổi dữ liệu raster bên dưới, vì vậy PDF vẫn có thể tìm kiếm được nếu có lớp OCR.

**H: Làm sao tôi xử lý các PDF rất lớn mà không hết bộ nhớ?**  
Đ: Xử lý tài liệu trang‑theo‑trang bằng `LoadOptions.PageNumbers`, giải phóng mỗi thể hiện `Annotator` ngay sau khi sử dụng, và bật lưu dạng luồng vào `MemoryStream` để tránh tăng đột biến đĩa.

## Tích hợp với Ứng dụng ASP.NET

Khi bạn cung cấp chức năng ghi chú thông qua một web API, hãy tuân theo mẫu sau:

1. **Controller nhận luồng PDF** từ client.  
2. **Xác thực kích thước tệp** (từ chối > 200 MB trừ khi bạn có xử lý đặc biệt).  
3. **Khởi tạo `Annotator` trong khối `using`** để đảm bảo giải phóng.  
4. **Áp dụng ghi chú** dựa trên payload JSON mô tả loại ghi chú, tọa độ và văn bản.  
5. **Lưu vào vị trí tạm thời**, sau đó truyền luồng kết quả lại cho client với header `Content‑Disposition` phù hợp.

```csharp
[HttpPost("annotate")]
public async Task<IActionResult> Annotate(IFormFile pdf, [FromBody] AnnotationRequest request)
{
    using var stream = pdf.OpenReadStream();
    var annotator = new Annotator(stream);
    // add annotations based on request
    var output = new MemoryStream();
    annotator.Save(output);
    output.Position = 0;
    return File(output, "application/pdf", "annotated.pdf");
}
```

## Tài nguyên bổ sung
- [Trang mua GroupDocs](https://purchase.groupdocs.com/buy)  
- [Mua GroupDocs](https://purchase.groupdocs.com/buy)  
- [Tài liệu GroupDocs Annotation](https://docs.groupdocs.com/annotation/net/)  
- [Tham chiếu API GroupDocs](https://reference.groupdocs.com/annotation/net/)  
- [Bản phát hành mới nhất](https://releases.groupdocs.com/annotation/net/)  
- [Dùng thử GroupDocs miễn phí](https://releases.groupdocs.com/annotation/net/)  
- [Yêu cầu giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/)  
- [Diễn đàn GroupDocs](https://forum.groupdocs.com/c/annotation/)

## Kết luận và Các bước tiếp theo

Bạn hiện đã có một **lộ trình đầy đủ, sẵn sàng cho sản xuất** để xây dựng một **hệ thống đánh giá tài liệu** được hỗ trợ bởi GroupDocs.Annotation cho .NET. Bạn đã học cách thiết lập thư viện, thêm các ghi chú vùng, elip và văn bản, lọc khi lưu, và giữ mức sử dụng bộ nhớ thấp ngay cả với các PDF khổng lồ.

**Các hành động tiếp theo bạn có thể thực hiện ngay hôm nay:**  

1. **Thử nghiệm** các loại ghi chú bổ sung như `ArrowAnnotation` và `StampAnnotation`.  
2. **Tích hợp** quy trình vào API ASP.NET Core hiện có hoặc ứng dụng desktop WPF của bạn.  
3. **Khám phá** toàn bộ tài liệu API để tìm các tính năng nâng cao như phiên bản ghi chú và siêu dữ liệu tùy chỉnh.  
4. **Tham gia** diễn đàn cộng đồng GroupDocs để nhận hỗ trợ và cập nhật các bản phát hành mới.

---

**Cập nhật lần cuối:** 2026-05-26  
**Tested With:** GroupDocs.Annotation 23.11 for .NET  
**Author:** GroupDocs  

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main()
    {
        string inputPdfPath = "input.pdf";
        
        try
        {
            // Initialize the Annotator with the path of the document
            using (Annotator annotator = new Annotator(inputPdfPath))
            {
                Console.WriteLine("GroupDocs.Annotation initialized successfully!");
                // Your annotation code will go here
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Setup issue: {ex.Message}");
        }
    }
}
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // All annotation work happens inside this using block
    // This ensures proper resource cleanup
}
```

```csharp
AreaAnnotation areaAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // X, Y, Width, Height
    BackgroundColor = 65535,                 // Yellow highlight
    PageNumber = 0                           // First page
};
```

```csharp
EllipseAnnotation ellipseAnnotation = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Same coordinate system
    BackgroundColor = 123456,                // Different color
    PageNumber = 1                           // Second page
};
```

```csharp
annotator.Add(new List<AnnotationBase>() { areaAnnotation, ellipseAnnotation });
```

```csharp
SaveOptions saveOptions = new SaveOptions 
{
    AnnotationTypes = AnnotationType.Ellipse // Only save ellipse annotations
};
```

```csharp
annotator.Save(outputPath, saveOptions);
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // Your annotation code here
} // Automatic cleanup happens here
```

```csharp
var annotationsToAdd = new List<AnnotationBase>();
// Add multiple annotations to the list
annotator.Add(annotationsToAdd); // Single operation
```

```csharp
// Always verify file exists before processing
if (!File.Exists(inputPdfPath))
{
    throw new FileNotFoundException($"PDF file not found: {inputPdfPath}");
}

// Use absolute paths when possible
string absolutePath = Path.GetFullPath(inputPdfPath);
```

```csharp
// Test with known coordinates first
AreaAnnotation testAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(50, 50, 100, 100), // Start with simple values
    BackgroundColor = 65535,
    PageNumber = 0
};

// Verify page dimensions if needed
// Consider PDF scaling factors in your calculations
```

```csharp
// Define color constants for consistency
public static class AnnotationColors
{
    public const int ImportantHighlight = 65535;    // Yellow
    public const int AttentionMarker = 255;         // Red
    public const int ApprovedSection = 65280;       // Green
}
```

```csharp
try
{
    using (Annotator annotator = new Annotator(inputPdfPath))
    {
        // Your annotation operations
        annotator.Add(annotations);
        annotator.Save(outputPath, saveOptions);
    }
}
catch (GroupDocsException ex)
{
    // Handle GroupDocs-specific errors
    Logger.Error($"GroupDocs error: {ex.Message}");
}
catch (IOException ex)
{
    // Handle file I/O errors
    Logger.Error($"File operation error: {ex.Message}");
}
catch (Exception ex)
{
    // Handle unexpected errors
    Logger.Error($"Unexpected error: {ex.Message}");
}
```

```csharp
[HttpPost]
public async Task<IActionResult> AnnotatePdf(IFormFile pdfFile, AnnotationRequest request)
{
    // Validate input
    if (pdfFile == null || pdfFile.Length == 0)
        return BadRequest("No file provided");

    // Process asynchronously to avoid blocking the UI
    var result = await ProcessAnnotationsAsync(pdfFile, request);
    return Ok(result);
}
```

## Các hướng dẫn liên quan

- [Hướng dẫn GroupDocs Annotation .NET - Hướng dẫn đầy đủ cho Quản lý Tài liệu](/annotation/net/annotation-management/)  
- [Hướng dẫn Xem trước Tài liệu .NET - Hướng dẫn đầy đủ GroupDocs.Annotation](/annotation/net/document-preview/)  
- [Hướng dẫn Giấy phép Định mức GroupDocs Annotation - Hướng dẫn cài đặt .NET đầy đủ](/annotation/net/licensing-and-configuration/implement-metered-license-groupdocs-annotation-net/)