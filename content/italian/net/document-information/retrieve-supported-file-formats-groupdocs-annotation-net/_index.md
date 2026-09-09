---
categories:
- .NET Development
date: '2026-06-26'
description: Scopri come recuperare i formati con GroupDocs.Annotation per .NET, risolvere
  i problemi di formati di file non supportati e applicare la validazione best‑practice.
keywords:
- how to retrieve formats
- troubleshoot unsupported file format
- GroupDocs.Annotation .NET
lastmod: '2026-06-26'
linktitle: Recupera i formati di file supportati .NET
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  headline: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete
    Guide
  type: TechArticle
- description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  name: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete Guide
  steps:
  - name: Verify installation
    text: Run `dotnet list package` or check the NuGet console output for any warnings.
  - name: Check license status
    text: Ensure `License.SetLicense("path/to/license.json")` executes before any
      API call.
  - name: Diagnose environment constraints
    text: '- Confirm .NET runtime version matches the library’s requirements. - Verify
      the process has read/write permissions for the temporary folder used by GroupDocs.Annotation.'
  type: HowTo
- questions:
  - answer: The library supports **over 50 formats**, including PDF, DOCX, XLSX, PPTX,
      JPEG, PNG, TIFF, and many others. Run the sample code to retrieve the exact
      list for your license.
    question: What file formats does GroupDocs.Annotation actually support?
  - answer: This usually points to a licensing issue—either an expired trial or an
      incorrectly loaded license file. Re‑apply a valid license and restart the app.
    question: Why am I getting fewer supported formats than expected?
  - answer: No direct “IsSupported” method exists; the recommended approach is to
      cache the full list once and query it locally for fast lookups.
    question: Can I check a single format without pulling the whole list?
  - answer: Initialise the format cache at application startup (e.g., in `ConfigureServices`)
      and store it in a static or singleton service. This eliminates per‑request overhead.
    question: How should I handle format checking in a high‑traffic web app?
  - answer: Exceptions typically stem from licensing or corrupted installations. Verify
      the package integrity, re‑install if needed, and ensure the license file is
      accessible.
    question: What if GetSupportedFileTypes() throws an exception?
  type: FAQPage
tags:
- GroupDocs.Annotation
- file-formats
- document-processing
- dotnet-tutorial
title: Come recuperare i formati in .NET usando GroupDocs.Annotation – Guida completa
type: docs
url: /it/net/document-information/retrieve-supported-file-formats-groupdocs-annotation-net/
weight: 1
---

# Come recuperare i formati in .NET usando GroupDocs.Annotation

## Introduzione

Ti sei mai chiesto quali formati di file la tua applicazione .NET può effettivamente gestire per l'annotazione dei documenti? **Come recuperare i formati** è una domanda che molti sviluppatori si pongono quando devono convalidare i caricamenti degli utenti o costruire filtri UI dinamici. Conoscere esattamente quali formati di file supporta la tua implementazione di GroupDocs.Annotation non è solo utile—è essenziale per creare applicazioni robuste che non si blocchino a causa di un tipo di file imprevisto.

In questa guida imparerai come recuperare e convalidare programmaticamente i formati di file supportati usando GroupDocs.Annotation per .NET. Vedremo l'implementazione di base, ti mostreremo come trasformare l'elenco grezzo in un menu a discesa pulito per gli utenti finali e tratteremo consigli pratici di troubleshooting così da poter gestire qualsiasi scenario di formato documento con fiducia.

**Cosa otterrai**

- Una comprensione cristallina delle capacità di formati file di GroupDocs.Annotation  
- Codice pronto all'uso che recupera e visualizza tutti i formati supportati  
- Strategie provate per caching, gestione degli errori e casi limite di licenza  
- Raccomandazioni di best practice per la convalida dei tipi di file in produzione  

Immergiamoci e risolviamo questo puzzle dei formati una volta per tutte.

## Risposte rapide
- **Cosa significa “come recuperare i formati”?** È il modo programmatico di chiedere a GroupDocs.Annotation quali estensioni può annotare.  
- **Quali formati principali sono supportati di default?** Oltre 50, inclusi PDF, DOCX, XLSX, PPTX, JPEG, PNG e TIFF.  
- **È necessaria una licenza per ottenere l'elenco completo?** Sì—una licenza commerciale attiva o di prova sblocca l'intero catalogo.  
- **È consigliato cacheare l'elenco dei formati?** Assolutamente; il caching evita chiamate inutili e migliora i tempi di risposta.  
- **Come posso convalidare un caricamento rispetto all'elenco?** Confronta l'estensione del file con la collezione cacheata di estensioni supportate.

## Cos’è “come recuperare i formati”?
**Come recuperare i formati** si riferisce al processo di chiamare l'API di GroupDocs.Annotation per ottenere una collezione di tutti i tipi di file che la libreria può annotare. Questa operazione restituisce un elenco di sola lettura di oggetti `FileType` che includono sia l'estensione del file sia una descrizione amichevole.

## Perché usare GroupDocs.Annotation per il rilevamento dei formati?
GroupDocs.Annotation supporta **oltre 50 formati di input e output**—inclusi PDF, Microsoft Office (Word, Excel, PowerPoint) e i più comuni tipi di immagine—elaborando documenti di centinaia di pagine senza caricare l'intero file in memoria. Questa capacità quantificata lo rende una scelta affidabile per pipeline di annotazione su scala enterprise.

## Prerequisiti e configurazione dell'ambiente

### Cosa ti serve
- **IDE:** Visual Studio 2019 o versioni successive (l'edizione Community va benissimo)  
- **Framework di destinazione:** .NET Framework 4.6.1 + o .NET Core 2.0 +   
- **Nozioni di base C#:** Se sai scrivere un’app “Hello World”, sei pronto  

### Installazione di GroupDocs.Annotation
Il modo più semplice è tramite NuGet. Scegli il metodo che corrisponde al tuo flusso di lavoro:

**Opzione 1: Console di Package Manager**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**Opzione 2: .NET CLI**  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

**Suggerimento professionale:** In ambienti aziendali con restrizioni, scarica il pacchetto manualmente da [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/) e fai riferimento al DLL localmente.

### Licenze semplificate
- **Sviluppo e test:** Inizia con la prova gratuita per funzionalità complete.  
- **Valutazione estesa:** Ottieni una [licenza temporanea](https://purchase.groupdocs.com/temporary-license/) (rilasciata in ~5 minuti).  
- **Produzione:** Acquista una licenza commerciale da [GroupDocs Purchase](https://purchase.groupdocs.com/buy); una licenza copre tutti gli scenari di distribuzione.

## Come recuperare i formati di file supportati programmaticamente?

Carica i formati supportati con una singola chiamata a `FileType.GetSupportedFileTypes()` e poi trasforma il risultato in un elenco user‑friendly che può essere mostrato nei controlli UI o usato per la convalida. Il metodo restituisce una collezione di sola lettura di oggetti `FileType`, ciascuno contenente un'estensione e una descrizione, rendendo semplice il loro utilizzo.

```csharp
var supported = FileType.GetSupportedFileTypes()
                         .OrderBy(f => f.Extension)
                         .Select(f => new { f.Extension, f.Description })
                         .ToList();
```

Il codice sopra interroga i metadati interni di GroupDocs.Annotation, ordina le estensioni alfabeticamente e restituisce una collezione leggera che puoi collegare a controlli UI o usare per la convalida.

### Ancora di definizione: classe FileType
La classe `FileType` è la rappresentazione di GroupDocs.Annotation di un singolo formato documento, esponendo proprietà come `Extension` e `Description`.  

### Walkthrough passo‑passo
1. **Aggiungi lo spazio dei nomi** – `using GroupDocs.Annotation;` in cima al tuo file.  
2. **Chiama il metodo statico** – `FileType.GetSupportedFileTypes()` restituisce un `IEnumerable<FileType>`.  
3. **Ordina e proietta** – Usa `OrderBy` e `Select` di LINQ per modellare i dati per la visualizzazione.  
4. **Renderizza** – Scorri l'elenco in una console, vista MVC o dropdown WinForms.

```csharp
using System;
using System.Linq;
using GroupDocs.Annotation; // This is where the FileType class lives
```  

## Come cacheare l'elenco dei formati per l'uso in produzione?

Il caching elimina ricerche ripetute dei metadati e garantisce tempi di risposta sub‑millisecondo per ogni richiesta, cosa critica in applicazioni ad alto traffico. Memorizzando l'elenco dei formati in un campo statico e caricandolo pigramente al primo utilizzo, assicuri che i dati vengano recuperati una sola volta e poi riutilizzati efficientemente per l'intero ciclo di vita dell'applicazione.

```csharp
public static class FormatCache
{
    private static IReadOnlyList<FileType> _cachedFormats;

    public static IReadOnlyList<FileType> SupportedFormats =>
        _cachedFormats ??= FileType.GetSupportedFileTypes()
                                    .OrderBy(f => f.Extension)
                                    .ToList();
}
```

```csharp
public static void RunGetSupportedFileFormats()
{
    // Retrieve collection of supported file types, ordered by their extension
    IEnumerable<FileType> fileTypes = FileType.GetSupportedFileTypes().OrderBy(fileType => fileType.Extension);

    // Iterate through each FileType object and output its details to the console
    foreach (FileType fileType in fileTypes)
        Console.WriteLine($"{fileType.Extension} - {fileType.Name}");
}
```  

**Perché cacheare?** Il set di formati supportati non cambia a runtime, quindi un unico caricamento all'avvio dell'applicazione salva cicli CPU ed evita potenziali controlli di licenza ad ogni chiamata.

## Problemi comuni e soluzioni

### Problema 1: errore di compilazione “GroupDocs.Annotation not found”
**Risposta diretta:** Verifica che il pacchetto NuGet sia installato correttamente, pulisci e ricostruisci la soluzione, e assicurati che il framework di destinazione corrisponda alle versioni supportate dal pacchetto.  

**Analisi della causa** – Riferimento mancante, framework incompatibile o restrizioni della sorgente dei pacchetti aziendali.

### Problema 2: Elenco dei formati vuoto o incompleto
**Risposta diretta:** Una licenza scaduta o mal configurata spesso tronca l'elenco; riapplica un file di licenza valido e riavvia l'applicazione.  

**Possibili cause:**  
- File di licenza non caricato (`License.SetLicense("license.json")` mancante)  
- Pacchetto NuGet corrotto  
- Dipendenze native mancanti  

**Correzione rapida:**  
```csharp
public static void DiagnoseFormatIssues()
{
    try
    {
        var formats = FileType.GetSupportedFileTypes();
        Console.WriteLine($"Found {formats.Count()} supported formats");
        
        if (formats.Count() < 10) // GroupDocs supports many more formats
        {
            Console.WriteLine("Warning: Fewer formats than expected. Check your license.");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Cannot retrieve formats: {ex.Message}");
        // This usually indicates a licensing or installation issue
    }
}
```  

### Problema 3: Impatti sulle prestazioni da chiamate frequenti
**Risposta diretta:** Cachea il risultato come mostrato nella sezione “Come cacheare”; le chiamate successive diventano O(1).  

**Suggerimento di implementazione:** Memorizza l'elenco in `MemoryCache` o in un campo statico, e rinfrescalo solo quando aggiorni la libreria.

```csharp
public static class FileFormatCache
{
    private static List<FileType> _cachedFormats;
    
    public static IEnumerable<FileType> GetSupportedFormats()
    {
        if (_cachedFormats == null)
        {
            _cachedFormats = FileType.GetSupportedFileTypes().ToList();
        }
        return _cachedFormats;
    }
}
```  

## Applicazioni reali e casi d'uso

### Come convalidare i caricamenti di file usando l'elenco cacheato?
Quando un utente invia un documento, estrai l'estensione del file e confrontala con la collezione cacheata:

```csharp
bool IsSupported(string fileName)
{
    var ext = Path.GetExtension(fileName).ToLowerInvariant();
    return FormatCache.SupportedFormats.Any(f => f.Extension.Equals(ext, StringComparison.OrdinalIgnoreCase));
}
```

```csharp
public bool IsFileSupported(string fileName)
{
    var extension = Path.GetExtension(fileName).ToLowerInvariant();
    var supportedExtensions = GetSupportedExtensions();
    return supportedExtensions.Contains(extension);
}
```  

### Come generare un filtro file dinamico per un OpenFileDialog?
Popola la stringa di filtro del dialogo dalle estensioni cacheate, garantendo che l'interfaccia rifletta sempre le capacità della libreria:

```csharp
var filter = string.Join(";", FormatCache.SupportedFormats.Select(f => $"*{f.Extension}"));
openFileDialog.Filter = $"Supported Files ({filter})|{filter}";
```

```csharp
public string GenerateFileFilter()
{
    var extensions = GetSupportedExtensions();
    var filterParts = extensions.Select(ext => $"*{ext}");
    return $"Supported Documents|{string.Join(";", filterParts)}";
}
```  

### Come saltare i file non supportati in una scansione batch di cartelle?
Itera su una directory, verifica ogni file con `IsSupported` e processa solo quelli validi:

```csharp
foreach (var file in Directory.EnumerateFiles(folderPath))
{
    if (IsSupported(file))
    {
        // Process with GroupDocs.Annotation
    }
}
```

```csharp
public void ProcessDirectory(string directoryPath)
{
    var supportedExtensions = GetSupportedExtensions();
    var files = Directory.GetFiles(directoryPath)
        .Where(file => supportedExtensions.Contains(Path.GetExtension(file).ToLowerInvariant()));
    
    foreach (var file in files)
    {
        // Process each supported file
        ProcessAnnotationFile(file);
    }
}
```  

## Considerazioni sulle prestazioni e best practice

- **Cache una volta, riutilizza ovunque** – Inizializza `FormatCache` all’avvio dell’applicazione (es. in `Program.cs` o `Startup.cs`).  
- **Caricamento pigro** – La proprietà statica garantisce che l'elenco venga caricato solo al primo utilizzo, evitando overhead di avvio non necessari.  
- **Sicurezza thread** – L'operatore di coalescenza null (`??=`) è sicuro per la maggior parte degli scenari monothread; per app ad alta concorrenza, avvolgi la cache in un `Lazy<IReadOnlyList<FileType>>`.  
- **Dispose degli oggetti Annotation** – Sebbene l'elenco dei formati non richieda disposal, qualsiasi istanza di `Annotation` dovrebbe essere avvolta in un blocco `using` per liberare le risorse native.  

### Modello di gestione errori per problemi di licenza
Avvolgi il recupero dei formati in un blocco try‑catch che cattura specificamente `LicenseException` e registra un messaggio chiaro:

```csharp
try
{
    var formats = FileType.GetSupportedFileTypes();
}
catch (LicenseException ex)
{
    // Log and fallback to a hard‑coded minimal list
}
```

```csharp
public static class RobustFormatRetrieval
{
    public static IEnumerable<FileType> GetSupportedFormatsWithFallback()
    {
        try
        {
            return FileType.GetSupportedFileTypes();
        }
        catch (LicenseException)
        {
            // Handle licensing issues gracefully
            LogWarning("License issue detected. Using basic format list.");
            return GetBasicFormatList();
        }
        catch (Exception ex)
        {
            LogError($"Unexpected error retrieving formats: {ex}");
            return Enumerable.Empty<FileType>();
        }
    }
    
    private static IEnumerable<FileType> GetBasicFormatList()
    {
        // Return a hardcoded list of common formats as fallback
        // This ensures your app doesn't break completely
        return new[] { FileType.Pdf, FileType.Docx, FileType.Xlsx };
    }
}
```  

## Guida al troubleshooting

### Passo 1: Verifica l'installazione
Esegui `dotnet list package` o controlla l'output della console NuGet per eventuali avvisi.  

```csharp
public static void VerifyInstallation()
{
    try
    {
        var version = typeof(FileType).Assembly.GetName().Version;
        Console.WriteLine($"GroupDocs.Annotation version: {version}");
        
        var formatCount = FileType.GetSupportedFileTypes().Count();
        Console.WriteLine($"Supported formats: {formatCount}");
        
        if (formatCount > 50) // Expected range
        {
            Console.WriteLine("✓ Installation looks good!");
        }
        else
        {
            Console.WriteLine("⚠ Possible installation or licensing issue");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"✗ Installation problem: {ex.Message}");
    }
}
```  

### Passo 2: Controlla lo stato della licenza
Assicurati che `License.SetLicense("path/to/license.json")` venga eseguito prima di qualsiasi chiamata API.  

### Passo 3: Diagnostica le limitazioni ambientali
- Conferma che la versione del runtime .NET corrisponda ai requisiti della libreria.  
- Verifica che il processo abbia permessi di lettura/scrittura sulla cartella temporanea usata da GroupDocs.Annotation.  

## Domande frequenti

**D: Quali formati di file supporta realmente GroupDocs.Annotation?**  
R: La libreria supporta **oltre 50 formati**, inclusi PDF, DOCX, XLSX, PPTX, JPEG, PNG, TIFF e molti altri. Esegui il codice di esempio per recuperare l'elenco esatto per la tua licenza.

**D: Perché ottengo meno formati supportati del previsto?**  
R: Di solito è un problema di licenza—una prova scaduta o un file di licenza caricato in modo errato. Riapplica una licenza valida e riavvia l'app.

**D: Posso verificare un singolo formato senza estrarre l'intero elenco?**  
R: Non esiste un metodo diretto “IsSupported”; l'approccio consigliato è cacheare l'elenco completo una volta e interrogare localmente per ricerche rapide.

**D: Come gestire il controllo dei formati in un'app web ad alto traffico?**  
R: Inizializza la cache dei formati all’avvio dell’app (es. in `ConfigureServices`) e memorizzala in un servizio statico o singleton. Questo elimina l'overhead per ogni richiesta.

**D: Cosa succede se GetSupportedFileTypes() genera un'eccezione?**  
R: Le eccezioni derivano tipicamente da problemi di licenza o installazioni corrotte. Verifica l'integrità del pacchetto, reinstalla se necessario e assicurati che il file di licenza sia accessibile.

## Conclusione

Ora disponi di una strategia completa, pronta per la produzione, su **come recuperare i formati** con GroupDocs.Annotation in .NET. Dalla chiamata API a riga singola al caching robusto, gestione degli errori e integrazione UI, puoi convalidare i caricamenti, generare filtri file dinamici e costruire pipeline di annotazione scalabili con fiducia.

**Passi successivi:**  
- Esplora il [GroupDocs.Annotation API Reference](https://reference.groupdocs.com/annotation/net/) per approfondire le funzionalità di annotazione.  
- Unisciti alla community sul [Support Forum](https://forum.groupdocs.com/c/annotation/) se incontri scenari particolari.  
- Sperimenta combinando la validazione dei formati con regole di business personalizzate (es. limiti di dimensione, scansioni di sicurezza) per rendere ancora più solido il tuo flusso di lavoro documentale.

## Risorse
- [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/)
- [Download Latest Version](https://releases.groupdocs.com/annotation/net/)
- [Free Trial](https://releases.groupdocs.com/annotation/net/)
- [temporary license](https://purchase.groupdocs.com/temporary-license/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [GroupDocs Purchase](https://purchase.groupdocs.com/buy)
- [Purchase Licensing](https://purchase.groupdocs.com/buy)
- [Documentation](https://docs.groupdocs.com/annotation/net/)
- [API Reference](https://reference.groupdocs.com/annotation/net/)
- [GroupDocs.Annotation API Reference](https://reference.groupdocs.com/annotation/net/)
- [Support Forum](https://forum.groupdocs.com/c/annotation/)
- [Community Support](https://forum.groupdocs.com/c/annotation/)

---

**Ultimo aggiornamento:** 2026-06-26  
**Testato con:** GroupDocs.Annotation 25.4.0 per .NET  
**Autore:** GroupDocs  

---

```csharp
public static List<string> GetSupportedExtensions()
{
    try
    {
        var supportedExtensions = FileType.GetSupportedFileTypes()
            .Select(ft => ft.Extension.ToLowerInvariant())
            .OrderBy(ext => ext)
            .ToList();
        
        return supportedExtensions;
    }
    catch (Exception ex)
    {
        // Log the error appropriately in your application
        Console.WriteLine($"Error retrieving supported formats: {ex.Message}");
        return new List<string>();
    }
}
```

## Tutorial correlati

- [Estrazione metadati documento .NET - Guida completa a GroupDocs.Annotation](/annotation/net/document-information/)
- [Caricamento PDF da URL .NET - Guida completa con GroupDocs.Annotation](/annotation/net/document-loading-essentials/load-document-from-url/)
- [Anteprima documento .NET - Guida completa a GroupDocs.Annotation](/annotation/net/document-preview/)