---
title: Lägg bildkommentar över text
linktitle: Lägg bildkommentar över text
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du lägger till bildkommentarer över text i .NET med GroupDocs.Annotation för effektiv dokumenthantering och samarbete.
weight: 21
url: /sv/net/advanced-usage/put-image-annotation-over-text/
---

# Lägg bildkommentar över text

## Introduktion
en värld av .NET-utveckling erbjuder GroupDocs.Annotation en kraftfull lösning för att lägga till kommentarer till dokument, vilket gör samarbete och dokumenthantering effektivare. Ett vanligt krav är att sätta bildkommentarer över text, vilket kan göras sömlöst med GroupDocs.Annotation för .NET.
## Förutsättningar
Innan du går in i processen att lägga bildkommentarer över text med GroupDocs.Annotation för .NET, se till att du har följande:
1.  GroupDocs.Annotation for .NET Library: Ladda ner och installera biblioteket från[här](https://releases.groupdocs.com/annotation/net/).
2. Utvecklingsmiljö: Sätt upp en lämplig utvecklingsmiljö, som Visual Studio eller någon annan .NET IDE.
3. Dokument- och bildfiler: Förbered dokumentfilen (PDF, DOCX, etc.) och bildfilen du vill använda för kommentarer.
4. Grundläggande förståelse för C#: Bekantskap med programmeringsspråket C# är nödvändigt för att implementera kodavsnitten som tillhandahålls i denna handledning.

## Importera namnområden
Innan du fortsätter med anteckningsprocessen, se till att du importerar de nödvändiga namnrymden i ditt C#-projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Steg 1: Definiera utdatasökväg
Definiera först utmatningsvägen där det kommenterade dokumentet ska sparas:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Steg 2: Initiera Annotator
 Initiera`Annotator` objekt genom att tillhandahålla indatadokumentets sökväg:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Anteckningskoden kommer hit
}
```
## Steg 3: Skapa bildkommentarer
 Skapa en`ImageAnnotation` objekt med önskade egenskaper som boxdimensioner, opacitet, sidnummer, bildsökväg och z-index:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## Steg 4: Lägg till anteckning
 Lägg till bildkommentaren till dokumentet med hjälp av`Add` metod för`Annotator` objekt:
```csharp
annotator.Add(image);
```
## Steg 5: Spara kommenterat dokument
Spara det kommenterade dokumentet till den angivna utdatasökvägen:
```csharp
annotator.Save(outputPath);
```
## Steg 6: Visa framgångsmeddelande
Visa ett framgångsmeddelande med sökvägen till det kommenterade dokumentet:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats
Sammanfattningsvis är det en enkel process att lägga till bildkommentarer över text i .NET-applikationer med GroupDocs.Annotation. Genom att följa den steg-för-steg-guide som finns i den här handledningen kan du effektivt kommentera dokument och förbättra samarbets- och dokumenthanteringsmöjligheterna i dina .NET-projekt.
## FAQ's
### Kan jag kommentera andra dokument än PDF-filer?
Ja, GroupDocs.Annotation stöder olika dokumentformat som DOCX, XLSX, PPTX och mer.
### Finns det en gratis testversion tillgänglig för GroupDocs.Annotation?
 Ja, du kan ladda ner en gratis testversion från[här](https://releases.groupdocs.com/).
### Hur kan jag få support för GroupDocs.Annotation?
 Du kan få support från GroupDocs.Annotation-gemenskapsforumet[här](https://forum.groupdocs.com/c/annotation/10).
### Behöver jag en tillfällig licens för teständamål?
 Ja, du kan få en tillfällig licens från[här](https://purchase.groupdocs.com/temporary-license/) för teständamål.
### Kan jag anpassa utseendet på kommentarer?
Ja, GroupDocs.Annotation erbjuder olika alternativ för att anpassa utseendet på kommentarer som färg, opacitet, teckenstorlek, etc.