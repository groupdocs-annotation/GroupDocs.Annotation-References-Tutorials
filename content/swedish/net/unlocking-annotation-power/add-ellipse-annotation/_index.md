---
"description": "Lär dig hur du lägger till ellipsannoteringar i dokument i .NET med GroupDocs.Annotation. Förbättra samarbete och kommunikation utan ansträngning."
"linktitle": "Lägg till ellipsannotering i dokument"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg till ellipsannotering i dokument"
"url": "/sv/net/unlocking-annotation-power/add-ellipse-annotation/"
type: docs
"weight": 13
---

# Lägg till ellipsannotering i dokument

## Introduktion
I den här handledningen lär du dig hur du lägger till en ellipsannotering i ett dokument med GroupDocs.Annotation för .NET. Den här steg-för-steg-guiden guidar dig genom processen och säkerställer att du förstår varje steg tydligt.
## Förkunskapskrav
Innan du börjar, se till att du har följande:
1. GroupDocs.Annotation för .NET: Se till att du har laddat ner och installerat GroupDocs.Annotation för .NET. Du kan ladda ner det från [här](https://releases.groupdocs.com/annotation/net/).
2. IDE (Integrated Development Environment): Du behöver en IDE installerad på ditt system, till exempel Visual Studio, för att skriva och köra koden.

## Importera namnrymder
Importera först de nödvändiga namnrymderna till ditt projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Steg 1: Ställ in utmatningsväg
Definiera utdatasökvägen där det kommenterade dokumentet ska sparas:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Initiera annotatorn
Initiera annotatorn genom att ange sökvägen för indatadokumentet:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Steg 3: Skapa ellipsannotering
Skapa en instans av `EllipseAnnotation` klass och ange dess egenskaper:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
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
## Steg 4: Lägg till annotering
Lägg till ellipsannoteringen i dokumentet:
```csharp
annotator.Add(ellipse);
```
## Steg 5: Spara dokument
Spara det kommenterade dokumentet till utdatasökvägen:
```csharp
annotator.Save(outputPath);
```

## Slutsats
Grattis! Du har lagt till en ellipsannotering i ett dokument med GroupDocs.Annotation för .NET. Du kan nu integrera den här funktionen i dina .NET-applikationer för att förbättra samarbete och kommunikation i dokument.
## Vanliga frågor
### Kan jag anpassa utseendet på ellipsannoteringen?
Ja, du kan anpassa olika egenskaper som bakgrundsfärg, kantfärg, opacitet etc., enligt dina behov.
### Är GroupDocs.Annotation för .NET kompatibel med alla dokumentformat?
GroupDocs.Annotation för .NET stöder ett brett utbud av dokumentformat, inklusive PDF, DOCX, PPTX, XLSX med flera.
### Kan jag lägga till flera anteckningar i ett enda dokument?
Ja, du kan lägga till flera anteckningar, inklusive ellipser, rektanglar, text etc., i ett enda dokument.
### Finns det en testversion tillgänglig för teständamål?
Ja, du kan ladda ner en gratis testversion från [här](https://releases.groupdocs.com/) att utvärdera dess egenskaper.
### Var kan jag få teknisk support för GroupDocs.Annotation för .NET?
Du kan få teknisk support från GroupDocs.Annotation-communityforumet. [här](https://forum.groupdocs.com/c/annotation/10).