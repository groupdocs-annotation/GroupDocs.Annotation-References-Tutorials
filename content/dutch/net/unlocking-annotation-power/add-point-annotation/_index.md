---
title: Voeg puntannotatie toe aan document
linktitle: Voeg puntannotatie toe aan document
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u puntannotatie aan PDF's kunt toevoegen met GroupDocs.Annotation voor .NET. Stapsgewijze handleiding voor naadloze integratie.
weight: 17
url: /nl/net/unlocking-annotation-power/add-point-annotation/
---
## Invoering
GroupDocs.Annotation voor .NET is een krachtige tool waarmee ontwikkelaars programmatisch verschillende soorten annotaties aan documenten kunnen toevoegen. In deze zelfstudie concentreren we ons op het toevoegen van een puntannotatie aan een document met behulp van C#.
## Vereisten
Voordat we beginnen, zorg ervoor dat u over het volgende beschikt:
1. Basiskennis van de programmeertaal C#.
2. Visual Studio is op uw systeem geïnstalleerd.
3.  GroupDocs.Annotation voor .NET-bibliotheek geïnstalleerd. Je kunt het downloaden van[hier](https://releases.groupdocs.com/annotation/net/).

## Noodzakelijke naamruimten importeren
Om aan de slag te gaan, moet u de vereiste naamruimten in uw C#-project importeren:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Stap 1: Definieer het uitvoerpad
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
In deze stap definiëren we het uitvoerpad waar het geannoteerde document zal worden opgeslagen.
## Stap 2: Initialiseer Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Hier initialiseren we de`Annotator` object met het invoerdocument ("input.pdf").
## Stap 3: Maak puntannotatie
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
 In deze stap maken we een`PointAnnotation` object en specificeer de eigenschappen ervan, zoals positie, bericht, paginanummer en antwoorden.
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
In deze zelfstudie hebben we geleerd hoe u een puntannotatie aan een document kunt toevoegen met GroupDocs.Annotation voor .NET. Met deze krachtige bibliotheek kunt u uw documentbeheertoepassingen verbeteren door annotatiefunctionaliteiten op te nemen.
## Veelgestelde vragen
### Is GroupDocs.Annotation voor .NET compatibel met alle documentformaten?
Ja, GroupDocs.Annotation voor .NET ondersteunt een breed scala aan documentformaten, waaronder PDF, Microsoft Word, Excel, PowerPoint en meer.
### Kan ik het uiterlijk van annotaties aanpassen?
Absoluut! GroupDocs.Annotation voor .NET biedt uitgebreide mogelijkheden om het uiterlijk van annotaties aan te passen aan de behoeften van uw toepassing.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Annotation voor .NET?
 Ja, u kunt profiteren van een gratis proefperiode van[hier](https://releases.groupdocs.com/).
### Hoe kan ik ondersteuning krijgen voor eventuele problemen of vragen met betrekking tot GroupDocs.Annotation voor .NET?
 U kunt ondersteuning krijgen van het GroupDocs.Annotation-forum[hier](https://forum.groupdocs.com/c/annotation/10).
### Kan ik een tijdelijke licentie verkrijgen voor testdoeleinden?
 Ja, u kunt een tijdelijke licentie verkrijgen via[hier](https://purchase.groupdocs.com/temporary-license/).