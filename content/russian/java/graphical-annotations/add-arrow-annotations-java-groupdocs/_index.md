---
categories:
- Java Development
date: '2026-02-21'
description: Узнайте, как добавить стрелку в PDF с помощью GroupDocs.Annotation для
  Java. Пошаговое руководство с кодом, лучшими практиками и устранением неполадок.
keywords: Java PDF arrow annotations, GroupDocs annotation tutorial, PDF annotation
  Java library, Java document annotation, PDF collaboration tools Java
lastmod: '2026-02-21'
linktitle: Java PDF Arrow Annotations Guide
tags:
- pdf-annotations
- java-tutorial
- document-processing
- groupdocs
title: Как добавить стрелку в PDF с помощью Java – Полный учебник и лучшие практики
type: docs
url: /ru/java/graphical-annotations/add-arrow-annotations-java-groupdocs/
weight: 1
---

.

# Java PDF Аннотации со стрелками - Полный учебник и лучшие практики (2025)

## Введение

Когда‑то вам приходилось пытаться заставить команду сосредоточиться на конкретных разделах PDF‑документа во время обзоров? Вы не одиноки. Будь то техническая документация, юридические контракты или спецификации проекта, указание точных областей для обсуждения может быть раздражающим без подходящих инструментов.

**Вот решение**: Java PDF аннотации со стрелками с использованием GroupDocs.Annotation API. Этот мощный подход позволяет программно **добавлять стрелку в pdf** файлы, делая совместную работу плавной и профессиональной.

В этом всестороннем руководстве вы узнаете, как реализовать аннотации‑стрелки, которые действительно работают в производственной среде. Мы охватим всё — от базовой настройки до продвинутой кастомизации, а также реальные сценарии, с которыми вы столкнётесь (и как их решить).

**Что делает этот учебник особенным?** Вы получите практические инсайты от человека, который внедрял это в корпоративных приложениях, включая подводные камни, о которых документация обычно не говорит.

## Быстрые ответы
- **Какая библиотека позволяет добавить стрелку в pdf на Java?** GroupDocs.Annotation для Java.  
- **Нужна ли лицензия для продакшна?** Да, коммерческая лицензия убирает водяные знаки.  
- **Какая версия Java рекомендуется?** JDK 11 обеспечивает лучшую производительность.  
- **Можно ли добавить несколько стрелок в один документ?** Абсолютно — просто создайте несколько объектов ArrowAnnotation.  
- **Поддерживается ли пакетная обработка?** Да, обрабатывайте документы в циклах и освобождайте объекты Annotator.

## Что такое добавить стрелку в pdf?
Добавление аннотации‑стрелки означает программное рисование направляющего маркера на странице PDF. Это помогает рецензентам указывать разделы, выделять проблемы или вести читателя через рабочий процесс без ручного редактирования файла.

## Почему стоит выбрать GroupDocs.Annotation для Java PDF Аннотаций со стрелками?

Прежде чем погрузиться в код, давайте разберём «слона в комнате»: почему использовать GroupDocs, когда существуют другие библиотеки аннотаций PDF?

**Честное сравнение:**

- **iText**: Хорошо подходит для базовых аннотаций, но возможности кастомизации стрелок ограничены  
- **PDFBox**: Бесплатно и мощно, но требует больше шаблонного кода  
- **GroupDocs.Annotation**: Лучший баланс функций и простоты использования (хотя это коммерческий продукт)

**GroupDocs выделяется, когда вам нужны:**

- Несколько типов аннотаций в одном проекте  
- Поддержка уровня предприятия и обширная документация  
- Быстрая реализация с минимальным количеством кода  
- Встроенные функции совместной работы (например, ответы)

**Честное предупреждение**: Продукт не бесплатный. Но если вы создаёте коммерческое приложение, где важна скорость выхода на рынок, инвестиции обычно окупаются за счёт сокращения времени разработки.

## Предварительные требования — Что действительно нужно

Давайте практично разберём, что требуется перед началом. Я видел, как слишком многие разработчики бросаются в работу без надлежащей настройки и теряют часы на проблемы с конфигурацией.

### Необходимые библиотеки и зависимости

Сначала добавьте GroupDocs.Annotation в ваш Maven‑проект. Ниже представлена конфигурация, которая действительно работает (я тестировал её в нескольких проектах):

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

**Совет профессионала**: Всегда проверяйте наличие последней версии на странице релизов. Версия 25.2 актуальна на момент написания, но более новые версии часто включают важные исправления ошибок.

### Настройка окружения, не вызывающая головных болей

Вот что нужно для комфортной разработки:

- **JDK 8 или новее** (рекомендую JDK 11 для лучшей производительности)  
- **Maven 3.6+** (старые версии иногда дают проблемы с разрешением зависимостей)  
- **IDE**: IntelliJ IDEA или Eclipse (VS Code тоже подойдёт, но отладка проще в специализированных Java‑IDE)  
- **Память**: Убедитесь, что у JVM выделено минимум 2 ГБ кучи для обработки больших PDF‑файлов  

### Требования к знаниям (Будьте честны с собой)

Вы должны уверенно разбираться в:

- Основах Java (коллекции, обработка исключений)  
- Управлении зависимостями Maven  
- Операциях ввода‑вывода файлов в Java  

Если вы новичок в каком‑либо из этих пунктов, это нормально — просто планируйте потратить дополнительное время на изучение.

## Настройка GroupDocs.Annotation — Правильный способ

Вот как правильно настроить GroupDocs.Annotation, включая шаги, которые часто упускаются в официальной документации.

### Шаг 1: Конфигурация Maven (с устранением неполадок)

Добавьте репозиторий и зависимость, указанные выше. Если столкнётесь с проблемами разрешения зависимостей (это бывает), попробуйте добавить следующее в ваш `pom.xml`:

```xml
<properties>
    <maven.compiler.source>11</maven.compiler.source>
    <maven.compiler.target>11</maven.compiler.target>
</properties>
```

### Шаг 2: Настройка лицензии (критично для продакшна)

Для разработки и тестирования:
```java
// For evaluation purposes
License license = new License();
// license.setLicense("path/to/license.lic"); // Comment this out for trial
```

**Реальная проверка**: Пробная версия добавляет водяные знаки в ваш вывод. Для продакшна понадобится полноценная лицензия от [GroupDocs](https://purchase.groupdocs.com/temporary-license/).

### Шаг 3: Базовый шаблон инициализации

Всегда используйте такой шаблон для инициализации аннотатора:

```java
Annotator annotator = null;
try {
    annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
    // Your annotation code here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

**Зачем блок try‑finally?** Поверьте мне — объекты GroupDocs требуют корректного освобождения, иначе возникнут утечки памяти, особенно при обработке множества документов.

## Полное руководство по реализации — От нуля до продакшна

Соберём реальную реализацию аннотации‑стрелки, готовую к использованию в продакшене.

### Понимание аннотаций‑стрелок в контексте

Аннотации‑стрелки — это не просто декоративные элементы, а инструменты коммуникации. В рабочих процессах с документами они обычно служат следующим целям:

1. **Обратная связь при ревью** — «Этот раздел требует исправления»  
2. **Ссылка на материал** — «Смотрите связанный контент здесь»  
3. **Навигация процесса** — «Начните ревью с этой точки»  
4. **Выделение проблем** — «Проблема обнаружена в этой области»

Понимание контекста помогает проектировать более эффективные системы аннотаций.

### Шаг 1: Создание ответов к аннотациям (умный подход)

Ответы делают ваши аннотации интерактивными. Как создать осмысленные ответы:

```java
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

**Лучший практик**: Включайте информацию о пользователе в ответы для лучшего отслеживания совместной работы. В продакшне обычно берёте эти данные из системы управления пользователями.

### Шаг 2: Создание аннотации‑стрелки (с учётом реальных условий)

Вот ядро реализации с пояснениями к каждому параметру:

```java
ArrowAnnotation arrow = new ArrowAnnotation();
arrow.setBox(new Rectangle(100, 100, 100, 100)); // Position and size
arrow.setCreatedOn(Calendar.getInstance().getTime()); // Creation time
arrow.setMessage("This is an arrow annotation"); // Annotation message
arrow.setOpacity(0.7); // Opacity level
arrow.setPageNumber(0); // Page number
arrow.setPenColor(65535); // ARGB pen color
arrow.setPenStyle(PenStyle.DOT); // Pen style
arrow.setPenWidth((byte) 3); // Arrow line width
arrow.setReplies(replies); // Attach replies
```

**Разберём сложные части:**

- **Координаты прямоугольника**: (x, y, width, height), где x,y — координаты левого верхнего угла  
- **PenColor**: задаётся в формате ARGB. 65535 — ярко‑синий. Для пользовательских цветов используйте онлайн‑конвертеры  
- **PenStyle**: варианты DOT, DASH, SOLID, DASHDOT, DASHDOTDOT  
- **Opacity**: от 0.0 (прозрачный) до 1.0 (непрозрачный). 0.7 обычно идеально для видимости без излишней навязчивости  

### Шаг 3: Добавление и сохранение (с обработкой ошибок)

Продакшн‑готовый способ добавить аннотации:

```java
try {
    annotator.add(arrow);
    annotator.save("YOUR_OUTPUT_DIRECTORY/output.pdf");
    System.out.println("Arrow annotation added successfully!");
} catch (Exception e) {
    System.err.println("Failed to add annotation: " + e.getMessage());
    // Log the full stack trace in production
    e.printStackTrace();
} finally {
    annotator.dispose();
}
```

**Критический момент**: Всегда обрабатывайте исключения при работе с файловой системой. PDF‑файлы могут быть повреждены, пути недоступны, а права доступа — проблемой.

## Распространённые подводные камни и как их избежать

После внедрения в нескольких проектах я выявил типичные проблемы, с которыми вы, скорее всего, столкнётесь.

### Проблема 1: Координаты не соответствуют ожидаемому положению

**Суть**: Стрелка появляется не там, где должна, на PDF.

**Решение**: Система координат PDF начинается с нижнего левого угла, тогда как большинство библиотек аннотаций используют верхний левый. GroupDocs автоматически конвертирует, но иногда требуется корректировка в зависимости от особенностей вашего PDF.

```java
// If arrows appear in wrong positions, try adjusting the Y coordinate
int adjustedY = pageHeight - originalY - annotationHeight;
arrow.setBox(new Rectangle(x, adjustedY, width, height));
```

### Проблема 2: Аннотации исчезают после сохранения

**Суть**: Аннотации видны во время обработки, но исчезают в финальном PDF.

**Решение**: Чаще всего это проблема лицензии. Убедитесь, что лицензия загружена корректно:

```java
License license = new License();
try {
    license.setLicense("GroupDocs.Annotation.lic");
} catch (Exception e) {
    System.out.println("License not found, using trial mode");
}
```

### Проблема 3: Утечки памяти при пакетной обработке

**Суть**: Приложение выходит из памяти при обработке множества документов.

**Решение**: Всегда освобождайте объекты аннотатора и рассматривайте обработку документов небольшими партиями:

```java
for (String documentPath : documentPaths) {
    Annotator annotator = null;
    try {
        annotator = new Annotator(documentPath);
        // Process document
    } finally {
        if (annotator != null) {
            annotator.dispose();
        }
    }
    
    // Force garbage collection every 10 documents
    if (processedCount % 10 == 0) {
        System.gc();
    }
}
```

## Продвинутые техники кастомизации

### Динамическое позиционирование стрелок

Для интерактивных приложений может потребоваться позиционировать стрелки на основе ввода пользователя:

```java
public ArrowAnnotation createArrowAt(int x, int y, String message) {
    ArrowAnnotation arrow = new ArrowAnnotation();
    
    // Create arrow pointing to specific coordinates
    int arrowLength = 50;
    arrow.setBox(new Rectangle(x - arrowLength, y - arrowLength, arrowLength, arrowLength));
    arrow.setMessage(message);
    arrow.setOpacity(0.8);
    arrow.setPenColor(0xFF0000); // Red color
    arrow.setPenStyle(PenStyle.SOLID);
    arrow.setPenWidth((byte) 2);
    
    return arrow;
}
```

### Стилизация стрелок под разные сценарии использования

```java
// Error highlighting (red, thick, solid)
public ArrowAnnotation createErrorArrow() {
    ArrowAnnotation arrow = new ArrowAnnotation();
    arrow.setPenColor(0xFF0000); // Red
    arrow.setPenWidth((byte) 4);
    arrow.setPenStyle(PenStyle.SOLID);
    arrow.setOpacity(0.9);
    return arrow;
}

// Suggestion arrows (blue, thin, dashed)
public ArrowAnnotation createSuggestionArrow() {
    ArrowAnnotation arrow = new ArrowAnnotation();
    arrow.setPenColor(0x0000FF); // Blue
    arrow.setPenWidth((byte) 2);
    arrow.setPenStyle(PenStyle.DASH);
    arrow.setOpacity(0.6);
    return arrow;
}
```

## Реальные сценарии внедрения

### Сценарий 1: Система рецензирования документов

Вы создаёте систему рецензирования, где несколько пользователей могут оставлять обратную связь:

```java
public class DocumentReviewSystem {
    public void addReviewArrow(String documentPath, int x, int y, 
                              String reviewComment, String reviewerName) {
        Annotator annotator = new Annotator(documentPath);
        
        ArrowAnnotation arrow = new ArrowAnnotation();
        arrow.setBox(new Rectangle(x, y, 50, 50));
        arrow.setMessage("Review by " + reviewerName);
        
        // Add reviewer's comment as reply
        Reply review = new Reply();
        review.setComment(reviewComment);
        review.setUser(new User(reviewerName));
        review.setRepliedOn(new Date());
        
        arrow.setReplies(Arrays.asList(review));
        
        annotator.add(arrow);
        annotator.save(documentPath.replace(".pdf", "_reviewed.pdf"));
        annotator.dispose();
    }
}
```

### Сценарий 2: Автоматическое обнаружение проблем

Интеграция с инструментами анализа для автоматического выделения потенциальных проблем:

```java
public void highlightDetectedIssues(String documentPath, List<Issue> issues) {
    Annotator annotator = new Annotator(documentPath);
    
    for (Issue issue : issues) {
        ArrowAnnotation arrow = createArrowForIssue(issue);
        annotator.add(arrow);
    }
    
    annotator.save(documentPath.replace(".pdf", "_issues_highlighted.pdf"));
    annotator.dispose();
}

private ArrowAnnotation createArrowForIssue(Issue issue) {
    ArrowAnnotation arrow = new ArrowAnnotation();
    arrow.setBox(new Rectangle(issue.getX(), issue.getY(), 40, 40));
    arrow.setMessage("Issue detected: " + issue.getType());
    
    // Color‑code by severity
    switch (issue.getSeverity()) {
        case HIGH:
            arrow.setPenColor(0xFF0000); // Red
            break;
        case MEDIUM:
            arrow.setPenColor(0xFFA500); // Orange
            break;
        case LOW:
            arrow.setPenColor(0xFFFF00); // Yellow
            break;
    }
    
    return arrow;
}
```

## Советы по оптимизации производительности

### Лучшие практики управления памятью

При обработке больших документов или множества файлов:

1. **Используйте шаблон try‑with‑resources** (если ваша версия Java его поддерживает):
```java
try (Annotator annotator = new Annotator("document.pdf")) {
    // Your annotation code
} // Automatically disposed
```

2. **Обрабатывайте пачками**:
```java
public void processBatch(List<String> documents, int batchSize) {
    for (int i = 0; i < documents.size(); i += batchSize) {
        List<String> batch = documents.subList(i, 
            Math.min(i + batchSize, documents.size()));
        
        processBatchInternal(batch);
        
        // Allow GC between batches
        System.gc();
        Thread.sleep(100);
    }
}
```

3. **Отслеживайте потребление памяти**:
```java
Runtime runtime = Runtime.getRuntime();
long memoryBefore = runtime.totalMemory() - runtime.freeMemory();

// Your annotation processing

long memoryAfter = runtime.totalMemory() - runtime.freeMemory();
System.out.println("Memory used: " + (memoryAfter - memoryBefore) + " bytes");
```

### Соображения по производительности CPU

- Избегайте ненужного создания объектов в циклах  
- Переиспользуйте объекты цвета и стиля, когда это возможно  
- Рассмотрите параллельную обработку независимых документов (но следите за потреблением памяти)

## Руководство по устранению неполадок — Решения реальных проблем

### Проблема: Аннотации не видны в Adobe Reader

**Симптомы**: Аннотации отображаются в вашем приложении, но не в Adobe Reader или других PDF‑просмотрщиках.

**Решения**:

1. Убедитесь, что сохраняете с соблюдением правильных PDF‑стандартов:
```java
// Try different save options if available
SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationType(AnnotationType.All);
annotator.save(outputPath, saveOptions);
```

2. Проверьте совместимость версии PDF — старые версии могут не поддерживать все возможности аннотаций.

### Проблема: Плохая производительность с большими PDF

**Симптомы**: Приложение замедляется или перестаёт реагировать при работе с большими документами.

**Решения**:

1. **Обрабатывайте страницы по отдельности**, а не весь документ целиком:
```java
// Process specific pages
LoadOptions loadOptions = new LoadOptions();
loadOptions.setLoadCharts(false); // Skip charts if not needed
Annotator annotator = new Annotator(documentPath, loadOptions);
```

2. **Используйте потоковую обработку**, когда работаете с очень большими файлами.  

3. **Увеличьте размер кучи JVM**:
```bash
java -Xmx4g -jar your-application.jar
```

### Проблема: Проблемы с отображением цветов

**Симптомы**: Цвета выглядят иначе, чем ожидалось, в финальном PDF.

**Решение**: Применяйте корректные определения цветового пространства:
```java
// Use hex values for consistent colors
int red = 0xFFFF0000;    // ARGB format
int blue = 0xFF0000FF;
int green = 0xFF00FF00;

// Or convert from RGB
public int rgbToArgb(int r, int g, int b) {
    return (0xFF << 24) | (r << 16) | (g << 8) | b;
}
```

## Тестирование вашей реализации

### Юнит‑тесты для аннотаций‑стрелок

Практический пример структуры теста:

```java
@Test
public void testArrowAnnotationCreation() {
    // Arrange
    String inputPath = "test-documents/sample.pdf";
    String outputPath = "test-output/annotated.pdf";
    
    // Act
    Annotator annotator = new Annotator(inputPath);
    ArrowAnnotation arrow = new ArrowAnnotation();
    arrow.setBox(new Rectangle(100, 100, 50, 50));
    arrow.setMessage("Test annotation");
    
    annotator.add(arrow);
    annotator.save(outputPath);
    annotator.dispose();
    
    // Assert
    assertTrue("Output file should exist", new File(outputPath).exists());
    
    // Verify annotation was added
    Annotator verifyAnnotator = new Annotator(outputPath);
    List<AnnotationInfo> annotations = verifyAnnotator.get();
    assertEquals("Should have one annotation", 1, annotations.size());
    verifyAnnotator.dispose();
}
```

### Интеграционные тесты

Тестируйте с различными типами и размерами PDF, чтобы убедиться, что реализация работает во всех сценариях.

## Заключение

Теперь у вас есть полный набор инструментов для реализации Java PDF аннотаций‑стрелок с помощью GroupDocs.Annotation. Это не просто добавление стрелок в PDF — это построение надёжных функций совместной работы с документами, которые действительно работают в продакшене.

**Ключевые выводы из руководства:**

- Всегда корректно освобождайте ресурсы (используйте блоки try‑finally)  
- Тестируйте с разными типами и размерами PDF  
- Планируйте управление памятью при пакетной обработке  
- Реализуйте надёжную обработку ошибок для продакшна  
- Подбирайте стиль аннотаций в соответствии с их назначением  

**Ваши дальнейшие шаги**: Начните с простого прототипа, используя базовую реализацию, а затем постепенно добавляйте продвинутые функции, такие как динамическое позиционирование и кастомный стиль, по мере роста требований.

**Готовы идти дальше?** Исследуйте другие возможности GroupDocs.Annotation, такие как текстовые аннотации, областные аннотации и водяные знаки. Принципы, изученные здесь, применимы ко всем типам аннотаций.

## Часто задаваемые вопросы

**В: Можно ли добавить аннотации‑стрелки в PDF, защищённые паролем?**  
О: Да, но необходимо передать пароль при создании Annotator:
```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("your-password");
Annotator annotator = new Annotator("protected.pdf", loadOptions);
```

**В: Как эффективно пакетно обрабатывать несколько документов?**  
О: Обрабатывайте документы небольшими партиями и корректно освобождайте ресурсы:
```java
for (String doc : documents) {
    try (Annotator annotator = new Annotator(doc)) {
        // Add annotations
        annotator.save(doc.replace(".pdf", "_annotated.pdf"));
    }
    if (processedCount % 10 == 0) {
        System.gc(); // Encourage garbage collection
    }
}
```

**В: Каково максимальное количество аннотаций в документе?**  
О: Жёсткого ограничения от GroupDocs нет, но практические лимиты зависят от памяти, возможностей PDF‑просмотрщика и требований к производительности. При большом количестве (1000 +) применяйте техники оптимизации производительности, описанные выше.

**В: Можно ли кастомизировать форму стрелки за пределами стандартных вариантов?**  
О: GroupDocs.Annotation предоставляет стандартные формы стрелок. Для пользовательских форм может потребоваться использовать областные аннотации, комбинировать несколько простых аннотаций или перейти к более специализированной графической библиотеке.

**В: Как работать с разными системами координат PDF?**  
О: GroupDocs обычно автоматически конвертирует координаты. Если возникают проблемы:
```java
// Get page info for coordinate calculations
PageInfo pageInfo = annotator.getDocument().getPages().get(pageNumber);
int pageHeight = pageInfo.getHeight();

// Adjust Y coordinate if needed
int adjustedY = pageHeight - originalY;
```

**В: Какова стоимость лицензии для продакшна?**  
О: GroupDocs предлагает различные модели лицензирования (Developer, Site, OEM). Актуальные цены смотрите на [странице ценообразования GroupDocs](https://purchase.groupdocs.com/buy).

**В: Как интегрировать это в приложения Spring Boot?**  
О: Создайте сервисный класс для операций аннотирования:
```java
@Service
public class AnnotationService {
    public void addArrowAnnotation(String inputPath, String outputPath, 
                                 int x, int y, String message) {
        try (Annotator annotator = new Annotator(inputPath)) {
            ArrowAnnotation arrow = new ArrowAnnotation();
            arrow.setBox(new Rectangle(x, y, 50, 50));
            arrow.setMessage(message);
            
            annotator.add(arrow);
            annotator.save(outputPath);
        }
    }
}
```

**В: Можно ли извлекать существующие аннотации‑стрелки из PDF?**  
О: Да, используйте метод `get()` для получения уже существующих аннотаций:
```java
Annotator annotator = new Annotator("document.pdf");
List<AnnotationInfo> annotations = annotator.get();

for (AnnotationInfo annotation : annotations) {
    if (annotation instanceof ArrowAnnotation) {
        ArrowAnnotation arrow = (ArrowAnnotation) annotation;
        System.out.println("Arrow message: " + arrow.getMessage());
    }
}
```

## Дополнительные ресурсы

- **Документация**: [GroupDocs.Annotation for Java Documentation](https://docs.groupdocs.com/annotation/java/)  
- **Справочник API**: [Complete API Reference](https://reference.groupdocs.com/annotation/java/)  
- **Скачать последнюю версию**: [GroupDocs Releases](https://releases.groupdocs.com/annotation/java/)  
- **Приобрести лицензию**: [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **Бесплатная пробная версия**: [Download Free Trial](https://releases.groupdocs.com/annotation/java/)  
- **Временная лицензия**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Сообщество**: [GroupDocs Forum](https://forum.groupdocs.com/c/annotation/)  
- **Профессиональная поддержка**: Доступна при платных лицензиях для приоритетной помощи  

---

**Последнее обновление:** 2026-02-21  
**Тестировано с:** GroupDocs.Annotation 25.2 для Java  
**Автор:** GroupDocs