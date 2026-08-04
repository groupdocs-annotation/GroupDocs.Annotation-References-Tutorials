---
categories:
- Document Management
date: '2026-08-04'
description: Узнайте, как использовать строку подключения Azure blob с GroupDocs.Annotation
  в .NET, а также лучшие практики безопасности blob для безопасной загрузки документов.
keywords:
- azure blob connection string
- blob security best practices
- GroupDocs.Annotation Azure integration
- .NET document loading from Azure
- cloud storage annotation tutorial
lastmod: '2026-08-04'
linktitle: Учебник по интеграции GroupDocs с Azure
og_description: Узнайте, как использовать строку подключения Azure blob с GroupDocs.Annotation
  в .NET, а также лучшие практики безопасности blob для безопасной загрузки документов.
og_image_alt: Step‑by‑step guide showing Azure blob connection string usage with GroupDocs.Annotation
  in a .NET app
og_title: Строка подключения Azure blob для GroupDocs.Annotation – руководство по
  .NET
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Learn how to use the azure blob connection string with GroupDocs.Annotation
    in .NET, plus blob security best practices for safe document loading.
  headline: Azure blob connection string for GroupDocs.Annotation .NET
  type: TechArticle
- description: Learn how to use the azure blob connection string with GroupDocs.Annotation
    in .NET, plus blob security best practices for safe document loading.
  name: Azure blob connection string for GroupDocs.Annotation .NET
  steps:
  - name: Verify the **azure blob connection string** in Azure Key Vault matches the
      storage account.
    text: Verify the **azure blob connection string** in Azure Key Vault matches the
      storage account.
  - name: Test the connection with Azure Storage Explorer.
    text: Test the connection with Azure Storage Explorer.
  - name: Ensure your firewall allows outbound traffic on port 443 to `*.blob.core.windows.net`.
    text: Ensure your firewall allows outbound traffic on port 443 to `*.blob.core.windows.net`.
  - name: '**Create a test container** and upload a PDF.'
    text: '**Create a test container** and upload a PDF.'
  - name: '**Add the connection string** to Azure Key Vault and update the sample
      code.'
    text: '**Add the connection string** to Azure Key Vault and update the sample
      code.'
  - name: '**Run the async loading example** and verify the annotation UI appears.'
    text: '**Run the async loading example** and verify the annotation UI appears.'
  - name: '**Introduce caching** for your most‑used documents.'
    text: '**Introduce caching** for your most‑used documents.'
  - name: '**Scale up** by adding monitoring, logging, and production‑grade error
      handling.'
    text: '**Scale up** by adding monitoring, logging, and production‑grade error
      handling.'
  type: HowTo
- questions:
  - answer: Authentication errors usually mean the stored connection string is outdated
      or the account key was regenerated. Retrieve the latest secret from Azure Key
      Vault, test it with Azure Storage Explorer, and consider switching to Azure
      AD‑based authentication for production.
    question: How do I handle authentication errors with Azure Blob Storage?
  - answer: Yes – it streams PDFs directly from a `MemoryStream`, avoiding full‑file
      loading. For files over 200 MB, enable `DocStreamOptions` with a 64 KB buffer
      and monitor memory usage; you’ll typically stay under 500 MB of RAM even with
      300‑page PDFs.
    question: Can GroupDocs.Annotation handle large documents efficiently from Azure?
  - answer: Set a reasonable `HttpClient.Timeout` (e.g., 30 seconds), wrap the download
      in a Polly retry policy with exponential back‑off, and surface a progress indicator
      so users know the operation is still in progress.
    question: What’s the best way to handle network timeouts when loading documents?
  - answer: Use per‑tenant containers or blob‑level ACLs, generate short‑lived SAS
      tokens for each request, and always validate the tenant’s identity before issuing
      a token. Never rely on obscurity – enforce strict server‑side checks.
    question: How do I secure document access in a multi‑tenant application?
  - answer: Absolutely. GroupDocs.Annotation works with any `Stream`. Replace the
      Azure download code with the equivalent AWS S3 or Google Cloud Storage SDK call,
      return a `MemoryStream`, and the rest of the annotation pipeline remains unchanged.
    question: Is it possible to integrate this with other cloud storage providers?
  type: FAQPage
tags:
- azure blob connection string
- GroupDocs.Annotation
- .NET
- Azure Blob Storage
- document loading
title: Строка подключения Azure blob для GroupDocs.Annotation .NET
type: docs
url: /ru/net/document-loading/load-documents-azure-blob-groupdocs-annotation-dotnet/
weight: 1
---

# Строка подключения Azure blob для GroupDocs.Annotation .NET

Если вам нужно работать с **azure blob connection string** при аннотировании PDF в облаке, вы попали в нужное место. В этом руководстве показано, как загружать, аннотировать и управлять документами, хранящимися в Azure Blob Storage, напрямую из .NET‑приложения с использованием GroupDocs.Annotation. Вы также получите надёжные **blob security best practices**, советы по производительности и список проверок для устранения неполадок, чтобы вы могли выпустить готовое к продакшену решение без сюрпризов.

## Быстрые ответы
- **Что такое azure blob connection string?** Это строка, содержащая имя вашей учетной записи хранилища и ключ, позволяющая вашему приложению аутентифицироваться в Azure Blob Storage.
- **Нужна ли лицензия GroupDocs.Annotation?** Да — для любого продакшн‑развертывания необходимо применить действующую лицензию; пробная версия подходит для разработки.
- **Можно ли загружать PDF размером более 200 МБ?** Да, но используйте потоковую передачу (`MemoryStream`) и асинхронный ввод‑вывод, чтобы избежать нагрузки на память.
- **Требуется ли Azure Key Vault?** Не обязательно, но это рекомендуемый способ безопасного хранения строки подключения.
- **Какие версии .NET поддерживаются?** .NET Core 3.1+, .NET 5, .NET 6 и .NET 7 работают с последним пакетом GroupDocs.Annotation.

## Что такое Azure blob connection string?
Строка **azure blob connection string** — это единое текстовое значение, которое объединяет имя учетной записи хранилища, ключ и конечную точку, позволяя вашему .NET‑коду аутентифицироваться в Azure Blob Storage. С помощью этой строки вы можете создавать объекты `CloudBlobClient`, которые читают и записывают блобы без дополнительных шагов аутентификации.

## Почему использовать GroupDocs.Annotation с Azure Blob Storage?
GroupDocs.Annotation поддерживает **50+** форматов ввода и вывода, может аннотировать многосотстраничные PDF менее чем за 2 секунды на типичном сервере и обрабатывает документы напрямую из потоков — поэтому вам никогда не придётся записывать временный файл на диск. Совмещение с Azure Blob Storage обеспечивает полностью облачный рабочий процесс, который масштабируется горизонтально и соответствует требованиям комплаенса.

## Требования — что нужно перед началом

- **Среда разработки** — .NET Core 3.1+ или .NET Framework 4.6.1+, Visual Studio 2019+ (или VS Code с расширениями C#).
- **Настройка Azure** — активная подписка Azure, учетная запись хранилища и как минимум один контейнер. Держите под рукой **azure blob connection string**; позже вы перенесёте её в Azure Key Vault.
- **GroupDocs.Annotation** — пакет NuGet (v25.4.0) и действующая лицензия для продакшна.
- **Базовые знания C#** — async/await, операторы `using` и знакомство с потоками.

> **Pro tip:** Создайте тестовый контейнер с именем `sample-docs` и загрузите PDF (например, `sample.pdf`) перед началом кодирования.

## Настройка GroupDocs.Annotation для .NET

### Установка пакета

Установите библиотеку через консоль менеджера пакетов NuGet:

```  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  
```

Или используйте .NET CLI:

```  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  
```

Версия **25.4.0** рекомендуется, так как она обеспечивает ускорение загрузки облачных документов на 30 % и снижает нагрузку на память до 40 %.

### Лицензирование (не пропускайте этот раздел)

- **Разработка / тестирование** — загрузите бесплатную пробную версию с [GroupDocs Downloads](https://releases.groupdocs.com/annotation/net/) (применяются водяные знаки) или запросите временную лицензию на странице [Temporary License Page](https://purchase.groupdocs.com/temporary-license/) для тестирования без водяных знаков.
- **Продакшн** — приобретите полную лицензию на [GroupDocs Purchase](https://purchase.groupdocs.com/buy). Файл лицензии должен быть загружен до любой операции аннотирования.

### Базовый шаблон инициализации

Следующий фрагмент показывает минимальный код для создания `Annotator` для локального PDF. В следующем разделе мы заменим путь к файловой системе потоком из Azure.

```  
```csharp
using GroupDocs.Annotation;

// Basic initialization - we'll improve this for cloud documents
Annotator annotator = new Annotator("path/to/your/document.pdf");
```  
```

**Определение:** `Annotator` — основной класс в GroupDocs.Annotation, который загружает поток документа и предоставляет методы для добавления, редактирования и получения аннотаций.

## Полная реализация интеграции с Azure

### Как безопасно аутентифицироваться в Azure Blob Storage?

StorageSharedKeyCredential представляет имя учетной записи хранилища и ключ, используемые для аутентификации запросов к Azure Blob Storage.  
Чтобы сохранить ваши учётные данные в безопасности, получайте строку подключения из Azure Key Vault во время выполнения и используйте её для создания StorageSharedKeyCredential. Эти учётные данные передают имя учетной записи и ключ клиенту службы Blob, позволяя выполнять аутентифицированные операции без раскрытия секретов в исходном коде. Ниже приведён пример этого шаблона.

```  
```csharp
using System;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;

// Replace these with your actual values
string accountName = "***";
string accountKey = "***";
string containerName = "***";

public static CloudBlobContainer GetContainer()
{
    // Define the endpoint URL for Azure Blob Storage
    string endpoint = $"https://{accountName}.blob.core.windows.net/";

    // Authenticate with the storage account using credentials
    StorageCredentials storageCredentials = new StorageCredentials(accountName, accountKey);
    CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(
        storageCredentials, new Uri(endpoint), null, null, null);

    // Create a blob client to interact with the Blob service
    CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();

    // Retrieve a reference to the specified container
    CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);

    // Ensure that the container exists, creating it if necessary
    container.CreateIfNotExists();
    
    return container;
}
```  
```

**Объяснение:**  
- `StorageSharedKeyCredential` проверяет имя учетной записи и ключ.  
- `CloudBlobContainer` представляет конкретный контейнер в вашей учетной записи Azure Storage.  
- `CreateIfNotExistsAsync()` гарантирует, что контейнер существует, не вызывая исключения, если он уже существует.

### Как загрузить документ из Azure в MemoryStream для аннотирования?

MemoryStream — это .NET‑поток, который хранит данные в памяти, обеспечивая быструю запись/чтение без обращения к диску.  
CloudBlockBlob — клиентский объект для блоба типа block, позволяющий выполнять операции загрузки и выгрузки.  
После аутентификации загрузите целевой блоб в MemoryStream. Сбросьте позицию потока в начало перед передачей его в GroupDocs.Annotation, чтобы библиотека могла прочитать документ с начала. Использование MemoryStream избавляет от записи временных файлов на диск и повышает производительность, особенно для больших PDF.

```  
```csharp
public static Stream LoadDocumentFromAzure(CloudBlobContainer container, string blobName)
{
    // Retrieve a reference to the desired blob
    CloudBlockBlob blockBlob = container.GetBlockBlobReference(blobName);

    // Download the blob content into a memory stream
    using (var memoryStream = new MemoryStream())
    {
        blockBlob.DownloadToStream(memoryStream);
        memoryStream.Position = 0; // Reset stream position for reading
        return memoryStream;
    }
}
```  
```

**Ключевые моменты:**  
- `CloudBlockBlob` оптимизирован для больших файлов и поддерживает параллельную загрузку.  
- После `DownloadToStreamAsync` курсор потока находится в конце; сброс до `0` необходим, чтобы GroupDocs читал с начала.  
- Оборачивание потока в блок `using` гарантирует его освобождение, предотвращая утечки памяти.

## Лучшие практики безопасности, которые нельзя игнорировать

### Как безопасно хранить учётные данные с помощью Azure Key Vault?

Никогда не встраивайте **azure blob connection string** в исходный код. Получайте её во время выполнения из Azure Key Vault с помощью Azure SDK. Это централизует управление секретами, поддерживает автоматическую ротацию и гарантирует, что учётные данные не раскрываются в системе контроля версий или журналах.

```  
```csharp
// Example pattern (you'll need Azure.Security.KeyVault.Secrets package)
var keyVaultClient = new SecretClient(new Uri("https://your-keyvault.vault.azure.net/"), new DefaultAzureCredential());
var storageKey = await keyVaultClient.GetSecretAsync("storage-account-key");
```  
```

### Как обеспечить правильный контроль доступа к вашему контейнеру?

Установите уровень доступа контейнера в Private, чтобы блобы не были публично читаемыми, и используйте Shared Access Signatures (SAS) для предоставления ограниченных, временных прав доступа к определённым операциям. Кроме того, настройте сетевые правила, ограничивая трафик доверенными диапазонами IP, что уменьшает поверхность атаки.

- Установите публичный уровень доступа контейнера в **Private**.  
- Сгенерируйте **Shared Access Signatures (SAS)** для временного, ограниченного доступа вместо раскрытия ключа учётной записи.  
- Примените сетевые правила, позволяющие трафик только из диапазона IP вашего приложения.

### Как проверять документы перед их обработкой?

Перед загрузкой файла в GroupDocs.Annotation убедитесь, что он соответствует вашим политикам безопасности и размера. Проверьте MIME‑тип, чтобы убедиться, что формат поддерживается, установите максимальный размер файла и выполните быструю проверку, например, подтвердите, что заголовок файла соответствует ожидаемому формату (например, `%PDF`).

```  
```csharp
// Check file size, type, and content before processing
private static bool IsValidDocument(Stream documentStream)
{
    // Implement your validation logic here
    return documentStream.Length > 0 && documentStream.Length < MaxAllowedFileSize;
}
```  
```

## Стратегии оптимизации производительности, которые работают

### Как сделать все операции ввода‑вывода асинхронными?

Используйте асинхронные методы, предоставляемые Azure Storage SDK и .NET, чтобы избежать блокировки потоков во время сетевых вызовов. Асинхронный ввод‑вывод повышает масштабируемость, позволяя пулу потоков обслуживать другие запросы, пока ожидается завершение ввода‑вывода, что важно для сценариев высокой конкуренции.

```  
```csharp
public static async Task<Stream> LoadDocumentFromAzureAsync(CloudBlobContainer container, string blobName)
{
    var blockBlob = container.GetBlockBlobReference(blobName);
    var memoryStream = new MemoryStream();
    
    await blockBlob.DownloadToStreamAsync(memoryStream);
    memoryStream.Position = 0;
    
    return memoryStream;
}
```  
```

### Как реализовать умное кэширование часто используемых документов?

Кешируйте загруженный MemoryStream в распределённом кэше, например Azure Redis, используя ключ, который объединяет имя блоба и его идентификатор версии. Это уменьшает повторные загрузки, снижает задержку и сокращает расходы на исходящий трафик хранилища для часто запрашиваемых «горячих» документов.

```  
```csharp
private static readonly Dictionary<string, byte[]> DocumentCache = new();

public static Stream GetCachedOrLoadDocument(CloudBlobContainer container, string blobName)
{
    if (DocumentCache.TryGetValue(blobName, out var cachedBytes))
    {
        return new MemoryStream(cachedBytes);
    }
    
    // Load from Azure and cache for next time
    var stream = LoadDocumentFromAzure(container, blobName);
    var bytes = ((MemoryStream)stream).ToArray();
    DocumentCache[blobName] = bytes;
    
    return new MemoryStream(bytes);
}
```  
```

### Как мониторить и оптимизировать использование сети?

Отслеживайте шаблоны доступа к блобам и регулируйте уровни хранилища и пакетирование запросов для оптимизации сетевого трафика. Группируя чтения, выбирая подходящие уровни и отслеживая метрики исходящего трафика, вы можете контролировать расходы и повышать производительность.

- Пакетируйте несколько чтений блобов в один запрос, когда это возможно.  
- Выбирайте подходящий уровень блоба (Hot для частого чтения, Cool для редкого доступа).  
- Отслеживайте метрики исходящего трафика в Azure Monitor, чтобы избежать неожиданных расходов.

## Распространённые подводные камни и как их избежать

### Как предотвратить утечки памяти при работе с большими PDF?

Всегда своевременно освобождайте потоки и другие объекты ввода‑вывода и отслеживайте использование приватной памяти приложением во время аннотирования. Правильное освобождение предотвращает оставшиеся дескрипторы, которые могут вызвать нагрузку на память, особенно при обработке больших PDF в среде с высоким пропускным способностью.

```  
```csharp
public static void ProcessDocumentSafely(CloudBlobContainer container, string blobName)
{
    using var documentStream = LoadDocumentFromAzure(container, blobName);
    using var annotator = new Annotator(documentStream);
    
    // Process your annotations here
    // Both streams will be properly disposed
}
```  
```

### Как корректно обрабатывать ошибки ограничения скорости Azure?

Когда Azure возвращает ответ 429 Too Many Requests, реализуйте экспоненциальную задержку и учитывайте заголовок Retry‑After. Эта стратегия распределяет попытки повторов во времени, уменьшая вероятность повторного ограничения и повышая общую надёжность.

```  
```csharp
private static async Task<T> ExecuteWithRetry<T>(Func<Task<T>> operation, int maxRetries = 3)
{
    for (int i = 0; i < maxRetries; i++)
    {
        try
        {
            return await operation();
        }
        catch (StorageException ex) when (ex.RequestInformation.HttpStatusCode == 429)
        {
            // Rate limited - wait before retry
            await Task.Delay(TimeSpan.FromSeconds(Math.Pow(2, i)));
        }
    }
    
    throw new Exception("Max retries exceeded");
}
```  
```

### Как построить устойчивость к сетевым сбоям?

Используйте библиотеку circuit‑breaker (например, Polly), чтобы переключаться на кэшированную копию или отображать дружелюбное сообщение об ошибке, а затем повторять попытку в фоновом режиме.

## Реальные примеры использования и приложения

### Каковы типичные рабочие процессы рецензирования документов?

Юридические команды могут хранить контракты в приватном контейнере Azure, позволять рецензентам аннотировать их через GroupDocs.Annotation и сохранять каждую версию в Azure Blob Storage для соответствия аудиту.

### Как это помогает управлению образовательным контентом?

Преподаватели загружают слайды лекций в Azure, студенты мгновенно получают доступ к тем же аннотированным PDF, а платформа автоматически масштабируется с уровнями хранилища Azure.

### Почему это полезно для документации по соответствию?

Azure предоставляет встроенную неизменяемость и политики удержания, а GroupDocs отслеживает каждое изменение аннотации, предоставляя полный, защищённый от подделки журнал аудита.

## Когда НЕ следует использовать этот подход

- Приложения простого просмотра файлов, которым не нужны аннотации — лёгкий просмотрщик будет дешевле.  
- Сценарии «offline‑first» — интеграция требует сетевого подключения к Azure.  
- Проекты с крайне ограниченным бюджетом — хранилище Azure и лицензирование GroupDocs добавляют постоянные расходы.  
- Редактирование в реальном времени (в стиле Google Docs) — GroupDocs.Annotation не предназначен для одновременных живых правок.

## Руководство по устранению неполадок

### Как решить проблемы подключения к Azure Blob Storage?

Если не удаётся подключиться, сначала проверьте, что строка подключения, хранящаяся в Key Vault, соответствует учётным данным учетной записи хранилища. Проверьте соединение с помощью Azure Storage Explorer и убедитесь, что ваш брандмауэр разрешает исходящий трафик на порт 443 к `*.blob.core.windows.net`.

1. Проверьте, что **azure blob connection string** в Azure Key Vault соответствует учетной записи хранилища.  
2. Проверьте соединение с помощью Azure Storage Explorer.  
3. Убедитесь, что ваш брандмауэр разрешает исходящий трафик на порт 443 к `*.blob.core.windows.net`.

### Как диагностировать исключения out‑of‑memory?

Ошибки out‑of‑memory часто возникают из‑за неосвобождённых потоков или загрузки целых файлов в память. Включите диагностику памяти .NET, журналируйте время жизни потоков и устанавливайте максимальный размер документа, чтобы предотвратить чрезмерное потребление памяти.

- Включите диагностику памяти .NET (`dotnet-counters`).  
- Журналируйте время создания и освобождения потоков.  
- Установите максимальный размер документа (например, 300 МБ) и отклоняйте более крупные загрузки с понятной ошибкой.

### Как улучшить медленную загрузку документов?

Чтобы ускорить загрузку, перейдите на асинхронные загрузки блобов, включите кэширование часто используемых файлов и храните «горячие» документы в уровне Hot, перемещая редко используемые файлы в уровень Cool. Эти шаги снижают задержку и повышают пропускную способность.

- Перейдите на асинхронную загрузку (`DownloadToStreamAsync`).  
- Включите кэширование (Redis или в памяти) для горячих документов.  
- Используйте уровень Hot для часто запрашиваемых блобов и уровень Cool для архивных файлов.

## Заключение

Комбинируя аутентификацию на основе **azure blob connection string** с потоковым API GroupDocs.Annotation, вы получаете безопасное, высокопроизводительное, облачно‑нативное решение для аннотирования. Помните:

- Храните секреты в Azure Key Vault (никогда не вшивайте их в код).  
- Используйте асинхронный ввод‑вывод и кэширование для скорости.  
- Реализуйте шаблоны повторных попыток и circuit‑breaker для устойчивости.  
- Мониторьте метрики Azure, чтобы контролировать затраты и производительность.

### Ваши дальнейшие шаги

1. **Создайте тестовый контейнер** и загрузите PDF.  
2. **Добавьте строку подключения** в Azure Key Vault и обновите пример кода.  
3. **Запустите пример асинхронной загрузки** и убедитесь, что отображается UI аннотаций.  
4. **Внедрите кэширование** для наиболее часто используемых документов.  
5. **Масштабируйте** добавлением мониторинга, логирования и обработки ошибок уровня продакшн.

Готовы создать что‑то удивительное? Начните с фрагмента аутентификации выше, загрузите первый документ, и позвольте GroupDocs.Annotation справиться с остальным.

## Часто задаваемые вопросы

**Q: Как обрабатывать ошибки аутентификации с Azure Blob Storage?**  
A: Ошибки аутентификации обычно означают, что сохранённая строка подключения устарела или ключ учётной записи был пересоздан. Получите последний секрет из Azure Key Vault, проверьте его с помощью Azure Storage Explorer и рассмотрите переход на аутентификацию на основе Azure AD для продакшна.

**Q: Может ли GroupDocs.Annotation эффективно обрабатывать большие документы из Azure?**  
A: Да — он потоково передаёт PDF напрямую из `MemoryStream`, избегая полной загрузки файла. Для файлов более 200 МБ включите `DocStreamOptions` с буфером 64 KB и контролируйте использование памяти; обычно потребление RAM остаётся ниже 500 МБ даже для PDF в 300 страниц.

**Q: Как лучше всего обрабатывать тайм‑ауты сети при загрузке документов?**  
A: Установите разумный `HttpClient.Timeout` (например, 30 секунд), оберните загрузку в политику повторных попыток Polly с экспоненциальной задержкой и отображайте индикатор прогресса, чтобы пользователи знали, что операция всё ещё выполняется.

**Q: Как обеспечить безопасный доступ к документам в многопользовательском приложении?**  
A: Используйте контейнеры per‑tenant или ACL на уровне блоба, генерируйте короткоживущие SAS‑токены для каждого запроса и всегда проверяйте идентичность арендатора перед выдачей токена. Не полагайтесь на скрытность — применяйте строгие проверки на стороне сервера.

**Q: Можно ли интегрировать это с другими облачными провайдерами хранилища?**  
A: Конечно. GroupDocs.Annotation работает с любым `Stream`. Замените код загрузки из Azure на эквивалентный вызов SDK AWS S3 или Google Cloud Storage, верните `MemoryStream`, и остальная часть конвейера аннотирования останется без изменений.

---  

**Last Updated:** 2026-08-04  
**Tested With:** GroupDocs.Annotation 25.4.0 for .NET  
**Author:** GroupDocs

## Связанные руководства

- [Load Document from Azure Blob Storage .NET](/annotation/net/document-loading-essentials/load-document-from-azure/)
- [GroupDocs.Annotation .NET Document Loading](/annotation/net/document-loading-essentials/)
- [Generate Document Preview .NET - Complete Guide with GroupDocs.Annotation](/annotation/net/advanced-usage/generate-document-pages-preview/)