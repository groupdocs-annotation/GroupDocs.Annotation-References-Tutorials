---
categories:
- Java Development
date: '2026-05-16'
description: Naučte se, jak v Javě vytvářet odpovědi na anotace pomocí GroupDocs.Annotation.
  Ovládněte PDF anotace v Javě s praktickými příklady, tipy na výkon a osvědčenými
  postupy.
keywords:
- create annotation reply java
- GroupDocs.Annotation Java
- PDF annotation Java tutorial
lastmod: '2026-05-16'
linktitle: Kurz Java PDF anotací
schemas:
- author: GroupDocs
  dateModified: '2026-05-16'
  description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  headline: 'Java PDF Annotation Library: create annotation reply java'
  type: TechArticle
- description: Learn how to create annotation replies java using GroupDocs.Annotation.
    Master PDF annotation in Java with practical examples, performance tips, and best
    practices.
  name: 'Java PDF Annotation Library: create annotation reply java'
  steps:
  - name: Import All Required Classes
    text: '- `Annotator` is the entry point for all document‑level operations. - `Point`
      represents a coordinate on a page (X and Y measured from the top‑left). - `SquigglyAnnotation`
      defines the wavy underline used to highlight errors. - `Reply` stores threaded
      comments attached to an annotation. - `SaveOptio'
  - name: Create and Configure Your Squiggly Annotation
    text: 'SquigglyAnnotation is a class that creates a wavy underline used to highlight
      errors in a PDF. - **Coordinate system**: Points start at the top‑left corner.
      The two points above draw a horizontal wavy line from (100, 200) to (300, 200).
      - **Opacity** 0.7 means the annotation is 70 % opaque, letting '
  - name: Add Interactive Replies (Optional but Powerful)
    text: Reply is a class representing a comment thread attached to an annotation.
      - Replies create a **threaded discussion** directly on the annotation, mirroring
      the experience of modern PDF reviewers. - Each reply stores author information
      and a timestamp, which you can later filter or display in a UI.
  - name: Apply Annotation and Save Document
    text: '- The **try‑with‑resources** construct automatically closes the `Annotator`,
      releasing file handles and native buffers. - `save` writes the modified PDF
      to `output.pdf`. > **Memory note:** The `Annotator` loads only the pages you
      touch. For multi‑hundred‑page PDFs, this approach keeps heap usage und'
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation focuses exclusively on annotation workflows, offering
      over 30 annotation types, threaded replies, and native support for 50 + file
      formats while keeping the memory footprint under 200 MB for 500‑page PDFs.
    question: What makes GroupDocs.Annotation better than other Java PDF libraries?
  - answer: Absolutely. Create a `@RestController` that injects the `Annotator` service,
      processes multipart uploads, and streams the annotated PDF back to the client.
      Remember to configure a thread‑pool for concurrent requests.
    question: Can I use this library with Spring Boot applications?
  - answer: Query each page’s dimensions via `annotator.getPageInfo(pageIndex)` and
      calculate relative coordinates (e.g., percentages) instead of hard‑coding point
      values. This ensures annotations appear correctly on A4, Letter, and custom‑size
      pages.
    question: How do I handle documents with different page sizes?
  - answer: Yes. Call `annotator.get()` to retrieve a collection of all annotations,
      then iterate to read properties such as author, comment, and geometry. This
      is useful for migration or analytics scenarios.
    question: Is there a way to extract existing annotations from PDFs?
  - answer: Implement authentication at the application layer, store the user ID with
      each `Reply`, and enforce business rules (e.g., only the author or an admin
      can edit or delete a reply). The API itself does not enforce permissions, giving
      you full flexibility.
    question: What's the best approach for handling annotation permissions in multi‑user
      systems?
  type: FAQPage
tags:
- pdf-annotations
- java-libraries
- document-processing
- groupdocs
title: 'Java PDF Annotation Library: vytvořit odpověď na anotaci v Javě'
type: docs
url: /cs/java/graphical-annotations/groupdocs-java-squiggly-annotations-pdf/
weight: 1
---

# Java PDF knihovna pro anotace: vytvořit odpověď na anotaci java

Pokud potřebujete **create annotation reply java** pro PDF—ať už budujete portál pro revizi smluv, e‑learning systém nebo hromadnou zpracovatelskou pipeline—tento průvodce vám přesně ukáže, jak to provést pomocí GroupDocs.Annotation pro Java. Provedeme vás nastavením, vytvořením vlnité anotace, vlákny odpovědí a laděním výkonu, abyste mohli nasadit spolehlivé řešení během dní, ne týdnů.

## Rychlé odpovědi
- **Jaký je hlavní účel GroupDocs.Annotation?** Umožňuje programové vytváření, úpravu a extrakci PDF anotací v Javě.  
- **Jak přidám vlnitou anotaci?** Vytvořte instanci `SquigglyAnnotation`, nastavte její geometrii a styl a poté zavolejte `annotator.add(...)`.  
- **Mohu k anotaci připojit odpovědi?** Ano—vytvořte objekty `Reply`, nastavte autora a text a přiřaďte je k nadřazené anotaci.  
- **Potřebuji licenci pro produkci?** Rozhodně; bez platné licence bude výstup obsahovat vodoznaky.  
- **Je vhodná pro dávkové zpracování?** Ano—použijte try‑with‑resources k otevření každého dokumentu, anotaci a jeho uzavření, čímž udržíte nízkou spotřebu paměti.

## Proč vývojáři Java potřebují PDF knihovny pro anotace

Manuální označování PDF je časově náročné a náchylné k chybám, zejména když musíte zkontrolovat stovky smluv nebo zkušebních prací. Java PDF knihovna pro anotace automatizuje tuto práci, umožňuje vložit zvýraznění, vlnité podtržení a vlákna komentářů přímo do souboru. Výsledkem je prohledávatelný, přenosný dokument, který zachovává veškeré značky bez potřeby samostatného prohlížeče.

**Co se v tomto průvodci naučíte**
- Instalace a licencování GroupDocs.Annotation v Maven projektu
- Vytváření vlnitých anotací, které vypadají jako nativní podtržení ve Wordu
- Přidávání vláken odpovědí k jakékoli anotaci pro spolupracující revizi
- Optimalizace využití paměti a CPU při zpracování velkých PDF
- Nasazení řešení v Spring Boot, mikro‑službách nebo desktopových aplikacích  

Ať už budujete systém pro revizi právních dokumentů, nástroj pro hodnocení ve vzdělávání nebo automatizovanou pipeline pro kontrolu kvality, níže uvedené techniky vám poskytnou produkčně připravený základ.

## Co je create annotation reply java?

`create annotation reply java` je programový proces připojení vlákna komentářů (Reply) k existující PDF anotaci pomocí Javy. Odpovědi umožňují více recenzentům diskutovat konkrétní značku bez opuštění dokumentu, což umožňuje plynulou spolupráci přímo v dokumentu. Tato funkce promění statický PDF na interaktivní platformu pro diskusi, zachovávající kontext a auditní stopy přímo v souboru.

## Předpoklady: Připravení vašeho prostředí

- **JDK** 8 nebo vyšší (JDK 11 + se doporučuje pro lepší výkon garbage‑collection)
- **Maven** nebo **Gradle** pro správu závislostí (příklady používají Maven)
- IDE s podporou Maven (IntelliJ IDEA, Eclipse nebo VS Code)
- Alespoň **2 GB** volné RAM pro IDE a testovací běhy
- Ukázkové PDF soubory pro experimentování (můžete vytvořit jednoduché PDF pomocí libovolného PDF editoru)

GroupDocs.Annotation běží kompletně v procesu; nejsou vyžadovány externí PDF prohlížeče ani nativní knihovny.

## Nastavení GroupDocs.Annotation pro Java

Integrace knihovny je několik kroků, ale několik skrytých úskalí může způsobit chyby za běhu, pokud je přehlédnete.

### Konfigurace Maven závislosti

Přidejte repozitář a závislost do vašeho `pom.xml`. Umístěte element `<repositories>` **před** `<dependencies>`, aby Maven mohl vyřešit artefakt.

```xml
<repositories>
    <repository>
        <id>groupdocs-repo</id>
        <url>https://repo.groupdocs.com/repo</url>
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

> **Tip:** Zkontrolujte stránku vydání GroupDocs pro nejnovější verzi. Nová vydání často zahrnují podporu nových PDF standardů a vylepšení výkonu.

### Nastavení licence (nepřeskakujte!)

GroupDocs.Annotation vyžaduje licenční soubor pro produkční použití. Bez něj bude každý vygenerovaný PDF obsahovat vodoznak.

1. **Free Trial** – Plná sada funkcí na 30 dnů, ideální pro hodnocení.  
2. **Temporary License** – Vhodná pro vývoj a interní testování.  
3. **Full License** – Vyžadována pro jakékoli komerční nasazení.  

Umístěte soubor `GroupDocs.Annotation.lic` do složky resources a načtěte jej při spuštění:

```java
License license = new License();
license.setLicense("GroupDocs.Annotation.lic");
```

> **Častá chyba:** Zapomenutí kroku s licencí vede k PDF s vodoznakem a API voláním, která tiše selhávají. Vždy ověřte licenci brzy ve spouštěcí rutině.

## Kompletní průvodce implementací: Přidání vlnitých anotací

Níže je krok‑za‑krokem průvodce, který ukazuje, jak **create annotation reply java** při vytváření vlnité anotace. Každý krok obsahuje stručné vysvětlení, takže pochopíte „proč“ za každým řádkem.

### Krok 1: Import všech požadovaných tříd

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.annotation.SquigglyAnnotation;
import com.groupdocs.annotation.models.annotation.Reply;
import com.groupdocs.annotation.options.SaveOptions;
```

- `Annotator` je vstupní bod pro všechny operace na úrovni dokumentu.  
- `Point` reprezentuje souřadnici na stránce (X a Y měřeno od levého horního rohu).  
- `SquigglyAnnotation` definuje vlnité podtržení používané k zvýraznění chyb.  
- `Reply` ukládá vlákna komentářů připojených k anotaci.  
- `SaveOptions` umožňuje řídit výstupní formát a kompresi.  

### Krok 2: Vytvoření a konfigurace vaší vlnité anotace

```java
SquigglyAnnotation squiggly = new SquigglyAnnotation();
squiggly.setPageNumber(1);
squiggly.setColor(0xFFFF0000); // ARGB red
squiggly.setOpacity(0.7);
squiggly.setPoints(Arrays.asList(
    new Point(100, 200),
    new Point(300, 200)
));
```

SquigglyAnnotation je třída, která vytváří vlnité podtržení používané k zvýraznění chyb v PDF.

- **Soustava souřadnic**: Body začínají v levém horním rohu. Dva body výše kreslí horizontální vlnitou čáru od (100, 200) do (300, 200).  
- **Opacity** 0.7 znamená, že anotace je 70 % neprůhledná, což umožňuje čitelnost podkladového textu.

### Krok 3: Přidání interaktivních odpovědí (volitelné, ale výkonné)

```java
Reply reply1 = new Reply();
reply1.setComment("Please double‑check this clause.");
reply1.setAuthor("Alice");
reply1.setCreatedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("I think the wording is correct.");
reply2.setAuthor("Bob");
reply2.setCreatedOn(new Date());

squiggly.setReplies(Arrays.asList(reply1, reply2));
```

Reply je třída představující vlákno komentářů připojených k anotaci.

- Odpovědi vytvářejí **vláknovou diskusi** přímo na anotaci, což odráží zkušenost moderních PDF recenzentů.  
- Každá odpověď ukládá informace o autorovi a časové razítko, které můžete později filtrovat nebo zobrazit v UI.

### Krok 4: Aplikace anotace a uložení dokumentu

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    annotator.add(squiggly);
    SaveOptions options = new SaveOptions();
    options.setOutputPath("output.pdf");
    annotator.save(options);
}
```

- Konstrukce **try‑with‑resources** automaticky uzavře `Annotator`, uvolní souborové handly a nativní buffery.  
- `save` zapíše upravený PDF do `output.pdf`.  

> **Poznámka o paměti:** `Annotator` načítá pouze stránky, které upravujete. Pro PDF s několika stovkami stránek tento přístup udržuje využití haldy pod 150 MB na typickém serveru.

## Pokročilé konfigurační možnosti

### Přizpůsobení vzhledu anotace

```java
squiggly.setBorderWidth(2);
squiggly.setColor(0xFF00FF00); // ARGB green
squiggly.setOpacity(0.5);
```

- **Border width** řídí tloušťku čáry (v bodech).  
- **ARGB** formát zahrnuje alfa kanál pro průhlednost.

### Přesné umístění anotací

Získání správných souřadnic může být obtížné u PDF s různými velikostmi stránek. Postupujte podle tohoto systematického přístupu:

1. Otevřete PDF v prohlížeči (např. Adobe Acrobat) a zaznamenejte hodnoty pravítka pro cílovou oblast.  
2. Převěďte hodnoty pravítka na body (1 point = 1/72 inch).  
3. Použijte `annotator.getPageInfo(pageIndex)` k získání šířky a výšky stránky, poté vypočítejte relativní pozice.

## Časté problémy a řešení

### Problém: Anotace se nezobrazují

**Nejpravděpodobnější příčiny**
- Body leží mimo hranice stránky  
- Licence není načtena (vodoznak skrývá anotaci)  
- Špatné číslo stránky (stránky jsou v API číslovány od nuly)  

**Kontrolní seznam řešení**
```text
- Verify page dimensions with annotator.getPageInfo(pageIndex)
- Ensure all Point X/Y values are within [0, pageWidth] and [0, pageHeight]
- Confirm license file path and that license.setLicense() returns true
- Check that squiggly.setPageNumber(pageIndex) uses zero‑based indexing
```

### Problém: Špatný výkon u velkých souborů

Načtení 500‑stránkového PDF do paměti může zastavit vaši službu. Zmírněte to tím, že:

- **Zpracování jedné stránky najednou** – otevřete dokument, anotujte jednu stránku, uložte a poté přejděte na další.  
- **Streaming** – použijte streaming API `Annotator`, abyste se vyhnuli úplnému načítání dokumentu do paměti.  
- **Caching** – uložte často přistupované PDF do rychlé cache (např. Redis) a anotujte kopii z cache.

### Problém: Hodnoty barev nefungují

GroupDocs očekává **ARGB** (Alpha, Red, Green, Blue) místo prostého RGB. Hodnota ARGB `0xFFFF0000` znamená plně neprůhlednou červenou. Pokud zadáte `0xFF0000`, knihovna ji interpretuje nesprávně, což vede k černé anotaci.

```java
int argbRed = 0xFFFF0000; // Alpha=255, Red=255, Green=0, Blue=0
squiggly.setColor(argbRed);
```

## Nejlepší postupy pro výkon

### Správa paměti

Při anotaci desítek PDF v dávkovém úkolu zabalte každý soubor do vlastního bloku try‑with‑resources:

```java
for (String filePath : pdfList) {
    try (Annotator annotator = new Annotator(filePath)) {
        // add annotations
        annotator.save(new SaveOptions().setOutputPath(filePath.replace(".pdf", "_annotated.pdf")));
    }
}
```

- Tento vzor zaručuje uvolnění nativních bufferů po každé iteraci, což zabraňuje **OutOfMemoryError** u dlouho běžících procesů.

### Optimalizace dávkového zpracování

Pro prostředí s vysokou propustností zvažte paralelní streamy v kombinaci s omezeným thread pool:

```java
ExecutorService executor = Executors.newFixedThreadPool(Runtime.getRuntime().availableProcessors());
pdfList.parallelStream().forEach(path -> executor.submit(() -> annotateDocument(path)));
executor.shutdown();
executor.awaitTermination(1, TimeUnit.HOURS);
```

- **Omezený pool** zabraňuje výbuchu vláken, zatímco paralelní streamy udržují CPU jádra vytížená.

### Úvahy o velikosti souboru

Velké PDF (> 100 MB) mohou snižovat výkon. Použijte tyto strategie:

- **Předkomprimujte** zdrojové PDF pomocí nástroje jako Ghostscript před anotací.  
- **Anotujte pouze potřebné stránky** – přeskočte stránky, které nevyžadují značky.  
- **Rozdělte** dokument na logické sekce (např. po kapitolách) a zpracovávejte každý úsek samostatně.

## Reálné aplikace

### Systémy pro revizi dokumentů

Právnické firmy často potřebují označit problematické klauzule. Vlnité anotace kombinované s vlákny odpovědí umožňují více právníkům diskutovat jeden odstavec bez opuštění PDF:

- **Právník A** přidá červenou vlnitou čáru pod klauzuli a napíše „Nejasná formulace“.  
- **Právník B** odpoví „Přidejte definici ‘material breach’“.  
- Celá diskuse zůstane vložená, prohledávatelná a auditovatelná.

### Integrace s existujícími systémy

GroupDocs.Annotation funguje hladce s populárními Java frameworky:

- **Spring Boot** – vystavte REST endpoint `/api/annotate`, který přijímá multipart upload PDF, přidá anotace a streamuje výsledek zpět.  
- **JSF** – svázat akce anotací s UI komponentami pro okamžité značkování ve webovém zobrazení.  
- **Microservices** – malá velikost knihovny (< 15 MB) vám umožní kontejnerizovat ji pomocí Dockeru a horizontálně škálovat.

### Automatizace pracovních toků

Kombinujte anotaci s dalšími produkty GroupDocs (např. GroupDocs.Signature) k vytvoření end‑to‑end pipeline:

```text
1. Upload contract → 2. Auto‑apply squiggly for missing signatures → 3. Add reviewer replies → 4. Route to signing service.
```

## Kdy použít vlnité anotace vs. alternativy

| Use‑case | Recommended annotation |
|----------|------------------------|
| Označování pravopisných nebo gramatických chyb | **Squiggly** – vizuální nápověda podobná textovým editorům |
| Zvýraznění důležitých částí bez naznačení chyby | **Highlight** – průhledný překryv |
| Poskytování podrobné zpětné vazby | **Text** nebo **Comment** – volná poznámková schránka |
| Schvalování nebo odmítnutí dokumentu | **Stamp** – odznak „Approved“ nebo „Rejected“ |

## Závěr

Nyní máte kompletní, produkčně připravený návod pro **create annotation reply java** pomocí GroupDocs.Annotation. Ovládnutím API, správou licencí a aplikací výše uvedených tipů pro výkon můžete:

- Automatizovat označování chyb ve tisících PDF  
- Umožnit spolupracující, vlákna diskusí přímo v souboru  
- Udržet nízkou spotřebu paměti i při zpracování obrovských dokumentů  

**Další kroky**

1. Experimentujte s dalšími typy anotací (zvýraznění, razítka, text).  
2. Vytvořte REST službu, která přijímá PDF, anotuje je a vrací výsledek.  
3. Prozkoumejte API pro extrakci (`annotator.get()`), abyste získali existující komentáře pro analytiku.  

Síla programové PDF anotace spočívá v její schopnosti nahradit únavné ruční značkování opakovatelným, auditovatelným kódem. Ať už budujete specializovaný legal‑tech produkt nebo obecný engine pro workflow dokumentů, techniky v tomto průvodci vám poskytnou pevný základ pro další kroky.

## Často kladené otázky

**Q: Co dělá GroupDocs.Annotation lepší než jiné Java PDF knihovny?**  
A: GroupDocs.Annotation se zaměřuje výhradně na workflow anotací, nabízí více než 30 typů anotací, vlákna odpovědí a nativní podporu pro více než 50 formátů souborů, přičemž udržuje paměťovou stopu pod 200 MB pro 500‑stránkové PDF.

**Q: Mohu tuto knihovnu použít s aplikacemi Spring Boot?**  
A: Rozhodně. Vytvořte `@RestController`, který injektuje službu `Annotator`, zpracovává multipart uploady a streamuje anotovaný PDF zpět klientovi. Nezapomeňte nakonfigurovat thread‑pool pro souběžné požadavky.

**Q: Jak zacházet s dokumenty s různými velikostmi stránek?**  
A: Dotazujte se na rozměry každé stránky pomocí `annotator.getPageInfo(pageIndex)` a vypočítejte relativní souřadnice (např. procenta) místo pevného kódování hodnot v bodech. To zajistí, že anotace se zobrazí správně na stránkách A4, Letter a vlastních velikostech.

**Q: Existuje způsob, jak extrahovat existující anotace z PDF?**  
A: Ano. Zavolejte `annotator.get()`, abyste získali kolekci všech anotací, a poté iterujte pro čtení vlastností jako autor, komentář a geometrie. To je užitečné pro migraci nebo analytické scénáře.

**Q: Jaký je nejlepší přístup pro správu oprávnění anotací v multi‑uživatelských systémech?**  
A: Implementujte autentizaci na úrovni aplikace, uložte ID uživatele s každým `Reply` a vynucujte obchodní pravidla (např. pouze autor nebo admin může upravit či smazat odpověď). API samo nevyžaduje oprávnění, což vám dává plnou flexibilitu.

**Q: Jak optimalizovat využití paměti při zpracování stovek PDF?**  
A: Používejte try‑with‑resources pro každý dokument, zpracovávejte stránky jednotlivě a zvažte omezený thread pool pro omezení souběžné spotřeby paměti. Monitorování haldy JVM pomocí nástrojů jako VisualVM vám pomůže doladit nastavení `-Xmx`.

**Poslední aktualizace:** 2026-05-16  
**Testováno s:** GroupDocs.Annotation 25.2 for Java  
**Autor:** GroupDocs  

**Další zdroje**

- [Dokumentace GroupDocs.Annotation pro Java](https://docs.groupdocs.com/annotation/java/)
- [Kompletní referenční API](https://reference.groupdocs.com/annotation/java/)

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}

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

```java
import com.groupdocs.annotation.Annotator;

// Initialize your annotator - this is your entry point to all annotation features
try (Annotator annotator = new Annotator("path/to/your/document.pdf")) {
    // All your annotation magic happens here
    System.out.println("Annotator initialized successfully!");
}
```

```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Point;
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.annotationmodels.SquigglyAnnotation;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;
```

```java
// Create a new SquigglyAnnotation instance
SquigglyAnnotation squigglyAnnotation = new SquigglyAnnotation();

// Set the creation date of the annotation
squigglyAnnotation.setCreatedOn(new Date());

// Define font and background colors using RGB values
squigglyAnnotation.setFontColor(65535); // Yellow color in ARGB format
squigglyAnnotation.setBackgroundColor(16761035); // Light blue color in ARGB format

// Set a message to display with the annotation
squigglyAnnotation.setMessage("This is squiggly annotation");

// Define opacity (range 0.0 - 1.0)
squigglyAnnotation.setOpacity(0.7);

// Specify the page number for the annotation (zero-based index)
squigglyAnnotation.setPageNumber(0);

// Set squiggly line color specific to Word and PDF documents
squigglyAnnotation.setSquigglyColor(1422623); // Color code for squiggly lines

// Define points marking the start and end of the annotation on the page
List<Point> points = new ArrayList<>();
points.add(new Point(80, 730));
points.add(new Point(240, 730));
points.add(new Point(80, 650));
points.add(new Point(240, 650));
squigglyAnnotation.setPoints(points);
```

```java
// Create replies to the annotation (optional)
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(new Date());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(new Date());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);

// Associate replies with the annotation
squigglyAnnotation.setReplies(replies);
```

```java
try (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Add the prepared squiggly annotation to the document
    annotator.add(squigglyAnnotation);
    
    // Save the annotated document
    annotator.save("YOUR_OUTPUT_DIRECTORY/result_squiggly_annotation.pdf");
}
```

```java
// Custom color configurations
squigglyAnnotation.setFontColor(0xFF0000); // Red text
squigglyAnnotation.setBackgroundColor(0x00FF00); // Green background
squigglyAnnotation.setSquigglyColor(0x0000FF); // Blue squiggly line

// Transparency effects
squigglyAnnotation.setOpacity(0.3); // Very subtle
// or
squigglyAnnotation.setOpacity(0.9); // Almost opaque
```

```java
// Verify your points are within page boundaries
System.out.println("Page dimensions: " + annotator.getPageInfo(0));

// Check if your points make sense
List<Point> points = squigglyAnnotation.getPoints();
for (Point point : points) {
    System.out.println("Point: (" + point.getX() + ", " + point.getY() + ")");
}
```

```java
// Wrong: RGB format
int wrongColor = 0xFF0000; // This might not work as expected

// Right: ARGB format
int rightColor = 0xFFFF0000; // Full opacity red
```

```java
// Good practice: Use try-with-resources
try (Annotator annotator = new Annotator(inputPath)) {
    // Process annotations
    annotator.add(annotation);
    annotator.save(outputPath);
} // Automatic cleanup happens here

// Avoid: Manual resource management
Annotator annotator = new Annotator(inputPath); // Resources might leak
```

```java
public void processBatch(List<String> documentPaths) {
    for (String path : documentPaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Process each document independently
            addAnnotations(annotator);
            annotator.save(getOutputPath(path));
        } catch (Exception e) {
            // Handle individual document failures without stopping the batch
            System.err.println("Failed to process: " + path + " - " + e.getMessage());
        }
    }
}
```

```java
public class DocumentWorkflow {
    public void reviewDocument(String documentPath, ReviewLevel level) {
        try (Annotator annotator = new Annotator(documentPath)) {
            switch (level) {
                case GRAMMAR_CHECK:
                    addGrammarAnnotations(annotator);
                    break;
                case LEGAL_REVIEW:
                    addLegalAnnotations(annotator);
                    break;
                case FINAL_PROOF:
                    addProofreadingAnnotations(annotator);
                    break;
            }
            annotator.save(getReviewedPath(documentPath));
        }
    }
}
```

## Související tutoriály

- [Java PDF knihovna pro anotace – tutoriál](/annotation/java/reply-management/java-annotator-groupdocs-pdf-annotations-replies/)
- [Odstranění odpovědí na anotace v Java – Správa odpovědí podle ID s GroupDocs.Annotation](/annotation/java/annotation-management/java-groupdocs-annotation-remove-replies-by-id/)
- [Úprava PDF anotací v Java – Kompletní tutoriál GroupDocs](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)