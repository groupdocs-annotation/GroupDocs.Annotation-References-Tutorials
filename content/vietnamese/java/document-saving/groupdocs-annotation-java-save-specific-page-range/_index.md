---
categories:
- Java Development
date: '2026-01-10'
description: Tìm hiểu cách sử dụng try‑with‑resources trong Java để lưu các trang
  cụ thể từ tài liệu đã chú thích bằng GroupDocs.Annotation. Bao gồm ví dụ dịch vụ
  tài liệu Spring Boot.
keywords: save specific pages Java annotation, GroupDocs annotation page range, Java
  document annotation tutorial, selective PDF page saving Java, extract annotated
  pages
lastmod: '2026-01-10'
linktitle: Save Specific Pages Java Annotation
tags:
- groupdocs
- java-annotation
- document-processing
- pdf-manipulation
title: Thử với tài nguyên Java – Lưu các trang cụ thể từ tài liệu đã chú thích
type: docs
url: /vi/java/document-saving/groupdocs-annotation-java-save-specific-page-range/
weight: 1
---

# Cách Lưu Các Trang Cụ Thể Từ Tài Liệu Được Ghi Chú trong Java

## Giới thiệu

Bạn đã bao giờ cảm thấy ngập trong những tài liệu được ghi chú khổng lồ khi chỉ cần một vài trang cụ thể? Với **try with resources java**, bạn có thể hiệu quả trích xuất đúng những trang cần thiết bằng GroupDocs.Annotation. Dù bạn đang xử lý hợp đồng pháp lý, hướng dẫn kỹ thuật hay các bài báo nghiên cứu, việc chỉ lấy các trang liên quan sẽ tiết kiệm không gian lưu trữ, tăng tốc xử lý và giữ cho quy trình làm việc của bạn gọn gàng.

Trong hướng dẫn này, chúng tôi sẽ đi qua mọi thứ bạn cần biết – từ cài đặt thư viện đến các thủ thuật tối ưu hiệu năng nâng cao giúp ứng dụng Java của bạn chạy mượt mà.

**Bạn sẽ thành thạo vào cuối bài:**
- Cài đặt GroupDocs.Annotation trong dự án Java (cách đúng)
- Thực hiện lưu trang chọn lọc với mã sạch, dễ bảo trì
- Tránh các lỗi phổ biến khiến nhiều nhà phát triển gặp rắc rối
- Tối ưu hiệu năng cho việc xử lý tài liệu lớn
- Khắc phục sự cố trước khi chúng trở thành vấn đề nghiêm trọng

## Câu trả lời nhanh
- **“try with resources java” làm gì?** Nó tự động đóng Annotator, ngăn chặn khóa tệp và rò rỉ bộ nhớ.  
- **Thư viện nào xử lý lưu theo phạm vi trang?** `GroupDocs.Annotation` cung cấp `SaveOptions` với `setFirstPage`/`setLastPage`.  
- **Có thể dùng trong dịch vụ Spring Boot không?** Có – xem phần “Spring Boot Document Service Integration”.  
- **Cần giấy phép không?** Bản dùng thử miễn phí đủ cho phát triển; giấy phép đầy đủ cần cho môi trường production.  
- **An toàn cho PDF lớn (1000+ trang)?** Sử dụng `load‑only‑annotated‑pages` và xử lý batch để giảm mức sử dụng bộ nhớ.

## Tại sao cần lưu các trang cụ thể? (Bối cảnh thực tế)

Trước khi nhảy vào phần kỹ thuật, hãy nói về lý do tính năng này lại là “game‑changer”:

**Hiệu quả lưu trữ**: Một cuốn hướng dẫn 500 trang chỉ có ghi chú trên 20 trang? Tại sao phải lưu toàn bộ 500 trang khi bạn có thể trích xuất 20 trang cần thiết và giảm kích thước tệp tới 96 %?

**Xử lý nhanh hơn**: Tệp nhỏ hơn đồng nghĩa với việc tải lên, tải xuống và xử lý nhanh hơn. Người dùng (và máy chủ) của bạn sẽ cảm ơn.

**Trải nghiệm người dùng tốt hơn**: Không ai muốn cuộn qua hàng trăm trang để tìm các phần được ghi chú. Hãy cung cấp đúng những gì họ cần.

**Tuân thủ và bảo mật**: Trong các ngành được quy định, bạn có thể chỉ được phép chia sẻ một số phần cụ thể của tài liệu. Lưu chọn lọc giúp việc tuân thủ trở nên dễ dàng hơn.

## Yêu cầu trước và Cài đặt

### Những gì bạn cần

- **Java Development Kit (JDK)**: Phiên bản 8 trở lên (khuyến nghị JDK 11+).  
- **Maven hoặc Gradle**: Để quản lý phụ thuộc.  
- **GroupDocs.Annotation for Java**: Phiên bản 25.2 trở lên.  
- **Kiến thức Java cơ bản**: Hiểu về I/O tệp và OOP.  

### Cài đặt GroupDocs.Annotation cho Java

#### Cấu hình Maven

Thêm đoạn này vào `pom.xml` của bạn (tin tôi đi, sao chép‑dán là cách nhanh nhất):

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

#### Cấu hình Gradle (Nếu bạn dùng Gradle)

```gradle
repositories {
    maven {
        url "https://releases.groupdocs.com/annotation/java/"
    }
}

dependencies {
    implementation 'com.groupdocs:groupdocs-annotation:25.2'
}
```

### Sắp xếp giấy phép

Đây là điều hầu hết các hướng dẫn không nói: **bắt đầu với bản dùng thử miễn phí**. Thật sự. Đừng làm phức tạp.

- **Free Trial**: Hoàn hảo để thử nghiệm và phát triển – tải từ [GroupDocs releases](https://releases.groupdocs.com/annotation/java/)  
- **Temporary License**: Cần thêm thời gian để đánh giá? Lấy một [temporary license](https://purchase.groupdocs.com/temporary-license/)  
- **Full License**: Sẵn sàng đưa vào production? [Purchase here](https://purchase.groupdocs.com/buy)

Mẹo: Bản dùng thử có một số hạn chế, nhưng đủ để làm theo tutorial này và xây dựng proof of concept.

## Triển khai cốt lõi: Lưu các phạm vi trang cụ thể

### Cách tiếp cận cơ bản (Bắt đầu ở đây)

Hãy bắt đầu với triển khai đơn giản nhất. Đây là gì mà 90 % trường hợp sử dụng cần:

#### Bước 1: Thiết lập quản lý đường dẫn tệp

Đầu tiên, tạo một lớp tiện ích để xử lý đường dẫn tệp (bạn sẽ cảm ơn tôi khi cần thay đổi thư mục):

```java
import org.apache.commons.io.FilenameUtils;

public class FilePathConfiguration {
    public String getOutputFilePath(String inputFile) {
        return "YOUR_OUTPUT_DIRECTORY/SavingSpecificPageRange" + "." + FilenameUtils.getExtension(inputFile);
    }
}
```

**Tại sao lại dùng cách này?** Nó tập trung logic đường dẫn tệp vào một nơi, giúp việc kiểm thử dễ dàng hơn. Sử dụng `FilenameUtils` để tự động giữ nguyên phần mở rộng gốc của tệp.

#### Bước 2: Thực hiện lưu phạm vi trang

Đây là nơi “phép màu” xảy ra:

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.options.export.SaveOptions;

public class SaveSpecificPageRange {
    public void run(String inputFile) {
        String outputPath = new FilePathConfiguration().getOutputFilePath(inputFile);
        
        try (final Annotator annotator = new Annotator(inputFile)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(2);  // Start from page 2
            saveOptions.setLastPage(4);   // End at page 4
            
            annotator.save(outputPath, saveOptions);
        }
    }
}
```

**Giải thích:**
- Chúng ta dùng khối **try‑with‑resources java** (`try ( … )`) để `Annotator` được đóng tự động, tránh các vấn đề khóa tệp.  
- `setFirstPage(2)` và `setLastPage(4)` xác định phạm vi bao gồm (trang 2‑4).  
- Phạm vi **bao gồm** cả hai đầu – chi tiết này thường làm nhiều nhà phát triển nhầm lẫn.

### Cấu hình đường dẫn tệp nâng cao

Trong các ứng dụng production, bạn sẽ muốn xử lý đường dẫn linh hoạt hơn:

```java
public class FilePathConfiguration {
    private final String baseOutputDirectory;
    
    public FilePathConfiguration(String baseOutputDirectory) {
        this.baseOutputDirectory = baseOutputDirectory;
    }
    
    public String getInputFilePath(String filename) {
        return "YOUR_DOCUMENT_DIRECTORY/" + filename;
    }
    
    public String getOutputFilePath(String inputFile, String suffix) {
        String baseName = FilenameUtils.getBaseName(inputFile);
        String extension = FilenameUtils.getExtension(inputFile);
        return String.format("%s/%s_%s.%s", baseOutputDirectory, baseName, suffix, extension);
    }
}
```

Giờ bạn có thể tự động tạo tên như `contract_pages_2-4.pdf`.

## Các lỗi thường gặp và cách tránh

### Lỗi #1: Nhầm lẫn chỉ số trang

**Vấn đề**: Giả sử số trang bắt đầu từ 0 (thực tế không phải trong GroupDocs.Annotation).

**Giải pháp**: Đánh số trang bắt đầu từ 1, giống như trong tài liệu thực tế. Trang 1 là trang đầu, không phải trang 0.

```java
// Wrong - this tries to start from page 0 (doesn't exist)
saveOptions.setFirstPage(0);

// Right - this starts from the actual first page
saveOptions.setFirstPage(1);
```

### Lỗi #2: Rò rỉ tài nguyên

**Vấn đề**: Quên đóng Annotator đúng cách, dẫn đến khóa tệp và rò rỉ bộ nhớ.

**Giải pháp**: Luôn luôn dùng **try‑with‑resources java** hoặc đóng thủ công:

```java
// Good - automatic resource management
try (final Annotator annotator = new Annotator(inputFile)) {
    // your code here
} // automatically closes

// Also acceptable - manual closing
Annotator annotator = null;
try {
    annotator = new Annotator(inputFile);
    // your code here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

### Lỗi #3: Phạm vi trang không hợp lệ

**Vấn đề**: Chỉ định phạm vi trang không tồn tại trong tài liệu.

**Giải pháp**: Kiểm tra phạm vi trước khi thực hiện:

```java
public void savePageRangeWithValidation(String inputFile, int firstPage, int lastPage) {
    try (final Annotator annotator = new Annotator(inputFile)) {
        // Get document info to check page count
        DocumentInfo documentInfo = annotator.getDocument().getDocumentInfo();
        int totalPages = documentInfo.getPageCount();
        
        // Validate range
        if (firstPage < 1 || firstPage > totalPages) {
            throw new IllegalArgumentException("First page out of range: " + firstPage);
        }
        if (lastPage < firstPage || lastPage > totalPages) {
            throw new IllegalArgumentException("Last page out of range: " + lastPage);
        }
        
        SaveOptions saveOptions = new SaveOptions();
        saveOptions.setFirstPage(firstPage);
        saveOptions.setLastPage(lastPage);
        
        String outputPath = new FilePathConfiguration().getOutputFilePath(inputFile);
        annotator.save(outputPath, saveOptions);
    }
}
```

## Mẹo tối ưu hiệu năng

### Quản lý bộ nhớ cho tài liệu lớn

Khi làm việc với tài liệu lớn (100 + trang), việc sử dụng bộ nhớ trở nên quan trọng:

```java
public class OptimizedPageRangeSaver {
    public void saveWithOptimization(String inputFile, int firstPage, int lastPage) {
        // Configure for lower memory usage
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setLoadOnlyAnnotatedPages(true); // Only load pages with annotations
        
        try (final Annotator annotator = new Annotator(inputFile, loadOptions)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(firstPage);
            saveOptions.setLastPage(lastPage);
            
            // Optional: Enable compression for smaller output files
            saveOptions.setAnnotationsOnly(false); // Set to true if you only want annotations
            
            String outputPath = new FilePathConfiguration().getOutputFilePath(inputFile);
            annotator.save(outputPath, saveOptions);
        }
    }
}
```

**Chiến lược tối ưu chính**
- `setLoadOnlyAnnotatedPages(true)` giảm đáng kể dung lượng bộ nhớ.  
- `setAnnotationsOnly(true)` tạo tệp nhẹ chỉ chứa lớp ghi chú.  
- Xử lý tài liệu theo batch nếu có nhiều tệp.

### Xử lý batch nhiều tài liệu

Trong các kịch bản production cần xử lý hàng loạt tài liệu:

```java
public class BatchPageRangeSaver {
    public void processBatch(List<String> inputFiles, int firstPage, int lastPage) {
        for (String inputFile : inputFiles) {
            try {
                savePageRangeWithValidation(inputFile, firstPage, lastPage);
                System.out.println("Successfully processed: " + inputFile);
            } catch (Exception e) {
                System.err.println("Failed to process " + inputFile + ": " + e.getMessage());
                // Log the error and continue with next file
            }
        }
    }
}
```

## Tích hợp với các framework phổ biến

### Tích hợp dịch vụ Spring Boot

Đây là một dịch vụ Spring Boot đơn giản để lưu theo phạm vi trang (lưu ý cụm từ **spring boot document service**):

```java
@Service
public class DocumentPageRangeService {
    
    @Value("${app.document.output-directory}")
    private String outputDirectory;
    
    public String savePageRange(String inputFile, int firstPage, int lastPage) {
        try (final Annotator annotator = new Annotator(inputFile)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(firstPage);
            saveOptions.setLastPage(lastPage);
            
            String outputPath = generateOutputPath(inputFile, firstPage, lastPage);
            annotator.save(outputPath, saveOptions);
            
            return outputPath;
        } catch (Exception e) {
            throw new DocumentProcessingException("Failed to save page range", e);
        }
    }
    
    private String generateOutputPath(String inputFile, int firstPage, int lastPage) {
        String baseName = FilenameUtils.getBaseName(inputFile);
        String extension = FilenameUtils.getExtension(inputFile);
        return String.format("%s/%s_pages_%d-%d.%s", 
                            outputDirectory, baseName, firstPage, lastPage, extension);
    }
}
```

## Ứng dụng thực tiễn và trường hợp sử dụng

### Xử lý tài liệu pháp lý

Các công ty luật thường cần trích xuất các phần cụ thể của hợp đồng hoặc tài liệu tòa án:

```java
public class LegalDocumentProcessor {
    public void extractEvidencePages(String caseFile, List<Integer> evidencePages) {
        // Group consecutive pages for efficient processing
        List<PageRange> ranges = groupConsecutivePages(evidencePages);
        
        for (PageRange range : ranges) {
            String outputFile = String.format("evidence_%d_%d-to-%d.pdf", 
                                            getCaseNumber(caseFile), range.start, range.end);
            savePageRange(caseFile, range.start, range.end, outputFile);
        }
    }
}
```

### Quản lý nội dung giáo dục

Giáo viên trích xuất các chương cụ thể từ sách giáo trình cho bài tập của học sinh:

```java
public class EducationalContentExtractor {
    public void createAssignmentPacket(String textbook, int chapterStart, int chapterEnd) {
        try (final Annotator annotator = new Annotator(textbook)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(chapterStart);
            saveOptions.setLastPage(chapterEnd);
            
            String assignmentFile = generateAssignmentFileName(textbook, chapterStart, chapterEnd);
            annotator.save(assignmentFile, saveOptions);
        }
    }
}
```

### Đánh giá chất lượng

Chỉ trích xuất các trang có bình luận đánh giá để tập trung vào việc sửa đổi:

```java
public class QAReviewExtractor {
    public void extractReviewedPages(String document) {
        try (final Annotator annotator = new Annotator(document)) {
            // Get pages with annotations
            List<Integer> annotatedPages = getAnnotatedPageNumbers(annotator);
            
            if (!annotatedPages.isEmpty()) {
                int firstPage = Collections.min(annotatedPages);
                int lastPage = Collections.max(annotatedPages);
                
                SaveOptions saveOptions = new SaveOptions();
                saveOptions.setFirstPage(firstPage);
                saveOptions.setLastPage(lastPage);
                
                String reviewFile = document.replace(".pdf", "_review_comments.pdf");
                annotator.save(reviewFile, saveOptions);
            }
        }
    }
}
```

## Tóm tắt các thực hành tốt nhất

1. **Luôn kiểm tra tham số đầu vào** – xác minh phạm vi trang trước khi xử lý.  
2. **Sử dụng try‑with‑resources java** – ngăn ngừa rò rỉ tài nguyên và vấn đề khóa tệp.  
3. **Triển khai xử lý lỗi hợp lý** – không để một tệp lỗi làm sập toàn bộ batch.  
4. **Xem xét mức sử dụng bộ nhớ** – dùng `setLoadOnlyAnnotatedPages(true)` cho tài liệu lớn.  
5. **Kiểm thử với nhiều loại tệp** – PDF, Word, PowerPoint có thể hành vi khác nhau.  
6. **Giám sát hiệu năng** – theo dõi thời gian xử lý và bộ nhớ trong môi trường production.

## Khắc phục các vấn đề thường gặp

### Vấn đề: Lỗi “File is locked”

**Triệu chứng**: Ngoại lệ được ném khi cố lưu, thông báo về khóa tệp.  

**Nguyên nhân**:  
- Annotator không được đóng đúng cách từ lần thao tác trước.  
- Tệp vẫn mở trong ứng dụng khác.  
- Quyền truy cập không đủ.  

**Giải pháp**:

```java
// Ensure proper cleanup
try (final Annotator annotator = new Annotator(inputFile)) {
    // ... your code ...
} // Automatically releases file handles

// Verify file accessibility before processing
File file = new File(inputFile);
if (!file.canRead()) {
    throw new IllegalArgumentException("Cannot read input file: " + inputFile);
}
if (!file.getParentFile().canWrite()) {
    throw new IllegalArgumentException("Cannot write to output directory");
}
```

### Vấn đề: Lỗi Out of Memory

**Triệu chứng**: `OutOfMemoryError` khi xử lý tài liệu lớn.  

**Giải pháp**:  
1. Tăng kích thước heap JVM, ví dụ `-Xmx2g`.  
2. Sử dụng các tùy chọn tải tối ưu đã trình bày ở trên.  
3. Xử lý tài liệu theo các batch nhỏ hơn.

### Vấn đề: Ghi chú không được giữ lại

**Triệu chứng**: Tệp đầu ra không chứa các ghi chú gốc.  

**Giải pháp**: Đảm bảo bạn không loại bỏ ghi chú:

```java
SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationsOnly(false); // Keep both content and annotations
saveOptions.setFirstPage(firstPage);
saveOptions.setLastPage(lastPage);
```

## Câu hỏi thường gặp

**Hỏi: Có thể lưu các trang không liên tiếp (ví dụ trang 1, 3, 7) không?**  
Đáp: Không trực tiếp trong một thao tác. Bạn cần thực hiện lưu riêng cho mỗi phạm vi hoặc ghép kết quả lại sau đó.

**Hỏi: Tính năng này có hoạt động với tài liệu được bảo vệ bằng mật khẩu không?**  
Đáp: Có, nhưng bạn phải cung cấp mật khẩu khi tạo `Annotator`: `new Annotator(inputFile, loadOptions.setPassword("your_password"))`.

**Hỏi: Các định dạng tệp nào được hỗ trợ?**  
Đáp: PDF, Microsoft Word, Excel, PowerPoint và nhiều định dạng khác. Xem [official documentation](https://docs.groupdocs.com/annotation/java/) để biết danh sách đầy đủ.

**Hỏi: Có thể lưu chỉ phần ghi chú mà không có nội dung gốc không?**  
Đáp: Chắc chắn – đặt `saveOptions.setAnnotationsOnly(true)` để tạo tệp chỉ chứa ghi chú.

**Hỏi: Làm sao xử lý tài liệu rất lớn (1000+ trang)?**  
Đáp: Dùng `setLoadOnlyAnnotatedPages(true)`, xử lý theo từng khối, và cân nhắc tăng heap JVM.

**Hỏi: Có cách xem trước các trang trước khi lưu không?**  
Đáp: GroupDocs.Annotation tập trung vào xử lý hơn là hiển thị, nhưng bạn có thể lấy thông tin tài liệu (số trang, vị trí ghi chú) để quyết định phạm vi cần trích xuất.

## Tài nguyên

- **Documentation**: [GroupDocs.Annotation for Java Docs](https://docs.groupdocs.com/annotation/java/)  
- **API Reference**: [Complete API Documentation](https://reference.groupdocs.com/annotation/java/)  
- **Download**: [Latest Releases](https://releases.groupdocs.com/annotation/java/)  
- **Purchase**: [License Options](https://purchase.groupdocs.com/buy)  
- **Free Trial**: [Try It Now](https://releases.groupdocs.com/annotation/java/)  
- **Temporary License**: [Get Evaluation License](https://purchase.groupdocs.com/temporary-license/)  
- **Support**: [Community Forum](https://forum.groupdocs.com/c/annotation/)

---

**Cập nhật lần cuối:** 2026-01-10  
**Kiểm thử với:** GroupDocs.Annotation 25.2 (Java)  
**Tác giả:** GroupDocs