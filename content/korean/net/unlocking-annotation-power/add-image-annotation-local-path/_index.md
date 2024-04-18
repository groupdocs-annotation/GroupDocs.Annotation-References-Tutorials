---
title: 문서에 이미지 주석 추가(로컬 경로)
linktitle: 문서에 이미지 주석 추가(로컬 경로)
second_title: GroupDocs.Annotation .NET API
description: .NET용 GroupDocs.Annotation을 사용하여 문서에 이미지 주석을 추가하는 방법을 알아보세요. 문서 처리 기능을 쉽게 향상하세요.
type: docs
weight: 14
url: /ko/net/unlocking-annotation-power/add-image-annotation-local-path/
---
## 소개
.NET용 GroupDocs.Annotation은 개발자가 프로그래밍 방식으로 문서에 다양한 유형의 주석을 추가할 수 있는 강력한 라이브러리입니다. 이 튜토리얼에서는 로컬 경로를 사용하여 문서에 이미지 주석을 추가하는 방법을 알아봅니다.
## 전제 조건
시작하기 전에 다음 필수 구성 요소가 있는지 확인하세요.
1. C# 프로그래밍 언어에 대한 기본 지식.
2. 시스템에 Visual Studio가 설치되어 있습니다.
3. 프로젝트에 설치되거나 참조되는 .NET 라이브러리용 GroupDocs.Annotation입니다.
4. 입력 문서(예: PDF) 및 주석용 이미지 파일.
## 네임스페이스 가져오기
먼저 필요한 네임스페이스를 C# 파일로 가져와야 합니다. 이러한 네임스페이스는 GroupDocs.Annotation 작업에 필요한 클래스 및 메서드에 대한 액세스를 제공합니다.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## 1단계: 출력 경로 정의
주석이 달린 문서가 저장될 출력 경로를 정의합니다.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2단계: 주석자 초기화
입력 문서에 대한 경로를 제공하여 어노테이터를 초기화하십시오.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 주석 코드는 여기에 표시됩니다.
}
```
## 3단계: 이미지 주석 생성
 인스턴스를 생성합니다.`ImageAnnotation`클래스를 선택하고 위치, 불투명도, 페이지 번호, 이미지 경로 등의 속성을 지정합니다.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## 4단계: 주석 추가
 생성된 이미지 주석을 다음을 사용하여 문서에 추가합니다.`Add` 주석자의 방법.
```csharp
annotator.Add(image);
```
## 5단계: 문서 저장
주석이 달린 문서를 출력 경로에 저장합니다.
```csharp
annotator.Save(outputPath);
```
## 6단계: 출력 경로 표시
문서가 성공적으로 저장되었음을 알리는 메시지와 출력 파일의 위치를 표시합니다.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론
이 튜토리얼에서는 .NET용 GroupDocs.Annotation을 사용하여 문서에 이미지 주석을 추가하는 방법을 배웠습니다. 이러한 간단한 단계를 따르면 강력한 주석 기능으로 문서 처리 기능을 향상시킬 수 있습니다.
## FAQ
### PDF 이외의 문서에 주석을 달 수 있나요?
예, GroupDocs.Annotation은 Word, Excel, PowerPoint 등을 포함한 다양한 문서 형식을 지원합니다.
### GroupDocs.Annotation은 .NET Core와 호환되나요?
예, GroupDocs.Annotation은 .NET Framework 및 .NET Core 모두와 호환됩니다.
### 주석의 모양을 맞춤설정할 수 있나요?
물론, 요구 사항에 따라 주석의 모양, 크기, 색상 및 기타 속성을 사용자 정의할 수 있습니다.
### GroupDocs.Annotation은 공동 주석을 지원합니까?
예, GroupDocs.Annotation은 여러 사용자가 동시에 문서에 주석을 달 수 있는 공동 주석 기능을 제공합니다.
### 추가 도움이나 지원은 어디서 찾을 수 있나요?
커뮤니티의 도움과 지원을 받으려면 GroupDocs.Annotation 포럼을 방문하세요.