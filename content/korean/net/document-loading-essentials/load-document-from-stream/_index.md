---
title: 스트림에서 문서 로드
linktitle: 스트림에서 문서 로드
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation을 사용하여 .NET 문서에 손쉽게 주석을 추가하는 방법을 알아보세요. 협업과 생산성을 향상하세요.
type: docs
weight: 14
url: /ko/net/document-loading-essentials/load-document-from-stream/
---
## 소개
.NET용 GroupDocs.Annotation은 개발자가 문서 주석 기능을 .NET 응용 프로그램에 쉽게 통합할 수 있도록 지원하는 강력한 라이브러리입니다. 문서 관리 시스템, 공동 작업 플랫폼 또는 e-러닝 응용 프로그램을 구축하는 경우 GroupDocs.Annotation은 PDF, Word 문서, Excel 시트 등에 주석을 달 수 있는 다양한 도구 세트를 제공합니다.
## 전제 조건
주석 프로세스를 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1. .NET용 GroupDocs.Annotation 설치: 다음에서 .NET용 GroupDocs.Annotation을 다운로드하여 설치합니다.[여기](https://releases.groupdocs.com/annotation/net/).
2. C# 프로그래밍에 대한 기본 이해: C# 프로그래밍 언어 및 .NET 프레임워크에 대한 지식이 필수적입니다.
3. 개발 환경 설정: .NET 프레임워크 지원을 통해 선호하는 개발 환경을 설정합니다.

## 네임스페이스 가져오기
.NET용 GroupDocs.Annotation을 사용하여 문서에 주석을 추가하려면 필요한 네임스페이스를 C# 프로젝트로 가져옵니다.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

이제 주석 프로세스를 여러 단계로 나누어 보겠습니다.
## 1단계: 스트림에서 문서 로드
먼저 스트림에서 문서를 로드해야 합니다. 이를 달성하는 방법은 다음과 같습니다.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator(File.OpenRead("input.pdf")))
{
```
## 2단계: 주석 추가
다음으로 문서에 주석을 추가할 수 있습니다. 예를 들어 영역 주석을 작성해 보겠습니다.
```csharp
	AreaAnnotation area = new AreaAnnotation()
	{
		Box = new Rectangle(100, 100, 100, 100),
		BackgroundColor = 65535,
	};
	annotator.Add(area);
```
## 3단계: 주석이 포함된 문서 저장
주석을 추가한 후 주석이 달린 문서를 저장합니다.
```csharp
	annotator.Save(File.Create(outputPath));
}
```
## 4단계: 확인 메시지 표시
마지막으로 주석이 달린 문서가 성공적으로 저장되었음을 확인하는 메시지를 표시합니다.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론
결론적으로, .NET용 GroupDocs.Annotation은 .NET 응용 프로그램 내의 문서 주석을 위한 포괄적인 솔루션을 제공합니다. 이 튜토리얼에 설명된 단계를 따르면 문서 주석 기능을 프로젝트에 원활하게 통합하여 협업과 생산성을 향상시킬 수 있습니다.
## FAQ
### .NET용 GroupDocs.Annotation은 모든 문서 형식과 호환됩니까?
GroupDocs.Annotation은 PDF, Word, Excel, PowerPoint 등을 포함한 광범위한 문서 형식을 지원합니다.
### 특정 요구사항에 따라 주석을 맞춤설정할 수 있나요?
예, GroupDocs.Annotation은 색상, 모양 및 속성을 포함하여 주석에 대한 광범위한 사용자 정의 옵션을 제공합니다.
### GroupDocs.Annotation은 공동 주석 기능을 지원합니까?
예, GroupDocs.Annotation은 여러 사용자가 동시에 문서에 주석을 달 수 있도록 하여 협업 주석을 용이하게 합니다.
### GroupDocs.Annotation 사용자에게 기술 지원이 제공됩니까?
 예, GroupDocs는 포럼을 통해 전담 기술 지원을 제공합니다. 방문하다[여기](https://forum.groupdocs.com/c/annotation/10) 지원을 위해.
### 구매하기 전에 GroupDocs.Annotation을 사용해 볼 수 있나요?
 예, 무료 평가판을 통해 GroupDocs.Annotation을 탐색할 수 있습니다.[여기](https://releases.groupdocs.com/).