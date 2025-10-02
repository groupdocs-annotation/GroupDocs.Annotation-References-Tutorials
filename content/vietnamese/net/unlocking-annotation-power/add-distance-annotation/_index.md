---
"description": "Tìm hiểu cách thêm chú thích khoảng cách vào tài liệu bằng GroupDocs.Annotation cho .NET. Tăng cường cộng tác và giao tiếp dễ dàng."
"linktitle": "Thêm chú thích khoảng cách vào tài liệu"
"second_title": "GroupDocs.Chú thích API .NET"
"title": "Thêm chú thích khoảng cách vào tài liệu"
"url": "/vi/net/unlocking-annotation-power/add-distance-annotation/"
type: docs
"weight": 12
---

# Thêm chú thích khoảng cách vào tài liệu

## Giới thiệu
Trong hướng dẫn này, bạn sẽ học cách thêm chú thích khoảng cách vào tài liệu bằng GroupDocs.Annotation cho .NET. Thực hiện theo các bước sau để hoàn thành nhiệm vụ:
## Điều kiện tiên quyết

Hãy đảm bảo rằng bạn đã đáp ứng đủ các điều kiện tiên quyết sau đây trước khi tiếp tục:

- GroupDocs.Annotation cho Thư viện .NET: Tải xuống và cài đặt GroupDocs.Annotation cho thư viện .NET từ [liên kết này](https://releases.groupdocs.com/annotation/net/).
- Tài liệu cần chú thích: Chuẩn bị tài liệu (ví dụ: PDF) mà bạn muốn thêm chú thích khoảng cách.
- Môi trường phát triển: Thiết lập môi trường phát triển của bạn bằng Visual Studio hoặc bất kỳ IDE nào khác mà bạn chọn.

## Nhập không gian tên

Trước khi bắt đầu, hãy đảm bảo bao gồm các không gian tên cần thiết trong mã của bạn. Các không gian tên này rất cần thiết để truy cập các lớp và phương thức cần thiết.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Bước 1: Khởi tạo Annotator

Bắt đầu bằng cách khởi tạo `Annotator` đối tượng có đường dẫn đến tài liệu bạn muốn chú thích.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Mã chú thích sẽ được đặt ở đây
}
```

## Bước 2: Tạo chú thích khoảng cách

Bây giờ, hãy tạo một `DistanceAnnotation` đối tượng và cấu hình các thuộc tính của nó như kích thước hộp, thông điệp, độ mờ, màu bút, v.v.

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

Thêm chú thích khoảng cách đã tạo vào tài liệu bằng cách sử dụng `Add` phương thức của đối tượng chú thích.

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

Cuối cùng, hiển thị thông báo xác nhận việc lưu tài liệu có chú thích thành công.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Phần kết luận

Thêm chú thích khoảng cách vào tài liệu bằng GroupDocs.Annotation cho .NET là một quá trình đơn giản. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể cải thiện tài liệu của mình bằng các chú thích có giá trị, tạo điều kiện cho sự cộng tác và giao tiếp tốt hơn.

## Câu hỏi thường gặp

### H: Tôi có thể tùy chỉnh giao diện của chú thích khoảng cách không?

A: Có, bạn có thể tùy chỉnh nhiều thuộc tính khác nhau như màu sắc, độ mờ, kiểu đường nét, v.v. để phù hợp với yêu cầu của bạn.

### H: GroupDocs.Annotation có hỗ trợ chú thích trên các loại tài liệu khác nhau không?

A: Có, GroupDocs.Annotation hỗ trợ chú thích trên nhiều định dạng tài liệu bao gồm PDF, Word, Excel, PowerPoint, v.v.

### H: Có bản dùng thử miễn phí cho GroupDocs.Annotation không?

A: Có, bạn có thể truy cập dùng thử miễn phí GroupDocs.Annotation từ [liên kết này](https://releases.groupdocs.com/).

### H: Tôi có thể tìm tài liệu về GroupDocs.Annotation cho .NET ở đâu?

A: Bạn có thể tham khảo tài liệu chi tiết có sẵn [đây](https://tutorials.groupdocs.com/annotation/net/).

### H: Tôi có thể nhận được hỗ trợ hoặc trợ giúp về GroupDocs.Annotation như thế nào?

A: Bạn có thể tìm kiếm sự hỗ trợ và trợ giúp từ diễn đàn cộng đồng GroupDocs.Annotation [đây](https://forum.groupdocs.com/c/annotation/10).