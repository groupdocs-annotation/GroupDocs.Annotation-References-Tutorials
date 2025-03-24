---
title: Lägg till anteckning om söktextfragment i dokumentet
linktitle: Lägg till anteckning om söktextfragment i dokumentet
second_title: GroupDocs.Annotation .NET API
description: Utforska kraften med GroupDocs.Annotation för .NET och lägg enkelt till dokumentkommentarfunktioner till dina applikationer.
weight: 20
url: /sv/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---

# Lägg till anteckning om söktextfragment i dokumentet

## Introduktion
Inom området .NET-utveckling framstår GroupDocs.Annotation som ett kraftfullt verktyg för att sömlöst kommentera dokument. Oavsett om du är en erfaren utvecklare eller bara kliver in i .NET-världen, kommer den här omfattande handledningen att leda dig genom det väsentliga i att använda GroupDocs.Annotation för .NET, från att importera namnrymder till att bemästra krångligheterna med att lägga till anteckningar för söktextfragment till din dokument.
## Introduktion
GroupDocs.Annotation för .NET ger utvecklare möjlighet att integrera dokumentkommentarer i sina applikationer utan ansträngning. Med sitt intuitiva API och robusta funktioner kan utvecklare kommentera olika dokumentformat, inklusive PDF-filer, Microsoft Office-dokument, bilder och mer.
## Förutsättningar
Innan du dyker in i GroupDocs.Annotation för .NET, se till att du har följande förutsättningar:

## Importera namnområden
Importera först de nödvändiga namnområdena för att komma åt GroupDocs.Annotation-klasser och metoder i ditt .NET-projekt:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Steg 1: Definiera utdatasökväg
Börja med att definiera utdatabanan där det kommenterade dokumentet ska sparas:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Steg 2: Initiera Annotator
 Initiera sedan en instans av`Annotator` klass genom att ange sökvägen till dokumentet du vill kommentera:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Steg 3: Skapa söktextfragmentanteckning
 Skapa en`SearchTextFragment` objekt med önskade egenskaper, såsom text att söka efter, teckenstorlek, teckensnittsfamilj, teckensnittsfärg och bakgrundsfärg:
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
## Steg 4: Lägg till anteckning
 Lägg till anteckningen för det skapade söktextfragmentet till dokumentet med hjälp av`Add` annotatorns metod:
```csharp
annotator.Add(searchText);
```
## Steg 5: Spara kommenterat dokument
Spara det kommenterade dokumentet till den angivna utdatasökvägen:
```csharp
annotator.Save(outputPath);
```
## Steg 6: Visa framgångsmeddelande
Informera användaren om att dokumentet har sparats:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats
Sammanfattningsvis förenklar GroupDocs.Annotation för .NET processen att lägga till kommentarer till dokument, vilket förbättrar samarbets- och dokumentgranskningsprocesser. Genom att följa stegen som beskrivs i den här guiden kan du sömlöst integrera funktioner för dokumentkommentarer i dina .NET-applikationer.
## FAQ's
### Är GroupDocs.Annotation kompatibel med alla dokumentformat?
Ja, GroupDocs.Annotation stöder ett brett utbud av dokumentformat, inklusive PDF-filer, Microsoft Office-dokument, bilder och mer.
### Kan jag anpassa utseendet på kommentarer?
Absolut! GroupDocs.Annotation erbjuder omfattande anpassningsalternativ för kommentarer, så att du kan justera egenskaper som teckenstorlek, färg och stil.
### Finns det en gratis testversion tillgänglig för GroupDocs.Annotation?
 Ja, du kan få tillgång till en kostnadsfri provversion av GroupDocs.Annotation för att utforska dess funktioner och möjligheter innan du gör ett köp[här](https://releases.groupdocs.com/)..
### Var kan jag hitta support för GroupDocs.Annotation?
 För support och hjälp med GroupDocs.Annotation kan du besöka GroupDocs[forum](https://forum.groupdocs.com/c/annotation/10) tillägnad anteckningsrelaterade frågor och diskussioner.
### Hur får jag en tillfällig licens för GroupDocs.Annotation?
 Du kan skaffa en tillfällig licens för GroupDocs.Annotation genom GroupDocs[hemsida](https://purchase.groupdocs.com/temporary-license/), vilket gör att du kan utvärdera produkten fullständigt.