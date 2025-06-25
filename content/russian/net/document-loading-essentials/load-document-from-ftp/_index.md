---
"description": "Улучшите свои приложения .NET с помощью GroupDocs.Annotation для бесшовного аннотирования документов. Пошаговое руководство включено."
"linktitle": "Загрузить документ с FTP"
"second_title": "GroupDocs.Аннотация .NET API"
"title": "Загрузить документ с FTP"
"url": "/ru/net/document-loading-essentials/load-document-from-ftp/"
"weight": 12
---

# Загрузить документ с FTP

## Введение
GroupDocs.Annotation для .NET — это универсальная библиотека, разработанная для облегчения возможностей аннотирования документов в приложениях .NET без особых усилий. Независимо от того, работаете ли вы с PDF-файлами, документами Microsoft Office, изображениями или другими форматами, эта библиотека предоставляет унифицированное решение для добавления аннотаций, таких как комментарии, выделения и фигуры, для улучшения совместной работы и управления документами.
## Предпосылки
Прежде чем приступить к изучению руководства, убедитесь, что у вас выполнены следующие предварительные условия:
1. Знание C#: Знание языка программирования C# необходимо для понимания и реализации примеров кода, представленных в этом руководстве.
2. GroupDocs.Annotation для .NET: Обязательно загрузите и установите GroupDocs.Annotation для .NET с сайта [ссылка для скачивания](https://releases.groupdocs.com/annotation/net/). Следуйте инструкциям по установке, чтобы успешно интегрировать библиотеку в ваш проект .NET.
## Импорт пространств имен
Чтобы использовать GroupDocs.Annotation для функциональности .NET, вам необходимо импортировать требуемые пространства имен в ваш проект C#. Выполните следующие шаги:

В вашем проекте C# включите необходимые пространства имен в начало файла кода:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Теперь давайте углубимся в процесс загрузки документа с FTP и добавления к нему аннотаций с помощью GroupDocs.Annotation для .NET.
## Шаг 1: Определите выходной путь
Укажите выходной путь, по которому будет сохранен аннотированный документ.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Шаг 2: Загрузите документ с FTP
Загрузите документ с FTP-сервера, используя указанный путь к файлу.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Код аннотации будет добавлен здесь
}
```
## Шаг 3: Добавьте аннотацию
Определите и добавьте в документ нужную аннотацию, например, аннотацию области.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Шаг 4: Сохраните аннотированный документ
Сохраните аннотированный документ по указанному пути вывода.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Шаг 5: Извлечение файла с FTP
Реализуйте метод извлечения файла с FTP-сервера.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## Шаг 6: Создание FTP-запроса
Создайте FTP-запрос для загрузки файла.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Шаг 7: Получите поток файлов
Извлеките поток файлов из ответа FTP.
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
В заключение, GroupDocs.Annotation для .NET позволяет разработчикам легко интегрировать функции аннотации документов в свои приложения .NET. Следуя пошаговому руководству, изложенному в этом руководстве, вы сможете эффективно загружать документы с FTP и с легкостью добавлять аннотации, улучшая совместную работу и управление документами в ваших приложениях.
## Часто задаваемые вопросы
### Совместим ли GroupDocs.Annotation для .NET со всеми форматами документов?
Да, GroupDocs.Annotation для .NET поддерживает широкий спектр форматов документов, включая PDF, документы Microsoft Office, изображения и многое другое.
### Можно ли настроить внешний вид аннотаций, добавленных с помощью GroupDocs.Annotation для .NET?
Безусловно, GroupDocs.Annotation для .NET предлагает обширные возможности настройки внешнего вида аннотаций, включая цвета, стили и формы.
### Поддерживает ли GroupDocs.Annotation для .NET службы облачного хранения?
Да, GroupDocs.Annotation для .NET легко интегрируется с популярными сервисами облачного хранения данных, позволяя загружать и сохранять документы из таких сервисов, как Dropbox, Google Drive и OneDrive.
### Существует ли пробная версия GroupDocs.Annotation для .NET?
Да, вы можете изучить возможности GroupDocs.Annotation для .NET, загрузив бесплатную пробную версию с сайта [страница релиза](https://releases.groupdocs.com/).
### Как я могу получить техническую помощь или поддержку по GroupDocs.Annotation для .NET?
Для получения технической помощи, устранения неполадок или общих вопросов вы можете посетить GroupDocs.Annotation for .NET [форум поддержки](https://forum.groupdocs.com/c/annotation/10).