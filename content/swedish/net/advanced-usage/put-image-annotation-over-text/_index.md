---
"description": "Lär dig hur du lägger till bildannoteringar över text i .NET med GroupDocs.Annotation för effektiv dokumenthantering och samarbete."
"linktitle": "Lägg bildannotering över text"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg bildannotering över text"
"url": "/sv/net/advanced-usage/put-image-annotation-over-text/"
type: docs
"weight": 21
---

# Lägg bildannotering över text

## Introduktion
Inom .NET-utveckling erbjuder GroupDocs.Annotation en kraftfull lösning för att lägga till annoteringar i dokument, vilket effektiviserar samarbete och dokumenthantering. Ett vanligt krav är att lägga till bildannoteringar över text, vilket kan åstadkommas sömlöst med GroupDocs.Annotation för .NET.
## Förkunskapskrav
Innan du börjar med att lägga till bildannoteringar över text med GroupDocs.Annotation för .NET, se till att du har följande:
1. GroupDocs.Annotation för .NET-biblioteket: Ladda ner och installera biblioteket från [här](https://releases.groupdocs.com/annotation/net/).
2. Utvecklingsmiljö: Konfigurera en lämplig utvecklingsmiljö, till exempel Visual Studio eller någon annan .NET IDE.
3. Dokument- och bildfiler: Förbered dokumentfilen (PDF, DOCX, etc.) och bildfilen som du vill använda för anteckningar.
4. Grundläggande förståelse för C#: Bekantskap med programmeringsspråket C# är nödvändig för att implementera kodavsnitten som ges i den här handledningen.

## Importera namnrymder
Innan du fortsätter med annoteringsprocessen, se till att du importerar nödvändiga namnrymder i ditt C#-projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Steg 1: Definiera utmatningsväg
Definiera först utdatasökvägen där det kommenterade dokumentet ska sparas:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Steg 2: Initiera annotatorn
Initiera `Annotator` objekt genom att ange sökvägen till indatadokumentet:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annoteringskoden kommer att placeras här
}
```
## Steg 3: Skapa bildannotering
Skapa en `ImageAnnotation` objekt med önskade egenskaper såsom boxdimensioner, opacitet, sidnummer, bildsökväg och z-index:
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
## Steg 4: Lägg till annotering
Lägg till bildanteckningen i dokumentet med hjälp av `Add` metod för `Annotator` objekt:
```csharp
annotator.Add(image);
```
## Steg 5: Spara kommenterat dokument
Spara det kommenterade dokumentet till den angivna utdatasökvägen:
```csharp
annotator.Save(outputPath);
```
## Steg 6: Visa meddelande om framgång
Visa ett meddelande om att det lyckades med sökvägen till det kommenterade dokumentet:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats
Sammanfattningsvis är det en enkel process att lägga till bildannoteringar över text i .NET-applikationer med GroupDocs.Annotation. Genom att följa steg-för-steg-guiden i den här handledningen kan du effektivt annotera dokument och förbättra samarbete och dokumenthanteringsfunktioner i dina .NET-projekt.
## Vanliga frågor
### Kan jag kommentera andra dokument än PDF-filer?
Ja, GroupDocs.Annotation stöder olika dokumentformat som DOCX, XLSX, PPTX med flera.
### Finns det en gratis provversion av GroupDocs.Annotation?
Ja, du kan ladda ner en gratis testversion från [här](https://releases.groupdocs.com/).
### Hur kan jag få support för GroupDocs.Annotation?
Du kan få support från GroupDocs.Annotation-communityforumet [här](https://forum.groupdocs.com/c/annotation/10).
### Behöver jag en tillfällig licens för teständamål?
Ja, du kan få en tillfällig licens från [här](https://purchase.groupdocs.com/temporary-license/) för teständamål.
### Kan jag anpassa utseendet på annoteringar?
Ja, GroupDocs.Annotation erbjuder olika alternativ för att anpassa utseendet på annoteringar, såsom färg, opacitet, teckenstorlek etc.