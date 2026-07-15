---
categories:
- Document Processing
date: '2026-04-01'
description: Tìm hiểu cách tạo thumbnail trong .NET mà không có bình luận bằng GroupDocs.Annotation.
  Hướng dẫn này sẽ chỉ cách ẩn chú thích, loại bỏ phần xem trước bình luận và tạo
  bản xem trước PDF sạch sẽ.
keywords:
- how to generate thumbnails
- how to hide annotations
- remove comments preview
- document preview without comments
- clean pdf preview
lastmod: '2026-04-01'
linktitle: Tạo bản xem trước mà không có bình luận
second_title: GroupDocs.Annotation .NET API
tags:
- document-preview
- pdf-thumbnails
- groupdocs
- dotnet
title: Cách tạo hình thu nhỏ trong .NET – Xem trước PDF sạch sẽ
type: docs
url: /vi/net/advanced-usage/generate-preview-without-comments/
weight: 14
---

# Cách tạo hình thu nhỏ trong .NET – Xem trước PDF sạch

## Giới thiệu

Bạn đã bao giờ cần **cách tạo hình thu nhỏ** cho một trình xem tài liệu, trình khám phá tệp, hoặc hệ thống quản lý nội dung trong khi giữ cho hình ảnh không có bất kỳ ghi chú nào của người dùng không? Bạn không phải là người duy nhất. Nhiều nhà phát triển .NET gặp khó khăn khi họ cố gắng tạo các bản xem trước tài liệu mà ẩn các chú thích và bình luận.

Trong hướng dẫn này, chúng tôi sẽ hướng dẫn chi tiết các bước để tạo ra các bản xem trước PDF sạch bằng cách sử dụng **GroupDocs.Annotation for .NET**. Bạn sẽ thấy cách ẩn chú thích, loại bỏ bản xem trước bình luận, và tạo các hình thu nhỏ chuyên nghiệp phù hợp hoàn hảo trong các bộ sưu tập, bảng điều khiển, hoặc bất kỳ giao diện người dùng nào cần một ảnh chụp nhanh không rối mắt.

## Câu trả lời nhanh

- **Thư viện nào tạo hình thu nhỏ không có bình luận?** GroupDocs.Annotation for .NET  
- **Thuộc tính nào vô hiệu hoá chú thích?** `RenderComments = false`  
- **Tôi có thể chọn định dạng hình ảnh không?** Có – PNG, JPEG, BMP, v.v. qua `PreviewFormat`  
- **Tôi có cần giấy phép cho môi trường sản xuất không?** Cần một giấy phép thương mại; giấy phép tạm thời hoạt động cho việc thử nghiệm.  
- **Nó chỉ hỗ trợ .NET không?** Hoạt động với .NET Framework, .NET Core, và .NET 5/6+.

## Tạo hình thu nhỏ mà không có bình luận là gì?

Tạo hình thu nhỏ mà không có bình luận có nghĩa là tạo ra một ảnh chụp nhanh trực quan của mỗi trang **không** có bất kỳ đánh dấu, ghi chú, hoặc chú thích cộng tác nào có thể đã được thêm vào tệp gốc. Kết quả là một hình ảnh tĩnh, sạch sẽ đại diện cho nội dung thực của tài liệu—lý tưởng cho các cổng thông tin công cộng, kho lưu trữ pháp lý, hoặc bất kỳ kịch bản nào mà các nhận xét nội bộ phải được ẩn.

## Tại sao lại ẩn chú thích khi tạo bản xem trước?

- **Giao diện chuyên nghiệp:** Người dùng cuối chỉ thấy nội dung tài liệu, không phải các cuộc thảo luận đánh giá.  
- **Bảo mật & riêng tư:** Các bình luận nhạy cảm được giữ nội bộ.  
- **Hiệu suất:** Việc render ít lớp hơn giúp tăng tốc tạo hình ảnh.  
- **Tính nhất quán:** Các hình thu nhỏ khớp với các phiên bản đã in hoặc xuất ra mà cũng không có bình luận.

## Yêu cầu trước

### 1. Cài đặt GroupDocs.Annotation for .NET
Tải gói từ trang phân phối chính thức **[đây](https://releases.groupdocs.com/annotation/net/)** hoặc cài đặt qua NuGet. Đảm bảo dự án của bạn nhắm tới một phiên bản .NET được hỗ trợ.

### 2. Nhận giấy phép
Cần một giấy phép thương mại cho việc sử dụng trong môi trường sản xuất. Mua một giấy phép **[tại đây](https://purchase.groupdocs.com/buy)** hoặc yêu cầu giấy phép đánh giá tạm thời **[tại đây](https://purchase.groupdocs.com/temporary-license/)**.

### 3. Kiến thức .NET
Bạn nên quen thuộc với các kiến thức cơ bản của C#, I/O tệp, và việc sử dụng câu lệnh `using` để quản lý tài nguyên.

## Nhập không gian tên

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

## Hướng dẫn từng bước: Tạo bản xem trước tài liệu sạch

### Bước 1: Khởi tạo Annotator
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
Đối tượng `Annotator` tải tệp nguồn. Khối `using` đảm bảo rằng tất cả các tài nguyên không quản lý được giải phóng khi chúng ta hoàn thành.

### Bước 2: Cấu hình tùy chọn xem trước
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
Ở đây chúng tôi chỉ cho thư viện nơi lưu trữ hình ảnh của mỗi trang. Lambda nhận số trang và trả về một `FileStream` có thể ghi.

### Bước 3: Chọn định dạng và các trang
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
PNG cung cấp các hình thu nhỏ sắc nét, nhưng bạn có thể chuyển sang JPEG nếu kích thước tệp là mối quan tâm lớn hơn. Lựa chọn một tập hợp con các trang sẽ giảm thời gian xử lý—lý tưởng cho các bộ sưu tập hình thu nhỏ chỉ cần vài trang đầu.

### Bước 4: Vô hiệu hoá việc render bình luận
```csharp
    previewOptions.RenderComments = false;
```
**Dòng này là chìa khóa để “cách ẩn chú thích.”** Đặt `RenderComments` thành `false` sẽ loại bỏ tất cả các lớp bình luận, cung cấp cho bạn một bản xem trước PDF sạch.

### Bước 5: Tạo các hình ảnh xem trước
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
Thư viện xử lý tài liệu và ghi các hình ảnh vào các vị trí bạn đã định nghĩa trước đó.

## Các thực hành tốt nhất cho việc tạo bản xem trước tài liệu

- **Thay đổi kích thước cho hình thu nhỏ:** Sau khi tạo PNG, hãy cân nhắc thay đổi kích thước chúng xuống khoảng ~200 × 300 px để tải UI nhanh hơn.  
- **Xử lý tệp lớn theo lô:** Ban đầu chỉ tạo vài trang đầu, sau đó tạo phần còn lại khi cần.  
- **Luôn bao bọc trong `using`:** Đảm bảo dọn dẹp bộ nhớ đúng cách, đặc biệt khi xử lý nhiều tài liệu.  
- **Thêm xử lý lỗi:** Bắt `FileNotFoundException`, `InvalidOperationException`, và các lỗi giấy phép để giữ cho ứng dụng của bạn ổn định.

## Các vấn đề thường gặp và khắc phục

- **Không có hình ảnh nào xuất hiện:** Kiểm tra thư mục đầu ra tồn tại và ứng dụng có quyền ghi.  
- **Hình thu nhỏ mờ:** Thử tăng DPI bằng cách đặt `previewOptions.Dpi = 150;` (không hiển thị trong mã để giữ nguyên khối gốc).  
- **Lỗi hết bộ nhớ khi xử lý PDF lớn:** Xử lý từng trang một, hoặc sử dụng API async trong một worker nền.  
- **Không tìm thấy giấy phép:** Đảm bảo đối tượng `License` được tải trước khi tạo `Annotator`.

## Mẹo tối ưu hoá hiệu suất

- **Xử lý nhiều tài liệu cùng lúc:** Lặp qua một bộ sưu tập và tái sử dụng một thể hiện `Annotator` duy nhất khi có thể.  
- **Tạo async:** Chuyển việc tạo bản xem trước sang một dịch vụ nền để giao diện người dùng luôn phản hồi.  
- **Lưu kết quả trong cache:** Lưu các hình thu nhỏ đã tạo vào CDN hoặc bộ nhớ cache cục bộ để tránh xử lý lại cùng một tệp.  
- **Chọn định dạng phù hợp:** PNG cho chất lượng không mất dữ liệu, JPEG cho tệp nhỏ hơn khi tài liệu chứa nhiều hình ảnh.

## Các định dạng tài liệu được hỗ trợ

GroupDocs.Annotation for .NET có thể tạo bản xem trước cho:

- **PDF** – trường hợp sử dụng phổ biến nhất.  
- **Microsoft Office** – DOCX, XLSX, PPTX và các định dạng kế thừa của chúng.  
- **Hình ảnh** – TIFF, JPEG, PNG, BMP (hữu ích cho tài liệu đã quét).  
- **OpenDocument** – ODT, ODS, ODP và các tiêu chuẩn mở khác.

## Khi nào nên sử dụng tạo bản xem trước không có bình luận

- **Cổng thông tin công cộng** nơi các ghi chú đánh giá nội bộ phải được ẩn.  
- **Trình duyệt lưu trữ** hiển thị lưới hình thu nhỏ sạch sẽ.  
- **Quy trình sẵn sàng in** cần hiển thị hình ảnh cuối cùng trước khi gửi tới máy in.  
- **Kiểm tra kiểm soát chất lượng** nơi bạn so sánh phiên bản “có bình luận” và “không có bình luận”.

## Kết luận

Bây giờ bạn đã biết **cách tạo hình thu nhỏ** trong .NET đồng thời loại bỏ hoàn toàn các chú thích và bình luận. Bằng cách đặt `RenderComments = false` bạn sẽ có các bản xem trước PDF sạch sẽ, chuyên nghiệp, phù hợp hoàn hảo với bất kỳ giao diện người dùng nào. Hãy nhớ tùy chỉnh định dạng xem trước, lựa chọn trang và kích thước hình ảnh cho kịch bản cụ thể của bạn, và luôn xử lý giấy phép và các trường hợp lỗi một cách khéo léo. Với những bước này, ứng dụng của bạn sẽ cung cấp các hình thu nhỏ tài liệu nhanh chóng, không rối mắt, nâng cao trải nghiệm người dùng.

## Câu hỏi thường gặp

**Q: GroupDocs.Annotation for .NET có tương thích với tất cả các định dạng tài liệu không?**  
A: Có. Nó hỗ trợ PDF, DOCX, PPTX, XLSX, các loại hình ảnh phổ biến, và nhiều định dạng OpenDocument.

**Q: Tôi có thể tùy chỉnh giao diện của các bản xem trước đã tạo không?**  
A: Chắc chắn. Bạn có thể thay đổi `PreviewFormat`, đặt kích thước hình ảnh, DPI, và chọn các trang cụ thể để render.

**Q: Thư viện có hỗ trợ cộng tác đa người dùng không?**  
A: GroupDocs.Annotation cung cấp các tính năng chú thích cộng tác. Việc tạo bản xem trước có thể được sử dụng để tạo các giao diện sạch sẽ ẩn tất cả bình luận của người dùng.

**Q: Tôi có thể nhận được sự hỗ trợ ở đâu nếu gặp vấn đề?**  
A: Cộng đồng và đội ngũ hỗ trợ hoạt động trên **[diễn đàn hỗ trợ](https://forum.groupdocs.com/c/annotation/10)** nơi bạn có thể đặt câu hỏi và chia sẻ kinh nghiệm.

**Q: Có bản dùng thử miễn phí không?**  
A: Có, bạn có thể tải xuống bản dùng thử đầy đủ chức năng **[tại đây](https://releases.groupdocs.com/)** để thử nghiệm khả năng tạo bản xem trước trước khi mua.

---

**Cập nhật lần cuối:** 2026-04-01  
**Kiểm tra với:** GroupDocs.Annotation for .NET (latest release)  
**Tác giả:** GroupDocs  

---