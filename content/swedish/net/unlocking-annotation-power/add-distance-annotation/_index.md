---
title: Lägg till avståndsanteckning till dokument
linktitle: Lägg till avståndsanteckning till dokument
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du lägger till distanskommentarer till dokument med GroupDocs.Annotation för .NET. Förbättra samarbete och kommunikation utan ansträngning.
weight: 12
url: /sv/net/unlocking-annotation-power/add-distance-annotation/
---
## Introduktion
I den här handledningen kommer du att lära dig hur du lägger till en distanskommentar till ett dokument med GroupDocs.Annotation för .NET. Följ dessa steg för att utföra uppgiften:
## Förutsättningar

Se till att du har följande förutsättningar innan du fortsätter:

-  GroupDocs.Annotation for .NET Library: Ladda ner och installera GroupDocs.Annotation for .NET-biblioteket från[den här länken](https://releases.groupdocs.com/annotation/net/).
- Dokument att kommentera: Förbered dokumentet (t.ex. PDF) som du vill lägga till avståndsanteckningen till.
- Utvecklingsmiljö: Konfigurera din utvecklingsmiljö med Visual Studio eller valfri annan IDE.

## Importera namnområden

Innan du börjar, se till att inkludera de nödvändiga namnrymden i din kod. Dessa namnutrymmen är viktiga för att komma åt de klasser och metoder som krävs.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Steg 1: Initiera Annotator

 Börja med att initiera`Annotator` objekt med sökvägen till dokumentet du vill kommentera.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Anteckningskoden kommer hit
}
```

## Steg 2: Skapa avståndsanteckning

 Skapa nu en`DistanceAnnotation` objekt och konfigurera dess egenskaper som boxdimensioner, meddelande, opacitet, pennfärg etc.

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

## Steg 3: Lägg till anteckning

 Lägg till den skapade avståndsanteckningen till dokumentet med hjälp av`Add` metod för anteckningsobjektet.

```csharp
annotator.Add(distance);
```

## Steg 4: Spara dokument

Spara det kommenterade dokumentet på önskad plats på ditt system.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Steg 5: Visa bekräftelse

Visa slutligen ett meddelande som bekräftar att det kommenterade dokumentet har sparats.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats

Att lägga till distanskommentarer till dokument med GroupDocs.Annotation för .NET är en enkel process. Genom att följa stegen som beskrivs i den här handledningen kan du förbättra dina dokument med värdefulla kommentarer, vilket underlättar bättre samarbete och kommunikation.

## FAQ's

### F: Kan jag anpassa utseendet på avståndsanteckningen?

S: Ja, du kan anpassa olika egenskaper som färg, opacitet, linjestil, etc., för att passa dina krav.

### F: Stöder GroupDocs.Annotation anteckningar på olika typer av dokument?

S: Ja, GroupDocs.Annotation stöder kommentarer i ett brett utbud av dokumentformat inklusive PDF, Word, Excel, PowerPoint och mer.

### F: Finns det en gratis testversion tillgänglig för GroupDocs.Annotation?

 S: Ja, du kan få tillgång till en gratis provversion av GroupDocs.Annotation från[den här länken](https://releases.groupdocs.com/).

### F: Var kan jag hitta dokumentationen för GroupDocs.Annotation för .NET?

 S: Du kan hänvisa till den detaljerade dokumentationen som finns tillgänglig[här](https://tutorials.groupdocs.com/annotation/net/).

### F: Hur kan jag få support eller hjälp med GroupDocs.Annotation?

 S: Du kan söka stöd och hjälp från GroupDocs.Annotation-gemenskapsforumet[här](https://forum.groupdocs.com/c/annotation/10).