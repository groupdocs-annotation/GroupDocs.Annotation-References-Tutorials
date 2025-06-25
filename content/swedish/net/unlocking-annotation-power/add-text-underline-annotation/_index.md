---
"description": "Lär dig hur du lägger till understrykningar av text i dokument med GroupDocs.Annotation för .NET. Förbättra samarbete och kommunikation utan ansträngning."
"linktitle": "Lägg till understrykningsanteckning för text i dokument"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg till understrykningsanteckning för text i dokument"
"url": "/sv/net/unlocking-annotation-power/add-text-underline-annotation/"
"weight": 27
---

# Lägg till understrykningsanteckning för text i dokument

## Introduktion
den här handledningen går vi igenom processen att lägga till en understrykningsanteckning i ett dokument med GroupDocs.Annotation för .NET. Understrykningsanteckningar kan vara användbara för att betona specifika delar av ett dokument, till exempel viktiga avsnitt eller nyckelpunkter.
## Förkunskapskrav
Innan vi börjar, se till att du har följande förutsättningar installerade:
1. GroupDocs.Annotation för .NET: Ladda ner och installera GroupDocs.Annotation för .NET från [här](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Se till att du har .NET Framework installerat på ditt system.

## Importera namnrymder
Låt oss först importera de nödvändiga namnrymderna till vårt projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Nu ska vi dela upp exemplet i flera steg:
## Steg 1: Definiera utmatningsväg
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
I det här steget definierar vi utdatasökvägen där det kommenterade dokumentet ska sparas.
## Steg 2: Initiera annotatorn
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Här initierar vi en instans av `Annotator` klassen genom att ange sökvägen till indatadokumentet.
## Steg 3: Skapa understrykningsannotering
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // fungerar endast Word- och PDF-dokument som stöds
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
Detta steg innebär att skapa en `UnderlineAnnotation` objekt med olika egenskaper som teckenfärg, meddelande, opacitet, sidnummer, bakgrundsfärg, understrykningsfärg, punkter och svar.
## Steg 4: Lägg till anteckning i dokumentet
```csharp
annotator.Add(underline);
```
Här lägger vi till understrykningsanteckningen i dokumentet.
## Steg 5: Spara kommenterat dokument
```csharp
annotator.Save(outputPath);
```
Slutligen sparar vi det kommenterade dokumentet till den angivna utdatasökvägen.

## Slutsats
I den här handledningen lärde vi oss hur man lägger till en understrykningsanteckning i ett dokument med GroupDocs.Annotation för .NET. Detta kraftfulla bibliotek erbjuder olika anteckningsalternativ för att förbättra samarbete och kommunikation i dokument.
## Vanliga frågor
### Kan jag anpassa utseendet på understrykningsanteckningen?
Ja, du kan anpassa egenskaper som färg, opacitet och position efter dina behov.
### Är GroupDocs.Annotation kompatibel med olika dokumentformat?
Ja, GroupDocs.Annotation stöder en mängd olika dokumentformat, inklusive Word och PDF.
### Kan jag lägga till flera anteckningar i ett enda dokument?
Absolut, GroupDocs.Annotation låter dig lägga till flera anteckningar av olika typer i ett dokument.
### Finns det en gratis provversion av GroupDocs.Annotation?
Ja, du kan få tillgång till den kostnadsfria testversionen från [här](https://releases.groupdocs.com/).
### Var kan jag få support för GroupDocs.Annotation?
Du kan få support från GroupDocs.Annotation-communityforumet [här](https://forum.groupdocs.com/c/annotation/10).