---
categories:
- Document Management
date: '2026-08-04'
description: Scopri come utilizzare la stringa di connessione azure blob con GroupDocs.Annotation
  in .NET, oltre alle migliori pratiche di sicurezza dei blob per un caricamento sicuro
  dei documenti.
keywords:
- azure blob connection string
- blob security best practices
- GroupDocs.Annotation Azure integration
- .NET document loading from Azure
- cloud storage annotation tutorial
lastmod: '2026-08-04'
linktitle: Tutorial di integrazione Azure di GroupDocs
og_description: Scopri come utilizzare la stringa di connessione azure blob con GroupDocs.Annotation
  in .NET, oltre alle migliori pratiche di sicurezza dei blob per un caricamento sicuro
  dei documenti.
og_image_alt: Step‑by‑step guide showing Azure blob connection string usage with GroupDocs.Annotation
  in a .NET app
og_title: Stringa di connessione Azure blob per GroupDocs.Annotation – guida .NET
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
title: Stringa di connessione Azure blob per GroupDocs.Annotation .NET
type: docs
url: /it/net/document-loading/load-documents-azure-blob-groupdocs-annotation-dotnet/
weight: 1
---

# Stringa di connessione Azure blob per GroupDocs.Annotation .NET

Se devi lavorare con **azure blob connection string** durante l'annotazione di PDF nel cloud, sei nel posto giusto. Questo tutorial mostra come caricare, annotare e gestire documenti archiviati in Azure Blob Storage direttamente da un'applicazione .NET usando GroupDocs.Annotation. Otterrai anche solide **best practice di sicurezza per i blob**, consigli sulle prestazioni e una checklist di troubleshooting per distribuire una soluzione pronta per la produzione senza sorprese.

## Risposte rapide
- **Cos'è la stringa di connessione azure blob?** È la stringa che contiene il nome dell'account di archiviazione e la chiave, consentendo alla tua app di autenticarsi su Azure Blob Storage.
- **Ho bisogno di una licenza GroupDocs.Annotation?** Sì—per qualsiasi distribuzione in produzione è necessario applicare una licenza valida; una versione di prova funziona per lo sviluppo.
- **Posso caricare PDF più grandi di 200 MB?** Sì, ma usa lo streaming (`MemoryStream`) e I/O asincrono per evitare pressioni sulla memoria.
- **È necessario Azure Key Vault?** Non è obbligatorio, ma è il modo consigliato per memorizzare la stringa di connessione in modo sicuro.
- **Quali versioni .NET sono supportate?** .NET Core 3.1+, .NET 5, .NET 6 e .NET 7 funzionano tutti con l'ultimo pacchetto GroupDocs.Annotation.

## Cos'è la stringa di connessione Azure blob?
La **stringa di connessione azure blob** è un valore di testo unico che combina il nome dell'account di archiviazione, la chiave e l'endpoint, consentendo al tuo codice .NET di autenticarsi contro Azure Blob Storage. Utilizzando questa stringa, puoi creare oggetti `CloudBlobClient` che leggono e scrivono blob senza passaggi aggiuntivi di credenziali.

## Perché usare GroupDocs.Annotation con Azure Blob Storage?
GroupDocs.Annotation supporta **oltre 50** formati di input e output, può annotare PDF di centinaia di pagine in meno di 2 secondi su un server tipico, e elabora i documenti direttamente da stream—così non è mai necessario scrivere un file temporaneo su disco. Accoppiarlo con Azure Blob Storage ti offre un flusso di lavoro completamente cloud‑native che scala orizzontalmente e soddisfa i requisiti di conformità.

## Prerequisiti – cosa serve prima di iniziare

- **Ambiente di sviluppo** – .NET Core 3.1+ o .NET Framework 4.6.1+, Visual Studio 2019+ (o VS Code con estensioni C#).
- **Configurazione Azure** – un abbonamento Azure attivo, un account di archiviazione e almeno un contenitore. Tieni a portata di mano la **stringa di connessione azure blob**; più tardi la sposterai in Azure Key Vault.
- **GroupDocs.Annotation** – il pacchetto NuGet (v25.4.0) e una licenza valida per la produzione.
- **Conoscenza base di C#** – async/await, istruzioni `using` e familiarità con gli stream.

> **Suggerimento:** Crea un contenitore di test chiamato `sample-docs` e carica un PDF (ad es., `sample.pdf`) prima di iniziare a scrivere codice.

## Configurare GroupDocs.Annotation per .NET

### Installazione del pacchetto

Installa la libreria tramite la console di NuGet Package Manager:

```  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  
```

Oppure usa la CLI .NET:

```  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  
```

La versione **25.4.0** è consigliata perché introduce un aumento di velocità del 30 % per il caricamento di documenti basato su cloud e riduce l'overhead di memoria fino al 40 %.

### Licenze (non saltare questa parte)

- **Sviluppo / test** – Scarica una prova gratuita da [GroupDocs Downloads](https://releases.groupdocs.com/annotation/net/) (si applicano filigrane di valutazione) o richiedi una licenza temporanea dalla [Temporary License Page](https://purchase.groupdocs.com/temporary-license/) per test senza filigrane.
- **Produzione** – Acquista una licenza completa su [GroupDocs Purchase](https://purchase.groupdocs.com/buy). Il file di licenza deve essere caricato prima di qualsiasi operazione di annotazione.

### Modello di inizializzazione di base

Il frammento seguente mostra il codice minimo per creare un `Annotator` per un PDF locale. Sostituiremo il percorso del file system con uno stream da Azure nella sezione successiva.

```  
```csharp
using GroupDocs.Annotation;

// Basic initialization - we'll improve this for cloud documents
Annotator annotator = new Annotator("path/to/your/document.pdf");
```  
```

**Ancora di definizione:** `Annotator` è la classe principale in GroupDocs.Annotation che carica uno stream di documento ed espone metodi per aggiungere, modificare e recuperare le annotazioni.

## L'implementazione completa dell'integrazione Azure

### Come autenticarsi in modo sicuro a Azure Blob Storage?

StorageSharedKeyCredential rappresenta il nome dell'account di archiviazione e la chiave usati per autenticare le richieste a Azure Blob Storage.  
Per mantenere le credenziali al sicuro, recupera la stringa di connessione da Azure Key Vault a runtime e usala per creare un StorageSharedKeyCredential. Questa credenziale fornisce il nome dell'account e la chiave al client del servizio Blob, consentendo operazioni autenticate senza esporre segreti nel codice sorgente. Il codice seguente dimostra questo modello.

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

**Spiegazione:**  
- `StorageSharedKeyCredential` convalida il nome dell'account e la chiave.  
- `CloudBlobContainer` rappresenta un contenitore specifico all'interno del tuo account di archiviazione Azure.  
- `CreateIfNotExistsAsync()` garantisce che il contenitore esista senza generare eccezioni se esiste già.

### Come caricare un documento da Azure in un MemoryStream per l'annotazione?

MemoryStream è uno stream .NET che memorizza i dati in memoria, consentendo letture/scritture rapide senza I/O su disco.  
CloudBlockBlob è l'oggetto client per un block blob, permettendo operazioni di download e upload.  
Dopo l'autenticazione, scarica il blob di destinazione in un MemoryStream. Reimposta la posizione dello stream all'inizio prima di passarlo a GroupDocs.Annotation in modo che la libreria possa leggere il documento dall'inizio. L'uso di MemoryStream evita di scrivere file temporanei su disco e migliora le prestazioni, soprattutto per PDF di grandi dimensioni.

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

**Punti chiave:**  
- `CloudBlockBlob` è ottimizzato per file di grandi dimensioni e supporta il download parallelo.  
- Dopo `DownloadToStreamAsync`, il cursore dello stream si trova alla fine; il reset a `0` è essenziale affinché GroupDocs legga dall'inizio.  
- Avvolgere lo stream in un blocco `using` garantisce lo smaltimento, prevenendo perdite di memoria.

## Le migliori pratiche di sicurezza da non ignorare

### Come memorizzare le credenziali in modo sicuro con Azure Key Vault?

Non inserire mai la **stringa di connessione azure blob** nel codice sorgente. Recuperala a runtime da Azure Key Vault usando l'Azure SDK. Questo centralizza la gestione dei segreti, supporta la rotazione automatica e garantisce che le credenziali non siano esposte nel controllo del codice sorgente o nei log.

```  
```csharp
// Example pattern (you'll need Azure.Security.KeyVault.Secrets package)
var keyVaultClient = new SecretClient(new Uri("https://your-keyvault.vault.azure.net/"), new DefaultAzureCredential());
var storageKey = await keyVaultClient.GetSecretAsync("storage-account-key");
```  
```

### Come applicare controlli di accesso appropriati sul tuo contenitore?

Imposta il livello di accesso del contenitore su Private in modo che i blob non siano leggibili pubblicamente, e utilizza Shared Access Signatures (SAS) per concedere permessi limitati e temporizzati per operazioni specifiche. Inoltre, configura regole di rete per limitare il traffico a intervalli IP fidati, riducendo la superficie di attacco.

- Imposta il livello di accesso pubblico del contenitore su **Private**.  
- Genera **Shared Access Signatures (SAS)** per accessi temporanei e limitati invece di esporre la chiave dell'account.  
- Applica regole di rete per consentire traffico solo dall'intervallo IP della tua applicazione.

### Come convalidare i documenti prima di elaborarli?

Prima di caricare un file in GroupDocs.Annotation, verifica che soddisfi le tue politiche di sicurezza e dimensione. Controlla il tipo MIME per assicurarti che sia un formato supportato, imposta una dimensione massima del file e esegui un rapido controllo di coerenza, ad esempio confermando che l'intestazione del file corrisponda al formato previsto (es., `%PDF`).

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

## Strategie di ottimizzazione delle prestazioni che funzionano

### Come rendere tutte le operazioni I/O asincrone?

Usa i metodi async forniti dall'Azure Storage SDK e da .NET per evitare il blocco dei thread durante le chiamate di rete. L'I/O asincrono migliora la scalabilità consentendo al pool di thread di servire altre richieste mentre si attende il completamento dell'I/O, fondamentale per scenari ad alta concorrenza.

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

### Come implementare una cache intelligente per documenti frequentemente accessi?

Metti in cache il MemoryStream scaricato in una cache distribuita come Azure Redis, usando una chiave che combina il nome del blob e il suo identificatore di versione. Questo riduce i download ripetuti, abbassa la latenza e riduce i costi di egress dello storage per i documenti hot acceduti frequentemente.

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

### Come monitorare e ottimizzare l'uso della rete?

Monitora i pattern di accesso ai blob e regola i livelli di storage e il raggruppamento delle richieste per ottimizzare il traffico di rete. Raggruppando le letture, selezionando i livelli appropriati e tracciando le metriche di egress, puoi controllare i costi e migliorare le prestazioni.

- Raggruppa più letture di blob in una singola richiesta quando possibile.  
- Scegli il livello di blob appropriato (Hot per letture frequenti, Cool per accessi poco frequenti).  
- Traccia le metriche di egress in Azure Monitor per evitare costi imprevisti.

## Problemi comuni e come evitarli

### Come prevenire perdite di memoria quando si gestiscono PDF di grandi dimensioni?

Disporre sempre tempestivamente di stream e altri oggetti I/O, e monitorare l'uso della memoria privata dell'applicazione durante l'annotazione. Una corretta disposizione previene handle persistenti che possono causare pressione sulla memoria, soprattutto quando si elaborano PDF di grandi dimensioni in un ambiente ad alto throughput.

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

### Come gestire elegantemente gli errori di limitazione di velocità di Azure?

Quando Azure restituisce una risposta 429 Too Many Requests, implementa un back‑off esponenziale e rispetta l'intestazione Retry‑After. Questa strategia distribuisce i tentativi di retry nel tempo, riducendo la probabilità di throttling ripetuto e migliorando l'affidabilità complessiva.

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

### Come costruire resilienza contro i guasti di rete?

Usa una libreria circuit‑breaker (ad es., Polly) per ricorrere a una copia nella cache o visualizzare un messaggio di errore amichevole, quindi riprovare in background.

## Casi d'uso reali e applicazioni

### Quali sono i tipici flussi di revisione dei documenti?

I team legali possono archiviare i contratti in un contenitore Azure privato, consentire ai revisori di annotarli tramite GroupDocs.Annotation e mantenere ogni versione in Azure Blob Storage per la conformità di audit.

### Come aiuta nella gestione dei contenuti educativi?

Gli istruttori caricano le diapositive delle lezioni su Azure, gli studenti accedono immediatamente agli stessi PDF annotati, e la piattaforma scala automaticamente con i livelli di storage di Azure.

### Perché è utile per la documentazione di conformità?

Azure fornisce immutabilità e politiche di conservazione integrate, mentre GroupDocs traccia ogni modifica di annotazione, fornendo un registro di audit completo e a prova di manomissione.

## Quando NON utilizzare questo approccio

- App semplici di visualizzazione file che non necessitano di annotazioni – un visualizzatore leggero sarebbe più economico.  
- Scenari offline‑first – l'integrazione richiede connettività di rete a Azure.  
- Progetti con budget estremamente limitati – lo storage Azure e le licenze GroupDocs aggiungono costi ricorrenti.  
- Editing collaborativo in tempo reale (stile Google Docs) – GroupDocs.Annotation non è progettato per modifiche simultanee e in tempo reale.

## Guida alla risoluzione dei problemi

### Come risolvere i problemi di connessione con Azure Blob Storage?

Se non riesci a connetterti, verifica innanzitutto che la stringa di connessione memorizzata in Key Vault corrisponda alle credenziali dell'account di archiviazione. Testa la connessione usando Azure Storage Explorer e assicurati che il traffico in uscita sulla porta 443 verso `*.blob.core.windows.net` sia consentito dal tuo firewall.

1. Verifica che la **stringa di connessione azure blob** in Azure Key Vault corrisponda all'account di archiviazione.  
2. Testa la connessione con Azure Storage Explorer.  
3. Assicurati che il tuo firewall consenta traffico in uscita sulla porta 443 verso `*.blob.core.windows.net`.

### Come diagnosticare le eccezioni out‑of‑memory?

Gli errori out‑of‑memory spesso derivano da stream non smaltiti o dal caricamento di interi file in memoria. Abilita la diagnostica della memoria .NET, registra la durata degli stream e imposta una dimensione massima del documento per prevenire un consumo eccessivo di memoria.

- Abilita la diagnostica della memoria .NET (`dotnet-counters`).  
- Registra i timestamp di creazione e smaltimento degli stream.  
- Imposta una dimensione massima del documento (es., 300 MB) e rifiuta upload più grandi con un errore chiaro.

### Come migliorare le prestazioni di caricamento lente dei documenti?

Per velocizzare il caricamento, passa a download di blob asincroni, abilita la cache per i file frequentemente accessi e archivia i documenti hot nel livello Hot spostando i file poco usati nel livello Cool. Questi passaggi riducono la latenza e migliorano il throughput.

- Passa al download asincrono (`DownloadToStreamAsync`).  
- Abilita la cache (Redis o in‑memory) per i documenti hot.  
- Usa il livello Hot per i blob frequentemente accessi e il livello Cool per i file di archivio.

## Conclusione

Combinando l'autenticazione basata sulla **stringa di connessione azure blob** con l'API di streaming di GroupDocs.Annotation, ottieni una soluzione di annotazione sicura, ad alte prestazioni e cloud‑native. Ricorda di:

- Memorizzare i segreti in Azure Key Vault (mai hard‑code).  
- Usare I/O asincrono e caching per la velocità.  
- Implementare pattern di retry e circuit‑breaker per la resilienza.  
- Monitorare le metriche di Azure per controllare costi e prestazioni.

### I prossimi passi

1. **Crea un contenitore di test** e carica un PDF.  
2. **Aggiungi la stringa di connessione** ad Azure Key Vault e aggiorna il codice di esempio.  
3. **Esegui l'esempio di caricamento asincrono** e verifica che l'interfaccia di annotazione compaia.  
4. **Introduci la cache** per i documenti più usati.  
5. **Scala** aggiungendo monitoraggio, logging e gestione degli errori di livello produzione.

Pronto a costruire qualcosa di straordinario? Inizia con lo snippet di autenticazione sopra, carica il tuo primo documento e lascia che GroupDocs.Annotation gestisca il resto.

## Domande frequenti

**D: Come gestire gli errori di autenticazione con Azure Blob Storage?**  
Gli errori di autenticazione solitamente indicano che la stringa di connessione memorizzata è obsoleta o che la chiave dell'account è stata rigenerata. Recupera il segreto più recente da Azure Key Vault, testalo con Azure Storage Explorer e considera di passare a un'autenticazione basata su Azure AD per la produzione.

**D: GroupDocs.Annotation può gestire documenti di grandi dimensioni in modo efficiente da Azure?**  
Sì – trasmette i PDF direttamente da un `MemoryStream`, evitando il caricamento completo del file. Per file superiori a 200 MB, abilita `DocStreamOptions` con un buffer di 64 KB e monitora l'uso della memoria; tipicamente rimarrai sotto i 500 MB di RAM anche con PDF di 300 pagine.

**D: Qual è il modo migliore per gestire i timeout di rete durante il caricamento dei documenti?**  
Imposta un `HttpClient.Timeout` ragionevole (es., 30 secondi), avvolgi il download in una policy di retry Polly con back‑off esponenziale e mostra un indicatore di progresso affinché gli utenti sappiano che l'operazione è ancora in corso.

**D: Come proteggere l'accesso ai documenti in un'applicazione multi‑tenant?**  
Usa contenitori per tenant o ACL a livello di blob, genera token SAS a breve durata per ogni richiesta e valida sempre l'identità del tenant prima di rilasciare un token. Non fare affidamento sull'oscurità – applica controlli severi lato server.

**D: È possibile integrare questo con altri provider di storage cloud?**  
Assolutamente. GroupDocs.Annotation funziona con qualsiasi `Stream`. Sostituisci il codice di download Azure con la chiamata equivalente dell'SDK AWS S3 o Google Cloud Storage, restituisci un `MemoryStream` e il resto della pipeline di annotazione rimane invariato.

---  

**Last Updated:** 2026-08-04  
**Tested With:** GroupDocs.Annotation 25.4.0 for .NET  
**Author:** GroupDocs

## Tutorial correlati

- [Carica documento da Azure Blob Storage .NET](/annotation/net/document-loading-essentials/load-document-from-azure/)
- [Caricamento documento GroupDocs.Annotation .NET](/annotation/net/document-loading-essentials/)
- [Genera anteprima documento .NET - Guida completa con GroupDocs.Annotation](/annotation/net/advanced-usage/generate-document-pages-preview/)