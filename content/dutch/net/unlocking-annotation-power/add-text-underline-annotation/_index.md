---
title: Voeg tekstonderstrepingsannotatie toe aan document
linktitle: Voeg tekstonderstrepingsannotatie toe aan document
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u annotaties met tekstonderstrepingen aan documenten kunt toevoegen met GroupDocs.Annotation voor .NET. Verbeter moeiteloos de samenwerking en communicatie.
type: docs
weight: 27
url: /nl/net/unlocking-annotation-power/add-text-underline-annotation/
---
## Invoering
In deze zelfstudie doorlopen we het proces van het toevoegen van een tekstonderstrepingsannotatie aan een document met behulp van GroupDocs.Annotation voor .NET. Annotaties met tekstonderstrepingen kunnen handig zijn om specifieke delen van een document te benadrukken, zoals belangrijke passages of belangrijke punten.
## Vereisten
Voordat we beginnen, moet u ervoor zorgen dat de volgende vereisten zijn geïnstalleerd:
1.  GroupDocs.Annotation voor .NET: Download en installeer GroupDocs.Annotation voor .NET vanaf[hier](https://releases.groupdocs.com/annotation/net/).
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

Laten we het voorbeeld nu in meerdere stappen opsplitsen:
## Stap 1: Definieer het uitvoerpad
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
In deze stap definiëren we het uitvoerpad waar het geannoteerde document zal worden opgeslagen.
## Stap 2: Initialiseer Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Hier initialiseren we een exemplaar van de`Annotator` klasse door het pad van het invoerdocument op te geven.
## Stap 3: Maak een onderstreepte annotatie
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // werkt alleen ondersteund Word- en PDF-documenten
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
 Deze stap omvat het maken van een`UnderlineAnnotation`object met verschillende eigenschappen, zoals tekstkleur, bericht, dekking, paginanummer, achtergrondkleur, onderstrepingskleur, punten en antwoorden.
## Stap 4: Annotatie toevoegen aan document
```csharp
annotator.Add(underline);
```
Hier voegen we de onderstreepte annotatie toe aan het document.
## Stap 5: Bewaar het geannoteerde document
```csharp
annotator.Save(outputPath);
```
Ten slotte slaan we het geannoteerde document op in het opgegeven uitvoerpad.

## Conclusie
In deze zelfstudie hebben we geleerd hoe u een annotatie voor tekstonderstrepingen aan een document kunt toevoegen met behulp van GroupDocs.Annotation voor .NET. Deze krachtige bibliotheek biedt verschillende annotatieopties om de samenwerking en communicatie aan documenten te verbeteren.
## Veelgestelde vragen
### Kan ik het uiterlijk van de onderstreepte annotatie aanpassen?
Ja, u kunt eigenschappen zoals kleur, dekking en positie aanpassen aan uw vereisten.
### Is GroupDocs.Annotation compatibel met verschillende documentformaten?
Ja, GroupDocs.Annotation ondersteunt een breed scala aan documentformaten, waaronder Word en PDF.
### Kan ik meerdere annotaties aan één document toevoegen?
Absoluut, met GroupDocs.Annotation kunt u meerdere annotaties van verschillende typen aan een document toevoegen.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Annotation?
 Ja, u kunt toegang krijgen tot de gratis proefversie van[hier](https://releases.groupdocs.com/).
### Waar kan ik ondersteuning krijgen voor GroupDocs.Annotation?
 U kunt ondersteuning krijgen van het GroupDocs.Annotation-communityforum[hier](https://forum.groupdocs.com/c/annotation/10).