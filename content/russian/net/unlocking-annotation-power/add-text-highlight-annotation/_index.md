---
title: Добавить аннотацию выделения текста в документ
linktitle: Добавить аннотацию выделения текста в документ
second_title: GroupDocs.Аннотация .NET API
description: Узнайте, как добавлять аннотации выделения текста в документы с помощью GroupDocs.Annotation для .NET. Улучшите сотрудничество и производительность с помощью этого комплексного решения.
weight: 22
url: /ru/net/unlocking-annotation-power/add-text-highlight-annotation/
---

# Добавить аннотацию выделения текста в документ

## Введение
В сфере управления документами и совместной работы GroupDocs.Annotation для .NET представляет собой надежное решение, позволяющее разработчикам легко интегрировать аннотации с выделением текста в свои приложения. Это руководство представляет собой подробное руководство по добавлению аннотаций выделения текста в документы с помощью GroupDocs.Annotation для .NET. Благодаря пошаговым инструкциям и подробным объяснениям вы приобретете навыки использования возможностей этой мощной библиотеки.
## Предварительные условия
Прежде чем углубляться в реализацию аннотаций выделения текста, убедитесь, что у вас есть следующие предварительные условия:
1. Настройка среды: настройте подходящую среду разработки для разработки .NET.
2.  Установка GroupDocs.Annotation для .NET: Загрузите и установите GroupDocs.Annotation для .NET из прилагаемого файла.[ссылка для скачивания](https://releases.groupdocs.com/annotation/net/).
3. Знакомство с C#: базовое понимание языка программирования C#.
4. Документ для аннотации: подготовьте документ (например, PDF), который вы хотите аннотировать.

## Импортировать пространства имен
Для начала импортируйте необходимые пространства имен в свой код C#, чтобы использовать функциональные возможности GroupDocs.Annotation для .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Теперь давайте разобьем процесс добавления аннотаций выделения текста на несколько этапов:
## Шаг 1: Определите выходной путь
Укажите выходной путь, в котором будет сохранен документ с аннотациями:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Шаг 2. Инициализируйте аннотатор
 Создайте экземпляр`Annotator` класс, передав имя файла документа в качестве параметра:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Шаг 3. Создайте аннотацию выделения
 Создать экземпляр`HighlightAnnotation` объект и настройте его свойства:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
## Шаг 4. Добавьте аннотацию
Добавьте созданную аннотацию выделения в документ:
```csharp
annotator.Add(highlight);
```
## Шаг 5. Сохраните документ с аннотациями
Сохраните аннотированный документ в указанном пути вывода:
```csharp
annotator.Save(outputPath);
```

## Заключение
В заключение, GroupDocs.Annotation для .NET предлагает оптимизированный подход для включения аннотаций выделения текста в документы. Следуя шагам, описанным в этом руководстве, разработчики могут легко улучшить совместную работу с документами и повысить производительность в своих приложениях.
## Часто задаваемые вопросы
### Совместим ли GroupDocs.Annotation для .NET со всеми форматами документов?
GroupDocs.Annotation для .NET поддерживает различные форматы документов, включая PDF, Word, Excel и другие. Полный список см. в документации.
### Можно ли настроить аннотации в соответствии с конкретными требованиями?
Да, разработчики имеют полный контроль над свойствами и внешним видом аннотаций, что позволяет настраивать их в соответствии с различными потребностями.
### Доступна ли бесплатная пробная версия GroupDocs.Annotation для .NET?
 Да, вы можете изучить возможности GroupDocs.Annotation для .NET, открыв бесплатную пробную версию на предоставленном сайте.[связь](https://releases.groupdocs.com/).
### Как я могу получить поддержку по любым вопросам или вопросам, связанным с GroupDocs.Annotation для .NET?
 Для получения поддержки и помощи посетите форум GroupDocs.Annotation.[здесь](https://forum.groupdocs.com/c/annotation/10).
### Какие варианты лицензирования доступны для GroupDocs.Annotation для .NET?
 GroupDocs.Annotation для .NET предлагает различные варианты лицензирования, включая временные лицензии для целей тестирования и коммерческие лицензии для производственных сред. Посетите страницу покупки[здесь](https://purchase.groupdocs.com/buy) Больше подробностей.