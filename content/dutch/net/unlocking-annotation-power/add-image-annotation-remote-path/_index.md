---
"description": "Leer hoe u afbeeldingen aan documenten kunt toevoegen met GroupDocs.Annotation voor .NET. Verbeter uw documentbeheer met krachtige annotatiemogelijkheden."
"linktitle": "Afbeeldingannotatie toevoegen aan document (extern pad)"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "Afbeeldingannotatie toevoegen aan document (extern pad)"
"url": "/nl/net/unlocking-annotation-power/add-image-annotation-remote-path/"
type: docs
"weight": 15
---

# Afbeeldingannotatie toevoegen aan document (extern pad)

## Invoering
In deze tutorial laten we zien hoe je beeldannotaties aan een document toevoegt met GroupDocs.Annotation voor .NET. Deze bibliotheek biedt krachtige tools voor het programmatisch annoteren van verschillende documenttypen.
## Vereisten
Voordat we beginnen, zorg ervoor dat u het volgende heeft:
1. GroupDocs.Annotation voor .NET: Download en installeer de bibliotheek van [hier](https://releases.groupdocs.com/annotation/net/).
2. Ontwikkelomgeving: Zorg ervoor dat u een werkende ontwikkelomgeving hebt ingesteld voor .NET-ontwikkeling.
3. Document: Bereid het document voor dat u wilt annoteren. Voor deze tutorial gaan we ervan uit dat u een PDF-document hebt met de naam `input.pdf`.
4. Afbeelding voor annotatie: Kies de afbeelding die u wilt gebruiken voor annotatie. Zorg ervoor dat u de URL of het lokale pad van de afbeelding bij de hand hebt.

## Naamruimten importeren
Voordat we beginnen met coderen, importeren we de benodigde naamruimten:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Stap 1: Uitvoerpad instellen
Definieer eerst het uitvoerpad waar het geannoteerde document wordt opgeslagen.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Stap 2: Annotator initialiseren
Maak een exemplaar van de `Annotator` klasse en specificeer het invoerdocument.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotatiecode komt hier
}
```
## Stap 3: Afbeeldingannotatie toevoegen
Laten we nu de afbeeldingannotatie aan het document toevoegen. We specificeren de eigenschappen van de afbeeldingannotatie, zoals positie, dekking, paginanummer en afbeeldingspad.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Geef de positie van de annotatie op
    CreatedOn = DateTime.Now, // Stel de aanmaakdatum in
    Opacity = 0.7, // Dekking instellen (0 tot 1)
    PageNumber = 0, // Geef het paginanummer op
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Geef de URL van de afbeelding op
};
annotator.Add(image); // Voeg de afbeeldingannotatie toe
```
## Stap 4: Document opslaan
Sla het geannoteerde document op in het opgegeven uitvoerpad.
```csharp
annotator.Save(outputPath);
```
## Stap 5: Uitvoerpad weergeven
Informeer de gebruiker over het succesvol opslaan van het document en geef het uitvoerpad weer.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusie
In deze tutorial hebben we geleerd hoe je afbeeldingen aantekeningen aan een document kunt toevoegen met GroupDocs.Annotation voor .NET. Door deze stappen te volgen, kunt u uw documentbeheertoepassingen uitbreiden met krachtige annotatiemogelijkheden.
## Veelgestelde vragen
### Kan GroupDocs.Annotation gebruikt worden met andere documentformaten dan PDF?
Ja, GroupDocs.Annotation ondersteunt verschillende documentformaten, waaronder Word, Excel, PowerPoint en meer.
### Is GroupDocs.Annotation compatibel met .NET Core?
Ja, GroupDocs.Annotation is compatibel met zowel .NET Framework als .NET Core.
### Kan ik het uiterlijk van annotaties aanpassen?
Ja, u kunt het uiterlijk van annotaties aanpassen, bijvoorbeeld de kleur, dekking en grootte.
### Ondersteunt GroupDocs.Annotation functies voor samenwerking bij het maken van aantekeningen?
Ja, GroupDocs.Annotation biedt functies voor samenwerking bij het maken van aantekeningen, zodat u in realtime kunt samenwerken aan documenten.
### Is er een proefversie beschikbaar om te testen?
Ja, u kunt een gratis proefversie van GroupDocs.Annotation krijgen van [hier](https://releases.groupdocs.com/).