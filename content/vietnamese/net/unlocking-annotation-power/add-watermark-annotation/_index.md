---
"description": "Tìm hiểu cách thêm chú thích hình mờ vào tài liệu của bạn một cách dễ dàng bằng GroupDocs.Annotation cho .NET. Tăng cường tính rõ ràng và bảo mật của tài liệu."
"linktitle": "Thêm chú thích hình mờ vào tài liệu"
"second_title": "GroupDocs.Chú thích API .NET"
"title": "Thêm chú thích hình mờ vào tài liệu"
"url": "/vi/net/unlocking-annotation-power/add-watermark-annotation/"
"weight": 28
---

# Thêm chú thích hình mờ vào tài liệu

## Giới thiệu
Trong hướng dẫn này, chúng tôi sẽ hướng dẫn quy trình thêm chú thích hình mờ vào tài liệu bằng GroupDocs.Annotation cho .NET. Chú thích hình mờ hữu ích để chỉ ra trạng thái của tài liệu, đánh dấu tài liệu là bí mật hoặc thêm bất kỳ thông tin liên quan nào khác.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

1. GroupDocs.Annotation cho .NET: Bạn có thể tải xuống từ [đây](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Đảm bảo bạn đã cài đặt Visual Studio trên hệ thống của mình.
3. Kiến thức cơ bản về C#: Cần phải quen thuộc với ngôn ngữ lập trình C# để hiểu và triển khai các ví dụ mã.

## Nhập không gian tên

Trước khi bắt đầu viết mã, hãy nhập các không gian tên cần thiết:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Bây giờ, chúng ta hãy chia nhỏ quy trình thêm chú thích hình mờ thành nhiều bước:

## Bước 1: Xác định Đường dẫn đầu ra

Đầu tiên, chúng ta cần xác định đường dẫn đầu ra nơi tài liệu được chú thích sẽ được lưu. Chúng ta sẽ sử dụng `Path` lớp từ `System.IO` không gian tên để kết hợp đường dẫn thư mục đầu ra với tên tệp.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Bước 2: Khởi tạo Annotator

Tiếp theo, chúng ta sẽ khởi tạo trình chú thích bằng cách cung cấp đường dẫn của tài liệu đầu vào. Điều này sẽ cho phép chúng ta thêm chú thích vào tài liệu.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Mã chú thích sẽ được đặt ở đây
}
```

## Bước 3: Tạo chú thích hình mờ

Bây giờ, chúng ta hãy tạo một đối tượng chú thích hình mờ có các thuộc tính mong muốn như góc, vị trí, văn bản, màu phông chữ, độ mờ, v.v.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## Bước 4: Thêm chú thích hình mờ

Bây giờ, chúng ta sẽ thêm chú thích hình mờ vào tài liệu bằng cách sử dụng `Add` phương thức của đối tượng chú thích.

```csharp
annotator.Add(watermark);
```

## Bước 5: Lưu tài liệu

Cuối cùng, chúng ta sẽ lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định.

```csharp
annotator.Save(outputPath);
```

## Phần kết luận

Trong hướng dẫn này, chúng ta đã học cách thêm chú thích hình mờ vào tài liệu bằng GroupDocs.Annotation cho .NET. Chú thích hình mờ là một công cụ hữu ích để đánh dấu tài liệu bằng thông tin có liên quan hoặc chỉ ra trạng thái của chúng.

## Câu hỏi thường gặp

### H: Tôi có thể tùy chỉnh giao diện của chú thích hình mờ không?

A: Có, bạn có thể tùy chỉnh nhiều thuộc tính khác nhau như văn bản, cỡ chữ, màu sắc, độ mờ, vị trí, v.v. để tùy chỉnh hình mờ theo yêu cầu của bạn.

### H: GroupDocs.Annotation cho .NET có tương thích với các định dạng tài liệu khác nhau không?

A: Có, GroupDocs.Annotation hỗ trợ nhiều định dạng tài liệu bao gồm PDF, Microsoft Word, Excel, PowerPoint và định dạng hình ảnh.

### H: Tôi có thể thêm nhiều chú thích vào một tài liệu không?

A: Hoàn toàn có thể, GroupDocs.Annotation cho phép bạn thêm nhiều chú thích thuộc nhiều loại khác nhau vào một tài liệu, cho phép đánh dấu tài liệu toàn diện.

### H: GroupDocs.Annotation có hỗ trợ chú thích cộng tác không?

A: Có, GroupDocs.Annotation hỗ trợ chú thích cộng tác bằng cách cho phép người dùng thêm bình luận, trả lời và chú thích, thúc đẩy sự cộng tác hiệu quả giữa các thành viên trong nhóm.

### H: Có phiên bản dùng thử của GroupDocs.Annotation dành cho .NET không?

A: Có, bạn có thể tải xuống phiên bản dùng thử miễn phí từ [đây](https://releases.groupdocs.com/).