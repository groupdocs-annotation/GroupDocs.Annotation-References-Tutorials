---
title: Lägg till textmarkeringskommentar till dokument
linktitle: Lägg till textmarkeringskommentar till dokument
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du lägger till textmarkeringskommentarer i dokument med GroupDocs.Annotation för .NET. Förbättra samarbetet och produktiviteten med detta omfattande.
weight: 22
url: /sv/net/unlocking-annotation-power/add-text-highlight-annotation/
---

# Lägg till textmarkeringskommentar till dokument

## Introduktion
När det gäller dokumenthantering och samarbete framstår GroupDocs.Annotation för .NET som en robust lösning som ger utvecklare möjlighet att sömlöst integrera textmarkeringskommentarer i sina applikationer. Den här handledningen fungerar som en omfattande guide för att lägga till textmarkeringskommentarer till dokument med GroupDocs.Annotation för .NET. Genom steg-för-steg-instruktioner och detaljerade förklaringar kommer du att få färdighet i att utnyttja funktionerna i detta kraftfulla bibliotek.
## Förutsättningar
Innan du fördjupar dig i implementeringen av textmarkeringskommentarer, se till att du har följande förutsättningar på plats:
1. Miljöinställningar: Ha en lämplig utvecklingsmiljö konfigurerad för .NET-utveckling.
2.  Installation av GroupDocs.Annotation for .NET: Ladda ner och installera GroupDocs.Annotation for .NET från den medföljande[nedladdningslänk](https://releases.groupdocs.com/annotation/net/).
3. Kännedom om C#: Grundläggande förståelse för programmeringsspråket C#.
4. Dokument att kommentera: Förbered ett dokument (t.ex. PDF) som du tänker kommentera.

## Importera namnområden
För att börja, importera de nödvändiga namnområdena i din C#-kod för att använda funktionerna i GroupDocs.Annotation for .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Låt oss nu dela upp processen att lägga till textmarkeringskommentarer i flera steg:
## Steg 1: Definiera utdatasökväg
Ange utdatasökvägen där det kommenterade dokumentet ska sparas:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Initiera Annotator
 Skapa en instans av`Annotator` klass och skickar dokumentets filnamn som en parameter:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Steg 3: Skapa höjdpunktskommentarer
 Instantiera en`HighlightAnnotation` objekt och konfigurera dess egenskaper:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
## Steg 4: Lägg till anteckning
Lägg till den skapade markeringskommentaren till dokumentet:
```csharp
annotator.Add(highlight);
```
## Steg 5: Spara kommenterat dokument
Spara det kommenterade dokumentet till den angivna utdatasökvägen:
```csharp
annotator.Save(outputPath);
```

## Slutsats
Sammanfattningsvis erbjuder GroupDocs.Annotation för .NET ett strömlinjeformat tillvägagångssätt för att införliva textmarkeringskommentarer i dokument. Genom att följa stegen som beskrivs i denna handledning kan utvecklare sömlöst förbättra dokumentsamarbetet och produktiviteten inom sina applikationer.
## FAQ's
### Är GroupDocs.Annotation for .NET kompatibelt med alla dokumentformat?
GroupDocs.Annotation för .NET stöder olika dokumentformat, inklusive PDF, Word, Excel och mer. Se dokumentationen för den fullständiga listan.
### Kan kommentarer anpassas efter specifika krav?
Ja, utvecklare har full kontroll över egenskaperna och utseendet på kommentarer, vilket möjliggör anpassning för att möta olika behov.
### Finns det en gratis testversion tillgänglig för GroupDocs.Annotation för .NET?
 Ja, du kan utforska funktionerna i GroupDocs.Annotation för .NET genom att få tillgång till den kostnadsfria testversionen från den medföljande[länk](https://releases.groupdocs.com/).
### Hur kan jag få support för eventuella problem eller frågor relaterade till GroupDocs.Annotation for .NET?
 För support och hjälp kan du besöka forumet GroupDocs.Annotation[här](https://forum.groupdocs.com/c/annotation/10).
### Vilka licensalternativ finns för GroupDocs.Annotation för .NET?
 GroupDocs.Annotation för .NET erbjuder olika licensalternativ, inklusive tillfälliga licenser för teständamål och kommersiella licenser för produktionsmiljöer. Besök köpsidan[här](https://purchase.groupdocs.com/buy) för mer detaljer.