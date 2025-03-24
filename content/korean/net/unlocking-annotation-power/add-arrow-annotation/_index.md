---
title: 문서에 화살표 주석 추가
linktitle: 문서에 화살표 주석 추가
second_title: GroupDocs.Annotation .NET API
description: .NET용 GroupDocs.Annotation을 사용하여 문서에 화살표 주석을 추가하는 방법을 알아보세요. 문서의 명확성과 상호작용성을 손쉽게 향상할 수 있습니다.
weight: 11
url: /ko/net/unlocking-annotation-power/add-arrow-annotation/
---

# 문서에 화살표 주석 추가

## 소개
이 자습서에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 화살표 주석을 추가하는 과정을 안내합니다. 화살표 주석은 방향을 나타내거나 문서 내의 특정 요소를 가리키는 데 유용합니다.
## 전제 조건
시작하기 전에 다음 사항이 있는지 확인하세요.
1.  .NET용 GroupDocs.Annotation: .NET용 GroupDocs.Annotation 라이브러리를 설치합니다. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/annotation/net/).
2. 개발 환경: Visual Studio 또는 기타 선호하는 IDE를 포함하여 .NET 개발을 위한 개발 환경이 설정되어 있는지 확인하세요.

## 네임스페이스 가져오기
먼저, 주석에 필요한 클래스와 메서드에 액세스하려면 필요한 네임스페이스를 가져와야 합니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1단계: 주석자 초기화
입력 문서 파일 경로를 제공하여 어노테이터를 초기화하십시오.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 2단계: 화살표 주석 생성
ArrowAnnotation 클래스의 인스턴스를 생성하고 위치, 메시지, 불투명도, 펜 색상, 스타일, 너비 등과 같은 속성을 정의합니다.
```csharp
	ArrowAnnotation arrow = new ArrowAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		CreatedOn = DateTime.Now,
		Message = "This is arrow annotation",
		Opacity = 0.7,
		PageNumber = 0,
		PenColor = 65535,
		PenStyle = PenStyle.Dot,
		PenWidth = 3,
		Replies = new List<Reply>
		{
			new Reply
			{
				Comment = "First comment",
				RepliedOn = DateTime.Now
			},
			new Reply
			{
				Comment = "Second comment",
				RepliedOn = DateTime.Now
			}
		}
	};
```
## 3단계: 주석 추가
 다음을 사용하여 문서에 화살표 주석을 추가합니다.`Add` 주석자의 방법.
```csharp
	annotator.Add(arrow);
```
## 4단계: 문서 저장
주석이 달린 문서를 지정된 출력 경로에 저장합니다.
```csharp
	annotator.Save(outputPath);
}
```
## 5단계: 표시 확인
문서가 성공적으로 저장되었음을 나타내는 확인 메시지를 표시합니다.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
이제 .NET용 GroupDocs.Annotation을 사용하여 문서에 화살표 주석을 성공적으로 추가했습니다.

## 결론
이 튜토리얼에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 화살표 주석을 추가하는 과정을 다루었습니다. 다음 단계를 따르면 명확한 방향 표시기를 사용하여 문서를 더욱 유익하고 매력적으로 만들 수 있습니다.
## FAQ
### 화살표 주석의 모양을 사용자 정의할 수 있나요?
예, 색상, 스타일, 너비, 불투명도 등 다양한 속성을 사용자의 기본 설정 및 문서 요구 사항에 맞게 사용자 정의할 수 있습니다.
### GroupDocs.Annotation은 모든 문서 형식과 호환됩니까?
GroupDocs.Annotation은 PDF, DOCX, PPTX, XLSX 등을 포함한 광범위한 문서 형식을 지원합니다.
### GroupDocs.Annotation을 사용하여 프로그래밍 방식으로 주석을 추가할 수 있습니까?
예, GroupDocs.Annotation은 프로그래밍 방식으로 문서에서 주석을 추가, 편집 및 제거할 수 있는 API를 제공합니다.
### GroupDocs.Annotation은 무료 평가판을 제공합니까?
 예, 다음에서 GroupDocs.Annotation을 무료로 다운로드하여 사용해 볼 수 있습니다.[여기](https://releases.groupdocs.com/).
### GroupDocs.Annotation에 대한 기술 지원은 어디서 받을 수 있나요?
기술 지원 및 지원을 받으려면 GroupDocs.Annotation 포럼을 방문하세요.[여기](https://forum.groupdocs.com/c/annotation/10).