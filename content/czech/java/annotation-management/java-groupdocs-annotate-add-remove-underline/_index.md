---
categories:
- Java Development
date: '2025-12-21'
description: Naučte se, jak vytvářet čisté PDF soubory v Javě a anotovat PDF v Javě
  pomocí GroupDocs.Annotation, s kompletními ukázkami kódu a tipy na řešení problémů.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2025-12-21'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'Vytvořte čistý PDF v Javě - podtržené anotace pomocí GroupDocs'
type: docs
url: /cs/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Vytvoření čistého PDF Java: Podtržené anotace s GroupDocs

## Úvod

Máte potíže se správou dokumentů a spoluprací ve svých Java aplikacích? Nejste v tom sami. Mnoho vývojářů čelí výzvě implementovat robustní funkce anotací dokumentů, které spolehlivě fungují napříč různými formáty souborů.

V tomto průvodci **vytvoříte čisté PDF Java** soubory a naučíte se, jak **anotovat PDF v Javě** pomocí GroupDocs.Annotation. Na konci tohoto tutoriálu budete přesně vědět, jak přidat podtržené anotace s komentáři, odstranit existující anotace a tyto funkce hladce integrovat do svých projektů.

**Co v tomto průvodci zvládnete:**
- Nastavení GroupDocs.Annotation ve vašem Java projektu (správným způsobem)  
- Přidání podtržených anotací s vlastními komentáři a stylem  
- Odstranění všech anotací pro vytvoření čistých verzí dokumentů  
- Řešení běžných problémů, se kterými se vývojáři setkávají  
- Optimalizaci výkonu pro produkční aplikace  

Ať už budujete systém pro revizi dokumentů, vzdělávací platformu nebo nástroj pro kolaborativní úpravy, tento tutoriál vás provede praktickými, otestovanými ukázkami kódu.

## Rychlé odpovědi
- **Jak přidám podtrženou anotaci?** Použijte `UnderlineAnnotation` a `annotator.add()`, poté dokument uložte.  
- **Jak vytvořím čistý PDF Java soubor?** Načtěte anotovaný soubor, nastavte `AnnotationType.NONE` v `SaveOptions` a uložte novou kopii.  
- **Jaké knihovny jsou vyžadovány?** GroupDocs.Annotation v25.2 (nebo novější) a její Maven repozitář.  
- **Potřebuji licenci pro produkci?** Ano — aplikujte platnou GroupDocs licenci, aby se zabránilo vodoznakům.  
- **Mohu zpracovávat více dokumentů efektivně?** Zabalte každý `Annotator` do bloku try‑with‑resources a po každém souboru jej uvolněte.

## Jak vytvořit čisté PDF Java soubory
Vytvoření čistého PDF Java souboru znamená vygenerování verze dokumentu **bez jakýchkoli anotací** při zachování původního obsahu. To je užitečné pro finální distribuci, archivaci nebo když potřebujete sdílet „čistou“ kopii po revizním cyklu.

GroupDocs.Annotation to usnadňuje: načtěte anotovaný soubor, nakonfigurujte `SaveOptions` tak, aby vyloučily všechny typy anotací, a výsledek uložte. Kroky jsou ilustrovány později v sekci **Odstraňování anotací**.

## Jak anotovat PDF v Javě pomocí GroupDocs
GroupDocs.Annotation poskytuje bohaté API pro **anotaci PDF v Javě**. Podporuje širokou škálu typů anotací, včetně zvýraznění, razítek a podtržení. V tomto tutoriálu se zaměříme na podtržené anotace, protože jsou často používány k zdůraznění textu a umožňují vlákna komentářů.

## Předpoklady a nastavení prostředí

### Co budete potřebovat před zahájením

**Požadavky na vývojové prostředí:**
- Java Development Kit (JDK) 8 nebo vyšší (doporučeno JDK 11+)  
- Maven 3.6+ nebo Gradle 6.0+ pro správu závislostí  
- IDE jako IntelliJ IDEA, Eclipse nebo VS Code s rozšířeními pro Javu  
- Minimálně 2 GB volné RAM (zpracování dokumentů může být náročné na paměť)

**Předpoklady znalostí:**
Měli byste být obeznámeni se základními koncepty Javy — inicializací objektů, voláním metod a Maven závislostmi. Předchozí zkušenosti s knihovnami třetích stran urychlí adopci.

**Testovací dokumenty:**
Mějte připravené několik ukázkových PDF. Textové PDF fungují nejlépe; naskenované obrázky mohou vyžadovat OCR před anotací.

### Nastavení Maven: Přidání GroupDocs do projektu

Zde je správná konfigurace vašeho Maven projektu (mnoho vývojářů to při první pokusu špatně nastaví):

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

**Důležité:** Verze 25.2 je v době psaní nejnovější stabilní vydání. Pravidelně kontrolujte GroupDocs repozitář pro novější verze, které obsahují opravy chyb a vylepšení výkonu.

### Nastavení licence (nesmí chybět)

**Pro vývoj/testování:**  
Stáhněte si bezplatnou zkušební verzi z webu GroupDocs. Zkušební verze obsahuje všechny funkce, ale přidává vodoznak do zpracovaných dokumentů.

**Pro produkci:**  
Zakupte licenci a aplikujte ji při startu aplikace. Bez platné licence budou produkční sestavení omezená.

## Průvodce implementací: Přidání podtržených anotací

### Porozumění workflow anotací

Než se ponoříme do kódu, projděme čtyřkrokový workflow, který probíhá při **anotaci PDF v Javě**:

1. **Načtení dokumentu** — `Annotator` načte soubor do paměti.  
2. **Vytvoření anotace** — Definujte vlastnosti jako pozici, styl a komentáře.  
3. **Aplikace anotace** — Knihovna vloží anotaci do struktury PDF.  
4. **Uložení dokumentu** — Uložte upravený soubor, případně zachovejte originál.

Proces je nedestruktivní; zdrojový soubor zůstane nedotčen, pokud jej nepřepíšete.

### Krok 1: Inicializace Annotatoru a načtení dokumentu

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Tip:** Používejte absolutní cesty během vývoje, aby se předešlo chybám „soubor nenalezen“. V produkci zvažte načítání zdrojů ze classpath nebo z cloudového úložiště.

### Krok 2: Vytváření komentářů a odpovědí (kolaborativní část)

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

**Reálné použití:** Recenzenti mohou diskutovat o konkrétním odstavci přidáním vláken odpovědí, čímž je konverzace svázána s konkrétní anotací.

### Krok 3: Definování souřadnic anotace (správná pozice)

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

**Soustava souřadnic:**  
- Body 1 & 2 definují horní okraj podtržení.  
- Body 3 & 4 definují dolní okraj.  
- Rozdíl v Y (730 vs 650) řídí tloušťku.

### Krok 4: Vytvoření a konfigurace podtržené anotace

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

**Tipy pro barvu a neprůhlednost:**  
- `FontColor` používá ARGB; `65535` (0x00FFFF) dává jasně žlutou.  
- Pro červenou použijte `16711680` (0xFF0000); pro modrou `255` (0x0000FF).  
- Hodnoty neprůhlednosti mezi 0.5 a 0.8 poskytují dobrou čitelnost bez zakrytí textu.

### Krok 5: Uložení anotovaného dokumentu

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Správa paměti:** Volání `dispose()` uvolní nativní zdroje a zabrání únikům paměti — kritické při zpracování mnoha souborů v dávce.

## Odstraňování anotací: Vytváření čistých verzí dokumentů

Někdy potřebujete verzi PDF **bez jakýchkoli anotací** — například při dodání finální schválené smlouvy. GroupDocs to usnadňuje.

### Porozumění možnostem odstraňování anotací

Můžete:
- Odstranit **všechny** anotace (nejčastější)  
- Odstranit konkrétní typy (např. jen zvýraznění)  
- Odstranit anotace podle autora nebo stránky  

### Krok‑za‑krokem odstraňování anotací

**Krok 1: Načtení dříve anotovaného dokumentu**

```java
Annotator annotator = new Annotator(outputPath);
```

**Krok 2: Konfigurace Save Options pro čistý výstup**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Krok 3: Uložení čisté verze**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

Tím vznikne **čistý PDF Java** soubor, který neobsahuje žádné objekty anotací, ideální pro finální distribuci.

## Časté problémy a řešení

### Problém 1: Chyba „Document not found“

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

### Problém 2: Anotace se zobrazují na špatných místech

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Problém 3: Problémy s pamětí u velkých dokumentů

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### Problém 4: Licenční problémy v produkci

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

## Nejlepší praktiky výkonu pro produkční aplikace

### Strategie správy paměti

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

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

### Úvahy o vláknění

GroupDocs.Annotation není ve výchozím nastavení **thread‑safe**. Pokud vaše aplikace zpracovává dokumenty souběžně:

- **Nikdy nesdílejte** instanci `Annotator` mezi vlákny.  
- **Synchronizujte** přístup k souborům nebo použijte zamykací mechanismus.  
- Zvažte **pool** objektů `Annotator`, pokud potřebujete vysokou propustnost.

### Strategie cachování

- Cachujte často používané šablony anotací.  
- Znovu použijte kolekce `Point` pro běžné sady souřadnic.  
- Uchovávejte **šablonové PDF** v paměti, pokud opakovaně anotujete stejný základní dokument.

## Reálné aplikace a příklady použití

### Systémy pro revizi dokumentů

- **Právní revize:** Podtrhněte klauzule smlouvy a přidejte komentáře o rizicích.  
- **Audit shody:** Zvýrazněte problematické části ve finančních výkazech.  
- **Akademické recenze:** Profesori podtrhnou pasáže vyžadující upřesnění.

### Vzdělávací platformy

- **Nástroje pro anotaci studentů:** Umožněte studentům podtrhnout klíčové koncepty v e‑knihách.  
- **Zpětná vazba učitelů:** Poskytněte inline komentáře přímo na odevzdaných úlohách.

### Pracovní postupy kvality

- **Revize technické dokumentace:** Inženýři podtrhnou sekce, které je třeba aktualizovat.  
- **Standardní operační postupy:** Bezpečnostní pracovníci zvýrazní kritické kroky.

### Systémy pro správu obsahu

- **Redakční workflow:** Editoři podtrhnou text, který vyžaduje ověření faktů.  
- **Kontrola verzí:** Sledujte historii anotací napříč revizemi dokumentu.

## Pokročilé tipy pro profesionální implementaci

### Vlastní styly anotací

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Metadata anotací pro sledování

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### Integrace se systémy správy uživatelů

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

## Řešení problémů v produkci

### Monitorování výkonu

Sledujte tyto metriky v produkci:
- **Využití haldy** — zajistěte, aby byl volán `dispose()`.  
- **Čas zpracování na dokument** — logujte časové značky před a po `annotator.save()`.  
- **Míra chyb** — zachycujte výjimky a kategorizujte je.

### Časté překvapení v produkci

- **Zamykání souborů** — ujistěte se, že nahrané soubory jsou uzavřeny před anotací.  
- **Současné úpravy** — implementujte optimistické zamykání nebo kontrolu verzí.  
- **Velké soubory (> 50 MB)** — zvyšte JVM timeout a zvažte streaming API.

### Nejlepší praktiky pro zpracování chyb

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

## Závěr

Nyní máte vše potřebné k **vytvoření čistých PDF Java** souborů a **anotaci PDF v Javě** podtrženými anotacemi pomocí GroupDocs.Annotation. Pamatujte:

- Spravujte zdroje pomocí try‑with‑resources nebo explicitního `dispose()`.  
- Validujte souřadnice brzy, aby nedošlo k nesprávnému umístění podtržení.  
- Implementujte robustní zpracování chyb pro stabilitu v produkci.  
- Využívejte stylování na základě rolí a metadata, aby vyhovovaly vašemu workflowu.

Další kroky? Vyzkoušejte přidání dalších typů anotací — zvýraznění, razítka nebo nahrazení textu — a vytvořte kompletní řešení pro revizi dokumentů.

## Často kladené otázky

**Q: Jak anotovat více oblastí textu najednou?**  
A: Vytvořte několik objektů `UnderlineAnnotation` s různými souřadnicemi a přidejte je postupně pomocí `annotator.add()`.

**Q: Můžu anotovat obrázky v PDF dokumentech?**  
A: Ano. Použijte stejný souřadnicový systém a ujistěte se, že body leží uvnitř hranic obrázku.

**Q: Jaké formáty souborů kromě PDF GroupDocs.Annotation podporuje?**  
A: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) a obrazové formáty jako JPEG, PNG, TIFF.

**Q: Jak zvládnout velmi velké dokumenty, aby nedošlo k vyčerpání paměti?**  
A: Zpracovávejte dokumenty po jednom, zvyšte JVM heap (`-Xmx`) a vždy rychle uvolňujte instance `Annotator`.

**Q: Je možné extrahovat existující anotace z dokumentu?**  
A: Ano. Použijte `annotator.get()` k získání všech anotací a poté je filtrujte podle typu, autora nebo stránky.

---

**Poslední aktualizace:** 2025-12-21  
**Testováno s:** GroupDocs.Annotation 25.2  
**Autor:** GroupDocs  

---