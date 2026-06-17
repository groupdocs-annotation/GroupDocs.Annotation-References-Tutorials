---
categories:
- PDF Processing
date: '2026-05-26'
description: GroupDocs Annotation for .NET를 사용하여 문서 검토 시스템을 만드는 방법을 배웁니다. 단계별 튜토리얼에서는
  설정, 주석 유형, 성능 튜닝 및 C# 개발자를 위한 문제 해결을 다룹니다.
keywords:
- create document review system
- PDF annotation .NET
- GroupDocs annotation tutorial
lastmod: '2026-05-26'
linktitle: PDF Annotation .NET Guide
schemas:
- author: GroupDocs
  dateModified: '2026-05-26'
  description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  headline: 'Create Document Review System: PDF Annotation .NET Guide'
  type: TechArticle
- description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  name: 'Create Document Review System: PDF Annotation .NET Guide'
  steps:
  - name: Create an AreaAnnotation
    text: '`AreaAnnotation` represents a rectangular highlight area on a PDF page.'
  - name: Create an EllipseAnnotation
    text: '`EllipseAnnotation` represents an elliptical shape annotation on a PDF
      page.'
  - name: Add Annotations in Bulk
    text: '**Pro Tip:** Adding annotations in a list and calling `Add` once reduces
      I/O overhead, especially when you need to insert dozens of marks across many
      pages.'
  type: HowTo
- questions:
  - answer: GroupDocs automatically reads each page’s dimensions. When positioning
      annotations, always query `annotator.GetPageInfo(pageNumber)` and calculate
      coordinates based on that page’s width and height.
    question: How do I handle PDFs with different page sizes?
  - answer: Yes. Use the `LoadOptions` constructor that accepts a password string,
      e.g., `new LoadOptions { Password = "secret" }`, and pass it to the `Annotator`
      constructor.
    question: Can I annotate password‑protected PDFs?
  - answer: There is no hard limit, but performance degrades after a few thousand
      annotations. For very large annotation sets, group them into logical sections
      and process each section separately.
    question: What is the maximum number of annotations I can add to a single PDF?
  - answer: Retrieve the annotation’s `Id` via `GetAnnotations()`, then call `Delete(id)`
      or create a `SaveOptions` instance that excludes the unwanted `AnnotationType`.
    question: How do I remove specific annotations programmatically?
  - answer: Absolutely. You can set opacity, border thickness, dash style, and even
      embed custom SVG icons for stamp annotations.
    question: Can I customize annotation appearance beyond colors?
  type: FAQPage
tags:
- pdf-annotation
- groupdocs
- dotnet
- csharp
- document-processing
title: '문서 검토 시스템 만들기: PDF Annotation .NET Guide'
type: docs
url: /ko/net/annotation-management/annotate-pdfs-groupdocs-annotation-net/
weight: 1
---

# 문서 검토 시스템 만들기: PDF 주석 .NET 가이드

.NET 애플리케이션에서 직접 PDF에 댓글, 하이라이트 및 도형을 추가할 수 있는 **문서 검토 시스템**을 만들고 싶다면, 바로 여기가 정답입니다. GroupDocs.Annotation for .NET은 저수준 PDF 처리를 복잡하게 만드는 문제를 없애면서 모든 주석 유형에 대해 세밀한 제어를 제공합니다. 이 가이드에서는 라이브러리를 설정하고, 영역, 타원 및 텍스트 주석을 추가하고, 저장되는 내용을 필터링하며, 수백 페이지 파일에서도 성능을 빠르게 유지하는 방법을 보여줍니다.

## 빠른 답변
- **.NET에서 PDF 주석을 처리하는 라이브러리는?** GroupDocs.Annotation for .NET.
- **하이라이트, 원, 댓글을 프로그래밍 방식으로 추가할 수 있나요?** 예 – `AreaAnnotation`, `EllipseAnnotation` 및 `TextAnnotation` 객체를 사용합니다.
- **프로덕션에 라이선스가 필요합니까?** 모든 프로덕션 배포에는 유효한 GroupDocs 라이선스가 필수입니다.
- **처리할 수 있는 PDF 크기는 얼마나 됩니까?** 전체 파일을 메모리에 로드하지 않고도 최대 500 MB까지 처리할 수 있습니다.
- **이것이 문서 검토 시스템을 만드는 데 도움이 됩니까?** 물론입니다 – 주석을 일괄 저장, 필터링 및 버전 관리하여 검토자를 지원할 수 있습니다.

## 문서 검토 시스템이란?
**문서 검토 시스템**은 여러 이해관계자가 PDF 파일에 주석을 달고, 댓글을 달며, 승인하는 협업 워크플로를 제공하는 소프트웨어 솔루션입니다. 피드백을 중앙 집중화하고, 변경 사항을 추적하며, 최종 승인용 깨끗한 버전을 내보내는 경우가 많습니다.

## GroupDocs Annotation for .NET을 사용해 문서 검토 시스템을 만드는 이유
GroupDocs Annotation은 **30개 이상의 주석 유형**을 지원하고, **500 MB**까지의 PDF를 처리하며, **.NET Framework 4.6.1+**, **.NET Core 2.0+**, **.NET 6+**에서 실행됩니다. API를 통해 PDF 내부 구조를 건드리지 않고도 주석을 추가, 제거 및 필터링할 수 있어 개발 속도가 빨라지고 버그가 감소합니다.

## 사전 요구 사항 및 환경 설정

코드를 작성하기 전에 개발 환경이 다음 기준을 충족하는지 확인하십시오:

- **IDE:** Visual Studio 2019 이상 또는 C# 확장이 설치된 VS Code.
- **대상 프레임워크:** .NET Framework 4.6.1 + 또는 .NET Core 2.0 + (새 프로젝트에는 .NET 6 권장).
- **NuGet 접근:** nuget.org에서 패키지를 설치할 수 있어야 함.
- **샘플 PDF:** 주석 위치 테스트를 위한 최소 1개의 다중 페이지 PDF.
- **메모리 및 디스크:** 최소 4 GB RAM 및 임시 파일을 위한 충분한 여유 디스크 공간(주석 처리 시 임시 스트림이 생성될 수 있음).

### 권장 개발 관행
- 솔루션을 **Git** 등 소스 컨트롤에 보관하여 주석 관련 변경을 롤백할 수 있도록 합니다.
- 프로젝트에 **Annotations** 폴더를 만들어 구성 파일 및 라이선스 키를 저장합니다.
- **nullable reference types**(`\<Nullable>enable\</Nullable>`)를 활성화하여 잠재적인 null‑reference 버그를 조기에 포착합니다.

## 시작하기: GroupDocs.Annotation 설치

### 설치 방법

**옵션 1: NuGet 패키지 관리자 콘솔**  
패키지 관리자 콘솔에서 다음 명령을 실행합니다:  

`Install-Package GroupDocs.Annotation`

**옵션 2: .NET CLI (크로스‑플랫폼 개발 권장)**  
터미널에서 실행합니다:  

`dotnet add package GroupDocs.Annotation`

**옵션 3: Visual Studio 패키지 관리자 UI**  
- 프로젝트를 우클릭 → **Manage NuGet Packages**  
- **GroupDocs.Annotation** 검색  
- 최신 안정 버전의 **Install** 클릭  

세 방법 모두 동일한 바이너리를 설치합니다; 워크플로에 맞는 방법을 선택하십시오.

### 라이선스 구성

GroupDocs는 모든 프로덕션 사용에 유효한 라이선스를 요구합니다. 선택 가능한 경로는 다음과 같습니다:

- **무료 체험:** 전체 기능을 제공하는 30일 평가판.  
- **임시 라이선스:** 개발 및 테스트용 연장 평가판.  
- **상용 라이선스:** 프로덕션 환경에서 무제한 사용.

`License` 클래스는 GroupDocs 라이선스 파일을 로드하고 적용하여 전체 기능을 활성화합니다. 라이선스는 [GroupDocs 구매 페이지](https://purchase.groupdocs.com/buy)에서 얻을 수 있습니다. `.lic` 파일을 받은 후, 애플리케이션이 읽을 수 있는 폴더에 배치하고 시작 시 `License` 클래스에 경로를 지정하십시오.

### 초기 설정 확인

PDF를 로드하고 페이지 수를 콘솔에 출력하는 작은 콘솔 프로그램을 만들어 보세요. 예외가 발생하지 않으면 라이브러리가 올바르게 설치되고 라이선스가 적용된 것입니다.

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;

var annotator = new Annotator("sample.pdf");
var info = annotator.GetDocumentInfo();
Console.WriteLine($"Pages: {info.PageCount}");
```

> **참고:** 위 코드는 예시용이며 최종 문서에 fenced code block을 넣을 필요는 없지만, 인라인 스니펫은 정확한 API 사용법을 보여줍니다.

페이지 수가 출력되면 실제 주석 추가를 시작할 준비가 된 것입니다.

## 핵심 구현: PDF에 주석 추가하기

### 정의 앵커 – Annotator
`Annotator` 클래스는 GroupDocs.Annotation for .NET에서 모든 PDF 주석 작업의 진입점입니다. PDF를 메모리로 로드하고, 주석을 추가·편집·조회하는 메서드를 제공하며, 수정된 문서를 저장하는 역할을 담당합니다.

### 영역 및 타원 주석을 어떻게 추가하나요?
`new Annotator(...)`로 PDF를 로드하고, `AreaAnnotation` 및 `EllipseAnnotation` 객체를 생성한 뒤 좌표를 설정하고, 컬렉션에 추가합니다. 마지막으로 `Save`를 호출해 변경 사항을 영구 저장합니다. 이 워크플로를 통해 단일 원자적 작업으로 섹션을 강조(영역)하거나 중요한 그래픽을 원으로 둘러쌀 수 있습니다.

#### 1단계: Annotator 초기화
```csharp
var annotator = new Annotator("input.pdf");
```

#### 2단계: AreaAnnotation 생성
`AreaAnnotation`은 PDF 페이지에 사각형 강조 영역을 나타냅니다.  
```csharp
var area = new AreaAnnotation
{
    PageNumber = 0,
    Box = new RectangleF(100, 150, 200, 50),
    Color = Color.Yellow,
    Opacity = 0.4f,
    Text = "Review this paragraph"
};
```

#### 3단계: EllipseAnnotation 생성
`EllipseAnnotation`은 PDF 페이지에 타원형 도형 주석을 나타냅니다.  
```csharp
var ellipse = new EllipseAnnotation
{
    PageNumber = 2,
    Box = new RectangleF(300, 400, 120, 80),
    Color = Color.Red,
    Opacity = 0.6f,
    Text = "Check this figure"
};
```

#### 4단계: 주석을 일괄 추가
```csharp
annotator.Add(new List<AnnotationBase> { area, ellipse });
annotator.Save("output.pdf");
```

**팁:** 주석을 리스트에 모아 한 번에 `Add`하면 I/O 오버헤드가 감소합니다. 특히 여러 페이지에 수십 개의 마크를 삽입할 때 유용합니다.

### 선택적 주석만 저장하려면 어떻게 하나요?
`SaveOptions`는 주석이 포함된 PDF 저장 방식을 구성하며, 포함할 주석 유형을 지정할 수 있습니다. GroupDocs.Annotation은 출력 파일에 기록할 주석 유형을 필터링할 수 있게 해줍니다. `SaveOptions` 인스턴스를 만들고 `AnnotationTypes` 컬렉션에 유지하고 싶은 유형을 설정한 뒤 `Save`에 전달하십시오. 이는 검토자 전용 PDF를 생성하거나 보관 전 임시 메모를 제거할 때 이상적입니다.

```csharp
var saveOptions = new SaveOptions
{
    AnnotationTypes = new[] { AnnotationType.Text, AnnotationType.Area }
};
annotator.Save("filtered.pdf", saveOptions);
```

## 실제 구현 시나리오

### 시나리오 1: 문서 검토 워크플로
여러 검토자가 **Area**, **Ellipse**, **Text** 주석을 추가합니다. 검토가 끝나면 세 가지 PDF를 생성합니다:
1. 모든 댓글이 포함된 전체 버전.  
2. 내부 메모를 제외한 검토자 전용 버전.  
3. 하이라이트만 남긴 최종 승인용 클린 버전.

### 시나리오 2: 자동 보고서 생성
백엔드가 일일 매출 보고서를 처리하면서 영역 주석으로 핵심 지표를 강조하고, 타원 주석으로 이상 차트를 둘러씁니다. 생성된 PDF는 자동으로 이해관계자에게 이메일로 전송됩니다.

### 시나리오 3: 협업 법률 문서
법무법인에서는 파트너 의견과 주니어 어소시에이트 메모를 구분해야 합니다. 주석에 사용자 정의 메타데이터를 태그하고 선택적 저장을 활용하면 주니어 메모를 숨긴 파트너 검토용 PDF를 만들 수 있어 버전 관리가 간소화됩니다.

## 프로덕션 사용을 위한 성능 최적화

### 대용량 PDF 주석 시 메모리 관리 방법은?
`LoadOptions`를 사용하면 페이지 범위나 비밀번호 등 로드 방식을 지정할 수 있습니다. PDF가 100 MB를 초과하면 전체 파일을 로드하지 말고 페이지 범위를 받는 `LoadOptions` 생성자를 사용하십시오. 페이지를 배치로 처리하고, 각 `Annotator` 인스턴스를 `using` 블록으로 폐기하며, 배치마다 임시 파일을 정리하면 500‑페이지 문서에서도 피크 메모리를 200 MB 이하로 유지할 수 있습니다.

```csharp
using (var annotator = new Annotator("large.pdf", new LoadOptions { PageNumbers = new[] { 0, 1, 2 } }))
{
    // annotate first three pages
}
```

### 메모리 관리 모범 사례
- **항상 `Annotator`를 `using` 문으로 감싸** 비관리 리소스가 확실히 해제되도록 합니다.  
- **주석을 배치 처리**: 문서당 모든 주석을 수집한 뒤 한 번에 `Add`합니다.  
- **전체 PDF를 로드하지 않음**: 필요한 페이지만 수정할 경우 `LoadOptions.PageNumbers`를 사용합니다.

### 대용량 파일 처리 전략
1. **페이지 단위 처리** – 한 페이지씩 로드·주석·저장.  
2. **스트리밍 출력** – `Save` 메서드를 `MemoryStream`에 직접 전달해 중간 디스크 쓰기를 피함.  
3. **임시 파일 정리** – 각 작업 후 Annotator가 만든 임시 파일을 삭제합니다.

### 동시 처리 고려 사항
- **스레드 안전성:** `Annotator` 인스턴스는 스레드‑안전하지 않으므로 스레드당 별도 인스턴스를 생성합니다.  
- **리소스 제한:** CPU 코어 수 만큼 동시 작업을 제한해 CPU 과부하를 방지합니다.  
- **비동기 API:** `SaveAsync`는 주석이 달린 문서를 비동기적으로 저장하고 `Task`를 반환하므로 ASP.NET Core 환경에서 유용합니다.

## 일반적인 문제 해결

### 문제 1: “File Not Found” 오류
**직접 답변:** `new Annotator(...)`에 전달한 파일 경로가 절대 경로나 실행 어셈블리 기준으로 올바른 상대 경로인지 확인하고, 해당 위치에 대한 읽기 권한이 있는지 확인하십시오. 네트워크 공유에 파일이 있는 경우 공유를 매핑하거나 UNC 경로를 사용합니다.

**일반적인 해결책:**  
- `Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Docs", "sample.pdf")` 사용.  
- IIS 애플리케이션 풀 아이덴티티에 폴더에 대한 읽기/쓰기 권한 부여.

### 문제 2: 주석이 잘못된 위치에 표시됨
**직접 답변:** 동일한 좌표계(좌상단 원점)를 사용하고 페이지 DPI가 제공한 값과 일치하는지 확인하십시오. `annotator.GetPageInfo(pageNumber)`로 페이지 크기를 가져와 해당 크기에 상대적인 좌표를 계산합니다.

**일반적인 해결책:**  
- PDF가 비표준 DPI로 생성된 경우 페이지 스케일링 팩터에 좌표를 곱합니다.  
- 포인트(1/72인치)와 픽셀을 혼용하지 않았는지 재확인.

### 문제 3: 대용량 파일에서 성능 저하
**직접 답변:** 페이지 범위 로딩으로 전환하고, 주석을 배치 처리하며, 각 `Annotator` 인스턴스를 즉시 폐기하십시오. 또한 `LoadOptions`의 `MemoryCache` 옵션을 활성화해 버퍼를 재사용합니다.

**일반적인 해결책:**  
- `LoadOptions.UseMemoryCache = true` 설정.  
- `await annotator.SaveAsync(...)`로 비동기 처리.

### 문제 4: 라이선스 관련 오류
**직접 답변:** `.lic` 파일을 애플리케이션이 읽을 수 있는 폴더에 두고, 다른 GroupDocs 호출 전에 `License license = new License(); license.SetLicense("path/to/license.lic");`를 호출하십시오. 라이선스 버전이 사용 중인 라이브러리 버전과 일치하는지 확인합니다.

**일반적인 해결책:**  
- 라이선스 파일이 손상되지 않았는지(파일 크기 비교) 확인.  
- 동일 환경에 트라이얼 라이선스와 상용 라이선스를 혼용하지 않음.

## 고급 팁 및 모범 사례

### 색상 관리
일관된 색상은 검토자의 가독성을 높입니다. 정적 헬퍼 클래스에 팔레트를 정의하고(예: 하이라이트는 Yellow, 중요 이슈는 Red) 접근하십시오. 접근성을 위해 고대비 색상을 사용하고, PDF에 색상 설명 페이지(레전드)를 추가하는 것도 좋습니다.

### 오류 처리 패턴
주석 호출을 모두 `try‑catch` 블록으로 감싸고, 특히 `GroupDocs.Annotation.Exceptions.AnnotationException`을 잡아 처리하십시오. 예외 메시지, 스택 트레이스 및 PDF 이름을 로깅해 디버깅을 용이하게 합니다.

### 테스트 전략
- **단위 테스트:** 알려진 크기의 작은 PDF에 주석을 추가하고 `GetAnnotations()`가 예상 좌표를 반환하는지 확인합니다.  
- **통합 테스트:** 1 페이지부터 200 페이지까지 다양한 PDF에 전체 워크플로를 실행하고, 50 MB 이하 파일은 5초 이내 처리되는지 검증합니다.  
- **부하 테스트:** k6 또는 Apache JMeter와 같은 도구로 50개의 동시 주석 요청을 시뮬레이션하고 CPU/메모리 사용량을 모니터링합니다.

## 자주 묻는 질문

**Q: 페이지 크기가 다른 PDF를 어떻게 처리하나요?**  
A: GroupDocs는 각 페이지의 치수를 자동으로 읽어옵니다. 주석 위치를 지정할 때는 항상 `annotator.GetPageInfo(pageNumber)`를 호출해 해당 페이지의 너비와 높이를 기준으로 좌표를 계산하십시오.

**Q: 비밀번호로 보호된 PDF에 주석을 달 수 있나요?**  
A: 가능합니다. 비밀번호 문자열을 받는 `LoadOptions` 생성자를 사용합니다. 예: `new LoadOptions { Password = "secret" }`를 `Annotator` 생성자에 전달합니다.

**Q: 단일 PDF에 추가할 수 있는 주석 수의 최대치는?**  
A: 명확한 제한은 없지만, 몇 천 개를 넘으면 성능이 저하됩니다. 매우 많은 주석이 필요한 경우 논리적 섹션으로 나누어 각각 별도로 처리하십시오.

**Q: 특정 주석을 프로그래밍 방식으로 삭제하려면?**  
A: `GetAnnotations()`로 주석의 `Id`를 조회한 뒤 `Delete(id)`를 호출하거나, 원하지 않는 `AnnotationType`을 제외하도록 `SaveOptions`를 구성합니다.

**Q: 색상 외에 주석 외관을 커스터마이즈할 수 있나요?**  
A: 물론입니다. 불투명도, 테두리 두께, 대시 스타일을 설정하고, 스탬프 주석의 경우 사용자 정의 SVG 아이콘을 삽입할 수 있습니다.

**Q: 스캔된(이미지 기반) PDF에 주석을 달면 어떻게 되나요?**  
A: 주석은 페이지 이미지 위에 오버레이 객체로 렌더링됩니다. 기본 래스터 데이터를 수정하지 않으므로 OCR 레이어가 있으면 PDF는 여전히 검색 가능합니다.

**Q: 메모리 부족 없이 매우 큰 PDF를 처리하려면?**  
A: `LoadOptions.PageNumbers`를 사용해 페이지별로 문서를 처리하고, 각 `Annotator` 인스턴스를 즉시 폐기하며, `MemoryStream`에 스트리밍 저장을 적용해 디스크 사용 급증을 방지합니다.

## ASP.NET 애플리케이션과의 통합

주석 기능을 웹 API로 제공할 때는 다음 패턴을 따르세요:

1. **컨트롤러가 클라이언트로부터 PDF 스트림을 수신**합니다.  
2. **파일 크기를 검증**하고(200 MB 초과는 별도 처리) 거부합니다.  
3. **`using` 블록 안에서 `Annotator`를 인스턴스화**해 리소스 해제를 보장합니다.  
4. **JSON 페이로드**(주석 유형, 좌표, 텍스트)를 기반으로 주석을 적용합니다.  
5. **임시 위치에 저장**한 뒤 적절한 `Content‑Disposition` 헤더와 함께 결과를 스트리밍 반환합니다.

```csharp
[HttpPost("annotate")]
public async Task<IActionResult> Annotate(IFormFile pdf, [FromBody] AnnotationRequest request)
{
    using var stream = pdf.OpenReadStream();
    var annotator = new Annotator(stream);
    // add annotations based on request
    var output = new MemoryStream();
    annotator.Save(output);
    output.Position = 0;
    return File(output, "application/pdf", "annotated.pdf");
}
```

## 추가 리소스
- [GroupDocs 구매 페이지](https://purchase.groupdocs.com/buy)  
- [GroupDocs 구매하기](https://purchase.groupdocs.com/buy)  
- [GroupDocs Annotation 문서](https://docs.groupdocs.com/annotation/net/)  
- [GroupDocs API 레퍼런스](https://reference.groupdocs.com/annotation/net/)  
- [최신 릴리스](https://releases.groupdocs.com/annotation/net/)  
- [무료 체험하기](https://releases.groupdocs.com/annotation/net/)  
- [임시 라이선스 요청](https://purchase.groupdocs.com/temporary-license/)  
- [GroupDocs 포럼](https://forum.groupdocs.com/c/annotation/)

## 결론 및 다음 단계

이제 GroupDocs.Annotation for .NET을 활용한 **문서 검토 시스템** 구축을 위한 **완전하고 프로덕션 준비된 로드맵**을 갖추었습니다. 라이브러리 설정, 영역·타원·텍스트 주석 추가, 저장 필터링, 대용량 PDF에서도 메모리 사용을 최소화하는 방법을 익혔습니다.

**오늘 바로 실행할 수 있는 다음 작업:**  

1. `ArrowAnnotation`·`StampAnnotation` 등 추가 주석 유형을 **실험**해 보세요.  
2. 기존 ASP.NET Core API 또는 데스크톱 WPF 애플리케이션에 **워크플로를 통합**합니다.  
3. 전체 API 레퍼런스를 **탐색**해 주석 버전 관리·사용자 정의 메타데이터 등 고급 기능을 발견합니다.  
4. GroupDocs 커뮤니티 포럼에 **가입**해 동료 지원을 받고 최신 릴리스 소식을 받아보세요.

---

**마지막 업데이트:** 2026-05-26  
**테스트 환경:** GroupDocs.Annotation 23.11 for .NET  
**작성자:** GroupDocs  

---

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main()
    {
        string inputPdfPath = "input.pdf";
        
        try
        {
            // Initialize the Annotator with the path of the document
            using (Annotator annotator = new Annotator(inputPdfPath))
            {
                Console.WriteLine("GroupDocs.Annotation initialized successfully!");
                // Your annotation code will go here
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Setup issue: {ex.Message}");
        }
    }
}
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // All annotation work happens inside this using block
    // This ensures proper resource cleanup
}
```

```csharp
AreaAnnotation areaAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // X, Y, Width, Height
    BackgroundColor = 65535,                 // Yellow highlight
    PageNumber = 0                           // First page
};
```

```csharp
EllipseAnnotation ellipseAnnotation = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Same coordinate system
    BackgroundColor = 123456,                // Different color
    PageNumber = 1                           // Second page
};
```

```csharp
annotator.Add(new List<AnnotationBase>() { areaAnnotation, ellipseAnnotation });
```

```csharp
SaveOptions saveOptions = new SaveOptions 
{
    AnnotationTypes = AnnotationType.Ellipse // Only save ellipse annotations
};
```

```csharp
annotator.Save(outputPath, saveOptions);
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // Your annotation code here
} // Automatic cleanup happens here
```

```csharp
var annotationsToAdd = new List<AnnotationBase>();
// Add multiple annotations to the list
annotator.Add(annotationsToAdd); // Single operation
```

```csharp
// Always verify file exists before processing
if (!File.Exists(inputPdfPath))
{
    throw new FileNotFoundException($"PDF file not found: {inputPdfPath}");
}

// Use absolute paths when possible
string absolutePath = Path.GetFullPath(inputPdfPath);
```

```csharp
// Test with known coordinates first
AreaAnnotation testAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(50, 50, 100, 100), // Start with simple values
    BackgroundColor = 65535,
    PageNumber = 0
};

// Verify page dimensions if needed
// Consider PDF scaling factors in your calculations
```

```csharp
// Define color constants for consistency
public static class AnnotationColors
{
    public const int ImportantHighlight = 65535;    // Yellow
    public const int AttentionMarker = 255;         // Red
    public const int ApprovedSection = 65280;       // Green
}
```

```csharp
try
{
    using (Annotator annotator = new Annotator(inputPdfPath))
    {
        // Your annotation operations
        annotator.Add(annotations);
        annotator.Save(outputPath, saveOptions);
    }
}
catch (GroupDocsException ex)
{
    // Handle GroupDocs-specific errors
    Logger.Error($"GroupDocs error: {ex.Message}");
}
catch (IOException ex)
{
    // Handle file I/O errors
    Logger.Error($"File operation error: {ex.Message}");
}
catch (Exception ex)
{
    // Handle unexpected errors
    Logger.Error($"Unexpected error: {ex.Message}");
}
```

```csharp
[HttpPost]
public async Task<IActionResult> AnnotatePdf(IFormFile pdfFile, AnnotationRequest request)
{
    // Validate input
    if (pdfFile == null || pdfFile.Length == 0)
        return BadRequest("No file provided");

    // Process asynchronously to avoid blocking the UI
    var result = await ProcessAnnotationsAsync(pdfFile, request);
    return Ok(result);
}
```

## 관련 튜토리얼

- [GroupDocs Annotation .NET 튜토리얼 - 문서 관리 완전 가이드](/annotation/net/annotation-management/)
- [Document Preview .NET 튜토리얼 - GroupDocs.Annotation 완전 가이드](/annotation/net/document-preview/)
- [GroupDocs Annotation Metered License 튜토리얼 - .NET 설정 완전 가이드](/annotation/net/licensing-and-configuration/implement-metered-license-groupdocs-annotation-net/)