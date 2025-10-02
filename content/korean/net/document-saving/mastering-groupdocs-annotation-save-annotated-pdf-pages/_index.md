---
"date": "2025-05-06"
"description": "GroupDocs.Annotation for .NET을 사용하여 PDF에서 주석이 달린 페이지만 효율적으로 저장하는 방법을 알아보세요. 이 자세한 가이드를 통해 문서 관리 및 협업을 향상시켜 보세요."
"title": "GroupDocs.Annotation for .NET을 사용하여 주석이 달린 페이지를 PDF로 저장하는 방법"
"url": "/ko/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
type: docs
"weight": 1
---

# GroupDocs.Annotation for .NET을 사용하여 주석이 달린 페이지를 PDF로 저장하는 방법

## 소개

PDF 문서에서 특정 주석이 달린 페이지를 저장하는 데 어려움을 겪고 계신가요? 이 종합 가이드는 GroupDocs.Annotation for .NET을 사용하여 효율적으로 저장하는 방법을 보여줍니다. 주석 기능을 활용하여 관련 콘텐츠에 집중함으로써 문서 관리를 간소화하고 협업을 향상시키세요.

이 튜토리얼에서는 다음 내용을 학습합니다.
- GroupDocs.Annotation을 사용하여 개발 환경 설정
- 다양한 유형의 주석 추가
- 주석이 달린 페이지만 효과적으로 저장

시작할 준비가 되셨나요? 모든 것을 준비했는지 확인해 볼까요?

### 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.
- **.NET 프레임워크** (버전 4.6 이상) 또는 **.NET 코어/5+**
- Visual Studio와 같은 코드 편집기
- C# 및 .NET 프로젝트 설정에 대한 기본 지식

## .NET용 GroupDocs.Annotation 설정

GroupDocs.Annotation을 사용하려면 NuGet을 통해 설치하세요.

**NuGet 패키지 관리자 콘솔**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET CLI**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### 라이센스 취득

GroupDocs는 소프트웨어를 완전히 체험해 볼 수 있도록 무료 체험판을 제공합니다. 장기간 사용하려면 라이선스를 구매하거나 임시 라이선스를 요청하세요.
- **무료 체험**: 초기 기간 동안 제한 없는 기능을 탐색해 보세요.
- **임시 면허**: GroupDocs.Annotation을 일시적으로 프로덕션에 사용합니다.
- **구입**상업용 라이선스로 장기적인 요구 사항을 확보하세요.

설치가 완료되면 다음과 같이 라이브러리를 초기화합니다.

```csharp
using GroupDocs.Annotation;

// 문서를 로드하고 주석을 달기 위한 기본 설정
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## 구현 가이드

### 주석 추가

#### 개요

주석은 문서 내 중요한 부분을 강조하는 데 도움이 됩니다. 주석을 추가하는 방법을 살펴보겠습니다. `AreaAnnotation` 그리고 `EllipseAnnotation`.

**1단계: 영역 주석 만들기**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// 영역 주석 정의
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // 위치 및 크기
    BackgroundColor = 65535,                // 하이라이트를 위한 ARGB 색상 값
    PageNumber = 1                          // 특정 페이지 번호
};
```

그만큼 `AreaAnnotation` 문서의 직사각형 영역을 강조 표시합니다. 위치 사용자 지정(`Box`) 및 배경색.

**2단계: 타원 주석 만들기**

```csharp
// 타원 주석을 정의합니다
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // 위치 및 크기
    BackgroundColor = 123456,                // 하이라이트를 위한 ARGB 색상 값
    PageNumber = 1                           // 특정 페이지 번호
};
```

그만큼 `EllipseAnnotation` 문서에 타원 모양을 그릴 수 있습니다. 다음을 사용하여 위치와 크기를 조정하세요. `Box` 재산.

**3단계: 주석 추가**

```csharp
// Annotator 인스턴스에 주석 추가
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

를 사용하여 `Add` 메서드에는 여러 유형의 주석이 포함됩니다. 이 단계에서는 다음 두 가지를 모두 추가합니다. `AreaAnnotation` 그리고 `EllipseAnnotation`.

### 주석이 달린 페이지만 저장

#### 개요

주석이 포함된 페이지만 저장하려면 저장 옵션을 적절히 구성하세요.

**4단계: 주석이 달린 페이지 저장**

```csharp
using GroupDocs.Annotation.Options;

// 주석이 달린 페이지만 포함하도록 저장 옵션을 설정합니다.
annotator.Save("path/to/output/document.pdf\