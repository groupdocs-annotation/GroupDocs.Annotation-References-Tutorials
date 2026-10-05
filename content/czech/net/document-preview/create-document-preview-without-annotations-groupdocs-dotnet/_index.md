---
categories:
- Document Processing
date: '2026-10-05'
description: Naučte se, jak skrýt anotace při generování čistých document preview
  v C# pomocí GroupDocs.Annotation .NET. Praktický návod krok za krokem s ukázkami
  kódu, tipy na výkon a řešením problémů.
keywords:
- how to hide annotations
- preview document without annotations
- remove annotations from preview
- clean document preview .NET
- generate document preview without annotations
lastmod: '2026-10-05'
linktitle: Náhled dokumentu bez anotací
og_description: Naučte se, jak skrýt anotace při generování čistých document preview
  v C#. Tento průvodce zahrnuje nastavení, kód, tipy na výkon a řešení problémů.
og_image_alt: Guide showing how to generate document preview without annotations using
  GroupDocs.Annotation for .NET
og_title: Jak skrýt anotace při generování document preview v C#
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
title: Jak skrýt anotace při generování document preview v C#
type: docs
url: /cs/net/document-preview/create-document-preview-without-annotations-groupdocs-dotnet/
weight: 1
---

# Jak skrýt anotace při generování náhledu dokumentu v C#

Pokud potřebujete sdílet náhled dokumentu, ale chcete **skrýt anotace**, jste na správném místě. Tento tutoriál vám ukáže, jak v C# pomocí GroupDocs.Annotation pro .NET generovat čisté náhledy bez anotací, a to od instalace až po optimalizaci výkonu.

## Rychlé odpovědi
- **Jaká primární třída vytváří náhled?** Třída `Annotator`.
- **Která volba zakazuje anotace?** Nastavte `RenderAnnotations = false` v `PreviewOptions`.
- **Minimální verze .NET?** Doporučuje se .NET 6; .NET Core 3.1 také funguje.
- **Mohu náhledovat PDF a Word soubory?** Ano – podporováno je více než 50 formátů.
- **Potřebuji licenci pro testování?** Dočasná licence je k dispozici pro bezplatné zkušební verze.

## Co je skrývání anotací?
*Jak skrýt anotace* je proces generování obrázků náhledu dokumentu při potlačení jakýchkoli komentářů, zvýraznění nebo značek, které jsou v původním souboru. Tato technika zajišťuje, že vizuální výstup obsahuje pouze původní obsah, což je vhodné pro veřejnou distribuci, prezentace klientům nebo jakýkoli scénář, kde musí interní poznámky zůstat skryté.

## Proč potřebujete čisté náhledy dokumentů (a jak je získat)

Když sdílíte náhled s klienty, partnery nebo veřejností, interní komentáře mohou vypadat neprofesionálně nebo dokonce odhalit důvěrnou strategii. Čisté náhledy udržují pozornost na obsahu a chrání váš pracovní postup. GroupDocs.Annotation vám umožňuje přepínat vykreslování anotací, takže můžete z jednoho zdrojového souboru vytvořit jak anotovanou, tak čistou verzi.

## Co budete potřebovat před zahájením

### Jaké jsou předpoklady?
Abyste mohli začít, potřebujete na svém vývojovém počítači nainstalovat následující komponenty. Mít tyto položky připravené zajišťuje, že kód poběží bez runtime chyb a že můžete lokálně otestovat celý pipeline náhledu.

- GroupDocs.Annotation pro .NET 25.4.0 nebo novější (nejnovější verze přidává paměťově optimalizovanou generaci náhledů).
- Visual Studio 2022 nebo jakékoli IDE kompatibilní s .NET.
- Platná licence GroupDocs (dočasné licence jsou zdarma pro hodnocení).

## Rychlé nastavení: získání GroupDocs.Annotation do vašeho projektu

### Možnost 1: NuGet Package Manager Console
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```

### Možnost 2: .NET CLI (moje osobní preference)
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

**Tip:** Udržujte verzi balíčku konzistentní u všech členů týmu, aby se předešlo jemným rozdílům ve vykreslování.

Ověřte instalaci krátkou kontrolou:
```csharp
using System.IO;
using GroupDocs.Annotation;

// This should compile without errors
using (Annotator annotator = new Annotator("path/to/document"))
{
    // You're good to go!
}
```

## Jak můžete generovat náhled bez anotací?

Načtěte dokument pomocí `Annotator`, nakonfigurujte `PreviewOptions` a zavolejte `GeneratePreview`. Nastavení `RenderAnnotations = false` říká enginu, aby vynechal každý komentář, zvýraznění a razítko z výstupních obrázků.

### Krok 1: inicializujte svůj annotátor (základ)
Třída `Annotator` načte dokument a poskytuje metody pro vykreslování a manipulaci s anotacemi.  
```csharp
```csharp
using (Annotator annotator = new Annotator("path/to/your/document"))
{
    // All your preview generation happens within this scope
}
```
```

### Krok 2: nakonfigurujte své možnosti náhledu (tady se děje magie)
Třída `PreviewOptions` definuje parametry vykreslování, jako je formát, rozlišení a zda jsou zahrnuty anotace.  
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

### Krok 3: vygenerujte náhled (odměna)
Metoda `GeneratePreview` zpracuje dokument podle poskytnutých možností a vrátí cesty k souborům vytvořených obrázků.  
```csharp
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
```

## Časté problémy (a jak je vyřešit)

### Problém 1: chyby „Soubor nenalezen“
**Příznaky:** Při vytvoření `Annotator` je vyhozena výjimka.  
**Řešení:** Použijte absolutní cesty nebo ověřte, že vaše relativní cesty jsou správné. Krátká kontrola vypadá takto:
```csharp
string fullPath = Path.GetFullPath("your-document.pdf");
using (Annotator annotator = new Annotator(fullPath))
```

### Problém 2: Špatná kvalita náhledu
**Příznaky:** Výstupní obrázky jsou rozmazané nebo pixelované.  
**Řešení:** Zvyšte nastavení DPI v `PreviewOptions` pro zlepšení ostrosti:
```csharp
previewOptions.Width = 1920;  // Higher resolution
previewOptions.Height = 1080;
```

### Problém 3: Problémy s pamětí u velkých dokumentů
**Příznaky:** `OutOfMemoryException` nebo zřetelně pomalé zpracování.  
**Řešení:** Zpracovávejte stránky po dávkách místo načítání celého souboru najednou:
```csharp
// Process 5 pages at a time instead of all at once
previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5};
```

## Reálné příklady použití (kde to skutečně má význam)

### Sdílení právních dokumentů
Právnické firmy mohou distribuovat náhledy smluv, které skrývají interní poznámky k jednání, a tak udržovat profesionální komunikaci s klienty.

### Akademické publikování
Výzkumníci mohou sdílet čisté návrhy rukopisů po kole recenzí, odstraněním komentářů recenzentů před podáním do časopisu.

### Obchodní reporting
Zainteresované strany dostávají vyladěné zprávy bez poznámek jako „ověřte toto číslo“ nebo „aktualizovat před zasedáním představenstva“, které by jinak mohly podkopat důvěru.

### Archivace dokumentů
Týmy pro soulad ukládají kopie bez anotací, aby splnily regulační standardy, a zároveň zachovávají původní anotovanou verzi pro interní referenci.

## Nejlepší postupy pro výkon

### Jak byste měli spravovat paměť u velkých souborů?
Zpracovávejte stránky v malých dávkách a rychle uvolňujte `Annotator`. Tento přístup snižuje špičkové využití paměti až o 60 % u dokumentů větších než 200 stránek.
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

### Jak můžete urychlit dávkové zpracování?
Rozdělte 100‑stránkový dokument na skupiny po 10 stránkách, generujte každou skupinu sekvenčně a výsledek uložte do dočasné složky. Tato technika zkrátí celkový čas zpracování přibližně o 30 % na typickém serverovém hardware.
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

### Jak vybrat optimální výstupní formát?
- **PNG:** Nejlepší vizuální věrnost; ideální pro detailní schémata.  
- **JPEG:** Menší velikost souboru; vhodný pro dokumenty s velkým množstvím textu, kde jsou drobné artefakty komprese přijatelné.  
- **WebP:** Moderní formát s vynikající kompresí; před nasazením zkontrolujte podporu v prohlížečích.

## Pokročilé konfigurační možnosti

### Jak můžete přizpůsobit pojmenování souborů?
Lambda `PreviewOptions` vám umožní vložit čísla stránek, časová razítka nebo vlastní identifikátory do názvu každého souboru.
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    string timestamp = DateTime.Now.ToString("yyyyMMdd_HHmmss");
    var pagePath = $"previews\\{timestamp}_page_{pageNumber:D3}.png";
    return File.Create(pagePath);
});
```

### Jak ovládat kvalitu obrázku?
Upravte vlastnosti `Width`, `Height` a `Resolution` v `PreviewOptions`. Větší rozměry poskytují vyšší kvalitu za cenu větší velikosti souboru.
```csharp
previewOptions.Width = 2400;   // Higher resolution
previewOptions.Height = 3200;  // Maintains aspect ratio
previewOptions.PreviewFormat = PreviewFormats.PNG; // Best quality
```

### Jak můžete zpracovat jen konkrétní stránky?
Nastavte kolekci `PageNumbers` na přesné stránky, které potřebujete, což snižuje I/O a urychluje generování u dokumentů s stovkami stránek.
```csharp
// Only process odd pages (useful for double-sided documents)
var oddPages = Enumerable.Range(1, totalPages)
                        .Where(p => p % 2 == 1)
                        .ToArray();
previewOptions.PageNumbers = oddPages;
```

## Průvodce řešením problémů

### Proč selhává generování náhledu tiše?
Běžné příčiny zahrnují:
1. Chybějící výstupní adresář nebo nedostatečná oprávnění k zápisu.  
2. Zdrojové dokumenty chráněné heslem.  
3. Nepodporovaný formát souboru.  
4. Nedostatečná systémová paměť.

### Proč se anotace stále zobrazují?
Ujistěte se, že `RenderAnnotations = false` je nastaveno na instanci `PreviewOptions` před voláním `GeneratePreview`. Vlastnost `RenderAnnotations` řídí, zda jsou během vykreslování náhledu vykresleny vrstvy anotací.
```csharp
previewOptions.RenderAnnotations = false;  // Must be explicitly false
previewOptions.RenderComments = false;     // Also disable comments if needed
```

### Proč je výkon pomalý?
- Snižte rozlišení během testování.  
- Zpracovávejte méně stránek na dávku.  
- Ověřte, že používáte nejnovější verzi GroupDocs.Annotation (25.4.0 nebo novější), která obsahuje vylepšení výkonu.

## Kdy NEpoužívat tento přístup

- **Náhled v reálném čase:** Pro okamžité, on‑the‑fly náhledy může být rychlejší vykreslování na straně klienta.  
- **Interaktivní dokumenty:** Formuláře nebo vložené skripty mohou ztratit funkčnost při vykreslení jako statické obrázky.  
- **Škálovatelná grafika:** Pokud potřebujete výstupy založené na vektorech (např. SVG), zvažte generování PDF stránek místo rastrových obrázků.

## Závěr

Generování čistých náhledů dokumentů bez anotací je s GroupDocs.Annotation pro .NET jednoduché. Pamatujte na:
1. Správně uvolňujte `Annotator`.  
2. Nastavte `RenderAnnotations = false` v `PreviewOptions`.  
3. Zpracovávejte velké soubory po dávkách, aby byl nízký odběr paměti.  
4. Testujte s reálnými dokumenty, abyste doladili DPI a volby formátu.

Začněte s jednoduchým testovacím souborem, experimentujte s výše uvedenými možnostmi a budete mít profesionální náhledy bez anotací připravené pro jakékoliv publikum.

## Často kladené otázky

**Q: Mohu náhledovat dokumenty jiné než DOCX soubory?**  
A: Rozhodně! GroupDocs.Annotation podporuje více než 50 formátů — včetně PDF, PPTX, XLSX a běžných typů obrázků. Viz [documentation](https://docs.groupdocs.com/annotation/net/) pro úplný seznam.

**Q: Jak zacházet s dokumenty chráněnými heslem?**  
A: Inicializujte `Annotator` s objektem `LoadOptions`, který obsahuje heslo. Třída `LoadOptions` vám umožní zadat heslo dokumentu a další parametry načítání.
```csharp
LoadOptions loadOptions = new LoadOptions { Password = "your-password" };
using (Annotator annotator = new Annotator("protected-doc.pdf", loadOptions))
```

**Q: Mohu generovat náhledy ve webové aplikaci?**  
A: Ano. Stejný kód funguje v ASP.NET, ale ukládejte vygenerované obrázky do dočasné složky a po odeslání odpovědi je vyčistěte, aby nedošlo k zaplnění disku.

**Q: Jaký je nejlepší výstupní formát pro webové zobrazení?**  
A: PNG nabízí nejvyšší kvalitu, JPEG se načítá rychleji a WebP poskytuje nejlepší kompresi, pokud vaše cílové prohlížeče podporují. PNG je nejbezpečnější výchozí volba.

**Q: Jak zacházet s velmi velkými dokumenty efektivně?**  
A: Zpracovávejte stránky v dávkách po 5‑10, monitorujte využití paměti a případně zobrazte ukazatel průběhu pro zlepšení uživatelského zážitku.

**Q: Mohu přizpůsobit kvalitu výstupního obrázku?**  
A: Ano — upravením `Width`, `Height` a `Resolution` v `PreviewOptions`. Větší hodnoty zvyšují kvalitu, ale také velikost souboru.

**Q: Co když potřebuji jak anotovanou, tak čistou verzi?**  
A: Spusťte náhled dvakrát — jednou s `RenderAnnotations = true` a podruhé s `false`. Každou sadu uložte do samostatných adresářů pro snadné načtení.

## Zdroje

- [GroupDocs.Annotation .NET Documentation](https://docs.groupdocs.com/annotation/net/)  
- [GroupDocs Annotation API Reference](https://reference.groupdocs.com/annotation/net/)  
- [GroupDocs Releases for .NET](https://releases.groupdocs.com/annotation/net/)  
- [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- [GroupDocs Free Trials](https://releases.groupdocs.com/annotation/net/)  
- [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- [GroupDocs Forum](https://forum.groupdocs.com/c/annotation/)  

**Poslední aktualizace:** 2026-10-05  
**Testováno s:** GroupDocs.Annotation 25.4.0 for .NET  
**Autor:** GroupDocs

## Související tutoriály

- [Jak odstranit PDF anotace C# – Průvodce GroupDocs.Annotation](/annotation/net/annotation-management/remove-annotations-groupdocs-annotation-dotnet/)
- [Generování náhledů dokumentů bez komentářů v .NET](/annotation/net/document-preview/groupdocs-annotation-net-document-preview-no-comments/)
- [Načtení vlastních fontů .NET – Průvodce integrací GroupDocs.Annotation](/annotation/net/advanced-usage/loading-custom-fonts/)