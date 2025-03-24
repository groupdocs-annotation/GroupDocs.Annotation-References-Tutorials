---
title: Tải tài liệu từ FTP
linktitle: Tải tài liệu từ FTP
second_title: GroupDocs.Annotation .NET API
description: Nâng cao các ứng dụng .NET của bạn với GroupDocs.Annotation để chú thích tài liệu liền mạch. Hướng dẫn từng bước bao gồm.
weight: 12
url: /vi/net/document-loading-essentials/load-document-from-ftp/
---

# Tải tài liệu từ FTP

## Giới thiệu
GroupDocs.Annotation for .NET là một thư viện đa năng được thiết kế để hỗ trợ khả năng chú thích tài liệu trong các ứng dụng .NET một cách dễ dàng. Cho dù bạn đang xử lý tệp PDF, tài liệu Microsoft Office, hình ảnh hay các định dạng khác, thư viện này đều cung cấp giải pháp thống nhất để thêm chú thích, chẳng hạn như nhận xét, đánh dấu và hình dạng, nhằm nâng cao khả năng cộng tác và quản lý tài liệu.
## Điều kiện tiên quyết
Trước khi đi sâu vào hướng dẫn, hãy đảm bảo rằng bạn có sẵn các điều kiện tiên quyết sau:
1. Kiến thức về C#: Cần phải thành thạo ngôn ngữ lập trình C# để hiểu và triển khai các ví dụ mã được cung cấp trong hướng dẫn này.
2.  GroupDocs.Annotation cho .NET: Đảm bảo tải xuống và cài đặt GroupDocs.Annotation cho .NET từ[Liên kết tải xuống](https://releases.groupdocs.com/annotation/net/). Làm theo hướng dẫn cài đặt để tích hợp thư viện vào dự án .NET của bạn thành công.
## Nhập không gian tên
Để sử dụng GroupDocs.Annotation cho các chức năng .NET, bạn cần nhập các vùng tên cần thiết vào dự án C# của mình. Thực hiện theo các bước sau:

Trong dự án C# của bạn, hãy bao gồm các vùng tên cần thiết ở đầu tệp mã của bạn:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Bây giờ, hãy đi sâu vào quá trình tải tài liệu từ FTP và thêm chú thích vào tài liệu đó bằng GroupDocs.Annotation for .NET.
## Bước 1: Xác định đường dẫn đầu ra
Chỉ định đường dẫn đầu ra nơi tài liệu được chú thích sẽ được lưu.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Bước 2: Tải tài liệu từ FTP
Truy xuất tài liệu từ máy chủ FTP bằng đường dẫn tệp được cung cấp.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Mã chú thích sẽ được thêm vào đây
}
```
## Bước 3: Thêm chú thích
Xác định và thêm chú thích mong muốn, chẳng hạn như chú thích khu vực, vào tài liệu.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Bước 4: Lưu tài liệu chú thích
Lưu tài liệu có chú thích vào đường dẫn đầu ra đã chỉ định.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Bước 5: Truy xuất tệp từ FTP
Thực hiện phương pháp tìm nạp tệp từ máy chủ FTP.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## Bước 6: Tạo yêu cầu FTP
Tạo yêu cầu FTP để tải xuống tệp.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Bước 7: Nhận luồng tệp
Truy xuất luồng tệp từ phản hồi FTP.
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## Phần kết luận
Tóm lại, GroupDocs.Annotation dành cho .NET trao quyền cho các nhà phát triển tích hợp liền mạch các chức năng chú thích tài liệu vào các ứng dụng .NET của họ. Bằng cách làm theo hướng dẫn từng bước được nêu trong hướng dẫn này, bạn có thể tải tài liệu từ FTP một cách hiệu quả và thêm chú thích một cách dễ dàng, tăng cường cộng tác và quản lý tài liệu trong ứng dụng của bạn.
## Câu hỏi thường gặp
### GroupDocs.Annotation for .NET có tương thích với tất cả các định dạng tài liệu không?
Có, GroupDocs.Annotation for .NET hỗ trợ nhiều định dạng tài liệu, bao gồm PDF, tài liệu Microsoft Office, hình ảnh, v.v.
### Tôi có thể tùy chỉnh giao diện của chú thích được thêm bằng GroupDocs.Annotation cho .NET không?
Hoàn toàn có thể, GroupDocs.Annotation dành cho .NET cung cấp các tùy chọn tùy chỉnh mở rộng về giao diện chú thích, bao gồm màu sắc, kiểu dáng và hình dạng.
### GroupDocs.Annotation cho .NET có cung cấp hỗ trợ cho các dịch vụ lưu trữ đám mây không?
Có, GroupDocs.Annotation for .NET tích hợp liền mạch với các dịch vụ lưu trữ đám mây phổ biến, cho phép bạn tải và lưu tài liệu từ các dịch vụ như Dropbox, Google Drive và OneDrive.
### Có phiên bản dùng thử cho GroupDocs.Annotation cho .NET không?
 Có, bạn có thể khám phá các tính năng của GroupDocs.Annotation dành cho .NET bằng cách tải xuống phiên bản dùng thử miễn phí từ[trang phát hành](https://releases.groupdocs.com/).
### Làm cách nào tôi có thể nhận được hỗ trợ hoặc hỗ trợ kỹ thuật cho GroupDocs.Annotation cho .NET?
 Để được hỗ trợ kỹ thuật, khắc phục sự cố hoặc yêu cầu chung, bạn có thể truy cập GroupDocs.Annotation for .NET[diễn đàn hỗ trợ](https://forum.groupdocs.com/c/annotation/10).