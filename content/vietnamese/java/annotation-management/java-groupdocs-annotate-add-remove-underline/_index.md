---
categories:
- Java Development
date: '2025-12-21'
description: Tìm hiểu cách tạo các tệp PDF Java sạch sẽ và chú thích PDF trong Java
  bằng GroupDocs.Annotation, kèm theo các ví dụ mã đầy đủ và mẹo khắc phục sự cố.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2025-12-21'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'Tạo PDF sạch bằng Java: Gạch chân chú thích với GroupDocs'
type: docs
url: /vi/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Tạo PDF Java Sạch: Ghi chú Gạch chân với GroupDocs

## Giới thiệu

Bạn đang gặp khó khăn trong việc quản lý tài liệu và cộng tác trong các ứng dụng Java của mình? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp thách thức trong việc triển khai các tính năng chú thích tài liệu mạnh mẽ, hoạt động đáng tin cậy trên các định dạng tệp khác nhau.

Trong hướng dẫn này, bạn sẽ **tạo các tệp PDF Java sạch** và học cách **chú thích PDF trong Java** bằng GroupDocs.Annotation. Khi kết thúc tutorial, bạn sẽ biết chính xác cách thêm ghi chú gạch chân kèm bình luận, xóa các chú thích hiện có, và tích hợp các tính năng này một cách liền mạch vào dự án của mình.

**Bạn sẽ nắm vững trong hướng dẫn này:**
- Cài đặt GroupDocs.Annotation trong dự án Java của bạn (đúng cách)  
- Thêm ghi chú gạch chân với bình luận tùy chỉnh và kiểu dáng  
- Xóa tất cả các chú thích để tạo các phiên bản tài liệu sạch  
- Khắc phục các vấn đề phổ biến mà nhà phát triển gặp phải  
- Tối ưu hiệu năng cho các ứng dụng sản xuất  

Dù bạn đang xây dựng hệ thống duyệt tài liệu, nền tảng giáo dục, hay công cụ chỉnh sửa cộng tác, tutorial này sẽ cung cấp cho bạn các ví dụ mã thực tế, đã được kiểm chứng.

## Câu trả lời nhanh
- **Làm thế nào để thêm ghi chú gạch chân?** Sử dụng `UnderlineAnnotation` và `annotator.add()` rồi lưu tài liệu.  
- **Làm sao để tạo tệp PDF Java sạch?** Tải tệp đã chú thích, đặt `AnnotationType.NONE` trong `SaveOptions`, và lưu một bản sao mới.  
- **Thư viện nào cần thiết?** GroupDocs.Annotation v25.2 (hoặc mới hơn) và kho Maven của nó.  
- **Có cần giấy phép cho môi trường sản xuất không?** Có — áp dụng giấy phép GroupDocs hợp lệ để tránh watermark.  
- **Tôi có thể xử lý nhiều tài liệu một cách hiệu quả không?** Đặt mỗi `Annotator` trong khối try‑with‑resources và giải phóng sau mỗi tệp.

## Cách tạo tệp PDF Java sạch
Tạo một tệp PDF Java sạch có nghĩa là tạo ra một phiên bản của tài liệu **không có bất kỳ chú thích nào** đồng thời giữ nguyên nội dung gốc. Điều này hữu ích cho việc phân phối cuối cùng, lưu trữ, hoặc khi bạn cần chia sẻ bản sao “sạch” sau một vòng duyệt.

GroupDocs.Annotation làm cho việc này trở nên đơn giản: tải tệp đã chú thích, cấu hình `SaveOptions` để loại trừ tất cả các loại chú thích, và lưu kết quả. Các bước sẽ được minh họa sau trong phần **Removing Annotations**.

## Cách chú thích PDF trong Java bằng GroupDocs
GroupDocs.Annotation cung cấp một API phong phú cho **annotate PDF in Java**. Nó hỗ trợ nhiều loại chú thích, bao gồm tô sáng, dấu, và gạch chân. Trong tutorial này chúng ta tập trung vào các ghi chú gạch chân vì chúng thường được dùng để nhấn mạnh văn bản đồng thời cho phép bình luận dạng chuỗi.

## Yêu cầu trước và Cấu hình môi trường

### Những gì bạn cần trước khi bắt đầu

**Yêu cầu môi trường phát triển:**
- Java Development Kit (JDK) 8 hoặc cao hơn (khuyến nghị JDK 11+)
- Maven 3.6+ hoặc Gradle 6.0+ để quản lý phụ thuộc
- IDE như IntelliJ IDEA, Eclipse, hoặc VS Code với các extension Java
- Ít nhất 2 GB RAM khả dụng (xử lý tài liệu có thể tiêu tốn nhiều bộ nhớ)

**Yêu cầu kiến thức:**
Bạn nên quen thuộc với các khái niệm Java cơ bản — khởi tạo đối tượng, gọi phương thức, và phụ thuộc Maven. Kinh nghiệm trước với các thư viện bên thứ ba sẽ giúp bạn nhanh chóng tiếp cận.

**Tài liệu thử nghiệm:**
Chuẩn bị một vài tệp PDF mẫu. PDF dạng văn bản hoạt động tốt nhất; hình ảnh quét có thể cần OCR trước khi chú thích.

### Cấu hình Maven: Nhập GroupDocs vào dự án của bạn

Dưới đây là cách cấu hình đúng dự án Maven của bạn (điều này thường gây khó khăn cho nhiều nhà phát triển lần đầu):

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/annotation/java/</url>
   </repository>
</repositories>
<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-annotation</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

**Lưu ý:** Phiên bản 25.2 là bản phát hành ổn định mới nhất tại thời điểm viết. Hãy kiểm tra kho GroupDocs thường xuyên để có các phiên bản mới hơn có chứa bản sửa lỗi và cải thiện hiệu năng.

### Cấu hình giấy phép (Không bỏ qua phần này)

**Dành cho phát triển/kiểm thử:**
Tải bản dùng thử miễn phí từ trang web GroupDocs. Bản dùng thử bao gồm tất cả tính năng nhưng sẽ thêm watermark vào các tài liệu đã xử lý.

**Dành cho sản xuất:**
Mua giấy phép và áp dụng nó khi khởi động ứng dụng. Nếu không có giấy phép hợp lệ, bản dựng sản xuất sẽ bị giới hạn.

## Hướng dẫn triển khai: Thêm ghi chú gạch chân

### Hiểu quy trình làm việc của chú thích

Trước khi chúng ta đi vào mã, hãy cùng xem qua quy trình bốn bước xảy ra khi bạn **annotate PDF in Java**:

1. **Tải tài liệu** – `Annotator` đọc tệp vào bộ nhớ.  
2. **Tạo chú thích** – Xác định các thuộc tính như vị trí, kiểu dáng và bình luận.  
3. **Áp dụng chú thích** – Thư viện chèn chú thích vào cấu trúc PDF.  
4. **Lưu tài liệu** – Lưu tệp đã sửa đổi, tùy chọn giữ nguyên bản gốc.  

Quá trình này không phá hủy; tệp nguồn vẫn không bị thay đổi trừ khi bạn ghi đè lên nó.

### Bước 1: Khởi tạo Annotator và tải tài liệu của bạn

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Mẹo chuyên nghiệp:** Sử dụng đường dẫn tuyệt đối khi phát triển để tránh lỗi “file not found”. Trong môi trường sản xuất, hãy cân nhắc tải tài nguyên từ classpath hoặc bucket lưu trữ đám mây.

### Bước 2: Tạo bình luận và trả lời (Phần cộng tác)

```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;
import java.util.ArrayList;
import java.util.List;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

**Ứng dụng thực tế:** Các người duyệt có thể thảo luận một điều khoản cụ thể bằng cách thêm các trả lời dạng chuỗi, giữ cuộc trò chuyện gắn liền với chú thích cụ thể.

### Bước 3: Xác định tọa độ chú thích (Đặt vị trí chính xác)

```java
import com.groupdocs.annotation.models.Point;

Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = new ArrayList<>();
points.add(point1);
points.add(point2);
points.add(point3);
points.add(point4);
```

**Hệ thống tọa độ:**
- Các điểm 1 & 2 xác định cạnh trên của gạch chân.  
- Các điểm 3 & 4 xác định cạnh dưới.  
- Sự chênh lệch Y (730 so với 650) điều khiển độ dày.

### Bước 4: Tạo và cấu hình ghi chú gạch chân

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Yellow in ARGB format
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**Mẹo màu và độ trong suốt:**
- `FontColor` sử dụng ARGB; `65535` (0x00FFFF) cho màu vàng sáng.  
- Đối với màu đỏ, dùng `16711680` (0xFF0000); đối với màu xanh, `255` (0x0000FF).  
- Giá trị độ trong suốt từ 0.5 đến 0.8 cung cấp khả năng đọc tốt mà không che khuất văn bản.

### Bước 5: Lưu tài liệu đã chú thích của bạn

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Quản lý bộ nhớ:** Lệnh `dispose()` giải phóng tài nguyên gốc và ngăn ngừa rò rỉ bộ nhớ — rất quan trọng khi xử lý nhiều tệp trong một lô.

## Xóa chú thích: Tạo các phiên bản tài liệu sạch

Đôi khi bạn cần một phiên bản PDF **không có bất kỳ chú thích nào** — ví dụ, khi giao bản hợp đồng đã được phê duyệt cuối cùng. GroupDocs làm cho việc này trở nên dễ dàng.

### Hiểu các tùy chọn xóa chú thích

Bạn có thể:
- Xóa **tất cả** các chú thích (phổ biến nhất)  
- Xóa các loại cụ thể (ví dụ, chỉ các tô sáng)  
- Xóa chú thích theo tác giả hoặc trang  

### Các bước xóa chú thích từng bước

**Bước 1: Tải tài liệu đã được chú thích trước đó**

```java
Annotator annotator = new Annotator(outputPath);
```

**Bước 2: Cấu hình Save Options cho đầu ra sạch**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Bước 3: Lưu phiên bản sạch**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

Điều này tạo ra một tệp **clean PDF Java** không chứa bất kỳ đối tượng chú thích nào, hoàn hảo cho việc phân phối cuối cùng.

## Các vấn đề thường gặp và giải pháp

### Vấn đề 1: Lỗi “Document not found”

```java
File inputFile = new File("path/to/your/document.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Document not found: " + inputFile.getAbsolutePath());
}
if (!inputFile.canRead()) {
    throw new IllegalArgumentException("Cannot read document: " + inputFile.getAbsolutePath());
}

Annotator annotator = new Annotator(inputFile.getAbsolutePath());
```

### Vấn đề 2: Chú thích xuất hiện ở vị trí sai

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Vấn đề 3: Vấn đề bộ nhớ với tài liệu lớn

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### Vấn đề 4: Vấn đề giấy phép trong môi trường sản xuất

```java
try {
    License license = new License();
    license.setLicense("path/to/your/license.lic");
    System.out.println("License loaded successfully");
} catch (Exception e) {
    System.err.println("License loading failed: " + e.getMessage());
    // Handle the error appropriately
}
```

## Các thực tiễn tốt nhất về hiệu năng cho ứng dụng sản xuất

### Chiến lược quản lý bộ nhớ

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

```java
List<String> documentPaths = Arrays.asList("doc1.pdf", "doc2.pdf", "doc3.pdf");

for (String docPath : documentPaths) {
    try (Annotator annotator = new Annotator(docPath)) {
        // Process one document at a time
        annotator.add(createAnnotation());
        annotator.save(getOutputPath(docPath));
    }
    // Memory is freed after each iteration
}
```

### Lưu ý về đa luồng

GroupDocs.Annotation **không an toàn với đa luồng** theo mặc định. Nếu ứng dụng của bạn xử lý tài liệu đồng thời:
- **Không bao giờ chia sẻ** một thể hiện `Annotator` giữa các luồng.  
- **Đồng bộ** truy cập tệp hoặc sử dụng cơ chế khóa.  
- Xem xét **pool** các đối tượng `Annotator` nếu bạn cần thông lượng cao.

### Chiến lược cache

- Cache các mẫu chú thích thường dùng.  
- Tái sử dụng các collection `Point` cho các bộ tọa độ chung.  
- Giữ một **template PDF** trong bộ nhớ nếu bạn liên tục chú thích cùng một tài liệu gốc.

## Ứng dụng thực tế và các trường hợp sử dụng

### Hệ thống duyệt tài liệu

- **Duyệt pháp lý:** Gạch chân các điều khoản hợp đồng và thêm bình luận về rủi ro.  
- **Kiểm toán tuân thủ:** Tô sáng các phần có vấn đề trong báo cáo tài chính.  
- **Đánh giá đồng nghiệp học thuật:** Giảng viên gạch chân các đoạn cần làm rõ.

### Nền tảng giáo dục

- **Công cụ chú thích cho sinh viên:** Cho phép người học gạch chân các khái niệm chính trong e‑book.  
- **Phản hồi của giáo viên:** Cung cấp bình luận trực tiếp trên các bài tập đã nộp.

### Quy trình kiểm soát chất lượng

- **Duyệt tài liệu kỹ thuật:** Kỹ sư gạch chân các phần cần cập nhật.  
- **Quy trình vận hành chuẩn:** Nhân viên an toàn tô sáng các bước quan trọng.

### Hệ thống quản lý nội dung

- **Quy trình biên tập:** Biên tập viên gạch chân văn bản cần kiểm chứng thực tế.  
- **Kiểm soát phiên bản:** Theo dõi lịch sử chú thích qua các phiên bản tài liệu.

## Mẹo nâng cao cho triển khai chuyên nghiệp

### Kiểu chú thích tùy chỉnh

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Siêu dữ liệu chú thích để theo dõi

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### Tích hợp với hệ thống quản lý người dùng

```java
// Assume you have a method that returns the current authenticated user
String currentUser = getCurrentUser();
String userRole = getUserRole(currentUser);

// Apply role‑based styling
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedBy(currentUser);
underline.setFontColor(getRoleColor(userRole));
underline.setMessage(String.format("[%s] %s", userRole.toUpperCase(), commentText));
```

## Khắc phục sự cố trong môi trường sản xuất

### Giám sát hiệu năng

Theo dõi các chỉ số này trong môi trường sản xuất:
- **Sử dụng heap** – đảm bảo gọi `dispose()`.  
- **Thời gian xử lý mỗi tài liệu** – ghi lại thời gian trước/sau `annotator.save()`.  
- **Tỷ lệ lỗi** – bắt các ngoại lệ và phân loại chúng.

### Các bẫy thường gặp trong sản xuất

- **Khóa tệp** – đảm bảo các tệp đã tải lên được đóng trước khi chú thích.  
- **Chỉnh sửa đồng thời** – triển khai khóa lạc quan hoặc kiểm tra phiên bản.  
- **Tệp lớn (> 50 MB)** – tăng thời gian chờ JVM và cân nhắc API streaming.

### Thực tiễn tốt nhất về xử lý lỗi

```java
try (Annotator annotator = new Annotator(documentPath)) {
    UnderlineAnnotation annotation = createAnnotation();
    annotator.add(annotation);
    annotator.save(outputPath);
    
} catch (Exception e) {
    logger.error("Annotation failed for document: " + documentPath, e);
    // Implement appropriate error recovery
    throw new DocumentProcessingException("Failed to annotate document", e);
}
```

## Kết luận

Bây giờ bạn đã có mọi thứ cần thiết để **tạo tệp PDF Java sạch** và **chú thích PDF trong Java** với các ghi chú gạch chân bằng GroupDocs.Annotation. Hãy nhớ:
- Quản lý tài nguyên bằng try‑with‑resources hoặc gọi `dispose()` một cách rõ ràng.  
- Xác thực tọa độ sớm để tránh gạch chân sai vị trí.  
- Triển khai xử lý lỗi mạnh mẽ để đảm bảo ổn định trong môi trường sản xuất.  
- Tận dụng kiểu dáng dựa trên vai trò và siêu dữ liệu để phù hợp với quy trình làm việc của bạn.

Bước tiếp theo? Hãy thử thêm các loại chú thích khác — tô sáng, dấu, hoặc thay thế văn bản — để xây dựng một giải pháp duyệt tài liệu đầy đủ tính năng.

## Câu hỏi thường gặp

**H: Làm sao để tôi chú thích nhiều vùng văn bản trong một thao tác?**  
**Đ:** Tạo nhiều đối tượng `UnderlineAnnotation` với các tọa độ khác nhau và thêm chúng tuần tự bằng `annotator.add()`.

**H: Tôi có thể chú thích hình ảnh trong tài liệu PDF không?**  
**Đ:** Có. Sử dụng cùng hệ thống tọa độ, đảm bảo các điểm nằm trong giới hạn của hình ảnh.

**H: GroupDocs.Annotation hỗ trợ những định dạng tệp nào ngoài PDF?**  
**Đ:** Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), và các định dạng hình ảnh như JPEG, PNG, TIFF.

**H: Làm sao để xử lý tài liệu rất lớn mà không hết bộ nhớ?**  
**Đ:** Xử lý tài liệu từng cái một, tăng heap JVM (`-Xmx`), và luôn giải phóng các thể hiện `Annotator` kịp thời.

**H: Có thể trích xuất các chú thích hiện có từ tài liệu không?**  
**Đ:** Có. Sử dụng `annotator.get()` để lấy tất cả các chú thích, sau đó lọc theo loại, tác giả hoặc trang tùy nhu cầu.

---

**Last Updated:** 2025-12-21  
**Tested With:** GroupDocs.Annotation 25.2  
**Author:** GroupDocs