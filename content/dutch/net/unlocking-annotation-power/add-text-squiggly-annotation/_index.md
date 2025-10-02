---
"description": "Leer hoe u moeiteloos tekstuele annotaties aan documenten toevoegt met Groupdocs.Annotation voor .NET. Verbeter samenwerking en documentbeoordelingsprocessen."
"linktitle": "Voeg een golvende tekstannotatie toe aan het document"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "Voeg een golvende tekstannotatie toe aan het document"
"url": "/nl/net/unlocking-annotation-power/add-text-squiggly-annotation/"
type: docs
"weight": 25
---

# Voeg een golvende tekstannotatie toe aan het document

## Invoering

Groupdocs.Annotation voor .NET is een veelzijdige bibliotheek waarmee ontwikkelaars moeiteloos robuuste annotatiemogelijkheden in hun .NET-applicaties kunnen integreren. Of u nu werkt met PDF's, Word-documenten of andere populaire bestandsformaten, Groupdocs.Annotation biedt een naadloze oplossing voor het maken van annotaties en het verbeteren van de samenwerking aan documenten.

## Vereisten

Voordat u met de tutorial begint, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:

## Naamruimten importeren

Zorg ervoor dat u de benodigde naamruimten importeert om toegang te krijgen tot de functionaliteiten die Groupdocs.Annotation voor .NET biedt.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Nu we de vereisten hebben besproken, kunnen we het proces voor het toevoegen van kronkelige tekstannotaties opsplitsen in meerdere stappen.

## Stap 1: Uitvoerpad definiëren

Definieer het pad waar het geannoteerde document wordt opgeslagen.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Stap 2: Annotator initialiseren

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

Er wordt een bericht weergegeven waarin wordt bevestigd dat het geannoteerde document succesvol is opgeslagen.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusie

Kortom, Groupdocs.Annotation voor .NET biedt ontwikkelaars een robuuste set tools om documentannotatiefuncties naadloos te integreren in hun .NET-applicaties. Door deze stapsgewijze handleiding te volgen, kunt u moeiteloos tekstuele annotaties aan uw documenten toevoegen, wat de samenwerking en documentbeoordeling verbetert.

## Veelgestelde vragen

### V: Ondersteunt Groupdocs.Annotation annotaties in verschillende bestandsformaten?

A: Ja, Groupdocs.Annotation ondersteunt annotaties in een breed scala aan bestandsformaten, waaronder PDF's, Word-documenten, Excel-sheets en meer.

### V: Is Groupdocs.Annotation compatibel met zowel desktop- als webapplicaties?

A: Absoluut! Groupdocs.Annotation kan naadloos worden geïntegreerd in zowel desktop- als webapplicaties en biedt flexibiliteit en veelzijdigheid.

### V: Zijn er licentieopties beschikbaar voor Groupdocs.Annotation?

A: Ja, Groupdocs.Annotation biedt flexibele licentieopties op maat voor individuele of zakelijke behoeften, inclusief tijdelijke licenties voor proefdoeleinden.

### V: Kunnen annotaties die met Groupdocs.Annotation zijn gemaakt, worden aangepast?

A: Zeker! Groupdocs.Annotation biedt uitgebreide aanpassingsmogelijkheden voor annotaties, waardoor ontwikkelaars deze kunnen afstemmen op hun specifieke behoeften.

### V: Biedt Groupdocs.Annotation ondersteuning en documentatie voor ontwikkelaars?

A: Zeker! Groupdocs.Annotation biedt uitgebreide documentatie en speciale ondersteuningsforums om ontwikkelaars te helpen de functies effectief te gebruiken.