---
additionalTitle: GroupDocs API references
date: 2026-08-04
description: Document annotation API를 사용하여 .NET 및 Java 애플리케이션에서 PDF, Word, Excel 및
  PowerPoint 주석을 추가하는 방법을 배웁니다. 단계별 튜토리얼에서는 텍스트 마크업, 댓글, 도형 및 협업 기능을 다룹니다.
keywords:
- document annotation API
- PDF annotation
- Java annotation library
- collaborative review
- .NET annotation
lastmod: 2026-08-04
linktitle: GroupDocs.Annotation 개발자 가이드
og_description: Document annotation API를 사용하면 PDF, Word, Excel 및 PowerPoint 주석을 빠르게
  추가할 수 있습니다. .NET 및 Java 애플리케이션에 하이라이트, 댓글 및 도형을 통합하는 방법을 배웁니다.
og_image_alt: Guide showing how to annotate PDFs and Office documents using GroupDocs.Annotation
og_title: Document annotation API – .NET 및 Java에서 하이라이트, 댓글 및 도형 추가
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Learn how to use the document annotation API to add PDF, Word, Excel
    & PowerPoint annotations in .NET and Java applications. Step‑by‑step tutorials
    cover text markup, comments, shapes, and collaboration features.
  headline: Document annotation API | GroupDocs.Annotation tutorials & SDK examples
  type: TechArticle
- questions:
  - answer: Yes. A valid GroupDocs license is required for production deployments,
      and a free trial is available for evaluation.
    question: Can I use the document annotation API in a commercial product?
  - answer: Absolutely. You can supply the password when opening the document, and
      all annotation operations work transparently.
    question: Does the API support password‑protected PDFs?
  - answer: The SDK supports .NET Framework 4.5+, .NET Core 3.1+, .NET 5, and .NET
      6+.
    question: Which .NET versions are compatible?
  - answer: Yes. You can load and save documents directly from Amazon S3, Azure Blob
      Storage, Google Cloud Storage, and other cloud providers.
    question: Is there built‑in support for cloud storage services?
  type: FAQPage
tags:
- document annotation
- GroupDocs.Annotation
- .NET annotation
- Java annotation
title: Document annotation API | GroupDocs.Annotation 튜토리얼 및 SDK 예제
type: docs
url: /ko/
weight: 11
---

# GroupDocs.Annotation 개발자 가이드 – 문서 주석 API

이 가이드에서는 **document annotation API**가 PDF, Word, Excel, PowerPoint 및 기타 많은 파일 형식에 하이라이트, 댓글, 도형과 같은 풍부한 주석 기능을 직접 삽입하도록 어떻게 지원하는지 알아볼 수 있습니다. 협업 검토 포털, 교육용 앱, 혹은 법률 문서 워크플로를 구축하든, API는 .NET 및 Java 환경 모두에서 일관되고 고성능의 주석 작업 방식을 제공합니다.

## 빠른 답변
- **문서 주석 API는 무엇을 하나요?** 개발자가 외부 종속성 없이 50개 이상의 문서 형식에 주석을 추가, 편집 및 관리할 수 있게 합니다.  
- **지원되는 플랫폼은 무엇인가요?** .NET (Framework, Core, .NET 5/6) 및 Java (JDK 8 이상).  
- **개발에 라이선스가 필요합니까?** 무료 체험을 이용할 수 있으며, 프로덕션 사용을 위해서는 라이선스가 필요합니다.  
- **PDF와 Office 파일을 동일한 코드로 주석 달 수 있나요?** 예—통합 API 하나로 PDF, Word, Excel, PowerPoint, 이미지, HTML 등 다양한 형식을 처리합니다.  
- **클라우드 배포가 가능한가요?** 물론입니다—Windows, Linux, macOS, Docker 또는 모든 클라우드 서비스에서 실행할 수 있습니다.

## 문서 주석 API란?

문서 주석 API는 문서에 주석을 추가, 편집 및 제거하기 위한 크로스‑플랫폼 SDK입니다. PDF, Word, Excel, PowerPoint, 이미지, HTML 등 50개 이상의 형식을 지원하므로 단일 객체 모델로 작업할 수 있어 형식별 코드를 피하면서 레이아웃 정확도와 메타데이터를 유지합니다.

## GroupDocs.Annotation를 선택해야 하는 이유?

GroupDocs.Annotation는 PDF, Word, Excel, PowerPoint 및 이미지 등 50개 이상의 파일 유형에 대한 주석을 외부 종속성 없이 처리한다는 점에서 돋보입니다. 고성능 렌더링 엔진은 표준 서버에서 수백 페이지 문서를 1초 미만에 처리하며, 내장된 협업 도구를 통해 여러 사용자가 실시간으로 스레드형 댓글을 추가할 수 있습니다.

- **포맷 독립성** – 하나의 API로 PDF부터 Excel 스프레드시트까지 50개 이상의 문서 유형을 지원합니다.  
- **다양한 주석 유형** – 텍스트 마크업, 그래픽 도형, 댓글 및 협업 답글 스레드가 모두 내장되어 있습니다.  
- **외부 종속성 없음** – Adobe Reader, Office 또는 기타 서드파티 도구가 필요하지 않습니다.  
- **고성능 렌더링** – 빠른 미리보기 생성을 위한 품질 및 해상도 조정이 가능합니다.  
- **크로스 플랫폼 지원** – Windows, Linux, macOS, Docker 또는 서버리스 환경에서 원활하게 실행됩니다.

## 주요 사용 사례
- **문서 검토 워크플로** – 검토자가 실시간으로 댓글을 추가하고 변경을 승인할 수 있습니다.  
- **교육 애플리케이션** – 교사가 문서 내에서 학습 자료를 강조하고 피드백을 제공할 수 있습니다.  
- **법률 문서 처리** – 조항을 표시하고, 메모를 추가하며, 계약서의 수정 내역을 추적합니다.  
- **헬스케어 문서** – HIPAA 준수를 유지하면서 중요한 환자 정보를 강조합니다.  
- **건설 및 엔지니어링** – 청사진, 회로도 및 기술 도면에 정밀한 측정값을 주석 달 수 있습니다.

## .NET 시작하기
강력한 문서 주석 기능을 .NET 애플리케이션에 제공

C# 및 .NET 프로젝트에 포괄적인 주석 기능을 통합하세요.

[Explore .NET Tutorials](./net/)

### 필수 .NET 튜토리얼
- [**Document Loading**](./net/document-loading) - 파일, 스트림, URL 및 클라우드 스토리지에서 문서를 로드합니다
- [**Annotation Types**](./net/text-annotations) - 텍스트, 그래픽, 폼 및 이미지 주석을 구현합니다
- [**Document Saving**](./net/document-saving) - 다양한 출력 옵션으로 주석이 달린 문서를 저장합니다
- [**Annotation Management**](./net/annotation-management) - 프로그래밍 방식으로 주석을 추가, 업데이트, 삭제 및 필터링합니다
- [**Collaboration Features**](./net/reply-management) - 댓글 스레드와 협업 검토를 구현합니다
- [**Document Preview**](./net/document-preview) - 사용자 정의 해상도로 문서 미리보기를 생성합니다
- [**Form Fields**](./net/form-field-annotations) - 인터랙티브 폼 컴포넌트를 생성합니다
- [**Document Analysis**](./net/document-information) - 메타데이터와 페이지 정보를 추출합니다
- [**Licensing Options**](./net/licensing-and-configuration) - 라이선스를 구현하고 구성합니다

### 고급 .NET 기능
- [**Document Preview**](./net/document-preview) - 사용자 정의 해상도로 문서 미리보기를 생성합니다
- [**Form Fields**](./net/form-field-annotations) - 인터랙티브 폼 컴포넌트를 생성합니다
- [**Document Analysis**](./net/document-information) - 메타데이터와 페이지 정보를 추출합니다
- [**Licensing Options**](./net/licensing-and-configuration) - 라이선스를 구현하고 구성합니다

## Java 시작하기
Java 문서 주석 SDK

플랫폼 독립적인 API로 Java 애플리케이션에 포괄적인 주석 기능을 추가합니다.

[Explore Java Tutorials](./java/)

### 필수 Java 튜토리얼
- [**Document Loading**](./java/document-loading) - 클라우드 스토리지 통합을 포함한 다양한 방법으로 문서를 로드합니다
- [**Text Annotations**](./java/text-annotations) - 강조, 밑줄, 취소선 및 텍스트 교체
- [**Graphical Annotations**](./java/graphical-annotations) - 화살표, 도형 및 측정값을 추가합니다
- [**Image Annotations**](./java/image-annotations) - 문서에 이미지를 삽입하고 맞춤 설정합니다  
- [**Annotation Management**](./java/annotation-management) - 전체 주석 수명 주기 관리

### 고급 Java 기능
- [**Document Preview**](./java/document-preview) - 고품질 썸네일 및 미리보기를 생성합니다
- [**Collaboration Tools**](./java/reply-management) - 스레드형 댓글 및 답글을 구현합니다
- [**Document Information**](./java/document-information) - 문서 메타데이터와 구조에 접근합니다
- [**Advanced Features**](./java/advanced-features) - 특화된 주석 기능 및 최적화
- [**Configuration Options**](./java/licensing-and-configuration) - 주석 동작 및 성능을 맞춤 설정합니다

## 오늘 바로 사용해 보기

AnnotationConfig는 SDK의 라이선스 키와 전역 설정을 지정하는 구성 클래스입니다. 지금 바로 문서 주석 API를 체험하려면 GroupDocs 웹사이트에서 무료 체험을 다운로드하고, 프로젝트에 NuGet 패키지(.NET) 또는 Maven 의존성(Java)을 추가한 뒤, 라이선스 키로 AnnotationConfig를 초기화하십시오. 포함된 샘플 프로젝트는 파일 로드, 하이라이트 추가, 주석이 달린 문서 저장을 몇 줄의 코드만으로 보여줍니다.

### 무료 체험
구매 전 모든 기능을 탐색할 수 있는 무료 체험을 시작하세요.  
[Download Trial](https://releases.groupdocs.com/annotation/)

### API 문서
지원되는 모든 플랫폼에 대한 자세한 API 레퍼런스입니다.  
[Browse API Reference](https://reference.groupdocs.com/annotation/)

## 자주 묻는 질문

**Q: 문서 주석 API를 상용 제품에 사용할 수 있나요?**  
A: 예. 프로덕션 배포에는 유효한 GroupDocs 라이선스가 필요하며, 평가용 무료 체험을 제공합니다.

**Q: API가 비밀번호로 보호된 PDF를 지원하나요?**  
A: 물론입니다. 문서를 열 때 비밀번호를 제공하면 모든 주석 작업이 투명하게 작동합니다.

**Q: 호환되는 .NET 버전은 무엇인가요?**  
A: SDK는 .NET Framework 4.5+, .NET Core 3.1+, .NET 5 및 .NET 6+을 지원합니다.

**Q: API가 대용량 파일을 어떻게 처리하나요?**  
`Document.OptimizeResources()`는 주석 작업 중 캐시된 데이터를 해제하고 메모리 사용량을 줄이는 메서드입니다.  
콘텐츠를 스트리밍하고 `Document.OptimizeResources()`와 같은 메모리 최적화 메서드를 제공하여 메모리 사용량을 낮게 유지합니다.

**Q: 클라우드 스토리지 서비스에 대한 내장 지원이 있나요?**  
A: 예. Amazon S3, Azure Blob Storage, Google Cloud Storage 및 기타 클라우드 제공업체에서 문서를 직접 로드하고 저장할 수 있습니다.

---

**Last updated:** 2026-08-04  
**Tested with:** GroupDocs.Annotation 23.11 for .NET & Java  
**Author:** GroupDocs