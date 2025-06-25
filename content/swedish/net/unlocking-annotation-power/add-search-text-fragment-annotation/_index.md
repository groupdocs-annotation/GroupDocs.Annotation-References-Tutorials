---
"description": "Utforska kraften hos GroupDocs.Annotation för .NET och lägg enkelt till dokumentannoteringsfunktioner i dina applikationer."
"linktitle": "Lägg till annotering av söktextfragment i dokument"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg till annotering av söktextfragment i dokument"
"url": "/sv/net/unlocking-annotation-power/add-search-text-fragment-annotation/"
"weight": 20
---

# Lägg till annotering av söktextfragment i dokument

## Introduktion
Inom .NET-utveckling framstår GroupDocs.Annotation som ett kraftfullt verktyg för att sömlöst kommentera dokument. Oavsett om du är en erfaren utvecklare eller precis har börjat använda .NET, kommer den här omfattande handledningen att guida dig genom grunderna i att använda GroupDocs.Annotation för .NET, från att importera namnrymder till att bemästra komplikationerna med att lägga till annoteringar i söktextfragment i dina dokument.
## Introduktion
GroupDocs.Annotation för .NET ger utvecklare möjlighet att enkelt integrera dokumentannoteringsfunktioner i sina applikationer. Med sitt intuitiva API och robusta funktioner kan utvecklare annotera olika dokumentformat, inklusive PDF-filer, Microsoft Office-dokument, bilder och mer.
## Förkunskapskrav
Innan du börjar med GroupDocs.Annotation för .NET, se till att du har följande förutsättningar på plats:

## Importera namnrymder
Importera först de namnrymder som behövs för att komma åt GroupDocs.Annotation-klasser och -metoder i ditt .NET-projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Steg 1: Definiera utmatningsväg
Börja med att definiera utdatasökvägen där det kommenterade dokumentet ska sparas:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Initiera annotatorn
Initiera sedan en instans av `Annotator` klassen genom att ange sökvägen till dokumentet du vill annotera:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Steg 3: Skapa en annotering för söktextfragment
Skapa en `SearchTextFragment` objekt med önskade egenskaper, såsom text att söka efter, teckenstorlek, teckensnittsfamilj, teckenfärg och bakgrundsfärg:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## Steg 4: Lägg till annotering
Lägg till den skapade anteckningen för söktextfragmentet i dokumentet med hjälp av `Add` annotatorns metod:
```csharp
annotator.Add(searchText);
```
## Steg 5: Spara kommenterat dokument
Spara det kommenterade dokumentet till den angivna utdatasökvägen:
```csharp
annotator.Save(outputPath);
```
## Steg 6: Visa meddelande om framgång
Informera användaren om att dokumentet har sparats:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats
Sammanfattningsvis förenklar GroupDocs.Annotation för .NET processen att lägga till annoteringar i dokument, vilket förbättrar samarbete och dokumentgranskningsprocesser. Genom att följa stegen som beskrivs i den här guiden kan du sömlöst integrera dokumentannoteringsfunktioner i dina .NET-applikationer.
## Vanliga frågor
### Är GroupDocs.Annotation kompatibel med alla dokumentformat?
Ja, GroupDocs.Annotation stöder en mängd olika dokumentformat, inklusive PDF-filer, Microsoft Office-dokument, bilder och mer.
### Kan jag anpassa utseendet på annoteringar?
Absolut! GroupDocs.Annotation erbjuder omfattande anpassningsalternativ för annoteringar, vilket gör att du kan justera egenskaper som teckenstorlek, färg och stil.
### Finns det en gratis provversion av GroupDocs.Annotation?
Ja, du kan få tillgång till en gratis provperiod av GroupDocs.Annotation för att utforska dess funktioner och möjligheter innan du gör ett köp. [här](https://releases.groupdocs.com/)..
### Var kan jag hitta support för GroupDocs.Annotation?
För support och hjälp med GroupDocs.Annotation kan du besöka GroupDocs [forum](https://forum.groupdocs.com/c/annotation/10) tillägnad annoteringsrelaterade frågor och diskussioner.
### Hur får jag en tillfällig licens för GroupDocs.Annotation?
Du kan skaffa en tillfällig licens för GroupDocs.Annotation via GroupDocs. [webbplats](https://purchase.groupdocs.com/temporary-license/), vilket gör att du kan utvärdera produkten fullt ut.