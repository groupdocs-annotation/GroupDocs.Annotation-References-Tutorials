---
title: Thêm chú thích gạch bỏ văn bản vào tài liệu
linktitle: Thêm chú thích gạch bỏ văn bản vào tài liệu
second_title: GroupDocs.Annotation .NET API
description: Tìm hiểu cách thêm chú thích gạch ngang văn bản vào tài liệu bằng GroupDocs.Annotation cho .NET. Tăng cường hợp tác và quá trình xem xét tài liệu một cách hiệu quả.
weight: 26
url: /vi/net/unlocking-annotation-power/add-text-strikeout-annotation/
---

# Thêm chú thích gạch bỏ văn bản vào tài liệu

## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách thêm chú thích gạch ngang văn bản vào tài liệu bằng GroupDocs.Annotation cho .NET. Thư viện này cung cấp các công cụ mạnh mẽ để chú thích các loại tài liệu khác nhau, tăng cường quá trình cộng tác và xem xét tài liệu.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có các điều kiện tiên quyết sau:
1.  GroupDocs.Annotation for .NET: Cài đặt thư viện. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/annotation/net/).
2. Môi trường phát triển: Thiết lập môi trường phát triển phù hợp để phát triển .NET.
3. Tài liệu: Chuẩn bị sẵn tài liệu để chú thích, chẳng hạn như tệp PDF.

## Nhập không gian tên
Đầu tiên, nhập các không gian tên cần thiết để truy cập các chức năng của GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Bây giờ, hãy chia nhỏ quá trình thêm chú thích gạch ngang văn bản thành nhiều bước:
## Bước 1: Xác định đường dẫn đầu ra
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Ở đây, chúng tôi xác định đường dẫn đầu ra nơi tài liệu được chú thích sẽ được lưu.
## Bước 2: Khởi tạo Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Khởi tạo đối tượng Annotator bằng cách cung cấp đường dẫn đến tài liệu đầu vào (tệp PDF trong trường hợp này).
## Bước 3: Tạo chú thích gạch bỏ
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
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
    }
};
```
Tạo một đối tượng StrikeoutAnnotation với các thuộc tính mong muốn như thông báo, độ mờ, số trang, màu nền, điểm (tọa độ) và phản hồi.
## Bước 4: Thêm chú thích
```csharp
annotator.Add(strikeout);
```
Thêm chú thích gạch ngang đã tạo vào tài liệu.
## Bước 5: Lưu tài liệu
```csharp
annotator.Save(outputPath);
```
Lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định.

## Phần kết luận
Trong hướng dẫn này, chúng ta đã tìm hiểu cách thêm chú thích gạch ngang văn bản vào tài liệu bằng GroupDocs.Annotation cho .NET. Thư viện mạnh mẽ này cho phép chú thích tài liệu hiệu quả, tăng cường quá trình cộng tác và xem xét tài liệu.
## Câu hỏi thường gặp
### GroupDocs.Annotation có tương thích với nhiều định dạng tài liệu khác nhau không?
Có, GroupDocs.Annotation hỗ trợ nhiều định dạng tài liệu bao gồm PDF, Word, Excel, PowerPoint, v.v.
### Tôi có thể tùy chỉnh hình thức của chú thích không?
Hoàn toàn có thể, bạn có thể tùy chỉnh các thuộc tính chú thích như màu sắc, độ mờ, kích thước phông chữ, v.v. theo yêu cầu của bạn.
### GroupDocs.Annotation có cung cấp các tính năng cộng tác không?
Có, GroupDocs.Annotation hỗ trợ cộng tác bằng cách cho phép người dùng thêm nhận xét, câu trả lời và chú thích vào tài liệu.
### Có bản dùng thử miễn phí không?
 Có, bạn có thể tận dụng bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).
### Tôi có thể nhận hỗ trợ cho GroupDocs.Annotation ở đâu?
 Bạn có thể nhận được sự hỗ trợ từ[Diễn đàn GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation/10).