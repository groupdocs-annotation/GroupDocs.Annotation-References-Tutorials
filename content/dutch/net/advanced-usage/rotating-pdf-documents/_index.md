---
title: PDF-documenten roteren
linktitle: PDF-documenten roteren
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u moeiteloos PDF-documenten kunt roteren met Groupdocs.Annotation voor .NET. Verbeter de efficiëntie van documentbeheer.
weight: 22
url: /nl/net/advanced-usage/rotating-pdf-documents/
---

# PDF-documenten roteren

## Invoering
Het roteren van PDF-documenten kan een cruciale taak zijn als het gaat om bestanden die op een andere manier moeten worden bekeken of verwerkt. In deze zelfstudie onderzoeken we stap voor stap hoe u PDF-documenten kunt roteren met Groupdocs.Annotation voor .NET.
## Vereisten
Voordat u in de zelfstudie duikt, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1.  Groupdocs.Annotation voor .NET-bibliotheek: Zorg ervoor dat u de Groupdocs.Annotation voor .NET-bibliotheek hebt gedownload en geïnstalleerd. Je kunt het downloaden van[hier](https://releases.groupdocs.com/annotation/net/).
2. Basiskennis van programmeren in C#: Deze tutorial gaat ervan uit dat je een basiskennis hebt van de programmeertaal C# en hoe je met .NET-bibliotheken kunt werken.

## Naamruimten importeren
Eerst moet u de benodigde naamruimten in uw C#-project importeren om toegang te krijgen tot de functionaliteit van de Groupdocs.Annotation-bibliotheek.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Stap 1: Laad het PDF-document
 Begin met het laden van het PDF-document dat u wilt roteren met behulp van de`Annotator` klas.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Stap 2: Stel rotatie- en procespagina's in
Geef de rotatiehoek op en de pagina's die u wilt roteren. In dit voorbeeld draaien we de eerste pagina 90 graden met de klok mee.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Stap 3: Sla het geroteerde document op
Sla het geroteerde PDF-document op met de opgegeven wijzigingen.
```csharp
annotator.Save("result.pdf");
```
## Stap 4: Bevestiging weergeven
Informeer de gebruiker dat het document succesvol is geroteerd.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Conclusie
Het roteren van PDF-documenten is een fundamentele handeling, en met Groupdocs.Annotation voor .NET wordt het eenvoudig en efficiënt. Door de stappen in deze zelfstudie te volgen, kunt u eenvoudig PDF-bestanden roteren volgens uw vereisten.
## Veelgestelde vragen
### Kan ik meerdere pagina's in een PDF-document roteren met Groupdocs.Annotation voor .NET?
 Ja, u kunt meerdere pagina's opgeven om te roteren door de instellingen aan te passen`ProcessPages` eigendom dienovereenkomstig.
### Is Groupdocs.Annotation voor .NET compatibel met alle versies van het .NET-framework?
Groupdocs.Annotation voor .NET ondersteunt een breed scala aan .NET-frameworkversies, waardoor compatibiliteit voor de meeste ontwikkelomgevingen wordt gegarandeerd.
### Biedt Groupdocs.Annotation voor .NET opties voor het roteren van PDF-documenten in verschillende richtingen?
Ja, u kunt PDF-documenten met de klok mee, tegen de klok in of onder aangepaste hoeken roteren, afhankelijk van uw vereisten.
### Kan ik Groupdocs.Annotation voor .NET integreren in mijn bestaande documentbeheersysteem?
Absoluut, Groupdocs.Annotation voor .NET biedt naadloze integratieopties, waardoor u de mogelijkheden voor documentbeheer moeiteloos kunt verbeteren.
### Is er een proefversie beschikbaar voor Groupdocs.Annotation voor .NET?
 Ja, u kunt een gratis proefversie krijgen van[hier](https://releases.groupdocs.com/).