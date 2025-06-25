---
"description": "Leer hoe u moeiteloos tekstvervangende annotaties aan uw .NET-documenten kunt toevoegen met GroupDocs.Annotation voor .NET. Verbeter uw mogelijkheden voor documentbewerking."
"linktitle": "Tekstvervangende annotatie toevoegen aan document"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "Tekstvervangende annotatie toevoegen aan document"
"url": "/nl/net/unlocking-annotation-power/add-text-replacement-annotation/"
"weight": 24
---

# Tekstvervangende annotatie toevoegen aan document

## Invoering
In deze tutorial begeleiden we je door het proces van het toevoegen van een tekstvervangende annotatie aan je documenten met behulp van GroupDocs.Annotation voor .NET. Deze krachtige bibliotheek stelt ontwikkelaars in staat om verschillende soorten documenten programmatisch te bewerken en te annoteren. Aan het einde van deze tutorial ben je uitgerust met de kennis om tekstvervangende annotaties naadloos te integreren in je .NET-applicaties.
## Vereisten
Voordat we beginnen, moet u ervoor zorgen dat de volgende vereisten zijn geïnstalleerd:
### 1. .NET Framework geïnstalleerd
Zorg ervoor dat .NET Framework op uw ontwikkelcomputer is geïnstalleerd. U kunt het downloaden van de Microsoft-website.
### 2. GroupDocs.Annotation voor .NET-bibliotheek
Download en installeer de GroupDocs.Annotation voor .NET-bibliotheek van de [website](https://releases.groupdocs.com/annotation/net/)Deze bibliotheek biedt de benodigde hulpmiddelen en functionaliteiten om met annotaties in verschillende documentformaten te werken.
### 3. Instellen van de ontwikkelomgeving
Stel uw favoriete ontwikkelomgeving in, zoals Visual Studio, om .NET-toepassingen te maken en uit te voeren.

## Naamruimten importeren
Voordat we met coderen beginnen, importeren we de benodigde naamruimten voor het werken met GroupDocs.Annotation voor .NET:
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
## Stap 1: Uitvoerpad definiëren
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Hier definiëren we het uitvoerpad waar het geannoteerde document wordt opgeslagen.
## Stap 2: Annotator initialiseren
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // De annotatiecode wordt hier geplaatst
}
```
We initialiseren het Annotator-object door het invoerdocument ("input.pdf") in een blok op te geven om ervoor te zorgen dat bronnen op de juiste manier worden verwijderd.
## Stap 3: Vervangende annotatie maken
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
Hier maken we een ReplacementAnnotation-object met verschillende eigenschappen, zoals aanmaakdatum, lettertypekleur, bericht, dekking, paginanummer, achtergrondkleur, punten (coördinaten), antwoorden (opmerkingen) en de te vervangen tekst.
## Stap 4: Annotatie toevoegen
```csharp
annotator.Add(replacement);
```
We voegen de vervangende annotatie toe aan de annotator.
## Stap 5: Document opslaan
```csharp
annotator.Save(outputPath);
```
Ten slotte slaan we het geannoteerde document op in het opgegeven uitvoerpad.
## Stap 6: Succesbericht weergeven
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Er wordt een succesbericht weergegeven om aan te geven dat het document succesvol is opgeslagen.

## Conclusie
In deze tutorial hebben we het proces behandeld van het toevoegen van tekstvervangende annotaties aan documenten met behulp van GroupDocs.Annotation voor .NET. Door de stapsgewijze handleiding te volgen en de vereisten te begrijpen, kunt u deze functionaliteit eenvoudig integreren in uw .NET-applicaties.
## Veelgestelde vragen
### Kan ik documenten van verschillende formaten annoteren met GroupDocs.Annotation voor .NET?
Ja, GroupDocs.Annotation voor .NET ondersteunt het annoteren van diverse documentformaten, zoals PDF, DOCX, PPTX, XLSX en meer.
### Is GroupDocs.Annotation voor .NET geschikt voor zowel desktop- als webapplicaties?
Ja, GroupDocs.Annotation voor .NET kan worden gebruikt in zowel desktop- als webapplicaties, wat ontwikkelaars flexibiliteit biedt.
### Kan ik het uiterlijk aanpassen van annotaties die ik heb toegevoegd met GroupDocs.Annotation voor .NET?
Jazeker, u kunt het uiterlijk van de annotaties aanpassen door eigenschappen als kleur, dekking, lettertype, etc. te wijzigen.
### Biedt GroupDocs.Annotation voor .NET ondersteuning voor functies voor collaboratieve annotatie?
Ja, GroupDocs.Annotation voor .NET biedt functies voor gezamenlijke annotatie, waardoor meerdere gebruikers tegelijkertijd documenten kunnen annoteren.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Annotation voor .NET?
Ja, u kunt een gratis proefversie van GroupDocs.Annotation voor .NET gebruiken vanaf de [website](https://releases.groupdocs.com/).