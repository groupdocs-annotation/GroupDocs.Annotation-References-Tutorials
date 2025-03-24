---
title: Lägg till bildkommentar till dokument (lokal sökväg)
linktitle: Lägg till bildkommentar till dokument (lokal sökväg)
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du lägger till bildkommentarer till dokument med GroupDocs.Annotation för .NET. Förbättra dokumentbehandlingskapaciteten med lätthet.
weight: 14
url: /sv/net/unlocking-annotation-power/add-image-annotation-local-path/
---

# Lägg till bildkommentar till dokument (lokal sökväg)

## Introduktion
GroupDocs.Annotation för .NET är ett kraftfullt bibliotek som gör det möjligt för utvecklare att lägga till olika typer av kommentarer till dokument programmässigt. I den här handledningen kommer vi att lära oss hur du lägger till bildkommentarer till ett dokument med hjälp av en lokal sökväg.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar:
1. Grundläggande kunskaper i programmeringsspråket C#.
2. Visual Studio installerat på ditt system.
3. GroupDocs.Annotation för .NET-biblioteket installerat eller refererat till i ditt projekt.
4. Ett inmatningsdokument (t.ex. PDF) och en bildfil för anteckning.
## Importera namnområden
Först måste du importera de nödvändiga namnområdena till din C#-fil. Dessa namnrymder ger åtkomst till de klasser och metoder som krävs för att arbeta med GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Steg 1: Definiera utdatasökväg
Definiera utdatavägen där det kommenterade dokumentet ska sparas.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Initiera Annotator
Initiera annotatorn genom att ange sökvägen till inmatningsdokumentet.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Anteckningskoden går här
}
```
## Steg 3: Skapa bildkommentarer
 Skapa en instans av`ImageAnnotation`klass och ange dess egenskaper som position, opacitet, sidnummer och bildsökväg.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## Steg 4: Lägg till anteckning
 Lägg till den skapade bildkommentaren till dokumentet med hjälp av`Add` annotatorns metod.
```csharp
annotator.Add(image);
```
## Steg 5: Spara dokument
Spara det kommenterade dokumentet i utmatningsvägen.
```csharp
annotator.Save(outputPath);
```
## Steg 6: Visa utdatasökväg
Visa ett meddelande som anger att dokumentet har sparats och platsen för utdatafilen.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats
I den här handledningen har vi lärt oss hur man lägger till bildkommentarer till ett dokument med GroupDocs.Annotation för .NET. Genom att följa dessa enkla steg kan du förbättra dina dokumentbearbetningsmöjligheter med kraftfulla anteckningsfunktioner.
## FAQ's
### Kan jag kommentera andra dokument än PDF?
Ja, GroupDocs.Annotation stöder olika dokumentformat inklusive Word, Excel, PowerPoint och mer.
### Är GroupDocs.Annotation kompatibel med .NET Core?
Ja, GroupDocs.Annotation är kompatibel med både .NET Framework och .NET Core.
### Kan jag anpassa utseendet på kommentarer?
Absolut, du kan anpassa utseendet, storleken, färgen och andra egenskaper för anteckningar enligt dina krav.
### Ger GroupDocs.Annotation stöd för samarbetskommentarer?
Ja, GroupDocs.Annotation erbjuder gemensamma annoteringsfunktioner som gör att flera användare kan kommentera dokument samtidigt.
### Var kan jag hitta ytterligare hjälp eller stöd?
Du kan besöka forumet GroupDocs.Annotation för hjälp och stöd från communityn.