---
"description": "Lär dig hur du enkelt lägger till snirkliga textanteckningar i dokument med Groupdocs.Annotation för .NET. Förbättra samarbete och dokumentgranskningsprocesser."
"linktitle": "Lägg till snirklig textanteckning i dokument"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg till snirklig textanteckning i dokument"
"url": "/sv/net/unlocking-annotation-power/add-text-squiggly-annotation/"
type: docs
"weight": 25
---

# Lägg till snirklig textanteckning i dokument

## Introduktion

Groupdocs.Annotation för .NET är ett mångsidigt bibliotek som gör det möjligt för utvecklare att enkelt integrera robusta annoteringsfunktioner i sina .NET-applikationer. Oavsett om du arbetar med PDF-filer, Word-dokument eller andra populära filformat, erbjuder Groupdocs.Annotation en sömlös lösning för att annotera och förbättra dokumentsamarbete.

## Förkunskapskrav

Innan du börjar med handledningen, se till att du har följande förutsättningar på plats:

## Importera namnrymder

Se till att importera nödvändiga namnrymder för att komma åt funktionerna som tillhandahålls av Groupdocs.Annotation för .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Nu när vi har täckt förutsättningarna, låt oss dela upp processen för att lägga till snirkliga textanteckningar i flera steg.

## Steg 1: Definiera utmatningsväg

Definiera sökvägen där det kommenterade dokumentet ska sparas.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Steg 2: Initiera annotatorn

Initiera Annotator-objektet genom att ange sökvägen för indatadokumentet.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annoteringskoden placeras här
}
```

## Steg 3: Skapa en snirklig annotering

Skapa ett SquigglyAnnotation-objekt och ange dess egenskaper.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

Lägg till den skapade snirkliga anteckningen i dokumentet.

```csharp
annotator.Add(squiggly);
```

## Steg 5: Spara dokument

Spara det kommenterade dokumentet till den angivna utdatasökvägen.

```csharp
annotator.Save(outputPath);
```

## Steg 6: Visa bekräftelse

Visa ett meddelande som bekräftar att det kommenterade dokumentet har sparats.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats

Sammanfattningsvis ger Groupdocs.Annotation för .NET utvecklare en robust uppsättning verktyg för att sömlöst integrera dokumentannoteringsfunktioner i sina .NET-applikationer. Genom att följa den här steg-för-steg-guiden kan du enkelt lägga till snirkliga textannoteringar i dina dokument, vilket förbättrar samarbete och dokumentgranskningsprocesser.

## Vanliga frågor

### F: Kan Groupdocs.Annotation stödja annoteringar i olika filformat?

A: Ja, Groupdocs.Annotation stöder annotering i en mängd olika filformat, inklusive PDF-filer, Word-dokument, Excel-ark med mera.

### F: Är Groupdocs.Annotation kompatibelt med både skrivbords- och webbapplikationer?

A: Absolut! Groupdocs.Annotation kan integreras sömlöst i både skrivbords- och webbapplikationer, vilket erbjuder flexibilitet och mångsidighet.

### F: Finns det några licensalternativ tillgängliga för Groupdocs.Annotation?

A: Ja, Groupdocs.Annotation erbjuder flexibla licensalternativ skräddarsydda för att passa individuella eller företagsbehov, inklusive tillfälliga licenser för teständamål.

### F: Kan anteckningar som skapats med Groupdocs.Annotation anpassas?

A: Absolut! Groupdocs.Annotation erbjuder omfattande anpassningsalternativ för annoteringar, vilket gör det möjligt för utvecklare att skräddarsy annoteringar efter sina specifika behov.

### F: Erbjuder Groupdocs.Annotation support och dokumentation för utvecklare?

A: Javisst! Groupdocs.Annotation tillhandahåller omfattande dokumentation och dedikerade supportforum för att hjälpa utvecklare att använda dess funktioner effektivt.