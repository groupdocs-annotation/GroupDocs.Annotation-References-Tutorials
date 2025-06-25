---
"description": "Lär dig hur du lägger till polyline-anteckningar i dokument med GroupDocs.Annotation för .NET. Förbättra samarbete och dokumentgranskningsprocesser utan ansträngning."
"linktitle": "Lägg till polylinjeannotering i dokument"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg till polylinjeannotering i dokument"
"url": "/sv/net/unlocking-annotation-power/add-polyline-annotation/"
"weight": 18
---

# Lägg till polylinjeannotering i dokument

## Introduktion
GroupDocs.Annotation för .NET är ett kraftfullt verktyg som låter utvecklare kommentera PDF- och Microsoft Office-dokument programmatiskt. Bland dess funktioner finns möjligheten att lägga till polyline-anteckningar i dokument, vilket förbättrar samarbete och dokumentgranskningsprocesser.
## Förkunskapskrav
Innan du fortsätter med den här handledningen, se till att du har följande:
- Visual Studio installerat på ditt system.
- Grundläggande kunskaper i programmeringsspråket C#.
- GroupDocs.Annotation för .NET-biblioteket är installerat. Du kan ladda ner det från [här](https://releases.groupdocs.com/annotation/net/).

## Importera namnrymder
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Steg 1: Definiera utmatningsväg
Definiera först utdatasökvägen där det kommenterade dokumentet ska sparas.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Initiera annotatorn
Initiera annotatorn genom att ange namnet på indatadokumentet.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Steg 3: Skapa ett polylinjeannoteringsobjekt
Skapa ett polylinjeannoteringsobjekt och ange dess egenskaper som position, meddelande, opacitet, pennfärg, pennstil och pennbredd.
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
## Steg 4: Lägg till polylinjeannotering
Lägg till polylinjeannoteringen i dokumentet med hjälp av annotator-objektet.
```csharp
annotator.Add(polyline);
```
## Steg 5: Spara dokument
Spara det kommenterade dokumentet till den angivna utdatasökvägen.
```csharp
annotator.Save(outputPath);
```
## Steg 6: Visa meddelande om framgång
Visa ett meddelande som bekräftar att dokumentet har sparats.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats
I den här handledningen har vi lärt oss hur man lägger till en polylinjeannotering i ett dokument med GroupDocs.Annotation för .NET. Den här funktionen förbättrar samarbete och dokumentgranskningsprocesser, vilket gör det enklare för användare att kommunicera feedback och förslag effektivt.
## Vanliga frågor
### Är GroupDocs.Annotation för .NET kompatibel med alla dokumentformat?
GroupDocs.Annotation för .NET stöder populära dokumentformat som PDF och Microsoft Office-format inklusive Word, Excel och PowerPoint.
### Kan jag anpassa utseendet på annoteringar?
Ja, du kan anpassa olika egenskaper för annoteringar, såsom färg, opacitet, stil och bredd, så att de passar dina behov.
### Erbjuder GroupDocs.Annotation för .NET en gratis provperiod?
Ja, du kan få en gratis provversion av GroupDocs.Annotation för .NET genom att besöka [den här länken](https://releases.groupdocs.com/).
### Var kan jag hitta dokumentation för GroupDocs.Annotation för .NET?
Du hittar dokumentationen för GroupDocs.Annotation för .NET [här](https://tutorials.groupdocs.com/annotation/net/).
### Hur kan jag få support för problem eller frågor relaterade till GroupDocs.Annotation för .NET?
Du kan få support genom att besöka GroupDocs.Annotation-forumet. [här](https://forum.groupdocs.com/c/annotation/10).