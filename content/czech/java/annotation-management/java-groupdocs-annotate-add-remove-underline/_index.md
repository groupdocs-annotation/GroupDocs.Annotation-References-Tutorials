---
date: '2026-10-16'
description: Naučte se, jak uložit PDF bez annotations v Javě, ovládněte java pdf
  memory management a přidejte podtržené annotations pomocí GroupDocs.Annotation.
  Průvodce krok za krokem.
keywords:
- save pdf without annotations
- java pdf memory management
- java document review system
- groupdocs annotation tutorial
- underline annotation java
lastmod: '2026-10-16'
linktitle: Java Document Annotation s GroupDocs
og_description: Naučte se, jak uložit PDF bez annotations v Javě, ovládněte java pdf
  memory management a přidejte podtržené annotations pomocí GroupDocs.Annotation.
  Průvodce krok za krokem.
og_image_alt: 'Developer guide: Save PDF without annotations in Java using GroupDocs.Annotation'
og_title: Jak uložit PDF bez annotations v Javě pomocí GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  headline: How to save PDF without annotations in Java using GroupDocs
  type: TechArticle
- description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  name: How to save PDF without annotations in Java using GroupDocs
  steps:
  - name: initialize the annotator and load your document
    text: '`Annotator` is the main entry point in GroupDocs.Annotation for loading
      and modifying PDF documents. It abstracts file‑system handling, stream management,
      and native resource allocation. **Pro tip:** Use absolute paths while developing
      to avoid “file not found” errors. In production, consider loadin'
  - name: creating comments and replies (the collaborative part)
    text: '`Comment` objects represent threaded discussion attached to an annotation.
      Each comment can have an author, a timestamp, and optional replies, enabling
      a full conversation around a specific markup. **Real‑world use:** Reviewers
      can discuss a specific clause by adding threaded replies, keeping the co'
  - name: defining annotation coordinates (getting the position right)
    text: '`Point` defines a single coordinate in PDF space (measured in points, where
      72 points = 1 inch). Four points are required for an underline: two for the
      start line and two for the end line. **Coordinate system:** - Points 1 & 2 define
      the top edge of the underline. - Points 3 & 4 define the bottom ed'
  - name: creating and configuring the underline annotation
    text: '`UnderlineAnnotation` is the concrete class that represents an underline
      markup. It inherits from the base `Annotation` class and adds properties specific
      to underlines, such as line thickness and style. **Color & opacity tips:** -
      `FontColor` uses ARGB; `65535` (0x00FFFF) yields bright yellow. - Fo'
  - name: saving your annotated document
    text: '`SaveOptions` lets you control the output format, whether to embed annotations,
      and how to handle metadata. Setting `AnnotationType.NONE` instructs the library
      to strip all annotation objects, which is the key to **save PDF without annotations**.
      **Memory management:** The `dispose()` call releases '
  type: HowTo
- questions:
  - answer: Create several `UnderlineAnnotation` objects with different coordinates
      and add them sequentially using `annotator.add()`.
    question: How do I annotate multiple areas of text in a single operation?
  - answer: Yes. Use the same coordinate system, ensuring the points lie inside the
      image bounds.
    question: Can I annotate images within PDF documents?
  - answer: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), and image formats
      such as JPEG, PNG, TIFF.
    question: What file formats besides PDF does GroupDocs.Annotation support?
  - answer: Process documents one at a time, increase the JVM heap (`-Xmx`), and always
      dispose of `Annotator` instances promptly.
    question: How do I handle very large documents without running out of memory?
  - answer: Yes. Use `annotator.get()` to retrieve all annotations, then filter by
      type, author, or page as needed.
    question: Is it possible to extract existing annotations from a document?
  type: FAQPage
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
- java pdf memory management
title: Jak uložit PDF bez annotations v Javě pomocí GroupDocs
type: docs
url: /cs/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Jak uložit PDF bez anotací v Javě pomocí GroupDocs

Pokud potřebujete **uložit PDF bez anotací** a zároveň mít možnost přidávat kolaborativní podtržené poznámky, jste na správném místě. Mnoho vývojářů Java má potíže s udržováním čisté verze dokumentu pro finální distribuci, zejména když je stejný soubor používán pro iterativní revize. V tomto tutoriálu se naučíte, jak vygenerovat čisté PDF, efektivně spravovat paměť a aplikovat podtržené anotace s komentáři pomocí GroupDocs.Annotation. Na konci pochopíte kompletní workflow—od načtení PDF po vytvoření finální kopie bez vodoznaku—plus tipy na osvědčené postupy pro vytvoření robustního **java document review system**.

## Rychlé odpovědi
- **Jak přidám podtrženou anotaci?** Použijte `UnderlineAnnotation` s `annotator.add()` a poté uložte dokument.  
- **Jak mohu uložit PDF bez anotací?** Načtěte anotovaný soubor, nastavte `AnnotationType.NONE` v `SaveOptions` a uložte novou kopii.  
- **Které knihovny jsou vyžadovány?** GroupDocs.Annotation v25.2 (nebo novější) a jeho Maven repozitář.  
- **Potřebuji licenci pro produkci?** Ano—aplikujte platnou licenci GroupDocs, aby se zabránilo vodoznakům.  
- **Mohu efektivně zpracovávat více dokumentů?** Zabalte každý `Annotator` do bloku try‑with‑resources a po každém souboru jej uvolněte.

## Jak uložit PDF bez anotací v Javě?

Načtěte zdrojové PDF pomocí `Annotator`, nakonfigurujte `SaveOptions` tak, aby vyloučily všechny typy anotací, a zavolejte `save()` pro zápis čisté kopie. Tato operace nemění původní soubor, takže máte jak anotovanou verzi pro recenzenty, tak čistou verzi pro distribuci. Proces používá streamování, což znamená, že celý dokument nikdy není kompletně v paměti—což je klíčové pro velká PDF.

## Co znamená uložit PDF bez anotací?

`save pdf without annotations` označuje export PDF dokumentu při odstranění všech objektů anotací (zvýraznění, komentáře, razítka, podtržení atd.). Výsledný soubor obsahuje pouze původní obsah a rozvržení, což jej činí vhodným pro právní podání, veřejné zveřejnění nebo archivaci.

## Proč vytvářet čisté PDF soubory v java document review system?

Čistá verze odstraňuje značky recenzentů, komentáře a zvýraznění, což vám poskytuje upravený dokument připravený pro klienty, regulátory nebo veřejné zveřejnění. Také průměrně snižuje velikost souboru až o 30 % a zabraňuje neúmyslnému odhalení interních poznámek—což je kritické pro právní a compliance workflow. GroupDocs.Annotation může odstranit všechny objekty anotací v jednom průchodu a podporuje PDF až do 500 MB bez načítání celého souboru do paměti.

## Předpoklady a nastavení prostředí

### Požadavky před zahájením

**Požadavky na vývojové prostředí**  
- Java Development Kit (JDK) 8 nebo vyšší (doporučeno JDK 11+)  
- Maven 3.6+ nebo Gradle 6.0+ pro správu závislostí  
- IDE jako IntelliJ IDEA, Eclipse nebo VS Code s rozšířeními pro Javu  
- Minimálně 2 GB volné RAM (zpracování dokumentů může být paměťově náročné)

**Předpoklady znalostí**  
Měli byste být obeznámeni se základními koncepty Javy — inicializací objektů, voláním metod a Maven závislostmi. Předchozí zkušenost s knihovnami třetích stran urychlí adopci.

**Testovací dokumenty**  
Mějte připravené několik ukázkových PDF. Textové PDF fungují nejlépe; naskenované obrázky mohou vyžadovat OCR před anotací.

### Nastavení Maven: získání GroupDocs do vašeho projektu

Přidejte následující závislost do svého `pom.xml`. Tento krok mnohým vývojářům při první pokusu dělá problémy, protože group ID a artifact ID se musí shodovat přesně.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```

**Důležité:** Verze 25.2 je v době psaní nejnovější stabilní vydání. Pravidelně kontrolujte GroupDocs repozitář pro novější verze, které obsahují opravy chyb a vylepšení výkonu.

### Nastavení licencování (nepřeskakujte)

**Pro vývoj/testování** – Stáhněte si bezplatnou zkušební verzi z webu GroupDocs. Zkušební verze obsahuje všechny funkce, ale přidává vodoznak do zpracovaných dokumentů.

**Pro produkci** – Zakupte licenci a aplikujte ji během spouštění aplikace. Bez platné licence budou produkční sestavy omezené a opatřené vodoznakem.

## Průvodce implementací: přidání podtržených anotací

### Porozumění workflow anotací

Než se ponoříme do kódu, projděme si čtyřkrokový workflow, který probíhá, když **annotate PDF in Java**:

1. **Načítání dokumentu** – `Annotator` čte soubor do paměti.  
2. **Vytváření anotace** – Definujte vlastnosti jako pozici, styl a komentáře.  
3. **Aplikace anotace** – Knihovna vloží anotaci do struktury PDF.  
4. **Ukládání dokumentu** – Uložte upravený soubor, volitelně zachovávající originál.

Proces je ne‑destruktivní; zdrojový soubor zůstane nedotčen, pokud jej nepřepíšete.

### Krok 1: inicializace annotátoru a načtení dokumentu

`Annotator` je hlavní vstupní bod v GroupDocs.Annotation pro načítání a úpravu PDF dokumentů. Abstrahuje práci se souborovým systémem, správu streamů a alokaci nativních zdrojů.

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

**Pro tip:** Používejte absolutní cesty během vývoje, abyste se vyhnuli chybám „file not found“. V produkci zvažte načítání zdrojů z classpath nebo z cloudového úložiště.

### Krok 2: vytváření komentářů a odpovědí (kolaborativní část)

`Comment` objekty představují vlákna diskuse připojená k anotaci. Každý komentář může mít autora, časové razítko a volitelné odpovědi, což umožňuje kompletní konverzaci kolem konkrétního označení.

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Reálné použití:** Recenzenti mohou diskutovat o konkrétní klauzuli přidáváním vláknových odpovědí, čímž udržují konverzaci vázanou na přesnou anotaci.

### Krok 3: definování souřadnic anotace (správná pozice)

`Point` definuje jednu souřadnici v PDF prostoru (měřeno v bodech, kde 72 bodů = 1 palec). Pro podtržení jsou potřeba čtyři body: dva pro počáteční čáru a dva pro koncovou čáru.

```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;
import java.util.ArrayList;
import java.util.List;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

**Souřadnicový systém:**  
- Body 1 & 2 definují horní okraj podtržení.  
- Body 3 & 4 definují dolní okraj podtržení.  
- Rozdíl v Y (730 vs 650) řídí tloušťku.

### Krok 4: vytvoření a konfigurace podtržené anotace

`UnderlineAnnotation` je konkrétní třída, která představuje podtržené označení. Dědí z základní třídy `Annotation` a přidává vlastnosti specifické pro podtržení, jako je tloušťka čáry a styl.

```java
import com.groupdocs.annotation.models.Point;

Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = new ArrayList<>();
points.add(point1);
points.add(point2);
points.add(point3);
points.add(point4);
```

**Tipy pro barvu a průhlednost:**  
- `FontColor` používá ARGB; `65535` (0x00FFFF) dává jasně žlutou.  
- Pro červenou použijte `16711680` (0xFF0000); pro modrou `255` (0x0000FF).  
- Hodnoty průhlednosti mezi 0.5 a 0.8 poskytují dobrou čitelnost bez zakrytí textu.

### Krok 5: uložení anotovaného dokumentu

`SaveOptions` vám umožňuje řídit výstupní formát, zda vložit anotace, a jak zacházet s metadaty. Nastavení `AnnotationType.NONE` instruuje knihovnu, aby odstranila všechny objekty anotací, což je klíč k **save PDF without annotations**.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Yellow in ARGB format
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**Správa paměti:** Volání `dispose()` uvolňuje nativní zdroje a zabraňuje únikům paměti — kritické při zpracování mnoha souborů v dávce.

## Odstraňování anotací: vytváření čistých verzí dokumentu

Někdy potřebujete verzi PDF **bez jakýchkoli anotací** — například při dodání finální schválené smlouvy. GroupDocs to usnadňuje.

### Porozumění možnostem odstraňování anotací

Můžete:  
- Odstranit **všechny** anotace (nejčastější)  
- Odstranit konkrétní typy (např. jen zvýraznění)  
- Odstranit anotace podle autora nebo stránky  

### Krok za krokem odstraňování anotací

**Krok 1: načtěte dříve anotovaný dokument**

`Annotator` opět funguje jako načítač; načte soubor, který stále obsahuje objekty anotací.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Krok 2: nakonfigurujte možnosti uložení pro čistý výstup**

`SaveOptions` poskytuje fluent API pro specifikaci, že žádné typy anotací nebudou zapsány do výstupního souboru.

```java
Annotator annotator = new Annotator(outputPath);
```

**Krok 3: uložte čistou verzi**

Volání `save()` s nakonfigurovanými možnostmi zapíše PDF, které obsahuje jen původní obsah.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

Tím vznikne **clean PDF** soubor, který neobsahuje žádné objekty anotací, ideální pro finální distribuci.

## Časté problémy a řešení

### Problém 1: chyby „Document not found“

Ujistěte se, že cesta k souboru je správná a že aplikace má oprávnění ke čtení. Použití `Path.of()` s absolutními cestami eliminuje většinu nejasností.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

### Problém 2: Anotace se objevují na špatných místech

Počátek souřadnic PDF je v levém dolním rohu. Ověřte, že vaše Y‑hodnoty rostou směrem nahoru a že zohledňujete otočení stránky.

```java
File inputFile = new File("path/to/your/document.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Document not found: " + inputFile.getAbsolutePath());
}
if (!inputFile.canRead()) {
    throw new IllegalArgumentException("Cannot read document: " + inputFile.getAbsolutePath());
}

Annotator annotator = new Annotator(inputFile.getAbsolutePath());
```

### Problém 3: Problémy s pamětí u velkých dokumentů

GroupDocs.Annotation streamuje obsah a nikdy nenačítá celý soubor do haldy. Přesto musíte volat `dispose()` a zvážit zvýšení JVM haldy (`-Xmx`) pro soubory větší než 200 MB.

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Problém 4: Problémy s licencováním v produkci

Pokud chybí licenční soubor nebo je cesta nesprávná, knihovna přejde do zkušebního režimu a přidá vodoznak na každou stránku. Umístěte licenční soubor na místo, které je na classpath, a načtěte jej brzy v životním cyklu aplikace.

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

## Nejlepší praktiky výkonu pro produkční aplikace

### Strategie správy paměti

GroupDocs.Annotation zpracovává PDF ve streamovacím režimu, což mu umožňuje pracovat se soubory až do 500 MB bez načítání celého dokumentu do paměti. Přesto dodržujte následující pokyny:

```java
try {
    License license = new License();
    license.setLicense("path/to/your/license.lic");
    System.out.println("License loaded successfully");
} catch (Exception e) {
    System.err.println("License loading failed: " + e.getMessage());
    // Handle the error appropriately
}
```

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

### Úvahy o vláknování

GroupDocs.Annotation je **ne thread‑safe** ve výchozím nastavení. Pokud vaše aplikace zpracovává dokumenty souběžně:

- **Nikdy nesdílejte** instanci `Annotator` mezi vlákny.  
- **Synchronizujte** přístup k souborům nebo použijte zamykací mechanismus.  
- Zvažte **pool** objektů `Annotator`, pokud potřebujete vysoký průtok.

### Strategie cachování

- Cachujte často používané šablony anotací.  
- Znovu použijte kolekce `Point` pro běžné sady souřadnic.  
- Uchovávejte **template PDF** v paměti, pokud opakovaně anotujete stejný základní dokument.

## Nejlepší praktiky správy paměti pro Java PDF

Efektivní využití paměti je zásadní při práci s velkými PDF nebo při zpracování mnoha souborů v dávce. Zde je několik praktických doporučení:

- **Používejte try‑with‑resources** pro každý `Annotator`, aby byla zajištěna likvidace.  
- **Zvyšte JVM haldu** (`-Xmx`) jen podle potřeby; sledujte využití pomocí profilovacích nástrojů.  
- **Zpracovávejte dokumenty sekvenčně**, pokud je to možné, a po každém souboru uvolněte paměť.  
- **Vyhněte se opakovanému načítání stejného PDF**; pokud jej potřebujete číst opakovaně, znovu použijte stejný stream.

Použití těchto praktik pomáhá udržet aplikaci responzivní a zabraňuje pádům kvůli nedostatku paměti během náročných anotací.

## Reálné aplikace a příklady použití

### Systémy revize dokumentů

- **Legal review:** Podtrhněte klauzule smlouvy a přidejte komentáře o rizicích.  
- **Compliance audits:** Zvýrazněte problematické části ve finančních výkazech.  
- **Academic peer review:** Profesoři podtrhují pasáže, které vyžadují upřesnění.

### Vzdělávací platformy

- **Student annotation tools:** Umožněte studentům podtrhávat klíčové koncepty v e‑knihách.  
- **Teacher feedback:** Poskytněte inline komentáře přímo na odevzdaných úkolech.

### Workflowy zajištění kvality

- **Technical documentation review:** Inženýři podtrhují sekce, které potřebují aktualizaci.  
- **Standard operating procedures:** Bezpečnostní pracovníci zvýrazňují kritické kroky.

### Systémy správy obsahu

- **Editorial workflow:** Editoři podtrhují text, který vyžaduje fakt‑checking.  
- **Version control:** Sledujte historii anotací napříč revizemi dokumentu.

## Pokročilé tipy pro profesionální implementaci

### Vlastní styly anotací

Můžete rozšířit vizuální vzhled podtržení nastavením vlastních vzorů čáry, koncových úseků a úrovní průhlednosti. To je užitečné, když potřebujete rozlišovat role recenzentů (např. právní vs. technické).

```java
List<String> documentPaths = Arrays.asList("doc1.pdf", "doc2.pdf", "doc3.pdf");

for (String docPath : documentPaths) {
    try (Annotator annotator = new Annotator(docPath)) {
        // Process one document at a time
        annotator.add(createAnnotation());
        annotator.save(getOutputPath(docPath));
    }
    // Memory is freed after each iteration
}
```

### Metadata anotací pro sledování

Každá anotace může nést uživatelem definovaný slovník metadat. Ukládejte ID, časová razítka nebo stav workflow pro integraci s externími sledovacími systémy.

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Integrace se systémy správy uživatelů

Mapujte vlastnost `author` objektu `Comment` na ID uživatelů ve vaší aplikaci. To umožňuje stylování podle rolí a generování audit‑trailu.

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

## Odstraňování problémů v produkci

### Monitorování výkonu

Sledujte tyto metriky v produkci:  
- **Heap usage** — zajistěte, že je voláno `dispose()`.  
- **Processing time per document** — logujte časové značky před a po `annotator.save()`.  
- **Error rate** — zachytávejte výjimky a kategorizujte je.

### Časté problémy v produkci

- **File locking** — ujistěte se, že nahrané soubory jsou uzavřeny před anotací.  
- **Concurrent edits** — implementujte optimistické zamykání nebo kontrolu verzí.  
- **Large files (> 50 MB)** — zvyšte timeout JVM a zvažte streaming API.

### Nejlepší praktiky pro zpracování chyb

Zabalte všechny volání anotací do try‑catch bloků, logujte kompletní stack trace a znovu vyhoďte vlastní `AnnotationException` s uživatelsky přívětivou zprávou. Tento vzor usnadňuje ladění a poskytuje jasnou zpětnou vazbu spotřebitelům API.

```java
// Assume you have a method that returns the current authenticated user
String currentUser = getCurrentUser();
String userRole = getUserRole(currentUser);

// Apply role‑based styling
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedBy(currentUser);
underline.setFontColor(getRoleColor(userRole));
underline.setMessage(String.format("[%s] %s", userRole.toUpperCase(), commentText));
```

## Často kladené otázky

**Q: Jak anotovat více oblastí textu v jedné operaci?**  
A: Vytvořte několik objektů `UnderlineAnnotation` s různými souřadnicemi a přidejte je postupně pomocí `annotator.add()`.

**Q: Mohu anotovat obrázky v PDF dokumentech?**  
A: Ano. Použijte stejný souřadnicový systém a ujistěte se, že body leží uvnitř hranic obrázku.

**Q: Jaké formáty souborů kromě PDF podporuje GroupDocs.Annotation?**  
A: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) a obrazové formáty jako JPEG, PNG, TIFF.

**Q: Jak zacházet s velmi velkými dokumenty, aby nedošlo k vyčerpání paměti?**  
A: Zpracovávejte dokumenty po jednom, zvyšte JVM haldu (`-Xmx`) a vždy promptně uvolňujte instance `Annotator`.

**Q: Je možné extrahovat existující anotace z dokumentu?**  
A: Ano. Použijte `annotator.get()` k získání všech anotací a poté filtrujte podle typu, autora nebo stránky podle potřeby.

---

**Poslední aktualizace:** 2026-10-16  
**Testováno s:** GroupDocs.Annotation 25.2  
**Autor:** GroupDocs  

---

```java
try (Annotator annotator = new Annotator(documentPath)) {
    UnderlineAnnotation annotation = createAnnotation();
    annotator.add(annotation);
    annotator.save(outputPath);
    
} catch (Exception e) {
    logger.error("Annotation failed for document: " + documentPath, e);
    // Implement appropriate error recovery
    throw new DocumentProcessingException("Failed to annotate document", e);
}
```

## Související tutoriály

- [Vytvořit čisté PDF v Javě: podtržené anotace s GroupDocs](/annotation/java/annotation-management/java-groupdocs-annotate-add-remove-underline/)
- [Upravit PDF anotace v Javě – kompletní tutoriál GroupDocs](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [Anotovat PDF pomocí GroupDocs Annotation v Javě](/annotation/java/annotation-management/annotate-pdfs-groupdocs-annotation-java/)