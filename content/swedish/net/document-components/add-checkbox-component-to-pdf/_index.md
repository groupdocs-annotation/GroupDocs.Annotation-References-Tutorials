---
"description": "Lär dig hur du lägger till en kryssrutekomponent i PDF-dokument med Groupdocs.Annotation för .NET. Förbättra dina PDF-filer med interaktiva element."
"linktitle": "Lägg till kryssrutekomponent i PDF-dokument"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg till kryssrutekomponent i PDF-dokument"
"url": "/sv/net/document-components/add-checkbox-component-to-pdf/"
type: docs
"weight": 11
---

# Lägg till kryssrutekomponent i PDF-dokument

## Introduktion
I den här handledningen guidar vi dig genom processen att lägga till en Checkbox-komponent i ett PDF-dokument med hjälp av Groupdocs.Annotation för .NET.
## Förkunskapskrav
Innan vi börjar, se till att du har följande:
1. Groupdocs.Annotation för .NET SDK: Du kan ladda ner den från [här](https://releases.groupdocs.com/annotation/net/).
2. Utvecklingsmiljö: Se till att du har en .NET-utvecklingsmiljö konfigurerad.

## Importera namnrymder
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
Nu ska vi dela upp exemplet i flera steg:
## Steg 1: Definiera utmatningsväg
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Här definierar vi utdatasökvägen där det modifierade PDF-dokumentet ska sparas.
## Steg 2: Initiera annotatorn
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Initiera `Annotator` objektet genom att skicka sökvägen till PDF-dokumentet.
## Steg 3: Skapa kryssrutekomponent
```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100),
    PenColor = 65535,
    Style = BoxStyle.Star,
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
    }
};
```
Skapa en `CheckBoxComponent` objekt och anpassa dess egenskaper som `Checked`, `Box` mått, `PenColor`, `Style`och lägg till några svar.
## Steg 4: Lägg till kryssrutekomponent
```csharp
annotator.Add(checkBox);
```
Lägg till den skapade kryssrutekomponenten i PDF-dokumentet.
## Steg 5: Spara dokument
```csharp
annotator.Save("result.pdf");
```
Spara det modifierade PDF-dokumentet med kryssrutekomponenten.
## Steg 6: Visa utdataväg
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Visa sökvägen där det ändrade PDF-dokumentet är sparat.

## Slutsats
I den här handledningen har vi lärt oss hur man lägger till en Checkbox-komponent i ett PDF-dokument med Groupdocs.Annotation för .NET. Med den här kunskapen kan du förbättra dina PDF-dokument med interaktiva element.
## Vanliga frågor
### Kan jag anpassa utseendet på kryssrutan?
Ja, du kan anpassa olika egenskaper som färg, stil och storlek efter dina behov.
### Är Groupdocs.Annotation för .NET lämplig för kommersiellt bruk?
Ja, Groupdocs.Annotation för .NET erbjuder kommersiella licenser för företag.
### Kan jag prova Groupdocs.Annotation för .NET innan jag köper?
Ja, du kan prova gratis från [här](https://releases.groupdocs.com/).
### Var kan jag hitta support för Groupdocs.Annotation för .NET?
Du kan hitta stöd och resurser på [Groupdocs-forum](https://forum.groupdocs.com/c/annotation/10).
### Behöver jag en tillfällig licens för teständamål?
Du kan få en tillfällig licens för testning från [här](https://purchase.groupdocs.com/temporary-license/).