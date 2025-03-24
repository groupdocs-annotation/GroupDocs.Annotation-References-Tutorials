---
title: Đặt chú thích hình ảnh lên văn bản
linktitle: Đặt chú thích hình ảnh lên văn bản
second_title: GroupDocs.Annotation .NET API
description: Tìm hiểu cách thêm chú thích hình ảnh trên văn bản trong .NET bằng GroupDocs.Annotation để cộng tác và quản lý tài liệu hiệu quả.
weight: 21
url: /vi/net/advanced-usage/put-image-annotation-over-text/
---

# Đặt chú thích hình ảnh lên văn bản

## Giới thiệu
Trong thế giới phát triển .NET, GroupDocs.Annotation cung cấp một giải pháp mạnh mẽ để thêm chú thích vào tài liệu, giúp việc cộng tác và quản lý tài liệu hiệu quả hơn. Một yêu cầu chung là đặt chú thích hình ảnh lên trên văn bản, việc này có thể được thực hiện liền mạch bằng cách sử dụng GroupDocs.Annotation for .NET.
## Điều kiện tiên quyết
Trước khi đi sâu vào quá trình đặt chú thích hình ảnh lên văn bản bằng GroupDocs.Annotation cho .NET, hãy đảm bảo bạn có những điều sau:
1.  GroupDocs.Annotation for .NET Library: Tải xuống và cài đặt thư viện từ[đây](https://releases.groupdocs.com/annotation/net/).
2. Môi trường phát triển: Thiết lập môi trường phát triển phù hợp, chẳng hạn như Visual Studio hoặc bất kỳ .NET IDE nào khác.
3. Tệp tài liệu và hình ảnh: Chuẩn bị tệp tài liệu (PDF, DOCX, v.v.) và tệp hình ảnh bạn muốn sử dụng cho chú thích.
4. Hiểu biết cơ bản về C#: Cần phải làm quen với ngôn ngữ lập trình C# để triển khai các đoạn mã được cung cấp trong hướng dẫn này.

## Nhập không gian tên
Trước khi tiếp tục quá trình chú thích, hãy đảm bảo bạn nhập các vùng tên cần thiết trong dự án C# của mình:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Bước 1: Xác định đường dẫn đầu ra
Đầu tiên, xác định đường dẫn đầu ra nơi tài liệu chú thích sẽ được lưu:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Bước 2: Khởi tạo Annotator
 Khởi tạo`Annotator` đối tượng bằng cách cung cấp đường dẫn tài liệu đầu vào:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Mã chú thích sẽ ở đây
}
```
## Bước 3: Tạo chú thích hình ảnh
 Tạo ra một`ImageAnnotation` đối tượng có các thuộc tính mong muốn như kích thước hộp, độ mờ, số trang, đường dẫn hình ảnh và chỉ mục z:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## Bước 4: Thêm chú thích
 Thêm chú thích hình ảnh vào tài liệu bằng cách sử dụng`Add` phương pháp của`Annotator` sự vật:
```csharp
annotator.Add(image);
```
## Bước 5: Lưu tài liệu chú thích
Lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định:
```csharp
annotator.Save(outputPath);
```
## Bước 6: Hiển thị thông báo thành công
Hiển thị thông báo thành công kèm theo đường dẫn đến tài liệu được chú thích:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Phần kết luận
Tóm lại, việc thêm chú thích hình ảnh vào văn bản trong các ứng dụng .NET bằng GroupDocs.Annotation là một quá trình đơn giản. Bằng cách làm theo hướng dẫn từng bước được cung cấp trong hướng dẫn này, bạn có thể chú thích tài liệu một cách hiệu quả cũng như nâng cao khả năng cộng tác và quản lý tài liệu trong các dự án .NET của mình.
## Câu hỏi thường gặp
### Tôi có thể chú thích các tài liệu không phải là PDF không?
Có, GroupDocs.Annotation hỗ trợ nhiều định dạng tài liệu khác nhau như DOCX, XLSX, PPTX, v.v.
### Có bản dùng thử miễn phí cho GroupDocs.Annotation không?
 Có, bạn có thể tải xuống phiên bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).
### Làm cách nào tôi có thể nhận được hỗ trợ cho GroupDocs.Annotation?
 Bạn có thể nhận hỗ trợ từ diễn đàn cộng đồng GroupDocs.Annotation[đây](https://forum.groupdocs.com/c/annotation/10).
### Tôi có cần giấy phép tạm thời cho mục đích thử nghiệm không?
 Có, bạn có thể xin giấy phép tạm thời từ[đây](https://purchase.groupdocs.com/temporary-license/) cho mục đích thử nghiệm.
### Tôi có thể tùy chỉnh hình thức của chú thích không?
Có, GroupDocs.Annotation cung cấp nhiều tùy chọn khác nhau để tùy chỉnh giao diện của chú thích như màu sắc, độ mờ, cỡ chữ, v.v.