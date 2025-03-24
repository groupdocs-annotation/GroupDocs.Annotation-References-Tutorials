---
title: Tải tài liệu từ Azure
linktitle: Tải tài liệu từ Azure
second_title: GroupDocs.Annotation .NET API
description: Tìm hiểu cách chú thích tài liệu trong .NET bằng GroupDocs.Annotation. Hướng dẫn từng bước để tích hợp liền mạch với Azure Blob Storage.
weight: 11
url: /vi/net/document-loading-essentials/load-document-from-azure/
---

# Tải tài liệu từ Azure

## Giới thiệu
Trong lĩnh vực cộng tác và quản lý tài liệu, GroupDocs.Annotation dành cho .NET nổi lên như một giải pháp mạnh mẽ, hỗ trợ các chức năng đánh dấu và chú thích liền mạch trong các ứng dụng .NET. Hướng dẫn này đi sâu vào sự phức tạp của việc tận dụng GroupDocs.Annotation cho .NET để chú thích tài liệu, cung cấp hướng dẫn từng bước từ điều kiện tiên quyết đến cách sử dụng nâng cao.
## Điều kiện tiên quyết
Trước khi đi sâu vào GroupDocs.Annotation cho .NET, hãy đảm bảo bạn có sẵn các điều kiện tiên quyết sau:
1. Cài đặt .NET Framework: GroupDocs.Annotation cho .NET yêu cầu môi trường thời gian chạy .NET tương thích. Đảm bảo rằng bạn đã cài đặt .NET Framework trên hệ thống của mình.
2. Truy cập vào Thư viện GroupDocs.Annotation: Có quyền truy cập vào thư viện GroupDocs.Annotation cho .NET bằng cách tải xuống từ trang web hoặc thông qua trình quản lý gói như NuGet.
3. Tài liệu cần chú thích: Chuẩn bị tài liệu (ví dụ: PDF) mà bạn định chú thích. Đảm bảo rằng tài liệu có thể truy cập được cục bộ hoặc thông qua dịch vụ lưu trữ đám mây như Azure Blob Storage.

## Nhập không gian tên
Để bắt đầu chú thích tài liệu bằng GroupDocs.Annotation cho .NET, hãy nhập các vùng tên cần thiết vào dự án của bạn. Bước này đảm bảo rằng bạn có quyền truy cập vào các lớp và chức năng cần thiết.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Tải tài liệu từ Azure
Để chú thích tài liệu được lưu trữ trong Azure Blob Storage, hãy làm theo các bước sau:
### Bước 1: Đặt đường dẫn đầu ra
Xác định đường dẫn đầu ra nơi tài liệu chú thích sẽ được lưu.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Bước 2: Tải tài liệu
 Truy xuất tài liệu từ Azure Blob Storage bằng cách gọi`DownloadFile` phương pháp.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Logic chú thích
    annotator.Save(outputPath);
}
```
## Tải xuống tệp từ bộ lưu trữ Azure Blob
 Để tải xuống tài liệu từ Azure Blob Storage, hãy triển khai`DownloadFile` phương pháp.
### Bước 1: Truy xuất Blob
Truy cập vùng lưu trữ Azure Blob Storage và truy xuất blob mong muốn.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### Bước 2: Tải xuống nội dung Blob
Tải nội dung blob xuống luồng bộ nhớ.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Nhận Bộ chứa lưu trữ Azure Blob
 Để tương tác với Azure Blob Storage, hãy triển khai`GetContainer` phương pháp.
### Bước 1: Khởi tạo thông tin xác thực lưu trữ
Cung cấp thông tin xác thực tài khoản cần thiết và thông tin điểm cuối.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{accountName}.blob.core.windows.net/";
```
### Bước 2: Tạo ứng dụng khách Blob
Tạo một ứng dụng khách để tương tác với Azure Blob Storage.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### Bước 3: Truy xuất tham chiếu vùng chứa
Lấy tham chiếu đến vùng chứa được chỉ định.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### Bước 4: Tạo vùng chứa nếu không tồn tại
Đảm bảo rằng vùng chứa tồn tại và tạo nó nếu không.
```csharp
container.CreateIfNotExists();
```

## Phần kết luận
GroupDocs.Annotation dành cho .NET trao quyền cho các nhà phát triển khả năng chú thích tài liệu mạnh mẽ, tích hợp liền mạch vào các ứng dụng .NET. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể tận dụng hiệu quả các chức năng của GroupDocs.Annotation để chú thích các tài liệu được lưu trữ trong Azure Blob Storage.
#### Câu hỏi thường gặp
### GroupDocs.Annotation for .NET có tương thích với tất cả các định dạng tài liệu không?
GroupDocs.Annotation hỗ trợ nhiều định dạng tài liệu, bao gồm PDF, DOCX, PPTX, v.v.
### Chú thích có thể được tùy chỉnh theo yêu cầu cụ thể không?
Có, GroupDocs.Annotation cung cấp các tùy chọn tùy chỉnh mở rộng cho chú thích, cho phép người dùng sửa đổi giao diện, hành vi và siêu dữ liệu.
### GroupDocs.Annotation có phù hợp với chú thích tài liệu cộng tác không?
Tuyệt đối! GroupDocs.Annotation tạo điều kiện thuận lợi cho việc cộng tác chú thích tài liệu bằng cách cho phép nhiều người dùng thêm, chỉnh sửa và xem lại các chú thích cùng một lúc.
### GroupDocs.Annotation có cung cấp khả năng tương thích đa nền tảng không?
Có, GroupDocs.Annotation được thiết kế để hoạt động trơn tru trên nhiều nền tảng khác nhau, bao gồm Windows, Linux và macOS.
### Người dùng GroupDocs.Annotation có được hỗ trợ kỹ thuật không?
Có, GroupDocs cung cấp hỗ trợ kỹ thuật toàn diện thông qua các diễn đàn và các kênh hỗ trợ riêng.