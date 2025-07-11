---
"description": "Узнайте, как добавлять аннотации изображений поверх текста в .NET с помощью GroupDocs.Annotation для эффективного управления документами и совместной работы."
"linktitle": "Разместить аннотацию изображения поверх текста"
"second_title": "GroupDocs.Аннотация .NET API"
"title": "Разместить аннотацию изображения поверх текста"
"url": "/ru/net/advanced-usage/put-image-annotation-over-text/"
"weight": 21
---

# Разместить аннотацию изображения поверх текста

## Введение
В мире разработки .NET GroupDocs.Annotation предлагает мощное решение для добавления аннотаций к документам, что делает совместную работу и управление документами более эффективными. Одним из распространенных требований является размещение аннотаций изображений поверх текста, что может быть легко выполнено с помощью GroupDocs.Annotation для .NET.
## Предпосылки
Прежде чем приступить к процессу добавления аннотаций изображений поверх текста с помощью GroupDocs.Annotation для .NET, убедитесь, что у вас есть следующее:
1. GroupDocs.Annotation для библиотеки .NET: Загрузите и установите библиотеку с [здесь](https://releases.groupdocs.com/annotation/net/).
2. Среда разработки: настройте подходящую среду разработки, например Visual Studio или любую другую .NET IDE.
3. Файлы документов и изображений: подготовьте файл документа (PDF, DOCX и т. д.) и файл изображения, которые вы хотите использовать для аннотаций.
4. Базовые знания C#: для реализации фрагментов кода, представленных в этом руководстве, необходимо знакомство с языком программирования C#.

## Импорт пространств имен
Прежде чем приступить к процессу аннотирования, убедитесь, что вы импортировали необходимые пространства имен в свой проект C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Шаг 1: Определите выходной путь
Сначала определите выходной путь, по которому будет сохранен аннотированный документ:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Шаг 2: Инициализация аннотатора
Инициализируйте `Annotator` объект, указав путь к входному документу:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Код аннотации будет здесь
}
```
## Шаг 3: Создание аннотации к изображению
Создайте `ImageAnnotation` объект с требуемыми свойствами, такими как размеры блока, непрозрачность, номер страницы, путь к изображению и z-индекс:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## Шаг 4: Добавьте аннотацию
Добавьте аннотацию изображения к документу с помощью `Add` Метод `Annotator` объект:
```csharp
annotator.Add(image);
```
## Шаг 5: Сохраните аннотированный документ
Сохраните аннотированный документ по указанному пути вывода:
```csharp
annotator.Save(outputPath);
```
## Шаг 6: Отображение сообщения об успешном завершении
Отобразить сообщение об успешном завершении с указанием пути к аннотированному документу:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Заключение
В заключение, добавление аннотаций изображений поверх текста в приложениях .NET с помощью GroupDocs.Annotation — это простой процесс. Следуя пошаговому руководству, представленному в этом руководстве, вы сможете эффективно аннотировать документы и улучшить возможности совместной работы и управления документами в ваших проектах .NET.
## Часто задаваемые вопросы
### Могу ли я комментировать документы, отличные от PDF-файлов?
Да, GroupDocs.Annotation поддерживает различные форматы документов, такие как DOCX, XLSX, PPTX и другие.
### Существует ли бесплатная пробная версия GroupDocs.Annotation?
Да, вы можете загрузить бесплатную пробную версию с сайта [здесь](https://releases.groupdocs.com/).
### Как я могу получить поддержку по GroupDocs.Annotation?
Вы можете получить поддержку на форуме сообщества GroupDocs.Annotation [здесь](https://forum.groupdocs.com/c/annotation/10).
### Нужна ли мне временная лицензия для проведения тестирования?
Да, вы можете получить временную лицензию от [здесь](https://purchase.groupdocs.com/temporary-license/) для целей тестирования.
### Могу ли я настроить внешний вид аннотаций?
Да, GroupDocs.Annotation предоставляет различные параметры для настройки внешнего вида аннотаций, такие как цвет, прозрачность, размер шрифта и т. д.