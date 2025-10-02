---
"description": "Lär dig hur du lägger till textborttagningsanteckningar i PDF-dokument med GroupDocs.Annotation för .NET. Skydda känslig information utan ansträngning."
"linktitle": "Lägg till textborttagningsanteckning i dokument"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg till textborttagningsanteckning i dokument"
"url": "/sv/net/unlocking-annotation-power/add-text-redaction-annotation/"
type: docs
"weight": 23
---

# Lägg till textborttagningsanteckning i dokument

## Introduktion
Att lägga till en textborttagningsanteckning i ett dokument kan vara ett avgörande steg för att hantera känslig information på ett säkert sätt. GroupDocs.Annotation för .NET erbjuder en robust lösning för att uppnå detta smidigt. I den här handledningen guidar vi dig genom processen att lägga till en textborttagningsanteckning i ditt dokument steg för steg.
## Förkunskapskrav
Innan vi börjar, se till att du har följande förutsättningar på plats:
1. GroupDocs.Annotation för .NET: Se till att du har installerat GroupDocs.Annotation för .NET-biblioteket. Du kan ladda ner det från [webbplats](https://releases.groupdocs.com/annotation/net/).
2. Utvecklingsmiljö: Konfigurera en utvecklingsmiljö med en .NET-kompatibel IDE, till exempel Visual Studio.

## Importera namnrymder
Först, låt oss importera de nödvändiga namnrymderna till vårt projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Steg 1: Definiera utmatningsväg
Definiera utdatasökvägen där du vill spara det kommenterade dokumentet. Se till att den är tillgänglig och skrivbar.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Initiera annotatorn
Initiera annotatorn med sökvägen för inmatningsdokumentet. Ersätt `"input.pdf"` med sökvägen till ditt dokument.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annoteringskoden kommer att placeras här
}
```
## Steg 3: Skapa textborttagningsannotering
Skapa en `TextRedactionAnnotation` objekt med de nödvändiga egenskaperna, såsom `PageNumber`, `FontColor`och `Points`Anpassa anteckningen efter dina behov.
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
Lägg till den skapade anteckningen i dokumentet med hjälp av annotatorn och spara det annoterade dokumentet till den angivna utdatasökvägen.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Steg 5: Kontrollera utdata
Bekräfta slutligen att dokumentet har sparats till den angivna utdatasökvägen.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats
I den här handledningen har vi gått igenom processen att lägga till en textborttagningsanteckning i ett dokument med GroupDocs.Annotation för .NET. Med dessa steg kan du nu säkert hantera känslig information i dina dokument.
## Vanliga frågor
### Kan jag anpassa utseendet på textborttagningsanteckningen?
Ja, du kan anpassa olika egenskaper som teckenfärg, fyllningsfärg och opacitet efter dina behov.
### Finns det en testversion tillgänglig innan köp?
Ja, du kan få tillgång till en gratis testversion från [webbplats](https://releases.groupdocs.com/).
### Hur kan jag få support om jag stöter på några problem?
Du kan få support från GroupDocs.Annotation-communityforumet [här](https://forum.groupdocs.com/c/annotation/10).
### Behöver jag en tillfällig licens för teständamål?
Ja, du kan få ett tillfälligt körkort från [köpsida](https://purchase.groupdocs.com/temporary-license/) för testning.
### Kan jag lägga till flera anteckningar i ett enda dokument?
Absolut, GroupDocs.Annotation låter dig lägga till olika typer av anteckningar och flera instanser i ett enda dokument.