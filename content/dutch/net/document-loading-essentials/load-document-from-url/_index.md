---
title: Document laden vanaf URL
linktitle: Document laden vanaf URL
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u PDF-documenten programmatisch kunt annoteren met GroupDocs.Annotation voor .NET. Stapsgewijze zelfstudie met codevoorbeelden.
weight: 15
url: /nl/net/document-loading-essentials/load-document-from-url/
---

# Document laden vanaf URL

## Invoering
GroupDocs.Annotation voor .NET is een bibliotheek met veel functies waarmee ontwikkelaars moeiteloos annotatiemogelijkheden aan hun .NET-applicaties kunnen toevoegen. Met GroupDocs.Annotation kunt u PDF-documenten programmatisch annoteren, zodat gebruikers tekst kunnen markeren, opmerkingen kunnen toevoegen, vormen kunnen tekenen en meer. In deze zelfstudie wordt u door de stappen geleid voor het laden van een document vanaf een URL, het toevoegen van annotaties en het opslaan van het geannoteerde document met GroupDocs.Annotation voor .NET.
## Vereisten
Voordat u begint, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1. Visual Studio: Zorg ervoor dat Visual Studio op uw ontwikkelmachine is geïnstalleerd.
2.  GroupDocs.Annotation voor .NET: Download en installeer GroupDocs.Annotation voor .NET vanaf de[website](https://releases.groupdocs.com/annotation/net/).
3. Basiskennis van C#: Maak uzelf vertrouwd met de programmeertaal C#.
4. Internetverbinding: u hebt een internetverbinding nodig om toegang te krijgen tot externe bronnen en om voorbeeldbestanden te downloaden.

## Naamruimten importeren
Laten we eerst de benodigde naamruimten in uw C#-project importeren:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## Stap 1: Document laden vanaf URL
Volg deze stappen om een PDF-document vanaf een URL te annoteren:
### Stap 1.1: Definieer het uitvoerpad
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Stap 1.2: Geef de URL op
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### Stap 1.3: Document laden
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // Voeg hier annotaties toe
    annotator.Save(outputPath);
}
```
## Stap 2: Annotaties toevoegen
Laten we nu annotaties toevoegen aan het geladen document. In dit voorbeeld voegen we een gebiedannotatie toe:
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Stap 3: geannoteerd document opslaan
Sla ten slotte het geannoteerde document op in het opgegeven uitvoerpad:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusie
In deze zelfstudie hebben we geleerd hoe u PDF-documenten kunt annoteren met GroupDocs.Annotation voor .NET. Door de stapsgewijze handleiding te volgen, kunt u de annotatiefunctionaliteit naadloos integreren in uw .NET-toepassingen, waardoor gebruikers effectief kunnen samenwerken aan PDF-bestanden.

## Veelgestelde vragen
### Is GroupDocs.Annotation voor .NET compatibel met alle .NET-frameworks?
Ja, GroupDocs.Annotation voor .NET is compatibel met verschillende .NET-frameworks, waaronder .NET Framework, .NET Core en .NET Standard.
### Kan ik het uiterlijk van annotaties aanpassen?
Absoluut! GroupDocs.Annotation voor .NET biedt uitgebreide aanpassingsopties, waardoor u het uiterlijk en het gedrag van annotaties kunt aanpassen aan uw vereisten.
### Is er een gratis proefversie beschikbaar voor GroupDocs.Annotation voor .NET?
 Ja, u kunt een gratis proefversie van GroupDocs.Annotation voor .NET downloaden van de[website](https://releases.groupdocs.com/).
### Hoe kan ik technische ondersteuning krijgen voor GroupDocs.Annotation voor .NET?
 Als u technische problemen ondervindt of vragen heeft over GroupDocs.Annotation voor .NET, kunt u hulp vragen aan de[Helpforum](https://forum.groupdocs.com/c/annotation/10).
### Waar kan ik een licentie kopen voor GroupDocs.Annotation voor .NET?
 U kunt een licentie voor GroupDocs.Annotation voor .NET aanschaffen bij de[aankooppagina](https://purchase.groupdocs.com/buy).