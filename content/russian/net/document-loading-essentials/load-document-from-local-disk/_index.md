---
"description": "Откройте для себя мощь аннотирования документов с GroupDocs.Annotation для .NET. Легко интегрируйте функции аннотирования в свои приложения .NET."
"linktitle": "Загрузить документ с локального диска"
"second_title": "GroupDocs.Аннотация .NET API"
"title": "Загрузить документ с локального диска"
"url": "/ru/net/document-loading-essentials/load-document-from-local-disk/"
"weight": 13
---

# Загрузить документ с локального диска

## Введение
Раскрытие потенциала аннотирования документов никогда не было таким простым с GroupDocs.Annotation для .NET. Этот мощный инструмент позволяет разработчикам легко интегрировать надежные функции аннотирования в свои приложения .NET. В этом всеобъемлющем руководстве мы шаг за шагом проведем вас через процесс использования GroupDocs.Annotation для .NET для аннотирования документов. Независимо от того, являетесь ли вы опытным разработчиком или только начинаете, это руководство даст вам знания для улучшения совместной работы с документами и оптимизации рабочего процесса.
## Предпосылки
Прежде чем приступить к аннотированию документов с помощью GroupDocs.Annotation для .NET, убедитесь, что выполнены следующие предварительные условия:
1. Базовые знания C#: Знакомство с основами языка программирования C# обязательно.
2. Установка GroupDocs.Annotation для .NET: Загрузите и установите GroupDocs.Annotation для .NET с сайта [здесь](https://releases.groupdocs.com/annotation/net/).
3. Среда разработки: настройте среду разработки с помощью Visual Studio или любой совместимой IDE.

## Импорт пространств имен
Чтобы начать аннотировать документы с помощью GroupDocs.Annotation для .NET, импортируйте необходимые пространства имен в свой проект:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Шаг 1: Загрузка документа с локального диска
Сначала вам нужно загрузить документ с локального диска. Используйте следующий фрагмент кода:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Шаг 2: Определите область аннотации
Далее, определите область аннотации. В этом примере мы создадим AreaAnnotation:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Шаг 3: Сохраните документ с аннотациями
После аннотирования документа сохраните его с аннотациями:
```csharp
    annotator.Save(outputPath);
}
```
## Шаг 4: Отображение сообщения об успешном завершении
Наконец, отобразите сообщение об успешном выполнении с указанием пути вывода:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Заключение
В заключение, GroupDocs.Annotation для .NET предоставляет надежное решение для интеграции возможностей аннотирования документов в ваши приложения .NET. Следуя этому пошаговому руководству, вы сможете без усилий аннотировать документы и улучшить совместную работу в ваших проектах.
## Часто задаваемые вопросы
### Могу ли я попробовать GroupDocs.Annotation для .NET перед покупкой?
Да, вы можете загрузить бесплатную пробную версию с сайта [здесь](https://releases.groupdocs.com/).
### Где можно найти документацию по GroupDocs.Annotation для .NET?
Вы можете получить доступ к документации [здесь](https://tutorials.groupdocs.com/annotation/net/).
### Как получить временную лицензию на GroupDocs.Annotation для .NET?
Вы можете получить временную лицензию [здесь](https://purchase.groupdocs.com/temporary-license/).
### Доступна ли поддержка GroupDocs.Annotation для .NET?
Да, вы можете найти поддержку на форуме GroupDocs. [здесь](https://forum.groupdocs.com/c/annotation/10).
### Где можно приобрести GroupDocs.Annotation для .NET?
Вы можете приобрести GroupDocs.Annotation для .NET [здесь](https://purchase.groupdocs.com/buy).