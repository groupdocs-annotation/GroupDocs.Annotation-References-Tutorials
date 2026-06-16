---
categories:
- Java Development
date: '2026-06-16'
description: Tìm hiểu cách thêm đo lường vào hình ảnh và các đo lường tài liệu khác
  trong Java bằng GroupDocs.Annotation. Hướng dẫn đầy đủ với code examples, troubleshooting
  tips, và best practices.
keywords:
- how to add measurement
- distance annotation Java
- measure image Java
- GroupDocs annotation tutorial
- Java document measurement
lastmod: '2026-06-16'
linktitle: Hướng dẫn Java Distance Annotations
schemas:
- author: GroupDocs
  dateModified: '2026-06-16'
  description: Learn how to add measurement to image and other document measurements
    in Java using GroupDocs.Annotation. Complete tutorial with code examples, troubleshooting
    tips, and best practices.
  headline: 'Java Distance Annotation Tutorial: How to add measurement to image with
    GroupDocs'
  type: TechArticle
- description: Learn how to add measurement to image and other document measurements
    in Java using GroupDocs.Annotation. Complete tutorial with code examples, troubleshooting
    tips, and best practices.
  name: 'Java Distance Annotation Tutorial: How to add measurement to image with GroupDocs'
  steps:
  - name: Create Interactive Replies (Optional But Recommended)
    text: Replies let collaborators attach comments directly to a measurement, turning
      a simple ruler into a discussion thread. java import com.groupdocs.annotation.models.Reply;
      import java.util.ArrayList; import java.util.Calendar; Reply reply1 = new Reply();
      reply1.setComment("First comment"); reply1.setRe
  - name: Configure Your Distance Annotation
    text: The `DistanceAnnotation` class is GroupDocs.Annotation's top‑level object
      that represents a ruler measurement. You can customize its geometry, visual
      style, and attached message. `Rectangle` defines the annotation's bounding box
      on the page. `PenStyle` enumerates line styles such as solid, dash, and
  - name: Apply the Annotation and Save
    text: Once the annotation is ready, add it to the document and persist the changes.
      java annotator.add(distance); annotator.save("YOUR_OUTPUT_DIRECTORY/output.pdf");
      annotator.dispose(); **Important:** Always invoke `dispose()` after saving,
      especially when processing many documents in a batch job.
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation supports PDFs, Word documents, PowerPoint presentations,
      Excel spreadsheets, and common image formats (PNG, JPEG, TIFF, BMP). The feature
      works consistently across all 50+ supported formats.
    question: What document formats support distance annotations?
  - answer: Absolutely! You have full control over pen color, line style (solid, dotted,
      dashed), line width, and opacity. You can also define custom end‑cap symbols
      for specialized engineering standards.
    question: Can I customize the appearance of measurement lines?
  - answer: The annotation itself displays the text you set in the `message` property.
      Perform any unit conversion (e.g., inches ↔ millimeters) in your Java code before
      assigning the message.
    question: How do I handle measurements in different units?
  - answer: Yes. In compatible viewers (GroupDocs.Viewer, Adobe Acrobat, or your own
      web viewer), users can click, drag, and edit the ruler. Replies and comments
      remain attached to the measurement for collaborative review.
    question: Can users interact with distance annotations after they're added?
  - answer: Adding up to several hundred annotations per document has a negligible
      impact (< 5 % CPU overhead). When you exceed 1,000 annotations, loading times
      may increase modestly, but the library remains stable and responsive.
    question: What's the performance impact of adding many annotations?
  type: FAQPage
tags:
- GroupDocs
- document-annotation
- Java-tutorial
- PDF-processing
title: 'Hướng dẫn chú thích khoảng cách Java: Cách thêm đo lường vào hình ảnh với
  GroupDocs'
type: docs
url: /vi/java/graphical-annotations/add-distance-annotations-java-groupdocs-annotation/
weight: 1
---

# Hướng dẫn chú thích khoảng cách Java: Cách thêm đo lường vào hình ảnh với GroupDocs

Trong hướng dẫn toàn diện này, bạn sẽ khám phá **cách thêm đo lường** vào hình ảnh, PDF và các loại tài liệu khác bằng cách sử dụng GroupDocs.Annotation cho Java. Dù bạn đang xây dựng một trình xem CAD, một công cụ đánh giá kiến trúc, hay một nền tảng tài liệu kỹ thuật, các chú thích khoảng cách cung cấp cho người dùng một thước đo rõ ràng, tương tác mà họ có thể tin cậy. Khi kết thúc tutorial, bạn sẽ có một giải pháp sẵn sàng cho sản xuất, có khả năng vẽ các đo lường chính xác, tùy chỉnh giao diện và tích hợp mượt mà với mã Java hiện có của bạn.

## Cách thêm đo lường vào hình ảnh trong Java?

Tải tài liệu mục tiêu bằng `Annotator`, tạo một `DistanceAnnotation`, cấu hình các thuộc tính hiển thị, thêm nó vào trang mong muốn và cuối cùng lưu tệp. Chỉ với bốn dòng mã, bạn sẽ có một thước đo hoạt động đầy đủ mà người dùng cuối có thể chỉnh sửa trong bất kỳ trình xem tuân thủ nào. Cách tiếp cận này hoạt động cho PDF, tệp Word, bản trình chiếu PowerPoint, bảng tính Excel và các định dạng hình ảnh phổ biến như PNG, JPEG và TIFF.

## Câu trả lời nhanh
- **Cách dễ nhất để thêm đo lường vào hình ảnh trong Java là gì?** Sử dụng lớp `DistanceAnnotation` của GroupDocs.Annotation.  
- **Các định dạng nào được hỗ trợ?** PDF, Word, PowerPoint, Excel và các loại hình ảnh phổ biến (PNG, JPEG, TIFF).  
- **Tôi có cần giấy phép cho việc phát triển không?** Một bản dùng thử miễn phí hoặc giấy phép tạm thời đủ cho việc thử nghiệm; giấy phép thương mại cần thiết cho môi trường sản xuất.  
- **Tôi có thể tùy chỉnh giao diện của đường thước đo không?** Có – bạn có thể đặt màu, kiểu, độ rộng và độ trong suốt.  
- **Làm sao tránh rò rỉ bộ nhớ?** Luôn giải phóng đối tượng `Annotator` hoặc sử dụng try‑with‑resources.

## Các chú thích khoảng cách là gì (Và tại sao bạn cần chúng)?

Các chú thích khoảng cách là các yếu tố hình ảnh tương tác hiển thị độ dài đo được giữa hai điểm trong tài liệu. Chúng hoạt động như những thước đo kỹ thuật số có thể đặt ở bất kỳ vị trí nào, kéo thả và chỉnh sửa trong thời gian thực, cung cấp cho người dùng phản hồi trực quan ngay lập tức mà không cần tính toán thủ công.

Các chú thích này mang lại **độ rõ ràng về hình ảnh**, **phản hồi tương tác**, và **giao diện chuyên nghiệp** cho bất kỳ tài liệu kỹ thuật nào. Chúng đặc biệt có giá trị đối với bản vẽ kiến trúc, sơ đồ kỹ thuật, hình ảnh y tế và bản đồ mặt bằng bất động sản, nơi các kích thước chính xác là yếu tố then chốt.

## Các thực hành tốt nhất khi đo lường tài liệu

Trước khi bắt đầu viết mã, hãy ghi nhớ những thực hành đã được chứng minh sau:

1. **Chỉ mục trang bắt đầu từ 0** – `pageNumber = 0` chỉ trang đầu tiên, phù hợp với mô hình nội bộ của GroupDocs.Annotation.  
2. **Màu sắc tương phản cao** – Chọn màu thước đo nổi bật trên nền tài liệu (ví dụ: vàng sáng trên sơ đồ tối).  
3. **Điều chỉnh độ trong suốt** – Độ trong suốt `0.7` cân bằng giữa khả năng nhìn thấy và chi tiết nền; tăng lên `1.0` cho các đo lường quan trọng.  
4. **Nhóm các chú thích liên quan** – Sử dụng trả lời hoặc bình luận để giữ các cuộc thảo luận được tổ chức quanh một đo lường cụ thể.  
5. **Giải phóng kịp thời** – Luôn gọi `annotator.dispose()` hoặc dùng try‑with‑resources để giải phóng bộ nhớ native, đặc biệt khi xử lý các tệp lớn.

## Yêu cầu trước: Những gì bạn cần trước khi bắt đầu

### Yêu cầu môi trường phát triển
- **Java Development Kit (JDK)**: Phiên bản 8 trở lên (khuyến nghị JDK 11+).  
- **Maven hoặc Gradle**: Các ví dụ sử dụng Maven, nhưng cùng các phụ thuộc cũng hoạt động với Gradle.  
- **IDE**: Bất kỳ IDE Java nào (IntelliJ IDEA, Eclipse, VS Code, v.v.) đều được.

### Kiến thức tiên quyết
Bạn nên đã quen thuộc với:
- Các khái niệm cơ bản của Java (lớp, đối tượng, phương thức).  
- Thêm thư viện bên ngoài qua Maven/Gradle.  
- I/O tệp cơ bản và xử lý đường dẫn.

### Tài liệu thử nghiệm
Chuẩn bị một vài tệp mẫu:
- Một hoặc nhiều trang PDF.  
- Hình ảnh PNG/JPEG/TIFF để thử nghiệm dạng raster.  
- Tùy chọn: tệp CAD nếu bạn muốn thử nghiệm với bản vẽ kỹ thuật.

## Cài đặt GroupDocs.Annotation cho Java

Việc tích hợp GroupDocs.Annotation rất đơn giản. Dưới đây là các tọa độ Maven bạn cần thêm vào dự án.

### Tích hợp Maven

Thêm cấu hình sau vào tệp `pom.xml` của bạn:

```xml
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
```

### Hiểu yêu cầu cấp phép

GroupDocs.Annotation cung cấp ba mô hình cấp phép:

1. **Dùng thử miễn phí** – Lý tưởng để đánh giá; bao gồm tất cả tính năng với một số hạn chế nhỏ về sử dụng.  
2. **Giấy phép tạm thời** – Loại bỏ các hạn chế của bản dùng thử cho phát triển và thử nghiệm.  
3. **Giấy phép thương mại** – Sử dụng đầy đủ tính năng, sẵn sàng cho môi trường sản xuất mà không có giới hạn.

Bắt đầu với bản dùng thử miễn phí, sau đó nâng cấp khi bạn đã sẵn sàng cho sản xuất.

### Khởi tạo cơ bản

Lớp `Annotator` là điểm vào cho mọi thao tác chú thích. Nó tải tài liệu, cung cấp API chỉnh sửa và ghi kết quả trở lại đĩa.

```java
```java
import com.groupdocs.annotation.Annotator;

// Initialize annotator with the input file path
final Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```
```

**Pro Tip:** Đặt `Annotator` trong khối try‑with‑resources hoặc gọi `dispose()` một cách rõ ràng để tránh rò rỉ bộ nhớ native.

## Hướng dẫn triển khai từng bước

Bây giờ chúng ta sẽ đi qua một quy trình hoàn chỉnh, sẵn sàng cho sản xuất để thêm các chú thích khoảng cách.

### Bước 1: Tạo phản hồi tương tác (Tùy chọn nhưng được khuyến nghị)

Phản hồi cho phép cộng tác viên đính kèm bình luận trực tiếp vào một đo lường, biến một thước đo đơn giản thành một chuỗi thảo luận.

```java
```java
import com.groupdocs.annotation.models.Reply;
import java.util.ArrayList;
import java.util.Calendar;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

ArrayList<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```
```

**Khi nào nên sử dụng phản hồi:** Trong các vòng duyệt đa người dùng, khi bạn cần giải thích lý do chọn một kích thước hoặc yêu cầu đồng nghiệp làm rõ.

### Bước 2: Cấu hình chú thích khoảng cách của bạn

Lớp `DistanceAnnotation` là đối tượng cấp cao của GroupDocs.Annotation đại diện cho một đo lường thước. Bạn có thể tùy chỉnh hình học, kiểu hiển thị và thông điệp đính kèm.

`Rectangle` xác định hộp bao của chú thích trên trang. `PenStyle` liệt kê các kiểu đường như solid, dash và dot.

```java
```java
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.PenStyle;
import com.groupdocs.annotation.models.annotationmodels.DistanceAnnotation;

DistanceAnnotation distance = new DistanceAnnotation();
distance.setBox(new Rectangle(200, 150, 200, 30)); // Set the annotation's position and size
distance.setCreatedOn(Calendar.getInstance().getTime()); 
distance.setMessage("This is a distance annotation");
distance.setOpacity(0.7);
distance.setPageNumber(0); 
distance.setPenColor(65535);
distance.setPenStyle(PenStyle.DOT);
distance.setPenWidth((byte) 3);

distance.setReplies(replies); // Attach replies
```
```

**Các tùy chọn cấu hình chính**  
- `setBox()` – Đặt hình chữ nhật bao quanh của chú thích trên trang.  
- `setOpacity()` – Điều chỉnh độ trong suốt (`0.0` = vô hình, `1.0` = hoàn toàn không trong suốt).  
- `setPenColor()` – Màu RGB cho đường đo.  
- `setPenStyle()` – Kiểu đường (`DOT`, `DASH`, `SOLID`).  
- `setPenWidth()` – Độ dày của đường tính bằng điểm.

### Bước 3: Áp dụng chú thích và lưu

Khi chú thích đã sẵn sàng, thêm nó vào tài liệu và lưu các thay đổi.

```java
```java
annotator.add(distance);
annotator.save("YOUR_OUTPUT_DIRECTORY/output.pdf");
annotator.dispose();
```
```

**Important:** Luôn gọi `dispose()` sau khi lưu, đặc biệt khi xử lý nhiều tài liệu trong một công việc batch.

## Ví dụ làm việc hoàn chỉnh

Kết hợp tất cả lại, dưới đây là một ví dụ end‑to‑end đầy đủ, tải một PDF, thêm chú thích khoảng cách và lưu kết quả.

```java
```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.PenStyle;
import com.groupdocs.annotation.models.annotationmodels.DistanceAnnotation;
import java.util.ArrayList;
import java.util.Calendar;

public class DistanceAnnotationExample {
    public static void main(String[] args) {
        try (Annotator annotator = new Annotator("input.pdf")) {
            // Create replies for the annotation
            ArrayList<Reply> replies = new ArrayList<>();
            Reply reply = new Reply();
            reply.setComment("Measurement verified by engineering team");
            reply.setRepliedOn(Calendar.getInstance().getTime());
            replies.add(reply);

            // Configure the distance annotation
            DistanceAnnotation distance = new DistanceAnnotation();
            distance.setBox(new Rectangle(100, 100, 300, 50));
            distance.setCreatedOn(Calendar.getInstance().getTime());
            distance.setMessage("Wall length: 12 feet");
            distance.setOpacity(0.8);
            distance.setPageNumber(0);
            distance.setPenColor(0xFF0000); // Red color
            distance.setPenStyle(PenStyle.SOLID);
            distance.setPenWidth((byte) 2);
            distance.setReplies(replies);

            // Add and save
            annotator.add(distance);
            annotator.save("output_with_distance_annotation.pdf");
            
            System.out.println("Distance annotation added successfully!");
        } catch (Exception e) {
            System.err.println("Error adding distance annotation: " + e.getMessage());
        }
    }
}
```
```

Chạy đoạn mã, mở tệp đầu ra trong bất kỳ trình xem PDF nào hỗ trợ chú thích, và bạn sẽ thấy một thước đo hoạt động đầy đủ, sẵn sàng cho tương tác.

## Các trường hợp sử dụng phổ biến và ứng dụng thực tế

Hiểu được nơi các chú thích khoảng cách tỏa sáng giúp bạn quyết định cách nhúng chúng vào sản phẩm của mình.

### Tài liệu kỹ thuật và hướng dẫn
- Làm nổi bật kích thước thành phần trong hướng dẫn lắp ráp.  
- Hiển thị khu vực cách ly trong hướng dẫn cài đặt.  
- Cung cấp các đo lường tham khảo nhanh cho danh sách kiểm tra kiểm soát chất lượng.

### Dự án kiến trúc và kỹ thuật
- Hiển thị kích thước phòng trên bản đồ mặt bằng.  
- Chỉ ra khoảng cách giữa các yếu tố cấu trúc.  
- Đánh dấu khoảng cách dây điện và khoảng cách an toàn.

### Ứng dụng y tế và khoa học
- Đo các cấu trúc giải phẫu trong hình ảnh y khoa.  
- Thêm thước tỷ lệ vào slide kính hiển vi.  
- Ghi lại kích thước mẫu trong báo cáo nghiên cứu.

### Bất động sản và quản lý tài sản
- Trực quan hoá ranh giới lô đất và đường biên.  
- Hiển thị kích thước phòng cho các danh sách bất động sản.  
- Chỉ ra kích thước chỗ đậu xe và các đo lường cảnh quan.

## Khắc phục các vấn đề thường gặp

Ngay cả một ví dụ được viết tốt cũng có thể gặp trục trặc. Dưới đây là những vấn đề phổ biến nhất và cách giải quyết chúng.

### Vấn đề: “File not found” hoặc vấn đề đường dẫn

**Symptoms:** Một ngoại lệ được ném khi tạo `Annotator`.  
**Solution:** Sử dụng đường dẫn tuyệt đối trong quá trình phát triển, xác minh tệp tồn tại và đảm bảo quy trình có quyền đọc.

```java
```java
// Better path handling
String inputPath = new File("documents/input.pdf").getAbsolutePath();
final Annotator annotator = new Annotator(inputPath);
```
```

### Vấn đề: Chú thích không hiển thị

**Symptoms:** Mã chạy không có lỗi, nhưng không có thước đo nào xuất hiện.  
**Common causes:** Chỉ mục trang sai (nhớ rằng các trang bắt đầu từ 0), chú thích được đặt ngoài vùng hiển thị, hoặc độ trong suốt được đặt quá thấp.

**Quick fixes:**

```java
```java
distance.setPageNumber(0); // First page
distance.setOpacity(1.0);  // Fully opaque
distance.setBox(new Rectangle(50, 50, 200, 30)); // Visible position
```
```

### Vấn đề: Vấn đề bộ nhớ với tài liệu lớn

**Symptoms:** `OutOfMemoryError` hoặc hiệu năng chậm trên các tệp có hàng trăm trang.  
**Solutions:**  
- Giải phóng mỗi đối tượng `Annotator` ngay khi hoàn thành.  
- Xử lý tài liệu tuần tự thay vì tải tất cả cùng một lúc.  
- Tăng bộ nhớ heap JVM (`-Xmx4g` hoặc cao hơn) cho các đầu vào rất lớn.

```java
```java
// Good practice - use try-with-resources
try (Annotator annotator = new Annotator("large-document.pdf")) {
    // Your annotation code here
} // Automatic disposal
```
```

### Vấn đề: Lỗi liên quan đến giấy phép

**Symptoms:** Cảnh báo về giới hạn bản dùng thử hoặc lỗi xác thực giấy phép.  
**Solutions:**  
- Xác nhận đường dẫn tệp giấy phép đúng và tệp có thể đọc được.  
- Đảm bảo phiên bản giấy phép khớp với phiên bản thư viện GroupDocs.Annotation bạn đang sử dụng.  
- Kiểm tra xem giấy phép tạm thời đã hết hạn chưa.

## Mẹo tối ưu hoá hiệu suất

Khi bạn chuyển từ prototype sang sản xuất, hãy lưu ý các cân nhắc về hiệu suất sau.

### Các thực hành tốt nhất quản lý bộ nhớ
- **Always dispose**: Ưu tiên try‑with‑resources hoặc gọi `dispose()` một cách rõ ràng.  
- **Batch operations**: Nhóm nhiều thay đổi chú thích trong một phiên `Annotator` duy nhất để giảm chi phí.  
- **Profiling**: Sử dụng các profiler Java (VisualVM, YourKit) để giám sát việc sử dụng bộ nhớ native.

### Tối ưu hoá xử lý tệp
- **Cache frequently accessed documents** trong bộ nhớ khi chỉ đọc.  
- **Prefer PDF** hơn hình ảnh độ phân giải cao để tăng tốc render; PDF thường nhỏ hơn 30‑40 % so với cùng nội dung hình ảnh.  
- **Adjust image resolution**: Giảm độ phân giải nguồn xuống tối đa 150 DPI trừ khi cần độ chi tiết cao hơn.

### Các cân nhắc xử lý đồng thời

Nếu dịch vụ của bạn xử lý nhiều tệp đồng thời, hãy tuân theo các quy tắc sau:

```java
```java
// Example of efficient batch processing
public void processMultipleDocuments(List<String> filePaths) {
    for (String path : filePaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Add multiple annotations per document
            addDistanceAnnotation(annotator, config1);
            addDistanceAnnotation(annotator, config2);
            // Save once with all annotations
            annotator.save(getOutputPath(path));
        }
    }
}
```
```

- Mỗi luồng phải tạo một thể hiện `Annotator` riêng.  
- Sử dụng thread pool có giới hạn để tránh cạn kiệt tài nguyên hệ thống.  
- Giám sát CPU và heap khi tải; mở rộng quy mô ngang nếu cần.

## Các tùy chọn cấu hình nâng cao

Khi bạn đã nắm vững các kiến thức cơ bản, hãy khám phá các tính năng nâng cao này để tinh chỉnh các chú thích của mình.

### Tùy chọn kiểu dáng tùy chỉnh

```java
```java
// Advanced pen styling
distance.setPenStyle(PenStyle.DASH_DOT);
distance.setPenWidth((byte) 4);
distance.setPenColor(0x00FF00); // Hex color codes work too

// Custom opacity for different emphasis levels
distance.setOpacity(0.6); // Subtle background measurements
// vs
distance.setOpacity(1.0); // Prominent foreground measurements
```
```

Bạn có thể định nghĩa một đối tượng `Pen` tùy chỉnh, áp dụng gradient fill, hoặc thậm chí nhúng các ký hiệu SVG ở đầu và cuối đường thước.

### Định vị động

```java
```java
// Calculate position based on document dimensions or content
Rectangle dynamicBox = calculateOptimalPosition(documentWidth, documentHeight);
distance.setBox(dynamicBox);
```
```

Tận dụng tọa độ tương đối trang để chú thích tự động định vị lại khi tài liệu được phóng to hoặc xoay.

### Chú thích có điều kiện

```java
```java
// Add annotations based on document content or user preferences
if (document.getType() == DocumentType.ARCHITECTURAL_PLAN) {
    distance.setMessage("Room dimension");
    distance.setPenStyle(PenStyle.SOLID);
} else if (document.getType() == DocumentType.ENGINEERING_DRAWING) {
    distance.setMessage("Component spacing");
    distance.setPenStyle(PenStyle.DOT);
}
```
```

Thêm logic chỉ tạo chú thích khoảng cách khi đáp ứng một điều kiện nhất định (ví dụ: khi một thành phần vượt quá ngưỡng dung sai).

## Tích hợp với các hệ thống khác

Các chú thích khoảng cách không tồn tại độc lập — chúng tự nhiên phù hợp với các hệ sinh thái quản lý tài liệu rộng hơn.

### Tích hợp cơ sở dữ liệu

`AnnotationRecord` là mô hình dữ liệu tùy chỉnh để lưu trữ siêu dữ liệu chú thích trong cơ sở dữ liệu.

```java
```java
// Save annotation details to database
AnnotationRecord record = new AnnotationRecord();
record.setDocumentId(documentId);
record.setAnnotationType("distance");
record.setMeasurement(distance.getMessage());
record.setCreatedDate(distance.getCreatedOn());
```
```

Lưu siêu dữ liệu chú thích (tác giả, thời gian, giá trị đo) trong cơ sở dữ liệu quan hệ để phục vụ báo cáo và tìm kiếm.

### Tích hợp ứng dụng web

`DistanceAnnotationRequest` là DTO truyền tham số chú thích từ client tới server.

```java
```java
@PostMapping("/documents/{id}/annotations/distance")
public ResponseEntity<String> addDistanceAnnotation(
    @PathVariable String id,
    @RequestBody DistanceAnnotationRequest request) {
    // Process the annotation request
    // Return success/failure response
}
```
```

Cung cấp endpoint REST nhận tệp, thêm chú thích khoảng cách dựa trên payload JSON và trả về tài liệu đã được chú thích.

### Tích hợp lưu trữ đám mây

```java
```java
// Download from cloud, process, upload result
byte[] documentBytes = cloudStorageService.download(documentPath);
// Process with GroupDocs.Annotation
byte[] annotatedDocument = processAnnotations(documentBytes);
cloudStorageService.upload(outputPath, annotatedDocument);
```
```

Đọc và ghi tệp trực tiếp từ AWS S3, Azure Blob Storage hoặc Google Cloud Storage bằng SDK tương ứng, sau đó truyền stream tới `Annotator`.

## Câu hỏi thường gặp

**Q: Các định dạng tài liệu nào hỗ trợ chú thích khoảng cách?**  
A: GroupDocs.Annotation hỗ trợ PDF, tài liệu Word, bản trình chiếu PowerPoint, bảng tính Excel và các định dạng hình ảnh phổ biến (PNG, JPEG, TIFF, BMP). Tính năng này hoạt động nhất quán trên hơn 50 định dạng được hỗ trợ.

**Q: Tôi có thể tùy chỉnh giao diện của các đường đo không?**  
A: Chắc chắn! Bạn có toàn quyền kiểm soát màu bút, kiểu đường (solid, dotted, dashed), độ rộng và độ trong suốt. Bạn cũng có thể định nghĩa các ký hiệu đầu mút tùy chỉnh cho các tiêu chuẩn kỹ thuật đặc thù.

**Q: Làm sao xử lý đo lường ở các đơn vị khác nhau?**  
A: Chính chú thích hiển thị văn bản bạn đặt trong thuộc tính `message`. Thực hiện bất kỳ chuyển đổi đơn vị nào (ví dụ: inch ↔ millimeter) trong mã Java trước khi gán thông điệp.

**Q: Người dùng có thể tương tác với chú thích khoảng cách sau khi chúng được thêm không?**  
A: Có. Trong các trình xem tương thích (GroupDocs.Viewer, Adobe Acrobat, hoặc trình xem web của bạn), người dùng có thể click, kéo và chỉnh sửa thước đo. Các phản hồi và bình luận vẫn được gắn vào đo lường để hỗ trợ đánh giá cộng tác.

**Q: Tác động hiệu suất của việc thêm nhiều chú thích là như thế nào?**  
A: Thêm đến vài trăm chú thích mỗi tài liệu chỉ gây tăng nhẹ (< 5 % tải CPU). Khi vượt quá 1.000 chú thích, thời gian tải có thể tăng nhẹ, nhưng thư viện vẫn ổn định và phản hồi tốt.

## Kết luận và các bước tiếp theo

Bạn hiện đã có một lộ trình hoàn chỉnh, sẵn sàng cho sản xuất để **cách thêm đo lường** vào hình ảnh và các tài liệu khác trong Java bằng GroupDocs.Annotation. Bằng cách tận dụng các chú thích khoảng cách, bạn có thể biến các bản vẽ tĩnh thành các tài sản tương tác, giàu dữ liệu, giúp cải thiện hợp tác và giảm lỗi.

**Những điểm chính**
- Các chú thích khoảng cách cung cấp đo lường chính xác, trực quan trên hơn 50 định dạng tệp.  
- Triển khai ngắn gọn: tải, cấu hình, thêm, lưu.  
- Hiệu suất vững chắc cho tài liệu vừa và lớn; tuân thủ các mẹo quản lý bộ nhớ cho các tệp lớn.  
- Các điểm tích hợp (CSDL, REST, đám mây) cho phép bạn nhúng chú thích vào bất kỳ quy trình làm việc nào.

### Các bước tiếp theo được đề xuất
1. **Prototype**: Sao chép ví dụ đầy đủ, chạy trên các PDF hoặc hình ảnh của bạn, và xác nhận thước đo xuất hiện như mong đợi.  
2. **Khám phá các loại chú thích khác**: Chú thích highlight, text và stamp có thể bổ trợ cho các đo lường khoảng cách.  
3. **Xây dựng UI**: Thiết kế giao diện kéo‑thả cho phép người dùng cuối đặt thước đo trực tiếp trong trình duyệt hoặc ứng dụng desktop.  
4. **Lập kế hoạch mở rộng**: Nếu bạn dự kiến hàng ngàn người dùng đồng thời, triển khai chiến lược thread‑pool và giám sát heap như mô tả trong phần tối ưu hoá hiệu suất.  

---

**Last Updated:** 2026-06-16  
**Tested With:** GroupDocs.Annotation 25.2 for Java  
**Author:** GroupDocs  

**Related Resources:**  
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - Tài liệu API toàn diện  
- [API Reference](https://reference.groupdocs.com/annotation/java/) - Tham chiếu chi tiết các phương thức và lớp  
- [Download Page](https://releases.groupdocs.com/annotation/java/) - Phiên bản mới nhất và ghi chú phát hành  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - Hỗ trợ cộng đồng và thảo luận  
- [Purchase Options](https://purchase.groupdocs.com/buy) - Thông tin về giấy phép thương mại  
- [Free Trial](https://releases.groupdocs.com/annotation/java/) - Dùng thử trước khi mua  
- [Temporary License](https://purchase.groupdocs.com/temporary-license/) - Giấy phép đánh giá mở rộng  

## Hướng dẫn liên quan

- [How to add arrow to pdf with Java – Complete Tutorial & Best Practices](/annotation/java/graphical-annotations/add-arrow-annotations-java-groupdocs/)  
- [Java PDF Image Annotation - Complete GroupDocs Tutorial](/annotation/java/image-annotations/annotate-pdfs-java-groupdocs-image-annotations/)  
- [Edit PDF Annotations Java - Complete GroupDocs Tutorial](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)