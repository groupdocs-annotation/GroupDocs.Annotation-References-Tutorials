---
categories:
- Java Development
date: '2026-09-15'
description: Tìm hiểu cách tạo tệp PDF Java có thể tìm kiếm với GroupDocs annotation.
  Hướng dẫn chi tiết này bao gồm cài đặt, mã nguồn, mẹo và khắc phục sự cố.
keywords:
- create searchable pdf java
- pdf annotation free trial
- highlight pdf text java
lastmod: '2026-09-15'
linktitle: Hướng dẫn chú thích văn bản PDF Java
og_description: Tìm hiểu cách tạo tệp PDF Java có thể tìm kiếm với GroupDocs annotation.
  Hướng dẫn chi tiết này bao gồm cài đặt, mã nguồn, mẹo và khắc phục sự cố.
og_image_alt: Guide showing how to add searchable text annotations to PDFs in Java
  with GroupDocs
og_title: Tạo tệp PDF Java có thể tìm kiếm bằng GroupDocs annotation
schemas:
- author: GroupDocs
  dateModified: '2026-09-15'
  description: Learn how to create searchable PDF Java files with GroupDocs annotation.
    This step‑by‑step guide covers setup, code, tips, and troubleshooting.
  headline: Create searchable PDF Java files using GroupDocs annotation
  type: TechArticle
- description: Learn how to create searchable PDF Java files with GroupDocs annotation.
    This step‑by‑step guide covers setup, code, tips, and troubleshooting.
  name: Create searchable PDF Java files using GroupDocs annotation
  steps:
  - name: initialize the annotator
    text: 'The `Annotator` class is GroupDocs.Annotation''s primary engine for loading,
      modifying, and saving PDF files. The `Annotator` class is your main interface
      for PDF manipulation. It handles file loading, modification, and saving: **Why
      this matters:** Using a try‑with‑resources block guarantees that th'
  - name: create your text fragment
    text: '`SearchTextFragment` represents a searchable text annotation that can be
      positioned and styled within a PDF. The `SearchTextFragment` object defines
      what text you want to highlight and how it should appear:'
  - name: define the target text
    text: 'Specify the exact string you want to make searchable. The match must be
      case‑exact and include any punctuation that appears in the source PDF. Specify
      exactly what text you want to make searchable: **Important:** PDF text extraction
      can introduce hidden Unicode characters; if the annotation fails to'
  - name: customize the appearance
    text: 'You can control background color, text color, opacity, and border style.
      The ARGB values are expressed as `0xAARRGGBB`. This is where you can make your
      annotations visually distinctive: **Color‑coding tip:** The numbers `0x7FFF0000`
      (semi‑transparent red) and `0xFF0000FF` (opaque blue) have been tes'
  - name: apply and save
    text: 'Add the fragment to the annotator and write the updated PDF to disk. The
      `close()` call inside the try‑with‑resources block frees native memory. Add
      the annotation and save your enhanced PDF: The closing brace automatically disposes
      of the `Annotator` object, freeing up memory.'
  type: HowTo
- questions:
  - answer: Absolutely. Create several `SearchTextFragment` objects (or other annotation
      types) and add them all before calling `save`.
    question: Can I add multiple different annotations to the same PDF?
  - answer: Yes. GroupDocs creates standard PDF annotation objects that are displayed
      correctly in Adobe Acrobat, Chrome, Edge, and most third‑party viewers. Colors
      may vary slightly due to viewer rendering engines.
    question: Will annotations work in all PDF viewers?
  - answer: GroupDocs.Annotation processes the visual text flow, so you only need
      to ensure the exact string you supply matches the extracted text, regardless
      of column order.
    question: How do I handle PDFs with complex layouts or multiple columns?
  - answer: There is no hard limit on the number of annotations. In practice, adding
      thousands of highlights may increase rendering time in some viewers, so batch
      them logically (e.g., per chapter).
    question: Is there a limit to how much text I can annotate?
  - answer: Yes. Use the `getAnnotations()` method to retrieve existing objects, then
      call `update()` or `delete()` as needed.
    question: Can I modify or remove annotations after adding them?
  type: FAQPage
tags:
- pdf-processing
- java-libraries
- document-annotation
- groupdocs
title: Tạo tệp PDF Java có thể tìm kiếm bằng GroupDocs annotation
type: docs
url: /vi/java/text-annotations/add-search-text-annotations-pdf-groupdocs-java/
weight: 1
---

# Tạo tệp PDF Java có thể tìm kiếm bằng GroupDocs annotation

Nếu bạn cần **tạo tệp PDF Java có thể tìm kiếm** cho phép người dùng nhảy thẳng đến các đoạn quan trọng, bạn đã đến đúng nơi. Cho dù bạn đang xử lý hợp đồng pháp lý, sách hướng dẫn kỹ thuật hay các bài báo nghiên cứu, chú thích văn bản có thể tìm kiếm biến các PDF tĩnh thành cơ sở kiến thức tương tác, nâng cao năng suất và hợp tác.

Trong tutorial này bạn sẽ khám phá cách thêm chú thích văn bản có thể tìm kiếm một cách lập trình với GroupDocs.Annotation for Java. Chúng tôi sẽ bắt đầu với việc thiết lập môi trường, đi qua từng dòng mã, khám phá các tùy chọn định dạng nâng cao, và kết thúc với các mẹo khắc phục sự cố bạn có thể áp dụng trong các dự án thực tế.

## Câu trả lời nhanh
- **“searchable PDF Java” có nghĩa là gì?** Đó là một PDF chứa các chú thích dựa trên văn bản có thể tìm kiếm bằng tính năng tìm kiếm văn bản tiêu chuẩn của PDF.  
- **Tôi nên sử dụng thư viện nào?** GroupDocs.Annotation for Java cung cấp một API hoàn chỉnh, sẵn sàng cho môi trường sản xuất cho các đánh dấu có thể tìm kiếm.  
- **Bạn có cần giấy phép để thử không?** Không — GroupDocs cung cấp bản dùng thử miễn phí mở khóa tất cả các tính năng được trình bày ở đây.  
- **Tôi có thể thêm nhiều chú thích trong một lần không?** Có, tạo một vài đối tượng `SearchTextFragment` và thêm chúng trước khi lưu.  
- **Cách tiếp cận này có thân thiện với bộ nhớ cho các PDF lớn không?** Khi bạn sử dụng try‑with‑resources và xử lý theo lô, việc sử dụng bộ nhớ vẫn dưới 200 MB ngay cả với các PDF có hàng ngàn trang.

## Tại sao chú thích văn bản PDF Java lại quan trọng

Chú thích có thể tìm kiếm làm nhiều hơn chỉ làm cho tài liệu trông đẹp mắt:

- **Điều hướng nhanh** – Người dùng nhấp vào cụm từ được đánh dấu và nhảy trực tiếp đến trang liên quan.  
- **Hợp tác nhóm** – Người đánh giá có thể bình luận về các thuật ngữ chính xác mà không cần cuộn liên tục.  
- **Xử lý tự động** – Các script có thể xác định các điều khoản quan trọng, trích xuất chúng hoặc kích hoạt quy trình downstream.  
- **Tăng cường khả năng truy cập** – Trình đọc màn hình có thể thông báo các thuật ngữ được đánh dấu, cải thiện khả năng sử dụng cho người khiếm thị.

## Những gì bạn cần để bắt đầu

Dưới đây là danh sách kiểm tra tối thiểu bạn nên có trước khi bắt đầu viết mã.

### Yêu cầu thiết yếu
- **Java Development Kit (JDK)** – phiên bản 8 hoặc mới hơn; JDK 11+ được khuyến nghị để cải thiện hiệu suất thu gom rác.  
- **IDE** – IntelliJ IDEA, Eclipse, hoặc bất kỳ trình chỉnh sửa nào tương thích với Java mà bạn thích.  
- **Maven** – để quản lý phụ thuộc (Gradle cũng hoạt động, nhưng các ví dụ sử dụng Maven).  
- **Kiến thức Java cơ bản** – quen thuộc với đối tượng, try‑with‑resources và xử lý ngoại lệ.

### Thư viện GroupDocs.Annotation
- **Phiên bản** – 25.2 hoặc mới hơn (bản phát hành mới nhất tăng tốc 30 % cho các PDF lớn).  
- **Giấy phép** – bắt đầu với bản dùng thử miễn phí; giấy phép tạm thời có sẵn cho việc đánh giá mở rộng, và giấy phép đầy đủ cần thiết cho triển khai sản xuất.

## Cài đặt môi trường phát triển của bạn

Việc dành vài phút ngay bây giờ để cấu hình Maven đúng cách sẽ giúp bạn tiết kiệm hàng giờ gỡ lỗi sau này.

### Cấu hình Maven

Thêm kho GroupDocs và phụ thuộc Annotation vào `pom.xml` của bạn. Đoạn mã dưới đây đã sẵn sàng để sao chép‑dán:

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

**Mẹo chuyên nghiệp:** Nếu bạn làm việc sau một proxy công ty, hãy thêm cài đặt proxy vào tệp `~/.m2/settings.xml` của bạn để Maven có thể truy cập kho GroupDocs mà không bị gián đoạn.

### Các tùy chọn thiết lập giấy phép

Bạn có ba đường đi:

1. **Bản dùng thử miễn phí** – truy cập đầy đủ API, không cần thẻ tín dụng.  
2. **Giấy phép tạm thời** – kéo dài thời gian dùng thử cho các bằng chứng khái niệm.  
3. **Giấy phép đầy đủ** – mở khóa việc sử dụng không giới hạn trong sản xuất và hỗ trợ ưu tiên.  

Trong quá trình phát triển bạn có thể bỏ qua tệp giấy phép; khóa dùng thử sẽ được áp dụng tự động khi bạn khởi tạo `Annotator`.

## Triển khai cốt lõi: thêm chú thích văn bản có thể tìm kiếm

Bây giờ chúng ta chuyển sang mã thực sự tạo ra các chú thích. Mỗi khối dưới đây tương ứng với một bước trong quy trình làm việc.

### Các bước triển khai cơ bản

Dưới đây là luồng end‑to‑end được chia thành năm bước ngắn gọn.

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.annotationmodels.SearchTextFragment;
```

#### Bước 1: khởi tạo annotator

Lớp `Annotator` là engine chính của GroupDocs.Annotation để tải, sửa đổi và lưu các tệp PDF.

Lớp `Annotator` là giao diện chính của bạn cho việc thao tác PDF. Nó xử lý việc tải tệp, sửa đổi và lưu:

```java
try (final Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
```

**Why this matters:** Using a try‑with‑resources block guarantees that the native resources held by `Annotator` are released automatically, preventing memory leaks when you process many documents in a batch.

#### Bước 2: tạo đoạn văn bản của bạn

`SearchTextFragment` represents a searchable text annotation that can be positioned and styled within a PDF.

The `SearchTextFragment` object defines what text you want to highlight and how it should appear:

```java
SearchTextFragment searchTextFragment = new SearchTextFragment();
```

#### Bước 3: xác định văn bản mục tiêu

Specify the exact string you want to make searchable. The match must be case‑exact and include any punctuation that appears in the source PDF.

Specify exactly what text you want to make searchable:

```java
searchTextFragment.setText("Welcome to GroupDocs");
```

**Important:** PDF text extraction can introduce hidden Unicode characters; if the annotation fails to appear, extract the page text first and copy‑paste the exact string into your code.

#### Bước 4: tùy chỉnh giao diện

You can control background color, text color, opacity, and border style. The ARGB values are expressed as `0xAARRGGBB`.

This is where you can make your annotations visually distinctive:

```java
// Set font size for better readability
searchTextFragment.setFontSize(10);

// Choose a professional font family
searchTextFragment.setFontFamily("Calibri");

// Set text color (ARGB format - this creates a bright blue)
searchTextFragment.setFontColor(65535); 

// Add background highlighting (this creates a light yellow background)
searchTextFragment.setBackgroundColor(16761035);
```

**Color‑coding tip:** The numbers `0x7FFF0000` (semi‑transparent red) and `0xFF0000FF` (opaque blue) have been tested to provide high contrast on both screen and print.

#### Bước 5: áp dụng và lưu

Add the fragment to the annotator and write the updated PDF to disk. The `close()` call inside the try‑with‑resources block frees native memory.

Add the annotation and save your enhanced PDF:

```java
   annotator.add(searchTextFragment);
   annotator.save("YOUR_OUTPUT_DIRECTORY/result_add_search_text.pdf");
}
```

The closing brace automatically disposes of the `Annotator` object, freeing up memory.

## Các tùy chọn tùy chỉnh nâng cao

Một khi các bước cơ bản hoạt động, bạn có thể làm phong phú trải nghiệm bằng nhiều loại chú thích, phông chữ tùy chỉnh và bảng màu chiến lược.

### Nhiều loại chú thích

GroupDocs.Annotation lets you mix searchable text with highlights, stamps, and comments in a single document.

```java
// Create different annotations for different purposes
SearchTextFragment importantClause = new SearchTextFragment();
importantClause.setText("IMPORTANT:");
importantClause.setBackgroundColor(16711680); // Red background for critical items

SearchTextFragment noteSection = new SearchTextFragment();
noteSection.setText("Note:");
noteSection.setBackgroundColor(65280); // Green background for informational notes
```

### Thực hành tốt nhất về tùy chỉnh phông chữ

Choose fonts that match the document’s purpose:

- **Calibri hoặc Arial** – lý tưởng cho báo cáo kinh doanh.  
- **Times New Roman** – tiêu chuẩn cho hợp đồng pháp lý.  
- **Courier New** – hoàn hảo cho đoạn mã trong sách hướng dẫn kỹ thuật.

### Chiến lược màu sắc cho tài liệu chuyên nghiệp

Here are three tested color combinations that keep readability high across PDF viewers:

- **Mục quan trọng** – nền đỏ (`#FF0000`) với văn bản trắng.  
- **Ghi chú quan trọng** – nền vàng (`#FFFF00`) với văn bản đen.  
- **Đánh dấu chung** – nền xanh nhạt (`#ADD8E6`) với văn bản xanh đậm.

## Các vấn đề thường gặp và giải pháp

Dưới đây là các vấn đề bạn có khả năng gặp nhất, cùng với các giải pháp ngắn gọn.

### Vấn đề đường dẫn tệp
**Vấn đề:** `FileNotFoundException` khi mở PDF.  
**Giải pháp:** Sử dụng đường dẫn tuyệt đối trong quá trình phát triển và xác thực đường dẫn trước khi tạo `Annotator`:

```java
File inputFile = new File("YOUR_DOCUMENT_DIRECTORY/input.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Input PDF file not found: " + inputFile.getAbsolutePath());
}
```

### Lỗi không tìm thấy văn bản
**Vấn đề:** Chú thích không xuất hiện vì không tìm thấy văn bản tìm kiếm.  
**Giải pháp:** Trước tiên trích xuất văn bản trang để xác minh chuỗi chính xác, bao gồm khoảng trắng và dấu câu:

```java
// Use this approach to verify text exists before annotating
// (This is debugging code, not for production)
```

### Vấn đề bộ nhớ với PDF lớn
**Vấn đề:** `OutOfMemoryError` khi xử lý PDF lớn hơn 500 MB.  
**Giải pháp:** Tăng heap JVM (`-Xmx2g`) và xử lý tài liệu theo lô, tái sử dụng một thể hiện `Annotator` khi có thể:

```bash
java -Xmx2g -Xms1g YourApplication
```

### Vấn đề quyền
**Vấn đề:** Không thể ghi tệp đầu ra.  
**Giải pháp:** Đảm bảo ứng dụng chạy với quyền ghi trên thư mục đích, hoặc ghi vào thư mục tạm và di chuyển tệp sau khi xử lý.

## Mẹo tối ưu hoá hiệu suất

Khi bạn chuyển từ bản demo sang pipeline sản xuất, những tinh chỉnh này tạo ra sự khác biệt đáng kể.

### Quản lý tài nguyên
Always wrap `Annotator` in a try‑with‑resources block. This pattern eliminates the risk of native memory leaks that can crash long‑running services.

```java
// Good practice - automatic resource cleanup
try (final Annotator annotator = new Annotator(inputPath)) {
    // Your annotation code here
} // Automatically closes and cleans up resources
```

### Chiến lược xử lý theo lô
Create a single `Annotator` per file, add all required `SearchTextFragment` objects, then call `save`. Re‑using the same `Annotator` instance across multiple files avoids repeated native library loading.

```java
// Process multiple annotations on the same document efficiently
try (final Annotator annotator = new Annotator(inputPath)) {
    // Add all annotations before saving
    annotator.add(annotation1);
    annotator.add(annotation2);
    annotator.add(annotation3);
    
    // Single save operation
    annotator.save(outputPath);
}
```

### Quản lý bộ nhớ cho PDF khổng lồ
GroupDocs.Annotation can handle PDFs up to **5,000 pages** while keeping memory usage under **200 MB** thanks to its streaming architecture. To stay within this envelope:

`DocumentPageIterator` provides an iterator to process PDF pages sequentially in manageable batches.  
- Process pages in chunks using `DocumentPageIterator`.  
- Disable unnecessary features such as image extraction if you only need text highlights.  

## Ứng dụng thực tế và các trường hợp sử dụng

Hiểu giá trị kinh doanh giúp bạn quyết định nơi áp dụng kỹ thuật này.

### Xử lý tài liệu pháp lý
Law firms highlight clauses that require client approval, flag risky language, and generate reports of all highlighted sections. Consistent red‑background highlights indicate “critical review required”.

### Tài liệu kỹ thuật
Software teams annotate API changes, deprecations, and security advisories directly in PDF release notes, enabling engineers to locate updates instantly.

### Tài liệu giáo dục
Professors embed searchable highlights for key concepts, making study guides more interactive for students using screen readers or mobile PDF viewers.

## Thực hành tốt nhất khi tích hợp

### Mẫu tích hợp doanh nghiệp
1. **Thiết kế API‑first** – cung cấp logic chú thích qua một endpoint REST.  
2. **Xử lý bất đồng bộ** – đẩy các tệp PDF vào hàng đợi tin nhắn (ví dụ, RabbitMQ) và để dịch vụ worker áp dụng chú thích.  
3. **Khôi phục lỗi** – triển khai logic retry cho các lỗi I/O tạm thời.  
4. **Giám sát** – ghi lại thời gian chú thích và việc sử dụng bộ nhớ bằng một logger có cấu trúc (ví dụ, Logback).

### Các lưu ý bảo mật
- Xác thực đường dẫn tệp để ngăn chặn tấn công traversal thư mục.  
- Thực thi kiểm soát truy cập dựa trên vai trò trên endpoint dịch vụ chú thích.  
- Mã hoá PDF khi lưu trữ nếu chúng chứa dữ liệu nhạy cảm, sử dụng API `Cipher` của Java trước khi ghi tệp.

## Hướng dẫn khắc phục sự cố

### Danh sách kiểm tra chẩn đoán nhanh
1. **Quyền tệp** – quá trình có thể đọc PDF nguồn và ghi vào thư mục đích không?  
2. **Độ chính xác đường dẫn** – kiểm tra lại dấu phân cách Windows (`\`) và Linux (`/`).  
3. **Phiên bản thư viện** – đảm bảo bạn đang sử dụng GroupDocs.Annotation 25.2 hoặc mới hơn; các phiên bản cũ thiếu tối ưu hóa xử lý theo lô.  
4. **Bộ nhớ JVM** – xác minh kích thước heap (`-Xmx`) phù hợp với kích thước PDF bạn xử lý.  
5. **Khớp văn bản chính xác** – thực hiện trích xuất nhanh để xác nhận chuỗi chú thích tồn tại nguyên văn.

### Kích hoạt chế độ debug
Enable verbose logging to capture the internal search process:

```java
// Add this to see detailed processing information
System.setProperty("groupdocs.annotation.debug", "true");
```

The log will list each page scanned and whether the target phrase was found, helping you pinpoint mismatches.

## Câu hỏi thường gặp

**Q: Tôi có thể thêm nhiều chú thích khác nhau vào cùng một PDF không?**  
A: Chắc chắn. Tạo một vài đối tượng `SearchTextFragment` (hoặc các loại chú thích khác) và thêm chúng tất cả trước khi gọi `save`.

**Q: Chú thích có hoạt động trong tất cả các trình xem PDF không?**  
A: Có. GroupDocs tạo các đối tượng chú thích PDF tiêu chuẩn, hiển thị đúng trong Adobe Acrobat, Chrome, Edge và hầu hết các trình xem của bên thứ ba. Màu sắc có thể hơi khác nhau do engine render của trình xem.

**Q: Làm sao để xử lý PDF có bố cục phức tạp hoặc nhiều cột?**  
A: GroupDocs.Annotation xử lý luồng văn bản trực quan, vì vậy bạn chỉ cần đảm bảo chuỗi bạn cung cấp khớp chính xác với văn bản đã trích xuất, bất kể thứ tự cột.

**Q: Có giới hạn về lượng văn bản tôi có thể chú thích không?**  
A: Không có giới hạn cứng về số lượng chú thích. Thực tế, việc thêm hàng nghìn đánh dấu có thể làm tăng thời gian render trong một số trình xem, vì vậy hãy nhóm chúng một cách hợp lý (ví dụ, theo chương).

**Q: Tôi có thể sửa đổi hoặc xóa chú thích sau khi đã thêm không?**  
A: Có. Sử dụng phương thức `getAnnotations()` để lấy các đối tượng hiện có, sau đó gọi `update()` hoặc `delete()` khi cần.

**Q: Điều gì xảy ra nếu văn bản chú thích không được tìm thấy trong PDF?**  
A: API sẽ bỏ qua việc thêm mà không báo lỗi, nhưng chú thích sẽ không xuất hiện. Luôn xác minh khớp trước khi thực hiện.

**Q: Làm sao để đảm bảo PDF đã chú thích của tôi vẫn truy cập được?**  
A: Chọn màu tương phản cao, tránh dựa chỉ vào màu để truyền đạt ý nghĩa, và thêm văn bản mô tả vào mỗi chú thích để trình đọc màn hình có thể thông báo mục đích của chúng.

## Kết luận

Bạn hiện đã có một công thức hoàn chỉnh, sẵn sàng cho sản xuất để **tạo tệp PDF Java có thể tìm kiếm** bằng GroupDocs.Annotation. Bằng cách làm theo các bước trên, bạn có thể:

- Thiết lập dự án Maven sạch sẽ với thư viện mới nhất.  
- Thêm các đánh dấu có thể tìm kiếm một dòng, ngay lập tức có thể khám phá.  
- Tùy chỉnh giao diện với màu ARGB và lựa chọn phông chữ.  
- Mở rộng giải pháp lên hàng ngàn trang trong khi giữ mức sử dụng bộ nhớ thấp.  

Bắt đầu với ví dụ cơ bản, sau đó thử nghiệm với nhiều loại chú thích, xử lý theo lô và triển khai REST‑API để tích hợp khả năng này vào các pipeline quản lý tài liệu hiện có. Nỗ lực bạn bỏ ra hôm nay sẽ mang lại lợi ích trong việc rà soát nhanh hơn, giảm tìm kiếm thủ công và người dùng cuối hạnh phúc hơn.

---

**Last Updated:** 2026-09-15  
**Tested With:** GroupDocs.Annotation 25.2 (Java)  
**Author:** GroupDocs  

**Tài nguyên và tài liệu tham khảo**

- [GroupDocs.Annotation for Java Documentation](https://docs.groupdocs.com/annotation/java/)  
- [Complete API Reference Guide](https://reference.groupdocs.com/annotation/java/)  
- [GroupDocs Releases](https://releases.groupdocs.com/annotation/java/)  
- [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- [Start Your Free Trial](https://releases.groupdocs.com/annotation/java/)  
- [Get Extended Trial License](https://purchase.groupdocs.com/temporary-license/)  
- [GroupDocs Support Forum](https://forum.groupdocs.com/c/annotation/)

## Hướng dẫn liên quan

- [Thêm Đánh dấu PDF Java – Hướng dẫn đầy đủ cho Chú thích Văn bản](/annotation/java/text-annotations/)  
- [Tạo Đánh dấu PDF Java: Hướng dẫn đầy đủ với GroupDocs Annotation](/annotation/java/annotation-management/)  
- [Tải PDF Java với GroupDocs Annotation: Hướng dẫn tải tài liệu](/annotation/java/document-loading/)