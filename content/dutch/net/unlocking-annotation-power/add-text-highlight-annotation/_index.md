---
title: Voeg tekstmarkeringannotatie toe aan document
linktitle: Voeg tekstmarkeringannotatie toe aan document
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u annotaties met tekstmarkering aan documenten kunt toevoegen met GroupDocs.Annotation voor .NET. Verbeter de samenwerking en productiviteit met dit uitgebreide programma.
type: docs
weight: 22
url: /nl/net/unlocking-annotation-power/add-text-highlight-annotation/
---
## Invoering
Op het gebied van documentbeheer en samenwerking komt GroupDocs.Annotation voor .NET naar voren als een robuuste oplossing, waarmee ontwikkelaars tekstmarkeringsannotaties naadloos in hun toepassingen kunnen integreren. Deze zelfstudie dient als een uitgebreide handleiding voor het toevoegen van tekstmarkeringsannotaties aan documenten met behulp van GroupDocs.Annotation voor .NET. Door middel van stapsgewijze instructies en gedetailleerde uitleg wordt u vaardig in het benutten van de mogelijkheden van deze krachtige bibliotheek.
## Vereisten
Voordat u zich verdiept in de implementatie van annotaties voor tekstmarkeringen, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1. Omgevingsinstellingen: Zorg ervoor dat er een geschikte ontwikkelomgeving is geconfigureerd voor .NET-ontwikkeling.
2.  Installatie van GroupDocs.Annotation voor .NET: Download en installeer GroupDocs.Annotation voor .NET vanaf de meegeleverde[download link](https://releases.groupdocs.com/annotation/net/).
3. Bekendheid met C#: Basiskennis van de programmeertaal C#.
4. Document om aantekeningen te maken: Bereid een document voor (bijvoorbeeld een PDF) waarvoor u aantekeningen wilt maken.

## Naamruimten importeren
Importeer om te beginnen de benodigde naamruimten in uw C#-code om de functionaliteiten van GroupDocs.Annotation voor .NET te gebruiken:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Laten we nu het proces van het toevoegen van annotaties voor tekstmarkering in meerdere stappen opsplitsen:
## Stap 1: Definieer het uitvoerpad
Geef het uitvoerpad op waar het geannoteerde document zal worden opgeslagen:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Stap 2: Initialiseer Annotator
 Maak een exemplaar van de`Annotator` class, waarbij de documentbestandsnaam als parameter wordt doorgegeven:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Stap 3: Maak een hoogtepuntannotatie
 Instantieer een`HighlightAnnotation` object en configureer de eigenschappen ervan:
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
Voeg de gemaakte hoogtepuntannotatie toe aan het document:
```csharp
annotator.Add(highlight);
```
## Stap 5: Bewaar het geannoteerde document
Sla het geannoteerde document op in het opgegeven uitvoerpad:
```csharp
annotator.Save(outputPath);
```

## Conclusie
Concluderend biedt GroupDocs.Annotation voor .NET een gestroomlijnde aanpak om tekstmarkeringannotaties in documenten op te nemen. Door de stappen in deze tutorial te volgen, kunnen ontwikkelaars naadloos de samenwerking aan documenten en de productiviteit binnen hun applicaties verbeteren.
## Veelgestelde vragen
### Is GroupDocs.Annotation voor .NET compatibel met alle documentformaten?
GroupDocs.Annotation voor .NET ondersteunt verschillende documentformaten, waaronder PDF, Word, Excel en meer. Raadpleeg de documentatie voor de volledige lijst.
### Kunnen annotaties worden aangepast aan specifieke vereisten?
Ja, ontwikkelaars hebben volledige controle over de eigenschappen en het uiterlijk van annotaties, waardoor aanpassingen mogelijk zijn om aan uiteenlopende behoeften te voldoen.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Annotation voor .NET?
 Ja, u kunt de functies van GroupDocs.Annotation voor .NET verkennen door gebruik te maken van de gratis proefversie via de meegeleverde[koppeling](https://releases.groupdocs.com/).
### Hoe kan ik ondersteuning krijgen voor eventuele problemen of vragen met betrekking tot GroupDocs.Annotation voor .NET?
 Voor ondersteuning en hulp kunt u het GroupDocs.Annotation-forum bezoeken[hier](https://forum.groupdocs.com/c/annotation/10).
### Welke licentieopties zijn beschikbaar voor GroupDocs.Annotation voor .NET?
 GroupDocs.Annotation voor .NET biedt verschillende licentiemogelijkheden, waaronder tijdelijke licenties voor testdoeleinden en commerciële licenties voor productieomgevingen. Bezoek de aankooppagina[hier](https://purchase.groupdocs.com/buy) voor meer details.