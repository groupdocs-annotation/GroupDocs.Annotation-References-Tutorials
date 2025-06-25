---
"description": "Leer hoe u moeiteloos watermerkannotaties aan uw documenten kunt toevoegen met GroupDocs.Annotation voor .NET. Verbeter de helderheid en beveiliging van uw documenten."
"linktitle": "Watermerkannotatie toevoegen aan document"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "Watermerkannotatie toevoegen aan document"
"url": "/nl/net/unlocking-annotation-power/add-watermark-annotation/"
"weight": 28
---

# Watermerkannotatie toevoegen aan document

## Invoering
In deze tutorial laten we zien hoe u een watermerkannotatie aan een document toevoegt met behulp van GroupDocs.Annotation voor .NET. Watermerkannotaties zijn handig om de status van een document aan te geven, het als vertrouwelijk te markeren of andere relevante informatie toe te voegen.

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

1. GroupDocs.Annotation voor .NET: U kunt het downloaden van [hier](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: zorg ervoor dat Visual Studio op uw systeem is geïnstalleerd.
3. Basiskennis van C#: Kennis van de programmeertaal C# is noodzakelijk om de codevoorbeelden te begrijpen en te implementeren.

## Naamruimten importeren

Voordat we beginnen met coderen, importeren we de benodigde naamruimten:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Laten we het proces voor het toevoegen van een watermerkannotatie opsplitsen in meerdere stappen:

## Stap 1: Uitvoerpad definiëren

Eerst moeten we het uitvoerpad definiëren waar het geannoteerde document wordt opgeslagen. We gebruiken de `Path` klas van `System.IO` naamruimte om het pad naar de uitvoermap te combineren met de bestandsnaam.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Stap 2: Annotator initialiseren

Vervolgens initialiseren we de annotator door het pad van het invoerdocument op te geven. Dit stelt ons in staat om annotaties aan het document toe te voegen.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotatiecode komt hier
}
```

## Stap 3: Watermerkannotatie maken

Laten we nu een watermerkannotatieobject maken met de gewenste eigenschappen, zoals hoek, positie, tekst, letterkleur, dekking, enzovoort.

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

## Stap 4: Watermerkannotatie toevoegen

Nu voegen we de watermerkannotatie toe aan het document met behulp van de `Add` methode van het annotatorobject.

```csharp
annotator.Add(watermark);
```

## Stap 5: Document opslaan

Ten slotte slaan we het geannoteerde document op in het opgegeven uitvoerpad.

```csharp
annotator.Save(outputPath);
```

## Conclusie

In deze tutorial hebben we geleerd hoe je een watermerkannotatie aan een document toevoegt met GroupDocs.Annotation voor .NET. Watermerkannotaties zijn een waardevol hulpmiddel om documenten te markeren met relevante informatie of hun status aan te geven.

## Veelgestelde vragen

### V: Kan ik het uiterlijk van de watermerkannotatie aanpassen?

A: Ja, u kunt verschillende eigenschappen aanpassen, zoals tekst, lettergrootte, kleur, dekking, positie, enz. om het watermerk aan te passen aan uw wensen.

### V: Is GroupDocs.Annotation voor .NET compatibel met verschillende documentformaten?

A: Ja, GroupDocs.Annotation ondersteunt een breed scala aan documentformaten, waaronder PDF, Microsoft Word, Excel, PowerPoint en afbeeldingsformaten.

### V: Kan ik meerdere aantekeningen aan één document toevoegen?

A: Absoluut, met GroupDocs.Annotation kunt u meerdere annotaties van verschillende typen aan één document toevoegen, waardoor u het document uitgebreid kunt markeren.

### V: Biedt GroupDocs.Annotation ondersteuning voor gezamenlijke annotatie?

A: Ja, GroupDocs.Annotation maakt het mogelijk om samen aantekeningen te maken door gebruikers opmerkingen, antwoorden en aantekeningen te laten toevoegen. Zo wordt de effectieve samenwerking tussen teamleden bevorderd.

### V: Is er een proefversie beschikbaar voor GroupDocs.Annotation voor .NET?

A: Ja, u kunt een gratis proefversie downloaden van [hier](https://releases.groupdocs.com/).