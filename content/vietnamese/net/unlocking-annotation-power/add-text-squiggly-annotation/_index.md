---
title: Thêm chú thích nguệch ngoạc văn bản vào tài liệu
linktitle: Thêm chú thích nguệch ngoạc văn bản vào tài liệu
second_title: GroupDocs.Annotation .NET API
description: Tìm hiểu cách dễ dàng thêm các chú thích nguệch ngoạc văn bản vào tài liệu bằng Groupdocs.Annotation cho .NET. Tăng cường hợp tác và quá trình xem xét tài liệu.
weight: 25
url: /vi/net/unlocking-annotation-power/add-text-squiggly-annotation/
---
## Giới thiệu

Groupdocs.Annotation for .NET là một thư viện linh hoạt cho phép các nhà phát triển tích hợp khả năng chú thích mạnh mẽ vào các ứng dụng .NET của họ một cách dễ dàng. Cho dù bạn đang làm việc với tệp PDF, tài liệu Word hay các định dạng tệp phổ biến khác, Groupdocs.Annotation đều cung cấp giải pháp liền mạch để chú thích và nâng cao khả năng cộng tác trên tài liệu.

## Điều kiện tiên quyết

Trước khi đi sâu vào hướng dẫn, hãy đảm bảo rằng bạn có sẵn các điều kiện tiên quyết sau:

## Nhập không gian tên

Đảm bảo nhập các không gian tên cần thiết để truy cập các chức năng do Groupdocs.Annotation cung cấp cho .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Bây giờ chúng ta đã đề cập đến các điều kiện tiên quyết, hãy chia nhỏ quy trình thêm chú thích nguệch ngoạc văn bản thành nhiều bước.

## Bước 1: Xác định đường dẫn đầu ra

Xác định đường dẫn nơi tài liệu có chú thích sẽ được lưu.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Bước 2: Khởi tạo Annotator

Khởi tạo đối tượng Annotator bằng cách cung cấp đường dẫn tài liệu đầu vào.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Mã chú thích ở đây
}
```

## Bước 3: Tạo chú thích nguệch ngoạc

Tạo một đối tượng SquigglyAnnotation và chỉ định các thuộc tính của nó.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

Thêm chú thích nguệch ngoạc đã tạo vào tài liệu.

```csharp
annotator.Add(squiggly);
```

## Bước 5: Lưu tài liệu

Lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định.

```csharp
annotator.Save(outputPath);
```

## Bước 6: Hiển thị xác nhận

Hiển thị thông báo xác nhận việc lưu thành công tài liệu được chú thích.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Phần kết luận

Tóm lại, Groupdocs.Annotation for .NET cung cấp cho các nhà phát triển một bộ công cụ mạnh mẽ để tích hợp các chức năng chú thích tài liệu vào các ứng dụng .NET của họ một cách liền mạch. Bằng cách làm theo hướng dẫn từng bước này, bạn có thể dễ dàng thêm các chú thích nguệch ngoạc bằng văn bản vào tài liệu của mình, tăng cường quá trình cộng tác và đánh giá tài liệu.

## Câu hỏi thường gặp

### Câu hỏi: Groupdocs.Annotation có thể hỗ trợ chú thích trên nhiều định dạng tệp khác nhau không?

Trả lời: Có, Groupdocs.Annotation hỗ trợ chú thích trên nhiều định dạng tệp, bao gồm PDF, tài liệu Word, trang tính Excel, v.v.

### Câu hỏi: Groupdocs.Annotation có tương thích với cả ứng dụng web và máy tính để bàn không?

Đ: Chắc chắn rồi! Groupdocs.Annotation có thể được tích hợp liền mạch vào cả ứng dụng web và máy tính để bàn, mang lại sự linh hoạt và linh hoạt.

### Câu hỏi: Có bất kỳ tùy chọn cấp phép nào dành cho Groupdocs.Annotation không?

Trả lời: Có, Groupdocs.Annotation cung cấp các tùy chọn cấp phép linh hoạt được điều chỉnh để phù hợp với nhu cầu của cá nhân hoặc doanh nghiệp, bao gồm cả giấy phép tạm thời cho mục đích dùng thử.

### Câu hỏi: Các chú thích được tạo bằng Groupdocs.Annotation có thể được tùy chỉnh không?

Đ: Chắc chắn rồi! Groupdocs.Annotation cung cấp các tùy chọn tùy chỉnh mở rộng cho chú thích, cho phép nhà phát triển điều chỉnh chú thích theo yêu cầu cụ thể của họ.

### Câu hỏi: Groupdocs.Annotation có cung cấp hỗ trợ và tài liệu cho nhà phát triển không?

Đ: Thật vậy! Groupdocs.Annotation cung cấp tài liệu toàn diện và các diễn đàn hỗ trợ chuyên dụng để hỗ trợ các nhà phát triển sử dụng các tính năng của nó một cách hiệu quả.