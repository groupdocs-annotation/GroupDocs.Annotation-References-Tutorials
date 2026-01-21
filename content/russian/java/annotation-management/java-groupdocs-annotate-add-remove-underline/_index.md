---
categories:
- Java Development
date: '2025-12-21'
description: Узнайте, как создавать чистые PDF‑файлы на Java и аннотировать PDF в
  Java с помощью GroupDocs.Annotation, с полными примерами кода и советами по устранению
  неполадок.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2025-12-21'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'Создание чистого PDF на Java - подчеркивание аннотаций с помощью GroupDocs'
type: docs
url: /ru/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Создание чистого PDF Java: подчёркивающие аннотации с GroupDocs

## Введение

Столкнулись с проблемами управления документами и совместной работы в ваших Java‑приложениях? Вы не одиноки. Многие разработчики сталкиваются с задачей реализации надёжных функций аннотирования документов, которые работают стабильно с различными форматами файлов.

В этом руководстве вы **создадите чистые PDF Java** файлы и узнаете, как **аннотировать PDF в Java** с помощью GroupDocs.Annotation. К концу урока вы точно будете знать, как добавить подчёркивающие аннотации с комментариями, удалить существующие аннотации и без проблем интегрировать эти возможности в свои проекты.

**Что вы освоите в этом руководстве:**
- Настройка GroupDocs.Annotation в вашем Java‑проекте (правильным способом)  
- Добавление подчёркивающих аннотаций с пользовательскими комментариями и стилем  
- Удаление всех аннотаций для создания чистых версий документов  
- Устранение распространённых проблем, с которыми сталкиваются разработчики  
- Оптимизация производительности для продакшн‑приложений  

Независимо от того, создаёте ли вы систему рецензирования документов, образовательную платформу или инструмент совместного редактирования, этот туториал покрывает всё необходимое с практическими проверенными примерами кода.

## Быстрые ответы
- **Как добавить подчёркивающую аннотацию?** Используйте `UnderlineAnnotation` и `annotator.add()`, затем сохраните документ.  
- **Как создать чистый PDF Java файл?** Загрузите аннотированный файл, установите `AnnotationType.NONE` в `SaveOptions` и сохраните новую копию.  
- **Какие библиотеки требуются?** GroupDocs.Annotation v25.2 (или новее) и её Maven‑репозиторий.  
- **Нужна ли лицензия для продакшна?** Да — примените действующую лицензию GroupDocs, чтобы избавиться от водяных знаков.  
- **Можно ли эффективно обрабатывать несколько документов?** Оберните каждый `Annotator` в блок `try‑with‑resources` и освобождайте ресурсы после обработки каждого файла.

## Как создать чистые PDF Java файлы
Создание чистого PDF Java файла означает генерацию версии документа **без каких‑либо аннотаций**, при этом сохраняется оригинальное содержимое. Это полезно для финального распространения, архивирования или когда необходимо поделиться «чистой» копией после цикла рецензирования.

GroupDocs.Annotation делает это простым: загрузите аннотированный файл, настройте `SaveOptions` так, чтобы исключить все типы аннотаций, и сохраните результат. Шаги показаны ниже в разделе **Удаление аннотаций**.

## Как аннотировать PDF в Java с помощью GroupDocs
GroupDocs.Annotation предоставляет богатый API для **аннотировать PDF в Java**. Он поддерживает широкий спектр типов аннотаций, включая выделения, штампы и подчёркивания. В этом руководстве мы сосредоточимся на подчёркивающих аннотациях, поскольку они часто используются для акцентирования текста с возможностью добавления цепочки комментариев.

## Предварительные требования и настройка окружения

### Что понадобится перед началом

**Требования к среде разработки:**
- Java Development Kit (JDK) 8 или выше (рекомендовано JDK 11+)  
- Maven 3.6+ или Gradle 6.0+ для управления зависимостями  
- IDE, например IntelliJ IDEA, Eclipse или VS Code с Java‑расширениями  
- Не менее 2 ГБ свободной оперативной памяти (обработка документов может быть ресурсоёмкой)

**Базовые знания:**
Вы должны уверенно владеть базовыми концепциями Java — инициализацией объектов, вызовами методов и зависимостями Maven. Предыдущий опыт работы с сторонними библиотеками ускорит освоение.

**Тестовые документы:**
Подготовьте несколько образцов PDF. Текстовые PDF работают лучше всего; отсканированные изображения могут потребовать OCR перед аннотированием.

### Настройка Maven: подключение GroupDocs к проекту

Ниже показано, как правильно сконфигурировать ваш Maven‑проект (многие разработчики сталкиваются с проблемами на первой попытке):

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

**Важно:** Версия 25.2 — последняя стабильная на момент написания. Регулярно проверяйте репозиторий GroupDocs на наличие более новых версий с исправлениями багов и улучшениями производительности.

### Настройка лицензии (не пропустите)

**Для разработки/тестирования:**  
Скачайте бесплатную trial‑версию с сайта GroupDocs. Триал включает все функции, но добавляет водяной знак к обработанным документам.

**Для продакшна:**  
Приобретите лицензию и примените её при запуске приложения. Без действующей лицензии продакшн‑сборки будут ограничены.

## Руководство по реализации: добавление подчёркивающих аннотаций

### Понимание рабочего процесса аннотирования

Прежде чем перейти к коду, рассмотрим четырёхшаговый процесс, происходящий при **аннотировании PDF в Java**:

1. **Загрузка документа** – `Annotator` читает файл в память.  
2. **Создание аннотации** – задаются свойства, такие как позиция, стиль и комментарии.  
3. **Применение аннотации** – библиотека внедряет аннотацию в структуру PDF.  
4. **Сохранение документа** – сохраняется изменённый файл, при желании оригинал остаётся нетронутым.

Процесс не разрушителен; исходный файл остаётся без изменений, если вы его явно не перезапишете.

### Шаг 1: Инициализация Annotator и загрузка документа

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Совет:** Используйте абсолютные пути во время разработки, чтобы избежать ошибок «file not found». В продакшне лучше загружать ресурсы из classpath или облачного хранилища.

### Шаг 2: Создание комментариев и ответов (коллаборативная часть)

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

**Пример из практики:** Рецензенты могут обсуждать конкретный пункт, добавляя вложенные ответы, привязанные к самой аннотации.

### Шаг 3: Определение координат аннотации (правильное позиционирование)

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

**Система координат:**  
- Точки 1 и 2 определяют верхний край подчёркивания.  
- Точки 3 и 4 определяют нижний край.  
- Разница по Y (730 vs 650) контролирует толщину линии.

### Шаг 4: Создание и настройка подчёркивающей аннотации

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Yellow in ARGB format
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**Подсказки по цвету и непрозрачности:**  
- `FontColor` использует ARGB; `65535` (0x00FFFF) даёт ярко‑жёлтый цвет.  
- Для красного используйте `16711680` (0xFF0000); для синего — `255` (0x0000FF).  
- Значения непрозрачности от 0.5 до 0.8 обеспечивают хорошую читаемость без скрытия текста.

### Шаг 5: Сохранение аннотированного документа

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Управление памятью:** Вызов `dispose()` освобождает нативные ресурсы и предотвращает утечки памяти — критично при пакетной обработке множества файлов.

## Удаление аннотаций: создание чистых версий документов

Иногда требуется версия PDF **без каких‑либо аннотаций** — например, при выдаче окончательного согласованного контракта. GroupDocs делает это простым.

### Понимание вариантов удаления аннотаций

Вы можете:
- Удалить **все** аннотации (самый распространённый вариант)  
- Удалить конкретные типы (например, только выделения)  
- Удалить аннотации по автору или странице  

### Пошаговое удаление аннотаций

**Шаг 1: Загрузка ранее аннотированного документа**

```java
Annotator annotator = new Annotator(outputPath);
```

**Шаг 2: Настройка параметров сохранения для чистого вывода**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Шаг 3: Сохранение чистой версии**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

В результате вы получаете **чистый PDF Java** файл без объектов аннотаций, идеально подходящий для финального распространения.

## Распространённые проблемы и их решения

### Проблема 1: Ошибки «Document not found»

```java
File inputFile = new File("path/to/your/document.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Document not found: " + inputFile.getAbsolutePath());
}
if (!inputFile.canRead()) {
    throw new IllegalArgumentException("Cannot read document: " + inputFile.getAbsolutePath());
}

Annotator annotator = new Annotator(inputFile.getAbsolutePath());
```

### Проблема 2: Аннотации отображаются в неправильных местах

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Проблема 3: Проблемы с памятью при работе с большими документами

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### Проблема 4: Лицензионные проблемы в продакшне

```java
try {
    License license = new License();
    license.setLicense("path/to/your/license.lic");
    System.out.println("License loaded successfully");
} catch (Exception e) {
    System.err.println("License loading failed: " + e.getMessage());
    // Handle the error appropriately
}
```

## Лучшие практики производительности для продакшн‑приложений

### Стратегии управления памятью

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

```java
List<String> documentPaths = Arrays.asList("doc1.pdf", "doc2.pdf", "doc3.pdf");

for (String docPath : documentPaths) {
    try (Annotator annotator = new Annotator(docPath)) {
        // Process one document at a time
        annotator.add(createAnnotation());
        annotator.save(getOutputPath(docPath));
    }
    // Memory is freed after each iteration
}
```

### Особенности многопоточности

GroupDocs.Annotation **не является потокобезопасным** по умолчанию. Если ваше приложение обрабатывает документы параллельно:

- **Никогда не делитесь** экземпляром `Annotator` между потоками.  
- **Синхронизируйте** доступ к файлам или используйте механизм блокировок.  
- Рассмотрите возможность создания **пула** объектов `Annotator` при необходимости высокой пропускной способности.

### Стратегии кэширования

- Кешируйте часто используемые шаблоны аннотаций.  
- Переиспользуйте коллекции `Point` для общих наборов координат.  
- Держите **шаблонный PDF** в памяти, если вы многократно аннотируете один и тот же базовый документ.

## Реальные сценарии и примеры использования

### Системы рецензирования документов

- **Юридический аудит:** подчёркивайте пункты контракта и добавляйте комментарии о рисках.  
- **Комплаенс‑аудиты:** выделяйте проблемные разделы в финансовой отчётности.  
- **Академическое рецензирование:** преподаватели подчёркивают фрагменты, требующие уточнения.

### Образовательные платформы

- **Инструменты аннотирования для студентов:** позволяют учащимся подчёркивать ключевые концепции в электронных книгах.  
- **Обратная связь от преподавателей:** предоставляют встроенные комментарии непосредственно в заданиях.

### Рабочие процессы контроля качества

- **Обзор технической документации:** инженеры подчёркивают разделы, требующие обновления.  
- **Стандартные операционные процедуры:** сотрудники службы безопасности выделяют критические шаги.

### Системы управления контентом

- **Редакционный процесс:** редакторы подчёркивают текст, требующий проверки фактов.  
- **Контроль версий:** отслеживание истории аннотаций между ревизиями документов.

## Продвинутые советы для профессиональной реализации

### Пользовательские стили аннотаций

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Метаданные аннотаций для отслеживания

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### Интеграция с системами управления пользователями

```java
// Assume you have a method that returns the current authenticated user
String currentUser = getCurrentUser();
String userRole = getUserRole(currentUser);

// Apply role‑based styling
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedBy(currentUser);
underline.setFontColor(getRoleColor(userRole));
underline.setMessage(String.format("[%s] %s", userRole.toUpperCase(), commentText));
```

## Устранение проблем в продакшне

### Мониторинг производительности

Отслеживайте следующие метрики в продакшне:
- **Использование кучи** — убедитесь, что вызывается `dispose()`.  
- **Время обработки одного документа** — логируйте метки времени до и после `annotator.save()`.  
- **Уровень ошибок** — фиксируйте исключения и классифицируйте их.

### Частые подводные камни в продакшне

- **Блокировка файлов** — убедитесь, что загруженные файлы закрыты перед аннотированием.  
- **Конкурентные правки** — реализуйте оптимистичную блокировку или проверку версии.  
- **Большие файлы (> 50 MB)** — увеличьте таймаут JVM и рассмотрите потоковые API.

### Лучшие практики обработки ошибок

```java
try (Annotator annotator = new Annotator(documentPath)) {
    UnderlineAnnotation annotation = createAnnotation();
    annotator.add(annotation);
    annotator.save(outputPath);
    
} catch (Exception e) {
    logger.error("Annotation failed for document: " + documentPath, e);
    // Implement appropriate error recovery
    throw new DocumentProcessingException("Failed to annotate document", e);
}
```

## Заключение

Теперь у вас есть всё необходимое, чтобы **создавать чистые PDF Java** файлы и **аннотировать PDF в Java** подчёркивающими аннотациями с помощью GroupDocs.Annotation. Помните:

- Управляйте ресурсами с помощью `try‑with‑resources` или явного `dispose()`.  
- Раннее проверяйте координаты, чтобы избежать неверных подчёркиваний.  
- Реализуйте надёжную обработку ошибок для стабильности в продакшне.  
- Используйте стили и метаданные, основанные на ролях, чтобы адаптировать процесс под ваш workflow.

Что дальше? Попробуйте добавить другие типы аннотаций — выделения, штампы или замену текста — и построить полноценное решение для обзора документов.

## Часто задаваемые вопросы

**В: Как аннотировать несколько участков текста за одну операцию?**  
О: Создайте несколько объектов `UnderlineAnnotation` с разными координатами и последовательно добавляйте их через `annotator.add()`.

**В: Можно ли аннотировать изображения внутри PDF‑документов?**  
О: Да. Используйте ту же систему координат, убедившись, что точки находятся внутри границ изображения.

**В: Какие форматы файлов, помимо PDF, поддерживает GroupDocs.Annotation?**  
О: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) и графические форматы, такие как JPEG, PNG, TIFF.

**В: Как обрабатывать очень большие документы, не исчерпывая память?**  
О: Обрабатывайте документы по одному, увеличьте размер кучи JVM (`-Xmx`), и всегда своевременно вызывайте `dispose()` у экземпляров `Annotator`.

**В: Можно ли извлечь существующие аннотации из документа?**  
О: Да. Вызовите `annotator.get()`, чтобы получить все аннотации, затем отфильтруйте их по типу, автору или странице при необходимости.

---

**Последнее обновление:** 2025-12-21  
**Тестировано с:** GroupDocs.Annotation 25.2  
**Автор:** GroupDocs  

---