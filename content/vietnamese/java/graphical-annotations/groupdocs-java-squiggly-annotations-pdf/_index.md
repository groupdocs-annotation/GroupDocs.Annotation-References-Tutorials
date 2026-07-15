---
categories:
- Java Development
date: '2026-05-16'
description: Tìm hiểu cách tạo phản hồi chú thích java bằng GroupDocs.Annotation.
  Nắm vững việc chú thích PDF trong Java với các ví dụ thực tế, mẹo tối ưu hiệu năng
  và các thực tiễn tốt nhất.
keywords:
- create annotation reply java
- GroupDocs.Annotation Java
- PDF annotation Java tutorial
lastmod: '2026-05-16'
linktitle: Hướng dẫn chú thích PDF Java
schemas:
- author: GroupDocs
  dateModified: '2026-05-16'
  description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  headline: 'Java PDF Annotation Library: create annotation reply java'
  type: TechArticle
- description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  name: 'Java PDF Annotation Library: create annotation reply java'
  steps:
  - name: Import All Required Classes
    text: '- `Annotator` is the entry point for all document‑level operations. - `Point`
      represents a coordinate on a page (X and Y measured from the top‑left). - `SquigglyAnnotation`
      defines the wavy underline used to highlight errors. - `Reply` stores threaded
      comments attached to an annotation. - `SaveOptio'
  - name: Create and Configure Your Squiggly Annotation
    text: 'SquigglyAnnotation is a class that creates a wavy underline used to highlight
      errors in a PDF. - **Coordinate system**: Points start at the top‑left corner.
      The two points above draw a horizontal wavy line from (100, 200) to (300, 200).
      - **Opacity** 0.7 means the annotation is 70 % opaque, letting '
  - name: Add Interactive Replies (Optional but Powerful)
    text: Reply is a class representing a comment thread attached to an annotation.
      - Replies create a **threaded discussion** directly on the annotation, mirroring
      the experience of modern PDF reviewers. - Each reply stores author information
      and a timestamp, which you can later filter or display in a UI.
  - name: Apply Annotation and Save Document
    text: '- The **try‑with‑resources** construct automatically closes the `Annotator`,
      releasing file handles and native buffers. - `save` writes the modified PDF
      to `output.pdf`. > **Memory note:** The `Annotator` loads only the pages you
      touch. For multi‑hundred‑page PDFs, this approach keeps heap usage und'
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation focuses exclusively on annotation workflows, offering
      over 30 annotation types, threaded replies, and native support for 50 + file
      formats while keeping the memory footprint under 200 MB for 500‑page PDFs.
    question: What makes GroupDocs.Annotation better than other Java PDF libraries?
  - answer: Absolutely. Create a `@RestController` that injects the `Annotator` service,
      processes multipart uploads, and streams the annotated PDF back to the client.
      Remember to configure a thread‑pool for concurrent requests.
    question: Can I use this library with Spring Boot applications?
  - answer: Query each page’s dimensions via `annotator.getPageInfo(pageIndex)` and
      calculate relative coordinates (e.g., percentages) instead of hard‑coding point
      values. This ensures annotations appear correctly on A4, Letter, and custom‑size
      pages.
    question: How do I handle documents with different page sizes?
  - answer: Yes. Call `annotator.get()` to retrieve a collection of all annotations,
      then iterate to read properties such as author, comment, and geometry. This
      is useful for migration or analytics scenarios.
    question: Is there a way to extract existing annotations from PDFs?
  - answer: Implement authentication at the application layer, store the user ID with
      each `Reply`, and enforce business rules (e.g., only the author or an admin
      can edit or delete a reply). The API itself does not enforce permissions, giving
      you full flexibility.
    question: What's the best approach for handling annotation permissions in multi‑user
      systems?
  type: FAQPage
tags:
- pdf-annotations
- java-libraries
- document-processing
- groupdocs
title: 'Thư viện chú thích PDF Java: tạo phản hồi chú thích java'
type: docs
url: /vi/java/graphical-annotations/groupdocs-java-squiggly-annotations-pdf/
weight: 1
---

# Thư viện chú thích PDF Java: create annotation reply java

Nếu bạn cần **create annotation reply java** cho các tệp PDF—cho dù bạn đang xây dựng một cổng portal đánh giá hợp đồng, một hệ thống e‑learning, hoặc một quy trình xử lý hàng loạt—hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác với GroupDocs.Annotation cho Java. Chúng tôi sẽ hướng dẫn qua việc cài đặt, tạo chú thích squiggly, tạo chuỗi phản hồi, và tối ưu hiệu năng để bạn có thể triển khai giải pháp đáng tin cậy trong vài ngày, không phải vài tuần.

## Câu trả lời nhanh
- **Mục đích chính của GroupDocs.Annotation là gì?** Nó cho phép tạo, sửa đổi và trích xuất chú thích PDF một cách lập trình trong Java.  
- **Làm thế nào để thêm chú thích squiggly?** Khởi tạo `SquigglyAnnotation`, đặt hình học và kiểu dáng, sau đó gọi `annotator.add(...)`.  
- **Tôi có thể đính kèm phản hồi vào một chú thích không?** Có—tạo các đối tượng `Reply`, đặt tác giả và nội dung, và liên kết chúng với chú thích cha.  
- **Có cần giấy phép cho môi trường production không?** Chắc chắn; nếu không có giấy phép hợp lệ, đầu ra sẽ chứa watermark.  
- **Có phù hợp cho xử lý hàng loạt không?** Có—sử dụng try‑with‑resources để mở mỗi tài liệu, chú thích, và đóng lại, giữ mức sử dụng bộ nhớ thấp.

## Tại sao các nhà phát triển Java cần thư viện chú thích PDF
Việc đánh dấu PDF thủ công tốn thời gian và dễ gây lỗi, đặc biệt khi bạn phải xem xét hàng trăm hợp đồng hoặc bài thi. Một thư viện chú thích PDF cho Java tự động hoá công việc này, cho phép bạn nhúng các phần nổi bật, gạch chân squiggly và các bình luận dạng chuỗi trực tiếp trong tệp. Kết quả là một tài liệu có thể tìm kiếm, di động, giữ nguyên mọi chú thích mà không cần một trình xem riêng.

**Bạn sẽ nắm vững trong hướng dẫn này**
- Cài đặt và cấp phép GroupDocs.Annotation trong dự án Maven  
- Tạo các chú thích squiggly trông giống như gạch chân gốc của Word  
- Thêm phản hồi dạng chuỗi vào bất kỳ chú thích nào để đánh giá cộng tác  
- Tối ưu hóa việc sử dụng bộ nhớ và CPU khi xử lý các tệp PDF lớn  
- Triển khai giải pháp trong Spring Boot, micro‑services, hoặc ứng dụng desktop  

Cho dù bạn đang xây dựng hệ thống đánh giá tài liệu pháp lý, công cụ chấm điểm giáo dục, hoặc quy trình kiểm soát chất lượng tự động, các kỹ thuật dưới đây sẽ cung cấp cho bạn nền tảng sẵn sàng cho production.

## create annotation reply java là gì?
`create annotation reply java` là quá trình lập trình để gắn một chuỗi bình luận (một Reply) vào một chú thích PDF hiện có bằng Java. Các phản hồi cho phép nhiều người đánh giá thảo luận một đánh dấu cụ thể mà không rời tài liệu, tạo ra sự cộng tác liền mạch, ngay trong chỗ. Khả năng này biến một PDF tĩnh thành một nền tảng thảo luận tương tác, giữ nguyên ngữ cảnh và lịch sử kiểm tra trực tiếp trong tệp.

## Yêu cầu trước: Chuẩn bị môi trường của bạn
Trước khi chúng ta bắt đầu viết mã, hãy xác minh rằng máy làm việc phát triển của bạn đáp ứng các yêu cầu sau:

- **JDK** 8 hoặc cao hơn (JDK 11 + được khuyến nghị để có hiệu năng thu gom rác tốt hơn)  
- **Maven** hoặc **Gradle** để quản lý phụ thuộc (các ví dụ sử dụng Maven)  
- Một IDE hỗ trợ Maven (IntelliJ IDEA, Eclipse, hoặc VS Code)  
- Ít nhất **2 GB** RAM trống cho IDE và các lần chạy thử  
- Các tệp PDF mẫu để thử nghiệm (bạn có thể tạo PDF đơn giản bằng bất kỳ trình chỉnh sửa PDF nào)

GroupDocs.Annotation chạy hoàn toàn trong tiến trình; không cần trình xem PDF bên ngoài hay thư viện gốc.

## Cài đặt GroupDocs.Annotation cho Java
Việc tích hợp thư viện là một quy trình vài bước, nhưng một vài bẫy ẩn có thể gây lỗi thời gian chạy nếu bạn bỏ qua.

### Cấu hình phụ thuộc Maven
Thêm kho và phụ thuộc vào `pom.xml` của bạn. Đặt phần tử `<repositories>` **trước** `<dependencies>` để Maven có thể giải quyết artifact.

```xml
<repositories>
    <repository>
        <id>groupdocs-repo</id>
        <url>https://repo.groupdocs.com/repo</url>
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

> **Mẹo:** Kiểm tra trang phát hành của GroupDocs để biết phiên bản mới nhất. Các bản phát hành mới thường bao gồm hỗ trợ cho các tiêu chuẩn PDF mới nổi và cải thiện hiệu năng.

### Cài đặt giấy phép (Đừng bỏ qua!)
GroupDocs.Annotation yêu cầu tệp giấy phép cho việc sử dụng trong môi trường production. Nếu không, mọi PDF được tạo sẽ có watermark.

1. **Dùng thử miễn phí** – Bộ tính năng đầy đủ trong 30 ngày, lý tưởng để đánh giá.  
2. **Giấy phép tạm thời** – Thích hợp cho phát triển và kiểm thử nội bộ.  
3. **Giấy phép đầy đủ** – Yêu cầu cho bất kỳ triển khai thương mại nào.  

Đặt tệp `GroupDocs.Annotation.lic` vào thư mục resources và tải nó khi khởi động:

```java
License license = new License();
license.setLicense("GroupDocs.Annotation.lic");
```

> **Lỗi thường gặp:** Bỏ qua bước cấp giấy phép sẽ dẫn đến PDF có watermark và các cuộc gọi API thất bại mà không thông báo. Luôn xác thực giấy phép ngay trong quy trình khởi động.

## Hướng dẫn triển khai đầy đủ: Thêm chú thích Squiggly
Dưới đây là hướng dẫn chi tiết từng bước cho thấy cách **create annotation reply java** trong khi xây dựng một chú thích squiggly. Mỗi bước bao gồm giải thích ngắn gọn, giúp bạn hiểu “tại sao” đằng sau mỗi dòng.

### Bước 1: Nhập tất cả các lớp cần thiết
```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.annotation.SquigglyAnnotation;
import com.groupdocs.annotation.models.annotation.Reply;
import com.groupdocs.annotation.options.SaveOptions;
```

- `Annotator` là điểm vào cho tất cả các thao tác ở mức tài liệu.  
- `Point` đại diện cho một tọa độ trên trang (X và Y đo từ góc trên‑trái).  
- `SquigglyAnnotation` định nghĩa gạch chân gợn sóng dùng để đánh dấu lỗi.  
- `Reply` lưu trữ các bình luận dạng chuỗi gắn vào một chú thích.  
- `SaveOptions` cho phép bạn kiểm soát định dạng đầu ra và nén.

### Bước 2: Tạo và cấu hình chú thích Squiggly của bạn
```java
SquigglyAnnotation squiggly = new SquigglyAnnotation();
squiggly.setPageNumber(1);
squiggly.setColor(0xFFFF0000); // ARGB red
squiggly.setOpacity(0.7);
squiggly.setPoints(Arrays.asList(
    new Point(100, 200),
    new Point(300, 200)
));
```

SquigglyAnnotation là một lớp tạo gạch chân gợn sóng dùng để đánh dấu lỗi trong PDF.

- **Hệ thống tọa độ**: Các điểm bắt đầu từ góc trên‑trái. Hai điểm ở trên vẽ một đường gợn sóng ngang từ (100, 200) đến (300, 200).  
- **Độ trong suốt** 0.7 có nghĩa là chú thích có độ mờ 70 %, cho phép văn bản nền vẫn đọc được.

### Bước 3: Thêm phản hồi tương tác (Tùy chọn nhưng mạnh mẽ)
```java
Reply reply1 = new Reply();
reply1.setComment("Please double‑check this clause.");
reply1.setAuthor("Alice");
reply1.setCreatedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("I think the wording is correct.");
reply2.setAuthor("Bob");
reply2.setCreatedOn(new Date());

squiggly.setReplies(Arrays.asList(reply1, reply2));
```

`Reply` là một lớp đại diện cho một chuỗi bình luận gắn vào một chú thích.

- Các phản hồi tạo ra một **cuộc thảo luận dạng chuỗi** trực tiếp trên chú thích, phản ánh trải nghiệm của các công cụ xem PDF hiện đại.  
- Mỗi phản hồi lưu thông tin tác giả và dấu thời gian, bạn có thể lọc hoặc hiển thị trong giao diện người dùng.

### Bước 4: Áp dụng chú thích và lưu tài liệu
```java
try (Annotator annotator = new Annotator("input.pdf")) {
    annotator.add(squiggly);
    SaveOptions options = new SaveOptions();
    options.setOutputPath("output.pdf");
    annotator.save(options);
}
```

- Cấu trúc **try‑with‑resources** tự động đóng `Annotator`, giải phóng các handle tệp và bộ đệm gốc.  
- `save` ghi PDF đã chỉnh sửa vào `output.pdf`.

> **Ghi chú bộ nhớ:** `Annotator` chỉ tải các trang bạn thao tác. Đối với PDF hàng trăm trang, cách tiếp cận này giữ mức sử dụng heap dưới 150 MB trên máy chủ tiêu chuẩn.

## Tùy chọn cấu hình nâng cao

### Tùy chỉnh giao diện chú thích
Bạn có thể tinh chỉnh phong cách hiển thị để phù hợp với hướng dẫn thương hiệu của mình:

```java
squiggly.setBorderWidth(2);
squiggly.setColor(0xFF00FF00); // ARGB green
squiggly.setOpacity(0.5);
```

- **Độ rộng viền** kiểm soát độ dày đường (đơn vị point).  
- Định dạng **ARGB** bao gồm kênh alpha cho độ trong suốt.

### Định vị chú thích một cách chính xác
Việc xác định tọa độ chính xác có thể khó khăn trên các PDF có kích thước trang khác nhau. Thực hiện theo quy trình hệ thống này:

1. Mở PDF trong một trình xem (ví dụ, Adobe Acrobat) và ghi lại giá trị thước đo cho khu vực mục tiêu.  
2. Chuyển đổi giá trị thước đo sang point (1 point = 1/72 inch).  
3. Sử dụng `annotator.getPageInfo(pageIndex)` để lấy chiều rộng và chiều cao trang, sau đó tính vị trí tương đối.

## Các vấn đề thường gặp và giải pháp

### Vấn đề: Chú thích không hiển thị
**Nguyên nhân phổ biến nhất**
- Các điểm nằm ngoài giới hạn trang  
- Giấy phép chưa được tải (watermark ẩn chú thích)  
- Số trang sai (trang được đánh số bắt đầu từ 0 trong API)  

**Danh sách kiểm tra giải pháp**
```text
- Verify page dimensions with annotator.getPageInfo(pageIndex)
- Ensure all Point X/Y values are within [0, pageWidth] and [0, pageHeight]
- Confirm license file path and that license.setLicense() returns true
- Check that squiggly.setPageNumber(pageIndex) uses zero‑based indexing
```

### Vấn đề: Hiệu năng kém với tệp lớn
Tải một PDF 500 trang vào bộ nhớ có thể làm dịch vụ của bạn bị treo. Giảm thiểu bằng cách:

- **Xử lý một trang mỗi lần** – mở tài liệu, chú thích một trang, lưu, sau đó chuyển sang trang tiếp theo.  
- **Streaming** – sử dụng API streaming của `Annotator` để tránh bộ nhớ đệm toàn bộ tài liệu.  
- **Caching** – lưu các PDF thường truy cập trong bộ nhớ cache nhanh (ví dụ, Redis) và chú thích bản sao đã cache.

### Vấn đề: Giá trị màu không hoạt động
GroupDocs yêu cầu **ARGB** (Alpha, Red, Green, Blue) thay vì RGB thuần. Giá trị ARGB `0xFFFF0000` nghĩa là màu đỏ hoàn toàn không trong suốt. Nếu bạn cung cấp `0xFF0000` thư viện sẽ hiểu sai, dẫn đến chú thích màu đen.

```java
int argbRed = 0xFFFF0000; // Alpha=255, Red=255, Green=0, Blue=0
squiggly.setColor(argbRed);
```

## Các thực hành tốt về hiệu năng

### Quản lý bộ nhớ
Khi chú thích hàng chục PDF trong một công việc batch, bao bọc mỗi tệp trong một khối try‑with‑resources riêng:

```java
for (String filePath : pdfList) {
    try (Annotator annotator = new Annotator(filePath)) {
        // add annotations
        annotator.save(new SaveOptions().setOutputPath(filePath.replace(".pdf", "_annotated.pdf")));
    }
}
```

- Mẫu này đảm bảo các bộ đệm gốc được giải phóng sau mỗi vòng lặp, ngăn ngừa **OutOfMemoryError** trong các quy trình chạy lâu.

### Tối ưu hoá xử lý batch
Đối với môi trường thông lượng cao, cân nhắc sử dụng parallel streams kết hợp với một pool thread có giới hạn:

```java
ExecutorService executor = Executors.newFixedThreadPool(Runtime.getRuntime().availableProcessors());
pdfList.parallelStream().forEach(path -> executor.submit(() -> annotateDocument(path)));
executor.shutdown();
executor.awaitTermination(1, TimeUnit.HOURS);
```

- **Pool có giới hạn** tránh việc tạo quá nhiều thread, trong khi parallel streams giữ các lõi CPU bận rộn.

### Lưu ý về kích thước tệp
Các PDF lớn (> 100 MB) có thể làm giảm hiệu năng. Áp dụng các chiến lược sau:

- **Tiền nén** PDF nguồn bằng công cụ như Ghostscript trước khi chú thích.  
- **Chỉ chú thích các trang cần thiết** – bỏ qua các trang không cần chú thích.  
- **Chia** tài liệu thành các phần logic (ví dụ, theo chương) và xử lý từng phần độc lập.

## Ứng dụng thực tế

### Hệ thống đánh giá tài liệu
Các công ty luật thường cần đánh dấu các điều khoản có vấn đề. Chú thích squiggly kết hợp với phản hồi dạng chuỗi cho phép nhiều luật sư thảo luận một đoạn văn duy nhất mà không rời PDF:

- **Luật sư A** thêm một gạch chân squiggly màu đỏ dưới một điều khoản và viết “Cụm từ mơ hồ”.  
- **Luật sư B** phản hồi “Thêm định nghĩa cho ‘vi phạm nghiêm trọng’”.  
- Toàn bộ cuộc thảo luận được nhúng, có thể tìm kiếm và kiểm toán.

### Tích hợp với các hệ thống hiện có
GroupDocs.Annotation hoạt động mượt mà với các framework Java phổ biến:

- **Spring Boot** – cung cấp endpoint REST `/api/annotate` nhận tải lên PDF dạng multipart, thêm chú thích và truyền lại kết quả.  
- **JSF** – liên kết các hành động chú thích với các thành phần UI để đánh dấu ngay trong view web.  
- **Microservices** – kích thước nhỏ của thư viện (< 15 MB) cho phép bạn container hoá với Docker và mở rộng theo chiều ngang.

### Tự động hoá quy trình làm việc
Kết hợp chú thích với các sản phẩm GroupDocs khác (ví dụ, GroupDocs.Signature) để xây dựng quy trình end‑to‑end:

```text
1. Upload contract → 2. Auto‑apply squiggly for missing signatures → 3. Add reviewer replies → 4. Route to signing service.
```

## Khi nào nên sử dụng chú thích Squiggly so với các lựa chọn khác
| Trường hợp sử dụng | Chú thích đề xuất |
|--------------------|-------------------|
| Đánh dấu lỗi chính tả hoặc ngữ pháp | **Squiggly** – dấu hiệu trực quan giống như trình xử lý văn bản |
| Tô sáng các phần quan trọng mà không ngụ ý lỗi | **Highlight** – lớp phủ trong suốt |
| Cung cấp phản hồi chi tiết | **Text** hoặc **Comment** – hộp ghi chú tự do |
| Phê duyệt hoặc từ chối tài liệu | **Stamp** – huy hiệu “Approved” hoặc “Rejected” |

## Kết luận
Bây giờ bạn đã có một công thức hoàn chỉnh, sẵn sàng cho production cho **create annotation reply java** sử dụng GroupDocs.Annotation. Bằng cách nắm vững API, xử lý giấy phép, và áp dụng các mẹo hiệu năng ở trên, bạn có thể:

- Tự động đánh dấu lỗi trên hàng ngàn PDF  
- Kích hoạt các cuộc thảo luận dạng chuỗi cộng tác ngay trong tệp  
- Giữ mức sử dụng bộ nhớ thấp ngay cả khi xử lý các tài liệu khổng lồ  

**Các bước tiếp theo**
1. Thử nghiệm các loại chú thích khác (highlight, stamp, text).  
2. Xây dựng dịch vụ REST nhận PDF, chú thích và trả về kết quả.  
3. Khám phá API trích xuất (`annotator.get()`) để lấy các bình luận hiện có cho mục đích phân tích.  

Sức mạnh của việc chú thích PDF bằng lập trình nằm ở khả năng thay thế việc đánh dấu thủ công tẻ nhạt bằng mã lặp lại, có thể kiểm toán. Dù bạn đang xây dựng một sản phẩm legal‑tech chuyên biệt hay một engine quy trình tài liệu đa năng, các kỹ thuật trong hướng dẫn này cung cấp cho bạn nền tảng vững chắc để tiến bước.

## Câu hỏi thường gặp

**Q: Điều gì khiến GroupDocs.Annotation tốt hơn các thư viện PDF Java khác?**  
A: GroupDocs.Annotation tập trung riêng vào quy trình chú thích, cung cấp hơn 30 loại chú thích, phản hồi dạng chuỗi, và hỗ trợ gốc cho hơn 50 định dạng tệp trong khi giữ dung lượng bộ nhớ dưới 200 MB cho PDF 500 trang.

**Q: Tôi có thể sử dụng thư viện này với các ứng dụng Spring Boot không?**  
A: Chắc chắn. Tạo một `@RestController` tiêm dịch vụ `Annotator`, xử lý tải lên multipart, và truyền lại PDF đã chú thích cho client. Nhớ cấu hình thread‑pool cho các yêu cầu đồng thời.

**Q: Làm thế nào để xử lý tài liệu có kích thước trang khác nhau?**  
A: Truy vấn kích thước mỗi trang qua `annotator.getPageInfo(pageIndex)` và tính toán tọa độ tương đối (ví dụ, phần trăm) thay vì mã cứng giá trị point. Điều này đảm bảo chú thích hiển thị đúng trên các trang A4, Letter và kích thước tùy chỉnh.

**Q: Có cách nào để trích xuất các chú thích hiện có từ PDF không?**  
A: Có. Gọi `annotator.get()` để lấy bộ sưu tập tất cả các chú thích, sau đó lặp để đọc các thuộc tính như tác giả, bình luận và hình học. Điều này hữu ích cho các kịch bản di chuyển hoặc phân tích.

**Q: Cách tiếp cận tốt nhất để xử lý quyền chú thích trong hệ thống đa người dùng là gì?**  
A: Thực hiện xác thực ở lớp ứng dụng, lưu ID người dùng cùng mỗi `Reply`, và áp dụng quy tắc kinh doanh (ví dụ, chỉ tác giả hoặc admin mới có thể chỉnh sửa hoặc xóa phản hồi). API không tự động áp dụng quyền, cho bạn toàn quyền tùy chỉnh.

**Q: Làm thế nào để tối ưu hóa việc sử dụng bộ nhớ khi xử lý hàng trăm PDF?**  
A: Sử dụng try‑with‑resources cho mỗi tài liệu, xử lý từng trang riêng biệt, và cân nhắc sử dụng thread pool có giới hạn để hạn chế tiêu thụ bộ nhớ đồng thời. Giám sát heap JVM bằng các công cụ như VisualVM giúp bạn tinh chỉnh thiết lập `-Xmx`.

**Cập nhật lần cuối:** 2026-05-16  
**Kiểm thử với:** GroupDocs.Annotation 25.2 for Java  
**Tác giả:** GroupDocs  

**Tài nguyên bổ sung**

- [Tài liệu GroupDocs.Annotation cho Java](https://docs.groupdocs.com/annotation/java/)
- [Tham chiếu API đầy đủ](https://reference.groupdocs.com/annotation/java/)

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}

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

```java
import com.groupdocs.annotation.Annotator;

// Initialize your annotator - this is your entry point to all annotation features
try (Annotator annotator = new Annotator("path/to/your/document.pdf")) {
    // All your annotation magic happens here
    System.out.println("Annotator initialized successfully!");
}
```

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.annotationmodels.SquigglyAnnotation;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;
```

```java
// Create a new SquigglyAnnotation instance
SquigglyAnnotation squigglyAnnotation = new SquigglyAnnotation();

// Set the creation date of the annotation
squigglyAnnotation.setCreatedOn(new Date());

// Define font and background colors using RGB values
squigglyAnnotation.setFontColor(65535); // Yellow color in ARGB format
squigglyAnnotation.setBackgroundColor(16761035); // Light blue color in ARGB format

// Set a message to display with the annotation
squigglyAnnotation.setMessage("This is squiggly annotation");

// Define opacity (range 0.0 - 1.0)
squigglyAnnotation.setOpacity(0.7);

// Specify the page number for the annotation (zero-based index)
squigglyAnnotation.setPageNumber(0);

// Set squiggly line color specific to Word and PDF documents
squigglyAnnotation.setSquigglyColor(1422623); // Color code for squiggly lines

// Define points marking the start and end of the annotation on the page
List<Point> points = new ArrayList<>();
points.add(new Point(80, 730));
points.add(new Point(240, 730));
points.add(new Point(80, 650));
points.add(new Point(240, 650));
squigglyAnnotation.setPoints(points);
```

```java
// Create replies to the annotation (optional)
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(new Date());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);

// Associate replies with the annotation
squigglyAnnotation.setReplies(replies);
```

```java
try (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Add the prepared squiggly annotation to the document
    annotator.add(squigglyAnnotation);
    
    // Save the annotated document
    annotator.save("YOUR_OUTPUT_DIRECTORY/result_squiggly_annotation.pdf");
}
```

```java
// Custom color configurations
squigglyAnnotation.setFontColor(0xFF0000); // Red text
squigglyAnnotation.setBackgroundColor(0x00FF00); // Green background
squigglyAnnotation.setSquigglyColor(0x0000FF); // Blue squiggly line

// Transparency effects
squigglyAnnotation.setOpacity(0.3); // Very subtle
// or
squigglyAnnotation.setOpacity(0.9); // Almost opaque
```

```java
// Verify your points are within page boundaries
System.out.println("Page dimensions: " + annotator.getPageInfo(0));

// Check if your points make sense
List<Point> points = squigglyAnnotation.getPoints();
for (Point point : points) {
    System.out.println("Point: (" + point.getX() + ", " + point.getY() + ")");
}
```

```java
// Wrong: RGB format
int wrongColor = 0xFF0000; // This might not work as expected

// Right: ARGB format
int rightColor = 0xFFFF0000; // Full opacity red
```

```java
// Good practice: Use try-with-resources
try (Annotator annotator = new Annotator(inputPath)) {
    // Process annotations
    annotator.add(annotation);
    annotator.save(outputPath);
} // Automatic cleanup happens here

// Avoid: Manual resource management
Annotator annotator = new Annotator(inputPath); // Resources might leak
```

```java
public void processBatch(List<String> documentPaths) {
    for (String path : documentPaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Process each document independently
            addAnnotations(annotator);
            annotator.save(getOutputPath(path));
        } catch (Exception e) {
            // Handle individual document failures without stopping the batch
            System.err.println("Failed to process: " + path + " - " + e.getMessage());
        }
    }
}
```

```java
public class DocumentWorkflow {
    public void reviewDocument(String documentPath, ReviewLevel level) {
        try (Annotator annotator = new Annotator(documentPath)) {
            switch (level) {
                case GRAMMAR_CHECK:
                    addGrammarAnnotations(annotator);
                    break;
                case LEGAL_REVIEW:
                    addLegalAnnotations(annotator);
                    break;
                case FINAL_PROOF:
                    addProofreadingAnnotations(annotator);
                    break;
            }
            annotator.save(getReviewedPath(documentPath));
        }
    }
}
```

## Related Tutorials

- [Java PDF Annotation Library Tutorial](/annotation/java/reply-management/java-annotator-groupdocs-pdf-annotations-replies/)
- [Remove Annotation Replies Java - Manage Replies by ID with GroupDocs.Annotation](/annotation/java/annotation-management/java-groupdocs-annotation-remove-replies-by-id/)
- [Edit PDF Annotations Java - Complete GroupDocs Tutorial](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)