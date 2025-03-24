---
title: Thêm chú thích khu vực vào tài liệu
linktitle: Thêm chú thích khu vực vào tài liệu
second_title: GroupDocs.Annotation .NET API
description: Nâng cao khả năng cộng tác tài liệu của bạn với Groupdocs.Annotation for .NET. Tìm hiểu cách thêm chú thích khu vực theo từng bước.
weight: 10
url: /vi/net/unlocking-annotation-power/add-area-annotation/
---
## Giới thiệu
Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình thêm chú thích vùng vào tài liệu bằng Groupdocs.Annotation cho .NET. Chú thích vùng là một tính năng có giá trị cho phép người dùng làm nổi bật các vùng cụ thể của tài liệu, mang lại sự rõ ràng và ngữ cảnh cho nội dung.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có các điều kiện tiên quyết sau:
1.  Groupdocs.Annotation for .NET: Đảm bảo bạn đã cài đặt các thư viện và phần phụ thuộc cần thiết. Bạn có thể tải chúng xuống từ[trang mạng](https://releases.groupdocs.com/annotation/net/).
2. Môi trường phát triển: Có môi trường phát triển phù hợp được thiết lập để phát triển .NET.

## Nhập không gian tên
Để bắt đầu, hãy nhập các không gian tên cần thiết vào dự án của bạn. Các không gian tên này chứa các lớp và phương thức cần thiết để làm việc với các chú thích.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

## Bước 1: Khởi tạo đường dẫn đầu ra
Xác định đường dẫn đầu ra nơi tài liệu chú thích sẽ được lưu.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Bước 2: Khởi tạo Annotator
 Tạo một thể hiện của`Annotator` lớp bằng cách chuyển đường dẫn của tài liệu làm tham số.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Mã chú thích sẽ ở đây
}
```
## Bước 3: Tạo chú thích khu vực
Xác định các thuộc tính của chú thích khu vực, chẳng hạn như màu nền, vị trí, thông báo, độ mờ, v.v.
```csharp
AreaAnnotation area = new AreaAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is area annotation",
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
 Thêm chú thích khu vực vào tài liệu bằng cách sử dụng`Add` phương pháp của`Annotator` ví dụ.
```csharp
annotator.Add(area);
```
## Bước 5: Lưu tài liệu
Lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định.
```csharp
annotator.Save(outputPath);
```
## Bước 6: Hiển thị thông báo thành công
Thông báo cho người dùng rằng tài liệu đã được chú thích và lưu thành công.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Phần kết luận
Trong hướng dẫn này, chúng ta đã tìm hiểu cách thêm chú thích vùng vào tài liệu bằng Groupdocs.Annotation cho .NET. Bằng cách làm theo hướng dẫn từng bước, bạn có thể dễ dàng nâng cao tài liệu của mình bằng các chú thích có giá trị, cải thiện khả năng cộng tác và hiểu biết.
## Câu hỏi thường gặp
### Tôi có thể tùy chỉnh giao diện của chú thích khu vực không?
Có, bạn có thể tùy chỉnh nhiều khía cạnh khác nhau như màu nền, độ mờ, kiểu bút, v.v. để phù hợp với sở thích của bạn.
### Groupdocs.Annotation có tương thích với các định dạng tài liệu khác không?
Có, Groupdocs.Annotation hỗ trợ nhiều định dạng tài liệu khác nhau bao gồm PDF, DOCX, PPTX, v.v.
### Tôi có thể thêm nhiều chú thích vào cùng một tài liệu không?
Hoàn toàn có thể, bạn có thể thêm nhiều chú thích thuộc các loại khác nhau vào cùng một tài liệu nếu cần.
### Groupdocs.Annotation có cung cấp khả năng tương thích đa nền tảng không?
Có, Groupdocs.Annotation tương thích với .NET framework, khiến nó phù hợp với môi trường phát triển Windows, Linux và macOS.
### Có phiên bản dùng thử nào dành cho mục đích thử nghiệm không?
 Có, bạn có thể truy cập phiên bản dùng thử miễn phí từ[trang mạng](https://releases.groupdocs.com/).