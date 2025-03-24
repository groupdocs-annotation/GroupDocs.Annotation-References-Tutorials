---
title: Voeg tekstkronkelige annotatie toe aan document
linktitle: Voeg tekstkronkelige annotatie toe aan document
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u moeiteloos kronkelige annotaties aan documenten kunt toevoegen met Groupdocs.Annotation voor .NET. Verbeter de samenwerking en documentbeoordelingsprocessen.
weight: 25
url: /nl/net/unlocking-annotation-power/add-text-squiggly-annotation/
---

# Voeg tekstkronkelige annotatie toe aan document

## Invoering

Groupdocs.Annotation voor .NET is een veelzijdige bibliotheek waarmee ontwikkelaars moeiteloos robuuste annotatiemogelijkheden in hun .NET-applicaties kunnen integreren. Of u nu werkt met PDF's, Word-documenten of andere populaire bestandsformaten, Groupdocs.Annotation biedt een naadloze oplossing voor het annoteren en verbeteren van de samenwerking aan documenten.

## Vereisten

Voordat u in de zelfstudie duikt, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:

## Naamruimten importeren

Zorg ervoor dat u de benodigde naamruimten importeert om toegang te krijgen tot de functionaliteiten van Groupdocs.Annotation voor .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Nu we aan de vereisten hebben voldaan, gaan we het proces van het toevoegen van kronkelige tekstannotaties in meerdere stappen opsplitsen.

## Stap 1: Definieer het uitvoerpad

Definieer het pad waar het geannoteerde document zal worden opgeslagen.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Stap 2: Initialiseer Annotator

Initialiseer het Annotator-object door het invoerdocumentpad op te geven.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotatiecode komt hier
}
```

## Stap 3: Maak een kronkelige annotatie

Maak een SquigglyAnnotation-object en geef de eigenschappen ervan op.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

Voeg de gemaakte kronkelige annotatie toe aan het document.

```csharp
annotator.Add(squiggly);
```

## Stap 5: Document opslaan

Sla het geannoteerde document op in het opgegeven uitvoerpad.

```csharp
annotator.Save(outputPath);
```

## Stap 6: Bevestiging weergeven

Geef een bericht weer waarin wordt bevestigd dat het geannoteerde document succesvol is opgeslagen.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusie

Concluderend biedt Groupdocs.Annotation voor .NET ontwikkelaars een robuuste set tools voor het naadloos integreren van documentannotatiefunctionaliteiten in hun .NET-applicaties. Door deze stapsgewijze handleiding te volgen, kunt u moeiteloos kronkelige annotaties aan uw documenten toevoegen, waardoor de samenwerking en documentbeoordelingsprocessen worden verbeterd.

## Veelgestelde vragen

### Vraag: Kan Groupdocs.Annotation annotatie in verschillende bestandsformaten ondersteunen?

A: Ja, Groupdocs.Annotation ondersteunt annotaties in een breed scala aan bestandsindelingen, waaronder PDF's, Word-documenten, Excel-werkbladen en meer.

### Vraag: Is Groupdocs.Annotation compatibel met zowel desktop- als webapplicaties?

EEN: Absoluut! Groupdocs.Annotation kan naadloos worden geïntegreerd in zowel desktop- als webapplicaties, wat flexibiliteit en veelzijdigheid biedt.

### Vraag: Zijn er licentieopties beschikbaar voor Groupdocs.Annotation?

A: Ja, Groupdocs.Annotation biedt flexibele licentieopties die zijn afgestemd op individuele of zakelijke behoeften, inclusief tijdelijke licenties voor proefdoeleinden.

### Vraag: Kunnen annotaties die zijn gemaakt met Groupdocs.Annotation worden aangepast?

EEN: Zeker! Groupdocs.Annotation biedt uitgebreide aanpassingsmogelijkheden voor annotaties, waardoor ontwikkelaars annotaties kunnen afstemmen op hun specifieke vereisten.

### Vraag: Biedt Groupdocs.Annotation ondersteuning en documentatie voor ontwikkelaars?

EEN: Inderdaad! Groupdocs.Annotation biedt uitgebreide documentatie en speciale ondersteuningsforums om ontwikkelaars te helpen de functies ervan effectief te gebruiken.