---
date: '2026-10-16'
description: Узнайте, как сохранить PDF без аннотаций в Java, освоить управление памятью
  PDF в Java и добавить подчёркнутые аннотации с помощью GroupDocs.Annotation. Пошаговое
  руководство.
keywords:
- save pdf without annotations
- java pdf memory management
- java document review system
- groupdocs annotation tutorial
- underline annotation java
lastmod: '2026-10-16'
linktitle: Аннотирование документов Java с GroupDocs
og_description: Узнайте, как сохранить PDF без аннотаций в Java, освоить управление
  памятью PDF в Java и добавить подчёркнутые аннотации с помощью GroupDocs.Annotation.
  Пошаговое руководство.
og_image_alt: 'Developer guide: Save PDF without annotations in Java using GroupDocs.Annotation'
og_title: Как сохранить PDF без аннотаций в Java с использованием GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  headline: How to save PDF without annotations in Java using GroupDocs
  type: TechArticle
- description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  name: How to save PDF without annotations in Java using GroupDocs
  steps:
  - name: initialize the annotator and load your document
    text: '`Annotator` is the main entry point in GroupDocs.Annotation for loading
      and modifying PDF documents. It abstracts file‑system handling, stream management,
      and native resource allocation. **Pro tip:** Use absolute paths while developing
      to avoid “file not found” errors. In production, consider loadin'
  - name: creating comments and replies (the collaborative part)
    text: '`Comment` objects represent threaded discussion attached to an annotation.
      Each comment can have an author, a timestamp, and optional replies, enabling
      a full conversation around a specific markup. **Real‑world use:** Reviewers
      can discuss a specific clause by adding threaded replies, keeping the co'
  - name: defining annotation coordinates (getting the position right)
    text: '`Point` defines a single coordinate in PDF space (measured in points, where
      72 points = 1 inch). Four points are required for an underline: two for the
      start line and two for the end line. **Coordinate system:** - Points 1 & 2 define
      the top edge of the underline. - Points 3 & 4 define the bottom ed'
  - name: creating and configuring the underline annotation
    text: '`UnderlineAnnotation` is the concrete class that represents an underline
      markup. It inherits from the base `Annotation` class and adds properties specific
      to underlines, such as line thickness and style. **Color & opacity tips:** -
      `FontColor` uses ARGB; `65535` (0x00FFFF) yields bright yellow. - Fo'
  - name: saving your annotated document
    text: '`SaveOptions` lets you control the output format, whether to embed annotations,
      and how to handle metadata. Setting `AnnotationType.NONE` instructs the library
      to strip all annotation objects, which is the key to **save PDF without annotations**.
      **Memory management:** The `dispose()` call releases '
  type: HowTo
- questions:
  - answer: Create several `UnderlineAnnotation` objects with different coordinates
      and add them sequentially using `annotator.add()`.
    question: How do I annotate multiple areas of text in a single operation?
  - answer: Yes. Use the same coordinate system, ensuring the points lie inside the
      image bounds.
    question: Can I annotate images within PDF documents?
  - answer: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), and image formats
      such as JPEG, PNG, TIFF.
    question: What file formats besides PDF does GroupDocs.Annotation support?
  - answer: Process documents one at a time, increase the JVM heap (`-Xmx`), and always
      dispose of `Annotator` instances promptly.
    question: How do I handle very large documents without running out of memory?
  - answer: Yes. Use `annotator.get()` to retrieve all annotations, then filter by
      type, author, or page as needed.
    question: Is it possible to extract existing annotations from a document?
  type: FAQPage
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
- java pdf memory management
title: Как сохранить PDF без аннотаций в Java с использованием GroupDocs
type: docs
url: /ru/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Как сохранить PDF без аннотаций в Java с использованием GroupDocs

Если вам нужно **save PDF without annotations** и при этом иметь возможность добавлять совместные подчеркивающие заметки, вы попали в нужное место. Многие Java‑разработчики сталкиваются с проблемой сохранения чистой версии документа для финального распространения, особенно когда один и тот же файл используется для итеративных обзоров. В этом руководстве вы узнаете, как создать чистый PDF, эффективно управлять памятью и применять подчеркивающие аннотации с комментариями с помощью GroupDocs.Annotation. К концу вы поймете полный рабочий процесс — от загрузки PDF до создания финальной копии без водяных знаков — а также получите рекомендации по построению надёжной **java document review system**.

## Быстрые ответы
- **Как добавить подчеркивающую аннотацию?** Используйте `UnderlineAnnotation` с `annotator.add()`, затем сохраните документ.  
- **Как сохранить PDF без аннотаций?** Загрузите аннотированный файл, установите `AnnotationType.NONE` в `SaveOptions` и сохраните новую копию.  
- **Какие библиотеки требуются?** GroupDocs.Annotation v25.2 (или новее) и её Maven‑репозиторий.  
- **Нужна ли лицензия для продакшн?** Да — примените действующую лицензию GroupDocs, чтобы избежать водяных знаков.  
- **Можно ли эффективно обрабатывать несколько документов?** Оберните каждый `Annotator` в блок try‑with‑resources и вызывайте dispose после каждого файла.

## Как сохранить PDF без аннотаций в Java?

Загрузите исходный PDF с помощью `Annotator`, настройте `SaveOptions` так, чтобы исключить все типы аннотаций, и вызовите `save()` для записи чистой копии. Эта операция не изменяет оригинальный файл, поэтому у вас остаются как аннотированная версия для рецензентов, так и безупречная версия для распространения. Процесс использует потоковую передачу, что означает, что весь документ никогда полностью не находится в памяти — критично для больших PDF‑файлов.

## Что означает сохранение PDF без аннотаций?

`save pdf without annotations` означает экспорт PDF‑документа с удалением всех объектов аннотаций (выделения, комментарии, штампы, подчеркивания и т.д.). Полученный файл содержит только оригинальное содержимое и макет, что делает его подходящим для юридических дел, публичного выпуска или архивного хранения.

## Почему создавать чистые PDF‑файлы в системе обзора документов на Java?

Чистая версия устраняет отметки рецензентов, комментарии и выделения, предоставляя отшлифованный документ, готовый для клиентов, регуляторов или публичного выпуска. Она также уменьшает размер файла в среднем на 30 % и предотвращает случайное раскрытие внутренних заметок — критично для юридических и комплаенс‑процессов. GroupDocs.Annotation может удалить все объекты аннотаций за один проход, поддерживая PDF‑файлы до 500 MB без загрузки всего файла в память.

## Предварительные требования и настройка окружения

### Требования перед началом

**Требования к среде разработки**  
- Java Development Kit (JDK) 8 или выше (рекомендовано JDK 11+)  
- Maven 3.6+ или Gradle 6.0+ для управления зависимостями  
- IDE, например IntelliJ IDEA, Eclipse или VS Code с Java‑расширениями  
- Не менее 2 GB доступной ОЗУ (обработка документов может быть ресурсоёмкой)

**Необходимые знания**  
Вы должны уверенно владеть базовыми концепциями Java — инициализацией объектов, вызовами методов и зависимостями Maven. Предыдущий опыт работы с сторонними библиотеками ускорит внедрение.

**Тестовые документы**  
Подготовьте несколько образцов PDF. Текстовые PDF работают лучше всего; отсканированные изображения могут потребовать OCR перед аннотированием.

### Настройка Maven: добавление GroupDocs в ваш проект

Добавьте следующую зависимость в ваш `pom.xml`. Этот шаг часто ставит в тупик многих разработчиков при первой попытке, потому что `groupId` и `artifactId` должны точно совпадать.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```

**Важно:** Версия 25.2 — последняя стабильная на момент написания. Регулярно проверяйте репозиторий GroupDocs на наличие более новых версий с исправлениями ошибок и улучшениями производительности.

### Настройка лицензирования (не пропускайте)

**Для разработки/тестирования** — Скачайте бесплатную trial‑версию с сайта GroupDocs. trial включает все функции, но добавляет водяной знак к обработанным документам.

**Для продакшн** — Приобретите лицензию и примените её при запуске приложения. Без действующей лицензии сборки продакшн будут ограничены и помечены водяным знаком.

## Руководство по реализации: добавление подчеркивающих аннотаций

### Понимание рабочего процесса аннотаций

Перед тем как перейти к коду, рассмотрим четырёхшаговый процесс, который происходит при **annotate PDF in Java**:

1. **Document loading** — `Annotator` читает файл в память.  
2. **Annotation creation** — Определяются свойства, такие как позиция, стиль и комментарии.  
3. **Annotation application** — Библиотека внедряет аннотацию в структуру PDF.  
4. **Document saving** — Сохраняется изменённый файл, при желании сохраняется оригинал.

Процесс не разрушительный; исходный файл остаётся нетронутым, если вы его не перезапишете.

### Шаг 1: инициализировать annotator и загрузить документ

`Annotator` — основной входной пункт в GroupDocs.Annotation для загрузки и изменения PDF‑документов. Он абстрагирует работу с файловой системой, потоками и нативными ресурсами.

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

**Совет:** Используйте абсолютные пути во время разработки, чтобы избежать ошибок «file not found». В продакшн рассматривайте загрузку ресурсов из classpath или облачного хранилища.

### Шаг 2: создание комментариев и ответов (совместная часть)

Объекты `Comment` представляют ветвистую дискуссию, привязанную к аннотации. Каждый комментарий может иметь автора, метку времени и опциональные ответы, позволяя вести полноценный разговор вокруг конкретной разметки.

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Применение в реальном мире:** Рецензенты могут обсуждать конкретный пункт, добавляя ответы, привязанные к точной аннотации.

### Шаг 3: определение координат аннотации (правильное позиционирование)

`Point` определяет одну координату в пространстве PDF (измеряется в пунктах, где 72 пункта = 1 дюйм). Для подчеркивания требуется четыре точки: две для верхней линии и две для нижней.

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

**Система координат:**  
- Точки 1 и 2 задают верхний край подчеркивания.  
- Точки 3 и 4 задают нижний край.  
- Разница по Y (730 vs 650) контролирует толщину.

### Шаг 4: создание и настройка подчеркивающей аннотации

`UnderlineAnnotation` — конкретный класс, представляющий подчеркивающую разметку. Он наследуется от базового `Annotation` и добавляет свойства, специфичные для подчеркиваний, такие как толщина линии и стиль.

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

**Подсказки по цвету и непрозрачности:**  
- `FontColor` использует ARGB; `65535` (0x00FFFF) даёт ярко‑желтый.  
- Для красного используйте `16711680` (0xFF0000); для синего — `255` (0x0000FF).  
- Значения непрозрачности от 0.5 до 0.8 обеспечивают хорошую читаемость без затемнения текста.

### Шаг 5: сохранение аннотированного документа

`SaveOptions` позволяет управлять форматом вывода, включением аннотаций и обработкой метаданных. Установка `AnnotationType.NONE` инструктирует библиотеку удалить все объекты аннотаций, что является ключом к **save PDF without annotations**.

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

**Управление памятью:** Вызов `dispose()` освобождает нативные ресурсы и предотвращает утечки памяти — критично при пакетной обработке множества файлов.

## Удаление аннотаций: создание чистых версий документов

Иногда требуется версия PDF **без каких‑либо аннотаций** — например, при передаче окончательно утверждённого контракта. GroupDocs делает это простым.

### Понимание вариантов удаления аннотаций

Вы можете:  
- Удалить **все** аннотации (самый распространённый вариант)  
- Удалить конкретные типы (например, только выделения)  
- Удалить аннотации по автору или странице  

### Пошаговое удаление аннотаций

**Step 1: load the previously annotated document**

`Annotator` снова выступает загрузчиком; он прочитает файл, который всё ещё содержит объекты аннотаций.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Step 2: configure save options for a clean output**

`SaveOptions` предоставляет fluent‑API для указания, что в выходной файл не следует записывать типы аннотаций.

```java
Annotator annotator = new Annotator(outputPath);
```

**Step 3: save the clean version**

Вызов `save()` с настроенными параметрами записывает PDF, содержащий только оригинальное содержимое.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

Это создаёт **clean PDF** файл без объектов аннотаций, идеально подходящий для финального распространения.

## Распространённые проблемы и решения

### Проблема 1: ошибка «Document not found»

Убедитесь, что путь к файлу правильный и приложение имеет права чтения. Использование `Path.of()` с абсолютными путями устраняет большинство неоднозначностей.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

### Проблема 2: аннотации появляются в неправильных местах

Начало координат PDF находится в левом нижнем углу. Проверьте, что ваши значения Y увеличиваются вверх и учитывайте поворот страницы.

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

### Проблема 3: проблемы с памятью при больших документах

GroupDocs.Annotation потоково обрабатывает содержимое и никогда не загружает весь файл в heap‑память. Тем не менее, необходимо вызывать `dispose()` и рассматривать увеличение heap‑памяти JVM (`-Xmx`) для файлов более 200 MB.

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Проблема 4: проблемы с лицензированием в продакшн

Если файл лицензии отсутствует или путь указан неверно, библиотека переходит в trial‑режим, добавляя водяной знак на каждую страницу. Разместите файл лицензии в каталоге, доступном в classpath, и загрузите его на ранних этапах жизненного цикла приложения.

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

## Лучшие практики производительности для продакшн‑приложений

### Стратегии управления памятью

GroupDocs.Annotation обрабатывает PDF в потоковом режиме, что позволяет работать с файлами до 500 MB без полной загрузки документа в память. Тем не менее, соблюдайте следующие рекомендации:

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

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

### Особенности многопоточности

GroupDocs.Annotation **не является потокобезопасным** по умолчанию. Если ваше приложение обрабатывает документы одновременно:

- **Никогда не делитесь** экземпляром `Annotator` между потоками.  
- **Синхронизируйте** доступ к файлам или используйте механизм блокировок.  
- Рассмотрите **пул** объектов `Annotator`, если требуется высокая пропускная способность.

### Стратегии кэширования

- Кешируйте часто используемые шаблоны аннотаций.  
- Переиспользуйте коллекции `Point` для типовых наборов координат.  
- Храните **шаблонный PDF** в памяти, если вы многократно аннотируете один и тот же базовый документ.

## Лучшие практики управления памятью при работе с PDF в Java

Эффективное использование памяти критично при работе с большими PDF или при пакетной обработке множества файлов. Вот несколько практических рекомендаций:

- **Используйте try‑with‑resources** для каждого `Annotator`, чтобы гарантировать освобождение ресурсов.  
- **Увеличивайте heap‑память JVM** (`-Xmx`) только при необходимости; контролируйте использование с помощью профилирующих инструментов.  
- **Обрабатывайте документы последовательно**, освобождая память после каждого файла.  
- **Избегайте многократной загрузки одного и того же PDF**; переиспользуйте один и тот же поток, если требуется повторное чтение.

Применение этих практик помогает поддерживать отзывчивость приложения и предотвращает сбои из‑за нехватки памяти при интенсивных аннотационных нагрузках.

## Реальные примеры применения и сценарии использования

### Системы обзора документов

- **Юридический обзор:** Подчёркивайте пункты контрактов и добавляйте комментарии о рисках.  
- **Аудит соответствия:** Выделяйте проблемные разделы в финансовой отчётности.  
- **Академический рецензент:** Преподаватели подчёркивают фрагменты, требующие уточнения.

### Образовательные платформы

- **Инструменты аннотирования для студентов:** Позволяют учащимся подчёркивать ключевые концепции в электронных книгах.  
- **Обратная связь преподавателя:** Предоставляет встроенные комментарии непосредственно в загруженных заданиях.

### Рабочие процессы контроля качества

- **Обзор технической документации:** Инженеры подчёркивают разделы, требующие обновления.  
- **Стандарты операционных процедур:** Службы безопасности выделяют критически важные шаги.

### Системы управления контентом

- **Редакционный процесс:** Редакторы подчёркивают текст, требующий проверки фактов.  
- **Контроль версий:** Отслеживание истории аннотаций между ревизиями документов.

## Продвинутые советы для профессиональной реализации

### Пользовательские стили аннотаций

Вы можете расширить визуальное оформление подчеркивания, задав пользовательские шаблоны штриховки, окончания линий и уровни непрозрачности. Это полезно, когда нужно различать роли рецензентов (например, юридический vs. инженерный).

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

### Метаданные аннотаций для отслеживания

Каждая аннотация может содержать пользовательский словарь метаданных. Сохраняйте идентификаторы, метки времени или состояние рабочего процесса для интеграции с внешними системами отслеживания.

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Интеграция с системами управления пользователями

Сопоставьте свойство `author` объекта `Comment` с идентификаторами пользователей вашего приложения. Это позволяет применять стили по ролям и генерировать аудит‑треки.

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

## Устранение проблем в продакшн

### Мониторинг производительности

Отслеживайте следующие метрики в продакшн:  
- **Heap usage** — убедитесь, что вызывается `dispose()`.  
- **Processing time per document** — логируйте метки времени до и после `annotator.save()`.  
- **Error rate** — фиксируйте исключения и классифицируйте их.

### Распространённые подводные камни в продакшн

- **Блокировка файлов** — убедитесь, что загруженные файлы закрыты перед аннотированием.  
- **Конкурентные правки** — реализуйте оптимистичную блокировку или проверку версии.  
- **Большие файлы (> 50 MB)** — увеличьте таймаут JVM и рассмотрите использование потоковых API.

### Лучшие практики обработки ошибок

Оборачивайте все вызовы аннотаций в блоки try‑catch, логируйте полный стек трассировки и бросайте пользовательское `AnnotationException` с понятным сообщением. Такой подход упрощает отладку и предоставляет ясную обратную связь потребителям API.

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

## Часто задаваемые вопросы

**Q: Как аннотировать несколько областей текста за одну операцию?**  
A: Создайте несколько объектов `UnderlineAnnotation` с разными координатами и добавляйте их последовательно с помощью `annotator.add()`.

**Q: Можно ли аннотировать изображения внутри PDF‑документов?**  
A: Да. Используйте ту же систему координат, убедившись, что точки находятся внутри границ изображения.

**Q: Какие форматы файлов, кроме PDF, поддерживает GroupDocs.Annotation?**  
A: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) и графические форматы, такие как JPEG, PNG, TIFF.

**Q: Как работать с очень большими документами, не исчерпывая память?**  
A: Обрабатывайте документы по одному, увеличьте heap‑память JVM (`-Xmx`) и всегда своевременно вызывайте `dispose()` у экземпляров `Annotator`.

**Q: Можно ли извлечь существующие аннотации из документа?**  
A: Да. Используйте `annotator.get()` для получения всех аннотаций, затем фильтруйте их по типу, автору или странице по необходимости.

---

**Last Updated:** 2026-10-16  
**Tested With:** GroupDocs.Annotation 25.2  
**Author:** GroupDocs  

---

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

## Связанные руководства

- [Create Clean PDF Java: Underline Annotations with GroupDocs](/annotation/java/annotation-management/java-groupdocs-annotate-add-remove-underline/)
- [Edit PDF Annotations Java - Complete GroupDocs Tutorial](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [Annotate Pdfs Groupdocs Annotation Java](/annotation/java/annotation-management/annotate-pdfs-groupdocs-annotation-java/)