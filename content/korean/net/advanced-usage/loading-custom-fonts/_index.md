---
"description": "GroupDocs.Annotation for .NET에서 사용자 지정 글꼴을 원활하게 로드하여 문서 주석 기능을 강화하는 방법을 알아보세요. 간편한 통합을 위한 단계별 안내를 따르세요."
"linktitle": "사용자 정의 글꼴 로딩"
"second_title": "GroupDocs.Annotation .NET API"
"title": "사용자 정의 글꼴 로딩"
"url": "/ko/net/advanced-usage/loading-custom-fonts/"
type: docs
"weight": 20
---

# 사용자 정의 글꼴 로딩

## 소개
GroupDocs.Annotation for .NET은 개발자가 .NET 애플리케이션에 주석 기능을 손쉽게 추가할 수 있도록 지원하는 강력한 라이브러리입니다. 주요 기능 중 하나는 사용자 지정 글꼴을 로드하는 기능으로, 이를 통해 문서 주석의 사용자 지정 및 유연성을 향상시킬 수 있습니다.
## 필수 조건
튜토리얼을 진행하기 전에 다음 필수 조건이 충족되었는지 확인하세요.
1. .NET 라이브러리용 GroupDocs.Annotation: 라이브러리를 다운로드하여 설치하세요. [여기](https://releases.groupdocs.com/annotation/net/).
2. .NET 개발 환경: .NET 개발을 위한 작업 환경이 설정되어 있는지 확인하세요.
3. 사용자 정의 글꼴 액세스: 애플리케이션에 로드할 사용자 정의 글꼴을 준비합니다.

## 네임스페이스 가져오기
.NET 프로젝트에서 GroupDocs.Annotation을 활용하는 데 필요한 네임스페이스를 가져옵니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## 1단계: Annotator 객체 인스턴스화
인스턴스를 생성합니다 `Annotator` 사용자 정의 글꼴 디렉토리와 함께 입력 PDF 문서 경로를 제공하여 클래스를 만듭니다.
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    // 추가 작업에 대한 코드는 여기에 입력됩니다.
}
```
## 2단계: 미리 보기 옵션 구성
문서 미리보기 생성 방식을 지정하려면 미리보기 옵션을 정의하세요. 미리보기 형식, 페이지 번호 등의 옵션을 설정할 수 있습니다.
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_with_font_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
```
## 3단계: 문서 미리보기 생성
활용하다 `GeneratePreview` 방법 `Document` 사용자 정의 글꼴로 미리보기를 생성하는 속성:
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## 4단계: 출력 경로 표시
마지막으로, 출력 디렉토리 경로와 함께 문서 미리 보기가 성공적으로 생성되었음을 나타내는 메시지를 표시합니다.
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## 결론
결론적으로, GroupDocs.Annotation for .NET에서 사용자 지정 글꼴을 로드하면 개발자는 필요에 따라 문서 주석을 사용자 지정할 수 있는 유연성을 확보할 수 있습니다. 이 튜토리얼에 설명된 단계를 따르면 사용자 지정 글꼴을 .NET 애플리케이션에 원활하게 통합하고 사용자에게 향상된 주석 경험을 제공할 수 있습니다.
## 자주 묻는 질문
### 여러 개의 사용자 정의 글꼴을 동시에 로드할 수 있나요?
예, 인스턴스화할 때 여러 개의 글꼴 디렉토리를 지정할 수 있습니다. `Annotator` 물체.
### 지원되는 글꼴 유형에 제한이 있나요?
.NET용 GroupDocs.Annotation은 TrueType(.ttf) 및 OpenType(.otf) 글꼴을 포함한 다양한 글꼴 유형을 지원합니다.
### 런타임 중에 로드된 글꼴을 동적으로 변경할 수 있나요?
네, 필요에 따라 글꼴 디렉토리를 동적으로 수정하고 문서 주석을 다시 로드할 수 있습니다.
### GroupDocs.Annotation은 출력 문서에 글꼴을 포함하는 것을 지원합니까?
네, 다양한 플랫폼에서 일관된 렌더링을 보장하기 위해 출력 문서에 사용자 정의 글꼴을 포함할 수 있습니다.
### 애플리케이션 내에서 글꼴 라이선스를 처리할 방법이 있나요?
GroupDocs.Annotation은 평가 목적의 임시 라이선스를 포함하여 글꼴 라이선스를 관리하는 옵션을 제공합니다.