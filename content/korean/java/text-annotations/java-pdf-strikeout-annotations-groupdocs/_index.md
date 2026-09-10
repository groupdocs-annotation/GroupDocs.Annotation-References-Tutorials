---
categories:
- Java PDF Processing
date: '2026-05-21'
description: GroupDocs를 사용하여 Java에서 PDF에 취소선 주석을 추가하는 방법을 배웁니다. 이 단계별 튜토리얼에서는 설정,
  코드, 문제 해결 및 성능 팁을 다룹니다.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Java PDF 텍스트 취소선 가이드
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  type: TechArticle
- description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
  steps:
  - name: Setting Up File Paths
    text: Define the locations of your source PDF and the destination file. Incorrect
      paths are a common source of “File Not Found” errors. **Common Mistake Alert:**
      Ensure the output directory exists and is writable; GroupDocs will not auto‑create
      missing folders.
  - name: Initialize the Annotator
    text: Create an `Annotator` instance that loads the PDF into memory. **What happens
      here?** The library parses the PDF structure, builds an internal representation,
      and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this
      step may take a few seconds.
  - name: Adding Comments (Optional but Recommended)
    text: '`Comment` is a class that represents a textual note attached to an annotation,
      allowing collaborators to explain the reason for the strikeout. **Real‑world
      tip:** Use comments to explain why text is being removed—this is especially
      useful in legal or editorial review workflows.'
  - name: Defining Annotation Coordinates
    text: '`Point` objects store X‑Y coordinate pairs that define the exact location
      of an annotation on a PDF page. **Coordinate System Explained:** PDF coordinates
      start at the bottom‑left corner (0,0). The example creates a horizontal line
      from (80,730) to (240,730) on the target page. **Finding the Right C'
  - name: Creating the Strikeout Annotation
    text: '`StrikeoutAnnotation` encapsulates the visual line, its style properties
      such as color and opacity, and any associated metadata for a strikeout mark.
      **Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright
      yellow). Use an online converter if you need brand‑specific shades. '
  - name: Apply the Annotation
    text: '`addAnnotation` is a method of the `Annotator` that registers the prepared
      annotation with the document so it will be rendered and saved.'
  - name: Save and Clean Up
    text: '`dispose()` releases native resources held by the `Annotator` instance,
      preventing memory leaks after processing is complete. **Memory Management Note:**
      Calling `dispose()` frees native resources and prevents memory leaks when processing
      batches of PDFs.'
  type: HowTo
- questions:
  - answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
    question: Can I strikeout text across multiple lines?
  - answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
    question: What happens if I specify coordinates outside the page boundaries?
  - answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
    question: Can I remove strikeout annotations after adding them?
  - answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
    question: Is there a limit to how many annotations I can add to a single PDF?
  - answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
    question: How do I work with password‑protected PDFs?
  type: FAQPage
tags:
- java-pdf
- annotations
- groupdocs
- document-processing
title: Java에서 PDF에 취소선 주석을 추가하는 방법 – 완전한 GroupDocs 가이드
type: docs
url: /ko/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# Java에서 PDF에 취소선 주석 추가하는 방법

프로그래밍으로 PDF에서 텍스트를 취소선으로 표시해야 했던 적이 있나요? 문서 검토 시스템을 구축하거나, 편집 워크플로를 만들거나, 단순히 삭제할 텍스트를 표시해야 할 때, Java에서 **how to add strikeout** 주석을 추가하는 것은 시간을 절약하고 수동 작업을 줄여주는 실용적인 기술입니다. 이 포괄적인 가이드에서는 프로젝트 설정부터 성능 튜닝까지 GroupDocs.Annotation for Java를 사용하여 취소선 주석을 구현하는 데 필요한 모든 것을 알아볼 수 있습니다.

## 빠른 답변
- **첫 번째 단계는 무엇인가요?** `pom.xml`에 GroupDocs.Annotation Maven 의존성을 추가합니다.  
- **취소선을 어떻게 생성하나요?** `Annotator`를 인스턴스화하고, 포인트와 함께 `StrikeoutAnnotation`을 정의한 뒤 색상/불투명도를 설정하고 `addAnnotation`을 호출합니다.  
- **댓글을 추가할 수 있나요?** 예, 협업을 위해 주석에 `Comment` 객체를 첨부합니다.  
- **주석이 잘못 배치된 경우 어떻게 하나요?** 좌표 포인트를 조정하세요; PDF는 좌측 하단 원점을 사용합니다.  
- **문서 크기에 제한이 있나요?** GroupDocs는 전체 파일을 메모리에 로드하지 않고 수백 페이지 PDF를 처리합니다.

## PDF 주석에서 “how to add strikeout”이란 무엇인가요?
“how to add strikeout”이라는 문구는 주석 API를 사용하여 PDF 문서 내 선택된 텍스트에 프로그래밍 방식으로 선을 그어 취소선을 표시하는 과정을 의미합니다. Java에서는 GroupDocs.Annotation이 취소선 표시의 렌더링, 스타일링 및 영속성을 처리하는 전용 `StrikeoutAnnotation` 클래스를 제공합니다.

## Java PDF 취소선에 GroupDocs를 사용하는 이유는?
GroupDocs.Annotation은 **50개 이상의 입력 및 출력 형식**을 지원합니다—PDF, DOCX, XLSX, PPTX, HTML 및 일반 이미지 형식을 포함—따라서 단일 파일 형식에 얽매이지 않습니다. 이 라이브러리는 저수준 PDF 구조를 추상화하는 고수준 API를 제공하여 글꼴 포함, 페이지 렌더링 및 주석 영속성을 자동으로 처리하므로 개발자는 PDF 내부보다 비즈니스 로직에 집중할 수 있습니다.

## 전제 조건 및 설정 요구 사항

### 필수 요구 사항
- **Java Development Kit (JDK):** 버전 8 이상 (최적의 가비지 컬렉션을 위해 JDK 11+ 권장).  
- **GroupDocs.Annotation for Java:** Maven을 통해 통합 (아래 Maven 스니펫 참조).  
- **IDE:** IntelliJ IDEA, Eclipse 또는 Java 호환 편집기.

### Maven 의존성 설정
`pom.xml`에 다음 의존성 블록을 추가합니다:

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

**Pro Tip:** 항상 GroupDocs 릴리스 페이지에서 최신 버전을 확인하세요; 최신 릴리스는 기능을 추가하고 주석 렌더링에 영향을 줄 수 있는 버그를 수정합니다.

### 라이선스 설정
GroupDocs.Annotation은 프로덕션 사용을 위해 유효한 라이선스가 필요합니다. 다음 세 가지 옵션이 있습니다:

- **Free Trial:** [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)에서 다운로드  
- **Temporary License:** [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)에서 개발 키를 요청  
- **Full License:** [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)에서 프로덕션용으로 구매  

트라이얼은 미묘한 워터마크를 추가하므로 테스트 계획을 적절히 세우세요.

## 단계별 구현 가이드

### 핵심 구성 요소 이해
다음 정의는 빠른 개념 모델을 제공합니다:

- **Annotator:** PDF를 로드하고 주석 메서드를 제공하는 주요 API 객체.  
- **StrikeoutAnnotation:** 시각적 취소선과 스타일 옵션을 나타냅니다.  
- **Point:** 선의 시작과 끝을 지정하는 좌표 쌍 (X, Y)입니다.  
- **Comment:** 협업을 위해 주석에 첨부되는 선택적 텍스트.

### Step 1: 파일 경로 설정
소스 PDF와 대상 파일의 위치를 정의합니다. 잘못된 경로는 “File Not Found” 오류의 일반적인 원인입니다.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Common Mistake Alert:** 출력 디렉터리가 존재하고 쓰기 가능한지 확인하세요; GroupDocs는 누락된 폴더를 자동으로 생성하지 않습니다.

### Step 2: Annotator 초기화
`Annotator` 인스턴스를 생성하여 PDF를 메모리로 로드합니다.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**What happens here?** 라이브러리가 PDF 구조를 파싱하고 내부 표현을 구축한 뒤 페이지별 주석 캔버스를 준비합니다. 수백 페이지 파일의 경우 이 단계에 몇 초가 걸릴 수 있습니다.

### Step 3: 댓글 추가 (선택 사항이지만 권장)
`Comment`는 주석에 첨부된 텍스트 메모를 나타내는 클래스이며, 협업자가 취소선 이유를 설명할 수 있게 합니다.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Real‑world tip:** 텍스트가 제거되는 이유를 설명하기 위해 댓글을 사용하세요—법률 또는 편집 검토 워크플로에서 특히 유용합니다.

### Step 4: 주석 좌표 정의
`Point` 객체는 PDF 페이지에서 주석의 정확한 위치를 정의하는 X‑Y 좌표 쌍을 저장합니다.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Coordinate System Explained:** PDF 좌표는 좌측 하단 코너 (0,0)에서 시작합니다. 예제는 대상 페이지에서 (80,730)에서 (240,730)까지의 수평선을 생성합니다.

**Finding the Right Coordinates:** 많은 개발자가 페이지 너비/높이 비율을 절대 포인트로 변환하는 도우미를 만들어 코드가 다양한 페이지 크기에 강인하도록 합니다.

### Step 5: 취소선 주석 생성
`StrikeoutAnnotation`은 시각적 선, 색상 및 불투명도와 같은 스타일 속성, 그리고 취소선 표시와 연관된 메타데이터를 캡슐화합니다.

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535); // Yellow
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0); 
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

**Color Values:** `fontColor`는 십진수 RGB 값(예: 밝은 노란색은 65535)을 사용합니다. 브랜드 고유 색상이 필요하면 온라인 변환기를 사용하세요.

**Opacity Recommendation:** `0.7`(70 %) 불투명도는 기본 텍스트를 읽을 수 있게 하면서 명확한 시각적 신호를 제공합니다.

### Step 6: 주석 적용
`addAnnotation`은 `Annotator`의 메서드로, 준비된 주석을 문서에 등록하여 렌더링 및 저장이 되도록 합니다.

```java
annotator.add(strikeout);
```

### Step 7: 저장 및 정리
`dispose()`는 `Annotator` 인스턴스가 보유한 네이티브 리소스를 해제하여 처리 완료 후 메모리 누수를 방지합니다.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Memory Management Note:** `dispose()`를 호출하면 네이티브 리소스가 해제되고 PDF 배치를 처리할 때 메모리 누수를 방지합니다.

## 일반적인 문제와 해결 방법

### Issue 1: “File Not Found” 오류
**Symptoms:** `Annotator` 생성 중 예외 발생.  
**Solution:** 입력 및 출력 경로를 확인하고 애플리케이션에 읽기/쓰기 권한이 있는지 확인하세요.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### Issue 2: 취소선이 잘못된 위치에 표시됨
**Symptoms:** 선이 의도한 텍스트와 맞지 않습니다.  
**Solution:** PDF Y‑좌표는 위쪽으로 증가한다는 점을 기억하세요. 시각적 디버깅 도구를 사용하거나 페이지 크기를 출력하여 포인트를 미세 조정합니다.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### Issue 3: 주석이 보이지 않음
**Symptoms:** 저장 후 취소선이 표시되지 않습니다.  
**가능한 원인 및 해결책:**  
- **Opacity too low:** 일시적으로 불투명도를 `1.0`으로 설정하여 가시성을 확인합니다.  
- **Color blending:** 빨간색(`255`)과 같은 고대비 색상을 사용합니다.  
- **Incorrect page index:** 페이지 번호는 0부터 시작하므로 올바른 페이지를 지정했는지 확인합니다.

### Issue 4: 대용량 파일 메모리 문제
**Symptoms:** `OutOfMemoryError` 또는 성능 저하.  
**해결책:**  
- 문서를 더 작은 배치로 처리합니다.  
- 가능한 경우 스트리밍 API를 사용합니다.  
- 각 문서 처리 후 항상 `dispose()`를 호출합니다.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## 실제 적용 사례 및 사용 예

### 법률 문서 검토
법률 사무소는 계약서에 취소선을 주석으로 달아 삭제된 조항을 표시하면서 감사 추적을 유지합니다.

### 학술 논문 편집
교수들은 동료 검토 중에 삭제를 제안하기 위해 취소선을 사용하며, 원본 텍스트를 컨텍스트로 남겨 둡니다.

### 콘텐츠 관리 시스템
출판 플랫폼은 수동 검토 전에 정책 위반 섹션을 자동으로 취소선으로 표시합니다.

### 문서 버전 관리
기업은 문서 중심 버전 관리 워크플로에서 취소선 주석을 코드 차이와 유사한 “삭제 표시”로 활용합니다.

## 성능 최적화 팁

### 배치 처리 전략
많은 PDF를 처리할 때 가능한 경우 단일 `Annotator` 인스턴스를 재사용하고 파일을 병렬 스레드로 처리합니다.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### 메모리 관리 모범 사례
- 모든 `Annotator`에 대해 `dispose()`를 호출합니다.  
- 힙 압박을 피하기 위해 동시에 로드하는 문서 수를 제한합니다.  
- VisualVM과 같은 도구로 JVM 메모리 사용량을 모니터링합니다.

### 좌표 캐싱
여러 파일에 동일한 주석 레이아웃을 적용한다면 `Point` 객체를 캐시하여 재계산을 피합니다.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## 고급 사용자 정의 옵션

### 동적 색상 선택
비즈니스 규칙에 따라 런타임에 색상을 선택합니다(예: 중요한 삭제는 빨강, 잠정적인 경우는 노랑).

```java
// Choose colors based on annotation type or user
int colorByPriority = getPriorityColor(annotationType);
strikeout.setFontColor(colorByPriority);

private int getPriorityColor(String type) {
    switch(type) {
        case "HIGH": return 255;    // Red
        case "MEDIUM": return 65535; // Yellow  
        case "LOW": return 65280;   // Green
        default: return 0;          // Black
    }
}
```

### 다중 라인 취소선
여러 텍스트 라인을 가로지르는 지그재그 선을 그리기 위해 `Point` 쌍을 연속으로 생성합니다.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## 문제 해결 체크리스트
1. **File Permissions:** 읽기/쓰기 접근 권한을 확인합니다.  
2. **Library Version:** 지원되는 GroupDocs.Annotation 릴리스를 사용하고 있는지 확인합니다.  
3. **License Status:** 라이선스 파일이 올바르게 참조되는지 확인합니다.  
4. **PDF Compatibility:** PDF가 손상되지 않았으며 지원되는 크기 제한 내에 있는지 확인합니다.  
5. **Coordinate Validation:** 모든 포인트가 페이지 경계 내에 있는지 확인합니다.  
6. **Heap Space:** 매우 큰 파일을 처리할 경우 JVM `-Xmx`를 늘립니다.

## 자주 묻는 질문

**Q: 여러 줄에 걸쳐 텍스트에 취소선을 적용할 수 있나요?**  
A: 예. 원하는 경로를 따라 여러 `Point` 객체를 생성하면 주석이 제공된 폴리라인을 따라 그려집니다.

**Q: 페이지 경계 밖의 좌표를 지정하면 어떻게 되나요?**  
A: 주석이 잘려 보이지 않을 수 있습니다. 항상 좌표가 페이지의 너비와 높이 내에 있는지 검증하세요.

**Q: 추가한 취소선 주석을 제거할 수 있나요?**  
A: 물론입니다. `removeAnnotation` 메서드를 사용해 주석 ID를 지정하거나 유형별로 필터링하여 프로그래밍 방식으로 삭제합니다.

**Q: 단일 PDF에 추가할 수 있는 주석 수에 제한이 있나요?**  
A: GroupDocs는 명확한 상한을 두지 않지만 수천 개 이상의 주석이 있으면 성능이 저하될 수 있습니다. 매우 큰 경우 페이지네이션이나 주석 요약을 고려하세요.

**Q: 비밀번호로 보호된 PDF를 어떻게 다루나요?**  
A: 비밀번호를 `Annotator` 생성자에 전달하면 라이브러리가 메모리에서 문서를 복호화한 뒤 주석을 적용합니다.

**Q: 페이지 크기와 방향이 다른 PDF를 어떻게 처리하나요?**  
A: `annotator.getPageInfo(pageNumber)`를 통해 각 페이지의 크기를 가져오고, 해당 크기에 상대적인 좌표를 계산하여 일관된 배치를 보장합니다.

## 결론

이제 GroupDocs.Annotation을 사용하여 Java에서 PDF에 **how to add strikeout** 주석을 추가하는 완전하고 프로덕션 준비된 솔루션을 갖추었습니다. 파일 경로 처리, 좌표 계산 및 리소스 관리를 마스터하면 이 기능을 문서 검토 도구, 콘텐츠 파이프라인 또는 정밀한 시각적 피드백이 필요한 모든 Java 기반 애플리케이션에 통합할 수 있습니다.

**다음 단계**
1. 예제 프로젝트를 복제하고 샘플 PDF에 실행합니다.  
2. 다양한 색상, 불투명도 및 댓글 텍스트를 실험합니다.  
3. 주석 워크플로를 기존 문서 처리 서비스에 통합합니다.  
4. 관련 주석 유형—하이라이트, 스티키 노트, 도형 주석—을 탐색하여 PDF 조작 툴킷을 확장합니다.

더 알아보고 싶으신가요? 자세한 API 통찰을 위해 공식 문서를 확인하세요.

## 추가 리소스
- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - GroupDocs 라이브러리 일반 문서  
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - 전체 API 레퍼런스  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - 메서드별 상세 정보  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - 라이브러리를 최신 상태로 유지  
- [Purchase License](https://purchase.groupdocs.com/buy) - 프로덕션용 라이선스  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - 구매 전 평가  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - 개발 테스트  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - 커뮤니티 도움 및 공식 지원  

---

**Last Updated:** 2026-05-21  
**Tested With:** GroupDocs.Annotation 23.12 for Java  
**Author:** GroupDocs

## 관련 튜토리얼
- [Add PDF Annotation Java – Complete GroupDocs Guide](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)
- [Java PDF Annotation Tutorial - Complete Guide to Highlighting PDFs](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)
- [How to Add Arrow to PDF in Java – Complete GroupDocs Tutorial](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)