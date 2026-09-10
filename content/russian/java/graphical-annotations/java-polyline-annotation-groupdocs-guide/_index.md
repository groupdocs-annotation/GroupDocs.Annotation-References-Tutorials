---
categories:
- Java Development
date: '2026-09-10'
description: Узнайте, как использовать pdf annotation library java для добавления
  интерактивных полилинейных аннотаций, интеграции с spring boot pdf annotation services
  и генерации SVG-путей в Java.
keywords:
- pdf annotation library java
- spring boot pdf annotation
- generate svg path java
- polyline annotation java
- groupdocs annotation java
lastmod: '2026-09-10'
linktitle: Руководство по полилинейным аннотациям Java
og_description: Узнайте, как использовать pdf annotation library java для добавления
  интерактивных полилинейных аннотаций, интеграции с spring boot pdf annotation services
  и генерации SVG-путей в Java.
og_image_alt: Guide to adding interactive polyline annotations using a pdf annotation
  library java
og_title: Как использовать pdf annotation library java для полилинейных PDF
schemas:
- author: GroupDocs
  dateModified: '2026-09-10'
  description: Learn how to use a pdf annotation library java to add interactive polyline
    annotations, integrate with spring boot pdf annotation services, and generate
    SVG paths in Java.
  headline: How to use a pdf annotation library java for polyline PDFs
  type: TechArticle
- description: Learn how to use a pdf annotation library java to add interactive polyline
    annotations, integrate with spring boot pdf annotation services, and generate
    SVG paths in Java.
  name: How to use a pdf annotation library java for polyline PDFs
  steps:
  - name: '**Create the annotation replies collection** – this gives reviewers a place
      to add comments.'
    text: '**Create the annotation replies collection** – this gives reviewers a place
      to add comments.'
  - name: '**Organize the replies** into a list that the annotation will reference.'
    text: '**Organize the replies** into a list that the annotation will reference.'
  - name: '**Configure the polyline** – set the bounding box, pen color, opacity,
      and most importantly the `SVGPath` that draws the line.'
    text: '**Configure the polyline** – set the bounding box, pen color, opacity,
      and most importantly the `SVGPath` that draws the line.'
  - name: '**Add the annotation to the document** via `annotator.addAnnotation(polyline)`.'
    text: '**Add the annotation to the document** via `annotator.addAnnotation(polyline)`.'
  - name: '**Save and clean up** – persist the PDF and dispose of the `Annotator`
      instance.'
    text: '**Save and clean up** – persist the PDF and dispose of the `Annotator`
      instance.'
  - name: '**Trim coordinate precision** – round to two decimal places.'
    text: '**Trim coordinate precision** – round to two decimal places.'
  - name: '**Prefer relative commands (`l`)** – they reduce string length by up to
      30 %.'
    text: '**Prefer relative commands (`l`)** – they reduce string length by up to
      30 %.'
  - name: '**Group similar annotations** – apply the same style to multiple polylines
      to reuse resources.'
    text: '**Group similar annotations** – apply the same style to multiple polylines
      to reuse resources.'
  type: HowTo
- questions:
  - answer: It connects multiple points to form complex, interactive paths in a PDF.
    question: What is the primary purpose of a polyline annotation?
  - answer: GroupDocs.Annotation for Java, a leading pdf annotation library java.
    question: Which library makes this easiest in Java?
  - answer: Yes – see the Spring Boot integration section.
    question: Can I use it with Spring Boot?
  - answer: By providing an SVG path string (e.g., using `generate svg path java`).
    question: How do I define the line shape?
  - answer: A trial license works for development; a production license is required
      for deployment.
    question: Do I need a license?
  type: FAQPage
tags:
- pdf annotation
- java
- groupdocs
- spring boot
title: Как использовать pdf annotation library java для полилинейных PDF
type: docs
---

# Как использовать pdf annotation library java для полилинейных PDF

В этом подробном руководстве вы узнаете, как **использовать pdf annotation library java** для создания интерактивных полилинейных аннотаций, внедрения их в сервисы Spring Boot и программного генерации строк SVG‑пути. Независимо от того, создаёте ли вы платформу для рецензирования документов, инструмент электронного обучения или генератор технических диаграмм, приведённые ниже шаги предоставят готовое к производству решение, масштабируемое.

## Быстрые ответы
- **Какова основная цель полилинейной аннотации?** Она соединяет несколько точек, образуя сложные интерактивные пути в PDF.  
- **Какая библиотека делает это проще всего в Java?** GroupDocs.Annotation for Java, ведущая pdf annotation library java.  
- **Можно ли использовать её с Spring Boot?** Да — см. раздел интеграции с Spring Boot.  
- **Как определить форму линии?** Предоставив строку SVG‑пути (например, используя `generate svg path java`).  
- **Нужна ли лицензия?** Пробная лицензия подходит для разработки; для развертывания требуется лицензия для продакшн.

## Почему стоит выбрать GroupDocs.Annotation для Java?

GroupDocs.Annotation предоставляет полный набор функций, упрощающих разработку аннотаций PDF, включая высокопроизводительную обработку, широкую поддержку форматов и встроенные интерактивные типы аннотаций, одновременно уменьшая сложность кода и потребление памяти. Это делает её идеальной для корпоративных приложений, требующих надёжного, масштабируемого управления документами в различных средах.

GroupDocs.Annotation — это **pdf annotation library java**, превосходящая общие PDF‑инструменты. Она предлагает:

- **Более 50 форматов ввода и вывода** — включая DOCX, XLSX, PPTX, HTML и распространённые типы изображений — при обработке PDF‑файлов из сотен страниц без загрузки всего файла в память.  
- **Встроенные типы аннотаций** (polyline, highlight, comment и др.), которые отображаются одинаково во всех основных PDF‑просмотрщиках.  
- **Обработка на стороне сервера**, устраняющая проблемы безопасности на клиенте и обеспечивающая одинаковый рендеринг на любой платформе.  
- **Производительность корпоративного уровня** — библиотека может аннотировать PDF‑файл в 300 страниц менее чем за 2 секунды на типичных облачных ВМ.

По сравнению с iText или PDFBox вы пишете гораздо меньше шаблонного кода; по сравнению с клиентскими решениями на JavaScript вы оставляете тяжёлую работу на сервере, где полностью контролируете лицензирование и использование ресурсов.

## Чему вы научитесь

К концу этого руководства вы сможете:

- Установить и настроить pdf annotation library java в проекте Maven или Gradle.  
- Создавать интерактивные полилинейные PDF‑аннотации с пользовательскими цветами, прозрачностью и геометрией, определённой SVG.  
- Прикреплять ответы‑комментарии к аннотациям для совместных процессов рецензирования.  
- Оптимизировать использование памяти и пакетно обрабатывать большие коллекции документов.  
- Предоставлять создание аннотаций через REST API Spring Boot.

## Предварительные требования и настройка окружения

**Необходимые требования**

- JDK 8 или выше (рекомендовано JDK 11+).  
- Maven 3.6+ или Gradle 6+.  
- IDE, например IntelliJ IDEA или Eclipse.  
- Базовое знакомство с Java и управлением зависимостями Maven.

**Желательно**

- Понимание системы координат страниц PDF.  
- Опыт работы с синтаксисом SVG‑пути (полезно для `generate svg path java`).

### Конфигурация Maven

Добавьте зависимость GroupDocs.Annotation в ваш `pom.xml`:

```xml
<!-- placeholder for Maven dependency -->
```

**Совет**: Всегда проверяйте, что используете последнюю стабильную версию на сайте GroupDocs. Версия 25.2 добавила ускорение на 30 % при рендеринге polyline.

### Настройка лицензии

GroupDocs.Annotation требует лицензии для использования в продакшн.

- **Разработка/тестирование** – начните с [бесплатной пробной лицензии](https://releases.groupdocs.com/annotation/java/), предоставляющей полный функционал на 30 дней.  
- **Расширенная оценка** – запросите [временную лицензию](https://purchase.groupdocs.com/temporary-license/), если вам нужно больше времени.  
- **Продакшн** – приобретите подписку на [странице покупки GroupDocs](https://purchase.groupdocs.com/buy). Лицензирование делится на уровни в зависимости от размера развертывания (один‑приложение vs. на весь сайт).

### Базовая инициализация окружения

Класс `Annotator` является точкой входа для всех операций с аннотациями:

```java
// placeholder for Annotator initialization
```

**Важно**: Используйте try‑with‑resources или явно вызывайте `close()` у `Annotator`, чтобы избежать утечек памяти, особенно в длительно работающих сервисах.

## Как создать полилинейную аннотацию с использованием pdf annotation library java?

`PolylineAnnotation` представляет собой многосегментную линию, геометрия которой определяется строкой SVG‑пути.

Загрузите целевой PDF, создайте экземпляр `PolylineAnnotation`, задайте его визуальные свойства, прикрепите любые ответы‑комментарии и затем сохраните документ. Этот сквозной процесс требует лишь трёх вызовов API и выполняется менее чем за секунду для типичных 10‑страничных файлов, эффективно обрабатывая их.

### Определение

`PolylineAnnotation` — класс GroupDocs.Annotation, представляющий многосегментную линию, геометрия которой определяется строкой SVG‑пути. Он наследует общие свойства аннотации, такие как цвет, прозрачность и расположение на странице.

### Пошаговое руководство

1. **Создать коллекцию ответов‑аннотаций** — это предоставляет рецензентам место для добавления комментариев.  
2. **Организовать ответы** в список, на который будет ссылаться аннотация.  
3. **Настроить полилинию** — задать ограничивающий прямоугольник, цвет пера, прозрачность и, что самое важное, `SVGPath`, который рисует линию.  
4. **Добавить аннотацию в документ** через `annotator.addAnnotation(polyline)`.  
5. **Сохранить и очистить** — сохранить PDF и освободить экземпляр `Annotator`.

Ниже приведены заполнители, указывающие, где обычно вставляются реальные фрагменты Java:

```text
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
```

```text
```java
import com.groupdocs.annotation.Annotator;

// Initialize Annotator with your document
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```
```

```text
```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;

// Create reply instances with comments
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());
```
```

```text
```java
import java.util.ArrayList;
import java.util.List;

// Add replies to a list
List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```
```

```text
```java
import com.groupdocs.annotation.models.PenStyle;
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.annotationmodels.PolylineAnnotation;

// Initialize polyline annotation
PolylineAnnotation polyline = new PolylineAnnotation();
polyline.setBox(new Rectangle(250, 35, 102, 12)); // Position and size
polyline.setMessage("This is a polyline annotation"); // Annotation message
polyline.setOpacity(0.7); // Opacity (0-1)
polyline.setPageNumber(0); // Page index (0-based)
polyline.setPenColor(65535); // Color in ARGB format
polyline.setPenStyle(PenStyle.DOT); // Pen style options
polyline.setPenWidth((byte) 3); // Pen width in pixels

// Associate replies and define the path
polyline.setReplies(replies);
polyline.setSvgPath("M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793...");
```
```

```text
```java
// Add the annotation using Annotator
annotator.add(polyline);
```
```

```text
```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/Annotated.pdf";
annotator.save(outputPath); // Save annotated document

// Dispose of annotator resources
annotator.dispose();
```
```

## Работа с SVG‑путями

Строка SVG‑пути определяет точную форму полилинии. Она использует компактный язык команд, который pdf annotation library java интерпретирует для рисования линий.

### Основные команды пути

- **M** — перемещение к (начальная точка)  
- **L** — линия к (абсолютные координаты)  
- **l** — линия к (относительные координаты)  

Простой L‑образный путь выглядит так:

```text
```
M10,10 L50,10 L50,50
```
```

### Программная генерация путей

Когда необходимо построить пути из точек, предоставленных пользователем, сгенерируйте строку SVG в Java:

```text
```java
public String generatePolylinePath(Point[] points) {
    if (points.length == 0) return "";
    
    StringBuilder path = new StringBuilder();
    path.append("M").append(points[0].x).append(",").append(points[0].y);
    
    for (int i = 1; i < points.length; i++) {
        path.append("L").append(points[i].x).append(",").append(points[i].y);
    }
    
    return path.toString();
}
```
```

Эта техника идеальна для `generate svg path java` сценариев, таких как динамические редакторы диаграмм.

## Реальные примеры использования и приложения

### Техническая документация

```text
```java
// Create annotation for data flow path
PolylineAnnotation dataFlow = new PolylineAnnotation();
dataFlow.setMessage("Data flow from API to Database");
dataFlow.setPenColor(0xFF0000FF); // Blue for data flow
dataFlow.setPenStyle(PenStyle.SOLID);
dataFlow.setPenWidth((byte) 2);
// SVG path would show the actual route through your architecture
```
```

### Образовательные материалы

```text
```java
// Highlight geometric proof steps
PolylineAnnotation proofStep = new PolylineAnnotation();
proofStep.setMessage("Proof step 3: Angle bisector construction");
proofStep.setPenColor(0xFF00FF00); // Green for completed steps
proofStep.setOpacity(0.8); // Slightly transparent to not obscure text
```
```

### Юридический обзор документов

```text
```java
// Connect related contract sections
PolylineAnnotation clauseConnection = new PolylineAnnotation();
clauseConnection.setMessage("This clause relates to section 4.2");
clauseConnection.setPenStyle(PenStyle.DASH); // Dashed for suggestions
clauseConnection.setPenColor(0xFFFF9900); // Orange for attention
```
```

## Интеграция с популярными Java‑фреймворками

### Интеграция Spring boot pdf annotation

Предоставьте создание аннотаций через сервис Spring:

```text
```java
@Service
public class DocumentAnnotationService {
    
    public String addPolylineAnnotation(String documentPath, 
                                       PolylineConfig config) {
        try (Annotator annotator = new Annotator(documentPath)) {
            PolylineAnnotation polyline = createPolylineFromConfig(config);
            annotator.add(polyline);
            
            String outputPath = generateOutputPath(documentPath);
            annotator.save(outputPath);
            return outputPath;
        }
    }
    
    private PolylineAnnotation createPolylineFromConfig(PolylineConfig config) {
        // Implementation details based on your config structure
        // This pattern keeps your annotation logic organized and testable
    }
}
```
```

### Интеграция REST API

Определите конечные точки, принимающие JSON‑полезные нагрузки, описывающие координаты полилиний:

```text
```java
@RestController
@RequestMapping("/api/annotations")
public class AnnotationController {
    
    @Autowired
    private DocumentAnnotationService annotationService;
    
    @PostMapping("/polyline")
    public ResponseEntity<String> addPolylineAnnotation(
            @RequestBody PolylineRequest request) {
        
        try {
            String result = annotationService.addPolylineAnnotation(
                request.getDocumentPath(), 
                request.getConfig()
            );
            return ResponseEntity.ok(result);
        } catch (Exception e) {
            return ResponseEntity.badRequest()
                .body("Error adding annotation: " + e.getMessage());
        }
    }
}
```
```

## Оптимизация производительности и лучшие практики

### Управление памятью

Для сценариев с высокой пропускной способностью переиспользуйте один экземпляр `Annotator` на поток и закрывайте его сразу же:

```text
```java
// Use try-with-resources for automatic cleanup
public void processMultipleDocuments(List<String> documentPaths) {
    for (String path : documentPaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Process document
            addPolylineAnnotations(annotator);
            annotator.save(generateOutputPath(path));
        } // Automatic disposal happens here
    }
}
```
```

### Пакетная обработка

При обработке тысяч PDF‑файлов обрабатывайте их пакетами, чтобы снизить использование кучи:

```text
```java
public void batchAddPolylines(String documentPath, 
                             List<PolylineConfig> configs) {
    try (Annotator annotator = new Annotator(documentPath)) {
        // Add all annotations before saving
        for (PolylineConfig config : configs) {
            PolylineAnnotation polyline = createFromConfig(config);
            annotator.add(polyline);
        }
        // Single save operation is more efficient
        annotator.save(generateOutputPath(documentPath));
    }
}
```
```

### Оптимизация SVG‑пути

Сложные пути могут замедлять рендеринг. Следуйте этим рекомендациям:

1. **Обрезать точность координат** — округлять до двух знаков после запятой.  
2. **Предпочитать относительные команды (`l`)** — они сокращают длину строки до 30 %.  
3. **Группировать похожие аннотации** — применять одинаковый стиль к нескольким полилиниям для повторного использования ресурсов.

```text
```java
// Optimize coordinate precision
public String optimizePath(String svgPath) {
    return svgPath.replaceAll("(\\d+\\.\\d{3})\\d+", "$1");
}
```
```

## Распространённые проблемы и решения

### Проблема 1: аннотация не видна

Типичные причины включают неверный индекс страницы (страницы нумеруются с нуля), координаты SVG за пределами страницы или слишком низкую прозрачность. Скорректируйте номер страницы и проверьте, что SVG‑путь находится внутри прямоугольника страницы.

```text
```java
// Debug your annotation placement
PolylineAnnotation polyline = new PolylineAnnotation();
polyline.setPageNumber(0); // Ensure correct page
polyline.setOpacity(1.0); // Full opacity for testing
polyline.setPenWidth((byte) 5); // Thicker line for visibility

// Log the bounding box to verify coordinates
Rectangle box = polyline.getBox();
System.out.println("Annotation bounds: " + box.getX() + "," + box.getY());
```
```

### Проблема 2: OutOfMemoryError при работе с большими документами

Обрабатывайте большие PDF‑файлы в режиме потоковой передачи и избегайте загрузки всего документа в память:

```text
```java
// Implement proper memory management
public void processLargeDocument(String documentPath) {
    // Process in smaller batches
    int maxAnnotationsPerBatch = 50;
    List<PolylineConfig> allConfigs = getAnnotationConfigs();
    
    for (int i = 0; i < allConfigs.size(); i += maxAnnotationsPerBatch) {
        try (Annotator annotator = new Annotator(documentPath)) {
            int end = Math.min(i + maxAnnotationsPerBatch, allConfigs.size());
            List<PolylineConfig> batch = allConfigs.subList(i, end);
            
            processBatch(annotator, batch);
            annotator.save(generateBatchOutputPath(documentPath, i));
        }
        // Force garbage collection between batches if needed
        System.gc();
    }
}
```
```

### Проблема 3: Неверный формат SVG‑пути

Убедитесь, что путь начинается с команды перемещения (`M`) и все числовые значения являются корректными double.

```text
```java
// Validate SVG path before using
public boolean isValidSVGPath(String path) {
    // Basic validation - should start with M or m
    if (!path.matches("^[Mm]\\d+.*")) {
        return false;
    }
    
    // Additional validation logic here
    return true;
}

// Use validated paths only
if (isValidSVGPath(pathString)) {
    polyline.setSvgPath(pathString);
} else {
    throw new IllegalArgumentException("Invalid SVG path: " + pathString);
}
```
```

### Проблема 4: Ошибка проверки лицензии

Разместите файл `GroupDocs.Annotation.lic` в classpath или задайте лицензию программно при запуске приложения.

```text
```java
// Proper license initialization
public class AnnotationConfig {
    
    @PostConstruct
    public void initializeLicense() {
        try {
            // Load license from classpath or file system
            String licensePath = getClass().getClassLoader()
                .getResource("GroupDocs.Annotation.lic").getPath();
            
            License license = new License();
            license.setLicense(licensePath);
            
            System.out.println("GroupDocs.Annotation license loaded successfully");
        } catch (Exception e) {
            System.err.println("Failed to load license: " + e.getMessage());
            // Handle license failure appropriately
        }
    }
}
```
```

## Продвинутые техники настройки

### Динамическое назначение цвета

`ColorHelper` предоставляет вспомогательные методы для сопоставления категорий аннотаций с ARGB‑значениями цвета.

```text
```java
public class ColorHelper {
    private static final Map<String, Integer> CATEGORY_COLORS = Map.of(
        "error", 0xFFFF0000,      // Red
        "warning", 0xFFFF9900,    // Orange  
        "info", 0xFF0099FF,       // Blue
        "success", 0xFF00FF00     // Green
    );
    
    public static int getColorForCategory(String category) {
        return CATEGORY_COLORS.getOrDefault(category, 0xFF000000); // Default black
    }
}
```
```

### Интерактивные аннотации с пользовательскими свойствами

Добавьте метаданные, такие как `authorId` или `timestamp`, чтобы обогатить полезную нагрузку аннотации:

```text
```java
// Create custom annotation with metadata
PolylineAnnotation polyline = new PolylineAnnotation();
polyline.setMessage("Process Flow: " + processName);

// Add custom properties (stored in message or replies)
Reply metadataReply = new Reply();
metadataReply.setComment("metadata:{\"processId\":\"12345\",\"priority\":\"high\"}");
polyline.setReplies(Arrays.asList(metadataReply));
```
```

## Тестирование вашей реализации

### Модульное тестирование

Замокайте `Annotator` и проверьте, что `addAnnotation` получает правильно сконфигурированный `PolylineAnnotation`.

```text
```java
@Test
public void testPolylineAnnotationCreation() {
    // Arrange
    String documentPath = "test-documents/sample.pdf";
    PolylineConfig config = new PolylineConfig();
    config.setMessage("Test polyline");
    config.setPath("M10,10L50,50");
    
    // Act
    try (Annotator annotator = new Annotator(documentPath)) {
        PolylineAnnotation polyline = createPolylineFromConfig(config);
        annotator.add(polyline);
        
        // Assert
        assertNotNull(polyline);
        assertEquals("Test polyline", polyline.getMessage());
        assertEquals(0.7, polyline.getOpacity(), 0.01);
    }
}
```
```

### Интеграционное тестирование

Запустите сквозные тесты на реальных PDF‑файлах, чтобы убедиться, что полилиния отображается как ожидается во множестве просмотрщиков.

```text
```java
@Test
public void testEndToEndAnnotationWorkflow() {
    // Test complete process from document input to annotated output
    String inputPath = "test-documents/input.pdf";
    String outputPath = "test-output/annotated.pdf";
    
    DocumentAnnotationService service = new DocumentAnnotationService();
    String result = service.addPolylineAnnotation(inputPath, createTestConfig());
    
    // Verify output file exists and contains annotations
    assertTrue(Files.exists(Paths.get(result)));
    
    // Additional verification logic
    verifyAnnotationExists(result);
}
```
```

## Заключение

Теперь у вас есть надёжный, готовый к продакшн подход к использованию **pdf annotation library java** для создания интерактивных полилинейных PDF. Решение масштабируется от прототипа с одним документом до пакетной обработки уровня предприятия, чисто интегрируется со Spring Boot и предоставляет полный контроль над геометрией, основанной на SVG.

## Следующие шаги

- Исследовать **area annotations** для выделения неправильных областей.  
- Добавить **arrow annotations** для указания направления.  
- Реализовать **real‑time editing**, раскрывая метаданные аннотаций через WebSocket‑конечные точки.  
- Ознакомиться с [документацией](https://docs.groupdocs.com/annotation/java/) GroupDocs.Annotation для более глубоких возможностей API.

## Ресурсы и дополнительное чтение

- **Документация**: [GroupDocs.Annotation for Java Documentation](https://docs.groupdocs.com/annotation/java/)  
- **Справочник API**: [Complete API Reference](https://reference.groupdocs.com/annotation/java/)  
- **Примерные проекты**: Просмотрите репозиторий GroupDocs на GitHub для полноценных примеров приложений.  
- **Форум поддержки**: Задавайте вопросы и делитесь решениями с сообществом и экспертами GroupDocs.  
- **Варианты покупки и лицензирования**: Ознакомьтесь с [Purchase and licensing options](https://purchase.groupdocs.com/buy) для деталей.

**Последнее обновление:** 2026-09-10  
**Тестировано с:** GroupDocs.Annotation 25.2 for Java  
**Автор:** GroupDocs  

## Связанные руководства

- [Add PDF Annotation Java – Complete GroupDocs Guide](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)  
- [Load PDF Java with GroupDocs Annotation: Document Loading Guide](/annotation/java/document-loading/)  
- [Groupdocs Java Watermark Annotations Pdf Guide](/annotation/java/graphical-annotations/groupdocs-java-watermark-annotations-pdf-guide/)