---
categories:
- Document Processing
date: '2026-05-21'
description: Naučte se, jak anotovat PDF soubory pomocí GroupDocs Annotation .NET
  v C#. Tento krok‑za‑krokem průvodce pokrývá nastavení, přidávání, aktualizaci a
  správu PDF anotací pro právní, vzdělávací a podnikové případy použití.
keywords:
- how to annotate pdf
- legal document annotation
- collaborative pdf markup
- create document review system
lastmod: '2026-05-21'
linktitle: Průvodce GroupDocs Annotation .NET
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to annotate PDF files with GroupDocs Annotation .NET in C#.
    This step‑by‑step guide covers setup, adding, updating, and managing PDF annotations
    for legal, education, and enterprise use cases.
  headline: How to Annotate PDF using GroupDocs Annotation .NET (C#) Guide
  type: TechArticle
- questions:
  - answer: Yes, the free trial provides full functionality for 30 days but adds evaluation
      watermarks to every output file. For any production deployment you must apply
      a temporary or full license to remove those watermarks.
    question: Can I use GroupDocs.Annotation .NET without a license?
  - answer: The library works with .NET Framework 4.6.1+, .NET Core 2.0+, .NET 5,
      .NET 6, and .NET 7, making it suitable for both legacy Windows services and
      modern cross‑platform containers.
    question: Which .NET versions are supported by GroupDocs.Annotation?
  - answer: Pricing starts around $1,999 for a developer license and scales with the
      number of deployed applications. Check the [GroupDocs pricing page](https://purchase.groupdocs.com/buy)
      for the latest rates and volume discounts.
    question: How much does GroupDocs.Annotation .NET cost?
  - answer: Over **50 formats** are supported, including PDF, DOC/DOCX, PPT/PPTX,
      XLS/XLSX, JPEG, PNG, TIFF, and many more. PDF receives the most comprehensive
      feature set, including vector‑based shapes and OCR‑ready redaction.
    question: What document formats can I annotate with GroupDocs.Annotation?
  - answer: 'Yes. Provide the password when constructing the `Annotator`:'
    question: Can I annotate password‑protected PDFs?
  type: FAQPage
tags:
- GroupDocs
- Annotation
- C#
- PDF
- Document Management
title: Jak anotovat PDF pomocí GroupDocs Annotation .NET (C#) průvodce
type: docs
url: /cs/net/annotation-management/annotate-documents-groupdocs-dotnet/
weight: 1
---

# Jak anotovat PDF pomocí GroupDocs Annotation .NET (C#)

Už jste někdy potřebovali **jak anotovat pdf** soubory programově a přemýšleli, která knihovna vám poskytne jak sílu, tak jednoduchost? Ať už vytváříte platformu pro právní revize, e‑learning systém nebo kolaborativní workflow dokumentů, GroupDocs.Annotation .NET nabízí produkčně připravené API, které vám umožní přidávat, upravovat a mazat PDF anotace přímo z C# kódu. V tomto průvodci se naučíte vše potřebné k implementaci plnohodnotného anotovacího enginu, od počátečního nastavení až po ladění výkonu pro obrovské knihovny dokumentů.

## Rychlé odpovědi
- **Jaký je nejrychlejší způsob, jak přidat textovou poznámku do PDF?** Načtěte dokument pomocí `Annotator`, vytvořte `TextAnnotation`, nastavte jeho `Box` a `Message`, a poté zavolejte `Add()` – vše za méně než sekundu pro typické stránky.  
- **Které verze .NET jsou podporovány?** .NET Framework 4.6.1+, .NET Core 2.0+, .NET 5, .NET 6 a .NET 7.  
- **Potřebuji licenci pro produkci?** Ano – plná nebo dočasná licence odstraňuje vodoznaky a odemyká všechny funkce.  
- **Mohu zpracovávat 200‑stránkové PDF na serveru s 4 GB RAM?** Ano, pomocí dávkového zpracování a správných vzorů uvolňování zdrojů, jak je ukázáno později.  
- **Je GroupDocs.Annotation vhodný pro anotaci právních dokumentů?** Rozhodně – podporuje více než 50 formátů, detailní řízení oprávnění a metadata připravená pro audit.

## Co je “jak anotovat pdf”?
**“Jak anotovat pdf”** odkazuje na proces programového přidávání značek – jako jsou komentáře, zvýraznění, tvary nebo redakce – do PDF souborů. Pomocí GroupDocs.Annotation .NET můžete tento workflow automatizovat, ukládat data anotací do databází a okamžitě zobrazovat výsledky ve webových nebo desktopových prohlížečích.

## Proč použít GroupDocs.Annotation pro PDF anotace?
GroupDocs.Annotation podporuje **více než 50 vstupních a výstupních formátů**, dokáže zpracovat PDF až do **500 MB** bez načítání celého souboru do paměti a poskytuje **vláknově‑bezpečné** operace, když každá žádost vytvoří vlastní instanci `Annotator`. Ve srovnání s lehčími knihovnami zaměřenými jen na PDF vám také umožňuje anotovat soubory Word, PowerPoint a obrázky pomocí stejného API, což dramaticky snižuje vývojové úsilí pro platformy s více formáty.

## Praktické aplikace: Kde anotace dokumentů vynikají

Porozumění obchodnímu kontextu vám pomůže vybrat správný typ anotace.

- **Právní revize dokumentů** – Právníci přidávají komentáře, zvýrazňují klauzule a připojují revizní historii. GroupDocs.Annotation sleduje každou změnu pomocí uživatelských ID, časových razítek a volitelných digitálních podpisů pro auditní soulad.  
- **Vzdělávací platformy** – Instruktoři mohou hodnotit úkoly kreslením tvarů, přidáváním poznámek nebo vložením audio zpětné vazby přímo do PDF studentů.  
- **Zdravotnická dokumentace** – Klinici anotují radiologické zprávy nebo pacientské karty při zachování metadat v souladu s HIPAA.  
- **Softwarová dokumentace** – Technickí autoři spolupracují na specifikacích API, vkládají výzvy a revizní poznámky, aniž by opustili zdrojové PDF.  
- **Finanční služby** – Odpovědní osoby za soulad označují smlouvy o úvěrech, hodnocení rizik a auditní stopy a poté exportují anotovanou verzi pro archivaci.

## Předpoklady a nastavení: Připravení vašeho prostředí

### Systémové požadavky
- **IDE**: Visual Studio 2019 nebo novější (Community edice funguje dobře).  
- **Runtime**: .NET Framework 4.6.1+ **nebo** .NET Core 2.0+ (doporučeno 8 GB RAM pro velké PDF).  
- **Oprávnění**: Zápisový přístup do složky, kde budou ukládány anotované PDF.

### Předpoklady znalostí
- Základní syntaxe C# a objektově orientované koncepty.  
- Znalost správy balíčků NuGet.  
- Porozumění souborovému I/O (čtení/zápis streamů).

### Instalace GroupDocs.Annotation .NET
Knihovnu můžete přidat pomocí NuGet. Vyberte metodu, která odpovídá vašemu workflow.

**Použití NuGet Package Manager Console**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**Použití .NET CLI** (preferováno pro CI/CD pipeline)  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

> **Tip:** Vždy připněte konkrétní verzi (např. `Install-Package GroupDocs.Annotation -Version 23.12`). Tím zabráníte neúmyslným breaking changes při automatické aktualizaci balíčku. Podívejte se na nejnovější vydání na [GroupDocs releases page](https://releases.groupdocs.com/annotation/net/).

### Možnosti licence: Vyberte, co vyhovuje vašemu projektu
- **Bezplatná zkušební verze** – Plná funkčnost s evaluačními vodoznaky po 30 dnů.  
- **Dočasná licence** – Odstraňuje vodoznaky po 30 dnů, ideální pro proof‑of‑concepty. Viz [temporary license page](https://purchase.groupdocs.com/temporary-license/).  
- **Plná licence** – Neomezené použití v produkci, prioritní podpora a žádné vodoznaky. Zakupte přes [GroupDocs store](https://purchase.groupdocs.com/buy).

### Základní nastavení projektu
Vytvořte nový C# konzolový nebo ASP.NET projekt a po instalaci balíčku přidejte následující using direktivy:

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System.IO;
using System.Collections.Generic;

// Initialize Annotator with an input document path
string inputPath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pdf");
```

> **Důležité:** Nahraďte `YOUR_DOCUMENT_DIRECTORY` absolutní cestou k vašim PDF. Použití `Path.Combine` zajišťuje správné oddělovače cest ve Windows i Linuxu.

## Praktický tutoriál: Přidání první anotace

### Jak načíst PDF dokument pro anotaci?
Třída `Annotator` je hlavní komponenta, která načítá dokument a spravuje všechny operace anotací. Správné načtení PDF zajišťuje, že knihovna může přečíst rozměry stránky, metadata a existující anotace před aplikací jakýchkoli změn.  
Načtěte PDF pomocí konstruktoru `Annotator`, předáním cesty k souboru a volitelných možností načtení. Tento krok ověří soubor a připraví jeho reprezentaci v paměti, kterou můžete bezpečně upravovat, a zároveň zpracuje šifrované soubory, pokud je zadáno heslo.

```csharp
try 
{
    using (Annotator annotator = new Annotator(inputPath))
    {
        // Your annotation code goes here
        Console.WriteLine("Document loaded successfully!");
    }
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

Blok `try‑catch` chrání před chybějícími soubory, poškozenými PDF nebo nepodporovanými formáty a zajišťuje, že aplikace selže elegantně místo zhroucení.

### Jak přidat textovou anotaci do PDF?
`TextAnnotation` představuje komentář ve stylu lepicí poznámky, který lze umístit na stránku PDF. Přidání zahrnuje vytvoření objektu, definování jeho umístění, nastavení zobrazované zprávy a nakonec vložení do dokumentu pomocí `Annotator`.  
Vytvořte objekt `TextAnnotation`, definujte jeho ohraničující obdélník pomocí vlastnosti `Box`, nastavte viditelnou `Message` a poté zavolejte `Add()` na `Annotator`. Anotace se okamžitě zobrazí na určené stránce a můžete upravit její vzhled pomocí nastavení barvy a průhlednosti, pokud je potřeba.

```csharp
// Create a highlight annotation
HighlightAnnotation highlight = new HighlightAnnotation
{
    Box = new Rectangle(100, 100, 200, 20), // x, y, width, height
    CreatedOn = DateTime.Now,
    Message = "This section needs review",
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "Please verify these numbers",
            RepliedOn = DateTime.Now
        }
    }
};

// Add the annotation to the document
annotator.Add(highlight);
```

> **Proč je důležitá vlastnost `Box`:** Obdélník používá body (1 point = 1/72 inch) měřené od levého dolního rohu stránky. Přesné souřadnice vám umožní umístit poznámky přesně tam, kde je recenzenti očekávají.

### Jak uložit anotovaný PDF bez přepsání zdroje?
Uložení do nového souboru zachovává původní dokument pro auditní stopy a scénáře rollbacku. Metoda `Save` zapíše všechny změny, včetně nových anotací a metadat, na zadanou cestu a ponechá zdroj nedotčený.  
Zavolejte `Save()` na `Annotator` a uveďte novou cestu k souboru. Tím zachováte původní dokument, což je nezbytné pro auditní stopy a rollback, a můžete volitelně specifikovat jiný výstupní formát, pokud je potřeba konverze.

```csharp
string outputPath = Path.Combine("YOUR_OUTPUT_DIRECTORY", "annotated_document.pdf");
annotator.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

> **Best Practice:** Ukládejte originální a anotované verze do samostatných složek pod verzovacím systémem. Tato strategie zjednodušuje regulatorní soulad a sledování změn.

## Pokročilé techniky anotací

### Jak mohu přidat více typů anotací v jedné operaci?
GroupDocs.Annotation nabízí bohatou sadu tříd anotací – `HighlightAnnotation`, `StrikeoutAnnotation`, `PolylineAnnotation`, `RedactionAnnotation` a další. Vytvořením každé instance, nastavením jejích vlastností a přidáním do stejného `Annotator` před uložením minimalizujete I/O a udržíte stav dokumentu konzistentní.  
Instancujte každý typ anotace, nastavte jeho specifické atributy (barvu, průhlednost, body atd.) a přidejte je sekvenčně do stejné instance `Annotator`. Když zavoláte `Save()`, všechny anotace jsou zapsány najednou, což zajišťuje atomické aktualizace a snižuje riziko částečných zápisů.

```csharp
// Text annotation for comments
TextAnnotation textNote = new TextAnnotation
{
    Box = new Rectangle(300, 200, 100, 30),
    Message = "Review required",
    CreatedOn = DateTime.Now,
    FontColor = 16711680, // Red color in RGB
    BackgroundColor = 16777215 // White background
};

// Arrow annotation to point out specific elements
ArrowAnnotation pointer = new ArrowAnnotation
{
    Box = new Rectangle(150, 150, 50, 50),
    Message = "Important calculation here",
    CreatedOn = DateTime.Now
};

// Add all annotations at once
annotator.Add(textNote);
annotator.Add(pointer);
```

### Jak aktualizovat barvu nebo komentář existující anotace?
Metoda `GetById` získá konkrétní anotaci podle jejího jedinečného identifikátoru, což vám umožní upravit jen požadovaná pole. Po načtení objektu můžete změnit vlastnosti jako `Color` nebo `Message` a poté změny uložit pomocí `Update`.  
Získejte anotaci podle jejího jedinečného `Id` pomocí `GetById()`, upravte požadované vlastnosti (např. `Color`, `Message`) a zavolejte `Update()`. Tento přístup zabraňuje opětovnému vytváření anotace a zachovává její původní umístění, historii verzí a případné připojené odpovědi.

```csharp
// Get all annotations from the document
List<AnnotationBase> annotations = annotator.Get();

// Find and update a specific annotation
foreach (var annotation in annotations)
{
    if (annotation.Message.Contains("Review required"))
    {
        annotation.Message = "Review completed ✓";
        annotator.Update(annotation);
        break;
    }
}
```

> **Poznámka k výkonu:** Pro dokumenty s tisíci anotacemi cacheujte ID anotací ve slovníku, aby se předešlo lineárním vyhledáváním.

## Běžné problémy a řešení

### Problém 1 – “Formát dokumentu není podporován”
**Přímá odpověď:** Ověřte, že přípona souboru je uvedena v seznamu podporovaných formátů GroupDocs.Annotation; pokud ne, nejprve soubor převeďte na PDF nebo použijte jiný produkt GroupDocs, který daný formát zpracuje.  
**Řešení:**  
- Zkontrolujte [seznam podporovaných formátů](https://docs.groupdocs.com/annotation/net/supported-document-formats/)  
- Použijte GroupDocs.Conversion k převodu nepodporovaných souborů na PDF před anotací.

```csharp
// Check if format is supported before processing
string extension = Path.GetExtension(inputPath).ToLower();
if (extension != ".pdf" && extension != ".docx" && extension != ".pptx")
{
    throw new NotSupportedException($"File format {extension} is not supported");
}
```

### Problém 2 – Anotace se zobrazují na špatných pozicích
**Přímá odpověď:** Ujistěte se, že používáte správný souřadnicový systém (počátek v levém dolním rohu) a že jsou respektována metadata o otočení stránky. Podle toho upravte hodnoty `Box`.  
**Řešení:**  
```csharp
// Always validate coordinates before adding annotations
private bool IsValidCoordinate(Rectangle box, double pageWidth, double pageHeight)
{
    return box.X >= 0 && box.Y >= 0 && 
           (box.X + box.Width) <= pageWidth && 
           (box.Y + box.Height) <= pageHeight;
}
```

### Problém 3 – Problémy s pamětí u velkých dokumentů
**Přímá odpověď:** Zpracovávejte velké PDF v dávkách, po každé dávce uvolněte (`dispose`) `Annotator` a povolte režim streamování, aby se celý soubor nenačítal do RAM.  
**Řešení:**  

```csharp
// Process large documents in chunks
using (Annotator annotator = new Annotator(inputPath))
{
    // Set memory-friendly options
    LoadOptions loadOptions = new LoadOptions
    {
        PreviewPageCount = 1 // Load pages on demand
    };
    
    // Process annotations in batches
    const int batchSize = 10;
    for (int i = 0; i < annotations.Count; i += batchSize)
    {
        var batch = annotations.Skip(i).Take(batchSize);
        foreach (var annotation in batch)
        {
            annotator.Add(annotation);
        }
        
        // Force garbage collection between batches for large documents
        if (i % 50 == 0)
        {
            GC.Collect();
            GC.WaitForPendingFinalizers();
        }
    }
}
```

## Tipy pro optimalizaci výkonu

### Jak efektivně dávkově zpracovat tisíce PDF?
Shromážděte požadavky na anotace do seznamu, otevřete jeden `Annotator` pro dokument, aplikujte všechny změny a poté jednou zavolejte `Save()`. Tím snížíte I/O zátěž, využijete interní bufferování a udržíte předvídatelnou spotřebu paměti při velkém zatížení.  
Shromážděte požadavky na anotace do seznamu, otevřete jeden `Annotator` pro dokument, aplikujte všechny změny a poté jednou zavolejte `Save()`. Tím snížíte I/O zátěž a využijete interní bufferování.

```csharp
// Inefficient approach (don't do this)
foreach (var annotation in annotations)
{
    annotator.Add(annotation);
    annotator.Save(outputPath); // Saving after each annotation is expensive
}

// Efficient approach
foreach (var annotation in annotations)
{
    annotator.Add(annotation);
}
annotator.Save(outputPath); // Save once at the end
```

### Jak spravovat paměť při práci s PDF o stovkách stránek?
Povolte příznak `LoadOptions` `MemoryOptimization = true` a zpracovávejte stránky sekvenčně. Tím řeknete knihovně, aby v paměti držela jen aktivní stránku, což dramaticky snižuje nároky na RAM u velmi velkých souborů.

```csharp
// Use using statements to ensure proper disposal
using (var annotator = new Annotator(inputPath))
{
    // Your annotation code here
} // Annotator is automatically disposed, freeing memory
```

### Jak by měl být cachován často přistupovaný dokument?
Uložte serializovaný JSON anotací do distribuované cache (např. Redis) s klíčem podle ID dokumentu. Když uživatel požaduje stejný PDF, načtěte cachovanou sadu anotací místo opětovného čtení souboru z disku, čímž snížíte latenci a zátěž I/O.

```csharp
// Cache document metadata to avoid reloading
private static readonly Dictionary<string, DocumentInfo> _documentCache = 
    new Dictionary<string, DocumentInfo>();

private DocumentInfo GetDocumentInfo(string path)
{
    if (!_documentCache.ContainsKey(path))
    {
        using (var annotator = new Annotator(path))
        {
            _documentCache[path] = annotator.GetDocumentInfo();
        }
    }
    return _documentCache[path];
}
```

## Nejlepší postupy pro produkční aplikace

### Jak implementovat robustní zpracování chyb a logování?
Zabalte každou operaci `Annotator` do bloků `try‑catch`, logujte výjimky pomocí strukturovaného loggeru (Serilog, NLog) a zahrňte cestu k dokumentu, ID uživatele a stack trace. To výrazně usnadní odstraňování problémů v produkci a pomůže splnit požadavky auditního souladu.

```csharp
public async Task<bool> AddAnnotationSafely(string documentPath, AnnotationBase annotation)
{
    try
    {
        using (var annotator = new Annotator(documentPath))
        {
            annotator.Add(annotation);
            annotator.Save(documentPath.Replace(".pdf", "_annotated.pdf"));
            return true;
        }
    }
    catch (Exception ex)
    {
        // Log the error (use your preferred logging framework)
        Console.WriteLine($"Annotation failed for {documentPath}: {ex.Message}");
        return false;
    }
}
```

### Jak mohu validovat uživatelem poskytnutá data anotací?
Zkontrolujte, že příchozí pole JSON (číslo stránky, souřadnice obdélníku, typ anotace) spadají do přijatelných rozsahů před vytvořením objektů anotací. Odmítněte mimo‑rozsahové souřadnice s jasnou HTTP 400 odpovědí a poskytněte užitečnou chybovou zprávu.

```csharp
public bool ValidateAnnotationInput(AnnotationBase annotation)
{
    if (annotation == null)
        return false;
    
    if (string.IsNullOrWhiteSpace(annotation.Message))
        return false;
    
    if (annotation.Box.Width <= 0 || annotation.Box.Height <= 0)
        return false;
    
    return true;
}
```

### Jak zajistit bezpečnost vláken v multi‑uživatelské webové službě?
Instancujte nový `Annotator` pro každou žádost; nikdy nesdílejte jednu instanci mezi vlákny. Pokud potřebujete koordinovat přístup ke sdílenému souboru, použijte `SemaphoreSlim` nebo zámek na úrovni souboru, aby se zabránilo souběžnému zápisu.

```csharp
private readonly object _annotationLock = new object();

public void AddAnnotationThreadSafe(string documentPath, AnnotationBase annotation)
{
    lock (_annotationLock)
    {
        using (var annotator = new Annotator(documentPath))
        {
            annotator.Add(annotation);
            annotator.Save(documentPath);
        }
    }
}
```

## Kdy použít GroupDocs.Annotation vs. alternativy

**Zvolte GroupDocs.Annotation, když** potřebujete:
- Podporu více formátů (PDF, DOCX, PPTX, obrázky).  
- Pokročilé typy anotací jako redakce, volné kreslení a vlastní metadata.  
- Enterprise‑úroveň licencování, podpora s SLA a pravidelné bezpečnostní aktualizace.

**Zvažte lehčí alternativy, pokud** pracujete pouze s PDF, máte přísná rozpočtová omezení nebo potřebujete open‑source stack.

## Často kladené otázky

**Q: Mohu použít GroupDocs.Annotation .NET bez licence?**  
A: Ano, bezplatná zkušební verze poskytuje plnou funkčnost po 30 dnů, ale přidává evaluační vodoznaky ke každému výstupnímu souboru. Pro jakékoli nasazení do produkce musíte použít dočasnou nebo plnou licenci k odstranění těchto vodoznaků.

**Q: Které verze .NET jsou podporovány GroupDocs.Annotation?**  
A: Knihovna funguje s .NET Framework 4.6.1+, .NET Core 2.0+, .NET 5, .NET 6 a .NET 7, což ji činí vhodnou jak pro starší Windows služby, tak pro moderní cross‑platform kontejnery.

**Q: Kolik stojí GroupDocs.Annotation .NET?**  
A: Cena začíná kolem $1,999 za vývojářskou licenci a roste s počtem nasazených aplikací. Podívejte se na [GroupDocs pricing page](https://purchase.groupdocs.com/buy) pro aktuální sazby a objemové slevy.

**Q: Jaké formáty dokumentů mohu anotovat pomocí GroupDocs.Annotation?**  
A: Podporováno je více než **50 formátů**, včetně PDF, DOC/DOCX, PPT/PPTX, XLS/XLSX, JPEG, PNG, TIFF a mnoha dalších. PDF získává nejkomplexnější sadu funkcí, včetně vektorových tvarů a redakce připravené pro OCR.

**Q: Mohu anotovat PDF chráněné heslem?**  
A: Ano. Poskytněte heslo při vytváření `Annotator`:

```csharp
LoadOptions loadOptions = new LoadOptions { Password = "your_password" };
using (Annotator annotator = new Annotator(inputPath, loadOptions))
{
    // Your annotation code here
}
```

**Q: Proč se moje anotace zobrazují na špatné pozici?**  
A: GroupDocs používá kartézský souřadnicový systém, kde (0,0) je levý dolní roh a měření jsou v bodech. Nesprávné umístění obvykle pramení z používání hodnot v pixelech nebo ignorování otočení stránky. Převádějte pixelové hodnoty na body (1 pixel ≈ 0.75 point při 96 DPI) a upravte podle metadat o otočení.

```csharp
// Correct approach - validate coordinates
private bool ValidateCoordinates(Rectangle box, double pageWidth, double pageHeight)
{
    return box.X >= 0 && box.Y >= 0 && 
           (box.X + box.Width) <= pageWidth && 
           (box.Y + box.Height) <= pageHeight;
}
```

**Q: Jak získat existující anotace z PDF?**  
A: Zavolejte metodu `Get()` na instanci `Annotator`; vrátí kolekci všech objektů anotací s jejich ID, typy a metadaty.

```csharp
using (Annotator annotator = new Annotator(inputPath))
{
    List<AnnotationBase> annotations = annotator.Get();
    foreach (var annotation in annotations)
    {
        Console.WriteLine($"Annotation: {annotation.Message}");
    }
}
```

**Q: Mohu programově smazat konkrétní anotace?**  
A: Ano. Použijte `Delete(id)` k odstranění jedné anotace nebo `DeleteAll()` k úplnému vymazání dokumentu. Můžete také před smazáním filtrovat podle typu.

```csharp
List<AnnotationBase> annotationsToDelete = annotator.Get()
    .Where(a => a.Message.Contains("obsolete"))
    .ToList();

foreach (var annotation in annotationsToDelete)
{
    annotator.Remove(annotation);
}
```

**Q: Jak aktualizovat vlastnosti anotace, jako je barva nebo zpráva?**  
A: Načtěte anotaci, upravte `Color` nebo `Message` a poté zavolejte `Update()`. Změna se uloží při dalším volání `Save()`.

```csharp
var annotations = annotator.Get();
var targetAnnotation = annotations.FirstOrDefault(a => a.Id == specificId);
if (targetAnnotation != null)
{
    targetAnnotation.Message = "Updated message";
    annotator.Update(targetAnnotation);
}
```

**Q: Mohu přidat vlastní metadata k anotacím?**  
A: Rozhodně. Většina tříd anotací expose kolekci `Replies`, kde můžete ukládat páry klíč‑hodnota, což vám umožní připojit ID recenzentů, časová razítka nebo stavy workflow.

```csharp
var annotation = new HighlightAnnotation
{
    // ... other properties
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "Custom metadata: priority=high, category=legal",
            RepliedOn = DateTime.Now
        }
    }
};
```

**Q: Podporuje GroupDocs.Annotation digitální podpisy na anotovaných PDF?**  
A: Zatímco knihovna Annotation se zaměřuje na značky, můžete ji kombinovat s GroupDocs.Signature .NET k aplikaci kryptografických podpisů po přidání anotací, což zajišťuje jak vizuální, tak právní integritu.

**Q: Mohu exportovat anotace do JSON nebo XML pro externí zpracování?**  
A: Knihovna neobsahuje vestavěný exportér, ale můžete si sami serializovat objekty anotací pomocí `System.Text.Json` nebo `XmlSerializer`. To usnadňuje integraci s externími auditními systémy.

```csharp
List<AnnotationBase> annotations = annotator.Get();
string jsonAnnotations = JsonConvert.SerializeObject(annotations, Formatting.Indented);
File.WriteAllText("annotations.json", jsonAnnotations);
```

---

**Poslední aktualizace:** 2026-05-21  
**Testováno s:** GroupDocs.Annotation 23.12 pro .NET  
**Autor:** GroupDocs  

---

## Související tutoriály

- [GroupDocs Annotation .NET Tutoriál - Kompletní průvodce pro správu dokumentů](/annotation/net/annotation-management/)
- [Uložit PDF anotace .NET - Kompletní průvodce ukládáním dokumentů](/annotation/net/document-saving/)
- [Načíst PDF z URL .NET - Kompletní průvodce s GroupDocs.Annotation](/annotation/net/document-loading-essentials/load-document-from-url/)