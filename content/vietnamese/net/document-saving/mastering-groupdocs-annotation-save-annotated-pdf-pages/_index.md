---
"date": "2025-05-06"
"description": "Tìm hiểu cách lưu hiệu quả chỉ các trang có chú thích của PDF bằng GroupDocs.Annotation cho .NET. Nâng cao khả năng quản lý tài liệu và cộng tác với hướng dẫn chi tiết này."
"title": "Cách lưu các trang có chú thích trong PDF bằng GroupDocs.Annotation cho .NET"
"url": "/vi/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
type: docs
"weight": 1
---

# Cách lưu các trang có chú thích trong PDF bằng GroupDocs.Annotation cho .NET

## Giới thiệu

Bạn đang gặp khó khăn trong việc lưu các trang chú thích cụ thể từ tài liệu PDF của mình? Hướng dẫn toàn diện này sẽ trình bày cách thực hiện việc này hiệu quả bằng cách sử dụng GroupDocs.Annotation cho .NET. Bằng cách tận dụng các khả năng chú thích, hợp lý hóa việc quản lý tài liệu và tăng cường cộng tác bằng cách tập trung vào nội dung có liên quan.

Trong hướng dẫn này, bạn sẽ học:
- Thiết lập môi trường phát triển của bạn với GroupDocs.Annotation
- Thêm nhiều loại chú thích khác nhau
- Chỉ lưu các trang có chú thích một cách hiệu quả

Bạn đã sẵn sàng bắt đầu chưa? Hãy đảm bảo rằng bạn đã chuẩn bị mọi thứ.

### Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:
- **Khung .NET** (phiên bản 4.6 trở lên) hoặc **.NET Core/5+**
- Một trình soạn thảo mã như Visual Studio
- Kiến thức cơ bản về thiết lập dự án C# và .NET

## Thiết lập GroupDocs.Annotation cho .NET

Để bắt đầu sử dụng GroupDocs.Annotation, hãy cài đặt nó thông qua NuGet.

**Bảng điều khiển quản lý gói NuGet**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NETCLI**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Mua lại giấy phép

GroupDocs cung cấp bản dùng thử miễn phí để khám phá toàn bộ phần mềm của họ. Để sử dụng lâu dài, hãy mua giấy phép hoặc yêu cầu giấy phép tạm thời:
- **Dùng thử miễn phí**: Khám phá các tính năng không giới hạn trong thời gian đầu.
- **Giấy phép tạm thời**: Sử dụng GroupDocs.Annotation trong quá trình sản xuất tạm thời.
- **Mua**Đảm bảo nhu cầu dài hạn của bạn bằng giấy phép thương mại.

Sau khi cài đặt, hãy khởi tạo thư viện như sau:

```csharp
using GroupDocs.Annotation;

// Thiết lập cơ bản để tải và chú thích tài liệu
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## Hướng dẫn thực hiện

### Thêm chú thích

#### Tổng quan

Chú thích giúp làm nổi bật các khu vực quan trọng trong tài liệu của bạn. Hãy cùng khám phá cách thêm `AreaAnnotation` và một `EllipseAnnotation`.

**Bước 1: Tạo chú thích khu vực**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// Xác định chú thích khu vực
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Vị trí và kích thước
    BackgroundColor = 65535,                // Giá trị màu ARGB để làm nổi bật
    PageNumber = 1                          // Số trang cụ thể
};
```

Các `AreaAnnotation` làm nổi bật một vùng hình chữ nhật trên tài liệu. Tùy chỉnh vị trí của nó (`Box`) và màu nền.

**Bước 2: Tạo chú thích hình elip**

```csharp
// Xác định chú thích hình elip
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Vị trí và kích thước
    BackgroundColor = 123456,                // Giá trị màu ARGB để làm nổi bật
    PageNumber = 1                           // Số trang cụ thể
};
```

Các `EllipseAnnotation` cho phép vẽ hình bầu dục trên tài liệu. Điều chỉnh vị trí và kích thước bằng cách sử dụng `Box` tài sản.

**Bước 3: Thêm chú thích**

```csharp
// Thêm chú thích vào phiên bản Annotator
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

Sử dụng `Add` phương pháp, bao gồm nhiều loại chú thích. Bước này thêm cả `AreaAnnotation` Và `EllipseAnnotation`.

### Chỉ lưu các trang có chú thích

#### Tổng quan

Để chỉ lưu các trang có chú thích, hãy cấu hình tùy chọn lưu của bạn cho phù hợp.

**Bước 4: Lưu các trang có chú thích**

```csharp
using GroupDocs.Annotation.Options;

// Thiết lập tùy chọn lưu để chỉ bao gồm các trang có chú thích
annotator.Save("path/to/output/document.pdf\