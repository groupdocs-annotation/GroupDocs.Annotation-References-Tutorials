---
"description": "Leer hoe u tekstmarkeringen aan documenten toevoegt met GroupDocs.Annotation voor .NET. Verbeter samenwerking en productiviteit met deze uitgebreide tool."
"linktitle": "Tekstmarkeringsaantekening toevoegen aan document"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "Tekstmarkeringsaantekening toevoegen aan document"
"url": "/nl/net/unlocking-annotation-power/add-text-highlight-annotation/"
type: docs
"weight": 22
---

# Tekstmarkeringsaantekening toevoegen aan document

## Invoering
Op het gebied van documentbeheer en samenwerking is GroupDocs.Annotation voor .NET een robuuste oplossing waarmee ontwikkelaars naadloos tekstmarkeringen in hun applicaties kunnen integreren. Deze tutorial dient als een uitgebreide handleiding voor het toevoegen van tekstmarkeringen aan documenten met behulp van GroupDocs.Annotation voor .NET. Door middel van stapsgewijze instructies en gedetailleerde uitleg leert u de mogelijkheden van deze krachtige bibliotheek optimaal te benutten.
## Vereisten
Voordat u begint met de implementatie van tekstmarkeringsannotaties, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1. Omgevingsinstelling: Zorg dat er een geschikte ontwikkelomgeving is geconfigureerd voor .NET-ontwikkeling.
2. Installatie van GroupDocs.Annotation voor .NET: Download en installeer GroupDocs.Annotation voor .NET vanaf de meegeleverde [downloadlink](https://releases.groupdocs.com/annotation/net/).
3. Kennis van C#: basiskennis van de programmeertaal C#.
4. Te annoteren document: bereid een document voor (bijv. een PDF) waarop u aantekeningen wilt maken.

## Naamruimten importeren
Om te beginnen importeert u de benodigde naamruimten in uw C#-code om de functionaliteiten van GroupDocs.Annotation voor .NET te gebruiken:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Laten we het proces voor het toevoegen van tekstmarkeringsannotaties opsplitsen in meerdere stappen:
## Stap 1: Uitvoerpad definiëren
Geef het uitvoerpad op waar het geannoteerde document wordt opgeslagen:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Stap 2: Annotator initialiseren
Maak een exemplaar van de `Annotator` klasse, waarbij de bestandsnaam van het document als parameter wordt doorgegeven:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Stap 3: Markeernotatie maken
Instantieer een `HighlightAnnotation` object en configureer de eigenschappen ervan:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
## Stap 4: Annotatie toevoegen
Voeg de gemaakte markeringsannotatie toe aan het document:
```csharp
annotator.Add(highlight);
```
## Stap 5: Geannoteerd document opslaan
Sla het geannoteerde document op in het opgegeven uitvoerpad:
```csharp
annotator.Save(outputPath);
```

## Conclusie
Concluderend biedt GroupDocs.Annotation voor .NET een gestroomlijnde aanpak voor het integreren van tekstmarkeringen in documenten. Door de stappen in deze tutorial te volgen, kunnen ontwikkelaars naadloos de samenwerking aan documenten en de productiviteit binnen hun applicaties verbeteren.
## Veelgestelde vragen
### Is GroupDocs.Annotation voor .NET compatibel met alle documentformaten?
GroupDocs.Annotation voor .NET ondersteunt verschillende documentformaten, waaronder PDF, Word, Excel en meer. Raadpleeg de documentatie voor een volledige lijst.
### Kunnen annotaties worden aangepast aan specifieke vereisten?
Ja, ontwikkelaars hebben volledige controle over de eigenschappen en het uiterlijk van annotaties, waardoor ze aangepast kunnen worden om aan uiteenlopende behoeften te voldoen.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Annotation voor .NET?
Ja, u kunt de functies van GroupDocs.Annotation voor .NET verkennen door de gratis proefversie te gebruiken via de meegeleverde [link](https://releases.groupdocs.com/).
### Hoe kan ik ondersteuning krijgen voor problemen of vragen met betrekking tot GroupDocs.Annotation voor .NET?
Voor ondersteuning en hulp kunt u terecht op het GroupDocs.Annotation-forum [hier](https://forum.groupdocs.com/c/annotation/10).
### Welke licentieopties zijn beschikbaar voor GroupDocs.Annotation voor .NET?
GroupDocs.Annotation voor .NET biedt verschillende licentieopties, waaronder tijdelijke licenties voor testdoeleinden en commerciële licenties voor productieomgevingen. Ga naar de aankooppagina. [hier](https://purchase.groupdocs.com/buy) voor meer details.