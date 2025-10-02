---
"date": "2025-05-06"
"description": "GroupDocs.Annotation을 사용하여 Java 문서에 밑줄 주석을 추가하고 제거하는 방법을 알아보세요. 이 자세한 가이드를 통해 문서 관리를 더욱 효율적으로 개선하세요."
"title": "GroupDocs를 사용하여 Java에서 밑줄 주석 추가 및 제거&#58; 종합 가이드"
"url": "/ko/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
type: docs
"weight": 1
---

# Java 구현 방법: GroupDocs를 사용하여 밑줄 주석 추가 및 제거

## 소개

프로그래밍 방식으로 주석을 추가하거나 제거하여 문서 관리 시스템을 개선하고 싶으신가요? 이 튜토리얼에서는 Java 기반의 강력한 GroupDocs.Annotation 라이브러리를 사용하여 PDF와 같은 문서에 밑줄 주석을 추가하고 제거하는 방법을 안내합니다.

**배울 내용:**
- Annotator 클래스를 초기화합니다.
- Java용 GroupDocs.Annotation을 사용하여 주석에 밑줄 주석을 추가합니다.
- 문서에서 모든 주석을 제거합니다.
- GroupDocs.Annotation을 효율적으로 사용할 수 있도록 환경을 구성하세요.

이러한 기능을 프로젝트에서 어떻게 활용할 수 있는지 살펴보겠습니다. 시작하기 전에 필요한 전제 조건이 충족되었는지 확인하세요.

## 필수 조건

### 필수 라이브러리 및 종속성
이 튜토리얼을 효과적으로 따르려면 다음 사항이 있는지 확인하세요.
- **Java용 GroupDocs.Annotation**: 버전 25.2 이상을 권장합니다.
- **자바 개발 키트(JDK)**: 버전 8 이상이 필요합니다.

### 환경 설정 요구 사항
IntelliJ IDEA나 Eclipse와 같은 IDE와 Maven과 같은 빌드 도구가 개발 환경에 포함되어 있는지 확인하세요.

### 지식 전제 조건
Java 프로그래밍에 대한 기본적인 이해, 특히 Maven을 통한 라이브러리 작업에 대한 이해가 유익합니다.

## Java용 GroupDocs.Annotation 설정

Java 프로젝트에서 GroupDocs.Annotation을 사용하려면 다음 설정 단계를 따르세요.

**Maven 구성:**
다음 구성을 추가하세요. `pom.xml` GroupDocs.Annotation을 다운로드하고 통합할 파일입니다.

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/annotation/java/</url>
   </repository>
</repositories>
<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-annotation</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

**라이센스 취득:**
GroupDocs에서 무료 평가판을 다운로드하거나 임시 라이선스를 구매하여 라이브러리의 모든 기능을 사용해 보세요. 실제 업무용으로 사용하려면 라이선스를 구매해야 합니다.

## 구현 가이드

### 기능 1: 주석자 초기화 및 밑줄 주석 추가

이 섹션에서는 초기화 과정을 안내합니다. `Annotator` 클래스를 사용하여 문서에 밑줄 주석을 추가합니다.

#### 개요
주석을 추가하면 문서의 특정 부분을 강조하는 데 도움이 됩니다. 여기서는 설명이나 피드백을 위해 텍스트에 밑줄을 긋는 데 중점을 둡니다.

#### 단계별 구현

**1. Annotator 초기화**
생성하다 `Annotator` 객체를 선택하고 PDF 파일을 로드합니다.

```java
import com.groupdocs.annotation.Annotator;

// 주석을 달고 싶은 문서를 로드하세요
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. 답글로 댓글 만들기**
밑줄 주석과 관련된 주석을 정의합니다.

```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;
import java.util.ArrayList;
import java.util.List;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

**3. 밑줄 주석을 위한 점 정의**
밑줄이 나타날 위치를 결정하기 위해 좌표를 설정합니다.

```java
import com.groupdocs.annotation.models.Point;

Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = new ArrayList<>();
points.add(point1);
points.add(point2);
points.add(point3);
points.add(point4);
```

**4. 밑줄 주석 만들기 및 구성**
밑줄 주석을 만들고 색상, 불투명도, 주석 등의 속성을 설정합니다.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // ARGB 형식의 노란색
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. 주석이 달린 문서 저장**
변경 사항을 새 파일에 저장합니다.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### 문제 해결 팁
- 모든 지점의 좌표가 문서 범위 내에 있는지 확인하세요.
- 다음을 확인하십시오. `outputPath` 디렉토리가 존재하며 쓰기가 가능합니다.

### 기능 2: 주석 없이 문서 저장

이 섹션에서는 이전에 주석이 달린 문서에서 모든 주석을 제거하는 방법을 다룹니다.

#### 개요
공유 또는 보관 목적으로 주석이 없는 깔끔한 버전의 문서를 저장해야 할 수도 있습니다.

#### 단계별 구현

**1. 주석이 달린 문서로 Annotator 초기화**
기존 주석이 있는 문서를 로드합니다.

```java
Annotator annotator = new Annotator(outputPath);
```

**2. 주석 제거를 위한 저장 옵션 구성**
출력 파일에 주석을 저장하지 않도록 지정합니다.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. 주석 없이 문서 저장**
정리된 문서의 경로를 정의하고 저장합니다.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## 실제 응용 프로그램

이러한 기능이 유익할 수 있는 실제 시나리오는 다음과 같습니다.
1. **문서 검토**: 계약서나 보고서의 특정 부분을 강조하고 의견을 달아 검토합니다.
2. **교육 도구**: 학생들을 위해 교과서에 주석이나 수정사항을 덧붙입니다.
3. **협업 편집**: 팀원들 간에 주석이 달린 초안을 공유하여 피드백을 얻습니다.
4. **법률 문서**: 토론 중 법률 문서의 주요 조항에 밑줄을 긋습니다.
5. **마케팅 자료**: 배포하기 전에 브로셔에 중요한 정보를 강조 표시합니다.

## 성능 고려 사항
GroupDocs.Annotation을 사용할 때 성능을 최적화하기 위해 다음 팁을 고려하세요.
- **메모리 관리**: 적절하게 폐기하세요 `Annotator` 리소스를 확보하기 위한 객체.
- **일괄 처리**: 여러 문서에 주석을 달 경우, 시스템 부하를 효과적으로 관리하기 위해 일괄적으로 처리합니다.
- **자원 할당**: 대용량 파일을 처리하는 데 필요한 충분한 메모리와 처리 능력이 환경에 있는지 확인하세요.

## 결론
Java용 GroupDocs.Annotation을 사용하여 밑줄 주석을 추가하고 제거하는 방법을 알아보았습니다. 이 튜토리얼에서는 Annotator 클래스 초기화, 주석을 포함한 주석 구성, 주석 없이 문서 저장 방법을 다루었습니다. 

더 자세히 알아보려면 이러한 기능을 기존 문서 관리 시스템에 통합하거나 GroupDocs에서 제공하는 다른 주석 유형을 실험해 보세요.

## FAQ 섹션
1. **한 번의 실행으로 여러 개의 밑줄 주석을 구성하려면 어떻게 해야 하나요?**
   - 여러 개 생성 `UnderlineAnnotation` 객체를 추가하고 순차적으로 추가합니다. `annotator.add()` 방법.
2. **이 라이브러리를 사용하여 PDF 내의 이미지에 주석을 달 수 있나요?**
   - 네, GroupDocs.Annotation은 PDF와 같은 문서 내의 이미지에 주석을 다는 것을 지원합니다.
3. **GroupDocs.Annotation은 어떤 파일 형식을 지원합니까?**
   - PDF, Word, Excel 등 다양한 문서 형식을 지원합니다.