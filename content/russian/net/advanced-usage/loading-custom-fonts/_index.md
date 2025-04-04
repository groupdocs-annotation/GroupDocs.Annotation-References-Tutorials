---
title: Загрузка пользовательских шрифтов
linktitle: Загрузка пользовательских шрифтов
second_title: GroupDocs.Аннотация .NET API
description: Узнайте, как легко загружать пользовательские шрифты в GroupDocs.Annotation для .NET, чтобы улучшить аннотации документов. Следуйте нашим шагам для легкой интеграции.
weight: 20
url: /ru/net/advanced-usage/loading-custom-fonts/
---

# Загрузка пользовательских шрифтов

## Введение
GroupDocs.Annotation for .NET — это мощная библиотека, которая позволяет разработчикам легко добавлять функции аннотаций в свои .NET-приложения. Одной из ключевых функций, которые он предлагает, является возможность загрузки собственных шрифтов, что обеспечивает расширенную настройку и гибкость аннотаций документов.
## Предварительные условия
Прежде чем приступить к изучению руководства, убедитесь, что у вас есть следующие предварительные условия:
1.  GroupDocs.Annotation для библиотеки .NET: загрузите и установите библиотеку с сайта[здесь](https://releases.groupdocs.com/annotation/net/).
2. Среда разработки .NET. Убедитесь, что у вас настроена рабочая среда для разработки .NET.
3. Доступ к пользовательским шрифтам: подготовьте пользовательские шрифты, которые вы хотите загрузить в свое приложение.

## Импортировать пространства имен
В свой проект .NET импортируйте необходимые пространства имен для использования GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Шаг 1. Создайте экземпляр объекта аннотатора
 Создайте экземпляр`Annotator` класс, указав путь к входному PDF-документу вместе с каталогами пользовательских шрифтов:
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    // Здесь будет находиться ваш код для дальнейших операций
}
```
## Шаг 2. Настройте параметры предварительного просмотра
Определите параметры предварительного просмотра, чтобы указать, как будут создаваться предварительные просмотры документов. Вы можете установить такие параметры, как формат предварительного просмотра, номера страниц и т. д.:
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_with_font_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
```
## Шаг 3. Создайте предварительный просмотр документа
 Используйте`GeneratePreview` метод`Document` свойство для создания предварительного просмотра с использованием пользовательских шрифтов:
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## Шаг 4. Отображение пути вывода
Наконец, отобразите сообщение, указывающее на успешное создание предварительного просмотра документа, а также путь к выходному каталогу:
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## Заключение
В заключение, загрузка пользовательских шрифтов в GroupDocs.Annotation для .NET предоставляет разработчикам возможность гибко настраивать аннотации документов в соответствии со своими требованиями. Следуя шагам, описанным в этом руководстве, вы сможете легко интегрировать пользовательские шрифты в свои приложения .NET и улучшить качество аннотаций для пользователей.
## Часто задаваемые вопросы
### Могу ли я загрузить несколько пользовательских шрифтов одновременно?
 Да, вы можете указать несколько каталогов шрифтов при создании экземпляра.`Annotator` объект.
### Существуют ли какие-либо ограничения на типы поддерживаемых шрифтов?
GroupDocs.Annotation для .NET поддерживает широкий спектр типов шрифтов, включая шрифты TrueType (.ttf) и OpenType (.otf).
### Могу ли я динамически изменять загруженные шрифты во время выполнения?
Да, вы можете динамически изменять каталоги шрифтов и при необходимости перезагружать аннотации к документу.
### Поддерживает ли GroupDocs.Annotation встраивание шрифтов в выходные документы?
Да, вы можете встраивать собственные шрифты в выходные документы, чтобы обеспечить единообразную визуализацию на разных платформах.
### Есть ли способ управлять лицензированием шрифтов в приложении?
GroupDocs.Annotation предоставляет возможности управления лицензированием шрифтов, включая временные лицензии для ознакомительных целей.