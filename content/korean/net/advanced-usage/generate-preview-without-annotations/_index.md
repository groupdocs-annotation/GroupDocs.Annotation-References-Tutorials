---
"description": "GroupDocs.Annotation for .NET을 사용하여 .NET 애플리케이션 내에서 문서 협업 및 주석 기능을 강화하세요. 이 강력한 라이브러리를 사용하여 문서에 주석을 달고, 마크업하고, 검토하세요."
"linktitle": "주석 없이 미리보기 생성"
"second_title": "GroupDocs.Annotation .NET API"
"title": "주석 없이 미리보기 생성"
"url": "/ko/net/advanced-usage/generate-preview-without-annotations/"
"weight": 13
---

# 주석 없이 미리보기 생성

## 소개
오늘날의 디지털 시대에 효율적인 문서 협업은 생산성과 성공의 핵심입니다. 전 세계에 흩어져 있는 팀원들과 함께 프로젝트를 진행하든, 중요한 계약에 대해 고객과 협업하든, 문서에 주석을 달고 원활하게 검토할 수 있는 기능은 매우 중요합니다. GroupDocs.Annotation for .NET을 사용하면 .NET 애플리케이션 내에서 바로 주석을 달고, 마크업하고, 검토할 수 있어 문서 협업을 한 단계 더 발전시킬 수 있습니다.
## 필수 조건
GroupDocs.Annotation for .NET을 사용하여 문서 주석을 작성하는 방법을 알아보기 전에 몇 가지 필수 사항을 준비해야 합니다.
### 1. .NET용 GroupDocs.Annotation 설치
먼저, GroupDocs.Annotation for .NET을 다운로드하여 설치해야 합니다. 다운로드 링크는 다음과 같습니다. [여기](https://releases.groupdocs.com/annotation/net/)제공된 설치 지침에 따라 .NET 환경에서 라이브러리를 설정하세요.
### 2. 라이센스 취득(선택 사항)
GroupDocs.Annotation for .NET은 무료 평가판을 제공하지만, 모든 기능을 사용하려면 라이선스를 구매하는 것이 좋습니다. 라이선스를 구매하려면 [여기](https://purchase.groupdocs.com/buy) 또는 임시 면허를 요청하세요 [여기](https://purchase.groupdocs.com/temporary-license/) 테스트 목적으로.
### 3. C# 및 .NET 개발에 대한 지식
GroupDocs.Annotation for .NET을 최대한 활용하려면 C# 및 .NET 개발에 대한 기본적인 이해가 필요합니다. 이를 통해 라이브러리를 기존 애플리케이션 및 워크플로에 원활하게 통합할 수 있습니다.
### 4. PDF 뷰어 설치
GroupDocs.Annotation for .NET은 PDF 문서와 호환되므로, 주석이 달린 문서를 미리 보려면 시스템에 PDF 뷰어가 설치되어 있어야 합니다. Adobe Acrobat Reader나 다른 PDF 뷰어를 사용하면 됩니다.

## 네임스페이스 가져오기
문서에 주석을 추가하려면 먼저 필요한 네임스페이스를 .NET 프로젝트로 가져와야 합니다. 이렇게 하면 .NET용 GroupDocs.Annotation에서 제공하는 클래스와 메서드에 액세스할 수 있습니다.

```csharp
using System.IO;
using GroupDocs.Annotation.Options;
```

이제 모든 설정이 완료되었으니, 주석이 없는 문서의 미리보기를 생성해 보겠습니다. 다음 단계에 따라 생성하세요.
## 1단계: Annotator 초기화
먼저 인스턴스를 생성합니다. `Annotator` 클래스에 주석을 달고자 하는 문서의 경로를 전달합니다.
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
```
## 2단계: 미리 보기 옵션 구성
다음으로, 필요에 따라 미리보기 옵션을 구성하세요. 미리보기에 포함할 페이지 번호, 미리보기 형식(예: PNG), 그리고 주석 렌더링 여부를 지정할 수 있습니다.
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};
    previewOptions.RenderAnnotations = false;
```
## 3단계: 미리보기 생성
마지막으로 다음을 사용하여 미리보기를 생성합니다. `GeneratePreview` 방법 `Document` 클래스, 구성된 미리보기 옵션을 전달합니다.
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
이러한 간단한 단계를 따르면 .NET용 GroupDocs.Annotation을 사용하여 주석이 없는 문서의 미리보기를 생성할 수 있습니다.

## 결론
결론적으로, GroupDocs.Annotation for .NET은 .NET 애플리케이션 내에서 문서 협업 및 주석 처리를 위한 강력한 솔루션을 제공합니다. 이 튜토리얼에 설명된 단계를 따르면 문서 주석 기능을 프로젝트에 원활하게 통합하여 협업과 생산성을 향상시킬 수 있습니다.
## 자주 묻는 질문
### 질문: PDF 외의 다른 문서 형식에도 GroupDocs.Annotation for .NET을 사용할 수 있나요?
네, .NET용 GroupDocs.Annotation은 DOCX, XLSX, PPTX 등 다양한 문서 형식을 지원합니다.
### 질문: .NET용 GroupDocs.Annotation은 .NET Core와 호환됩니까?
네, .NET용 GroupDocs.Annotation은 .NET Framework와 .NET Core 환경 모두와 호환됩니다.
### 질문: .NET용 GroupDocs.Annotation은 사용자 정의 가능한 주석 도구를 제공합니까?
네, .NET용 GroupDocs.Annotation은 사용자의 특정 요구 사항에 맞게 사용자 정의할 수 있는 다양한 주석 도구를 제공합니다.
### 질문: GroupDocs.Annotation for .NET을 내 웹 애플리케이션에 통합할 수 있나요?
네, GroupDocs.Annotation for .NET은 데스크톱과 웹 애플리케이션에 모두 통합되어 원활한 문서 협업 기능을 제공합니다.
### 질문: .NET용 GroupDocs.Annotation에 대한 지원과 도움을 받을 수 있는 커뮤니티 포럼이 있나요?
예, GroupDocs.Annotation 포럼에서 지원과 도움을 받을 수 있습니다. [여기](https://forum.groupdocs.com/c/annotation/10).