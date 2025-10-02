---
"description": "Tìm hiểu cách thêm chú thích hình ảnh vào văn bản trong .NET bằng GroupDocs.Annotation để quản lý tài liệu và cộng tác hiệu quả."
"linktitle": "Đặt chú thích hình ảnh lên trên văn bản"
"second_title": "GroupDocs.Chú thích API .NET"
"title": "Đặt chú thích hình ảnh lên trên văn bản"
"url": "/vi/net/advanced-usage/put-image-annotation-over-text/"
type: docs
"weight": 21
---

# Đặt chú thích hình ảnh lên trên văn bản

## Giới thiệu
Trong thế giới phát triển .NET, GroupDocs.Annotation cung cấp giải pháp mạnh mẽ để thêm chú thích vào tài liệu, giúp cộng tác và quản lý tài liệu hiệu quả hơn. Một yêu cầu phổ biến là đặt chú thích hình ảnh lên văn bản, có thể thực hiện liền mạch bằng GroupDocs.Annotation cho .NET.
## Điều kiện tiên quyết
Trước khi bắt đầu quá trình chú thích hình ảnh lên văn bản bằng GroupDocs.Annotation cho .NET, hãy đảm bảo bạn có những điều sau:
1. GroupDocs.Annotation cho Thư viện .NET: Tải xuống và cài đặt thư viện từ [đây](https://releases.groupdocs.com/annotation/net/).
2. Môi trường phát triển: Thiết lập môi trường phát triển phù hợp, chẳng hạn như Visual Studio hoặc bất kỳ IDE .NET nào khác.
3. Tệp tài liệu và hình ảnh: Chuẩn bị tệp tài liệu (PDF, DOCX, v.v.) và tệp hình ảnh bạn muốn sử dụng để chú thích.
4. Hiểu biết cơ bản về C#: Cần phải quen thuộc với ngôn ngữ lập trình C# để triển khai các đoạn mã được cung cấp trong hướng dẫn này.

## Nhập không gian tên
Trước khi tiến hành quá trình chú thích, hãy đảm bảo bạn nhập các không gian tên cần thiết vào dự án C# của mình:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Bước 1: Xác định Đường dẫn đầu ra
Đầu tiên, hãy xác định đường dẫn đầu ra nơi tài liệu có chú thích sẽ được lưu:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Bước 2: Khởi tạo Annotator
Khởi tạo `Annotator` đối tượng bằng cách cung cấp đường dẫn tài liệu đầu vào:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Mã chú thích sẽ được đặt ở đây
}
```
## Bước 3: Tạo chú thích hình ảnh
Tạo một `ImageAnnotation` đối tượng có các thuộc tính mong muốn như kích thước hộp, độ mờ, số trang, đường dẫn hình ảnh và chỉ mục z:
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
Thêm chú thích hình ảnh vào tài liệu bằng cách sử dụng `Add` phương pháp của `Annotator` sự vật:
```csharp
annotator.Add(image);
```
## Bước 5: Lưu tài liệu có chú thích
Lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định:
```csharp
annotator.Save(outputPath);
```
## Bước 6: Hiển thị thông báo thành công
Hiển thị thông báo thành công cùng đường dẫn đến tài liệu có chú thích:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Phần kết luận
Tóm lại, việc thêm chú thích hình ảnh vào văn bản trong các ứng dụng .NET bằng GroupDocs.Annotation là một quá trình đơn giản. Bằng cách làm theo hướng dẫn từng bước được cung cấp trong hướng dẫn này, bạn có thể chú thích tài liệu hiệu quả và nâng cao khả năng cộng tác và quản lý tài liệu trong các dự án .NET của mình.
## Câu hỏi thường gặp
### Tôi có thể chú thích vào các tài liệu khác ngoài PDF không?
Có, GroupDocs.Annotation hỗ trợ nhiều định dạng tài liệu khác nhau như DOCX, XLSX, PPTX, v.v.
### Có bản dùng thử miễn phí cho GroupDocs.Annotation không?
Có, bạn có thể tải xuống phiên bản dùng thử miễn phí từ [đây](https://releases.groupdocs.com/).
### Tôi có thể nhận được hỗ trợ cho GroupDocs.Annotation như thế nào?
Bạn có thể nhận được sự hỗ trợ từ diễn đàn cộng đồng GroupDocs.Annotation [đây](https://forum.groupdocs.com/c/annotation/10).
### Tôi có cần giấy phép tạm thời để thử nghiệm không?
Có, bạn có thể xin giấy phép tạm thời từ [đây](https://purchase.groupdocs.com/temporary-license/) với mục đích thử nghiệm.
### Tôi có thể tùy chỉnh giao diện của chú thích không?
Có, GroupDocs.Annotation cung cấp nhiều tùy chọn để tùy chỉnh giao diện chú thích như màu sắc, độ mờ, kích thước phông chữ, v.v.