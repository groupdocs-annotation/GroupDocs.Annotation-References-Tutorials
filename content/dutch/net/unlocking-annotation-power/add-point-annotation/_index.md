---
"description": "Leer hoe u puntannotaties aan pdf's toevoegt met GroupDocs.Annotation voor .NET. Stapsgewijze handleiding voor naadloze integratie."
"linktitle": "Puntannotatie toevoegen aan document"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "Puntannotatie toevoegen aan document"
"url": "/nl/net/unlocking-annotation-power/add-point-annotation/"
type: docs
"weight": 17
---

# Puntannotatie toevoegen aan document

## Invoering
GroupDocs.Annotation voor .NET is een krachtige tool waarmee ontwikkelaars programmatisch verschillende soorten annotaties aan documenten kunnen toevoegen. In deze tutorial concentreren we ons op het toevoegen van een puntannotatie aan een document met behulp van C#.
## Vereisten
Voordat we beginnen, zorg ervoor dat u het volgende heeft:
1. Basiskennis van de programmeertaal C#.
2. Visual Studio op uw systeem geïnstalleerd.
3. GroupDocs.Annotation voor .NET-bibliotheek geïnstalleerd. U kunt het downloaden van [hier](https://releases.groupdocs.com/annotation/net/).

## Noodzakelijke naamruimten importeren
Om te beginnen moet u de vereiste naamruimten importeren in uw C#-project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Stap 1: Uitvoerpad definiëren
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
In deze stap definiëren we het uitvoerpad waar het geannoteerde document wordt opgeslagen.
## Stap 2: Annotator initialiseren
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Hier initialiseren we de `Annotator` object met het invoerdocument ("input.pdf").
## Stap 3: Puntannotatie maken
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
In deze stap maken we een `PointAnnotation` object en specificeer de eigenschappen ervan, zoals positie, bericht, paginanummer en antwoorden.
## Stap 4: Annotatie toevoegen
```csharp
annotator.Add(point);
```
Hier voegen we de gemaakte puntannotatie toe aan het document.
## Stap 5: Document opslaan
```csharp
annotator.Save(outputPath);
```
Ten slotte slaan we het geannoteerde document op in het opgegeven uitvoerpad.

## Conclusie
In deze tutorial hebben we geleerd hoe je een puntannotatie aan een document toevoegt met GroupDocs.Annotation voor .NET. Met deze krachtige bibliotheek kun je je documentbeheertoepassingen uitbreiden met annotatiefunctionaliteit.
## Veelgestelde vragen
### Is GroupDocs.Annotation voor .NET compatibel met alle documentformaten?
Ja, GroupDocs.Annotation voor .NET ondersteunt een breed scala aan documentformaten, waaronder PDF, Microsoft Word, Excel, PowerPoint en meer.
### Kan ik het uiterlijk van annotaties aanpassen?
Absoluut! GroupDocs.Annotation voor .NET biedt uitgebreide opties voor het aanpassen van de weergave van annotaties aan de behoeften van uw toepassing.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Annotation voor .NET?
Ja, u kunt gebruik maken van een gratis proefperiode van [hier](https://releases.groupdocs.com/).
### Hoe kan ik ondersteuning krijgen voor problemen of vragen met betrekking tot GroupDocs.Annotation voor .NET?
U kunt ondersteuning krijgen via het GroupDocs.Annotation-forum [hier](https://forum.groupdocs.com/c/annotation/10).
### Kan ik een tijdelijke licentie krijgen voor testdoeleinden?
Ja, u kunt een tijdelijke licentie verkrijgen bij [hier](https://purchase.groupdocs.com/temporary-license/).