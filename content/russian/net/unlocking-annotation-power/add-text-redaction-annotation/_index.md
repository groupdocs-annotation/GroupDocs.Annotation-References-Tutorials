---
"description": "Узнайте, как добавлять аннотации редактирования текста в документы PDF с помощью GroupDocs.Annotation для .NET. Защитите конфиденциальную информацию без усилий."
"linktitle": "Добавить аннотацию к тексту редактирования в документ"
"second_title": "GroupDocs.Аннотация .NET API"
"title": "Добавить аннотацию к тексту редактирования в документ"
"url": "/ru/net/unlocking-annotation-power/add-text-redaction-annotation/"
"weight": 23
---

# Добавить аннотацию к тексту редактирования в документ

## Введение
Добавление аннотации редактирования текста в документ может стать важным шагом в безопасном управлении конфиденциальной информацией. GroupDocs.Annotation для .NET предоставляет надежное решение для беспрепятственного достижения этой цели. В этом руководстве мы проведем вас через процесс добавления аннотации редактирования текста в ваш документ шаг за шагом.
## Предпосылки
Прежде чем начать, убедитесь, что у вас выполнены следующие предварительные условия:
1. GroupDocs.Annotation for .NET: Убедитесь, что у вас установлена библиотека GroupDocs.Annotation for .NET. Вы можете загрузить ее с [веб-сайт](https://releases.groupdocs.com/annotation/net/).
2. Среда разработки: настройте среду разработки с помощью совместимой с .NET IDE, например Visual Studio.

## Импорт пространств имен
Для начала импортируем необходимые пространства имен в наш проект:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Шаг 1: Определите выходной путь
Определите выходной путь, где вы хотите сохранить аннотированный документ. Убедитесь, что он доступен и доступен для записи.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Шаг 2: Инициализация аннотатора
Инициализируйте аннотатор с помощью пути к входному документу. Заменить `"input.pdf"` с путем к вашему документу.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Код аннотации будет здесь
}
```
## Шаг 3: Создание аннотации к тексту для редактирования
Создать `TextRedactionAnnotation` объект с требуемыми свойствами, такими как `PageNumber`, `FontColor`, и `Points`. Настройте аннотацию в соответствии с вашими требованиями.
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
## Шаг 4: Добавьте аннотацию и сохраните
Добавьте созданную аннотацию к документу с помощью аннотатора и сохраните аннотированный документ по указанному выходному пути.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Шаг 5: Проверьте вывод
Наконец, подтвердите, что документ успешно сохранен по указанному пути вывода.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Заключение
В этом уроке мы прошли процесс добавления аннотации редактирования текста в документ с помощью GroupDocs.Annotation для .NET. С помощью этих шагов вы теперь можете безопасно управлять конфиденциальной информацией в ваших документах.
## Часто задаваемые вопросы
### Могу ли я настроить внешний вид аннотации к тексту?
Да, вы можете настроить различные свойства, такие как цвет шрифта, цвет заливки и непрозрачность, в соответствии со своими требованиями.
### Доступна ли пробная версия перед покупкой?
Да, вы можете получить доступ к бесплатной пробной версии с сайта [веб-сайт](https://releases.groupdocs.com/).
### Как я могу получить поддержку, если у меня возникнут какие-либо проблемы?
Вы можете получить поддержку на форуме сообщества GroupDocs.Annotation [здесь](https://forum.groupdocs.com/c/annotation/10).
### Нужна ли мне временная лицензия для проведения тестирования?
Да, вы можете получить временную лицензию в [страница покупки](https://purchase.groupdocs.com/temporary-license/) для тестирования.
### Могу ли я добавить несколько аннотаций к одному документу?
Безусловно, GroupDocs.Annotation позволяет добавлять различные типы аннотаций и несколько экземпляров в один документ.