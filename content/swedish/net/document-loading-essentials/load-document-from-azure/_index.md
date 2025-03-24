---
title: Ladda dokument från Azure
linktitle: Ladda dokument från Azure
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du kommenterar dokument i .NET med GroupDocs.Annotation. Steg-för-steg handledning för sömlös integration med Azure Blob Storage.
weight: 11
url: /sv/net/document-loading-essentials/load-document-from-azure/
---
## Introduktion
När det gäller dokumenthantering och samarbete framstår GroupDocs.Annotation för .NET som en robust lösning som underlättar sömlösa antecknings- och uppmärkningsfunktioner inom .NET-applikationer. Denna handledning fördjupar sig i krångligheterna med att utnyttja GroupDocs.Annotation för .NET för att kommentera dokument, och erbjuder steg-för-steg-vägledning från förutsättningar till avancerad användning.
## Förutsättningar
Innan du dyker in i GroupDocs.Annotation för .NET, se till att du har följande förutsättningar:
1. Installation av .NET Framework: GroupDocs.Annotation för .NET kräver en kompatibel .NET runtime-miljö. Se till att du har .NET Framework installerat på ditt system.
2. Tillgång till GroupDocs.Annotation Library: Få tillgång till GroupDocs.Annotation för .NET-biblioteket antingen genom att ladda ner det från webbplatsen eller genom pakethanterare som NuGet.
3. Dokument att kommentera: Förbered dokumentet (t.ex. PDF) som du tänker kommentera. Se till att dokumentet är tillgängligt antingen lokalt eller via en molnlagringstjänst som Azure Blob Storage.

## Importera namnområden
För att börja kommentera dokument med GroupDocs.Annotation för .NET, importera de nödvändiga namnrymden till ditt projekt. Detta steg säkerställer att du har tillgång till de klasser och funktioner som krävs.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Ladda dokument från Azure
Följ dessa steg för att kommentera ett dokument som lagras i Azure Blob Storage:
### Steg 1: Ställ in utdatasökväg
Definiera utdatavägen där det kommenterade dokumentet ska sparas.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Steg 2: Ladda ner dokument
 Hämta dokumentet från Azure Blob Storage genom att anropa`DownloadFile` metod.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Anteckningslogik
    annotator.Save(outputPath);
}
```
## Ladda ner fil från Azure Blob Storage
 För att ladda ner dokumentet från Azure Blob Storage, implementera`DownloadFile` metod.
### Steg 1: Hämta Blob
Gå till Azure Blob Storage-behållaren och hämta önskad blob.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### Steg 2: Ladda ner Blob-innehåll
Ladda ner blobinnehållet till en minnesström.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Skaffa Azure Blob Storage Container
 För att interagera med Azure Blob Storage, implementera`GetContainer` metod.
### Steg 1: Initiera lagringsuppgifter
Ange nödvändiga kontouppgifter och slutpunktsinformation.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{accountName}.blob.core.windows.net/";
```
### Steg 2: Skapa Blob Client
Skapa en klient för att interagera med Azure Blob Storage.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### Steg 3: Hämta containerreferens
Skaffa en referens till den angivna behållaren.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### Steg 4: Skapa behållare om den inte finns
Se till att behållaren finns och skapa den om inte.
```csharp
container.CreateIfNotExists();
```

## Slutsats
GroupDocs.Annotation for .NET ger utvecklare kraftfulla dokumentkommentarer som sömlöst integreras i .NET-applikationer. Genom att följa stegen som beskrivs i den här självstudien kan du effektivt utnyttja funktionerna i GroupDocs.Annotation för att kommentera dokument som lagras i Azure Blob Storage.
#### FAQ's
### Är GroupDocs.Annotation for .NET kompatibelt med alla dokumentformat?
GroupDocs.Annotation stöder ett brett utbud av dokumentformat, inklusive PDF, DOCX, PPTX och mer.
### Kan kommentarer anpassas efter specifika krav?
Ja, GroupDocs.Annotation erbjuder omfattande anpassningsalternativ för kommentarer, så att användare kan ändra utseende, beteende och metadata.
### Är GroupDocs.Annotation lämplig för samverkande dokumentkommentarer?
Absolut! GroupDocs.Annotation underlättar samverkande dokumentkommentarer genom att göra det möjligt för flera användare att lägga till, redigera och granska kommentarer samtidigt.
### Erbjuder GroupDocs.Annotation kompatibilitet över plattformar?
Ja, GroupDocs.Annotation är utformad för att fungera sömlöst på olika plattformar, inklusive Windows, Linux och macOS.
### Finns teknisk support tillgänglig för GroupDocs.Annotation-användare?
Ja, GroupDocs tillhandahåller omfattande teknisk support genom sina forum och dedikerade supportkanaler.