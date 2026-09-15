---
categories:
- Java PDF Processing
date: '2026-05-21'
description: Ismerje meg, hogyan adhat hozzá áthúzott annotációkat PDF-ekhez Java-ban
  a GroupDocs segítségével. Ez a lépésről‑lépésre útmutató a beállítást, a kódot,
  a hibakeresést és a teljesítményre vonatkozó tippeket tárgyalja.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Java PDF szöveg áthúzási útmutató
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
title: Hogyan adhatunk hozzá áthúzott annotációkat PDF-ekhez Java-ban – Teljes GroupDocs
  útmutató
type: docs
url: /hu/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# Hogyan adjunk hozzá áthúzott megjegyzéseket PDF-ekhez Java-ban

Szükséged volt már arra, hogy programozottan áthúzd a szöveget egy PDF-ben? Akár dokumentum-ellenőrző rendszert építesz, szerkesztési munkafolyamatot hozol létre, vagy egyszerűen csak meg kell jelölnöd a törlendő szöveget, a **how to add strikeout** annotációk Java-ban egy gyakorlati készség, amely időt takarít meg és csökkenti a kézi munkát. Ebben az átfogó útmutatóban mindent megtudsz, amit a strikeout annotációk megvalósításához a GroupDocs.Annotation for Java segítségével tudni kell, a projekt beállításától a teljesítmény optimalizálásáig.

## Gyors válaszok
- **Mi az első lépés?** Add the GroupDocs.Annotation Maven dependency to your `pom.xml`.  
- **Hogyan hozhatok létre áthúzást?** Instantiate `Annotator`, define `StrikeoutAnnotation` with points, set color/opacity, then call `addAnnotation`.  
- **Hozzáadhatok megjegyzéseket?** Yes, attach a `Comment` object to the annotation for collaboration.  
- **Mi van, ha a megjegyzés rossz helyen van?** Adjust the coordinate points; PDF uses a bottom‑left origin system.  
- **Van korlátozás a dokumentum méretére?** GroupDocs processes multi‑hundred‑page PDFs without loading the entire file into memory.

## Mi az a “how to add strikeout” a PDF megjegyzésben?
A “how to add strikeout” kifejezés a programozott módon egy vonal rajzolását jelenti a kiválasztott szöveg áthaladásához egy PDF-dokumentumban egy annotációs API használatával. Java-ban a GroupDocs.Annotation egy dedikált `StrikeoutAnnotation` osztályt biztosít, amely kezeli az áthúzási jelek megjelenítését, stílusát és megőrzését.

## Miért használjuk a GroupDocs-et Java PDF áthúzáshoz?
A GroupDocs.Annotation **50+ bemeneti és kimeneti formátumot** támogat—beleértve a PDF, DOCX, XLSX, PPTX, HTML és a gyakori képformátumokat—így nem vagy korlátozva egyetlen fájltípusra. Magas szintű API-t biztosít, amely elrejti az alacsony szintű PDF struktúrát, automatikusan kezeli a betűtípus beágyazását, az oldal renderelését és az annotációk megőrzését, így a fejlesztők az üzleti logikára koncentrálhatnak a PDF belső részletei helyett.

## Előfeltételek és beállítási követelmények

### Alapvető követelmények
- **Java Development Kit (JDK):** Version 8 vagy újabb (JDK 11+ ajánlott a legoptimálisabb garbage‑collection-hoz).  
- **GroupDocs.Annotation for Java:** Maven-en keresztül integrálva (lásd az alábbi Maven kódrészletet).  
- **IDE:** IntelliJ IDEA, Eclipse vagy bármely Java‑kompatibilis szerkesztő.

### Maven függőségek beállítása
Adja hozzá a következő függőségi blokkot a `pom.xml`-hez:

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

**Pro Tip:** Mindig ellenőrizze a legújabb verziót a GroupDocs kiadási oldalon; az újabb kiadások új funkciókat adnak hozzá és hibákat javítanak, amelyek befolyásolhatják az annotáció megjelenítését.

### Licenc beszerzése
A GroupDocs.Annotation érvényes licencet igényel a termelésben való használathoz. Három lehetőséged van:
- **Ingyenes próba:** Letöltés innen: [GroupDocs letöltések](https://releases.groupdocs.com/annotation/java/)
- **Ideiglenes licenc:** Fejlesztői kulcs kérése itt: [GroupDocs Ideiglenes Licenc](https://purchase.groupdocs.com/temporary-license/)
- **Teljes licenc:** Vásárlás a termeléshez itt: [GroupDocs Vásárlási oldal](https://purchase.groupdocs.com/buy)

A próba egy finom vízjelet ad hozzá, ezért ennek megfelelően tervezze a tesztelést.

## Lépésről‑lépésre megvalósítási útmutató

### A fő komponensek megértése
A következő definíciók gyors mentális modellt adnak:
- **Annotator:** Az elsődleges API objektum, amely betölti a PDF-et és elérhetővé teszi az annotációs metódusokat.  
- **StrikeoutAnnotation:** A vizuális áthúzási vonalat és annak stílusbeállításait képviseli.  
- **Point:** Egy koordináta pár (X, Y), amely megmondja a könyvtárnak, hol kezdődik és végződik a vonal.  
- **Comment:** Opcionális szöveg, amely egy annotációhoz csatolva van az együttműködéshez.

### 1. lépés: Fájl útvonalak beállítása
Határozza meg a forrás PDF és a célfájl helyét. A helytelen útvonalak gyakori oka a “File Not Found” hibáknak.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Common Mistake Alert:** Győződjön meg arról, hogy a kimeneti könyvtár létezik és írható; a GroupDocs nem hoz létre automatikusan hiányzó mappákat.

### 2. lépés: Az Annotator inicializálása
Hozzon létre egy `Annotator` példányt, amely betölti a PDF-et a memóriába.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**What happens here?** A könyvtár beolvassa a PDF struktúráját, belső reprezentációt épít, és előkészíti az oldalankénti annotációs vásznat. Több száz oldalas fájlok esetén ez a lépés néhány másodpercet vehet igénybe.

### 3. lépés: Megjegyzések hozzáadása (opcionális, de ajánlott)
`Comment` egy osztály, amely szöveges megjegyzést képvisel, amely egy annotációhoz csatolva van, lehetővé téve a közreműködők számára, hogy elmagyarázzák az áthúzás okát.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Real‑world tip:** Használjon megjegyzéseket, hogy elmagyarázza, miért távolítják el a szöveget—ez különösen hasznos jogi vagy szerkesztői felülvizsgálati munkafolyamatokban.

### 4. lépés: Az annotáció koordinátáinak meghatározása
`Point` objektumok tárolják az X‑Y koordináta párokat, amelyek meghatározzák egy annotáció pontos helyét egy PDF oldalon.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Coordinate System Explained:** A PDF koordináták a bal alsó sarokból (0,0) indulnak. A példa egy vízszintes vonalat hoz létre (80,730) és (240,730) között a céloldalon.

**Finding the Right Coordinates:** Sok fejlesztő készít egy segédfüggvényt, amely az oldal szélességének/magasságának százalékát átalakítja abszolút pontokba, így a kód rugalmas marad különböző oldalméretekhez.

### 5. lépés: Az áthúzott annotáció létrehozása
`StrikeoutAnnotation` magába foglalja a vizuális vonalat, annak stílus tulajdonságait, mint a szín és az átlátszatlanság, valamint minden kapcsolódó metaadatot az áthúzási jelhez.

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

**Color Values:** A `fontColor` decimális RGB értékeket használ (pl. 65535 a világos sárgához). Használjon online konvertert, ha márkaspecifikus árnyalatokra van szükség.

**Opacity Recommendation:** A `0.7` (70 %) átlátszatlanság tiszta vizuális jelzést ad, miközben a háttérszöveg olvasható marad.

### 6. lépés: Az annotáció alkalmazása
`addAnnotation` a `Annotator` egy metódusa, amely regisztrálja a előkészített annotációt a dokumentummal, így az megjelenik és el lesz mentve.

```java
annotator.add(strikeout);
```

### 7. lépés: Mentés és takarítás
`dispose()` felszabadítja a `Annotator` példány által tartott natív erőforrásokat, megakadályozva a memória szivárgást a feldolgozás befejezése után.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Memory Management Note:** A `dispose()` hívása felszabadítja a natív erőforrásokat és megakadályozza a memória szivárgást PDF kötegek feldolgozásakor.

## Gyakori problémák és megoldások

### 1. probléma: “File Not Found” hibák
**Symptoms:** Kivétel dobódik a `Annotator` konstrukciója során.  
**Solution:** Ellenőrizze mind a bemeneti, mind a kimeneti útvonalakat, és győződjön meg arról, hogy az alkalmazásnak olvasási/írási jogosultsága van.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### 2. probléma: Az áthúzás a rossz helyen jelenik meg
**Symptoms:** A vonal nem illeszkedik a kívánt szöveghez.  
**Solution:** Ne feledje, hogy a PDF Y‑koordináták felfelé növekednek. Használjon vizuális hibakereső eszközt vagy nyomtassa ki az oldal méreteit a pontok finomhangolásához.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### 3. probléma: Az annotáció nem látható
**Symptoms:** Mentés után nem jelenik meg áthúzás.  
**Possible Causes & Fixes:**  
- **Opacity too low:** Ideiglenesen állítsa az átlátszatlanságot `1.0`-ra a láthatóság ellenőrzéséhez.  
- **Color blending:** Használjon nagy kontrasztú színt, például piros (`255`).  
- **Incorrect page index:** Az oldalszámok nullával kezdődnek; győződjön meg róla, hogy a megfelelő oldalt célozza.

### 4. probléma: Memória problémák nagy fájlok esetén
**Symptoms:** `OutOfMemoryError` vagy lassú teljesítmény.  
**Solutions:**  
- Dokumentumok feldolgozása kisebb kötegekben.  
- Használja a streaming API-t, ha elérhető.  
- Mindig hívja meg a `dispose()`-t minden dokumentum után.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## Valós életbeli alkalmazások és felhasználási esetek

### Jogi dokumentum felülvizsgálat
A jogi irodák szerződéseket áthúzással jelölik, hogy a törölt záradékokat mutassák, miközben megőrzik az audit nyomvonalat.

### Tudományos dolgozat szerkesztése
A professzorok áthúzást használnak a törlések javaslatára a lektorálás során, az eredeti szöveget láthatóan hagyva a kontextus érdekében.

### Tartalomkezelő rendszerek
A kiadói platformok automatikusan megjelölik a szabályzatot sértő részeket áthúzással a manuális moderálás előtt.

### Dokumentumok verziókezelése
A vállalatok az áthúzott annotációkat “törlési jelölőként” kezelik egy dokumentum‑központú verziókezelési munkafolyamatban, hasonlóan a kóddiffekhez.

## Teljesítményoptimalizálási tippek

### Kötetes feldolgozási stratégia
Sok PDF kezelésekor, ahol lehetséges, használja újra egyetlen `Annotator` példányt, és a fájlokat párhuzamos szálakban dolgozza fel.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### Memóriakezelési legjobb gyakorlatok
- Hívja meg a `dispose()`-t minden `Annotator` esetén.  
- Korlátozza a párhuzamos dokumentum betöltéseket a heap nyomás elkerülése érdekében.  
- Figyelje a JVM memóriahasználatát olyan eszközökkel, mint a VisualVM.

### Koordináta gyorsítótárazás
Ha ugyanazt az annotációs elrendezést több fájlra alkalmazza, gyorsítótárazza a `Point` objektumokat a újraszámítás elkerülése érdekében.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## Haladó testreszabási lehetőségek

### Dinamikus színválasztás
Válasszon színeket futásidőben az üzleti szabályok alapján (pl. piros kritikus törlésekhez, sárga a bizonytalanokhoz).

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

### Többsoros áthúzások
Hozzon létre egy sor `Point` párost, hogy egy cikkcakk vonalat rajzoljon, amely több szövegsort is áthalad.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## Hibaelhárítási ellenőrzőlista
1. **Fájl jogosultságok:** Ellenőrizze az olvasási/írási hozzáférést.  
2. **Könyvtár verzió:** Győződjön meg arról, hogy támogatott GroupDocs.Annotation kiadást használ.  
3. **Licenc állapot:** Erősítse meg, hogy a licencfájl helyesen van hivatkozva.  
4. **PDF kompatibilitás:** Ellenőrizze, hogy a PDF nem sérült és a támogatott méretkorlátokon belül van.  
5. **Koordináta ellenőrzés:** Győződjön meg arról, hogy minden pont az oldal határain belül van.  
6. **Heap memória:** Növelje a JVM `-Xmx` beállítást, ha nagyon nagy fájlokat dolgoz fel.

## Gyakran Ismételt Kérdések

**Q: Áthúzhatok szöveget több soron keresztül?**  
A: Igen. Hozzon létre több `Point` objektumot, amelyek a kívánt útvonalat követik; az annotáció a megadott poliline-ot követi.

**Q: Mi történik, ha a koordinátákat az oldal határain kívül adom meg?**  
A: Az annotáció levágásra kerül, és láthatatlanná válhat. Mindig ellenőrizze a koordinátákat az oldal szélességéhez és magasságához képest.

**Q: Eltávolíthatom az áthúzott annotációkat a hozzáadásuk után?**  
A: Teljesen. Használja a `removeAnnotation` metódust az annotáció ID-jével vagy szűrje típus szerint a programozott törléshez.

**Q: Van korlátozás arra, hogy hány annotációt adhatok egyetlen PDF-hez?**  
A: A GroupDocs nem szab szigorú korlátot, de a teljesítmény romolhat több ezer annotáció után. Fontolja meg az oldalakra bontást vagy az annotációk összegzését nagyon nagy halmazok esetén.

**Q: Hogyan dolgozhatok jelszóval védett PDF-ekkel?**  
A: Adja át a jelszót a `Annotator` konstruktorának. A könyvtár a memóriában dekódolja a dokumentumot, mielőtt bármilyen annotációt alkalmazna.

**Q: Hogyan kezelhetem a különböző oldalméretű és orientációjú PDF-eket?**  
A: Szerezze meg minden oldal méreteit a `annotator.getPageInfo(pageNumber)` segítségével, és számolja ki a koordinátákat a méretekhez viszonyítva a következetes elhelyezés érdekében.

## Következtetés
Most már egy teljes, termelésre kész megoldással rendelkezik a **how to add strikeout** annotációk PDF-ekhez Java-ban a GroupDocs.Annotation használatával. A fájlútvonal-kezelés, a koordináta-számítás és az erőforrás-kezelés elsajátításával beépítheti ezt a képességet dokumentum-ellenőrző eszközökbe, tartalmi csővezetékekbe vagy bármely Java‑alapú alkalmazásba, amely pontos vizuális visszajelzést igényel.

## Következő lépések
1. Klónozza a példaprojektet, és futtassa egy mintapdf-en.  
2. Kísérletezzen különböző színekkel, átlátszatlanságokkal és megjegyzés szövegekkel.  
3. Integrálja az annotációs munkafolyamatot a meglévő dokumentumfeldolgozó szolgáltatásába.  
4. Fedezze fel a kapcsolódó annotációtípusokat—kiemelések, ragadós jegyzetek és alakzat annotációk—hogy bővítse a PDF manipulációs eszköztárát.

Készen áll a továbbiakra? Merüljön el a hivatalos dokumentációban a mélyebb API ismeretekért.

## További források
- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - Általános dokumentáció a GroupDocs könyvtárakhoz  
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - Teljes API referencia  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - Módszer‑ről‑módszer részletek  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - Tartsa naprakészen a könyvtárat  
- [Purchase License](https://purchase.groupdocs.com/buy) - Termelés‑kész licenc  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - Értékelés vásárlás előtt  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - Fejlesztői tesztelés  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - Közösségi segítség és hivatalos támogatás  

**Legutóbb frissítve:** 2026-05-21  
**Tesztelt verzió:** GroupDocs.Annotation 23.12 for Java  
**Szerző:** GroupDocs

## Kapcsolódó oktatóanyagok
- [PDF annotáció hozzáadása Java – Teljes GroupDocs útmutató](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)
- [Java PDF annotációs oktató - Teljes útmutató a PDF-ek kiemeléséhez](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)
- [Hogyan adjunk hozzá nyilat PDF-hez Java-ban – Teljes GroupDocs oktató](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)