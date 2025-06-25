---
"description": "Lär dig hur du lägger till textmarkeringar i dokument med GroupDocs.Annotation för .NET. Förbättra samarbete och produktivitet med denna omfattande guide."
"linktitle": "Lägg till textmarkeringsanteckning i dokument"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg till textmarkeringsanteckning i dokument"
"url": "/sv/net/unlocking-annotation-power/add-text-highlight-annotation/"
"weight": 22
---

# Lägg till textmarkeringsanteckning i dokument

## Introduktion
Inom dokumenthantering och samarbete framstår GroupDocs.Annotation för .NET som en robust lösning som ger utvecklare möjlighet att sömlöst integrera textmarkeringsannoteringar i sina applikationer. Den här handledningen fungerar som en omfattande guide till att lägga till textmarkeringsannoteringar i dokument med GroupDocs.Annotation för .NET. Genom steg-för-steg-instruktioner och detaljerade förklaringar får du skicklighet i att utnyttja funktionerna i detta kraftfulla bibliotek.
## Förkunskapskrav
Innan du fördjupar dig i implementeringen av textmarkeringsannoteringar, se till att du har följande förutsättningar på plats:
1. Miljökonfiguration: Ha en lämplig utvecklingsmiljö konfigurerad för .NET-utveckling.
2. Installation av GroupDocs.Annotation för .NET: Ladda ner och installera GroupDocs.Annotation för .NET från den medföljande [nedladdningslänk](https://releases.groupdocs.com/annotation/net/).
3. Bekantskap med C#: Grundläggande förståelse för programmeringsspråket C#.
4. Dokument att kommentera: Förbered ett dokument (t.ex. PDF) som du avser att kommentera.

## Importera namnrymder
Börja med att importera de namnrymder som behövs i din C#-kod för att använda funktionerna i GroupDocs.Annotation för .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Nu ska vi dela upp processen för att lägga till textmarkeringsanteckningar i flera steg:
## Steg 1: Definiera utmatningsväg
Ange utdatasökvägen där det kommenterade dokumentet ska sparas:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Initiera annotatorn
Skapa en instans av `Annotator` klass, och skickar dokumentets filnamn som en parameter:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Steg 3: Skapa markeringsannotering
Instansiera en `HighlightAnnotation` objekt och konfigurera dess egenskaper:
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
## Steg 4: Lägg till annotering
Lägg till den skapade markeringsanteckningen i dokumentet:
```csharp
annotator.Add(highlight);
```
## Steg 5: Spara kommenterat dokument
Spara det kommenterade dokumentet till den angivna utdatasökvägen:
```csharp
annotator.Save(outputPath);
```

## Slutsats
Sammanfattningsvis erbjuder GroupDocs.Annotation för .NET en effektiv metod för att integrera textmarkeringsannoteringar i dokument. Genom att följa stegen som beskrivs i den här handledningen kan utvecklare sömlöst förbättra dokumentsamarbete och produktivitet i sina applikationer.
## Vanliga frågor
### Är GroupDocs.Annotation för .NET kompatibel med alla dokumentformat?
GroupDocs.Annotation för .NET stöder olika dokumentformat, inklusive PDF, Word, Excel med flera. Se dokumentationen för en fullständig lista.
### Kan annoteringar anpassas efter specifika krav?
Ja, utvecklare har full kontroll över annoteringarnas egenskaper och utseende, vilket möjliggör anpassning för att möta olika behov.
### Finns det en gratis testversion av GroupDocs.Annotation för .NET?
Ja, du kan utforska funktionerna i GroupDocs.Annotation för .NET genom att öppna den kostnadsfria testversionen från den medföljande [filen/webbplatsen]. [länk](https://releases.groupdocs.com/).
### Hur kan jag få support för problem eller frågor relaterade till GroupDocs.Annotation för .NET?
För support och hjälp kan du besöka forumet GroupDocs.Annotation. [här](https://forum.groupdocs.com/c/annotation/10).
### Vilka licensalternativ finns tillgängliga för GroupDocs.Annotation för .NET?
GroupDocs.Annotation för .NET erbjuder olika licensalternativ, inklusive tillfälliga licenser för teständamål och kommersiella licenser för produktionsmiljöer. Besök köpsidan [här](https://purchase.groupdocs.com/buy) för mer information.