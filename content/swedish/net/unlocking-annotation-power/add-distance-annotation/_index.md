---
"description": "Lär dig hur du lägger till avståndsannoteringar i dokument med GroupDocs.Annotation för .NET. Förbättra samarbete och kommunikation utan ansträngning."
"linktitle": "Lägg till avståndsannotering i dokument"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg till avståndsannotering i dokument"
"url": "/sv/net/unlocking-annotation-power/add-distance-annotation/"
type: docs
"weight": 12
---

# Lägg till avståndsannotering i dokument

## Introduktion
I den här handledningen lär du dig hur du lägger till en avståndsannotering i ett dokument med GroupDocs.Annotation för .NET. Följ dessa steg för att slutföra uppgiften:
## Förkunskapskrav

Se till att du har följande förutsättningar på plats innan du fortsätter:

- GroupDocs.Annotation för .NET-biblioteket: Ladda ner och installera GroupDocs.Annotation för .NET-biblioteket från [den här länken](https://releases.groupdocs.com/annotation/net/).
- Dokument att kommentera: Förbered dokumentet (t.ex. PDF) som du vill lägga till avståndsannoteringen till.
- Utvecklingsmiljö: Konfigurera din utvecklingsmiljö med Visual Studio eller någon annan IDE som du väljer.

## Importera namnrymder

Innan du börjar, se till att inkludera nödvändiga namnrymder i din kod. Dessa namnrymder är viktiga för att komma åt de obligatoriska klasserna och metoderna.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Steg 1: Initiera annotatorn

Börja med att initialisera `Annotator` objekt med sökvägen till dokumentet du vill annotera.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annoteringskoden kommer att placeras här
}
```

## Steg 2: Skapa avståndsannotering

Skapa nu en `DistanceAnnotation` objekt och konfigurera dess egenskaper såsom rutans dimensioner, meddelande, opacitet, pennfärg etc.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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

## Steg 3: Lägg till annotering

Lägg till den skapade avståndsannoteringen i dokumentet med hjälp av `Add` metod för annotator-objektet.

```csharp
annotator.Add(distance);
```

## Steg 4: Spara dokument

Spara det kommenterade dokumentet på önskad plats i systemet.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Steg 5: Visa bekräftelse

Slutligen visas ett meddelande som bekräftar att det kommenterade dokumentet har sparats.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats

Att lägga till avståndsannoteringar till dokument med GroupDocs.Annotation för .NET är en enkel process. Genom att följa stegen som beskrivs i den här handledningen kan du förbättra dina dokument med värdefulla annoteringar, vilket underlättar bättre samarbete och kommunikation.

## Vanliga frågor

### F: Kan jag anpassa utseendet på avståndsannoteringen?

A: Ja, du kan anpassa olika egenskaper som färg, opacitet, linjestil etc. för att passa dina behov.

### F: Har GroupDocs.Annotation stöd för anteckningar på olika typer av dokument?

A: Ja, GroupDocs.Annotation stöder anteckningar i en mängd olika dokumentformat, inklusive PDF, Word, Excel, PowerPoint med flera.

### F: Finns det en gratis provversion av GroupDocs.Annotation?

A: Ja, du kan få tillgång till en gratis provperiod av GroupDocs.Annotation från [den här länken](https://releases.groupdocs.com/).

### F: Var kan jag hitta dokumentationen för GroupDocs.Annotation för .NET?

A: Du kan se den detaljerade dokumentationen som finns tillgänglig [här](https://tutorials.groupdocs.com/annotation/net/).

### F: Hur kan jag få support eller hjälp med GroupDocs.Annotation?

A: Du kan söka stöd och hjälp från GroupDocs.Annotation-forumet [här](https://forum.groupdocs.com/c/annotation/10).