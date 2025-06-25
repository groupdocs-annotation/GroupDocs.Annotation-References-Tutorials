---
"description": "Узнайте, как добавлять аннотации с подчеркиванием текста в документы с помощью GroupDocs.Annotation для .NET. Улучшайте сотрудничество и общение без усилий."
"linktitle": "Добавить аннотацию с подчеркиванием текста в документ"
"second_title": "GroupDocs.Аннотация .NET API"
"title": "Добавить аннотацию с подчеркиванием текста в документ"
"url": "/ru/net/unlocking-annotation-power/add-text-underline-annotation/"
"weight": 27
---

# Добавить аннотацию с подчеркиванием текста в документ

## Введение
В этом уроке мы рассмотрим процесс добавления аннотации с подчеркиванием текста в документ с помощью GroupDocs.Annotation для .NET. Аннотации с подчеркиванием текста могут быть полезны для выделения определенных частей документа, таких как важные отрывки или ключевые моменты.
## Предпосылки
Прежде чем начать, убедитесь, что у вас установлены следующие необходимые компоненты:
1. GroupDocs.Annotation для .NET: Загрузите и установите GroupDocs.Annotation для .NET с сайта [здесь](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Убедитесь, что в вашей системе установлен .NET Framework.

## Импорт пространств имен
Сначала импортируем необходимые пространства имен в наш проект:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Теперь давайте разберем пример на несколько шагов:
## Шаг 1: Определите выходной путь
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
На этом этапе мы определяем выходной путь, по которому будет сохранен аннотированный документ.
## Шаг 2: Инициализация аннотатора
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Здесь мы инициализируем экземпляр `Annotator` класс, указав путь к входному документу.
## Шаг 3: Создание подчеркивания аннотации
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // работает поддерживается только документы Word и PDF
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
Этот шаг включает в себя создание `UnderlineAnnotation` объект с различными свойствами, такими как цвет шрифта, сообщение, непрозрачность, номер страницы, цвет фона, цвет подчеркивания, баллы и ответы.
## Шаг 4: Добавьте аннотацию к документу
```csharp
annotator.Add(underline);
```
Здесь мы добавляем подчеркивающую аннотацию к документу.
## Шаг 5: Сохраните аннотированный документ
```csharp
annotator.Save(outputPath);
```
Наконец, мы сохраняем аннотированный документ по указанному выходному пути.

## Заключение
В этом уроке мы узнали, как добавить аннотацию подчеркивания текста в документ с помощью GroupDocs.Annotation для .NET. Эта мощная библиотека предоставляет различные варианты аннотаций для улучшения совместной работы и общения в документах.
## Часто задаваемые вопросы
### Могу ли я настроить внешний вид подчеркивания аннотации?
Да, вы можете настроить такие свойства, как цвет, прозрачность и положение, в соответствии с вашими требованиями.
### Совместим ли GroupDocs.Annotation с различными форматами документов?
Да, GroupDocs.Annotation поддерживает широкий спектр форматов документов, включая Word и PDF.
### Могу ли я добавить несколько аннотаций к одному документу?
Безусловно, GroupDocs.Annotation позволяет добавлять в документ несколько аннотаций разных типов.
### Существует ли бесплатная пробная версия GroupDocs.Annotation?
Да, вы можете получить доступ к бесплатной пробной версии по ссылке [здесь](https://releases.groupdocs.com/).
### Где я могу получить поддержку по GroupDocs.Annotation?
Вы можете получить поддержку на форуме сообщества GroupDocs.Annotation [здесь](https://forum.groupdocs.com/c/annotation/10).