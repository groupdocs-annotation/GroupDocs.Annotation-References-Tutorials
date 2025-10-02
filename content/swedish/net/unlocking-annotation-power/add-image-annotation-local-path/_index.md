---
"description": "Lär dig hur du lägger till bildannoteringar i dokument med GroupDocs.Annotation för .NET. Förbättra dokumentbehandlingsfunktionerna med lätthet."
"linktitle": "Lägg till bildannotering i dokument (lokal sökväg)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg till bildannotering i dokument (lokal sökväg)"
"url": "/sv/net/unlocking-annotation-power/add-image-annotation-local-path/"
type: docs
"weight": 14
---

# Lägg till bildannotering i dokument (lokal sökväg)

## Introduktion
GroupDocs.Annotation för .NET är ett kraftfullt bibliotek som låter utvecklare lägga till olika typer av annoteringar i dokument programmatiskt. I den här handledningen lär vi oss hur man lägger till bildannoteringar i ett dokument med hjälp av en lokal sökväg.
## Förkunskapskrav
Innan vi börjar, se till att du har följande förutsättningar:
1. Grundläggande kunskaper i programmeringsspråket C#.
2. Visual Studio installerat på ditt system.
3. GroupDocs.Annotation för .NET-biblioteket installerat eller handledningar i ditt projekt.
4. Ett indatadokument (t.ex. PDF) och en bildfil för annotering.
## Importera namnrymder
Först måste du importera de nödvändiga namnrymderna till din C#-fil. Dessa namnrymder ger åtkomst till de klasser och metoder som krävs för att arbeta med GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Steg 1: Definiera utmatningsväg
Definiera utdatasökvägen där det kommenterade dokumentet ska sparas.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Initiera annotatorn
Initiera annotatorn genom att ange sökvägen till indatadokumentet.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annoteringskoden placeras här
}
```
## Steg 3: Skapa bildannotering
Skapa en instans av `ImageAnnotation` klassen och ange dess egenskaper såsom position, opacitet, sidnummer och bildsökväg.
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
## Steg 4: Lägg till annotering
Lägg till den skapade bildannoteringen i dokumentet med hjälp av `Add` annotatorns metod.
```csharp
annotator.Add(image);
```
## Steg 5: Spara dokument
Spara det kommenterade dokumentet i utdatasökvägen.
```csharp
annotator.Save(outputPath);
```
## Steg 6: Visa utdataväg
Visa ett meddelande som anger att dokumentet har sparats och var utdatafilen finns.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats
den här handledningen har vi lärt oss hur man lägger till bildannoteringar i ett dokument med GroupDocs.Annotation för .NET. Genom att följa dessa enkla steg kan du förbättra dina dokumentbehandlingsmöjligheter med kraftfulla annoteringsfunktioner.
## Vanliga frågor
### Kan jag kommentera andra dokument än PDF?
Ja, GroupDocs.Annotation stöder olika dokumentformat, inklusive Word, Excel, PowerPoint med flera.
### Är GroupDocs.Annotation kompatibelt med .NET Core?
Ja, GroupDocs.Annotation är kompatibel med både .NET Framework och .NET Core.
### Kan jag anpassa utseendet på annoteringar?
Absolut, du kan anpassa utseende, storlek, färg och andra egenskaper för annoteringar efter dina behov.
### Har GroupDocs.Annotation stöd för gemensam annotering?
Ja, GroupDocs.Annotation erbjuder funktioner för gemensamma anteckningar som gör det möjligt för flera användare att anteckna dokument samtidigt.
### Var kan jag hitta ytterligare hjälp eller stöd?
Du kan besöka GroupDocs.Annotation-forumet för hjälp och stöd från communityn.