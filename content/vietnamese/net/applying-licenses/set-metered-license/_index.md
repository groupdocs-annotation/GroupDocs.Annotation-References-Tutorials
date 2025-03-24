---
title: Đặt giấy phép đo lường
linktitle: Đặt giấy phép đo lường
second_title: GroupDocs.Annotation .NET API
description: Tìm hiểu cách thiết lập giấy phép đo lường cho GroupDocs.Annotation .NET để sử dụng tài nguyên và khả năng chú thích tài liệu trong các ứng dụng .NET của bạn.
weight: 12
url: /vi/net/applying-licenses/set-metered-license/
---

# Đặt giấy phép đo lường

## Giới thiệu
GroupDocs.Annotation dành cho .NET là một thư viện mạnh mẽ cho phép các nhà phát triển thêm khả năng chú thích tài liệu vào các ứng dụng .NET của họ một cách dễ dàng. Cho dù bạn đang xây dựng hệ thống quản lý tài liệu, nền tảng cộng tác hay bất kỳ ứng dụng nào liên quan đến việc xem xét và đánh dấu tài liệu, GroupDocs.Annotation dành cho .NET đều cung cấp một bộ công cụ toàn diện để hợp lý hóa quy trình.
Trong hướng dẫn này, chúng ta sẽ đi sâu vào quá trình thiết lập giấy phép đo lường cho GroupDocs.Annotation .NET. Giấy phép có đồng hồ đo cho phép bạn chỉ trả tiền cho những tài nguyên bạn sử dụng, khiến giấy phép này trở thành giải pháp tiết kiệm chi phí cho các dự án ở mọi quy mô. Bằng cách làm theo các bước được nêu bên dưới, bạn sẽ có thể tích hợp liền mạch GroupDocs.Annotation vào ứng dụng .NET của mình trong khi tối ưu hóa việc sử dụng tài nguyên và duy trì kiểm soát ngân sách.
## Điều kiện tiên quyết
Trước khi đi sâu vào hướng dẫn, hãy đảm bảo rằng bạn có các điều kiện tiên quyết sau:
1.  GroupDocs.Annotation for .NET Library: Tải xuống thư viện từ[trang mạng](https://releases.groupdocs.com/annotation/net/).
2. Truy cập vào Tài khoản GroupDocs: Bạn sẽ cần có tài khoản GroupDocs để lấy khóa công khai và khóa riêng cần thiết để thiết lập giấy phép đồng hồ đo. Nếu chưa có tài khoản, bạn có thể đăng ký dùng thử miễn phí[đây](https://releases.groupdocs.com/).
3. Hiểu biết cơ bản về C# và .NET Framework: Làm quen với ngôn ngữ lập trình C# và .NET framework sẽ có ích cho việc triển khai các bước được nêu trong hướng dẫn này.

## Nhập không gian tên
Để bắt đầu, hãy đảm bảo nhập các vùng tên cần thiết vào dự án C# của bạn. Các không gian tên này rất cần thiết để tương tác với chức năng GroupDocs.Annotation.
```csharp
using System;
```
## Bước 1: Lấy khóa công khai và khóa riêng
Trước khi thiết lập giấy phép đo lường, bạn cần lấy khóa công khai và khóa riêng tư từ trang tổng quan tài khoản GroupDocs của mình.
1. Đăng nhập vào tài khoản GroupDocs của bạn.
2. Điều hướng đến phần quản lý giấy phép.
3. Sao chép khóa công khai và riêng tư do GroupDocs cung cấp.
## Bước 2: Đặt giấy phép đo
Khi bạn đã có được khóa chung và khóa riêng, bạn có thể thiết lập giấy phép đo trong ứng dụng .NET của mình.
```csharp
string publicKey = "*****"; // Thay thế ***** bằng khóa chung của bạn
string privateKey = "*****"; // Thay thế ***** bằng khóa riêng của bạn
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Phần kết luận
Tóm lại, thiết lập giấy phép đo lường cho GroupDocs.Annotation .NET là một quy trình đơn giản đảm bảo sử dụng tài nguyên hiệu quả và tiết kiệm chi phí cho các dự án chú thích tài liệu của bạn. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể tích hợp liền mạch GroupDocs.Annotation vào ứng dụng .NET của mình và nâng cao khả năng cộng tác và đánh giá tài liệu.
## Câu hỏi thường gặp
### Tôi có thể sử dụng GroupDocs.Annotation cho .NET trong các dự án thương mại không?
Có, GroupDocs.Annotation for .NET có thể được sử dụng trong cả dự án thương mại và phi thương mại. Tuy nhiên, bạn cần có được giấy phép phù hợp dựa trên yêu cầu dự án của bạn.
### Có phiên bản dùng thử cho GroupDocs.Annotation cho .NET không?
 Có, bạn có thể tận dụng bản dùng thử miễn phí GroupDocs.Annotation cho .NET bằng cách truy cập[liên kết này](https://releases.groupdocs.com/).
### Làm cách nào tôi có thể nhận được hỗ trợ kỹ thuật cho GroupDocs.Annotation cho .NET?
 Bạn có thể tìm kiếm hỗ trợ kỹ thuật bằng cách truy cập diễn đàn GroupDocs[đây](https://forum.groupdocs.com/c/annotation/10).
### Có sẵn bất kỳ tùy chọn giấy phép tạm thời nào không?
 Có, bạn có thể xin giấy phép tạm thời từ GroupDocs cho mục đích đánh giá hoặc sử dụng ngắn hạn. Thăm nom[liên kết này](https://purchase.groupdocs.com/temporary-license/) để biết thêm thông tin.
### Tôi có thể tùy chỉnh các tính năng chú thích theo yêu cầu dự án của mình không?
Có, GroupDocs.Annotation for .NET cung cấp các tùy chọn tùy chỉnh mở rộng, cho phép bạn điều chỉnh các tính năng chú thích cho phù hợp với nhu cầu dự án cụ thể của mình.