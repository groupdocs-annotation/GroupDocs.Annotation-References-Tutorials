---
title: Thêm chú thích khoảng cách vào tài liệu
linktitle: Thêm chú thích khoảng cách vào tài liệu
second_title: GroupDocs.Annotation .NET API
description: Tìm hiểu cách thêm chú thích khoảng cách vào tài liệu bằng GroupDocs.Annotation cho .NET. Tăng cường hợp tác và giao tiếp dễ dàng.
weight: 12
url: /vi/net/unlocking-annotation-power/add-distance-annotation/
---

# Thêm chú thích khoảng cách vào tài liệu

## Giới thiệu
Trong hướng dẫn này, bạn sẽ tìm hiểu cách thêm chú thích khoảng cách vào tài liệu bằng GroupDocs.Annotation cho .NET. Thực hiện theo các bước sau để hoàn thành nhiệm vụ:
## Điều kiện tiên quyết

Đảm bảo rằng bạn có sẵn các điều kiện tiên quyết sau đây trước khi tiếp tục:

-  GroupDocs.Annotation for .NET Library: Tải xuống và cài đặt thư viện GroupDocs.Annotation for .NET từ[liên kết này](https://releases.groupdocs.com/annotation/net/).
- Tài liệu cần chú thích: Chuẩn bị tài liệu (ví dụ: PDF) mà bạn muốn thêm chú thích khoảng cách.
- Môi trường phát triển: Thiết lập môi trường phát triển của bạn với Visual Studio hoặc bất kỳ IDE nào khác mà bạn chọn.

## Nhập không gian tên

Trước khi bắt đầu, hãy đảm bảo bao gồm các không gian tên cần thiết trong mã của bạn. Những không gian tên này rất cần thiết để truy cập các lớp và phương thức được yêu cầu.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Bước 1: Khởi tạo Annotator

 Bắt đầu bằng cách khởi tạo`Annotator` đối tượng bằng đường dẫn đến tài liệu bạn muốn chú thích.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Mã chú thích sẽ ở đây
}
```

## Bước 2: Tạo chú thích khoảng cách

 Bây giờ, hãy tạo một`DistanceAnnotation` đối tượng và định cấu hình các thuộc tính của nó như kích thước hộp, thông báo, độ mờ, màu bút, v.v.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
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

## Bước 3: Thêm chú thích

 Thêm chú thích khoảng cách đã tạo vào tài liệu bằng cách sử dụng`Add` phương thức của đối tượng chú thích.

```csharp
annotator.Add(distance);
```

## Bước 4: Lưu tài liệu

Lưu tài liệu có chú thích vào vị trí mong muốn trên hệ thống của bạn.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Bước 5: Hiển thị xác nhận

Cuối cùng hiển thị thông báo xác nhận việc lưu thành công tài liệu được chú thích.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Phần kết luận

Thêm chú thích khoảng cách vào tài liệu bằng GroupDocs.Annotation cho .NET là một quá trình đơn giản. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể nâng cao tài liệu của mình bằng các chú thích có giá trị, hỗ trợ cộng tác và giao tiếp tốt hơn.

## Câu hỏi thường gặp

### Câu hỏi: Tôi có thể tùy chỉnh hình thức của chú thích khoảng cách không?

Trả lời: Có, bạn có thể tùy chỉnh các thuộc tính khác nhau như màu sắc, độ mờ, kiểu đường kẻ, v.v. để phù hợp với yêu cầu của bạn.

### Câu hỏi: GroupDocs.Annotation có hỗ trợ chú thích trên các loại tài liệu khác nhau không?

Trả lời: Có, GroupDocs.Annotation hỗ trợ chú thích trên nhiều định dạng tài liệu bao gồm PDF, Word, Excel, PowerPoint, v.v.

### Câu hỏi: Có bản dùng thử miễn phí cho GroupDocs.Annotation không?

 Đáp: Có, bạn có thể truy cập bản dùng thử miễn phí của GroupDocs.Annotation từ[liên kết này](https://releases.groupdocs.com/).

### Câu hỏi: Tôi có thể tìm tài liệu về GroupDocs.Annotation cho .NET ở đâu?

 A: Bạn có thể tham khảo tài liệu chi tiết có sẵn[đây](https://tutorials.groupdocs.com/annotation/net/).

### Câu hỏi: Làm cách nào tôi có thể nhận được hỗ trợ hoặc trợ giúp với GroupDocs.Annotation?

 Trả lời: Bạn có thể tìm kiếm sự hỗ trợ và trợ giúp từ diễn đàn cộng đồng GroupDocs.Annotation[đây](https://forum.groupdocs.com/c/annotation/10).