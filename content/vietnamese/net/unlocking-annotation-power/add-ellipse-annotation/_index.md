---
title: Thêm chú thích hình elip vào tài liệu
linktitle: Thêm chú thích hình elip vào tài liệu
second_title: GroupDocs.Annotation .NET API
description: Tìm hiểu cách thêm chú thích hình elip vào tài liệu trong .NET bằng GroupDocs.Annotation. Tăng cường hợp tác và giao tiếp dễ dàng.
type: docs
weight: 13
url: /vi/net/unlocking-annotation-power/add-ellipse-annotation/
---
## Giới thiệu
Trong hướng dẫn này, bạn sẽ tìm hiểu cách thêm chú thích hình elip vào tài liệu bằng GroupDocs.Annotation cho .NET. Hướng dẫn từng bước này sẽ hướng dẫn bạn thực hiện quy trình, đảm bảo rằng bạn hiểu rõ từng bước.
## Điều kiện tiên quyết
Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:
1.  GroupDocs.Annotation for .NET: Đảm bảo bạn đã tải xuống và cài đặt GroupDocs.Annotation for .NET. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/annotation/net/).
2. IDE (Môi trường phát triển tích hợp): Bạn sẽ cần cài đặt IDE trên hệ thống của mình, chẳng hạn như Visual Studio, để viết và thực thi mã.

## Nhập không gian tên
Đầu tiên, nhập các không gian tên cần thiết vào dự án của bạn:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Bước 1: Đặt đường dẫn đầu ra
Xác định đường dẫn đầu ra nơi tài liệu chú thích sẽ được lưu:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Bước 2: Khởi tạo Annotator
Khởi tạo trình chú thích bằng cách cung cấp đường dẫn tài liệu đầu vào:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Bước 3: Tạo chú thích hình elip
 Tạo một thể hiện của`EllipseAnnotation` lớp và thiết lập các thuộc tính của nó:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
## Bước 4: Thêm chú thích
Thêm chú thích hình elip vào tài liệu:
```csharp
annotator.Add(ellipse);
```
## Bước 5: Lưu tài liệu
Lưu tài liệu được chú thích vào đường dẫn đầu ra:
```csharp
annotator.Save(outputPath);
```

## Phần kết luận
Chúc mừng! Bạn đã thêm thành công chú thích hình elip vào tài liệu bằng GroupDocs.Annotation cho .NET. Bây giờ bạn có thể tích hợp chức năng này vào các ứng dụng .NET của mình để nâng cao khả năng cộng tác và liên lạc tài liệu.
## Câu hỏi thường gặp
### Tôi có thể tùy chỉnh hình thức của chú thích hình elip không?
Có, bạn có thể tùy chỉnh các thuộc tính khác nhau như màu nền, màu đường viền, độ mờ, v.v., theo yêu cầu của bạn.
### GroupDocs.Annotation for .NET có tương thích với tất cả các định dạng tài liệu không?
GroupDocs.Annotation for .NET hỗ trợ nhiều định dạng tài liệu bao gồm PDF, DOCX, PPTX, XLSX, v.v.
### Tôi có thể thêm nhiều chú thích vào một tài liệu không?
Có, bạn có thể thêm nhiều chú thích bao gồm hình elip, hình chữ nhật, văn bản, v.v. vào một tài liệu.
### Có phiên bản dùng thử nào dành cho mục đích thử nghiệm không?
 Có, bạn có thể tải xuống phiên bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/) để đánh giá các tính năng của nó.
### Tôi có thể nhận hỗ trợ kỹ thuật cho GroupDocs.Annotation cho .NET ở đâu?
 Bạn có thể nhận hỗ trợ kỹ thuật từ diễn đàn cộng đồng GroupDocs.Annotation[đây](https://forum.groupdocs.com/c/annotation/10).