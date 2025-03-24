---
title: Загрузить документ по URL
linktitle: Загрузить документ по URL
second_title: GroupDocs.Аннотация .NET API
description: Узнайте, как программно комментировать PDF-документы с помощью GroupDocs.Annotation для .NET. Пошаговое руководство с примерами кода.
weight: 15
url: /ru/net/document-loading-essentials/load-document-from-url/
---

# Загрузить документ по URL

## Введение
GroupDocs.Annotation for .NET — это многофункциональная библиотека, которая позволяет разработчикам легко добавлять возможности аннотаций в свои .NET-приложения. С помощью GroupDocs.Annotation вы можете программно комментировать PDF-документы, позволяя пользователям выделять текст, добавлять комментарии, рисовать фигуры и многое другое. В этом руководстве вы узнаете, как загрузить документ по URL-адресу, добавить аннотации и сохранить документ с аннотациями с помощью GroupDocs.Annotation для .NET.
## Предварительные условия
Прежде чем начать, убедитесь, что у вас есть следующие предварительные условия:
1. Visual Studio: убедитесь, что на вашем компьютере разработки установлена Visual Studio.
2.  GroupDocs.Annotation для .NET: загрузите и установите GroupDocs.Annotation для .NET с сайта[Веб-сайт](https://releases.groupdocs.com/annotation/net/).
3. Базовые знания C#: познакомьтесь с языком программирования C#.
4. Подключение к Интернету: вам потребуется подключение к Интернету для доступа к внешним ресурсам и загрузки файлов примеров.

## Импортировать пространства имен
Сначала давайте импортируем необходимые пространства имен в ваш проект C#:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## Шаг 1. Загрузите документ по URL-адресу.
Чтобы аннотировать PDF-документ по URL-адресу, выполните следующие действия:
### Шаг 1.1: Определите выходной путь
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Шаг 1.2. Укажите URL-адрес
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### Шаг 1.3: Загрузите документ
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // Добавьте сюда аннотации
    annotator.Save(outputPath);
}
```
## Шаг 2. Добавьте аннотации
Теперь добавим аннотации к загруженному документу. В этом примере мы добавим аннотацию области:
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Шаг 3. Сохраните документ с аннотациями
Наконец, сохраните аннотированный документ в указанном пути вывода:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Заключение
В этом руководстве мы узнали, как аннотировать PDF-документы с помощью GroupDocs.Annotation для .NET. Следуя пошаговому руководству, вы сможете легко интегрировать функции аннотирования в свои приложения .NET, предоставив пользователям возможность эффективно совместно работать над файлами PDF.

## Часто задаваемые вопросы
### Совместима ли GroupDocs.Annotation для .NET со всеми платформами .NET?
Да, GroupDocs.Annotation для .NET совместим с различными платформами .NET, включая .NET Framework, .NET Core и .NET Standard.
### Могу ли я настроить внешний вид аннотаций?
Абсолютно! GroupDocs.Annotation для .NET предоставляет широкие возможности настройки, позволяющие изменять внешний вид и поведение аннотаций в соответствии с вашими требованиями.
### Доступна ли бесплатная пробная версия GroupDocs.Annotation для .NET?
 Да, вы можете загрузить бесплатную пробную версию GroupDocs.Annotation для .NET с сайта[Веб-сайт](https://releases.groupdocs.com/).
### Как я могу получить техническую поддержку для GroupDocs.Annotation для .NET?
 Если у вас возникнут какие-либо технические проблемы или возникнут вопросы о GroupDocs.Annotation для .NET, вы можете обратиться за помощью к[форум поддержки](https://forum.groupdocs.com/c/annotation/10).
### Где я могу приобрести лицензию на GroupDocs.Annotation для .NET?
 Вы можете приобрести лицензию на GroupDocs.Annotation для .NET на сайте[страница покупки](https://purchase.groupdocs.com/buy).