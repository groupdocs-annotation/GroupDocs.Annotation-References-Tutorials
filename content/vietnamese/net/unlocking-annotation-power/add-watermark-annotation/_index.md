---
title: Thêm chú thích hình mờ vào tài liệu
linktitle: Thêm chú thích hình mờ vào tài liệu
second_title: GroupDocs.Annotation .NET API
description: Tìm hiểu cách thêm chú thích hình mờ vào tài liệu của bạn một cách dễ dàng bằng GroupDocs.Annotation for .NET. Tăng cường sự rõ ràng và bảo mật của tài liệu.
weight: 28
url: /vi/net/unlocking-annotation-power/add-watermark-annotation/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ tìm hiểu quy trình thêm chú thích hình mờ vào tài liệu bằng GroupDocs.Annotation cho .NET. Chú thích hình mờ rất hữu ích để cho biết trạng thái của tài liệu, đánh dấu tài liệu đó là bí mật hoặc thêm bất kỳ thông tin liên quan nào khác.

## Điều kiện tiên quyết

Trước khi chúng ta bắt đầu, hãy đảm bảo bạn có những điều sau:

1.  GroupDocs.Annotation cho .NET: Bạn có thể tải xuống từ[đây](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Đảm bảo bạn đã cài đặt Visual Studio trên hệ thống của mình.
3. Kiến thức cơ bản về C#: Cần phải làm quen với ngôn ngữ lập trình C# để hiểu và triển khai các ví dụ về mã.

## Nhập không gian tên

Trước khi bắt đầu viết mã, hãy nhập các không gian tên cần thiết:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Bây giờ, hãy chia nhỏ quá trình thêm chú thích hình mờ thành nhiều bước:

## Bước 1: Xác định đường dẫn đầu ra

 Đầu tiên, chúng ta cần xác định đường dẫn đầu ra nơi tài liệu được chú thích sẽ được lưu. Chúng tôi sẽ sử dụng`Path` lớp từ`System.IO` không gian tên để kết hợp đường dẫn thư mục đầu ra với tên tệp.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Bước 2: Khởi tạo Annotator

Tiếp theo, chúng ta sẽ khởi tạo trình chú thích bằng cách cung cấp đường dẫn của tài liệu đầu vào. Điều này sẽ cho phép chúng tôi thêm chú thích vào tài liệu.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Mã chú thích sẽ ở đây
}
```

## Bước 3: Tạo chú thích hình mờ

Bây giờ, hãy tạo một đối tượng chú thích hình mờ với các thuộc tính mong muốn như góc, vị trí, văn bản, màu phông chữ, độ mờ, v.v.

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

 Bây giờ, chúng ta sẽ thêm chú thích hình mờ vào tài liệu bằng cách sử dụng`Add` phương thức của đối tượng chú thích.

```csharp
annotator.Add(watermark);
```

## Bước 5: Lưu tài liệu

Cuối cùng, chúng ta sẽ lưu tài liệu được chú thích vào đường dẫn đầu ra đã chỉ định.

```csharp
annotator.Save(outputPath);
```

## Phần kết luận

Trong hướng dẫn này, chúng ta đã tìm hiểu cách thêm chú thích hình mờ vào tài liệu bằng GroupDocs.Annotation cho .NET. Chú thích hình mờ là một công cụ có giá trị để đánh dấu tài liệu bằng thông tin liên quan hoặc cho biết trạng thái của chúng.

## Câu hỏi thường gặp

### Hỏi: Tôi có thể tùy chỉnh hình thức của chú thích hình mờ không?

Trả lời: Có, bạn có thể tùy chỉnh các thuộc tính khác nhau như văn bản, cỡ chữ, màu sắc, độ mờ, vị trí, v.v. để điều chỉnh hình mờ theo yêu cầu của bạn.

### Câu hỏi: GroupDocs.Annotation dành cho .NET có tương thích với các định dạng tài liệu khác nhau không?

Trả lời: Có, GroupDocs.Annotation hỗ trợ nhiều định dạng tài liệu bao gồm PDF, Microsoft Word, Excel, PowerPoint và định dạng hình ảnh.

### Câu hỏi: Tôi có thể thêm nhiều chú thích vào một tài liệu không?

Đáp: Hoàn toàn có thể, GroupDocs.Annotation cho phép bạn thêm nhiều chú thích thuộc các loại khác nhau vào một tài liệu, cho phép đánh dấu tài liệu toàn diện.

### Câu hỏi: GroupDocs.Annotation có hỗ trợ chú thích cộng tác không?

Trả lời: Có, GroupDocs.Annotation hỗ trợ chú thích cộng tác bằng cách cho phép người dùng thêm nhận xét, câu trả lời và chú thích, thúc đẩy sự cộng tác hiệu quả giữa các thành viên trong nhóm.

### Câu hỏi: Có phiên bản dùng thử cho GroupDocs.Annotation cho .NET không?

 Đ: Có, bạn có thể tải xuống phiên bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).