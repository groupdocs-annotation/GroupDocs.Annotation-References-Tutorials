---
"description": "Узнайте, как добавлять аннотации на расстоянии к документам с помощью GroupDocs.Annotation для .NET. Улучшайте сотрудничество и общение без усилий."
"linktitle": "Добавить аннотацию расстояния к документу"
"second_title": "GroupDocs.Аннотация .NET API"
"title": "Добавить аннотацию расстояния к документу"
"url": "/ru/net/unlocking-annotation-power/add-distance-annotation/"
type: docs
"weight": 12
---

# Добавить аннотацию расстояния к документу

## Введение
В этом уроке вы узнаете, как добавить аннотацию расстояния к документу с помощью GroupDocs.Annotation для .NET. Выполните следующие шаги для выполнения задачи:
## Предпосылки

Прежде чем продолжить, убедитесь, что выполнены следующие предварительные условия:

- GroupDocs.Annotation for .NET Library: Загрузите и установите библиотеку GroupDocs.Annotation for .NET с сайта [эта ссылка](https://releases.groupdocs.com/annotation/net/).
- Документ для аннотирования: подготовьте документ (например, PDF), к которому вы хотите добавить аннотацию расстояния.
- Среда разработки: настройте среду разработки с помощью Visual Studio или любой другой IDE по вашему выбору.

## Импорт пространств имен

Прежде чем начать, убедитесь, что вы включили необходимые пространства имен в свой код. Эти пространства имен необходимы для доступа к требуемым классам и методам.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Шаг 1: Инициализация аннотатора

Начните с инициализации `Annotator` объект с путем к документу, который вы хотите аннотировать.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Код аннотации будет здесь
}
```

## Шаг 2: Создание аннотации расстояния

Теперь создайте `DistanceAnnotation` объект и настройте его свойства, такие как размеры поля, сообщение, прозрачность, цвет пера и т. д.

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

## Шаг 3: Добавьте аннотацию

Добавьте созданную аннотацию расстояния в документ с помощью `Add` метод объекта аннотатора.

```csharp
annotator.Add(distance);
```

## Шаг 4: Сохраните документ

Сохраните аннотированный документ в нужном месте в вашей системе.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Шаг 5: Отображение подтверждения

В заключение отобразите сообщение, подтверждающее успешное сохранение аннотированного документа.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Заключение

Добавление аннотаций расстояния к документам с помощью GroupDocs.Annotation для .NET — это простой процесс. Следуя шагам, описанным в этом руководстве, вы можете улучшить свои документы ценными аннотациями, способствуя лучшему сотрудничеству и общению.

## Часто задаваемые вопросы

### В: Могу ли я настроить внешний вид аннотации расстояния?

A: Да, вы можете настраивать различные свойства, такие как цвет, непрозрачность, стиль линии и т. д., в соответствии с вашими требованиями.

### В: Поддерживает ли GroupDocs.Annotation аннотации к разным типам документов?

A: Да, GroupDocs.Annotation поддерживает аннотации в широком спектре форматов документов, включая PDF, Word, Excel, PowerPoint и другие.

### В: Существует ли бесплатная пробная версия GroupDocs.Annotation?

A: Да, вы можете получить доступ к бесплатной пробной версии GroupDocs.Annotation из [эта ссылка](https://releases.groupdocs.com/).

### В: Где я могу найти документацию по GroupDocs.Annotation для .NET?

A: Вы можете обратиться к подробной документации, доступной [здесь](https://tutorials.groupdocs.com/annotation/net/).

### В: Как я могу получить поддержку или помощь по GroupDocs.Annotation?

A: Вы можете обратиться за поддержкой и помощью на форум сообщества GroupDocs.Annotation. [здесь](https://forum.groupdocs.com/c/annotation/10).