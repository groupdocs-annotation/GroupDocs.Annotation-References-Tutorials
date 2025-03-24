---
title: Plaats beeldannotatie over tekst
linktitle: Plaats beeldannotatie over tekst
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u beeldannotaties over tekst in .NET kunt toevoegen met GroupDocs.Annotation voor efficiënt documentbeheer en samenwerking.
weight: 21
url: /nl/net/advanced-usage/put-image-annotation-over-text/
---
## Invoering
In de wereld van .NET-ontwikkeling biedt GroupDocs.Annotation een krachtige oplossing voor het toevoegen van annotaties aan documenten, waardoor samenwerking en documentbeheer efficiënter worden. Een veel voorkomende vereiste is het plaatsen van beeldannotaties over tekst, wat naadloos kan worden gerealiseerd met behulp van GroupDocs.Annotation voor .NET.
## Vereisten
Voordat u zich verdiept in het proces van het plaatsen van afbeeldingsannotaties over tekst met GroupDocs.Annotation voor .NET, moet u ervoor zorgen dat u over het volgende beschikt:
1.  GroupDocs.Annotation voor .NET Library: Download en installeer de bibliotheek van[hier](https://releases.groupdocs.com/annotation/net/).
2. Ontwikkelomgeving: Zet een geschikte ontwikkelomgeving op, zoals Visual Studio of een andere .NET IDE.
3. Document- en afbeeldingsbestanden: bereid het documentbestand (PDF, DOCX, enz.) en het afbeeldingsbestand voor dat u voor annotaties wilt gebruiken.
4. Basiskennis van C#: Bekendheid met de programmeertaal C# is noodzakelijk om de codefragmenten uit deze tutorial te implementeren.

## Naamruimten importeren
Voordat u doorgaat met het annotatieproces, moet u ervoor zorgen dat u de benodigde naamruimten in uw C#-project importeert:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Stap 1: Definieer het uitvoerpad
Definieer eerst het uitvoerpad waar het geannoteerde document zal worden opgeslagen:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Stap 2: Initialiseer Annotator
 Initialiseer de`Annotator` object door het invoerdocumentpad op te geven:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // De annotatiecode komt hier terecht
}
```
## Stap 3: Maak een afbeeldingannotatie
 Creëer een`ImageAnnotation` object met de gewenste eigenschappen zoals doosafmetingen, dekking, paginanummer, afbeeldingspad en z-index:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## Stap 4: Annotatie toevoegen
 Voeg de afbeeldingannotatie toe aan het document met behulp van de`Add` werkwijze van de`Annotator` voorwerp:
```csharp
annotator.Add(image);
```
## Stap 5: Bewaar het geannoteerde document
Sla het geannoteerde document op in het opgegeven uitvoerpad:
```csharp
annotator.Save(outputPath);
```
## Stap 6: Succesbericht weergeven
Geef een succesbericht weer met het pad naar het geannoteerde document:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusie
Concluderend: het toevoegen van beeldannotaties over tekst in .NET-toepassingen met behulp van GroupDocs.Annotation is een eenvoudig proces. Door de stapsgewijze handleiding in deze zelfstudie te volgen, kunt u documenten efficiënt annoteren en de mogelijkheden voor samenwerking en documentbeheer in uw .NET-projecten verbeteren.
## Veelgestelde vragen
### Kan ik andere documenten dan PDF's annoteren?
Ja, GroupDocs.Annotation ondersteunt verschillende documentformaten zoals DOCX, XLSX, PPTX en meer.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Annotation?
 Ja, u kunt een gratis proefversie downloaden van[hier](https://releases.groupdocs.com/).
### Hoe kan ik ondersteuning krijgen voor GroupDocs.Annotation?
 U kunt ondersteuning krijgen van het GroupDocs.Annotation-communityforum[hier](https://forum.groupdocs.com/c/annotation/10).
### Heb ik een tijdelijke licentie nodig voor testdoeleinden?
 Ja, u kunt een tijdelijke licentie verkrijgen via[hier](https://purchase.groupdocs.com/temporary-license/) voor testdoeleinden.
### Kan ik het uiterlijk van annotaties aanpassen?
Ja, GroupDocs.Annotation biedt verschillende opties om het uiterlijk van annotaties aan te passen, zoals kleur, dekking, lettergrootte, enz.