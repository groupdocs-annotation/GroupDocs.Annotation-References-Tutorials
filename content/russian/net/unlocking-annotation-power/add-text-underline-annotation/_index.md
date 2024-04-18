---
title: Добавить аннотацию с подчеркиванием текста в документ
linktitle: Добавить аннотацию с подчеркиванием текста в документ
second_title: GroupDocs.Аннотация .NET API
description: Узнайте, как добавлять к документам аннотации с подчеркиванием текста с помощью GroupDocs.Annotation для .NET. Улучшайте сотрудничество и общение без особых усилий.
type: docs
weight: 27
url: /ru/net/unlocking-annotation-power/add-text-underline-annotation/
---
## Введение
В этом руководстве мы рассмотрим процесс добавления аннотации с подчеркиванием текста в документ с помощью GroupDocs.Annotation для .NET. Аннотации с подчеркиванием текста могут быть полезны для выделения определенных частей документа, например важных отрывков или ключевых моментов.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас установлены следующие необходимые компоненты:
1.  GroupDocs.Annotation для .NET: загрузите и установите GroupDocs.Annotation для .NET с сайта[здесь](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: убедитесь, что в вашей системе установлена .NET Framework.

## Импорт пространств имен
Для начала давайте импортируем необходимые пространства имен в наш проект:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Теперь давайте разобьем пример на несколько этапов:
## Шаг 1: Определите выходной путь
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
На этом этапе мы определяем выходной путь, в котором будет сохранен документ с аннотациями.
## Шаг 2. Инициализируйте аннотатор
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Здесь мы инициализируем экземпляр`Annotator` класс, указав путь к входному документу.
## Шаг 3. Создайте аннотацию с подчеркиванием
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // работает, поддерживаются только документы Word и PDF
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
 Этот шаг предполагает создание`UnderlineAnnotation`объект с различными свойствами, такими как цвет шрифта, сообщение, непрозрачность, номер страницы, цвет фона, цвет подчеркивания, точки и ответы.
## Шаг 4. Добавьте аннотацию в документ
```csharp
annotator.Add(underline);
```
Здесь мы добавляем подчеркнутую аннотацию к документу.
## Шаг 5. Сохраните документ с аннотациями
```csharp
annotator.Save(outputPath);
```
Наконец, мы сохраняем аннотированный документ в указанном пути вывода.

## Заключение
В этом уроке мы узнали, как добавить в документ аннотацию с подчеркиванием текста с помощью GroupDocs.Annotation для .NET. Эта мощная библиотека предоставляет различные варианты аннотаций для улучшения совместной работы над документами и общения.
## Часто задаваемые вопросы
### Могу ли я настроить внешний вид подчеркнутой аннотации?
Да, вы можете настроить такие свойства, как цвет, непрозрачность и положение, в соответствии со своими требованиями.
### Совместим ли GroupDocs.Annotation с различными форматами документов?
Да, GroupDocs.Annotation поддерживает широкий спектр форматов документов, включая Word и PDF.
### Могу ли я добавить несколько аннотаций в один документ?
Конечно, GroupDocs.Annotation позволяет добавлять в документ несколько аннотаций разных типов.
### Доступна ли бесплатная пробная версия для GroupDocs.Annotation?
 Да, вы можете получить доступ к бесплатной пробной версии с[здесь](https://releases.groupdocs.com/).
### Где я могу получить поддержку для GroupDocs.Annotation?
 Вы можете получить поддержку на форуме сообщества GroupDocs.Annotation.[здесь](https://forum.groupdocs.com/c/annotation/10).