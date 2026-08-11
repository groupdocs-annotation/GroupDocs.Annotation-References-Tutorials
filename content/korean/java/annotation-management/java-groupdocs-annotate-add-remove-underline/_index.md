---
categories:
- Java Development
date: '2026-03-24'
description: GroupDocs.Annotation을 사용하여 Java에서 깔끔한 PDF 파일을 생성하고, Java PDF 메모리를 관리하며,
  PDF에 주석을 다는 방법을 전체 코드 예제와 문제 해결 팁과 함께 배워보세요.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2026-03-24'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'Java로 깨끗한 PDF 만들기: GroupDocs를 사용한 밑줄 주석'
type: docs
url: /ko/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# 깨끗한 PDF Java 만들기: GroupDocs를 사용한 밑줄 주석

깨끗한 PDF Java 파일을 **create clean PDF Java**하고 협업 주석을 추가해야 한다면, 여기가 바로 맞는 곳입니다. Java 애플리케이션에서 문서 관리 및 협업에 어려움을 겪고 있나요? 혼자가 아닙니다. 많은 개발자들이 다양한 파일 형식에서 안정적으로 작동하는 강력한 문서 주석 기능을 구현하는 데 어려움을 겪고 있습니다.

이 가이드에서는 **create clean PDF Java** 파일을 만들고 GroupDocs.Annotation을 사용하여 **annotate PDF in Java**하는 방법을 배웁니다. 튜토리얼이 끝날 때쯤에는 주석과 함께 밑줄 주석을 추가하고, 기존 주석을 제거하며, 이러한 기능을 프로젝트에 원활히 통합하는 방법을 정확히 알게 될 것입니다.

**이 가이드에서 마스터하게 될 내용:**
- Java 프로젝트에 GroupDocs.Annotation을 설정하기 (올바른 방법)  
- 맞춤형 댓글 및 스타일링으로 밑줄 주석 추가하기  
- 모든 주석을 제거하여 깨끗한 문서 버전 만들기  
- 개발자가 흔히 겪는 일반적인 문제 해결  
- 프로덕션 애플리케이션을 위한 성능 최적화  

문서 검토 시스템, 교육 플랫폼, 또는 협업 편집 도구를 구축하든, 이 튜토리얼은 실용적이고 검증된 코드 예제로 여러분을 지원합니다.

## 빠른 답변
- **밑줄 주석을 어떻게 추가하나요?** `UnderlineAnnotation`과 `annotator.add()`를 사용한 뒤 문서를 저장합니다.  
- **깨끗한 PDF Java 파일을 어떻게 만들 수 있나요?** 주석이 달린 파일을 로드하고 `SaveOptions`에서 `AnnotationType.NONE`을 설정한 뒤 새 복사본을 저장합니다.  
- **필요한 라이브러리는 무엇인가요?** GroupDocs.Annotation v25.2(또는 최신 버전)와 해당 Maven 저장소.  
- **프로덕션에 라이선스가 필요합니까?** 예—워터마크를 방지하려면 유효한 GroupDocs 라이선스를 적용하세요.  
- **여러 문서를 효율적으로 처리할 수 있나요?** 각 `Annotator`를 try‑with‑resources 블록으로 감싸고 파일마다 dispose합니다.

## 깨끗한 PDF Java 파일 만드는 방법
깨끗한 PDF Java 파일을 만든다는 것은 원본 내용을 보존하면서 문서의 **without any annotations** 버전을 생성하는 것을 의미합니다. 이는 최종 배포, 보관, 또는 검토 사이클 후에 “깨끗한” 사본을 공유해야 할 때 유용합니다.

GroupDocs.Annotation을 사용하면 이 작업이 간단합니다: 주석이 달린 파일을 로드하고 `SaveOptions`를 구성하여 모든 주석 유형을 제외한 뒤 결과를 저장합니다. 단계는 아래 **Removing Annotations** 섹션에 나와 있습니다.

## 왜 깨끗한 PDF Java 파일을 만들까요?
깨끗한 버전은 검토자의 표시, 댓글, 하이라이트를 제거하여 고객, 규제 기관 또는 공개 배포에 적합한 다듬어진 문서를 제공합니다. 또한 파일 크기를 줄이고 내부 메모가 실수로 노출되는 것을 방지해 법률 및 컴플라이언스 워크플로에 필수적입니다.

## GroupDocs를 사용해 Java에서 PDF에 주석 달기
GroupDocs.Annotation은 **annotate PDF in Java**를 위한 풍부한 API를 제공합니다. 하이라이트, 스탬프, 밑줄 등 다양한 주석 유형을 지원합니다. 이 튜토리얼에서는 텍스트 강조와 스레드형 댓글을 허용하는 밑줄 주석에 중점을 둡니다.

## 사전 요구 사항 및 환경 설정

### 시작하기 전에 필요한 것

**개발 환경 요구 사항:**  
- Java Development Kit (JDK) 8 이상 (JDK 11+ 권장)  
- Maven 3.6+ 또는 Gradle 6.0+ (의존성 관리)  
- IntelliJ IDEA, Eclipse, 또는 Java 확장이 포함된 VS Code와 같은 IDE  
- 최소 2 GB 사용 가능한 RAM (문서 처리 시 메모리를 많이 사용할 수 있음)

**지식 사전 요구 사항:**  
기본 Java 개념(객체 초기화, 메서드 호출, Maven 의존성)에 익숙해야 합니다. 서드파티 라이브러리 경험이 있으면 도입이 빨라집니다.

**테스트용 문서:**  
샘플 PDF 몇 개를 준비하세요. 텍스트 기반 PDF가 가장 좋으며, 스캔 이미지의 경우 주석을 달기 전에 OCR이 필요할 수 있습니다.

### Maven 설정: 프로젝트에 GroupDocs 가져오기

다음은 Maven 프로젝트를 올바르게 구성하는 방법입니다(첫 시도에서 많은 개발자가 실수합니다):

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

**중요:** 현재 작성 시점에서 최신 안정 버전은 25.2입니다. 버그 수정 및 성능 향상이 포함된 최신 버전을 확인하려면 GroupDocs 저장소를 정기적으로 확인하세요.

### 라이선스 설정 (이 단계는 건너뛰지 마세요)

**개발/테스트용:**  
GroupDocs 웹사이트에서 무료 체험판을 다운로드하세요. 체험판은 모든 기능을 포함하지만 처리된 문서에 워터마크가 추가됩니다.

**프로덕션용:**  
라이선스를 구매하고 애플리케이션 시작 시 적용하세요. 유효한 라이선스가 없으면 프로덕션 빌드에 제한이 있습니다.

## 구현 가이드: 밑줄 주석 추가

### 주석 워크플로 이해하기

코드에 들어가기 전에, **annotate PDF in Java** 시 발생하는 네 단계 워크플로를 살펴보겠습니다:

1. **문서 로드** – `Annotator`가 파일을 메모리로 읽어들입니다.  
2. **주석 생성** – 위치, 스타일, 댓글 등 속성을 정의합니다.  
3. **주석 적용** – 라이브러리가 PDF 구조에 주석을 삽입합니다.  
4. **문서 저장** – 수정된 파일을 영구 저장하며, 필요 시 원본을 보존합니다.

이 과정은 비파괴적이며, 파일을 덮어쓰지 않는 한 원본 파일은 그대로 유지됩니다.

### 단계 1: Annotator 초기화 및 문서 로드

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**팁:** 개발 중에는 절대 경로를 사용해 “파일을 찾을 수 없습니다” 오류를 방지하세요. 프로덕션에서는 클래스패스나 클라우드 스토리지 버킷에서 리소스를 로드하는 것을 고려하세요.

### 단계 2: 댓글 및 답글 생성 (협업 부분)

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

**실제 사용 사례:** 검토자는 스레드형 답글을 추가해 특정 조항에 대해 토론할 수 있으며, 대화가 정확한 주석에 연결됩니다.

### 단계 3: 주석 좌표 정의 (정확한 위치 지정)

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

**좌표 시스템:**  
- 포인트 1 과 2는 밑줄의 상단 가장자리를 정의합니다.  
- 포인트 3 과 4는 하단 가장자리를 정의합니다.  
- Y 차이(730 대 650)는 두께를 제어합니다.

### 단계 4: 밑줄 주석 생성 및 구성

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

**색상 및 불투명도 팁:**  
- `FontColor`는 ARGB를 사용합니다; `65535`(0x00FFFF)는 밝은 노란색을 제공합니다.  
- 빨강은 `16711680`(0xFF0000), 파랑은 `255`(0x0000FF)를 사용합니다.  
- 불투명도 값을 0.5와 0.8 사이로 설정하면 텍스트를 가리지 않으면서 가독성이 좋습니다.

### 단계 5: 주석이 달린 문서 저장

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**메모리 관리:** `dispose()` 호출은 네이티브 리소스를 해제하고 메모리 누수를 방지합니다—배치로 많은 파일을 처리할 때 중요합니다.

## 주석 제거: 깨끗한 문서 버전 만들기

때때로 PDF **without any annotations** 버전이 필요합니다—예를 들어 최종 승인된 계약서를 전달할 때. GroupDocs를 사용하면 간단합니다.

### 주석 제거 옵션 이해하기

다음과 같이 할 수 있습니다:  
- **전체** 주석 제거(가장 일반적)  
- 특정 유형 제거(예: 하이라이트만)  
- 작성자 또는 페이지별 주석 제거

### 단계별 주석 제거

**Step 1: Load the Previously Annotated Document**

```java
Annotator annotator = new Annotator(outputPath);
```

**Step 2: Configure Save Options for a Clean Output**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Step 3: Save the Clean Version**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

이렇게 하면 주석 객체가 전혀 포함되지 않은 **clean PDF Java** 파일이 생성되어 최종 배포에 적합합니다.

## 일반적인 문제와 해결책

### 문제 1: “Document not found” 오류

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

### 문제 2: 주석이 잘못된 위치에 표시됨

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### 문제 3: 대용량 문서의 메모리 문제

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### 문제 4: 프로덕션 라이선스 문제

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

## 프로덕션 애플리케이션을 위한 성능 모범 사례

### 메모리 관리 전략

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

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

### 스레딩 고려 사항

GroupDocs.Annotation은 기본적으로 **thread‑safe**하지 않습니다. 애플리케이션이 문서를 동시에 처리한다면:  
- **절대** `Annotator` 인스턴스를 스레드 간에 공유하지 마세요.  
- 파일 접근을 **동기화**하거나 잠금 메커니즘을 사용하세요.  
- 높은 처리량이 필요하면 **Annotator** 객체 풀을 고려하세요.

### 캐싱 전략

- 자주 사용하는 주석 템플릿을 캐시합니다.  
- `Point` 컬렉션을 공통 좌표 세트에 재사용합니다.  
- 같은 기본 문서를 반복해서 주석 달 경우 **template PDF**를 메모리에 유지합니다.

## Java PDF 메모리 관리 팁

대용량 PDF를 다루거나 배치로 많은 파일을 처리할 때 효율적인 메모리 사용이 필수적입니다. 다음은 몇 가지 실용적인 권장 사항입니다:

- `Annotator`마다 **try‑with‑resources**를 사용해 반드시 해제하도록 합니다.  
- 필요에 따라 **JVM 힙(`-Xmx`)을 늘리되**, 프로파일링 도구로 사용량을 모니터링합니다.  
- 가능하면 **문서를 순차적으로 처리**하고 각 파일 후 메모리를 해제합니다.  
- **같은 PDF를 여러 번 로드하지 않도록**; 반복 읽어야 할 경우 동일 스트림을 재사용합니다.

이러한 실천을 적용하면 애플리케이션이 응답성을 유지하고 대량 주석 작업 중 메모리 부족 오류를 방지할 수 있습니다.

## 실제 적용 사례 및 사용 예시

### 문서 검토 시스템

- **법률 검토:** 계약 조항에 밑줄을 그리고 위험에 대한 댓글을 추가합니다.  
- **컴플라이언스 감사:** 재무제표에서 문제 섹션을 하이라이트합니다.  
- **학술 피어 리뷰:** 교수는 명확히 해야 할 구절에 밑줄을 긋습니다.

### 교육 플랫폼

- **학생 주석 도구:** 학습자가 전자책에서 핵심 개념에 밑줄을 긋게 합니다.  
- **교사 피드백:** 제출된 과제에 직접 인라인 댓글을 제공합니다.

### 품질 보증 워크플로

- **기술 문서 검토:** 엔지니어가 업데이트가 필요한 섹션에 밑줄을 긋습니다.  
- **표준 운영 절차:** 안전 담당자가 중요한 단계에 하이라이트합니다.

### 콘텐츠 관리 시스템

- **편집 워크플로:** 편집자는 사실 확인이 필요한 텍스트에 밑줄을 긋습니다.  
- **버전 관리:** 문서 개정 시 주석 이력을 추적합니다.

## 전문가 구현을 위한 고급 팁

### 사용자 정의 주석 스타일

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### 추적을 위한 주석 메타데이터

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### 사용자 관리 시스템과의 통합

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

## 프로덕션 문제 해결

### 성능 모니터링

프로덕션에서 다음 지표를 모니터링하세요:  
- **Heap 사용량** – `dispose()`가 호출되었는지 확인합니다.  
- **문서당 처리 시간** – `annotator.save()` 전후에 타임스탬프를 기록합니다.  
- **오류 비율** – 예외를 캡처하고 분류합니다.

### 흔히 발생하는 프로덕션 함정

- **파일 잠금** – 주석을 달기 전에 업로드된 파일이 닫혔는지 확인합니다.  
- **동시 편집** – 낙관적 잠금 또는 버전 검사를 구현합니다.  
- **대용량 파일(> 50 MB)** – JVM 타임아웃을 늘리고 스트리밍 API를 고려합니다.

### 오류 처리 모범 사례

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

## 결론

이제 GroupDocs.Annotation을 사용해 **create clean PDF Java** 파일과 **annotate PDF in Java** 밑줄 주석을 추가하는 데 필요한 모든 것을 갖추었습니다. 기억하세요:

- try‑with‑resources 또는 명시적 `dispose()`로 리소스를 관리합니다.  
- 좌표를 초기에 검증해 잘못된 밑줄을 방지합니다.  
- 프로덕션 안정성을 위해 견고한 오류 처리를 구현합니다.  
- 워크플로에 맞게 역할 기반 스타일링 및 메타데이터를 활용합니다.

다음 단계는? 하이라이트, 스탬프, 텍스트 교체 등 다른 주석 유형을 추가해 전체 기능을 갖춘 문서 검토 솔루션을 구축해 보세요.

## 자주 묻는 질문

**Q: 단일 작업으로 텍스트 여러 영역에 주석을 달려면 어떻게 하나요?**  
A: 서로 다른 좌표를 가진 여러 `UnderlineAnnotation` 객체를 생성하고 `annotator.add()`로 순차적으로 추가합니다.

**Q: PDF 문서 내 이미지에 주석을 달 수 있나요?**  
A: 예. 동일한 좌표 시스템을 사용하고, 포인트가 이미지 경계 안에 위치하도록 합니다.

**Q: PDF 외에 GroupDocs.Annotation이 지원하는 파일 형식은 무엇인가요?**  
A: Word(DOC/DOCX), Excel(XLS/XLSX), PowerPoint(PPT/PPTX) 및 JPEG, PNG, TIFF와 같은 이미지 형식.

**Q: 메모리 부족 없이 매우 큰 문서를 처리하려면 어떻게 해야 하나요?**  
A: 문서를 하나씩 처리하고, JVM 힙(`-Xmx`)을 늘리며, `Annotator` 인스턴스를 즉시 dispose합니다.

**Q: 문서에서 기존 주석을 추출할 수 있나요?**  
A: 예. `annotator.get()`을 사용해 모든 주석을 가져온 뒤, 필요에 따라 유형, 작성자, 페이지별로 필터링합니다.

---
**마지막 업데이트:** 2026-03-24  
**테스트 환경:** GroupDocs.Annotation 25.2  
**작성자:** GroupDocs