---
title: Ladda dokument från FTP
linktitle: Ladda dokument från FTP
second_title: GroupDocs.Annotation .NET API
description: Förbättra dina .NET-applikationer med GroupDocs.Annotation för sömlös dokumentkommentar. Steg-för-steg handledning ingår.
type: docs
weight: 12
url: /sv/net/document-loading-essentials/load-document-from-ftp/
---
## Introduktion
GroupDocs.Annotation for .NET är ett mångsidigt bibliotek utformat för att underlätta dokumentkommentarer i .NET-applikationer utan ansträngning. Oavsett om du har att göra med PDF-filer, Microsoft Office-dokument, bilder eller andra format, erbjuder det här biblioteket en enhetlig lösning för att lägga till kommentarer, såsom kommentarer, höjdpunkter och former, för att förbättra samarbetet och dokumenthanteringen.
## Förutsättningar
Innan du dyker in i handledningen, se till att du har följande förutsättningar på plats:
1. Kunskaper i C#: Kunskaper i programmeringsspråket C# är avgörande för att förstå och implementera kodexemplen som ges i denna handledning.
2.  GroupDocs.Annotation for .NET: Se till att ladda ner och installera GroupDocs.Annotation for .NET från[nedladdningslänk](https://releases.groupdocs.com/annotation/net/). Följ installationsinstruktionerna för att framgångsrikt integrera biblioteket i ditt .NET-projekt.
## Importera namnområden
För att kunna använda GroupDocs.Annotation för .NET-funktioner måste du importera de nödvändiga namnrymden till ditt C#-projekt. Följ dessa steg:

Inkludera de nödvändiga namnrymden i början av din kodfil i ditt C#-projekt:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Låt oss nu fördjupa oss i processen att ladda ett dokument från FTP och lägga till kommentarer till det med GroupDocs.Annotation för .NET.
## Steg 1: Definiera utdatasökväg
Ange utdatasökvägen där det kommenterade dokumentet ska sparas.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Ladda dokument från FTP
Hämta dokumentet från FTP-servern med hjälp av den angivna sökvägen.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Anteckningskod kommer att läggas till här
}
```
## Steg 3: Lägg till anteckning
Definiera och lägg till önskad anteckning, till exempel en områdesanteckning, till dokumentet.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Steg 4: Spara kommenterat dokument
Spara det kommenterade dokumentet till den angivna utmatningsvägen.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Steg 5: Hämta fil från FTP
Implementera metoden för att hämta filen från FTP-servern.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## Steg 6: Skapa FTP-förfrågan
Skapa en FTP-förfrågan för att ladda ner filen.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Steg 7: Hämta File Stream
Hämta filströmmen från FTP-svaret.
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
## Slutsats
Sammanfattningsvis ger GroupDocs.Annotation för .NET utvecklare möjlighet att sömlöst integrera funktioner för dokumentkommentarer i sina .NET-applikationer. Genom att följa den steg-för-steg-guide som beskrivs i den här handledningen kan du effektivt ladda dokument från FTP och lägga till kommentarer med lätthet, vilket förbättrar samarbete och dokumenthantering i dina applikationer.
## FAQ's
### Är GroupDocs.Annotation for .NET kompatibelt med alla dokumentformat?
Ja, GroupDocs.Annotation för .NET stöder ett brett utbud av dokumentformat, inklusive PDF, Microsoft Office-dokument, bilder och mer.
### Kan jag anpassa utseendet på anteckningar som lagts till med GroupDocs.Annotation för .NET?
Absolut, GroupDocs.Annotation för .NET erbjuder omfattande anpassningsalternativ för anteckningsutseende, inklusive färger, stilar och former.
### Ger GroupDocs.Annotation för .NET stöd för molnlagringstjänster?
Ja, GroupDocs.Annotation för .NET integreras sömlöst med populära molnlagringstjänster, så att du kan ladda och spara dokument från tjänster som Dropbox, Google Drive och OneDrive.
### Finns det en testversion tillgänglig för GroupDocs.Annotation för .NET?
 Ja, du kan utforska funktionerna i GroupDocs.Annotation för .NET genom att ladda ner den kostnadsfria testversionen från[släpp sida](https://releases.groupdocs.com/).
### Hur kan jag få teknisk assistans eller support för GroupDocs.Annotation för .NET?
 För teknisk assistans, felsökning eller allmänna frågor kan du besöka GroupDocs.Annotation for .NET[supportforum](https://forum.groupdocs.com/c/annotation/10).