---
categories:
- Document Processing
date: '2026-10-05'
description: Leer hoe je annotaties kunt verbergen tijdens het genereren van schone
  documentpreviews in C# met GroupDocs.Annotation .NET. Stapsgewijze handleiding met
  codevoorbeelden, prestatie‑tips en probleemoplossing.
keywords:
- how to hide annotations
- preview document without annotations
- remove annotations from preview
- clean document preview .NET
- generate document preview without annotations
lastmod: '2026-10-05'
linktitle: Documentpreview zonder annotaties
og_description: Leer hoe je annotaties kunt verbergen tijdens het genereren van schone
  documentpreviews in C#. Deze gids behandelt installatie, code, prestatie‑tips en
  probleemoplossing.
og_image_alt: Guide showing how to generate document preview without annotations using
  GroupDocs.Annotation for .NET
og_title: Hoe annotaties verbergen bij het genereren van een documentpreview in C#
schemas:
- author: GroupDocs
  dateModified: '2026-10-05'
  description: Learn how to hide annotations while generating clean document previews
    in C# using GroupDocs.Annotation .NET. Step-by-step guide with code examples,
    performance tips, and troubleshooting.
  headline: How to hide annotations when generating document preview in C#
  type: TechArticle
- description: Learn how to hide annotations while generating clean document previews
    in C# using GroupDocs.Annotation .NET. Step-by-step guide with code examples,
    performance tips, and troubleshooting.
  name: How to hide annotations when generating document preview in C#
  steps:
  - name: initialize your annotator (the foundation)
    text: The `Annotator` class loads a document and provides methods for rendering
      and annotation manipulation. csharp using (Annotator annotator = new Annotator("path/to/your/document"))
      { // All your preview generation happens within this scope }
  - name: configure your preview options (this is where the magic happens)
    text: The `PreviewOptions` class defines rendering parameters such as format,
      resolution, and whether annotations are included. csharp // Define how each
      page should be handled during preview generation PreviewOptions previewOptions
      = new PreviewOptions(pageNumber => { var pagePath = $"output_directory\\r
  - name: generate the preview (the payoff)
    text: The `GeneratePreview` method processes the document according to the supplied
      options and returns file paths for the created images. csharp annotator.Document.GeneratePreview(previewOptions);
  type: HowTo
- questions:
  - answer: Absolutely! GroupDocs.Annotation supports over 50 formats—including PDF,
      PPTX, XLSX, and common image types. See the [documentation](https://docs.groupdocs.com/annotation/net/)
      for the full list.
    question: Can I preview documents other than DOCX files?
  - answer: Initialise the `Annotator` with a `LoadOptions` object that includes the
      password. The `LoadOptions` class lets you specify the document password and
      other loading parameters.
    question: How do I handle password‑protected documents?
  - answer: Yes. The same code works in ASP.NET, but store generated images in a temporary
      folder and clean them up after the response to avoid disk bloat.
    question: Can I generate previews in a web application?
  - answer: PNG offers the highest quality, JPEG loads faster, and WebP provides the
      best compression if your target browsers support it. PNG is the safest default.
    question: What’s the best output format for web display?
  - answer: Process pages in batches of 5‑10, monitor memory usage, and optionally
      show a progress bar to improve the user experience.
    question: How do I handle very large documents efficiently?
  type: FAQPage
tags:
- groupdocs
- document-preview
- annotations
- dotnet
- csharp
title: Hoe annotaties verbergen bij het genereren van een documentpreview in C#
type: docs
url: /nl/net/document-preview/create-document-preview-without-annotations-groupdocs-dotnet/
weight: 1
---

# Hoe annotaties verbergen bij het genereren van documentpreview in C#

Als je een documentpreview wilt delen maar **annotaties wilt verbergen**, ben je hier op de juiste plek. Deze tutorial laat zien hoe je schone, annotatie‑vrije previews genereert in C# met GroupDocs.Annotation voor .NET, en behandelt alles van installatie tot prestatie‑optimalisatie.

## Snelle antwoorden
- **Welke primaire klasse maakt de preview?** De `Annotator`‑klasse.
- **Welke optie schakelt annotaties uit?** Stel `RenderAnnotations = false` in `PreviewOptions` in.
- **Minimale .NET‑versie?** .NET 6 wordt aanbevolen; .NET Core 3.1 werkt ook.
- **Kan ik PDF‑ en Word‑bestanden previewen?** Ja – meer dan 50 formaten worden ondersteund.
- **Heb ik een licentie nodig voor testen?** Een tijdelijke licentie is beschikbaar voor gratis proefversies.

## Wat is het verbergen van annotaties?
*Hoe annotaties te verbergen* is het proces van het genereren van documentpreview‑afbeeldingen terwijl elke opmerking, markering of markup in het bronbestand wordt onderdrukt. Deze techniek zorgt ervoor dat de visuele output alleen de originele inhoud bevat, waardoor het geschikt is voor openbare distributie, klantpresentaties, of elke situatie waarin interne notities verborgen moeten blijven.

## Waarom je schone documentpreviews nodig hebt (en hoe je ze krijgt)
Wanneer je een preview deelt met klanten, partners of het publiek, kunnen interne opmerkingen onprofessioneel overkomen of zelfs vertrouwelijke strategie onthullen. Schone previews houden de focus op de inhoud en beschermen je workflow. GroupDocs.Annotation stelt je in staat om de weergave van annotaties in of uit te schakelen, zodat je zowel geannoteerde als schone versies kunt produceren vanuit hetzelfde bronbestand.

## Wat je nodig hebt voordat je begint

### Wat zijn de vereisten?
Om te beginnen heb je de volgende componenten nodig die op je ontwikkelmachine geïnstalleerd zijn. Het klaar hebben van deze items zorgt ervoor dat de code zonder runtime‑fouten draait en dat je de volledige preview‑pipeline lokaal kunt testen.

- GroupDocs.Annotation voor .NET 25.4.0 of later (de nieuwste release voegt geheugen‑geoptimaliseerde preview‑generatie toe).
- Visual Studio 2022 of een andere .NET‑compatibele IDE.
- Een geldige GroupDocs‑licentie (tijdelijke licenties zijn gratis voor evaluatie).

## Snelle installatie: GroupDocs.Annotation in je project krijgen

### Optie 1: NuGet Package Manager Console
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```

### Optie 2: .NET CLI (mijn persoonlijke voorkeur)
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

**Pro tip:** Houd de pakketversie consistent voor alle teamleden om subtiele weergaveverschillen te voorkomen.

Verifieer de installatie met een korte sanity‑check:
```csharp
using System.IO;
using GroupDocs.Annotation;

// This should compile without errors
using (Annotator annotator = new Annotator("path/to/document"))
{
    // You're good to go!
}
```

## Hoe kun je een preview genereren zonder annotaties?
Laad het document met `Annotator`, configureer `PreviewOptions` en roep `GeneratePreview` aan. Het instellen van `RenderAnnotations = false` vertelt de engine om elke opmerking, markering en stempel uit de uitvoerafbeeldingen weg te laten.

### Stap 1: initialiseert je annotator (de basis)
De `Annotator`‑klasse laadt een document en biedt methoden voor rendering en annotatie‑manipulatie.  
```csharp
```csharp
using (Annotator annotator = new Annotator("path/to/your/document"))
{
    // All your preview generation happens within this scope
}
```
```

### Stap 2: configureer je preview‑opties (hier gebeurt de magie)
De `PreviewOptions`‑klasse definieert render‑parameters zoals formaat, resolutie en of annotaties zijn inbegrepen.  
```csharp
```csharp
// Define how each page should be handled during preview generation
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = $"output_directory\\result{pageNumber}.png";
    return File.Create(pagePath);
});

// Set the output format for the preview as PNG
previewOptions.PreviewFormat = PreviewFormats.PNG;

// Specify which pages to include in the preview generation
previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};

// The key setting: disable rendering of annotations
previewOptions.RenderAnnotations = false;
```
```

### Stap 3: genereer de preview (de beloning)
De `GeneratePreview`‑methode verwerkt het document volgens de opgegeven opties en retourneert bestands‑paden voor de gemaakte afbeeldingen.  
```csharp
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
```

## Veelvoorkomende problemen (en hoe ze op te lossen)

### Probleem 1: “Bestand niet gevonden” fouten
**Symptomen:** Er wordt een uitzondering gegooid wanneer de `Annotator` wordt aangemaakt.  
**Oplossing:** Gebruik absolute paden of controleer of je relatieve paden correct zijn. Een snelle sanity‑check ziet er als volgt uit:
```csharp
string fullPath = Path.GetFullPath("your-document.pdf");
using (Annotator annotator = new Annotator(fullPath))
```

### Probleem 2: Slechte preview‑kwaliteit
**Symptomen:** Uitvoer‑afbeeldingen lijken wazig of gepixeld.  
**Oplossing:** Verhoog de DPI‑instelling in `PreviewOptions` om de helderheid te verbeteren:
```csharp
previewOptions.Width = 1920;  // Higher resolution
previewOptions.Height = 1080;
```

### Probleem 3: Geheugenproblemen met grote documenten
**Symptomen:** `OutOfMemoryException` of merkbaar trage verwerking.  
**Oplossing:** Verwerk pagina’s in batches in plaats van het volledige bestand in één keer te laden:
```csharp
// Process 5 pages at a time instead of all at once
previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5};
```

## Praktijkvoorbeelden (waar dit echt van belang is)

### Juridisch document delen
Advocatenkantoren kunnen contractpreviews distribueren die interne onderhandelingsnotities verbergen, waardoor klantcommunicatie professioneel blijft.

### Academisch publiceren
Onderzoekers kunnen schone manuscript‑concepten delen na een ronde peer‑review, waarbij beoordelaars‑commentaren worden verwijderd vóór indiening bij een tijdschrift.

### Zakelijke rapportage
Belanghebbenden ontvangen gepolijste rapporten zonder “verifieer dit getal” of “update vóór bestuursvergadering” notities, die anders het vertrouwen kunnen ondermijnen.

### Documentarchivering
Compliance‑teams slaan annotatie‑vrije kopieën op om te voldoen aan regelgeving, terwijl ze de originele geannoteerde versie voor intern gebruik behouden.

## Prestatie‑best practices

### Hoe moet je geheugen beheren voor grote bestanden?
Verwerk pagina’s in kleine batches en maak de `Annotator` snel vrij. Deze aanpak vermindert het piek‑geheugengebruik met tot 60 % bij documenten groter dan 200 pagina’s.
```csharp
// Good: Dispose properly
using (Annotator annotator = new Annotator(documentPath))
{
    // Generate preview
} // Automatically disposed here

// Avoid: Manual disposal (easy to forget)
Annotator annotator = new Annotator(documentPath);
// ... use annotator
annotator.Dispose(); // Easy to forget or skip due to exceptions
```

### Hoe kun je batch‑verwerking versnellen?
Verdeel een document van 100 pagina’s in groepen van 10 pagina’s, genereer elke groep opeenvolgend en schrijf de resultaten naar een tijdelijke map. Deze techniek verkort de totale verwerkingstijd met ongeveer 30 % op typische serverhardware.
```csharp
// Process in batches of 10 pages
for (int startPage = 1; startPage <= totalPages; startPage += 10)
{
    int endPage = Math.Min(startPage + 9, totalPages);
    var pageRange = Enumerable.Range(startPage, endPage - startPage + 1).ToArray();
    
    previewOptions.PageNumbers = pageRange;
    annotator.Document.GeneratePreview(previewOptions);
}
```

### Hoe kies je het optimale uitvoerformaat?
- **PNG:** Beste visuele getrouwheid; ideaal voor gedetailleerde schema’s.  
- **JPEG:** Kleinere bestandsgrootte; geschikt voor tekst‑zware documenten waarbij lichte compressie‑artefacten acceptabel zijn.  
- **WebP:** Modern formaat met uitstekende compressie; controleer browserondersteuning voordat je het adopteert.

## Geavanceerde configuratie‑opties

### Hoe kun je bestandsnaam aanpassen?
De `PreviewOptions`‑lambda stelt je in staat paginanummers, tijdstempels of aangepaste identifiers in elke bestandsnaam in te voegen.
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    string timestamp = DateTime.Now.ToString("yyyyMMdd_HHmmss");
    var pagePath = $"previews\\{timestamp}_page_{pageNumber:D3}.png";
    return File.Create(pagePath);
});
```

### Hoe beheer je de beeldkwaliteit?
Pas de `Width`, `Height` en `Resolution`‑eigenschappen in `PreviewOptions` aan. Grotere afmetingen geven hogere kwaliteit, maar vergroten de bestandsgrootte.
```csharp
previewOptions.Width = 2400;   // Higher resolution
previewOptions.Height = 3200;  // Maintains aspect ratio
previewOptions.PreviewFormat = PreviewFormats.PNG; // Best quality
```

### Hoe kun je alleen specifieke pagina’s verwerken?
Stel de `PageNumbers`‑collectie in op de exacte pagina’s die je nodig hebt, waardoor I/O wordt verminderd en de generatie voor documenten met honderden pagina’s wordt versneld.
```csharp
// Only process odd pages (useful for double-sided documents)
var oddPages = Enumerable.Range(1, totalPages)
                        .Where(p => p % 2 == 1)
                        .ToArray();
previewOptions.PageNumbers = oddPages;
```

## Probleemoplossingsgids

### Waarom faalt preview‑generatie stilletjes?
Veelvoorkomende oorzaken zijn:
1. Uitvoermap ontbreekt of heeft geen schrijfrechten.  
2. Wachtwoord‑beveiligde bron‑documenten.  
3. Niet‑ondersteund bestandsformaat.  
4. Onvoldoende systeemgeheugen.

### Waarom worden annotaties nog steeds weergegeven?
Zorg ervoor dat `RenderAnnotations = false` is ingesteld op de `PreviewOptions`‑instantie voordat je `GeneratePreview` aanroept. De `RenderAnnotations`‑eigenschap bepaalt of annotatielagen worden getekend tijdens het renderen van de preview.
```csharp
previewOptions.RenderAnnotations = false;  // Must be explicitly false
previewOptions.RenderComments = false;     // Also disable comments if needed
```

### Waarom is de prestatie traag?
- Verlaag de resolutie tijdens het testen.  
- Verwerk minder pagina’s per batch.  
- Controleer of je de nieuwste GroupDocs.Annotation‑versie (25.4.0 of nieuwer) gebruikt, die prestatie‑verbeteringen bevat.

## Wanneer je deze aanpak NIET moet gebruiken
- **Realtime preview:** Voor directe, on‑the‑fly previews kan client‑side rendering sneller zijn.  
- **Interactieve documenten:** Formulieren of ingesloten scripts kunnen functionaliteit verliezen wanneer ze als statische afbeeldingen worden gerenderd.  
- **Schaalbare graphics:** Als je vector‑gebaseerde output nodig hebt (bijv. SVG), overweeg dan PDF‑pagina’s te genereren in plaats van raster‑afbeeldingen.

## Samenvatting
Het genereren van schone documentpreviews zonder annotaties is eenvoudig met GroupDocs.Annotation voor .NET. Vergeet niet:

1. Maak `Annotator` correct vrij.  
2. Stel `RenderAnnotations = false` in `PreviewOptions` in.  
3. Verwerk grote bestanden in batches om het geheugengebruik laag te houden.  
4. Test met real‑world documenten om DPI en formaatkeuzes fijn af te stemmen.

Begin met een eenvoudig testbestand, experimenteer met de bovenstaande opties, en je hebt professionele, annotatie‑vrije previews klaar voor elk publiek.

## Veelgestelde vragen

**Q: Kan ik documenten previewen anders dan DOCX‑bestanden?**  
A: Absoluut! GroupDocs.Annotation ondersteunt meer dan 50 formaten — waaronder PDF, PPTX, XLSX en veelvoorkomende afbeeldings‑typen. Zie de [documentatie](https://docs.groupdocs.com/annotation/net/) voor de volledige lijst.

**Q: Hoe ga ik om met wachtwoord‑beveiligde documenten?**  
A: Initialiseert de `Annotator` met een `LoadOptions`‑object dat het wachtwoord bevat. De `LoadOptions`‑klasse stelt je in staat het documentwachtwoord en andere laad‑parameters op te geven.
```csharp
LoadOptions loadOptions = new LoadOptions { Password = "your-password" };
using (Annotator annotator = new Annotator("protected-doc.pdf", loadOptions))
```

**Q: Kan ik previews genereren in een webapplicatie?**  
A: Ja. dezelfde code werkt in ASP.NET, maar sla de gegenereerde afbeeldingen op in een tijdelijke map en maak ze op na de respons om schijfruimte‑opbouw te voorkomen.

**Q: Wat is het beste uitvoerformaat voor weergave op het web?**  
A: PNG biedt de hoogste kwaliteit, JPEG laadt sneller, en WebP biedt de beste compressie als je doel‑browsers het ondersteunen. PNG is de veiligste standaard.

**Q: Hoe ga je efficiënt om met zeer grote documenten?**  
A: Verwerk pagina’s in batches van 5‑10, monitor het geheugengebruik, en toon eventueel een voortgangsbalk om de gebruikerservaring te verbeteren.

**Q: Kan ik de kwaliteit van de uitvoerafbeelding aanpassen?**  
A: Ja — pas `Width`, `Height` en `Resolution` aan in `PreviewOptions`. Grotere waarden verhogen de kwaliteit maar ook de bestandsgrootte.

**Q: Wat als ik zowel geannoteerde als schone versies nodig heb?**  
A: Voer de preview twee keer uit — één keer met `RenderAnnotations = true` en één keer met `false`. Sla elke set op in aparte mappen voor gemakkelijke toegang.

## Bronnen
- [GroupDocs.Annotation .NET Documentatie](https://docs.groupdocs.com/annotation/net/)  
- [GroupDocs Annotation API Referentie](https://reference.groupdocs.com/annotation/net/)  
- [GroupDocs Releases voor .NET](https://releases.groupdocs.com/annotation/net/)  
- [Koop GroupDocs Licentie](https://purchase.groupdocs.com/buy)  
- [GroupDocs Gratis Proefversies](https://releases.groupdocs.com/annotation/net/)  
- [Vraag Tijdelijke Licentie Aan](https://purchase.groupdocs.com/temporary-license/)  
- [GroupDocs Forum](https://forum.groupdocs.com/c/annotation/)  

**Laatst bijgewerkt:** 2026-10-05  
**Getest met:** GroupDocs.Annotation 25.4.0 voor .NET  
**Auteur:** GroupDocs

## Gerelateerde tutorials
- [Hoe PDF-annotaties verwijderen C# – GroupDocs.Annotation Gids](/annotation/net/annotation-management/remove-annotations-groupdocs-annotation-dotnet/)
- [Documentpreviews genereren zonder opmerkingen in .NET](/annotation/net/document-preview/groupdocs-annotation-net-document-preview-no-comments/)
- [Aangepaste lettertypen laden .NET - GroupDocs.Annotation Integratiegids](/annotation/net/advanced-usage/loading-custom-fonts/)