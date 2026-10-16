---
date: '2026-10-16'
description: Tìm hiểu cách lưu PDF mà không có chú thích trong Java, nắm vững quản
  lý bộ nhớ PDF trong Java, và thêm chú thích gạch chân bằng GroupDocs.Annotation.
  Hướng dẫn từng bước.
keywords:
- save pdf without annotations
- java pdf memory management
- java document review system
- groupdocs annotation tutorial
- underline annotation java
lastmod: '2026-10-16'
linktitle: Chú thích tài liệu Java với GroupDocs
og_description: Tìm hiểu cách lưu PDF mà không có chú thích trong Java, nắm vững quản
  lý bộ nhớ PDF trong Java, và thêm chú thích gạch chân bằng GroupDocs.Annotation.
  Hướng dẫn từng bước.
og_image_alt: 'Developer guide: Save PDF without annotations in Java using GroupDocs.Annotation'
og_title: Cách lưu PDF mà không có chú thích trong Java bằng GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  headline: How to save PDF without annotations in Java using GroupDocs
  type: TechArticle
- description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  name: How to save PDF without annotations in Java using GroupDocs
  steps:
  - name: initialize the annotator and load your document
    text: '`Annotator` is the main entry point in GroupDocs.Annotation for loading
      and modifying PDF documents. It abstracts file‑system handling, stream management,
      and native resource allocation. **Pro tip:** Use absolute paths while developing
      to avoid “file not found” errors. In production, consider loadin'
  - name: creating comments and replies (the collaborative part)
    text: '`Comment` objects represent threaded discussion attached to an annotation.
      Each comment can have an author, a timestamp, and optional replies, enabling
      a full conversation around a specific markup. **Real‑world use:** Reviewers
      can discuss a specific clause by adding threaded replies, keeping the co'
  - name: defining annotation coordinates (getting the position right)
    text: '`Point` defines a single coordinate in PDF space (measured in points, where
      72 points = 1 inch). Four points are required for an underline: two for the
      start line and two for the end line. **Coordinate system:** - Points 1 & 2 define
      the top edge of the underline. - Points 3 & 4 define the bottom ed'
  - name: creating and configuring the underline annotation
    text: '`UnderlineAnnotation` is the concrete class that represents an underline
      markup. It inherits from the base `Annotation` class and adds properties specific
      to underlines, such as line thickness and style. **Color & opacity tips:** -
      `FontColor` uses ARGB; `65535` (0x00FFFF) yields bright yellow. - Fo'
  - name: saving your annotated document
    text: '`SaveOptions` lets you control the output format, whether to embed annotations,
      and how to handle metadata. Setting `AnnotationType.NONE` instructs the library
      to strip all annotation objects, which is the key to **save PDF without annotations**.
      **Memory management:** The `dispose()` call releases '
  type: HowTo
- questions:
  - answer: Create several `UnderlineAnnotation` objects with different coordinates
      and add them sequentially using `annotator.add()`.
    question: How do I annotate multiple areas of text in a single operation?
  - answer: Yes. Use the same coordinate system, ensuring the points lie inside the
      image bounds.
    question: Can I annotate images within PDF documents?
  - answer: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), and image formats
      such as JPEG, PNG, TIFF.
    question: What file formats besides PDF does GroupDocs.Annotation support?
  - answer: Process documents one at a time, increase the JVM heap (`-Xmx`), and always
      dispose of `Annotator` instances promptly.
    question: How do I handle very large documents without running out of memory?
  - answer: Yes. Use `annotator.get()` to retrieve all annotations, then filter by
      type, author, or page as needed.
    question: Is it possible to extract existing annotations from a document?
  type: FAQPage
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
- java pdf memory management
title: Cách lưu PDF mà không có chú thích trong Java bằng GroupDocs
type: docs
url: /vi/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Cách lưu PDF mà không có chú thích trong Java bằng GroupDocs

Nếu bạn cần **save PDF without annotations** trong khi vẫn có thể thêm ghi chú gạch chân hợp tác, bạn đã đến đúng nơi. Nhiều nhà phát triển Java gặp khó khăn trong việc giữ một phiên bản sạch của tài liệu để phân phối cuối cùng, đặc biệt khi cùng một tệp được sử dụng cho các vòng đánh giá lặp lại. Trong hướng dẫn này, bạn sẽ học cách tạo một PDF sạch, quản lý bộ nhớ hiệu quả, và áp dụng các chú thích gạch chân kèm bình luận bằng GroupDocs.Annotation. Khi kết thúc, bạn sẽ hiểu toàn bộ quy trình—từ việc tải PDF đến tạo bản sao cuối cùng không có watermark—cùng các mẹo thực tiễn để xây dựng một **java document review system** mạnh mẽ.

## Câu trả lời nhanh
- **Làm thế nào để thêm chú thích gạch chân?** Use `UnderlineAnnotation` with `annotator.add()` then save the document.  
- **Làm thế nào để lưu PDF mà không có chú thích?** Load the annotated file, set `AnnotationType.NONE` in `SaveOptions`, and save a new copy.  
- **Cần những thư viện nào?** GroupDocs.Annotation v25.2 (hoặc mới hơn) và kho Maven của nó.  
- **Có cần giấy phép cho môi trường production không?** Có—áp dụng giấy phép GroupDocs hợp lệ để tránh watermark.  
- **Tôi có thể xử lý nhiều tài liệu một cách hiệu quả không?** Wrap each `Annotator` in a try‑with‑resources block and dispose after each file.

## Làm thế nào để lưu PDF mà không có chú thích trong Java?

Load the source PDF with an `Annotator`, configure `SaveOptions` to exclude all annotation types, and call `save()` to write a clean copy. This operation does not modify the original file, so you retain both the annotated version for reviewers and a pristine version for distribution. The process uses streaming under the hood, meaning the entire document never fully resides in memory—crucial for large PDFs.

## “save PDF without annotations” là gì?

`save pdf without annotations` refers to exporting a PDF document while stripping out every annotation object (highlights, comments, stamps, underlines, etc.). The resulting file contains only the original content and layout, making it suitable for legal filing, public release, or archival storage.

## Tại sao tạo các tệp PDF sạch trong hệ thống đánh giá tài liệu Java?

A clean version eliminates reviewer marks, comments, and highlights, giving you a polished document ready for clients, regulators, or public release. It also reduces file size by up to 30 % on average and prevents accidental disclosure of internal notes—critical for legal and compliance workflows. GroupDocs.Annotation can remove all annotation objects in a single pass, supporting PDFs up to 500 MB without loading the whole file into memory.

## Các yêu cầu trước và cài đặt môi trường

### Yêu cầu trước khi bắt đầu

**Yêu cầu môi trường phát triển**  
- Java Development Kit (JDK) 8 hoặc cao hơn (khuyến nghị JDK 11+)  
- Maven 3.6+ hoặc Gradle 6.0+ để quản lý phụ thuộc  
- IDE như IntelliJ IDEA, Eclipse, hoặc VS Code với các extension Java  
- Ít nhất 2 GB RAM khả dụng (xử lý tài liệu có thể tốn nhiều bộ nhớ)

**Kiến thức nền tảng**  
Bạn nên quen thuộc với các khái niệm cơ bản của Java—khởi tạo đối tượng, gọi phương thức, và phụ thuộc Maven. Kinh nghiệm với các thư viện bên thứ ba sẽ giúp bạn nhanh chóng áp dụng.

**Tài liệu thử nghiệm**  
Chuẩn bị một vài PDF mẫu. PDF dạng văn bản hoạt động tốt nhất; ảnh quét có thể cần OCR trước khi chú thích.

### Cài đặt Maven: đưa GroupDocs vào dự án của bạn

Thêm phụ thuộc sau vào `pom.xml`. Bước này thường gây khó cho nhiều nhà phát triển vì group ID và artifact ID phải khớp chính xác.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```

**Lưu ý:** Phiên bản 25.2 là bản ổn định mới nhất tại thời điểm viết. Hãy kiểm tra kho GroupDocs thường xuyên để cập nhật các phiên bản mới có sửa lỗi và cải thiện hiệu năng.

### Cài đặt giấy phép (đừng bỏ qua)

**Dành cho phát triển/kiểm thử** – Tải bản dùng thử miễn phí từ trang web GroupDocs. Bản dùng thử bao gồm mọi tính năng nhưng sẽ thêm watermark vào tài liệu đã xử lý.

**Dành cho production** – Mua giấy phép và áp dụng nó khi khởi động ứng dụng. Nếu không có giấy phép hợp lệ, các bản build production sẽ bị giới hạn và có watermark.

## Hướng dẫn triển khai: thêm chú thích gạch chân

### Hiểu quy trình chú thích

Trước khi đi vào mã, hãy xem qua quy trình bốn bước xảy ra khi bạn **annotate PDF in Java**:

1. **Document loading** – `Annotator` đọc tệp vào bộ nhớ.  
2. **Annotation creation** – Xác định các thuộc tính như vị trí, kiểu dáng, và bình luận.  
3. **Annotation application** – Thư viện chèn chú thích vào cấu trúc PDF.  
4. **Document saving** – Lưu tệp đã sửa đổi, tùy chọn giữ nguyên bản gốc.

Quy trình này không phá hủy; tệp nguồn vẫn không bị thay đổi trừ khi bạn ghi đè lên nó.

### Bước 1: khởi tạo annotator và tải tài liệu

`Annotator` là điểm vào chính trong GroupDocs.Annotation để tải và chỉnh sửa tài liệu PDF. Nó trừu tượng hoá việc xử lý hệ thống tệp, quản lý stream, và cấp phát tài nguyên gốc.

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

**Mẹo:** Sử dụng đường dẫn tuyệt đối khi phát triển để tránh lỗi “file not found”. Trong production, cân nhắc tải tài nguyên từ classpath hoặc bucket lưu trữ đám mây.

### Bước 2: tạo bình luận và trả lời (phần hợp tác)

Đối tượng `Comment` đại diện cho cuộc thảo luận dạng chuỗi gắn vào một chú thích. Mỗi bình luận có thể có tác giả, thời gian, và các trả lời tùy chọn, cho phép một cuộc trò chuyện đầy đủ quanh một đánh dấu cụ thể.

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Ứng dụng thực tế:** Người đánh giá có thể thảo luận một điều khoản cụ thể bằng cách thêm các trả lời chuỗi, giữ cuộc trò chuyện gắn liền với chú thích đó.

### Bước 3: xác định tọa độ chú thích (đặt vị trí đúng)

`Point` định nghĩa một tọa độ duy nhất trong không gian PDF (được đo bằng points, 72 points = 1 inch). Bốn điểm cần cho một gạch chân: hai điểm cho đường bắt đầu và hai điểm cho đường kết thúc.

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

**Hệ thống tọa độ:**  
- Điểm 1 và 2 xác định cạnh trên của gạch chân.  
- Điểm 3 và 4 xác định cạnh dưới.  
- Chênh lệch Y (730 vs 650) điều chỉnh độ dày.

### Bước 4: tạo và cấu hình chú thích gạch chân

`UnderlineAnnotation` là lớp cụ thể đại diện cho đánh dấu gạch chân. Nó kế thừa từ lớp cơ sở `Annotation` và thêm các thuộc tính đặc thù cho gạch chân, như độ dày và kiểu đường.

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

**Mẹo về màu và độ trong suốt:**  
- `FontColor` dùng ARGB; `65535` (0x00FFFF) cho màu vàng sáng.  
- Đối với màu đỏ, dùng `16711680` (0xFF0000); màu xanh, `255` (0x0000FF).  
- Giá trị opacity từ 0.5 đến 0.8 cung cấp độ đọc tốt mà không che khuất văn bản.

### Bước 5: lưu tài liệu đã chú thích

`SaveOptions` cho phép bạn kiểm soát định dạng đầu ra, có nhúng chú thích hay không, và cách xử lý metadata. Đặt `AnnotationType.NONE` sẽ yêu cầu thư viện loại bỏ mọi đối tượng chú thích, đây là chìa khóa để **save PDF without annotations**.

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

**Quản lý bộ nhớ:** Lệnh `dispose()` giải phóng tài nguyên gốc và ngăn rò rỉ bộ nhớ—rất quan trọng khi xử lý nhiều tệp trong một batch.

## Xóa chú thích: tạo phiên bản tài liệu sạch

Đôi khi bạn cần một phiên bản PDF **không có bất kỳ chú thích nào**—ví dụ khi giao hợp đồng đã được phê duyệt cuối cùng. GroupDocs làm việc này rất dễ dàng.

### Hiểu các tùy chọn xóa chú thích

Bạn có thể:  
- Xóa **tất cả** chú thích (phổ biến nhất)  
- Xóa các loại cụ thể (ví dụ chỉ xóa highlight)  
- Xóa chú thích theo tác giả hoặc trang  

### Quy trình xóa chú thích từng bước

**Bước 1: tải tài liệu đã được chú thích trước đó**

`Annotator` lại đóng vai trò tải tệp; nó sẽ đọc tệp vẫn còn chứa các đối tượng chú thích.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Bước 2: cấu hình tùy chọn lưu cho đầu ra sạch**

`SaveOptions` cung cấp API fluent để chỉ định không ghi bất kỳ loại chú thích nào vào tệp đầu ra.

```java
Annotator annotator = new Annotator(outputPath);
```

**Bước 3: lưu phiên bản sạch**

Gọi `save()` với các tùy chọn đã cấu hình sẽ ghi ra một PDF chỉ chứa nội dung gốc.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

Kết quả là một tệp **PDF sạch** không có đối tượng chú thích, hoàn hảo cho việc phân phối cuối cùng.

## Các vấn đề thường gặp và giải pháp

### Vấn đề 1: lỗi “Document not found”

Đảm bảo đường dẫn tệp đúng và ứng dụng có quyền đọc. Sử dụng `Path.of()` với đường dẫn tuyệt đối sẽ loại bỏ hầu hết các trường hợp mơ hồ.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

### Vấn đề 2: Chú thích xuất hiện ở vị trí sai

Gốc tọa độ PDF nằm ở góc dưới‑trái. Kiểm tra giá trị Y tăng lên phía trên và cân nhắc độ quay của trang.

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

### Vấn đề 3: Vấn đề bộ nhớ với tài liệu lớn

GroupDocs.Annotation stream nội dung và không tải toàn bộ tệp vào heap. Tuy nhiên, bạn vẫn cần gọi `dispose()` và cân nhắc tăng heap JVM (`-Xmx`) cho các tệp lớn hơn 200 MB.

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Vấn đề 4: Vấn đề giấy phép trong production

Nếu file giấy phép thiếu hoặc đường dẫn sai, thư viện sẽ chuyển sang chế độ dùng thử, thêm watermark vào mỗi trang. Đặt file giấy phép ở vị trí nằm trong classpath và tải nó sớm trong vòng đời ứng dụng.

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

## Các thực tiễn tốt nhất về hiệu năng cho ứng dụng production

### Chiến lược quản lý bộ nhớ

GroupDocs.Annotation xử lý PDF theo kiểu streaming, cho phép làm việc với các tệp lên tới 500 MB mà không cần tải toàn bộ vào bộ nhớ. Tuy nhiên, vẫn nên tuân thủ các hướng dẫn sau:

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

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

### Lưu ý về đa luồng

GroupDocs.Annotation **không thread‑safe** theo mặc định. Nếu ứng dụng của bạn xử lý tài liệu đồng thời:

- **Không bao giờ chia sẻ** một thể hiện `Annotator` giữa các luồng.  
- **Đồng bộ** việc truy cập tệp hoặc sử dụng cơ chế lock.  
- Xem xét tạo **pool** các đối tượng `Annotator` nếu cần thông lượng cao.

### Chiến lược caching

- Lưu trữ cache các mẫu chú thích thường dùng.  
- Tái sử dụng các collection `Point` cho các bộ tọa độ chung.  
- Giữ một **template PDF** trong bộ nhớ nếu bạn thường xuyên chú thích cùng một tài liệu gốc.

## Các thực tiễn tốt nhất về quản lý bộ nhớ PDF trong Java

Việc sử dụng bộ nhớ hiệu quả là yếu tố then chốt khi xử lý PDF lớn hoặc xử lý nhiều tệp trong một batch. Dưới đây là một số khuyến nghị thực tế:

- **Sử dụng try‑with‑resources** cho mọi `Annotator` để đảm bảo giải phóng.  
- **Tăng heap JVM** (`-Xmx`) chỉ khi cần; giám sát việc sử dụng bằng công cụ profiling.  
- **Xử lý tài liệu tuần tự** khi có thể, giải phóng bộ nhớ sau mỗi tệp.  
- **Tránh tải cùng một PDF nhiều lần**; tái sử dụng stream nếu cần đọc lại.

Áp dụng những thực tiễn này giúp ứng dụng của bạn luôn phản hồi nhanh và tránh crash do hết bộ nhớ trong các khối lượng công việc chú thích nặng.

## Ứng dụng thực tế và các trường hợp sử dụng

### Hệ thống đánh giá tài liệu

- **Đánh giá pháp lý:** Gạch chân các điều khoản hợp đồng và thêm bình luận về rủi ro.  
- **Kiểm toán tuân thủ:** Highlight các phần vấn đề trong báo cáo tài chính.  
- **Đánh giá học thuật:** Giảng viên gạch chân các đoạn cần làm rõ.

### Nền tảng giáo dục

- **Công cụ chú thích cho sinh viên:** Cho phép học viên gạch chân các khái niệm quan trọng trong e‑book.  
- **Phản hồi của giáo viên:** Cung cấp bình luận nội tuyến trực tiếp trên bài tập đã nộp.

### Quy trình kiểm soát chất lượng

- **Đánh giá tài liệu kỹ thuật:** Kỹ sư gạch chân các phần cần cập nhật.  
- **Quy trình SOP:** Nhân viên an toàn đánh dấu các bước quan trọng.

### Hệ thống quản lý nội dung

- **Quy trình biên tập:** Biên tập viên gạch chân văn bản cần kiểm chứng thực tế.  
- **Kiểm soát phiên bản:** Theo dõi lịch sử chú thích qua các phiên bản tài liệu.

## Mẹo nâng cao cho triển khai chuyên nghiệp

### Kiểu chú thích tùy chỉnh

Bạn có thể mở rộng giao diện visual của gạch chân bằng cách đặt các mẫu dash tùy chỉnh, đầu mút line, và mức độ trong suốt. Điều này hữu ích khi cần phân biệt vai trò người đánh giá (ví dụ: pháp lý vs. kỹ thuật).

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

### Metadata chú thích để theo dõi

Mỗi chú thích có thể mang một dictionary metadata do người dùng định nghĩa. Lưu ID, timestamp, hoặc trạng thái workflow để tích hợp với hệ thống theo dõi bên ngoài.

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Tích hợp với hệ thống quản lý người dùng

Ánh xạ thuộc tính `author` của `Comment` tới ID người dùng trong ứng dụng của bạn. Điều này cho phép định dạng dựa trên vai trò và tạo audit‑trail.

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

## Khắc phục sự cố trong môi trường production

### Giám sát hiệu năng

Theo dõi các chỉ số sau trong production:  
- **Heap usage** – đảm bảo gọi `dispose()`.  
- **Thời gian xử lý mỗi tài liệu** – ghi log timestamp trước và sau `annotator.save()`.  
- **Tỷ lệ lỗi** – bắt các ngoại lệ và phân loại chúng.

### Các bẫy thường gặp trong production

- **Lock tệp** – đảm bảo các tệp đã tải lên được đóng trước khi thực hiện chú thích.  
- **Chỉnh sửa đồng thời** – triển khai optimistic locking hoặc kiểm tra phiên bản.  
- **Tệp lớn (> 50 MB)** – tăng timeout JVM và cân nhắc sử dụng API streaming.

### Thực tiễn tốt nhất về xử lý lỗi

Bao bọc mọi lời gọi chú thích trong khối try‑catch, ghi lại stack trace đầy đủ, và ném lại một `AnnotationException` tùy chỉnh với thông báo thân thiện cho người dùng. Mẫu này đơn giản hoá việc debug và cung cấp phản hồi rõ ràng cho người tiêu dùng API.

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

## Câu hỏi thường gặp

**H: Làm thế nào để chú thích nhiều vùng văn bản trong một thao tác?**  
Đ: Tạo nhiều đối tượng `UnderlineAnnotation` với các tọa độ khác nhau và thêm chúng tuần tự bằng `annotator.add()`.

**H: Tôi có thể chú thích hình ảnh trong tài liệu PDF không?**  
Đ: Có. Sử dụng cùng hệ thống tọa độ, đảm bảo các điểm nằm trong giới hạn của hình ảnh.

**H: GroupDocs.Annotation hỗ trợ những định dạng tệp nào ngoài PDF?**  
Đ: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), và các định dạng ảnh như JPEG, PNG, TIFF.

**H: Làm sao để xử lý tài liệu rất lớn mà không hết bộ nhớ?**  
Đ: Xử lý tài liệu từng cái một, tăng heap JVM (`-Xmx`), và luôn gọi `dispose()` cho các thể hiện `Annotator` ngay sau khi dùng.

**H: Có thể trích xuất các chú thích hiện có từ tài liệu không?**  
Đ: Có. Dùng `annotator.get()` để lấy tất cả chú thích, sau đó lọc theo loại, tác giả, hoặc trang tùy nhu cầu.

---

**Cập nhật lần cuối:** 2026-10-16  
**Đã kiểm tra với:** GroupDocs.Annotation 25.2  
**Tác giả:** GroupDocs  

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

## Các hướng dẫn liên quan

- [Tạo PDF sạch Java: Chú thích gạch chân với GroupDocs](/annotation/java/annotation-management/java-groupdocs-annotate-add-remove-underline/)
- [Chỉnh sửa chú thích PDF Java - Hướng dẫn đầy đủ của GroupDocs](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [Annotate Pdfs Groupdocs Annotation Java](/annotation/java/annotation-management/annotate-pdfs-groupdocs-annotation-java/)