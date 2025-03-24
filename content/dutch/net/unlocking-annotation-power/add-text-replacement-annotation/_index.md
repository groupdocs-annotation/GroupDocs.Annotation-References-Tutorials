---
title: Voeg een annotatie voor tekstvervanging toe aan het document
linktitle: Voeg een annotatie voor tekstvervanging toe aan het document
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u moeiteloos tekstvervangende annotaties aan uw .NET-documenten kunt toevoegen met GroupDocs.Annotation voor .NET. Verbeter uw mogelijkheden voor documentmanipulatie.
weight: 24
url: /nl/net/unlocking-annotation-power/add-text-replacement-annotation/
---
## Invoering
In deze zelfstudie begeleiden we u bij het toevoegen van een tekstvervangende annotatie aan uw documenten met behulp van GroupDocs.Annotation voor .NET. Met deze krachtige bibliotheek kunnen ontwikkelaars verschillende soorten documenten programmatisch manipuleren en annoteren. Aan het einde van deze zelfstudie beschikt u over de kennis om annotaties voor tekstvervanging naadloos te integreren in uw .NET-toepassingen.
## Vereisten
Voordat we beginnen, moet u ervoor zorgen dat de volgende vereisten zijn geïnstalleerd:
### 1. .NET Framework geïnstalleerd
Zorg ervoor dat .NET Framework op uw ontwikkelmachine is geïnstalleerd. U kunt het downloaden van de Microsoft-website.
### 2. GroupDocs.Annotation voor .NET-bibliotheek
 Download en installeer de GroupDocs.Annotation voor .NET-bibliotheek vanuit de[website](https://releases.groupdocs.com/annotation/net/). Deze bibliotheek biedt de nodige tools en functionaliteiten om met annotaties in verschillende documentformaten te werken.
### 3. Installatie van de ontwikkelomgeving
Stel de ontwikkelomgeving van uw voorkeur in, zoals Visual Studio, om .NET-applicaties te maken en uit te voeren.

## Naamruimten importeren
Voordat we in het codeergedeelte duiken, importeren we de benodigde naamruimten die nodig zijn voor het werken met GroupDocs.Annotation voor .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## Stap 1: Definieer het uitvoerpad
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Hier definiëren we het uitvoerpad waar het geannoteerde document zal worden opgeslagen.
## Stap 2: Initialiseer Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Hier wordt de annotatiecode geplaatst
}
```
We initialiseren het Annotator-object door het invoerdocument ("input.pdf") op te geven binnen een gebruiksblok om een juiste verwijdering van bronnen te garanderen.
## Stap 3: Maak een vervangende annotatie
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
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
    TextToReplace = "replaced text"
};
```
Hier maken we een ReplacementAnnotation-object met verschillende eigenschappen, zoals aanmaakdatum, letterkleur, bericht, dekking, paginanummer, achtergrondkleur, punten (coördinaten), antwoorden (opmerkingen) en de tekst die moet worden vervangen.
## Stap 4: Annotatie toevoegen
```csharp
annotator.Add(replacement);
```
We voegen de gemaakte vervangende annotatie toe aan de annotator.
## Stap 5: Document opslaan
```csharp
annotator.Save(outputPath);
```
Ten slotte slaan we het geannoteerde document op in het opgegeven uitvoerpad.
## Stap 6: Succesbericht weergeven
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Er wordt een succesbericht weergegeven dat aangeeft dat het document succesvol is opgeslagen.

## Conclusie
In deze zelfstudie hebben we het proces besproken van het toevoegen van tekstvervangende annotaties aan documenten met behulp van GroupDocs.Annotation voor .NET. Door de stapsgewijze handleiding te volgen en de vereisten te begrijpen, kunt u deze functionaliteit eenvoudig in uw .NET-applicaties integreren.
## Veelgestelde vragen
### Kan ik documenten van verschillende formaten annoteren met GroupDocs.Annotation voor .NET?
Ja, GroupDocs.Annotation voor .NET ondersteunt het annoteren van verschillende documentformaten, zoals PDF, DOCX, PPTX, XLSX en meer.
### Is GroupDocs.Annotation voor .NET geschikt voor zowel desktop- als webapplicaties?
Ja, GroupDocs.Annotation voor .NET kan zowel in desktop- als in webapplicaties worden gebruikt, wat ontwikkelaars flexibiliteit biedt.
### Kan ik de weergave aanpassen van annotaties die zijn toegevoegd met GroupDocs.Annotation voor .NET?
Absoluut, u kunt het uiterlijk van annotaties aanpassen door eigenschappen zoals kleur, dekking, lettertype, enz. te wijzigen.
### Biedt GroupDocs.Annotation voor .NET ondersteuning voor functies voor gezamenlijke annotatie?
Ja, GroupDocs.Annotation voor .NET biedt functies voor gezamenlijke annotatie, waardoor meerdere gebruikers tegelijk aantekeningen kunnen maken op documenten.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Annotation voor .NET?
Ja, u kunt profiteren van een gratis proefversie van GroupDocs.Annotation voor .NET van de[website](https://releases.groupdocs.com/).