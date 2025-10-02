---
"description": "Узнайте, как добавлять аннотации с многоточием к документам в .NET с помощью GroupDocs.Annotation. Улучшайте сотрудничество и общение без усилий."
"linktitle": "Добавить аннотацию эллипса к документу"
"second_title": "GroupDocs.Аннотация .NET API"
"title": "Добавить аннотацию эллипса к документу"
"url": "/ru/net/unlocking-annotation-power/add-ellipse-annotation/"
type: docs
"weight": 13
---

# Добавить аннотацию эллипса к документу

## Введение
В этом уроке вы узнаете, как добавить аннотацию эллипса в документ с помощью GroupDocs.Annotation для .NET. Это пошаговое руководство проведет вас через весь процесс, гарантируя, что вы четко поймете каждый шаг.
## Предпосылки
Прежде чем начать, убедитесь, что у вас есть следующее:
1. GroupDocs.Annotation для .NET: Убедитесь, что вы загрузили и установили GroupDocs.Annotation для .NET. Вы можете загрузить его с [здесь](https://releases.groupdocs.com/annotation/net/).
2. IDE (интегрированная среда разработки): для написания и выполнения кода вам понадобится установленная в вашей системе IDE, например Visual Studio.

## Импорт пространств имен
Сначала импортируйте необходимые пространства имен в свой проект:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Шаг 1: Задайте выходной путь
Определите выходной путь, по которому будет сохранен аннотированный документ:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Шаг 2: Инициализация аннотатора
Инициализируйте аннотатор, указав путь к входному документу:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Шаг 3: Создание аннотации эллипса
Создайте экземпляр `EllipseAnnotation` класс и задайте его свойства:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
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
## Шаг 4: Добавьте аннотацию
Добавьте аннотацию в виде эллипса в документ:
```csharp
annotator.Add(ellipse);
```
## Шаг 5: Сохраните документ
Сохраните аннотированный документ в выходной папке:
```csharp
annotator.Save(outputPath);
```

## Заключение
Поздравляем! Вы успешно добавили аннотацию в виде эллипса к документу с помощью GroupDocs.Annotation для .NET. Теперь вы можете интегрировать эту функциональность в свои приложения .NET для улучшения совместной работы с документами и общения.
## Часто задаваемые вопросы
### Могу ли я настроить внешний вид аннотации в виде эллипса?
Да, вы можете настраивать различные свойства, такие как цвет фона, цвет границы, прозрачность и т. д., в соответствии с вашими требованиями.
### Совместим ли GroupDocs.Annotation для .NET со всеми форматами документов?
GroupDocs.Annotation для .NET поддерживает широкий спектр форматов документов, включая PDF, DOCX, PPTX, XLSX и другие.
### Могу ли я добавить несколько аннотаций к одному документу?
Да, вы можете добавлять в один документ несколько аннотаций, включая эллипсы, прямоугольники, текст и т. д.
### Существует ли пробная версия для тестирования?
Да, вы можете загрузить бесплатную пробную версию с сайта [здесь](https://releases.groupdocs.com/) оценить его особенности.
### Где я могу получить техническую поддержку по GroupDocs.Annotation для .NET?
Вы можете получить техническую поддержку на форуме сообщества GroupDocs.Annotation. [здесь](https://forum.groupdocs.com/c/annotation/10).