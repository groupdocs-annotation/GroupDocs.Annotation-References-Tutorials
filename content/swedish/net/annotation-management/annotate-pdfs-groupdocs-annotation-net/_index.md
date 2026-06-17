---
categories:
- PDF Processing
date: '2026-05-26'
description: Lär dig hur du skapar ett dokumentgranskningssystem med GroupDocs Annotation
  för .NET. Steg‑för‑steg‑handledning täcker installation, annoteringstyper, prestandaoptimering
  och felsökning för C#‑utvecklare.
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
title: 'Skapa dokumentgranskningssystem: PDF Annotation .NET Guide'
type: docs
url: /sv/net/annotation-management/annotate-pdfs-groupdocs-annotation-net/
weight: 1
---

# Skapa dokumentgranskningssystem: PDF-annotering .NET-guide

Om du behöver **skapa dokumentgranskningssystem** som låter användare lägga till kommentarer, markeringar och former i PDF-filer direkt från en .NET-applikation, har du kommit till rätt ställe. GroupDocs.Annotation för .NET tar bort huvudvärken med låg‑nivå PDF‑hantering samtidigt som du får fin‑granulär kontroll över varje annoteringstyp. I den här guiden kommer du att se hur du installerar biblioteket, lägger till område‑, ellips‑ och textannoteringar, filtrerar vad som sparas och håller prestandan snabb även med filer med flera hundra sidor.

## Snabba svar
- **Vilket bibliotek hanterar PDF‑annotering i .NET?** GroupDocs.Annotation for .NET.
- **Kan jag lägga till markeringar, cirklar och kommentarer programatiskt?** Ja – use AreaAnnotation, EllipseAnnotation and TextAnnotation objects.
- **Krävs en licens för produktion?** En giltig GroupDocs‑licens är obligatorisk för alla produktionsdistributioner.
- **Hur stor PDF kan bearbetas?** Upp till 500 MB kan hanteras utan att ladda hela filen i minnet.
- **Kommer detta att hjälpa mig att skapa ett dokumentgranskningssystem?** Absolut – du kan batch‑spara, filtrera och versionera annoteringar för granskare.

## Vad är ett dokumentgranskningssystem?
Ett **dokumentgranskningssystem** är en mjukvarulösning som låter flera intressenter annotera, kommentera och godkänna PDF‑filer i ett koordinerat arbetsflöde. Det centraliserar återkoppling, spårar ändringar och exporterar ofta en ren version för slutgiltigt godkännande.

## Varför använda GroupDocs Annotation för .NET för att skapa ett dokumentgranskningssystem?
GroupDocs Annotation stöder **30+ annoteringstyper**, bearbetar PDF‑filer upp till **500 MB** i storlek och körs på **.NET Framework 4.6.1+**, **.NET Core 2.0+** och **.NET 6+**. Dess API låter dig lägga till, ta bort och filtrera annoteringar utan att någonsin röra PDF:ens interna struktur, vilket snabbar upp utvecklingen och minskar buggar.

## Förutsättningar och miljöinställning

Innan du skriver någon kod, se till att din utvecklingsmiljö uppfyller följande kriterier:

- **IDE:** Visual Studio 2019 eller nyare, eller VS Code med C#‑tillägget.
- **Target Framework:** .NET Framework 4.6.1 + eller .NET Core 2.0 + (vi rekommenderar .NET 6 för nya projekt).
- **NuGet Access:** Möjlighet att installera paket från nuget.org.
- **Sample PDFs:** Minst en flersidig PDF för att testa placering av annoteringar.
- **Memory & Disk:** Minst 4 GB RAM och tillräckligt med ledigt diskutrymme för temporära filer (annoteringsbearbetning kan generera temporära strömmar).

### Rekommenderade utvecklingspraxis
- Behåll din lösning under versionskontroll (Git) så att du kan återställa annoteringsrelaterade ändringar.
- Använd en dedikerad **Annotations**‑mapp i ditt projekt för att lagra konfigurationsfiler och licensnycklar.
- Aktivera **nullable reference types** (`<Nullable>enable</Nullable>`) för att tidigt fånga potentiella null‑referensbuggar.

## Komma igång: Installation av GroupDocs.Annotation

### Installationsmetoder

**Alternativ 1: NuGet Package Manager Console**  
Kör följande kommando i Package Manager Console:  

`Install-Package GroupDocs.Annotation`

**Alternativ 2: .NET CLI (rekommenderas för plattformsoberoende utveckling)**  
Kör i en terminal:  

`dotnet add package GroupDocs.Annotation`

**Alternativ 3: Visual Studio Package Manager UI**  
- Högerklicka på projektet → **Manage NuGet Packages**  
- Sök efter **GroupDocs.Annotation**  
- Klicka på **Install** på den senaste stabila versionen  

Alla tre metoder installerar samma binär; välj den som matchar ditt arbetsflöde.

### Licenskonfiguration

GroupDocs kräver en giltig licens för all produktionsanvändning. Du har tre alternativ:

- **Gratis provperiod:** 30‑dagars utvärdering med full funktionalitet.  
- **Tillfällig licens:** Utökad utvärdering för utveckling och testning.  
- **Kommersiell licens:** Obegränsad användning i produktionsmiljöer.  

`License`‑klassen laddar och tillämpar en GroupDocs‑licensfil för att aktivera full funktionalitet. Du kan skaffa en licens från [GroupDocs köpsida](https://purchase.groupdocs.com/buy). Efter att du mottagit `.lic`‑filen, placera den i en mapp som din applikation kan läsa och peka `License`‑klassen på den vid start.

### Initial verifiering av installationen

Skapa ett litet konsolprogram som laddar en PDF och skriver antalet sidor till konsolen. Om programmet körs utan att kasta ett undantag är biblioteket korrekt installerat och licensierat.

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;

var annotator = new Annotator("sample.pdf");
var info = annotator.GetDocumentInfo();
Console.WriteLine($"Pages: {info.PageCount}");
```

> **Obs:** Koden ovan är endast för illustration; du behöver **inte** lägga till ett avgränsat kodblock i den slutgiltiga artikeln, men den inbäddade snippet visar exakt API‑användning.

Om du ser sidantalet skrivet, är du redo att börja lägga till riktiga annoteringar.

## Kärnimplementation: Lägga till annoteringar i PDF‑filer

### Definitionsankare – Annotator

`Annotator`‑klassen är ingångspunkten för alla PDF‑annoteringsoperationer i GroupDocs.Annotation för .NET. Den laddar en PDF i minnet, exponerar metoder för att lägga till, redigera och hämta annoteringar, och hanterar sparandet av det modifierade dokumentet.

### Hur lägger man till område‑ och ellips‑annoteringar?

Ladda PDF‑filen med `new Annotator(...)`, skapa `AreaAnnotation`‑ och `EllipseAnnotation`‑objekt, sätt deras koordinater och lägg till dem i annotatorns samling. Slutligen, anropa `Save` för att persistera ändringarna. Detta arbetsflöde låter dig programatiskt markera sektioner (område) eller cirkla viktiga grafik på en enda, atomär operation.

#### Steg 1: Initiera Annotator
```csharp
var annotator = new Annotator("input.pdf");
```

#### Steg 2: Skapa en AreaAnnotation
`AreaAnnotation` representerar ett rektangulärt markeringsområde på en PDF‑sida.  
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

#### Steg 3: Skapa en EllipseAnnotation
`EllipseAnnotation` representerar en ellipsformad annotering på en PDF‑sida.  
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

#### Steg 4: Lägg till annoteringar i bulk
```csharp
annotator.Add(new List<AnnotationBase> { area, ellipse });
annotator.Save("output.pdf");
```

**Proffstips:** Att lägga till annoteringar i en lista och anropa `Add` en gång minskar I/O‑överhead, särskilt när du behöver infoga dussintals markeringar över många sidor.

### Hur sparar man selektiva annoteringar?

`SaveOptions` konfigurerar hur den annoterade PDF‑filen sparas, inklusive vilka annoteringstyper som ska inkluderas. GroupDocs.Annotation låter dig filtrera vilka annoteringstyper som skrivs till utdatafilen. Skapa en `SaveOptions`‑instans, sätt `AnnotationTypes`‑samlingen till de typer du vill behålla, och skicka alternativen till `Save`. Detta är perfekt för att generera PDF‑filer enbart för granskare eller för att ta bort temporära anteckningar innan arkivering.

```csharp
var saveOptions = new SaveOptions
{
    AnnotationTypes = new[] { AnnotationType.Text, AnnotationType.Area }
};
annotator.Save("filtered.pdf", saveOptions);
```

## Verkliga implementeringsscenarier

### Scenario 1: Dokumentgranskningsarbetsflöde
Flera granskare lägger till **Area**, **Ellipse** och **Text**‑annoteringar. Efter granskningsrundan genererar du tre PDF‑filer:
1. Full version med varje kommentar.  
2. Endast‑granskare‑version (filtrerar bort interna anteckningar).  
3. Ren version för slutgiltigt godkännande (behåller endast markeringar).

### Scenario 2: Automatisk rapportgenerering
Din backend bearbetar dagliga försäljningsrapporter, markerar automatiskt nyckeltal med område‑annoteringar och cirklar avvikande diagram med ellips‑annoteringar. De genererade PDF‑filerna e‑postas sedan till intressenter utan någon manuell inblandning.

### Scenario 3: Samarbetsjuridiska dokument
Advokatbyråer behöver ofta separera partnerkommentarer från juniorassistenters anteckningar. Genom att tagga annoteringar med anpassad metadata och använda selektiv sparning kan du producera en partner‑gransknings‑PDF som döljer junioranteckningar, vilket förenklar versionskontroll.

## Prestandaoptimering för produktionsanvändning

### Hur hanterar man minne vid annotering av stora PDF‑filer?

`LoadOptions` låter dig specificera hur en PDF laddas, t.ex. sidintervall eller lösenord. När en PDF överstiger 100 MB, undvik att ladda hela filen genom att använda `LoadOptions`‑konstruktorn som accepterar ett sidintervall. Bearbeta sidor i batchar, frigör varje `Annotator`‑instans med ett `using`‑block, och rensa temporära filer efter varje batch. Detta tillvägagångssätt håller maxminnesanvändning under 200 MB även för 500‑sidiga dokument.

```csharp
using (var annotator = new Annotator("large.pdf", new LoadOptions { PageNumbers = new[] { 0, 1, 2 } }))
{
    // annotate first three pages
}
```

### Bästa praxis för minneshantering
- **Wrap alltid `Annotator` i ett `using`‑statement** för att garantera att ohanterade resurser frigörs.  
- **Batch‑processa annoteringar**: samla alla annoteringar för ett dokument, och anropa sedan `Add` en gång.  
- **Undvik att ladda hela PDF‑filer** när du bara behöver modifiera ett delmängd av sidor; använd `LoadOptions.PageNumbers`.

### Strategier för hantering av stora filer
1. **Sidsvis bearbetning** – Ladda, annotera och spara en sida åt gången.  
2. **Strömmande utdata** – Rikta `Save`‑metoden till ett `MemoryStream` för att undvika mellansteg på disk.  
3. **Rengöring av temporära filer** – Ta bort alla temporära filer som skapats av annotatorn efter varje operation.

### Överväganden för samtidig bearbetning
- **Trådsäkerhet:** `Annotator`‑instanser är inte trådsäkra. Skapa en separat instans per tråd.  
- **Resurstilldelning:** Begränsa samtidiga jobb till antalet CPU‑kärnor för att förhindra CPU‑översvämmning.  
- **Async‑API:** `SaveAsync` sparar det annoterade dokumentet asynkront och returnerar en Task, vilket är användbart i ASP.NET Core‑miljöer.

## Felsökning av vanliga problem

### Problem 1: “File Not Found”-fel
**Direkt svar:** Verifiera att filvägen du skickar till `new Annotator(...)` är absolut eller korrekt relativ till den körande assemblyn, och säkerställ att applikationsprocessen har läsrättigheter för den platsen. Om filen ligger på en nätverksdelning, mappa delningen eller använd UNC‑vägar.

**Typiska lösningar:**  
- Använd `Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Docs", "sample.pdf")`.  
- Ge IIS‑applikationspoolens identitet läs‑/skrivrättigheter på mappen.

### Problem 2: Annoteringar visas på fel plats
**Direkt svar:** Säkerställ att du använder samma koordinatsystem (övre‑vänstra ursprung) och att sidans DPI matchar de värden du anger. Hämta sidstorleken via `annotator.GetPageInfo(pageNumber)` och beräkna koordinater relativt den storleken.

**Typiska lösningar:**  
- Multiplicera koordinater med sidans skalningsfaktor om PDF‑filen skapades med en icke‑standard DPI.  
- Dubbelkolla att du inte blandar punkter (1/72 tum) med pixlar.

### Problem 3: Prestandaproblem med stora filer
**Direkt svar:** Byt till sidintervallsladdning, bearbeta annoteringar i batchar och frigör varje `Annotator`‑instans omedelbart. Aktivera också `MemoryCache`‑alternativet i `LoadOptions` för att återanvända buffertar mellan operationer.

**Typiska lösningar:**  
- Sätt `LoadOptions.UseMemoryCache = true`.  
- Bearbeta filer asynkront med `await annotator.SaveAsync(...)`.

### Problem 4: Licensrelaterade fel
**Direkt svar:** Placera `.lic`‑filen i en mapp som applikationen kan läsa, och anropa `License license = new License(); license.SetLicense("path/to/license.lic");` innan någon annan GroupDocs‑anrop. Verifiera att licensversionen matchar biblioteksversionen du använder.

**Typiska lösningar:**  
- Kontrollera att licensfilen inte är korrupt (jämför filstorlek).  
- Säkerställ att du inte blandar en provlicens med en kommersiell i samma miljö.

## Avancerade tips och bästa praxis

### Färghantering
Konsekventa färger förbättrar läsbarheten för granskare. Definiera en palett (t.ex. Gul för markeringar, Röd för kritiska problem) och lagra den i en statisk hjälparklass. Kom ihåg att använda högkontrastfärger för tillgänglighet och att lägga till en förklaringssida i PDF‑filen som referens.

### Mönster för felhantering
Wrapa alla annoteringsanrop i try‑catch‑block som specifikt fångar `GroupDocs.Annotation.Exceptions.AnnotationException`. Logga undantagsmeddelandet, stack‑trace och PDF‑namnet för att underlätta felsökning.

### Teststrategier
- **Unit‑tester:** Använd en liten PDF med kända dimensioner, lägg till en annotering och verifiera att `GetAnnotations()` returnerar de förväntade koordinaterna.  
- **Integrationstester:** Kör hela arbetsflödet på PDF‑filer från 1 sida till 200 sidor och verifiera att behandlingstiden hålls under 5 sekunder för filer under 50 MB.  
- **Lasttester:** Simulera 50 samtidiga annoteringsförfrågningar med ett verktyg som k6 eller Apache JMeter och övervaka CPU/minne.

## Vanliga frågor

**Q: Hur hanterar jag PDF‑filer med olika sidstorlekar?**  
A: GroupDocs läser automatiskt varje sidas dimensioner. När du placerar annoteringar, fråga alltid `annotator.GetPageInfo(pageNumber)` och beräkna koordinater baserat på sidans bredd och höjd.

**Q: Kan jag annotera lösenordsskyddade PDF‑filer?**  
A: Ja. Använd `LoadOptions`‑konstruktorn som accepterar en lösenordsträng, t.ex. `new LoadOptions { Password = "secret" }`, och skicka den till `Annotator`‑konstruktorn.

**Q: Vad är det maximala antalet annoteringar jag kan lägga till i en enda PDF?**  
A: Det finns ingen hård gräns, men prestandan försämras efter några tusen annoteringar. För mycket stora annoteringsuppsättningar, gruppera dem i logiska sektioner och bearbeta varje sektion separat.

**Q: Hur tar jag bort specifika annoteringar programatiskt?**  
A: Hämta annoteringens `Id` via `GetAnnotations()`, anropa sedan `Delete(id)` eller skapa en `SaveOptions`‑instans som exkluderar den oönskade `AnnotationType`.

**Q: Kan jag anpassa annoteringens utseende utöver färger?**  
A: Absolut. Du kan sätta opacitet, kanttjocklek, streckstil och till och med bädda in anpassade SVG‑ikoner för stämpelannoteringar.

**Q: Vad händer om jag försöker annotera en skannad (bildbaserad) PDF?**  
A: Annoteringar renderas som överlagringsobjekt ovanpå sidans bild. De ändrar inte den underliggande rasterdata, så PDF‑filen förblir sökbar om OCR‑lager finns.

**Q: Hur hanterar jag mycket stora PDF‑filer utan att få slut på minne?**  
A: Bearbeta dokumentet sida‑för‑sida med `LoadOptions.PageNumbers`, frigör varje `Annotator`‑instans omedelbart efter användning, och aktivera strömmande sparning till ett `MemoryStream` för att undvika diskspikar.

## Integration med ASP.NET‑applikationer

När du exponerar annoteringsfunktionalitet via ett webb‑API, håll dig till följande mönster:

1. **Controller tar emot PDF‑strömmen** från klienten.  
2. **Validera filstorleken** (avvisa > 200 MB om du inte har särskild hantering).  
3. **Instansiera `Annotator` i ett `using`‑block** för att garantera frigöring.  
4. **Applicera annoteringar** baserat på JSON‑payload som beskriver annoteringstyp, koordinater och text.  
5. **Spara till en temporär plats**, och strömma sedan resultatet tillbaka till klienten med lämplig `Content‑Disposition`‑header.

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

## Ytterligare resurser
- [GroupDocs köpsida](https://purchase.groupdocs.com/buy)  
- [Köp GroupDocs](https://purchase.groupdocs.com/buy)  
- [GroupDocs Annotation-dokumentation](https://docs.groupdocs.com/annotation/net/)  
- [GroupDocs API-referens](https://reference.groupdocs.com/annotation/net/)  
- [Senaste releaser](https://releases.groupdocs.com/annotation/net/)  
- [Prova GroupDocs gratis](https://releases.groupdocs.com/annotation/net/)  
- [Begär en tillfällig licens](https://purchase.groupdocs.com/temporary-license/)  
- [GroupDocs-forum](https://forum.groupdocs.com/c/annotation/)

## Slutsats och nästa steg

Du har nu en **fullständig, produktionsklar färdplan** för att bygga ett **dokumentgranskningssystem** drivet av GroupDocs.Annotation för .NET. Du har lärt dig hur du installerar biblioteket, lägger till område-, ellips- och textannoteringar, filtrerar sparningar och håller minnesanvändning låg även med massiva PDF‑filer.  

**Nästa åtgärder du kan göra idag:**  

1. **Experimentera** med ytterligare annoteringstyper såsom `ArrowAnnotation` och `StampAnnotation`.  
2. **Integrera** arbetsflödet i ditt befintliga ASP.NET Core‑API eller skrivbords‑WPF‑applikation.  
3. **Utforska** den fullständiga API‑referensen för att upptäcka avancerade funktioner som annoteringsversionering och anpassad metadata.  
4. **Gå med i** GroupDocs‑community‑forum för stöd från kollegor och för att hålla dig uppdaterad om nya releaser.

---

**Senast uppdaterad:** 2026-05-26  
**Testat med:** GroupDocs.Annotation 23.11 for .NET  
**Författare:** GroupDocs  

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

## Relaterade handledningar

- [GroupDocs Annotation .NET‑handledning – Komplett guide för dokumenthantering](/annotation/net/annotation-management/)
- [Dokumentförhandsgranskning .NET‑handledningar – Komplett GroupDocs.Annotation‑guide](/annotation/net/document-preview/)
- [GroupDocs Annotation Metered‑licenstutorial – Komplett .NET‑installationsguide](/annotation/net/licensing-and-configuration/implement-metered-license-groupdocs-annotation-net/)