---
"description": "Lås upp kraften i dokumentannotering med GroupDocs.Annotation för .NET. Integrera annoteringsfunktioner sömlöst i dina .NET-applikationer."
"linktitle": "Läs in dokument från lokal disk"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Läs in dokument från lokal disk"
"url": "/sv/net/document-loading-essentials/load-document-from-local-disk/"
"weight": 13
---

# Läs in dokument från lokal disk

## Introduktion
Att frigöra potentialen hos dokumentannotering har aldrig varit enklare med GroupDocs.Annotation för .NET. Detta kraftfulla verktyg ger utvecklare möjlighet att integrera robusta annoteringsfunktioner sömlöst i sina .NET-applikationer. I den här omfattande guiden guidar vi dig genom processen att använda GroupDocs.Annotation för .NET för att annotera dokument steg för steg. Oavsett om du är en erfaren utvecklare eller precis har börjat, kommer den här handledningen att ge dig kunskapen för att förbättra dokumentsamarbete och effektivisera ditt arbetsflöde.
## Förkunskapskrav
Innan du börjar med dokumentannotering med GroupDocs.Annotation för .NET, se till att du har följande förutsättningar:
1. Grundläggande kunskaper i C#: Det är viktigt att ha goda kunskaper i programmeringsspråket C#.
2. Installation av GroupDocs.Annotation för .NET: Ladda ner och installera GroupDocs.Annotation för .NET från [här](https://releases.groupdocs.com/annotation/net/).
3. Utvecklingsmiljö: Konfigurera en utvecklingsmiljö med Visual Studio eller någon kompatibel IDE.

## Importera namnrymder
För att börja kommentera dokument med GroupDocs.Annotation för .NET, importera nödvändiga namnrymder till ditt projekt:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Steg 1: Ladda dokument från lokal disk
Först måste du ladda dokumentet från din lokala hårddisk. Använd följande kodavsnitt:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Steg 2: Definiera annoteringsområde
Definiera sedan annoteringsområdet. I det här exemplet skapar vi en AreaAnnotation:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Steg 3: Spara dokument med anteckningar
Efter att du har kommenterat dokumentet, spara det med anteckningarna:
```csharp
    annotator.Save(outputPath);
}
```
## Steg 4: Visa meddelande om framgång
Slutligen, visa ett lyckat meddelande med utdatavägen:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats
Sammanfattningsvis erbjuder GroupDocs.Annotation för .NET en robust lösning för att integrera dokumentannoteringsfunktioner i dina .NET-applikationer. Genom att följa den här steg-för-steg-guiden kan du enkelt annotera dokument och förbättra samarbetet i dina projekt.
## Vanliga frågor
### Kan jag prova GroupDocs.Annotation för .NET innan jag köper?
Ja, du kan ladda ner en gratis provversion från [här](https://releases.groupdocs.com/).
### Var kan jag hitta dokumentation för GroupDocs.Annotation för .NET?
Du kan komma åt dokumentationen [här](https://tutorials.groupdocs.com/annotation/net/).
### Hur kan jag få en tillfällig licens för GroupDocs.Annotation för .NET?
Du kan få en tillfällig licens från [här](https://purchase.groupdocs.com/temporary-license/).
### Finns det stöd för GroupDocs.Annotation för .NET?
Ja, du kan hitta support på GroupDocs-forumet [här](https://forum.groupdocs.com/c/annotation/10).
### Var kan jag köpa GroupDocs.Annotation för .NET?
Du kan köpa GroupDocs.Annotation för .NET [här](https://purchase.groupdocs.com/buy).