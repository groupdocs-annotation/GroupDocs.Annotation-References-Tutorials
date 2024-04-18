---
title: Laddar kommenterad dokumentversion
linktitle: Laddar kommenterad dokumentversion
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du enkelt laddar kommenterade dokumentversioner med GroupDocs.Annotation för .NET. Förenkla samarbets- och granskningsprocesser.
type: docs
weight: 16
url: /sv/net/document-loading-essentials/loading-annotated-document-version/
---
## Introduktion
dagens digitala tidsålder har dokumentkommentarer blivit ett viktigt verktyg för samarbete, granskning och feedback i olika branscher. Oavsett om du är en utvecklare som integrerar anteckningsfunktioner i din applikation eller en användare som vill utnyttja dessa funktioner, erbjuder GroupDocs.Annotation för .NET en kraftfull lösning. I den här handledningen kommer vi att fördjupa oss i processen att ladda kommenterade dokumentversioner med GroupDocs.Annotation för .NET.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar på plats:
### 1. Installera GroupDocs.Annotation för .NET
 Du kan ladda ner de nödvändiga filerna från[släpper sida](https://releases.groupdocs.com/annotation/net/). Följ installationsinstruktionerna för att ställa in biblioteket i din .NET-miljö.
### 2. Skaffa ett dokument med anteckningar
För den här handledningen behöver du ett dokument med kommentarer. Se till att du har ett kompatibelt dokumentformat (t.ex. PDF) som innehåller anteckningar som du vill ladda.

## Importera namnområden
För att kickstarta processen måste du importera de nödvändiga namnrymden till ditt projekt. Dessa namnutrymmen ger åtkomst till funktionerna i GroupDocs.Annotation för .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


Nu när vi har täckt förutsättningarna och import av namnutrymmen, låt oss dyka in i den steg-för-steg-process att läsa in kommenterade dokumentversioner med GroupDocs.Annotation för .NET.
## Steg 1: Definiera utdatasökväg
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Ange laddningsalternativ
```csharp
LoadOptions loadOptions = new LoadOptions { Version = "FIRST" };
```
## Steg 3: Initiera Annotator
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf", loadOptions))
```
## Steg 4: Hämta kommentarer
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
I den här handledningen har vi utforskat hur man laddar annoterade dokumentversioner med GroupDocs.Annotation för .NET. Genom att följa den steg-för-steg-guide och utnyttja funktionerna i detta kraftfulla bibliotek kan du sömlöst integrera dokumentkommentarsfunktioner i dina .NET-applikationer.
## FAQ's
### Kan jag kommentera dokument i olika format med GroupDocs.Annotation för .NET?
Ja, GroupDocs.Annotation stöder att kommentera dokument i format som PDF, DOCX, PPTX, XLSX och mer.
### Finns det en gratis testversion tillgänglig för GroupDocs.Annotation för .NET?
 Ja, du kan komma åt den kostnadsfria testversionen från[här](https://releases.groupdocs.com/).
### Var kan jag hitta dokumentation för GroupDocs.Annotation för .NET?
 Du kan hänvisa till den detaljerade dokumentationen[här](https://reference.groupdocs.com/annotation/net/).
### Hur kan jag få en tillfällig licens för GroupDocs.Annotation för .NET?
 Du kan skaffa en tillfällig licens från[den här länken](https://purchase.groupdocs.com/temporary-license/).
### Var kan jag söka support eller ställa frågor om GroupDocs.Annotation för .NET?
 Du kan besöka forumet GroupDocs.Annotation[här](https://forum.groupdocs.com/c/annotation/10).