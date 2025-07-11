---
"description": "Tìm hiểu cách thêm chú thích hình ảnh vào tài liệu bằng GroupDocs.Annotation cho .NET. Nâng cao khả năng xử lý tài liệu một cách dễ dàng."
"linktitle": "Thêm chú thích hình ảnh vào tài liệu (Đường dẫn cục bộ)"
"second_title": "GroupDocs.Chú thích API .NET"
"title": "Thêm chú thích hình ảnh vào tài liệu (Đường dẫn cục bộ)"
"url": "/vi/net/unlocking-annotation-power/add-image-annotation-local-path/"
"weight": 14
---

# Thêm chú thích hình ảnh vào tài liệu (Đường dẫn cục bộ)

## Giới thiệu
GroupDocs.Annotation for .NET là một thư viện mạnh mẽ cho phép các nhà phát triển thêm nhiều loại chú thích khác nhau vào tài liệu theo chương trình. Trong hướng dẫn này, chúng ta sẽ tìm hiểu cách thêm chú thích hình ảnh vào tài liệu bằng đường dẫn cục bộ.
## Điều kiện tiên quyết
Trước khi bắt đầu, hãy đảm bảo bạn đáp ứng đủ các điều kiện tiên quyết sau:
1. Kiến thức cơ bản về ngôn ngữ lập trình C#.
2. Visual Studio được cài đặt trên hệ thống của bạn.
3. GroupDocs.Annotation cho thư viện .NET được cài đặt hoặc tutorialsd trong dự án của bạn.
4. Một tài liệu đầu vào (ví dụ: PDF) và một tệp hình ảnh để chú thích.
## Nhập không gian tên
Đầu tiên, bạn cần nhập các không gian tên cần thiết vào tệp C# của mình. Các không gian tên này cung cấp quyền truy cập vào các lớp và phương thức cần thiết để làm việc với GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Bước 1: Xác định Đường dẫn đầu ra
Xác định đường dẫn đầu ra nơi tài liệu có chú thích sẽ được lưu.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Bước 2: Khởi tạo Annotator
Khởi tạo trình chú thích bằng cách cung cấp đường dẫn đến tài liệu đầu vào.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Mã chú thích ở đây
}
```
## Bước 3: Tạo chú thích hình ảnh
Tạo một phiên bản của `ImageAnnotation` lớp và chỉ định các thuộc tính của nó như vị trí, độ mờ, số trang và đường dẫn hình ảnh.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## Bước 4: Thêm chú thích
Thêm chú thích hình ảnh đã tạo vào tài liệu bằng cách sử dụng `Add` phương pháp của người chú thích.
```csharp
annotator.Add(image);
```
## Bước 5: Lưu tài liệu
Lưu tài liệu có chú thích vào đường dẫn đầu ra.
```csharp
annotator.Save(outputPath);
```
## Bước 6: Hiển thị đường dẫn đầu ra
Hiển thị thông báo cho biết tài liệu đã được lưu thành công và vị trí lưu tệp đầu ra.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Phần kết luận
Trong hướng dẫn này, chúng ta đã học cách thêm chú thích hình ảnh vào tài liệu bằng GroupDocs.Annotation cho .NET. Bằng cách làm theo các bước đơn giản này, bạn có thể nâng cao khả năng xử lý tài liệu của mình bằng các tính năng chú thích mạnh mẽ.
## Câu hỏi thường gặp
### Tôi có thể chú thích vào các tài liệu khác ngoài PDF không?
Có, GroupDocs.Annotation hỗ trợ nhiều định dạng tài liệu khác nhau bao gồm Word, Excel, PowerPoint, v.v.
### GroupDocs.Annotation có tương thích với .NET Core không?
Có, GroupDocs.Annotation tương thích với cả .NET Framework và .NET Core.
### Tôi có thể tùy chỉnh giao diện của chú thích không?
Hoàn toàn có thể tùy chỉnh giao diện, kích thước, màu sắc và các thuộc tính khác của chú thích theo yêu cầu của bạn.
### GroupDocs.Annotation có hỗ trợ chú thích cộng tác không?
Có, GroupDocs.Annotation cung cấp tính năng chú thích cộng tác cho phép nhiều người dùng chú thích tài liệu cùng lúc.
### Tôi có thể tìm thêm sự trợ giúp hoặc hỗ trợ ở đâu?
Bạn có thể truy cập diễn đàn GroupDocs.Annotation để được cộng đồng hỗ trợ và giúp đỡ.