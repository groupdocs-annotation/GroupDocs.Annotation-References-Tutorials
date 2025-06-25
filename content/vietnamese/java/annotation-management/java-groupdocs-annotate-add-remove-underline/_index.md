---
"date": "2025-05-06"
"description": "Tìm hiểu cách thêm và xóa chú thích gạch chân trong tài liệu Java bằng GroupDocs.Annotation. Nâng cao khả năng quản lý tài liệu của bạn với hướng dẫn chi tiết này."
"title": "Thêm và xóa chú thích gạch chân trong Java bằng GroupDocs&#58; Hướng dẫn toàn diện"
"url": "/vi/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
"weight": 1
---

# Cách triển khai Java: Thêm và xóa chú thích gạch chân bằng GroupDocs

## Giới thiệu

Cải thiện hệ thống quản lý tài liệu của bạn bằng cách thêm hoặc xóa chú thích theo chương trình? Hướng dẫn này hướng dẫn bạn sử dụng thư viện GroupDocs.Annotation mạnh mẽ trong Java để thêm chú thích gạch chân và xóa chúng khỏi các tài liệu như PDF.

**Những gì bạn sẽ học được:**
- Khởi tạo lớp Annotator.
- Thêm chú thích gạch chân kèm theo bình luận bằng GroupDocs.Annotation cho Java.
- Xóa tất cả chú thích khỏi tài liệu.
- Cấu hình môi trường của bạn để sử dụng GroupDocs.Annotation một cách hiệu quả.

Hãy cùng khám phá cách các chức năng này có thể được tận dụng trong các dự án của bạn. Đảm bảo bạn đã đáp ứng các điều kiện tiên quyết cần thiết trước khi bắt đầu.

## Điều kiện tiên quyết

### Thư viện và phụ thuộc bắt buộc
Để thực hiện hướng dẫn này một cách hiệu quả, hãy đảm bảo bạn có:
- **GroupDocs.Annotation cho Java**: Khuyến nghị sử dụng phiên bản 25.2 trở lên.
- **Bộ phát triển Java (JDK)**: Yêu cầu phiên bản 8 trở lên.

### Yêu cầu thiết lập môi trường
Đảm bảo môi trường phát triển của bạn bao gồm một IDE như IntelliJ IDEA hoặc Eclipse và một công cụ xây dựng như Maven.

### Điều kiện tiên quyết về kiến thức
Hiểu biết cơ bản về lập trình Java, đặc biệt là làm việc với các thư viện thông qua Maven, sẽ rất có lợi.

## Thiết lập GroupDocs.Annotation cho Java

Để bắt đầu sử dụng GroupDocs.Annotation trong các dự án Java của bạn, hãy làm theo các bước thiết lập sau:

**Cấu hình Maven:**
Thêm cấu hình sau vào `pom.xml` tệp để tải xuống và tích hợp GroupDocs.Annotation.

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

**Mua giấy phép:**
Bắt đầu bằng cách tải xuống bản dùng thử miễn phí hoặc lấy giấy phép tạm thời từ GroupDocs để khám phá toàn bộ khả năng của thư viện. Đối với mục đích sử dụng sản xuất, cần phải mua giấy phép.

## Hướng dẫn thực hiện

### Tính năng 1: Khởi tạo Annotator và Thêm chú thích gạch chân

Phần này hướng dẫn bạn cách khởi tạo `Annotator` lớp và thêm chú thích gạch chân vào tài liệu của bạn.

#### Tổng quan
Thêm chú thích giúp làm nổi bật các phần cụ thể của tài liệu. Ở đây, chúng tôi tập trung vào việc gạch chân văn bản bằng các bình luận để làm rõ hoặc phản hồi.

#### Thực hiện từng bước

**1. Khởi tạo Annotator**
Tạo một `Annotator` đối tượng và tải tệp PDF của bạn.

```java
import com.groupdocs.annotation.Annotator;

// Tải tài liệu bạn muốn chú thích
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. Tạo bình luận với trả lời**
Xác định các bình luận liên quan đến chú thích gạch chân.

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

**3. Xác định các điểm cho chú thích gạch chân**
Đặt tọa độ để xác định vị trí phần gạch chân sẽ xuất hiện.

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

**4. Tạo và cấu hình chú thích gạch chân**
Tạo chú thích gạch chân và thiết lập các thuộc tính như màu sắc, độ mờ và chú thích.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Màu vàng ở định dạng ARGB
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. Lưu tài liệu đã chú thích**
Lưu thay đổi vào một tập tin mới.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### Mẹo khắc phục sự cố
- Đảm bảo tất cả tọa độ của các điểm đều nằm trong giới hạn tài liệu.
- Xác minh rằng `outputPath` thư mục tồn tại và có thể ghi được.

### Tính năng 2: Lưu tài liệu không có chú thích

Phần này hướng dẫn cách xóa toàn bộ chú thích khỏi tài liệu đã chú thích trước đó.

#### Tổng quan
Bạn có thể cần lưu phiên bản sạch của tài liệu mà không có bất kỳ chú thích nào để chia sẻ hoặc lưu trữ.

#### Thực hiện từng bước

**1. Khởi tạo Annotator với Tài liệu được chú thích**
Tải tài liệu có chú thích hiện có.

```java
Annotator annotator = new Annotator(outputPath);
```

**2. Cấu hình tùy chọn lưu để xóa chú thích**
Chỉ định rằng không có chú thích nào được lưu trong tệp đầu ra.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. Lưu tài liệu mà không có chú thích**
Xác định đường dẫn đến tài liệu đã làm sạch và lưu nó.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## Ứng dụng thực tế

Sau đây là một số tình huống thực tế mà những tính năng này có thể mang lại lợi ích:
1. **Đánh giá tài liệu**: Làm nổi bật và bình luận các phần của hợp đồng hoặc báo cáo để xem xét.
2. **Công cụ giáo dục**: Ghi chú hoặc sửa lỗi vào sách giáo khoa cho học sinh.
3. **Biên tập cộng tác**: Chia sẻ bản thảo có chú thích giữa các thành viên trong nhóm để nhận phản hồi.
4. **Tài liệu pháp lý**:Gạch chân các điều khoản quan trọng trong văn bản pháp lý trong các cuộc thảo luận.
5. **Tài liệu tiếp thị**: Làm nổi bật thông tin quan trọng trong tờ rơi trước khi phân phối.

## Cân nhắc về hiệu suất
Khi làm việc với GroupDocs.Annotation, hãy cân nhắc những mẹo sau để tối ưu hóa hiệu suất:
- **Quản lý bộ nhớ**: Xử lý đúng cách `Annotator` các đối tượng để giải phóng tài nguyên.
- **Xử lý hàng loạt**: Nếu chú thích nhiều tài liệu, hãy xử lý chúng theo từng đợt để quản lý tải hệ thống hiệu quả.
- **Phân bổ nguồn lực**: Đảm bảo môi trường của bạn có đủ bộ nhớ và sức mạnh xử lý để xử lý các tệp lớn.

## Phần kết luận
Bạn đã học cách thêm và xóa chú thích gạch chân bằng GroupDocs.Annotation cho Java. Hướng dẫn này bao gồm khởi tạo lớp Annotator, cấu hình chú thích bằng bình luận và lưu tài liệu mà không có bất kỳ chú thích nào. 

Để khám phá sâu hơn, hãy cân nhắc tích hợp các tính năng này vào hệ thống quản lý tài liệu hiện có của bạn hoặc thử nghiệm các loại chú thích khác do GroupDocs cung cấp.

## Phần Câu hỏi thường gặp
1. **Làm thế nào để cấu hình nhiều chú thích gạch chân trong một lần chạy?**
   - Tạo nhiều `UnderlineAnnotation` các đối tượng và thêm chúng theo trình tự bằng cách sử dụng `annotator.add()` phương pháp.
2. **Tôi có thể chú thích hình ảnh trong tệp PDF bằng thư viện này không?**
   - Có, GroupDocs.Annotation hỗ trợ chú thích hình ảnh trong tài liệu như PDF.
3. **GroupDocs.Annotation hỗ trợ những định dạng tệp nào?**
   - Nó hỗ trợ nhiều định dạng tài liệu khác nhau bao gồm PDF, Word, Excel, v.v.