---
categories:
- Java PDF Processing
date: '2026-05-21'
description: Tìm hiểu cách thêm strikeout annotations vào PDF trong Java bằng GroupDocs.
  Hướng dẫn step‑by‑step này bao gồm setup, code, troubleshooting và performance tips.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Hướng Dẫn Java PDF Text Strikeout
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  type: TechArticle
- description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
  steps:
  - name: Setting Up File Paths
    text: Define the locations of your source PDF and the destination file. Incorrect
      paths are a common source of “File Not Found” errors. **Common Mistake Alert:**
      Ensure the output directory exists and is writable; GroupDocs will not auto‑create
      missing folders.
  - name: Initialize the Annotator
    text: Create an `Annotator` instance that loads the PDF into memory. **What happens
      here?** The library parses the PDF structure, builds an internal representation,
      and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this
      step may take a few seconds.
  - name: Adding Comments (Optional but Recommended)
    text: '`Comment` is a class that represents a textual note attached to an annotation,
      allowing collaborators to explain the reason for the strikeout. **Real‑world
      tip:** Use comments to explain why text is being removed—this is especially
      useful in legal or editorial review workflows.'
  - name: Defining Annotation Coordinates
    text: '`Point` objects store X‑Y coordinate pairs that define the exact location
      of an annotation on a PDF page. **Coordinate System Explained:** PDF coordinates
      start at the bottom‑left corner (0,0). The example creates a horizontal line
      from (80,730) to (240,730) on the target page. **Finding the Right C'
  - name: Creating the Strikeout Annotation
    text: '`StrikeoutAnnotation` encapsulates the visual line, its style properties
      such as color and opacity, and any associated metadata for a strikeout mark.
      **Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright
      yellow). Use an online converter if you need brand‑specific shades. '
  - name: Apply the Annotation
    text: '`addAnnotation` is a method of the `Annotator` that registers the prepared
      annotation with the document so it will be rendered and saved.'
  - name: Save and Clean Up
    text: '`dispose()` releases native resources held by the `Annotator` instance,
      preventing memory leaks after processing is complete. **Memory Management Note:**
      Calling `dispose()` frees native resources and prevents memory leaks when processing
      batches of PDFs.'
  type: HowTo
- questions:
  - answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
    question: Can I strikeout text across multiple lines?
  - answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
    question: What happens if I specify coordinates outside the page boundaries?
  - answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
    question: Can I remove strikeout annotations after adding them?
  - answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
    question: Is there a limit to how many annotations I can add to a single PDF?
  - answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
    question: How do I work with password‑protected PDFs?
  type: FAQPage
tags:
- java-pdf
- annotations
- groupdocs
- document-processing
title: Cách Thêm strikeout annotations vào PDF trong Java – Hướng Dẫn Toàn Diện của
  GroupDocs
type: docs
url: /vi/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# Cách Thêm Ghi Chú Gạch Đè vào PDF trong Java

Bạn đã bao giờ cần gạch bỏ văn bản trong một PDF một cách lập trình chưa? Dù bạn đang xây dựng hệ thống đánh giá tài liệu, tạo quy trình chỉnh sửa, hay chỉ cần đánh dấu văn bản để xóa, **cách thêm ghi chú gạch đè** trong Java là một kỹ năng thực tiễn giúp tiết kiệm thời gian và giảm công sức thủ công. Trong hướng dẫn toàn diện này, bạn sẽ khám phá mọi thứ cần biết để triển khai ghi chú gạch đè bằng GroupDocs.Annotation cho Java, từ cài đặt dự án đến tối ưu hiệu năng.

## Câu trả lời nhanh
- **Bước đầu tiên là gì?** Thêm phụ thuộc GroupDocs.Annotation Maven vào `pom.xml` của bạn.  
- **Làm thế nào để tạo gạch đè?** Tạo một đối tượng `Annotator`, định nghĩa `StrikeoutAnnotation` với các điểm, đặt màu/độ trong suốt, sau đó gọi `addAnnotation`.  
- **Tôi có thể thêm bình luận không?** Có, đính kèm một đối tượng `Comment` vào ghi chú để cộng tác.  
- **Nếu ghi chú bị đặt sai vị trí thì sao?** Điều chỉnh các điểm tọa độ; PDF sử dụng hệ thống gốc ở góc dưới‑trái.  
- **Có giới hạn kích thước tài liệu không?** GroupDocs xử lý các PDF hàng trăm trang mà không cần tải toàn bộ tệp vào bộ nhớ.

## “cách thêm gạch đè” trong ghi chú PDF là gì?
Cụm từ “cách thêm gạch đè” đề cập đến quá trình vẽ một đường qua văn bản đã chọn trong tài liệu PDF một cách lập trình bằng API ghi chú. Trong Java, GroupDocs.Annotation cung cấp một lớp `StrikeoutAnnotation` chuyên dụng để xử lý việc hiển thị, định dạng và lưu trữ các dấu gạch đè.

## Tại sao nên sử dụng GroupDocs cho gạch đè PDF trong Java?
GroupDocs.Annotation hỗ trợ **hơn 50 định dạng đầu vào và đầu ra** — bao gồm PDF, DOCX, XLSX, PPTX, HTML và các loại ảnh phổ biến — vì vậy bạn không bị giới hạn vào một loại tệp duy nhất. Nó cung cấp một API cấp cao trừu tượng hoá cấu trúc PDF cấp thấp, tự động xử lý nhúng phông chữ, render trang và lưu trữ ghi chú, cho phép các nhà phát triển tập trung vào logic nghiệp vụ thay vì các chi tiết nội bộ của PDF.

## Yêu cầu trước và các yêu cầu cài đặt

### Yêu cầu thiết yếu
- **Java Development Kit (JDK):** Phiên bản 8 trở lên (khuyến nghị JDK 11+ để thu gom rác tối ưu).  
- **GroupDocs.Annotation for Java:** Tích hợp qua Maven (xem đoạn mã Maven bên dưới).  
- **IDE:** IntelliJ IDEA, Eclipse, hoặc bất kỳ trình chỉnh sửa nào hỗ trợ Java.

### Cài đặt phụ thuộc Maven
Thêm khối phụ thuộc sau vào `pom.xml` của bạn:

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

**Mẹo chuyên nghiệp:** Luôn kiểm tra phiên bản mới nhất trên trang phát hành của GroupDocs; các bản phát hành mới thêm tính năng và sửa lỗi có thể ảnh hưởng đến việc render ghi chú.

### Cách sắp xếp giấy phép của bạn
GroupDocs.Annotation yêu cầu giấy phép hợp lệ để sử dụng trong môi trường sản xuất. Bạn có ba lựa chọn:

- **Dùng thử miễn phí:** Tải về từ [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)  
- **Giấy phép tạm thời:** Yêu cầu khóa phát triển tại [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Giấy phép đầy đủ:** Mua cho môi trường sản xuất tại [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

Bản dùng thử sẽ thêm một watermark nhẹ, vì vậy hãy lên kế hoạch kiểm thử phù hợp.

## Hướng dẫn triển khai từng bước

### Hiểu các thành phần cốt lõi
Các định nghĩa sau cung cấp cho bạn một mô hình tư duy nhanh:

- **Annotator:** Đối tượng API chính tải PDF và cung cấp các phương thức ghi chú.  
- **StrikeoutAnnotation:** Đại diện cho đường gạch đè trực quan và các tùy chọn định dạng của nó.  
- **Point:** Một cặp tọa độ (X, Y) cho biết thư viện nơi đường bắt đầu và kết thúc.  
- **Comment:** Văn bản tùy chọn được đính kèm vào ghi chú để cộng tác.

### Bước 1: Thiết lập đường dẫn tệp
Xác định vị trí của PDF nguồn và tệp đích. Các đường dẫn không đúng là nguyên nhân phổ biến gây lỗi “File Not Found”.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Cảnh báo lỗi thường gặp:** Đảm bảo thư mục đầu ra tồn tại và có quyền ghi; GroupDocs sẽ không tự động tạo thư mục thiếu.

### Bước 2: Khởi tạo Annotator
Tạo một thể hiện `Annotator` để tải PDF vào bộ nhớ.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**Điều gì xảy ra ở đây?** Thư viện phân tích cấu trúc PDF, xây dựng một biểu diễn nội bộ và chuẩn bị một canvas ghi chú cho từng trang. Đối với các tệp hàng trăm trang, bước này có thể mất vài giây.

### Bước 3: Thêm bình luận (Tùy chọn nhưng Được khuyến nghị)
`Comment` là một lớp đại diện cho ghi chú văn bản đính kèm vào một ghi chú, cho phép cộng tác viên giải thích lý do gạch đè.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Mẹo thực tế:** Sử dụng bình luận để giải thích lý do văn bản bị xóa—điều này đặc biệt hữu ích trong quy trình đánh giá pháp lý hoặc biên tập.

### Bước 4: Xác định tọa độ ghi chú
Các đối tượng `Point` lưu cặp tọa độ X‑Y xác định vị trí chính xác của một ghi chú trên trang PDF.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Giải thích hệ thống tọa độ:** Tọa độ PDF bắt đầu từ góc dưới‑trái (0,0). Ví dụ tạo một đường ngang từ (80,730) tới (240,730) trên trang mục tiêu.

**Tìm tọa độ phù hợp:** Nhiều nhà phát triển tạo một hàm trợ giúp chuyển phần trăm chiều rộng/chiều cao trang thành các điểm tuyệt đối, giúp mã chịu được các kích thước trang khác nhau.

### Bước 5: Tạo ghi chú gạch đè
`StrikeoutAnnotation` bao gồm đường visual, các thuộc tính kiểu như màu và độ trong suốt, và bất kỳ siêu dữ liệu nào liên quan đến dấu gạch đè.

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535); // Yellow
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0); 
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

**Giá trị màu:** `fontColor` sử dụng giá trị RGB thập phân (ví dụ, 65535 cho màu vàng sáng). Sử dụng công cụ chuyển đổi trực tuyến nếu bạn cần màu sắc đặc thù của thương hiệu.

**Khuyến nghị độ trong suốt:** Độ trong suốt `0.7` (70 %) cung cấp dấu hiệu trực quan rõ ràng đồng thời giữ cho văn bản nền vẫn đọc được.

### Bước 6: Áp dụng ghi chú
`addAnnotation` là một phương thức của `Annotator` đăng ký ghi chú đã chuẩn bị vào tài liệu để nó được render và lưu.

```java
annotator.add(strikeout);
```

### Bước 7: Lưu và dọn dẹp
`dispose()` giải phóng các tài nguyên gốc mà thể hiện `Annotator` giữ, ngăn ngừa rò rỉ bộ nhớ sau khi xử lý hoàn tất.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Lưu ý quản lý bộ nhớ:** Gọi `dispose()` giải phóng tài nguyên gốc và ngăn ngừa rò rỉ bộ nhớ khi xử lý hàng loạt PDF.

## Các vấn đề thường gặp và cách khắc phục

### Vấn đề 1: Lỗi “File Not Found”
**Triệu chứng:** Ngoại lệ được ném trong quá trình khởi tạo `Annotator`.  
**Giải pháp:** Xác minh cả đường dẫn đầu vào và đầu ra, và chắc chắn ứng dụng có quyền đọc/ghi.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### Vấn đề 2: Gạch đè xuất hiện ở vị trí sai
**Triệu chứng:** Đường không khớp với văn bản mong muốn.  
**Giải pháp:** Nhớ rằng tọa độ Y của PDF tăng lên phía trên. Sử dụng công cụ gỡ lỗi trực quan hoặc in kích thước trang để tinh chỉnh các điểm.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### Vấn đề 3: Ghi chú không hiển thị
**Triệu chứng:** Không có gạch đè nào hiển thị sau khi lưu.  
**Nguyên nhân có thể & Cách khắc phục:**  
- **Độ trong suốt quá thấp:** Tạm thời đặt độ trong suốt thành `1.0` để kiểm tra khả năng hiển thị.  
- **Màu pha trộn:** Sử dụng màu tương phản cao như đỏ (`255`).  
- **Chỉ số trang không đúng:** Số trang bắt đầu từ 0; đảm bảo bạn nhắm đúng trang.

### Vấn đề 4: Vấn đề bộ nhớ với tệp lớn
**Triệu chứng:** `OutOfMemoryError` hoặc hiệu năng chậm.  
**Giải pháp:**  
- Xử lý tài liệu theo các lô nhỏ hơn.  
- Sử dụng API streaming nếu có.  
- Luôn gọi `dispose()` sau mỗi tài liệu.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## Ứng dụng thực tế và các trường hợp sử dụng

### Đánh giá tài liệu pháp lý
Các công ty luật ghi chú gạch đè vào hợp đồng để chỉ ra các điều khoản đã xóa đồng thời giữ lại dấu vết kiểm toán.

### Chỉnh sửa bài báo học thuật
Giáo sư sử dụng gạch đè để đề xuất loại bỏ trong quá trình phản biện, giữ nguyên văn bản gốc để ngữ cảnh.

### Hệ thống quản lý nội dung
Các nền tảng xuất bản tự động đánh dấu các phần vi phạm chính sách bằng gạch đè trước khi kiểm duyệt thủ công.

### Kiểm soát phiên bản cho tài liệu
Doanh nghiệp coi các ghi chú gạch đè như “dấu xóa” trong quy trình kiểm soát phiên bản tập trung vào tài liệu, tương tự như diff trong mã nguồn.

## Mẹo tối ưu hiệu năng

### Chiến lược xử lý hàng loạt
Khi xử lý nhiều PDF, tái sử dụng một thể hiện `Annotator` duy nhất nếu có thể và xử lý các tệp bằng các luồng song song.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### Thực hành tốt quản lý bộ nhớ
- Gọi `dispose()` trên mọi `Annotator`.  
- Giới hạn số tài liệu tải đồng thời để tránh áp lực lên heap.  
- Giám sát việc sử dụng bộ nhớ JVM bằng các công cụ như VisualVM.

### Lưu trữ bộ nhớ đệm tọa độ
Nếu bạn áp dụng cùng một bố cục ghi chú trên nhiều tệp, hãy lưu vào bộ nhớ đệm các đối tượng `Point` để tránh tính toán lại.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## Tùy chọn tùy chỉnh nâng cao

### Lựa chọn màu động
Chọn màu tại thời gian chạy dựa trên quy tắc kinh doanh (ví dụ, đỏ cho các xóa quan trọng, vàng cho các xóa tạm thời).

```java
// Choose colors based on annotation type or user
int colorByPriority = getPriorityColor(annotationType);
strikeout.setFontColor(colorByPriority);

private int getPriorityColor(String type) {
    switch(type) {
        case "HIGH": return 255;    // Red
        case "MEDIUM": return 65535; // Yellow  
        case "LOW": return 65280;   // Green
        default: return 0;          // Black
    }
}
```

### Gạch đè đa dòng
Tạo một loạt các cặp `Point` để vẽ một đường zíc-zắc cắt qua nhiều dòng văn bản.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## Danh sách kiểm tra khắc phục sự cố
1. **Quyền tệp:** Xác minh quyền đọc/ghi.  
2. **Phiên bản thư viện:** Đảm bảo bạn đang sử dụng phiên bản GroupDocs.Annotation được hỗ trợ.  
3. **Trạng thái giấy phép:** Xác nhận tệp giấy phép được tham chiếu đúng.  
4. **Tương thích PDF:** Kiểm tra PDF không bị hỏng và nằm trong giới hạn kích thước hỗ trợ.  
5. **Xác thực tọa độ:** Đảm bảo tất cả các điểm nằm trong giới hạn trang.  
6. **Không gian heap:** Tăng JVM `-Xmx` nếu xử lý các tệp rất lớn.

## Câu hỏi thường gặp

**Hỏi: Tôi có thể gạch đè văn bản trên nhiều dòng không?**  
**Đáp:** Có. Tạo một vài đối tượng `Point` theo đường dẫn mong muốn; ghi chú sẽ theo polyline đã cung cấp.

**Hỏi: Điều gì xảy ra nếu tôi chỉ định tọa độ ngoài giới hạn trang?**  
**Đáp:** Ghi chú sẽ bị cắt và có thể không hiển thị. Luôn xác thực tọa độ so với chiều rộng và chiều cao của trang.

**Hỏi: Tôi có thể xóa các ghi chú gạch đè sau khi đã thêm không?**  
**Đáp:** Chắc chắn. Sử dụng phương thức `removeAnnotation` với ID của ghi chú hoặc lọc theo loại để xóa chúng bằng lập trình.

**Hỏi: Có giới hạn số lượng ghi chú tôi có thể thêm vào một PDF duy nhất không?**  
**Đáp:** GroupDocs không đặt giới hạn cứng, nhưng hiệu năng có thể giảm sau hàng nghìn ghi chú. Hãy cân nhắc phân trang hoặc tóm tắt ghi chú cho các bộ dữ liệu rất lớn.

**Hỏi: Làm thế nào để làm việc với PDF được bảo vệ bằng mật khẩu?**  
**Đáp:** Truyền mật khẩu vào hàm khởi tạo `Annotator`. Thư viện sẽ giải mã tài liệu trong bộ nhớ trước khi áp dụng bất kỳ ghi chú nào.

**Hỏi: Làm sao tôi có thể xử lý PDF với các kích thước và hướng trang khác nhau?**  
**Đáp:** Lấy kích thước của mỗi trang qua `annotator.getPageInfo(pageNumber)` và tính toán tọa độ tương đối với các kích thước đó để đảm bảo vị trí nhất quán.

## Kết luận
Bạn giờ đã có một giải pháp hoàn chỉnh, sẵn sàng cho môi trường sản xuất để **cách thêm gạch đè** vào PDF trong Java bằng GroupDocs.Annotation. Bằng cách nắm vững việc xử lý đường dẫn tệp, tính toán tọa độ và quản lý tài nguyên, bạn có thể tích hợp khả năng này vào công cụ đánh giá tài liệu, quy trình nội dung, hoặc bất kỳ ứng dụng Java nào cần phản hồi trực quan chính xác.

**Các bước tiếp theo**
1. Sao chép dự án mẫu và chạy nó trên một PDF mẫu.  
2. Thử nghiệm với các màu, độ trong suốt và văn bản bình luận khác nhau.  
3. Tích hợp quy trình làm việc ghi chú vào dịch vụ xử lý tài liệu hiện có của bạn.  
4. Khám phá các loại ghi chú liên quan — đánh dấu, ghi chú dính, và ghi chú hình dạng — để mở rộng bộ công cụ thao tác PDF của bạn.

Sẵn sàng cho nhiều hơn? Hãy khám phá tài liệu chính thức để hiểu sâu hơn về API.

## Tài nguyên bổ sung
- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - Tài liệu chung cho các thư viện GroupDocs
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - Tham chiếu API đầy đủ  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - Chi tiết từng phương thức  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - Giữ thư viện của bạn luôn cập nhật  
- [Purchase License](https://purchase.groupdocs.com/buy) - Giấy phép sẵn sàng cho sản xuất  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - Đánh giá trước khi mua  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - Kiểm thử phát triển  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - Hỗ trợ cộng đồng và hỗ trợ chính thức  

**Cập nhật lần cuối:** 2026-05-21  
**Kiểm thử với:** GroupDocs.Annotation 23.12 cho Java  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan
- [Thêm Ghi chú PDF Java – Hướng dẫn đầy đủ của GroupDocs](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)
- [Hướng dẫn Ghi chú PDF Java - Hướng dẫn toàn diện về Đánh dấu PDF](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)
- [Cách Thêm Mũi tên vào PDF trong Java – Hướng dẫn đầy đủ của GroupDocs](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)