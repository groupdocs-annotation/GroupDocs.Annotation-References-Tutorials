---
categories:
- Java Development
date: '2026-03-24'
description: Tìm hiểu cách tạo các tệp PDF Java sạch sẽ, quản lý bộ nhớ PDF Java và
  chú thích PDF trong Java bằng GroupDocs.Annotation, kèm theo các ví dụ mã đầy đủ
  và mẹo khắc phục sự cố.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2026-03-24'
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

Nếu bạn cần **create clean PDF Java** files và thêm các ghi chú cộng tác, bạn đã đến đúng nơi. Gặp khó khăn trong việc quản lý tài liệu và cộng tác trong các ứng dụng Java của mình? Bạn không đơn độc. Nhiều nhà phát triển gặp thách thức trong việc triển khai các tính năng ghi chú tài liệu mạnh mẽ, hoạt động đáng tin cậy trên các định dạng tệp khác nhau.

Trong hướng dẫn này, bạn sẽ **create clean PDF Java** files và học cách **annotate PDF in Java** bằng GroupDocs.Annotation. Khi kết thúc tutorial, bạn sẽ biết chính xác cách thêm ghi chú gạch chân kèm bình luận, xóa các ghi chú hiện có, và tích hợp các tính năng này một cách liền mạch vào dự án của mình.

**Những gì bạn sẽ thành thạo trong hướng dẫn này:**
- Thiết lập GroupDocs.Annotation trong dự án Java của bạn (theo cách đúng)  
- Thêm ghi chú gạch chân với bình luận tùy chỉnh và kiểu dáng  
- Xóa tất cả các ghi chú để tạo các phiên bản tài liệu sạch  
- Khắc phục các vấn đề thường gặp mà nhà phát triển gặp phải  
- Tối ưu hiệu năng cho các ứng dụng sản xuất  

Dù bạn đang xây dựng hệ thống duyệt tài liệu, nền tảng giáo dục, hay công cụ chỉnh sửa cộng tác, tutorial này sẽ cung cấp cho bạn các ví dụ mã thực tế, đã được kiểm nghiệm.

## Trả lời nhanh
- **Làm thế nào để thêm ghi chú gạch chân?** Sử dụng `UnderlineAnnotation` và `annotator.add()` rồi lưu tài liệu.  
- **Làm sao tạo một clean PDF Java file?** Tải tệp đã được ghi chú, đặt `AnnotationType.NONE` trong `SaveOptions`, và lưu một bản sao mới.  
- **Cần những thư viện nào?** GroupDocs.Annotation v25.2 (hoặc mới hơn) và kho Maven của nó.  
- **Có cần giấy phép cho môi trường sản xuất không?** Có—áp dụng giấy phép GroupDocs hợp lệ để tránh watermark.  
- **Có thể xử lý nhiều tài liệu một cách hiệu quả không?** Đặt mỗi `Annotator` trong khối try‑with‑resources và giải phóng sau mỗi tệp.

## Cách tạo clean PDF Java files
Tạo một clean PDF Java file có nghĩa là tạo ra một phiên bản tài liệu **không có bất kỳ ghi chú nào** đồng thời giữ nguyên nội dung gốc. Điều này hữu ích cho việc phân phối cuối cùng, lưu trữ, hoặc khi bạn cần chia sẻ bản “sạch” sau một vòng duyệt.

GroupDocs.Annotation làm cho việc này trở nên đơn giản: tải tệp đã được ghi chú, cấu hình `SaveOptions` để loại bỏ mọi loại ghi chú, và lưu kết quả. Các bước được minh họa sau trong phần **Removing Annotations**.

## Tại sao tạo clean PDF Java files?
Một phiên bản sạch loại bỏ các dấu hiệu của người duyệt, bình luận và đánh dấu, mang lại cho bạn một tài liệu được chỉnh sửa sẵn sàng cho khách hàng, cơ quan quản lý, hoặc công bố công cộng. Nó cũng giảm kích thước tệp và ngăn ngừa việc vô tình tiết lộ các ghi chú nội bộ—rất quan trọng trong quy trình pháp lý và tuân thủ.

## Cách annotate PDF in Java bằng GroupDocs
GroupDocs.Annotation cung cấp một API phong phú cho **annotate PDF in Java**. Nó hỗ trợ nhiều loại ghi chú, bao gồm highlight, stamp và underline. Trong tutorial này chúng ta tập trung vào ghi chú gạch chân vì chúng thường được dùng để nhấn mạnh văn bản đồng thời cho phép bình luận dạng chuỗi.

## Các yêu cầu trước và thiết lập môi trường

### Những gì bạn cần trước khi bắt đầu

**Yêu cầu môi trường phát triển:**
- Java Development Kit (JDK) 8 hoặc cao hơn (khuyến nghị JDK 11+)  
- Maven 3.6+ hoặc Gradle 6.0+ để quản lý phụ thuộc  
- IDE như IntelliJ IDEA, Eclipse, hoặc VS Code với các extension Java  
- Ít nhất 2 GB RAM khả dụng (xử lý tài liệu có thể tiêu tốn nhiều bộ nhớ)

**Kiến thức tiên quyết:**
Bạn nên quen thuộc với các khái niệm Java cơ bản—khởi tạo đối tượng, gọi phương thức, và phụ thuộc Maven. Kinh nghiệm với các thư viện bên thứ ba sẽ giúp bạn nhanh chóng áp dụng.

**Tài liệu thử nghiệm:**
Chuẩn bị một vài file PDF mẫu. PDF dạng văn bản hoạt động tốt nhất; các ảnh quét có thể cần OCR trước khi ghi chú.

### Cấu hình Maven: Đưa GroupDocs vào dự án của bạn

Đây là cách cấu hình dự án Maven một cách chính xác (nhiều nhà phát triển gặp khó khăn ở bước này lần đầu):

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

**Lưu ý:** Phiên bản 25.2 là bản ổn định mới nhất tại thời điểm viết. Hãy kiểm tra kho GroupDocs thường xuyên để cập nhật các phiên bản mới có bản sửa lỗi và cải thiện hiệu năng.

### Cấu hình giấy phép (Đừng bỏ qua phần này)

**Cho phát triển/kiểm thử:**  
Tải bản dùng thử miễn phí từ trang web GroupDocs. Bản dùng thử bao gồm mọi tính năng nhưng sẽ thêm watermark vào tài liệu đã xử lý.

**Cho sản xuất:**  
Mua giấy phép và áp dụng nó khi khởi động ứng dụng. Nếu không có giấy phép hợp lệ, các bản build sản xuất sẽ bị giới hạn.

## Hướng dẫn triển khai: Thêm ghi chú gạch chân

### Hiểu quy trình làm việc của ghi chú

Trước khi đi vào mã, hãy cùng xem qua quy trình bốn bước xảy ra khi bạn **annotate PDF in Java**:

1. **Document Loading** – `Annotator` đọc file vào bộ nhớ.  
2. **Annotation Creation** – Định nghĩa các thuộc tính như vị trí, kiểu dáng và bình luận.  
3. **Annotation Application** – Thư viện chèn ghi chú vào cấu trúc PDF.  
4. **Document Saving** – Lưu file đã chỉnh sửa, tùy chọn giữ nguyên bản gốc.

Quá trình này không phá hủy; file nguồn vẫn không bị thay đổi trừ khi bạn ghi đè lên nó.

### Bước 1: Khởi tạo Annotator và tải tài liệu của bạn

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Mẹo chuyên nghiệp:** Sử dụng đường dẫn tuyệt đối khi phát triển để tránh lỗi “file not found”. Trong môi trường sản xuất, cân nhắc tải tài nguyên từ classpath hoặc bucket lưu trữ đám mây.

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

**Ứng dụng thực tế:** Người duyệt có thể thảo luận một điều khoản cụ thể bằng cách thêm các trả lời chuỗi, giữ cho cuộc trò chuyện gắn liền với ghi chú tương ứng.

### Bước 3: Xác định tọa độ ghi chú (Đặt vị trí chính xác)

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
- Điểm 1 & 2 xác định cạnh trên của gạch chân.  
- Điểm 3 & 4 xác định cạnh dưới.  
- Khoảng cách Y (730 vs 650) điều chỉnh độ dày.

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

**Mẹo về màu và độ trong suốt:**  
- `FontColor` sử dụng ARGB; `65535` (0x00FFFF) cho màu vàng sáng.  
- Đối với màu đỏ, dùng `16711680` (0xFF0000); màu xanh dương, `255` (0x0000FF).  
- Giá trị opacity từ 0.5 đến 0.8 cung cấp độ đọc tốt mà không che khuất văn bản.

### Bước 5: Lưu tài liệu đã được ghi chú

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Quản lý bộ nhớ:** Lệnh `dispose()` giải phóng tài nguyên gốc và ngăn rò rỉ bộ nhớ—rất quan trọng khi xử lý nhiều file trong một batch.

## Xóa ghi chú: Tạo phiên bản tài liệu sạch

Đôi khi bạn cần một phiên bản PDF **không có bất kỳ ghi chú nào**—ví dụ, khi giao hợp đồng đã được phê duyệt cuối cùng. GroupDocs thực hiện việc này một cách dễ dàng.

### Hiểu các tùy chọn xóa ghi chú

Bạn có thể:
- Xóa **tất cả** ghi chú (phổ biến nhất)  
- Xóa các loại cụ thể (ví dụ, chỉ highlight)  
- Xóa ghi chú theo tác giả hoặc trang  

### Quy trình xóa ghi chú từng bước

**Bước 1: Tải tài liệu đã được ghi chú trước đó**

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

Điều này tạo ra một **clean PDF Java** file không chứa bất kỳ đối tượng ghi chú nào, hoàn hảo cho việc phân phối cuối cùng.

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

### Vấn đề 2: Ghi chú xuất hiện ở vị trí sai

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

## Các thực hành tốt nhất về hiệu năng cho ứng dụng sản xuất

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

### Xem xét đa luồng

GroupDocs.Annotation **không thread‑safe** theo mặc định. Nếu ứng dụng của bạn xử lý tài liệu đồng thời:

- **Không bao giờ chia sẻ** một instance `Annotator` giữa các luồng.  
- **Đồng bộ** việc truy cập file hoặc sử dụng cơ chế khóa.  
- Xem xét **pool** các đối tượng `Annotator` nếu cần throughput cao.

### Chiến lược cache

- Lưu cache các mẫu ghi chú thường dùng.  
- Tái sử dụng các collection `Point` cho các tập hợp tọa độ chung.  
- Giữ một **template PDF** trong bộ nhớ nếu bạn thường xuyên ghi chú vào cùng một tài liệu gốc.

## Mẹo quản lý bộ nhớ Java PDF
Sử dụng bộ nhớ hiệu quả là điều cần thiết khi xử lý PDF lớn hoặc xử lý nhiều file trong một batch. Dưới đây là một vài khuyến nghị thực tế:

- **Sử dụng try‑with‑resources** cho mọi `Annotator` để đảm bảo giải phóng.  
- **Tăng heap JVM** (`-Xmx`) chỉ khi cần; theo dõi mức sử dụng bằng công cụ profiling.  
- **Xử lý tài liệu tuần tự** khi có thể, giải phóng bộ nhớ sau mỗi file.  
- **Tránh tải cùng một PDF nhiều lần**; tái sử dụng cùng một stream nếu cần đọc lại.

Áp dụng các thực hành này giúp ứng dụng của bạn phản hồi nhanh và ngăn ngừa lỗi out‑of‑memory trong các khối lượng công việc ghi chú nặng.

## Ứng dụng thực tế và các trường hợp sử dụng

### Hệ thống duyệt tài liệu

- **Duyệt pháp lý:** Gạch chân các điều khoản hợp đồng và thêm bình luận về rủi ro.  
- **Kiểm toán tuân thủ:** Đánh dấu các phần có vấn đề trong báo cáo tài chính.  
- **Duyệt học thuật:** Giảng viên gạch chân các đoạn cần làm rõ.

### Nền tảng giáo dục

- **Công cụ ghi chú cho sinh viên:** Cho phép người học gạch chân các khái niệm quan trọng trong e‑book.  
- **Phản hồi của giáo viên:** Cung cấp bình luận nội tuyến trực tiếp trên bài tập đã nộp.

### Quy trình đảm bảo chất lượng

- **Duyệt tài liệu kỹ thuật:** Kỹ sư gạch chân các phần cần cập nhật.  
- **Quy trình vận hành tiêu chuẩn:** Nhân viên an toàn đánh dấu các bước quan trọng.

### Hệ thống quản lý nội dung

- **Quy trình biên tập:** Biên tập viên gạch chân văn bản cần kiểm chứng thực tế.  
- **Kiểm soát phiên bản:** Theo dõi lịch sử ghi chú qua các phiên bản tài liệu.

## Mẹo nâng cao cho triển khai chuyên nghiệp

### Kiểu ghi chú tùy chỉnh

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Siêu dữ liệu ghi chú để theo dõi

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

Theo dõi các chỉ số sau trong môi trường sản xuất:
- **Heap usage** – đảm bảo gọi `dispose()`.  
- **Thời gian xử lý mỗi tài liệu** – ghi log thời gian trước và sau `annotator.save()`.  
- **Tỷ lệ lỗi** – bắt các ngoại lệ và phân loại chúng.

### Các bẫy thường gặp trong sản xuất

- **Khóa file** – đảm bảo các file đã tải lên được đóng trước khi ghi chú.  
- **Chỉnh sửa đồng thời** – triển khai optimistic locking hoặc kiểm tra phiên bản.  
- **File lớn (> 50 MB)** – tăng timeout JVM và cân nhắc sử dụng API streaming.

### Thực hành tốt nhất về xử lý lỗi

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

Bạn đã có mọi thứ cần thiết để **create clean PDF Java** files và **annotate PDF in Java** với ghi chú gạch chân bằng GroupDocs.Annotation. Hãy nhớ:

- Quản lý tài nguyên bằng try‑with‑resources hoặc gọi `dispose()` một cách rõ ràng.  
- Xác thực tọa độ sớm để tránh gạch chân sai vị trí.  
- Thực hiện xử lý lỗi mạnh mẽ để đảm bảo độ ổn định trong môi trường sản xuất.  
- Tận dụng kiểu dáng dựa trên vai trò và siêu dữ liệu để phù hợp với quy trình làm việc của bạn.

Bước tiếp theo? Hãy thử thêm các loại ghi chú khác—highlight, stamp, hoặc thay thế văn bản—để xây dựng giải pháp duyệt tài liệu toàn diện.

## Câu hỏi thường gặp

**Q: Làm sao để ghi chú nhiều vùng văn bản trong một thao tác?**  
A: Tạo nhiều đối tượng `UnderlineAnnotation` với các tọa độ khác nhau và thêm chúng tuần tự bằng `annotator.add()`.

**Q: Có thể ghi chú hình ảnh trong tài liệu PDF không?**  
A: Có. Sử dụng cùng hệ thống tọa độ, đảm bảo các điểm nằm trong giới hạn của hình ảnh.

**Q: GroupDocs.Annotation hỗ trợ những định dạng tệp nào ngoài PDF?**  
A: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), và các định dạng hình ảnh như JPEG, PNG, TIFF.

**Q: Làm sao xử lý tài liệu rất lớn mà không hết bộ nhớ?**  
A: Xử lý tài liệu từng cái một, tăng heap JVM (`-Xmx`), và luôn giải phóng các instance `Annotator` kịp thời.

**Q: Có thể trích xuất các ghi chú đã tồn tại từ tài liệu không?**  
A: Có. Sử dụng `annotator.get()` để lấy tất cả ghi chú, sau đó lọc theo loại, tác giả hoặc trang theo nhu cầu.

---

**Last Updated:** 2026-03-24  
**Tested With:** GroupDocs.Annotation 25.2  
**Author:** GroupDocs