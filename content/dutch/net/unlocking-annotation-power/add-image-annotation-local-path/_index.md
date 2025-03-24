---
title: Afbeeldingannotatie toevoegen aan document (lokaal pad)
linktitle: Afbeeldingannotatie toevoegen aan document (lokaal pad)
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u afbeeldingannotaties aan documenten kunt toevoegen met GroupDocs.Annotation voor .NET. Verbeter eenvoudig de documentverwerkingsmogelijkheden.
weight: 14
url: /nl/net/unlocking-annotation-power/add-image-annotation-local-path/
---
## Invoering
GroupDocs.Annotation voor .NET is een krachtige bibliotheek waarmee ontwikkelaars programmatisch verschillende soorten annotaties aan documenten kunnen toevoegen. In deze zelfstudie leren we hoe u afbeeldingannotaties aan een document kunt toevoegen met behulp van een lokaal pad.
## Vereisten
Voordat we beginnen, zorg ervoor dat u aan de volgende vereisten voldoet:
1. Basiskennis van de programmeertaal C#.
2. Visual Studio is op uw systeem geïnstalleerd.
3. GroupDocs.Annotation voor de .NET-bibliotheek die in uw project is geïnstalleerd of waarnaar wordt verwezen.
4. Een invoerdocument (bijvoorbeeld PDF) en een afbeeldingsbestand voor annotatie.
## Naamruimten importeren
Eerst moet u de benodigde naamruimten in uw C#-bestand importeren. Deze naamruimten bieden toegang tot de klassen en methoden die nodig zijn voor het werken met GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Stap 1: Definieer het uitvoerpad
Definieer het uitvoerpad waar het geannoteerde document zal worden opgeslagen.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Stap 2: Initialiseer Annotator
Initialiseer de annotator door het pad naar het invoerdocument op te geven.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotatiecode komt hier
}
```
## Stap 3: Maak een afbeeldingannotatie
 Maak een exemplaar van de`ImageAnnotation`klasse en specificeer de eigenschappen ervan, zoals positie, dekking, paginanummer en afbeeldingspad.
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
 Voeg de gemaakte afbeeldingannotatie toe aan het document met behulp van de`Add` methode van de annotator.
```csharp
annotator.Add(image);
```
## Stap 5: Document opslaan
Sla het geannoteerde document op in het uitvoerpad.
```csharp
annotator.Save(outputPath);
```
## Stap 6: Geef het uitvoerpad weer
Geef een bericht weer dat de succesvolle opslag van het document en de locatie van het uitvoerbestand aangeeft.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusie
In deze zelfstudie hebben we geleerd hoe u afbeeldingannotaties aan een document kunt toevoegen met GroupDocs.Annotation voor .NET. Door deze eenvoudige stappen te volgen, kunt u uw documentverwerkingsmogelijkheden uitbreiden met krachtige annotatiefuncties.
## Veelgestelde vragen
### Kan ik andere documenten dan PDF annoteren?
Ja, GroupDocs.Annotation ondersteunt verschillende documentformaten, waaronder Word, Excel, PowerPoint en meer.
### Is GroupDocs.Annotation compatibel met .NET Core?
Ja, GroupDocs.Annotation is compatibel met zowel .NET Framework als .NET Core.
### Kan ik het uiterlijk van annotaties aanpassen?
Absoluut, u kunt het uiterlijk, de grootte, de kleur en andere eigenschappen van annotaties aanpassen aan uw wensen.
### Biedt GroupDocs.Annotation ondersteuning voor gezamenlijke annotatie?
Ja, GroupDocs.Annotation biedt functies voor gezamenlijke annotaties waarmee meerdere gebruikers tegelijk aantekeningen kunnen maken op documenten.
### Waar kan ik aanvullende hulp of ondersteuning vinden?
U kunt het GroupDocs.Annotation-forum bezoeken voor hulp en ondersteuning van de community.