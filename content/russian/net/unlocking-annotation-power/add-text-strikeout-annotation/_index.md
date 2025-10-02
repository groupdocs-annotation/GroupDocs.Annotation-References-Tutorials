---
"description": "Узнайте, как добавлять текстовые зачеркнутые аннотации к документам с помощью GroupDocs.Annotation для .NET. Эффективно улучшайте процессы совместной работы и рецензирования документов."
"linktitle": "Добавить зачеркнутый текст в документ"
"second_title": "GroupDocs.Аннотация .NET API"
"title": "Добавить зачеркнутый текст в документ"
"url": "/ru/net/unlocking-annotation-power/add-text-strikeout-annotation/"
type: docs
"weight": 26
---

# Добавить зачеркнутый текст в документ

## Введение
В этом уроке мы рассмотрим, как добавить текстовую зачеркнутую аннотацию к документу с помощью GroupDocs.Annotation для .NET. Эта библиотека предоставляет мощные инструменты для аннотирования различных типов документов, улучшая процессы совместной работы и рецензирования документов.
## Предпосылки
Прежде чем начать, убедитесь, что у вас выполнены следующие предварительные условия:
1. GroupDocs.Annotation для .NET: Установите библиотеку. Вы можете скачать ее с [здесь](https://releases.groupdocs.com/annotation/net/).
2. Среда разработки: настройте подходящую среду разработки для .NET-разработки.
3. Документ: подготовьте документ для аннотирования, например, файл PDF.

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

Теперь давайте разобьем процесс добавления зачеркнутого текста на несколько этапов:
## Шаг 1: Определите выходной путь
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Здесь мы определяем выходной путь, по которому будет сохранен аннотированный документ.
## Шаг 2: Инициализация аннотатора
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Инициализируйте объект Annotator, указав путь к входному документу (в данном случае — PDF-файлу).
## Шаг 3: Создание зачеркнутой аннотации
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
Создайте объект StrikeoutAnnotation с требуемыми свойствами, такими как сообщение, непрозрачность, номер страницы, цвет фона, точки (координаты) и ответы.
## Шаг 4: Добавьте аннотацию
```csharp
annotator.Add(strikeout);
```
Добавьте созданную зачеркнутую аннотацию в документ.
## Шаг 5: Сохраните документ
```csharp
annotator.Save(outputPath);
```
Сохраните аннотированный документ по указанному пути вывода.

## Заключение
В этом уроке мы узнали, как добавить текстовую зачеркнутую аннотацию к документу с помощью GroupDocs.Annotation для .NET. Эта мощная библиотека обеспечивает эффективное аннотирование документов, улучшая совместную работу и процессы рецензирования документов.
## Часто задаваемые вопросы
### Совместим ли GroupDocs.Annotation с различными форматами документов?
Да, GroupDocs.Annotation поддерживает широкий спектр форматов документов, включая PDF, Word, Excel, PowerPoint и другие.
### Могу ли я настроить внешний вид аннотаций?
Конечно, вы можете настраивать свойства аннотации, такие как цвет, прозрачность, размер шрифта и многое другое, в соответствии с вашими требованиями.
### Предоставляет ли GroupDocs.Annotation функции совместной работы?
Да, GroupDocs.Annotation облегчает совместную работу, позволяя пользователям добавлять комментарии, ответы и аннотации к документам.
### Есть ли бесплатная пробная версия?
Да, вы можете воспользоваться бесплатной пробной версией [здесь](https://releases.groupdocs.com/).
### Где я могу получить поддержку по GroupDocs.Annotation?
Вы можете получить поддержку от [Форум GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation/10).