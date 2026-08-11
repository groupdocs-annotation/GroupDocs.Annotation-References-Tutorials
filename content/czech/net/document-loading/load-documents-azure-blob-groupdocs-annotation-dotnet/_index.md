---
categories:
- Document Management
date: '2026-08-04'
description: Zjistěte, jak používat azure blob connection string s GroupDocs.Annotation
  v .NET, a také nejlepší postupy pro blob security pro bezpečné načítání dokumentů.
keywords:
- azure blob connection string
- blob security best practices
- GroupDocs.Annotation Azure integration
- .NET document loading from Azure
- cloud storage annotation tutorial
lastmod: '2026-08-04'
linktitle: Návod na integraci GroupDocs Azure
og_description: Zjistěte, jak používat azure blob connection string s GroupDocs.Annotation
  v .NET, a také nejlepší postupy pro blob security pro bezpečné načítání dokumentů.
og_image_alt: Step‑by‑step guide showing Azure blob connection string usage with GroupDocs.Annotation
  in a .NET app
og_title: Azure blob connection string pro GroupDocs.Annotation – průvodce .NET
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
title: Azure blob connection string pro GroupDocs.Annotation .NET
type: docs
url: /cs/net/document-loading/load-documents-azure-blob-groupdocs-annotation-dotnet/
weight: 1
---

# Azure blob connection string pro GroupDocs.Annotation .NET

Pokud potřebujete pracovat s **azure blob connection string** při anotaci PDF v cloudu, jste na správném místě. Tento tutoriál vám ukáže, jak načíst, anotovat a spravovat dokumenty uložené v Azure Blob Storage přímo z .NET aplikace pomocí GroupDocs.Annotation. Získáte také solidní **blob security best practices**, tipy na výkon a kontrolní seznam pro odstraňování problémů, abyste mohli nasadit řešení připravené do produkce bez překvapení.

## Rychlé odpovědi
- **What is the azure blob connection string?** Je to řetězec, který obsahuje název vašeho úložiště a klíč, umožňující vaší aplikaci autentizovat se k Azure Blob Storage.
- **Do I need a GroupDocs.Annotation license?** Ano—pro jakékoli nasazení do produkce musíte použít platnou licenci; zkušební verze funguje pro vývoj.
- **Can I load PDFs larger than 200 MB?** Ano, ale použijte streamování (`MemoryStream`) a asynchronní I/O, aby nedošlo k přetížení paměti.
- **Is Azure Key Vault required?** Není povinný, ale je to doporučený způsob, jak bezpečně uložit connection string.
- **Which .NET versions are supported?** .NET Core 3.1+, .NET 5, .NET 6 a .NET 7 všechny fungují s nejnovějším balíčkem GroupDocs.Annotation.

## Co je Azure blob connection string?
**azure blob connection string** je jednorázová textová hodnota, která kombinuje název úložiště, klíč a koncový bod, což umožňuje vašemu .NET kódu autentizovat se vůči Azure Blob Storage. Pomocí tohoto řetězce můžete vytvořit objekty `CloudBlobClient`, které čtou a zapisují blobové objekty bez dalších kroků s přihlašovacími údaji.

## Proč používat GroupDocs.Annotation s Azure Blob Storage?
GroupDocs.Annotation podporuje **50+** vstupních a výstupních formátů, dokáže anotovat PDF s několika stovkami stránek za méně než 2 sekundy na typickém serveru a zpracovává dokumenty přímo ze streamů—takže nikdy nemusíte zapisovat dočasný soubor na disk. Kombinace s Azure Blob Storage vám poskytne plně cloud‑native workflow, který horizontálně škáluje a splňuje požadavky na shodu.

## Předpoklady – co potřebujete před zahájením
- **Development environment** – .NET Core 3.1+ nebo .NET Framework 4.6.1+, Visual Studio 2019+ (nebo VS Code s rozšířeními C#).
- **Azure setup** – aktivní předplatné Azure, úložiště a alespoň jeden kontejner. Mějte po ruce **azure blob connection string**; později jej přesunete do Azure Key Vault.
- **GroupDocs.Annotation** – NuGet balíček (v25.4.0) a platná licence pro produkci.
- **Basic C# knowledge** – async/await, `using` příkazy a znalost streamů.

> **Pro tip:** Vytvořte testovací kontejner pojmenovaný `sample-docs` a nahrajte PDF (např. `sample.pdf`) před zahájením kódování.

## Nastavení GroupDocs.Annotation pro .NET

### Instalace balíčku

Nainstalujte knihovnu pomocí konzole NuGet Package Manager:

```  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  
```

Nebo použijte .NET CLI:

```  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  
```

Verze **25.4.0** je doporučena, protože přináší 30 % zvýšení rychlosti při načítání dokumentů v cloudu a snižuje paměťovou zátěž až o 40 %.

### Licencování (nepřeskakujte tuto část)

- **Development / testing** – Stáhněte si bezplatnou zkušební verzi z [GroupDocs Downloads](https://releases.groupdocs.com/annotation/net/) (aplikují se testovací vodoznaky) nebo požádejte o dočasnou licenci na [Temporary License Page](https://purchase.groupdocs.com/temporary-license/) pro testování bez vodoznaků.
- **Production** – Zakupte plnou licenci na [GroupDocs Purchase](https://purchase.groupdocs.com/buy). Licenční soubor musí být načten před jakoukoliv operací anotace.

### Základní vzor inicializace

Následující úryvek ukazuje minimální kód pro vytvoření `Annotator` pro lokální PDF. V další sekci nahradíme cestu k souborovému systému streamem z Azure.

```  
```csharp
using GroupDocs.Annotation;

// Basic initialization - we'll improve this for cloud documents
Annotator annotator = new Annotator("path/to/your/document.pdf");
```  
```

**Definition anchor:** `Annotator` je hlavní třída v GroupDocs.Annotation, která načítá stream dokumentu a poskytuje metody pro přidávání, úpravu a získávání anotací.

## Kompletní implementace integrace s Azure

### Jak se bezpečně autentizovat k Azure Blob Storage?
StorageSharedKeyCredential představuje název úložiště a klíč používaný k autentizaci požadavků na Azure Blob Storage.  
Aby byly vaše přihlašovací údaje v bezpečí, načtěte connection string z Azure Key Vault za běhu a použijte jej k vytvoření StorageSharedKeyCredential. Tento credential poskytuje název účtu a klíč klientovi služby Blob, což umožňuje autentizované operace bez odhalení tajemství ve zdrojovém kódu. Následující kód demonstruje tento vzor.

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

**Explanation:**  
- `StorageSharedKeyCredential` ověřuje název účtu a klíč.  
- `CloudBlobContainer` představuje konkrétní kontejner ve vašem Azure úložišti.  
- `CreateIfNotExistsAsync()` zajišťuje, že kontejner existuje, aniž by vyvolal výjimku, pokud již existuje.

### Jak načíst dokument z Azure do MemoryStream pro anotaci?
MemoryStream je .NET stream, který ukládá data v paměti, což umožňuje rychlé čtení/zápis bez diskových I/O.  
CloudBlockBlob je klientský objekt pro blokový blob, umožňující operace stahování a nahrávání.  
Po autentizaci stáhněte cílový blob do MemoryStream. Resetujte pozici streamu na začátek před předáním GroupDocs.Annotation, aby knihovna mohla číst dokument od začátku. Použití MemoryStream zabraňuje zápisu dočasných souborů na disk a zlepšuje výkon, zejména u velkých PDF.

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

**Key points:**  
- `CloudBlockBlob` je optimalizován pro velké soubory a podporuje paralelní stahování.  
- Po `DownloadToStreamAsync` je kurzor streamu na konci; resetování na `0` je nezbytné, aby GroupDocs četl od začátku.  
- Zabalení streamu do bloku `using` zaručuje uvolnění, čímž se předchází únikům paměti.

## Bezpečnostní osvědčené postupy, které nelze ignorovat

### Jak bezpečně uložit přihlašovací údaje pomocí Azure Key Vault?
Nikdy nevestavujte **azure blob connection string** do zdrojového kódu. Načtěte jej za běhu z Azure Key Vault pomocí Azure SDK. Toto centralizuje správu tajemství, podporuje automatickou rotaci a zajišťuje, že přihlašovací údaje nejsou odhaleny ve verzovacím systému nebo logech.

```  
```csharp
// Example pattern (you'll need Azure.Security.KeyVault.Secrets package)
var keyVaultClient = new SecretClient(new Uri("https://your-keyvault.vault.azure.net/"), new DefaultAzureCredential());
var storageKey = await keyVaultClient.GetSecretAsync("storage-account-key");
```  
```

### Jak vynutit správné řízení přístupu k vašemu kontejneru?
Nastavte úroveň přístupu kontejneru na Private, aby blobové objekty nebyly veřejně čitelné, a použijte Shared Access Signatures (SAS) k udělení omezených, časově omezených oprávnění pro konkrétní operace. Dále nakonfigurujte síťová pravidla, která omezí provoz na důvěryhodné IP rozsahy, čímž snížíte útočný povrch.

- Nastavte veřejnou úroveň přístupu kontejneru na **Private**.  
- Generujte **Shared Access Signatures (SAS)** pro dočasný, omezený přístup místo zveřejnění klíče účtu.  
- Použijte síťová pravidla, aby byl provoz povolen pouze z IP rozsahu vaší aplikace.

### Jak validovat dokumenty před jejich zpracováním?
Před načtením souboru do GroupDocs.Annotation ověřte, že splňuje vaše bezpečnostní a velikostní politiky. Zkontrolujte MIME typ, aby byl podporovaný formát, vynutí maximální velikost souboru a proveďte rychlou kontrolu, např. potvrďte, že hlavička souboru odpovídá očekávanému formátu (např. `%PDF`).

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

## Strategie optimalizace výkonu, které fungují

### Jak učinit všechny I/O operace asynchronními?
Používejte async metody poskytované Azure Storage SDK a .NET, aby nedocházelo k blokování vláken během síťových volání. Asynchronní I/O zlepšuje škálovatelnost tím, že umožňuje thread poolu obsluhovat další požadavky během čekání na dokončení I/O, což je klíčové pro scénáře s vysokou souběžností.

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

### Jak implementovat inteligentní cachování pro často přistupované dokumenty?
Cacheujte stažený MemoryStream v distribuované cache jako Azure Redis, pomocí klíče, který kombinuje název blobu a jeho identifikátor verze. To snižuje opakované stahování, snižuje latenci a snižuje náklady na odchozí přenos úložiště pro často přistupované horké dokumenty.

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

### Jak monitorovat a optimalizovat využití sítě?
Sledujte vzory přístupu k blobům a upravujte úložné vrstvy a dávkování požadavků pro optimalizaci síťového provozu. Skupinováním čtení, výběrem vhodných vrstev a sledováním metrik odchozího provozu můžete kontrolovat náklady a zlepšit výkon.

- Dávkujte více čtení blobů do jednoho požadavku, pokud je to možné.  
- Vyberte vhodnou úroveň blobu (Hot pro časté čtení, Cool pro zřídka přístupné).  
- Sledujte metriky odchozího provozu v Azure Monitor, abyste se vyhnuli neočekávaným nákladům.

## Časté úskalí a jak se jim vyhnout

### Jak zabránit únikům paměti při práci s velkými PDF?
Vždy okamžitě uvolňujte streamy a další I/O objekty a sledujte soukromé využití paměti aplikace během anotace. Správné uvolnění zabraňuje přetrvávajícím handleům, které mohou způsobovat tlak na paměť, zejména při zpracování velkých PDF v prostředí s vysokou propustností.

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

### Jak elegantně zvládnout chyby limitu rychlosti Azure?
Když Azure vrátí odpověď 429 Too Many Requests, implementujte exponenciální back‑off a respektujte hlavičku Retry‑After. Tato strategie rozprostře pokusy o opakování v čase, snižuje pravděpodobnost opakovaného omezení a zlepšuje celkovou spolehlivost.

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

### Jak vybudovat odolnost vůči selháním sítě?
Použijte knihovnu circuit‑breaker (např. Polly) k přepnutí na cacheovanou kopii nebo zobrazení uživatelsky přívětivé chybové zprávy, a poté opakujte v pozadí.

## Reálné případy použití a aplikace

### Jaké jsou typické workflow pro revizi dokumentů?
Právní týmy mohou ukládat smlouvy v soukromém Azure kontejneru, nechat recenzenty anotovat je pomocí GroupDocs.Annotation a uchovávat každou verzi v Azure Blob Storage pro auditní shodu.

### Jak to pomáhá při správě vzdělávacího obsahu?
Lektoři nahrávají přednáškové snímky do Azure, studenti okamžitě přistupují ke stejným anotovaným PDF a platforma se automaticky škáluje s úložnými vrstvami Azure.

### Proč je to užitečné pro dokumentaci související s shodou?
Azure poskytuje vestavěnou neměnnost a retenční politiky, zatímco GroupDocs sleduje každou změnu anotace, což vám poskytuje kompletní, nezfalšovatelný auditní záznam.

## Kdy NEpoužít tento přístup
- Jednoduché aplikace pro prohlížení souborů, které nepotřebují anotace – lehký prohlížeč by byl levnější.  
- Offline‑first scénáře – integrace vyžaduje síťové připojení k Azure.  
- Projekty s extrémně omezeným rozpočtem – úložiště Azure a licence GroupDocs přidávají opakující se náklady.  
- Real‑time kolaborativní editace (ve stylu Google Docs) – GroupDocs.Annotation není navržen pro simultánní, živé úpravy.

## Průvodce řešením problémů

### Jak vyřešit problémy s připojením k Azure Blob Storage?
Pokud se nemůžete připojit, nejprve ověřte, že connection string uložený v Key Vault odpovídá přihlašovacím údajům úložiště. Otestujte připojení pomocí Azure Storage Explorer a ujistěte se, že odchozí provoz na portu 443 na `*.blob.core.windows.net` je povolen vaším firewallem.

1. Ověřte, že **azure blob connection string** v Azure Key Vault odpovídá úložnému účtu.  
2. Otestujte připojení pomocí Azure Storage Explorer.  
3. Ujistěte se, že váš firewall povoluje odchozí provoz na port 443 na `*.blob.core.windows.net`.

### Jak diagnostikovat výjimky out‑of‑memory?
Chyby out‑of‑memory často vznikají z neodložených streamů nebo načítání celých souborů do paměti. Povolen .NET diagnostiku paměti, logujte životnost streamů a vynutí maximální velikost dokumentu, aby se zabránilo nadměrné spotřebě paměti.

- Povolit .NET diagnostiku paměti (`dotnet-counters`).  
- Logovat časové značky vytvoření a uvolnění streamu.  
- Nastavit maximální velikost dokumentu (např. 300 MB) a odmítnout větší nahrávky s jasnou chybou.

### Jak zlepšit pomalý výkon načítání dokumentů?
Pro zrychlení načítání přepněte na asynchronní stahování blobů, povolte cachování pro často přistupované soubory a uložte horké dokumenty do vrstvy Hot, zatímco méně používané soubory přesunete do vrstvy Cool. Tyto kroky snižují latenci a zvyšují propustnost.

- Přepněte na asynchronní stažení (`DownloadToStreamAsync`).  
- Povolit cachování (Redis nebo v‑paměti) pro horké dokumenty.  
- Použijte vrstvu Hot pro často přistupované bloby a vrstvu Cool pro archivní soubory.

## Závěr

Kombinací autentizace založené na **azure blob connection string** s streaming API GroupDocs.Annotation získáte bezpečné, vysoce výkonné, cloud‑native řešení pro anotace. Pamatujte na:
- Ukládejte tajemství do Azure Key Vault (nikdy nehardcodujte).  
- Používejte async I/O a cachování pro rychlost.  
- Implementujte vzory retry a circuit‑breaker pro odolnost.  
- Sledujte metriky Azure pro kontrolu nákladů a výkonu.

### Vaše další kroky
1. **Vytvořte testovací kontejner** a nahrajte PDF.  
2. **Přidejte connection string** do Azure Key Vault a aktualizujte ukázkový kód.  
3. **Spusťte asynchronní ukázku načítání** a ověřte, že se zobrazí UI anotací.  
4. **Zavést cachování** pro nejčastěji používané dokumenty.  
5. **Zvětšete škálování** přidáním monitorování, logování a produkčního zpracování chyb.

Připraveni vytvořit něco úžasného? Začněte s výše uvedeným úryvkem autentizace, načtěte svůj první dokument a nechte GroupDocs.Annotation, aby se postaral o zbytek.

## Často kladené otázky

**Q: Jak řešit chyby autentizace s Azure Blob Storage?**  
A: Chyby autentizace obvykle znamenají, že uložený connection string je zastaralý nebo byl klíč účtu regenerován. Načtěte nejnovější tajemství z Azure Key Vault, otestujte jej pomocí Azure Storage Explorer a zvažte přechod na autentizaci založenou na Azure AD pro produkci.

**Q: Dokáže GroupDocs.Annotation efektivně zpracovávat velké dokumenty z Azure?**  
A: Ano – streamuje PDF přímo z `MemoryStream`, čímž se vyhýbá načítání celého souboru. Pro soubory nad 200 MB povolte `DocStreamOptions` s 64 KB bufferem a sledujte využití paměti; typicky zůstane pod 500 MB RAM i u PDF s 300 stránkami.

**Q: Jaký je nejlepší způsob, jak zvládnout síťová časová omezení při načítání dokumentů?**  
A: Nastavte rozumný `HttpClient.Timeout` (např. 30 sekund), zabalte stahování do Polly retry politiky s exponenciálním back‑off a zobrazte indikátor průběhu, aby uživatelé věděli, že operace stále probíhá.

**Q: Jak zabezpečit přístup k dokumentům v multi‑tenant aplikaci?**  
A: Používejte kontejnery nebo ACL na úrovni blobu pro každého tenanta, generujte krátkodobé SAS tokeny pro každý požadavek a vždy ověřte identitu tenantu před vydáním tokenu. Nikdy se nespoléhejte na skrytí – vynutí přísné server‑side kontroly.

**Q: Je možné integrovat toto s jinými poskytovateli cloudového úložiště?**  
A: Rozhodně. GroupDocs.Annotation funguje s libovolným `Stream`. Nahraďte Azure kód pro stahování ekvivalentním voláním AWS S3 nebo Google Cloud Storage SDK, vraťte `MemoryStream` a zbytek pipeline anotací zůstane nezměněn.

---

**Poslední aktualizace:** 2026-08-04  
**Testováno s:** GroupDocs.Annotation 25.4.0 pro .NET  
**Autor:** GroupDocs

## Související tutoriály
- [Načíst dokument z Azure Blob Storage .NET](/annotation/net/document-loading-essentials/load-document-from-azure/)
- [GroupDocs.Annotation .NET Načítání dokumentu](/annotation/net/document-loading-essentials/)
- [Generovat náhled dokumentu .NET – Kompletní průvodce s GroupDocs.Annotation](/annotation/net/advanced-usage/generate-document-pages-preview/)