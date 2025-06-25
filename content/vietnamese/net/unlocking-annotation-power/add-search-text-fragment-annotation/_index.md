---
"description": "Khám phá sức mạnh của GroupDocs.Annotation cho .NET và dễ dàng thêm chức năng chú thích tài liệu vào ứng dụng của bạn."
"linktitle": "Thêm chú thích đoạn văn bản tìm kiếm vào tài liệu"
"second_title": "GroupDocs.Chú thích API .NET"
"title": "Thêm chú thích đoạn văn bản tìm kiếm vào tài liệu"
"url": "/vi/net/unlocking-annotation-power/add-search-text-fragment-annotation/"
"weight": 20
---

# Thêm chú thích đoạn văn bản tìm kiếm vào tài liệu

## Giới thiệu
Trong lĩnh vực phát triển .NET, GroupDocs.Annotation nổi bật như một công cụ mạnh mẽ để chú thích tài liệu một cách liền mạch. Cho dù bạn là một nhà phát triển dày dạn kinh nghiệm hay chỉ mới bước vào thế giới .NET, hướng dẫn toàn diện này sẽ hướng dẫn bạn những điều cơ bản khi sử dụng GroupDocs.Annotation cho .NET, từ việc nhập không gian tên đến việc thành thạo các phức tạp của việc thêm chú thích đoạn văn bản tìm kiếm vào tài liệu của bạn.
## Giới thiệu
GroupDocs.Annotation for .NET cho phép các nhà phát triển tích hợp khả năng chú thích tài liệu vào ứng dụng của họ một cách dễ dàng. Với API trực quan và các tính năng mạnh mẽ, các nhà phát triển có thể chú thích nhiều định dạng tài liệu khác nhau, bao gồm PDF, tài liệu Microsoft Office, hình ảnh, v.v.
## Điều kiện tiên quyết
Trước khi tìm hiểu sâu hơn về GroupDocs.Annotation cho .NET, hãy đảm bảo bạn đã đáp ứng đủ các điều kiện tiên quyết sau:

## Nhập không gian tên
Trước tiên, hãy nhập các không gian tên cần thiết để truy cập các lớp và phương thức GroupDocs.Annotation trong dự án .NET của bạn:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Bước 1: Xác định Đường dẫn đầu ra
Bắt đầu bằng cách xác định đường dẫn đầu ra nơi tài liệu có chú thích sẽ được lưu:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Bước 2: Khởi tạo Annotator
Tiếp theo, khởi tạo một thể hiện của `Annotator` lớp bằng cách cung cấp đường dẫn đến tài liệu bạn muốn chú thích:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Bước 3: Tạo chú thích cho đoạn văn bản tìm kiếm
Tạo một `SearchTextFragment` đối tượng có các thuộc tính mong muốn, chẳng hạn như văn bản để tìm kiếm, kích thước phông chữ, họ phông chữ, màu phông chữ và màu nền:
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
Thêm chú thích đoạn văn bản tìm kiếm đã tạo vào tài liệu bằng cách sử dụng `Add` phương pháp của người chú thích:
```csharp
annotator.Add(searchText);
```
## Bước 5: Lưu tài liệu có chú thích
Lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định:
```csharp
annotator.Save(outputPath);
```
## Bước 6: Hiển thị thông báo thành công
Thông báo cho người dùng rằng tài liệu đã được lưu thành công:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Phần kết luận
Tóm lại, GroupDocs.Annotation for .NET đơn giản hóa quy trình thêm chú thích vào tài liệu, tăng cường quá trình cộng tác và xem xét tài liệu. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể tích hợp liền mạch các chức năng chú thích tài liệu vào các ứng dụng .NET của mình.
## Câu hỏi thường gặp
### GroupDocs.Annotation có tương thích với mọi định dạng tài liệu không?
Có, GroupDocs.Annotation hỗ trợ nhiều định dạng tài liệu, bao gồm PDF, tài liệu Microsoft Office, hình ảnh, v.v.
### Tôi có thể tùy chỉnh giao diện của chú thích không?
Chắc chắn rồi! GroupDocs.Annotation cung cấp nhiều tùy chọn tùy chỉnh cho chú thích, cho phép bạn điều chỉnh các thuộc tính như kích thước phông chữ, màu sắc và kiểu chữ.
### Có bản dùng thử miễn phí cho GroupDocs.Annotation không?
Có, bạn có thể truy cập dùng thử miễn phí GroupDocs.Annotation để khám phá các tính năng và khả năng của nó trước khi mua [đây](https://releases.groupdocs.com/)..
### Tôi có thể tìm hỗ trợ cho GroupDocs.Annotation ở đâu?
Để được hỗ trợ và trợ giúp với GroupDocs.Annotation, bạn có thể truy cập GroupDocs [diễn đàn](https://forum.groupdocs.com/c/annotation/10) dành riêng cho các câu hỏi và thảo luận liên quan đến chú thích.
### Làm thế nào để tôi có được giấy phép tạm thời cho GroupDocs.Annotation?
Bạn có thể mua giấy phép tạm thời cho GroupDocs.Annotation thông qua GroupDocs [trang web](https://purchase.groupdocs.com/temporary-license/), cho phép bạn đánh giá sản phẩm một cách đầy đủ.