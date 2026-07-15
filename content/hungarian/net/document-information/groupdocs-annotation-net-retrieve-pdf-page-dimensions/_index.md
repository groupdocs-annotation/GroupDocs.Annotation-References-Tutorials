---
categories:
- Document Processing
date: '2026-06-16'
description: Tanulja meg, hogyan lehet .NET-ben PDF oldalméretet lekérni a GroupDocs.Annotation
  használatával. PDF oldal szélesség és magasság kinyerése, PDF szélesség és magasság
  lekérése, valamint a C# PDF oldalméretek hatékony kezelése.
keywords: pdf page dimensions .net, groupdocs.annotation tutorial, pdf metadata extraction
  c#, .net document processing, retrieve pdf dimensions programmatically
lastmod: '2026-06-16'
linktitle: PDF oldal méretei .NET útmutató
schemas:
- author: GroupDocs
  dateModified: '2026-06-16'
  description: Learn how to get pdf page size in .NET using GroupDocs.Annotation.
    Extract pdf page width height, retrieve pdf width height, and handle c# pdf page
    dimensions efficiently.
  headline: PDF Page Dimensions .NET - Extract Width & Height with C#
  type: TechArticle
- description: Learn how to get pdf page size in .NET using GroupDocs.Annotation.
    Extract pdf page width height, retrieve pdf width height, and handle c# pdf page
    dimensions efficiently.
  name: PDF Page Dimensions .NET - Extract Width & Height with C#
  steps:
  - name: Initialize the Annotator with Your PDF
    text: Create an `Annotator` instance pointing to your PDF file. Always wrap it
      in a `using` block so the file handle is released promptly. **Pro Tip:** Proper
      disposal prevents memory leaks, especially when processing dozens of large PDFs
      in a batch job.
  - name: Retrieve Document Information
    text: '`DocumentInfo` is an object that holds overall PDF metadata such as total
      page count and a collection of `PageInfo` objects for each page. GroupDocs.Annotation
      makes metadata extraction a one‑liner: The returned `DocumentInfo` object gives
      you: - Total page count - File format details - A `Pages` li'
  - name: Validate the Retrieved Data
    text: Before you start looping over pages, confirm the document info isn’t null
      and that the page collection contains entries. This defensive check avoids null‑reference
      exceptions and provides early feedback if the PDF is corrupted.
  - name: Extract Width and Height for Each Page
    text: '`PageInfo` represents a single page’s properties, including its width,
      height, and rotation angle. Iterate through the `Pages` collection and read
      `Width` and `Height`. Remember that the values are expressed in **points** (1
      point = 1/72 inch). **Key Points** - Width appears first, then height. - Pa'
  type: HowTo
- questions:
  - answer: Yes. The free trial version supports basic dimension extraction, though
      it may impose a limit on the number of pages processed per session.
    question: Can I extract PDF page dimensions without a license?
  - answer: GroupDocs.Annotation returns dimensions in **points** (1 point = 1/72
      inch). Convert to inches by dividing by 72, or to millimeters by multiplying
      by 0.352778.
    question: What units are the width and height measurements in?
  - answer: 'Pass the password via `LoadOptions` when constructing the `Annotator`:
      `new Annotator(path, new LoadOptions { Password = "your‑password" })`.'
    question: How do I handle password‑protected PDFs?
  - answer: Yes. Download the file to a local `Stream` first, then use the stream‑based
      `Annotator` constructor to avoid intermediate files.
    question: Can this work with PDFs stored in cloud storage like Azure or AWS?
  - answer: GroupDocs.Annotation reads only the PDF’s cross‑reference table and page
      dictionaries, so most PDFs under 100 MB are processed in under 1 second on typical
      server hardware.
    question: What is the performance impact of extracting dimensions from large PDFs?
  type: FAQPage
tags:
- pdf-processing
- dotnet
- groupdocs
- document-metadata
title: PDF oldal méretei .NET - Szélesség és magasság kinyerése C#-val
type: docs
url: /hu/net/document-information/groupdocs-annotation-net-retrieve-pdf-page-dimensions/
weight: 1
---

# PDF oldal méretek .NET - Szélesség és magasság kinyerése C#-val

## Bevezetés

Valaha is küzdöttél PDF dokumentumokkal a .NET alkalmazásodban, és minden oldalra szükséged van a **get pdf page size** lekérésére? Nem vagy egyedül. Akár dokumentumnézőt építesz, nyomtatási elrendezéseket hozol létre, vagy űrlapokat dolgozol fel, a pontos oldalméretek a kifogástalan felhasználói élmény alapját képezik.

Ebben a részletes útmutatóban végigvezetünk a PDF oldalméretek kinyerésén a **GroupDocs.Annotation for .NET** segítségével — ez az egyik legmegbízhatóbb könyvtár erre a feladatra. A végére működő kódot kapsz, amely bármely PDF dokumentumból lekéri a szélességet, magasságot és egyéb fontos metaadatokat.

### Gyors válaszok
- **Hogyan kaphatom meg a pdf oldal méretét .NET-ben?** Use `Annotator.GetDocumentInfo()` and read `PageInfo.Width` / `PageInfo.Height`.
- **Melyik könyvtár támogatja a pdf oldal szélesség és magasság kinyerését?** GroupDocs.Annotation for .NET (v25.4.0+).
- **Szükségem van licencre az alapvető méretkivonáshoz?** A ingyenes próba működik; a kereskedelmi licenc szükséges a termeléshez.
- **Milyen egységekben térnek vissza az értékek?** Pontok (1/72 hüvelyk); szükség szerint átalakítható hüvelykre vagy milliméterre.
- **Hatékonyan tudok nagy PDF-eket feldolgozni?** Igen — a GroupDocs.Annotation metaadatokat olvas be anélkül, hogy a teljes fájlt a memóriába töltené.

### Mi az a **get pdf page size**?
**Get pdf page size** a PDF oldal szélességének és magasságának programozott lekérését jelenti. Ez a művelet elengedhetetlen az elrendezés számításokhoz, nyomtatási előkészítéshez és űrlapmezők pozicionálásához .NET alkalmazásokban.

## Miért fontosak a PDF oldalméretek a .NET fejlesztésben

Mielőtt belevágnánk a kódba, vizsgáljuk meg, miért fontos a **pdf page width height** ismerete. Ezek a számok nem csak apróságok — valós funkciókat hajtanak végre:

- **Elrendezéskezelés** – A reszponzív nézők automatikusan méretezhetők a pontos oldalméret alapján, kiküszöbölve a kellemetlen görgetősávokat.
- **Nyomtatás optimalizálása** – A pontos méretek megakadályozzák a papírpazarlást és a rosszul igazított nyomatokat a kereskedelmi munkafolyamatokban.
- **Űrlapfeldolgozás** – A kinyerési koordináták pontos oldalmérettől függenek; egy 2 mm hiba tönkreteheti az adatgyűjtést.
- **Erőforrás-tervezés** – Nagy, vegyes méretű PDF-ek különböző memória stratégiákat igényelnek; a méret korai ismerete okosabb kötegelt feldolgozást tesz lehetővé.

## Előfeltételek

### Szükséges könyvtárak és verziók
- **GroupDocs.Annotation for .NET** (Version 25.4.0 vagy újabb). Ez a verzió támogatja a **50+ bemeneti és kimeneti formátumot**, és képes több száz oldalas PDF-eket kezelni anélkül, hogy a teljes fájlt a memóriába töltené.
- .NET Framework 4.6.1+ **vagy** .NET Core 2.0+

### Környezet beállítási követelmények
- Visual Studio 2019 vagy újabb (a Community kiadás tökéletesen működik)
- Egy teszt PDF fájl (megmutatjuk, hogyan kezelj különböző típusokat)
- Alapvető ismeretek a `using` utasításokról és az objektumok felszabadításáról C#-ban

### Tudás előfeltételek
- C# alapok
- NuGet csomagkezelés alapjai
- Egyszerű fájl I/O .NET-ben

Minden készen van? Remek — állítsuk be a könyvtárat.

## A GroupDocs.Annotation beállítása .NET-hez

A GroupDocs.Annotation telepítése egyszerű, de több módon is megtehető a munkafolyamatodtól függően.

### 1. módszer: NuGet Package Manager Console használata
Open the Package Manager Console in Visual Studio and run:

```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```

### 2. módszer: .NET CLI használata
If you prefer command‑line tools:

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### 3. módszer: Visual Package Manager
1. Kattints jobb gombbal a projektedre a Solution Explorerben  
2. Válaszd a **Manage NuGet Packages** lehetőséget  
3. Keress rá a **GroupDocs.Annotation**-ra  
4. Kattints az **Install** gombra

#### Licencelési lehetőségek (Válaszd, ami neked megfelel)

- **Free Trial** – A fő funkciók, beleértve a méretkivonást, kisebb használati korlátokkal elérhetők — tökéletes a koncepció bizonyításához.
- **Temporary License** – Kérj egy 30‑napos ideiglenes kulcsot a teljes funkcionalitáshoz az értékelés során.
- **Commercial License** – Szükséges a termelési környezethez; az ár a fejlesztők számától és a telepítési modelltől függ.

### Gyors beállítás ellenőrzése

Here's a simple test to confirm everything is wired correctly:

```csharp
using GroupDocs.Annotation;

// This should compile without errors if installation succeeded
using (Annotator annotator = new Annotator(@"path\to\your\test.pdf"))
{
    Console.WriteLine("GroupDocs.Annotation is ready to use!");
}
```

If this compiles and runs without throwing exceptions, you’re ready to extract page sizes.

## Mi a **Annotator** osztály?

A `Annotator` osztály a GroupDocs.Annotation központi objektuma, amely egy PDF dokumentumot reprezentál a memóriában, és metódusokat biztosít a metaadatok olvasásához, annotációk hozzáadásához és oldalinformációk kinyeréséhez. Kezeli a fájlkezelést, támogatja a stream‑ből való betöltést, és biztosítja, hogy minden további művelet egy `Annotator` példányon keresztül történjen, egyszerűsítve a munkafolyamat-kezelést.

## Hogyan **get pdf page size** a GroupDocs.Annotation segítségével?

`GetDocumentInfo()` egy `DocumentInfo` objektumot ad vissza, amely az általános PDF metaadatokat tartalmazza, beleértve az oldalszámot és az oldal részleteinek gyűjteményét. Töltsd be a PDF-et a `new Annotator("file.pdf")`‑vel, és hívd meg ezt a metódust; a `Pages` gyűjteményben minden `PageInfo` tartalmazza a `Width` és `Height` értékeket. Ez a kéts lépéses megközelítés azonnal pontokban adja meg a méreteket, anélkül, hogy a teljes fájlt feldolgozná.

## Lépésről‑lépésre megvalósítási útmutató

### 1. lépés: Az Annotator inicializálása a PDF‑eddel

Create an `Annotator` instance pointing to your PDF file. Always wrap it in a `using` block so the file handle is released promptly.

```csharp
using (Annotator annotator = new Annotator(@"YOUR_DOCUMENT_DIRECTORY\INPUT_PDF"))
{
    // All our dimension extraction magic happens here
}
```

**Pro Tip:** A megfelelő felszabadítás megakadályozza a memória szivárgásokat, különösen ha tucatnyi nagy PDF-et dolgozol fel egy kötegelt feladatban.

### 2. lépés: Dokumentuminformációk lekérése

`DocumentInfo` is an object that holds overall PDF metadata such as total page count and a collection of `PageInfo` objects for each page.  

GroupDocs.Annotation makes metadata extraction a one‑liner:

```csharp
IDocumentInfo info = annotator.Document.GetDocumentInfo();
```

The returned `DocumentInfo` object gives you:
- Teljes oldalszám  
- Fájlformátum részletek  
- Egy `Pages` lista, ahol minden bejegyzés tartalmazza a szélességet, magasságot, forgatást és egyebeket

### 3. lépés: A lekért adatok ellenőrzése

Before you start looping over pages, confirm the document info isn’t null and that the page collection contains entries.

```csharp
if (info.PagesInfo != null && info.PagesInfo.Count > 0)
{
    Console.WriteLine($"\t Document info: Type {info.FileType}, size = {info.Size}, pages = {info.PageCount}");
}
else
{
    Console.WriteLine("No page information available - check your PDF file");
    return;
}
```

Ez a védelmi ellenőrzés elkerüli a null‑referencia kivételeket, és korai visszajelzést ad, ha a PDF sérült.

### 4. lépés: Szélesség és magasság kinyerése minden oldalra

`PageInfo` represents a single page’s properties, including its width, height, and rotation angle.  

Iterate through the `Pages` collection and read `Width` and `Height`. Remember that the values are expressed in **points** (1 point = 1/72 inch).

```csharp
foreach (var page in info.PagesInfo)
{
    Console.WriteLine($"\t\t page #{page.PageNumber}: {page.Width}x{page.Height}");
}
```

**Kulcsfontosságú pontok**  
- Először a szélesség, majd a magasság.  
- Az oldalszámok 1‑től kezdődnek, ahogy a felhasználók a nézőkben látják.  
- A forgatás információ is elérhető, ha koordinátákat kell módosítani.

### Teljes működő példa (metódus)

You can wrap the above steps into a reusable method:

```csharp
using GroupDocs.Annotation;
using System;

public void ExtractPdfPageDimensions(string pdfPath)
{
    try
    {
        using (Annotator annotator = new Annotator(pdfPath))
        {
            IDocumentInfo info = annotator.Document.GetDocumentInfo();
            
            if (info.PagesInfo != null && info.PagesInfo.Count > 0)
            {
                Console.WriteLine($"Document: {info.FileType}, {info.Size} bytes, {info.PageCount} pages");
                
                foreach (var page in info.PagesInfo)
                {
                    Console.WriteLine($"Page {page.PageNumber}: {page.Width} x {page.Height} points");
                }
            }
            else
            {
                Console.WriteLine("Could not retrieve page information");
            }
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error processing PDF: {ex.Message}");
    }
}
```

## Gyakori buktatók és elkerülésük módjai

Még a legegyszerűbb kóddal is a fejlesztők előre látható problémákkal szembesülnek. Az alábbiakban a leggyakoribb csapdákat és bevált megoldásokat mutatjuk be.

### Fájlútvonal problémák
**Probléma:** “File not found” hibák fejlesztés közben.  
**Megoldás:** Használj abszolút útvonalakat teszteléskor, és mindig ellenőrizd, hogy a fájl létezik-e a `Annotator` létrehozása előtt.

```csharp
if (!File.Exists(pdfPath))
{
    throw new FileNotFoundException($"PDF file not found: {pdfPath}");
}
```

### Jogosultsági problémák
**Probléma:** Az alkalmazásnak nincs olvasási joga a PDF fájlhoz, különösen webkiszolgálókon.  
**Megoldás:** Adj megfelelő olvasási jogosultságot az alkalmazás pool identitásnak, vagy használj impersonation‑t a korlátozott mappákhoz.

### Sérült PDF kezelése
**Probléma:** Egyes PDF-ek részben sérültek vagy nem szabványos funkciókat használnak.  
**Megoldás:** Tedd a kinyerési logikát `try‑catch` blokkba, és jeleníts meg egyértelmű hibaüzenetet. A GroupDocs.Annotation `DocumentException`‑t dob a nem támogatott struktúrák esetén.

### Memóriaszivárgás nagy fájlok esetén
**Probléma:** Sok nagy PDF feldolgozása a `Annotator` példányok felszabadítása nélkül memóriahiányhoz vezet.  
**Megoldás:** Mindig használj `using` utasításokat, és fontold meg a fájlok kisebb kötegekben vagy streaming módban történő feldolgozását.

### Verziókompatibilitás
**Probléma:** Különböző GroupDocs könyvtárverziók keverése típuseltéréseket okozhat.  
**Megoldás:** Egységesíts egyetlen verziót a megoldásban, és frissítsd együtt az összes kapcsolódó csomagot.

## Valós‑világos alkalmazások

A **retrieve pdf width height** megértése erőteljes forgatókönyveket nyit meg:

### Dokumentumnéző alkalmazások
A reszponzív nézők automatikusan beállíthatják a kezdeti zoom szintet az oldalméretek alapján, így “képernyőhöz illesztett” élményt nyújtanak manuális beállítás nélkül.

```csharp
// Example: Calculate optimal zoom for viewport
double optimalZoom = Math.Min(viewportWidth / pageWidth, viewportHeight / pageHeight);
```

### Automatizált jelentéskészítés
Több PDF egy jelentésbe való egyesítésekor az egyes oldalak méretének ismerete biztosítja a konzisztens méretezést és elkerüli a váratlan oldaltöréseket.

### Nyomtatáskezelő rendszerek
A pontos méretek lehetővé teszik az optimális papírhasználat kiszámítását, a portré‑ és tájkép‑orientáció felismerését, valamint a dokumentumok előellenőrzését a kereskedelmi nyomtatókba küldés előtt.

### Űrlapfeldolgozó megoldások
Az oldalméretből származó pontos koordináták megbízható kinyerést tesznek lehetővé a jelölőnégyzetek, aláírások és szövegmezők számára különböző elrendezésű PDF-ekben.

### Digitális eszközkezelés
Címkézd a PDF-eket méret metaadatokkal a gyors keresések (pl. „mutasd az összes A4‑méretű dokumentumot”) megkönnyítése és a katalógus hatékonyságának javítása érdekében.

## Teljesítményoptimalizálási tippek

Amikor a prototípusról a termelésre lépsz, a teljesítmény kritikus lesz.

### Kötegelt feldolgozási stratégia
Csoportosíts hasonló műveleteket a terhelés csökkentése érdekében. Például olvasd be a metaadatokat egy fájlköteghez, tárold az eredményeket, majd a második átfutásban dolgozd fel az annotációkat.

```csharp
var results = new List<PageDimensionResult>();
foreach (var pdfFile in pdfFiles.Take(10)) // Process in batches of 10
{
    // Extract dimensions and add to results
}
```

### Gyakran elérhető méretek gyorsítótárazása
Ha ugyanazokat a PDF-eket többször lekérdezik, gyorsítótárazd a `DocumentInfo` objektumaikat egy szálbiztos szótárban. Ne felejtsd el érvényteleníteni a gyorsítótárat, ha a forrásfájl változik.

```csharp
private static readonly Dictionary<string, IDocumentInfo> _dimensionCache = 
    new Dictionary<string, IDocumentInfo>();
```

### Aszinkron feldolgozás nagy fájlokhoz
Használd az `async/await` mintákat, hogy a UI szálak reagálóképesek maradjanak, miközben a GroupDocs.Annotation a háttérben metaadatokat olvas.

```csharp
public async Task<List<PageInfo>> ExtractDimensionsAsync(string pdfPath)
{
    return await Task.Run(() => {
        // Your dimension extraction code here
    });
}
```

### Memóriakezelési legjobb gyakorlatok
- Minden `Annotator` példányt azonnal szabadíts fel.  
- Nagy gyűjteményeket dolgozz fel 20–50 fájlos adagokban a memóriahasználat alacsonyan tartása érdekében.  
- Figyeld a memóriahasználatot teljesítménymérőkkel vagy profilozó eszközökkel.  
- Használj gyenge referenciákat a gyorsítótárazott objektumokhoz, ha nagy forgási gyakoriságra számítasz.

## Haladó felhasználási esetek

Miután magabiztos vagy az alapvető kinyerésben, fedezd fel ezeket a kifinomult forgatókönyveket.

### Vegyes méretű dokumentumok kezelése
Néhány PDF különböző méretű oldalakat tartalmaz (pl. A4 borítóoldal, majd A5 belső oldalak). Észleld a méretváltozásokat egymást követő `PageInfo.Width`/`Height` értékek összehasonlításával, és alkalmazz feltételes logikát.

```csharp
var pageSizes = info.PagesInfo.Select(p => new { p.PageNumber, p.Width, p.Height }).ToList();
var uniqueSizes = pageSizes.Select(p => new { p.Width, p.Height }).Distinct().Count();

if (uniqueSizes > 1)
{
    Console.WriteLine("Document contains multiple page sizes");
}
```

### Orientáció felismerése
Határozd meg a portré vagy tájkép orientációt a szélesség és magasság összehasonlításával. Ez hasznos az oldalak automatikus forgatásához a nézőkben vagy orientáció‑érzékeny bélyegképek generálásához.

```csharp
foreach (var page in info.PagesInfo)
{
    string orientation = page.Width > page.Height ? "Landscape" : "Portrait";
    Console.WriteLine($"Page {page.PageNumber}: {orientation}");
}
```

### Integráció más GroupDocs funkciókkal
Kombináld a méretkivonást az annotációs API‑kkal a pecsétek pontos elhelyezéséhez, vagy a konverziós API‑kkal, hogy olyan képeket generálj, amelyek tiszteletben tartják az eredeti oldalméretet.

## Gyakran Ismételt Kérdések

**Q: Kinyerhetem a PDF oldalméreteket licenc nélkül?**  
A: Igen. Az ingyenes próba verzió támogatja az alapvető méretkivonást, bár korlátozhatja a munkamenetenként feldolgozott oldalak számát.

**Q: Milyen egységekben vannak a szélesség és magasság mérések?**  
A: A GroupDocs.Annotation **pontokban** adja vissza a méreteket (1 pont = 1/72 hüvelyk). Átalakítható hüvelykre a 72‑el való osztással, vagy milliméterre a 0,352778‑mal való szorzással.

**Q: Hogyan kezelem a jelszóval védett PDF-eket?**  
A: Add meg a jelszót a `LoadOptions`‑on keresztül az `Annotator` létrehozásakor: `new Annotator(path, new LoadOptions { Password = "your‑password" })`.

**Q: Működik ez felhőben tárolt PDF-ekkel, például Azure vagy AWS?**  
A: Igen. Először töltsd le a fájlt egy helyi `Stream`‑be, majd használd a stream‑alapú `Annotator` konstruktort, hogy elkerüld a köztes fájlokat.

**Q: Milyen teljesítményhatása van a méretek kinyerésének nagy PDF-ekből?**  
A: A GroupDocs.Annotation csak a PDF keresztreferencia‑tábláját és oldal‑szótárát olvassa, így a legtöbb, 100 MB alatti PDF kevesebb, mint 1 másodperc alatt feldolgozható egy tipikus szerver hardveren.

**Q: Hogyan kezelem a forgatott oldalú PDF-eket?**  
A: A `PageInfo.Rotation` tulajdonság a forgatási szöget jelzi. Ha egy oldal 90° vagy 270°-ra van forgatva, cseréld fel a szélesség és magasság értékeket a megjelenített méretekhez.

**Q: Kinyerhetem a méreteket csak bizonyos oldalakból?**  
A: Igen. A `GetDocumentInfo()` meghívása után szűrd a `Pages` gyűjteményt `PageNumber` alapján, hogy egyedi oldalakat célozz meg.

**Q: Működik ez PDF/A formátumú dokumentumokkal?**  
A: Teljesen. A GroupDocs.Annotation teljes mértékben támogatja a PDF/A‑1, PDF/A‑2 és PDF/A‑3 szabványokat.

**Q: Hogyan hárítsam el a “Unable to load document” hibákat?**  
A: Ellenőrizd a fájl jogosultságait, győződj meg róla, hogy a fájl nem sérült egy PDF‑olvasóval, és erősítsd meg, hogy támogatott PDF verziót (1.4–2.0) használsz.

**Q: Kaphatok méreteket pixelben a pontok helyett?**  
A: Kézzel konvertálhatod: `pixels = points * DPI / 72`. Tipikus 96 DPI‑nél a pontokat szorozd 1.3333‑mal.

## Alapvető erőforrások

- **Dokumentáció**: [GroupDocs Annotation Documentation](https://docs.groupdocs.com/annotation/net/)
- **API referencia**: [GroupDocs Annotation API Reference](https://reference.groupdocs.com/annotation/net/)
- **Letöltés**: [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/)
- **Vásárlás**: [Buy GroupDocs](https://purchase.groupdocs.com/buy)
- **Ingyenes próba**: [Try Free Version](https://releases.groupdocs.com/annotation/net/)
- **Ideiglenes licenc**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Támogatás**: [GroupDocs Forum](https://forum.groupdocs.com/c/annotation/)

**Utolsó frissítés:** 2026-06-16  
**Tesztelve:** GroupDocs.Annotation 25.4.0 for .NET  
**Szerző:** GroupDocs

## Kapcsolódó oktatóanyagok

- [Dokumentum metaadatok kinyerése .NET - Teljes útmutató a GroupDocs.Annotation-hoz](/annotation/net/document-information/)
- [PDF betöltése URL‑ről .NET - Teljes útmutató a GroupDocs.Annotation segítségével](/annotation/net/document-loading-essentials/load-document-from-url/)
- [Dokumentum előnézet generálása .NET - Teljes útmutató a GroupDocs.Annotation segítségével](/annotation/net/advanced-usage/generate-document-pages-preview/)