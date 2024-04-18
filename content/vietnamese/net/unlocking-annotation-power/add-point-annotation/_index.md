---
title: Thêm chú thích điểm vào tài liệu
linktitle: Thêm chú thích điểm vào tài liệu
second_title: GroupDocs.Annotation .NET API
description: Tìm hiểu cách thêm Chú thích điểm vào tệp PDF bằng GroupDocs.Annotation cho .NET. Hướng dẫn từng bước để tích hợp liền mạch.
type: docs
weight: 17
url: /vi/net/unlocking-annotation-power/add-point-annotation/
---
## Giới thiệu
GroupDocs.Annotation for .NET là một công cụ mạnh mẽ cho phép các nhà phát triển thêm nhiều loại chú thích khác nhau vào tài liệu theo chương trình. Trong hướng dẫn này, chúng tôi sẽ tập trung vào việc thêm Chú thích điểm vào tài liệu bằng C#.
## Điều kiện tiên quyết
Trước khi chúng ta bắt đầu, hãy đảm bảo bạn có những điều sau:
1. Hiểu biết cơ bản về ngôn ngữ lập trình C#.
2. Visual Studio được cài đặt trên hệ thống của bạn.
3.  GroupDocs.Annotation cho thư viện .NET đã được cài đặt. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/annotation/net/).

## Nhập các không gian tên cần thiết
Để bắt đầu, bạn cần nhập các không gian tên cần thiết vào dự án C# của mình:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Bước 1: Xác định đường dẫn đầu ra
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Trong bước này, chúng tôi xác định đường dẫn đầu ra nơi tài liệu được chú thích sẽ được lưu.
## Bước 2: Khởi tạo Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Ở đây, chúng ta khởi tạo`Annotator` đối tượng với tài liệu đầu vào ("input.pdf").
## Bước 3: Tạo chú thích điểm
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
 Ở bước này, chúng ta tạo một`PointAnnotation` đối tượng và chỉ định các thuộc tính của nó như vị trí, tin nhắn, số trang và câu trả lời.
## Bước 4: Thêm chú thích
```csharp
annotator.Add(point);
```
Ở đây, chúng tôi thêm chú thích điểm đã tạo vào tài liệu.
## Bước 5: Lưu tài liệu
```csharp
annotator.Save(outputPath);
```
Cuối cùng, chúng ta lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định.

## Phần kết luận
Trong hướng dẫn này, chúng ta đã tìm hiểu cách thêm Chú thích Điểm vào tài liệu bằng GroupDocs.Annotation cho .NET. Với thư viện mạnh mẽ này, bạn có thể nâng cao ứng dụng quản lý tài liệu của mình bằng cách kết hợp các chức năng chú thích.
## Câu hỏi thường gặp
### GroupDocs.Annotation for .NET có tương thích với tất cả các định dạng tài liệu không?
Có, GroupDocs.Annotation for .NET hỗ trợ nhiều định dạng tài liệu bao gồm PDF, Microsoft Word, Excel, PowerPoint, v.v.
### Tôi có thể tùy chỉnh hình thức của chú thích không?
Tuyệt đối! GroupDocs.Annotation for .NET cung cấp các tùy chọn mở rộng để tùy chỉnh giao diện của chú thích cho phù hợp với nhu cầu ứng dụng của bạn.
### Có bản dùng thử miễn phí GroupDocs.Annotation cho .NET không?
 Có, bạn có thể tận dụng bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).
### Làm cách nào tôi có thể nhận được hỗ trợ cho bất kỳ vấn đề hoặc truy vấn nào liên quan đến GroupDocs.Annotation cho .NET?
 Bạn có thể nhận hỗ trợ từ diễn đàn GroupDocs.Annotation[đây](https://forum.groupdocs.com/c/annotation/10).
### Tôi có thể xin giấy phép tạm thời cho mục đích thử nghiệm không?
 Có, bạn có thể xin giấy phép tạm thời từ[đây](https://purchase.groupdocs.com/temporary-license/).