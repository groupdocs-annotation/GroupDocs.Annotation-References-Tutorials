---
title: Afbeeldingannotatie toevoegen aan document (pad op afstand)
linktitle: Afbeeldingannotatie toevoegen aan document (pad op afstand)
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u afbeeldingannotaties aan documenten kunt toevoegen met GroupDocs.Annotation voor .NET. Verbeter documentbeheer met krachtige annotatiemogelijkheden.
weight: 15
url: /nl/net/unlocking-annotation-power/add-image-annotation-remote-path/
---

# Afbeeldingannotatie toevoegen aan document (pad op afstand)

## Invoering
In deze zelfstudie doorlopen we het proces van het toevoegen van afbeeldingsannotaties aan een document met behulp van GroupDocs.Annotation voor .NET. Deze bibliotheek biedt krachtige tools voor het programmatisch annoteren van verschillende soorten documenten.
## Vereisten
Voordat we beginnen, zorg ervoor dat u over het volgende beschikt:
1.  GroupDocs.Annotation voor .NET: Download en installeer de bibliotheek van[hier](https://releases.groupdocs.com/annotation/net/).
2. Ontwikkelomgeving: Zorg ervoor dat u een werkende ontwikkelomgeving hebt ingesteld voor .NET-ontwikkeling.
3.  Document: bereid het document voor dat u wilt annoteren. Voor deze zelfstudie gaan we ervan uit dat u een PDF-document met de naam`input.pdf`.
4. Afbeelding voor annotatie: Kies de afbeelding die u voor annotatie wilt gebruiken. Zorg ervoor dat u de afbeeldings-URL of het lokale pad bij de hand heeft.

## Naamruimten importeren
Voordat we beginnen met coderen, importeren we de benodigde naamruimten:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Stap 1: Stel het uitvoerpad in
Definieer eerst het uitvoerpad waar het geannoteerde document zal worden opgeslagen.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Stap 2: Initialiseer Annotator
 Maak een exemplaar van de`Annotator` class en specificeer het invoerdocument.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // De annotatiecode komt hier terecht
}
```
## Stap 3: Voeg afbeeldingannotatie toe
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
## Stap 5: Geef het uitvoerpad weer
Informeer de gebruiker over de succesvolle documentopslagbewerking en geef het uitvoerpad weer.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusie
In deze zelfstudie hebben we geleerd hoe u afbeeldingsannotaties aan een document kunt toevoegen met GroupDocs.Annotation voor .NET. Door deze stappen te volgen, kunt u uw documentbeheertoepassingen uitbreiden met krachtige annotatiemogelijkheden.
## Veelgestelde vragen
### Kan GroupDocs.Annotation worden gebruikt met andere documentformaten dan PDF?
Ja, GroupDocs.Annotation ondersteunt verschillende documentformaten, waaronder Word, Excel, PowerPoint en meer.
### Is GroupDocs.Annotation compatibel met .NET Core?
Ja, GroupDocs.Annotation is compatibel met zowel .NET Framework als .NET Core.
### Kan ik het uiterlijk van annotaties aanpassen?
Ja, u kunt het uiterlijk van annotaties aanpassen, zoals kleur, dekking en grootte.
### Ondersteunt GroupDocs.Annotation functies voor collaboratieve annotaties?
Ja, GroupDocs.Annotation biedt functies voor collaboratieve annotaties voor realtime samenwerking aan documenten.
### Is er een proefversie beschikbaar om te testen?
 Ja, u kunt een gratis proefversie van GroupDocs.Annotation krijgen van[hier](https://releases.groupdocs.com/).