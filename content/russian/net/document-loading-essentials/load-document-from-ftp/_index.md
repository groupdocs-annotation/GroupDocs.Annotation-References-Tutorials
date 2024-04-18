---
title: Загрузить документ с FTP
linktitle: Загрузить документ с FTP
second_title: GroupDocs.Аннотация .NET API
description: Усовершенствуйте свои приложения .NET с помощью GroupDocs.Annotation для удобного аннотирования документов. Пошаговое руководство включено.
type: docs
weight: 12
url: /ru/net/document-loading-essentials/load-document-from-ftp/
---
## Введение
GroupDocs.Annotation for .NET — это универсальная библиотека, предназначенная для упрощения возможности аннотирования документов в приложениях .NET. Независимо от того, работаете ли вы с PDF-файлами, документами Microsoft Office, изображениями или другими форматами, эта библиотека предоставляет унифицированное решение для добавления аннотаций, таких как комментарии, выделение и фигуры, для улучшения совместной работы и управления документами.
## Предварительные условия
Прежде чем приступить к изучению руководства, убедитесь, что у вас есть следующие предварительные условия:
1. Знание C#: знание языка программирования C# необходимо для понимания и реализации примеров кода, представленных в этом руководстве.
2.  GroupDocs.Annotation для .NET: обязательно загрузите и установите GroupDocs.Annotation для .NET с сайта[ссылка для скачивания](https://releases.groupdocs.com/annotation/net/). Следуйте инструкциям по установке, чтобы успешно интегрировать библиотеку в ваш проект .NET.
## Импортировать пространства имен
Чтобы использовать GroupDocs.Annotation для функций .NET, вам необходимо импортировать необходимые пространства имен в проект C#. Следуй этим шагам:

В проекте C# включите необходимые пространства имен в начало файла кода:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Теперь давайте углубимся в процесс загрузки документа с FTP и добавления к нему аннотаций с помощью GroupDocs.Annotation для .NET.
## Шаг 1: Определите выходной путь
Укажите выходной путь, в котором будет сохранен документ с аннотациями.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Шаг 2. Загрузите документ с FTP
Получите документ с FTP-сервера, используя предоставленный путь к файлу.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Код аннотации будет добавлен сюда
}
```
## Шаг 3. Добавьте аннотацию
Определите и добавьте в документ нужную аннотацию, например аннотацию области.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Шаг 4. Сохраните документ с аннотациями
Сохраните документ с аннотациями в указанном пути вывода.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Шаг 5: Получить файл с FTP
Реализуйте метод для получения файла с FTP-сервера.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## Шаг 6. Создайте FTP-запрос
Создайте FTP-запрос для загрузки файла.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Шаг 7: Получите файловый поток
Получите поток файлов из ответа FTP.
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## Заключение
В заключение, GroupDocs.Annotation for .NET позволяет разработчикам легко интегрировать функции аннотаций документов в свои .NET-приложения. Следуя пошаговому руководству, изложенному в этом руководстве, вы сможете эффективно загружать документы с FTP и с легкостью добавлять аннотации, улучшая совместную работу и управление документами в ваших приложениях.
## Часто задаваемые вопросы
### Совместим ли GroupDocs.Annotation для .NET со всеми форматами документов?
Да, GroupDocs.Annotation для .NET поддерживает широкий спектр форматов документов, включая PDF, документы Microsoft Office, изображения и многое другое.
### Могу ли я настроить внешний вид аннотаций, добавленных с помощью GroupDocs.Annotation для .NET?
Разумеется, GroupDocs.Annotation for .NET предлагает широкие возможности настройки внешнего вида аннотаций, включая цвета, стили и формы.
### Предоставляет ли GroupDocs.Annotation для .NET поддержку служб облачного хранения?
Да, GroupDocs.Annotation для .NET легко интегрируется с популярными службами облачного хранения, позволяя загружать и сохранять документы из таких служб, как Dropbox, Google Drive и OneDrive.
### Доступна ли пробная версия GroupDocs.Annotation для .NET?
 Да, вы можете изучить возможности GroupDocs.Annotation для .NET, загрузив бесплатную пробную версию с сайта[страница выпуска](https://releases.groupdocs.com/).
### Как я могу получить техническую помощь или поддержку для GroupDocs.Annotation для .NET?
 Для получения технической помощи, устранения неполадок или общих вопросов вы можете посетить GroupDocs.Annotation для .NET.[форум поддержки](https://forum.groupdocs.com/c/annotation/10).