---
title: Lägg till vattenstämpelkommentar till dokumentet
linktitle: Lägg till vattenstämpelkommentar till dokumentet
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du lägger till vattenstämpelkommentarer till dina dokument utan ansträngning med GroupDocs.Annotation för .NET. Förbättra dokumentets tydlighet och säkerhet.
type: docs
weight: 28
url: /sv/net/unlocking-annotation-power/add-watermark-annotation/
---
## Introduktion
I den här handledningen går vi igenom processen att lägga till en vattenstämpelkommentar till ett dokument med GroupDocs.Annotation för .NET. Vattenstämpelkommentarer är användbara för att indikera status för ett dokument, markera det som konfidentiellt eller lägga till annan relevant information.

## Förutsättningar

Innan vi börjar, se till att du har följande:

1.  GroupDocs.Annotation för .NET: Du kan ladda ner den från[här](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Se till att du har Visual Studio installerat på ditt system.
3. Grundläggande kunskaper i C#: Förtrogenhet med programmeringsspråket C# är nödvändig för att förstå och implementera kodexemplen.

## Importera namnområden

Innan vi börjar koda, låt oss importera de nödvändiga namnrymden:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Låt oss nu dela upp processen att lägga till en vattenstämpelkommentar i flera steg:

## Steg 1: Definiera utdatasökväg

 Först måste vi definiera utdatavägen där det kommenterade dokumentet ska sparas. Vi kommer att använda`Path` klass från`System.IO` namnutrymme för att kombinera utdatakatalogens sökväg med filnamnet.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Steg 2: Initiera Annotator

Därefter initierar vi annotatorn genom att ange indatadokumentets sökväg. Detta gör att vi kan lägga till kommentarer till dokumentet.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Anteckningskoden kommer hit
}
```

## Steg 3: Skapa vattenmärkesanteckning

Låt oss nu skapa ett vattenmärkesanteckningsobjekt med önskade egenskaper som vinkel, position, text, teckensnittsfärg, opacitet, etc.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## Steg 4: Lägg till vattenstämpelkommentar

 Nu lägger vi till vattenstämpelkommentaren till dokumentet med hjälp av`Add` metod för anteckningsobjektet.

```csharp
annotator.Add(watermark);
```

## Steg 5: Spara dokument

Slutligen kommer vi att spara det kommenterade dokumentet till den angivna utdatasökvägen.

```csharp
annotator.Save(outputPath);
```

## Slutsats

I den här handledningen lärde vi oss hur man lägger till en vattenstämpelkommentar till ett dokument med GroupDocs.Annotation för .NET. Vattenmärkeskommentarer är ett värdefullt verktyg för att markera dokument med relevant information eller ange deras status.

## FAQ's

### F: Kan jag anpassa utseendet på vattenstämpelkommentaren?

S: Ja, du kan anpassa olika egenskaper som text, teckenstorlek, färg, opacitet, position, etc., för att skräddarsy vattenstämpeln efter dina krav.

### F: Är GroupDocs.Annotation för .NET kompatibelt med olika dokumentformat?

S: Ja, GroupDocs.Annotation stöder ett brett utbud av dokumentformat inklusive PDF, Microsoft Word, Excel, PowerPoint och bildformat.

### F: Kan jag lägga till flera kommentarer till ett enda dokument?

S: Absolut, GroupDocs.Annotation låter dig lägga till flera kommentarer av olika typer till ett enda dokument, vilket möjliggör omfattande dokumentuppmärkning.

### F: Ger GroupDocs.Annotation stöd för samarbetskommentarer?

S: Ja, GroupDocs.Annotation underlättar samverkanskommentarer genom att tillåta användare att lägga till kommentarer, svar och anteckningar, vilket främjar effektivt samarbete mellan teammedlemmar.

### F: Finns det en testversion tillgänglig för GroupDocs.Annotation för .NET?

 S: Ja, du kan ladda ner en gratis testversion från[här](https://releases.groupdocs.com/).