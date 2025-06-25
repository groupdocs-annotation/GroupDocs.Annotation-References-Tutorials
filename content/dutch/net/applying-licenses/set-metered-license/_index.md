---
"description": "Leer hoe u een gemeten licentie instelt voor GroupDocs.Annotation .NET voor resourcegebruik en documentannotatiemogelijkheden in uw .NET-toepassingen."
"linktitle": "Metered-licentie instellen"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "Metered-licentie instellen"
"url": "/nl/net/applying-licenses/set-metered-license/"
"weight": 12
---

# Metered-licentie instellen

## Invoering
GroupDocs.Annotation voor .NET is een krachtige bibliotheek waarmee ontwikkelaars moeiteloos documentannotatiemogelijkheden aan hun .NET-applicaties kunnen toevoegen. Of u nu een documentbeheersysteem, samenwerkingsplatform of een applicatie bouwt die documentcontrole en -markering vereist, GroupDocs.Annotation voor .NET biedt een uitgebreide set tools om het proces te stroomlijnen.
In deze tutorial verdiepen we ons in het instellen van een gedoseerde licentie voor GroupDocs.Annotation .NET. Met een gedoseerde licentie betaalt u alleen voor de resources die u gebruikt, waardoor het een kosteneffectieve oplossing is voor projecten van elke omvang. Door de onderstaande stappen te volgen, kunt u GroupDocs.Annotation naadloos integreren in uw .NET-applicatie, terwijl u het resourcegebruik optimaliseert en de budgettaire controle behoudt.
## Vereisten
Voordat u met de tutorial begint, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1. GroupDocs.Annotation voor .NET-bibliotheek: download de bibliotheek van de [website](https://releases.groupdocs.com/annotation/net/).
2. Toegang tot GroupDocs-account: U hebt een GroupDocs-account nodig om de openbare en privésleutels te verkrijgen die nodig zijn voor het instellen van de gemeten licentie. Als u nog geen account hebt, kunt u zich aanmelden voor een gratis proefperiode. [hier](https://releases.groupdocs.com/).
3. Basiskennis van C# en .NET Framework: Kennis van de programmeertaal C# en het .NET Framework is nuttig voor het implementeren van de stappen die in deze tutorial worden beschreven.

## Naamruimten importeren
Zorg er allereerst voor dat u de benodigde naamruimten in uw C#-project importeert. Deze naamruimten zijn essentieel voor interactie met de functionaliteit van GroupDocs.Annotation.
```csharp
using System;
```
## Stap 1: Publieke en privésleutels verkrijgen
Voordat u de gemeten licentie instelt, moet u uw openbare en persoonlijke sleutels ophalen via het dashboard van uw GroupDocs-account.
1. Meld u aan bij uw GroupDocs-account.
2. Ga naar het gedeelte Licentiebeheer.
3. Kopieer de openbare en persoonlijke sleutels die u van GroupDocs hebt gekregen.
## Stap 2: Stel een gemeten licentie in
Nadat u uw openbare en persoonlijke sleutels hebt ontvangen, kunt u de gemeten licentie instellen in uw .NET-toepassing.
```csharp
string publicKey = "*****"; // Vervang ***** door uw openbare sleutel
string privateKey = "*****"; // Vervang ***** door uw persoonlijke sleutel
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Conclusie
Kortom, het instellen van een gelimiteerde licentie voor GroupDocs.Annotation .NET is een eenvoudig proces dat zorgt voor efficiënt resourcegebruik en kosteneffectiviteit voor uw documentannotatieprojecten. Door de stappen in deze tutorial te volgen, kunt u GroupDocs.Annotation naadloos integreren in uw .NET-applicatie en de mogelijkheden voor samenwerking en review van documenten verbeteren.
## Veelgestelde vragen
### Kan ik GroupDocs.Annotation voor .NET gebruiken in commerciële projecten?
Ja, GroupDocs.Annotation voor .NET kan worden gebruikt in zowel commerciële als niet-commerciële projecten. U moet echter wel een geschikte licentie aanschaffen op basis van uw projectvereisten.
### Is er een proefversie beschikbaar voor GroupDocs.Annotation voor .NET?
Ja, u kunt een gratis proefversie van GroupDocs.Annotation voor .NET gebruiken door naar [deze link](https://releases.groupdocs.com/).
### Hoe kan ik technische ondersteuning krijgen voor GroupDocs.Annotation voor .NET?
U kunt technische ondersteuning krijgen door het GroupDocs-forum te bezoeken [hier](https://forum.groupdocs.com/c/annotation/10).
### Zijn er tijdelijke licentieopties beschikbaar?
Ja, u kunt een tijdelijke licentie van GroupDocs verkrijgen voor kortdurend gebruik of evaluatiedoeleinden. Bezoek [deze link](https://purchase.groupdocs.com/temporary-license/) voor meer informatie.
### Kan ik de annotatiefuncties aanpassen aan de vereisten van mijn project?
Ja, GroupDocs.Annotation voor .NET biedt uitgebreide aanpassingsopties, waarmee u de annotatiefuncties kunt afstemmen op uw specifieke projectbehoeften.