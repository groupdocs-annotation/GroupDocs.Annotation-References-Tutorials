---
title: Добавить аннотацию эллипса в документ
linktitle: Добавить аннотацию эллипса в документ
second_title: GroupDocs.Аннотация .NET API
description: Узнайте, как добавлять аннотации в виде эллипсов к документам в .NET с помощью GroupDocs.Annotation. Улучшайте сотрудничество и общение без особых усилий.
weight: 13
url: /ru/net/unlocking-annotation-power/add-ellipse-annotation/
---

# Добавить аннотацию эллипса в документ

## Введение
В этом руководстве вы узнаете, как добавить аннотацию в виде эллипса в документ с помощью GroupDocs.Annotation для .NET. Это пошаговое руководство проведет вас через весь процесс, гарантируя, что вы четко поймете каждый шаг.
## Предварительные условия
Прежде чем начать, убедитесь, что у вас есть следующее:
1.  GroupDocs.Annotation для .NET: убедитесь, что вы загрузили и установили GroupDocs.Annotation для .NET. Вы можете скачать его с[здесь](https://releases.groupdocs.com/annotation/net/).
2. IDE (интегрированная среда разработки): вам понадобится установленная в вашей системе IDE, например Visual Studio, для написания и выполнения кода.

## Импортировать пространства имен
Сначала импортируйте необходимые пространства имен в ваш проект:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Шаг 1. Установите путь вывода
Определите путь вывода, в котором будет сохранен документ с аннотациями:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Шаг 2. Инициализируйте аннотатор
Инициализируйте аннотатор, указав путь к входному документу:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Шаг 3. Создайте аннотацию эллипса
 Создайте экземпляр`EllipseAnnotation` класс и установите его свойства:
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
## Шаг 4. Добавьте аннотацию
Добавьте аннотацию в виде эллипса в документ:
```csharp
annotator.Add(ellipse);
```
## Шаг 5: Сохранить документ
Сохраните аннотированный документ в выходной путь:
```csharp
annotator.Save(outputPath);
```

## Заключение
Поздравляем! Вы успешно добавили аннотацию в виде эллипса в документ с помощью GroupDocs.Annotation для .NET. Теперь вы можете интегрировать эту функцию в свои приложения .NET, чтобы улучшить совместную работу над документами и обмен информацией.
## Часто задаваемые вопросы
### Могу ли я настроить внешний вид аннотации в виде эллипса?
Да, вы можете настроить различные свойства, такие как цвет фона, цвет границы, непрозрачность и т. д., в соответствии с вашими требованиями.
### Совместим ли GroupDocs.Annotation для .NET со всеми форматами документов?
GroupDocs.Annotation для .NET поддерживает широкий спектр форматов документов, включая PDF, DOCX, PPTX, XLSX и другие.
### Могу ли я добавить несколько аннотаций в один документ?
Да, вы можете добавить в один документ несколько аннотаций, включая эллипсы, прямоугольники, текст и т. д.
### Доступна ли пробная версия для тестирования?
 Да, вы можете скачать бесплатную пробную версию с сайта[здесь](https://releases.groupdocs.com/) оценить его особенности.
### Где я могу получить техническую поддержку для GroupDocs.Annotation для .NET?
 Вы можете получить техническую поддержку на форуме сообщества GroupDocs.Annotation.[здесь](https://forum.groupdocs.com/c/annotation/10).