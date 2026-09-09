---
categories:
- .NET Development
date: '2026-06-26'
description: Узнайте, как получать форматы с помощью GroupDocs.Annotation для .NET,
  устранять проблемы с неподдерживаемыми типами файлов и применять проверку по лучшим
  практикам.
keywords:
- how to retrieve formats
- troubleshoot unsupported file format
- GroupDocs.Annotation .NET
lastmod: '2026-06-26'
linktitle: Получить поддерживаемые форматы файлов .NET
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  headline: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete
    Guide
  type: TechArticle
- description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  name: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete Guide
  steps:
  - name: Verify installation
    text: Run `dotnet list package` or check the NuGet console output for any warnings.
  - name: Check license status
    text: Ensure `License.SetLicense("path/to/license.json")` executes before any
      API call.
  - name: Diagnose environment constraints
    text: '- Confirm .NET runtime version matches the library’s requirements. - Verify
      the process has read/write permissions for the temporary folder used by GroupDocs.Annotation.'
  type: HowTo
- questions:
  - answer: The library supports **over 50 formats**, including PDF, DOCX, XLSX, PPTX,
      JPEG, PNG, TIFF, and many others. Run the sample code to retrieve the exact
      list for your license.
    question: What file formats does GroupDocs.Annotation actually support?
  - answer: This usually points to a licensing issue—either an expired trial or an
      incorrectly loaded license file. Re‑apply a valid license and restart the app.
    question: Why am I getting fewer supported formats than expected?
  - answer: No direct “IsSupported” method exists; the recommended approach is to
      cache the full list once and query it locally for fast lookups.
    question: Can I check a single format without pulling the whole list?
  - answer: Initialise the format cache at application startup (e.g., in `ConfigureServices`)
      and store it in a static or singleton service. This eliminates per‑request overhead.
    question: How should I handle format checking in a high‑traffic web app?
  - answer: Exceptions typically stem from licensing or corrupted installations. Verify
      the package integrity, re‑install if needed, and ensure the license file is
      accessible.
    question: What if GetSupportedFileTypes() throws an exception?
  type: FAQPage
tags:
- GroupDocs.Annotation
- file-formats
- document-processing
- dotnet-tutorial
title: Как получить форматы в .NET с помощью GroupDocs.Annotation – Полное руководство
type: docs
url: /ru/net/document-information/retrieve-supported-file-formats-groupdocs-annotation-net/
weight: 1
---

# Как получить форматы в .NET с помощью GroupDocs.Annotation

## Введение

Когда‑нибудь задавались вопросом, какие файловые форматы действительно поддерживает ваше .NET‑приложение для аннотирования документов? **Как получить форматы** — вопрос, который задают многие разработчики, когда им нужно проверять загружаемые пользователями файлы или создавать динамические фильтры UI. Точное знание того, какие форматы поддерживает ваша реализация GroupDocs.Annotation, полезно, но в то же время необходимо для построения надёжных приложений, которые не падают из‑за неожиданного типа файла.

В этом руководстве вы узнаете, как программно получить и проверить поддерживаемые форматы файлов с помощью GroupDocs.Annotation для .NET. Мы пройдём базовую реализацию, покажем, как превратить сырой список в удобный выпадающий список для конечных пользователей, а также рассмотрим практические советы по устранению неполадок, чтобы вы могли уверенно справляться с любой ситуацией, связанной с форматами документов.

**Что вы получите**

- Чёткое понимание возможностей GroupDocs.Annotation в отношении форматов файлов  
- Готовый к запуску код, который получает и отображает каждый поддерживаемый формат  
- Проверенные стратегии кэширования, обработки ошибок и особенностей лицензирования  
- Рекомендации лучшей практики для проверки типов файлов в продакшене  

Давайте разберём эту головоломку с форматами раз и навсегда.

## Быстрые ответы
- **Что значит «как получить форматы»?** Это программный способ спросить GroupDocs.Annotation, какие расширения он может аннотировать.  
- **Какие основные форматы поддерживаются «из коробки»?** Более 50, включая PDF, DOCX, XLSX, PPTX, JPEG, PNG и TIFF.  
- **Нужна ли лицензия для получения полного списка?** Да — активная коммерческая или пробная лицензия открывает полный каталог.  
- **Рекомендуется ли кэшировать список форматов?** Определённо; кэширование избавляет от лишних вызовов и ускоряет отклик.  
- **Как проверить загрузку файла против списка?** Сравните расширение файла с кэшированной коллекцией поддерживаемых расширений.

## Что значит «как получить форматы»?
**Как получить форматы** — процесс вызова API GroupDocs.Annotation для получения коллекции всех типов файлов, которые библиотека может аннотировать. Эта операция возвращает только‑для‑чтения список объектов `FileType`, содержащих как расширение файла, так и дружественное описание.

## Почему стоит использовать GroupDocs.Annotation для обнаружения форматов?
GroupDocs.Annotation поддерживает **более 50 входных и выходных форматов** — включая PDF, Microsoft Office (Word, Excel, PowerPoint) и распространённые типы изображений — при обработке многосотстраничных документов без загрузки всего файла в память. Такая измеримая возможность делает её надёжным выбором для аннотационных конвейеров корпоративного уровня.

## Предварительные требования и настройка среды

### Что вам понадобится
- **IDE:** Visual Studio 2019 или новее (Community‑издание подходит)  
- **Целевая платформа:** .NET Framework 4.6.1 + или .NET Core 2.0 +   
- **Базовые знания C#:** Если умеете писать приложение «Hello World», вы готовы  

### Установка GroupDocs.Annotation
Самый простой способ — через NuGet. Выберите метод, соответствующий вашему рабочему процессу:

**Вариант 1: Package Manager Console**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**Вариант 2: .NET CLI**  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

**Совет:** В ограниченных корпоративных средах скачайте пакет вручную с [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/) и подключите DLL локально.

### Лицензирование без проблем
- **Разработка и тестирование:** Начните с бесплатной пробной версии для полной функциональности.  
- **Расширенная оценка:** Возьмите [временную лицензию](https://purchase.groupdocs.com/temporary-license/) (выдаётся за ~5 минут).  
- **Продакшн:** Приобретите коммерческую лицензию на [GroupDocs Purchase](https://purchase.groupdocs.com/buy); одна лицензия покрывает все сценарии развертывания.

## Как программно получить поддерживаемые форматы файлов?

Загрузите поддерживаемые форматы одним вызовом `FileType.GetSupportedFileTypes()` и затем преобразуйте результат в удобный список для UI‑элементов или проверки. Метод возвращает только‑для‑чтения коллекцию объектов `FileType`, каждый из которых содержит расширение и описание, что упрощает работу.

```csharp
var supported = FileType.GetSupportedFileTypes()
                         .OrderBy(f => f.Extension)
                         .Select(f => new { f.Extension, f.Description })
                         .ToList();
```

Код выше запрашивает внутренние метаданные GroupDocs.Annotation, сортирует расширения в алфавитном порядке и возвращает лёгкую коллекцию, которую можно привязать к элементам UI или использовать для валидации.

### Определение: класс FileType
Класс `FileType` — представление GroupDocs.Annotation одного формата документа, раскрывающее свойства `Extension` и `Description`.  

### Пошаговое руководство
1. **Подключите пространство имён** — `using GroupDocs.Annotation;` в начале файла.  
2. **Вызовите статический метод** — `FileType.GetSupportedFileTypes()` возвращает `IEnumerable<FileType>`.  
3. **Сортировка и проекция** — используйте LINQ `OrderBy` и `Select` для формирования данных для отображения.  
4. **Отображение** — пройдитесь по списку в консоли, MVC‑вью или выпадающем списке WinForms.

```csharp
using System;
using System.Linq;
using GroupDocs.Annotation; // This is where the FileType class lives
```  

## Как кэшировать список форматов для продакшн‑использования?

Кэширование устраняет повторные обращения к метаданным и гарантирует субмиллисекундные времена отклика для каждого запроса, что критично в приложениях с высоким трафиком. Сохраняя список форматов в статическом поле и загружая его лениво при первом обращении, вы обеспечиваете единовременное получение данных и их эффективное повторное использование на протяжении всего жизненного цикла приложения.

```csharp
public static class FormatCache
{
    private static IReadOnlyList<FileType> _cachedFormats;

    public static IReadOnlyList<FileType> SupportedFormats =>
        _cachedFormats ??= FileType.GetSupportedFileTypes()
                                    .OrderBy(f => f.Extension)
                                    .ToList();
}
```

```csharp
public static void RunGetSupportedFileFormats()
{
    // Retrieve collection of supported file types, ordered by their extension
    IEnumerable<FileType> fileTypes = FileType.GetSupportedFileTypes().OrderBy(fileType => fileType.Extension);

    // Iterate through each FileType object and output its details to the console
    foreach (FileType fileType in fileTypes)
        Console.WriteLine($"{fileType.Extension} - {fileType.Name}");
}
```  

**Зачем кэшировать?** Набор поддерживаемых форматов не меняется во время выполнения, поэтому однократная загрузка при старте приложения экономит CPU‑циклы и избавляет от потенциальных проверок лицензии при каждом вызове.

## Распространённые проблемы и их решения

### Проблема 1: ошибка компиляции «GroupDocs.Annotation not found»
**Прямой ответ:** Убедитесь, что пакет NuGet установлен корректно, выполните очистку и пересборку решения, и проверьте, что целевая платформа соответствует поддерживаемым версиям пакета.  

**Анализ причины** — отсутствие ссылки, несовместимая платформа или ограничения корпоративного источника пакетов.

### Проблема 2: пустой или неполный список форматов
**Прямой ответ:** Просроченная или неправильно настроенная лицензия часто обрезает список; примените действительный файл лицензии и перезапустите приложение.  

**Возможные причины:**  
- Файл лицензии не загружен (`License.SetLicense("license.json")` отсутствует)  
- Повреждённый пакет NuGet  
- Отсутствуют нативные зависимости  

**Быстрое решение:**  
```csharp
public static void DiagnoseFormatIssues()
{
    try
    {
        var formats = FileType.GetSupportedFileTypes();
        Console.WriteLine($"Found {formats.Count()} supported formats");
        
        if (formats.Count() < 10) // GroupDocs supports many more formats
        {
            Console.WriteLine("Warning: Fewer formats than expected. Check your license.");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Cannot retrieve formats: {ex.Message}");
        // This usually indicates a licensing or installation issue
    }
}
```  

### Проблема 3: падение производительности из‑за частых вызовов
**Прямой ответ:** Кэшируйте результат, как показано в разделе «Как кэшировать»; последующие вызовы становятся O(1).  

**Совет по реализации:** Храните список в `MemoryCache` или статическом поле и обновляйте только при обновлении библиотеки.

```csharp
public static class FileFormatCache
{
    private static List<FileType> _cachedFormats;
    
    public static IEnumerable<FileType> GetSupportedFormats()
    {
        if (_cachedFormats == null)
        {
            _cachedFormats = FileType.GetSupportedFileTypes().ToList();
        }
        return _cachedFormats;
    }
}
```  

## Реальные сценарии и примеры использования

### Как проверять загрузку файлов, используя кэшированный список?
Когда пользователь отправляет документ, извлеките расширение файла и сравните его с кэшированной коллекцией:

```csharp
bool IsSupported(string fileName)
{
    var ext = Path.GetExtension(fileName).ToLowerInvariant();
    return FormatCache.SupportedFormats.Any(f => f.Extension.Equals(ext, StringComparison.OrdinalIgnoreCase));
}
```

```csharp
public bool IsFileSupported(string fileName)
{
    var extension = Path.GetExtension(fileName).ToLowerInvariant();
    var supportedExtensions = GetSupportedExtensions();
    return supportedExtensions.Contains(extension);
}
```  

### Как сформировать динамический фильтр файлов для OpenFileDialog?
Сформируйте строку фильтра диалога из кэшированных расширений, чтобы UI всегда отражал возможности библиотеки:

```csharp
var filter = string.Join(";", FormatCache.SupportedFormats.Select(f => $"*{f.Extension}"));
openFileDialog.Filter = $"Supported Files ({filter})|{filter}";
```

```csharp
public string GenerateFileFilter()
{
    var extensions = GetSupportedExtensions();
    var filterParts = extensions.Select(ext => $"*{ext}");
    return $"Supported Documents|{string.Join(";", filterParts)}";
}
```  

### Как пропускать неподдерживаемые файлы при пакетном сканировании папки?
Пройдитесь по каталогу, проверьте каждый файл с помощью `IsSupported` и обрабатывайте только допустимые:

```csharp
foreach (var file in Directory.EnumerateFiles(folderPath))
{
    if (IsSupported(file))
    {
        // Process with GroupDocs.Annotation
    }
}
```

```csharp
public void ProcessDirectory(string directoryPath)
{
    var supportedExtensions = GetSupportedExtensions();
    var files = Directory.GetFiles(directoryPath)
        .Where(file => supportedExtensions.Contains(Path.GetExtension(file).ToLowerInvariant()));
    
    foreach (var file in files)
    {
        // Process each supported file
        ProcessAnnotationFile(file);
    }
}
```  

## Соображения по производительности и лучшие практики

- **Кэшировать один раз, использовать везде** — инициализируйте `FormatCache` при старте приложения (например, в `Program.cs` или `Startup.cs`).  
- **Ленивая загрузка** — статическое свойство гарантирует загрузку списка только при первом обращении, избегая лишних задержек при старте.  
- **Потокобезопасность** — оператор объединения с null (`??=`) безопасен для большинства однопоточных сценариев; для высококонкурентных приложений оберните кэш в `Lazy<IReadOnlyList<FileType>>`.  
- **Освобождайте объекты аннотации** — хотя сам список форматов не требует освобождения, любые созданные экземпляры `Annotation` следует помещать в `using`, чтобы освободить нативные ресурсы.  

### Шаблон обработки ошибок для проблем с лицензией
Обёрните получение форматов в блок try‑catch, который специально ловит `LicenseException` и записывает понятное сообщение:

```csharp
try
{
    var formats = FileType.GetSupportedFileTypes();
}
catch (LicenseException ex)
{
    // Log and fallback to a hard‑coded minimal list
}
```

```csharp
public static class RobustFormatRetrieval
{
    public static IEnumerable<FileType> GetSupportedFormatsWithFallback()
    {
        try
        {
            return FileType.GetSupportedFileTypes();
        }
        catch (LicenseException)
        {
            // Handle licensing issues gracefully
            LogWarning("License issue detected. Using basic format list.");
            return GetBasicFormatList();
        }
        catch (Exception ex)
        {
            LogError($"Unexpected error retrieving formats: {ex}");
            return Enumerable.Empty<FileType>();
        }
    }
    
    private static IEnumerable<FileType> GetBasicFormatList()
    {
        // Return a hardcoded list of common formats as fallback
        // This ensures your app doesn't break completely
        return new[] { FileType.Pdf, FileType.Docx, FileType.Xlsx };
    }
}
```  

## Руководство по устранению неполадок

### Шаг 1: проверка установки
Выполните `dotnet list package` или проверьте вывод консоли NuGet на наличие предупреждений.  

```csharp
public static void VerifyInstallation()
{
    try
    {
        var version = typeof(FileType).Assembly.GetName().Version;
        Console.WriteLine($"GroupDocs.Annotation version: {version}");
        
        var formatCount = FileType.GetSupportedFileTypes().Count();
        Console.WriteLine($"Supported formats: {formatCount}");
        
        if (formatCount > 50) // Expected range
        {
            Console.WriteLine("✓ Installation looks good!");
        }
        else
        {
            Console.WriteLine("⚠ Possible installation or licensing issue");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"✗ Installation problem: {ex.Message}");
    }
}
```  

### Шаг 2: проверка статуса лицензии
Убедитесь, что `License.SetLicense("path/to/license.json")` вызывается до любого обращения к API.  

### Шаг 3: диагностика ограничений среды
- Убедитесь, что версия .NET Runtime соответствует требованиям библиотеки.  
- Проверьте, что процесс имеет права чтения/записи во временной папке, используемой GroupDocs.Annotation.  

## Часто задаваемые вопросы

**В опросе:** Какие форматы файлов действительно поддерживает GroupDocs.Annotation?  
**Ответ:** Библиотека поддерживает **более 50 форматов**, включая PDF, DOCX, XLSX, PPTX, JPEG, PNG, TIFF и многие другие. Запустите пример кода, чтобы получить точный список для вашей лицензии.

**В опросе:** Почему я получаю меньше поддерживаемых форматов, чем ожидал?  
**Ответ:** Чаще всего это проблема лицензии — истёкший пробный период или неверно загруженный файл лицензии. Примените действительную лицензию и перезапустите приложение.

**В опросе:** Можно ли проверить отдельный формат без получения полного списка?  
**Ответ:** Прямого метода «IsSupported» нет; рекомендуется один раз кэшировать полный список и выполнять локальные быстрые проверки.

**В опросе:** Как обрабатывать проверку форматов в веб‑приложении с высоким трафиком?  
**Ответ:** Инициализируйте кэш форматов при старте приложения (например, в `ConfigureServices`) и храните его в статическом или singleton‑сервисе. Это устраняет нагрузку на каждый запрос.

**В опросе:** Что делать, если `GetSupportedFileTypes()` бросает исключение?  
**Ответ:** Исключения обычно связаны с лицензированием или повреждённой установкой. Проверьте целостность пакета, переустановите при необходимости и убедитесь, что файл лицензии доступен.

## Заключение

Теперь у вас есть полная, готовая к продакшну стратегия **как получить форматы** с помощью GroupDocs.Annotation в .NET. От однострочного вызова API до надёжного кэширования, обработки ошибок и интеграции в UI — вы можете уверенно проверять загрузки, генерировать динамические фильтры файлов и строить масштабируемые аннотационные конвейеры.

**Следующие шаги:**  
- Изучите [GroupDocs.Annotation API Reference](https://reference.groupdocs.com/annotation/net/) для более глубоких возможностей аннотации.  
- Присоединяйтесь к сообществу на [Support Forum](https://forum.groupdocs.com/c/annotation/), если столкнётесь с редкими сценариями.  
- Поэкспериментируйте с комбинированием проверки форматов и пользовательских бизнес‑правил (например, ограничения по размеру, сканирование на безопасность), чтобы ещё больше укрепить ваш документооборот.

## Ресурсы
- [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/)
- [Download Latest Version](https://releases.groupdocs.com/annotation/net/)
- [Free Trial](https://releases.groupdocs.com/annotation/net/)
- [temporary license](https://purchase.groupdocs.com/temporary-license/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [GroupDocs Purchase](https://purchase.groupdocs.com/buy)
- [Purchase Licensing](https://purchase.groupdocs.com/buy)
- [Documentation](https://docs.groupdocs.com/annotation/net/)
- [API Reference](https://reference.groupdocs.com/annotation/net/)
- [GroupDocs.Annotation API Reference](https://reference.groupdocs.com/annotation/net/)
- [Support Forum](https://forum.groupdocs.com/c/annotation/)
- [Community Support](https://forum.groupdocs.com/c/annotation/)

---

**Последнее обновление:** 2026-06-26  
**Тестировано с:** GroupDocs.Annotation 25.4.0 for .NET  
**Автор:** GroupDocs  

---

```csharp
public static List<string> GetSupportedExtensions()
{
    try
    {
        var supportedExtensions = FileType.GetSupportedFileTypes()
            .Select(ft => ft.Extension.ToLowerInvariant())
            .OrderBy(ext => ext)
            .ToList();
        
        return supportedExtensions;
    }
    catch (Exception ex)
    {
        // Log the error appropriately in your application
        Console.WriteLine($"Error retrieving supported formats: {ex.Message}");
        return new List<string>();
    }
}
```

## Связанные руководства

- [Document Metadata Extraction .NET - Complete Guide to GroupDocs.Annotation](/annotation/net/document-information/)
- [Load PDF from URL .NET - Complete Guide with GroupDocs.Annotation](/annotation/net/document-loading-essentials/load-document-from-url/)
- [Document Preview .NET Tutorials - Complete GroupDocs.Annotation Guide](/annotation/net/document-preview/)