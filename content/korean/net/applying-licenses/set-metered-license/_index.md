---
"description": ".NET 애플리케이션에서 GroupDocs.Annotation .NET의 리소스 사용 및 문서 주석 기능에 대한 미터링 라이선스를 설정하는 방법을 알아보세요."
"linktitle": "미터링 라이센스 설정"
"second_title": "GroupDocs.Annotation .NET API"
"title": "미터링 라이센스 설정"
"url": "/ko/net/applying-licenses/set-metered-license/"
"weight": 12
---

# 미터링 라이센스 설정

## 소개
GroupDocs.Annotation for .NET은 개발자가 .NET 애플리케이션에 문서 주석 기능을 손쉽게 추가할 수 있도록 지원하는 강력한 라이브러리입니다. 문서 관리 시스템, 협업 플랫폼 또는 문서 검토 및 마크업이 필요한 애플리케이션을 구축하는 경우, GroupDocs.Annotation for .NET은 프로세스를 간소화하는 포괄적인 도구 세트를 제공합니다.
이 튜토리얼에서는 GroupDocs.Annotation .NET용 계량형 라이선스를 설정하는 과정을 자세히 살펴보겠습니다. 계량형 라이선스를 사용하면 사용한 리소스에 대해서만 비용을 지불하면 되므로 규모에 관계없이 모든 프로젝트에 비용 효율적인 솔루션입니다. 아래 설명된 단계를 따르면 리소스 사용을 최적화하고 예산을 효율적으로 관리하면서 GroupDocs.Annotation을 .NET 애플리케이션에 원활하게 통합할 수 있습니다.
## 필수 조건
튜토리얼을 시작하기 전에 다음 필수 조건을 충족하는지 확인하세요.
1. .NET 라이브러리용 GroupDocs.Annotation: 라이브러리를 다음에서 다운로드하세요. [웹사이트](https://releases.groupdocs.com/annotation/net/).
2. GroupDocs 계정 접근: 계량형 라이선스 설정에 필요한 공개 키와 개인 키를 얻으려면 GroupDocs 계정이 필요합니다. 아직 계정이 없으신 경우 무료 체험판에 가입하실 수 있습니다. [여기](https://releases.groupdocs.com/).
3. C# 및 .NET Framework에 대한 기본적인 이해: C# 프로그래밍 언어와 .NET Framework에 대한 지식이 있으면 이 튜토리얼에 설명된 단계를 구현하는 데 도움이 됩니다.

## 네임스페이스 가져오기
먼저, 필요한 네임스페이스를 C# 프로젝트로 가져오세요. 이러한 네임스페이스는 GroupDocs.Annotation 기능과 상호 작용하는 데 필수적입니다.
```csharp
using System;
```
## 1단계: 공개 키와 개인 키 얻기
미터링 라이선스를 설정하기 전에 GroupDocs 계정 대시보드에서 공개 키와 개인 키를 얻어야 합니다.
1. GroupDocs 계정에 로그인하세요.
2. 라이선스 관리 섹션으로 이동합니다.
3. GroupDocs에서 제공한 공개 키와 개인 키를 복사하세요.
## 2단계: 미터링된 라이센스 설정
공개 키와 개인 키를 얻으면 .NET 애플리케이션에서 미터링 라이선스를 설정할 수 있습니다.
```csharp
string publicKey = "*****"; // *****를 공개 키로 바꾸세요
string privateKey = "*****"; // *****를 개인 키로 바꾸세요
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## 결론
결론적으로, GroupDocs.Annotation .NET용 계량형 라이선스를 설정하는 것은 문서 주석 프로젝트의 효율적인 리소스 활용과 비용 효율성을 보장하는 간단한 과정입니다. 이 튜토리얼에 설명된 단계를 따르면 GroupDocs.Annotation을 .NET 애플리케이션에 원활하게 통합하고 문서 협업 및 검토 기능을 향상시킬 수 있습니다.
## 자주 묻는 질문
### 상업용 프로젝트에서 GroupDocs.Annotation for .NET을 사용할 수 있나요?
네, GroupDocs.Annotation for .NET은 상업적 및 비상업적 프로젝트 모두에서 사용할 수 있습니다. 단, 프로젝트 요구 사항에 따라 적절한 라이선스를 구매해야 합니다.
### GroupDocs.Annotation for .NET의 평가판이 있나요?
예, .NET용 GroupDocs.Annotation의 무료 평가판을 이용하려면 여기를 방문하세요. [이 링크](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Annotation에 대한 기술 지원을 어떻게 받을 수 있나요?
GroupDocs 포럼을 방문하여 기술 지원을 요청할 수 있습니다. [여기](https://forum.groupdocs.com/c/annotation/10).
### 임시 라이센스 옵션은 있나요?
네, GroupDocs에서 단기 사용 또는 평가 목적으로 임시 라이선스를 받으실 수 있습니다. 여기를 방문하세요. [이 링크](https://purchase.groupdocs.com/temporary-license/) 자세한 내용은.
### 프로젝트 요구 사항에 맞게 주석 기능을 사용자 정의할 수 있나요?
네, GroupDocs.Annotation for .NET은 광범위한 사용자 정의 옵션을 제공하므로 특정 프로젝트 요구 사항에 맞게 주석 기능을 조정할 수 있습니다.