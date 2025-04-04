---
title: Добавить аннотацию водяного знака в документ
linktitle: Добавить аннотацию водяного знака в документ
second_title: GroupDocs.Аннотация .NET API
description: Узнайте, как легко добавлять аннотации к вашим документам с помощью GroupDocs.Annotation для .NET. Повысьте четкость и безопасность документов.
weight: 28
url: /ru/net/unlocking-annotation-power/add-watermark-annotation/
---

# Добавить аннотацию водяного знака в документ

## Введение
В этом руководстве мы рассмотрим процесс добавления аннотации водяного знака в документ с помощью GroupDocs.Annotation для .NET. Аннотации с водяными знаками полезны для указания статуса документа, пометки его как конфиденциального или добавления любой другой соответствующей информации.

## Предварительные условия

Прежде чем мы начнем, убедитесь, что у вас есть следующее:

1.  GroupDocs.Annotation для .NET: вы можете скачать его с сайта[здесь](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: убедитесь, что в вашей системе установлена Visual Studio.
3. Базовые знания C#. Знакомство с языком программирования C# необходимо для понимания и реализации примеров кода.

## Импортировать пространства имен

Прежде чем мы начнем кодировать, давайте импортируем необходимые пространства имен:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Теперь давайте разобьем процесс добавления аннотации водяного знака на несколько этапов:

## Шаг 1: Определите выходной путь

 Во-первых, нам нужно определить путь вывода, в котором будет сохранен документ с аннотациями. Мы будем использовать`Path` класс из`System.IO` пространство имен для объединения пути к выходному каталогу с именем файла.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Шаг 2. Инициализируйте аннотатор

Далее мы инициализируем аннотатор, указав путь к входному документу. Это позволит нам добавлять аннотации к документу.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Здесь будет находиться код аннотации
}
```

## Шаг 3. Создайте аннотацию водяного знака

Теперь давайте создадим объект аннотации водяного знака с нужными свойствами, такими как угол, положение, текст, цвет шрифта, непрозрачность и т. д.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## Шаг 4. Добавьте аннотацию водяного знака

 Теперь мы добавим аннотацию водяного знака в документ, используя`Add` метод объекта аннотатора.

```csharp
annotator.Add(watermark);
```

## Шаг 5: Сохранить документ

Наконец, мы сохраним аннотированный документ в указанном пути вывода.

```csharp
annotator.Save(outputPath);
```

## Заключение

В этом уроке мы узнали, как добавить аннотацию водяного знака в документ с помощью GroupDocs.Annotation для .NET. Аннотации с водяными знаками — ценный инструмент для маркировки документов соответствующей информацией или указания их статуса.

## Часто задаваемые вопросы

### Вопрос: Могу ли я настроить внешний вид аннотации водяного знака?

О: Да, вы можете настроить различные свойства, такие как текст, размер шрифта, цвет, непрозрачность, положение и т. д., чтобы настроить водяной знак в соответствии с вашими требованиями.

### Вопрос: Совместим ли GroupDocs.Annotation для .NET с различными форматами документов?

О: Да, GroupDocs.Annotation поддерживает широкий спектр форматов документов, включая PDF, Microsoft Word, Excel, PowerPoint и форматы изображений.

### Вопрос: Могу ли я добавить несколько аннотаций в один документ?

О: Конечно, GroupDocs.Annotation позволяет добавлять в один документ несколько аннотаций разных типов, обеспечивая комплексную разметку документа.

### Вопрос: Обеспечивает ли GroupDocs.Annotation поддержку совместного аннотирования?

О: Да, GroupDocs.Annotation облегчает совместное аннотирование, позволяя пользователям добавлять комментарии, ответы и аннотации, способствуя эффективному сотрудничеству между членами команды.

### Вопрос: Доступна ли пробная версия GroupDocs.Annotation для .NET?

 О: Да, вы можете скачать бесплатную пробную версию с сайта[здесь](https://releases.groupdocs.com/).