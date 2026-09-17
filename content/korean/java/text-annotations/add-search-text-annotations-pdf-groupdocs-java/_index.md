---
categories:
- Java Development
date: '2026-09-15'
description: GroupDocs annotation을 사용하여 검색 가능한 PDF Java 파일을 만드는 방법을 배웁니다. 이 step‑by‑step
  가이드는 설정, 코드, 팁 및 문제 해결을 다룹니다.
keywords:
- create searchable pdf java
- pdf annotation free trial
- highlight pdf text java
lastmod: '2026-09-15'
linktitle: Java PDF 텍스트 주석 가이드
og_description: GroupDocs annotation을 사용하여 검색 가능한 PDF Java 파일을 만드는 방법을 배웁니다. 이 step‑by‑step
  가이드는 설정, 코드, 팁 및 문제 해결을 다룹니다.
og_image_alt: Guide showing how to add searchable text annotations to PDFs in Java
  with GroupDocs
og_title: GroupDocs annotation을 사용하여 검색 가능한 PDF Java 파일 만들기
schemas:
- author: GroupDocs
  dateModified: '2026-09-15'
  description: Learn how to create searchable PDF Java files with GroupDocs annotation.
    This step‑by‑step guide covers setup, code, tips, and troubleshooting.
  headline: Create searchable PDF Java files using GroupDocs annotation
  type: TechArticle
- description: Learn how to create searchable PDF Java files with GroupDocs annotation.
    This step‑by‑step guide covers setup, code, tips, and troubleshooting.
  name: Create searchable PDF Java files using GroupDocs annotation
  steps:
  - name: initialize the annotator
    text: 'The `Annotator` class is GroupDocs.Annotation''s primary engine for loading,
      modifying, and saving PDF files. The `Annotator` class is your main interface
      for PDF manipulation. It handles file loading, modification, and saving: **Why
      this matters:** Using a try‑with‑resources block guarantees that th'
  - name: create your text fragment
    text: '`SearchTextFragment` represents a searchable text annotation that can be
      positioned and styled within a PDF. The `SearchTextFragment` object defines
      what text you want to highlight and how it should appear:'
  - name: define the target text
    text: 'Specify the exact string you want to make searchable. The match must be
      case‑exact and include any punctuation that appears in the source PDF. Specify
      exactly what text you want to make searchable: **Important:** PDF text extraction
      can introduce hidden Unicode characters; if the annotation fails to'
  - name: customize the appearance
    text: 'You can control background color, text color, opacity, and border style.
      The ARGB values are expressed as `0xAARRGGBB`. This is where you can make your
      annotations visually distinctive: **Color‑coding tip:** The numbers `0x7FFF0000`
      (semi‑transparent red) and `0xFF0000FF` (opaque blue) have been tes'
  - name: apply and save
    text: 'Add the fragment to the annotator and write the updated PDF to disk. The
      `close()` call inside the try‑with‑resources block frees native memory. Add
      the annotation and save your enhanced PDF: The closing brace automatically disposes
      of the `Annotator` object, freeing up memory.'
  type: HowTo
- questions:
  - answer: Absolutely. Create several `SearchTextFragment` objects (or other annotation
      types) and add them all before calling `save`.
    question: Can I add multiple different annotations to the same PDF?
  - answer: Yes. GroupDocs creates standard PDF annotation objects that are displayed
      correctly in Adobe Acrobat, Chrome, Edge, and most third‑party viewers. Colors
      may vary slightly due to viewer rendering engines.
    question: Will annotations work in all PDF viewers?
  - answer: GroupDocs.Annotation processes the visual text flow, so you only need
      to ensure the exact string you supply matches the extracted text, regardless
      of column order.
    question: How do I handle PDFs with complex layouts or multiple columns?
  - answer: There is no hard limit on the number of annotations. In practice, adding
      thousands of highlights may increase rendering time in some viewers, so batch
      them logically (e.g., per chapter).
    question: Is there a limit to how much text I can annotate?
  - answer: Yes. Use the `getAnnotations()` method to retrieve existing objects, then
      call `update()` or `delete()` as needed.
    question: Can I modify or remove annotations after adding them?
  type: FAQPage
tags:
- pdf-processing
- java-libraries
- document-annotation
- groupdocs
title: GroupDocs annotation을 사용하여 검색 가능한 PDF Java 파일 만들기
type: docs
url: /ko/java/text-annotations/add-search-text-annotations-pdf-groupdocs-java/
weight: 1
---

# GroupDocs 주석을 사용하여 검색 가능한 PDF Java 파일 만들기

검색 가능한 PDF Java 파일을 **생성**하여 사용자가 중요한 구절로 바로 이동할 수 있도록 하려면, 여기가 바로 정답입니다. 법률 계약서, 기술 매뉴얼, 연구 논문 등을 처리하든, 검색 가능한 텍스트 주석은 정적인 PDF를 인터랙티브한 지식 베이스로 전환하여 생산성과 협업을 향상시킵니다.

이 튜토리얼에서는 GroupDocs.Annotation for Java를 사용하여 프로그래밍 방식으로 검색 가능한 텍스트 주석을 추가하는 방법을 알아봅니다. 환경 설정부터 시작해 코드 한 줄씩 살펴보고, 고급 스타일 옵션을 탐색하며, 실제 프로젝트에 적용할 수 있는 문제 해결 팁으로 마무리합니다.

## 빠른 답변
- **“searchable PDF Java”가 무엇을 의미하나요?** 표준 PDF 텍스트 검색 기능으로 검색 가능한 텍스트 기반 주석이 포함된 PDF입니다.  
- **어떤 라이브러리를 사용해야 하나요?** GroupDocs.Annotation for Java는 검색 가능한 하이라이트를 위한 완전하고 프로덕션 준비된 API를 제공합니다.  
- **시도하려면 라이선스가 필요합니까?** 필요 없습니다—GroupDocs는 여기서 시연된 모든 기능을 사용할 수 있는 무료 체험판을 제공합니다.  
- **한 번에 여러 주석을 추가할 수 있나요?** 예, 여러 `SearchTextFragment` 객체를 생성하고 저장하기 전에 추가하면 됩니다.  
- **이 방법이 대용량 PDF에 메모리 친화적인가요?** try‑with‑resources와 배치 처리를 사용하면 수천 페이지 PDF에서도 메모리 사용량이 200 MB 이하로 유지됩니다.  

## Java PDF 텍스트 주석이 중요한 이유

검색 가능한 주석은 문서를 보기 좋게 만드는 것 이상의 역할을 합니다:

- **즉시 탐색** – 사용자가 하이라이트된 구문을 클릭하면 해당 페이지로 바로 이동합니다.  
- **팀 협업** – 검토자는 무한히 스크롤하지 않고 정확한 용어에 댓글을 달 수 있습니다.  
- **자동 처리** – 스크립트가 핵심 조항을 찾아 추출하거나 후속 워크플로를 트리거할 수 있습니다.  
- **향상된 접근성** – 스크린 리더가 하이라이트된 용어를 읽어 시각 장애 사용자의 사용성을 개선합니다.  

## 시작하기 위해 필요한 것

아래는 코딩을 시작하기 전에 갖추어야 할 최소 체크리스트입니다.

### 필수 요구 사항
- **Java Development Kit (JDK)** – 버전 8 이상; 더 나은 가비지 컬렉션 성능을 위해 JDK 11+ 권장.  
- **IDE** – IntelliJ IDEA, Eclipse 또는 선호하는 Java 호환 편집기.  
- **Maven** – 의존성 관리를 위해 사용 (Gradle도 가능하지만 예제는 Maven 사용).  
- **기본 Java 지식** – 객체, try‑with‑resources, 예외 처리에 익숙함.  

### GroupDocs.Annotation 라이브러리
- **버전** – 25.2 이상 (최신 릴리스는 대용량 PDF에 대해 30 % 속도 향상을 제공합니다).  
- **라이선스** – 무료 체험으로 시작; 장기 평가를 위한 임시 라이선스가 제공되며, 프로덕션 배포에는 정식 라이선스가 필요합니다.  

## 개발 환경 설정

지금 몇 분만 투자해 Maven을 올바르게 구성하면 나중에 디버깅에 소요되는 시간을 크게 절약할 수 있습니다.

### Maven 구성

`pom.xml`에 GroupDocs 저장소와 Annotation 의존성을 추가합니다. 아래 스니펫은 복사‑붙여넣기 바로 사용할 수 있습니다:

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

**팁:** 기업 프록시 뒤에서 작업하는 경우 `~/.m2/settings.xml` 파일에 프록시 설정을 추가하여 Maven이 GroupDocs 저장소에 중단 없이 접근할 수 있도록 하세요.

### 라이선스 설정 옵션

다음 세 가지 방법이 있습니다:

1. **무료 체험** – 전체 API 접근 가능, 신용카드 필요 없음.  
2. **임시 라이선스** – PoC를 위해 체험 기간을 연장.  
3. **정식 라이선스** – 무제한 프로덕션 사용 및 우선 지원 제공.  

개발 중에는 라이선스 파일을 생략할 수 있습니다; `Annotator`를 인스턴스화하면 체험 키가 자동으로 적용됩니다.

## 핵심 구현: 검색 가능한 텍스트 주석 추가

이제 실제로 주석을 생성하는 코드로 이동합니다. 아래 각 블록은 워크플로의 단계에 해당합니다.

### 기본 구현 단계

아래는 다섯 단계로 나눈 전체 흐름입니다.

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.annotationmodels.SearchTextFragment;
```

#### 단계 1: annotator 초기화

`Annotator` 클래스는 PDF 파일을 로드, 수정 및 저장하기 위한 GroupDocs.Annotation의 주요 엔진입니다.

`Annotator` 클래스는 PDF 조작을 위한 주요 인터페이스이며, 파일 로드, 수정 및 저장을 담당합니다:

```java
try (final Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
```

**왜 중요한가:** try‑with‑resources 블록을 사용하면 `Annotator`가 보유한 네이티브 리소스가 자동으로 해제되어 배치로 많은 문서를 처리할 때 메모리 누수를 방지합니다.

#### 단계 2: 텍스트 조각 생성

`SearchTextFragment`는 PDF 내에서 위치와 스타일을 지정할 수 있는 검색 가능한 텍스트 주석을 나타냅니다.

`SearchTextFragment` 객체는 강조하고자 하는 텍스트와 그 표시 방식을 정의합니다:

```java
SearchTextFragment searchTextFragment = new SearchTextFragment();
```

#### 단계 3: 대상 텍스트 정의

검색하려는 정확한 문자열을 지정합니다. 일치는 대소문자를 구분하며 원본 PDF에 나타나는 모든 구두점을 포함해야 합니다.

검색하려는 정확한 텍스트를 지정하세요:

```java
searchTextFragment.setText("Welcome to GroupDocs");
```

**중요:** PDF 텍스트 추출 시 숨겨진 유니코드 문자가 포함될 수 있습니다; 주석이 나타나지 않으면 먼저 페이지 텍스트를 추출하고 정확한 문자열을 코드에 복사‑붙여넣기 하세요.

#### 단계 4: 외관 맞춤화

배경색, 텍스트 색, 불투명도, 테두리 스타일을 제어할 수 있습니다. ARGB 값은 `0xAARRGGBB` 형식으로 표현됩니다.

여기서 주석을 시각적으로 구별되게 만들 수 있습니다:

```java
// Set font size for better readability
searchTextFragment.setFontSize(10);

// Choose a professional font family
searchTextFragment.setFontFamily("Calibri");

// Set text color (ARGB format - this creates a bright blue)
searchTextFragment.setFontColor(65535); 

// Add background highlighting (this creates a light yellow background)
searchTextFragment.setBackgroundColor(16761035);
```

**색상 코딩 팁:** `0x7FFF0000` (반투명 빨강)과 `0xFF0000FF` (불투명 파랑) 값은 화면과 인쇄 모두에서 높은 대비를 제공하도록 테스트되었습니다.

#### 단계 5: 적용 및 저장

조각을 annotator에 추가하고 업데이트된 PDF를 디스크에 기록합니다. try‑with‑resources 블록 내부의 `close()` 호출은 네이티브 메모리를 해제합니다.

주석을 추가하고 향상된 PDF를 저장하세요:

```java
   annotator.add(searchTextFragment);
   annotator.save("YOUR_OUTPUT_DIRECTORY/result_add_search_text.pdf");
}
```

닫는 중괄호가 `Annotator` 객체를 자동으로 해제하여 메모리를 확보합니다.

## 고급 맞춤 옵션

기본이 작동하면 여러 주석 유형, 사용자 정의 폰트, 전략적 색상 팔레트를 사용해 경험을 풍부하게 할 수 있습니다.

### 다중 주석 유형

GroupDocs.Annotation을 사용하면 검색 가능한 텍스트와 하이라이트, 스탬프, 댓글을 하나의 문서에 혼합할 수 있습니다.

```java
// Create different annotations for different purposes
SearchTextFragment importantClause = new SearchTextFragment();
importantClause.setText("IMPORTANT:");
importantClause.setBackgroundColor(16711680); // Red background for critical items

SearchTextFragment noteSection = new SearchTextFragment();
noteSection.setText("Note:");
noteSection.setBackgroundColor(65280); // Green background for informational notes
```

### 폰트 맞춤 모범 사례

문서 목적에 맞는 폰트를 선택하세요:

- **Calibri 또는 Arial** – 비즈니스 보고서에 이상적.  
- **Times New Roman** – 법률 계약서 표준.  
- **Courier New** – 기술 매뉴얼의 코드 스니펫에 적합.  

### 전문 문서를 위한 색상 전략

다음은 PDF 뷰어 전반에서 가독성을 높게 유지하는 세 가지 테스트된 색상 조합입니다:

- **중요 항목** – 빨간 배경 (`#FF0000`)에 흰색 텍스트.  
- **중요 메모** – 노란 배경 (`#FFFF00`)에 검은색 텍스트.  
- **일반 하이라이트** – 연한 파란 배경 (`#ADD8E6`)에 진한 파란 텍스트.  

## 일반적인 문제와 해결책

다음은 가장 흔히 마주칠 문제와 간결한 해결 방법입니다.

### 파일 경로 문제

**문제:** PDF를 열 때 `FileNotFoundException` 발생.  
**해결책:** 개발 중 절대 경로를 사용하고 `Annotator`를 생성하기 전에 경로를 검증하세요:

```java
File inputFile = new File("YOUR_DOCUMENT_DIRECTORY/input.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Input PDF file not found: " + inputFile.getAbsolutePath());
}
```

### 텍스트 미발견 오류

**문제:** 검색 텍스트를 찾지 못해 주석이 나타나지 않음.  
**해결책:** 페이지 텍스트를 먼저 추출하여 정확한 문자열(공백 및 구두점 포함)을 확인하세요:

```java
// Use this approach to verify text exists before annotating
// (This is debugging code, not for production)
```

### 대용량 PDF 메모리 문제

**문제:** 500 MB 이상 PDF 처리 시 `OutOfMemoryError` 발생.  
**해결책:** JVM 힙을 (`-Xmx2g`) 늘리고 배치로 문서를 처리하며 가능한 경우 단일 `Annotator` 인스턴스를 재사용하세요:

```bash
java -Xmx2g -Xms1g YourApplication
```

### 권한 문제

**문제:** 출력 파일을 쓸 수 없음.  
**해결책:** 애플리케이션이 대상 폴더에 쓰기 권한을 가지고 실행되도록 하거나, 임시 디렉터리에 쓰고 처리 후 파일을 이동하세요.

## 성능 최적화 팁

데모에서 프로덕션 파이프라인으로 전환할 때, 다음 조정이 눈에 띄는 차이를 만듭니다.

### 리소스 관리

`Annotator`를 항상 try‑with‑resources 블록으로 감싸세요. 이 패턴은 장기 실행 서비스가 충돌할 수 있는 네이티브 메모리 누수 위험을 없애줍니다.

```java
// Good practice - automatic resource cleanup
try (final Annotator annotator = new Annotator(inputPath)) {
    // Your annotation code here
} // Automatically closes and cleans up resources
```

### 배치 처리 전략

파일당 하나의 `Annotator`를 생성하고, 필요한 모든 `SearchTextFragment` 객체를 추가한 뒤 `save`를 호출합니다. 여러 파일에 동일 `Annotator` 인스턴스를 재사용하면 네이티브 라이브러리 로딩을 반복하지 않아도 됩니다.

```java
// Process multiple annotations on the same document efficiently
try (final Annotator annotator = new Annotator(inputPath)) {
    // Add all annotations before saving
    annotator.add(annotation1);
    annotator.add(annotation2);
    annotator.add(annotation3);
    
    // Single save operation
    annotator.save(outputPath);
}
```

### 대용량 PDF 메모리 관리

GroupDocs.Annotation은 스트리밍 아키텍처 덕분에 **5,000 페이지**까지의 PDF를 처리하면서 메모리 사용량을 **200 MB** 이하로 유지합니다. 이를 위해:

`DocumentPageIterator`는 PDF 페이지를 순차적으로 처리할 수 있는 반복자를 제공하여 관리 가능한 배치로 나눕니다.
- `DocumentPageIterator`를 사용해 페이지를 청크 단위로 처리합니다.
- 텍스트 하이라이트만 필요하면 이미지 추출과 같은 불필요한 기능을 비활성화하세요.

## 실제 적용 사례와 사용 예시

비즈니스 가치를 이해하면 이 기술을 적용할 위치를 결정하는 데 도움이 됩니다.

### 법률 문서 처리

법무법인은 클라이언트 승인이 필요한 조항을 하이라이트하고 위험한 문구를 표시하며, 모든 하이라이트된 섹션의 보고서를 생성합니다. 일관된 빨간 배경 하이라이트는 “중요 검토 필요”를 나타냅니다.

### 기술 문서

소프트웨어 팀은 PDF 릴리스 노트에 API 변경, 폐기, 보안 권고를 직접 주석 달아 엔지니어가 업데이트를 즉시 찾을 수 있게 합니다.

### 교육 자료

교수는 핵심 개념에 검색 가능한 하이라이트를 삽입해 스크린 리더나 모바일 PDF 뷰어를 사용하는 학생들에게 학습 가이드를 더 인터랙티브하게 만듭니다.

## 통합 모범 사례

### 엔터프라이즈 통합 패턴
1. **API‑first 설계** – 주석 로직을 REST 엔드포인트로 노출합니다.  
2. **비동기 처리** – PDF 파일을 메시지 큐(e.g., RabbitMQ)로 푸시하고 워커 서비스가 주석을 적용하도록 합니다.  
3. **오류 복구** – 일시적인 I/O 실패에 대한 재시도 로직을 구현합니다.  
4. **모니터링** – 구조화된 로거(e.g., Logback)를 사용해 주석 처리 시간과 메모리 사용량을 기록합니다.  

### 보안 고려 사항
- 디렉터리 트래버설 공격을 방지하기 위해 파일 경로를 검증합니다.  
- 주석 서비스 엔드포인트에 역할 기반 접근 제어를 적용합니다.  
- 민감한 데이터가 포함된 경우, 파일을 쓰기 전에 Java의 `Cipher` API를 사용해 PDF를 암호화합니다.  

## 문제 해결 가이드

### 빠른 진단 체크리스트
1. **파일 권한** – 프로세스가 원본 PDF를 읽고 대상 폴더에 쓸 수 있나요?  
2. **경로 정확성** – Windows(`\`)와 Linux(`/`) 구분자를 다시 확인하세요.  
3. **라이브러리 버전** – GroupDocs.Annotation 25.2 이상을 사용하고 있는지 확인하세요; 이전 버전은 배치 처리 최적화가 없습니다.  
4. **JVM 메모리** – 힙 크기(`-Xmx`)가 처리하는 PDF 크기에 맞는지 확인하세요.  
5. **정확한 텍스트 일치** – 빠른 추출을 실행해 주석 문자열이 그대로 존재하는지 확인하세요.  

### 디버그 모드 활성화

내부 검색 과정을 캡처하려면 자세한 로깅을 활성화하세요:

```java
// Add this to see detailed processing information
System.setProperty("groupdocs.annotation.debug", "true");
```

로그는 스캔된 각 페이지와 대상 구문이 발견됐는지를 나열하여 불일치를 정확히 찾는 데 도움을 줍니다.

## 자주 묻는 질문

**Q: 같은 PDF에 여러 종류의 주석을 추가할 수 있나요?**  
A: 물론입니다. 여러 `SearchTextFragment` 객체(또는 다른 주석 유형)를 생성하고 `save` 호출 전에 모두 추가하면 됩니다.

**Q: 모든 PDF 뷰어에서 주석이 작동하나요?**  
A: 네. GroupDocs는 Adobe Acrobat, Chrome, Edge 및 대부분의 서드파티 뷰어에서 올바르게 표시되는 표준 PDF 주석 객체를 생성합니다. 색상은 뷰어 렌더링 엔진에 따라 약간 다를 수 있습니다.

**Q: 복잡한 레이아웃이나 다중 컬럼이 있는 PDF를 어떻게 처리하나요?**  
A: GroupDocs.Annotation은 시각적 텍스트 흐름을 처리하므로, 컬럼 순서와 관계없이 제공한 정확한 문자열이 추출된 텍스트와 일치하는지만 확인하면 됩니다.

**Q: 주석을 달 수 있는 텍스트 양에 제한이 있나요?**  
A: 주석 수에 엄격한 제한은 없습니다. 실제로 수천 개의 하이라이트를 추가하면 일부 뷰어에서 렌더링 시간이 늘어날 수 있으므로 논리적으로 배치하세요(예: 챕터별).

**Q: 주석을 추가한 후 수정하거나 제거할 수 있나요?**  
A: 가능합니다. `getAnnotations()` 메서드로 기존 객체를 가져온 뒤 필요에 따라 `update()` 또는 `delete()`를 호출하세요.

**Q: PDF에서 주석 텍스트를 찾지 못하면 어떻게 되나요?**  
A: API가 조용히 추가를 건너뛰며 예외는 발생하지 않지만 주석이 표시되지 않습니다. 항상 먼저 일치를 확인하세요.

**Q: 주석이 달린 PDF의 접근성을 어떻게 보장할 수 있나요?**  
A: 고대비 색상을 선택하고 색상만으로 의미를 전달하지 않으며, 각 주석에 설명 텍스트를 추가해 스크린 리더가 목적을 알릴 수 있게 하세요.

## 결론

이제 GroupDocs.Annotation을 사용해 **검색 가능한 PDF Java** 파일을 만드는 완전하고 프로덕션 준비된 레시피를 갖추었습니다. 위 단계들을 따르면 다음을 수행할 수 있습니다:

- 최신 라이브러리로 깔끔한 Maven 프로젝트 설정.  
- 즉시 검색 가능한 단일 라인 하이라이트 추가.  
- ARGB 색상 및 폰트 선택으로 외관 맞춤화.  
- 메모리 사용량을 낮게 유지하면서 수천 페이지로 솔루션 확장.  

기본 예제로 시작한 뒤, 다중 주석 유형, 배치 처리, REST‑API 노출을 실험해 기존 문서 관리 파이프라인에 이 기능을 통합해 보세요. 오늘 투자한 노력은 더 빠른 검토, 적은 수동 검색, 더 만족스러운 최종 사용자로 이어집니다.

---
**마지막 업데이트:** 2026-09-15  
**테스트 환경:** GroupDocs.Annotation 25.2 (Java)  
**작성자:** GroupDocs  

**리소스 및 추가 읽을거리**
- [GroupDocs.Annotation for Java 문서](https://docs.groupdocs.com/annotation/java/)  
- [전체 API 레퍼런스 가이드](https://reference.groupdocs.com/annotation/java/)  
- [GroupDocs 릴리스](https://releases.groupdocs.com/annotation/java/)  
- [GroupDocs 라이선스 구매](https://purchase.groupdocs.com/buy)  
- [무료 체험 시작](https://releases.groupdocs.com/annotation/java/)  
- [연장된 체험 라이선스 받기](https://purchase.groupdocs.com/temporary-license/)  
- [GroupDocs 지원 포럼](https://forum.groupdocs.com/c/annotation/)  

## 관련 튜토리얼
- [PDF 하이라이트 Java 추가 – 텍스트 주석 완전 가이드](/annotation/java/text-annotations/)  
- [PDF 하이라이트 Java 만들기: GroupDocs Annotation 완전 가이드](/annotation/java/annotation-management/)  
- [GroupDocs Annotation으로 PDF Java 로드: 문서 로딩 가이드](/annotation/java/document-loading/)