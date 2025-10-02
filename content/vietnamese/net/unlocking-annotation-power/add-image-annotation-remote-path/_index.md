---
"description": "Tìm hiểu cách thêm chú thích hình ảnh vào tài liệu bằng GroupDocs.Annotation cho .NET. Nâng cao khả năng quản lý tài liệu với khả năng chú thích mạnh mẽ."
"linktitle": "Thêm chú thích hình ảnh vào tài liệu (Đường dẫn từ xa)"
"second_title": "GroupDocs.Chú thích API .NET"
"title": "Thêm chú thích hình ảnh vào tài liệu (Đường dẫn từ xa)"
"url": "/vi/net/unlocking-annotation-power/add-image-annotation-remote-path/"
type: docs
"weight": 15
---

# Thêm chú thích hình ảnh vào tài liệu (Đường dẫn từ xa)

## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ tìm hiểu quy trình thêm chú thích hình ảnh vào tài liệu bằng GroupDocs.Annotation cho .NET. Thư viện này cung cấp các công cụ mạnh mẽ để chú thích nhiều loại tài liệu theo chương trình.
## Điều kiện tiên quyết
Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:
1. GroupDocs.Annotation cho .NET: Tải xuống và cài đặt thư viện từ [đây](https://releases.groupdocs.com/annotation/net/).
2. Môi trường phát triển: Đảm bảo bạn có môi trường phát triển phù hợp để phát triển .NET.
3. Tài liệu: Chuẩn bị tài liệu bạn muốn chú thích. Đối với hướng dẫn này, chúng tôi sẽ giả sử bạn có một tài liệu PDF có tên `input.pdf`.
4. Hình ảnh để chú thích: Chọn hình ảnh bạn muốn sử dụng để chú thích. Đảm bảo bạn đã chuẩn bị sẵn URL hình ảnh hoặc đường dẫn cục bộ.

## Nhập không gian tên
Trước khi bắt đầu viết mã, hãy nhập các không gian tên cần thiết:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Bước 1: Thiết lập Đường dẫn đầu ra
Đầu tiên, hãy xác định đường dẫn đầu ra nơi tài liệu có chú thích sẽ được lưu.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Bước 2: Khởi tạo Annotator
Tạo một phiên bản của `Annotator` lớp và chỉ định tài liệu đầu vào.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Mã chú thích sẽ được đặt ở đây
}
```
## Bước 3: Thêm chú thích hình ảnh
Bây giờ, hãy thêm chú thích hình ảnh vào tài liệu. Chúng ta sẽ chỉ định các thuộc tính của chú thích hình ảnh như vị trí, độ mờ, số trang và đường dẫn hình ảnh.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Chỉ định vị trí của chú thích
    CreatedOn = DateTime.Now, // Đặt ngày tạo
    Opacity = 0.7, // Đặt độ mờ đục (0 đến 1)
    PageNumber = 0, // Chỉ định số trang
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Cung cấp URL của hình ảnh
};
annotator.Add(image); // Thêm chú thích hình ảnh
```
## Bước 4: Lưu tài liệu
Lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định.
```csharp
annotator.Save(outputPath);
```
## Bước 5: Hiển thị đường dẫn đầu ra
Thông báo cho người dùng về thao tác lưu tài liệu thành công và hiển thị đường dẫn đầu ra.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Phần kết luận
Trong hướng dẫn này, chúng ta đã học cách thêm chú thích hình ảnh vào tài liệu bằng GroupDocs.Annotation cho .NET. Bằng cách làm theo các bước này, bạn có thể nâng cao các ứng dụng quản lý tài liệu của mình bằng các khả năng chú thích mạnh mẽ.
## Câu hỏi thường gặp
### GroupDocs.Annotation có thể sử dụng với các định dạng tài liệu khác ngoài PDF không?
Có, GroupDocs.Annotation hỗ trợ nhiều định dạng tài liệu khác nhau bao gồm Word, Excel, PowerPoint, v.v.
### GroupDocs.Annotation có tương thích với .NET Core không?
Có, GroupDocs.Annotation tương thích với cả .NET Framework và .NET Core.
### Tôi có thể tùy chỉnh giao diện của chú thích không?
Có, bạn có thể tùy chỉnh giao diện của chú thích như màu sắc, độ mờ và kích thước.
### GroupDocs.Annotation có hỗ trợ tính năng chú thích cộng tác không?
Có, GroupDocs.Annotation cung cấp tính năng chú thích cộng tác để cộng tác thời gian thực trên tài liệu.
### Có phiên bản dùng thử để kiểm tra không?
Có, bạn có thể dùng thử miễn phí GroupDocs.Annotation từ [đây](https://releases.groupdocs.com/).