---
title: Добавить аннотацию с зачеркиванием текста в документ
linktitle: Добавить аннотацию с зачеркиванием текста в документ
second_title: GroupDocs.Аннотация .NET API
description: Узнайте, как добавлять зачеркивания текста в документы с помощью GroupDocs.Annotation для .NET. Эффективно улучшайте сотрудничество и процессы проверки документов.
type: docs
weight: 26
url: /ru/net/unlocking-annotation-power/add-text-strikeout-annotation/
---
## Введение
В этом руководстве мы рассмотрим, как добавить зачеркнутую текстовую аннотацию в документ с помощью GroupDocs.Annotation для .NET. Эта библиотека предоставляет мощные инструменты для аннотирования различных типов документов, улучшения совместной работы и процессов проверки документов.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующие предварительные условия:
1.  GroupDocs.Annotation для .NET: установите библиотеку. Вы можете скачать его с[здесь](https://releases.groupdocs.com/annotation/net/).
2. Среда разработки: настройте подходящую среду разработки для разработки .NET.
3. Документ: подготовьте документ для аннотирования, например PDF-файл.

## Импорт пространств имен
Сначала импортируйте необходимые пространства имен для доступа к функциям GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Теперь давайте разобьем процесс добавления зачеркнутой аннотации на несколько этапов:
## Шаг 1: Определите выходной путь
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Здесь мы определяем путь вывода, в котором будет сохранен аннотированный документ.
## Шаг 2. Инициализируйте аннотатор
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Инициализируйте объект Annotator, указав путь к входному документу (в данном случае PDF-файлу).
## Шаг 3. Создайте зачеркнутую аннотацию
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    }
};
```
Создайте объект StrikeoutAnnotation с нужными свойствами, такими как сообщение, непрозрачность, номер страницы, цвет фона, точки (координаты) и ответы.
## Шаг 4. Добавьте аннотацию
```csharp
annotator.Add(strikeout);
```
Добавьте в документ созданную зачеркнутую аннотацию.
## Шаг 5: Сохранить документ
```csharp
annotator.Save(outputPath);
```
Сохраните документ с аннотациями в указанном пути вывода.

## Заключение
В этом уроке мы узнали, как добавить в документ зачеркнутую текстовую аннотацию с помощью GroupDocs.Annotation для .NET. Эта мощная библиотека обеспечивает эффективное аннотирование документов, улучшая процессы совместной работы и проверки документов.
## Часто задаваемые вопросы
### Совместим ли GroupDocs.Annotation с различными форматами документов?
Да, GroupDocs.Annotation поддерживает широкий спектр форматов документов, включая PDF, Word, Excel, PowerPoint и другие.
### Могу ли я настроить внешний вид аннотаций?
Конечно, вы можете настроить свойства аннотаций, такие как цвет, непрозрачность, размер шрифта и т. д., в соответствии с вашими требованиями.
### Предоставляет ли GroupDocs.Annotation функции совместной работы?
Да, GroupDocs.Annotation облегчает совместную работу, позволяя пользователям добавлять комментарии, ответы и аннотации к документам.
### Доступна ли бесплатная пробная версия?
 Да, вы можете воспользоваться бесплатной пробной версией на[здесь](https://releases.groupdocs.com/).
### Где я могу получить поддержку для GroupDocs.Annotation?
 Вы можете получить поддержку от[Форум GroupDocs.Аннотации](https://forum.groupdocs.com/c/annotation/10).