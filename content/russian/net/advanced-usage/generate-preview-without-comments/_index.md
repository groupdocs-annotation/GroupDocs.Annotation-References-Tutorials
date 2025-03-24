---
title: Создать предварительный просмотр без комментариев
linktitle: Создать предварительный просмотр без комментариев
second_title: GroupDocs.Аннотация .NET API
description: Узнайте, как легко интегрировать возможности аннотирования документов в ваши приложения .NET с помощью GroupDocs.Annotation for .NET.
weight: 14
url: /ru/net/advanced-usage/generate-preview-without-comments/
---
## Введение
GroupDocs.Annotation for .NET — это мощный инструмент, который позволяет разработчикам легко включать функции аннотаций в свои .NET-приложения. Независимо от того, работаете ли вы над системой управления документами, платформой для совместной работы или любым другим приложением, требующим возможности аннотирования документов, GroupDocs.Annotation предоставляет полный набор инструментов для улучшения функциональности вашего приложения.
## Предварительные условия
Прежде чем приступить к использованию GroupDocs.Annotation для .NET, убедитесь, что у вас настроены следующие предварительные условия:
### 1. Установите GroupDocs.Annotation для .NET.
 Для начала вам необходимо скачать и установить GroupDocs.Annotation для .NET. Вы можете найти ссылку для скачивания[здесь](https://releases.groupdocs.com/annotation/net/). Следуйте инструкциям по установке, приведенным в документации, чтобы процесс установки прошел гладко.
### 2. Получить лицензию
 GroupDocs.Annotation для .NET требует лицензии для коммерческого использования. Вы можете приобрести лицензию у[здесь](https://purchase.groupdocs.com/buy) или выберите временную лицензию[здесь](https://purchase.groupdocs.com/temporary-license/) в целях тестирования.
### 3. Знакомство с .NET Framework.
Базовые знания .NET Framework и языка программирования C# необходимы для эффективного использования GroupDocs.Annotation для .NET.

## Импортировать пространства имен
Теперь, когда вы настроили необходимые условия, давайте импортируем необходимые пространства имен в ваше .NET-приложение.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

Следуйте этим пошаговым инструкциям, чтобы создать предварительный просмотр без комментариев с помощью GroupDocs.Annotation для .NET:
## Шаг 1. Инициализируйте аннотатор
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## Шаг 2. Настройте параметры предварительного просмотра
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## Шаг 3. Укажите формат предварительного просмотра и номера страниц.
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## Шаг 4. Отключите отображение комментариев
```csharp
    previewOptions.RenderComments = false;
```
## Шаг 5: Создайте предварительный просмотр
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
После выполнения этих шагов ваше .NET-приложение сможет создать предварительный просмотр указанных страниц документа без отображения комментариев.

## Заключение
Включение функций аннотаций в ваши приложения .NET стало еще проще благодаря GroupDocs.Annotation for .NET. Следуя шагам, описанным в этом руководстве, вы сможете легко интегрировать возможности аннотирования документов в свои приложения, улучшая совместную работу и управление документами.
## Часто задаваемые вопросы
### Совместим ли GroupDocs.Annotation для .NET со всеми форматами документов?
GroupDocs.Annotation для .NET поддерживает широкий спектр форматов документов, включая PDF, DOCX, PPTX, XLSX и другие.
### Могу ли я настроить внешний вид аннотаций, созданных с помощью GroupDocs.Annotation for .NET?
Да, GroupDocs.Annotation для .NET предоставляет широкие возможности настройки, позволяющие адаптировать внешний вид аннотаций в соответствии с потребностями вашего приложения.
### Поддерживает ли GroupDocs.Annotation для .NET многопользовательскую совместную работу?
Да, GroupDocs.Annotation for .NET предлагает функции совместного аннотирования, позволяющие нескольким пользователям одновременно комментировать документы.
### Доступна ли техническая поддержка для GroupDocs.Annotation для .NET?
 Да, техническая поддержка GroupDocs.Annotation для .NET доступна через[форум поддержки](https://forum.groupdocs.com/c/annotation/10).
### Могу ли я бесплатно попробовать GroupDocs.Annotation для .NET перед покупкой?
 Да, вы можете изучить возможности GroupDocs.Annotation для .NET, загрузив бесплатную пробную версию.[здесь](https://releases.groupdocs.com/).