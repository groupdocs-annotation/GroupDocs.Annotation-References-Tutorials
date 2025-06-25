---
"description": "Tìm hiểu cách chú thích tài liệu trong .NET bằng GroupDocs.Annotation. Hướng dẫn từng bước để tích hợp liền mạch với Azure Blob Storage."
"linktitle": "Tải tài liệu từ Azure"
"second_title": "GroupDocs.Chú thích API .NET"
"title": "Tải tài liệu từ Azure"
"url": "/vi/net/document-loading-essentials/load-document-from-azure/"
"weight": 11
---

# Tải tài liệu từ Azure

## Giới thiệu
Trong lĩnh vực quản lý và cộng tác tài liệu, GroupDocs.Annotation for .NET nổi lên như một giải pháp mạnh mẽ, tạo điều kiện cho các chức năng chú thích và đánh dấu liền mạch trong các ứng dụng .NET. Hướng dẫn này đi sâu vào sự phức tạp của việc tận dụng GroupDocs.Annotation for .NET để chú thích tài liệu, cung cấp hướng dẫn từng bước từ các điều kiện tiên quyết đến cách sử dụng nâng cao.
## Điều kiện tiên quyết
Trước khi tìm hiểu sâu hơn về GroupDocs.Annotation cho .NET, hãy đảm bảo bạn đã đáp ứng đủ các điều kiện tiên quyết sau:
1. Cài đặt .NET Framework: GroupDocs.Annotation cho .NET yêu cầu môi trường chạy .NET tương thích. Đảm bảo rằng bạn đã cài đặt .NET Framework trên hệ thống của mình.
2. Truy cập vào thư viện GroupDocs.Annotation: Truy cập vào thư viện GroupDocs.Annotation cho .NET bằng cách tải xuống từ trang web hoặc thông qua trình quản lý gói như NuGet.
3. Tài liệu cần chú thích: Chuẩn bị tài liệu (ví dụ: PDF) mà bạn định chú thích. Đảm bảo rằng tài liệu có thể truy cập cục bộ hoặc thông qua dịch vụ lưu trữ đám mây như Azure Blob Storage.

## Nhập không gian tên
Để bắt đầu chú thích tài liệu bằng GroupDocs.Annotation cho .NET, hãy nhập các không gian tên cần thiết vào dự án của bạn. Bước này đảm bảo rằng bạn có quyền truy cập vào các lớp và chức năng cần thiết.
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
Để chú thích một tài liệu được lưu trữ trong Azure Blob Storage, hãy làm theo các bước sau:
### Bước 1: Thiết lập Đường dẫn đầu ra
Xác định đường dẫn đầu ra nơi tài liệu có chú thích sẽ được lưu.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Bước 2: Tải xuống tài liệu
Truy xuất tài liệu từ Azure Blob Storage bằng cách gọi lệnh `DownloadFile` phương pháp.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Logic chú thích
    annotator.Save(outputPath);
}
```
## Tải xuống tệp từ Azure Blob Storage
Để tải xuống tài liệu từ Azure Blob Storage, hãy triển khai `DownloadFile` phương pháp.
### Bước 1: Lấy lại Blob
Truy cập vào vùng chứa Azure Blob Storage và lấy blob mong muốn.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### Bước 2: Tải xuống nội dung Blob
Tải nội dung blob vào luồng bộ nhớ.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Nhận Azure Blob Storage Container
Để tương tác với Azure Blob Storage, hãy triển khai `GetContainer` phương pháp.
### Bước 1: Khởi tạo thông tin xác thực lưu trữ
Cung cấp thông tin tài khoản và thông tin điểm cuối cần thiết.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{tên tài khoản}.blob.core.windows.net/";
```
### Bước 2: Tạo Blob Client
Tạo một ứng dụng khách để tương tác với Azure Blob Storage.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### Bước 3: Truy xuất tham chiếu vùng chứa
Nhận hướng dẫn về vùng chứa được chỉ định.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### Bước 4: Tạo Container nếu không tồn tại
Đảm bảo rằng container tồn tại và tạo nó nếu chưa có.
```csharp
container.CreateIfNotExists();
```

## Phần kết luận
GroupDocs.Annotation for .NET cung cấp cho các nhà phát triển khả năng chú thích tài liệu mạnh mẽ, tích hợp liền mạch vào các ứng dụng .NET. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể tận dụng hiệu quả các chức năng của GroupDocs.Annotation để chú thích các tài liệu được lưu trữ trong Azure Blob Storage.
#### Câu hỏi thường gặp
### GroupDocs.Annotation cho .NET có tương thích với mọi định dạng tài liệu không?
GroupDocs.Annotation hỗ trợ nhiều định dạng tài liệu, bao gồm PDF, DOCX, PPTX, v.v.
### Có thể tùy chỉnh chú thích theo yêu cầu cụ thể không?
Có, GroupDocs.Annotation cung cấp nhiều tùy chọn tùy chỉnh cho chú thích, cho phép người dùng sửa đổi giao diện, hành vi và siêu dữ liệu.
### GroupDocs.Annotation có phù hợp để chú thích tài liệu cộng tác không?
Chắc chắn rồi! GroupDocs.Annotation hỗ trợ chú thích tài liệu cộng tác bằng cách cho phép nhiều người dùng thêm, chỉnh sửa và xem lại chú thích cùng lúc.
### GroupDocs.Annotation có khả năng tương thích đa nền tảng không?
Có, GroupDocs.Annotation được thiết kế để hoạt động liền mạch trên nhiều nền tảng khác nhau, bao gồm Windows, Linux và macOS.
### Người dùng GroupDocs.Annotation có được hỗ trợ kỹ thuật không?
Có, GroupDocs cung cấp hỗ trợ kỹ thuật toàn diện thông qua diễn đàn và kênh hỗ trợ chuyên dụng.