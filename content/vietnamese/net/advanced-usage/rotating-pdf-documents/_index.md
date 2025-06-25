---
"description": "Tìm hiểu cách xoay tài liệu PDF dễ dàng bằng Groupdocs.Annotation cho .NET. Cải thiện hiệu quả quản lý tài liệu."
"linktitle": "Xoay tài liệu PDF"
"second_title": "GroupDocs.Chú thích API .NET"
"title": "Xoay tài liệu PDF"
"url": "/vi/net/advanced-usage/rotating-pdf-documents/"
"weight": 22
---

# Xoay tài liệu PDF

## Giới thiệu
Xoay tài liệu PDF có thể là một nhiệm vụ quan trọng khi xử lý các tệp cần được xem hoặc xử lý theo cách khác. Trong hướng dẫn này, chúng ta sẽ khám phá cách xoay tài liệu PDF từng bước bằng Groupdocs.Annotation cho .NET.
## Điều kiện tiên quyết
Trước khi bắt đầu hướng dẫn, hãy đảm bảo bạn đáp ứng các điều kiện tiên quyết sau:
1. Groupdocs.Annotation cho Thư viện .NET: Đảm bảo rằng bạn đã tải xuống và cài đặt thư viện Groupdocs.Annotation cho .NET. Bạn có thể tải xuống từ [đây](https://releases.groupdocs.com/annotation/net/).
2. Kiến thức cơ bản về lập trình C#: Hướng dẫn này giả định rằng bạn có hiểu biết cơ bản về ngôn ngữ lập trình C# và cách làm việc với thư viện .NET.

## Nhập không gian tên
Trước tiên, bạn cần nhập các không gian tên cần thiết vào dự án C# của mình để truy cập chức năng do thư viện Groupdocs.Annotation cung cấp.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Bước 1: Tải Tài liệu PDF
Bắt đầu bằng cách tải tài liệu PDF mà bạn muốn xoay bằng cách sử dụng `Annotator` lớp học.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Bước 2: Thiết lập Xoay và Xử lý Trang
Chỉ định góc xoay và các trang bạn muốn xoay. Trong ví dụ này, chúng ta sẽ xoay trang đầu tiên 90 độ theo chiều kim đồng hồ.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Bước 3: Lưu tài liệu đã xoay
Lưu tài liệu PDF đã xoay với những thay đổi đã chỉ định.
```csharp
annotator.Save("result.pdf");
```
## Bước 4: Hiển thị xác nhận
Thông báo cho người dùng rằng tài liệu đã được xoay thành công.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Phần kết luận
Xoay tài liệu PDF là một thao tác cơ bản và với Groupdocs.Annotation cho .NET, thao tác này trở nên đơn giản và hiệu quả. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể dễ dàng xoay tệp PDF theo yêu cầu của mình.
## Câu hỏi thường gặp
### Tôi có thể xoay nhiều trang trong tài liệu PDF bằng Groupdocs.Annotation cho .NET không?
Có, bạn có thể chỉ định nhiều trang để xoay bằng cách điều chỉnh `ProcessPages` tài sản theo đó.
### Groupdocs.Annotation cho .NET có tương thích với tất cả các phiên bản của .NET framework không?
Groupdocs.Annotation cho .NET hỗ trợ nhiều phiên bản .NET framework, đảm bảo khả năng tương thích với hầu hết các môi trường phát triển.
### Groupdocs.Annotation cho .NET có cung cấp tùy chọn xoay tài liệu PDF theo các hướng khác nhau không?
Có, bạn có thể xoay tài liệu PDF theo chiều kim đồng hồ, ngược chiều kim đồng hồ hoặc theo góc tùy chỉnh tùy theo yêu cầu của bạn.
### Tôi có thể tích hợp Groupdocs.Annotation cho .NET vào hệ thống quản lý tài liệu hiện tại của mình không?
Đúng vậy, Groupdocs.Annotation cho .NET cung cấp các tùy chọn tích hợp liền mạch, cho phép bạn nâng cao khả năng quản lý tài liệu một cách dễ dàng.
### Có phiên bản dùng thử của Groupdocs.Annotation dành cho .NET không?
Có, bạn có thể nhận phiên bản dùng thử miễn phí từ [đây](https://releases.groupdocs.com/).