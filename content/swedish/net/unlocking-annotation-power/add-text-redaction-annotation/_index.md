---
title: Lägg till textredigeringskommentar till dokument
linktitle: Lägg till textredigeringskommentar till dokument
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du lägger till textredigeringskommentarer till PDF-dokument med GroupDocs.Annotation för .NET. Skydda känslig information utan ansträngning.
type: docs
weight: 23
url: /sv/net/unlocking-annotation-power/add-text-redaction-annotation/
---
## Introduktion
Att lägga till en textredigeringsanteckning till ett dokument kan vara ett avgörande steg för att säkert hantera känslig information. GroupDocs.Annotation för .NET tillhandahåller en robust lösning för att uppnå detta sömlöst. I den här självstudien guidar vi dig genom processen att lägga till en textredigeringskommentar till ditt dokument steg för steg.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar på plats:
1.  GroupDocs.Annotation for .NET: Se till att du har installerat GroupDocs.Annotation for .NET-biblioteket. Du kan ladda ner den från[hemsida](https://releases.groupdocs.com/annotation/net/).
2. Utvecklingsmiljö: Konfigurera en utvecklingsmiljö med en .NET-kompatibel IDE som Visual Studio.

## Importera namnområden
Låt oss först importera de nödvändiga namnrymden till vårt projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Steg 1: Definiera utdatasökväg
Definiera utdatasökvägen där du vill spara det kommenterade dokumentet. Se till att den är tillgänglig och skrivbar.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Initiera Annotator
 Initiera annotatorn med sökvägen till inmatningsdokumentet. Byta ut`"input.pdf"` med sökvägen till ditt dokument.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Anteckningskoden kommer hit
}
```
## Steg 3: Skapa textredigeringskommentarer
 Skapa en`TextRedactionAnnotation`objekt med de egenskaper som krävs som t.ex`PageNumber`, `FontColor` , och`Points`. Anpassa anteckningen enligt dina krav.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
## Steg 4: Lägg till anteckning och spara
Lägg till den skapade anteckningen till dokumentet med hjälp av anteckningsskrivaren och spara det annoterade dokumentet i den angivna utmatningsvägen.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Steg 5: Kontrollera utdata
Slutligen bekräftar du att dokumentet har sparats på den angivna utmatningsvägen.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats
I den här handledningen har vi gått igenom processen att lägga till en textredigeringskommentar till ett dokument med GroupDocs.Annotation för .NET. Med dessa steg kan du nu säkert hantera känslig information i dina dokument.
## FAQ's
### Kan jag anpassa utseendet på textredigeringskommentaren?
Ja, du kan anpassa olika egenskaper som teckensnittsfärg, fyllningsfärg och opacitet för att passa dina krav.
### Finns det en testversion innan köp?
 Ja, du kan få tillgång till en gratis testversion från[hemsida](https://releases.groupdocs.com/).
### Hur kan jag få support om jag stöter på några problem?
 Du kan få support från GroupDocs.Annotation-gemenskapsforumet[här](https://forum.groupdocs.com/c/annotation/10).
### Behöver jag en tillfällig licens för teständamål?
 Ja, du kan få en tillfällig licens från[köpsidan](https://purchase.groupdocs.com/temporary-license/)för provning.
### Kan jag lägga till flera kommentarer till ett enda dokument?
Absolut, GroupDocs.Annotation låter dig lägga till olika typer av kommentarer och flera instanser till ett enda dokument.