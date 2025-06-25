---
"description": "Lär dig hur du kommenterar dokument i .NET med GroupDocs.Annotation. Steg-för-steg-handledning för sömlös integration med Azure Blob Storage."
"linktitle": "Ladda dokument från Azure"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Ladda dokument från Azure"
"url": "/sv/net/document-loading-essentials/load-document-from-azure/"
"weight": 11
---

# Ladda dokument från Azure

## Introduktion
Inom dokumenthantering och samarbete framstår GroupDocs.Annotation för .NET som en robust lösning som underlättar sömlösa antecknings- och markupfunktioner i .NET-applikationer. Den här handledningen fördjupar sig i hur man använder GroupDocs.Annotation för .NET för att annotera dokument och erbjuder steg-för-steg-vägledning från förutsättningar till avancerad användning.
## Förkunskapskrav
Innan du börjar med GroupDocs.Annotation för .NET, se till att du har följande förutsättningar på plats:
1. Installation av .NET Framework: GroupDocs.Annotation för .NET kräver en kompatibel .NET-körmiljö. Se till att du har .NET Framework installerat på ditt system.
2. Åtkomst till GroupDocs.Annotation-biblioteket: Få åtkomst till GroupDocs.Annotation för .NET-biblioteket antingen genom att ladda ner det från webbplatsen eller via pakethanterare som NuGet.
3. Dokument att kommentera: Förbered dokumentet (t.ex. PDF) som du vill kommentera. Se till att dokumentet är tillgängligt antingen lokalt eller via en molnlagringstjänst som Azure Blob Storage.

## Importera namnrymder
För att börja kommentera dokument med GroupDocs.Annotation för .NET, importera nödvändiga namnrymder till ditt projekt. Detta steg säkerställer att du har tillgång till nödvändiga klasser och funktioner.
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
Så här kommenterar du ett dokument som lagras i Azure Blob Storage:
### Steg 1: Ställ in utmatningsväg
Definiera utdatasökvägen där det kommenterade dokumentet ska sparas.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Steg 2: Ladda ner dokument
Hämta dokumentet från Azure Blob Storage genom att anropa `DownloadFile` metod.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Annoteringslogik
    annotator.Save(outputPath);
}
```
## Ladda ner filen från Azure Blob Storage
För att ladda ner dokumentet från Azure Blob Storage, implementera `DownloadFile` metod.
### Steg 1: Hämta Blob
Åtkomst till Azure Blob Storage-behållaren och hämta önskad blob.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### Steg 2: Ladda ner Blob-innehåll
Ladda ner blob-innehållet till en minnesström.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Hämta Azure Blob Storage-behållare
För att interagera med Azure Blob Storage, implementera `GetContainer` metod.
### Steg 1: Initiera lagringsuppgifter
Ange nödvändiga kontouppgifter och slutpunktsinformation.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{kontonamn}.blob.core.windows.net/";
```
### Steg 2: Skapa Blob-klient
Skapa en klient för att interagera med Azure Blob Storage.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### Steg 3: Hämta containerreferens
Hämta handledningar till den angivna behållaren.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### Steg 4: Skapa container om den inte finns
Se till att containern finns, och skapa den om den inte finns.
```csharp
container.CreateIfNotExists();
```

## Slutsats
GroupDocs.Annotation för .NET ger utvecklare robusta dokumentannoteringsfunktioner som integreras sömlöst i .NET-applikationer. Genom att följa stegen som beskrivs i den här handledningen kan du effektivt utnyttja funktionerna i GroupDocs.Annotation för att kommentera dokument som lagras i Azure Blob Storage.
#### Vanliga frågor
### Är GroupDocs.Annotation för .NET kompatibel med alla dokumentformat?
GroupDocs.Annotation stöder en mängd olika dokumentformat, inklusive PDF, DOCX, PPTX med flera.
### Kan annoteringar anpassas efter specifika krav?
Ja, GroupDocs.Annotation erbjuder omfattande anpassningsalternativ för annoteringar, vilket gör det möjligt för användare att ändra utseende, beteende och metadata.
### Är GroupDocs.Annotation lämplig för gemensam dokumentannotering?
Absolut! GroupDocs.Annotation underlättar gemensam dokumentannotering genom att flera användare kan lägga till, redigera och granska anteckningar samtidigt.
### Erbjuder GroupDocs.Annotation kompatibilitet mellan plattformar?
Ja, GroupDocs.Annotation är utformat för att fungera sömlöst på olika plattformar, inklusive Windows, Linux och macOS.
### Finns teknisk support tillgänglig för GroupDocs.Annotation-användare?
Ja, GroupDocs erbjuder omfattande teknisk support via sina forum och dedikerade supportkanaler.