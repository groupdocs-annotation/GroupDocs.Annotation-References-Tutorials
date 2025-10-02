---
"date": "2025-05-06"
"description": "Tìm hiểu cách tạo bản xem trước tài liệu ngắn gọn và có liên quan từ các cột bảng tính cụ thể bằng GroupDocs.Annotation cho .NET. Hoàn hảo để hợp lý hóa quy trình làm việc trong phân tích dữ liệu và quản lý CNTT."
"title": "Tạo bản xem trước trang tính Excel có mục tiêu bằng GroupDocs.Annotation .NET"
"url": "/vi/net/document-preview/groupdocs-annotation-net-create-previews-worksheet-columns/"
type: docs
"weight": 1
---

# Tạo bản xem trước trang tính Excel có mục tiêu bằng GroupDocs.Annotation .NET
## Hướng dẫn xem trước tài liệu
### Giới thiệu
Bạn có muốn tăng cường tính rõ ràng của quá trình xử lý tài liệu bằng cách tập trung vào các điểm dữ liệu cụ thể không? Cho dù bạn là nhà phát triển tạo công cụ phân tích dữ liệu, chuyên gia CNTT quản lý tài liệu hay bất kỳ ai quan tâm đến việc hợp lý hóa quy trình làm việc, thì bản xem trước tài liệu có mục tiêu có thể tiết kiệm thời gian và cải thiện hiệu quả. Hướng dẫn này sẽ hướng dẫn bạn sử dụng GroupDocs.Annotation cho .NET để tạo bản xem trước từ các cột bảng tính đã chọn, đảm bảo đầu ra của bạn ngắn gọn và có liên quan.

#### Những gì bạn sẽ học được:
- Cách thiết lập GroupDocs.Annotation cho .NET
- Tạo bản xem trước với các cột bảng tính được chỉ định
- Cấu hình tùy chọn xem trước để có đầu ra tối ưu
- Ứng dụng thực tế của tính năng này trong các tình huống thực tế

Hãy bắt đầu bằng cách xem xét các điều kiện tiên quyết cần thiết trước khi bạn bắt đầu triển khai giải pháp này.
## Điều kiện tiên quyết
Trước khi bắt đầu triển khai, hãy đảm bảo rằng bạn có những điều sau:

### Thư viện và phiên bản bắt buộc:
- **GroupDocs.Annotation cho .NET**: Yêu cầu phiên bản 25.4.0 trở lên.

### Yêu cầu thiết lập môi trường:
- Môi trường phát triển có cài đặt .NET Framework hoặc .NET Core.

### Điều kiện tiên quyết về kiến thức:
- Hiểu biết cơ bản về lập trình C#
- Làm quen với các hoạt động I/O tệp trong .NET
## Thiết lập GroupDocs.Annotation cho .NET
Để bắt đầu, bạn cần cài đặt thư viện GroupDocs.Annotation. Sau đây là cách bạn có thể thực hiện bằng các trình quản lý gói khác nhau:

**Bảng điều khiển quản lý gói NuGet**
```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NETCLI**
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Các bước xin cấp phép:
- **Dùng thử miễn phí**: Tải xuống phiên bản dùng thử từ [Trang web GroupDocs](https://releases.groupdocs.com/annotation/net/) để kiểm tra các tính năng.
- **Giấy phép tạm thời**: Nhận giấy phép tạm thời để truy cập đầy đủ trong quá trình phát triển tại [Trang giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/).
- **Mua**: Đối với mục đích sản xuất, hãy mua giấy phép thông qua [Trang mua hàng của GroupDocs](https://purchase.groupdocs.com/buy).
### Khởi tạo và thiết lập cơ bản bằng C#:
Sau đây là cách bạn có thể thiết lập môi trường để bắt đầu làm việc với GroupDocs.Annotation cho .NET.
```csharp
using System;
using GroupDocs.Annotation;
// Khởi tạo đối tượng Annotator bằng đường dẫn tài liệu.
string inputFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.xlsx";
Annotator annotator = new Annotator(inputFilePath);
```
Bây giờ bạn đã thiết lập xong, hãy chuyển sang tạo bản xem trước từ các cột cụ thể của bảng tính.
## Hướng dẫn thực hiện
Hướng dẫn này sẽ hướng dẫn bạn cách triển khai tính năng tạo bản xem trước tài liệu với các cột bảng tính được chỉ định. Mỗi phần tập trung vào một khía cạnh cụ thể của quy trình triển khai.
### Tạo bản xem trước tài liệu từ các cột bảng tính cụ thể
**Tổng quan**Tính năng này cho phép các nhà phát triển tạo bản xem trước tài liệu chỉ bao gồm các cột được chọn từ bảng tính Excel, cải thiện cả hiệu suất và tính liên quan.
#### Bước 1: Xác định Tùy chọn Xem trước
Bắt đầu bằng cách thiết lập `PreviewOptions`. Điều này xác định cách thức và vị trí lưu tệp xem trước của bạn.
```csharp
using System.IO;
using GroupDocs.Annotation.Options;
string outputDirectoryPath = "YOUR_OUTPUT_DIRECTORY";
PreviewOptions previewOptions = new PreviewOptions(pageNumber => 
    new FileStream(Path.Combine(outputDirectoryPath, $"cells_page{pageNumber}.png"), FileMode.Create),
    (number, stream) => stream.Dispose());
```
**Giải thích**: Các `PreviewOptions` constructor lấy hai đại biểu. Đại biểu đầu tiên chỉ định đường dẫn tệp cho hình ảnh xem trước của mỗi trang. Đại biểu thứ hai đảm bảo rằng các luồng được xử lý đúng cách sau khi sử dụng.
#### Bước 2: Chỉ định các cột bảng tính
Chọn các cột từ bảng tính của bạn mà bạn muốn đưa vào bản xem trước bằng cách thêm chúng vào `WorksheetColumns`.
```csharp
// Bao gồm các cột cụ thể từ Sheet1.
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1\