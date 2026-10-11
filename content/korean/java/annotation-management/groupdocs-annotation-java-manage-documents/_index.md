---
categories:
- Java Development
date: '2026-10-11'
description: GroupDocs.Annotation을 사용하여 pdf 주석을 Java에서 로드하는 방법을 마스터하세요. 실제 시나리오에서
  Java를 사용해 문서 주석을 로드, 제거 및 최적화하는 방법을 배웁니다.
keywords:
- load pdf annotations java
- groupdocs annotation java
- java pdf annotation management
- document review java
- annotation processing java
lastmod: '2026-10-11'
linktitle: PDF 주석 로드 Java
og_description: GroupDocs.Annotation을 사용해 PDF 주석을 Java에서 빠르게 로드하세요. 단계별 튜토리얼을 따라 Java
  애플리케이션에서 주석 답변을 읽고, 필터링하고, 제거하는 방법을 배웁니다.
og_image_alt: Developer guide showing Java code for loading and managing PDF annotations
  with GroupDocs
og_title: PDF 주석 로드 Java – GroupDocs Annotation과 함께하는 완전한 가이드
schemas:
- author: GroupDocs
  dateModified: '2026-10-11'
  description: Master how to load pdf annotations java with GroupDocs.Annotation.
    Learn to load, remove, and optimize document annotations using Java in real‑world
    scenarios.
  headline: Load pdf annotations java – complete GroupDocs annotation management guide
  type: TechArticle
- description: Master how to load pdf annotations java with GroupDocs.Annotation.
    Learn to load, remove, and optimize document annotations using Java in real‑world
    scenarios.
  name: Load pdf annotations java – complete GroupDocs annotation management guide
  steps:
  - name: Load test documents with known annotation counts.
    text: Load test documents with known annotation counts.
  - name: Verify reply‑removal logic works as expected.
    text: Verify reply‑removal logic works as expected.
  - name: Measure memory consumption under load.
    text: Measure memory consumption under load.
  - name: Validate that output PDFs retain visual integrity.
    text: Validate that output PDFs retain visual integrity.
  type: HowTo
- questions:
  - answer: Use `LoadOptions` to specify the document password, e.g., `new LoadOptions("myPassword")`,
      then pass the options to the `Annotator` constructor.
    question: How do I handle password‑protected PDF files?
  - answer: Yes! GroupDocs.Annotation supports Word, Excel, PowerPoint, and many other
      formats. The API remains consistent across formats.
    question: Can I process multiple document formats beyond PDF?
  - answer: There’s no hard limit, but performance depends on available memory. For
      documents over 100 MB, consider streaming approaches and batch processing.
    question: What's the maximum document size the library can handle?
  - answer: The library automatically maintains formatting. After removing replies,
      call `annotator.update()` to refresh formatting and `annotator.save()` to persist
      changes.
    question: How do I preserve annotation formatting when removing replies?
  - answer: No direct undo exists. Always work on a copy or implement versioning in
      your application to support roll‑backs.
    question: Can I undo annotation removal operations?
  type: FAQPage
tags:
- java
- annotations
- document-processing
- groupdocs
- pdf-management
title: PDF 주석 로드 Java – 완전한 GroupDocs 주석 관리 가이드
type: docs
url: /ko/java/annotation-management/groupdocs-annotation-java-manage-documents/
weight: 1
---

# PDF 주석 로드 Java – 완전한 GroupDocs 주석 관리 가이드

문서 검토 시스템, e‑learning 플랫폼, 또는 협업 편집 도구를 구축하고 있다면, **load pdf annotations java**는 무시할 수 없는 핵심 기능입니다. 다음 몇 분 동안 우리는 주석 로드 기본부터 고급 답글 필터링 기술까지 필요한 모든 것을 안내하므로 Java 애플리케이션에 빠르고 신뢰할 수 있는 주석 기능을 오늘 바로 추가할 수 있습니다.

## 빠른 답변
- **어떤 라이브러리가 PDF 주석 로드를 Java에서 지원합니까?** GroupDocs.Annotation for Java.  
- **시도하려면 라이선스가 필요합니까?** A free trial is available; a production license is required for commercial use.  
- **지원되는 Java 버전은 무엇입니까?** JDK 8 or newer.  
- **OOM 오류 없이 큰 PDF를 처리할 수 있나요?** Yes—use streaming options and proper resource disposal.  
- **특정 답글만 어떻게 제거합니까?** Iterate the replies list, filter by user or content, and update the document.  
- **비밀번호로 보호된 PDF 지원이 내장되어 있나요?** Yes, supply the password via `LoadOptions`.  

## PDF 주석 로드 Java란 무엇입니까?
PDF 주석 로드 Java는 PDF 파일을 열고, 포함된 주석 객체(하이라이트, 메모, 스탬프, 답글 등)를 읽어 Java 객체로 노출하여 검사, 수정 또는 내보낼 수 있게 하는 것을 의미합니다. 이 단계는 감사 추적, 협업 검토 또는 데이터 추출과 같은 주석 기반 워크플로우의 기반이 됩니다.

## Java용 GroupDocs.Annotation을 사용하는 이유
GroupDocs.Annotation은 PDF, Word, Excel, PowerPoint 등 다양한 형식에서 작동하는 통합 API를 제공합니다. 복잡한 주석 구조를 처리하고 메모리 사용에 대한 세밀한 제어를 제공하며 비밀번호로 보호된 파일과 같은 보안 기능을 기본 지원합니다. 이는 신뢰할 수 있는 성능, 형식 간 호환성 및 강력한 보안을 필요로 하면서 개발 노력을 최소화하는 엔터프라이즈급 애플리케이션에 적합합니다.

## 사전 요구 사항 및 환경 설정

### 필요한 항목
- **GroupDocs.Annotation library** – 주석 처리를 위한 핵심 종속성입니다.  
- **Java Development Environment** – JDK 8+ 및 IDE(IntelliJ IDEA 또는 Eclipse).  
- **Maven or Gradle** – 종속성 관리를 위해.  
- **Sample PDF documents** – 테스트용 기존 주석이 포함된 PDF 문서.  

### Java용 GroupDocs.Annotation 설정

#### Maven 구성 (권장)

`pom.xml` 파일에 이 구성을 추가하여 원활한 종속성 관리를 수행하십시오:

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

**Pro tip**: 보안 업데이트와 성능 향상을 위해 항상 최신 안정 버전을 사용하십시오.

#### 라이선스 획득 전략
- **Free trial** – 평가 및 소규모 프로젝트에 적합합니다.  
- **Temporary license** – 개발 및 테스트 단계에 이상적입니다.  
- **Production license** – 상용 애플리케이션에 필요합니다.  

무료 체험으로 시작하여 라이브러리가 **load pdf annotations java** 요구 사항을 충족하는지 확인하십시오.

## GroupDocs.Annotation을 사용하여 PDF 주석 로드 Java 방법

GroupDocs.Annotation을 사용하여 PDF 주석을 로드하려면 세 가지 주요 단계가 있습니다: 첫째, 비밀번호나 캐시와 같은 필요한 설정을 지정하기 위해 `LoadOptions` 인스턴스를 생성합니다; 둘째, 대상 파일과 로드 옵션을 사용하여 `Annotator`를 인스턴스화합니다; 셋째, `annotator.get()`을 호출하여 주석 객체 전체 목록을 가져오고, 마지막으로 `Annotator`를 해제하여 리소스를 해제합니다.

`LoadOptions` 클래스는 비밀번호 및 캐시와 같은 문서 열기 매개변수를 구성합니다.

### 직접 답변
`LoadOptions` 객체를 생성하고(옵션으로 비밀번호 설정), 대상 PDF 경로로 `Annotator`를 인스턴스화한 뒤, `annotator.get()`을 호출하여 모든 주석을 포함하는 `List<AnnotationBase>`를 얻고, 마지막으로 `annotator.dispose()`를 호출하여 네이티브 리소스를 해제합니다. 이 패턴은 주석을 효율적으로 로드하고 메모리 누수를 방지합니다.

### 주석 로드 프로세스 이해
문서에서 주석을 로드하면 협업 요소(댓글, 하이라이트, 스탬프, 답글)를 설명하는 메타데이터에 접근하게 됩니다. 이 프로세스는 다음에 중요합니다:
- **Audit trails** – 누가 언제 어떤 변경을 했는지 추적합니다.
- **Collaboration insights** – 검토 패턴을 이해합니다.
- **Data extraction** – 보고서나 분석을 위해 주석 데이터를 추출합니다.

### 단계별 구현

#### 1. 필요한 클래스 가져오기
`Annotator` 클래스는 문서에서 주석을 읽고, 추가하고, 삭제하는 메서드를 제공합니다.

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.options.LoadOptions;
import java.util.List;
```

#### 2. 문서에서 주석 로드
`LoadOptions`를 사용하면 로드 동작(예: 비밀번호)을 구성할 수 있습니다. `Annotator`는 PDF의 주석 레이어를 엽니다. `annotator.get()`은 모든 주석을 `List<AnnotationBase>`로 반환합니다. `annotator.dispose()`는 네이티브 리소스를 해제합니다—대용량 파일에 필수적입니다.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/ANNOTATED_AREA_REPLIES_5.pdf";
LoadOptions loadOptions = new LoadOptions();
final Annotator annotator = new Annotator(inputFilePath, loadOptions);
List<AnnotationBase> annotations = annotator.get();
annotator.dispose();
```

#### 언제 이 기능을 사용해야 하는가
- 모든 댓글을 나열하는 **문서 검토 대시보드** 구축.
- **규정 준수 보고**를 위한 주석 데이터 내보내기.
- 형식 간 주석 마이그레이션(PDF → DOCX 등).

## 고급 기능: 특정 주석 답글 제거

### 답글 관리 비즈니스 사례
협업 환경에서 주석 스레드는 시끄러워질 수 있습니다. 선택적인 답글 제거는 원래 댓글을 보존하면서 토론을 집중시킵니다.

### 구현 가이드

#### 1. 문서 경로 설정
`Annotator`는 파일 경로 문자열과 함께 작동하며, 메모리 내 처리용 `InputStream`도 제공할 수 있습니다.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/ANNOTATED_AREA_REPLIES_5.pdf";
String outputPath = "YOUR_OUTPUT_DIRECTORY/RemovedRepliesOutput.pdf";
```

#### 2. 답글 필터링 및 제거
루프는 첫 번째 주석의 답글을 순회합니다. 답글 작성자가 `"Tom"`과 일치하면 제거됩니다. `annotator.update()`는 수정된 컬렉션을 문서에 다시 기록하고, `annotator.save()`는 정리된 PDF를 저장합니다.

```java
LoadOptions loadOptions = new LoadOptions();
final Annotator annotator = new Annotator(inputFilePath, loadOptions);
List<AnnotationBase> annotations = annotator.get();

for (int i = 0; i < annotations.get(0).getReplies().size(); i++) {
    if (annotations.get(0).getReplies().get(i).getUser().getName().toString().equals("Tom")) {
        annotations.get(0).getReplies().remove(i);
    }
}

annotator.update(annotations);
annotator.save(outputPath);
annotator.dispose();
```

#### 고급 답글 필터링 기술
제거 전에 날짜 범위, 키워드 또는 사용자 정의 메타데이터로 필터링하여 정교한 중재 워크플로를 구현할 수 있습니다.

```java
// Remove replies older than 30 days
Date cutoffDate = new Date(System.currentTimeMillis() - (30L * 24 * 60 * 60 * 1000));

// Remove replies based on content patterns
if (reply.getText().toLowerCase().contains("draft") || reply.getText().toLowerCase().contains("test")) {
    // Remove test/draft replies
}

// Remove replies from specific user roles
if (reply.getUser().getRole().equals("temporary_reviewer")) {
    // Clean up temporary reviewer comments
}
```

## 실제 적용 시나리오

### 시나리오 1: 법률 문서 검토 플랫폼
**Challenge** – 로펌은 최종 파일을 전달하기 전에 초기 검토자 댓글을 제거해야 합니다.  
**Solution** – 문서를 배치 처리하고 “temporary_reviewer” 사용자의 답글을 제거합니다:

```java
// Process multiple documents
String[] documentPaths = getDocumentBatch();
for (String docPath : documentPaths) {
    cleanupPreliminaryReviews(docPath);
}
```

### 시나리오 2: 교육 콘텐츠 관리
**Challenge** – 학기 종료 후 학생 주석이 강사의 화면을 어지럽힙니다.  
**Solution** – 강사 피드백을 유지하고, 학생 메모를 보관하며, 참여 보고서를 생성합니다.

### 시나리오 3: 기업 규정 준수 시스템
**Challenge** – 민감한 내부 토론을 클라이언트용 PDF에서 제거해야 합니다.  
**Solution** – 역할 기반 필터를 적용하고 모든 제거 작업을 감사 로그에 기록합니다.

## 성능 모범 사례

### 메모리 관리 전략
GroupDocs.Annotation은 주석 데이터를 스트리밍하여 전체 문서를 로드하지 않습니다. 200 MB보다 큰 PDF의 경우 `LoadOptions.setCacheEnabled(true)`를 활성화하여 메모리 사용량을 150 MB 이하로 유지합니다.

```java
// Always Dispose Resources
try (Annotator annotator = new Annotator(inputFilePath)) {
    // Your annotation processing logic
} // Automatic resource cleanup
```

### 주석 검색 최적화
여러 번 읽을 때 단일 `Annotator` 인스턴스를 재사용하고, 모든 작업이 완료된 후에만 `annotator.dispose()`를 호출합니다.

```java
// Process Annotations in Batches
int batchSize = 100;
for (int i = 0; i < annotations.size(); i += batchSize) {
    List<AnnotationBase> batch = annotations.subList(i, Math.min(i + batchSize, annotations.size()));
    processBatch(batch);
}
```

### I/O 오버헤드 감소
다수의 파일을 처리할 때 파일 읽기를 버퍼링 스트림으로 감싸고 `SaveOptions.setOverwrite(true)`와 함께 `annotator.save()`를 사용하여 임시 파일 생성을 방지합니다.

```java
// Use Streaming for Large Files
LoadOptions options = new LoadOptions();
options.setPreloadPageCount(1); // Load one page at a time
```

### 성능 모니터링
프로덕션에서 다음 메트릭을 추적하십시오:
- **Memory usage** – 주석 처리 중 힙 사용량.
- **Processing time** – 로드 및 필터링 단계 소요 시간.
- **Document size impact** – 파일 크기가 지연에 미치는 영향.
- **Concurrent operations** – 동시 요청 시 응답성.

## 일반적인 문제 및 해결 방법

### 문제 1: “document cannot be loaded” 오류
이는 일반적으로 파일 경로가 잘못되었거나 PDF가 손상되었거나 필요한 비밀번호가 제공되지 않았음을 의미합니다. 경로를 확인하고 파일 무결성을 검사한 뒤 `LoadOptions`를 사용해 비밀번호를 제공하십시오.

```java
try {
    Annotator annotator = new Annotator(inputFilePath);
    // Success
} catch (Exception e) {
    if (e.getMessage().contains("path")) {
        System.err.println("Check file path: " + inputFilePath);
    } else if (e.getMessage().contains("permission")) {
        System.err.println("Verify file permissions");
    }
}
```

### 문제 2: 장기 실행 애플리케이션에서 메모리 누수
각 문서 처리 후 항상 `annotator.dispose()`를 호출하십시오. 배치 작업의 경우 가끔 `System.gc()`를 호출하여 가비지 컬렉션을 유도하는 것을 고려하십시오.

```java
// Use try-with-resources
try (Annotator annotator = new Annotator(inputFilePath)) {
    // Process annotations
} // Automatic cleanup
```

### 문제 3: 대용량 문서에서 성능 저하
`LoadOptions.setCacheEnabled(true)`로 스트리밍 모드를 활성화하고 필요하면 JVM 힙 크기를 늘리십시오. 또한 `LoadOptions.setAnnotationTypes(...)`를 사용하여 로드하는 주석 유형을 제한하십시오.

```java
// Limit annotation loading scope
LoadOptions options = new LoadOptions();
options.setLoadOnlyAnnotatedPages(true);
```

```java
// Pagination for large annotation sets
int pageSize = 50;
for (int page = 0; page < totalPages; page++) {
    processAnnotationPage(annotations, page, pageSize);
}
```

### 문제 4: 제거 후 일관성 없는 주석 ID
답글을 삭제한 후 `annotator.update()`를 호출하여 남은 주석을 재인덱싱하십시오. 이렇게 하면 이후 작업을 위한 안정적인 ID가 보장됩니다.

```java
// Refresh annotation collections after modifications
annotator.update(annotations);
annotations = annotator.get(); // Refresh the collection
```

## 보안 고려 사항

### 입력 검증
로드하기 전에 파일 확장자와 MIME 유형을 검증하여 악성 페이로드를 방지하십시오. 신뢰할 수 있는 감지를 위해 `java.nio.file.Files.probeContentType`을 사용하십시오.

```java
// Validate file paths and user inputs
if (!isValidFilePath(inputFilePath)) {
    throw new IllegalArgumentException("Invalid file path");
}

if (!hasPermissionToModify(userId, documentId)) {
    throw new SecurityException("Insufficient permissions");
}
```

### 감사 로그
사용자 ID, 타임스탬프 및 문서 식별자를 포함해 모든 로드, 업데이트 및 삭제 작업을 기록하십시오. 이는 대부분의 규정 준수 프레임워크를 충족합니다.

```java
// Log annotation operations for compliance
auditLogger.info("User {} removed {} replies from document {}", 
    userId, removedCount, documentId);
```

### 접근 제어
역할 기반 권한을 구현하십시오:
- **Read‑only** – 주석만 보기.
- **Contributor** – 자신의 주석 추가/편집.
- **Moderator** – 모든 주석 또는 답글 삭제.
- **Administrator** – 전체 제어.

## 프로덕션 시스템을 위한 고급 팁

### 1. 캐싱 전략 구현
자주 접근하는 주석 메타데이터를 분산 캐시(예: Redis)에 캐시하여 핫 문서의 디스크 I/O를 감소시킵니다.

```java
// Simple annotation cache
Map<String, List<AnnotationBase>> annotationCache = new ConcurrentHashMap<>();

public List<AnnotationBase> getCachedAnnotations(String documentPath) {
    return annotationCache.computeIfAbsent(documentPath, path -> {
        try (Annotator annotator = new Annotator(path)) {
            return annotator.get();
        }
    });
}
```

### 2. 비동기 처리
무거운 주석 필터링 작업을 백그라운드 워커 큐(예: RabbitMQ)로 오프로드하여 UI 응답성을 유지하십시오.

```java
CompletableFuture<Void> processDocumentAsync(String documentPath) {
    return CompletableFuture.runAsync(() -> {
        processAnnotations(documentPath);
    });
}
```

### 3. 오류 복구 메커니즘
`AnnotationException`을 특별히 처리하고 일시적인 실패를 최대 세 번 재시도하도록 모든 주석 호출을 try‑catch 블록으로 감싸십시오.

```java
public boolean processWithRetry(String documentPath, int maxRetries) {
    for (int attempt = 1; attempt <= maxRetries; attempt++) {
        try {
            processAnnotations(documentPath);
            return true;
        } catch (Exception e) {
            if (attempt == maxRetries) {
                logger.error("Failed to process after {} attempts", maxRetries, e);
                return false;
            }
            try {
                Thread.sleep(1000 * attempt); // Exponential backoff
            } catch (InterruptedException ie) {
                Thread.currentThread().interrupt();
                return false;
            }
        }
    }
    return false;
}
```

## 주석 관리 시스템 테스트

### 단위 테스트 프레임워크
JUnit 5와 Mockito를 함께 사용하여 `Annotator` 동작을 모킹하고 답글 제거 로직이 예상대로 작동하는지 검증하십시오.

```java
@Test
public void testAnnotationLoading() {
    String testDocument = "test-documents/sample-with-annotations.pdf";
    
    try (Annotator annotator = new Annotator(testDocument)) {
        List<AnnotationBase> annotations = annotator.get();
        
        assertNotNull(annotations);
        assertTrue(annotations.size() > 0);
        
        // Verify annotation properties
        AnnotationBase firstAnnotation = annotations.get(0);
        assertNotNull(firstAnnotation.getAuthor());
        assertNotNull(firstAnnotation.getCreatedOn());
    }
}
```

### 통합 테스트
1. 알려진 주석 수를 가진 테스트 문서를 로드합니다.  
2. 답글 제거 로직이 예상대로 작동하는지 검증합니다.  
3. 부하 하에서 메모리 사용량을 측정합니다.  
4. 출력 PDF가 시각적 무결성을 유지하는지 확인합니다.

## 자주 묻는 질문

**Q: 비밀번호로 보호된 PDF 파일을 어떻게 처리합니까?**  
A: `LoadOptions`를 사용하여 문서 비밀번호를 지정합니다. 예: `new LoadOptions("myPassword")`, 그런 다음 옵션을 `Annotator` 생성자에 전달하십시오.

**Q: PDF 외에 여러 문서 형식을 처리할 수 있나요?**  
A: 예! GroupDocs.Annotation은 Word, Excel, PowerPoint 및 기타 많은 형식을 지원합니다. API는 형식에 관계없이 일관됩니다.

**Q: 라이브러리가 처리할 수 있는 최대 문서 크기는 얼마입니까?**  
A: 명확한 제한은 없지만 성능은 사용 가능한 메모리에 따라 달라집니다. 100 MB 이상의 문서는 스트리밍 방식 및 배치 처리를 고려하십시오.

**Q: 답글을 제거할 때 주석 형식을 어떻게 유지합니까?**  
A: 라이브러리는 자동으로 형식을 유지합니다. 답글을 제거한 후 `annotator.update()`를 호출하여 형식을 새로 고치고 `annotator.save()`로 변경 사항을 저장하십시오.

**Q: 주석 제거 작업을 되돌릴 수 있나요?**  
A: 직접적인 되돌리기는 없습니다. 항상 복사본에서 작업하거나 애플리케이션에 버전 관리를 구현하여 롤백을 지원하십시오.

**Q: 동일한 문서에 대한 동시 접근을 어떻게 처리합니까?**  
A: 애플리케이션 수준에서 파일 잠금 메커니즘을 구현하십시오. GroupDocs.Annotation은 내장된 동시성 제어를 제공하지 않습니다.

**Q: 답글 제거와 전체 주석 제거의 차이점은 무엇입니까?**  
A: 답글을 제거하면 주요 주석(예: 메모)은 유지되면서 토론 스레드만 삭제됩니다. 주석을 제거하면 모든 답글을 포함한 전체 객체가 삭제됩니다.

**Q: 주석 통계(수, 작성자, 날짜)를 어떻게 추출합니까?**  
A: 예를 들어 주석 컬렉션을 순회하며 속성을 집계하십시오:

```java
Map<String, Integer> authorCounts = annotations.stream()
    .collect(Collectors.groupingBy(
        a -> a.getAuthor(), 
        Collectors.summingInt(a -> 1)
    ));
```

**Q: 주석을 외부 형식(JSON, XML)으로 내보내는 방법이 있나요?**  
A: 기본 제공은 없지만 `AnnotationBase` 객체를 직접 직렬화하거나 라이브러리의 메타데이터 추출 기능을 사용해 맞춤형 익스포터를 만들 수 있습니다.

**Q: 손상되거나 부분적으로 손상된 문서를 어떻게 처리합니까?**  
A: 포괄적인 예외 처리를 포함한 방어적 프로그래밍을 구현하십시오. 라이브러리는 다양한 손상 유형에 대해 특정 예외를 발생시키므로 이를 잡아 사용자 친화적인 피드백을 제공하십시오.

## 추가 리소스

- **문서**: [GroupDocs Annotation Java Documentation](https://docs.groupdocs.com/annotation/java/)  
- **API 참조**: [Complete Java API Reference](https://reference.groupdocs.com/annotation/java/)  
- **다운로드 센터**: [Latest library releases](https://releases.groupdocs.com/annotation/java/)  
- **상업 라이선스**: [Purchase options](https://purchase.groupdocs.com/buy)  
- **무료 체험**: [Start your evaluation](https://releases.groupdocs.com/annotation/java/)  
- **개발 라이선스**: [Temporary license request](https://purchase.groupdocs.com/temporary-license/)  
- **커뮤니티 지원**: [Developer forum](https://forum.groupdocs.com/c/annotation/)

---

**마지막 업데이트:** 2026-10-11  
**테스트 환경:** GroupDocs.Annotation 25.2 (Java)  
**작성자:** GroupDocs

```java
LoadOptions options = new LoadOptions();
options.setPassword("your-document-password");
Annotator annotator = new Annotator(filePath, options);
```

## 관련 튜토리얼

- [PDF 주석 편집 Java - 완전한 GroupDocs 튜토리얼](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [PDF 주석 추출 자동화 GroupDocs Java](/annotation/java/annotation-management/automate-pdf-annotation-extraction-groupdocs-java/)
- [PDF 주석 생성 Java – 완전한 문서 마크업 가이드](/annotation/java/graphical-annotations/)