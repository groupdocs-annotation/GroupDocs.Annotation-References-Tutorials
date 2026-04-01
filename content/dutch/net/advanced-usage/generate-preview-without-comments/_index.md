---
categories:
- Document Processing
date: '2026-04-01'
description: Leer hoe u thumbnails genereert in .NET zonder opmerkingen met GroupDocs.Annotation.
  Deze gids behandelt hoe u annotaties verbergt, de voorbeeldweergave van opmerkingen
  verwijdert en schone PDF-voorvertoningen maakt.
keywords:
- how to generate thumbnails
- how to hide annotations
- remove comments preview
- document preview without comments
- clean pdf preview
lastmod: '2026-04-01'
linktitle: Voorbeeld genereren zonder opmerkingen
second_title: GroupDocs.Annotation .NET API
tags:
- document-preview
- pdf-thumbnails
- groupdocs
- dotnet
title: Hoe miniaturen te genereren in .NET – Schone PDF-voorbeelden
type: docs
url: /nl/net/advanced-usage/generate-preview-without-comments/
weight: 14
---

# Hoe miniatuurafbeeldingen te genereren in .NET – Schone PDF‑voorbeelden

## Introductie

Heb je ooit **hoe miniatuurafbeeldingen te genereren** nodig gehad voor een documentviewer, bestandsverkenner of content‑managementsysteem, terwijl je de afbeeldingen vrij houdt van gebruikersnotities? Je bent niet de enige. Veel .NET‑ontwikkelaars lopen tegen een muur aan wanneer ze documentvoorbeelden willen maken die annotaties en opmerkingen verbergen.  

In deze tutorial lopen we de exacte stappen door om schone PDF‑voorbeelden te produceren met behulp van **GroupDocs.Annotation for .NET**. Je zult zien hoe je annotaties verbergt, voorbeeld van opmerkingen verwijdert, en professioneel uitziende miniatuurafbeeldingen genereert die perfect passen in galerijen, dashboards of elke UI waar een rommelvrije snapshot vereist is.

## Snelle antwoorden
- **Welke bibliotheek maakt commentaar‑vrije miniatuurafbeeldingen?** GroupDocs.Annotation for .NET  
- **Welke eigenschap schakelt annotaties uit?** `RenderComments = false`  
- **Kan ik het afbeeldingsformaat kiezen?** Ja – PNG, JPEG, BMP, enz. via `PreviewFormat`  
- **Heb ik een licentie nodig voor productie?** Een commerciële licentie is vereist; een tijdelijke licentie werkt voor testen.  
- **Is het alleen voor .NET?** Werkt met .NET Framework, .NET Core en .NET 5/6+.

## Wat is miniatuurgeneratie zonder opmerkingen?

Miniatuurgeneratie zonder opmerkingen betekent het renderen van een visueel momentopname van elke pagina **zonder** enige markering, notities of collaboratieve annotaties die aan het originele bestand kunnen zijn toegevoegd. Het resultaat is een schone, statische afbeelding die de ware inhoud van het document weergeeft—ideaal voor publieke portals, juridische archieven, of elke situatie waarin interne opmerkingen verborgen moeten blijven.

## Waarom annotaties verbergen bij het maken van voorbeelden?

- **Professionele uitstraling:** Eindgebruikers zien alleen de inhoud van het document, niet de review‑gesprekken.  
- **Beveiliging & privacy:** Gevoelige opmerkingen blijven intern.  
- **Prestaties:** Het renderen van minder lagen versnelt het maken van afbeeldingen.  
- **Consistentie:** Miniatuurafbeeldingen komen overeen met afgedrukte of geëxporteerde versies die ook opmerkingen weglaten.

## Voorvereisten

### 1. Installeer GroupDocs.Annotation for .NET
Download het pakket van de officiële distributiepagina **[here](https://releases.groupdocs.com/annotation/net/)** of installeer het via NuGet. Zorg ervoor dat je project zich richt op een ondersteunde .NET‑versie.

### 2. Verkrijg een licentie
Een commerciële licentie is vereist voor productiegebruik. Koop er één **[here](https://purchase.groupdocs.com/buy)** of vraag een tijdelijke evaluatielicentie aan **[here](https://purchase.groupdocs.com/temporary-license/)**.

### 3. .NET‑kennis
Je moet vertrouwd zijn met de basis van C#, bestands‑I/O, en het gebruik van `using`‑statements voor resource‑beheer.

## Namespaces importeren

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

## Stapsgewijze handleiding: Schone documentvoorbeelden genereren

### Stap 1: Initialiseer de Annotator
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
Het `Annotator`‑object laadt het bronbestand. Het `using`‑blok garandeert dat alle niet‑beheerde resources worden vrijgegeven zodra we klaar zijn.

### Stap 2: Configureer preview‑opties
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
Hier vertellen we de bibliotheek waar elke paginabeeld moet worden opgeslagen. De lambda ontvangt het paginanummer en retourneert een schrijfbare `FileStream`.

### Stap 3: Kies formaat en pagina's
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
PNG levert scherpe miniatuurafbeeldingen, maar je kunt overschakelen naar JPEG als de bestandsgrootte een grotere zorg is. Het selecteren van een subset van pagina's vermindert de verwerkingstijd—perfect voor miniatuurgalerijen die alleen de eerste paar pagina's nodig hebben.

### Stap 4: Schakel het renderen van opmerkingen uit
```csharp
    previewOptions.RenderComments = false;
```
**Deze regel is de sleutel tot “hoe annotaties te verbergen.”** Het instellen van `RenderComments` op `false` verwijdert alle commentaarlagen, waardoor je een schoon PDF‑voorbeeld krijgt.

### Stap 5: Genereer de preview‑afbeeldingen
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
De bibliotheek verwerkt het document en schrijft de afbeeldingen naar de locaties die je eerder hebt gedefinieerd.

## Best practices voor documentpreview‑generatie

- **Resize voor miniatuurafbeeldingen:** Na het genereren van PNG's, overweeg ze te verkleinen tot ~200 × 300 px voor snellere UI‑lading.  
- **Verwerk grote bestanden in batches:** Genereer aanvankelijk alleen de eerste paar pagina's, maak de rest vervolgens on‑demand.  
- **Wrap altijd in `using`:** Garandeert correcte geheugen‑opschoning, vooral bij het verwerken van veel documenten.  
- **Voeg foutafhandeling toe:** Vang `FileNotFoundException`, `InvalidOperationException` en licentiefouten op om je app robuust te houden.

## Veelvoorkomende problemen en probleemoplossing

- **Geen afbeeldingen zichtbaar:** Controleer of de uitvoermap bestaat en de app schrijfrechten heeft.  
- **Vage miniatuurafbeeldingen:** Probeer de DPI te verhogen door `previewOptions.Dpi = 150;` in te stellen (niet getoond in de code om het originele blok intact te houden).  
- **Out‑of‑memory‑fouten bij enorme PDF's:** Verwerk pagina's één voor één, of gebruik de async‑API in een achtergrondworker.  
- **Licentie niet gevonden:** Zorg ervoor dat het `License`‑object is geladen voordat je de `Annotator` maakt.

## Tips voor prestatie‑optimalisatie

- **Batch meerdere documenten:** Loop door een collectie en hergebruik een enkele `Annotator`‑instantie wanneer mogelijk.  
- **Async generatie:** Schuif preview‑creatie naar een achtergrondservice zodat de UI responsief blijft.  
- **Cache resultaten:** Sla gegenereerde miniatuurafbeeldingen op in een CDN of lokale cache om herverwerking van hetzelfde bestand te vermijden.  
- **Kies het juiste formaat:** PNG voor verliesloze kwaliteit, JPEG voor kleinere bestanden wanneer het document veel afbeeldingen bevat.

## Ondersteunde documentformaten

GroupDocs.Annotation for .NET kan previews genereren voor:

- **PDF** – het meest voorkomende gebruiksscenario.  
- **Microsoft Office** – DOCX, XLSX, PPTX, en hun oudere tegenhangers.  
- **Afbeeldingen** – TIFF, JPEG, PNG, BMP (handig voor gescande documenten).  
- **OpenDocument** – ODT, ODS, ODP, en andere open standaarden.

## Wanneer commentaar‑vrije preview‑generatie te gebruiken

- **Publieke portals** waar interne review‑notities verborgen moeten blijven.  
- **Archiefbrowsers** die een schoon miniatuurgitter tonen.  
- **Print‑ready workflows** die de uiteindelijke weergave moeten tonen voordat ze naar een printer worden gestuurd.  
- **Kwaliteitscontroles** waarbij je “met opmerkingen” versus “zonder opmerkingen” versies vergelijkt.

## Conclusie

Je weet nu **hoe miniatuurafbeeldingen te genereren** in .NET terwijl je annotaties en opmerkingen volledig verwijdert. Door `RenderComments = false` in te stellen, krijg je schone, professionele PDF‑voorbeelden die perfect passen in elke UI. Vergeet niet het preview‑formaat, de paginaselectie en de afbeeldingsdimensies aan te passen aan je specifieke scenario, en behandel licenties en foutgevallen altijd zorgvuldig. Met deze stappen levert je applicatie snelle, rommelvrije documentminiatuurafbeeldingen die de gebruikerservaring verbeteren.

## Veelgestelde vragen

**Q: Is GroupDocs.Annotation for .NET compatibel met alle documentformaten?**  
A: Ja. Het ondersteunt PDF, DOCX, PPTX, XLSX, gangbare afbeeldingsformaten en vele OpenDocument‑formaten.

**Q: Kan ik het uiterlijk van de gegenereerde previews aanpassen?**  
A: Absoluut. Je kunt `PreviewFormat` wijzigen, afbeeldingsdimensies, DPI instellen en specifieke pagina's kiezen om te renderen.

**Q: Ondersteunt de bibliotheek multi‑user samenwerking?**  
A: GroupDocs.Annotation biedt collaboratieve annotatiefuncties. De preview‑generatie kan worden gebruikt om schone weergaven te maken die alle gebruikerscommentaren verbergen.

**Q: Waar kan ik hulp krijgen als ik tegen problemen aanloop?**  
A: De community en het supportteam zijn actief op het **[support forum](https://forum.groupdocs.com/c/annotation/10)** waar je vragen kunt stellen en ervaringen kunt delen.

**Q: Is er een gratis proefversie beschikbaar?**  
A: Ja, je kunt een volledige proefversie downloaden **[here](https://releases.groupdocs.com/)** om de preview‑generatiefuncties te testen voordat je een aankoop doet.

---

**Laatst bijgewerkt:** 2026-04-01  
**Getest met:** GroupDocs.Annotation for .NET (latest release)  
**Auteur:** GroupDocs  

---