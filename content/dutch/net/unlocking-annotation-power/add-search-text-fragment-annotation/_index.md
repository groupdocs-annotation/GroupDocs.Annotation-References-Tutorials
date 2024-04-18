---
title: Voeg zoektekstfragmentannotatie toe aan document
linktitle: Voeg zoektekstfragmentannotatie toe aan document
second_title: GroupDocs.Annotation .NET API
description: Ontdek de kracht van GroupDocs.Annotation voor .NET en voeg moeiteloos documentannotatiemogelijkheden toe aan uw toepassingen.
type: docs
weight: 20
url: /nl/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---
## Invoering
Op het gebied van .NET-ontwikkeling onderscheidt GroupDocs.Annotation zich als een krachtig hulpmiddel voor het naadloos annoteren van documenten. Of u nu een doorgewinterde ontwikkelaar bent of net de wereld van .NET betreedt, deze uitgebreide tutorial leidt u door de essentie van het gebruik van GroupDocs.Annotation voor .NET, van het importeren van naamruimten tot het beheersen van de fijne kneepjes van het toevoegen van zoektekstfragmentannotaties aan uw documenten.
## Invoering
GroupDocs.Annotation voor .NET stelt ontwikkelaars in staat om moeiteloos documentannotatiemogelijkheden in hun applicaties op te nemen. Met de intuïtieve API en robuuste functies kunnen ontwikkelaars aantekeningen maken in verschillende documentformaten, waaronder PDF's, Microsoft Office-documenten, afbeeldingen en meer.
## Vereisten
Voordat u in GroupDocs.Annotation voor .NET duikt, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:

## Naamruimten importeren
Importeer eerst de benodigde naamruimten om toegang te krijgen tot de GroupDocs.Annotation-klassen en -methoden in uw .NET-project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Stap 1: Definieer het uitvoerpad
Begin met het definiëren van het uitvoerpad waar het geannoteerde document zal worden opgeslagen:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Stap 2: Initialiseer Annotator
 Initialiseer vervolgens een exemplaar van het`Annotator` klasse door het pad op te geven naar het document dat u wilt annoteren:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Stap 3: Maak een zoektekstfragmentannotatie
 Maak een`SearchTextFragment` object met de gewenste eigenschappen, zoals tekst waarnaar moet worden gezocht, lettergrootte, letterfamilie, letterkleur en achtergrondkleur:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## Stap 4: Annotatie toevoegen
 Voeg de gemaakte zoektekstfragmentannotatie toe aan het document met behulp van de`Add` methode van de annotator:
```csharp
annotator.Add(searchText);
```
## Stap 5: Bewaar het geannoteerde document
Sla het geannoteerde document op in het opgegeven uitvoerpad:
```csharp
annotator.Save(outputPath);
```
## Stap 6: Succesbericht weergeven
Informeer de gebruiker dat het document succesvol is opgeslagen:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusie
Concluderend vereenvoudigt GroupDocs.Annotation voor .NET het proces van het toevoegen van annotaties aan documenten, waardoor de samenwerking en documentbeoordelingsprocessen worden verbeterd. Door de stappen in deze handleiding te volgen, kunt u de mogelijkheden voor documentannotatie naadloos integreren in uw .NET-toepassingen.
## Veelgestelde vragen
### Is GroupDocs.Annotation compatibel met alle documentformaten?
Ja, GroupDocs.Annotation ondersteunt een breed scala aan documentformaten, waaronder PDF's, Microsoft Office-documenten, afbeeldingen en meer.
### Kan ik het uiterlijk van annotaties aanpassen?
Absoluut! GroupDocs.Annotation biedt uitgebreide aanpassingsopties voor annotaties, waardoor u eigenschappen zoals lettergrootte, kleur en stijl kunt aanpassen.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Annotation?
 Ja, u krijgt toegang tot een gratis proefversie van GroupDocs.Annotation om de functies en mogelijkheden ervan te verkennen voordat u een aankoop doet[hier](https://releases.groupdocs.com/)..
### Waar kan ik ondersteuning vinden voor GroupDocs.Annotation?
 Voor ondersteuning en hulp bij GroupDocs.Annotation kunt u de GroupDocs bezoeken[forum](https://forum.groupdocs.com/c/annotation/10) gewijd aan annotatiegerelateerde vragen en discussies.
### Hoe verkrijg ik een tijdelijke licentie voor GroupDocs.Annotation?
 U kunt een tijdelijke licentie voor GroupDocs.Annotation verkrijgen via GroupDocs[website](https://purchase.groupdocs.com/temporary-license/), zodat u het product volledig kunt beoordelen.