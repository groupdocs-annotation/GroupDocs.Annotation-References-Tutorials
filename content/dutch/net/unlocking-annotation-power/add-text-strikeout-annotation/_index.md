---
"description": "Leer hoe u tekstdoorhalingen aan documenten toevoegt met GroupDocs.Annotation voor .NET. Verbeter samenwerking en verbeter de processen voor documentbeoordeling efficiënt."
"linktitle": "Tekstdoorhalingsannotatie toevoegen aan document"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "Tekstdoorhalingsannotatie toevoegen aan document"
"url": "/nl/net/unlocking-annotation-power/add-text-strikeout-annotation/"
type: docs
"weight": 26
---

# Tekstdoorhalingsannotatie toevoegen aan document

## Invoering
In deze tutorial laten we zien hoe je een tekstdoorhaling aan een document toevoegt met GroupDocs.Annotation voor .NET. Deze bibliotheek biedt krachtige tools voor het annoteren van verschillende documenttypen, waardoor samenwerking en documentbeoordeling worden verbeterd.
## Vereisten
Voordat we beginnen, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1. GroupDocs.Annotation voor .NET: Installeer de bibliotheek. Je kunt deze downloaden van [hier](https://releases.groupdocs.com/annotation/net/).
2. Ontwikkelomgeving: Richt een geschikte ontwikkelomgeving in voor .NET-ontwikkeling.
3. Document: Zorg dat u een document bij de hand hebt waar u aantekeningen aan kunt maken, bijvoorbeeld een PDF-bestand.

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

Laten we het proces voor het toevoegen van een tekstdoorhalingsannotatie opsplitsen in meerdere stappen:
## Stap 1: Uitvoerpad definiëren
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Hier definiëren we het uitvoerpad waar het geannoteerde document wordt opgeslagen.
## Stap 2: Annotator initialiseren
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Initialiseer het Annotator-object door het pad naar het invoerdocument (in dit geval een PDF-bestand) op te geven.
## Stap 3: Maak een doorhalingsannotatie
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
Maak een StrikeoutAnnotation-object met de gewenste eigenschappen, zoals bericht, dekking, paginanummer, achtergrondkleur, punten (coördinaten) en antwoorden.
## Stap 4: Annotatie toevoegen
```csharp
annotator.Add(strikeout);
```
Voeg de gemaakte doorhalingsannotatie toe aan het document.
## Stap 5: Document opslaan
```csharp
annotator.Save(outputPath);
```
Sla het geannoteerde document op in het opgegeven uitvoerpad.

## Conclusie
In deze tutorial hebben we geleerd hoe je een tekstdoorhalingsannotatie aan een document toevoegt met GroupDocs.Annotation voor .NET. Deze krachtige bibliotheek maakt efficiënte documentannotatie mogelijk en verbetert de samenwerking en het reviewproces van documenten.
## Veelgestelde vragen
### Is GroupDocs.Annotation compatibel met verschillende documentformaten?
Ja, GroupDocs.Annotation ondersteunt een breed scala aan documentformaten, waaronder PDF, Word, Excel, PowerPoint en meer.
### Kan ik het uiterlijk van annotaties aanpassen?
Jazeker, u kunt annotatie-eigenschappen zoals kleur, dekking, lettergrootte en meer naar wens aanpassen.
### Biedt GroupDocs.Annotation samenwerkingsfuncties?
Ja, GroupDocs.Annotation vergemakkelijkt samenwerking doordat gebruikers opmerkingen, antwoorden en aantekeningen aan documenten kunnen toevoegen.
### Is er een gratis proefperiode beschikbaar?
Ja, u kunt gebruik maken van een gratis proefperiode van [hier](https://releases.groupdocs.com/).
### Waar kan ik ondersteuning krijgen voor GroupDocs.Annotation?
U kunt ondersteuning krijgen van de [GroupDocs.Annotatieforum](https://forum.groupdocs.com/c/annotation/10).