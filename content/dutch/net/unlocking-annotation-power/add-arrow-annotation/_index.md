---
title: Voeg pijlannotatie toe aan document
linktitle: Voeg pijlannotatie toe aan document
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u pijlannotaties aan uw documenten kunt toevoegen met GroupDocs.Annotation voor .NET. Verbeter moeiteloos de duidelijkheid en interactiviteit van documenten.
weight: 11
url: /nl/net/unlocking-annotation-power/add-arrow-annotation/
---
## Invoering
In deze zelfstudie begeleiden we u bij het toevoegen van pijlannotaties aan uw documenten met behulp van GroupDocs.Annotation voor .NET. Pijlannotaties zijn handig om de richting aan te geven of om specifieke elementen in een document aan te wijzen.
## Vereisten
Zorg ervoor dat u over het volgende beschikt voordat u begint:
1.  GroupDocs.Annotation voor .NET: Installeer de GroupDocs.Annotation-bibliotheek voor .NET. Je kunt het downloaden van[hier](https://releases.groupdocs.com/annotation/net/).
2. Ontwikkelomgeving: Zorg ervoor dat u een ontwikkelomgeving hebt ingesteld voor .NET-ontwikkeling, inclusief Visual Studio of een andere gewenste IDE.

## Naamruimten importeren
Ten eerste moet u de benodigde naamruimten importeren om toegang te krijgen tot de vereiste klassen en methoden voor annotatie.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Stap 1: Initialiseer Annotator
Initialiseer de annotator door het invoerdocumentbestandspad op te geven.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Stap 2: Maak een pijlannotatie
Maak een exemplaar van de klasse ArrowAnnotation en definieer de eigenschappen ervan, zoals positie, bericht, dekking, penkleur, stijl, breedte, enz.
```csharp
	ArrowAnnotation arrow = new ArrowAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		CreatedOn = DateTime.Now,
		Message = "This is arrow annotation",
		Opacity = 0.7,
		PageNumber = 0,
		PenColor = 65535,
		PenStyle = PenStyle.Dot,
		PenWidth = 3,
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
## Stap 3: Annotatie toevoegen
 Voeg de pijlannotatie toe aan het document met behulp van de`Add` methode van de annotator.
```csharp
	annotator.Add(arrow);
```
## Stap 4: Document opslaan
Sla het geannoteerde document op in het opgegeven uitvoerpad.
```csharp
	annotator.Save(outputPath);
}
```
## Stap 5: Bevestiging weergeven
Geef een bevestigingsbericht weer dat aangeeft dat het document succesvol is opgeslagen.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Nu hebt u met succes een pijlannotatie aan uw document toegevoegd met GroupDocs.Annotation voor .NET.

## Conclusie
In deze zelfstudie hebben we het proces besproken van het toevoegen van pijlannotaties aan documenten met behulp van GroupDocs.Annotation voor .NET. Door deze stappen te volgen, kunt u uw documenten voorzien van duidelijke richtingaanwijzers, waardoor ze informatiever en aantrekkelijker worden.
## Veelgestelde vragen
### Kan ik het uiterlijk van de pijlannotatie aanpassen?
Ja, u kunt verschillende eigenschappen, zoals kleur, stijl, breedte en dekking, aanpassen aan uw voorkeuren en documentvereisten.
### Is GroupDocs.Annotation compatibel met alle documentformaten?
GroupDocs.Annotation ondersteunt een breed scala aan documentformaten, waaronder PDF, DOCX, PPTX, XLSX en meer.
### Kan ik annotaties programmatisch toevoegen met GroupDocs.Annotation?
Ja, GroupDocs.Annotation biedt API's waarmee u programmatisch annotaties aan documenten kunt toevoegen, bewerken en verwijderen.
### Biedt GroupDocs.Annotation een gratis proefperiode?
 Ja, u kunt GroupDocs.Annotation gratis uitproberen door het te downloaden van[hier](https://releases.groupdocs.com/).
### Waar kan ik technische ondersteuning krijgen voor GroupDocs.Annotation?
Voor technische ondersteuning en assistentie kunt u het GroupDocs.Annotation-forum bezoeken[hier](https://forum.groupdocs.com/c/annotation/10).