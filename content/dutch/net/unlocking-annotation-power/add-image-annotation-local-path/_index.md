---
"description": "Leer hoe u afbeeldingen aan documenten kunt toevoegen met GroupDocs.Annotation voor .NET. Verbeter uw documentverwerkingsmogelijkheden eenvoudig."
"linktitle": "Afbeeldingannotatie toevoegen aan document (lokaal pad)"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "Afbeeldingannotatie toevoegen aan document (lokaal pad)"
"url": "/nl/net/unlocking-annotation-power/add-image-annotation-local-path/"
type: docs
"weight": 14
---

# Afbeeldingannotatie toevoegen aan document (lokaal pad)

## Invoering
GroupDocs.Annotation voor .NET is een krachtige bibliotheek waarmee ontwikkelaars programmatisch verschillende soorten annotaties aan documenten kunnen toevoegen. In deze tutorial leren we hoe we afbeeldingen aan een document kunnen toevoegen met behulp van een lokaal pad.
## Vereisten
Voordat we beginnen, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1. Basiskennis van de programmeertaal C#.
2. Visual Studio op uw systeem geïnstalleerd.
3. GroupDocs.Annotation voor .NET-bibliotheek geïnstalleerd of tutorialsd in uw project.
4. Een invoerdocument (bijv. PDF) en een afbeeldingsbestand voor aantekeningen.
## Naamruimten importeren
Eerst moet u de benodigde naamruimten importeren in uw C#-bestand. Deze naamruimten bieden toegang tot de klassen en methoden die nodig zijn om met GroupDocs.Annotation te werken.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Stap 1: Uitvoerpad definiëren
Definieer het uitvoerpad waar het geannoteerde document wordt opgeslagen.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Stap 2: Annotator initialiseren
Initialiseer de annotator door het pad naar het invoerdocument op te geven.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotatiecode komt hier
}
```
## Stap 3: Afbeeldingannotatie maken
Maak een exemplaar van de `ImageAnnotation` klasse en specificeer de eigenschappen ervan, zoals positie, dekking, paginanummer en afbeeldingspad.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## Stap 4: Annotatie toevoegen
Voeg de gemaakte afbeeldingannotatie toe aan het document met behulp van de `Add` methode van de annotator.
```csharp
annotator.Add(image);
```
## Stap 5: Document opslaan
Sla het geannoteerde document op in het uitvoerpad.
```csharp
annotator.Save(outputPath);
```
## Stap 6: Uitvoerpad weergeven
Geef een bericht weer waarin staat dat het document succesvol is opgeslagen en waarin de locatie van het uitvoerbestand wordt vermeld.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusie
In deze tutorial hebben we geleerd hoe je afbeeldingen aan een document kunt toevoegen met GroupDocs.Annotation voor .NET. Door deze eenvoudige stappen te volgen, kun je je documentverwerkingsmogelijkheden uitbreiden met krachtige annotatiefuncties.
## Veelgestelde vragen
### Kan ik aantekeningen maken in andere documenten dan PDF-documenten?
Ja, GroupDocs.Annotation ondersteunt verschillende documentformaten, waaronder Word, Excel, PowerPoint en meer.
### Is GroupDocs.Annotation compatibel met .NET Core?
Ja, GroupDocs.Annotation is compatibel met zowel .NET Framework als .NET Core.
### Kan ik het uiterlijk van annotaties aanpassen?
Jazeker, u kunt het uiterlijk, de grootte, de kleur en andere eigenschappen van de annotaties naar wens aanpassen.
### Biedt GroupDocs.Annotation ondersteuning voor gezamenlijke annotatie?
Ja, GroupDocs.Annotation biedt functies voor samenwerking bij het maken van aantekeningen, waardoor meerdere gebruikers tegelijkertijd documenten kunnen annoteren.
### Waar kan ik extra hulp of ondersteuning vinden?
Bezoek het GroupDocs.Annotation-forum voor hulp en ondersteuning van de community.