---
categories:
- Java Development
date: '2026-10-16'
description: GroupDocs를 사용하여 PDF 주석을 Java에서 편집하는 방법을 배우세요. 단계별 코드 예제로 PDF 주석 로드, 수정
  및 관리에 능숙해지세요.
keywords:
- edit pdf annotations java
- modify pdf annotations java
- groupdocs annotation tutorial
lastmod: '2026-10-16'
linktitle: PDF 주석 편집 Java 가이드
og_description: GroupDocs.Annotation을 사용하여 PDF 주석을 Java에서 편집하세요. PDF 코멘트를 효율적으로 로드,
  수정 및 저장하는 방법을 배우고, 단계별 코드와 모범 사례를 확인하세요.
og_image_alt: Guide showing Java code for editing PDF annotations with GroupDocs.Annotation
og_title: PDF 주석 편집 Java – 완전한 GroupDocs 가이드
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Learn how to edit PDF annotations Java using GroupDocs. Master loading,
    modifying, and managing PDF annotations with step‑by‑step code examples.
  headline: Edit PDF annotations java – complete GroupDocs tutorial
  type: TechArticle
- questions:
  - answer: Yes, but you’ll need a commercial license. The free trial is perfect for
      development and testing, but production use requires a paid license. Check the
      pricing page for current options.
    question: Can I use GroupDocs.Annotation for Java in commercial projects?
  - answer: Java 8 is the minimum requirement, but Java 11+ is recommended for better
      performance and security. The library takes advantage of newer JVM optimizations
      when available.
    question: What's the minimum Java version required?
  - answer: Absolutely! It integrates seamlessly with Spring Boot applications. Just
      add the Maven dependency and configure it as a Spring bean if needed. Many developers
      use it in microservices architectures.
    question: Does GroupDocs.Annotation work with Spring Boot?
  - answer: Yes, you can handle password‑protected documents by providing the password
      through `LoadOptions` (see the example above).
    question: Can I process password‑protected PDFs?
  - answer: Use streaming approaches and process annotations in batches. Configure
      your JVM with appropriate heap settings (typically 2‑3× your largest file size)
      and always call `dispose()` to free resources promptly.
    question: How do I handle large PDF files without running out of memory?
  type: FAQPage
tags:
- pdf annotation
- java library
- document management
- groupdocs
- pdf editing
title: PDF 주석 편집 Java – 완전한 GroupDocs 튜토리얼
type: docs
url: /ko/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/
weight: 1
---

# PDF 주석 편집 java: 완전한 GroupDocs 튜토리얼

이 포괄적인 가이드에서는 GroupDocs.Annotation을 사용하여 **PDF 주석을 Java로 편집하는 방법**을 배웁니다. 문서 검토 시스템, e‑learning 플랫폼, 협업 작업 공간을 구축하든, 이 라이브러리는 몇 줄의 Java 코드만으로 PDF 주석을 프로그래밍 방식으로 로드, 수정 및 관리할 수 있게 해줍니다. 실제 예제, 일반적인 함정, 그리고 프로덕션에 적합한 모범 사례를 단계별로 살펴보며 강력한 주석 편집기를 빠르게 구현할 수 있습니다.

## 빠른 답변
- **어떤 라이브러리를 사용하면 PDF 주석을 Java로 편집할 수 있나요?** GroupDocs.Annotation for Java.  
- **라이선스가 필요합니까?** 무료 체험은 개발에 사용할 수 있으며, 프로덕션에는 상업용 라이선스가 필요합니다.  
- **필요한 Java 버전은 무엇인가요?** 최소 Java 8, 권장 Java 11 이상.  
- **대용량 PDF를 효율적으로 처리할 수 있나요?** 예—스트리밍 옵션과 적절한 리소스 해제를 사용하세요.  
- **스레드 안전한가요?** 아니요, 스레드당 별도의 `Annotator` 인스턴스를 생성하세요.

## PDF 주석 편집 Java란 무엇인가요?
Java에서 PDF 주석을 편집한다는 것은 GroupDocs.Annotation을 사용하여 PDF 파일 내부의 주석 객체를 프로그래밍 방식으로 읽고, 변경하고, 추가하거나 삭제하는 것을 의미합니다. 이를 통해 수동 UI 상호작용 없이 자동화된 검토 워크플로를 구현할 수 있습니다. 라이브러리는 저자, 텍스트, 위치, 타임스탬프와 같은 주석 속성에 접근할 수 있는 풍부한 객체 모델을 제공하며, 수정 사항을 원본 또는 새 문서에 다시 저장할 수 있습니다.

## 왜 GroupDocs.Annotation for Java를 선택해야 하나요?
GroupDocs.Annotation for Java는 PDF, Word, Excel 및 50개 이상의 다른 형식에 대한 완전한 프로그래밍 제어를 제공하여 몇 줄의 코드만으로 주석을 생성, 수정, 삭제 및 관리할 수 있게 해줍니다. 외부 종속성이 없으며 대용량 처리, 강력한 보안 기능, 상세한 문서 및 신속한 지원을 제공하므로 엔터프라이즈급 애플리케이션에 적합합니다.

**Key advantages you'll appreciate:**
- **의존성 문제 없음** – Maven으로 바로 사용 가능  
- **포맷 유연성** – PDF, Word, Excel 및 **50+** 기타 포맷을 처리합니다.  
- **엔터프라이즈 준비** – 대용량 문서 처리용으로 구축되었습니다.  
- **활발한 개발** – 정기적인 업데이트와 뛰어난 지원.  

## 이 튜토리얼에서 마스터할 내용
이 가이드를 끝낼 때쯤이면 다음을 자신 있게 수행할 수 있습니다:

- Maven 또는 Gradle을 사용한 모든 Java 프로젝트에 GroupDocs.Annotation 설정하기  
- 기존 주석이 포함된 PDF를 로드하고 내용을 검사하기  
- **PDF 주석을 Java로 편집** – 속성, 텍스트 및 답글을 프로그래밍 방식으로 수정  
- 엣지 케이스와 일반 오류를 우아하게 처리하기  
- 대용량 문서와 고볼륨 처리에 대한 성능 최적화  
- 프로덕션 환경을 위한 모범 사례 구현  

## 전제 조건 및 환경 설정
개발 환경을 준비해 봅시다. 걱정하지 마세요 – 대부분의 Java 라이브러리 설정보다 간단합니다.

### 필요 사항
**Essential requirements**
- **Java 8 이상** (성능 향상을 위해 Java 11+ 권장)  
- **Maven 3.6+** 또는 Gradle 6+ 의존성 관리용  
- **기본 Java 지식** – 파일 I/O와 컬렉션에 익숙함  
- **선호하는 IDE** – IntelliJ IDEA, Eclipse, VS Code 모두 정상 작동  

**Optional but helpful**
- 테스트용 기존 주석이 포함된 샘플 PDF 파일  
- PDF 구조에 대한 기본 이해 (있으면 좋지만 필수는 아님)  

### 빠른 환경 점검
코딩을 시작하기 전에 다음 빠른 점검을 실행하여 모든 것이 준비되었는지 확인하세요:

```bash
java -version  # Should show Java 8+
mvn -version   # Should show Maven 3.6+
```

## GroupDocs.Annotation for Java 설정

### Maven 구성 간단히
프로젝트에 GroupDocs.Annotation을 추가하는 것은 간단합니다. `pom.xml`에 다음 스니펫을 추가하세요:

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

**Pro tip:** 항상 최신 버전 번호를 사용하세요. 현재 버전은 25.2이지만, 더 최신 버전이 있을 수 있습니다.

### 라이선스 설정 (놓치지 마세요!)
GroupDocs.Annotation은 전체 기능을 위해 라이선스가 필요합니다. 올바르게 처리하는 방법은 다음과 같습니다:

**개발 단계:** 무료 체험을 시작하세요 – 학습 및 소규모 프로젝트에 적합합니다.  

**프로덕션 준비:** 임시 라이선스(확장 평가에 적합) 또는 정식 상업용 라이선스가 필요합니다.  

**License implementation:**

```java
import com.groupdocs.annotation.License;

public class InitializeGroupDocs {
    public static void main(String[] args) {
        // Apply GroupDocs license
        License license = new License();
        license.setLicense("path/to/your/license.lic");
        
        System.out.println("GroupDocs.Annotation for Java is initialized.");
    }
}
```

**일반적인 라이선스 문제**
- **File not found errors:** 라이선스 파일 경로를 다시 확인하세요  
- **Invalid license:** 라이선스가 GroupDocs.Annotation 버전과 일치하는지 확인하세요  
- **Expired license:** 임시 라이선스는 기간 제한이 있으니 필요에 따라 갱신하세요  

## 핵심 구현: Java PDF 주석 편집기

### 기존 주석이 포함된 문서 로드
`LoadOptions`는 GroupDocs.Annotation이 PDF를 읽는 방식을 구성하여 메모리 사용량 및 파싱 동작을 제어합니다. 이는 대부분의 주석 워크플로에서 시작점이 됩니다. 문서 검토 시스템을 구축하거나 협업 기능을 추가하든, 이미 주석이 포함된 PDF를 자주 다루게 됩니다.

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.options.LoadOptions;

public class LoadDocumentWithAnnotations {
    public static void main(String[] args) {
        String inputPath = "YOUR_DOCUMENT_DIRECTORY/ANNOTATED_WITH_REPLIES_NEW.pdf";
        
        // Create load options (optional configuration)
        LoadOptions loadOptions = new LoadOptions();
        
        // Initialize Annotator
        final Annotator annotator = new Annotator(inputPath, loadOptions);
        
        System.out.println("Document loaded successfully.");
    }
}
```

**What's happening here:** `LoadOptions` 객체는 문서 로드 방식을 세밀하게 제어합니다. 여기서는 기본값을 사용하지만, 메모리 사용량, 파싱 옵션 등을 특정 요구에 맞게 구성할 수 있습니다.

**Real‑world considerations**
- **File paths:** 프로덕션에서는 절대 경로를 사용해 배포 문제를 방지하세요  
- **Error handling:** 파일 작업은 항상 `try‑catch` 블록으로 감싸세요  
- **Memory management:** 대용량 PDF의 경우 스트리밍 옵션을 고려하세요  

### 주석 검색 및 검사
`AnnotationBase`는 라이브러리가 반환하는 모든 주석 유형을 나타내는 추상 기본 클래스입니다. 문서를 로드한 후에는 변경하기 전에 기존 주석을 검사해야 할 경우가 많습니다. 이는 주석을 검증, 보고 또는 선택적으로 수정해야 하는 애플리케이션에 필수적입니다.

```java
import com.groupdocs.annotation.models.annotationmodels.AnnotationBase;
import java.util.List;

public class RetrieveAnnotations {
    public static void main(String[] args) {
        String inputPath = "YOUR_DOCUMENT_DIRECTORY/ANNOTATED_WITH_REPLIES_NEW.pdf";
        
        LoadOptions loadOptions = new LoadOptions();
        final Annotator annotator = new Annotator(inputPath, loadOptions);
        
        // Retrieve annotations
        List<AnnotationBase> annotations = annotator.get();
        
        if (!annotations.isEmpty()) {
            System.out.println("Annotations retrieved successfully.");
        } else {
            System.out.println("No annotations found.");
        }
    }
}
```

**Understanding the results:** `get()` 메서드는 모든 주석을 포함하는 `List<AnnotationBase>`를 반환합니다. 각 주석 객체에는 위치, 내용, 저자, 생성 날짜 및 연관된 답글과 같은 속성이 포함됩니다.

**Practical applications**
- **Audit trails:** 누가 언제 어떤 주석을 추가했는지 추적  
- **Content filtering:** 문서 공유 전 민감 정보 제거  
- **Statistics:** 주석 사용 및 협업 패턴에 대한 보고서 생성  

### 주석 답글 수정
`AnnotationReply`는 주석에 첨부된 단일 답글을 나타내며 저자, 텍스트 및 타임스탬프를 포함합니다. 협업 환경에서 가장 일반적인 작업 중 하나는 주석 답글을 관리하는 것입니다. 사용자는 부적절한 답글을 삭제하거나 오래된 정보를 업데이트하거나 길어진 토론 스레드를 정리하고 싶어 할 수 있습니다.

```java
import com.groupdocs.annotation.models.annotationmodels.AnnotationBase;
import java.util.List;

public class RemoveReplyFromAnnotation {
    public static void main(String[] args) {
        String inputPath = "YOUR_DOCUMENT_DIRECTORY/ANNOTATED_WITH_REPLIES_NEW.pdf";
        
        LoadOptions loadOptions = new LoadOptions();
        final Annotator annotator = new Annotator(inputPath, loadOptions);
        
        List<AnnotationBase> annotations = annotator.get();
        
        if (!annotations.isEmpty()) {
            // Remove the first reply of the first annotation
            annotations.get(0).getReplies().remove(0);
        }
    }
}
```

**Safety first:** 주석 및 답글이 존재하는지 항상 확인한 후 수정 작업을 시도하세요. 위 코드는 최소 하나의 주석과 최소 하나의 답글이 존재한다는 전제하에 작성되었습니다.

**Better error‑handling approach:**

```java
if (!annotations.isEmpty() && !annotations.get(0).getReplies().isEmpty()) {
    annotations.get(0).getReplies().remove(0);
    System.out.println("Reply removed successfully.");
} else {
    System.out.println("No replies to remove.");
}
```

### 변경 사항 저장
`Annotator.save`는 메모리 내 모든 주석 수정 사항을 PDF 파일에 다시 씁니다. 모든 주석 워크플로의 마지막 단계는 변경 사항을 영구 저장하는 것입니다. GroupDocs.Annotation은 이를 간단히 처리하지만, 프로덕션 사용 시 고려해야 할 중요한 사항이 있습니다.

```java
import com.groupdocs.annotation.models.annotationmodels.AnnotationBase;
import java.util.List;

public class SaveChangesToDocument {
    public static void main(String[] args) {
        String inputPath = "YOUR_DOCUMENT_DIRECTORY/ANNOTATED_WITH_REPLIES_NEW.pdf";
        String outputPath = "YOUR_OUTPUT_DIRECTORY/ModifiedDocument.pdf";
        
        LoadOptions loadOptions = new LoadOptions();
        final Annotator annotator = new Annotator(inputPath, loadOptions);
        
        List<AnnotationBase> annotations = annotator.get();
        annotator.update(annotations);
        
        // Save changes
        annotator.save(outputPath);
        annotator.dispose();  // Free resources
        
        System.out.println("Changes saved successfully.");
    }
}
```

**Critical points**
- **Always call `dispose()`** – 메모리 누수를 방지합니다, 특히 고볼륨 애플리케이션에서 중요합니다  
- **Use different output paths** – 개발 중에 원본 파일을 절대 덮어쓰지 마세요  
- **Check write permissions** – 애플리케이션이 출력 디렉터리에 쓰기 권한이 있는지 확인하세요  

## 일반적인 문제 및 해결책
수백 명의 개발자가 PDF 주석 기능을 구현하도록 도와오면서 반복적으로 나타나는 문제와 해결책을 정리했습니다.

### 대용량 PDF 메모리 문제
**Problem:** 대용량 PDF 파일(>50 MB) 처리 시 애플리케이션이 메모리 부족 현상을 겪습니다.  
**Solution:** 스트리밍 옵션과 적절한 리소스 관리를 사용하세요:

```java
// Configure load options for large files
LoadOptions loadOptions = new LoadOptions();
// Additional memory optimization settings can be configured here

try (Annotator annotator = new Annotator(inputPath, loadOptions)) {
    // Process annotations in batches if needed
    List<AnnotationBase> annotations = annotator.get();
    
    // Process in smaller chunks for very large annotation lists
    for (int i = 0; i < annotations.size(); i += 100) {
        int end = Math.min(i + 100, annotations.size());
        List<AnnotationBase> batch = annotations.subList(i, end);
        // Process batch
    }
} // Automatic resource cleanup
```

### 주석 위치 문제
**Problem:** 수정 후 주석이 잘못된 위치에 표시됩니다.  
**Solution:** 좌표계와 페이지 참조를 항상 보존하세요:

```java
// When modifying annotation positions, maintain the coordinate system
AnnotationBase annotation = annotations.get(0);
// Preserve original page number and coordinate system
double originalX = annotation.getBox().getX();
double originalY = annotation.getBox().getY();
```

### 성능 병목 현상
**Problem:** 프로덕션 환경에서 주석 처리 속도가 느립니다.  
**Solutions**  
- **Batch operations:** `update()` 호출 전에 여러 변경을 그룹화  
- **Selective loading:** 실제 수정이 필요한 주석만 로드  
- **Connection pooling:** 많은 파일을 처리할 경우 가능한 `Annotator` 인스턴스를 재사용  

## 프로덕션 사용을 위한 모범 사례

### 리소스 관리
try‑with‑resources 또는 명시적 해제를 항상 사용하세요:

```java
// Preferred approach
try (Annotator annotator = new Annotator(inputPath)) {
    // Your annotation processing code
} // Automatic cleanup

// Alternative approach
Annotator annotator = null;
try {
    annotator = new Annotator(inputPath);
    // Process annotations
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

### 오류 처리 전략
견고한 애플리케이션을 위해 포괄적인 오류 처리를 구현하세요:

```java
public class RobustAnnotationProcessor {
    public boolean processAnnotations(String inputPath, String outputPath) {
        try (Annotator annotator = new Annotator(inputPath)) {
            List<AnnotationBase> annotations = annotator.get();
            
            // Validate annotations exist
            if (annotations.isEmpty()) {
                System.out.println("No annotations found to process.");
                return false;
            }
            
            // Process annotations safely
            for (AnnotationBase annotation : annotations) {
                if (annotation.getReplies() != null && !annotation.getReplies().isEmpty()) {
                    // Safe reply processing
                }
            }
            
            annotator.update(annotations);
            annotator.save(outputPath);
            return true;
            
        } catch (Exception e) {
            System.err.println("Error processing annotations: " + e.getMessage());
            return false;
        }
    }
}
```

## 실제 구현 예시

### 법률 문서 검토 시스템
```java
public class LegalDocumentProcessor {
    public boolean processLegalReview(String documentPath, String reviewerName) {
        try (Annotator annotator = new Annotator(documentPath)) {
            List<AnnotationBase> annotations = annotator.get();
            
            // Filter annotations by reviewer
            annotations.stream()
                .filter(annotation -> reviewerName.equals(annotation.getCreatedBy()))
                .forEach(annotation -> {
                    // Process reviewer-specific annotations
                    System.out.println("Processing annotation by: " + reviewerName);
                });
                
            return true;
        } catch (Exception e) {
            System.err.println("Legal document processing failed: " + e.getMessage());
            return false;
        }
    }
}
```

### 교육 피드백 플랫폼
```java
public class EducationalAnnotationManager {
    public void processStudentSubmission(String submissionPath, String feedbackPath) {
        try (Annotator annotator = new Annotator(submissionPath)) {
            List<AnnotationBase> annotations = annotator.get();
            
            // Add teacher feedback while preserving student annotations
            // Implementation would go here
            
            annotator.save(feedbackPath);
            System.out.println("Feedback added successfully.");
        } catch (Exception e) {
            System.err.println("Failed to process student submission: " + e.getMessage());
        }
    }
}
```

## 추가 주제

### 비밀번호 보호 PDF 처리
```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("your-pdf-password");
```

### 주석 데이터 내보내기
GroupDocs.Annotation은 직접적인 JSON/XML 내보내기를 제공하지 않지만, Jackson과 같은 라이브러리를 사용해 `AnnotationBase` 객체를 직렬화하여 다른 시스템과 연동할 수 있습니다.

### Docker에 배포
GroupDocs.Annotation은 컨테이너에서 잘 작동합니다. Java 런타임과 충분한 메모리를 할당하고, 라이선스 파일을 볼륨으로 마운트하거나 이미지에 포함시키세요.

### 클라우드 스토리지와 연동
AWS S3, Google Cloud 등에서 파일을 임시 로컬 경로로 다운로드한 뒤 GroupDocs로 처리하고, 결과를 다시 클라우드 스토리지에 업로드합니다.

## 자주 묻는 질문

**Q: Can I use GroupDocs.Annotation for Java in commercial projects?**  
**A:** 예, 상업용 라이선스가 필요합니다. 무료 체험은 개발 및 테스트에 적합하지만, 프로덕션 사용에는 유료 라이선스가 필요합니다. 현재 옵션은 가격 페이지를 확인하세요.

**Q: What's the minimum Java version required?**  
**A:** 최소 Java 8이 필요하지만, 더 나은 성능과 보안을 위해 Java 11+을 권장합니다. 라이브러리는 최신 JVM 최적화를 활용합니다.

**Q: Does GroupDocs.Annotation work with Spring Boot?**  
**A:** 물론입니다! Spring Boot 애플리케이션에 원활히 통합됩니다. Maven 의존성을 추가하고 필요에 따라 Spring Bean으로 구성하면 됩니다. 많은 개발자가 마이크로서비스 아키텍처에서 사용합니다.

**Q: Can I process password‑protected PDFs?**  
**A:** 예, `LoadOptions`에 비밀번호를 제공하면 비밀번호 보호 PDF를 처리할 수 있습니다(위 예시 참고).

**Q: How do I handle large PDF files without running out of memory?**  
**A:** 스트리밍 방식을 사용하고 주석을 배치로 처리하세요. JVM 힙 설정을 적절히 구성하고(보통 가장 큰 파일 크기의 2‑3배) `dispose()`를 호출해 리소스를 즉시 해제합니다.

**Q: Is the library thread‑safe for concurrent processing?**  
**A:** `Annotator` 클래스는 스레드 안전하지 않습니다. 동시 처리 시 스레드당 별도 `Annotator` 인스턴스를 만들거나 적절히 동기화하세요.

**Q: What happens if I try to modify a corrupted PDF?**  
**A:** 손상된 파일을 만나면 예외가 발생합니다. 항상 오류 처리를 구현하고 처리 전에 PDF 유효성을 검증하세요.

**Q: Can I extract annotation data to JSON or XML?**  
**A:** 라이브러리는 직접 JSON/XML로 내보내지는 않지만, Java 내장 직렬화 또는 Jackson과 같은 라이브러리를 사용해 쉽게 주석 데이터를 직렬화할 수 있습니다.

**Q: How do I deploy this in a Docker container?**  
**A:** Java 런타임을 포함하고 충분한 메모리를 할당한 뒤 라이선스 파일을 마운트하면 됩니다. 컨테이너 내부에서 별도 수정 없이 작동합니다.

**Q: Can I use this with cloud storage (AWS S3, Google Cloud)?**  
**A:** 예, 파일을 로컬에 다운로드한 뒤 처리하고 결과를 다시 업로드해야 합니다. 라이브러리는 로컬 파일 경로만 지원하며 클라우드 URL을 직접 다루지는 못합니다.

## 리소스
- [Complete API Reference](https://reference.groupdocs.com/annotation/java/) – GroupDocs.Annotation Java에 대한 상세 API 문서.  
- [Developer Guide](https://docs.groupdocs.com/annotation/java/) – 개발자를 위한 단계별 가이드.  
- [Release Notes](https://releases.groupdocs.com/annotation/java/release-notes/) – 최신 변경 사항 및 버전 기록.  
- [GroupDocs Forum](https://forum.groupdocs.com/c/annotation) – 커뮤니티 지원 및 토론.  
- [Free Support Portal](https://helpdesk.groupdocs.com/) – 지원 티켓 제출.  
- [GitHub Examples](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java) – 샘플 프로젝트 및 코드 스니펫.

**마지막 업데이트:** 2026-10-16  
**테스트 환경:** GroupDocs.Annotation 25.2 for Java  
**작성자:** GroupDocs

## 관련 튜토리얼

- [PDF 하이라이트 생성 Java: GroupDocs Annotation 완전 가이드](/annotation/java/annotation-management/)  
- [PDF 주석 추출 자동화 GroupDocs Java](/annotation/java/annotation-management/automate-pdf-annotation-extraction-groupdocs-java/)  
- [GroupDocs Annotation Java 텍스트 삭제 튜토리얼](/annotation/java/annotation-management/groupdocs-annotation-java-text-redaction-tutorial/)