---
title: Azure에서 문서 로드
linktitle: Azure에서 문서 로드
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation을 사용하여 .NET에서 문서에 주석을 추가하는 방법을 알아보세요. Azure Blob Storage와의 원활한 통합을 위한 단계별 자습서입니다.
type: docs
weight: 11
url: /ko/net/document-loading-essentials/load-document-from-azure/
---
## 소개
문서 관리 및 공동 작업 영역에서 .NET용 GroupDocs.Annotation은 .NET 응용 프로그램 내에서 원활한 주석 및 마크업 기능을 지원하는 강력한 솔루션으로 등장합니다. 이 튜토리얼에서는 문서에 주석을 달기 위해 .NET용 GroupDocs.Annotation을 활용하는 복잡한 과정을 자세히 살펴보고 전제 조건부터 고급 사용법까지 단계별 지침을 제공합니다.
## 전제 조건
.NET용 GroupDocs.Annotation을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1. .NET Framework 설치: .NET용 GroupDocs.Annotation에는 호환 가능한 .NET 런타임 환경이 필요합니다. 시스템에 .NET Framework가 설치되어 있는지 확인하십시오.
2. GroupDocs.Annotation 라이브러리에 액세스: 웹 사이트에서 다운로드하거나 NuGet과 같은 패키지 관리자를 통해 .NET용 GroupDocs.Annotation 라이브러리에 액세스할 수 있습니다.
3. 주석을 달 문서: 주석을 달려는 문서(예: PDF)를 준비합니다. 로컬로 또는 Azure Blob Storage와 같은 클라우드 스토리지 서비스를 통해 문서에 액세스할 수 있는지 확인하세요.

## 네임스페이스 가져오기
.NET용 GroupDocs.Annotation을 사용하여 문서에 주석을 추가하려면 필요한 네임스페이스를 프로젝트로 가져옵니다. 이 단계에서는 필요한 클래스와 기능에 액세스할 수 있는지 확인합니다.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Azure에서 문서 로드
Azure Blob Storage에 저장된 문서에 주석을 추가하려면 다음 단계를 따르세요.
### 1단계: 출력 경로 설정
주석이 달린 문서가 저장될 출력 경로를 정의합니다.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### 2단계: 문서 다운로드
 다음을 호출하여 Azure Blob Storage에서 문서를 검색합니다.`DownloadFile` 방법.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // 주석 논리
    annotator.Save(outputPath);
}
```
## Azure Blob Storage에서 파일 다운로드
 Azure Blob Storage에서 문서를 다운로드하려면 다음을 구현합니다.`DownloadFile` 방법.
### 1단계: Blob 검색
Azure Blob Storage 컨테이너에 액세스하고 원하는 Blob을 검색합니다.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### 2단계: Blob 콘텐츠 다운로드
Blob 콘텐츠를 메모리 스트림으로 다운로드합니다.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Azure Blob Storage 컨테이너 가져오기
 Azure Blob Storage와 상호 작용하려면 다음을 구현합니다.`GetContainer` 방법.
### 1단계: 스토리지 자격 증명 초기화
필요한 계정 자격 증명과 끝점 정보를 제공합니다.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{계정 이름}.blob.core.windows.net/";
```
### 2단계: Blob 클라이언트 만들기
Azure Blob Storage와 상호 작용할 클라이언트를 만듭니다.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### 3단계: 컨테이너 참조 검색
지정된 컨테이너에 대한 참조를 얻습니다.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### 4단계: 존재하지 않는 경우 컨테이너 생성
컨테이너가 있는지 확인하고, 없으면 만듭니다.
```csharp
container.CreateIfNotExists();
```

## 결론
.NET용 GroupDocs.Annotation은 개발자에게 강력한 문서 주석 기능을 제공하여 .NET 응용 프로그램에 원활하게 통합됩니다. 이 자습서에 설명된 단계를 수행하면 GroupDocs.Annotation의 기능을 효과적으로 활용하여 Azure Blob Storage에 저장된 문서에 주석을 달 수 있습니다.
#### FAQ
### .NET용 GroupDocs.Annotation은 모든 문서 형식과 호환됩니까?
GroupDocs.Annotation은 PDF, DOCX, PPTX 등을 포함한 광범위한 문서 형식을 지원합니다.
### 특정 요구사항에 따라 주석을 맞춤설정할 수 있나요?
예, GroupDocs.Annotation은 주석에 대한 광범위한 사용자 정의 옵션을 제공하므로 사용자가 모양, 동작 및 메타데이터를 수정할 수 있습니다.
### GroupDocs.Annotation은 공동 문서 주석에 적합합니까?
전적으로! GroupDocs.Annotation은 여러 사용자가 동시에 주석을 추가, 편집 및 검토할 수 있도록 하여 공동 문서 주석 작성을 용이하게 합니다.
### GroupDocs.Annotation은 플랫폼 간 호환성을 제공합니까?
예, GroupDocs.Annotation은 Windows, Linux 및 macOS를 포함한 다양한 플랫폼에서 원활하게 작동하도록 설계되었습니다.
### GroupDocs.Annotation 사용자에게 기술 지원이 제공됩니까?
예, GroupDocs는 포럼과 전용 지원 채널을 통해 포괄적인 기술 지원을 제공합니다.