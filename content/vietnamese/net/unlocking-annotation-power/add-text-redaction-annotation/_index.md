---
title: Thêm chú thích soạn thảo văn bản vào tài liệu
linktitle: Thêm chú thích soạn thảo văn bản vào tài liệu
second_title: GroupDocs.Annotation .NET API
description: Tìm hiểu cách thêm chú thích biên tập văn bản vào tài liệu PDF bằng GroupDocs.Annotation cho .NET. Bảo vệ thông tin nhạy cảm một cách dễ dàng.
weight: 23
url: /vi/net/unlocking-annotation-power/add-text-redaction-annotation/
---
## Giới thiệu
Thêm chú thích chỉnh sửa văn bản vào tài liệu có thể là một bước quan trọng trong việc quản lý thông tin nhạy cảm một cách an toàn. GroupDocs.Annotation for .NET cung cấp một giải pháp mạnh mẽ để đạt được điều này một cách liền mạch. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn từng bước trong quá trình thêm chú thích chỉnh sửa văn bản vào tài liệu của bạn.
## Điều kiện tiên quyết
Trước khi chúng ta bắt đầu, hãy đảm bảo bạn có sẵn các điều kiện tiên quyết sau:
1.  GroupDocs.Annotation for .NET: Đảm bảo bạn đã cài đặt thư viện GroupDocs.Annotation for .NET. Bạn có thể tải nó xuống từ[trang mạng](https://releases.groupdocs.com/annotation/net/).
2. Môi trường phát triển: Thiết lập môi trường phát triển với IDE tương thích .NET như Visual Studio.

## Nhập không gian tên
Đầu tiên, hãy nhập các không gian tên cần thiết vào dự án của chúng ta:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Bước 1: Xác định đường dẫn đầu ra
Xác định đường dẫn đầu ra nơi bạn muốn lưu tài liệu có chú thích. Đảm bảo nó có thể truy cập và ghi được.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Bước 2: Khởi tạo Annotator
 Khởi tạo chú thích với đường dẫn tài liệu đầu vào. Thay thế`"input.pdf"` với đường dẫn đến tài liệu của bạn.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Mã chú thích sẽ ở đây
}
```
## Bước 3: Tạo chú thích biên tập văn bản
 Tạo một`TextRedactionAnnotation`đối tượng có các thuộc tính cần thiết như`PageNumber`, `FontColor` , Và`Points`. Tùy chỉnh chú thích theo yêu cầu của bạn.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## Bước 4: Thêm chú thích và lưu
Thêm chú thích đã tạo vào tài liệu bằng cách sử dụng trình chú thích và lưu tài liệu được chú thích vào đường dẫn đầu ra đã chỉ định.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Bước 5: Kiểm tra đầu ra
Cuối cùng, xác nhận rằng tài liệu đã được lưu thành công vào đường dẫn đầu ra được chỉ định.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Phần kết luận
Trong hướng dẫn này, chúng ta đã thực hiện quy trình thêm chú thích biên tập văn bản vào tài liệu bằng GroupDocs.Annotation cho .NET. Với các bước này, giờ đây bạn có thể quản lý thông tin nhạy cảm trong tài liệu của mình một cách an toàn.
## Câu hỏi thường gặp
### Tôi có thể tùy chỉnh giao diện của chú thích biên tập văn bản không?
Có, bạn có thể tùy chỉnh các thuộc tính khác nhau như màu phông chữ, màu tô và độ mờ để phù hợp với yêu cầu của bạn.
### Có bản dùng thử trước khi mua không?
 Có, bạn có thể truy cập phiên bản dùng thử miễn phí từ[trang mạng](https://releases.groupdocs.com/).
### Làm cách nào tôi có thể nhận được hỗ trợ nếu gặp bất kỳ vấn đề nào?
 Bạn có thể nhận hỗ trợ từ diễn đàn cộng đồng GroupDocs.Annotation[đây](https://forum.groupdocs.com/c/annotation/10).
### Tôi có cần giấy phép tạm thời cho mục đích thử nghiệm không?
 Có, bạn có thể xin giấy phép tạm thời từ[trang mua hàng](https://purchase.groupdocs.com/temporary-license/)để thử nghiệm.
### Tôi có thể thêm nhiều chú thích vào một tài liệu không?
Hoàn toàn có thể, GroupDocs.Annotation cho phép bạn thêm nhiều loại chú thích khác nhau và nhiều phiên bản vào một tài liệu.