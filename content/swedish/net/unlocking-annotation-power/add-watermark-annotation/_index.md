---
"description": "Lär dig hur du enkelt lägger till vattenstämpelanteckningar i dina dokument med GroupDocs.Annotation för .NET. Förbättra dokumentens tydlighet och säkerhet."
"linktitle": "Lägg till vattenstämpelanteckning i dokumentet"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg till vattenstämpelanteckning i dokumentet"
"url": "/sv/net/unlocking-annotation-power/add-watermark-annotation/"
"weight": 28
---

# Lägg till vattenstämpelanteckning i dokumentet

## Introduktion
den här handledningen går vi igenom processen för att lägga till en vattenstämpelannotering i ett dokument med GroupDocs.Annotation för .NET. Vattenstämpelannoteringar är användbara för att indikera statusen för ett dokument, markera det som konfidentiellt eller lägga till annan relevant information.

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

1. GroupDocs.Annotation för .NET: Du kan ladda ner den från [här](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Se till att du har Visual Studio installerat på ditt system.
3. Grundläggande kunskaper i C#: Bekantskap med programmeringsspråket C# är nödvändig för att förstå och implementera kodexemplen.

## Importera namnrymder

Innan vi börjar koda, låt oss importera de nödvändiga namnrymderna:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Nu ska vi dela upp processen för att lägga till en vattenstämpelanteckning i flera steg:

## Steg 1: Definiera utmatningsväg

Först måste vi definiera utdatasökvägen där det kommenterade dokumentet ska sparas. Vi använder `Path` klass från `System.IO` namnrymd för att kombinera sökvägen till utdatakatalogen med filnamnet.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Steg 2: Initiera annotatorn

Nästa steg är att initiera annotatorn genom att ange sökvägen till indatadokumentet. Detta gör att vi kan lägga till anteckningar i dokumentet.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annoteringskoden kommer att placeras här
}
```

## Steg 3: Skapa vattenstämpelannotering

Nu ska vi skapa ett vattenstämpelannoteringsobjekt med önskade egenskaper som vinkel, position, text, teckenfärg, opacitet etc.

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

## Steg 4: Lägg till vattenstämpelannotering

Nu ska vi lägga till vattenstämpeln i dokumentet med hjälp av `Add` metod för annotator-objektet.

```csharp
annotator.Add(watermark);
```

## Steg 5: Spara dokument

Slutligen sparar vi det kommenterade dokumentet till den angivna utdatasökvägen.

```csharp
annotator.Save(outputPath);
```

## Slutsats

I den här handledningen lärde vi oss hur man lägger till en vattenstämpelannotering i ett dokument med GroupDocs.Annotation för .NET. Vattenstämpelannoteringar är ett värdefullt verktyg för att markera dokument med relevant information eller indikera deras status.

## Vanliga frågor

### F: Kan jag anpassa utseendet på vattenmärkesannoteringen?

A: Ja, du kan anpassa olika egenskaper som text, teckenstorlek, färg, opacitet, position etc. för att skräddarsy vattenstämpeln efter dina behov.

### F: Är GroupDocs.Annotation för .NET kompatibelt med olika dokumentformat?

A: Ja, GroupDocs.Annotation stöder en mängd olika dokumentformat, inklusive PDF, Microsoft Word, Excel, PowerPoint och bildformat.

### F: Kan jag lägga till flera anteckningar i ett enda dokument?

A: Absolut, GroupDocs.Annotation låter dig lägga till flera anteckningar av olika typer i ett enda dokument, vilket möjliggör omfattande dokumentmarkering.

### F: Har GroupDocs.Annotation stöd för gemensam annotering?

A: Ja, GroupDocs.Annotation underlättar gemensam annotering genom att låta användare lägga till kommentarer, svar och anteckningar, vilket främjar effektivt samarbete mellan teammedlemmar.

### F: Finns det en testversion tillgänglig för GroupDocs.Annotation för .NET?

A: Ja, du kan ladda ner en gratis testversion från [här](https://releases.groupdocs.com/).