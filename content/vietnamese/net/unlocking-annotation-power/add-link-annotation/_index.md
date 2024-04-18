---
title: Thêm chú thích liên kết vào tài liệu
linktitle: Thêm chú thích liên kết vào tài liệu
second_title: GroupDocs.Annotation .NET API
description: Tìm hiểu cách thêm chú thích liên kết vào tài liệu bằng Groupdocs.Annotation cho .NET. Tăng cường hợp tác và tương tác dễ dàng.
type: docs
weight: 16
url: /vi/net/unlocking-annotation-power/add-link-annotation/
---
## Giới thiệu
Groupdocs.Annotation for .NET là một thư viện mạnh mẽ cho phép các nhà phát triển tích hợp các chức năng chú thích toàn diện vào các ứng dụng .NET của họ một cách dễ dàng. Một trong những tính năng chính mà nó cung cấp là khả năng thêm chú thích liên kết vào tài liệu, tăng cường cộng tác và tương tác.
## Điều kiện tiên quyết
Trước khi đi sâu vào quá trình thêm chú thích liên kết, hãy đảm bảo bạn có các điều kiện tiên quyết sau:
- Hiểu biết cơ bản về ngôn ngữ lập trình C#.
- Đã cài đặt Groupdocs.Annotation cho thư viện .NET.
- Truy cập vào tài liệu mà bạn muốn chú thích.

## Nhập không gian tên
Trước tiên, bạn cần nhập các không gian tên cần thiết để sử dụng Groupdocs.Annotation cho các chức năng .NET. Điều này cho phép ứng dụng của bạn truy cập vào các lớp và phương thức cần thiết để chú thích tài liệu.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Bước 1: Đặt đường dẫn đầu ra
Xác định đường dẫn nơi bạn muốn lưu tài liệu có chú thích.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Bước 2: Khởi tạo Annotator
 Tạo một thể hiện của`Annotator` lớp bằng cách cung cấp đường dẫn của tài liệu bạn muốn chú thích.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Mã chú thích sẽ ở đây
}
```
## Bước 3: Tạo chú thích liên kết
 Xác định một`LinkAnnotation` đối tượng và chỉ định các thuộc tính của nó như tin nhắn, độ mờ, số trang, màu nền, điểm, câu trả lời và URL.
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
    Url = "https://www.google.com"
};
```
## Bước 4: Thêm chú thích
 Thêm chú thích liên kết đã tạo vào tài liệu bằng cách sử dụng`Add` phương thức của phiên bản chú thích.
```csharp
annotator.Add(link);
```
## Bước 5: Lưu tài liệu
Lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định.
```csharp
annotator.Save(outputPath);
```
## Bước 6: Hiển thị thông báo thành công
Thông báo cho người dùng về việc lưu thành công tài liệu được chú thích.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Phần kết luận
Tóm lại, bằng cách làm theo các bước trên, bạn có thể thêm liền mạch các chú thích liên kết vào tài liệu bằng Groupdocs.Annotation cho .NET. Điều này tăng cường sự cộng tác trên tài liệu và cung cấp cho người dùng các tính năng tương tác.
## Câu hỏi thường gặp
### Groupdocs.Annotation for .NET có tương thích với tất cả các loại tài liệu không?
Groupdocs.Annotation for .NET hỗ trợ nhiều định dạng tài liệu bao gồm PDF, Word, Excel, v.v.
### Tôi có thể tùy chỉnh hình thức của chú thích không?
Có, bạn có thể tùy chỉnh các thuộc tính khác nhau của chú thích như màu sắc, độ mờ và kích thước để phù hợp với yêu cầu của bạn.
### Groupdocs.Annotation cho .NET có cung cấp các tính năng cộng tác theo thời gian thực không?
Có, Groupdocs.Annotation for .NET cung cấp các tính năng cộng tác theo thời gian thực cho phép nhiều người dùng chú thích tài liệu cùng một lúc.
### Có hỗ trợ kỹ thuật cho các sản phẩm Groupdocs không?
 Có, hỗ trợ kỹ thuật cho các sản phẩm Groupdocs có sẵn thông qua diễn đàn và bộ phận hỗ trợ[đây](https://forum.groupdocs.com/c/annotation/10).
### Tôi có thể dùng thử Groupdocs.Annotation cho .NET trước khi mua không?
Có, bạn có thể tận dụng bản dùng thử miễn phí của Groupdocs. Chú thích cho .NET để khám phá các tính năng của nó trước khi mua hàng[đây](https://purchase.groupdocs.com/temporary-license/).