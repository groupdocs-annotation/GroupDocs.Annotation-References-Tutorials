---
"description": "Ontdek de kracht van GroupDocs.Annotation voor .NET en voeg moeiteloos documentannotatiemogelijkheden toe aan uw toepassingen."
"linktitle": "Zoektekstfragmentannotatie toevoegen aan document"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "Zoektekstfragmentannotatie toevoegen aan document"
"url": "/nl/net/unlocking-annotation-power/add-search-text-fragment-annotation/"
"weight": 20
---

# Zoektekstfragmentannotatie toevoegen aan document

## Invoering
In de wereld van .NET-ontwikkeling onderscheidt GroupDocs.Annotation zich als een krachtige tool voor het naadloos annoteren van documenten. Of je nu een ervaren ontwikkelaar bent of net begint met .NET, deze uitgebreide tutorial leidt je door de basisprincipes van het gebruik van GroupDocs.Annotation voor .NET, van het importeren van naamruimten tot het onder de knie krijgen van de complexiteit van het toevoegen van zoektekstfragmentannotaties aan je documenten.
## Invoering
Met GroupDocs.Annotation voor .NET kunnen ontwikkelaars moeiteloos documentannotatiemogelijkheden in hun applicaties integreren. Dankzij de intuïtieve API en robuuste functies kunnen ontwikkelaars verschillende documentformaten annoteren, waaronder pdf's, Microsoft Office-documenten, afbeeldingen en meer.
## Vereisten
Voordat u aan de slag gaat met GroupDocs.Annotation voor .NET, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:

## Naamruimten importeren
Importeer eerst de benodigde naamruimten om toegang te krijgen tot GroupDocs.Annotation-klassen en -methoden in uw .NET-project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Stap 1: Uitvoerpad definiëren
Begin met het definiëren van het uitvoerpad waar het geannoteerde document wordt opgeslagen:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Stap 2: Annotator initialiseren
Initialiseer vervolgens een exemplaar van de `Annotator` klasse door het pad naar het document dat u wilt annoteren op te geven:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Stap 3: Zoektekstfragmentannotatie maken
Maak een `SearchTextFragment` object met de gewenste eigenschappen, zoals de te zoeken tekst, lettergrootte, lettertype, letterkleur en achtergrondkleur:
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
Voeg de aangemaakte zoektekstfragmentannotatie toe aan het document met behulp van de `Add` methode van de annotator:
```csharp
annotator.Add(searchText);
```
## Stap 5: Geannoteerd document opslaan
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
Kortom, GroupDocs.Annotation voor .NET vereenvoudigt het toevoegen van annotaties aan documenten en verbetert zo de samenwerking en de beoordeling van documenten. Door de stappen in deze handleiding te volgen, kunt u documentannotatie naadloos integreren in uw .NET-applicaties.
## Veelgestelde vragen
### Is GroupDocs.Annotation compatibel met alle documentformaten?
Ja, GroupDocs.Annotation ondersteunt een breed scala aan documentformaten, waaronder PDF's, Microsoft Office-documenten, afbeeldingen en meer.
### Kan ik het uiterlijk van annotaties aanpassen?
Absoluut! GroupDocs.Annotation biedt uitgebreide aanpassingsopties voor annotaties, waarmee u eigenschappen zoals lettergrootte, kleur en stijl kunt aanpassen.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Annotation?
Ja, u kunt een gratis proefversie van GroupDocs.Annotation gebruiken om de functies en mogelijkheden ervan te verkennen voordat u een aankoop doet. [hier](https://releases.groupdocs.com/)..
### Waar kan ik ondersteuning vinden voor GroupDocs.Annotation?
Voor ondersteuning en hulp met GroupDocs.Annotation kunt u terecht op de GroupDocs [forum](https://forum.groupdocs.com/c/annotation/10) gewijd aan vragen en discussies met betrekking tot annotaties.
### Hoe verkrijg ik een tijdelijke licentie voor GroupDocs.Annotation?
U kunt een tijdelijke licentie voor GroupDocs.Annotation verkrijgen via de GroupDocs-website. [website](https://purchase.groupdocs.com/temporary-license/), zodat u het product volledig kunt evalueren.