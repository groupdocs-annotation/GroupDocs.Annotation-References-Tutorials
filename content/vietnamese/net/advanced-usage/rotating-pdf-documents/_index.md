---
title: Xoay tài liệu PDF
linktitle: Xoay tài liệu PDF
second_title: GroupDocs.Annotation .NET API
description: Tìm hiểu cách xoay tài liệu PDF dễ dàng bằng Groupdocs.Annotation for .NET. Nâng cao hiệu quả quản lý tài liệu.
weight: 22
url: /vi/net/advanced-usage/rotating-pdf-documents/
---

# Xoay tài liệu PDF

## Giới thiệu
Xoay tài liệu PDF có thể là một nhiệm vụ quan trọng khi xử lý các tệp cần được xem hoặc xử lý theo cách khác. Trong hướng dẫn này, chúng ta sẽ khám phá cách xoay tài liệu PDF từng bước bằng cách sử dụng Groupdocs.Annotation cho .NET.
## Điều kiện tiên quyết
Trước khi đi sâu vào hướng dẫn, hãy đảm bảo bạn có các điều kiện tiên quyết sau:
1.  Groupdocs.Annotation for .NET Library: Đảm bảo rằng bạn đã tải xuống và cài đặt thư viện Groupdocs.Annotation for .NET. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/annotation/net/).
2. Kiến thức cơ bản về lập trình C#: Hướng dẫn này giả sử bạn có hiểu biết cơ bản về ngôn ngữ lập trình C# và cách làm việc với các thư viện .NET.

## Nhập không gian tên
Trước tiên, bạn cần nhập các vùng tên cần thiết vào dự án C# của mình để truy cập chức năng do thư viện Groupdocs.Annotation cung cấp.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Bước 1: Tải tài liệu PDF
 Bắt đầu bằng cách tải tài liệu PDF mà bạn muốn xoay bằng cách sử dụng`Annotator` lớp học.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Bước 2: Đặt trang xoay và xử lý
Chỉ định góc xoay và các trang bạn muốn xoay. Trong ví dụ này, chúng tôi sẽ xoay trang đầu tiên 90 độ theo chiều kim đồng hồ.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Bước 3: Lưu tài liệu đã xoay
Lưu tài liệu PDF đã xoay với những thay đổi được chỉ định.
```csharp
annotator.Save("result.pdf");
```
## Bước 4: Hiển thị xác nhận
Thông báo cho người dùng rằng tài liệu đã được xoay thành công.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Phần kết luận
Xoay tài liệu PDF là một thao tác cơ bản và với Groupdocs.Annotation dành cho .NET, việc này trở nên đơn giản và hiệu quả. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể dễ dàng xoay tệp PDF theo yêu cầu của mình.
## Câu hỏi thường gặp
### Tôi có thể xoay nhiều trang trong tài liệu PDF bằng Groupdocs.Annotation cho .NET không?
 Có, bạn có thể chỉ định nhiều trang để xoay bằng cách điều chỉnh`ProcessPages` tài sản tương ứng.
### Groupdocs.Annotation for .NET có tương thích với tất cả các phiên bản .NET framework không?
Groupdocs.Annotation for .NET hỗ trợ nhiều phiên bản .NET framework, đảm bảo khả năng tương thích cho hầu hết các môi trường phát triển.
### Groupdocs.Annotation cho .NET có cung cấp tùy chọn xoay tài liệu PDF theo các hướng khác nhau không?
Có, bạn có thể xoay tài liệu PDF theo chiều kim đồng hồ, ngược chiều kim đồng hồ hoặc theo các góc tùy chỉnh dựa trên yêu cầu của bạn.
### Tôi có thể tích hợp Groupdocs.Annotation cho .NET vào hệ thống quản lý tài liệu hiện tại của mình không?
Hoàn toàn có thể, Groupdocs.Annotation for .NET cung cấp các tùy chọn tích hợp liền mạch, cho phép bạn nâng cao khả năng quản lý tài liệu một cách dễ dàng.
### Có phiên bản dùng thử nào cho Groupdocs.Annotation cho .NET không?
 Có, bạn có thể tải phiên bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).