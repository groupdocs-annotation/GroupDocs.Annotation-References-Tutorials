---
categories:
- Java PDF Processing
date: '2026-05-21'
description: Zjistěte, jak přidat přeškrtnuté anotace do PDF v Javě pomocí GroupDocs.
  Tento podrobný návod krok za krokem pokrývá nastavení, kód, řešení problémů a tipy
  na výkon.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Průvodce přeškrtnutím textu v PDF pro Javu
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  type: TechArticle
- description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
  steps:
  - name: Setting Up File Paths
    text: Define the locations of your source PDF and the destination file. Incorrect
      paths are a common source of “File Not Found” errors. **Common Mistake Alert:**
      Ensure the output directory exists and is writable; GroupDocs will not auto‑create
      missing folders.
  - name: Initialize the Annotator
    text: Create an `Annotator` instance that loads the PDF into memory. **What happens
      here?** The library parses the PDF structure, builds an internal representation,
      and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this
      step may take a few seconds.
  - name: Adding Comments (Optional but Recommended)
    text: '`Comment` is a class that represents a textual note attached to an annotation,
      allowing collaborators to explain the reason for the strikeout. **Real‑world
      tip:** Use comments to explain why text is being removed—this is especially
      useful in legal or editorial review workflows.'
  - name: Defining Annotation Coordinates
    text: '`Point` objects store X‑Y coordinate pairs that define the exact location
      of an annotation on a PDF page. **Coordinate System Explained:** PDF coordinates
      start at the bottom‑left corner (0,0). The example creates a horizontal line
      from (80,730) to (240,730) on the target page. **Finding the Right C'
  - name: Creating the Strikeout Annotation
    text: '`StrikeoutAnnotation` encapsulates the visual line, its style properties
      such as color and opacity, and any associated metadata for a strikeout mark.
      **Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright
      yellow). Use an online converter if you need brand‑specific shades. '
  - name: Apply the Annotation
    text: '`addAnnotation` is a method of the `Annotator` that registers the prepared
      annotation with the document so it will be rendered and saved.'
  - name: Save and Clean Up
    text: '`dispose()` releases native resources held by the `Annotator` instance,
      preventing memory leaks after processing is complete. **Memory Management Note:**
      Calling `dispose()` frees native resources and prevents memory leaks when processing
      batches of PDFs.'
  type: HowTo
- questions:
  - answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
    question: Can I strikeout text across multiple lines?
  - answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
    question: What happens if I specify coordinates outside the page boundaries?
  - answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
    question: Can I remove strikeout annotations after adding them?
  - answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
    question: Is there a limit to how many annotations I can add to a single PDF?
  - answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
    question: How do I work with password‑protected PDFs?
  type: FAQPage
tags:
- java-pdf
- annotations
- groupdocs
- document-processing
title: Jak přidat přeškrtnuté anotace do PDF v Javě – Kompletní průvodce GroupDocs
type: docs
url: /cs/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# Jak přidat přeškrtnutí anotací do PDF v Javě

Už jste někdy potřebovali programově přeškrtnout text v PDF? Ať už budujete systém pro revizi dokumentů, vytváříte workflow úprav, nebo jen potřebujete označit text ke smazání, **how to add strikeout** anotace v Javě jsou praktickou dovedností, která šetří čas a snižuje ruční úsilí. V tomto komplexním průvodci se dozvíte vše, co potřebujete vědět k implementaci přeškrtnutých anotací pomocí GroupDocs.Annotation pro Java, od nastavení projektu až po optimalizaci výkonu.

## Rychlé odpovědi
- **Jaký je první krok?** Přidejte Maven závislost GroupDocs.Annotation do vašeho `pom.xml`.  
- **Jak vytvořím přeškrtnutí?** Instancujte `Annotator`, definujte `StrikeoutAnnotation` s body, nastavte barvu/průhlednost a poté zavolejte `addAnnotation`.  
- **Mohu přidat komentáře?** Ano, připojte objekt `Comment` k anotaci pro spolupráci.  
- **Co když je anotace špatně umístěna?** Upravit souřadnice; PDF používá souřadnicový systém s počátkem v levém dolním rohu.  
- **Existuje limit velikosti dokumentu?** GroupDocs zpracovává PDF s několika stovkami stránek, aniž by načítal celý soubor do paměti.

## Co znamená “how to add strikeout” v PDF anotaci?
Fráze “how to add strikeout” odkazuje na proces programového nakreslení čáry přes vybraný text v PDF dokumentu pomocí API anotací. V Javě GroupDocs.Annotation poskytuje dedikovanou třídu `StrikeoutAnnotation`, která zajišťuje vykreslování, stylování a uchování přeškrtnutých značek.

## Proč použít GroupDocs pro Java PDF přeškrtnutí?
GroupDocs.Annotation podporuje **více než 50 vstupních a výstupních formátů** — včetně PDF, DOCX, XLSX, PPTX, HTML a běžných typů obrázků — takže nejste vázáni na jediný typ souboru. Poskytuje API na vysoké úrovni, které abstrahuje nízkoúrovňovou strukturu PDF, automaticky zpracovává vkládání fontů, vykreslování stránek a uchování anotací, což vývojářům umožňuje soustředit se na obchodní logiku místo interního fungování PDF.

## Předpoklady a požadavky na nastavení

### Základní požadavky
- **Java Development Kit (JDK):** Verze 8 nebo novější (JDK 11+ doporučeno pro optimální garbage‑collection).  
- **GroupDocs.Annotation pro Java:** Integrované přes Maven (viz níže ukázka Maven).  
- **IDE:** IntelliJ IDEA, Eclipse nebo jakýkoli editor kompatibilní s Javou.

### Nastavení Maven závislostí
Add the following dependency block to your `pom.xml`:

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/annotation/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>25.2</version>
    </dependency>
</dependencies>
```

**Tip:** Vždy ověřte nejnovější verzi na stránce vydání GroupDocs; novější verze přidávají funkce a opravují chyby, které mohou ovlivnit vykreslování anotací.

### Zajištění licence
GroupDocs.Annotation requires a valid license for production use. You have three options:

- **Free Trial:** Stáhněte z [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)  
- **Temporary License:** Požádejte o vývojový klíč na [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Full License:** Zakupte pro produkci na [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

Zkušební verze přidává jemnou vodoznak, proto plánujte testování odpovídajícím způsobem.

## Průvodce krok za krokem

### Porozumění základním komponentám
Následující definice vám poskytnou rychlý mentální model:

- **Annotator:** Hlavní objekt API, který načte PDF a poskytuje metody pro anotace.  
- **StrikeoutAnnotation:** Reprezentuje vizuální čáru přeškrtnutí a její možnosti stylování.  
- **Point:** Pár souřadnic (X, Y), který knihovně říká, kde čára začíná a končí.  
- **Comment:** Volitelný text připojený k anotaci pro spolupráci.

### Krok 1: Nastavení cest k souborům
Definujte umístění vašeho zdrojového PDF a cílového souboru. Nesprávné cesty jsou častým zdrojem chyb „File Not Found“.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Upozornění na častou chybu:** Ujistěte se, že výstupní adresář existuje a je zapisovatelný; GroupDocs automaticky nevytvoří chybějící složky.

### Krok 2: Inicializace Annotatoru
Vytvořte instanci `Annotator`, která načte PDF do paměti.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**Co se zde děje?** Knihovna parsuje strukturu PDF, vytvoří interní reprezentaci a připraví plátno anotací po stránkách. U souborů s několika stovkami stránek může tento krok trvat několik sekund.

### Krok 3: Přidání komentářů (volitelné, ale doporučené)
`Comment` je třída, která představuje textovou poznámku připojenou k anotaci, umožňující spolupracovníkům vysvětlit důvod přeškrtnutí.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Praktický tip:** Používejte komentáře k vysvětlení, proč je text odstraňován — to je zvláště užitečné v právních nebo redakčních revizních pracovních postupech.

### Krok 4: Definování souřadnic anotace
Objekty `Point` ukládají páry souřadnic X‑Y, které definují přesnou polohu anotace na stránce PDF.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Vysvětlení souřadnicového systému:** Souřadnice PDF začínají v levém dolním rohu (0,0). Příklad vytváří vodorovnou čáru od (80,730) do (240,730) na cílové stránce.

**Najít správné souřadnice:** Mnoho vývojářů vytváří pomocnou funkci, která převádí procenta šířky/výšky stránky na absolutní body, což činí kód odolným vůči různým velikostem stránek.

### Krok 5: Vytvoření přeškrtnuté anotace
`StrikeoutAnnotation` zapouzdřuje vizuální čáru, její stylové vlastnosti jako barvu a průhlednost a jakékoli související metadata pro přeškrtnutí.

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535); // Yellow
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0); 
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

**Hodnoty barev:** `fontColor` používá desetinné RGB hodnoty (např. 65535 pro jasně žlutou). Použijte online konvertor, pokud potřebujete odstíny specifické pro značku.

**Doporučení pro průhlednost:** Průhlednost `0.7` (70 %) poskytuje jasný vizuální signál a zároveň zachovává čitelnost podkladového textu.

### Krok 6: Aplikace anotace
`addAnnotation` je metoda `Annotator`, která zaregistruje připravenou anotaci v dokumentu, aby byla vykreslena a uložena.

```java
annotator.add(strikeout);
```

### Krok 7: Uložení a úklid
`dispose()` uvolňuje nativní zdroje držené instancí `Annotator`, čímž zabraňuje únikům paměti po dokončení zpracování.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Poznámka k správě paměti:** Volání `dispose()` uvolňuje nativní zdroje a zabraňuje únikům paměti při zpracování dávky PDF.

## Časté problémy a jak je opravit

### Problém 1: Chyby „File Not Found“
**Příznaky:** Výjimka vyvolaná během konstrukce `Annotator`.  
**Řešení:** Ověřte vstupní i výstupní cesty a potvrďte, že aplikace má oprávnění ke čtení/zápisu.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### Problém 2: Přeškrtnutí se zobrazuje na špatném místě
**Příznaky:** Čára nesedí s zamýšleným textem.  
**Řešení:** Pamatujte, že Y‑souřadnice v PDF rostou směrem nahoru. Použijte vizuální ladící nástroj nebo vytiskněte rozměry stránky pro jemné doladění bodů.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### Problém 3: Anotace není viditelná
**Příznaky:** Po uložení se žádné přeškrtnutí nezobrazí.  
**Možné příčiny a opravy:**  
- **Příliš nízká průhlednost:** Dočasně nastavte průhlednost na `1.0` pro ověření viditelnosti.  
- **Míchání barev:** Použijte vysoce kontrastní barvu, např. červenou (`255`).  
- **Špatný index stránky:** Čísla stránek jsou nulová‑základní; ujistěte se, že cílíte na správnou stránku.

### Problém 4: Problémy s pamětí u velkých souborů
**Příznaky:** `OutOfMemoryError` nebo pomalý výkon.  
**Řešení:**  
- Zpracovávejte dokumenty v menších dávkách.  
- Použijte streaming API, pokud je k dispozici.  
- Vždy zavolejte `dispose()` po každém dokumentu.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## Reálné aplikace a příklady použití

### Právní revize dokumentů
Právnické firmy anotují smlouvy přeškrtnutím, aby označily smazané klauzule, přičemž zachovávají auditní stopu.

### Úprava akademických prací
Profesoři používají přeškrtnutí k navržení odstranění během recenzního procesu, přičemž ponechávají původní text viditelný pro kontext.

### Systémy pro správu obsahu
Publikační platformy automaticky označují sekce porušující politiku přeškrtnutím před ruční moderací.

### Kontrola verzí pro dokumenty
Podniky považují přeškrtnuté anotace za „značky smazání“ v dokumentově‑centrickém workflow pro kontrolu verzí, podobně jako rozdíly v kódu.

## Tipy pro optimalizaci výkonu

### Strategie dávkového zpracování
Při zpracování mnoha PDF opakovaně používejte jednu instanci `Annotator`, pokud je to možné, a zpracovávejte soubory ve paralelních vláknech.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### Nejlepší postupy pro správu paměti
- Zavolejte `dispose()` na každém `Annotator`.  
- Omezte souběžné načítání dokumentů, aby nedošlo k přetížení haldy.  
- Sledujte využití paměti JVM pomocí nástrojů jako VisualVM.

### Cache souřadnic
Pokud používáte stejný rozvrh anotací napříč více soubory, cachujte objekty `Point`, abyste se vyhnuli opakovanému výpočtu.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## Pokročilé možnosti přizpůsobení

### Dynamický výběr barev
Vyberte barvy za běhu na základě obchodních pravidel (např. červená pro kritické smazání, žlutá pro předběžné).

```java
// Choose colors based on annotation type or user
int colorByPriority = getPriorityColor(annotationType);
strikeout.setFontColor(colorByPriority);

private int getPriorityColor(String type) {
    switch(type) {
        case "HIGH": return 255;    // Red
        case "MEDIUM": return 65535; // Yellow  
        case "LOW": return 65280;   // Green
        default: return 0;          // Black
    }
}
```

### Víceřádkové přeškrtnutí
Vytvořte sérii párů `Point` pro nakreslení cik‑cakovité čáry, která překříží několik řádků textu.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## Kontrolní seznam pro řešení problémů
1. **Oprávnění k souborům:** Ověřte přístup ke čtení/zápisu.  
2. **Verze knihovny:** Ujistěte se, že používáte podporovanou verzi GroupDocs.Annotation.  
3. **Stav licence:** Potvrďte, že soubor licence je správně odkazován.  
4. **Kompatibilita PDF:** Zkontrolujte, že PDF není poškozený a je v podporovaných velikostních limitech.  
5. **Validace souřadnic:** Ujistěte se, že všechny body leží uvnitř hranic stránky.  
6. **Prostor haldy:** Zvyšte JVM `-Xmx`, pokud zpracováváte velmi velké soubory.

## Často kladené otázky

**Q: Mohu přeškrtnout text napříč více řádky?**  
A: Ano. Vytvořte několik objektů `Point`, které vykreslí požadovanou cestu; anotace bude následovat zadanou lomenou čáru.

**Q: Co se stane, když zadám souřadnice mimo hranice stránky?**  
A: Anotace bude oříznuta a může se stát neviditelnou. Vždy validujte souřadnice vůči šířce a výšce stránky.

**Q: Mohu po přidání odstranit přeškrtnuté anotace?**  
A: Rozhodně. Použijte metodu `removeAnnotation` s ID anotace nebo filtrujte podle typu, abyste je programově smazali.

**Q: Existuje limit, kolik anotací mohu přidat do jednoho PDF?**  
A: GroupDocs nekladí pevný limit, ale výkon může klesat po tisících anotací. Zvažte stránkování nebo sumarizaci anotací pro velmi velké sady.

**Q: Jak pracovat s PDF chráněnými heslem?**  
A: Předávejte heslo konstruktoru `Annotator`. Knihovna dešifruje dokument v paměti před aplikací jakýchkoli anotací.

**Q: Jak mohu zacházet s PDF s různými velikostmi a orientacemi stránek?**  
A: Získejte rozměry každé stránky pomocí `annotator.getPageInfo(pageNumber)` a vypočítejte souřadnice relativně k těmto rozměrům, aby bylo umístění konzistentní.

## Závěr
Nyní máte kompletní, připravené řešení pro **how to add strikeout** anotace do PDF v Javě pomocí GroupDocs.Annotation. Ovládnutím manipulace s cestami k souborům, výpočtem souřadnic a správou zdrojů můžete tuto funkci vložit do nástrojů pro revizi dokumentů, obsahových pipeline nebo jakékoli Java‑aplikace, která potřebuje přesnou vizuální zpětnou vazbu.

**Další kroky**
1. Klonujte ukázkový projekt a spusťte jej na vzorovém PDF.  
2. Experimentujte s různými barvami, průhlednostmi a texty komentářů.  
3. Integrovat workflow anotací do vašeho stávajícího služby pro zpracování dokumentů.  
4. Prozkoumejte související typy anotací — zvýraznění, poznámky, a tvarové anotace — pro rozšíření vašeho nástroje pro manipulaci s PDF.

Připraven na další? Ponořte se do oficiální dokumentace pro podrobnější informace o API.

## Další zdroje
- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - Obecná dokumentace knihoven GroupDocs  
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - Kompletní reference API  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - Detailní popis metod  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - Udržujte knihovnu aktuální  
- [Purchase License](https://purchase.groupdocs.com/buy) - Licence připravená pro produkci  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - Vyzkoušejte před zakoupením  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - Testování vývoje  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - Komunitní pomoc a oficiální podpora  

---
**Poslední aktualizace:** 2026-05-21  
**Testováno s:** GroupDocs.Annotation 23.12 pro Java  
**Autor:** GroupDocs

## Související tutoriály
- [Add PDF Annotation Java – Complete GroupDocs Guide](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)
- [Java PDF Annotation Tutorial - Complete Guide to Highlighting PDFs](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)
- [How to Add Arrow to PDF in Java – Complete GroupDocs Tutorial](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)