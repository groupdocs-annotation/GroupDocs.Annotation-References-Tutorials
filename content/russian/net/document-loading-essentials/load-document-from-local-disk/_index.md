---
title: Загрузить документ с локального диска
linktitle: Загрузить документ с локального диска
second_title: GroupDocs.Аннотация .NET API
description: Раскройте возможности аннотаций документов с помощью GroupDocs.Annotation для .NET. Легко интегрируйте функции аннотаций в свои приложения .NET.
weight: 13
url: /ru/net/document-loading-essentials/load-document-from-local-disk/
---
## Введение
Раскрыть потенциал аннотаций документов еще никогда не было так просто с GroupDocs.Annotation for .NET. Этот мощный инструмент позволяет разработчикам легко интегрировать надежные функции аннотаций в свои .NET-приложения. В этом подробном руководстве мы шаг за шагом проведем вас через процесс использования GroupDocs.Annotation for .NET для аннотирования документов. Независимо от того, являетесь ли вы опытным разработчиком или только начинаете, это руководство предоставит вам знания, необходимые для улучшения совместной работы над документами и оптимизации рабочего процесса.
## Предварительные условия
Прежде чем углубляться в аннотацию документа с помощью GroupDocs.Annotation for .NET, убедитесь, что у вас есть следующие предварительные условия:
1. Базовые знания C#: Знание основ языка программирования C# необходимо.
2. Установка GroupDocs.Annotation для .NET: загрузите и установите GroupDocs.Annotation для .NET с сайта[здесь](https://releases.groupdocs.com/annotation/net/).
3. Среда разработки: настройте среду разработки с помощью Visual Studio или любой совместимой IDE.

## Импортировать пространства имен
Чтобы начать аннотировать документы с помощью GroupDocs.Annotation for .NET, импортируйте необходимые пространства имен в свой проект:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Шаг 1. Загрузите документ с локального диска
Сначала вам необходимо загрузить документ с локального диска. Используйте следующий фрагмент кода:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Шаг 2. Определите область аннотаций
Затем определите область аннотации. В этом примере мы создадим AreaAnnotation:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Шаг 3. Сохраните документ с аннотациями
После аннотирования документа сохраните его с аннотациями:
```csharp
    annotator.Save(outputPath);
}
```
## Шаг 4. Отображение сообщения об успехе
Наконец, отобразите сообщение об успехе с указанием пути вывода:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Заключение
В заключение, GroupDocs.Annotation для .NET предоставляет надежное решение для интеграции возможностей аннотаций документов в ваши .NET-приложения. Следуя этому пошаговому руководству, вы сможете легко комментировать документы и улучшить совместную работу в своих проектах.
## Часто задаваемые вопросы
### Могу ли я попробовать GroupDocs.Annotation для .NET перед покупкой?
 Да, вы можете загрузить бесплатную пробную версию с сайта[здесь](https://releases.groupdocs.com/).
### Где я могу найти документацию по GroupDocs.Annotation для .NET?
 Вы можете получить доступ к документации[здесь](https://tutorials.groupdocs.com/annotation/net/).
### Как получить временную лицензию на GroupDocs.Annotation для .NET?
 Вы можете получить временную лицензию[здесь](https://purchase.groupdocs.com/temporary-license/).
### Доступна ли поддержка GroupDocs.Annotation для .NET?
 Да, вы можете найти поддержку на форуме GroupDocs.[здесь](https://forum.groupdocs.com/c/annotation/10).
### Где я могу приобрести GroupDocs.Annotation для .NET?
 Вы можете приобрести GroupDocs.Annotation для .NET.[здесь](https://purchase.groupdocs.com/buy).