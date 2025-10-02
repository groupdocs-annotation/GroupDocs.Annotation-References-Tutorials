---
"description": "Leer hoe u tekstonderstreping aan documenten toevoegt met GroupDocs.Annotation voor .NET. Verbeter moeiteloos samenwerking en communicatie."
"linktitle": "Tekstonderstreping toevoegen aan document"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "Tekstonderstreping toevoegen aan document"
"url": "/nl/net/unlocking-annotation-power/add-text-underline-annotation/"
type: docs
"weight": 27
---

# Tekstonderstreping toevoegen aan document

## Invoering
In deze tutorial laten we zien hoe je een tekstonderstreping aan een document toevoegt met behulp van GroupDocs.Annotation voor .NET. Tekstonderstreping kan handig zijn om specifieke delen van een document te benadrukken, zoals belangrijke passages of hoofdpunten.
## Vereisten
Voordat we beginnen, moet u ervoor zorgen dat de volgende vereisten zijn geïnstalleerd:
1. GroupDocs.Annotation voor .NET: Download en installeer GroupDocs.Annotation voor .NET van [hier](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Zorg ervoor dat .NET Framework op uw systeem is geïnstalleerd.

## Naamruimten importeren
Laten we eerst de benodigde naamruimten in ons project importeren:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Laten we het voorbeeld nu opsplitsen in meerdere stappen:
## Stap 1: Uitvoerpad definiëren
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
In deze stap definiëren we het uitvoerpad waar het geannoteerde document wordt opgeslagen.
## Stap 2: Annotator initialiseren
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Hier initialiseren we een instantie van de `Annotator` klasse door het pad van het invoerdocument op te geven.
## Stap 3: Onderstreep-annotatie maken
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // werkt alleen ondersteunde Word- en PDF-documenten
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
Deze stap omvat het maken van een `UnderlineAnnotation` object met verschillende eigenschappen, zoals letterkleur, bericht, dekking, paginanummer, achtergrondkleur, onderstrepingskleur, punten en antwoorden.
## Stap 4: Annotatie toevoegen aan document
```csharp
annotator.Add(underline);
```
Hier voegen we de onderstrepingsannotatie toe aan het document.
## Stap 5: Geannoteerd document opslaan
```csharp
annotator.Save(outputPath);
```
Ten slotte slaan we het geannoteerde document op in het opgegeven uitvoerpad.

## Conclusie
In deze tutorial hebben we geleerd hoe je een tekstonderstreping aan een document toevoegt met GroupDocs.Annotation voor .NET. Deze krachtige bibliotheek biedt diverse annotatieopties om de samenwerking en communicatie binnen documenten te verbeteren.
## Veelgestelde vragen
### Kan ik het uiterlijk van de onderstrepingsannotatie aanpassen?
Ja, u kunt eigenschappen zoals kleur, dekking en positie naar uw wensen aanpassen.
### Is GroupDocs.Annotation compatibel met verschillende documentformaten?
Ja, GroupDocs.Annotation ondersteunt een breed scala aan documentformaten, waaronder Word en PDF.
### Kan ik meerdere aantekeningen aan één document toevoegen?
Jazeker, met GroupDocs.Annotation kunt u meerdere annotaties van verschillende typen aan een document toevoegen.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Annotation?
Ja, u kunt de gratis proefversie openen via [hier](https://releases.groupdocs.com/).
### Waar kan ik ondersteuning krijgen voor GroupDocs.Annotation?
U kunt ondersteuning krijgen via het GroupDocs.Annotation communityforum [hier](https://forum.groupdocs.com/c/annotation/10).