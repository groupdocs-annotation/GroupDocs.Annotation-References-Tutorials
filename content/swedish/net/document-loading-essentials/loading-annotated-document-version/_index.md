---
"description": "Lär dig hur du enkelt laddar kommenterade dokumentversioner med GroupDocs.Annotation för .NET. Förenkla samarbete och granskningsprocesser."
"linktitle": "Läser in version av kommenterat dokument"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Läser in version av kommenterat dokument"
"url": "/sv/net/document-loading-essentials/loading-annotated-document-version/"
"weight": 16
---

# Läser in version av kommenterat dokument

## Introduktion
I dagens digitala tidsålder har dokumentannotering blivit ett viktigt verktyg för samarbete, granskning och feedback inom olika branscher. Oavsett om du är en utvecklare som integrerar annoteringsfunktioner i din applikation eller en användare som vill utnyttja dessa funktioner, erbjuder GroupDocs.Annotation för .NET en kraftfull lösning. I den här handledningen ska vi fördjupa oss i processen att ladda annoterade dokumentversioner med GroupDocs.Annotation för .NET.
## Förkunskapskrav
Innan vi börjar, se till att du har följande förutsättningar på plats:
### 1. Installera GroupDocs.Annotation för .NET
Du kan ladda ner nödvändiga filer från [utgivningssida](https://releases.groupdocs.com/annotation/net/)Följ installationsanvisningarna för att konfigurera biblioteket i din .NET-miljö.
### 2. Hämta ett dokument med anteckningar
För den här handledningen behöver du ett dokument med anteckningar. Se till att du har ett kompatibelt dokumentformat (t.ex. PDF) som innehåller anteckningarna som du vill ladda.

## Importera namnrymder
För att kickstarta processen måste du importera de namnrymder som krävs till ditt projekt. Dessa namnrymder ger åtkomst till funktionaliteten i GroupDocs.Annotation för .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


Nu när vi har gått igenom förutsättningarna och namnrymdsimporterna, låt oss dyka ner i den steg-för-steg-processen för att läsa in kommenterade dokumentversioner med GroupDocs.Annotation för .NET.
## Steg 1: Definiera utmatningsväg
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Ange laddningsalternativ
```csharp
LoadOptions loadOptions = new LoadOptions { Version = "FIRST" };
```
## Steg 3: Initiera annotatorn
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf", loadOptions))
```
## Steg 4: Hämta anteckningar
```csharp
var annotations = annotator.Get();
```
## Steg 5: Spara dokument med anteckningar
```csharp
annotator.Save(outputPath);
```
## Steg 6: Visa bekräftelsemeddelande
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats
I den här handledningen har vi utforskat hur man laddar kommenterade dokumentversioner med GroupDocs.Annotation för .NET. Genom att följa steg-för-steg-guiden och utnyttja funktionerna i detta kraftfulla bibliotek kan du sömlöst integrera dokumentannoteringsfunktioner i dina .NET-applikationer.
## Vanliga frågor
### Kan jag kommentera dokument i olika format med GroupDocs.Annotation för .NET?
Ja, GroupDocs.Annotation stöder kommentering av dokument i format som PDF, DOCX, PPTX, XLSX med flera.
### Finns det en gratis testversion av GroupDocs.Annotation för .NET?
Ja, du kan få tillgång till den kostnadsfria testversionen från [här](https://releases.groupdocs.com/).
### Var kan jag hitta dokumentation för GroupDocs.Annotation för .NET?
Du kan hänvisa till den detaljerade dokumentationen [här](https://tutorials.groupdocs.com/annotation/net/).
### Hur kan jag få en tillfällig licens för GroupDocs.Annotation för .NET?
Du kan få en tillfällig licens från [den här länken](https://purchase.groupdocs.com/temporary-license/).
### Var kan jag söka support eller ställa frågor om GroupDocs.Annotation för .NET?
Du kan besöka GroupDocs.Annotation-forumet [här](https://forum.groupdocs.com/c/annotation/10).