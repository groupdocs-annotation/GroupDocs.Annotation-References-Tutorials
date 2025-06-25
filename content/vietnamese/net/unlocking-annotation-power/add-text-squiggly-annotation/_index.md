---
"description": "Tìm hiểu cách dễ dàng thêm chú thích dạng văn bản ngoằn ngoèo vào tài liệu bằng Groupdocs.Annotation cho .NET. Nâng cao quy trình cộng tác và xem xét tài liệu."
"linktitle": "Thêm chú thích ngoằn ngoèo dạng văn bản vào tài liệu"
"second_title": "GroupDocs.Chú thích API .NET"
"title": "Thêm chú thích ngoằn ngoèo dạng văn bản vào tài liệu"
"url": "/vi/net/unlocking-annotation-power/add-text-squiggly-annotation/"
"weight": 25
---

# Thêm chú thích ngoằn ngoèo dạng văn bản vào tài liệu

## Giới thiệu

Groupdocs.Annotation for .NET là một thư viện đa năng cho phép các nhà phát triển tích hợp các khả năng chú thích mạnh mẽ vào các ứng dụng .NET của họ một cách dễ dàng. Cho dù bạn đang làm việc với PDF, tài liệu Word hay các định dạng tệp phổ biến khác, Groupdocs.Annotation cung cấp giải pháp liền mạch để chú thích và tăng cường cộng tác tài liệu.

## Điều kiện tiên quyết

Trước khi bắt đầu hướng dẫn, hãy đảm bảo rằng bạn đã đáp ứng đủ các điều kiện tiên quyết sau:

## Nhập không gian tên

Hãy đảm bảo nhập các không gian tên cần thiết để truy cập các chức năng do Groupdocs.Annotation cung cấp cho .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Bây giờ chúng ta đã nắm được các điều kiện tiên quyết, hãy chia nhỏ quy trình thêm chú thích dạng ngoằn ngoèo cho văn bản thành nhiều bước.

## Bước 1: Xác định Đường dẫn đầu ra

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

## Bước 3: Tạo chú thích Squiggly

Tạo đối tượng SquigglyAnnotation và chỉ định các thuộc tính của nó.

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

Thêm chú thích ngoằn ngoèo đã tạo vào tài liệu.

```csharp
annotator.Add(squiggly);
```

## Bước 5: Lưu tài liệu

Lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định.

```csharp
annotator.Save(outputPath);
```

## Bước 6: Hiển thị xác nhận

Hiển thị thông báo xác nhận việc lưu tài liệu có chú thích thành công.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Phần kết luận

Tóm lại, Groupdocs.Annotation for .NET cung cấp cho các nhà phát triển một bộ công cụ mạnh mẽ để tích hợp các chức năng chú thích tài liệu vào các ứng dụng .NET của họ một cách liền mạch. Bằng cách làm theo hướng dẫn từng bước này, bạn có thể dễ dàng thêm các chú thích ngoằn ngoèo dạng văn bản vào tài liệu của mình, nâng cao quá trình cộng tác và xem xét tài liệu.

## Câu hỏi thường gặp

### H: Groupdocs.Annotation có hỗ trợ chú thích trên nhiều định dạng tệp khác nhau không?

A: Có, Groupdocs.Annotation hỗ trợ chú thích trên nhiều định dạng tệp, bao gồm PDF, tài liệu Word, bảng tính Excel, v.v.

### H: Groupdocs.Annotation có tương thích với cả ứng dụng trên máy tính để bàn và web không?

A: Hoàn toàn đúng! Groupdocs.Annotation có thể được tích hợp liền mạch vào cả ứng dụng máy tính để bàn và web, mang lại sự linh hoạt và đa năng.

### H: Có tùy chọn cấp phép nào dành cho Groupdocs.Annotation không?

A: Có, Groupdocs.Annotation cung cấp các tùy chọn cấp phép linh hoạt phù hợp với nhu cầu của cá nhân hoặc doanh nghiệp, bao gồm cả giấy phép tạm thời cho mục đích dùng thử.

### H: Có thể tùy chỉnh chú thích được tạo bằng Groupdocs.Annotation không?

A: Chắc chắn rồi! Groupdocs.Annotation cung cấp nhiều tùy chọn tùy chỉnh chú thích, cho phép các nhà phát triển tùy chỉnh chú thích theo yêu cầu cụ thể của họ.

### H: Groupdocs.Annotation có cung cấp hỗ trợ và tài liệu cho nhà phát triển không?

A: Thật vậy! Groupdocs.Annotation cung cấp tài liệu toàn diện và diễn đàn hỗ trợ chuyên dụng để hỗ trợ các nhà phát triển sử dụng các tính năng của nó một cách hiệu quả.