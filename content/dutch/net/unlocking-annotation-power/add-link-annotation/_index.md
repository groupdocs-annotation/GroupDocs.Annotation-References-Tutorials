---
title: Voeg linkannotatie toe aan document
linktitle: Voeg linkannotatie toe aan document
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u linkannotaties aan documenten kunt toevoegen met Groupdocs.Annotation voor .NET. Verbeter moeiteloos de samenwerking en interactiviteit.
type: docs
weight: 16
url: /nl/net/unlocking-annotation-power/add-link-annotation/
---
## Invoering
Groupdocs.Annotation voor .NET is een krachtige bibliotheek waarmee ontwikkelaars moeiteloos uitgebreide annotatiefunctionaliteiten in hun .NET-applicaties kunnen integreren. Een van de belangrijkste functies die het biedt, is de mogelijkheid om linkannotaties aan documenten toe te voegen, waardoor de samenwerking en interactiviteit worden verbeterd.
## Vereisten
Voordat u begint met het toevoegen van linkannotaties, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
- Basiskennis van de programmeertaal C#.
- Groupdocs.Annotation voor .NET-bibliotheek geïnstalleerd.
- Toegang tot een document dat u wilt annoteren.

## Naamruimten importeren
Ten eerste moet u de benodigde naamruimten importeren om Groupdocs.Annotation voor .NET-functionaliteiten te kunnen gebruiken. Hierdoor heeft uw toepassing toegang tot de klassen en methoden die nodig zijn voor het annoteren van documenten.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Stap 1: Stel het uitvoerpad in
Definieer het pad waar u het geannoteerde document wilt opslaan.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Stap 2: Initialiseer Annotator
 Maak een exemplaar van de`Annotator` klasse door het pad op te geven van het document dat u wilt annoteren.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // De annotatiecode komt hier terecht
}
```
## Stap 3: Maak een linkannotatie
 Definieer een`LinkAnnotation` object en specificeer de eigenschappen ervan, zoals bericht, dekking, paginanummer, achtergrondkleur, punten, antwoorden en URL.
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
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
    },
    Url = "https://www.google.com"
};
```
## Stap 4: Annotatie toevoegen
 Voeg de gemaakte linkannotatie toe aan het document met behulp van de`Add` methode van de annotatorinstantie.
```csharp
annotator.Add(link);
```
## Stap 5: Document opslaan
Sla het geannoteerde document op in het opgegeven uitvoerpad.
```csharp
annotator.Save(outputPath);
```
## Stap 6: Succesbericht weergeven
Informeer de gebruiker over het succesvol opslaan van het geannoteerde document.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusie
Kortom, door de bovenstaande stappen te volgen, kunt u naadloos linkannotaties toevoegen aan documenten met behulp van Groupdocs.Annotation voor .NET. Dit verbetert de samenwerking tussen documenten en biedt gebruikers interactieve functies.
## Veelgestelde vragen
### Is Groupdocs.Annotation voor .NET compatibel met alle soorten documenten?
Groupdocs.Annotation voor .NET ondersteunt een breed scala aan documentformaten, waaronder PDF, Word, Excel en meer.
### Kan ik het uiterlijk van annotaties aanpassen?
Ja, u kunt verschillende eigenschappen van annotaties, zoals kleur, dekking en grootte, aanpassen aan uw wensen.
### Biedt Groupdocs.Annotation voor .NET realtime samenwerkingsfuncties?
Ja, Groupdocs.Annotation voor .NET biedt realtime samenwerkingsfuncties waarmee meerdere gebruikers tegelijkertijd documenten kunnen annoteren.
### Is er technische ondersteuning beschikbaar voor Groupdocs-producten?
 Ja, technische ondersteuning voor Groupdocs-producten is beschikbaar via het forum en de ondersteuning[hier](https://forum.groupdocs.com/c/annotation/10).
### Kan ik Groupdocs.Annotation voor .NET uitproberen voordat ik het aanschaf?
Ja, u kunt profiteren van een gratis proefversie van Groupdocs.Annotation voor .NET om de functies ervan te verkennen voordat u een aankoop doet[hier](https://purchase.groupdocs.com/temporary-license/).