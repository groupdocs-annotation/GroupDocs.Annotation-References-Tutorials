---
"description": "Tìm hiểu cách tải phông chữ tùy chỉnh một cách liền mạch trong GroupDocs.Annotation cho .NET để nâng cao chú thích tài liệu. Làm theo từng bước của chúng tôi để tích hợp dễ dàng."
"linktitle": "Đang tải Phông chữ Tùy chỉnh"
"second_title": "GroupDocs.Chú thích API .NET"
"title": "Đang tải Phông chữ Tùy chỉnh"
"url": "/vi/net/advanced-usage/loading-custom-fonts/"
type: docs
"weight": 20
---

# Đang tải Phông chữ Tùy chỉnh

## Giới thiệu
GroupDocs.Annotation for .NET là một thư viện mạnh mẽ cho phép các nhà phát triển thêm các tính năng chú thích vào ứng dụng .NET của họ một cách dễ dàng. Một trong những chức năng chính mà nó cung cấp là khả năng tải phông chữ tùy chỉnh, cho phép tùy chỉnh nâng cao và linh hoạt trong chú thích tài liệu.
## Điều kiện tiên quyết
Trước khi thực hiện hướng dẫn, hãy đảm bảo rằng bạn đáp ứng các điều kiện tiên quyết sau:
1. GroupDocs.Annotation cho Thư viện .NET: Tải xuống và cài đặt thư viện từ [đây](https://releases.groupdocs.com/annotation/net/).
2. Môi trường phát triển .NET: Đảm bảo bạn đã thiết lập môi trường làm việc cho việc phát triển .NET.
3. Truy cập vào Phông chữ tùy chỉnh: Chuẩn bị phông chữ tùy chỉnh mà bạn muốn tải vào ứng dụng của mình.

## Nhập không gian tên
Trong dự án .NET của bạn, hãy nhập các không gian tên cần thiết để sử dụng GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Bước 1: Khởi tạo đối tượng Annotator
Tạo một phiên bản của `Annotator` lớp bằng cách cung cấp đường dẫn đến tài liệu PDF đầu vào cùng với thư mục phông chữ tùy chỉnh:
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    // Mã của bạn cho các hoạt động tiếp theo sẽ được đưa vào đây
}
```
## Bước 2: Cấu hình Tùy chọn Xem trước
Xác định các tùy chọn xem trước để chỉ định cách tạo bản xem trước tài liệu. Bạn có thể thiết lập các tùy chọn như định dạng xem trước, số trang, v.v.:
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_with_font_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
```
## Bước 3: Tạo bản xem trước tài liệu
Sử dụng `GeneratePreview` phương pháp của `Document` thuộc tính để tạo bản xem trước với phông chữ tùy chỉnh:
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## Bước 4: Hiển thị đường dẫn đầu ra
Cuối cùng, hiển thị thông báo cho biết việc tạo bản xem trước tài liệu thành công cùng với đường dẫn thư mục đầu ra:
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## Phần kết luận
Tóm lại, việc tải phông chữ tùy chỉnh trong GroupDocs.Annotation cho .NET cung cấp cho các nhà phát triển sự linh hoạt để tùy chỉnh chú thích tài liệu theo yêu cầu của họ. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể tích hợp liền mạch các phông chữ tùy chỉnh vào các ứng dụng .NET của mình và nâng cao trải nghiệm chú thích cho người dùng.
## Câu hỏi thường gặp
### Tôi có thể tải nhiều phông chữ tùy chỉnh cùng lúc không?
Có, bạn có thể chỉ định nhiều thư mục phông chữ khi khởi tạo `Annotator` sự vật.
### Có giới hạn nào về loại phông chữ được hỗ trợ không?
GroupDocs.Annotation cho .NET hỗ trợ nhiều loại phông chữ, bao gồm phông chữ TrueType (.ttf) và OpenType (.otf).
### Tôi có thể thay đổi phông chữ đã tải một cách linh hoạt trong thời gian chạy không?
Có, bạn có thể sửa đổi thư mục phông chữ và tải lại chú thích tài liệu khi cần.
### GroupDocs.Annotation có hỗ trợ nhúng phông chữ vào tài liệu đầu ra không?
Có, bạn có thể nhúng phông chữ tùy chỉnh vào tài liệu đầu ra để đảm bảo hiển thị nhất quán trên các nền tảng khác nhau.
### Có cách nào để xử lý việc cấp phép phông chữ trong ứng dụng không?
GroupDocs.Annotation cung cấp các tùy chọn để quản lý cấp phép phông chữ, bao gồm cả giấy phép tạm thời cho mục đích đánh giá.