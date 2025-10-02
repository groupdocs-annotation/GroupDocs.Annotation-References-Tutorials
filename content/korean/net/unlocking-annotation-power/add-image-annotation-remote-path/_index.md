---
"description": "GroupDocs.Annotation for .NET을 사용하여 문서에 이미지 주석을 추가하는 방법을 알아보세요. 강력한 주석 기능으로 문서 관리를 더욱 효율적으로 개선하세요."
"linktitle": "문서에 이미지 주석 추가(원격 경로)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "문서에 이미지 주석 추가(원격 경로)"
"url": "/ko/net/unlocking-annotation-power/add-image-annotation-remote-path/"
type: docs
"weight": 15
---

# 문서에 이미지 주석 추가(원격 경로)

## 소개
이 튜토리얼에서는 GroupDocs.Annotation for .NET을 사용하여 문서에 이미지 주석을 추가하는 과정을 살펴보겠습니다. 이 라이브러리는 다양한 유형의 문서에 프로그래밍 방식으로 주석을 추가할 수 있는 강력한 도구를 제공합니다.
## 필수 조건
시작하기에 앞서 다음 사항이 있는지 확인하세요.
1. .NET용 GroupDocs.Annotation: 라이브러리를 다운로드하고 설치하세요. [여기](https://releases.groupdocs.com/annotation/net/).
2. 개발 환경: .NET 개발을 위해 작동하는 개발 환경이 설정되어 있는지 확인하세요.
3. 문서: 주석을 달 문서를 준비합니다. 이 튜토리얼에서는 PDF 문서가 있다고 가정합니다. `input.pdf`.
4. 주석 이미지: 주석에 사용할 이미지를 선택하세요. 이미지 URL이나 로컬 경로를 준비하세요.

## 네임스페이스 가져오기
코딩을 시작하기 전에 필요한 네임스페이스를 가져와 보겠습니다.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## 1단계: 출력 경로 설정
먼저, 주석이 달린 문서가 저장될 출력 경로를 정의합니다.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2단계: Annotator 초기화
인스턴스를 생성합니다 `Annotator` 클래스를 지정하고 입력 문서를 지정합니다.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 주석 코드는 여기에 들어갑니다
}
```
## 3단계: 이미지 주석 추가
이제 문서에 이미지 주석을 추가해 보겠습니다. 위치, 불투명도, 페이지 번호, 이미지 경로 등 이미지 주석의 속성을 지정합니다.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // 주석의 위치를 지정하세요
    CreatedOn = DateTime.Now, // 생성 날짜를 설정하세요
    Opacity = 0.7, // 불투명도 설정(0~1)
    PageNumber = 0, // 페이지 번호를 지정하세요
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // 이미지 URL을 제공하세요
};
annotator.Add(image); // 이미지 주석 추가
```
## 4단계: 문서 저장
주석이 달린 문서를 지정된 출력 경로에 저장합니다.
```csharp
annotator.Save(outputPath);
```
## 5단계: 출력 경로 표시
사용자에게 문서 저장 작업이 성공적으로 완료되었음을 알리고 출력 경로를 표시합니다.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 결론
이 튜토리얼에서는 GroupDocs.Annotation for .NET을 사용하여 문서에 이미지 주석을 추가하는 방법을 알아보았습니다. 다음 단계를 따라 하면 강력한 주석 기능으로 문서 관리 애플리케이션을 더욱 강화할 수 있습니다.
## 자주 묻는 질문
### GroupDocs.Annotation을 PDF 외의 다른 문서 형식에도 사용할 수 있나요?
네, GroupDocs.Annotation은 Word, Excel, PowerPoint 등 다양한 문서 형식을 지원합니다.
### GroupDocs.Annotation은 .NET Core와 호환됩니까?
네, GroupDocs.Annotation은 .NET Framework와 .NET Core 모두와 호환됩니다.
### 주석의 모양을 사용자 지정할 수 있나요?
네, 색상, 불투명도, 크기 등 주석의 모양을 사용자 지정할 수 있습니다.
### GroupDocs.Annotation은 협업 주석 기능을 지원합니까?
네, GroupDocs.Annotation은 문서에 대한 실시간 협업을 위한 협업 주석 기능을 제공합니다.
### 테스트해 볼 수 있는 체험판이 있나요?
네, GroupDocs.Annotation의 무료 평가판을 받을 수 있습니다. [여기](https://releases.groupdocs.com/).