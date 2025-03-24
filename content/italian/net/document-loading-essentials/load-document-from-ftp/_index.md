---
title: Carica documento da FTP
linktitle: Carica documento da FTP
second_title: API GroupDocs.Annotation .NET
description: Migliora le tue applicazioni .NET con GroupDocs.Annotation per annotare facilmente i documenti. Tutorial passo passo incluso.
weight: 12
url: /it/net/document-loading-essentials/load-document-from-ftp/
---

# Carica documento da FTP

## introduzione
GroupDocs.Annotation per .NET è una libreria versatile progettata per facilitare facilmente le funzionalità di annotazione dei documenti all'interno delle applicazioni .NET. Che tu abbia a che fare con PDF, documenti di Microsoft Office, immagini o altri formati, questa libreria fornisce una soluzione unificata per aggiungere annotazioni, come commenti, evidenziazioni e forme, per migliorare la collaborazione e la gestione dei documenti.
## Prerequisiti
Prima di immergerti nel tutorial, assicurati di disporre dei seguenti prerequisiti:
1. Conoscenza di C#: la conoscenza del linguaggio di programmazione C# è essenziale per comprendere e implementare gli esempi di codice forniti in questo tutorial.
2.  GroupDocs.Annotation per .NET: assicurati di scaricare e installare GroupDocs.Annotation per .NET dal[Link per scaricare](https://releases.groupdocs.com/annotation/net/). Segui le istruzioni di installazione per integrare correttamente la libreria nel tuo progetto .NET.
## Importa spazi dei nomi
Per utilizzare GroupDocs.Annotation per le funzionalità .NET, devi importare gli spazi dei nomi richiesti nel tuo progetto C#. Segui questi passi:

All'interno del tuo progetto C#, includi gli spazi dei nomi necessari all'inizio del file di codice:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Ora, approfondiamo il processo di caricamento di un documento da FTP e l'aggiunta di annotazioni utilizzando GroupDocs.Annotation per .NET.
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
## Passaggio 3: aggiungi annotazione
Definire e aggiungere l'annotazione desiderata, ad esempio un'annotazione di area, al documento.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Passaggio 4: salva il documento con annotazioni
Salva il documento annotato nel percorso di output specificato.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Passaggio 5: recupera il file da FTP
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
## Passaggio 6: crea una richiesta FTP
Genera una richiesta FTP per scaricare il file.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Passaggio 7: ottieni il flusso di file
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
In conclusione, GroupDocs.Annotation per .NET consente agli sviluppatori di integrare perfettamente le funzionalità di annotazione dei documenti nelle loro applicazioni .NET. Seguendo la guida passo passo delineata in questo tutorial, puoi caricare in modo efficiente i documenti da FTP e aggiungere annotazioni con facilità, migliorando la collaborazione e la gestione dei documenti all'interno delle tue applicazioni.
## Domande frequenti
### GroupDocs.Annotation per .NET è compatibile con tutti i formati di documenti?
Sì, GroupDocs.Annotation per .NET supporta un'ampia gamma di formati di documenti, inclusi PDF, documenti Microsoft Office, immagini e altro ancora.
### Posso personalizzare l'aspetto delle annotazioni aggiunte utilizzando GroupDocs.Annotation per .NET?
Assolutamente sì, GroupDocs.Annotation per .NET offre ampie opzioni di personalizzazione per l'aspetto delle annotazioni, inclusi colori, stili e forme.
### GroupDocs.Annotation per .NET fornisce supporto per i servizi di archiviazione cloud?
Sì, GroupDocs.Annotation per .NET si integra perfettamente con i più diffusi servizi di archiviazione cloud, consentendoti di caricare e salvare documenti da servizi come Dropbox, Google Drive e OneDrive.
### È disponibile una versione di prova per GroupDocs.Annotation per .NET?
 Sì, puoi esplorare le funzionalità di GroupDocs.Annotation per .NET scaricando la versione di prova gratuita dal sito[pagina di rilascio](https://releases.groupdocs.com/).
### Come posso ottenere assistenza tecnica o supporto per GroupDocs.Annotation per .NET?
 Per assistenza tecnica, risoluzione dei problemi o domande generali, puoi visitare GroupDocs.Annotation per .NET[Forum di assistenza](https://forum.groupdocs.com/c/annotation/10).