---
title: Добавить аннотацию расстояния в документ
linktitle: Добавить аннотацию расстояния в документ
second_title: GroupDocs.Аннотация .NET API
description: Узнайте, как добавлять удаленные аннотации к документам с помощью GroupDocs.Annotation для .NET. Улучшайте сотрудничество и общение без особых усилий.
type: docs
weight: 12
url: /ru/net/unlocking-annotation-power/add-distance-annotation/
---
## Введение
В этом руководстве вы узнаете, как добавить удаленную аннотацию к документу с помощью GroupDocs.Annotation для .NET. Для выполнения задачи выполните следующие действия:
## Предварительные условия

Прежде чем продолжить, убедитесь, что у вас есть следующие предварительные условия:

-  GroupDocs.Annotation для библиотеки .NET: загрузите и установите библиотеку GroupDocs.Annotation для .NET с сайта[эта ссылка](https://releases.groupdocs.com/annotation/net/).
- Документ для аннотации: подготовьте документ (например, PDF), к которому вы хотите добавить аннотацию расстояния.
- Среда разработки: настройте среду разработки с помощью Visual Studio или любой другой IDE по вашему выбору.

## Импортировать пространства имен

Прежде чем начать, обязательно включите в свой код необходимые пространства имен. Эти пространства имен необходимы для доступа к необходимым классам и методам.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Шаг 1. Инициализируйте аннотатор

 Начните с инициализации`Annotator` объект с путем к документу, который вы хотите аннотировать.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Здесь будет находиться код аннотации
}
```

## Шаг 2. Создайте аннотацию расстояния

 Теперь создайте`DistanceAnnotation` объект и настройте его свойства, такие как размеры поля, сообщение, непрозрачность, цвет пера и т. д.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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

## Шаг 3. Добавьте аннотацию

 Добавьте созданную аннотацию расстояния в документ, используя`Add` метод объекта аннотатора.

```csharp
annotator.Add(distance);
```

## Шаг 4: Сохранить документ

Сохраните аннотированный документ в нужном месте вашей системы.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Шаг 5: Отображение подтверждения

Наконец, отобразите сообщение, подтверждающее успешное сохранение аннотированного документа.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Заключение

Добавление удаленных аннотаций к документам с помощью GroupDocs.Annotation for .NET — простой процесс. Следуя шагам, описанным в этом руководстве, вы сможете улучшить свои документы ценными аннотациями, что упростит совместную работу и общение.

## Часто задаваемые вопросы

### Вопрос: Могу ли я настроить внешний вид аннотации расстояния?

О: Да, вы можете настроить различные свойства, такие как цвет, непрозрачность, стиль линий и т. д., в соответствии со своими требованиями.

### Вопрос: Поддерживает ли GroupDocs.Annotation аннотации к документам разных типов?

О: Да, GroupDocs.Annotation поддерживает аннотации в широком спектре форматов документов, включая PDF, Word, Excel, PowerPoint и другие.

### Вопрос: Доступна ли бесплатная пробная версия GroupDocs.Annotation?

 О: Да, вы можете получить доступ к бесплатной пробной версии GroupDocs.Annotation на сайте[эта ссылка](https://releases.groupdocs.com/).

### Вопрос: Где я могу найти документацию по GroupDocs.Annotation для .NET?

 О: Вы можете обратиться к доступной подробной документации.[здесь](https://reference.groupdocs.com/annotation/net/).

### Вопрос: Как я могу получить поддержку или помощь по GroupDocs.Annotation?

 О: Вы можете обратиться за поддержкой и помощью на форум сообщества GroupDocs.Annotation.[здесь](https://forum.groupdocs.com/c/annotation/10).