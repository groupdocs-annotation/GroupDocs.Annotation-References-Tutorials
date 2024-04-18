---
title: Загрузить документ из Azure
linktitle: Загрузить документ из Azure
second_title: GroupDocs.Аннотация .NET API
description: Узнайте, как аннотировать документы в .NET с помощью GroupDocs.Annotation. Пошаговое руководство по плавной интеграции с хранилищем BLOB-объектов Azure.
type: docs
weight: 11
url: /ru/net/document-loading-essentials/load-document-from-azure/
---
## Введение
В сфере управления документами и совместной работы GroupDocs.Annotation for .NET представляет собой надежное решение, обеспечивающее бесперебойную функциональность аннотаций и разметки в приложениях .NET. В этом руководстве рассматриваются тонкости использования GroupDocs.Annotation for .NET для аннотирования документов, а также предлагаются пошаговые инструкции от предварительных требований до расширенного использования.
## Предварительные условия
Прежде чем углубляться в GroupDocs.Annotation для .NET, убедитесь, что у вас есть следующие предварительные условия:
1. Установка .NET Framework: GroupDocs.Annotation для .NET требует совместимой среды выполнения .NET. Убедитесь, что в вашей системе установлена .NET Framework.
2. Доступ к библиотеке GroupDocs.Annotation. Получите доступ к библиотеке GroupDocs.Annotation для .NET, загрузив ее с веб-сайта или через менеджеры пакетов, такие как NuGet.
3. Документ для аннотирования: подготовьте документ (например, PDF), который вы хотите аннотировать. Убедитесь, что документ доступен локально или через службу облачного хранилища, например Azure Blob Storage.

## Импортировать пространства имен
Чтобы начать аннотировать документы с помощью GroupDocs.Annotation for .NET, импортируйте необходимые пространства имен в свой проект. Этот шаг гарантирует, что у вас есть доступ к необходимым классам и функциям.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Загрузить документ из Azure
Чтобы аннотировать документ, хранящийся в хранилище BLOB-объектов Azure, выполните следующие действия.
### Шаг 1. Установите путь вывода
Определите путь вывода, в котором будет сохранен документ с аннотациями.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Шаг 2. Загрузите документ.
 Получите документ из хранилища BLOB-объектов Azure, вызвав метод`DownloadFile` метод.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Логика аннотаций
    annotator.Save(outputPath);
}
```
## Загрузите файл из хранилища BLOB-объектов Azure.
 Чтобы загрузить документ из хранилища BLOB-объектов Azure, реализуйте`DownloadFile` метод.
### Шаг 1. Получение большого двоичного объекта
Получите доступ к контейнеру хранилища BLOB-объектов Azure и получите нужный BLOB-объект.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### Шаг 2. Загрузите содержимое BLOB-объекта
Загрузите содержимое большого двоичного объекта в поток памяти.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Получите контейнер хранилища BLOB-объектов Azure.
 Для взаимодействия с хранилищем BLOB-объектов Azure реализуйте`GetContainer` метод.
### Шаг 1. Инициализация учетных данных хранилища
Предоставьте необходимые учетные данные учетной записи и информацию о конечной точке.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{accountName}.blob.core.windows.net/";
```
### Шаг 2. Создайте клиент BLOB-объектов
Создайте клиент для взаимодействия с хранилищем BLOB-объектов Azure.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### Шаг 3. Получите ссылку на контейнер
Получите ссылку на указанный контейнер.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### Шаг 4. Создайте контейнер, если он не существует
Убедитесь, что контейнер существует, и создайте его, если нет.
```csharp
container.CreateIfNotExists();
```

## Заключение
GroupDocs.Annotation for .NET предоставляет разработчикам надежные возможности аннотирования документов, легко интегрируясь в приложения .NET. Выполнив действия, описанные в этом руководстве, вы сможете эффективно использовать функциональные возможности GroupDocs.Annotation для аннотирования документов, хранящихся в хранилище BLOB-объектов Azure.
#### Часто задаваемые вопросы
### Совместим ли GroupDocs.Annotation для .NET со всеми форматами документов?
GroupDocs.Annotation поддерживает широкий спектр форматов документов, включая PDF, DOCX, PPTX и другие.
### Можно ли настроить аннотации в соответствии с конкретными требованиями?
Да, GroupDocs.Annotation предлагает широкие возможности настройки аннотаций, позволяя пользователям изменять внешний вид, поведение и метаданные.
### Подходит ли GroupDocs.Annotation для совместного аннотирования документов?
Абсолютно! GroupDocs.Annotation упрощает совместное аннотирование документов, позволяя нескольким пользователям одновременно добавлять, редактировать и просматривать аннотации.
### Обеспечивает ли GroupDocs.Annotation кроссплатформенную совместимость?
Да, GroupDocs.Annotation разработан для бесперебойной работы на различных платформах, включая Windows, Linux и macOS.
### Доступна ли техническая поддержка для пользователей GroupDocs.Annotation?
Да, GroupDocs предоставляет комплексную техническую поддержку через свои форумы и специальные каналы поддержки.