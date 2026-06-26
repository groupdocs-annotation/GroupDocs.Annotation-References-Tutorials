---
categories:
- .NET Development
date: '2026-06-26'
description: Leer hoe u formaten kunt ophalen met GroupDocs.Annotation voor .NET,
  los problemen met niet‑ondersteunde bestandsformaten op en pas best‑practice validatie
  toe.
keywords:
- how to retrieve formats
- troubleshoot unsupported file format
- GroupDocs.Annotation .NET
lastmod: '2026-06-26'
linktitle: Ophalen ondersteunde bestandsformaten .NET
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  headline: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete
    Guide
  type: TechArticle
- description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  name: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete Guide
  steps:
  - name: Verify installation
    text: Run `dotnet list package` or check the NuGet console output for any warnings.
  - name: Check license status
    text: Ensure `License.SetLicense("path/to/license.json")` executes before any
      API call.
  - name: Diagnose environment constraints
    text: '- Confirm .NET runtime version matches the library’s requirements. - Verify
      the process has read/write permissions for the temporary folder used by GroupDocs.Annotation.'
  type: HowTo
- questions:
  - answer: The library supports **over 50 formats**, including PDF, DOCX, XLSX, PPTX,
      JPEG, PNG, TIFF, and many others. Run the sample code to retrieve the exact
      list for your license.
    question: What file formats does GroupDocs.Annotation actually support?
  - answer: This usually points to a licensing issue—either an expired trial or an
      incorrectly loaded license file. Re‑apply a valid license and restart the app.
    question: Why am I getting fewer supported formats than expected?
  - answer: No direct “IsSupported” method exists; the recommended approach is to
      cache the full list once and query it locally for fast lookups.
    question: Can I check a single format without pulling the whole list?
  - answer: Initialise the format cache at application startup (e.g., in `ConfigureServices`)
      and store it in a static or singleton service. This eliminates per‑request overhead.
    question: How should I handle format checking in a high‑traffic web app?
  - answer: Exceptions typically stem from licensing or corrupted installations. Verify
      the package integrity, re‑install if needed, and ensure the license file is
      accessible.
    question: What if GetSupportedFileTypes() throws an exception?
  type: FAQPage
tags:
- GroupDocs.Annotation
- file-formats
- document-processing
- dotnet-tutorial
title: Hoe formaten op te halen in .NET met GroupDocs.Annotation – Complete gids
type: docs
url: /nl/net/document-information/retrieve-supported-file-formats-groupdocs-annotation-net/
weight: 1
---

# Hoe formats ophalen in .NET met GroupDocs.Annotation

## Introductie

Heb je je ooit afgevraagd welke bestandsformaten je .NET‑applicatie daadwerkelijk kan verwerken voor documentannotatie? **How to retrieve formats** is een vraag die veel ontwikkelaars stellen wanneer ze gebruikersuploads moeten valideren of dynamische UI‑filters moeten bouwen. Exact weten welke bestandsformaten je GroupDocs.Annotation‑implementatie ondersteunt is niet alleen handig – het is essentieel voor het bouwen van robuuste applicaties die nooit crashen door een onverwacht bestandstype.

In deze gids leer je hoe je programmatically de ondersteunde bestandsformaten kunt ophalen en valideren met GroupDocs.Annotation voor .NET. We lopen de basisimplementatie door, laten zien hoe je de ruwe lijst omzet in een nette dropdown voor eindgebruikers, en behandelen praktische troubleshooting‑tips zodat je elk document‑formaatscenario met vertrouwen kunt afhandelen.

**Wat je zult meenemen**

- Een glashelder begrip van de bestandsformaatmogelijkheden van GroupDocs.Annotation  
- Klaar‑te‑gebruiken code die elke ondersteunde formaat ophaalt en weergeeft  
- Bewezen strategieën voor caching, foutafhandeling en licentie‑randgevallen  
- Best‑practice aanbevelingen voor productie‑klare bestands‑typevalidatie  

Laten we erin duiken en deze bestandsformaat‑puzzel een voor eens en voor altijd oplossen.

## Snelle antwoorden
- **What does “how to retrieve formats” mean?** Het is de programmatic manier om GroupDocs.Annotation te vragen welke extensies het kan annoteren.  
- **Which primary formats are supported out of the box?** Meer dan 50, inclusief PDF, DOCX, XLSX, PPTX, JPEG, PNG en TIFF.  
- **Do I need a license to get the full list?** Ja – een actieve commerciële of proeflicentie ontgrendelt de volledige catalogus.  
- **Is caching the format list recommended?** Absoluut; caching voorkomt onnodige oproepen en verbetert de responstijd.  
- **How can I validate an upload against the list?** Vergelijk de extensie van het bestand met de gecachte collectie van ondersteunde extensies.

## Wat is “how to retrieve formats”?
**How to retrieve formats** verwijst naar het proces van het aanroepen van de API van GroupDocs.Annotation om een collectie van alle bestandstypen te verkrijgen die de bibliotheek kan annoteren. Deze operatie retourneert een read‑only lijst van `FileType`‑objecten die zowel de bestandsextensie als een vriendelijke beschrijving bevatten.

## Waarom GroupDocs.Annotation gebruiken voor formatdetectie?
GroupDocs.Annotation ondersteunt **50+ invoer‑ en uitvoerformaten** – inclusief PDF, Microsoft Office (Word, Excel, PowerPoint) en veelvoorkomende beeldtypen – terwijl het documenten van honderden pagina’s verwerkt zonder het volledige bestand in het geheugen te laden. Deze gekwantificeerde mogelijkheid maakt het een betrouwbare keuze voor enterprise‑scale annotatie‑pijplijnen.

## Vereisten en omgeving configuratie

### Wat je nodig hebt
- **IDE:** Visual Studio 2019 of later (Community‑editie werkt prima)  
- **Doel‑framework:** .NET Framework 4.6.1 + of .NET Core 2.0 +   
- **C#‑basis:** Als je een “Hello World”‑app kunt schrijven, ben je klaar  

### GroupDocs.Annotation installeren
De eenvoudigste manier is via NuGet. Kies de methode die bij je workflow past:

**Optie 1: Package Manager Console**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**Optie 2: .NET CLI**  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

**Pro tip:** In beperkte bedrijfsomgevingen, download het pakket handmatig van [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/) en verwijs lokaal naar de DLL.

### Licenties eenvoudig gemaakt
- **Ontwikkeling & testen:** Begin met de gratis proefversie voor volledige functionaliteit.  
- **Uitgebreide evaluatie:** Haal een [temporary license](https://purchase.groupdocs.com/temporary-license/) (uitgegeven in ~5 minuten).  
- **Productie:** Koop een commerciële licentie via [GroupDocs Purchase](https://purchase.groupdocs.com/buy); één licentie dekt alle implementatiescenario’s.

## Hoe ondersteunde bestandsformaten programmatically ophalen?

Laad de ondersteunde formaten met één oproep naar `FileType.GetSupportedFileTypes()` en transformeer vervolgens het resultaat naar een gebruiksvriendelijke lijst die kan worden weergegeven in UI‑controls of gebruikt voor validatie. De methode retourneert een read‑only collectie van `FileType`‑objecten, elk met een extensie en beschrijving, waardoor het eenvoudig is om mee te werken.

```csharp
var supported = FileType.GetSupportedFileTypes()
                         .OrderBy(f => f.Extension)
                         .Select(f => new { f.Extension, f.Description })
                         .ToList();
```

De bovenstaande code vraagt de interne metadata van GroupDocs.Annotation op, sorteert de extensies alfabetisch en retourneert een lichte collectie die je kunt binden aan UI‑controls of gebruiken voor validatie.

### Definitie‑anker: FileType‑klasse
De `FileType`‑klasse is de weergave van GroupDocs.Annotation van één documentformaat, met eigenschappen zoals `Extension` en `Description`.  

### Stapsgewijze walkthrough
1. **Add the namespace** – `using GroupDocs.Annotation;` bovenaan je bestand.  
2. **Call the static method** – `FileType.GetSupportedFileTypes()` retourneert een `IEnumerable<FileType>`.  
3. **Sort and project** – Gebruik LINQ’s `OrderBy` en `Select` om de gegevens voor weergave vorm te geven.  
4. **Render** – Loop door de lijst in een console, MVC‑view of WinForms‑dropdown.

```csharp
using System;
using System.Linq;
using GroupDocs.Annotation; // This is where the FileType class lives
```  

## Hoe de format‑lijst cachen voor productiegebruik?

Caching elimineert herhaalde metadata‑lookups en garandeert sub‑milliseconde responstijden voor elk verzoek, wat cruciaal is in toepassingen met veel verkeer. Door de format‑lijst op te slaan in een static field en deze lazy te laden bij eerste gebruik, zorg je ervoor dat de data slechts één keer wordt opgehaald en daarna efficiënt wordt hergebruikt gedurende de volledige levenscyclus van de applicatie.

```csharp
public static class FormatCache
{
    private static IReadOnlyList<FileType> _cachedFormats;

    public static IReadOnlyList<FileType> SupportedFormats =>
        _cachedFormats ??= FileType.GetSupportedFileTypes()
                                    .OrderBy(f => f.Extension)
                                    .ToList();
}
```

```csharp
public static void RunGetSupportedFileFormats()
{
    // Retrieve collection of supported file types, ordered by their extension
    IEnumerable<FileType> fileTypes = FileType.GetSupportedFileTypes().OrderBy(fileType => fileType.Extension);

    // Iterate through each FileType object and output its details to the console
    foreach (FileType fileType in fileTypes)
        Console.WriteLine($"{fileType.Extension} - {fileType.Name}");
}
```  

**Waarom cachen?** De ondersteunde formatset verandert nooit tijdens runtime, dus één laadactie bij applicatiestart bespaart CPU‑cycli en voorkomt potentiële licentiecontroles bij elke oproep.

## Veelvoorkomende problemen en oplossingen

### Probleem 1: “GroupDocs.Annotation not found” compile‑fout
**Direct antwoord:** Controleer of het NuGet‑pakket correct is geïnstalleerd, maak de oplossing schoon en bouw opnieuw, en zorg dat je doel‑framework overeenkomt met de ondersteunde versies van het pakket.  

**Oorzaakanalyse** – Ontbrekende referentie, incompatibel framework, of bedrijfs‑package‑source beperkingen.

### Probleem 2: Lege of onvolledige formatlijst
**Direct antwoord:** Een verlopen of verkeerd geconfigureerde licentie truncateert vaak de lijst; pas een geldig licentiebestand toe en herstart de applicatie.  

**Mogelijke oorzaken:**  
- Licentiebestand niet geladen (`License.SetLicense("license.json")` ontbreekt)  
- Beschadigd NuGet‑pakket  
- Ontbrekende native dependencies  

**Snelle oplossing:**  
```csharp
public static void DiagnoseFormatIssues()
{
    try
    {
        var formats = FileType.GetSupportedFileTypes();
        Console.WriteLine($"Found {formats.Count()} supported formats");
        
        if (formats.Count() < 10) // GroupDocs supports many more formats
        {
            Console.WriteLine("Warning: Fewer formats than expected. Check your license.");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Cannot retrieve formats: {ex.Message}");
        // This usually indicates a licensing or installation issue
    }
}
```  

### Probleem 3: Prestatieverlies door frequente oproepen
**Direct antwoord:** Cache het resultaat zoals beschreven in de “Hoe cachen” sectie; latere oproepen worden O(1).  

**Implementatietip:** Bewaar de lijst in `MemoryCache` of een static field, en vernieuw alleen bij een bibliotheek‑upgrade.

```csharp
public static class FileFormatCache
{
    private static List<FileType> _cachedFormats;
    
    public static IEnumerable<FileType> GetSupportedFormats()
    {
        if (_cachedFormats == null)
        {
            _cachedFormats = FileType.GetSupportedFileTypes().ToList();
        }
        return _cachedFormats;
    }
}
```  

## Praktische toepassingen en use‑cases

### Hoe bestandsuploads valideren met de gecachte lijst?
Wanneer een gebruiker een document indient, haal je de bestandsextensie op en vergelijk je deze met de gecachte collectie:

```csharp
bool IsSupported(string fileName)
{
    var ext = Path.GetExtension(fileName).ToLowerInvariant();
    return FormatCache.SupportedFormats.Any(f => f.Extension.Equals(ext, StringComparison.OrdinalIgnoreCase));
}
```

```csharp
public bool IsFileSupported(string fileName)
{
    var extension = Path.GetExtension(fileName).ToLowerInvariant();
    var supportedExtensions = GetSupportedExtensions();
    return supportedExtensions.Contains(extension);
}
```  

### Hoe een dynamisch bestandsfilter genereren voor een OpenFileDialog?
Vul de filter‑string van de dialoog met de gecachte extensies, zodat de UI altijd de mogelijkheden van de bibliotheek weerspiegelt:

```csharp
var filter = string.Join(";", FormatCache.SupportedFormats.Select(f => $"*{f.Extension}"));
openFileDialog.Filter = $"Supported Files ({filter})|{filter}";
```

```csharp
public string GenerateFileFilter()
{
    var extensions = GetSupportedExtensions();
    var filterParts = extensions.Select(ext => $"*{ext}");
    return $"Supported Documents|{string.Join(";", filterParts)}";
}
```  

### Hoe niet‑ondersteunde bestanden overslaan in een batch‑mapscan?
Itereer over een map, controleer elk bestand met `IsSupported`, en verwerk alleen de geldige:

```csharp
foreach (var file in Directory.EnumerateFiles(folderPath))
{
    if (IsSupported(file))
    {
        // Process with GroupDocs.Annotation
    }
}
```

```csharp
public void ProcessDirectory(string directoryPath)
{
    var supportedExtensions = GetSupportedExtensions();
    var files = Directory.GetFiles(directoryPath)
        .Where(file => supportedExtensions.Contains(Path.GetExtension(file).ToLowerInvariant()));
    
    foreach (var file in files)
    {
        // Process each supported file
        ProcessAnnotationFile(file);
    }
}
```  

## Prestaties overwegingen en best practices

- **Cache once, reuse everywhere** – Initialise `FormatCache` bij applicatiestart (bijv. in `Program.cs` of `Startup.cs`).  
- **Lazy loading** – De static property zorgt ervoor dat de lijst alleen laadt wanneer deze voor het eerst nodig is, waardoor onnodige opstart‑overhead wordt vermeden.  
- **Thread safety** – De null‑coalescing operator (`??=`) is veilig voor de meeste single‑threaded scenario’s; voor high‑concurrency apps, wikkel de cache in een `Lazy<IReadOnlyList<FileType>>`.  
- **Dispose annotation objects** – Hoewel de format‑lijst zelf geen disposale vereist, moeten alle `Annotation`‑instanties die je maakt worden omgeven door `using`‑statements om native resources vrij te geven.  

### Foutafhandelingspatroon voor licentieproblemen
Wrap de format‑ophaling in een try‑catch‑blok dat specifiek zoekt naar `LicenseException` en log een duidelijke boodschap:

```csharp
try
{
    var formats = FileType.GetSupportedFileTypes();
}
catch (LicenseException ex)
{
    // Log and fallback to a hard‑coded minimal list
}
```

```csharp
public static class RobustFormatRetrieval
{
    public static IEnumerable<FileType> GetSupportedFormatsWithFallback()
    {
        try
        {
            return FileType.GetSupportedFileTypes();
        }
        catch (LicenseException)
        {
            // Handle licensing issues gracefully
            LogWarning("License issue detected. Using basic format list.");
            return GetBasicFormatList();
        }
        catch (Exception ex)
        {
            LogError($"Unexpected error retrieving formats: {ex}");
            return Enumerable.Empty<FileType>();
        }
    }
    
    private static IEnumerable<FileType> GetBasicFormatList()
    {
        // Return a hardcoded list of common formats as fallback
        // This ensures your app doesn't break completely
        return new[] { FileType.Pdf, FileType.Docx, FileType.Xlsx };
    }
}
```  

## Probleemoplossingsgids

### Stap 1: Installatie verifiëren
Voer `dotnet list package` uit of controleer de NuGet‑console‑output op waarschuwingen.  

```csharp
public static void VerifyInstallation()
{
    try
    {
        var version = typeof(FileType).Assembly.GetName().Version;
        Console.WriteLine($"GroupDocs.Annotation version: {version}");
        
        var formatCount = FileType.GetSupportedFileTypes().Count();
        Console.WriteLine($"Supported formats: {formatCount}");
        
        if (formatCount > 50) // Expected range
        {
            Console.WriteLine("✓ Installation looks good!");
        }
        else
        {
            Console.WriteLine("⚠ Possible installation or licensing issue");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"✗ Installation problem: {ex.Message}");
    }
}
```  

### Stap 2: Licentiestatus controleren
Zorg ervoor dat `License.SetLicense("path/to/license.json")` wordt uitgevoerd vóór enige API‑aanroep.  

### Stap 3: Omgevingsbeperkingen diagnosticeren
- Bevestig dat de .NET‑runtime versie overeenkomt met de vereisten van de bibliotheek.  
- Controleer of het proces lees‑/schrijfrechten heeft voor de tijdelijke map die GroupDocs.Annotation gebruikt.  

## Veelgestelde vragen

**Q: Welke bestandsformaten ondersteunt GroupDocs.Annotation daadwerkelijk?**  
A: De bibliotheek ondersteunt **meer dan 50 formaten**, waaronder PDF, DOCX, XLSX, PPTX, JPEG, PNG, TIFF en vele anderen. Voer de voorbeeldcode uit om de exacte lijst voor jouw licentie op te halen.

**Q: Waarom krijg ik minder ondersteunde formaten dan verwacht?**  
A: Dit duidt meestal op een licentieprobleem – een verlopen trial of een onjuist geladen licentiebestand. Pas een geldige licentie toe en herstart de app.

**Q: Kan ik een enkel formaat controleren zonder de hele lijst op te halen?**  
A: Er bestaat geen directe “IsSupported”‑methode; de aanbevolen aanpak is om de volledige lijst eenmaal te cachen en lokaal te raadplegen voor snelle lookups.

**Q: Hoe moet ik format‑checking afhandelen in een web‑app met veel verkeer?**  
A: Initialise de format‑cache bij applicatiestart (bijv. in `ConfigureServices`) en bewaar deze in een static of singleton service. Dit elimineert overhead per request.

**Q: Wat als GetSupportedFileTypes() een uitzondering gooit?**  
A: Uitzonderingen ontstaan meestal door licentie‑ of corrupte installaties. Controleer de pakketintegriteit, her‑installeer indien nodig, en zorg dat het licentiebestand toegankelijk is.

## Conclusie

Je beschikt nu over een volledige, productie‑klare strategie voor **how to retrieve formats** met GroupDocs.Annotation in .NET. Van de één‑lijn API‑call tot robuuste caching, foutafhandeling en UI‑integratie, kun je met vertrouwen uploads valideren, dynamische bestandsfilters genereren en schaalbare annotatie‑pijplijnen bouwen.

**Volgende stappen:**  
- Verken de [GroupDocs.Annotation API-referentie](https://reference.groupdocs.com/annotation/net/) voor diepere annotatiefuncties.  
- Word lid van de community op het [Supportforum](https://forum.groupdocs.com/c/annotation/) als je edge‑case scenario’s tegenkomt.  
- Experimenteer met het combineren van format‑validatie met aangepaste bedrijfsregels (bijv. grootte‑limieten, beveiligingsscans) om je document‑workflow verder te versterken.

## Bronnen
- [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/)
- [Laatste versie downloaden](https://releases.groupdocs.com/annotation/net/)
- [Gratis proefversie](https://releases.groupdocs.com/annotation/net/)
- [tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/)
- [Tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/)
- [GroupDocs aankoop](https://purchase.groupdocs.com/buy)
- [Licentie aanschaffen](https://purchase.groupdocs.com/buy)
- [Documentatie](https://docs.groupdocs.com/annotation/net/)
- [API-referentie](https://reference.groupdocs.com/annotation/net/)
- [GroupDocs.Annotation API-referentie](https://reference.groupdocs.com/annotation/net/)
- [Supportforum](https://forum.groupdocs.com/c/annotation/)
- [Community‑ondersteuning](https://forum.groupdocs.com/c/annotation/)

**Laatst bijgewerkt:** 2026-06-26  
**Getest met:** GroupDocs.Annotation 25.4.0 for .NET  
**Auteur:** GroupDocs  

```csharp
public static List<string> GetSupportedExtensions()
{
    try
    {
        var supportedExtensions = FileType.GetSupportedFileTypes()
            .Select(ft => ft.Extension.ToLowerInvariant())
            .OrderBy(ext => ext)
            .ToList();
        
        return supportedExtensions;
    }
    catch (Exception ex)
    {
        // Log the error appropriately in your application
        Console.WriteLine($"Error retrieving supported formats: {ex.Message}");
        return new List<string>();
    }
}
```

## Gerelateerde tutorials

- [Document Metadata Extraction .NET - Complete Guide to GroupDocs.Annotation](/annotation/net/document-information/)
- [Load PDF from URL .NET - Complete Guide with GroupDocs.Annotation](/annotation/net/document-loading-essentials/load-document-from-url/)
- [Document Preview .NET Tutorials - Complete GroupDocs.Annotation Guide](/annotation/net/document-preview/)