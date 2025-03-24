---
title: Voeg afstandannotatie toe aan document
linktitle: Voeg afstandannotatie toe aan document
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u afstandsannotaties aan documenten toevoegt met GroupDocs.Annotation voor .NET. Verbeter moeiteloos de samenwerking en communicatie.
weight: 12
url: /nl/net/unlocking-annotation-power/add-distance-annotation/
---

# Voeg afstandannotatie toe aan document

## Invoering
In deze zelfstudie leert u hoe u een afstandannotatie aan een document kunt toevoegen met GroupDocs.Annotation voor .NET. Volg deze stappen om de taak te volbrengen:
## Vereisten

Zorg ervoor dat u aan de volgende vereisten voldoet voordat u doorgaat:

-  GroupDocs.Annotation voor .NET Library: Download en installeer de GroupDocs.Annotation voor .NET-bibliotheek van[deze link](https://releases.groupdocs.com/annotation/net/).
- Document om te annoteren: Bereid het document voor (bijvoorbeeld PDF) waaraan u de afstandsannotatie wilt toevoegen.
- Ontwikkelomgeving: Stel uw ontwikkelomgeving in met Visual Studio of een andere IDE naar keuze.

## Naamruimten importeren

Zorg ervoor dat u, voordat u begint, de benodigde naamruimten in uw code opneemt. Deze naamruimten zijn essentieel voor toegang tot de vereiste klassen en methoden.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Stap 1: Initialiseer Annotator

 Begin met het initialiseren van de`Annotator` object met het pad naar het document dat u wilt annoteren.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // De annotatiecode komt hier terecht
}
```

## Stap 2: Maak afstandannotatie

 Maak nu een`DistanceAnnotation` object en configureer de eigenschappen ervan, zoals doosafmetingen, bericht, dekking, penkleur, enz.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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

## Stap 3: Annotatie toevoegen

 Voeg de gemaakte afstandannotatie toe aan het document met behulp van de`Add` methode van het annotatorobject.

```csharp
annotator.Add(distance);
```

## Stap 4: Document opslaan

Sla het geannoteerde document op de gewenste locatie op uw systeem op.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Stap 5: Bevestiging weergeven

Geef ten slotte een bericht weer waarin wordt bevestigd dat het geannoteerde document succesvol is opgeslagen.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusie

Het toevoegen van afstandsannotaties aan documenten met GroupDocs.Annotation voor .NET is een eenvoudig proces. Door de stappen in deze zelfstudie te volgen, kunt u uw documenten uitbreiden met waardevolle annotaties, waardoor een betere samenwerking en communicatie mogelijk wordt.

## Veelgestelde vragen

### Vraag: Kan ik het uiterlijk van de afstandannotatie aanpassen?

A: Ja, u kunt verschillende eigenschappen, zoals kleur, dekking, lijnstijl, enz., aanpassen aan uw wensen.

### Vraag: Ondersteunt GroupDocs.Annotation annotaties op verschillende soorten documenten?

A: Ja, GroupDocs.Annotation ondersteunt annotaties in een breed scala aan documentformaten, waaronder PDF, Word, Excel, PowerPoint en meer.

### Vraag: Is er een gratis proefversie beschikbaar voor GroupDocs.Annotation?

 A: Ja, u kunt een gratis proefversie van GroupDocs.Annotation downloaden[deze link](https://releases.groupdocs.com/).

### Vraag: Waar kan ik de documentatie voor GroupDocs.Annotation voor .NET vinden?

 A: U kunt de beschikbare gedetailleerde documentatie raadplegen[hier](https://tutorials.groupdocs.com/annotation/net/).

### Vraag: Hoe kan ik ondersteuning of hulp krijgen bij GroupDocs.Annotation?

 A: U kunt ondersteuning en hulp zoeken op het GroupDocs.Annotation-communityforum[hier](https://forum.groupdocs.com/c/annotation/10).