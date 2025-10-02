---
"description": "Lär dig hur du lägger till bildannoteringar i dokument med GroupDocs.Annotation för .NET. Förbättra dokumenthanteringen med kraftfulla annoteringsfunktioner."
"linktitle": "Lägg till bildannotering i dokument (fjärrsökväg)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg till bildannotering i dokument (fjärrsökväg)"
"url": "/sv/net/unlocking-annotation-power/add-image-annotation-remote-path/"
type: docs
"weight": 15
---

# Lägg till bildannotering i dokument (fjärrsökväg)

## Introduktion
I den här handledningen går vi igenom processen att lägga till bildannoteringar i ett dokument med GroupDocs.Annotation för .NET. Det här biblioteket tillhandahåller kraftfulla verktyg för att kommentera olika typer av dokument programmatiskt.
## Förkunskapskrav
Innan vi börjar, se till att du har följande:
1. GroupDocs.Annotation för .NET: Ladda ner och installera biblioteket från [här](https://releases.groupdocs.com/annotation/net/).
2. Utvecklingsmiljö: Se till att du har en fungerande utvecklingsmiljö konfigurerad för .NET-utveckling.
3. Dokument: Förbered dokumentet du vill kommentera. I den här handledningen antar vi att du har ett PDF-dokument med namnet `input.pdf`.
4. Bild för annotering: Välj den bild du vill använda för annotering. Se till att du har bildens URL eller lokala sökväg redo.

## Importera namnrymder
Innan vi börjar koda, låt oss importera de nödvändiga namnrymderna:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Steg 1: Ställ in utmatningsväg
Definiera först utdatasökvägen där det kommenterade dokumentet ska sparas.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Initiera annotatorn
Skapa en instans av `Annotator` klass och ange indatadokumentet.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annoteringskoden kommer att placeras här
}
```
## Steg 3: Lägg till bildannotering
Nu ska vi lägga till bildannoteringen i dokumentet. Vi anger egenskaperna för bildannoteringen, såsom position, opacitet, sidnummer och bildsökväg.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Ange annoteringens position
    CreatedOn = DateTime.Now, // Ange skapandedatum
    Opacity = 0.7, // Ställ in opacitet (0 till 1)
    PageNumber = 0, // Ange sidnumret
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Ange bildens URL
};
annotator.Add(image); // Lägg till bildannoteringen
```
## Steg 4: Spara dokument
Spara det kommenterade dokumentet till den angivna utdatasökvägen.
```csharp
annotator.Save(outputPath);
```
## Steg 5: Visa utdataväg
Informera användaren om att dokumentet har sparats och visa utdatasökvägen.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats
I den här handledningen har vi lärt oss hur man lägger till bildannoteringar i ett dokument med GroupDocs.Annotation för .NET. Genom att följa dessa steg kan du förbättra dina dokumenthanteringsprogram med kraftfulla annoteringsfunktioner.
## Vanliga frågor
### Kan GroupDocs.Annotation användas med andra dokumentformat förutom PDF?
Ja, GroupDocs.Annotation stöder olika dokumentformat, inklusive Word, Excel, PowerPoint med flera.
### Är GroupDocs.Annotation kompatibelt med .NET Core?
Ja, GroupDocs.Annotation är kompatibel med både .NET Framework och .NET Core.
### Kan jag anpassa utseendet på annoteringar?
Ja, du kan anpassa utseendet på annoteringar, till exempel färg, opacitet och storlek.
### Har GroupDocs.Annotation stöd för samarbetsannoteringsfunktioner?
Ja, GroupDocs.Annotation erbjuder funktioner för samarbetsanteckningar för samarbete i realtid kring dokument.
### Finns det en testversion tillgänglig för testning?
Ja, du kan få en gratis provperiod av GroupDocs.Annotation från [här](https://releases.groupdocs.com/).