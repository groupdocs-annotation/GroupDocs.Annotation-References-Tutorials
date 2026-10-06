---
categories:
- Document Processing
date: '2026-10-05'
description: Узнайте, как скрыть аннотации при создании чистых предварительных просмотров
  документов в C# с помощью GroupDocs.Annotation .NET. Пошаговое руководство с примерами
  кода, советами по производительности и устранению неполадок.
keywords:
- how to hide annotations
- preview document without annotations
- remove annotations from preview
- clean document preview .NET
- generate document preview without annotations
lastmod: '2026-10-05'
linktitle: Предварительный просмотр документа без аннотаций
og_description: Узнайте, как скрыть аннотации при генерации чистых предварительных
  просмотров документов в C#. Это руководство охватывает настройку, код, советы по
  производительности и устранение неполадок.
og_image_alt: Guide showing how to generate document preview without annotations using
  GroupDocs.Annotation for .NET
og_title: Как скрыть аннотации при генерации предварительного просмотра документа
  в C#
schemas:
- author: GroupDocs
  dateModified: '2026-10-05'
  description: Learn how to hide annotations while generating clean document previews
    in C# using GroupDocs.Annotation .NET. Step-by-step guide with code examples,
    performance tips, and troubleshooting.
  headline: How to hide annotations when generating document preview in C#
  type: TechArticle
- description: Learn how to hide annotations while generating clean document previews
    in C# using GroupDocs.Annotation .NET. Step-by-step guide with code examples,
    performance tips, and troubleshooting.
  name: How to hide annotations when generating document preview in C#
  steps:
  - name: initialize your annotator (the foundation)
    text: The `Annotator` class loads a document and provides methods for rendering
      and annotation manipulation. csharp using (Annotator annotator = new Annotator("path/to/your/document"))
      { // All your preview generation happens within this scope }
  - name: configure your preview options (this is where the magic happens)
    text: The `PreviewOptions` class defines rendering parameters such as format,
      resolution, and whether annotations are included. csharp // Define how each
      page should be handled during preview generation PreviewOptions previewOptions
      = new PreviewOptions(pageNumber => { var pagePath = $"output_directory\\r
  - name: generate the preview (the payoff)
    text: The `GeneratePreview` method processes the document according to the supplied
      options and returns file paths for the created images. csharp annotator.Document.GeneratePreview(previewOptions);
  type: HowTo
- questions:
  - answer: Absolutely! GroupDocs.Annotation supports over 50 formats—including PDF,
      PPTX, XLSX, and common image types. See the [documentation](https://docs.groupdocs.com/annotation/net/)
      for the full list.
    question: Can I preview documents other than DOCX files?
  - answer: Initialise the `Annotator` with a `LoadOptions` object that includes the
      password. The `LoadOptions` class lets you specify the document password and
      other loading parameters.
    question: How do I handle password‑protected documents?
  - answer: Yes. The same code works in ASP.NET, but store generated images in a temporary
      folder and clean them up after the response to avoid disk bloat.
    question: Can I generate previews in a web application?
  - answer: PNG offers the highest quality, JPEG loads faster, and WebP provides the
      best compression if your target browsers support it. PNG is the safest default.
    question: What’s the best output format for web display?
  - answer: Process pages in batches of 5‑10, monitor memory usage, and optionally
      show a progress bar to improve the user experience.
    question: How do I handle very large documents efficiently?
  type: FAQPage
tags:
- groupdocs
- document-preview
- annotations
- dotnet
- csharp
title: Как скрыть аннотации при генерации предварительного просмотра документа в C#
type: docs
url: /ru/net/document-preview/create-document-preview-without-annotations-groupdocs-dotnet/
weight: 1
---

# Как скрыть аннотации при генерации предварительного просмотра документа в C#

Если вам нужно поделиться предварительным просмотром документа, но вы хотите **скрыть аннотации**, вы попали в нужное место. Этот учебник покажет, как генерировать чистые, безаннотационные предварительные просмотры в C# с помощью GroupDocs.Annotation для .NET, охватывая всё от установки до оптимизации производительности.

## Быстрые ответы
- **Какой основной класс создает предварительный просмотр?** Класс `Annotator`.
- **Какая опция отключает аннотации?** Установите `RenderAnnotations = false` в `PreviewOptions`.
- **Минимальная версия .NET?** Рекомендуется .NET 6; также работает .NET Core 3.1.
- **Можно ли просматривать PDF и Word файлы?** Да — поддерживается более 50 форматов.
- **Нужна ли лицензия для тестирования?** Временная лицензия доступна для бесплатных пробных версий.

## Что такое скрытие аннотаций?
*Скрытие аннотаций* — это процесс создания изображений предварительного просмотра документа при подавлении любых комментариев, выделений или разметки, присутствующих в исходном файле. Эта техника гарантирует, что визуальный вывод содержит только оригинальное содержание, что делает его подходящим для публичного распространения, презентаций клиентам или любой ситуации, когда внутренние заметки должны оставаться скрытыми.

## Почему вам нужны чистые предварительные просмотры документов (и как их получить)
Когда вы делитесь предварительным просмотром с клиентами, партнёрами или публично, внутренние комментарии могут выглядеть непрофессионально или даже раскрыть конфиденциальную стратегию. Чистые просмотры сохраняют фокус на содержимом и защищают ваш рабочий процесс. GroupDocs.Annotation позволяет переключать отображение аннотаций, так что вы можете создавать как аннотированные, так и чистые версии из одного исходного файла.

## Что вам понадобится перед началом

### Какие требования?
Чтобы начать, вам необходимо установить следующие компоненты на вашу рабочую машину. Наличие этих элементов гарантирует, что код будет работать без ошибок выполнения и что вы сможете локально протестировать весь конвейер предварительного просмотра.

- GroupDocs.Annotation для .NET 25.4.0 или новее (последний релиз добавляет оптимизированную по памяти генерацию превью).
- Visual Studio 2022 или любой совместимый с .NET IDE.
- Действительная лицензия GroupDocs (временные лицензии бесплатны для оценки).

## Быстрая настройка: добавление GroupDocs.Annotation в ваш проект

### Вариант 1: Консоль менеджера пакетов NuGet
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```

### Вариант 2: .NET CLI (мой личный предпочтительный способ)
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

**Совет:** Держите версию пакета одинаковой у всех членов команды, чтобы избежать тонких различий в отображении.

Проверьте установку с помощью короткой проверки:
```csharp
using System.IO;
using GroupDocs.Annotation;

// This should compile without errors
using (Annotator annotator = new Annotator("path/to/document"))
{
    // You're good to go!
}
```

## Как сгенерировать предварительный просмотр без аннотаций?
Загрузите документ с помощью `Annotator`, настройте `PreviewOptions` и вызовите `GeneratePreview`. Установка `RenderAnnotations = false` сообщает движку исключить каждый комментарий, выделение и штамп из выходных изображений.

### Шаг 1: инициализировать ваш annotator (основа)
Класс `Annotator` загружает документ и предоставляет методы для рендеринга и управления аннотациями.
```csharp
```csharp
using (Annotator annotator = new Annotator("path/to/your/document"))
{
    // All your preview generation happens within this scope
}
```
```

### Шаг 2: настроить параметры предварительного просмотра (здесь происходит магия)
Класс `PreviewOptions` определяет параметры рендеринга, такие как формат, разрешение и включение аннотаций.
```csharp
```csharp
// Define how each page should be handled during preview generation
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = $"output_directory\\result{pageNumber}.png";
    return File.Create(pagePath);
});

// Set the output format for the preview as PNG
previewOptions.PreviewFormat = PreviewFormats.PNG;

// Specify which pages to include in the preview generation
previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};

// The key setting: disable rendering of annotations
previewOptions.RenderAnnotations = false;
```
```

### Шаг 3: сгенерировать предварительный просмотр (результат)
Метод `GeneratePreview` обрабатывает документ согласно переданным параметрам и возвращает пути к созданным изображениям.
```csharp
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
```

## Распространённые проблемы (и как их решить)

### Проблема 1: Ошибки «Файл не найден»
**Симптомы:** Исключение выбрасывается при создании `Annotator`.  
**Решение:** Используйте абсолютные пути или проверьте правильность относительных путей. Краткая проверка выглядит так:
```csharp
string fullPath = Path.GetFullPath("your-document.pdf");
using (Annotator annotator = new Annotator(fullPath))
```

### Проблема 2: Плохое качество предварительного просмотра
**Симптомы:** Выходные изображения выглядят размытыми или пикселизированными.  
**Решение:** Увеличьте значение DPI в `PreviewOptions` для повышения чёткости:
```csharp
previewOptions.Width = 1920;  // Higher resolution
previewOptions.Height = 1080;
```

### Проблема 3: Проблемы с памятью при работе с большими документами
**Симптомы:** `OutOfMemoryException` или заметно медленная обработка.  
**Решение:** Обрабатывайте страницы пакетами вместо загрузки всего файла сразу:
```csharp
// Process 5 pages at a time instead of all at once
previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5};
```

## Реальные примеры использования (где это действительно важно)

### Обмен юридическими документами
Юридические фирмы могут распространять предварительные просмотры контрактов, скрывая внутренние заметки о переговорах, поддерживая профессиональный уровень коммуникаций с клиентами.

### Академическое издание
Исследователи могут делиться чистыми черновиками рукописей после раунда рецензирования, удаляя комментарии рецензентов перед подачей в журнал.

### Бизнес-отчётность
Заинтересованные стороны получают отшлифованные отчёты без заметок типа «проверьте эту цифру» или «обновить перед заседанием совета», которые могли бы подорвать доверие.

### Архивирование документов
Команды по соблюдению нормативов хранят копии без аннотаций, чтобы соответствовать регулятивным требованиям, при этом сохраняют оригинальную аннотированную версию для внутреннего использования.

## Лучшие практики производительности

### Как управлять памятью для больших файлов?
Обрабатывайте страницы небольшими пакетами и своевременно освобождайте `Annotator`. Такой подход снижает пиковое использование памяти до 60 % для документов более 200 страниц.
```csharp
// Good: Dispose properly
using (Annotator annotator = new Annotator(documentPath))
{
    // Generate preview
} // Automatically disposed here

// Avoid: Manual disposal (easy to forget)
Annotator annotator = new Annotator(documentPath);
// ... use annotator
annotator.Dispose(); // Easy to forget or skip due to exceptions
```

### Как ускорить пакетную обработку?
Разбейте документ из 100 страниц на группы по 10 страниц, генерируйте каждую группу последовательно и сохраняйте результаты во временную папку. Эта техника сокращает общее время обработки примерно на 30 % на типичном серверном оборудовании.
```csharp
// Process in batches of 10 pages
for (int startPage = 1; startPage <= totalPages; startPage += 10)
{
    int endPage = Math.Min(startPage + 9, totalPages);
    var pageRange = Enumerable.Range(startPage, endPage - startPage + 1).ToArray();
    
    previewOptions.PageNumbers = pageRange;
    annotator.Document.GeneratePreview(previewOptions);
}
```

### Как выбрать оптимальный формат вывода?
- **PNG:** Наилучшее визуальное качество; идеально для детализированных схем.  
- **JPEG:** Меньший размер файла; подходит для документов с большим объёмом текста, где допустимы небольшие артефакты сжатия.  
- **WebP:** Современный формат с отличным сжатием; проверьте поддержку браузерами перед использованием.

## Расширенные параметры конфигурации

### Как настроить именование файлов?
Лямбда‑выражение `PreviewOptions` позволяет вставлять номера страниц, метки времени или пользовательские идентификаторы в каждое имя файла.
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    string timestamp = DateTime.Now.ToString("yyyyMMdd_HHmmss");
    var pagePath = $"previews\\{timestamp}_page_{pageNumber:D3}.png";
    return File.Create(pagePath);
});
```

### Как контролировать качество изображения?
Отрегулируйте свойства `Width`, `Height` и `Resolution` в `PreviewOptions`. Большие размеры дают более высокое качество ценой увеличения размера файла.
```csharp
previewOptions.Width = 2400;   // Higher resolution
previewOptions.Height = 3200;  // Maintains aspect ratio
previewOptions.PreviewFormat = PreviewFormats.PNG; // Best quality
```

### Как обработать только определённые страницы?
Установите коллекцию `PageNumbers` на точные нужные вам страницы, что уменьшает ввод‑вывод и ускоряет генерацию для документов со сотнями страниц.
```csharp
// Only process odd pages (useful for double-sided documents)
var oddPages = Enumerable.Range(1, totalPages)
                        .Where(p => p % 2 == 1)
                        .ToArray();
previewOptions.PageNumbers = oddPages;
```

## Руководство по устранению неполадок

### Почему генерация предварительного просмотра завершается без ошибок?
Распространённые причины включают:
1. Отсутствует каталог вывода или нет прав на запись.  
2. Исходные документы защищены паролем.  
3. Неподдерживаемый формат файла.  
4. Недостаточно памяти системы.

### Почему аннотации всё ещё отображаются?
Убедитесь, что `RenderAnnotations = false` установлен в экземпляре `PreviewOptions` перед вызовом `GeneratePreview`. Свойство `RenderAnnotations` контролирует, рисуются ли слои аннотаций при рендеринге предварительного просмотра.
```csharp
previewOptions.RenderAnnotations = false;  // Must be explicitly false
previewOptions.RenderComments = false;     // Also disable comments if needed
```

### Почему производительность медленная?
- Снизьте разрешение при тестировании.  
- Обрабатывайте меньше страниц за один пакет.  
- Убедитесь, что используете последнюю версию GroupDocs.Annotation (25.4.0 или новее), содержащую улучшения производительности.

## Когда НЕ следует использовать этот подход
- **Предпросмотр в реальном времени:** Для мгновенных, «на лету» превью клиентская отрисовка может быть быстрее.  
- **Интерактивные документы:** Формы или встроенные скрипты могут потерять функциональность при рендеринге в статические изображения.  
- **Масштабируемая графика:** Если нужны векторные выводы (например, SVG), рассмотрите генерацию страниц PDF вместо растровых изображений.

## Подведение итогов
Создание чистых предварительных просмотров документов без аннотаций просто с GroupDocs.Annotation для .NET. Помните:
1. Правильно освобождайте `Annotator`.  
2. Установите `RenderAnnotations = false` в `PreviewOptions`.  
3. Пакетно обрабатывайте большие файлы, чтобы снизить использование памяти.  
4. Тестируйте с реальными документами, чтобы точно настроить DPI и выбор формата.

Начните с простого тестового файла, поэкспериментируйте с приведёнными выше параметрами, и у вас будут профессиональные превью без аннотаций, готовые для любой аудитории.

## Часто задаваемые вопросы

**Q: Можно ли просматривать документы, отличные от DOCX?**  
A: Конечно! GroupDocs.Annotation поддерживает более 50 форматов — включая PDF, PPTX, XLSX и распространённые типы изображений. См. [documentation](https://docs.groupdocs.com/annotation/net/) для полного списка.

**Q: Как работать с документами, защищёнными паролем?**  
A: Инициализируйте `Annotator` объектом `LoadOptions`, содержащим пароль. Класс `LoadOptions` позволяет указать пароль документа и другие параметры загрузки.
```csharp
LoadOptions loadOptions = new LoadOptions { Password = "your-password" };
using (Annotator annotator = new Annotator("protected-doc.pdf", loadOptions))
```

**Q: Можно ли генерировать превью в веб‑приложении?**  
A: Да. Тот же код работает в ASP.NET, но сохраняйте сгенерированные изображения во временную папку и удаляйте их после ответа, чтобы избежать накопления файлов.

**Q: Какой лучший формат вывода для веб‑отображения?**  
A: PNG обеспечивает наивысшее качество, JPEG загружается быстрее, а WebP предоставляет лучшее сжатие, если целевые браузеры его поддерживают. PNG — самый надёжный вариант по умолчанию.

**Q: Как эффективно обрабатывать очень большие документы?**  
A: Обрабатывайте страницы пакетами по 5‑10, следите за использованием памяти и при желании показывайте индикатор прогресса для улучшения пользовательского опыта.

**Q: Можно ли настроить качество выходного изображения?**  
A: Да — отрегулируйте `Width`, `Height` и `Resolution` в `PreviewOptions`. Большие значения повышают качество, но также увеличивают размер файла.

**Q: Что делать, если нужны как аннотированные, так и чистые версии?**  
A: Запустите генерацию превью дважды — один раз с `RenderAnnotations = true`, второй раз с `false`. Сохраняйте каждый набор в отдельные каталоги для удобного доступа.

## Ресурсы
- [Документация GroupDocs.Annotation .NET](https://docs.groupdocs.com/annotation/net/)  
- [Справочник API GroupDocs Annotation](https://reference.groupdocs.com/annotation/net/)  
- [Выпуски GroupDocs для .NET](https://releases.groupdocs.com/annotation/net/)  
- [Купить лицензию GroupDocs](https://purchase.groupdocs.com/buy)  
- [Бесплатные пробные версии GroupDocs](https://releases.groupdocs.com/annotation/net/)  
- [Запросить временную лицензию](https://purchase.groupdocs.com/temporary-license/)  
- [Форум GroupDocs](https://forum.groupdocs.com/c/annotation/)  

**Последнее обновление:** 2026-10-05  
**Тестировано с:** GroupDocs.Annotation 25.4.0 for .NET  
**Автор:** GroupDocs

## Связанные руководства
- [Как удалить аннотации PDF в C# – Руководство GroupDocs.Annotation](/annotation/net/annotation-management/remove-annotations-groupdocs-annotation-dotnet/)
- [Генерация предварительных просмотров документов без комментариев в .NET](/annotation/net/document-preview/groupdocs-annotation-net-document-preview-no-comments/)
- [Загрузка пользовательских шрифтов .NET — Руководство по интеграции GroupDocs.Annotation](/annotation/net/advanced-usage/loading-custom-fonts/)