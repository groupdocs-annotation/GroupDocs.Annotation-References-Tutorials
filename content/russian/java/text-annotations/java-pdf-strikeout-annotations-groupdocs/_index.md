---
categories:
- Java PDF Processing
date: '2026-05-21'
description: Узнайте, как добавить аннотации зачеркивания в PDF-файлы на Java с помощью
  GroupDocs. Этот пошаговый учебник охватывает настройку, код, устранение неполадок
  и советы по производительности.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Руководство по зачеркиванию текста в PDF на Java
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  type: TechArticle
- description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
  steps:
  - name: Setting Up File Paths
    text: Define the locations of your source PDF and the destination file. Incorrect
      paths are a common source of “File Not Found” errors. **Common Mistake Alert:**
      Ensure the output directory exists and is writable; GroupDocs will not auto‑create
      missing folders.
  - name: Initialize the Annotator
    text: Create an `Annotator` instance that loads the PDF into memory. **What happens
      here?** The library parses the PDF structure, builds an internal representation,
      and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this
      step may take a few seconds.
  - name: Adding Comments (Optional but Recommended)
    text: '`Comment` is a class that represents a textual note attached to an annotation,
      allowing collaborators to explain the reason for the strikeout. **Real‑world
      tip:** Use comments to explain why text is being removed—this is especially
      useful in legal or editorial review workflows.'
  - name: Defining Annotation Coordinates
    text: '`Point` objects store X‑Y coordinate pairs that define the exact location
      of an annotation on a PDF page. **Coordinate System Explained:** PDF coordinates
      start at the bottom‑left corner (0,0). The example creates a horizontal line
      from (80,730) to (240,730) on the target page. **Finding the Right C'
  - name: Creating the Strikeout Annotation
    text: '`StrikeoutAnnotation` encapsulates the visual line, its style properties
      such as color and opacity, and any associated metadata for a strikeout mark.
      **Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright
      yellow). Use an online converter if you need brand‑specific shades. '
  - name: Apply the Annotation
    text: '`addAnnotation` is a method of the `Annotator` that registers the prepared
      annotation with the document so it will be rendered and saved.'
  - name: Save and Clean Up
    text: '`dispose()` releases native resources held by the `Annotator` instance,
      preventing memory leaks after processing is complete. **Memory Management Note:**
      Calling `dispose()` frees native resources and prevents memory leaks when processing
      batches of PDFs.'
  type: HowTo
- questions:
  - answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
    question: Can I strikeout text across multiple lines?
  - answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
    question: What happens if I specify coordinates outside the page boundaries?
  - answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
    question: Can I remove strikeout annotations after adding them?
  - answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
    question: Is there a limit to how many annotations I can add to a single PDF?
  - answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
    question: How do I work with password‑protected PDFs?
  type: FAQPage
tags:
- java-pdf
- annotations
- groupdocs
- document-processing
title: Как добавить аннотации зачеркивания в PDF-файлы на Java – Полное руководство
  GroupDocs
type: docs
url: /ru/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# Как добавить аннотации зачеркивания в PDF на Java

Ever needed to cross out text in a PDF programmatically? Whether you're building a document review system, creating an editing workflow, or just need to mark text for deletion, **how to add strikeout** annotations in Java is a practical skill that saves time and reduces manual effort. In this comprehensive guide you’ll discover everything you need to know to implement strikeout annotations with GroupDocs.Annotation for Java, from project setup to performance tuning.

## Быстрые ответы
- **Что является первым шагом?** Добавьте зависимость GroupDocs.Annotation Maven в ваш `pom.xml`.  
- **Как создать зачеркивание?** Создайте экземпляр `Annotator`, определите `StrikeoutAnnotation` с точками, задайте цвет/непрозрачность, затем вызовите `addAnnotation`.  
- **Можно ли добавить комментарии?** Да, прикрепите объект `Comment` к аннотации для совместной работы.  
- **Что делать, если аннотация размещена неверно?** Отрегулируйте координатные точки; PDF использует систему координат с началом в левом нижнем углу.  
- **Есть ли ограничение на размер документа?** GroupDocs обрабатывает PDF‑файлы со сотнями страниц без загрузки всего файла в память.

## Что означает “how to add strikeout” в аннотации PDF?
Фраза “how to add strikeout” относится к процессу программного рисования линии через выбранный текст внутри PDF‑документа с использованием API аннотаций. В Java GroupDocs.Annotation предоставляет специализированный класс `StrikeoutAnnotation`, который обрабатывает рендеринг, стилизацию и сохранение зачеркиваний.

## Почему использовать GroupDocs для зачеркивания PDF в Java?
GroupDocs.Annotation поддерживает **50+ форматов ввода и вывода** — включая PDF, DOCX, XLSX, PPTX, HTML и распространённые типы изображений — поэтому вы не привязаны к одному типу файлов. Он предоставляет высокоуровневый API, который абстрагирует низкоуровневую структуру PDF, автоматически обрабатывая встраивание шрифтов, рендеринг страниц и сохранение аннотаций, что позволяет разработчикам сосредоточиться на бизнес‑логике, а не на внутренностях PDF.

## Предварительные требования и требования к настройке

### Необходимые требования
- **Java Development Kit (JDK):** Версия 8 или новее (рекомендовано JDK 11+ для оптимальной сборки мусора).
- **GroupDocs.Annotation for Java:** Интегрируется через Maven (см. сниппет Maven ниже).
- **IDE:** IntelliJ IDEA, Eclipse или любой совместимый с Java редактор.

### Настройка зависимостей Maven
Add the following dependency block to your `pom.xml`:

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

**Совет:** Всегда проверяйте последнюю версию на странице релизов GroupDocs; новые версии добавляют функции и исправляют ошибки, которые могут влиять на отображение аннотаций.

### Получение лицензии
GroupDocs.Annotation requires a valid license for production use. You have three options:

- **Бесплатная пробная версия:** Download from [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)
- **Временная лицензия:** Request a development key at [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Полная лицензия:** Purchase for production at [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

The trial adds a subtle watermark, so plan your testing accordingly.

## Пошаговое руководство по реализации

### Понимание основных компонентов
The following definitions give you a quick mental model:

- **Annotator:** Основной объект API, который загружает PDF и предоставляет методы аннотаций.  
- **StrikeoutAnnotation:** Представляет визуальную линию зачеркивания и её параметры стиля.  
- **Point:** Пара координат (X, Y), указывающая библиотеке, где начинается и заканчивается линия.  
- **Comment:** Необязательный текст, прикреплённый к аннотации для совместной работы.

### Шаг 1: Настройка путей к файлам
Define the locations of your source PDF and the destination file. Incorrect paths are a common source of “File Not Found” errors.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Common Mistake Alert:** Ensure the output directory exists and is writable; GroupDocs will not auto‑create missing folders.

### Шаг 2: Инициализация Annotator
Create an `Annotator` instance that loads the PDF into memory.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**What happens here?** The library parses the PDF structure, builds an internal representation, and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this step may take a few seconds.

### Шаг 3: Добавление комментариев (необязательно, но рекомендуется)
`Comment` is a class that represents a textual note attached to an annotation, allowing collaborators to explain the reason for the strikeout.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Real‑world tip:** Use comments to explain why text is being removed—this is especially useful in legal or editorial review workflows.

### Шаг 4: Определение координат аннотации
`Point` objects store X‑Y coordinate pairs that define the exact location of an annotation on a PDF page.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Coordinate System Explained:** PDF coordinates start at the bottom‑left corner (0,0). The example creates a horizontal line from (80,730) to (240,730) on the target page.

**Finding the Right Coordinates:** Many developers create a helper that converts percentages of page width/height into absolute points, making the code resilient to different page sizes.

### Шаг 5: Создание аннотации зачеркивания
`StrikeoutAnnotation` encapsulates the visual line, its style properties such as color and opacity, and any associated metadata for a strikeout mark.

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535); // Yellow
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0); 
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

**Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright yellow). Use an online converter if you need brand‑specific shades.

**Opacity Recommendation:** An opacity of `0.7` (70 %) offers a clear visual cue while keeping the underlying text legible.

### Шаг 6: Применение аннотации
`addAnnotation` is a method of the `Annotator` that registers the prepared annotation with the document so it will be rendered and saved.

```java
annotator.add(strikeout);
```

### Шаг 7: Сохранение и очистка
`dispose()` releases native resources held by the `Annotator` instance, preventing memory leaks after processing is complete.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Memory Management Note:** Calling `dispose()` frees native resources and prevents memory leaks when processing batches of PDFs.

## Распространённые проблемы и их решения

### Проблема 1: Ошибки “File Not Found”
**Symptoms:** Exception thrown during `Annotator` construction.  
**Solution:** Verify both input and output paths, and confirm the application has read/write permissions.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### Проблема 2: Зачеркивание появляется в неправильном месте
**Symptoms:** The line does not line up with the intended text.  
**Solution:** Remember that PDF Y‑coordinates increase upward. Use a visual debugging tool or print the page dimensions to fine‑tune the points.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### Проблема 3: Аннотация не видна
**Symptoms:** No strikeout shows up after saving.  
**Possible Causes & Fixes:**
- **Opacity too low:** Temporarily set opacity to `1.0` to verify visibility.  
- **Color blending:** Use a high‑contrast color like red (`255`).  
- **Incorrect page index:** Page numbers are zero‑based; ensure you target the correct page.

### Проблема 4: Проблемы с памятью при работе с большими файлами
**Symptoms:** `OutOfMemoryError` or sluggish performance.  
**Solutions:**  
- Process documents in smaller batches.  
- Use the streaming API if available.  
- Always invoke `dispose()` after each document.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## Применения в реальном мире и примеры использования

### Обзор юридических документов
Law firms annotate contracts with strikeouts to indicate deleted clauses while preserving an audit trail.

### Редактирование академических статей
Professors use strikeouts to suggest removals during peer review, keeping the original text visible for context.

### Системы управления контентом
Publishing platforms automatically flag policy‑violating sections with strikeouts before manual moderation.

### Управление версиями документов
Enterprises treat strikeout annotations as “deletion markers” in a document‑centric version‑control workflow, similar to code diffs.

## Советы по оптимизации производительности

### Стратегия пакетной обработки
When handling many PDFs, reuse a single `Annotator` instance where possible and process files in parallel threads.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### Лучшие практики управления памятью
- Call `dispose()` on every `Annotator`.  
- Limit concurrent document loads to avoid heap pressure.  
- Monitor JVM memory usage with tools like VisualVM.

### Кеширование координат
If you apply the same annotation layout across multiple files, cache the `Point` objects to avoid recomputation.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## Расширенные параметры настройки

### Динамический выбор цвета
Choose colors at runtime based on business rules (e.g., red for critical deletions, yellow for tentative ones).

```java
// Choose colors based on annotation type or user
int colorByPriority = getPriorityColor(annotationType);
strikeout.setFontColor(colorByPriority);

private int getPriorityColor(String type) {
    switch(type) {
        case "HIGH": return 255;    // Red
        case "MEDIUM": return 65535; // Yellow  
        case "LOW": return 65280;   // Green
        default: return 0;          // Black
    }
}
```

### Многострочные зачеркивания
Create a series of `Point` pairs to draw a zig‑zag line that crosses several lines of text.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## Список проверки устранения неполадок
1. **File Permissions:** Verify read/write access.  
2. **Library Version:** Ensure you’re using a supported GroupDocs.Annotation release.  
3. **License Status:** Confirm the license file is correctly referenced.  
4. **PDF Compatibility:** Check that the PDF is not corrupted and is within supported size limits.  
5. **Coordinate Validation:** Ensure all points lie inside page bounds.  
6. **Heap Space:** Increase JVM `-Xmx` if processing very large files.

## Часто задаваемые вопросы

**Q: Can I strikeout text across multiple lines?**  
A: Yes. Create several `Point` objects that trace the desired path; the annotation will follow the supplied polyline.

**Q: What happens if I specify coordinates outside the page boundaries?**  
A: The annotation will be clipped and may become invisible. Always validate coordinates against the page’s width and height.

**Q: Can I remove strikeout annotations after adding them?**  
A: Absolutely. Use the `removeAnnotation` method with the annotation’s ID or filter by type to delete them programmatically.

**Q: Is there a limit to how many annotations I can add to a single PDF?**  
A: GroupDocs does not impose a hard cap, but performance may degrade after thousands of annotations. Consider pagination or summarizing annotations for very large sets.

**Q: How do I work with password‑protected PDFs?**  
A: Pass the password to the `Annotator` constructor. The library will decrypt the document in memory before applying any annotations.

**Q: How can I handle PDFs with different page sizes and orientations?**  
A: Retrieve each page’s dimensions via `annotator.getPageInfo(pageNumber)` and calculate coordinates relative to those dimensions to ensure consistent placement.

## Заключение
You now have a complete, production‑ready solution for **how to add strikeout** annotations to PDFs in Java using GroupDocs.Annotation. By mastering file‑path handling, coordinate calculation, and resource management, you can embed this capability into document review tools, content pipelines, or any Java‑based application that needs precise visual feedback.

**Следующие шаги**
1. Clone the example project and run it against a sample PDF.  
2. Experiment with different colors, opacities, and comment texts.  
3. Integrate the annotation workflow into your existing document‑processing service.  
4. Explore related annotation types—highlights, sticky notes, and shape annotations—to broaden your PDF manipulation toolkit.

Ready for more? Dive into the official documentation for deeper API insights.

## Дополнительные ресурсы

- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - Общая документация по библиотекам GroupDocs
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - Полное API‑справочное руководство  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - Подробное описание методов  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - Держите библиотеку в актуальном состоянии  
- [Purchase License](https://purchase.groupdocs.com/buy) - Лицензирование для продакшна  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - Оценка перед покупкой  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - Тестирование в разработке  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - Сообщество и официальная поддержка  

---

**Last Updated:** 2026-05-21  
**Tested With:** GroupDocs.Annotation 23.12 for Java  
**Author:** GroupDocs

## Связанные руководства

- [Add PDF Annotation Java – Complete GroupDocs Guide](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)  
- [Java PDF Annotation Tutorial - Complete Guide to Highlighting PDFs](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)  
- [How to Add Arrow to PDF in Java – Complete GroupDocs Tutorial](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)