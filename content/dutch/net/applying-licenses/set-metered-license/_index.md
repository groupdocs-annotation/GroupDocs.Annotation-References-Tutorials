---
title: Gemeten licentie instellen
linktitle: Gemeten licentie instellen
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u een gemeten licentie voor GroupDocs.Annotation .NET instelt voor het gebruik van bronnen en het documenteren van annotatiemogelijkheden in uw .NET-toepassingen.
weight: 12
url: /nl/net/applying-licenses/set-metered-license/
---
## Invoering
GroupDocs.Annotation voor .NET is een krachtige bibliotheek waarmee ontwikkelaars moeiteloos documentannotatiemogelijkheden aan hun .NET-applicaties kunnen toevoegen. Of u nu een documentbeheersysteem, een samenwerkingsplatform of een andere toepassing bouwt waarbij documentreview en -markering betrokken is, GroupDocs.Annotation voor .NET biedt een uitgebreide set tools om het proces te stroomlijnen.
In deze zelfstudie gaan we in op het proces van het instellen van een gemeten licentie voor GroupDocs.Annotation .NET. Met een gemeten licentie kunt u alleen betalen voor de resources die u verbruikt, waardoor het een kosteneffectieve oplossing is voor projecten van elke schaal. Door de onderstaande stappen te volgen, kunt u GroupDocs.Annotation naadloos integreren in uw .NET-toepassing, terwijl u het gebruik van bronnen optimaliseert en de budgetcontrole behoudt.
## Vereisten
Voordat u in de zelfstudie duikt, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1.  GroupDocs.Annotation voor .NET Library: Download de bibliotheek van de[website](https://releases.groupdocs.com/annotation/net/).
2. Toegang tot GroupDocs-account: u hebt een GroupDocs-account nodig om de openbare en privésleutels te verkrijgen die nodig zijn voor het instellen van de gemeten licentie. Als u nog geen account heeft, kunt u zich aanmelden voor een gratis proefperiode[hier](https://releases.groupdocs.com/).
3. Basiskennis van C# en .NET Framework: Bekendheid met de programmeertaal C# en het .NET-framework zal nuttig zijn bij het implementeren van de stappen die in deze zelfstudie worden beschreven.

## Naamruimten importeren
Zorg er om te beginnen voor dat u de benodigde naamruimten in uw C#-project importeert. Deze naamruimten zijn essentieel voor interactie met de GroupDocs.Annotation-functionaliteit.
```csharp
using System;
```
## Stap 1: Verkrijg publieke en privésleutels
Voordat u de gemeten licentie instelt, moet u uw openbare en privésleutels verkrijgen via uw GroupDocs-accountdashboard.
1. Meld u aan bij uw GroupDocs-account.
2. Navigeer naar het gedeelte Licentiebeheer.
3. Kopieer uw openbare en privésleutels die door GroupDocs zijn verstrekt.
## Stap 2: Stel de gemeten licentie in
Zodra u uw publieke en private sleutels heeft verkregen, kunt u de gemeten licentie instellen in uw .NET-applicatie.
```csharp
string publicKey = "*****"; // Vervang ***** door uw openbare sleutel
string privateKey = "*****"; // Vervang ***** door uw privésleutel
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Conclusie
Kortom, het instellen van een gemeten licentie voor GroupDocs.Annotation .NET is een eenvoudig proces dat zorgt voor een efficiënt gebruik van bronnen en kosteneffectiviteit voor uw documentannotatieprojecten. Door de stappen in deze zelfstudie te volgen, kunt u GroupDocs.Annotation naadloos integreren in uw .NET-toepassing en de samenwerkings- en beoordelingsmogelijkheden van documenten verbeteren.
## Veelgestelde vragen
### Kan ik GroupDocs.Annotation voor .NET gebruiken in commerciële projecten?
Ja, GroupDocs.Annotation voor .NET kan worden gebruikt in zowel commerciële als niet-commerciële projecten. U moet echter een geschikte licentie aanschaffen op basis van uw projectvereisten.
### Is er een proefversie beschikbaar voor GroupDocs.Annotation voor .NET?
 Ja, u kunt profiteren van een gratis proefversie van GroupDocs.Annotation voor .NET door naar te gaan[deze link](https://releases.groupdocs.com/).
### Hoe kan ik technische ondersteuning krijgen voor GroupDocs.Annotation voor .NET?
 U kunt technische ondersteuning zoeken door het GroupDocs-forum te bezoeken[hier](https://forum.groupdocs.com/c/annotation/10).
### Zijn er tijdelijke licentieopties beschikbaar?
 Ja, u kunt bij GroupDocs een tijdelijke licentie verkrijgen voor gebruik op korte termijn of voor evaluatiedoeleinden. Bezoek[deze link](https://purchase.groupdocs.com/temporary-license/) voor meer informatie.
### Kan ik de annotatiefuncties aanpassen aan mijn projectvereisten?
Ja, GroupDocs.Annotation voor .NET biedt uitgebreide aanpassingsopties, zodat u de annotatiefuncties kunt aanpassen aan uw specifieke projectbehoeften.