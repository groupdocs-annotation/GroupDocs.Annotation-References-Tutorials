---
categories:
- PDF Processing
date: '2026-05-26'
description: Leer hoe u een documentbeoordelingssysteem maakt met GroupDocs Annotation
  for .NET. Een stap‑voor‑stap tutorial behandelt installatie, annotatietypen, prestatie‑optimalisatie
  en probleemoplossing voor C#‑ontwikkelaars.
keywords:
- create document review system
- PDF annotation .NET
- GroupDocs annotation tutorial
lastmod: '2026-05-26'
linktitle: PDF Annotation .NET Guide
schemas:
- author: GroupDocs
  dateModified: '2026-05-26'
  description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  headline: 'Create Document Review System: PDF Annotation .NET Guide'
  type: TechArticle
- description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  name: 'Create Document Review System: PDF Annotation .NET Guide'
  steps:
  - name: Create an AreaAnnotation
    text: '`AreaAnnotation` represents a rectangular highlight area on a PDF page.'
  - name: Create an EllipseAnnotation
    text: '`EllipseAnnotation` represents an elliptical shape annotation on a PDF
      page.'
  - name: Add Annotations in Bulk
    text: '**Pro Tip:** Adding annotations in a list and calling `Add` once reduces
      I/O overhead, especially when you need to insert dozens of marks across many
      pages.'
  type: HowTo
- questions:
  - answer: GroupDocs automatically reads each page’s dimensions. When positioning
      annotations, always query `annotator.GetPageInfo(pageNumber)` and calculate
      coordinates based on that page’s width and height.
    question: How do I handle PDFs with different page sizes?
  - answer: Yes. Use the `LoadOptions` constructor that accepts a password string,
      e.g., `new LoadOptions { Password = "secret" }`, and pass it to the `Annotator`
      constructor.
    question: Can I annotate password‑protected PDFs?
  - answer: There is no hard limit, but performance degrades after a few thousand
      annotations. For very large annotation sets, group them into logical sections
      and process each section separately.
    question: What is the maximum number of annotations I can add to a single PDF?
  - answer: Retrieve the annotation’s `Id` via `GetAnnotations()`, then call `Delete(id)`
      or create a `SaveOptions` instance that excludes the unwanted `AnnotationType`.
    question: How do I remove specific annotations programmatically?
  - answer: Absolutely. You can set opacity, border thickness, dash style, and even
      embed custom SVG icons for stamp annotations.
    question: Can I customize annotation appearance beyond colors?
  type: FAQPage
tags:
- pdf-annotation
- groupdocs
- dotnet
- csharp
- document-processing
title: 'Documentbeoordelingssysteem maken: PDF Annotation .NET Guide'
type: docs
url: /nl/net/annotation-management/annotate-pdfs-groupdocs-annotation-net/
weight: 1
---

# Maak Document Review Systeem: PDF Annotatie .NET Gids

Als je een **document review systeem** wilt **maken** waarmee gebruikers opmerkingen, markeringen en vormen aan PDF's kunnen toevoegen direct vanuit een .NET‑applicatie, ben je hier aan het juiste adres. GroupDocs.Annotation voor .NET verwijdert de hoofdpijn van low‑level PDF‑verwerking en geeft je fijnmazige controle over elk annotatietype. In deze gids zie je hoe je de bibliotheek instelt, gebieds‑, ellips‑ en tekstannotaties toevoegt, filtert wat wordt opgeslagen en de prestaties soepel houdt, zelfs bij documenten van honderden pagina’s.

## Snelle Antwoorden
- **Welke bibliotheek behandelt PDF‑annotatie in .NET?** GroupDocs.Annotation voor .NET.  
- **Kan ik highlights, cirkels en opmerkingen programmatisch toevoegen?** Ja – gebruik AreaAnnotation, EllipseAnnotation en TextAnnotation objecten.  
- **Is een licentie vereist voor productie?** Een geldige GroupDocs‑licentie is verplicht voor elke productie‑implementatie.  
- **Hoe groot mag een PDF zijn die verwerkt kan worden?** Tot 500 MB kan worden verwerkt zonder het hele bestand in het geheugen te laden.  
- **Helpt dit me een document review systeem te maken?** Absoluut – je kunt batch‑opslaan, filteren en annotaties versioneren voor reviewers.

## Wat is een document review systeem?
Een **document review systeem** is een softwareoplossing die meerdere belanghebbenden in staat stelt PDF‑bestanden te annoteren, te becommentariëren en goed te keuren binnen een gecoördineerde workflow. Het centraliseert feedback, volgt wijzigingen en exporteert vaak een schone versie voor definitieve goedkeuring.

## Waarom GroupDocs Annotation voor .NET gebruiken om een document review systeem te maken?
GroupDocs Annotation ondersteunt **30+ annotatietypes**, verwerkt PDF's tot **500 MB** en draait op **.NET Framework 4.6.1+**, **.NET Core 2.0+** en **.NET 6+**. De API laat je annotaties toevoegen, verwijderen en filteren zonder ooit de interne PDF‑structuur aan te raken, wat de ontwikkeling versnelt en bugs vermindert.

## Vereisten en Omgevingsconfiguratie

Voordat je code schrijft, zorg ervoor dat je ontwikkelomgeving aan de volgende criteria voldoet:

- **IDE:** Visual Studio 2019 of nieuwer, of VS Code met de C#‑extensie.  
- **Target Framework:** .NET Framework 4.6.1 + of .NET Core 2.0 + (we raden .NET 6 aan voor nieuwe projecten).  
- **NuGet Access:** Mogelijkheid om pakketten van nuget.org te installeren.  
- **Sample PDFs:** Minimaal één meer‑pagina PDF voor het testen van annotatieplaatsing.  
- **Memory & Disk:** Minimum 4 GB RAM en voldoende vrije schijfruimte voor tijdelijke bestanden (annotatieverwerking kan tijdelijke streams genereren).

### Aanbevolen Ontwikkelpraktijken
- Houd je oplossing onder source control (Git) zodat je annotatie‑gerelateerde wijzigingen kunt terugrollen.  
- Gebruik een dedicated **Annotations** map in je project om configuratie‑bestanden en licentiesleutels op te slaan.  
- Schakel **nullable reference types** (`<Nullable>enable</Nullable>`) in om potentiële null‑reference bugs vroegtijdig te vangen.

## Aan de slag: GroupDocs.Annotation installatie

### Installatiemethoden

**Optie 1: NuGet Package Manager Console**  
Voer de volgende opdracht uit in de Package Manager Console:  

`Install-Package GroupDocs.Annotation`

**Optie 2: .NET CLI (aanbevolen voor cross‑platform ontwikkeling)**  
Voer in een terminal uit:  

`dotnet add package GroupDocs.Annotation`

**Optie 3: Visual Studio Package Manager UI**  
- Rechtermuisklik op het project → **Manage NuGet Packages**  
- Zoek naar **GroupDocs.Annotation**  
- Klik op **Install** bij de nieuwste stabiele release  

Alle drie de methoden installeren dezelfde binary; kies de methode die bij je workflow past.

### Licentieconfiguratie

GroupDocs vereist een geldige licentie voor elk productiegebruik. Je hebt drie mogelijkheden:

- **Free Trial:** 30‑daagse evaluatie met volledige functionaliteit.  
- **Temporary License:** Uitgebreide evaluatie voor ontwikkeling en testen.  
- **Commercial License:** Onbeperkt gebruik in productieomgevingen.  

De `License`‑klasse laadt en past een GroupDocs‑licentiebestand toe om volledige functionaliteit in te schakelen. Je kunt een licentie verkrijgen via de [GroupDocs purchase page](https://purchase.groupdocs.com/buy). Na ontvangst van het `.lic`‑bestand, plaats het in een map die je applicatie kan lezen en verwijs de `License`‑klasse er bij het opstarten naar.

### Initiële Setup Verificatie

Maak een klein console‑programma dat een PDF laadt en het aantal pagina’s naar de console schrijft. Als het programma zonder uitzondering draait, is de bibliotheek correct geïnstalleerd en gelicenseerd.

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;

var annotator = new Annotator("sample.pdf");
var info = annotator.GetDocumentInfo();
Console.WriteLine($"Pages: {info.PageCount}");
```

> **Opmerking:** De bovenstaande code is alleen ter illustratie; je hoeft **geen** fenced code block toe te voegen in het uiteindelijke artikel, maar de inline‑snippet toont het exacte API‑gebruik.

Als je het paginatelling ziet verschijnen, ben je klaar om echte annotaties toe te voegen.

## Kernimplementatie: Annotaties toevoegen aan PDF's

### Definitie Anker – Annotator
De `Annotator`‑klasse is het toegangspunt voor alle PDF‑annotatie‑operaties in GroupDocs.Annotation voor .NET. Hij laadt een PDF in het geheugen, biedt methoden om annotaties toe te voegen, te bewerken en op te halen, en verwerkt het opslaan van het gewijzigde document.

### Hoe voeg je gebieds‑ en ellips‑annotaties toe?
Laad de PDF met `new Annotator(...)`, maak `AreaAnnotation` en `EllipseAnnotation` objecten aan, stel hun coördinaten in en voeg ze toe aan de collectie van de annotator. Roep vervolgens `Save` aan om de wijzigingen permanent te maken. Deze workflow laat je programmatisch secties (gebied) markeren of belangrijke grafieken omcirkelen in één atomaire bewerking.

#### Stap 1: Initialiseer de Annotator
```csharp
var annotator = new Annotator("input.pdf");
```

#### Stap 2: Maak een AreaAnnotation
`AreaAnnotation` vertegenwoordigt een rechthoekig markeergebied op een PDF‑pagina.  
```csharp
var area = new AreaAnnotation
{
    PageNumber = 0,
    Box = new RectangleF(100, 150, 200, 50),
    Color = Color.Yellow,
    Opacity = 0.4f,
    Text = "Review this paragraph"
};
```

#### Stap 3: Maak een EllipseAnnotation
`EllipseAnnotation` vertegenwoordigt een ellipsvormige annotatie op een PDF‑pagina.  
```csharp
var ellipse = new EllipseAnnotation
{
    PageNumber = 2,
    Box = new RectangleF(300, 400, 120, 80),
    Color = Color.Red,
    Opacity = 0.6f,
    Text = "Check this figure"
};
```

#### Stap 4: Voeg annotaties in bulk toe
```csharp
annotator.Add(new List<AnnotationBase> { area, ellipse });
annotator.Save("output.pdf");
```

**Pro Tip:** Het toevoegen van annotaties in een lijst en één keer `Add` aanroepen vermindert I/O‑overhead, vooral wanneer je tientallen markeringen over vele pagina’s moet invoegen.

### Hoe selectieve annotaties opslaan?
`SaveOptions` configureert hoe de geannoteerde PDF wordt opgeslagen, inclusief welke annotatietypes worden meegenomen. GroupDocs.Annotation laat je filteren welke annotatietypes naar het uitvoerbestand worden geschreven. Maak een `SaveOptions`‑instantie, stel de `AnnotationTypes`‑collectie in op de types die je wilt behouden, en geef de opties door aan `Save`. Dit is perfect voor het genereren van alleen‑reviewer PDF's of het verwijderen van tijdelijke notities vóór archivering.

```csharp
var saveOptions = new SaveOptions
{
    AnnotationTypes = new[] { AnnotationType.Text, AnnotationType.Area }
};
annotator.Save("filtered.pdf", saveOptions);
```

## Reële Implementatiescenario's

### Scenario 1: Document Review Workflow
Meerdere reviewers voegen **Area**, **Ellipse** en **Text** annotaties toe. Na de reviewronde genereer je drie PDF's:
1. Volledige versie met elke opmerking.  
2. Alleen‑reviewer versie (filtert interne notities eruit).  
3. Schone versie voor definitieve goedkeuring (behoudt alleen highlights).

### Scenario 2: Geautomatiseerde Rapportgeneratie
Je backend verwerkt dagelijkse verkooprapporten, markeert automatisch belangrijke KPI's met gebieds‑annotaties en omcirkelt afwijkende grafieken met ellips‑annotaties. De gegenereerde PDF's worden vervolgens per e‑mail naar stakeholders gestuurd zonder handmatige tussenkomst.

### Scenario 3: Samenwerkende Juridische Documenten
Advocatenkantoren moeten vaak partner‑commentaren scheiden van notities van junior‑associés. Door annotaties te taggen met aangepaste metadata en selectief op te slaan, kun je een partner‑review PDF produceren die junior‑opmerkingen verbergt, waardoor versiebeheer eenvoudiger wordt.

## Prestatieoptimalisatie voor productiegebruik

### Hoe geheugen beheren bij het annoteren van grote PDF's?
`LoadOptions` stelt je in staat te specificeren hoe een PDF wordt geladen, bijvoorbeeld paginabereiken of wachtwoorden. Wanneer een PDF groter is dan 100 MB, vermijd dan het volledig laden van het bestand door de `LoadOptions`‑constructor te gebruiken die een paginabereik accepteert. Verwerk pagina’s in batches, vernietig elke `Annotator`‑instantie met een `using`‑blok en ruim tijdelijke bestanden op na elke batch. Deze aanpak houdt het piekgeheugen onder 200 MB, zelfs voor documenten van 500 pagina’s.

```csharp
using (var annotator = new Annotator("large.pdf", new LoadOptions { PageNumbers = new[] { 0, 1, 2 } }))
{
    // annotate first three pages
}
```

### Best Practices voor geheugenbeheer
- **Wrap `Annotator` altijd in een `using`‑statement** om de vrijgave van unmanaged resources te garanderen.  
- **Batch‑process annotaties:** verzamel alle annotaties voor een document en roep vervolgens één keer `Add` aan.  
- **Vermijd het volledig laden van PDF's** wanneer je alleen een subset van pagina’s moet wijzigen; gebruik `LoadOptions.PageNumbers`.

### Strategieën voor grote bestanden
1. **Pagina‑gewijze verwerking** – Laad, annoteer en sla één pagina tegelijk op.  
2. **Streaming output** – Leid de `Save`‑methode naar een `MemoryStream` om tussenliggende schijfbewerkingen te vermijden.  
3. **Opschonen van tijdelijke bestanden** – Verwijder alle tijdelijke bestanden die door de annotator zijn aangemaakt na elke bewerking.

### Overwegingen bij gelijktijdige verwerking
- **Thread safety:** `Annotator`‑instanties zijn niet thread‑safe. Maak een aparte instantie per thread.  
- **Resource throttling:** Beperk gelijktijdige taken tot het aantal CPU‑kernen om CPU‑verzadiging te voorkomen.  
- **Async API:** `SaveAsync` slaat het geannoteerde document asynchroon op, retourneert een Task, en is nuttig in ASP.NET Core‑omgevingen.

## Probleemoplossing Veelvoorkomende Problemen

### Probleem 1: “File Not Found” fouten
**Direct antwoord:** Controleer of het bestandspad dat je aan `new Annotator(...)` doorgeeft absoluut is of correct relatief ten opzichte van de uitvoerende assembly, en zorg dat het applicatie‑proces leesrechten heeft voor die locatie. Als het bestand zich op een netwerkschijf bevindt, koppel de share of gebruik UNC‑paden.

**Typische oplossingen:**  
- Gebruik `Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Docs", "sample.pdf")`.  
- Geef de IIS‑application‑pool‑identiteit lees‑/schrijfrechten op de map.

### Probleem 2: Annotaties verschijnen op verkeerde locaties
**Direct antwoord:** Zorg ervoor dat je hetzelfde coördinatensysteem (linksboven‑origin) gebruikt en dat de DPI van de pagina overeenkomt met de waarden die je opgeeft. Haal de paginagrootte op via `annotator.GetPageInfo(pageNumber)` en bereken coördinaten relatief ten opzichte van die grootte.

**Typische oplossingen:**  
- Vermenigvuldig coördinaten met de schaalfactor van de pagina als de PDF met een niet‑standaard DPI is gemaakt.  
- Controleer dat je geen punten (1/72 inch) verwart met pixels.

### Probleem 3: Prestatieproblemen met grote bestanden
**Direct antwoord:** Schakel over op paginabereik‑laden, verwerk annotaties in batches en vernietig elke `Annotator`‑instantie direct. Schakel ook de `MemoryCache`‑optie in `LoadOptions` in om buffers tussen bewerkingen te hergebruiken.

**Typische oplossingen:**  
- Stel `LoadOptions.UseMemoryCache = true`.  
- Verwerk bestanden asynchroon met `await annotator.SaveAsync(...)`.

### Probleem 4: Licentie‑gerelateerde fouten
**Direct antwoord:** Plaats het `.lic`‑bestand in een map die de applicatie kan lezen, en roep `License license = new License(); license.SetLicense("path/to/license.lic");` aan vóór enige andere GroupDocs‑aanroep. Controleer of de licentieversie overeenkomt met de bibliotheekversie die je gebruikt.

**Typische oplossingen:**  
- Controleer of het licentiebestand niet corrupt is (vergelijk bestandsgrootte).  
- Zorg dat je geen trial‑licentie mengt met een commerciële licentie in dezelfde omgeving.

## Geavanceerde Tips en Best Practices

### Kleurbeheer
Consistente kleuren verbeteren de leesbaarheid voor reviewers. Definieer een palet (bijv. Geel voor highlights, Rood voor kritieke issues) en sla het op in een statische helper‑klasse. Gebruik hoge‑contrast kleuren voor toegankelijkheid en voeg een legenda‑pagina toe aan de PDF voor referentie.

### Foutafhandelingspatronen
Wrap alle annotatie‑aanroepen in try‑catch‑blokken die specifiek `GroupDocs.Annotation.Exceptions.AnnotationException` vangen. Log het foutbericht, de stacktrace en de PDF‑naam om debugging te vergemakkelijken.

### Teststrategieën
- **Unit Tests:** Gebruik een kleine PDF met bekende afmetingen, voeg een annotatie toe, en controleer dat `GetAnnotations()` de verwachte coördinaten teruggeeft.  
- **Integration Tests:** Voer de volledige workflow uit op PDF's variërend van 1 pagina tot 200 pagina’s, en verifieer dat de verwerkingstijd onder 5 seconden blijft voor bestanden onder 50 MB.  
- **Load Tests:** Simuleer 50 gelijktijdige annotatie‑verzoeken met een tool zoals k6 of Apache JMeter en monitor CPU/geheugen.

## Veelgestelde Vragen

**Q: Hoe ga ik om met PDF's met verschillende paginagroottes?**  
A: GroupDocs leest automatisch de afmetingen van elke pagina. Bij het positioneren van annotaties, vraag altijd `annotator.GetPageInfo(pageNumber)` op en bereken coördinaten op basis van de breedte en hoogte van die pagina.

**Q: Kan ik password‑beveiligde PDF's annoteren?**  
A: Ja. Gebruik de `LoadOptions`‑constructor die een wachtwoord‑string accepteert, bijv. `new LoadOptions { Password = "secret" }`, en geef deze door aan de `Annotator`‑constructor.

**Q: Wat is het maximale aantal annotaties dat ik aan één PDF kan toevoegen?**  
A: Er is geen harde limiet, maar de prestaties nemen af na enkele duizenden annotaties. Voor zeer grote annotatiesets, groepeer ze in logische secties en verwerk elke sectie apart.

**Q: Hoe verwijder ik specifieke annotaties programmatisch?**  
A: Haal de `Id` van de annotatie op via `GetAnnotations()`, roep vervolgens `Delete(id)` aan of maak een `SaveOptions`‑instantie die de ongewenste `AnnotationType` uitsluit.

**Q: Kan ik het uiterlijk van annotaties aanpassen naast kleuren?**  
A: Absoluut. Je kunt doorzichtigheid, randdikte, stippellijn‑stijl en zelfs aangepaste SVG‑iconen voor stempel‑annotaties instellen.

**Q: Wat gebeurt er als ik een gescande (image‑based) PDF probeer te annoteren?**  
A: Annotaties worden gerenderd als overlay‑objecten bovenop de paginabeeld. Ze wijzigen de onderliggende rasterdata niet, dus de PDF blijft doorzoekbaar als er OCR‑lagen aanwezig zijn.

**Q: Hoe ga ik om met zeer grote PDF's zonder geheugen op te raken?**  
A: Verwerk het document pagina‑voor‑pagina met `LoadOptions.PageNumbers`, vernietig elke `Annotator`‑instantie direct na gebruik, en schakel streaming‑opslaan naar een `MemoryStream` in om schijfpieken te vermijden.

## Integratie met ASP.NET-toepassingen

Wanneer je annotatiefuncties via een web‑API beschikbaar maakt, houd dan het volgende patroon aan:

1. **Controller ontvangt de PDF‑stream** van de client.  
2. **Valideer de bestandsgrootte** (weiger > 200 MB tenzij je speciale handling hebt).  
3. **Instantieer `Annotator` binnen een `using`‑blok** om gegarandeerde opruiming te waarborgen.  
4. **Pas annotaties toe** op basis van de JSON‑payload die type, coördinaten en tekst beschrijft.  
5. **Sla op naar een tijdelijke locatie**, stream vervolgens het resultaat terug naar de client met de juiste `Content‑Disposition`‑header.

```csharp
[HttpPost("annotate")]
public async Task<IActionResult> Annotate(IFormFile pdf, [FromBody] AnnotationRequest request)
{
    using var stream = pdf.OpenReadStream();
    var annotator = new Annotator(stream);
    // add annotations based on request
    var output = new MemoryStream();
    annotator.Save(output);
    output.Position = 0;
    return File(output, "application/pdf", "annotated.pdf");
}
```

## Aanvullende bronnen
- [GroupDocs purchase page](https://purchase.groupdocs.com/buy)  
- [Buy GroupDocs](https://purchase.groupdocs.com/buy)  
- [GroupDocs Annotation Documentation](https://docs.groupdocs.com/annotation/net/)  
- [GroupDocs API Reference](https://reference.groupdocs.com/annotation/net/)  
- [Latest Releases](https://releases.groupdocs.com/annotation/net/)  
- [Try GroupDocs for Free](https://releases.groupdocs.com/annotation/net/)  
- [Request a Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- [GroupDocs Forum](https://forum.groupdocs.com/c/annotation/)

## Conclusie en Volgende Stappen

Je hebt nu een **volledig, productie‑klaar stappenplan** voor het bouwen van een **document review systeem** aangedreven door GroupDocs.Annotation voor .NET. Je hebt geleerd hoe je de bibliotheek instelt, gebieds‑, ellips‑ en tekstannotaties toevoegt, selectief opslaat en het geheugenverbruik laag houdt, zelfs bij enorme PDF's.  

**Volgende acties die je vandaag kunt nemen:**  

1. **Experimenteer** met extra annotatietypes zoals `ArrowAnnotation` en `StampAnnotation`.  
2. **Integreer** de workflow in je bestaande ASP.NET Core‑API of desktop‑WPF‑applicatie.  
3. **Verken** de volledige API‑referentie om geavanceerde functies zoals annotatie‑versionering en aangepaste metadata te ontdekken.  
4. **Word lid** van de GroupDocs‑community‑forums voor peer‑support en om op de hoogte te blijven van nieuwe releases.

---

**Last Updated:** 2026-05-26  
**Tested With:** GroupDocs.Annotation 23.11 for .NET  
**Author:** GroupDocs  

---

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main()
    {
        string inputPdfPath = "input.pdf";
        
        try
        {
            // Initialize the Annotator with the path of the document
            using (Annotator annotator = new Annotator(inputPdfPath))
            {
                Console.WriteLine("GroupDocs.Annotation initialized successfully!");
                // Your annotation code will go here
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Setup issue: {ex.Message}");
        }
    }
}
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // All annotation work happens inside this using block
    // This ensures proper resource cleanup
}
```

```csharp
AreaAnnotation areaAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // X, Y, Width, Height
    BackgroundColor = 65535,                 // Yellow highlight
    PageNumber = 0                           // First page
};
```

```csharp
EllipseAnnotation ellipseAnnotation = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Same coordinate system
    BackgroundColor = 123456,                // Different color
    PageNumber = 1                           // Second page
};
```

```csharp
annotator.Add(new List<AnnotationBase>() { areaAnnotation, ellipseAnnotation });
```

```csharp
SaveOptions saveOptions = new SaveOptions 
{
    AnnotationTypes = AnnotationType.Ellipse // Only save ellipse annotations
};
```

```csharp
annotator.Save(outputPath, saveOptions);
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // Your annotation code here
} // Automatic cleanup happens here
```

```csharp
var annotationsToAdd = new List<AnnotationBase>();
// Add multiple annotations to the list
annotator.Add(annotationsToAdd); // Single operation
```

```csharp
// Always verify file exists before processing
if (!File.Exists(inputPdfPath))
{
    throw new FileNotFoundException($"PDF file not found: {inputPdfPath}");
}

// Use absolute paths when possible
string absolutePath = Path.GetFullPath(inputPdfPath);
```

```csharp
// Test with known coordinates first
AreaAnnotation testAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(50, 50, 100, 100), // Start with simple values
    BackgroundColor = 65535,
    PageNumber = 0
};

// Verify page dimensions if needed
// Consider PDF scaling factors in your calculations
```

```csharp
// Define color constants for consistency
public static class AnnotationColors
{
    public const int ImportantHighlight = 65535;    // Yellow
    public const int AttentionMarker = 255;         // Red
    public const int ApprovedSection = 65280;       // Green
}
```

```csharp
try
{
    using (Annotator annotator = new Annotator(inputPdfPath))
    {
        // Your annotation operations
        annotator.Add(annotations);
        annotator.Save(outputPath, saveOptions);
    }
}
catch (GroupDocsException ex)
{
    // Handle GroupDocs-specific errors
    Logger.Error($"GroupDocs error: {ex.Message}");
}
catch (IOException ex)
{
    // Handle file I/O errors
    Logger.Error($"File operation error: {ex.Message}");
}
catch (Exception ex)
{
    // Handle unexpected errors
    Logger.Error($"Unexpected error: {ex.Message}");
}
```

```csharp
[HttpPost]
public async Task<IActionResult> AnnotatePdf(IFormFile pdfFile, AnnotationRequest request)
{
    // Validate input
    if (pdfFile == null || pdfFile.Length == 0)
        return BadRequest("No file provided");

    // Process asynchronously to avoid blocking the UI
    var result = await ProcessAnnotationsAsync(pdfFile, request);
    return Ok(result);
}
```

## Gerelateerde Tutorials

- [GroupDocs Annotation .NET Tutorial - Complete Guide for Document Management](/annotation/net/annotation-management/)
- [Document Preview .NET Tutorials - Complete GroupDocs.Annotation Guide](/annotation/net/document-preview/)
- [GroupDocs Annotation Metered License Tutorial - Complete .NET Setup Guide](/annotation/net/licensing-and-configuration/implement-metered-license-groupdocs-annotation-net/)