---
title: Document laden vanaf lokale schijf
linktitle: Document laden vanaf lokale schijf
second_title: GroupDocs.Annotation .NET API
description: Ontgrendel de kracht van documentannotatie met GroupDocs.Annotation voor .NET. Integreer annotatiefuncties naadloos in uw .NET-applicaties.
weight: 13
url: /nl/net/document-loading-essentials/load-document-from-local-disk/
---

# Document laden vanaf lokale schijf

## Invoering
Het benutten van de mogelijkheden van documentannotatie is nog nooit zo eenvoudig geweest met GroupDocs.Annotation voor .NET. Met deze krachtige tool kunnen ontwikkelaars robuuste annotatiefuncties naadloos in hun .NET-applicaties integreren. In deze uitgebreide handleiding leiden we u stap voor stap door het proces van het gebruik van GroupDocs.Annotation voor .NET om documenten te annoteren. Of u nu een doorgewinterde ontwikkelaar bent of net begint, deze tutorial geeft u de kennis om de samenwerking aan documenten te verbeteren en uw workflow te stroomlijnen.
## Vereisten
Voordat u zich gaat verdiepen in documentannotatie met GroupDocs.Annotation voor .NET, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1. Basiskennis van C#: Bekendheid met de grondbeginselen van de programmeertaal C# is essentieel.
2. Installatie van GroupDocs.Annotation voor .NET: Download en installeer GroupDocs.Annotation voor .NET vanaf[hier](https://releases.groupdocs.com/annotation/net/).
3. Ontwikkelomgeving: Zet een ontwikkelomgeving op met Visual Studio of een compatibele IDE.

## Naamruimten importeren
Om te beginnen met het annoteren van documenten met GroupDocs.Annotation voor .NET, importeert u de benodigde naamruimten in uw project:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Stap 1: Document laden vanaf lokale schijf
Eerst moet u het document vanaf uw lokale schijf laden. Gebruik het volgende codefragment:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Stap 2: Definieer het annotatiegebied
Definieer vervolgens het annotatiegebied. In dit voorbeeld maken we een AreaAnnotation:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Stap 3: Document opslaan met annotaties
Nadat u het document heeft geannoteerd, slaat u het op met de annotaties:
```csharp
    annotator.Save(outputPath);
}
```
## Stap 4: Succesbericht weergeven
Geef ten slotte een succesbericht weer met het uitvoerpad:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusie
Concluderend biedt GroupDocs.Annotation voor .NET een robuuste oplossing voor het integreren van documentannotatiemogelijkheden in uw .NET-toepassingen. Door deze stapsgewijze handleiding te volgen, kunt u moeiteloos documenten annoteren en de samenwerking in uw projecten verbeteren.
## Veelgestelde vragen
### Kan ik GroupDocs.Annotation voor .NET uitproberen voordat ik het aanschaf?
 Ja, u kunt een gratis proefversie downloaden van[hier](https://releases.groupdocs.com/).
### Waar kan ik documentatie vinden voor GroupDocs.Annotation voor .NET?
 U heeft toegang tot de documentatie[hier](https://tutorials.groupdocs.com/annotation/net/).
### Hoe kan ik een tijdelijke licentie verkrijgen voor GroupDocs.Annotation voor .NET?
 Een tijdelijke licentie kunt u verkrijgen bij[hier](https://purchase.groupdocs.com/temporary-license/).
### Is er ondersteuning beschikbaar voor GroupDocs.Annotation voor .NET?
 Ja, u kunt ondersteuning vinden op het GroupDocs-forum[hier](https://forum.groupdocs.com/c/annotation/10).
### Waar kan ik GroupDocs.Annotation voor .NET kopen?
 U kunt GroupDocs.Annotation voor .NET aanschaffen[hier](https://purchase.groupdocs.com/buy).