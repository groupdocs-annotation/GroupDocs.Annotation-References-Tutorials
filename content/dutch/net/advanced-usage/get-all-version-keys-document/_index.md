---
title: Alle versiesleutels op document ophalen
linktitle: Alle versiesleutels op document ophalen
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u alle versiesleutels van een document kunt ophalen met GroupDocs.Annotation voor .NET. Verbeter uw mogelijkheden voor documentbeheer met dit uitgebreide programma.
weight: 16
url: /nl/net/advanced-usage/get-all-version-keys-document/
---
## Invoering
In de snelle digitale wereld van vandaag is effectief documentbeheer cruciaal voor zowel bedrijven als particulieren. Of u nu aan projecten samenwerkt, contracten beoordeelt of eenvoudigweg uw bestanden ordent, de juiste tools kunnen het verschil maken. GroupDocs.Annotation voor .NET biedt een uitgebreide oplossing voor het annoteren en manipuleren van documenten binnen .NET-toepassingen. In deze zelfstudie onderzoeken we hoe u GroupDocs.Annotation voor .NET kunt gebruiken om alle versiesleutels van een document op te halen.
## Vereisten
Voordat we in de tutorial duiken, moet je ervoor zorgen dat je aan de volgende vereisten voldoet:
### 1. Installeer GroupDocs.Annotation voor .NET
 Om aan de slag te gaan, moet u GroupDocs.Annotation voor .NET downloaden en installeren. U kunt de nieuwste versie verkrijgen via de[download link](https://releases.groupdocs.com/annotation/net/).
### 2. Verkrijg API-referenties
Zorg ervoor dat u over de benodigde API-referenties beschikt om toegang te krijgen tot GroupDocs.Annotation voor .NET-functionaliteiten.

## Importeer de benodigde naamruimten
Zorg ervoor dat u, voordat u doorgaat, de vereiste naamruimten in uw project importeert:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
```

Laten we het proces voor het verkrijgen van alle versiesleutels voor een document in eenvoudige stappen opsplitsen:
## Stap 1: Initialiseer het Annotator-object
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf"))
{
    // Code komt hier
}
```
 Initialiseer de`Annotator` object met het pad naar het document waarmee u wilt werken.
## Stap 2: Versiesleutels ophalen
```csharp
List<object> versionKeys = annotator.GetVersionsList();
```
 Roep de`GetVersionsList()` methode op de`Annotator` object om alle versiesleutels op te halen die aan het document zijn gekoppeld. Deze methode retourneert een lijst met versiesleutels.

## Conclusie
GroupDocs.Annotation voor .NET vereenvoudigt documentannotatie- en manipulatietaken binnen .NET-toepassingen. Door deze zelfstudie te volgen, heeft u geleerd hoe u alle versiesleutels van een document kunt ophalen met GroupDocs.Annotation voor .NET. Neem deze functionaliteit op in uw projecten om de mogelijkheden voor documentbeheer te verbeteren.
## Veelgestelde vragen
### Is GroupDocs.Annotation voor .NET compatibel met alle documentformaten?
GroupDocs.Annotation voor .NET ondersteunt een breed scala aan documentformaten, waaronder PDF, DOCX, XLSX, PPTX en meer.
### Kan ik GroupDocs.Annotation voor .NET uitproberen voordat ik het aanschaf?
 Ja, u kunt de functies van GroupDocs.Annotation voor .NET verkennen door gebruik te maken van de gratis proefversie[hier](https://releases.groupdocs.com/).
### Hoe kan ik ondersteuning krijgen voor GroupDocs.Annotation voor .NET?
 U kunt hulp zoeken en in contact komen met de gemeenschap via het ondersteuningsforum[hier](https://forum.groupdocs.com/c/annotation/10).
### Zijn er tijdelijke licenties beschikbaar voor GroupDocs.Annotation voor .NET?
 Ja, tijdelijke licenties zijn beschikbaar voor evaluatiedoeleinden. U kunt er één verkrijgen bij[hier](https://purchase.groupdocs.com/temporary-license/).
### Waar kan ik GroupDocs.Annotation voor .NET kopen?
 U kunt GroupDocs.Annotation voor .NET kopen via de website[hier](https://purchase.groupdocs.com/buy).