---
date: '2026-10-16'
description: Java에서 PDF를 annotations 없이 저장하는 방법을 배우고, java pdf memory management에
  능숙해지며, GroupDocs.Annotation을 사용하여 underline annotations를 추가하는 단계별 가이드.
keywords:
- save pdf without annotations
- java pdf memory management
- java document review system
- groupdocs annotation tutorial
- underline annotation java
lastmod: '2026-10-16'
linktitle: GroupDocs와 함께하는 Java Document Annotation
og_description: Java에서 PDF를 annotations 없이 저장하는 방법을 배우고, java pdf memory management에
  능숙해지며, GroupDocs.Annotation을 사용하여 underline annotations를 추가하는 단계별 가이드.
og_image_alt: 'Developer guide: Save PDF without annotations in Java using GroupDocs.Annotation'
og_title: Java에서 GroupDocs를 사용하여 annotations 없이 PDF 저장하는 방법
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  headline: How to save PDF without annotations in Java using GroupDocs
  type: TechArticle
- description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  name: How to save PDF without annotations in Java using GroupDocs
  steps:
  - name: initialize the annotator and load your document
    text: '`Annotator` is the main entry point in GroupDocs.Annotation for loading
      and modifying PDF documents. It abstracts file‑system handling, stream management,
      and native resource allocation. **Pro tip:** Use absolute paths while developing
      to avoid “file not found” errors. In production, consider loadin'
  - name: creating comments and replies (the collaborative part)
    text: '`Comment` objects represent threaded discussion attached to an annotation.
      Each comment can have an author, a timestamp, and optional replies, enabling
      a full conversation around a specific markup. **Real‑world use:** Reviewers
      can discuss a specific clause by adding threaded replies, keeping the co'
  - name: defining annotation coordinates (getting the position right)
    text: '`Point` defines a single coordinate in PDF space (measured in points, where
      72 points = 1 inch). Four points are required for an underline: two for the
      start line and two for the end line. **Coordinate system:** - Points 1 & 2 define
      the top edge of the underline. - Points 3 & 4 define the bottom ed'
  - name: creating and configuring the underline annotation
    text: '`UnderlineAnnotation` is the concrete class that represents an underline
      markup. It inherits from the base `Annotation` class and adds properties specific
      to underlines, such as line thickness and style. **Color & opacity tips:** -
      `FontColor` uses ARGB; `65535` (0x00FFFF) yields bright yellow. - Fo'
  - name: saving your annotated document
    text: '`SaveOptions` lets you control the output format, whether to embed annotations,
      and how to handle metadata. Setting `AnnotationType.NONE` instructs the library
      to strip all annotation objects, which is the key to **save PDF without annotations**.
      **Memory management:** The `dispose()` call releases '
  type: HowTo
- questions:
  - answer: Create several `UnderlineAnnotation` objects with different coordinates
      and add them sequentially using `annotator.add()`.
    question: How do I annotate multiple areas of text in a single operation?
  - answer: Yes. Use the same coordinate system, ensuring the points lie inside the
      image bounds.
    question: Can I annotate images within PDF documents?
  - answer: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), and image formats
      such as JPEG, PNG, TIFF.
    question: What file formats besides PDF does GroupDocs.Annotation support?
  - answer: Process documents one at a time, increase the JVM heap (`-Xmx`), and always
      dispose of `Annotator` instances promptly.
    question: How do I handle very large documents without running out of memory?
  - answer: Yes. Use `annotator.get()` to retrieve all annotations, then filter by
      type, author, or page as needed.
    question: Is it possible to extract existing annotations from a document?
  type: FAQPage
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
- java pdf memory management
title: Java에서 GroupDocs를 사용하여 annotations 없이 PDF 저장하는 방법
type: docs
url: /ko/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Java와 GroupDocs를 사용하여 주석 없이 PDF 저장하는 방법

주석 없이 PDF를 **save PDF without annotations** 하면서 협업형 밑줄 메모를 추가할 수 있다면, 여기가 바로 정답입니다. 많은 Java 개발자들이 최종 배포를 위한 문서의 깔끔한 버전을 유지하는 데 어려움을 겪고 있습니다. 특히 같은 파일을 반복 검토에 사용할 때 그렇습니다. 이 튜토리얼에서는 깨끗한 PDF를 생성하고, 메모리를 효율적으로 관리하며, GroupDocs.Annotation을 사용해 주석과 댓글이 포함된 밑줄을 적용하는 방법을 배웁니다. 끝까지 읽으면 PDF 로드부터 워터마크 없는 최종 사본 생성까지 전체 워크플로우를 이해하고, 견고한 **java document review system** 구축을 위한 모범 사례 팁도 얻을 수 있습니다.

## 빠른 답변
- **밑줄 주석을 어떻게 추가하나요?** `UnderlineAnnotation`을 `annotator.add()`와 함께 사용한 다음 문서를 저장합니다.  
- **주석 없이 PDF를 어떻게 저장하나요?** 주석이 포함된 파일을 로드하고, `SaveOptions`에서 `AnnotationType.NONE`을 설정한 뒤 새 복사본을 저장합니다.  
- **필요한 라이브러리는 무엇인가요?** GroupDocs.Annotation v25.2(또는 최신)와 해당 Maven 저장소.  
- **프로덕션에 라이선스가 필요합니까?** 예—워터마크를 방지하려면 유효한 GroupDocs 라이선스를 적용하십시오.  
- **여러 문서를 효율적으로 처리할 수 있나요?** `Annotator`를 각각 try‑with‑resources 블록으로 감싸고 파일마다 dispose합니다.

## Java에서 주석 없이 PDF를 저장하는 방법은?
소스 PDF를 `Annotator`로 로드하고, `SaveOptions`를 구성하여 모든 주석 유형을 제외한 뒤 `save()`를 호출해 깨끗한 복사본을 작성합니다. 이 작업은 원본 파일을 수정하지 않으므로 검토자를 위한 주석이 포함된 버전과 배포용 깨끗한 버전을 모두 보유할 수 있습니다. 이 프로세스는 내부적으로 스트리밍을 사용하므로 전체 문서가 메모리에 완전히 로드되지 않아 대용량 PDF에 필수적입니다.

## 주석 없이 PDF 저장이란 무엇인가요?
`save pdf without annotations`은 모든 주석 객체(하이라이트, 댓글, 스탬프, 밑줄 등)를 제거한 채 PDF 문서를 내보내는 것을 의미합니다. 결과 파일은 원본 내용과 레이아웃만 포함하므로 법적 제출, 공개 배포 또는 보관에 적합합니다.

## java 문서 검토 시스템에서 깨끗한 PDF 파일을 만드는 이유는?
깨끗한 버전은 검토자의 표시, 댓글 및 하이라이트를 제거하여 고객, 규제 기관 또는 공개 배포에 적합한 다듬어진 문서를 제공합니다. 또한 평균적으로 파일 크기를 최대 30 %까지 줄이고 내부 메모가 실수로 노출되는 것을 방지합니다—법률 및 컴플라이언스 워크플로에 중요합니다. GroupDocs.Annotation은 한 번에 모든 주석 객체를 제거할 수 있으며, 전체 파일을 메모리에 로드하지 않고도 최대 500 MB PDF를 지원합니다.

## 사전 요구 사항 및 환경 설정

### 시작 전 요구 사항
- Java Development Kit (JDK) 8 이상 (JDK 11+ 권장)  
- Maven 3.6+ 또는 Gradle 6.0+ 의존성 관리  
- IntelliJ IDEA, Eclipse 또는 Java 확장이 포함된 VS Code와 같은 IDE  
- 사용 가능한 RAM 최소 2 GB (문서 처리 시 메모리 사용량이 많을 수 있음)

### Knowledge prerequisites
기본 Java 개념—객체 초기화, 메서드 호출 및 Maven 의존성에 익숙해야 합니다. 타사 라이브러리 경험이 있으면 도입이 빨라집니다.

### Testing documents
몇 개의 샘플 PDF를 준비하십시오. 텍스트 기반 PDF가 가장 좋으며, 스캔된 이미지의 경우 주석을 달기 전에 OCR이 필요할 수 있습니다.

### Maven 설정: 프로젝트에 GroupDocs 추가
`pom.xml`에 다음 의존성을 추가합니다. 이 단계는 그룹 ID와 아티팩트 ID가 정확히 일치해야 하기 때문에 많은 개발자들이 처음에 실수합니다.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```

**Important:** Version 25.2는 현재 최신 안정 버전입니다. 버그 수정 및 성능 향상이 포함된 최신 버전을 확인하려면 GroupDocs 저장소를 정기적으로 확인하십시오.

### 라이선스 설정 (생략 금지)
**개발/테스트용** – GroupDocs 웹사이트에서 무료 체험판을 다운로드하십시오. 체험판은 모든 기능을 포함하지만 처리된 문서에 워터마크가 추가됩니다.

**프로덕션용** – 라이선스를 구매하고 애플리케이션 시작 시 적용하십시오. 유효한 라이선스가 없으면 프로덕션 빌드에 제한이 걸리고 워터마크가 삽입됩니다.

## 구현 가이드: 밑줄 주석 추가

### 주석 워크플로 이해
코드에 들어가기 전에, **Java에서 PDF에 주석을 달 때** 발생하는 네 단계 워크플로를 살펴보겠습니다:

1. **문서 로드** – `Annotator`가 파일을 메모리로 읽습니다.  
2. **주석 생성** – 위치, 스타일 및 댓글과 같은 속성을 정의합니다.  
3. **주석 적용** – 라이브러리가 PDF 구조에 주석을 삽입합니다.  
4. **문서 저장** – 수정된 파일을 영구 저장하고, 필요에 따라 원본을 보존합니다.

이 프로세스는 비파괴적이며, 소스 파일은 덮어쓰지 않는 한 그대로 유지됩니다.

### 단계 1: annotator 초기화 및 문서 로드
`Annotator`는 PDF 문서를 로드하고 수정하기 위한 GroupDocs.Annotation의 주요 진입점입니다. 파일 시스템 처리, 스트림 관리 및 네이티브 리소스 할당을 추상화합니다.

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

**Pro tip:** 개발 중에는 절대 경로를 사용하여 “파일을 찾을 수 없습니다” 오류를 방지하십시오. 프로덕션에서는 클래스패스나 클라우드 스토리지 버킷에서 리소스를 로드하는 것을 고려하십시오.

### 단계 2: 댓글 및 회신 생성 (협업 부분)
`Comment` 객체는 주석에 연결된 스레드형 토론을 나타냅니다. 각 댓글은 작성자, 타임스탬프 및 선택적 회신을 가질 수 있어 특정 마크업에 대한 전체 대화를 가능하게 합니다.

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**실제 사용 사례:** 검토자는 스레드형 회신을 추가하여 특정 조항에 대해 토론하고, 대화를 정확한 주석에 연결할 수 있습니다.

### 단계 3: 주석 좌표 정의 (정확한 위치 지정)
`Point`는 PDF 좌표계에서 단일 좌표를 정의합니다(포인트 단위, 72 포인트 = 1 인치). 밑줄에는 네 개의 포인트가 필요합니다: 시작선 두 개와 끝선 두 개.

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

**Coordinate system:**
- 포인트 1 과 2는 밑줄의 상단 가장자리를 정의합니다.  
- 포인트 3 과 4는 하단 가장자리를 정의합니다.  
- Y 차이(730 대 650)가 두께를 제어합니다.

### 단계 4: 밑줄 주석 생성 및 구성
`UnderlineAnnotation`은 밑줄 마크업을 나타내는 구체 클래스입니다. 기본 `Annotation` 클래스를 상속하고, 선 두께와 스타일 등 밑줄에 특화된 속성을 추가합니다.

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

**Color & opacity tips:**
- `FontColor`는 ARGB를 사용합니다; `65535`(0x00FFFF)는 밝은 노란색을 제공합니다.  
- 빨강은 `16711680`(0xFF0000), 파랑은 `255`(0x0000FF)를 사용합니다.  
- 불투명도 값을 0.5와 0.8 사이로 설정하면 텍스트를 가리지 않으면서 가독성이 좋습니다.

### 단계 5: 주석이 포함된 문서 저장
`SaveOptions`를 사용하면 출력 형식, 주석 포함 여부 및 메타데이터 처리 방식을 제어할 수 있습니다. `AnnotationType.NONE`을 설정하면 라이브러리가 모든 주석 객체를 제거하도록 지시하며, 이는 **save PDF without annotations**의 핵심입니다.

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

**메모리 관리:** `dispose()` 호출은 네이티브 리소스를 해제하고 메모리 누수를 방지합니다—다수의 파일을 배치 처리할 때 중요합니다.

## 주석 제거: 깨끗한 문서 버전 만들기
때때로 PDF **주석 없이** 버전이 필요합니다—예를 들어 최종 승인된 계약서를 전달할 때. GroupDocs는 이를 쉽게 처리합니다.

### 주석 제거 옵션 이해
- **전체** 주석 제거(가장 일반적)  
- 특정 유형 제거(예: 하이라이트만)  
- 작성자 또는 페이지별 주석 제거  

### 단계별 주석 제거
**단계 1: 이전에 주석이 달린 문서 로드**
`Annotator`가 다시 로더 역할을 하며, 주석 객체가 포함된 파일을 읽습니다.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**단계 2: 깨끗한 출력용 저장 옵션 구성**
`SaveOptions`는 출력 파일에 주석 유형이 기록되지 않도록 지정하는 유창한 API를 제공합니다.

```java
Annotator annotator = new Annotator(outputPath);
```

**단계 3: 깨끗한 버전 저장**
구성된 옵션으로 `save()`를 호출하면 원본 내용만 포함된 PDF가 작성됩니다.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

이렇게 하면 주석 객체가 전혀 없는 **clean PDF** 파일이 생성되어 최종 배포에 적합합니다.

## 일반적인 문제 및 해결책

### 문제 1: “Document not found” 오류
파일 경로가 올바르고 애플리케이션에 읽기 권한이 있는지 확인하십시오. 절대 경로와 함께 `Path.of()`를 사용하면 대부분의 모호성을 없앨 수 있습니다.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

### 문제 2: 주석이 잘못된 위치에 표시됨
PDF 좌표 원점은 왼쪽 하단에 있습니다. Y값이 위쪽으로 증가하는지, 페이지 회전을 고려했는지 확인하십시오.

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

### 문제 3: 대용량 문서의 메모리 문제
GroupDocs.Annotation은 콘텐츠를 스트리밍하고 전체 파일을 힙 메모리에 로드하지 않습니다. 그러나 `dispose()`를 호출하고 200 MB보다 큰 파일의 경우 JVM 힙(`-Xmx`)을 늘리는 것을 고려해야 합니다.

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### 문제 4: 프로덕션 라이선스 문제
라이선스 파일이 없거나 경로가 잘못되면 라이브러리가 시험 모드로 전환되어 모든 페이지에 워터마크가 추가됩니다. 라이선스 파일을 클래스패스에 포함된 위치에 두고 애플리케이션 라이프사이클 초기에 로드하십시오.

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

## 프로덕션 애플리케이션 성능 모범 사례

### 메모리 관리 전략
GroupDocs.Annotation은 스트리밍 방식으로 PDF를 처리하여 전체 문서를 메모리에 로드하지 않고도 500 MB까지 파일을 처리할 수 있습니다. 그래도 다음 지침을 따르세요:

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

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

### 스레드 고려 사항
GroupDocs.Annotation은 기본적으로 **스레드 안전하지** 않습니다. 애플리케이션이 문서를 동시에 처리하는 경우:
- **절대 공유하지 마세요** 스레드 간에 `Annotator` 인스턴스를.  
- **동기화** 파일 접근 또는 잠금 메커니즘 사용.  
- 고처리량이 필요하면 `Annotator` 객체 **풀**을 고려하십시오.

### 캐싱 전략
- 자주 사용하는 주석 템플릿을 캐시합니다.  
- 공통 좌표 세트에 `Point` 컬렉션을 재사용합니다.  
- 같은 기본 문서를 반복해서 주석 달 경우 **템플릿 PDF**를 메모리에 유지합니다.

## Java PDF 메모리 관리 모범 사례
대용량 PDF를 다루거나 배치로 많은 파일을 처리할 때 효율적인 메모리 사용이 필수적입니다. 다음은 몇 가지 실용적인 권장 사항입니다:
- `Annotator`마다 **try‑with‑resources**를 사용해 반드시 해제하도록 합니다.  
- 필요에 따라 **JVM 힙**(`-Xmx`)을 늘리고, 프로파일링 도구로 사용량을 모니터링합니다.  
- 가능하면 **문서를 순차적으로 처리**하고 각 파일 후에 메모리를 해제합니다.  
- 같은 PDF를 여러 번 로드하지 마세요; 반복 읽어야 할 경우 동일 스트림을 재사용합니다.

이러한 관행을 적용하면 애플리케이션 응답성을 유지하고 무거운 주석 작업 중 메모리 부족 오류를 방지할 수 있습니다.

## 실제 적용 사례 및 사용 예시

### 문서 검토 시스템
- **법률 검토:** 계약 조항에 밑줄을 긋고 위험에 대한 댓글을 추가합니다.  
- **컴플라이언스 감사:** 재무제표에서 문제 섹션을 하이라이트합니다.  
- **학술 피어 리뷰:** 교수들이 명확히 해야 할 구절에 밑줄을 긋습니다.

### 교육 플랫폼
- **학생 주석 도구:** 학습자가 전자책에서 핵심 개념에 밑줄을 긋게 합니다.  
- **교사 피드백:** 제출된 과제에 직접 인라인 댓글을 제공합니다.

### 품질 보증 워크플로
- **기술 문서 검토:** 엔지니어가 업데이트가 필요한 섹션에 밑줄을 긋습니다.  
- **표준 운영 절차:** 안전 담당자가 중요한 단계를 하이라이트합니다.

### 콘텐츠 관리 시스템
- **편집 워크플로:** 편집자가 사실 확인이 필요한 텍스트에 밑줄을 긋습니다.  
- **버전 관리:** 문서 개정 간 주석 이력을 추적합니다.

## 전문가 구현을 위한 고급 팁

### 맞춤형 주석 스타일
맞춤 대시 패턴, 라인 캡 및 불투명도 수준을 설정하여 밑줄의 시각적 모습을 확장할 수 있습니다. 이는 검토자 역할(예: 법무 vs. 엔지니어링)을 구분해야 할 때 유용합니다.

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

### 추적을 위한 주석 메타데이터
각 주석은 사용자 정의 메타데이터 사전을 포함할 수 있습니다. ID, 타임스탬프 또는 워크플로 상태를 저장해 외부 추적 시스템과 통합하십시오.

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### 사용자 관리 시스템과 통합
`Comment`의 `author` 속성을 애플리케이션의 사용자 ID와 매핑하십시오. 이를 통해 역할 기반 스타일링 및 감사 추적 생성을 할 수 있습니다.

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

## 프로덕션 이슈 트러블슈팅

### 성능 모니터링
프로덕션에서 다음 지표를 확인하십시오:
- **Heap 사용량** – `dispose()`가 호출되었는지 확인합니다.  
- **문서당 처리 시간** – `annotator.save()` 전후에 타임스탬프를 기록합니다.  
- **오류율** – 예외를 포착하고 분류합니다.

### 일반적인 프로덕션 함정
- **파일 잠금** – 주석을 달기 전에 업로드된 파일이 닫혔는지 확인합니다.  
- **동시 편집** – 낙관적 잠금 또는 버전 검사를 구현합니다.  
- **대용량 파일(> 50 MB)** – JVM 타임아웃을 늘리고 스트리밍 API를 고려합니다.

### 오류 처리 모범 사례
모든 주석 호출을 try‑catch 블록으로 감싸고, 전체 스택 트레이스를 로그에 기록한 뒤 사용자 친화적인 메시지를 포함한 커스텀 `AnnotationException`을 다시 throw하십시오. 이 패턴은 디버깅을 단순화하고 API 사용자가 명확한 피드백을 받을 수 있게 합니다.

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

## 자주 묻는 질문

**Q: 단일 작업으로 텍스트 여러 영역에 주석을 달려면 어떻게 해야 하나요?**  
A: 서로 다른 좌표를 가진 여러 `UnderlineAnnotation` 객체를 생성하고 `annotator.add()`를 사용해 순차적으로 추가합니다.

**Q: PDF 문서 내 이미지에 주석을 달 수 있나요?**  
A: 예. 동일한 좌표계를 사용하고 포인트가 이미지 경계 안에 있도록 합니다.

**Q: PDF 외에 GroupDocs.Annotation이 지원하는 파일 형식은 무엇인가요?**  
A: Word(DOC/DOCX), Excel(XLS/XLSX), PowerPoint(PPT/PPTX) 및 JPEG, PNG, TIFF와 같은 이미지 형식.

**Q: 메모리 부족 없이 매우 큰 문서를 처리하려면 어떻게 해야 하나요?**  
A: 문서를 하나씩 처리하고, JVM 힙(`-Xmx`)을 늘리며, `Annotator` 인스턴스를 즉시 dispose하십시오.

**Q: 문서에서 기존 주석을 추출할 수 있나요?**  
A: 예. `annotator.get()`을 사용해 모든 주석을 가져온 뒤 필요에 따라 유형, 작성자 또는 페이지별로 필터링합니다.

---

**Last Updated:** 2026-10-16  
**Tested With:** GroupDocs.Annotation 25.2  
**Author:** GroupDocs  

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

## 관련 튜토리얼
- [깨끗한 PDF Java 만들기: GroupDocs로 밑줄 주석](/annotation/java/annotation-management/java-groupdocs-annotate-add-remove-underline/)
- [PDF 주석 편집 Java - 완전한 GroupDocs 튜토리얼](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [PDF 주석 달기 GroupDocs Annotation Java](/annotation/java/annotation-management/annotate-pdfs-groupdocs-annotation-java/)