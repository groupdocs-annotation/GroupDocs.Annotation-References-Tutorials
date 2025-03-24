---
title: Thêm chú thích đoạn văn bản tìm kiếm vào tài liệu
linktitle: Thêm chú thích đoạn văn bản tìm kiếm vào tài liệu
second_title: GroupDocs.Annotation .NET API
description: Khám phá sức mạnh của GroupDocs.Annotation dành cho .NET và dễ dàng thêm khả năng chú thích tài liệu vào ứng dụng của bạn.
weight: 20
url: /vi/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---

# Thêm chú thích đoạn văn bản tìm kiếm vào tài liệu

## Giới thiệu
Trong lĩnh vực phát triển .NET, GroupDocs.Annotation nổi bật như một công cụ mạnh mẽ để chú thích tài liệu một cách liền mạch. Cho dù bạn là nhà phát triển dày dặn kinh nghiệm hay chỉ mới bước chân vào thế giới .NET, hướng dẫn toàn diện này sẽ hướng dẫn bạn những điều cơ bản khi sử dụng GroupDocs.Annotation cho .NET, từ nhập vùng tên đến nắm vững sự phức tạp của việc thêm chú thích đoạn văn bản tìm kiếm vào các tài liệu.
## Giới thiệu
GroupDocs.Annotation dành cho .NET trao quyền cho các nhà phát triển kết hợp khả năng chú thích tài liệu vào ứng dụng của họ một cách dễ dàng. Với API trực quan và các tính năng mạnh mẽ, nhà phát triển có thể chú thích nhiều định dạng tài liệu khác nhau, bao gồm tệp PDF, tài liệu Microsoft Office, hình ảnh, v.v.
## Điều kiện tiên quyết
Trước khi đi sâu vào GroupDocs.Annotation cho .NET, hãy đảm bảo bạn có sẵn các điều kiện tiên quyết sau:

## Nhập không gian tên
Đầu tiên, nhập các không gian tên cần thiết để truy cập các lớp và phương thức GroupDocs.Annotation trong dự án .NET của bạn:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Bước 1: Xác định đường dẫn đầu ra
Bắt đầu bằng cách xác định đường dẫn đầu ra nơi tài liệu được chú thích sẽ được lưu:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Bước 2: Khởi tạo Annotator
 Tiếp theo, khởi tạo một thể hiện của`Annotator` lớp bằng cách cung cấp đường dẫn đến tài liệu bạn muốn chú thích:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Bước 3: Tạo chú thích đoạn văn bản tìm kiếm
 Tạo một`SearchTextFragment` đối tượng có các thuộc tính mong muốn, chẳng hạn như văn bản cần tìm kiếm, cỡ chữ, họ phông chữ, màu phông chữ và màu nền:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## Bước 4: Thêm chú thích
 Thêm chú thích đoạn văn bản tìm kiếm đã tạo vào tài liệu bằng cách sử dụng`Add` phương pháp của người chú thích:
```csharp
annotator.Add(searchText);
```
## Bước 5: Lưu tài liệu chú thích
Lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định:
```csharp
annotator.Save(outputPath);
```
## Bước 6: Hiển thị thông báo thành công
Thông báo cho người dùng biết tài liệu đã được lưu thành công:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Phần kết luận
Tóm lại, GroupDocs.Annotation dành cho .NET đơn giản hóa quá trình thêm chú thích vào tài liệu, tăng cường quá trình cộng tác và xem xét tài liệu. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể tích hợp liền mạch các khả năng chú thích tài liệu vào các ứng dụng .NET của mình.
## Câu hỏi thường gặp
### GroupDocs.Annotation có tương thích với tất cả các định dạng tài liệu không?
Có, GroupDocs.Annotation hỗ trợ nhiều định dạng tài liệu, bao gồm PDF, tài liệu Microsoft Office, hình ảnh, v.v.
### Tôi có thể tùy chỉnh hình thức của chú thích không?
Tuyệt đối! GroupDocs.Annotation cung cấp các tùy chọn tùy chỉnh mở rộng cho chú thích, cho phép bạn điều chỉnh các thuộc tính như kích thước phông chữ, màu sắc và kiểu dáng.
### Có bản dùng thử miễn phí cho GroupDocs.Annotation không?
 Có, bạn có thể truy cập bản dùng thử miễn phí của GroupDocs. Chú thích để khám phá các tính năng và khả năng của nó trước khi mua hàng[đây](https://releases.groupdocs.com/)..
### Tôi có thể tìm hỗ trợ cho GroupDocs.Annotation ở đâu?
 Để được hỗ trợ và trợ giúp với GroupDocs.Annotation, bạn có thể truy cập GroupDocs[diễn đàn](https://forum.groupdocs.com/c/annotation/10) dành riêng cho các truy vấn và thảo luận liên quan đến chú thích.
### Làm cách nào để có được giấy phép tạm thời cho GroupDocs.Annotation?
 Bạn có thể có được giấy phép tạm thời cho GroupDocs.Annotation thông qua GroupDocs[trang mạng](https://purchase.groupdocs.com/temporary-license/), cho phép bạn đánh giá sản phẩm một cách đầy đủ.