---
title: Lägg till kryssrutakomponent till PDF-dokument
linktitle: Lägg till kryssrutakomponent till PDF-dokument
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du lägger till en kryssrutekomponent till PDF-dokument med Groupdocs.Annotation för .NET. Förbättra dina PDF-filer med interaktiva element.
weight: 11
url: /sv/net/document-components/add-checkbox-component-to-pdf/
---

# Lägg till kryssrutakomponent till PDF-dokument

## Introduktion
I den här självstudien guidar vi dig genom processen att lägga till en kryssrutekomponent till ett PDF-dokument med Groupdocs.Annotation för .NET.
## Förutsättningar
Innan vi börjar, se till att du har följande:
1.  Groupdocs.Annotation för .NET SDK: Du kan ladda ner den från[här](https://releases.groupdocs.com/annotation/net/).
2. Utvecklingsmiljö: Se till att du har en .NET-utvecklingsmiljö inrättad.

## Importera namnområden
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
Låt oss nu dela upp exemplet i flera steg:
## Steg 1: Definiera utdatasökväg
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Här definierar vi utdatasökvägen där det ändrade PDF-dokumentet kommer att sparas.
## Steg 2: Initiera Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Initiera`Annotator` objekt genom att skicka sökvägen till PDF-dokumentet.
## Steg 3: Skapa kryssrutakomponent
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
 Skapa en`CheckBoxComponent` objekt och anpassa dess egenskaper som`Checked`, `Box` mått,`PenColor`, `Style`och lägg till några svar.
## Steg 4: Lägg till kryssrutakomponent
```csharp
annotator.Add(checkBox);
```
Lägg till den skapade kryssrutekomponenten till PDF-dokumentet.
## Steg 5: Spara dokument
```csharp
annotator.Save("result.pdf");
```
Spara det ändrade PDF-dokumentet med kryssrutan.
## Steg 6: Visa utdatasökväg
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Visa sökvägen där det ändrade PDF-dokumentet sparas.

## Slutsats
I den här handledningen har vi lärt oss hur man lägger till en kryssrutekomponent i ett PDF-dokument med Groupdocs.Annotation för .NET. Med denna kunskap kan du förbättra dina PDF-dokument med interaktiva element.
## FAQ's
### Kan jag anpassa utseendet på kryssrutan?
Ja, du kan anpassa olika egenskaper som färg, stil och storlek enligt dina krav.
### Är Groupdocs.Annotation for .NET lämplig för kommersiellt bruk?
Ja, Groupdocs.Annotation för .NET erbjuder kommersiella licenser för företag.
### Kan jag prova Groupdocs.Annotation för .NET innan jag köper?
 Ja, du kan utnyttja en gratis provperiod från[här](https://releases.groupdocs.com/).
### Var kan jag hitta support för Groupdocs.Annotation för .NET?
 Du kan hitta support och resurser på[Groupdocs forum](https://forum.groupdocs.com/c/annotation/10).
### Behöver jag en tillfällig licens för teständamål?
 Du kan få en tillfällig licens för att testa från[här](https://purchase.groupdocs.com/temporary-license/).