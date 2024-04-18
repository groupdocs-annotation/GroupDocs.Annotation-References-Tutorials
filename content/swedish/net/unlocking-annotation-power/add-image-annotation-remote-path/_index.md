---
title: Lägg till bildkommentar till dokument (fjärrsökväg)
linktitle: Lägg till bildkommentar till dokument (fjärrsökväg)
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du lägger till bildkommentarer till dokument med GroupDocs.Annotation för .NET. Förbättra dokumenthanteringen med kraftfulla anteckningsfunktioner.
type: docs
weight: 15
url: /sv/net/unlocking-annotation-power/add-image-annotation-remote-path/
---
## Introduktion
I den här handledningen går vi igenom processen att lägga till bildkommentarer till ett dokument med GroupDocs.Annotation för .NET. Detta bibliotek tillhandahåller kraftfulla verktyg för att annotera olika typer av dokument programmatiskt.
## Förutsättningar
Innan vi börjar, se till att du har följande:
1.  GroupDocs.Annotation for .NET: Ladda ner och installera biblioteket från[här](https://releases.groupdocs.com/annotation/net/).
2. Utvecklingsmiljö: Se till att du har en fungerande utvecklingsmiljö inrättad för .NET-utveckling.
3.  Dokument: Förbered dokumentet du vill kommentera. För denna handledning antar vi att du har ett PDF-dokument som heter`input.pdf`.
4. Bild för anteckning: Välj den bild du vill använda för anteckning. Se till att du har bildens URL eller den lokala sökvägen redo.

## Importera namnområden
Innan vi börjar koda, låt oss importera de nödvändiga namnrymden:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Steg 1: Ställ in utdatasökväg
Definiera först utmatningsvägen där det kommenterade dokumentet ska sparas.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Initiera Annotator
 Skapa en instans av`Annotator` klass och ange indatadokumentet.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Anteckningskoden kommer hit
}
```
## Steg 3: Lägg till bildkommentar
Låt oss nu lägga till bildkommentaren till dokumentet. Vi kommer att specificera egenskaperna för bildkommentaren som position, opacitet, sidnummer och bildsökväg.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Ange positionen för anteckningen
    CreatedOn = DateTime.Now, // Ställ in datum för skapande
    Opacity = 0.7, // Ställ in opacitet (0 till 1)
    PageNumber = 0, // Ange sidnummer
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Ange webbadressen till bilden
};
annotator.Add(image); // Lägg till bildkommentaren
```
## Steg 4: Spara dokument
Spara det kommenterade dokumentet till den angivna utmatningsvägen.
```csharp
annotator.Save(outputPath);
```
## Steg 5: Visa utdatasökväg
Informera användaren om den lyckade dokumentsparaoperationen och visa utmatningsvägen.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats
den här handledningen har vi lärt oss hur man lägger till bildkommentarer till ett dokument med GroupDocs.Annotation för .NET. Genom att följa dessa steg kan du förbättra dina dokumenthanteringsprogram med kraftfulla anteckningsfunktioner.
## FAQ's
### Kan GroupDocs.Annotation användas med andra dokumentformat än PDF?
Ja, GroupDocs.Annotation stöder olika dokumentformat inklusive Word, Excel, PowerPoint och mer.
### Är GroupDocs.Annotation kompatibel med .NET Core?
Ja, GroupDocs.Annotation är kompatibel med både .NET Framework och .NET Core.
### Kan jag anpassa utseendet på kommentarer?
Ja, du kan anpassa utseendet på kommentarer som färg, opacitet och storlek.
### Har GroupDocs.Annotation stöd för samverkande anteckningsfunktioner?
Ja, GroupDocs.Annotation erbjuder samverkande annoteringsfunktioner för samarbete i realtid om dokument.
### Finns det en testversion tillgänglig för testning?
 Ja, du kan få en gratis provversion av GroupDocs.Annotation från[här](https://releases.groupdocs.com/).