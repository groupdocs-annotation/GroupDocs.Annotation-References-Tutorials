---
"description": "GroupDocs.Annotation for .NET을 사용하여 문서에 이미지 주석을 추가하는 방법을 알아보세요. 문서 처리 기능을 손쉽게 향상시켜 보세요."
"linktitle": "문서에 이미지 주석 추가(로컬 경로)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "문서에 이미지 주석 추가(로컬 경로)"
"url": "/ko/net/unlocking-annotation-power/add-image-annotation-local-path/"
type: docs
"weight": 14
---

# 문서에 이미지 주석 추가(로컬 경로)

## 소개
GroupDocs.Annotation for .NET은 개발자가 다양한 유형의 주석을 프로그래밍 방식으로 문서에 추가할 수 있는 강력한 라이브러리입니다. 이 튜토리얼에서는 로컬 경로를 사용하여 문서에 이미지 주석을 추가하는 방법을 알아봅니다.
## 필수 조건
시작하기에 앞서 다음과 같은 전제 조건이 충족되었는지 확인하세요.
1. C# 프로그래밍 언어에 대한 기본 지식.
2. 시스템에 Visual Studio가 설치되어 있어야 합니다.
3. 프로젝트에 .NET 라이브러리에 대한 GroupDocs.Annotation이 설치되었거나 tutorialsd가 설치되어 있습니다.
4. 입력 문서(예: PDF)와 주석을 위한 이미지 파일.
## 네임스페이스 가져오기
먼저, 필요한 네임스페이스를 C# 파일로 가져와야 합니다. 이 네임스페이스는 GroupDocs.Annotation 작업에 필요한 클래스와 메서드에 대한 액세스를 제공합니다.
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
## 2단계: Annotator 초기화
입력 문서의 경로를 제공하여 주석자를 초기화합니다.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 주석 코드는 여기에 있습니다
}
```
## 3단계: 이미지 주석 만들기
인스턴스를 생성합니다 `ImageAnnotation` 클래스를 지정하고 위치, 불투명도, 페이지 번호, 이미지 경로와 같은 속성을 지정합니다.
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
생성된 이미지 주석을 문서에 추가하려면 다음을 사용합니다. `Add` 주석자의 방법.
```csharp
annotator.Add(image);
```
## 5단계: 문서 저장
주석이 달린 문서를 출력 경로에 저장합니다.
```csharp
annotator.Save(outputPath);
```
## 6단계: 출력 경로 표시
문서가 성공적으로 저장되었다는 메시지와 출력 파일의 위치를 표시합니다.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론
이 튜토리얼에서는 GroupDocs.Annotation for .NET을 사용하여 문서에 이미지 주석을 추가하는 방법을 알아보았습니다. 간단한 단계를 따라 하면 강력한 주석 기능을 통해 문서 처리 능력을 향상시킬 수 있습니다.
## 자주 묻는 질문
### PDF가 아닌 다른 문서에도 주석을 달 수 있나요?
네, GroupDocs.Annotation은 Word, Excel, PowerPoint 등 다양한 문서 형식을 지원합니다.
### GroupDocs.Annotation은 .NET Core와 호환됩니까?
네, GroupDocs.Annotation은 .NET Framework와 .NET Core 모두와 호환됩니다.
### 주석의 모양을 사용자 지정할 수 있나요?
물론입니다. 귀하의 요구 사항에 맞게 주석의 모양, 크기, 색상 및 기타 속성을 사용자 정의할 수 있습니다.
### GroupDocs.Annotation은 협업 주석 기능을 지원합니까?
네, GroupDocs.Annotation은 여러 사용자가 동시에 문서에 주석을 달 수 있는 협업 주석 기능을 제공합니다.
### 추가 도움이나 지원은 어디에서 받을 수 있나요?
커뮤니티로부터 도움과 지원을 받으려면 GroupDocs.Annotation 포럼을 방문하세요.