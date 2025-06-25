---
"description": "Förbättra dina .NET-applikationer med GroupDocs.Annotation för sömlös dokumentannotering. Steg-för-steg-handledning ingår."
"linktitle": "Ladda dokument från FTP"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Ladda dokument från FTP"
"url": "/sv/net/document-loading-essentials/load-document-from-ftp/"
"weight": 12
---

# Ladda dokument från FTP

## Introduktion
GroupDocs.Annotation för .NET är ett mångsidigt bibliotek utformat för att enkelt underlätta dokumentannoteringsfunktioner i .NET-applikationer. Oavsett om du arbetar med PDF-filer, Microsoft Office-dokument, bilder eller andra format, erbjuder detta bibliotek en enhetlig lösning för att lägga till annoteringar, till exempel kommentarer, markeringar och former, för att förbättra samarbete och dokumenthantering.
## Förkunskapskrav
Innan du börjar med handledningen, se till att du har följande förutsättningar på plats:
1. Kunskaper i C#: Kunskaper i programmeringsspråket C# är avgörande för att förstå och implementera kodexemplen som ges i den här handledningen.
2. GroupDocs.Annotation för .NET: Se till att ladda ner och installera GroupDocs.Annotation för .NET från [nedladdningslänk](https://releases.groupdocs.com/annotation/net/)Följ installationsanvisningarna för att integrera biblioteket i ditt .NET-projekt.
## Importera namnrymder
För att kunna använda GroupDocs.Annotation för .NET-funktioner måste du importera de namnrymder som krävs till ditt C#-projekt. Följ dessa steg:

Inkludera nödvändiga namnrymder i början av din kodfil i ditt C#-projekt:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Nu ska vi gå in på processen att ladda ett dokument från FTP och lägga till anteckningar i det med GroupDocs.Annotation för .NET.
## Steg 1: Definiera utmatningsväg
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
    // Annoteringskod kommer att läggas till här
}
```
## Steg 3: Lägg till annotering
Definiera och lägg till önskad anteckning, till exempel en områdesanteckning, i dokumentet.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Steg 4: Spara kommenterat dokument
Spara det kommenterade dokumentet till den angivna utdatasökvägen.
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
Generera en FTP-förfrågan för att ladda ner filen.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Steg 7: Hämta filströmmen
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
Sammanfattningsvis ger GroupDocs.Annotation för .NET utvecklare möjlighet att sömlöst integrera dokumentannoteringsfunktioner i sina .NET-applikationer. Genom att följa steg-för-steg-guiden som beskrivs i den här handledningen kan du effektivt ladda dokument från FTP och enkelt lägga till annoteringar, vilket förbättrar samarbete och dokumenthantering inom dina applikationer.
## Vanliga frågor
### Är GroupDocs.Annotation för .NET kompatibel med alla dokumentformat?
Ja, GroupDocs.Annotation för .NET stöder en mängd olika dokumentformat, inklusive PDF, Microsoft Office-dokument, bilder och mer.
### Kan jag anpassa utseendet på anteckningar som läggs till med GroupDocs.Annotation för .NET?
Absolut, GroupDocs.Annotation för .NET erbjuder omfattande anpassningsalternativ för annoteringars utseende, inklusive färger, stilar och former.
### Har GroupDocs.Annotation för .NET stöd för molnlagringstjänster?
Ja, GroupDocs.Annotation för .NET integreras sömlöst med populära molnlagringstjänster, vilket gör att du kan ladda och spara dokument från tjänster som Dropbox, Google Drive och OneDrive.
### Finns det en testversion tillgänglig för GroupDocs.Annotation för .NET?
Ja, du kan utforska funktionerna i GroupDocs.Annotation för .NET genom att ladda ner den kostnadsfria testversionen från [släppsida](https://releases.groupdocs.com/).
### Hur kan jag få teknisk hjälp eller support för GroupDocs.Annotation för .NET?
För teknisk hjälp, felsökning eller allmänna frågor kan du besöka GroupDocs.Annotation för .NET. [supportforum](https://forum.groupdocs.com/c/annotation/10).