---
title: Roterande PDF-dokument
linktitle: Roterande PDF-dokument
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du enkelt roterar PDF-dokument med Groupdocs.Annotation för .NET. Förbättra effektiviteten i dokumenthanteringen.
type: docs
weight: 22
url: /sv/net/advanced-usage/rotating-pdf-documents/
---
## Introduktion
Att rotera PDF-dokument kan vara en avgörande uppgift när man hanterar filer som behöver ses eller bearbetas på annat sätt. I den här handledningen kommer vi att utforska hur man roterar PDF-dokument steg för steg med Groupdocs.Annotation för .NET.
## Förutsättningar
Innan du dyker in i handledningen, se till att du har följande förutsättningar:
1.  Groupdocs.Annotation for .NET Library: Se till att du har laddat ner och installerat Groupdocs.Annotation for .NET-biblioteket. Du kan ladda ner den från[här](https://releases.groupdocs.com/annotation/net/).
2. Grundläggande kunskaper om C#-programmering: Denna handledning förutsätter att du har en grundläggande förståelse för C#-programmeringsspråk och hur man arbetar med .NET-bibliotek.

## Importera namnområden
Först måste du importera de nödvändiga namnrymden till ditt C#-projekt för att komma åt funktionaliteten som tillhandahålls av Groupdocs.Annotation-biblioteket.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Steg 1: Ladda PDF-dokumentet
 Börja med att ladda PDF-dokumentet som du vill rotera med hjälp av`Annotator` klass.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Steg 2: Ställ in rotations- och bearbetningssidor
Ange rotationsvinkeln och de sidor du vill rotera. I det här exemplet kommer vi att rotera den första sidan 90 grader medurs.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Steg 3: Spara det roterade dokumentet
Spara det roterade PDF-dokumentet med de angivna ändringarna.
```csharp
annotator.Save("result.pdf");
```
## Steg 4: Visa bekräftelse
Informera användaren om att dokumentet har roterats.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Slutsats
Att rotera PDF-dokument är en grundläggande operation, och med Groupdocs.Annotation för .NET blir det enkelt och effektivt. Genom att följa stegen som beskrivs i denna handledning kan du enkelt rotera PDF-filer enligt dina krav.
## FAQ's
### Kan jag rotera flera sidor i ett PDF-dokument med Groupdocs.Annotation för .NET?
 Ja, du kan ange att flera sidor ska roteras genom att justera`ProcessPages` egendom i enlighet därmed.
### Är Groupdocs.Annotation for .NET kompatibel med alla versioner av .NET framework?
Groupdocs.Annotation for .NET stöder ett brett utbud av .NET framework-versioner, vilket säkerställer kompatibilitet för de flesta utvecklingsmiljöer.
### Ger Groupdocs.Annotation för .NET alternativ för att rotera PDF-dokument i olika riktningar?
Ja, du kan rotera PDF-dokument medurs, moturs eller i anpassade vinklar baserat på dina krav.
### Kan jag integrera Groupdocs.Annotation för .NET i mitt befintliga dokumenthanteringssystem?
Absolut, Groupdocs.Annotation för .NET erbjuder sömlösa integrationsalternativ, så att du enkelt kan förbättra dokumenthanteringskapaciteten.
### Finns det en testversion tillgänglig för Groupdocs.Annotation för .NET?
 Ja, du kan få en gratis testversion från[här](https://releases.groupdocs.com/).