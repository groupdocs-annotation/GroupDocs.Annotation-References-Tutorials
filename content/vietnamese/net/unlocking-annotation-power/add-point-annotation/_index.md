---
"description": "Tìm hiểu cách thêm chú thích điểm vào tệp PDF bằng GroupDocs.Annotation cho .NET. Hướng dẫn từng bước để tích hợp liền mạch."
"linktitle": "Thêm chú thích điểm vào tài liệu"
"second_title": "GroupDocs.Chú thích API .NET"
"title": "Thêm chú thích điểm vào tài liệu"
"url": "/vi/net/unlocking-annotation-power/add-point-annotation/"
"weight": 17
---

# Thêm chú thích điểm vào tài liệu

## Giới thiệu
GroupDocs.Annotation for .NET là một công cụ mạnh mẽ cho phép các nhà phát triển thêm nhiều loại chú thích khác nhau vào tài liệu theo chương trình. Trong hướng dẫn này, chúng tôi sẽ tập trung vào việc thêm Chú thích điểm vào tài liệu bằng C#.
## Điều kiện tiên quyết
Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:
1. Hiểu biết cơ bản về ngôn ngữ lập trình C#.
2. Visual Studio được cài đặt trên hệ thống của bạn.
3. GroupDocs.Annotation cho thư viện .NET đã được cài đặt. Bạn có thể tải xuống từ [đây](https://releases.groupdocs.com/annotation/net/).

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
## Bước 1: Xác định Đường dẫn đầu ra
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Ở bước này, chúng ta sẽ xác định đường dẫn đầu ra nơi tài liệu có chú thích sẽ được lưu.
## Bước 2: Khởi tạo Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Ở đây, chúng tôi khởi tạo `Annotator` đối tượng có tài liệu đầu vào ("input.pdf").
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
Trong bước này, chúng ta tạo ra một `PointAnnotation` đối tượng và chỉ định các thuộc tính của nó như vị trí, tin nhắn, số trang và phản hồi.
## Bước 4: Thêm chú thích
```csharp
annotator.Add(point);
```
Tại đây, chúng ta thêm chú thích điểm đã tạo vào tài liệu.
## Bước 5: Lưu tài liệu
```csharp
annotator.Save(outputPath);
```
Cuối cùng, chúng ta lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định.

## Phần kết luận
Trong hướng dẫn này, chúng ta đã học cách thêm Chú thích điểm vào tài liệu bằng GroupDocs.Annotation cho .NET. Với thư viện mạnh mẽ này, bạn có thể nâng cao ứng dụng quản lý tài liệu của mình bằng cách kết hợp các chức năng chú thích.
## Câu hỏi thường gặp
### GroupDocs.Annotation cho .NET có tương thích với mọi định dạng tài liệu không?
Có, GroupDocs.Annotation for .NET hỗ trợ nhiều định dạng tài liệu bao gồm PDF, Microsoft Word, Excel, PowerPoint, v.v.
### Tôi có thể tùy chỉnh giao diện của chú thích không?
Hoàn toàn đúng! GroupDocs.Annotation cho .NET cung cấp nhiều tùy chọn để tùy chỉnh giao diện chú thích sao cho phù hợp với nhu cầu của ứng dụng.
### Có bản dùng thử miễn phí nào cho GroupDocs.Annotation dành cho .NET không?
Có, bạn có thể tận dụng bản dùng thử miễn phí từ [đây](https://releases.groupdocs.com/).
### Tôi có thể nhận được hỗ trợ cho bất kỳ vấn đề hoặc thắc mắc nào liên quan đến GroupDocs.Annotation cho .NET bằng cách nào?
Bạn có thể nhận được sự hỗ trợ từ diễn đàn GroupDocs.Annotation [đây](https://forum.groupdocs.com/c/annotation/10).
### Tôi có thể xin giấy phép tạm thời để phục vụ mục đích thử nghiệm không?
Có, bạn có thể xin giấy phép tạm thời từ [đây](https://purchase.groupdocs.com/temporary-license/).