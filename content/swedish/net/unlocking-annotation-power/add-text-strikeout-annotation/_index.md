---
title: Lägg till text genomstruken kommentar i dokumentet
linktitle: Lägg till text genomstruken kommentar i dokumentet
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du lägger till text genomstrukna kommentarer i dokument med GroupDocs.Annotation för .NET. Förbättra samarbets- och dokumentgranskningsprocesser effektivt.
weight: 26
url: /sv/net/unlocking-annotation-power/add-text-strikeout-annotation/
---
## Introduktion
den här handledningen kommer vi att undersöka hur du lägger till en text genomstruken kommentar till ett dokument med GroupDocs.Annotation för .NET. Detta bibliotek tillhandahåller kraftfulla verktyg för att kommentera olika dokumenttyper, förbättra samarbete och dokumentgranskning.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar:
1.  GroupDocs.Annotation för .NET: Installera biblioteket. Du kan ladda ner den från[här](https://releases.groupdocs.com/annotation/net/).
2. Utvecklingsmiljö: Sätt upp en lämplig utvecklingsmiljö för .NET-utveckling.
3. Dokument: Ha ett dokument redo att kommentera, till exempel en PDF-fil.

## Importera namnområden
Importera först de nödvändiga namnområdena för att komma åt funktionerna i GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Låt oss nu dela upp processen att lägga till en text genomstruken kommentar i flera steg:
## Steg 1: Definiera utdatasökväg
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Här definierar vi utmatningsvägen där det kommenterade dokumentet ska sparas.
## Steg 2: Initiera Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Initiera Annotator-objektet genom att ange sökvägen till indatadokumentet (PDF-fil i det här fallet).
## Steg 3: Skapa genomstruken kommentar
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
Skapa ett StrikeoutAnnotation-objekt med önskade egenskaper som meddelande, opacitet, sidnummer, bakgrundsfärg, punkter (koordinater) och svar.
## Steg 4: Lägg till anteckning
```csharp
annotator.Add(strikeout);
```
Lägg till den skapade överstrykningsanteckningen i dokumentet.
## Steg 5: Spara dokument
```csharp
annotator.Save(outputPath);
```
Spara det kommenterade dokumentet till den angivna utmatningsvägen.

## Slutsats
I den här handledningen lärde vi oss hur man lägger till en text genomstruken kommentar till ett dokument med hjälp av GroupDocs.Annotation för .NET. Detta kraftfulla bibliotek möjliggör effektiva dokumentkommentarer, förbättrar samarbete och dokumentgranskning.
## FAQ's
### Är GroupDocs.Annotation kompatibel med olika dokumentformat?
Ja, GroupDocs.Annotation stöder ett brett utbud av dokumentformat inklusive PDF, Word, Excel, PowerPoint och mer.
### Kan jag anpassa utseendet på kommentarer?
Absolut, du kan anpassa anteckningsegenskaper som färg, opacitet, teckenstorlek och mer enligt dina krav.
### Tillhandahåller GroupDocs.Annotation samarbetsfunktioner?
Ja, GroupDocs.Annotation underlättar samarbete genom att tillåta användare att lägga till kommentarer, svar och kommentarer till dokument.
### Finns det en gratis provperiod?
 Ja, du kan utnyttja en gratis provperiod från[här](https://releases.groupdocs.com/).
### Var kan jag få support för GroupDocs.Annotation?
 Du kan få stöd från[GroupDocs.Annotation forum](https://forum.groupdocs.com/c/annotation/10).