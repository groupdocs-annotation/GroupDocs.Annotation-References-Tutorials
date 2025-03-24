---
title: Добавить аннотацию редактирования текста в документ
linktitle: Добавить аннотацию редактирования текста в документ
second_title: GroupDocs.Аннотация .NET API
description: Узнайте, как добавлять аннотации редактирования текста в документы PDF с помощью GroupDocs.Annotation для .NET. Защитите конфиденциальную информацию без особых усилий.
weight: 23
url: /ru/net/unlocking-annotation-power/add-text-redaction-annotation/
---

# Добавить аннотацию редактирования текста в документ

## Введение
Добавление аннотации редактирования текста в документ может стать важным шагом в безопасном управлении конфиденциальной информацией. GroupDocs.Annotation для .NET предоставляет надежное решение для беспрепятственного достижения этой цели. В этом уроке мы шаг за шагом проведем вас через процесс добавления аннотации редактирования текста в ваш документ.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующие предварительные условия:
1.  GroupDocs.Annotation для .NET: убедитесь, что вы установили библиотеку GroupDocs.Annotation для .NET. Вы можете скачать его с сайта[Веб-сайт](https://releases.groupdocs.com/annotation/net/).
2. Среда разработки: настройте среду разработки с помощью .NET-совместимой IDE, например Visual Studio.

## Импорт пространств имен
Во-первых, давайте импортируем необходимые пространства имен в наш проект:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Шаг 1: Определите выходной путь
Определите путь вывода, в котором вы хотите сохранить документ с аннотациями. Убедитесь, что он доступен и доступен для записи.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Шаг 2. Инициализируйте аннотатор
 Инициализируйте аннотатор, указав путь к входному документу. Заменять`"input.pdf"` с путем к вашему документу.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Здесь будет находиться код аннотации
}
```
## Шаг 3. Создайте аннотацию редактирования текста
 Создать`TextRedactionAnnotation`объект с необходимыми свойствами, такими как`PageNumber`, `FontColor` , и`Points`. Настройте аннотацию в соответствии с вашими требованиями.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## Шаг 4. Добавьте аннотацию и сохраните.
Добавьте созданную аннотацию в документ с помощью аннотатора и сохраните аннотированный документ в указанном пути вывода.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Шаг 5: Проверьте вывод
Наконец, подтвердите, что документ успешно сохранен в указанном пути вывода.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Заключение
В этом руководстве мы рассмотрели процесс добавления аннотации редактирования текста в документ с помощью GroupDocs.Annotation для .NET. С помощью этих шагов вы теперь можете безопасно управлять конфиденциальной информацией в своих документах.
## Часто задаваемые вопросы
### Могу ли я настроить внешний вид аннотации редактирования текста?
Да, вы можете настроить различные свойства, такие как цвет шрифта, цвет заливки и непрозрачность, в соответствии со своими требованиями.
### Доступна ли пробная версия перед покупкой?
 Да, вы можете получить доступ к бесплатной пробной версии на сайте[Веб-сайт](https://releases.groupdocs.com/).
### Как я могу получить поддержку, если у меня возникнут какие-либо проблемы?
 Вы можете получить поддержку на форуме сообщества GroupDocs.Annotation.[здесь](https://forum.groupdocs.com/c/annotation/10).
### Нужна ли мне временная лицензия для целей тестирования?
 Да, вы можете получить временную лицензию в[страница покупки](https://purchase.groupdocs.com/temporary-license/)для тестирования.
### Могу ли я добавить несколько аннотаций в один документ?
Конечно, GroupDocs.Annotation позволяет добавлять различные типы аннотаций и несколько экземпляров в один документ.