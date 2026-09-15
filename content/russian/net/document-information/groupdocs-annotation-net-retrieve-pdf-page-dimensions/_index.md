---
categories:
- Document Processing
date: '2026-06-16'
description: Узнайте, как получить размер страницы PDF в .NET с помощью GroupDocs.Annotation.
  Извлеките ширину и высоту страницы PDF, получите ширину и высоту PDF и эффективно
  работайте с размерами страниц PDF в C#.
keywords: pdf page dimensions .net, groupdocs.annotation tutorial, pdf metadata extraction
  c#, .net document processing, retrieve pdf dimensions programmatically
lastmod: '2026-06-16'
linktitle: Руководство по размерам страниц PDF в .NET
schemas:
- author: GroupDocs
  dateModified: '2026-06-16'
  description: Learn how to get pdf page size in .NET using GroupDocs.Annotation.
    Extract pdf page width height, retrieve pdf width height, and handle c# pdf page
    dimensions efficiently.
  headline: PDF Page Dimensions .NET - Extract Width & Height with C#
  type: TechArticle
- description: Learn how to get pdf page size in .NET using GroupDocs.Annotation.
    Extract pdf page width height, retrieve pdf width height, and handle c# pdf page
    dimensions efficiently.
  name: PDF Page Dimensions .NET - Extract Width & Height with C#
  steps:
  - name: Initialize the Annotator with Your PDF
    text: Create an `Annotator` instance pointing to your PDF file. Always wrap it
      in a `using` block so the file handle is released promptly. **Pro Tip:** Proper
      disposal prevents memory leaks, especially when processing dozens of large PDFs
      in a batch job.
  - name: Retrieve Document Information
    text: '`DocumentInfo` is an object that holds overall PDF metadata such as total
      page count and a collection of `PageInfo` objects for each page. GroupDocs.Annotation
      makes metadata extraction a one‑liner: The returned `DocumentInfo` object gives
      you: - Total page count - File format details - A `Pages` li'
  - name: Validate the Retrieved Data
    text: Before you start looping over pages, confirm the document info isn’t null
      and that the page collection contains entries. This defensive check avoids null‑reference
      exceptions and provides early feedback if the PDF is corrupted.
  - name: Extract Width and Height for Each Page
    text: '`PageInfo` represents a single page’s properties, including its width,
      height, and rotation angle. Iterate through the `Pages` collection and read
      `Width` and `Height`. Remember that the values are expressed in **points** (1
      point = 1/72 inch). **Key Points** - Width appears first, then height. - Pa'
  type: HowTo
- questions:
  - answer: Yes. The free trial version supports basic dimension extraction, though
      it may impose a limit on the number of pages processed per session.
    question: Can I extract PDF page dimensions without a license?
  - answer: GroupDocs.Annotation returns dimensions in **points** (1 point = 1/72
      inch). Convert to inches by dividing by 72, or to millimeters by multiplying
      by 0.352778.
    question: What units are the width and height measurements in?
  - answer: 'Pass the password via `LoadOptions` when constructing the `Annotator`:
      `new Annotator(path, new LoadOptions { Password = "your‑password" })`.'
    question: How do I handle password‑protected PDFs?
  - answer: Yes. Download the file to a local `Stream` first, then use the stream‑based
      `Annotator` constructor to avoid intermediate files.
    question: Can this work with PDFs stored in cloud storage like Azure or AWS?
  - answer: GroupDocs.Annotation reads only the PDF’s cross‑reference table and page
      dictionaries, so most PDFs under 100 MB are processed in under 1 second on typical
      server hardware.
    question: What is the performance impact of extracting dimensions from large PDFs?
  type: FAQPage
tags:
- pdf-processing
- dotnet
- groupdocs
- document-metadata
title: Размеры страниц PDF в .NET — Извлечение ширины и высоты с C#
type: docs
url: /ru/net/document-information/groupdocs-annotation-net-retrieve-pdf-page-dimensions/
weight: 1
---

# Размеры страниц PDF в .NET — извлечение ширины и высоты с C#

## Введение

Вы когда‑нибудь сталкивались с работой с PDF‑документами в вашем .NET‑приложении, пытаясь **получить размер страницы PDF** для каждой страницы? Вы не одиноки. Независимо от того, создаёте ли вы просмотрщик документов, разрабатываете макеты для печати или обрабатываете формы, точные размеры страниц являются основой качественного пользовательского опыта.

В этом полном руководстве мы покажем, как извлекать размеры страниц PDF с помощью **GroupDocs.Annotation for .NET** — одной из самых надёжных библиотек для этой задачи. К концу вы получите рабочий код, который получает ширину, высоту и другие важные метаданные из любого PDF‑документа.

### Быстрые ответы
- **Как получить размер страницы PDF в .NET?** Используйте `Annotator.GetDocumentInfo()` и читайте `PageInfo.Width` / `PageInfo.Height`.
- **Какая библиотека поддерживает извлечение ширины и высоты страницы PDF?** GroupDocs.Annotation for .NET (v25.4.0+).
- **Нужна ли лицензия для базового извлечения размеров?** Доступно в бесплатной пробной версии; для продакшн‑использования требуется коммерческая лицензия.
- **В каких единицах возвращаются значения?** В пунктах (1/72 дюйма); при необходимости преобразуйте в дюймы или миллиметры.
- **Можно ли эффективно обрабатывать большие PDF?** Да — GroupDocs.Annotation читает метаданные без загрузки полного файла в память.

### Что такое **get pdf page size**?
**Get pdf page size** относится к программному получению ширины и высоты страницы PDF. Эта операция необходима для расчётов макета, подготовки к печати и позиционирования полей формы в .NET‑приложениях.

## Почему размеры страниц PDF важны в разработке на .NET

Прежде чем перейти к коду, давайте разберём, почему знание **pdf page width height** имеет значение. Эти цифры — не просто любопытство, они определяют реальную функциональность:

- **Управление макетом** — адаптивные просмотрщики могут автоматически масштабироваться в зависимости от точного размера страницы, устраняя неудобные полосы прокрутки.
- **Оптимизация печати** — точные размеры предотвращают растрату бумаги и несоответствие печати в коммерческих процессах.
- **Обработка форм** — координаты извлечения зависят от точного размера страницы; ошибка в 2 мм может нарушить захват данных.
- **Планирование ресурсов** — большие PDF с разными размерами требуют различных стратегий памяти; раннее знание размеров позволяет более эффективно группировать обработку.

## Предварительные требования

### Требуемые библиотеки и версии
- **GroupDocs.Annotation for .NET** (версия 25.4.0 или новее). Эта версия поддерживает **более 50 форматов ввода и вывода** и может обрабатывать PDF‑файлы со сотнями страниц без загрузки всего файла в память.
- .NET Framework 4.6.1+ **или** .NET Core 2.0+

### Требования к настройке окружения
- Visual Studio 2019 или новее (издание Community работает отлично)
- Тестовый PDF‑файл (мы покажем, как работать с разными типами)
- Базовое знакомство с инструкциями `using` и освобождением объектов в C#

### Требования к знаниям
Вам понадобится:
- Основы C#
- Основы управления пакетами NuGet
- Простые операции ввода‑вывода файлов в .NET

Все готово? Отлично — давайте настроим библиотеку.

## Настройка GroupDocs.Annotation для .NET

Установка GroupDocs.Annotation проста, но существует несколько способов сделать это в зависимости от вашего рабочего процесса.

### Метод 1: Использование консоли менеджера пакетов NuGet
Откройте консоль менеджера пакетов в Visual Studio и выполните:

```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```

### Метод 2: Использование .NET CLI
Если вы предпочитаете инструменты командной строки:

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Метод 3: Visual Package Manager
1. Щелкните правой кнопкой мыши ваш проект в обозревателе решений  
2. Выберите **Manage NuGet Packages**  
3. Найдите **GroupDocs.Annotation**  
4. Нажмите **Install**

#### Варианты лицензирования (выберите подходящий для вас)
- **Free Trial** — основные функции, включая извлечение размеров, доступны с небольшими ограничениями использования — идеально для прототипов.  
- **Temporary License** — запросите 30‑дневный временный ключ для полной функциональности во время оценки.  
- **Commercial License** — требуется для продакшн‑развертываний; цена зависит от количества разработчиков и модели развертывания.

### Быстрая проверка настройки
Вот простой тест, чтобы убедиться, что всё настроено правильно:

```csharp
using GroupDocs.Annotation;

// This should compile without errors if installation succeeded
using (Annotator annotator = new Annotator(@"path\to\your\test.pdf"))
{
    Console.WriteLine("GroupDocs.Annotation is ready to use!");
}
```

Если код компилируется и запускается без исключений, вы готовы извлекать размеры страниц.

## Что такое класс **Annotator**?
Класс `Annotator` — это основной объект GroupDocs.Annotation, представляющий PDF‑документ в памяти и предоставляющий методы для чтения метаданных, добавления аннотаций и извлечения информации о страницах. Он инкапсулирует работу с файлами, поддерживает загрузку из потоков и гарантирует, что все последующие операции проходят через экземпляр `Annotator`, упрощая управление рабочим процессом.

## Как **получить размер страницы PDF** с помощью GroupDocs.Annotation?
`GetDocumentInfo()` возвращает объект `DocumentInfo`, содержащий общие метаданные PDF, включая количество страниц и коллекцию деталей страниц. Загрузите ваш PDF с помощью `new Annotator("file.pdf")` и вызовите этот метод; каждый `PageInfo` в коллекции `Pages` содержит `Width` и `Height`. Такой двухшаговый подход мгновенно предоставляет размеры в пунктах, без парсинга всего файла.

## Пошаговое руководство по реализации

### Шаг 1: Инициализация Annotator с вашим PDF
Создайте экземпляр `Annotator`, указывающий на ваш PDF‑файл. Всегда оборачивайте его в блок `using`, чтобы дескриптор файла освобождался сразу.

```csharp
using (Annotator annotator = new Annotator(@"YOUR_DOCUMENT_DIRECTORY\INPUT_PDF"))
{
    // All our dimension extraction magic happens here
}
```

**Совет:** Правильное освобождение ресурсов предотвращает утечки памяти, особенно при обработке десятков больших PDF в пакетной задаче.

### Шаг 2: Получение информации о документе
`DocumentInfo` — объект, содержащий общие метаданные PDF, такие как общее количество страниц и коллекцию объектов `PageInfo` для каждой страницы.  
GroupDocs.Annotation делает извлечение метаданных однострочным:

```csharp
IDocumentInfo info = annotator.Document.GetDocumentInfo();
```

Возвращаемый объект `DocumentInfo` предоставляет вам:
- Общее количество страниц  
- Детали формата файла  
- Список `Pages`, где каждая запись содержит ширину, высоту, вращение и прочее

### Шаг 3: Проверка полученных данных
Прежде чем начинать перебор страниц, убедитесь, что объект информации о документе не равен null и что коллекция страниц содержит элементы.

```csharp
if (info.PagesInfo != null && info.PagesInfo.Count > 0)
{
    Console.WriteLine($"\t Document info: Type {info.FileType}, size = {info.Size}, pages = {info.PageCount}");
}
else
{
    Console.WriteLine("No page information available - check your PDF file");
    return;
}
```

Эта проверка защищает от исключений null‑reference и дает раннее уведомление, если PDF повреждён.

### Шаг 4: Извлечение ширины и высоты для каждой страницы
`PageInfo` представляет свойства отдельной страницы, включая её ширину, высоту и угол вращения.  
Итерируйте коллекцию `Pages` и читайте `Width` и `Height`. Помните, что значения выражены в **пунктах** (1 point = 1/72 дюйма).

```csharp
foreach (var page in info.PagesInfo)
{
    Console.WriteLine($"\t\t page #{page.PageNumber}: {page.Width}x{page.Height}");
}
```

**Ключевые моменты**
- Сначала ширина, затем высота.  
- Номера страниц начинаются с 1, как в большинстве просмотрщиков.  
- Информация о вращении также доступна, если необходимо скорректировать координаты.

### Полный рабочий пример (метод)
Вы можете объединить вышеописанные шаги в переиспользуемый метод:

```csharp
using GroupDocs.Annotation;
using System;

public void ExtractPdfPageDimensions(string pdfPath)
{
    try
    {
        using (Annotator annotator = new Annotator(pdfPath))
        {
            IDocumentInfo info = annotator.Document.GetDocumentInfo();
            
            if (info.PagesInfo != null && info.PagesInfo.Count > 0)
            {
                Console.WriteLine($"Document: {info.FileType}, {info.Size} bytes, {info.PageCount} pages");
                
                foreach (var page in info.PagesInfo)
                {
                    Console.WriteLine($"Page {page.PageNumber}: {page.Width} x {page.Height} points");
                }
            }
            else
            {
                Console.WriteLine("Could not retrieve page information");
            }
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error processing PDF: {ex.Message}");
    }
}
```

## Распространённые подводные камни и как их избежать

Даже при простом коде разработчики сталкиваются с предсказуемыми проблемами. Ниже перечислены наиболее распространённые ловушки и проверенные решения.

### Проблемы с путями к файлам
**Проблема:** Ошибки «File not found» во время разработки.  
**Решение:** Используйте абсолютные пути при тестировании и всегда проверяйте существование файла перед созданием `Annotator`.

```csharp
if (!File.Exists(pdfPath))
{
    throw new FileNotFoundException($"PDF file not found: {pdfPath}");
}
```

### Проблемы с разрешениями
**Проблема:** Приложение не имеет прав чтения PDF‑файла, особенно на веб‑серверах.  
**Решение:** Предоставьте соответствующие права чтения идентификатору пула приложений или используйте имперсонацию для ограниченных папок.

### Обработка повреждённых PDF
**Проблема:** Некоторые PDF частично повреждены или используют нестандартные функции.  
**Решение:** Оберните логику извлечения в блок `try‑catch` и выводите понятное сообщение об ошибке. GroupDocs.Annotation бросит `DocumentException` для неподдерживаемых структур.

### Утечки памяти при работе с большими файлами
**Проблема:** Обработка множества больших PDF без освобождения экземпляров `Annotator` приводит к сбоям из‑за нехватки памяти.  
**Решение:** Всегда используйте конструкции `using` и рассматривайте обработку файлов небольшими партиями или в режиме потоковой передачи.

### Совместимость версий
**Проблема:** Смешивание разных версий библиотек GroupDocs может вызвать несоответствия типов.  
**Решение:** Стандартизируйте одну версию во всём решении и обновляйте все связанные пакеты одновременно.

## Применения в реальном мире

Понимание **retrieve pdf width height** открывает мощные сценарии:

### Приложения для просмотра документов
Адаптивные просмотрщики могут автоматически задавать начальный уровень масштабирования на основе размеров страниц, обеспечивая режим «подгонки к экрану» без ручных настроек.

```csharp
// Example: Calculate optimal zoom for viewport
double optimalZoom = Math.Min(viewportWidth / pageWidth, viewportHeight / pageHeight);
```

### Автоматическая генерация отчётов
При объединении нескольких PDF в один отчёт знание размеров каждой страницы обеспечивает согласованное масштабирование и предотвращает неожиданные разрывы страниц.

### Системы управления печатью
Точные размеры позволяют рассчитывать оптимальное использование бумаги, определять ориентацию (портрет/ландшафт) и предварительно проверять документы перед отправкой в коммерческие типографии.

### Решения для обработки форм
Точные координаты, полученные из размеров страниц, позволяют надёжно извлекать флажки, подписи и текстовые поля из PDF с различными макетами.

### Управление цифровыми активами
Помечайте PDF метаданными о размере, чтобы ускорить поиск (например, «показать все документы формата A4») и повысить эффективность каталогизации.

## Советы по оптимизации производительности

Когда вы переходите от прототипа к продакшн‑версии, производительность становится критически важной.

### Стратегия пакетной обработки
Группируйте похожие операции, чтобы снизить накладные расходы. Например, считайте метаданные для пакета файлов, сохраните результаты, а затем обработайте аннотации во втором проходе.

```csharp
var results = new List<PageDimensionResult>();
foreach (var pdfFile in pdfFiles.Take(10)) // Process in batches of 10
{
    // Extract dimensions and add to results
}
```

### Кеширование часто используемых размеров
Если одни и те же PDF запрашиваются многократно, кешируйте их объекты `DocumentInfo` в потокобезопасном словаре. Не забудьте инвалидировать кеш при изменении исходного файла.

```csharp
private static readonly Dictionary<string, IDocumentInfo> _dimensionCache = 
    new Dictionary<string, IDocumentInfo>();
```

### Асинхронная обработка больших файлов
Используйте паттерны `async/await`, чтобы UI‑потоки оставались отзывчивыми, пока GroupDocs.Annotation читает метаданные в фоновом режиме.

```csharp
public async Task<List<PageInfo>> ExtractDimensionsAsync(string pdfPath)
{
    return await Task.Run(() => {
        // Your dimension extraction code here
    });
}
```

### Лучшие практики управления памятью
- Своевременно освобождайте каждый экземпляр `Annotator`.  
- Обрабатывайте большие коллекции порциями по 20–50 файлов, чтобы снизить потребление памяти.  
- Отслеживайте использование памяти с помощью счётчиков производительности или профилировочных инструментов.  
- Используйте слабые ссылки для кешируемых объектов, если ожидаете высокий оборот.

## Расширенные сценарии использования

После того как вы освоите базовое извлечение, изучите эти продвинутые сценарии.

### Обработка документов с разными размерами
Некоторые PDF содержат страницы разных размеров (например, обложка формата A4, а внутренние страницы — A5). Обнаружьте изменения размеров, сравнивая последовательные значения `PageInfo.Width`/`Height`, и применяйте условную логику.

```csharp
var pageSizes = info.PagesInfo.Select(p => new { p.PageNumber, p.Width, p.Height }).ToList();
var uniqueSizes = pageSizes.Select(p => new { p.Width, p.Height }).Distinct().Count();

if (uniqueSizes > 1)
{
    Console.WriteLine("Document contains multiple page sizes");
}
```

### Определение ориентации
Определите портретную или ландшафтную ориентацию, сравнив ширину и высоту. Это полезно для автоматического вращения страниц в просмотрщиках или для создания миниатюр с учётом ориентации.

```csharp
foreach (var page in info.PagesInfo)
{
    string orientation = page.Width > page.Height ? "Landscape" : "Portrait";
    Console.WriteLine($"Page {page.PageNumber}: {orientation}");
}
```

### Интеграция с другими функциями GroupDocs
Сочетайте извлечение размеров с API аннотаций для точного размещения штампов или с API конвертации для создания изображений, сохраняющих оригинальный размер страницы.

## Часто задаваемые вопросы

**Вопрос:** Можно ли извлечь размеры страниц PDF без лицензии?  
**Ответ:** Да. Бесплатная пробная версия поддерживает базовое извлечение размеров, хотя может накладывать ограничение на количество страниц, обрабатываемых за одну сессию.

**Вопрос:** В каких единицах измеряются ширина и высота?  
**Ответ:** GroupDocs.Annotation возвращает размеры в **пунктах** (1 point = 1/72 дюйма). Для получения дюймов разделите на 72, а для миллиметров умножьте на 0.352778.

**Вопрос:** Как работать с PDF, защищёнными паролем?  
**Ответ:** Передайте пароль через `LoadOptions` при создании `Annotator`: `new Annotator(path, new LoadOptions { Password = "your‑password" })`.

**Вопрос:** Можно ли использовать это с PDF, хранящимися в облачном хранилище, таком как Azure или AWS?  
**Ответ:** Да. Сначала скачайте файл в локальный `Stream`, затем используйте конструктор `Annotator`, принимающий поток, чтобы избежать промежуточных файлов.

**Вопрос:** Каково влияние на производительность при извлечении размеров из больших PDF?  
**Ответ:** GroupDocs.Annotation читает только таблицу перекрёстных ссылок и словари страниц PDF, поэтому большинство PDF размером до 100 МБ обрабатываются менее чем за 1 секунду на типичном серверном оборудовании.

**Вопрос:** Как обрабатывать PDF со страницами, повернутыми?  
**Ответ:** Свойство `PageInfo.Rotation` указывает угол вращения. Если страница повернута на 90° или 270°, поменяйте местами значения ширины и высоты, чтобы получить отображаемые размеры.

**Вопрос:** Можно ли извлечь размеры только из определённых страниц?  
**Ответ:** Да. После вызова `GetDocumentInfo()` отфильтруйте коллекцию `Pages` по `PageNumber`, чтобы получить отдельные страницы.

**Вопрос:** Работает ли это с документами формата PDF/A?  
**Ответ:** Абсолютно. GroupDocs.Annotation полностью поддерживает стандарты PDF/A‑1, PDF/A‑2 и PDF/A‑3.

**Вопрос:** Как решить ошибки «Unable to load document»?  
**Ответ:** Проверьте права доступа к файлу, убедитесь, что файл не повреждён, открыв его в PDF‑просмотрщике, и подтвердите, что используете поддерживаемую версию PDF (1.4–2.0).

**Вопрос:** Можно ли получить размеры в пикселях вместо пунктов?  
**Ответ:** Преобразуйте вручную: `pixels = points * DPI / 72`. Для типичного DPI экрана 96 умножьте пункты на 1.3333.

## Важные ресурсы

- **Документация**: [GroupDocs Annotation Documentation](https://docs.groupdocs.com/annotation/net/)
- **Справочник API**: [GroupDocs Annotation API Reference](https://reference.groupdocs.com/annotation/net/)
- **Загрузки**: [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/)
- **Купить GroupDocs**: [Buy GroupDocs](https://purchase.groupdocs.com/buy)
- **Попробовать бесплатную версию**: [Try Free Version](https://releases.groupdocs.com/annotation/net/)
- **Запросить временную лицензию**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Форум GroupDocs**: [GroupDocs Forum](https://forum.groupdocs.com/c/annotation/)

---

**Последнее обновление:** 2026-06-16  
**Тестировано с:** GroupDocs.Annotation 25.4.0 for .NET  
**Автор:** GroupDocs

## Связанные руководства

- [Извлечение метаданных документа .NET — Полное руководство по GroupDocs.Annotation](/annotation/net/document-information/)
- [Загрузка PDF из URL .NET — Полное руководство с GroupDocs.Annotation](/annotation/net/document-loading-essentials/load-document-from-url/)
- [Генерация предварительного просмотра документа .NET — Полное руководство с GroupDocs.Annotation](/annotation/net/advanced-usage/generate-document-pages-preview/)