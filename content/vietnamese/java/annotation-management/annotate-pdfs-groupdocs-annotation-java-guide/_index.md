---
categories:
- Java Development
date: '2025-12-17'
description: Tìm hiểu cách tạo PDF nhận xét đánh giá với GroupDocs.Annotation cho
  Java. Hướng dẫn từng bước này bao gồm cài đặt, triển khai và các thực tiễn tốt nhất
  cho các nhà phát triển.
keywords: PDF annotation Java tutorial, GroupDocs annotation Java setup, Java PDF
  markup library, add annotations PDF programmatically, GroupDocs annotation tutorial
  for beginners
lastmod: '2025-12-17'
tags:
- pdf-annotation
- groupdocs
- java-libraries
- document-processing
title: Tạo PDF bình luận đánh giá bằng GroupDocs.Annotation Java
type: docs
url: /vi/java/annotation-management/annotate-pdfs-groupdocs-annotation-java-guide/
weight: 1
---

# Hướng Dẫn Java Về Ghi Chú PDF

## Tại Sao Ghi Chú PDF Quan Trọng Trong Phát Triển Hiện Đại

Bạn đã bao giờ cần đánh dấu các tài liệu PDF một cách lập trình trong ứng dụng Java của mình chưa? Dù bạn đang xây dựng hệ thống xem xét tài liệu, tạo nền tảng e‑learning, hay phát triển công cụ cộng tác, ghi chú PDF luôn hiện hữu. Thách thức là gì? Hầu hết các giải pháp đều quá phức tạp cho nhu cầu đơn giản hoặc quá hạn chế cho yêu cầu doanh nghiệp.

Trong tutorial này, bạn sẽ học cách **tạo PDF có bình luận đánh giá** bằng GroupDocs.Annotation cho Java, để có thể thêm các đánh dấu chuyên nghiệp vào bất kỳ tài liệu nào chỉ với vài dòng code.

**Điểm gì làm cho hướng dẫn này khác biệt?** Chúng tôi sẽ không chỉ nói “cách làm” mà còn giải thích “tại sao” và “khi nào”, cùng với những lưu ý mà các tutorial khác thường bỏ qua.

## Câu Hỏi Nhanh
- **Mục đích chính của GroupDocs.Annotation là gì?** Thêm, chỉnh sửa và quản lý các ghi chú trên nhiều định dạng tài liệu từ Java.
- **Loại ghi chú nào phù hợp nhất cho bình luận đánh giá?** AreaAnnotation với tin nhắn tùy chỉnh và siêu dữ liệu người dùng.
- **Có cần giấy phép cho việc phát triển không?** Bản dùng thử miễn phí đủ cho việc thử nghiệm; giấy phép đầy đủ cần thiết cho môi trường sản xuất.
- **Có thể xử lý các file PDF lớn hơn 50 MB không?** Có — sử dụng streaming, xử lý batch và giải phóng tài nguyên đúng cách để giảm mức sử dụng bộ nhớ.
- **Thư viện có an toàn với đa luồng không?** Các instance không an toàn với đa luồng; tạo một Annotator riêng cho mỗi luồng.

## Tại Sao GroupDocs Annotation Nổi Bật

Trước khi đi sâu vào code, hãy cùng tìm hiểu vì sao GroupDocs.Annotation có thể là lựa chọn tốt nhất cho các dự án ghi chú PDF bằng Java.

### Những Ưu Điểm Chủ Chốt So Với Các Giải Pháp Khác

**Hỗ Trợ Định Dạng Toàn Diện**: Trong khi nhiều thư viện chỉ tập trung vào PDF, GroupDocs còn xử lý tài liệu Word, bản trình bày PowerPoint, hình ảnh và nhiều hơn nữa. Điều này có nghĩa là bạn chỉ cần một API cho mọi nhu cầu ghi chú.

**Đa Dạng Loại Ghi Chú**: Ngoài các highlight đơn giản, bạn còn có mũi tên, watermark, thay thế văn bản và các hình dạng tùy chỉnh — phù hợp với nhiều trường hợp sử dụng khác nhau.

**Sẵn Sàng Cho Doanh Nghiệp**: Tích hợp sẵn hỗ trợ cấp phép, khả năng mở rộng và tích hợp với kiến trúc Java hiện có.

**Phát Triển Chủ Động**: Cập nhật thường xuyên và cộng đồng hỗ trợ phản hồi nhanh (tin tôi đi, bạn sẽ cảm nhận được giá trị này khi gặp các trường hợp khó).

## Yêu Cầu Trước Khi Bắt Đầu Và Cài Đặt

### Những Gì Bạn Cần Chuẩn Bị

Hãy giải quyết những việc nhàm chán trước. Đây là danh sách kiểm tra của bạn:

**Môi Trường Phát Triển:**
- JDK 8 trở lên (Java 11+ được khuyến nghị để có hiệu năng tốt hơn)
- IDE yêu thích của bạn (IntelliJ IDEA, Eclipse, hoặc VS Code với các extension Java)
- Maven hoặc Gradle để quản lý phụ thuộc

**Kiến Thức Cần Thiết:**
- Lập trình Java cơ bản (nếu bạn biết vòng lặp và lớp, bạn đã đủ)
- Quen thuộc với các thao tác I/O file
- Hiểu về phụ thuộc Maven (chúng tôi sẽ hướng dẫn qua)

**Tùy Chọn Nhưng Hữu Ích:**
- Kiến thức cơ bản về cấu trúc PDF (giúp khắc phục lỗi)
- Kinh nghiệm với các thư viện Java khác (giúp nắm bắt khái niệm nhanh hơn)

### Cài Đặt GroupDocs.Annotation cho Java

#### Cấu Hình Maven

Thêm repository và dependency của GroupDocs vào `pom.xml`. Đây là những gì bạn cần:

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

**Mẹo Pro**: Luôn kiểm tra phiên bản mới nhất trên website GroupDocs. Phiên bản 25.2 là hiện tại tại thời điểm viết, nhưng các phiên bản mới hơn thường có cải tiến hiệu năng và sửa lỗi.

#### Các Tùy Chọn Cấp Phép (Và Ý Nghĩa Thực Tế)

**Dùng Thử Miễn Phí**: Phù hợp cho đánh giá ban đầu và dự án nhỏ. Bạn sẽ nhận được file có watermark, đủ cho việc thử nghiệm nhưng không thích hợp cho sản xuất.

**Giấy Phép Tạm Thời**: Lý tưởng cho giai đoạn phát triển. Lấy một giấy phép [tại đây](https://purchase.groupdocs.com/temporary-license/) để dùng trong 30 ngày không giới hạn.

**Giấy Phép Đầy Đủ**: Yêu cầu cho môi trường sản xuất. Giá cả thay đổi tùy theo loại triển khai và quy mô.

#### Thiết Lập Ban Đầu Và Kiểm Tra

Khi các phụ thuộc đã sẵn sàng, hãy kiểm tra mọi thứ hoạt động bằng đoạn test đơn giản sau:

```java
import com.groupdocs.annotation.Annotator;

public class SetupVerification {
    public static void main(String[] args) {
        try {
            // This should not throw any ClassNotFoundException
            System.out.println("GroupDocs.Annotation version: " + 
                com.groupdocs.annotation.internal.c.a.a.d());
            System.out.println("Setup successful!");
        } catch (Exception e) {
            System.err.println("Setup failed: " + e.getMessage());
        }
    }
}
```

## Cách Tạo PDF Có Bình Luận Đánh Giá Với GroupDocs.Annotation

### Tải Tài Liệu: Hơn Cả Đường Dẫn Tập Tin

#### Tải Tài Liệu Cơ Bản

Bắt đầu với những nền tảng. Tải một tài liệu PDF là bước đầu tiên:

```java
String INPUT_PDF = "YOUR_DOCUMENT_DIRECTORY/input.pdf";
String outputPath = "YOUR_OUTPUT_DIRECTORY/output_annotated.pdf";

// Initialize Annotator with the path to your document
final Annotator annotator = new Annotator(INPUT_PDF);
```

**Bối Cảnh Thực Tế**: Trong các ứng dụng sản xuất, các đường dẫn này thường đến từ tải lên của người dùng, mục nhập cơ sở dữ liệu, hoặc URL lưu trữ đám mây. GroupDocs xử lý linh hoạt các file cục bộ, stream và URL.

#### Xử Lý Các Nguồn Đầu Vào Khác Nhau

```java
// From file path (most common)
Annotator annotatorFromPath = new Annotator("path/to/document.pdf");

// From InputStream (useful for uploaded files)
FileInputStream inputStream = new FileInputStream("document.pdf");
Annotator annotatorFromStream = new Annotator(inputStream);

// Don't forget to close streams when done!
inputStream.close();
```

### Thêm Ghi Chú Đầu Tiên Của Bạn

#### Hiểu Về Area Annotations

Area annotations rất phù hợp để làm nổi bật vùng, đánh dấu các phần quan trọng, hoặc tạo các callout trực quan. Hãy nghĩ chúng như những ghi chú dán kỹ thuật số có phong cách.

```java
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.annotationmodels.AreaAnnotation;

// Create the annotation
AreaAnnotation area = new AreaAnnotation();

// Position and size: x, y, width, height
area.setBox(new Rectangle(100, 100, 100, 100));

// Background color in ARGB format (65535 = yellow with transparency)
area.setBackgroundColor(65535);

// Add the annotation to your document
annotator.add(area);
```

**Giải Thích Hệ Tọa Độ**: Tọa độ PDF bắt đầu từ góc dưới‑trái, nhưng GroupDocs sử dụng hệ thống gốc ở góc trên‑trái (dễ hiểu hơn cho lập trình viên). Các số đại diện cho pixel tính từ gốc.

#### Các Ví Dụ Thực Tế Về Ghi Chú

**Highlight Văn Bản Quan Trọng**:
```java
// Create a semi‑transparent highlight
AreaAnnotation highlight = new AreaAnnotation();
highlight.setBox(new Rectangle(50, 200, 200, 25));
highlight.setBackgroundColor(0x80FFFF00); // Semi‑transparent yellow
highlight.setMessage("Important clause - review carefully");
```

**Tạo Bình Luận Đánh Giá**:
```java
// Add a comment annotation with custom styling
AreaAnnotation comment = new AreaAnnotation();
comment.setBox(new Rectangle(300, 150, 150, 75));
comment.setBackgroundColor(0x80FF0000); // Semi‑transparent red
comment.setMessage("Needs revision - see discussion in email");
comment.setCreatedOn(new Date());
comment.setUser("John Reviewer");
```

### Lưu Và Quản Lý Tài Nguyên

#### Kỹ Thuật Lưu File Đúng Cách

```java
// Save the annotated document
annotator.save(outputPath);

// Always dispose of resources (critical for memory management)
annotator.dispose();
```

**Tại Sao Cần Dispose**: GroupDocs giữ dữ liệu tài liệu trong bộ nhớ để tăng tốc. Nếu không giải phóng đúng cách, bạn sẽ gặp rò rỉ bộ nhớ trong các ứng dụng chạy lâu.

#### Mẫu Quản Lý Tài Nguyên Tốt Hơn

```java
public void annotateDocument(String inputPath, String outputPath) {
    try (Annotator annotator = new Annotator(inputPath)) {
        // Your annotation code here
        AreaAnnotation area = new AreaAnnotation();
        area.setBox(new Rectangle(100, 100, 100, 100));
        area.setBackgroundColor(65535);
        
        annotator.add(area);
        annotator.save(outputPath);
        
        System.out.println("Document successfully annotated and saved to: " + outputPath);
    } catch (Exception e) {
        System.err.println("Annotation failed: " + e.getMessage());
        throw new RuntimeException("Failed to annotate document", e);
    }
}
```

## Những Sai Lầm Thường Gặp Và Cách Tránh

### Vấn Đề Đường Dẫn File Và Quyền Truy Cập

**Vấn Đề**: Lỗi “File not found” hoặc “Access denied” xuất hiện thường xuyên.

**Giải Pháp**:
- Luôn dùng đường dẫn tuyệt đối trong quá trình phát triển
- Kiểm tra quyền truy cập file trước khi xử lý
- Xác thực file tồn tại và có thể đọc được

```java
public boolean validateInputFile(String filePath) {
    File file = new File(filePath);
    if (!file.exists()) {
        System.err.println("File does not exist: " + filePath);
        return false;
    }
    if (!file.canRead()) {
        System.err.println("Cannot read file: " + filePath);
        return false;
    }
    return true;
}
```

### Sai Lầm Quản Lý Bộ Nhớ

**Vấn Đề**: Ứng dụng chậm lại hoặc sập sau khi xử lý nhiều tài liệu.

**Giải Pháp**: Luôn sử dụng try‑with‑resources hoặc giải phóng tài nguyên một cách rõ ràng:

```java
// Good practice - automatic resource management
try (Annotator annotator = new Annotator(inputPath)) {
    // Annotation code here
} // Automatically disposed

// If manual disposal is needed
Annotator annotator = null;
try {
    annotator = new Annotator(inputPath);
    // Annotation code here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

### Nhầm Lẫn Hệ Tọa Độ

**Vấn Đề**: Ghi chú xuất hiện ở vị trí sai hoặc ngoài màn hình.

**Giải Pháp**: Nhớ hệ thống tọa độ PDF và thử nghiệm với các vị trí đã biết:

```java
// Start with simple, visible coordinates for testing
Rectangle testPosition = new Rectangle(50, 50, 100, 50);

// Gradually adjust based on your PDF dimensions
// Most PDFs are 612x792 points (8.5"x11" at 72 DPI)
```

## Các Trường Hợp Sử Dụng Thực Tế

### Quy Trình Đánh Giá Tài Liệu

**Kịch Bản**: Các công ty luật xem xét hợp đồng trước các buổi họp với khách hàng.

**Chiến Lược Thực Hiện**:
- Màu ghi chú khác nhau cho từng người đánh giá
- Ghi thời gian và người dùng để tạo audit trail
- Khả năng xuất file cho khách hàng

```java
public void addReviewAnnotation(Annotator annotator, String reviewerName, 
                              String comment, Rectangle position, Color highlightColor) {
    AreaAnnotation review = new AreaAnnotation();
    review.setBox(position);
    review.setBackgroundColor(highlightColor.getRGB());
    review.setMessage(comment);
    review.setUser(reviewerName);
    review.setCreatedOn(new Date());
    
    annotator.add(review);
}
```

### Tạo Nội Dung Giáo Dục

**Kịch Bản**: Nền tảng e‑learning làm nổi bật các khái niệm quan trọng trong tài liệu học.

**Lý Do Thành Công**: Ghi chú trực quan tăng khả năng hiểu và ghi nhớ, đặc biệt với tài liệu kỹ thuật.

### Tài Liệu Kiểm Định Chất Lượng

**Kịch Bản**: Các công ty sản xuất đánh dấu các bản vẽ kỹ thuật và thông số.

**Lợi Ích**: Đánh dấu chuẩn hoá giữa các nhóm, theo dõi phiên bản, và giao tiếp thay đổi rõ ràng.

## Mẹo Tối Ưu Hiệu Năng

### Xử Lý Tài Liệu Lớn Một Cách Hiệu Quả

**Chiến Lược Xử Lý Batch**:
```java
public void processDocumentBatch(List<String> documentPaths) {
    for (String path : documentPaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Process each document independently
            // This prevents memory accumulation
            processAnnotations(annotator);
        }
        
        // Optional: Add small delay for very large batches
        // Thread.sleep(100);
    }
}
```

### Giám Sát Sử Dụng Bộ Nhớ

**Theo Dõi Bộ Nhớ Ứng Dụng**:
```java
Runtime runtime = Runtime.getRuntime();
long memoryBefore = runtime.totalMemory() - runtime.freeMemory();

// Process documents...

long memoryAfter = runtime.totalMemory() - runtime.freeMemory();
System.out.println("Memory used: " + (memoryAfter - memoryBefore) + " bytes");
```

### Xem Xét Xử Lý Đồng Thời

**An Toàn Đa Luồng**: GroupDocs.Annotation không an toàn với đa luồng trên cùng một instance. Sử dụng các instance Annotator riêng cho mỗi luồng:

```java
public class ConcurrentAnnotationProcessor {
    public void processDocumentsConcurrently(List<String> documents) {
        documents.parallelStream().forEach(docPath -> {
            try (Annotator annotator = new Annotator(docPath)) {
                // Each thread gets its own Annotator instance
                processAnnotations(annotator);
            }
        });
    }
}
```

## Kỹ Thuật Ghi Chú Nâng Cao

### Nhiều Loại Ghi Chú Trong Một Tài Liệu

```java
public void createComprehensiveAnnotation(Annotator annotator) {
    // Highlight important text
    AreaAnnotation highlight = new AreaAnnotation();
    highlight.setBox(new Rectangle(100, 100, 200, 30));
    highlight.setBackgroundColor(0x80FFFF00);
    
    // Add explanatory note
    AreaAnnotation note = new AreaAnnotation();
    note.setBox(new Rectangle(320, 95, 150, 40));
    note.setBackgroundColor(0x80ADD8E6);
    note.setMessage("See reference document #123");
    
    annotator.add(highlight);
    annotator.add(note);
}
```

### Ghi Chú Động Dựa Trên Nội Dung

Mặc dù tutorial này tập trung vào việc đặt ghi chú thủ công, bạn có thể kết hợp GroupDocs với các thư viện phân tích văn bản để tự động phát hiện và ghi chú các mẫu nội dung cụ thể.

## Hướng Dẫn Khắc Phục Sự Cố

### Các Thông Báo Lỗi Thường Gặp Và Giải Pháp

**Lỗi “Invalid license”**:
- Kiểm tra vị trí và định dạng file giấy phép
- Xác nhận ngày hết hạn giấy phép
- Đảm bảo giấy phép phù hợp với loại triển khai của bạn

**Lỗi “Unsupported file format”**:
- Kiểm tra PDF không bị hỏng
- Xác nhận PDF không được bảo vệ bằng mật khẩu
- Đảm bảo file không phải là 0 byte hoặc chưa hoàn chỉnh

**Vấn đề hiệu năng**:
- Giám sát bộ nhớ và thực hiện giải phóng tài nguyên đúng cách
- Xem xét xử lý tài liệu theo batch
- Kiểm tra phần mềm diệt virus có đang quét các file tạm không

### Mẹo Debug

**Bật Logging**:
```java
// Add to your application properties or logging configuration
java.util.logging.Logger.getLogger("com.groupdocs").setLevel(Level.FINE);
```

**Xác Thực Đầu Vào**:
```java
public boolean validateAnnotationParameters(Rectangle box, int color) {
    if (box.getWidth() <= 0 || box.getHeight() <= 0) {
        System.err.println("Invalid annotation dimensions");
        return false;
    }
    
    if (box.getX() < 0 || box.getY() < 0) {
        System.err.println("Annotation position cannot be negative");
        return false;
    }
    
    return true;
}
```

## Câu Hỏi Thường Gặp

### Làm sao để thêm nhiều ghi chú vào một PDF một cách hiệu quả?

Chỉ cần gọi `annotator.add(annotation)` cho mỗi ghi chú trước khi lưu. GroupDocs sẽ gom tất cả ghi chú và áp dụng khi bạn gọi `save()`:

```java
try (Annotator annotator = new Annotator("document.pdf")) {
    annotator.add(annotation1);
    annotator.add(annotation2);
    annotator.add(annotation3);
    annotator.save("output.pdf"); // All annotations applied at once
}
```

### GroupDocs.Annotation hỗ trợ những định dạng file nào ngoài PDF?

GroupDocs.Annotation hỗ trợ hơn 50 định dạng bao gồm tài liệu Word (DOC, DOCX), bản trình bày PowerPoint (PPT, PPTX), bảng tính Excel (XLS, XLSX), hình ảnh (JPEG, PNG, TIFF) và nhiều loại khác. Xem [tài liệu](https://docs.groupdocs.com/annotation/java/) để biết danh sách đầy đủ.

### Làm sao xử lý PDF được bảo vệ bằng mật khẩu?

Sử dụng tham số LoadOptions khi khởi tạo Annotator:

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("your-password");
Annotator annotator = new Annotator("protected.pdf", loadOptions);
```

### Có thể lấy và chỉnh sửa các ghi chú đã tồn tại trong PDF không?

Có! Bạn có thể lấy các ghi chú hiện có và chỉnh sửa chúng:

```java
try (Annotator annotator = new Annotator("annotated.pdf")) {
    List<AnnotationInfo> annotations = annotator.get(AnnotationType.Area);
    for (AnnotationInfo annotation : annotations) {
        // Modify properties as needed
        annotation.setMessage("Updated comment");
    }
    annotator.update(annotations);
    annotator.save("updated.pdf");
}
```

### Các ảnh hưởng về hiệu năng khi xử lý PDF lớn là gì?

PDF lớn (>50 MB) đòi hỏi quản lý bộ nhớ cẩn thận. Sử dụng streaming khi có thể, xử lý từng trang nếu cần, và luôn giải phóng tài nguyên. Cân nhắc triển khai theo dõi tiến độ để người dùng biết trạng thái trong các thao tác lâu.

### Làm sao xử lý đồng thời nhiều tài liệu trong một ứng dụng web?

Mỗi luồng cần một instance Annotator riêng vì thư viện không an toàn với đa luồng trên cùng một instance. Sử dụng thread pool hoặc mô hình lập trình reactive:

```java
@Service
public class AnnotationService {
    public CompletableFuture<String> annotateAsync(String inputPath) {
        return CompletableFuture.supplyAsync(() -> {
            try (Annotator annotator = new Annotator(inputPath)) {
                // Process annotations
                return processDocument(annotator);
            }
        });
    }
}
```

### Cách tốt nhất để debug vấn đề vị trí ghi chú?

Bắt đầu với các tọa độ đã biết và điều chỉnh dần. Hầu hết các PDF tiêu chuẩn có kích thước 612x792 points. Tạo một ghi chú thử nghiệm tại (50, 50, 100, 50) để xác nhận chức năng cơ bản, sau đó điều chỉnh dựa trên bố cục nội dung của bạn.

### Làm sao tích hợp GroupDocs.Annotation với Spring Boot?

Tạo một service component và dùng dependency injection:

```java
@Service
public class DocumentAnnotationService {
    
    public void annotateDocument(MultipartFile file, List<AnnotationRequest> requests) {
        try (InputStream inputStream = file.getInputStream();
             Annotator annotator = new Annotator(inputStream)) {
            
            // Process annotation requests
            requests.forEach(request -> addAnnotation(annotator, request));
            annotator.save("output.pdf");
        }
    }
}
```

## FAQ Bổ Sung

**Hỏi: Có thể xuất PDF đã ghi chú sang các định dạng khác không?**  
Đáp: Có, GroupDocs.Annotation có thể chuyển đổi tài liệu đã ghi chú sang các định dạng như DOCX, PPTX hoặc hình ảnh mà vẫn giữ nguyên các ghi chú.

**Hỏi: Có cách liệt kê tất cả các loại ghi chú mà thư viện hỗ trợ không?**  
Đáp: Dùng `AnnotationType.values()` để lấy mảng các enum ghi chú được hỗ trợ.

**Hỏi: Làm sao tùy chỉnh giao diện của watermark annotation?**  
Đáp: Đặt các thuộc tính như `setOpacity`, `setRotation`, và `setBackgroundColor` trên một instance `WatermarkAnnotation` trước khi thêm vào.

**Hỏi: Thư viện có hỗ trợ thêm bình luận từ cơ sở dữ liệu không?**  
Đáp: Chắc chắn. Bạn có thể đọc dữ liệu bình luận từ bất kỳ nguồn nào, gán vào `AreaAnnotation` (hoặc `TextAnnotation`) và thêm vào tài liệu.

**Hỏi: Nếu gặp rò rỉ bộ nhớ trong quá trình batch processing, nên làm gì?**  
Đáp: Đảm bảo mọi `Annotator` đều được đóng (try‑with‑resources), giám sát heap JVM, và cân nhắc xử lý tài liệu theo các batch nhỏ hơn.  

**Tài Nguyên Bổ Sung**  
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/)  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/)  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/)  
- [Purchase License](https://purchase.groupdocs.com/buy)  
- [Free Trial Access](https://releases.groupdocs.com/annotation/java/)  
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- [Support Forum](https://forum.groupdocs.com/c/annotation/)

---

**Cập Nhật Cuối Cùng:** 2025-12-17  
**Đã Kiểm Tra Với:** GroupDocs.Annotation 25.2 cho Java  
**Tác Giả:** GroupDocs