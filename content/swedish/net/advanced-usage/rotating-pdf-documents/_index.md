---
"description": "Lär dig hur du enkelt roterar PDF-dokument med Groupdocs.Annotation för .NET. Förbättra effektiviteten i dokumenthanteringen."
"linktitle": "Rotera PDF-dokument"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Rotera PDF-dokument"
"url": "/sv/net/advanced-usage/rotating-pdf-documents/"
type: docs
"weight": 22
---

# Rotera PDF-dokument

## Introduktion
Att rotera PDF-dokument kan vara en avgörande uppgift när man hanterar filer som behöver visas eller bearbetas på olika sätt. I den här handledningen utforskar vi hur man roterar PDF-dokument steg för steg med Groupdocs.Annotation för .NET.
## Förkunskapskrav
Innan du börjar med handledningen, se till att du har följande förkunskaper:
1. Groupdocs.Annotation för .NET-biblioteket: Se till att du har laddat ner och installerat Groupdocs.Annotation för .NET-biblioteket. Du kan ladda ner det från [här](https://releases.groupdocs.com/annotation/net/).
2. Grundläggande kunskaper i C#-programmering: Den här handledningen förutsätter att du har en grundläggande förståelse för programmeringsspråket C# och hur man arbetar med .NET-bibliotek.

## Importera namnrymder
Först måste du importera de nödvändiga namnrymderna till ditt C#-projekt för att få tillgång till funktionerna som tillhandahålls av Groupdocs.Annotation-biblioteket.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Steg 1: Ladda PDF-dokumentet
Börja med att ladda PDF-dokumentet som du vill rotera med hjälp av `Annotator` klass.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Steg 2: Ställ in rotations- och bearbetningssidor
Ange rotationsvinkeln och de sidor du vill rotera. I det här exemplet roterar vi den första sidan 90 grader medurs.
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
Att rotera PDF-dokument är en grundläggande åtgärd, och med Groupdocs.Annotation för .NET blir det enkelt och effektivt. Genom att följa stegen som beskrivs i den här handledningen kan du enkelt rotera PDF-filer enligt dina behov.
## Vanliga frågor
### Kan jag rotera flera sidor i ett PDF-dokument med Groupdocs.Annotation för .NET?
Ja, du kan ange att flera sidor ska roteras genom att justera `ProcessPages` egendom i enlighet därmed.
### Är Groupdocs.Annotation för .NET kompatibelt med alla versioner av .NET framework?
Groupdocs.Annotation för .NET stöder ett brett utbud av .NET Framework-versioner, vilket säkerställer kompatibilitet för de flesta utvecklingsmiljöer.
### Erbjuder Groupdocs.Annotation för .NET alternativ för att rotera PDF-dokument i olika riktningar?
Ja, du kan rotera PDF-dokument medurs, moturs eller i anpassade vinklar baserat på dina behov.
### Kan jag integrera Groupdocs.Annotation för .NET i mitt befintliga dokumenthanteringssystem?
Absolut, Groupdocs.Annotation för .NET erbjuder sömlösa integrationsalternativ, vilket gör att du enkelt kan förbättra dokumenthanteringsfunktionerna.
### Finns det en testversion tillgänglig för Groupdocs.Annotation för .NET?
Ja, du kan få en gratis testversion från [här](https://releases.groupdocs.com/).