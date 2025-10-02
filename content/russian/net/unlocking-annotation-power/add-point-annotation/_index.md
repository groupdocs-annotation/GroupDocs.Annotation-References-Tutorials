---
"description": "Узнайте, как добавлять точечные аннотации в PDF-файлы с помощью GroupDocs.Annotation для .NET. Пошаговое руководство для бесшовной интеграции."
"linktitle": "Добавить точечную аннотацию к документу"
"second_title": "GroupDocs.Аннотация .NET API"
"title": "Добавить точечную аннотацию к документу"
"url": "/ru/net/unlocking-annotation-power/add-point-annotation/"
type: docs
"weight": 17
---

# Добавить точечную аннотацию к документу

## Введение
GroupDocs.Annotation для .NET — мощный инструмент, позволяющий разработчикам добавлять различные типы аннотаций к документам программным способом. В этом уроке мы сосредоточимся на добавлении аннотации Point к документу с помощью C#.
## Предпосылки
Прежде чем начать, убедитесь, что у вас есть следующее:
1. Базовые знания языка программирования C#.
2. Visual Studio установлена в вашей системе.
3. GroupDocs.Annotation for .NET library установлена. Вы можете скачать ее с [здесь](https://releases.groupdocs.com/annotation/net/).

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
На этом этапе мы определяем выходной путь, по которому будет сохранен аннотированный документ.
## Шаг 2: Инициализация аннотатора
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Здесь мы инициализируем `Annotator` объект с входным документом («input.pdf»).
## Шаг 3: Создание аннотации точки
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
На этом этапе мы создаем `PointAnnotation` объект и укажите его свойства, такие как положение, сообщение, номер страницы и ответы.
## Шаг 4: Добавьте аннотацию
```csharp
annotator.Add(point);
```
Здесь мы добавляем созданную точечную аннотацию в документ.
## Шаг 5: Сохраните документ
```csharp
annotator.Save(outputPath);
```
Наконец, мы сохраняем аннотированный документ по указанному выходному пути.

## Заключение
В этом уроке мы узнали, как добавить точечную аннотацию к документу с помощью GroupDocs.Annotation для .NET. С помощью этой мощной библиотеки вы можете улучшить свои приложения для управления документами, включив в них функции аннотации.
## Часто задаваемые вопросы
### Совместим ли GroupDocs.Annotation для .NET со всеми форматами документов?
Да, GroupDocs.Annotation для .NET поддерживает широкий спектр форматов документов, включая PDF, Microsoft Word, Excel, PowerPoint и другие.
### Могу ли я настроить внешний вид аннотаций?
Конечно! GroupDocs.Annotation для .NET предоставляет обширные возможности для настройки внешнего вида аннотаций в соответствии с потребностями вашего приложения.
### Существует ли бесплатная пробная версия GroupDocs.Annotation для .NET?
Да, вы можете воспользоваться бесплатной пробной версией [здесь](https://releases.groupdocs.com/).
### Как я могу получить поддержку по любым вопросам или вопросам, связанным с GroupDocs.Annotation для .NET?
Вы можете получить поддержку на форуме GroupDocs.Annotation [здесь](https://forum.groupdocs.com/c/annotation/10).
### Могу ли я получить временную лицензию для целей тестирования?
Да, вы можете получить временную лицензию от [здесь](https://purchase.groupdocs.com/temporary-license/).