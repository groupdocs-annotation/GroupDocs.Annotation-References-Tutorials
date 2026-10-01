---
categories:
- Java Tutorials
date: '2026-09-30'
description: Ismerje meg, hogyan hozhat létre PDF highlights java a GroupDocs segítségével.
  Ez a lépésről‑lépésre útmutató bemutatja, hogyan kell kiemelni a PDF-et Java-ban,
  megjegyzéseket hozzáadni, és optimise performance.
keywords:
- create pdf highlights java
- highlight text pdf java
- groupdocs annotation java
- pdf annotation java tutorial
lastmod: '2026-09-30'
linktitle: Java PDF annotation útmutató
og_description: Készítsen PDF highlights java a GroupDocs.Annotation segítségével.
  Kövesse ezt a lépésről‑lépésre útmutatót, hogy highlights, comments hozzáadjon,
  és optimise performance Java-ban.
og_image_alt: Developer guide illustrating PDF highlight creation using GroupDocs.Annotation
  for Java
og_title: PDF highlights java létrehozása – teljes útmutató Java fejlesztőknek
schemas:
- author: GroupDocs
  dateModified: '2026-09-30'
  description: Learn how to create PDF highlights java using GroupDocs. This step‑by‑step
    tutorial shows how to highlight PDF in Java, add comments, and optimise performance.
  headline: 'How to create PDF highlights java: complete guide for highlighting PDFs'
  type: TechArticle
- description: Learn how to create PDF highlights java using GroupDocs. This step‑by‑step
    tutorial shows how to highlight PDF in Java, add comments, and optimise performance.
  name: 'How to create PDF highlights java: complete guide for highlighting PDFs'
  steps:
  - name: Initialize your annotator object
    text: '`Annotator` is the core class in GroupDocs.Annotation that loads a PDF
      and provides methods to add, edit, and save annotations. **What''s happening
      here?** - The `Annotator` constructor loads your PDF into memory. - We set an
      output path where the annotated PDF will be saved. - The input PDF remains '
  - name: Create interactive replies and comments
    text: '`Reply` and `Comment` objects enable threaded conversations on a highlight,
      turning a static annotation into a collaborative discussion. Reply represents
      a single comment in a thread, while Comment groups replies under a specific
      annotation. **Why this matters**: In real applications you often need '
  - name: Define precise highlight coordinates
    text: '`HighlightAnnotation` is the class that represents a highlight region on
      a PDF page. HighlightAnnotation defines a rectangular highlight region on a
      PDF page, specified by a set of points. **Understanding PDF coordinates**: -
      Origin (0,0) is at the bottom‑left of the page. - X increases to the right'
  - name: Configure your highlight annotation
    text: '`HighlightAnnotation` lets you customise colour, opacity, font colour,
      and page number. **Customization options explained**: - `setBackgroundColor(65535)`:
      Yellow highlight (RGB integer). - `setOpacity(0.5)`: 50 % transparency keeps
      the underlying text readable. - `setFontColor(0)`: Black text ensur'
  - name: Save your annotated PDF
    text: '`dispose()` releases native resources and finalizes the PDF file. `dispose()`
      releases native resources and finalizes the PDF file. **Resource management**:
      The `dispose()` call is crucial—it frees up memory and guarantees all changes
      are persisted. Always wrap the annotator in a try‑with‑resources '
  type: HowTo
- questions:
  - answer: Absolutely. It integrates with Spring Boot, Servlets, and other Java web
      frameworks. Expose a REST endpoint that accepts a PDF, applies highlights, and
      returns the annotated file.
    question: Can I use GroupDocs.Annotation in web applications?
  - answer: The library supports Unicode, so you can add comments and messages in
      any language. Just ensure your Java application uses UTF‑8 encoding.
    question: How do I handle annotations in different languages?
  - answer: Performance scales with the number of annotations, but PDF size has a
      larger impact. For documents with hundreds of highlights, consider lazy loading
      or pagination to keep memory usage low.
    question: What's the performance impact of adding many annotations?
  - answer: Yes. Load a PDF with existing annotations, update properties such as colour
      or position, and save the updated version. This is ideal for building annotation‑management
      tools.
    question: Can I modify existing annotations programmatically?
  - answer: GroupDocs.Annotation provides enumeration methods to read metadata (author,
      creation date, comment text, etc.). Export this data to CSV, JSON, or feed it
      into analytics pipelines.
    question: How do I extract annotation data for reporting?
  type: FAQPage
tags:
- pdf annotation
- groupdocs
- java library
- document processing
- create pdf highlights java
title: 'Hogyan készítsünk PDF highlights java: teljes útmutató a PDF-ek kiemeléséhez'
type: docs
url: /hu/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/
weight: 1
---


# PDF kiemelések létrehozása Java-ban: teljes útmutató a PDF-ek kiemeléséhez

## Bevezetés

Volt már nehézséged a visszajelzések kezelése több dokumentumverzió között? Nem vagy egyedül. Akár dokumentumkezelő rendszert építesz, oktatási platformot hozol létre, vagy együttműködő eszközöket fejlesztesz, a **create pdf highlights java** meglepően nehéz lehet a semmiből megvalósítani.

Itt jön képbe a **GroupDocs.Annotation for Java**. Ez a hatékony könyvtár a bonyolult PDF-annotációs feladatokat egyszerű műveletekké alakítja, lehetővé téve kiemelések, megjegyzések és válaszok hozzáadását anélkül, hogy alacsony szintű PDF-kezeléssel kellene küzdeni.

Ebben az átfogó útmutatóban megtudod, hogyan **highlight pdf in java** valós példákon keresztül. Végigvezetünk mindenen a alapbeállítástól a fejlett kiemelési technikákig, és megosztjuk a gyakorlati tippeket, amelyeket a termelési környezetben való megvalósítás során tanultam.

Íme, pontosan, mit fogsz elsajátítani:

- A GroupDocs.Annotation beállítása a Java projektedben (helyesen)  
- Interaktív PDF-kiemelések létrehozása egyéni stílussal  
- Szálas válaszok és megjegyzések hozzáadása az együttműködéshez  
- Gyakori buktatók kezelése és a teljesítmény optimalizálása  
- Valós implementációs stratégiák  

Készen állsz, hogy PDF-jeidet interaktív, együttműködő dokumentumokká alakítsd? Merüljünk bele!

## Gyors válaszok
- **Melyik könyvtár egyszerűsíti a PDF-kiemeléseket Java-ban?** GroupDocs.Annotation for Java.  
- **Melyik Maven függőség adja hozzá a könyvtárat?** `com.groupdocs:groupdocs-annotation:25.2`.  
- **Szükségem van licencre a fejlesztéshez?** Egy ingyenes ideiglenes licenc működik teszteléshez; a termeléshez fizetett licenc szükséges.  
- **Hozzáadhatok megjegyzéseket a kiemelésekhez?** Igen, csatolhatsz válaszokat és szálas megjegyzéseket.  
- **Hogyan kezelem a memóriát nagy PDF-ek esetén?** Használj try‑with‑resources blokkot, és hívd meg a `dispose()`-t a mentés után.

## Hogyan hozhatok létre PDF-kiemeléseket Java-ban?

Töltsd be a cél PDF-et a `new Annotator(inputPath)` segítségével, majd hívd meg az `addAnnotation(highlight)`-t, ezt követően a `save(outputPath)`-t. Az Annotator a központi osztály, amely betölti a PDF dokumentumot, és módszereket biztosít az annotációk hozzáadásához, szerkesztéséhez és mentéséhez. Ez a kétlépéses folyamat másodpercek alatt kiemelt PDF-et hoz létre, automatikusan kezeli a koordináták átalakítását, és felszabadítja az erőforrásokat, amikor a `dispose()` meghívásra kerül. Kézi PDF-parszolás nem szükséges.

## Mi a create pdf highlights java?

`create pdf highlights java` arra utal, hogy programozottan hozzáadunk kiemelés-annotációkat PDF fájlokhoz Java kóddal, általában egy dedikált könyvtár, például a GroupDocs.Annotation segítségével. Ez a folyamat lehetővé teszi az automatizált felülvizsgálatot, együttműködést és a vizuális hangsúlyozást manuális szerkesztés nélkül.

## Miért válasszuk a GroupDocs.Annotation-t Java PDF feldolgozáshoz?

A GroupDocs.Annotation **30+ annotáció típust** támogat, és akár **500 MB**-os PDF-eket is feldolgozhat anélkül, hogy a teljes dokumentumot a memóriába töltené. Automatikusan feloldja az oldal‑szintű koordinátákat, megőrzi a meglévő tartalmat, és gazdag API-t kínál a stílusozáshoz, megjegyzésekhez és az annotációs adatok exportálásához.

## Előfeltételek és környezet beállítása

### Amire szükséged lesz

- **Fejlesztői környezet**: Java 8+ (Java 11+ ajánlott), Maven vagy Gradle, és egy IDE, például IntelliJ IDEA, Eclipse vagy VS Code.  
- **Tudás követelmények**: Alap Java (gyűjtemények, objektumok, fájl I/O), Maven függőségkezelés, és általános ismeret a PDF koordináta rendszerekről.

### A GroupDocs.Annotation telepítése Java-hoz

A legegyszerűbb módja a kezdésnek a Maven használata. Add hozzá ezeket a konfigurációkat a `pom.xml` fájlodhoz:

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

**Pro tipp**: Mindig a legújabb stabil verziót használd. A GroupDocs rendszeresen ad ki frissítéseket teljesítményjavításokkal és hibajavításokkal.

### Licenc beállítása (ne hagyd ki!)

Licencre lesz szükséged a GroupDocs.Annotation termelésben való használatához. Íme, hogyan kezeld a licencelést:

- **Fejlesztéshez**: Szerezz ingyenes próbaverziót vagy [ideiglenes licencet](https://purchase.groupdocs.com/temporary-license/)  
- **Termeléshez**: Vásárolj licencet a [GroupDocs weboldaláról](https://purchase.groupdocs.com/buy)

Az ideiglenes licenc tökéletes a teszteléshez és fejlesztéshez – teljes funkcionalitást biztosít vízjelek nélkül.

## Lépésről‑lépésre megvalósítási útmutató

Most jön a izgalmas rész – építsünk egy teljes PDF-annotációs rendszert! Végigvezetünk minden komponensen, és elmagyarázzuk, nem csak hogy mit csinál a kód, hanem miért így csináljuk.

### 1. lépés: Az annotátor objektum inicializálása

`Annotator` a GroupDocs.Annotation központi osztálya, amely betölti a PDF-et, és módszereket biztosít az annotációk hozzáadásához, szerkesztéséhez és mentéséhez.

```java
import com.groupdocs.annotation.Annotator;
import org.apache.commons.io.FilenameUtils;

String outputPath = "YOUR_OUTPUT_DIRECTORY/AnnotationOutput.pdf";
final Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/InputDocument.pdf");
```

**Mi történik itt?**  
- Az `Annotator` konstruktor betölti a PDF-et a memóriába.  
- Beállítunk egy kimeneti útvonalat, ahová az annotált PDF mentésre kerül.  
- A bemeneti PDF változatlan marad – egy új annotált verziót hozunk létre.

**Gyakori csapda**: Győződj meg arról, hogy a fájl útvonalak helyesek és a könyvtárak léteznek. Sok fejlesztő időt pazarol egyszerű útvonalhibák hibakeresésére.

### 2. lépés: Interaktív válaszok és megjegyzések létrehozása

`Reply` és `Comment` objektumok szálas beszélgetéseket tesznek lehetővé egy kiemelésen, egy statikus annotációt együttműködő megbeszélésévé alakítva. A Reply egyetlen megjegyzést képvisel egy szálban, míg a Comment a válaszokat egy adott annotáció alatt csoportosítja.

```java
import java.util.ArrayList;
import java.util.Calendar;
import java.util.List;

List<Reply> replies = new ArrayList<>();

// First reply
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());
replies.add(reply1);

// Second reply  
Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());
replies.add(reply2);
```

**Miért fontos**: Valós alkalmazásokban gyakran szükséges nyomon követni, ki mit mondott és mikor. Ez a válaszrendszer lehetővé teszi az alábbi funkciók kiépítését:
- Megjegyzés szálak a kiemelt szövegen  
- Felülvizsgálati munkafolyamatok jóváhagyási láncokkal  
- Audit nyomvonalak a dokumentumváltozásokhoz  
- Együttműködő szerkesztő környezetek  

**Valós tippek**: Tárold a felhasználói információkat és időbélyegeket adatbázisban, ahelyett, hogy az alapértelmezett értékekre támaszkodnál.

### 3. lépés: Pontos kiemelési koordináták meghatározása

`HighlightAnnotation` az az osztály, amely egy kiemelési területet reprezentál egy PDF oldalon. A HighlightAnnotation egy téglalap alakú kiemelési területet definiál a PDF oldalon, amely pontok halmazával van megadva.

```java
import com.groupdocs.annotation.models.Point;
import java.util.ArrayList;
import java.util.List;

List<Point> points = new ArrayList<>();
points.add(new Point(80, 730));   // Top-left corner
points.add(new Point(240, 730));  // Top-right corner  
points.add(new Point(80, 650));   // Bottom-left corner
points.add(new Point(240, 650));  // Bottom-right corner
```

**A PDF koordináták megértése**:
- Az origó (0,0) az oldal bal alsó sarkában van.  
- Az X jobbra növekszik, a Y felfelé.  
- Négy pont hoz létre egy határoló dobozt a cél szöveg körül.  

**Pro tipp a koordináták megtalálásához**: Használj PDF nézőt, amely megjeleníti a kurzor koordinátáit, vagy kezdj hozzávetőleges értékekkel, majd finomhangold a vizuális eredmények alapján.

### 4. lépés: A kiemelés annotáció konfigurálása

`HighlightAnnotation` lehetővé teszi a szín, átlátszóság, betűszín és oldal szám testreszabását.

```java
import com.groupdocs.annotation.models.annotationmodels.HighlightAnnotation;

HighlightAnnotation highlight = new HighlightAnnotation();
highlight.setBackgroundColor(65535);  // Yellow highlight
highlight.setCreatedOn(Calendar.getInstance().getTime());
highlight.setFontColor(0);            // Black text  
highlight.setMessage("This is a highlight annotation");
highlight.setOpacity(0.5);            // Semi‑transparent
highlight.setPageNumber(0);           // First page (zero‑indexed)
highlight.setPoints(points);
highlight.setReplies(replies);

// Add the highlight to the annotator
annotator.add(highlight);
```

**A testreszabási lehetőségek magyarázata**:
- `setBackgroundColor(65535)`: Sárga kiemelés (RGB egész szám).  
- `setOpacity(0.5)`: 50 % átlátszóság, amely olvashatóvá teszi a háttér szöveget.  
- `setFontColor(0)`: Fekete szöveg, amely jó kontrasztot biztosít.  
- `setPageNumber(0)`: Oldal index (0 = első oldal).  

**Színválasztási tippek**:
- A sárga (65535) klasszikus és nem tolakodó.  
- Fontos kiemelésekhez próbáld ki a narancssárgát (16753920) vagy a pirosat (16711680).  
- Tartsd az átlátszóságot 0.3‑0.7 között a legjobb olvashatóság érdekében.

### 5. lépés: Az annotált PDF mentése

`dispose()` felszabadítja a natív erőforrásokat és befejezi a PDF fájlt. `dispose()` felszabadítja a natív erőforrásokat és befejezi a PDF fájlt.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Erőforrás-kezelés**: A `dispose()` hívás kulcsfontosságú – felszabadítja a memóriát és garantálja, hogy minden változás mentésre kerüljön. Mindig tedd az annotátort try‑with‑resources blokkba, vagy hívd meg a `dispose()`-t egy finally ágba.

## Gyakori problémák hibaelhárítása

### Fájl útvonal problémák  

**Tünet**: `FileNotFoundException` vagy “Cannot access file”.  
**Megoldás**: Ellenőrizd, hogy az útvonalak abszolútak vagy a projekt gyökeréhez relatívak, nézd meg a fájl jogosultságokat, és győződj meg arról, hogy a kimeneti könyvtárak léteznek a mentés előtt.

### A koordináták nem egyeznek a várt helyen  

**Tünet**: A kiemelések rossz helyen jelennek meg.  
**Megoldás**: Ne feledd, hogy a PDF koordináta rendszer a bal alsó sarokból indul. Különböző PDF generátorok enyhe eltéréseket mutathatnak; tesztelj mintapéldákkal és ennek megfelelően állítsd be.

### Memória problémák nagy PDF-ekkel  

**Tünet**: `OutOfMemoryError` vagy lassú teljesítmény.  
**Megoldás**: Növeld a JVM heap méretét (pl. `-Xmx2G`), dolgozd fel a PDF-eket kisebb adagokban, és mindig hívd meg a `dispose()`-t az erőforrások felszabadításához.

### A szín nem jelenik meg helyesen  

**Tünet**: Rossz kiemelési színek vagy láthatatlan annotációk.  
**Megoldás**: Használj RGB egész szám értékeket, ne hex stringeket. Tesztelj átlátszósági értékeket 0.1 és 0.9 között. Ellenőrizd, hogy a háttér és betűszín jó kontrasztot biztosít.

## Teljesítményoptimalizálás legjobb gyakorlatai

### Memóriakezelés

```java
// Good practice - use try-with-resources when available
try (Annotator annotator = new Annotator(inputPath)) {
    // Your annotation code here
    annotator.save(outputPath);
} // Automatically disposes resources
```

Hozd létre az annotátort egy try‑with‑resources blokkban, és szabadítsd fel gyorsan. Ez a minta megakadályozza a memória szivárgást, amikor sok dokumentumot dolgozol fel.

### Kötetes feldolgozási stratégia

```java
for (String pdfPath : pdfPaths) {
    try (Annotator annotator = new Annotator(pdfPath)) {
        // Process single PDF
        addAnnotations(annotator);
        annotator.save(getOutputPath(pdfPath));
    }
    // Memory freed before next iteration
}
```

Több PDF esetén dolgozd fel őket sorban, ahelyett, hogy mindet a memóriába töltenéd. Ez a megközelítés lineárisan skálázódik és alacsony JVM lábnyomot tart.

### Fájlméret szempontok

- Nagy PDF-ek (>10 MB) több memóriát és feldolgozási időt igényelnek.  
- Fontold meg nagyon nagy dokumentumok szakaszokra bontását.  
- Optimalizáld a bemeneti PDF-eket (képek tömörítése, nem használt objektumok eltávolítása) az annotáció előtt.

## Valós alkalmazások és felhasználási esetek

### Dokumentum felülvizsgálati rendszerek  

Tökéletes jogi szerződésekhez, műszaki specifikációkhoz és megfelelőségi dokumentumokhoz. Használj különböző kiemelési színeket minden ellenőrzőhöz, érvényesíts jogosultsági szabályokat, és tárold az annotáció metaadatait adatbázisban jelentéskészítéshez.

### Oktatási platformok  

Ideális tankönyv kiemelésekhez, feladat visszajelzésekhez és együttműködő tanuláshoz. Engedélyezd a diákoknak személyes annotációk mentését, a tanároknak hivatalos megjegyzések hozzáadását, és verziókezelés a tananyagok fejlődése során.

### Minőség‑biztosítási munkafolyamatok  

Remek tervezési felülvizsgálatokhoz, folyamat dokumentációhoz és megfelelőség ellenőrzéshez. Integráld meglévő QA eszközökkel, használj annotáció státuszt (nyitott/megoldott) a nyomon követéshez, és generálj audit jelentéseket az annotációs adatokból.

### Együttműködő kutatási eszközök  

Alkalmas tudományos cikkekhez, kutatási dokumentációhoz és lektoráláshoz. Valós idejű együttműködés megvalósítása, anonim véleményezés támogatása, és annotációk exportálása elemzéshez.

## Haladó tippek és legjobb gyakorlatok

### Koordináta számítás segítő metódusok

```java
public class AnnotationUtils {
    public static List<Point> createRectangle(double x, double y, double width, double height) {
        List<Point> points = new ArrayList<>();
        points.add(new Point(x, y + height));      // Top‑left
        points.add(new Point(x + width, y + height)); // Top‑right  
        points.add(new Point(x, y));               // Bottom‑left
        points.add(new Point(x + width, y));       // Bottom‑right
        return points;
    }
}
```

Készíts segédmetódusokat, amelyek a képernyő koordinátákat PDF pontokká konvertálják, csökkentve a sablonkódot és javítva az olvashatóságot.

### Annotáció sablonok

```java
public class AnnotationTemplates {
    public static HighlightAnnotation createStandardHighlight(List<Point> points, String message) {
        HighlightAnnotation highlight = new HighlightAnnotation();
        highlight.setBackgroundColor(65535);  // Yellow
        highlight.setOpacity(0.5);
        highlight.setFontColor(0);
        highlight.setMessage(message);
        highlight.setCreatedOn(Calendar.getInstance().getTime());
        highlight.setPoints(points);
        return highlight;
    }
}
```

Határozz meg újrahasználható annotáció konfigurációkat (szín, átlátszóság, szerző), hogy konzisztenciát biztosíts az alkalmazásodban.

## Gyakran ismételt kérdések

**Q: Használhatom a GroupDocs.Annotation-t webalkalmazásokban?**  
A: Teljesen. Integrálódik a Spring Boot, Servlets és más Java web keretrendszerekkel. Tegyél közzé egy REST végpontot, amely PDF-et fogad, alkalmaz kiemeléseket, és visszaadja az annotált fájlt.

**Q: Hogyan kezelem az annotációkat különböző nyelveken?**  
A: A könyvtár támogatja az Unicode-ot, így bármilyen nyelven hozzáadhatsz megjegyzéseket és üzeneteket. Csak győződj meg róla, hogy a Java alkalmazásod UTF‑8 kódolást használ.

**Q: Milyen teljesítményhatása van a sok annotáció hozzáadásának?**  
A: A teljesítmény a annotációk számával arányosan nő, de a PDF mérete nagyobb hatással van. Százszámú kiemelés esetén fontold meg a lusta betöltést vagy a lapozást a memóriahasználat alacsonyan tartásához.

**Q: Módosíthatom programozottan a meglévő annotációkat?**  
A: Igen. Tölts be egy PDF-et meglévő annotációkkal, frissítsd a tulajdonságokat, például a színt vagy a pozíciót, és mentsd el a frissített verziót. Ez ideális annotáció‑kezelő eszközök építéséhez.

**Q: Hogyan nyerhetem ki az annotációs adatokat jelentéshez?**  
A: A GroupDocs.Annotation felsoroló metódusokat biztosít a metaadatok (szerző, létrehozás dátuma, megjegyzés szövege stb.) olvasásához. Exportáld ezeket az adatokat CSV, JSON formátumba, vagy tápláld be elemzési folyamatokba.

## Alapvető források és dokumentáció

- [GroupDocs.Annotation Java Documentation](https://docs.groupdocs.com/annotation/java/) – átfogó útmutatók és API referenciák  
- [API Reference](https://reference.groupdocs.com/annotation/java/) – részletes metódus dokumentáció  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) – mindig a legújabb stabil kiadást használd  
- [Purchase License](https://purchase.groupdocs.com/buy) – termelési licenc opciók  
- [Get Temporary License](https://purchase.groupdocs.com/temporary-license/) – tökéletes fejlesztéshez és teszteléshez  
- [Community Support Forum](https://forum.groupdocs.com/c/annotation/) – segítség szakértőktől és más fejlesztőktől  

---

**Utolsó frissítés:** 2026-09-30  
**Tesztelve ezzel:** GroupDocs.Annotation 25.2  
**Szerző:** GroupDocs

## Kapcsolódó oktatóanyagok

- [Edit PDF Annotations Java - Complete GroupDocs Tutorial](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)  
- [Load PDF Annotations Java - Complete GroupDocs Annotation Management Guide](/annotation/java/annotation-management/groupdocs-annotation-java-manage-documents/)  
- [Add Arrow PDF in Java – Complete GroupDocs Tutorial](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)