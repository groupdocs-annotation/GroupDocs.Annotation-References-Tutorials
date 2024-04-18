---
title: Thêm chú thích gạch chân văn bản vào tài liệu
linktitle: Thêm chú thích gạch chân văn bản vào tài liệu
second_title: GroupDocs.Annotation .NET API
description: Tìm hiểu cách thêm chú thích gạch chân văn bản vào tài liệu bằng GroupDocs.Annotation cho .NET. Tăng cường hợp tác và giao tiếp dễ dàng.
type: docs
weight: 27
url: /vi/net/unlocking-annotation-power/add-text-underline-annotation/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ tìm hiểu quy trình thêm chú thích gạch chân văn bản vào tài liệu bằng GroupDocs.Annotation cho .NET. Chú thích gạch chân văn bản có thể hữu ích để nhấn mạnh các phần cụ thể của tài liệu, chẳng hạn như các đoạn văn quan trọng hoặc các điểm chính.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo rằng bạn đã cài đặt các điều kiện tiên quyết sau:
1.  GroupDocs.Annotation for .NET: Tải xuống và cài đặt GroupDocs.Annotation for .NET từ[đây](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework trên hệ thống của mình.

## Nhập không gian tên
Đầu tiên, hãy nhập các không gian tên cần thiết vào dự án của chúng ta:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Bây giờ, hãy chia ví dụ thành nhiều bước:
## Bước 1: Xác định đường dẫn đầu ra
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Trong bước này, chúng tôi xác định đường dẫn đầu ra nơi tài liệu được chú thích sẽ được lưu.
## Bước 2: Khởi tạo Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Ở đây, chúng ta khởi tạo một thể hiện của`Annotator` lớp bằng cách cung cấp đường dẫn của tài liệu đầu vào.
## Bước 3: Tạo chú thích gạch chân
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // chỉ hoạt động được hỗ trợ các tài liệu Word và PDF
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
 Bước này liên quan đến việc tạo một`UnderlineAnnotation`đối tượng với nhiều thuộc tính khác nhau như màu phông chữ, thông báo, độ mờ, số trang, màu nền, màu gạch chân, điểm và câu trả lời.
## Bước 4: Thêm chú thích vào tài liệu
```csharp
annotator.Add(underline);
```
Ở đây, chúng tôi thêm chú thích gạch chân vào tài liệu.
## Bước 5: Lưu tài liệu chú thích
```csharp
annotator.Save(outputPath);
```
Cuối cùng, chúng ta lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định.

## Phần kết luận
Trong hướng dẫn này, chúng ta đã tìm hiểu cách thêm chú thích gạch chân văn bản vào tài liệu bằng GroupDocs.Annotation cho .NET. Thư viện mạnh mẽ này cung cấp nhiều tùy chọn chú thích khác nhau để nâng cao khả năng cộng tác và giao tiếp tài liệu.
## Câu hỏi thường gặp
### Tôi có thể tùy chỉnh hình thức của chú thích gạch chân không?
Có, bạn có thể tùy chỉnh các thuộc tính như màu sắc, độ mờ và vị trí theo yêu cầu của mình.
### GroupDocs.Annotation có tương thích với các định dạng tài liệu khác nhau không?
Có, GroupDocs.Annotation hỗ trợ nhiều định dạng tài liệu bao gồm Word và PDF.
### Tôi có thể thêm nhiều chú thích vào một tài liệu không?
Hoàn toàn có thể, GroupDocs.Annotation cho phép bạn thêm nhiều chú thích thuộc các loại khác nhau vào một tài liệu.
### Có bản dùng thử miễn phí cho GroupDocs.Annotation không?
 Có, bạn có thể truy cập phiên bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).
### Tôi có thể nhận hỗ trợ cho GroupDocs.Annotation ở đâu?
 Bạn có thể nhận hỗ trợ từ diễn đàn cộng đồng GroupDocs.Annotation[đây](https://forum.groupdocs.com/c/annotation/10).