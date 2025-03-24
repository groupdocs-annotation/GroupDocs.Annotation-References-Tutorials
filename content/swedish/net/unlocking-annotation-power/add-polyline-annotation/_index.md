---
title: Lägg till polylinjeanteckning till dokumentet
linktitle: Lägg till polylinjeanteckning till dokumentet
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du lägger till polyline-kommentarer till dokument med GroupDocs.Annotation för .NET. Förbättra samarbets- och dokumentgranskningsprocesser utan ansträngning.
weight: 18
url: /sv/net/unlocking-annotation-power/add-polyline-annotation/
---
## Introduktion
GroupDocs.Annotation for .NET är ett kraftfullt verktyg som låter utvecklare kommentera PDF- och Microsoft Office-dokument programmatiskt. Bland dess funktioner är möjligheten att lägga till polyline-kommentarer till dokument, vilket förbättrar samarbete och dokumentgranskning.
## Förutsättningar
Innan du fortsätter med den här handledningen, se till att du har följande:
- Visual Studio installerat på ditt system.
- Grundläggande kunskaper i programmeringsspråket C#.
-  GroupDocs.Annotation för .NET-biblioteket installerat. Du kan ladda ner den från[här](https://releases.groupdocs.com/annotation/net/).

## Importera namnområden
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Steg 1: Definiera utdatasökväg
Definiera först utmatningsvägen där det kommenterade dokumentet ska sparas.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Initiera Annotator
Initiera annotatorn genom att ange namnet på inmatningsdokumentet.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Steg 3: Skapa Polyline Annotation Object
Skapa ett polyline-anteckningsobjekt och ställ in dess egenskaper som position, meddelande, opacitet, pennfärg, pennstil och pennbredd.
```csharp
PolylineAnnotation polyline = new PolylineAnnotation
{
    Box = new Rectangle(250, 35, 102, 12),
    CreatedOn = DateTime.Now,
    Message = "This is polyline annotation",
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
    },
    SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.698685
4460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
};
```
## Steg 4: Lägg till polylinjeanteckning
Lägg till polyline-anteckningen i dokumentet med hjälp av annotatorobjektet.
```csharp
annotator.Add(polyline);
```
## Steg 5: Spara dokument
Spara det kommenterade dokumentet till den angivna utmatningsvägen.
```csharp
annotator.Save(outputPath);
```
## Steg 6: Visa framgångsmeddelande
Visa ett meddelande som bekräftar att dokumentet har sparats.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats
den här handledningen har vi lärt oss hur man lägger till en polylinjekommentar till ett dokument med hjälp av GroupDocs.Annotation för .NET. Den här funktionen förbättrar samarbets- och dokumentgranskningsprocesser, vilket gör det lättare för användare att kommunicera feedback och förslag på ett effektivt sätt.
## FAQ's
### Är GroupDocs.Annotation for .NET kompatibelt med alla dokumentformat?
GroupDocs.Annotation for .NET stöder populära dokumentformat som PDF och Microsoft Office-format inklusive Word, Excel och PowerPoint.
### Kan jag anpassa utseendet på kommentarer?
Ja, du kan anpassa olika egenskaper för kommentarer som färg, opacitet, stil och bredd för att passa dina krav.
### Erbjuder GroupDocs.Annotation för .NET en gratis provperiod?
 Ja, du kan använda en gratis provversion av GroupDocs.Annotation för .NET genom att besöka[den här länken](https://releases.groupdocs.com/).
### Var kan jag hitta dokumentation för GroupDocs.Annotation för .NET?
 Du hittar dokumentationen för GroupDocs.Annotation för .NET[här](https://tutorials.groupdocs.com/annotation/net/).
### Hur kan jag få support för eventuella problem eller frågor relaterade till GroupDocs.Annotation for .NET?
 Du kan få support genom att besöka forumet GroupDocs.Annotation[här](https://forum.groupdocs.com/c/annotation/10).