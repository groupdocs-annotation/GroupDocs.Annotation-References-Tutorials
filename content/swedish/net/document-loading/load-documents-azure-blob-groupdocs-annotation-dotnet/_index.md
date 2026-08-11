---
categories:
- Document Management
date: '2026-08-04'
description: Lär dig hur du använder Azure blob-anslutningssträngen med GroupDocs.Annotation
  i .NET, samt bästa praxis för blob-säkerhet för säker dokumentladdning.
keywords:
- azure blob connection string
- blob security best practices
- GroupDocs.Annotation Azure integration
- .NET document loading from Azure
- cloud storage annotation tutorial
lastmod: '2026-08-04'
linktitle: GroupDocs Azure-integrationshandledning
og_description: Lär dig hur du använder Azure blob-anslutningssträngen med GroupDocs.Annotation
  i .NET, samt bästa praxis för blob-säkerhet för säker dokumentladdning.
og_image_alt: Step‑by‑step guide showing Azure blob connection string usage with GroupDocs.Annotation
  in a .NET app
og_title: Azure blob-anslutningssträng för GroupDocs.Annotation – .NET-guide
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
title: Azure blob-anslutningssträng för GroupDocs.Annotation .NET
type: docs
url: /sv/net/document-loading/load-documents-azure-blob-groupdocs-annotation-dotnet/
weight: 1
---

# Azure blob connection string för GroupDocs.Annotation .NET

Om du behöver arbeta med **azure blob connection string** när du annoterar PDF-filer i molnet, har du kommit till rätt ställe. Denna handledning visar hur du laddar, annoterar och hanterar dokument lagrade i Azure Blob Storage direkt från en .NET-applikation med GroupDocs.Annotation. Du får också gedigna **blob security best practices**, prestandatips och en felsökningschecklista så att du kan leverera en produktionsklar lösning utan överraskningar.

## Snabba svar
- **Vad är azure blob connection string?** Det är strängen som innehåller ditt lagringskontos namn och nyckel, vilket låter din app autentisera mot Azure Blob Storage.
- **Behöver jag en GroupDocs.Annotation-licens?** Ja—för alla produktionsdistributioner måste du tillämpa en giltig licens; en provversion fungerar för utveckling.
- **Kan jag ladda PDF-filer större än 200 MB?** Ja, men använd streaming (`MemoryStream`) och async I/O för att undvika minnespress.
- **Krävs Azure Key Vault?** Inte obligatoriskt, men det är det rekommenderade sättet att lagra anslutningssträngen säkert.
- **Vilka .NET-versioner stöds?** .NET Core 3.1+, .NET 5, .NET 6 och .NET 7 fungerar alla med det senaste GroupDocs.Annotation-paketet.

## Vad är Azure blob connection string?
**azure blob connection string** är ett enda textvärde som kombinerar lagringskontots namn, nyckel och slutpunkt, vilket låter din .NET-kod autentisera mot Azure Blob Storage. Med den här strängen kan du skapa `CloudBlobClient`-objekt som läser och skriver blobbar utan ytterligare autentiseringssteg.

## Varför använda GroupDocs.Annotation med Azure Blob Storage?
GroupDocs.Annotation stöder **50+** in- och utdataformat, kan annotera flersidiga PDF-filer på under 2 sekunder på en vanlig server, och bearbetar dokument direkt från strömmar—så du aldrig behöver skriva en temporär fil till disk. Att kombinera det med Azure Blob Storage ger dig ett helt molnbaserat arbetsflöde som skalar horisontellt och uppfyller efterlevnadskrav.

## Förutsättningar – vad du behöver innan du börjar

- **Development environment** – .NET Core 3.1+ eller .NET Framework 4.6.1+, Visual Studio 2019+ (eller VS Code med C#-tillägg).
- **Azure setup** – ett aktivt Azure-abonnemang, ett lagringskonto och minst en container. Ha **azure blob connection string** till hands; du kommer senare att flytta den till Azure Key Vault.
- **GroupDocs.Annotation** – NuGet-paketet (v25.4.0) och en giltig licens för produktion.
- **Basic C# knowledge** – async/await, `using`-satser och bekantskap med strömmar.

> **Pro tip:** Skapa en testcontainer med namnet `sample-docs` och ladda upp en PDF (t.ex. `sample.pdf`) innan du börjar koda.

## Konfigurera GroupDocs.Annotation för .NET

### Paketinstallation

Installera biblioteket via NuGet Package Manager Console:

```  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  
```

Eller använd .NET CLI:

```  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  
```

Version **25.4.0** rekommenderas eftersom den ger en 30 % hastighetsökning för molnbaserad dokumentladdning och minskar minnesanvändningen med upp till 40 %.

### Licensiering (hoppa inte över detta avsnitt)

- **Development / testing** – Ladda ner en gratis provversion från [GroupDocs Nedladdningar](https://releases.groupdocs.com/annotation/net/) (utvärderingsvattenstämplar gäller) eller begär en tillfällig licens från [Tillfällig licenssida](https://purchase.groupdocs.com/temporary-license/) för testning utan vattenstämplar.
- **Production** – Köp en full licens på [GroupDocs Köp](https://purchase.groupdocs.com/buy). Licensfilen måste laddas innan någon annoteringsoperation.

### Grundläggande initieringsmönster

Följande kodsnutt visar minimal kod för att skapa en `Annotator` för en lokal PDF. Vi kommer att ersätta filsystemssökvägen med en ström från Azure i nästa avsnitt.

```  
```csharp
using GroupDocs.Annotation;

// Basic initialization - we'll improve this for cloud documents
Annotator annotator = new Annotator("path/to/your/document.pdf");
```  
```

**Definition anchor:** `Annotator` är huvudklassen i GroupDocs.Annotation som laddar ett dokumentflöde och exponerar metoder för att lägga till, redigera och hämta annotationer.

## Den kompletta Azure-integrationsimplementationen

### Hur autentiserar du mot Azure Blob Storage på ett säkert sätt?

StorageSharedKeyCredential representerar lagringskontots namn och nyckel som används för att autentisera förfrågningar till Azure Blob Storage.  
För att hålla dina autentiseringsuppgifter säkra, hämta anslutningssträngen från Azure Key Vault vid körning och använd den för att skapa en StorageSharedKeyCredential. Denna autentiseringsuppgift levererar kontonamnet och nyckeln till Blob-tjänsteklienten, vilket möjliggör autentiserade operationer utan att avslöja hemligheter i källkoden. Följande kod demonstrerar detta mönster.

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

**Förklaring:**  
- `StorageSharedKeyCredential` validerar kontonamnet och nyckeln.  
- `CloudBlobContainer` representerar en specifik container i ditt Azure-lagringskonto.  
- `CreateIfNotExistsAsync()` säkerställer att containern finns utan att kasta ett undantag om den redan finns.

### Hur laddar du ett dokument från Azure till ett MemoryStream för annotering?

MemoryStream är en .NET-ström som lagrar data i minnet, vilket möjliggör snabb läsning/skrivning utan disk‑I/O.  
CloudBlockBlob är klientobjektet för en blockblob, vilket möjliggör nedladdnings- och uppladdningsoperationer.  
Efter autentisering, ladda ner målblobben till ett MemoryStream. Återställ strömmens position till början innan du skickar den till GroupDocs.Annotation så att biblioteket kan läsa dokumentet från start. Att använda ett MemoryStream undviker att skriva temporära filer till disk och förbättrar prestanda, särskilt för stora PDF-filer.

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

**Viktiga punkter:**  
- `CloudBlockBlob` är optimerad för stora filer och stödjer parallell nedladdning.  
- Efter `DownloadToStreamAsync` sitter strömmens markör i slutet; återställning till `0` är avgörande så att GroupDocs läser från början.  
- Att omsluta strömmen i ett `using`-block garanterar att den frigörs, vilket förhindrar minnesläckor.

## Security best practices du inte kan ignorera

### Hur lagrar du autentiseringsuppgifter säkert med Azure Key Vault?

Bädda aldrig in **azure blob connection string** i källkoden. Hämta den vid körning från Azure Key Vault med Azure SDK. Detta centraliserar hantering av hemligheter, stödjer automatisk rotation och säkerställer att autentiseringsuppgifter inte exponeras i källkontroll eller loggar.

```  
```csharp
// Example pattern (you'll need Azure.Security.KeyVault.Secrets package)
var keyVaultClient = new SecretClient(new Uri("https://your-keyvault.vault.azure.net/"), new DefaultAzureCredential());
var storageKey = await keyVaultClient.GetSecretAsync("storage-account-key");
```  
```

### Hur upprätthåller du korrekta åtkomstkontroller på din container?

Ställ in containerns åtkomstnivå till Private så att blobbar inte är offentligt läsbara, och använd Shared Access Signatures (SAS) för att bevilja begränsade, tidsbundna behörigheter för specifika operationer. Dessutom, konfigurera nätverksregler för att begränsa trafik till betrodda IP‑intervall, vilket minskar attackytan.

- Ställ in containerns offentliga åtkomstnivå till **Private**.  
- Generera **Shared Access Signatures (SAS)** för temporär, avgränsad åtkomst istället för att exponera kontonyckeln.  
- Applicera nätverksregler för att tillåta trafik endast från din applikations IP‑intervall.

### Hur validerar du dokument innan de bearbetas?

Innan du laddar en fil i GroupDocs.Annotation, verifiera att den uppfyller dina säkerhets- och storlekspolicyer. Kontrollera MIME-typen för att säkerställa att den är ett stödformat, verkställ en maximal filstorlek och utför en snabb kontroll, t.ex. bekräfta att filhuvudet matchar det förväntade formatet (t.ex. `%PDF`).

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

## Prestandaoptimeringsstrategier som fungerar

### Hur gör du alla I/O‑operationer asynkrona?

Använd async‑metoder som tillhandahålls av Azure Storage SDK och .NET för att undvika att blockera trådar under nätverksanrop. Asynkron I/O förbättrar skalbarheten genom att låta trådpoolen betjäna andra förfrågningar medan den väntar på I/O‑slutförande, vilket är avgörande för scenarier med hög samtidighet.

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

### Hur implementerar du smart caching för ofta åtkomna dokument?

Cacha den nedladdade MemoryStream i en distribuerad cache som Azure Redis, med en nyckel som kombinerar blob‑namnet och dess versionsidentifierare. Detta minskar upprepade nedladdningar, sänker latens och minskar lagringsutflödeskostnader för heta dokument som ofta nås.

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

### Hur övervakar och optimerar du nätverksanvändning?

Övervaka blob‑åtkomstmönster och justera lagringstiers och begäran‑batchning för att optimera nätverkstrafiken. Genom att gruppera läsningar, välja lämpliga tiers och spåra egress‑metrik kan du kontrollera kostnader och förbättra prestanda.

- Batcha flera blob‑läsningar till en enda begäran när det är möjligt.  
- Välj lämplig blob‑tier (Hot för frekventa läsningar, Cool för sällsynt åtkomst).  
- Spåra egress‑metrik i Azure Monitor för att undvika oväntade kostnader.

## Vanliga fallgropar och hur du undviker dem

### Hur förhindrar du minnesläckor när du hanterar stora PDF-filer?

Disposera alltid strömmar och andra I/O‑objekt omedelbart, och övervaka applikationens privata minnesanvändning under annotering. Korrekt disponering förhindrar kvarvarande handtag som kan orsaka minnespress, särskilt när stora PDF-filer bearbetas i en hög‑genomströmningsmiljö.

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

### Hur hanterar du Azure‑rate‑limit‑fel på ett smidigt sätt?

När Azure returnerar ett 429 Too Many Requests‑svar, implementera exponentiell back‑off och respektera Retry‑After‑headern. Denna strategi sprider omförsök över tid, minskar risken för återkommande throttling och förbättrar den övergripande tillförlitligheten.

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

### Hur bygger du motståndskraft mot nätverksfel?

Använd ett circuit‑breaker‑bibliotek (t.ex. Polly) för att falla tillbaka till en cachad kopia eller visa ett vänligt felmeddelande, och sedan försöka igen i bakgrunden.

## Verkliga användningsfall och tillämpningar

### Vilka är typiska dokument‑granskningsarbetsflöden?

Juridiska team kan lagra kontrakt i en privat Azure‑container, låta granskare annotera dem via GroupDocs.Annotation, och behålla varje version i Azure Blob Storage för regelefterlevnad.

### Hur hjälper detta hantering av utbildningsinnehåll?

Instruktörer laddar upp föreläsningsbilder till Azure, studenter får omedelbart åtkomst till samma annoterade PDF-filer, och plattformen skalar automatiskt med Azures lagringstiers.

### Varför är detta användbart för efterlevnadsdokumentation?

Azure erbjuder inbyggd oföränderlighet och lagringspolicyer, medan GroupDocs spårar varje annoteringsändring, vilket ger dig en komplett, manipulering‑säker revisionsspår.

## När du INTE bör använda detta tillvägagångssätt

- Enkla fil‑visningsappar som inte behöver annotationer – en lättviktig visare skulle vara billigare.  
- Offline‑först‑scenarier – integrationen kräver nätverksanslutning till Azure.  
- Projekt med extremt strama budgetar – Azure‑lagring och GroupDocs‑licensiering tillför återkommande kostnader.  
- Realtids‑samarbetsredigering (Google Docs‑stil) – GroupDocs.Annotation är inte byggt för simultana, live‑redigeringar.

## Felsökningsguide

### Hur löser du anslutningsproblem med Azure Blob Storage?

Om du inte kan ansluta, verifiera först att anslutningssträngen som lagras i Key Vault matchar lagringskontots autentiseringsuppgifter. Testa anslutningen med Azure Storage Explorer, och säkerställ att utgående trafik på port 443 till `*.blob.core.windows.net` tillåts av din brandvägg.

1. Verifiera att **azure blob connection string** i Azure Key Vault matchar lagringskontot.  
2. Testa anslutningen med Azure Storage Explorer.  
3. Säkerställ att din brandvägg tillåter utgående trafik på port 443 till `*.blob.core.windows.net`.

### Hur diagnostiserar du out‑of‑memory‑undantag?

Out‑of‑memory‑fel beror ofta på odisponerade strömmar eller att hela filer laddas in i minnet. Aktivera .NET‑minnesdiagnostik, logga strömmarnas livslängd och verkställ en maximal dokumentstorlek för att förhindra överdriven minnesanvändning.

- Aktivera .NET‑minnesdiagnostik (`dotnet-counters`).  
- Logga tidpunkter för strömmens skapande och disponering.  
- Påtvinga en maximal dokumentstorlek (t.ex. 300 MB) och avvisa större uppladdningar med ett tydligt felmeddelande.

### Hur förbättrar du långsam dokument‑laddningsprestanda?

För att snabba upp laddning, byt till asynkrona blob‑nedladdningar, aktivera caching för ofta åtkomna filer, och lagra heta dokument i Hot‑tier medan du flyttar sällan använda filer till Cool‑tier. Dessa steg minskar latens och förbättrar genomströmning.

- Byt till async‑nedladdning (`DownloadToStreamAsync`).  
- Aktivera caching (Redis eller i‑minnet) för heta dokument.  
- Använd Hot‑tier för frekvent åtkomna blobbar och Cool‑tier för arkiveringsfiler.

## Slutsats

Genom att kombinera **azure blob connection string**‑baserad autentisering med GroupDocs.Annotation:s streaming‑API får du en säker, högpresterande, molnbaserad annoteringslösning. Kom ihåg att:

- Lagra hemligheter i Azure Key Vault (aldrig hårdkoda).  
- Använd async I/O och caching för hastighet.  
- Implementera retry‑ och circuit‑breaker‑mönster för motståndskraft.  
- Övervaka Azure‑metrik för att kontrollera kostnad och prestanda.

### Dina nästa steg

1. **Skapa en testcontainer** och ladda upp en PDF.  
2. **Lägg till anslutningssträngen** i Azure Key Vault och uppdatera exempel‑koden.  
3. **Kör det asynkrona laddningsexemplet** och verifiera att annoterings‑UI visas.  
4. **Inför caching** för dina mest använda dokument.  
5. **Skala upp** genom att lägga till övervakning, loggning och felhantering i produktionsklass.

Redo att bygga något fantastiskt? Börja med autentiserings‑snutten ovan, ladda ditt första dokument, och låt GroupDocs.Annotation sköta resten.

## Vanliga frågor

**Q: Hur hanterar jag autentiseringsfel med Azure Blob Storage?**  
A: Autentiseringsfel betyder vanligtvis att den lagrade anslutningssträngen är föråldrad eller att kontonyckeln har regenererats. Hämta den senaste hemligheten från Azure Key Vault, testa den med Azure Storage Explorer, och överväg att byta till Azure AD‑baserad autentisering för produktion.

**Q: Kan GroupDocs.Annotation hantera stora dokument effektivt från Azure?**  
A: Ja – den strömmar PDF-filer direkt från ett `MemoryStream`, vilket undviker fullständig filinläsning. För filer över 200 MB, aktivera `DocStreamOptions` med en 64 KB‑buffer och övervaka minnesanvändning; du kommer vanligtvis att hålla dig under 500 MB RAM även med 300‑sidiga PDF-filer.

**Q: Vad är det bästa sättet att hantera nätverkstidsgränser när du laddar dokument?**  
A: Ställ in en rimlig `HttpClient.Timeout` (t.ex. 30 sekunder), omslut nedladdningen i en Polly‑retry‑policy med exponentiell back‑off, och visa en förloppsindikator så att användarna vet att operationen fortfarande pågår.

**Q: Hur säkrar jag dokumentåtkomst i en multi‑tenant‑applikation?**  
A: Använd per‑tenant‑containrar eller blob‑nivå‑ACL:er, generera kortlivade SAS‑token för varje begäran, och validera alltid hyresgästens identitet innan du utfärdar en token. Lita aldrig på fördoldhet – verkställ strikta server‑sidiga kontroller.

**Q: Är det möjligt att integrera detta med andra molnlagringstjänster?**  
A: Absolut. GroupDocs.Annotation fungerar med vilken `Stream` som helst. Ersätt Azure‑nedladdningskoden med motsvarande AWS S3‑ eller Google Cloud Storage‑SDK‑anrop, returnera ett `MemoryStream`, och resten av annoterings‑pipeline förblir oförändrad.

---  

**Senast uppdaterad:** 2026-08-04  
**Testat med:** GroupDocs.Annotation 25.4.0 for .NET  
**Författare:** GroupDocs

## Relaterade handledningar

- [Ladda dokument från Azure Blob Storage .NET](/annotation/net/document-loading-essentials/load-document-from-azure/)
- [GroupDocs.Annotation .NET Dokumentladdning](/annotation/net/document-loading-essentials/)
- [Generera dokumentförhandsgranskning .NET - Komplett guide med GroupDocs.Annotation](/annotation/net/advanced-usage/generate-document-pages-preview/)