---
"description": "Tìm hiểu cách thêm chú thích thay thế văn bản vào tài liệu .NET của bạn một cách dễ dàng bằng GroupDocs.Annotation cho .NET. Nâng cao khả năng thao tác tài liệu của bạn."
"linktitle": "Thêm chú thích thay thế văn bản vào tài liệu"
"second_title": "GroupDocs.Chú thích API .NET"
"title": "Thêm chú thích thay thế văn bản vào tài liệu"
"url": "/vi/net/unlocking-annotation-power/add-text-replacement-annotation/"
"weight": 24
---

# Thêm chú thích thay thế văn bản vào tài liệu

## Giới thiệu
Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình thêm Chú thích thay thế văn bản vào tài liệu của bạn bằng GroupDocs.Annotation cho .NET. Thư viện mạnh mẽ này cho phép các nhà phát triển thao tác và chú thích nhiều loại tài liệu theo chương trình. Đến cuối hướng dẫn này, bạn sẽ được trang bị kiến thức để tích hợp liền mạch các chú thích thay thế văn bản vào các ứng dụng .NET của mình.
## Điều kiện tiên quyết
Trước khi bắt đầu, hãy đảm bảo bạn đã cài đặt các điều kiện tiên quyết sau:
### 1. .NET Framework đã được cài đặt
Đảm bảo bạn đã cài đặt .NET Framework trên máy phát triển của mình. Bạn có thể tải xuống từ trang web của Microsoft.
### 2. GroupDocs.Annotation cho Thư viện .NET
Tải xuống và cài đặt GroupDocs.Annotation cho thư viện .NET từ [trang web](https://releases.groupdocs.com/annotation/net/). Thư viện này cung cấp các công cụ và chức năng cần thiết để làm việc với chú thích ở nhiều định dạng tài liệu khác nhau.
### 3. Thiết lập môi trường phát triển
Thiết lập môi trường phát triển ưa thích của bạn, chẳng hạn như Visual Studio, để tạo và chạy các ứng dụng .NET.

## Nhập không gian tên
Trước khi đi sâu vào phần mã hóa, chúng ta hãy nhập các không gian tên cần thiết để làm việc với GroupDocs.Annotation cho .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## Bước 1: Xác định Đường dẫn đầu ra
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Tại đây, chúng tôi xác định đường dẫn đầu ra nơi tài liệu có chú thích sẽ được lưu.
## Bước 2: Khởi tạo Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Mã chú thích sẽ được đặt ở đây
}
```
Chúng tôi khởi tạo đối tượng Annotator bằng cách chỉ định tài liệu đầu vào ("input.pdf") trong khối using để đảm bảo xử lý tài nguyên đúng cách.
## Bước 3: Tạo chú thích thay thế
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    },
    TextToReplace = "replaced text"
};
```
Tại đây, chúng ta tạo một đối tượng ReplacementAnnotation với nhiều thuộc tính khác nhau như ngày tạo, màu phông chữ, thông báo, độ mờ đục, số trang, màu nền, điểm (tọa độ), phản hồi (bình luận) và văn bản cần thay thế.
## Bước 4: Thêm chú thích
```csharp
annotator.Add(replacement);
```
Chúng tôi thêm chú thích thay thế đã tạo vào trình chú thích.
## Bước 5: Lưu tài liệu
```csharp
annotator.Save(outputPath);
```
Cuối cùng, chúng ta lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định.
## Bước 6: Hiển thị thông báo thành công
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Một thông báo thành công sẽ hiển thị cho biết tài liệu đã được lưu thành công.

## Phần kết luận
Trong hướng dẫn này, chúng tôi đã trình bày quy trình thêm chú thích thay thế văn bản vào tài liệu bằng GroupDocs.Annotation cho .NET. Bằng cách làm theo hướng dẫn từng bước và hiểu các điều kiện tiên quyết, bạn có thể dễ dàng tích hợp chức năng này vào các ứng dụng .NET của mình.
## Câu hỏi thường gặp
### Tôi có thể chú thích các tài liệu có định dạng khác nhau bằng GroupDocs.Annotation cho .NET không?
Có, GroupDocs.Annotation cho .NET hỗ trợ chú thích nhiều định dạng tài liệu khác nhau như PDF, DOCX, PPTX, XLSX, v.v.
### GroupDocs.Annotation cho .NET có phù hợp cho cả ứng dụng máy tính để bàn và web không?
Có, GroupDocs.Annotation cho .NET có thể được sử dụng trong cả ứng dụng máy tính để bàn và web, mang lại sự linh hoạt cho các nhà phát triển.
### Tôi có thể tùy chỉnh giao diện của chú thích được thêm bằng GroupDocs.Annotation cho .NET không?
Hoàn toàn có thể tùy chỉnh giao diện của chú thích bằng cách sửa đổi các thuộc tính như màu sắc, độ mờ, phông chữ, v.v.
### GroupDocs.Annotation cho .NET có hỗ trợ tính năng chú thích cộng tác không?
Có, GroupDocs.Annotation cho .NET cung cấp các tính năng chú thích cộng tác, cho phép nhiều người dùng chú thích tài liệu cùng lúc.
### Có bản dùng thử miễn phí nào cho GroupDocs.Annotation dành cho .NET không?
Có, bạn có thể dùng thử miễn phí GroupDocs.Annotation cho .NET từ [trang web](https://releases.groupdocs.com/).