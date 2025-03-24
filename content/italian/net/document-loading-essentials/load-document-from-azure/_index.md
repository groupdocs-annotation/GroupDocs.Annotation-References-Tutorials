---
title: Carica documento da Azure
linktitle: Carica documento da Azure
second_title: API GroupDocs.Annotation .NET
description: Scopri come annotare i documenti in .NET utilizzando GroupDocs.Annotation. Esercitazione dettagliata per un'integrazione perfetta con Archiviazione BLOB di Azure.
weight: 11
url: /it/net/document-loading-essentials/load-document-from-azure/
---

# Carica documento da Azure

## introduzione
Nell'ambito della gestione e della collaborazione dei documenti, GroupDocs.Annotation per .NET emerge come una soluzione solida, facilitando funzionalità di annotazione e markup senza soluzione di continuità all'interno delle applicazioni .NET. Questo tutorial approfondisce le complessità dell'utilizzo di GroupDocs.Annotation for .NET per annotare i documenti, offrendo indicazioni dettagliate dai prerequisiti all'utilizzo avanzato.
## Prerequisiti
Prima di immergerti in GroupDocs.Annotation per .NET, assicurati di disporre dei seguenti prerequisiti:
1. Installazione di .NET Framework: GroupDocs.Annotation per .NET richiede un ambiente runtime .NET compatibile. Assicurati di avere .NET Framework installato sul tuo sistema.
2. Accesso alla libreria GroupDocs.Annotation: ottieni l'accesso alla libreria GroupDocs.Annotation per .NET scaricandola dal sito Web o tramite gestori di pacchetti come NuGet.
3. Documento da annotare: prepara il documento (ad esempio PDF) che intendi annotare. Assicurarsi che il documento sia accessibile localmente o tramite un servizio di archiviazione cloud come Archiviazione BLOB di Azure.

## Importa spazi dei nomi
Per iniziare ad annotare i documenti utilizzando GroupDocs.Annotation per .NET, importa gli spazi dei nomi necessari nel tuo progetto. Questo passaggio garantisce l'accesso alle classi e alle funzionalità richieste.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Carica documento da Azure
Per annotare un documento archiviato nell'archivio BLOB di Azure, attenersi alla seguente procedura:
### Passaggio 1: impostare il percorso di output
Definire il percorso di output in cui verrà salvato il documento annotato.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Passaggio 2: scarica il documento
 Recuperare il documento da Archiviazione BLOB di Azure richiamando il file`DownloadFile` metodo.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Logica dell'annotazione
    annotator.Save(outputPath);
}
```
## Scaricare il file dall'archivio BLOB di Azure
 Per scaricare il documento da Archiviazione BLOB di Azure, implementare il file`DownloadFile` metodo.
### Passaggio 1: recuperare il BLOB
Accedi al contenitore Archiviazione BLOB di Azure e recupera il BLOB desiderato.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### Passaggio 2: scaricare il contenuto BLOB
Scaricare il contenuto del BLOB in un flusso di memoria.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Ottieni il contenitore di archiviazione BLOB di Azure
 Per interagire con Archiviazione BLOB di Azure, implementare il file`GetContainer` metodo.
### Passaggio 1: inizializzare le credenziali di archiviazione
Fornire le credenziali dell'account e le informazioni sull'endpoint necessarie.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{accountName}.blob.core.windows.net/";
```
### Passaggio 2: creare un client BLOB
Creare un client per interagire con Archiviazione BLOB di Azure.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### Passaggio 3: recuperare il riferimento al contenitore
Ottenere un riferimento al contenitore specificato.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### Passaggio 4: crea il contenitore se non esiste
Assicurati che il contenitore esista e crealo in caso contrario.
```csharp
container.CreateIfNotExists();
```

## Conclusione
GroupDocs.Annotation per .NET offre agli sviluppatori solide funzionalità di annotazione dei documenti, integrandosi perfettamente nelle applicazioni .NET. Seguendo i passaggi descritti in questa esercitazione, è possibile sfruttare in modo efficace le funzionalità di GroupDocs.Annotation per annotare i documenti archiviati nell'archivio BLOB di Azure.
#### Domande frequenti
### GroupDocs.Annotation per .NET è compatibile con tutti i formati di documenti?
GroupDocs.Annotation supporta un'ampia gamma di formati di documenti, inclusi PDF, DOCX, PPTX e altri.
### Le annotazioni possono essere personalizzate in base a requisiti specifici?
Sì, GroupDocs.Annotation offre ampie opzioni di personalizzazione per le annotazioni, consentendo agli utenti di modificare aspetto, comportamento e metadati.
### GroupDocs.Annotation è adatto per l'annotazione collaborativa dei documenti?
Assolutamente! GroupDocs.Annotation facilita l'annotazione collaborativa dei documenti consentendo a più utenti di aggiungere, modificare e rivedere le annotazioni contemporaneamente.
### GroupDocs.Annotation offre compatibilità multipiattaforma?
Sì, GroupDocs.Annotation è progettato per funzionare perfettamente su varie piattaforme, tra cui Windows, Linux e macOS.
### Il supporto tecnico è disponibile per gli utenti di GroupDocs.Annotation?
Sì, GroupDocs fornisce supporto tecnico completo attraverso i suoi forum e canali di supporto dedicati.