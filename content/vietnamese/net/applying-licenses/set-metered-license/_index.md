---
"description": "Tìm hiểu cách thiết lập giấy phép tính phí cho GroupDocs.Annotation .NET để sử dụng tài nguyên và khả năng chú thích tài liệu trong ứng dụng .NET của bạn."
"linktitle": "Thiết lập giấy phép đo lường"
"second_title": "GroupDocs.Chú thích API .NET"
"title": "Thiết lập giấy phép đo lường"
"url": "/vi/net/applying-licenses/set-metered-license/"
type: docs
"weight": 12
---

# Thiết lập giấy phép đo lường

## Giới thiệu
GroupDocs.Annotation for .NET là một thư viện mạnh mẽ giúp các nhà phát triển dễ dàng thêm chức năng chú thích tài liệu vào ứng dụng .NET của họ. Cho dù bạn đang xây dựng hệ thống quản lý tài liệu, nền tảng cộng tác hay bất kỳ ứng dụng nào liên quan đến việc xem xét và đánh dấu tài liệu, GroupDocs.Annotation for .NET đều cung cấp một bộ công cụ toàn diện để hợp lý hóa quy trình.
Trong hướng dẫn này, chúng ta sẽ đi sâu vào quá trình thiết lập giấy phép theo định mức cho GroupDocs.Annotation .NET. Giấy phép theo định mức cho phép bạn chỉ trả tiền cho các tài nguyên bạn sử dụng, khiến nó trở thành giải pháp tiết kiệm chi phí cho các dự án ở mọi quy mô. Bằng cách làm theo các bước được nêu dưới đây, bạn sẽ có thể tích hợp GroupDocs.Annotation vào ứng dụng .NET của mình một cách liền mạch trong khi tối ưu hóa việc sử dụng tài nguyên và duy trì kiểm soát ngân sách.
## Điều kiện tiên quyết
Trước khi bắt đầu hướng dẫn, hãy đảm bảo rằng bạn đáp ứng các điều kiện tiên quyết sau:
1. GroupDocs.Annotation cho Thư viện .NET: Tải xuống thư viện từ [trang web](https://releases.groupdocs.com/annotation/net/).
2. Truy cập vào Tài khoản GroupDocs: Bạn sẽ cần một tài khoản GroupDocs để có được khóa công khai và riêng tư cần thiết để thiết lập giấy phép đo lường. Nếu bạn chưa có tài khoản, bạn có thể đăng ký dùng thử miễn phí [đây](https://releases.groupdocs.com/).
3. Hiểu biết cơ bản về C# và .NET Framework: Sự quen thuộc với ngôn ngữ lập trình C# và .NET Framework sẽ có lợi cho việc thực hiện các bước được nêu trong hướng dẫn này.

## Nhập không gian tên
Để bắt đầu, hãy đảm bảo nhập các không gian tên cần thiết vào dự án C# của bạn. Các không gian tên này rất cần thiết để tương tác với chức năng GroupDocs.Annotation.
```csharp
using System;
```
## Bước 1: Lấy khóa công khai và khóa riêng tư
Trước khi thiết lập giấy phép tính phí, bạn cần lấy khóa công khai và khóa riêng tư từ bảng điều khiển tài khoản GroupDocs của mình.
1. Đăng nhập vào tài khoản GroupDocs của bạn.
2. Điều hướng đến phần quản lý giấy phép.
3. Sao chép khóa công khai và khóa riêng tư do GroupDocs cung cấp.
## Bước 2: Thiết lập Giấy phép theo lưu lượng
Sau khi có được khóa công khai và khóa riêng tư, bạn có thể thiết lập giấy phép giới hạn trong ứng dụng .NET của mình.
```csharp
string publicKey = "*****"; // Thay thế ***** bằng khóa công khai của bạn
string privateKey = "*****"; // Thay thế ***** bằng khóa riêng của bạn
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Phần kết luận
Tóm lại, việc thiết lập giấy phép có giới hạn cho GroupDocs.Annotation .NET là một quy trình đơn giản đảm bảo sử dụng tài nguyên hiệu quả và tiết kiệm chi phí cho các dự án chú thích tài liệu của bạn. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể tích hợp GroupDocs.Annotation vào ứng dụng .NET của mình một cách liền mạch và nâng cao khả năng cộng tác và xem xét tài liệu.
## Câu hỏi thường gặp
### Tôi có thể sử dụng GroupDocs.Annotation cho .NET trong các dự án thương mại không?
Có, GroupDocs.Annotation cho .NET có thể được sử dụng trong cả dự án thương mại và phi thương mại. Tuy nhiên, bạn cần phải có giấy phép phù hợp dựa trên yêu cầu của dự án.
### Có phiên bản dùng thử của GroupDocs.Annotation dành cho .NET không?
Có, bạn có thể dùng thử miễn phí GroupDocs.Annotation cho .NET bằng cách truy cập [liên kết này](https://releases.groupdocs.com/).
### Tôi có thể nhận được hỗ trợ kỹ thuật cho GroupDocs.Annotation dành cho .NET bằng cách nào?
Bạn có thể tìm kiếm hỗ trợ kỹ thuật bằng cách truy cập diễn đàn GroupDocs [đây](https://forum.groupdocs.com/c/annotation/10).
### Có bất kỳ tùy chọn cấp phép tạm thời nào không?
Có, bạn có thể xin giấy phép tạm thời từ GroupDocs cho mục đích sử dụng hoặc đánh giá ngắn hạn. Truy cập [liên kết này](https://purchase.groupdocs.com/temporary-license/) để biết thêm thông tin.
### Tôi có thể tùy chỉnh các tính năng chú thích theo yêu cầu của dự án không?
Có, GroupDocs.Annotation cho .NET cung cấp nhiều tùy chọn tùy chỉnh, cho phép bạn điều chỉnh các tính năng chú thích sao cho phù hợp với nhu cầu cụ thể của dự án.