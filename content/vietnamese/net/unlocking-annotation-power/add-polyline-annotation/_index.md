---
title: Thêm chú thích đa tuyến vào tài liệu
linktitle: Thêm chú thích đa tuyến vào tài liệu
second_title: GroupDocs.Annotation .NET API
description: Tìm hiểu cách thêm chú thích đa dòng vào tài liệu bằng GroupDocs.Annotation cho .NET. Tăng cường quá trình cộng tác và xem xét tài liệu một cách dễ dàng.
type: docs
weight: 18
url: /vi/net/unlocking-annotation-power/add-polyline-annotation/
---
## Giới thiệu
GroupDocs.Annotation for .NET là một công cụ mạnh mẽ cho phép các nhà phát triển chú thích các tài liệu PDF và Microsoft Office theo chương trình. Một trong những tính năng của nó là khả năng thêm chú thích đa tuyến vào tài liệu, tăng cường quá trình cộng tác và xem xét tài liệu.
## Điều kiện tiên quyết
Trước khi tiếp tục với hướng dẫn này, hãy đảm bảo bạn có những điều sau:
- Visual Studio được cài đặt trên hệ thống của bạn.
- Kiến thức cơ bản về ngôn ngữ lập trình C#.
-  GroupDocs.Annotation cho thư viện .NET đã được cài đặt. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/annotation/net/).

## Nhập không gian tên
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Bước 1: Xác định đường dẫn đầu ra
Đầu tiên, xác định đường dẫn đầu ra nơi tài liệu được chú thích sẽ được lưu.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Bước 2: Khởi tạo Annotator
Khởi tạo trình chú thích bằng cách cung cấp tên tài liệu đầu vào.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Bước 3: Tạo đối tượng chú thích Polyline
Tạo một đối tượng chú thích đa tuyến và đặt các thuộc tính của nó như vị trí, thông báo, độ mờ, màu bút, kiểu bút và chiều rộng bút.
```csharp
PolylineAnnotation polyline = new PolylineAnnotation
{
    Box = new Rectangle(250, 35, 102, 12),
    CreatedOn = DateTime.Now,
    Message = "This is polyline annotation",
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
    },
    SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.698685
4460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
};
```
## Bước 4: Thêm chú thích đa tuyến
Thêm chú thích đa tuyến vào tài liệu bằng đối tượng chú thích.
```csharp
annotator.Add(polyline);
```
## Bước 5: Lưu tài liệu
Lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định.
```csharp
annotator.Save(outputPath);
```
## Bước 6: Hiển thị thông báo thành công
Hiển thị thông báo xác nhận việc lưu tài liệu thành công.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Phần kết luận
Trong hướng dẫn này, chúng ta đã tìm hiểu cách thêm chú thích đa dòng vào tài liệu bằng GroupDocs.Annotation cho .NET. Tính năng này tăng cường quá trình cộng tác và đánh giá tài liệu, giúp người dùng dễ dàng truyền đạt phản hồi và đề xuất một cách hiệu quả hơn.
## Câu hỏi thường gặp
### GroupDocs.Annotation for .NET có tương thích với tất cả các định dạng tài liệu không?
GroupDocs.Annotation for .NET hỗ trợ các định dạng tài liệu phổ biến như định dạng PDF và Microsoft Office bao gồm Word, Excel và PowerPoint.
### Tôi có thể tùy chỉnh hình thức của chú thích không?
Có, bạn có thể tùy chỉnh các thuộc tính khác nhau của chú thích như màu sắc, độ mờ, kiểu và chiều rộng để phù hợp với yêu cầu của bạn.
### GroupDocs.Annotation cho .NET có cung cấp bản dùng thử miễn phí không?
 Có, bạn có thể tận dụng bản dùng thử miễn phí GroupDocs.Annotation cho .NET bằng cách truy cập[liên kết này](https://releases.groupdocs.com/).
### Tôi có thể tìm tài liệu về GroupDocs.Annotation cho .NET ở đâu?
 Bạn có thể tìm tài liệu về GroupDocs.Annotation for .NET[đây](https://reference.groupdocs.com/annotation/net/).
### Làm cách nào tôi có thể nhận được hỗ trợ cho bất kỳ vấn đề hoặc truy vấn nào liên quan đến GroupDocs.Annotation cho .NET?
 Bạn có thể nhận được hỗ trợ bằng cách truy cập diễn đàn GroupDocs.Annotation[đây](https://forum.groupdocs.com/c/annotation/10).