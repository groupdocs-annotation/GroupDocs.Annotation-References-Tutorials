---
"description": "Leer hoe u afstandsannotaties aan documenten kunt toevoegen met GroupDocs.Annotation voor .NET. Verbeter moeiteloos samenwerking en communicatie."
"linktitle": "Afstandsannotatie toevoegen aan document"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "Afstandsannotatie toevoegen aan document"
"url": "/nl/net/unlocking-annotation-power/add-distance-annotation/"
"weight": 12
---

# Afstandsannotatie toevoegen aan document

## Invoering
In deze tutorial leert u hoe u een afstandsannotatie aan een document toevoegt met GroupDocs.Annotation voor .NET. Volg deze stappen om de taak uit te voeren:
## Vereisten

Zorg ervoor dat u aan de volgende vereisten voldoet voordat u verdergaat:

- GroupDocs.Annotation voor .NET-bibliotheek: download en installeer de GroupDocs.Annotation voor .NET-bibliotheek van [deze link](https://releases.groupdocs.com/annotation/net/).
- Te annoteren document: bereid het document (bijv. PDF) voor waaraan u de afstandsannotatie wilt toevoegen.
- Ontwikkelomgeving: stel uw ontwikkelomgeving in met Visual Studio of een andere IDE naar keuze.

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


## Stap 1: Annotator initialiseren

Begin met het initialiseren van de `Annotator` object met het pad naar het document dat u wilt annoteren.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotatiecode komt hier
}
```

## Stap 2: Afstandsannotatie maken

Maak nu een `DistanceAnnotation` object en configureer de eigenschappen ervan, zoals afmetingen van het vak, bericht, dekking, penkleur, enz.

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

Voeg de gemaakte afstandsannotatie toe aan het document met behulp van de `Add` methode van het annotatorobject.

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

Het toevoegen van afstandsannotaties aan documenten met GroupDocs.Annotation voor .NET is een eenvoudig proces. Door de stappen in deze tutorial te volgen, kunt u uw documenten verrijken met waardevolle annotaties, wat de samenwerking en communicatie bevordert.

## Veelgestelde vragen

### V: Kan ik het uiterlijk van de afstandsannotatie aanpassen?

A: Ja, u kunt verschillende eigenschappen, zoals kleur, dekking, lijnstijl, etc., aanpassen aan uw wensen.

### V: Ondersteunt GroupDocs.Annotation annotaties in verschillende typen documenten?

A: Ja, GroupDocs.Annotation ondersteunt annotaties in een breed scala aan documentformaten, waaronder PDF, Word, Excel, PowerPoint en meer.

### V: Is er een gratis proefversie beschikbaar voor GroupDocs.Annotation?

A: Ja, u kunt een gratis proefversie van GroupDocs.Annotation gebruiken vanaf [deze link](https://releases.groupdocs.com/).

### V: Waar kan ik de documentatie voor GroupDocs.Annotation voor .NET vinden?

A: U kunt de beschikbare gedetailleerde documentatie raadplegen [hier](https://tutorials.groupdocs.com/annotation/net/).

### V: Hoe kan ik ondersteuning of hulp krijgen voor GroupDocs.Annotation?

A: U kunt ondersteuning en hulp krijgen via het GroupDocs.Annotation communityforum [hier](https://forum.groupdocs.com/c/annotation/10).