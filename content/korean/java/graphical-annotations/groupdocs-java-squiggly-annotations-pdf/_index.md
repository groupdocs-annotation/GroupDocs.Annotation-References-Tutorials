---
categories:
- Java Development
date: '2026-05-16'
description: GroupDocs.Annotation을 사용하여 Java 주석 답글을 만드는 방법을 배웁니다. 실용적인 예제, 성능 팁 및
  모범 사례와 함께 Java에서 PDF 주석을 마스터하세요.
keywords:
- create annotation reply java
- GroupDocs.Annotation Java
- PDF annotation Java tutorial
lastmod: '2026-05-16'
linktitle: Java PDF 주석 튜토리얼
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
title: 'Java PDF Annotation Library: 주석 답글 생성 java'
type: docs
url: /ko/java/graphical-annotations/groupdocs-java-squiggly-annotations-pdf/
weight: 1
---

# Java PDF 주석 라이브러리: create annotation reply java

PDF에 **create annotation reply java**가 필요하다면—계약 검토 포털, e‑learning 시스템, 또는 대량 처리 파이프라인을 구축하든—이 가이드는 GroupDocs.Annotation for Java를 사용하여 정확히 수행하는 방법을 보여줍니다. 설정, squiggly 주석 생성, 답글 스레딩, 성능 튜닝을 단계별로 안내하여 며칠 안에 신뢰할 수 있는 솔루션을 배포할 수 있습니다.

## 빠른 답변
- **GroupDocs.Annotation의 주요 목적은 무엇입니까?** Java에서 PDF 주석을 프로그래밍 방식으로 생성, 수정 및 추출할 수 있게 합니다.  
- **squiggly 주석을 어떻게 추가합니까?** `SquigglyAnnotation`을 인스턴스화하고, 기하학 및 스타일을 설정한 다음 `annotator.add(...)`를 호출합니다.  
- **주석에 답글을 첨부할 수 있나요?** 예—`Reply` 객체를 생성하고 작성자와 텍스트를 설정한 뒤 부모 주석에 연결합니다.  
- **프로덕션에 라이선스가 필요합니까?** 반드시 필요합니다; 유효한 라이선스가 없으면 출력에 워터마크가 표시됩니다.  
- **배치 처리에 적합합니까?** 예—try‑with‑resources를 사용해 각 문서를 열고, 주석을 추가하고, 닫아 메모리 사용량을 낮게 유지합니다.

## Java 개발자가 PDF 주석 라이브러리가 필요한 이유
PDF에 수동으로 주석을 달는 것은 특히 수백 개의 계약서나 시험지를 검토해야 할 때 시간도 많이 걸리고 오류가 발생하기 쉽습니다. Java PDF 주석 라이브러리는 이 작업을 자동화하여 하이라이트, squiggly 밑줄 및 스레드형 댓글을 파일에 직접 삽입할 수 있게 합니다. 그 결과 별도의 뷰어 없이도 모든 주석을 보존한 검색 가능하고 휴대 가능한 문서가 됩니다.

**이 가이드에서 마스터하게 될 내용**
- Maven 프로젝트에 GroupDocs.Annotation 설치 및 라이선스 적용
- 네이티브 Word 밑줄과 유사한 squiggly 주석 만들기
- 협업 검토를 위해 모든 주석에 스레드형 답글 추가
- 대용량 PDF 처리 시 메모리 및 CPU 사용 최적화
- Spring Boot, 마이크로서비스 또는 데스크톱 앱에 솔루션 배포

법률 문서 검토 시스템, 교육용 채점 도구, 또는 자동 품질 관리 파이프라인을 구축하든, 아래 기술은 프로덕션 준비된 기반을 제공합니다.

## create annotation reply java란 무엇입니까?
`create annotation reply java`는 Java를 사용하여 기존 PDF 주석에 댓글 스레드(Reply)를 연결하는 프로그래밍 방식의 프로세스입니다. 답글을 통해 여러 검토자가 문서를 떠나지 않고 특정 마크업에 대해 토론할 수 있어 원활한 인‑플레이스 협업이 가능합니다. 이 기능은 정적인 PDF를 인터랙티브한 토론 플랫폼으로 변환하여 컨텍스트와 감사 로그를 파일 내에 직접 보존합니다.

## 전제 조건: 환경 준비하기
코드에 들어가기 전에 개발 워크스테이션이 다음 사양을 충족하는지 확인하십시오:

- **JDK** 8 이상 (더 나은 가비지 컬렉션 성능을 위해 JDK 11 + 권장)
- 의존성 관리를 위한 **Maven** 또는 **Gradle** (예제는 Maven 사용)
- Maven을 지원하는 IDE (IntelliJ IDEA, Eclipse, 또는 VS Code)
- IDE와 테스트 실행을 위한 최소 **2 GB**의 여유 RAM
- 실험용 샘플 PDF 파일 (任意의 PDF 편집기로 간단한 PDF를 생성할 수 있음)

GroupDocs.Annotation은 완전히 인‑프로세스에서 실행되며 외부 PDF 뷰어나 네이티브 라이브러리가 필요하지 않습니다.

## GroupDocs.Annotation for Java 설정
라이브러리를 통합하는 과정은 몇 단계이며, 놓치면 런타임 오류를 일으킬 수 있는 숨겨진 함정이 몇 가지 있습니다.

### Maven 의존성 구성
`pom.xml`에 저장소와 의존성을 추가합니다. Maven이 아티팩트를 해결할 수 있도록 `<repositories>` 요소를 `<dependencies>` **앞에** 배치하십시오.

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

> **Pro tip:** 최신 버전을 확인하려면 GroupDocs 릴리스 페이지를 확인하십시오. 새로운 릴리스는 종종 최신 PDF 표준 지원 및 성능 향상을 포함합니다.

### 라이선스 설정 (절대 건너뛰지 마세요!)
GroupDocs.Annotation은 프로덕션 사용을 위해 라이선스 파일이 필요합니다. 없으면 생성된 모든 PDF에 워터마크가 표시됩니다.

1. **Free Trial** – 30일 동안 전체 기능을 제공, 평가에 이상적.
2. **Temporary License** – 개발 및 내부 테스트에 적합.
3. **Full License** – 모든 상업적 배포에 필요.

`GroupDocs.Annotation.lic` 파일을 resources 폴더에 배치하고 시작 시 로드하십시오:

```java
License license = new License();
license.setLicense("GroupDocs.Annotation.lic");
```

> **Common gotcha:** 라이선스 단계를 놓치면 워터마크가 있는 PDF와 조용히 실패하는 API 호출이 발생합니다. 시작 루틴 초기에 항상 라이선스를 검증하십시오.

## 전체 구현 가이드: Squiggly 주석 추가
아래는 squiggly 주석을 만들면서 **create annotation reply java**를 수행하는 단계별 안내입니다. 각 단계는 간결한 설명을 포함하여 각 라인의 “왜”를 이해할 수 있게 합니다.

### Step 1: 필요한 모든 클래스 가져오기
```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.annotation.SquigglyAnnotation;
import com.groupdocs.annotation.models.annotation.Reply;
import com.groupdocs.annotation.options.SaveOptions;
```

- `Annotator` 는 모든 문서 수준 작업의 진입점입니다.
- `Point` 는 페이지상의 좌표를 나타냅니다 (좌측 상단을 기준으로 X와 Y 측정).
- `SquigglyAnnotation` 은 오류를 강조하는 물결 밑줄을 정의합니다.
- `Reply` 는 주석에 연결된 스레드형 댓글을 저장합니다.
- `SaveOptions` 는 출력 형식 및 압축을 제어할 수 있게 합니다.

### Step 2: Squiggly 주석 생성 및 구성
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

SquigglyAnnotation은 PDF에서 오류를 강조하는 물결 밑줄을 생성하는 클래스입니다.

- **Coordinate system**: 좌표계는 좌측 상단을 시작점으로 합니다. 위의 두 점은 (100, 200)에서 (300, 200)까지 수평 물결선을 그립니다.
- **Opacity** 0.7은 주석이 70 % 불투명함을 의미하며, 하위 텍스트가 읽을 수 있게 유지됩니다.

### Step 3: 인터랙티브 답글 추가 (선택 사항이지만 강력함)
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

Reply는 주석에 연결된 댓글 스레드를 나타내는 클래스입니다.

- 답글은 주석에 직접 **스레드형 토론**을 생성하여 최신 PDF 검토자들의 경험을 그대로 제공합니다.
- 각 답글은 작성자 정보와 타임스탬프를 저장하며, 이후 UI에서 필터링하거나 표시할 수 있습니다.

### Step 4: 주석 적용 및 문서 저장
```java
try (Annotator annotator = new Annotator("input.pdf")) {
    annotator.add(squiggly);
    SaveOptions options = new SaveOptions();
    options.setOutputPath("output.pdf");
    annotator.save(options);
}
```

- **try‑with‑resources** 구문은 `Annotator`를 자동으로 닫아 파일 핸들과 네이티브 버퍼를 해제합니다.
- `save`는 수정된 PDF를 `output.pdf`에 기록합니다.

> **Memory note:** `Annotator`는 접근한 페이지만 로드합니다. 수백 페이지 PDF의 경우 이 접근법은 일반 서버에서 힙 사용량을 150 MB 이하로 유지합니다.

## 고급 구성 옵션
### 주석 외관 사용자 정의
시각적 스타일을 브랜드 가이드라인에 맞게 세밀하게 조정할 수 있습니다:

```java
squiggly.setBorderWidth(2);
squiggly.setColor(0xFF00FF00); // ARGB green
squiggly.setOpacity(0.5);
```

- **Border width** 는 선 두께(포인트 단위)를 제어합니다.
- **ARGB** 형식은 투명도를 위한 알파 채널을 포함합니다.

### 주석 정확히 배치하기
다양한 페이지 크기의 PDF에서 좌표를 정확히 맞추는 것은 까다로울 수 있습니다. 다음 체계적인 접근 방식을 따르세요:

1. **뷰어에서 PDF 열기** (예: Adobe Acrobat) 및 대상 영역의 눈금값을 기록합니다.
2. **눈금값을 포인트로 변환** (1 point = 1/72 inch).
3. **`annotator.getPageInfo(pageIndex)`** 를 사용해 페이지 너비와 높이를 가져온 뒤 상대 위치를 계산합니다.

## 일반적인 문제와 해결책
### 문제: 주석이 표시되지 않음
**가장 흔한 원인**
- 좌표가 페이지 경계 밖에 있음
- 라이선스가 로드되지 않음(워터마크가 주석을 가림)
- 잘못된 페이지 번호(API에서는 페이지 번호가 0부터 시작)

**해결 체크리스트**
```text
- Verify page dimensions with annotator.getPageInfo(pageIndex)
- Ensure all Point X/Y values are within [0, pageWidth] and [0, pageHeight]
- Confirm license file path and that license.setLicense() returns true
- Check that squiggly.setPageNumber(pageIndex) uses zero‑based indexing
```

### 문제: 대용량 파일에서 성능 저하
500페이지 PDF를 메모리에 로드하면 서비스가 정지될 수 있습니다. 이를 완화하려면:

- **Processing one page at a time** – 문서를 열고, 한 페이지에 주석을 추가하고, 저장한 뒤 다음 페이지로 이동합니다.
- **Streaming** – 전체 문서 버퍼링을 피하기 위해 `Annotator`의 스트리밍 API를 사용합니다.
- **Caching** – 자주 접근하는 PDF를 빠른 캐시(e.g., Redis)에 저장하고 캐시된 복사본에 주석을 추가합니다.

### 문제: 색상 값이 작동하지 않음
GroupDocs는 일반 RGB가 아니라 **ARGB**(Alpha, Red, Green, Blue)를 기대합니다. `0xFFFF0000` ARGB 값은 완전 불투명한 빨간색을 의미합니다. `0xFF0000`을 제공하면 라이브러리가 잘못 해석하여 검은색 주석이 생성됩니다.

```java
int argbRed = 0xFFFF0000; // Alpha=255, Red=255, Green=0, Blue=0
squiggly.setColor(argbRed);
```

## 성능 모범 사례
### 메모리 관리
배치 작업에서 수십 개의 PDF에 주석을 달 때는 각 파일을 자체 try‑with‑resources 블록으로 감싸세요:

```java
for (String filePath : pdfList) {
    try (Annotator annotator = new Annotator(filePath)) {
        // add annotations
        annotator.save(new SaveOptions().setOutputPath(filePath.replace(".pdf", "_annotated.pdf")));
    }
}
```

- 이 패턴은 각 반복 후 네이티브 버퍼가 해제되도록 보장하여 장기 실행 프로세스에서 **OutOfMemoryError**를 방지합니다.

### 배치 처리 최적화
고처리량 환경에서는 제한된 스레드 풀과 병렬 스트림을 결합하는 것을 고려하세요:

```java
ExecutorService executor = Executors.newFixedThreadPool(Runtime.getRuntime().availableProcessors());
pdfList.parallelStream().forEach(path -> executor.submit(() -> annotateDocument(path)));
executor.shutdown();
executor.awaitTermination(1, TimeUnit.HOURS);
```

- **Bounded pool**은 스레드 폭주를 방지하고, 병렬 스트림은 CPU 코어를 지속적으로 활용합니다.

### 파일 크기 고려 사항
100 MB 이상 대형 PDF는 성능을 저하시킬 수 있습니다. 다음 전략을 적용하세요:

- **Pre‑compress**: 주석을 추가하기 전에 Ghostscript와 같은 도구로 원본 PDF를 사전 압축합니다.
- **Annotate only needed pages** – 마크업이 필요 없는 페이지는 건너뜁니다.
- **Split**: 문서를 논리적 섹션(예: 장별)으로 분할하고 각 청크를 독립적으로 처리합니다.

## 실제 적용 사례
### 문서 검토 시스템
법률 사무소는 종종 문제 조항에 플래그를 달아야 합니다. Squiggly 주석과 스레드형 답글을 결합하면 여러 변호사가 PDF를 떠나지 않고 하나의 단락을 논의할 수 있습니다:

- **Lawyer A**는 조항 아래에 빨간색 squiggly를 추가하고 “모호한 표현”이라고 적습니다.
- **Lawyer B**는 “‘material breach’에 대한 정의를 추가하십시오”라고 답글을 달습니다.
- 전체 토론은 문서에 삽입된 채로 검색 가능하고 감사 가능하게 유지됩니다.

### 기존 시스템과의 통합
GroupDocs.Annotation은 인기 있는 Java 프레임워크와 원활하게 작동합니다:

- **Spring Boot** – PDF multipart 업로드를 받아 주석을 추가하고 결과를 스트리밍하는 REST 엔드포인트 `/api/annotate`를 노출합니다.
- **JSF** – 웹 뷰에서 실시간 마크업을 위해 주석 동작을 UI 컴포넌트에 바인딩합니다.
- **Microservices** – 라이브러리의 작은 풋프린트(< 15 MB) 덕분에 Docker로 컨테이너화하고 수평 확장이 가능합니다.

### 워크플로 자동화
주석을 다른 GroupDocs 제품(예: GroupDocs.Signature)과 결합하여 엔드‑투‑엔드 파이프라인을 구축합니다:

```text
1. Upload contract → 2. Auto‑apply squiggly for missing signatures → 3. Add reviewer replies → 4. Route to signing service.
```

## Squiggly 주석을 사용할 때와 대안
| 사용 사례 | 권장 주석 |
|----------|------------------------|
| 맞춤법이나 문법 오류 표시 | **Squiggly** – 워드 프로세서와 유사한 시각적 표시 |
| 오류를 의미하지 않고 중요한 섹션 강조 | **Highlight** – 반투명 오버레이 |
| 상세 피드백 제공 | **Text** 또는 **Comment** – 자유 형식 메모 박스 |
| 문서 승인 또는 거부 | **Stamp** – “Approved” 또는 “Rejected” 배지 |

## 결론
이제 GroupDocs.Annotation을 사용한 **create annotation reply java**에 대한 완전하고 프로덕션 준비된 레시피를 갖추었습니다. API를 마스터하고, 라이선스를 처리하며, 위의 성능 팁을 적용하면 다음을 수행할 수 있습니다:

- 수천 개의 PDF에 대한 오류 표시 자동화
- 파일 내부에서 협업형 스레드 토론 활성화
- 대용량 문서를 처리할 때도 메모리 사용량 최소화

**다음 단계**
1. 다른 주석 유형(하이라이트, 스탬프, 텍스트)으로 실험해 보세요.
2. PDF를 받아 주석을 추가하고 결과를 반환하는 REST 서비스를 구축하세요.
3. 추출 API(`annotator.get()`)를 탐색하여 기존 댓글을 분석용으로 가져오세요.

프로그래밍 방식 PDF 주석의 강점은 반복 가능하고 감사 가능한 코드로 지루한 수동 마크업을 대체할 수 있다는 점에 있습니다. 특화된 법률 기술 제품을 구축하든 일반 문서 워크플로 엔진을 구축하든, 이 가이드의 기술은 앞으로 나아갈 탄탄한 기반을 제공합니다.

## 자주 묻는 질문
**Q: GroupDocs.Annotation이 다른 Java PDF 라이브러리보다 뛰어난 점은 무엇인가요?**  
A: GroupDocs.Annotation은 주석 워크플로에만 집중하여 30가지 이상의 주석 유형, 스레드형 답글, 50개 이상의 파일 형식에 대한 네이티브 지원을 제공하며 500페이지 PDF에서도 메모리 사용량을 200 MB 이하로 유지합니다.

**Q: 이 라이브러리를 Spring Boot 애플리케이션에서 사용할 수 있나요?**  
A: 물론입니다. `Annotator` 서비스를 주입하고 multipart 업로드를 처리하며 주석이 추가된 PDF를 클라이언트에 스트리밍하는 `@RestController`를 생성하세요. 동시 요청을 위해 스레드 풀을 구성하는 것을 잊지 마세요.

**Q: 페이지 크기가 다른 문서를 어떻게 처리하나요?**  
A: `annotator.getPageInfo(pageIndex)`를 통해 각 페이지의 크기를 조회하고, 포인트 값을 하드코딩하는 대신 비율(예: 퍼센트)로 상대 좌표를 계산합니다. 이렇게 하면 A4, Letter 및 사용자 정의 크기 페이지에서도 주석이 올바르게 표시됩니다.

**Q: PDF에서 기존 주석을 추출하는 방법이 있나요?**  
A: 있습니다. `annotator.get()`을 호출하면 모든 주석의 컬렉션을 가져올 수 있으며, 이를 반복하여 작성자, 댓글, 기하학 등 속성을 읽을 수 있습니다. 이는 마이그레이션이나 분석 시나리오에 유용합니다.

**Q: 다중 사용자 시스템에서 주석 권한을 처리하는 최적의 방법은 무엇인가요?**  
A: 애플리케이션 계층에서 인증을 구현하고 각 `Reply`에 사용자 ID를 저장한 뒤 비즈니스 규칙(예: 작성자 또는 관리자만 답글을 편집·삭제 가능)을 적용합니다. API 자체는 권한을 강제하지 않으므로 완전한 유연성을 제공합니다.

**Q: 수백 개의 PDF를 처리할 때 메모리 사용량을 최적화하려면 어떻게 해야 하나요?**  
A: 각 문서에 대해 try‑with‑resources를 사용하고 페이지를 개별적으로 처리하며, 동시 메모리 사용을 제한하기 위해 제한된 스레드 풀을 고려하세요. VisualVM과 같은 도구로 JVM 힙을 모니터링하면 `-Xmx` 설정을 미세 조정할 수 있습니다.

**Last Updated:** 2026-05-16  
**Tested With:** GroupDocs.Annotation 25.2 for Java  
**작성자:** GroupDocs  

**추가 리소스**
- [GroupDocs.Annotation for Java 문서](https://docs.groupdocs.com/annotation/java/)
- [전체 API 레퍼런스](https://reference.groupdocs.com/annotation/java/)

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

## 관련 튜토리얼
- [Java PDF 주석 라이브러리 튜토리얼](/annotation/java/reply-management/java-annotator-groupdocs-pdf-annotations-replies/)
- [Java에서 주석 답글 제거 - GroupDocs.Annotation으로 ID별 답글 관리](/annotation/java/annotation-management/java-groupdocs-annotation-remove-replies-by-id/)
- [Java에서 PDF 주석 편집 - 전체 GroupDocs 튜토리얼](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)