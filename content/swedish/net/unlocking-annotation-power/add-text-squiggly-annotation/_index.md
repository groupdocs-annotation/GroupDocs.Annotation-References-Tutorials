---
title: Lägg till en snirklig textanteckning i dokumentet
linktitle: Lägg till en snirklig textanteckning i dokumentet
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du enkelt lägger till snirkliga kommentarer till dokument med Groupdocs.Annotation för .NET. Förbättra samarbets- och dokumentgranskningsprocesser.
type: docs
weight: 25
url: /sv/net/unlocking-annotation-power/add-text-squiggly-annotation/
---
## Introduktion

Groupdocs.Annotation for .NET är ett mångsidigt bibliotek som gör det möjligt för utvecklare att integrera robusta anteckningsfunktioner i sina .NET-applikationer utan ansträngning. Oavsett om du arbetar med PDF-filer, Word-dokument eller andra populära filformat, erbjuder Groupdocs.Annotation en sömlös lösning för att kommentera och förbättra dokumentsamarbetet.

## Förutsättningar

Innan du dyker in i handledningen, se till att du har följande förutsättningar på plats:

## Importera namnområden

Se till att importera de nödvändiga namnområdena för att komma åt funktionerna som tillhandahålls av Groupdocs.Annotation för .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Nu när vi har täckt förutsättningarna, låt oss dela upp processen med att lägga till snirkliga textanteckningar i flera steg.

## Steg 1: Definiera utdatasökväg

Definiera sökvägen där det kommenterade dokumentet ska sparas.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Steg 2: Initiera Annotator

Initiera Annotator-objektet genom att tillhandahålla indatadokumentets sökväg.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Anteckningskoden går här
}
```

## Steg 3: Skapa Squiggly Annotation

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

## Steg 4: Lägg till anteckning

Lägg till den skapade snirkliga anteckningen till dokumentet.

```csharp
annotator.Add(squiggly);
```

## Steg 5: Spara dokument

Spara det kommenterade dokumentet till den angivna utmatningsvägen.

```csharp
annotator.Save(outputPath);
```

## Steg 6: Visa bekräftelse

Visa ett meddelande som bekräftar att det kommenterade dokumentet har sparats.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats

Sammanfattningsvis ger Groupdocs.Annotation för .NET utvecklare en robust uppsättning verktyg för att sömlöst integrera dokumentkommentarfunktioner i sina .NET-applikationer. Genom att följa den här steg-för-steg-guiden kan du enkelt lägga till snirkliga textkommentarer till dina dokument, vilket förbättrar samarbetet och dokumentgranskningsprocesserna.

## FAQ's

### F: Kan Groupdocs.Annotation stödja anteckningar i olika filformat?

S: Ja, Groupdocs.Annotation stöder anteckningar i ett brett utbud av filformat, inklusive PDF-filer, Word-dokument, Excel-ark och mer.

### F: Är Groupdocs.Annotation kompatibel med både skrivbords- och webbapplikationer?

A: Absolut! Groupdocs.Annotation kan sömlöst integreras i både skrivbords- och webbapplikationer, vilket erbjuder flexibilitet och mångsidighet.

### F: Finns det några licensalternativ tillgängliga för Groupdocs.Annotation?

S: Ja, Groupdocs.Annotation erbjuder flexibla licensieringsalternativ som är skräddarsydda för att passa individuella eller företags behov, inklusive tillfälliga licenser för teständamål.

### F: Kan kommentarer skapade med Groupdocs.Annotation anpassas?

A: Visst! Groupdocs.Annotation erbjuder omfattande anpassningsalternativ för annoteringar, vilket gör att utvecklare kan skräddarsy annoteringar efter sina specifika krav.

### F: Erbjuder Groupdocs.Annotation stöd och dokumentation för utvecklare?

A: Verkligen! Groupdocs.Annotation tillhandahåller omfattande dokumentation och dedikerade supportforum för att hjälpa utvecklare att använda dess funktioner effektivt.