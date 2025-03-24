---
title: Lägg till punktkommentar till dokument
linktitle: Lägg till punktkommentar till dokument
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du lägger till punktkommentarer till PDF-filer med GroupDocs.Annotation för .NET. Steg-för-steg-guide för sömlös integration.
weight: 17
url: /sv/net/unlocking-annotation-power/add-point-annotation/
---

# Lägg till punktkommentar till dokument

## Introduktion
GroupDocs.Annotation för .NET är ett kraftfullt verktyg som gör det möjligt för utvecklare att lägga till olika typer av kommentarer till dokument programmatiskt. I den här handledningen kommer vi att fokusera på att lägga till en punktkommentar till ett dokument med C#.
## Förutsättningar
Innan vi börjar, se till att du har följande:
1. Grundläggande förståelse för programmeringsspråket C#.
2. Visual Studio installerat på ditt system.
3.  GroupDocs.Annotation för .NET-biblioteket installerat. Du kan ladda ner den från[här](https://releases.groupdocs.com/annotation/net/).

## Importera nödvändiga namnområden
För att komma igång måste du importera de nödvändiga namnrymden till ditt C#-projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Steg 1: Definiera utdatasökväg
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
I det här steget definierar vi utmatningsvägen där det kommenterade dokumentet ska sparas.
## Steg 2: Initiera Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Här initierar vi`Annotator` objekt med inmatningsdokumentet ("input.pdf").
## Steg 3: Skapa punktanteckning
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
 I detta steg skapar vi en`PointAnnotation` objekt och ange dess egenskaper såsom position, meddelande, sidnummer och svar.
## Steg 4: Lägg till anteckning
```csharp
annotator.Add(point);
```
Här lägger vi till den skapade punktanteckningen i dokumentet.
## Steg 5: Spara dokument
```csharp
annotator.Save(outputPath);
```
Slutligen sparar vi det kommenterade dokumentet till den angivna utmatningsvägen.

## Slutsats
I den här handledningen har vi lärt oss hur man lägger till en punktkommentar till ett dokument med GroupDocs.Annotation för .NET. Med detta kraftfulla bibliotek kan du förbättra dina dokumenthanteringsprogram genom att inkludera anteckningsfunktioner.
## FAQ's
### Är GroupDocs.Annotation for .NET kompatibelt med alla dokumentformat?
Ja, GroupDocs.Annotation för .NET stöder ett brett utbud av dokumentformat inklusive PDF, Microsoft Word, Excel, PowerPoint och mer.
### Kan jag anpassa utseendet på kommentarer?
Absolut! GroupDocs.Annotation för .NET ger omfattande alternativ för att anpassa utseendet på annoteringar för att passa ditt programs behov.
### Finns det en gratis testversion tillgänglig för GroupDocs.Annotation för .NET?
 Ja, du kan utnyttja en gratis provperiod från[här](https://releases.groupdocs.com/).
### Hur kan jag få support för eventuella problem eller frågor relaterade till GroupDocs.Annotation for .NET?
 Du kan få support från GroupDocs.Annotation-forumet[här](https://forum.groupdocs.com/c/annotation/10).
### Kan jag få en tillfällig licens för teständamål?
 Ja, du kan få en tillfällig licens från[här](https://purchase.groupdocs.com/temporary-license/).