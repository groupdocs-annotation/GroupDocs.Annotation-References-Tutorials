---
title: Skapa förhandsgranskning utan kommentarer
linktitle: Skapa förhandsgranskning utan kommentarer
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du sömlöst integrerar funktioner för dokumentkommentarer i dina .NET-applikationer med hjälp av GroupDocs.Annotation for .NET.
type: docs
weight: 14
url: /sv/net/advanced-usage/generate-preview-without-comments/
---
## Introduktion
GroupDocs.Annotation for .NET är ett kraftfullt verktyg som gör att utvecklare kan integrera anteckningsfunktioner i sina .NET-applikationer sömlöst. Oavsett om du arbetar med ett dokumenthanteringssystem, en samarbetsplattform eller någon annan applikation som kräver funktioner för dokumentkommentarer, tillhandahåller GroupDocs.Annotation en omfattande uppsättning verktyg för att förbättra din applikations funktionalitet.
## Förutsättningar
Innan du börjar använda GroupDocs.Annotation för .NET, se till att du har ställt in följande förutsättningar:
### 1. Installera GroupDocs.Annotation för .NET
 För att börja måste du ladda ner och installera GroupDocs.Annotation för .NET. Du hittar nedladdningslänken[här](https://releases.groupdocs.com/annotation/net/). Följ installationsinstruktionerna i dokumentationen för en smidig installationsprocess.
### 2. Skaffa licens
 GroupDocs.Annotation for .NET kräver en licens för kommersiellt bruk. Du kan skaffa en licens från[här](https://purchase.groupdocs.com/buy) eller välja en tillfällig licens[här](https://purchase.groupdocs.com/temporary-license/) för teständamål.
### 3. Bekantskap med .NET Framework
Grundläggande kunskaper i .NET Framework och C# programmeringsspråk är avgörande för att effektivt kunna använda GroupDocs.Annotation för .NET.

## Importera namnområden
Nu när du har ställt in förutsättningarna, låt oss importera de nödvändiga namnrymden till din .NET-applikation.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

Följ dessa steg-för-steg-instruktioner för att skapa en förhandsvisning utan kommentarer med GroupDocs.Annotation for .NET:
## Steg 1: Initiera Annotator
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## Steg 2: Konfigurera förhandsgranskningsalternativ
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## Steg 3: Ange förhandsgranskningsformat och sidnummer
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## Steg 4: Inaktivera rendering av kommentarer
```csharp
    previewOptions.RenderComments = false;
```
## Steg 5: Skapa förhandsgranskning
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
När du har följt dessa steg kommer din .NET-applikation att kunna generera en förhandsvisning av de angivna sidorna från dokumentet utan att göra kommentarer.

## Slutsats
Att införliva anteckningsfunktioner i dina .NET-applikationer har aldrig varit enklare tack vare GroupDocs.Annotation för .NET. Genom att följa stegen som beskrivs i den här handledningen kan du sömlöst integrera funktioner för dokumentkommentarer i dina applikationer, vilket förbättrar samarbete och dokumenthantering.
## FAQ's
### Är GroupDocs.Annotation for .NET kompatibelt med alla dokumentformat?
GroupDocs.Annotation for .NET stöder ett brett utbud av dokumentformat, inklusive PDF, DOCX, PPTX, XLSX och mer.
### Kan jag anpassa utseendet på anteckningar som genereras med GroupDocs.Annotation för .NET?
Ja, GroupDocs.Annotation för .NET erbjuder omfattande anpassningsalternativ, vilket gör att du kan skräddarsy utseendet på anteckningar för att passa din applikations behov.
### Stöder GroupDocs.Annotation for .NET samarbete mellan flera användare?
Ja, GroupDocs.Annotation för .NET erbjuder gemensamma anteckningsfunktioner, vilket gör att flera användare kan kommentera dokument samtidigt.
### Finns teknisk support tillgänglig för GroupDocs.Annotation för .NET?
 Ja, teknisk support för GroupDocs.Annotation för .NET är tillgänglig via[supportforum](https://forum.groupdocs.com/c/annotation/10).
### Kan jag prova GroupDocs.Annotation för .NET gratis innan jag köper?
 Ja, du kan utforska funktionerna i GroupDocs.Annotation för .NET genom att ladda ner den kostnadsfria testversionen[här](https://releases.groupdocs.com/).