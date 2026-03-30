---
categories:
- Java Development
date: '2026-03-30'
description: Tìm hiểu cách thêm chú thích gạch ngang trong Java bằng GroupDocs.Annotation.
  Hướng dẫn từng bước kèm ví dụ mã, mẹo khắc phục sự cố và các thực tiễn tốt nhất
  cho việc đánh dấu tài liệu.
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: 'Hướng dẫn Java: Thêm chú thích gạch ngang với GroupDocs'
type: docs
url: /vi/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# Thêm chú thích gạch ngang Java - Hướng dẫn đầy đủ GroupDocs

Bạn đã bao giờ nhìn chằm chằm vào một tài liệu và nghĩ, “Tôi cần gạch ngang đoạn văn bản này, nhưng không thể chỉ dùng bút đỏ” chưa? Bạn không phải là người duy nhất. Dù bạn đang xây dựng hệ thống xem xét tài liệu, tạo quy trình chỉnh sửa, hay chỉ cần đánh dấu văn bản để xóa trong ứng dụng Java của mình, **add strikeout annotation java** là một kỹ năng thiết yếu. Trong hướng dẫn này, chúng ta sẽ đi qua mọi thứ bạn cần biết để triển khai chức năng gạch ngang văn bản thực sự hoạt động trong môi trường production.

## Câu trả lời nhanh
- **Thư viện nào hỗ trợ chú thích gạch ngang trong Java?** GroupDocs.Annotation for Java  
- **Từ khóa chính nên nhắm tới cho SEO là gì?** add strikeout annotation java  
- **Có cần giấy phép để chạy mã mẫu không?** Bản dùng thử miễn phí hoặc giấy phép tạm thời đủ cho phát triển; giấy phép đầy đủ cần cho production.  
- **Có thể sử dụng với các file PDF, DOCX và PPTX không?** Có – GroupDocs.Annotation hỗ trợ tất cả các định dạng tài liệu chính.  
- **Yêu cầu phiên bản Java nào?** JDK 8 trở lên (khuyến nghị JDK 11+).

## add strikeout annotation java là gì?
Một chú thích gạch ngang vẽ một đường qua văn bản đã chọn, cho thấy nội dung nên bị xóa hoặc bỏ qua. Đây là cách không phá hủy để đề xuất xóa bỏ trong khi giữ nguyên văn bản gốc cho các bản ghi audit hoặc đánh giá hợp tác.

## Tại sao sử dụng chú thích gạch ngang trong các ứng dụng Java?
- **Quy trình xem xét tài liệu** – người đánh giá có thể đánh dấu văn bản không mong muốn mà không thay đổi nguồn.  
- **Chỉnh sửa hợp tác** – các thành viên đội ngũ thấy ngay các đề xuất xóa bỏ.  
- **Pháp lý và tuân thủ** – giữ một chuỗi audit rõ ràng của các thay đổi.  
- **Di chuyển nội dung** – đánh dấu các phần lỗi thời trước khi chuyển nội dung giữa các hệ thống.  

## Yêu cầu trước và Cài đặt môi trường
Bạn sẽ cần những thứ sau trước khi bắt đầu viết mã:

- **Java Development Kit (JDK)** 8+ (khuyến nghị JDK 11+)  
- **Maven hoặc Gradle** để quản lý phụ thuộc  
- **IDE** – IntelliJ IDEA, Eclipse, hoặc VS Code với các extension Java  
- **Thư viện GroupDocs.Annotation** – chúng ta sẽ dùng phiên bản 25.2 trong các ví dụ  

*Nice to have:* kiến thức cơ bản về annotation Java và xử lý PDF.

## Cài đặt GroupDocs.Annotation cho Java

### Cấu hình Maven thực sự hoạt động
Thêm repository và dependency vào `pom.xml` của bạn đúng như sau:

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

### Sắp xếp giấy phép của bạn
GroupDocs cung cấp một số tùy chọn cấp phép:

- **Free trial** – hoàn hảo cho việc thử nghiệm (không cần thẻ tín dụng)  
- **Temporary license** – lý tưởng cho phát triển và staging  
- **Full license** – bắt buộc cho môi trường production; xem [purchase page](https://purchase.groupdocs.com/buy)

> **Pro tip:** Bắt đầu với bản dùng thử miễn phí để khám phá API, sau đó chuyển sang giấy phép tạm thời khi bạn sẵn sàng xây dựng tính năng thực tế.

### Cài đặt kiểm tra nhanh
Chạy chương trình tối thiểu này để xác nhận thư viện được tải đúng:

```java
import com.groupdocs.annotation.Annotator;

public class DocumentSetup {
    public static void main(String[] args) {
        try {
            Annotator annotator = new Annotator("path/to/your/document.pdf");
            System.out.println("GroupDocs.Annotation is ready to use!");
            annotator.dispose();
        } catch (Exception e) {
            System.out.println("Setup issue: " + e.getMessage());
        }
    }
}
```

Nếu console in ra thông báo thành công mà không có lỗi, bạn đã sẵn sàng để thêm chú thích gạch ngang.

## Cách thêm chú thích gạch ngang java

Dưới đây là một triển khai hoàn chỉnh, sẵn sàng cho production, được chia thành các bước rõ ràng.

### Bước 1 – Khởi tạo Annotator
Tạo một thể hiện `Annotator` trỏ tới tài liệu nguồn:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **Why this matters:** Sử dụng đường dẫn tuyệt đối hoặc đường dẫn tương đối được giải quyết đúng sẽ ngăn lỗi “file not found”.

### Bước 2 – (Tùy chọn) Chuẩn bị trả lời bình luận
Thêm các reply để làm cho chú thích trở nên hợp tác hơn:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

Các bình luận này sẽ xuất hiện khi người dùng di chuột lên gạch ngang.

### Bước 3 – Xác định khu vực gạch ngang
Xác định hình chữ nhật bao quanh văn bản bạn muốn gạch ngang:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **Coordinate tip:** Gốc (0,0) là góc trên‑trái của trang; X tăng sang phải, Y tăng xuống. Sử dụng trình xem PDF hiển thị tọa độ để tinh chỉnh các giá trị này.

### Bước 4 – Cấu hình chú thích gạch ngang
Đặt kiểu hiển thị, số trang và đính kèm các bình luận:

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535);  // Yellow color
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0);
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

*Color note:* `65535` tương ứng với màu vàng trong định dạng RGB nguyên. Thay đổi giá trị để dùng màu khác.

### Bước 5 – Áp dụng chú thích và lưu
Thêm chú thích vào tài liệu và ghi file đầu ra:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### Bước 6 – Dọn dẹp tài nguyên (Quan trọng!)
Luôn giải phóng annotator để giải phóng tài nguyên native:

```java
if (annotator != null) {
    annotator.dispose();
}
```

Trong production, bao bọc việc sử dụng trong khối `try‑with‑resources` hoặc cấu trúc `try/finally`.

## Các vấn đề thường gặp và cách khắc phục

| Vấn đề | Triệu chứng | Cách khắc phục |
|--------|-------------|----------------|
| **File không tìm thấy** | `Annotator` ném ra một ngoại lệ | Sử dụng đường dẫn tuyệt đối, kiểm tra quyền đọc, đảm bảo không có tiến trình khác khóa file |
| **Tọa độ sai** | Gạch ngang xuất hiện ở vị trí không đúng với văn bản mong muốn | Kiểm tra lại hệ thống tọa độ của trình xem PDF; điều chỉnh các điểm cho phù hợp |
| **Chú thích không hiển thị** | Không có gạch ngang hiển thị sau khi lưu | Tăng `opacity` (ví dụ, `0.9`), xác minh `pageNumber` (0‑based), đảm bảo các điểm tạo thành một hình chữ nhật hợp lệ |
| **OutOfMemoryError** | Ứng dụng bị sập khi xử lý PDF lớn | Tăng bộ nhớ heap JVM (`-Xmx2048m`), xử lý tài liệu theo lô, luôn gọi `dispose()` |

## Thực hành tốt về hiệu năng cho môi trường sản xuất

### Quản lý bộ nhớ
```java
// Good: try‑with‑resources (Java 7+)
try (Annotator annotator = new Annotator(documentPath)) {
    // annotation logic here
} // annotator automatically disposed

// Alternative: explicit disposal
Annotator annotator = null;
try {
    annotator = new Annotator(documentPath);
    // annotation logic here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

### Chiến lược xử lý theo lô
Khi bạn cần chú thích hàng chục hoặc hàng trăm file:

- Xử lý 10‑20 tài liệu mỗi lô.  
- Ghi log thành công/thất bại cho mỗi file.  
- Khởi tạo lại `Annotator` cho mỗi tài liệu để tránh rò rỉ bộ nhớ.  

### Mẹo caching
- Lưu cache các mẫu tài liệu thường dùng.  
- Lưu bản đồ tọa độ đã tính trước cho các bố cục chuẩn.  

## Các trường hợp sử dụng thực tế

1. **Hệ thống xem xét tài liệu** – Biên tập viên đề xuất xóa bỏ mà không thay đổi hợp đồng gốc.  
2. **Sửa đổi pháp lý** – Luật sư theo dõi việc loại bỏ các điều khoản trong khi giữ nguyên ngôn ngữ gốc để kiểm toán.  
3. **Đánh giá đồng nghiệp học thuật** – Người đánh giá đánh dấu các phần cần loại bỏ và thêm bình luận nội dòng.  
4. **Di chuyển nội dung** – Trong quá trình di chuyển CMS, gạch ngang làm nổi bật nội dung lỗi thời cần thay thế.  

## Tùy chỉnh nâng cao

### Định dạng tùy chỉnh
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### Thêm metadata
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## Danh sách kiểm tra khắc phục sự cố
- ✅ Bạn có thể mở file nguồn thủ công không?  
- ✅ Tất cả các phụ thuộc GroupDocs có trong classpath không?  
- ✅ Các điểm có tạo thành một hình chữ nhật hợp lệ không?  
- ✅ Số trang có đúng không (0‑based)?  
- ✅ Có đủ bộ nhớ heap không?  
- ✅ Bạn có quyền ghi vào thư mục đầu ra không?  
- ✅ Định dạng tài liệu có được hỗ trợ không (PDF, DOCX, PPTX, v.v.)?  

## Câu hỏi thường gặp

**Q: Có thể sử dụng GroupDocs.Annotation trong một dịch vụ Spring Boot không?**  
A: Có. Thêm phụ thuộc Maven, tiêm một lớp dịch vụ tạo ra `Annotator`, và quản lý vòng đời của nó bằng các phạm vi bean của Spring.

**Q: Các định dạng tài liệu nào hỗ trợ chú thích gạch ngang?**  
A: PDF, DOCX, PPTX và nhiều định dạng khác được GroupDocs.Annotation hỗ trợ. PDF cung cấp khả năng xử lý tọa độ chính xác nhất.

**Q: Làm thế nào để xử lý tài liệu có kích thước trang khác nhau?**  
A: Lấy kích thước trang bằng `annotator.getPageInfo(pageNumber)` và điều chỉnh tọa độ của bạn cho phù hợp.

**Q: Có thể chỉnh sửa hoặc xóa một chú thích gạch ngang hiện có không?**  
A: Chắc chắn. Sử dụng `annotator.getAnnotations(pageNumber)` để lấy, sau đó `annotator.update(updatedAnnotation)` hoặc `annotator.delete(annotationId)`.

**Q: Tác động về hiệu năng khi thêm nhiều chú thích là gì?**  
A: Thêm hàng trăm chú thích thường không vấn đề, nhưng cần giám sát việc sử dụng bộ nhớ. Đối với bộ chú thích rất lớn, hãy cân nhắc phân trang hiển thị hoặc tải lazy các chú thích khi cần.

## Kết luận
Bạn giờ đã có một hướng dẫn đầy đủ, sẵn sàng cho môi trường sản xuất để **add strikeout annotation java** bằng GroupDocs.Annotation. Bắt đầu với ví dụ kiểm tra nhanh đơn giản, sau đó mở rộng lên xử lý theo lô, định dạng tùy chỉnh và bổ sung metadata. Hãy nhớ kiểm tra kỹ tọa độ, quản lý tài nguyên một cách có trách nhiệm, và chọn mô hình giấy phép phù hợp cho môi trường của bạn.

Sẵn sàng khám phá thêm? Hãy xem các loại chú thích khác—đánh dấu, ghi chú, hình ảnh, mũi tên và watermark—để xây dựng một bộ công cụ cộng tác tài liệu đầy đủ tính năng.

**Last Updated:** 2026-03-30  
**Tested With:** GroupDocs.Annotation 25.2 for Java  
**Author:** GroupDocs  

**Tài nguyên bổ sung**

- [Tài liệu GroupDocs Annotation](https://docs.groupdocs.com/annotation/java/)
- [Hướng dẫn tham chiếu API](https://reference.groupdocs.com/annotation/java/)
- [Tải phiên bản mới nhất](https://releases.groupdocs.com/annotation/java/)
- [Mua giấy phép đầy đủ](https://purchase.groupdocs.com/buy)
- [Bắt đầu dùng thử miễn phí](https://releases.groupdocs.com/annotation/java/)
- [Nhận giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/)
- [Diễn đàn hỗ trợ cộng đồng](https://forum.groupdocs.com/c/annotation/)