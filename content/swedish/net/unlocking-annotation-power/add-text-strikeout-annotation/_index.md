---
"description": "Lär dig hur du lägger till textanteckningar med överstrukna texter i dokument med GroupDocs.Annotation för .NET. Förbättra samarbete och dokumentgranskningsprocesser effektivt."
"linktitle": "Lägg till textanteckning med överstruken text i dokument"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg till textanteckning med överstruken text i dokument"
"url": "/sv/net/unlocking-annotation-power/add-text-strikeout-annotation/"
type: docs
"weight": 26
---

# Lägg till textanteckning med överstruken text i dokument

## Introduktion
den här handledningen ska vi utforska hur man lägger till en textannotering med överstruken text i ett dokument med GroupDocs.Annotation för .NET. Det här biblioteket tillhandahåller kraftfulla verktyg för att annotera olika dokumenttyper, vilket förbättrar samarbete och dokumentgranskningsprocesser.
## Förkunskapskrav
Innan vi börjar, se till att du har följande förutsättningar:
1. GroupDocs.Annotation för .NET: Installera biblioteket. Du kan ladda ner det från [här](https://releases.groupdocs.com/annotation/net/).
2. Utvecklingsmiljö: Konfigurera en lämplig utvecklingsmiljö för .NET-utveckling.
3. Dokument: Ha ett dokument redo att kommentera, till exempel en PDF-fil.

## Importera namnrymder
Importera först de namnrymder som behövs för att komma åt funktionerna i GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Nu ska vi dela upp processen för att lägga till en textöverstruken anteckning i flera steg:
## Steg 1: Definiera utmatningsväg
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Här definierar vi utdatasökvägen där det kommenterade dokumentet ska sparas.
## Steg 2: Initiera annotatorn
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Initiera Annotator-objektet genom att ange sökvägen till indatadokumentet (i det här fallet PDF-filen).
## Steg 3: Skapa en överstruken annotering
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
## Steg 4: Lägg till annotering
```csharp
annotator.Add(strikeout);
```
Lägg till den skapade överstrukna anteckningen i dokumentet.
## Steg 5: Spara dokument
```csharp
annotator.Save(outputPath);
```
Spara det kommenterade dokumentet till den angivna utdatasökvägen.

## Slutsats
I den här handledningen lärde vi oss hur man lägger till en textannotering med överstruken text i ett dokument med GroupDocs.Annotation för .NET. Detta kraftfulla bibliotek möjliggör effektiv dokumentannotering, vilket förbättrar samarbete och dokumentgranskningsprocesser.
## Vanliga frågor
### Är GroupDocs.Annotation kompatibel med olika dokumentformat?
Ja, GroupDocs.Annotation stöder en mängd olika dokumentformat, inklusive PDF, Word, Excel, PowerPoint med flera.
### Kan jag anpassa utseendet på annoteringar?
Absolut, du kan anpassa annoteringsegenskaper som färg, opacitet, teckenstorlek och mer efter dina behov.
### Har GroupDocs.Annotation samarbetsfunktioner?
Ja, GroupDocs.Annotation underlättar samarbete genom att låta användare lägga till kommentarer, svar och anteckningar i dokument.
### Finns det en gratis provperiod tillgänglig?
Ja, du kan prova gratis från [här](https://releases.groupdocs.com/).
### Var kan jag få support för GroupDocs.Annotation?
Du kan få stöd från [GroupDocs.Annotation-forumet](https://forum.groupdocs.com/c/annotation/10).