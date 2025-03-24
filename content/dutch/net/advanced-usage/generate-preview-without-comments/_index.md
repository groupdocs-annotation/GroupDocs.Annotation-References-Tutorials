---
title: Genereer een voorbeeld zonder opmerkingen
linktitle: Genereer een voorbeeld zonder opmerkingen
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u documentannotatiemogelijkheden naadloos kunt integreren in uw .NET-toepassingen met behulp van GroupDocs.Annotation voor .NET.
weight: 14
url: /nl/net/advanced-usage/generate-preview-without-comments/
---
## Invoering
GroupDocs.Annotation voor .NET is een krachtige tool waarmee ontwikkelaars annotatiefuncties naadloos in hun .NET-applicaties kunnen integreren. Of u nu werkt aan een documentbeheersysteem, samenwerkingsplatform of een andere toepassing die mogelijkheden voor documentannotatie vereist, GroupDocs.Annotation biedt een uitgebreide set hulpmiddelen om de functionaliteit van uw toepassing te verbeteren.
## Vereisten
Voordat u GroupDocs.Annotation voor .NET gaat gebruiken, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
### 1. Installeer GroupDocs.Annotation voor .NET
 Om te beginnen moet u GroupDocs.Annotation voor .NET downloaden en installeren. Je kunt de downloadlink vinden[hier](https://releases.groupdocs.com/annotation/net/). Volg de installatie-instructies in de documentatie voor een soepel installatieproces.
### 2. Verkrijg een licentie
 Voor GroupDocs.Annotation voor .NET is een licentie vereist voor commercieel gebruik. U kunt een licentie verkrijgen bij[hier](https://purchase.groupdocs.com/buy) of kies voor een tijdelijke licentie[hier](https://purchase.groupdocs.com/temporary-license/) voor testdoeleinden.
### 3. Bekendheid met .NET Framework
Basiskennis van .NET Framework en C#-programmeertaal is essentieel om GroupDocs.Annotation voor .NET effectief te kunnen gebruiken.

## Naamruimten importeren
Nu u de vereisten hebt ingesteld, gaan we de benodigde naamruimten in uw .NET-toepassing importeren.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

Volg deze stapsgewijze instructies om een voorbeeld zonder opmerkingen te genereren met GroupDocs.Annotation voor .NET:
## Stap 1: Initialiseer Annotator
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## Stap 2: Configureer voorbeeldopties
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## Stap 3: Geef het voorbeeldformaat en de paginanummers op
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## Stap 4: Schakel het weergeven van opmerkingen uit
```csharp
    previewOptions.RenderComments = false;
```
## Stap 5: Genereer een voorbeeld
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
Zodra u deze stappen heeft gevolgd, kan uw .NET-toepassing een voorbeeld van de opgegeven pagina's uit het document genereren zonder commentaar weer te geven.

## Conclusie
Het opnemen van annotatiefuncties in uw .NET-applicaties is nog nooit zo eenvoudig geweest dankzij GroupDocs.Annotation voor .NET. Door de stappen in deze zelfstudie te volgen, kunt u de mogelijkheden voor documentannotatie naadloos in uw toepassingen integreren, waardoor de samenwerking en het documentbeheer worden verbeterd.
## Veelgestelde vragen
### Is GroupDocs.Annotation voor .NET compatibel met alle documentformaten?
GroupDocs.Annotation voor .NET ondersteunt een breed scala aan documentformaten, waaronder PDF, DOCX, PPTX, XLSX en meer.
### Kan ik het uiterlijk aanpassen van annotaties die zijn gegenereerd met GroupDocs.Annotation voor .NET?
Ja, GroupDocs.Annotation voor .NET biedt uitgebreide aanpassingsopties, waardoor u de weergave van annotaties kunt aanpassen aan de behoeften van uw toepassing.
### Ondersteunt GroupDocs.Annotation voor .NET samenwerking tussen meerdere gebruikers?
Ja, GroupDocs.Annotation voor .NET biedt functies voor collaboratieve annotaties, waardoor meerdere gebruikers tegelijkertijd documenten kunnen annoteren.
### Is er technische ondersteuning beschikbaar voor GroupDocs.Annotation voor .NET?
 Ja, technische ondersteuning voor GroupDocs.Annotation voor .NET is beschikbaar via de[Helpforum](https://forum.groupdocs.com/c/annotation/10).
### Kan ik GroupDocs.Annotation voor .NET gratis uitproberen voordat ik het aanschaf?
 Ja, u kunt de functies van GroupDocs.Annotation voor .NET verkennen door de gratis proefversie te downloaden[hier](https://releases.groupdocs.com/).