---
title: Thêm chú thích đánh dấu văn bản vào tài liệu
linktitle: Thêm chú thích đánh dấu văn bản vào tài liệu
second_title: GroupDocs.Annotation .NET API
description: Tìm hiểu cách thêm chú thích đánh dấu văn bản vào tài liệu bằng GroupDocs.Annotation cho .NET. Nâng cao sự hợp tác và năng suất với tính năng toàn diện này.
type: docs
weight: 22
url: /vi/net/unlocking-annotation-power/add-text-highlight-annotation/
---
## Giới thiệu
Trong lĩnh vực cộng tác và quản lý tài liệu, GroupDocs.Annotation dành cho .NET nổi lên như một giải pháp mạnh mẽ, trao quyền cho các nhà phát triển tích hợp liền mạch các chú thích đánh dấu văn bản vào ứng dụng của họ. Hướng dẫn này đóng vai trò là hướng dẫn toàn diện để thêm chú thích đánh dấu văn bản vào tài liệu bằng GroupDocs.Annotation cho .NET. Thông qua các hướng dẫn từng bước và giải thích chi tiết, bạn sẽ thành thạo trong việc khai thác các khả năng của thư viện mạnh mẽ này.
## Điều kiện tiên quyết
Trước khi đi sâu vào việc triển khai chú thích đánh dấu văn bản, hãy đảm bảo rằng bạn có sẵn các điều kiện tiên quyết sau:
1. Thiết lập môi trường: Có môi trường phát triển phù hợp được định cấu hình để phát triển .NET.
2.  Cài đặt GroupDocs.Annotation cho .NET: Tải xuống và cài đặt GroupDocs.Annotation cho .NET từ gói được cung cấp[Liên kết tải xuống](https://releases.groupdocs.com/annotation/net/).
3. Làm quen với C#: Hiểu biết cơ bản về ngôn ngữ lập trình C#.
4. Tài liệu cần chú thích: Chuẩn bị một tài liệu (ví dụ: PDF) mà bạn định chú thích.

## Nhập không gian tên
Để bắt đầu, hãy nhập các vùng tên cần thiết trong mã C# của bạn để sử dụng các chức năng của GroupDocs.Annotation cho .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Bây giờ, hãy chia nhỏ quá trình thêm chú thích đánh dấu văn bản thành nhiều bước:
## Bước 1: Xác định đường dẫn đầu ra
Chỉ định đường dẫn đầu ra nơi tài liệu được chú thích sẽ được lưu:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Bước 2: Khởi tạo Annotator
 Tạo một thể hiện của`Annotator` class, truyền tên tệp tài liệu làm tham số:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Bước 3: Tạo chú thích nổi bật
 Khởi tạo một`HighlightAnnotation` đối tượng và cấu hình các thuộc tính của nó:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
## Bước 4: Thêm chú thích
Thêm chú thích đánh dấu đã tạo vào tài liệu:
```csharp
annotator.Add(highlight);
```
## Bước 5: Lưu tài liệu chú thích
Lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định:
```csharp
annotator.Save(outputPath);
```

## Phần kết luận
Tóm lại, GroupDocs.Annotation dành cho .NET cung cấp một cách tiếp cận hợp lý để kết hợp các chú thích đánh dấu văn bản vào tài liệu. Bằng cách làm theo các bước được nêu trong hướng dẫn này, các nhà phát triển có thể nâng cao hiệu suất và cộng tác tài liệu một cách liền mạch trong các ứng dụng của họ.
## Câu hỏi thường gặp
### GroupDocs.Annotation for .NET có tương thích với tất cả các định dạng tài liệu không?
GroupDocs.Annotation for .NET hỗ trợ nhiều định dạng tài liệu khác nhau, bao gồm PDF, Word, Excel, v.v. Tham khảo tài liệu để biết danh sách đầy đủ.
### Chú thích có thể được tùy chỉnh theo yêu cầu cụ thể không?
Có, nhà phát triển có toàn quyền kiểm soát các thuộc tính và hình thức của chú thích, cho phép tùy chỉnh để đáp ứng nhu cầu đa dạng.
### Có bản dùng thử miễn phí GroupDocs.Annotation cho .NET không?
 Có, bạn có thể khám phá các tính năng của GroupDocs.Annotation for .NET bằng cách truy cập bản dùng thử miễn phí từ trang được cung cấp[liên kết](https://releases.groupdocs.com/).
### Làm cách nào tôi có thể nhận được hỗ trợ cho bất kỳ vấn đề hoặc truy vấn nào liên quan đến GroupDocs.Annotation cho .NET?
 Để được hỗ trợ và trợ giúp, bạn có thể truy cập diễn đàn GroupDocs.Annotation[đây](https://forum.groupdocs.com/c/annotation/10).
### Những tùy chọn cấp phép nào có sẵn cho GroupDocs.Annotation cho .NET?
 GroupDocs.Annotation for .NET cung cấp nhiều tùy chọn cấp phép khác nhau, bao gồm giấy phép tạm thời cho mục đích thử nghiệm và giấy phép thương mại cho môi trường sản xuất. Truy cập trang mua hàng[đây](https://purchase.groupdocs.com/buy) để biết thêm chi tiết.