---
categories:
- Java Development
date: '2026-03-30'
description: GroupDocs.Annotation을 사용하여 Java에서 취소선 주석을 추가하는 방법을 배워보세요. 코드 예제, 문제 해결
  팁 및 문서 마크업을 위한 모범 사례를 포함한 단계별 가이드.
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: GroupDocs와 함께하는 Java 스트라이크아웃 주석 추가 튜토리얼
type: docs
url: /ko/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# Java에서 취소선 주석 추가 - 완전한 GroupDocs 가이드

문서를 보면서 “이 텍스트를 취소선으로 표시해야 하는데 빨간 펜을 바로 잡을 수가 없어” 라고 생각해 본 적이 있나요? 당신만 그런 것이 아닙니다. 문서 검토 시스템을 구축하거나, 편집 워크플로우를 만들거나, Java 애플리케이션에서 삭제할 텍스트를 표시해야 할 때, **add strikeout annotation java**는 필수 기술입니다. 이 튜토리얼에서는 실제 프로덕션에서 동작하는 텍스트 취소선 기능을 구현하는 데 필요한 모든 것을 단계별로 안내합니다.

## 빠른 답변
- **Java에서 취소선 주석을 지원하는 라이브러리는?** GroupDocs.Annotation for Java  
- **SEO를 위해 타깃으로 삼아야 할 주요 키워드는?** add strikeout annotation java  
- **샘플 코드를 실행하려면 라이선스가 필요합니까?** 개발에는 무료 체험 또는 임시 라이선스로 충분하지만, 프로덕션에서는 정식 라이선스가 필요합니다.  
- **PDF, DOCX, PPTX 파일에서도 사용할 수 있나요?** 네 – GroupDocs.Annotation은 모든 주요 문서 형식을 지원합니다.  
- **필요한 Java 버전은?** JDK 8 이상 (JDK 11+ 권장).

## add strikeout annotation java란 무엇인가요?
취소선 주석은 선택된 텍스트에 선을 그어 해당 내용이 삭제되거나 무시되어야 함을 시각적으로 표시합니다. 원본 텍스트를 그대로 유지하면서 삭제를 제안하는 비파괴적인 방법으로, 감사 로그나 협업 검토에 유용합니다.

## Java 애플리케이션에서 취소선 주석을 사용하는 이유
- **문서 검토 워크플로우** – 검토자는 원본을 변경하지 않고 원하지 않는 텍스트를 표시할 수 있습니다.  
- **협업 편집** – 팀원들이 제안된 삭제를 즉시 확인할 수 있습니다.  
- **법률 및 컴플라이언스** – 변경 사항에 대한 명명한 감사 로그를 유지합니다.  
- **콘텐츠 마이그레이션** – 시스템 간에 콘텐츠를 이동하기 전에 오래된 섹션을 표시합니다.  

## 사전 요구 사항 및 환경 설정
코드 작성을 시작하기 전에 다음이 필요합니다:

- **Java Development Kit (JDK)** 8 이상 (JDK 11+ 권장)  
- **Maven 또는 Gradle** – 의존성 관리를 위해  
- **IDE** – IntelliJ IDEA, Eclipse, 또는 Java 확장이 포함된 VS Code  
- **GroupDocs.Annotation 라이브러리** – 예제에서는 버전 25.2를 사용합니다  

*추가로 있으면 좋은 것:* Java 어노테이션 및 PDF 처리에 대한 기본 지식.

## GroupDocs.Annotation for Java 설정

### 실제 작동하는 Maven 설정
`pom.xml`에 아래와 같이 저장소와 의존성을 정확히 추가합니다:

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

### 라이선스 설정하기
GroupDocs는 여러 라이선스 옵션을 제공합니다:

- **Free trial** – 테스트에 적합 (신용카드 필요 없음)  
- **Temporary license** – 개발 및 스테이징에 이상적  
- **Full license** – 프로덕션 사용에 필요; [구매 페이지](https://purchase.groupdocs.com/buy) 참고

> **프로 팁:** 먼저 무료 체험으로 API를 살펴보고, 실제 기능을 구축할 준비가 되면 임시 라이선스로 전환하세요.

### 빠른 정상 확인 설정
다음 최소 프로그램을 실행하여 라이브러리가 올바르게 로드되는지 확인합니다:

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

콘솔에 오류 없이 성공 메시지가 출력되면 취소선 주석을 추가할 준비가 된 것입니다.

## add strikeout annotation java 구현 방법

아래는 명확한 단계로 나눈 완전한 프로덕션 준비 구현 예시입니다.

### Step 1 – Annotator 초기화
소스 문서를 가리키는 `Annotator` 인스턴스를 생성합니다:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **왜 중요한가:** 절대 경로나 올바르게 해석된 상대 경로를 사용하면 “파일을 찾을 수 없음” 예외를 방지할 수 있습니다.

### Step 2 – (선택) 댓글 회신 준비
회신을 추가하면 주석이 협업형이 됩니다:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

사용자가 취소선 위에 마우스를 올리면 이 댓글이 표시됩니다.

### Step 3 – 취소선 영역 정의
취소선으로 표시할 텍스트를 둘러싼 사각형을 지정합니다:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **좌표 팁:** 원점 (0,0)은 페이지의 왼쪽 위 모서리이며, X는 오른쪽으로, Y는 아래쪽으로 증가합니다. 좌표를 표시하는 PDF 뷰어를 사용해 값을 미세 조정하세요.

### Step 4 – 취소선 주석 설정
모양, 페이지 번호를 설정하고 댓글을 첨부합니다:

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

*색상 참고:* `65535`는 정수 RGB 형식에서 노란색을 의미합니다. 다른 색을 사용하려면 값을 변경하세요.

### Step 5 – 주석 적용 및 저장
문서에 주석을 추가하고 출력 파일을 씁니다:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### Step 6 – 리소스 정리 (중요!)
네이티브 리소스를 해제하기 위해 항상 annotator를 dispose해야 합니다:

```java
if (annotator != null) {
    annotator.dispose();
}
```

프로덕션에서는 사용을 try‑with‑resources 블록이나 `try/finally` 구문으로 감싸세요.

## 일반적인 문제 및 해결 방법

| Problem | Symptom | Fix |
|---------|---------|-----|
| **파일을 찾을 수 없음** | `Annotator` throws an exception | 절대 경로를 사용하고, 읽기 권한을 확인하며, 다른 프로세스가 파일을 잠그고 있지 않은지 확인하세요 |
| **잘못된 좌표** | Strikeout appears away from the intended text | PDF 뷰어의 좌표 시스템을 다시 확인하고, 포인트를 적절히 조정하세요 |
| **주석이 보이지 않음** | No visible strikeout after saving | `opacity`를 증가시키세요 (예: `0.9`), `pageNumber`가 0 기반인지 확인하고, 포인트가 올바른 사각형을 형성하는지 확인하세요 |
| **OutOfMemoryError** | Application crashes on large PDFs | JVM 힙을 늘리세요 (`-Xmx2048m`), 문서를 배치 처리하고, 항상 `dispose()`를 호출하세요 |

## 프로덕션을 위한 성능 모범 사례

### 메모리 관리
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

### 배치 처리 전략
수십 개 또는 수백 개의 파일에 주석을 달아야 할 때:

- 배치당 10‑20개의 문서를 처리합니다.  
- 각 파일에 대한 성공/실패를 로그에 기록합니다.  
- 메모리 누수를 방지하기 위해 각 문서마다 `Annotator`를 재초기화합니다.  

### 캐싱 팁
- 자주 사용하는 문서 템플릿을 캐시합니다.  
- 표준 레이아웃에 대한 사전 계산된 좌표 맵을 저장합니다.  

## 실제 사용 사례

1. **문서 검토 시스템** – 편집자는 원본 계약을 변경하지 않고 삭제를 제안합니다.  
2. **법률 수정** – 변호사는 원본 문구를 보존하면서 조항 삭제를 추적합니다.  
3. **학술 피어 리뷰** – 리뷰어는 삭제할 섹션을 표시하고 인라인 댓글을 추가합니다.  
4. **콘텐츠 마이그레이션** – CMS 마이그레이션 중에 취소선은 교체가 필요한 오래된 복사본을 강조합니다.  

## 고급 커스터마이징

### 맞춤 스타일링
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### 메타데이터 추가
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## 문제 해결 체크리스트
- ✅ 소스 파일을 수동으로 열 수 있나요?  
- ✅ 모든 GroupDocs 종속성이 클래스패스에 존재합니까?  
- ✅ 포인트가 유효한 사각형을 형성합니까?  
- ✅ 페이지 번호가 올바른가요 (0‑기반)?  
- ✅ 충분한 힙 메모리가 있나요?  
- ✅ 출력 폴더에 대한 쓰기 권한이 있나요?  
- ✅ 문서 형식이 지원됩니까 (PDF, DOCX, PPTX 등)?  

## 자주 묻는 질문

**Q: Can I use GroupDocs.Annotation inside a Spring Boot service?**  
A: Yes. Add the Maven dependency, inject a service class that creates the `Annotator`, and manage its lifecycle with Spring’s bean scopes.

**Q: Which document formats support strikeout annotations?**  
A: PDF, DOCX, PPTX, and many other formats supported by GroupDocs.Annotation. PDF offers the most precise coordinate handling.

**Q: How do I handle documents with varying page sizes?**  
A: Retrieve the page dimensions via `annotator.getPageInfo(pageNumber)` and scale your coordinates accordingly.

**Q: Is it possible to edit or delete an existing strikeout annotation?**  
A: Absolutely. Use `annotator.getAnnotations(pageNumber)` to fetch, then `annotator.update(updatedAnnotation)` or `annotator.delete(annotationId)`.

**Q: What is the performance impact of adding many annotations?**  
A: Adding hundreds of annotations is generally fine, but monitor memory usage. For very large annotation sets, consider paginating the view or lazy‑loading annotations on demand.

## 결론
이제 GroupDocs.Annotation을 사용한 **add strikeout annotation java**에 대한 완전하고 프로덕션 준비된 가이드를 보유하고 있습니다. 간단한 정상 확인 예제로 시작한 뒤, 배치 처리, 맞춤 스타일링, 메타데이터 강화로 확장하세요. 좌표를 신중히 테스트하고, 리소스를 책임감 있게 관리하며, 환경에 맞는 라이선스 모델을 선택하는 것을 잊지 마세요.

더 많은 것을 탐색하고 싶으신가요? 하이라이트, 노트, 이미지, 화살표, 워터마크 등 다른 주석 유형을 확인하여 전체 기능을 갖춘 문서 협업 스위트를 구축해 보세요.

---

**마지막 업데이트:** 2026-03-30  
**테스트 환경:** GroupDocs.Annotation 25.2 for Java  
**작성자:** GroupDocs  

**추가 리소스**
- [GroupDocs Annotation 문서](https://docs.groupdocs.com/annotation/java/)
- [API 레퍼런스 가이드](https://reference.groupdocs.com/annotation/java/)
- [최신 버전 다운로드](https://releases.groupdocs.com/annotation/java/)
- [전체 라이선스 구매](https://purchase.groupdocs.com/buy)
- [무료 체험 시작](https://releases.groupdocs.com/annotation/java/)
- [임시 라이선스 받기](https://purchase.groupdocs.com/temporary-license/)
- [커뮤니티 지원 포럼](https://forum.groupdocs.com/c/annotation/)