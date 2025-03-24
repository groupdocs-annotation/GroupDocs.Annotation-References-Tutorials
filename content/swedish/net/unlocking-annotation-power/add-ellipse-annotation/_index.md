---
title: Lägg till Ellipsannotering i dokumentet
linktitle: Lägg till Ellipsannotering i dokumentet
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du lägger till ellipskommentarer till dokument i .NET med GroupDocs.Annotation. Förbättra samarbete och kommunikation utan ansträngning.
weight: 13
url: /sv/net/unlocking-annotation-power/add-ellipse-annotation/
---

# Lägg till Ellipsannotering i dokumentet

## Introduktion
I den här handledningen får du lära dig hur du lägger till en ellipskommentar till ett dokument med GroupDocs.Annotation för .NET. Den här steg-för-steg-guiden leder dig genom processen och säkerställer att du förstår varje steg tydligt.
## Förutsättningar
Innan du börjar, se till att du har följande:
1.  GroupDocs.Annotation for .NET: Se till att du har laddat ner och installerat GroupDocs.Annotation for .NET. Du kan ladda ner den från[här](https://releases.groupdocs.com/annotation/net/).
2. IDE (Integrated Development Environment): Du behöver en IDE installerad på ditt system, såsom Visual Studio, för att skriva och köra koden.

## Importera namnområden
Importera först de nödvändiga namnrymden till ditt projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Steg 1: Ställ in utdatasökväg
Definiera utdatasökvägen där det kommenterade dokumentet ska sparas:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Initiera Annotator
Initiera annotatorn genom att tillhandahålla indatadokumentets sökväg:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Steg 3: Skapa Ellipse-anteckning
 Skapa en instans av`EllipseAnnotation` klass och ställ in dess egenskaper:
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
## Steg 4: Lägg till anteckning
Lägg till ellipsanteckningen i dokumentet:
```csharp
annotator.Add(ellipse);
```
## Steg 5: Spara dokument
Spara det kommenterade dokumentet i utmatningsvägen:
```csharp
annotator.Save(outputPath);
```

## Slutsats
Grattis! Du har framgångsrikt lagt till en ellipskommentar till ett dokument med GroupDocs.Annotation för .NET. Du kan nu integrera den här funktionen i dina .NET-applikationer för att förbättra dokumentsamarbete och kommunikation.
## FAQ's
### Kan jag anpassa utseendet på ellipsanteckningen?
Ja, du kan anpassa olika egenskaper som bakgrundsfärg, kantfärg, opacitet, etc., enligt dina krav.
### Är GroupDocs.Annotation for .NET kompatibelt med alla dokumentformat?
GroupDocs.Annotation för .NET stöder ett brett utbud av dokumentformat inklusive PDF, DOCX, PPTX, XLSX och mer.
### Kan jag lägga till flera kommentarer till ett enda dokument?
Ja, du kan lägga till flera kommentarer inklusive ellipser, rektanglar, text, etc., till ett enda dokument.
### Finns det en testversion tillgänglig för teständamål?
 Ja, du kan ladda ner en gratis testversion från[här](https://releases.groupdocs.com/) för att utvärdera dess egenskaper.
### Var kan jag få teknisk support för GroupDocs.Annotation för .NET?
 Du kan få teknisk support från GroupDocs.Annotation-gemenskapsforumet[här](https://forum.groupdocs.com/c/annotation/10).