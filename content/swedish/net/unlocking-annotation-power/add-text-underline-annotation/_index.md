---
title: Lägg till text understruken kommentar i dokumentet
linktitle: Lägg till text understruken kommentar i dokumentet
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du lägger till textunderstrukna kommentarer i dokument med GroupDocs.Annotation för .NET. Förbättra samarbete och kommunikation utan ansträngning.
weight: 27
url: /sv/net/unlocking-annotation-power/add-text-underline-annotation/
---
## Introduktion
I den här självstudien går vi igenom processen att lägga till en understruken text i ett dokument med GroupDocs.Annotation för .NET. Textunderstrukna kommentarer kan vara användbara för att framhäva specifika delar av ett dokument, till exempel viktiga stycken eller nyckelpunkter.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar installerade:
1.  GroupDocs.Annotation for .NET: Ladda ner och installera GroupDocs.Annotation for .NET från[här](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Se till att du har .NET Framework installerat på ditt system.

## Importera namnområden
Låt oss först importera de nödvändiga namnrymden till vårt projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Låt oss nu dela upp exemplet i flera steg:
## Steg 1: Definiera utdatasökväg
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
I det här steget definierar vi utmatningsvägen där det kommenterade dokumentet ska sparas.
## Steg 2: Initiera Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Här initierar vi en instans av`Annotator` klass genom att tillhandahålla indatadokumentets sökväg.
## Steg 3: Skapa understrykningskommentarer
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // fungerar endast stöds Word- och PDF-dokument
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
 Detta steg innebär att skapa en`UnderlineAnnotation`objekt med olika egenskaper som typsnittsfärg, meddelande, opacitet, sidnummer, bakgrundsfärg, understrykningsfärg, punkter och svar.
## Steg 4: Lägg till anteckning till dokument
```csharp
annotator.Add(underline);
```
Här lägger vi till understrykningsanteckningen i dokumentet.
## Steg 5: Spara kommenterat dokument
```csharp
annotator.Save(outputPath);
```
Slutligen sparar vi det kommenterade dokumentet till den angivna utmatningsvägen.

## Slutsats
I den här handledningen lärde vi oss hur man lägger till en understruken text i ett dokument med hjälp av GroupDocs.Annotation för .NET. Detta kraftfulla bibliotek erbjuder olika anteckningsalternativ för att förbättra dokumentsamarbete och kommunikation.
## FAQ's
### Kan jag anpassa utseendet på understrykningskommentaren?
Ja, du kan anpassa egenskaper som färg, opacitet och position enligt dina krav.
### Är GroupDocs.Annotation kompatibel med olika dokumentformat?
Ja, GroupDocs.Annotation stöder ett brett utbud av dokumentformat inklusive Word och PDF.
### Kan jag lägga till flera kommentarer till ett enda dokument?
Absolut, GroupDocs.Annotation låter dig lägga till flera kommentarer av olika typer till ett dokument.
### Finns det en gratis testversion tillgänglig för GroupDocs.Annotation?
 Ja, du kan komma åt den kostnadsfria testversionen från[här](https://releases.groupdocs.com/).
### Var kan jag få support för GroupDocs.Annotation?
 Du kan få support från GroupDocs.Annotation-gemenskapsforumet[här](https://forum.groupdocs.com/c/annotation/10).