---
title: Voeg tekstdoorgehaalde annotatie toe aan document
linktitle: Voeg tekstdoorgehaalde annotatie toe aan document
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u doorgehaalde annotaties aan documenten kunt toevoegen met GroupDocs.Annotation voor .NET. Verbeter de samenwerking en documentbeoordelingsprocessen efficiënt.
weight: 26
url: /nl/net/unlocking-annotation-power/add-text-strikeout-annotation/
---

# Voeg tekstdoorgehaalde annotatie toe aan document

## Invoering
In deze zelfstudie onderzoeken we hoe u een doorgehaalde annotatie aan een document kunt toevoegen met GroupDocs.Annotation voor .NET. Deze bibliotheek biedt krachtige tools voor het annoteren van verschillende documenttypen, waardoor de samenwerking en documentbeoordelingsprocessen worden verbeterd.
## Vereisten
Voordat we beginnen, zorg ervoor dat u aan de volgende vereisten voldoet:
1.  GroupDocs.Annotation voor .NET: Installeer de bibliotheek. Je kunt het downloaden van[hier](https://releases.groupdocs.com/annotation/net/).
2. Ontwikkelomgeving: Zet een geschikte ontwikkelomgeving op voor .NET-ontwikkeling.
3. Document: Zorg ervoor dat u een document gereed heeft om aantekeningen te maken, zoals een PDF-bestand.

## Naamruimten importeren
Importeer eerst de benodigde naamruimten om toegang te krijgen tot de functionaliteiten van GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Laten we nu het proces van het toevoegen van een doorgestreepte tekstannotatie in meerdere stappen opsplitsen:
## Stap 1: Definieer het uitvoerpad
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Hier definiëren we het uitvoerpad waar het geannoteerde document zal worden opgeslagen.
## Stap 2: Initialiseer Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Initialiseer het Annotator-object door het pad naar het invoerdocument op te geven (in dit geval PDF-bestand).
## Stap 3: Maak doorhaalannotatie
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
Maak een StrikeoutAnnotation-object met de gewenste eigenschappen zoals bericht, dekking, paginanummer, achtergrondkleur, punten (coördinaten) en antwoorden.
## Stap 4: Annotatie toevoegen
```csharp
annotator.Add(strikeout);
```
Voeg de gemaakte doorgehaalde annotatie toe aan het document.
## Stap 5: Document opslaan
```csharp
annotator.Save(outputPath);
```
Sla het geannoteerde document op in het opgegeven uitvoerpad.

## Conclusie
In deze zelfstudie hebben we geleerd hoe u een doorgehaalde annotatie aan een document kunt toevoegen met GroupDocs.Annotation voor .NET. Deze krachtige bibliotheek maakt efficiënte documentannotatie mogelijk, waardoor de samenwerking en documentbeoordelingsprocessen worden verbeterd.
## Veelgestelde vragen
### Is GroupDocs.Annotation compatibel met verschillende documentformaten?
Ja, GroupDocs.Annotation ondersteunt een breed scala aan documentformaten, waaronder PDF, Word, Excel, PowerPoint en meer.
### Kan ik het uiterlijk van annotaties aanpassen?
Absoluut, u kunt annotatie-eigenschappen zoals kleur, dekking, lettergrootte en meer aanpassen aan uw vereisten.
### Biedt GroupDocs.Annotation samenwerkingsfuncties?
Ja, GroupDocs.Annotation vergemakkelijkt de samenwerking doordat gebruikers opmerkingen, antwoorden en annotaties aan documenten kunnen toevoegen.
### Is er een gratis proefversie beschikbaar?
 Ja, u kunt profiteren van een gratis proefperiode van[hier](https://releases.groupdocs.com/).
### Waar kan ik ondersteuning krijgen voor GroupDocs.Annotation?
 U kunt ondersteuning krijgen van de[GroupDocs.Annotatieforum](https://forum.groupdocs.com/c/annotation/10).