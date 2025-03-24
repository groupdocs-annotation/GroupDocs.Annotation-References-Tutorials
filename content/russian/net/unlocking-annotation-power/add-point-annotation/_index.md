---
title: Добавить аннотацию точки в документ
linktitle: Добавить аннотацию точки в документ
second_title: GroupDocs.Аннотация .NET API
description: Узнайте, как добавить точечную аннотацию в PDF-файлы с помощью GroupDocs.Annotation для .NET. Пошаговое руководство по плавной интеграции.
weight: 17
url: /ru/net/unlocking-annotation-power/add-point-annotation/
---

# Добавить аннотацию точки в документ

## Введение
GroupDocs.Annotation для .NET — это мощный инструмент, который позволяет разработчикам программно добавлять к документам различные типы аннотаций. В этом уроке мы сосредоточимся на добавлении аннотации точки в документ с помощью C#.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующее:
1. Базовое понимание языка программирования C#.
2. Visual Studio установлена в вашей системе.
3.  Установлена библиотека GroupDocs.Annotation для .NET. Вы можете скачать его с[здесь](https://releases.groupdocs.com/annotation/net/).

## Импорт необходимых пространств имен
Для начала вам необходимо импортировать необходимые пространства имен в ваш проект C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Шаг 1: Определите выходной путь
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
На этом этапе мы определяем выходной путь, в котором будет сохранен документ с аннотациями.
## Шаг 2. Инициализируйте аннотатор
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Здесь мы инициализируем`Annotator` объект с входным документом ("input.pdf").
## Шаг 3. Создайте аннотацию точки
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
 На этом этапе мы создаем`PointAnnotation` объект и укажите его свойства, такие как положение, сообщение, номер страницы и ответы.
## Шаг 4. Добавьте аннотацию
```csharp
annotator.Add(point);
```
Здесь мы добавляем созданную аннотацию точки в документ.
## Шаг 5: Сохранить документ
```csharp
annotator.Save(outputPath);
```
Наконец, мы сохраняем аннотированный документ в указанном пути вывода.

## Заключение
В этом руководстве мы узнали, как добавить аннотацию точки в документ с помощью GroupDocs.Annotation для .NET. С помощью этой мощной библиотеки вы можете улучшить свои приложения для управления документами, включив в них функции аннотаций.
## Часто задаваемые вопросы
### Совместим ли GroupDocs.Annotation для .NET со всеми форматами документов?
Да, GroupDocs.Annotation для .NET поддерживает широкий спектр форматов документов, включая PDF, Microsoft Word, Excel, PowerPoint и другие.
### Могу ли я настроить внешний вид аннотаций?
Абсолютно! GroupDocs.Annotation для .NET предоставляет широкие возможности настройки внешнего вида аннотаций в соответствии с потребностями вашего приложения.
### Доступна ли бесплатная пробная версия GroupDocs.Annotation для .NET?
 Да, вы можете воспользоваться бесплатной пробной версией на[здесь](https://releases.groupdocs.com/).
### Как я могу получить поддержку по любым вопросам или вопросам, связанным с GroupDocs.Annotation для .NET?
 Вы можете получить поддержку на форуме GroupDocs.Annotation.[здесь](https://forum.groupdocs.com/c/annotation/10).
### Могу ли я получить временную лицензию для целей тестирования?
 Да, вы можете получить временную лицензию от[здесь](https://purchase.groupdocs.com/temporary-license/).