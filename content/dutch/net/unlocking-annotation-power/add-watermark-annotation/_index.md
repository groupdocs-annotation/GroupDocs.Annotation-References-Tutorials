---
title: Voeg watermerkannotatie toe aan document
linktitle: Voeg watermerkannotatie toe aan document
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u moeiteloos watermerkannotaties aan uw documenten kunt toevoegen met GroupDocs.Annotation voor .NET. Verbeter de duidelijkheid en beveiliging van documenten.
type: docs
weight: 28
url: /nl/net/unlocking-annotation-power/add-watermark-annotation/
---
## Invoering
In deze zelfstudie doorlopen we het proces van het toevoegen van een watermerkannotatie aan een document met behulp van GroupDocs.Annotation voor .NET. Watermerkannotaties zijn handig om de status van een document aan te geven, het als vertrouwelijk te markeren of andere relevante informatie toe te voegen.

## Vereisten

Voordat we beginnen, zorg ervoor dat u over het volgende beschikt:

1.  GroupDocs.Annotation voor .NET: u kunt het downloaden van[hier](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Zorg ervoor dat Visual Studio op uw systeem is geïnstalleerd.
3. Basiskennis van C#: Bekendheid met de programmeertaal C# is noodzakelijk om de codevoorbeelden te begrijpen en te implementeren.

## Naamruimten importeren

Voordat we beginnen met coderen, importeren we de benodigde naamruimten:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Laten we nu het proces van het toevoegen van een watermerkannotatie in meerdere stappen opsplitsen:

## Stap 1: Definieer het uitvoerpad

 Eerst moeten we het uitvoerpad definiëren waar het geannoteerde document zal worden opgeslagen. Wij gebruiken de`Path` klasse uit`System.IO` naamruimte om het pad van de uitvoermap te combineren met de bestandsnaam.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Stap 2: Initialiseer Annotator

Vervolgens initialiseren we de annotator door het pad van het invoerdocument op te geven. Hierdoor kunnen we annotaties aan het document toevoegen.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // De annotatiecode komt hier terecht
}
```

## Stap 3: Maak een watermerkannotatie

Laten we nu een watermerkannotatieobject maken met de gewenste eigenschappen, zoals hoek, positie, tekst, letterkleur, dekking, enz.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## Stap 4: Voeg watermerkannotatie toe

 Nu voegen we de watermerkannotatie aan het document toe met behulp van de`Add` methode van het annotatorobject.

```csharp
annotator.Add(watermark);
```

## Stap 5: Document opslaan

Ten slotte slaan we het geannoteerde document op in het opgegeven uitvoerpad.

```csharp
annotator.Save(outputPath);
```

## Conclusie

In deze zelfstudie hebben we geleerd hoe u een watermerkannotatie aan een document kunt toevoegen met GroupDocs.Annotation voor .NET. Watermerkannotaties zijn een waardevol hulpmiddel om documenten te markeren met relevante informatie of om hun status aan te geven.

## Veelgestelde vragen

### Vraag: Kan ik het uiterlijk van de watermerkannotatie aanpassen?

A: Ja, u kunt verschillende eigenschappen aanpassen, zoals tekst, lettergrootte, kleur, dekking, positie, enz., om het watermerk aan uw wensen aan te passen.

### Vraag: Is GroupDocs.Annotation voor .NET compatibel met verschillende documentformaten?

A: Ja, GroupDocs.Annotation ondersteunt een breed scala aan documentformaten, waaronder PDF, Microsoft Word, Excel, PowerPoint en afbeeldingsformaten.

### Vraag: Kan ik meerdere annotaties aan één document toevoegen?

A: Absoluut, met GroupDocs.Annotation kunt u meerdere annotaties van verschillende typen aan één document toevoegen, waardoor uitgebreide documentopmaak mogelijk wordt.

### Vraag: Biedt GroupDocs.Annotation ondersteuning voor gezamenlijke annotaties?

A: Ja, GroupDocs.Annotation vergemakkelijkt gezamenlijke annotatie door gebruikers de mogelijkheid te bieden opmerkingen, antwoorden en annotaties toe te voegen, waardoor een effectieve samenwerking tussen teamleden wordt bevorderd.

### Vraag: Is er een proefversie beschikbaar voor GroupDocs.Annotation voor .NET?

 A: Ja, u kunt een gratis proefversie downloaden van[hier](https://releases.groupdocs.com/).