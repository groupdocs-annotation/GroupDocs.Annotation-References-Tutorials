---
"description": "Leer hoe u PDF-documenten moeiteloos kunt roteren met Groupdocs.Annotation voor .NET. Verbeter de efficiëntie van uw documentbeheer."
"linktitle": "PDF-documenten roteren"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "PDF-documenten roteren"
"url": "/nl/net/advanced-usage/rotating-pdf-documents/"
"weight": 22
---

# PDF-documenten roteren

## Invoering
Het roteren van PDF-documenten kan een cruciale taak zijn wanneer u bestanden gebruikt die op verschillende manieren bekeken of verwerkt moeten worden. In deze tutorial laten we stap voor stap zien hoe u PDF-documenten kunt roteren met Groupdocs.Annotation voor .NET.
## Vereisten
Voordat u met de tutorial begint, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1. Groupdocs.Annotation voor .NET-bibliotheek: Zorg ervoor dat u de Groupdocs.Annotation voor .NET-bibliotheek hebt gedownload en geïnstalleerd. U kunt deze downloaden van [hier](https://releases.groupdocs.com/annotation/net/).
2. Basiskennis van C#-programmering: in deze tutorial wordt ervan uitgegaan dat u een basiskennis hebt van de programmeertaal C# en weet hoe u met .NET-bibliotheken kunt werken.

## Naamruimten importeren
Eerst moet u de benodigde naamruimten in uw C#-project importeren om toegang te krijgen tot de functionaliteit die de Groupdocs.Annotation-bibliotheek biedt.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Stap 1: Het PDF-document laden
Begin met het laden van het PDF-document dat u wilt roteren met behulp van de `Annotator` klas.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Stap 2: Rotatie instellen en pagina's verwerken
Geef de rotatiehoek en de pagina's op die u wilt roteren. In dit voorbeeld roteren we de eerste pagina 90 graden met de klok mee.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Stap 3: Sla het gedraaide document op
Sla het gedraaide PDF-document op met de opgegeven wijzigingen.
```csharp
annotator.Save("result.pdf");
```
## Stap 4: Bevestiging weergeven
Informeer de gebruiker dat het document succesvol is gedraaid.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Conclusie
Het roteren van PDF-documenten is een fundamentele handeling, en met Groupdocs.Annotation voor .NET wordt het eenvoudig en efficiënt. Door de stappen in deze tutorial te volgen, kunt u PDF-bestanden eenvoudig roteren naar uw wensen.
## Veelgestelde vragen
### Kan ik meerdere pagina's in een PDF-document roteren met Groupdocs.Annotation voor .NET?
Ja, u kunt meerdere pagina's opgeven die u wilt roteren door de `ProcessPages` eigendom dienovereenkomstig.
### Is Groupdocs.Annotation voor .NET compatibel met alle versies van het .NET Framework?
Groupdocs.Annotation voor .NET ondersteunt een breed scala aan .NET Framework-versies, waardoor compatibiliteit met de meeste ontwikkelomgevingen is gegarandeerd.
### Biedt Groupdocs.Annotation voor .NET opties voor het roteren van PDF-documenten in verschillende richtingen?
Ja, u kunt PDF-documenten met de klok mee, tegen de klok in of in een aangepaste hoek roteren, afhankelijk van uw wensen.
### Kan ik Groupdocs.Annotation voor .NET integreren in mijn bestaande documentbeheersysteem?
Absoluut, Groupdocs.Annotation voor .NET biedt naadloze integratieopties, waardoor u moeiteloos de mogelijkheden voor documentbeheer kunt uitbreiden.
### Is er een proefversie beschikbaar voor Groupdocs.Annotation voor .NET?
Ja, u kunt een gratis proefversie krijgen van [hier](https://releases.groupdocs.com/).