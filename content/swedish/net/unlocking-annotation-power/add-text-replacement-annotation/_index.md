---
title: Lägg till textersättningsanteckning till dokumentet
linktitle: Lägg till textersättningsanteckning till dokumentet
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du lägger till textersättningskommentarer till dina .NET-dokument utan ansträngning med GroupDocs.Annotation för .NET. Förbättra dina dokumenthanteringsmöjligheter.
weight: 24
url: /sv/net/unlocking-annotation-power/add-text-replacement-annotation/
---

# Lägg till textersättningsanteckning till dokumentet

## Introduktion
I den här handledningen guidar vi dig genom processen att lägga till en textersättningsanteckning till dina dokument med hjälp av GroupDocs.Annotation för .NET. Detta kraftfulla bibliotek låter utvecklare manipulera och kommentera olika typer av dokument programmatiskt. I slutet av denna handledning kommer du att vara utrustad med kunskapen för att sömlöst integrera textersättningsanteckningar i dina .NET-program.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar installerade:
### 1. .NET Framework installerat
Se till att du har .NET Framework installerat på din utvecklingsmaskin. Du kan ladda ner den från Microsofts webbplats.
### 2. GroupDocs.Annotation för .NET Library
 Ladda ner och installera GroupDocs.Annotation for .NET-biblioteket från[hemsida](https://releases.groupdocs.com/annotation/net/). Detta bibliotek tillhandahåller de nödvändiga verktygen och funktionerna för att arbeta med anteckningar i olika dokumentformat.
### 3. Inställning av utvecklingsmiljö
Konfigurera din föredragna utvecklingsmiljö, som Visual Studio, för att skapa och köra .NET-applikationer.

## Importera namnområden
Innan vi dyker in i kodningsdelen, låt oss importera de nödvändiga namnrymden som krävs för att arbeta med GroupDocs.Annotation för .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## Steg 1: Definiera utdatasökväg
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Här definierar vi utmatningsvägen där det kommenterade dokumentet ska sparas.
## Steg 2: Initiera Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Anteckningskoden kommer att placeras här
}
```
Vi initierar Annotator-objektet genom att ange indatadokumentet ("input.pdf") i ett användningsblock för att säkerställa korrekt avyttring av resurser.
## Steg 3: Skapa ersättningsanteckning
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
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
    },
    TextToReplace = "replaced text"
};
```
Här skapar vi ett ReplacementAnnotation-objekt med olika egenskaper som skapelsedatum, teckensnittsfärg, meddelande, opacitet, sidnummer, bakgrundsfärg, punkter (koordinater), svar (kommentarer) och texten som ska ersättas.
## Steg 4: Lägg till anteckning
```csharp
annotator.Add(replacement);
```
Vi lägger till den skapade ersättningsanteckningen till kommentatorn.
## Steg 5: Spara dokument
```csharp
annotator.Save(outputPath);
```
Slutligen sparar vi det kommenterade dokumentet till den angivna utmatningsvägen.
## Steg 6: Visa framgångsmeddelande
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Ett framgångsrikt meddelande visas som indikerar att dokumentet har sparats.

## Slutsats
I den här handledningen har vi täckt processen att lägga till textersättningskommentarer till dokument med GroupDocs.Annotation för .NET. Genom att följa steg-för-steg-guiden och förstå förutsättningarna kan du enkelt integrera denna funktionalitet i dina .NET-applikationer.
## FAQ's
### Kan jag kommentera dokument i olika format med GroupDocs.Annotation för .NET?
Ja, GroupDocs.Annotation för .NET stöder annotering av olika dokumentformat som PDF, DOCX, PPTX, XLSX och mer.
### Är GroupDocs.Annotation för .NET lämplig för både skrivbords- och webbapplikationer?
Ja, GroupDocs.Annotation för .NET kan användas i både skrivbords- och webbapplikationer, vilket ger flexibilitet för utvecklare.
### Kan jag anpassa utseendet på anteckningar som lagts till med GroupDocs.Annotation för .NET?
Absolut, du kan anpassa utseendet på kommentarer genom att ändra egenskaper som färg, opacitet, teckensnitt, etc.
### Erbjuder GroupDocs.Annotation for .NET stöd för samarbetande annoteringsfunktioner?
Ja, GroupDocs.Annotation för .NET tillhandahåller funktioner för gemensamma kommentarer, vilket gör att flera användare kan kommentera dokument samtidigt.
### Finns det en gratis testversion tillgänglig för GroupDocs.Annotation för .NET?
Ja, du kan använda en gratis provversion av GroupDocs.Annotation för .NET från[hemsida](https://releases.groupdocs.com/).