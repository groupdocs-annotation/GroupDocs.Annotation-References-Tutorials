---
"description": "Lär dig hur du lägger till punktannoteringar i PDF-filer med GroupDocs.Annotation för .NET. Steg-för-steg-guide för sömlös integration."
"linktitle": "Lägg till punktanteckning i dokumentet"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg till punktanteckning i dokumentet"
"url": "/sv/net/unlocking-annotation-power/add-point-annotation/"
"weight": 17
---

# Lägg till punktanteckning i dokumentet

## Introduktion
GroupDocs.Annotation för .NET är ett kraftfullt verktyg som låter utvecklare lägga till olika typer av annoteringar i dokument programmatiskt. I den här handledningen kommer vi att fokusera på att lägga till en punktannotering i ett dokument med hjälp av C#.
## Förkunskapskrav
Innan vi börjar, se till att du har följande:
1. Grundläggande förståelse för programmeringsspråket C#.
2. Visual Studio installerat på ditt system.
3. GroupDocs.Annotation för .NET-biblioteket är installerat. Du kan ladda ner det från [här](https://releases.groupdocs.com/annotation/net/).

## Importera nödvändiga namnrymder
För att komma igång måste du importera de namnrymder som krävs till ditt C#-projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Steg 1: Definiera utmatningsväg
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
I det här steget definierar vi utdatasökvägen där det kommenterade dokumentet ska sparas.
## Steg 2: Initiera annotatorn
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Här initierar vi `Annotator` objekt med indatadokumentet ("input.pdf").
## Steg 3: Skapa punktannotering
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    }
};
```
I det här steget skapar vi en `PointAnnotation` objektet och ange dess egenskaper såsom position, meddelande, sidnummer och svar.
## Steg 4: Lägg till annotering
```csharp
annotator.Add(point);
```
Här lägger vi till den skapade punktannoteringen i dokumentet.
## Steg 5: Spara dokument
```csharp
annotator.Save(outputPath);
```
Slutligen sparar vi det kommenterade dokumentet till den angivna utdatasökvägen.

## Slutsats
I den här handledningen har vi lärt oss hur man lägger till en punktannotering i ett dokument med GroupDocs.Annotation för .NET. Med det här kraftfulla biblioteket kan du förbättra dina dokumenthanteringsprogram genom att integrera annoteringsfunktioner.
## Vanliga frågor
### Är GroupDocs.Annotation för .NET kompatibel med alla dokumentformat?
Ja, GroupDocs.Annotation för .NET stöder en mängd olika dokumentformat, inklusive PDF, Microsoft Word, Excel, PowerPoint med flera.
### Kan jag anpassa utseendet på annoteringar?
Absolut! GroupDocs.Annotation för .NET erbjuder omfattande alternativ för att anpassa utseendet på annoteringar så att de passar din applikations behov.
### Finns det en gratis testversion av GroupDocs.Annotation för .NET?
Ja, du kan prova gratis från [här](https://releases.groupdocs.com/).
### Hur kan jag få support för problem eller frågor relaterade till GroupDocs.Annotation för .NET?
Du kan få support från GroupDocs.Annotation-forumet [här](https://forum.groupdocs.com/c/annotation/10).
### Kan jag få en tillfällig licens för teständamål?
Ja, du kan få en tillfällig licens från [här](https://purchase.groupdocs.com/temporary-license/).