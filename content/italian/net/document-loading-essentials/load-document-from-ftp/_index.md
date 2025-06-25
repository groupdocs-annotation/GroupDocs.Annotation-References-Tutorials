---
"description": "Migliora le tue applicazioni .NET con GroupDocs.Annotation per un'annotazione fluida dei documenti. Tutorial passo passo incluso."
"linktitle": "Carica documento da FTP"
"second_title": "API .NET di GroupDocs.Annotation"
"title": "Carica documento da FTP"
"url": "/it/net/document-loading-essentials/load-document-from-ftp/"
"weight": 12
---

# Carica documento da FTP

## Introduzione
GroupDocs.Annotation per .NET è una libreria versatile progettata per semplificare le funzionalità di annotazione dei documenti nelle applicazioni .NET. Che si tratti di PDF, documenti di Microsoft Office, immagini o altri formati, questa libreria offre una soluzione unificata per l'aggiunta di annotazioni, come commenti, evidenziazioni e forme, per migliorare la collaborazione e la gestione dei documenti.
## Prerequisiti
Prima di immergerti nel tutorial, assicurati di avere i seguenti prerequisiti:
1. Conoscenza di C#: la conoscenza del linguaggio di programmazione C# è essenziale per comprendere e implementare gli esempi di codice forniti in questo tutorial.
2. GroupDocs.Annotation per .NET: assicurati di scaricare e installare GroupDocs.Annotation per .NET da [collegamento per il download](https://releases.groupdocs.com/annotation/net/)Seguire le istruzioni di installazione per integrare correttamente la libreria nel progetto .NET.
## Importa spazi dei nomi
Per utilizzare le funzionalità di GroupDocs.Annotation per .NET, è necessario importare gli spazi dei nomi richiesti nel progetto C#. Seguire questi passaggi:

All'interno del tuo progetto C#, includi gli spazi dei nomi necessari all'inizio del file di codice:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Ora approfondiamo il processo di caricamento di un documento da FTP e di aggiunta di annotazioni utilizzando GroupDocs.Annotation per .NET.
## Passaggio 1: definire il percorso di output
Specificare il percorso di output in cui verrà salvato il documento annotato.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Passaggio 2: carica il documento da FTP
Recupera il documento dal server FTP utilizzando il percorso file fornito.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Il codice di annotazione verrà aggiunto qui
}
```
## Passaggio 3: aggiungere annotazioni
Definisci e aggiungi l'annotazione desiderata, ad esempio un'annotazione di area, al documento.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Passaggio 4: Salva il documento annotato
Salva il documento annotato nel percorso di output specificato.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Passaggio 5: Recupera il file da FTP
Implementare il metodo per recuperare il file dal server FTP.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## Passaggio 6: creare una richiesta FTP
Genera una richiesta FTP per scaricare il file.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Passaggio 7: Ottieni flusso di file
Recupera il flusso di file dalla risposta FTP.
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
## Conclusione
In conclusione, GroupDocs.Annotation per .NET consente agli sviluppatori di integrare perfettamente le funzionalità di annotazione dei documenti nelle loro applicazioni .NET. Seguendo la guida dettagliata descritta in questo tutorial, è possibile caricare documenti da FTP in modo efficiente e aggiungere annotazioni con facilità, migliorando la collaborazione e la gestione dei documenti all'interno delle applicazioni.
## Domande frequenti
### GroupDocs.Annotation per .NET è compatibile con tutti i formati di documento?
Sì, GroupDocs.Annotation per .NET supporta un'ampia gamma di formati di documenti, tra cui PDF, documenti Microsoft Office, immagini e altro ancora.
### Posso personalizzare l'aspetto delle annotazioni aggiunte tramite GroupDocs.Annotation per .NET?
Certamente, GroupDocs.Annotation per .NET offre ampie possibilità di personalizzazione dell'aspetto delle annotazioni, tra cui colori, stili e forme.
### GroupDocs.Annotation per .NET fornisce supporto per i servizi di archiviazione cloud?
Sì, GroupDocs.Annotation per .NET si integra perfettamente con i più diffusi servizi di archiviazione cloud, consentendo di caricare e salvare documenti da servizi come Dropbox, Google Drive e OneDrive.
### Esiste una versione di prova disponibile per GroupDocs.Annotation per .NET?
Sì, puoi esplorare le funzionalità di GroupDocs.Annotation per .NET scaricando la versione di prova gratuita da [pagina di rilascio](https://releases.groupdocs.com/).
### Come posso ottenere assistenza tecnica o supporto per GroupDocs.Annotation per .NET?
Per assistenza tecnica, risoluzione dei problemi o domande generali, puoi visitare GroupDocs.Annotation per .NET [forum di supporto](https://forum.groupdocs.com/c/annotation/10).