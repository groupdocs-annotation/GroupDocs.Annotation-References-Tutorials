---
categories:
- Document Processing
date: '2026-06-01'
description: Ismerje meg, hogyan lehet kinyerni a c# pdf oldalszámot, lekérdezni a
  fájltípust, és elolvasni a fájl tulajdonságait c#-ban a GroupDocs.Annotation .NET
  használatával. Gyakorlati kódot és tippeket tartalmaz.
keywords:
- c# pdf page count
- c# get file type
- read file properties c#
- c# read document size
lastmod: '2026-06-01'
linktitle: Dokumentum információk kinyerése C#
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract c# pdf page count, get file type, and read file
    properties c# using GroupDocs.Annotation .NET. Includes practical code and tips.
  headline: c# pdf page count – Extract Document Info with GroupDocs
  type: TechArticle
- description: Learn how to extract c# pdf page count, get file type, and read file
    properties c# using GroupDocs.Annotation .NET. Includes practical code and tips.
  name: c# pdf page count – Extract Document Info with GroupDocs
  steps:
  - name: '**Start with the Free Trial**: Download from the [GroupDocs website](https://releases.groupdocs.com/annotation/net/)
      – no strings attached.'
    text: '**Start with the Free Trial**: Download from the [GroupDocs website](https://releases.groupdocs.com/annotation/net/)
      – no strings attached.'
  - name: '**Need More Time?** Get a [temporary license](https://purchase.groupdocs.com/temporary-license/)
      for extended evaluation.'
    text: '**Need More Time?** Get a [temporary license](https://purchase.groupdocs.com/temporary-license/)
      for extended evaluation.'
  - name: '**Ready to Go Live?** [Purchase a full license](https://purchase.groupdocs.com/buy)
      when you''re ready to deploy.'
    text: '**Ready to Go Live?** [Purchase a full license](https://purchase.groupdocs.com/buy)
      when you''re ready to deploy.'
  - name: Clone the sample project and run the provided placeholders with real files.
    text: Clone the sample project and run the provided placeholders with real files.
  - name: Explore additional GroupDocs.Annotation features like annotation rendering
      and document comparison.
    text: Explore additional GroupDocs.Annotation features like annotation rendering
      and document comparison.
  - name: Integrate the metadata extraction into your existing upload pipeline to
      automate classification and validation.
    text: Integrate the metadata extraction into your existing upload pipeline to
      automate classification and validation.
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation supports over 50 document formats, including PDF,
      DOCX, XLSX, PPTX, JPEG, PNG, TIFF, CAD files, and many more.
    question: What document formats does GroupDocs.Annotation support for information
      extraction?
  - answer: '`GetDocumentInfo()` provides core metadata like file type, page count,
      and size. For custom properties such as author or creation date, combine GroupDocs.Annotation
      with GroupDocs.Metadata or use the native file format’s property APIs.'
    question: Can I extract custom metadata or properties from documents?
  - answer: Provide the password when creating the `Annotator` instance, e.g., `new
      Annotator("secure.pdf", new LoadOptions { Password = "pwd" })`.
    question: How do I handle password‑protected documents?
  - answer: Yes—`GetDocumentInfo()` reads only the file header, so memory consumption
      stays low even for multi‑hundred‑page PDFs.
    question: Is there a way to extract document information without loading the entire
      file into memory?
  - answer: Absolutely. GroupDocs.Annotation is thread‑safe; just create a new `Annotator`
      per request and dispose of it promptly.
    question: Can I use this in a web application or multi‑threaded environment?
  type: FAQPage
tags:
- csharp
- document-extraction
- groupdocs
- dotnet
title: c# pdf oldalszám – Dokumentum információk kinyerése a GroupDocs segítségével
type: docs
url: /hu/net/annotation-management/mastering-document-extraction-groupdocs-annotation-net/
weight: 1
---

# c# pdf oldal szám – Dokumentum információk kinyerése a GroupDocs.Annotation segítségével

## Bevezetés

Volt már olyan helyzet, amikor egy halom dokumentumra bámult, és arra gondolt, mi is van bennük anélkül, hogy mindegyiket megnyitná? Biztosan nem vagy egyedül ebben a küzdelemben. Akár dokumentumkezelő rendszert építesz, jogi fájlokat dolgozol fel, vagy csak a vállalat digitális eszközeit próbálod rendszerezni, a **C#-ban dokumentum információk kinyerése** – beleértve a **c# pdf oldal szám** – valóban forradalmi lehet.

Manuális fájltulajdonság-ellenőrzés időigényes és hibára hajlamos. A **GroupDocs.Annotation for .NET** segítségével automatizálhatod ezt a folyamatot, és néhány kódsorral lekérheted a fájltípust, az oldal számot, a dokumentum méretét és egyebeket. Ez az útmutató bemutatja, miért fontos, hogyan állítsd be a könyvtárat, és lépésről‑lépésre kódot, amely azonnal működik.

## Gyors válaszok
- **Mi a GroupDocs.Annotation által kinyert?** Fájltípus, oldal szám, méret és alap metaadatok.  
- **Hány formátumot támogat?** Több mint 50 bemeneti és kimeneti formátum, beleértve a PDF, DOCX, XLSX, PPTX és a gyakori képformátumok.  
- **Kaphatok c# pdf oldal számot a teljes fájl betöltése nélkül?** Igen – a `GetDocumentInfo()` csak a fejlécinformációt olvassa, amely az oldal számhoz szükséges.  
- **Szükség van licencre fejlesztéshez?** Az ingyenes próba verzió teszteléshez elegendő; a teljes licenc a termeléshez kötelező.  
- **Az API szálbiztos webalkalmazásokhoz?** Teljesen – csak megfelelően szabadítsd fel a `Annotator` példányokat.

## Mi az a c# pdf oldal szám?
A **c# pdf page count** a PDF-fájl által jelentett összes oldal száma, amikor egy API‑val lekérdezik. A GroupDocs.Annotation használatával ezt az értéket azonnal megkapod a `GetDocumentInfo()` metódussal anélkül, hogy a teljes dokumentumot renderelnéd. Ez a szám a PDF belső struktúrájából származik, lehetővé téve a feldolgozási, tárolási vagy megjelenítési döntések meghozatalát a fájl megnyitása nélkül. Különösen hasznos kötegelt validációhoz, megfelelőségi ellenőrzésekhez és UI előnézetekhez, ahol az oldalszám korlátozása fontos.

## Miért érdemes dokumentum információkat kinyerni a GroupDocs.Annotation segítségével?
A GroupDocs.Annotation **50+ dokumentumformátumot** támogat, és több száz oldalas fájlokat is képes feldolgozni anélkül, hogy a teljes fájlt a memóriába töltené, metaadatokat szállítva tipikusan 200 ms alatt egy átlagos szerveren. Ez a sebesség és a formátumok széles köre ideálissá teszi nagy léptékű automatizáláshoz, megfelelőségi ellenőrzésekhez és intelligens tartalom osztályozáshoz.

## Előkövetelmények és beállítás

### Amire szükséged lesz
- Visual Studio 2019 vagy újabb (a Community kiadás is megfelelő)  
- .NET Framework 4.6.1+ **vagy** .NET Core 2.0+  
- Alap C# ismeretek és a NuGet használatának ismerete  

### A GroupDocs.Annotation telepítése
A könyvtár projektbe való beillesztése egyszerű. Válaszd ki a számodra kedves módszert:

**1. opció: Package Manager Console (Ajánlott)**
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**2. opció: .NET CLI**
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

**3. opció: Package Manager UI**  
Ha inkább kattintani szeretnél a gépelés helyett, keresd meg a "GroupDocs.Annotation" kifejezést a NuGet Package Manager UI-ban, és telepítsd a legújabb verziót.

### Licenc beszerzése
1. **Kezdd az ingyenes próba verzióval**: Töltsd le a [GroupDocs weboldalról](https://releases.groupdocs.com/annotation/net/) – semmilyen kötelezettség nélkül.  
2. **További időre van szükséged?** Szerezz egy [ideiglenes licencet](https://purchase.groupdocs.com/temporary-license/) a meghosszabbított értékeléshez.  
3. **Készen állsz a bevetésre?** [Vásárolj teljes licencet](https://purchase.groupdocs.com/buy), amikor készen állsz a telepítésre.  

> **Pro tipp:** Az ingyenes próba verzió vízjeleket tartalmaz, de tökéletes a kód tanulásához és teszteléséhez.

A legújabb változásokért lásd a [kiadási megjegyzéseket](https://releases.groupdocs.com/annotation/net/).

## Hogyan szerezhetünk c# pdf oldal számot a GroupDocs.Annotation segítségével?
**Annotator** a fő osztály, amely betölti a dokumentumot és annotációs és metaadat funkciókat biztosít.  
Töltsd be a PDF-et a `new Annotator("file.pdf")` paranccsal, és hívd meg a `GetDocumentInfo()`‑t – a `PageCount` tulajdonság pontosan visszaadja az oldalak számát mindössze két kódsorban. **GetDocumentInfo()** egy **DocumentInfo** objektumot ad vissza, amely metaadatokat tartalmaz, mint például az oldalszám, a fájltípus és a méret. Ez a metódus csak a szükséges fejlécadatokat olvassa, így még a nagy PDF-eket is hatékonyan kezeli.

### Alap beállítás és dokumentum betöltése
```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main(string[] args)
    {
        // Initialize the annotator with a document path
        using (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf"))
        {
            Console.WriteLine("Document loaded successfully!");
            // We'll add the extraction code here next
        }
    }
}
```  

### Dokumentum metaadatok kinyerése
**DocumentInfo** tartalmazza a fájl kinyert tulajdonságait, megkönnyítve azok olvasását és alkalmazásban való használatát.  
```csharp
using (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf"))
{
    // Extract document info
    IDocumentInfo info = annotator.Document.GetDocumentInfo();
    
    // Always check if info was retrieved successfully
    if (info == null || info.PageCount == 0)
    {
        throw new Exception("Unexpected document information!");
    }

    // Display the extracted information
    Console.WriteLine($"\
File type: {info.FileType}\
Number of pages: {info.PageCount}\
Document size: {info.Size} bytes.");
    
    // Convert size to more readable format
    string readableSize = FormatFileSize(info.Size);
    Console.WriteLine($"Document size (formatted): {readableSize}");
}

// Helper method to format file size
static string FormatFileSize(long bytes)
{
    string[] suffixes = { "B", "KB", "MB", "GB", "TB" };
    int counter = 0;
    decimal number = bytes;
    
    while (Math.Round(number / 1024) >= 1)
    {
        number /= 1024;
        counter++;
    }
    
    return string.Format("{0:n1}{1}", number, suffixes[counter]);
}
```  

### Bővített információ megjelenítés
Ha több kontextusra van szükséged – például arra, hogy a dokumentum meghaladja-e a méretküszöböt – kiterjesztheted az alap példát további ellenőrzésekkel és üzleti logikával.  
```csharp
using (Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf"))
{
    IDocumentInfo info = annotator.Document.GetDocumentInfo();
    
    if (info == null)
    {
        Console.WriteLine("Could not retrieve document information.");
        return;
    }

    // Comprehensive info display
    Console.WriteLine("=== Document Information ===");
    Console.WriteLine($"File Type: {info.FileType}");
    Console.WriteLine($"Page Count: {info.PageCount}");
    Console.WriteLine($"Size: {FormatFileSize(info.Size)}");
    
    // Additional checks you might want to perform
    if (info.PageCount > 100)
    {
        Console.WriteLine("⚠️  Large document detected - consider batch processing");
    }
    
    if (info.Size > 10 * 1024 * 1024) // 10MB
    {
        Console.WriteLine("⚠️  Large file size - may impact processing time");
    }
    
    Console.WriteLine("=== Analysis Complete ===");
}
```  

## Gyakori problémák és megoldások

### Probléma 1: „File Not Found” hibák
**Közvetlen válasz:** Ellenőrizd, hogy a fájl útvonala abszolút vagy helyesen gyökerezik-e az alkalmazás alapkönyvtárához, és hogy a folyamatnak van‑e olvasási joga.  
```csharp
string documentPath = @"C:\Documents\test.pdf";

// Always check if file exists first
if (!File.Exists(documentPath))
{
    Console.WriteLine($"File not found: {documentPath}");
    return;
}

try
{
    using (Annotator annotator = new Annotator(documentPath))
    {
        // Your code here
    }
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```  

### Probléma 2: Nem támogatott fájlformátum
**Közvetlen válasz:** Győződj meg arról, hogy a fájl kiterjesztése egyezik a 50+ támogatott formátum egyikével; ha nem, konvertáld egy támogatott típusra a `GetDocumentInfo()` hívása előtt.  
```csharp
try
{
    using (Annotator annotator = new Annotator(documentPath))
    {
        IDocumentInfo info = annotator.Document.GetDocumentInfo();
        
        if (info == null)
        {
            Console.WriteLine("Unsupported file format or corrupted document");
            return;
        }
        
        // Process the info
    }
}
catch (UnsupportedFileTypeException ex)
{
    Console.WriteLine($"File type not supported: {ex.Message}");
}
```  

### Probléma 3: Memória problémák nagy dokumentumokkal
**Közvetlen válasz:** Végezz méretellenőrzést a betöltés előtt, és használj `using` blokkokat a `Annotator` példány biztosított felszabadításához, elkerülve a memória szivárgásokat.  
```csharp
const long MAX_FILE_SIZE = 50 * 1024 * 1024; // 50MB limit

FileInfo fileInfo = new FileInfo(documentPath);
if (fileInfo.Length > MAX_FILE_SIZE)
{
    Console.WriteLine("File too large for processing");
    return;
}

// Use proper disposal patterns
using (Annotator annotator = new Annotator(documentPath))
{
    // Process quickly and dispose
    IDocumentInfo info = annotator.Document.GetDocumentInfo();
    // Handle info immediately
}
// Annotator is automatically disposed here
```  

## Valós példák

### Dokumentumkezelő rendszer integráció
Amikor egy felhasználó feltölt egy fájlt, először kinyerheted a metaadatait, hogy meghatározd a tárolási helyet, az indexelési stratégiát vagy a szükséges jóváhagyási munkafolyamatot.  
```csharp
public class DocumentProcessor
{
    public DocumentMetadata ProcessUpload(string filePath)
    {
        using (Annotator annotator = new Annotator(filePath))
        {
            IDocumentInfo info = annotator.Document.GetDocumentInfo();
            
            return new DocumentMetadata
            {
                FileName = Path.GetFileName(filePath),
                FileType = info.FileType.ToString(),
                PageCount = info.PageCount,
                FileSizeBytes = info.Size,
                ProcessedDate = DateTime.UtcNow,
                Category = DetermineCategory(info)
            };
        }
    }
    
    private string DetermineCategory(IDocumentInfo info)
    {
        // Business logic for automatic categorization
        if (info.FileType.ToString().Contains("Pdf"))
        {
            return info.PageCount > 20 ? "Legal Document" : "Standard Document";
        }
        
        return "Other";
    }
}
```  

### Kötegelt dokumentumelemzés
Feldolgozz egy mappát fájlokkal háttérfeladatban, naplózva minden dokumentum oldal számát és típusát jelentési célokra.  
```csharp
public void AnalyzeDocumentFolder(string folderPath)
{
    string[] supportedExtensions = { ".pdf", ".docx", ".xlsx", ".pptx" };
    
    foreach (string file in Directory.GetFiles(folderPath))
    {
        if (!supportedExtensions.Contains(Path.GetExtension(file).ToLower()))
            continue;
            
        try
        {
            using (Annotator annotator = new Annotator(file))
            {
                IDocumentInfo info = annotator.Document.GetDocumentInfo();
                Console.WriteLine($"{Path.GetFileName(file)}: {info.FileType}, {info.PageCount} pages");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to process {file}: {ex.Message}");
        }
    }
}
```  

### Megfelelőség és validáció
A szabályozott iparágak gyakran megkövetelik, hogy a dokumentumok egy bizonyos oldalszám vagy méret alatt legyenek. Használd a kinyert metaadatokat a nem megfelelőséget mutató feltöltések automatikus elutasításához.  
```csharp
public bool ValidateDocument(string filePath, DocumentRequirements requirements)
{
    using (Annotator annotator = new Annotator(filePath))
    {
        IDocumentInfo info = annotator.Document.GetDocumentInfo();
        
        // Check file type
        if (requirements.AllowedTypes != null && 
            !requirements.AllowedTypes.Contains(info.FileType.ToString()))
        {
            return false;
        }
        
        // Check page count limits
        if (info.PageCount < requirements.MinPages || 
            info.PageCount > requirements.MaxPages)
        {
            return false;
        }
        
        // Check file size
        if (info.Size > requirements.MaxSizeBytes)
        {
            return false;
        }
        
        return true;
    }
}
```  

## Teljesítményoptimalizálási tippek

### 1. Gyorsítótár implementálása
```csharp
private static readonly Dictionary<string, IDocumentInfo> _infoCache = 
    new Dictionary<string, IDocumentInfo>();

public IDocumentInfo GetDocumentInfoCached(string filePath)
{
    string fileHash = GetFileHash(filePath);
    
    if (_infoCache.ContainsKey(fileHash))
    {
        return _infoCache[fileHash];
    }
    
    using (Annotator annotator = new Annotator(filePath))
    {
        IDocumentInfo info = annotator.Document.GetDocumentInfo();
        _infoCache[fileHash] = info;
        return info;
    }
}
```  

### 2. Aszinkron feldolgozás használata több dokumentumhoz
```csharp
public async Task<List<DocumentMetadata>> ProcessDocumentsAsync(string[] filePaths)
{
    var tasks = filePaths.Select(async path =>
    {
        return await Task.Run(() =>
        {
            using (Annotator annotator = new Annotator(path))
            {
                IDocumentInfo info = annotator.Document.GetDocumentInfo();
                return new DocumentMetadata(path, info);
            }
        });
    });
    
    return (await Task.WhenAll(tasks)).ToList();
}
```  

### 3. Memóriakezelési legjobb gyakorlatok
- Mindig `using` blokkba helyezd a `Annotator`‑t.  
- Dokumentumokat kötegekben dolgozd fel, ne egyszerre mindet.  
- 100 MB‑nál nagyobb fájlok esetén fontold meg a fájl először lemezre streamelését, majd a metaadatok olvasását.  

## Hibakeresési útmutató

### Licenchez kapcsolódó problémák
**License** az az objektum, amely regisztrálja a termék aktiválási fájlját a GroupDocs könyvtárral. Győződj meg arról, hogy a licencfájl az alkalmazás gyökérkönyvtárában van, és hogy a `License` objektum a többi GroupDocs hívás előtt példányosítva van.  
```csharp
// Set license before using any GroupDocs functionality
License license = new License();
license.SetLicense("path/to/your/license.lic");

// Or use stream for embedded licenses
using (Stream stream = Assembly.GetExecutingAssembly().GetManifestResourceStream("YourApp.license.lic"))
{
    license.SetLicense(stream);
}
```  

### Teljesítményproblémák
**Közvetlen válasz:** Profilozd az alkalmazást, korlátozd a fájlméreteket 100 MB‑ra a valós idejű feldolgozáshoz, és engedélyezd a gyorsítótárat az ismételt olvasásokhoz.  

### Platform‑specifikus problémák
**Közvetlen válasz:** Használd a `Path.Combine`‑t a platformok közötti útvonalak építéséhez; Windows visszafelé perjeleket, Linux pedig előre perjeleket használ.  
```csharp
// Use Path.Combine for cross-platform compatibility
string documentPath = Path.Combine(baseDirectory, "documents", fileName);
```  

### Jelszóval védett dokumentumok kezelése
**Közvetlen válasz:** Add meg a jelszót a `Annotator` konstruktorban vagy állítsd be a `LoadOptions`‑on keresztül a `GetDocumentInfo()` hívása előtt.  
```csharp
LoadOptions loadOptions = new LoadOptions() { Password = "your-password" };
using (Annotator annotator = new Annotator("protected-document.pdf", loadOptions))
{
    // Extract information normally
}
```  

### GroupDocs.Annotation frissítése
**Közvetlen válasz:** Futtasd a `dotnet add package GroupDocs.Annotation --version <latest>` parancsot, vagy használd a NuGet Package Manager UI‑t a legújabb verzió letöltéséhez.  
```shell
Update-Package GroupDocs.Annotation
```  

## Gyakran feltett kérdések

**K: Milyen dokumentumformátumokat támogat a GroupDocs.Annotation információk kinyerésére?**  
V: A GroupDocs.Annotation több mint 50 dokumentumformátumot támogat, beleértve a PDF, DOCX, XLSX, PPTX, JPEG, PNG, TIFF, CAD fájlokat és még sok mást.

**K: Kinyerhetek egyedi metaadatokat vagy tulajdonságokat a dokumentumokból?**  
V: A `GetDocumentInfo()` alap metaadatokat biztosít, mint a fájltípus, oldalszám és méret. Egyedi tulajdonságok, például szerző vagy létrehozási dátum esetén kombináld a GroupDocs.Annotation‑t a GroupDocs.Metadata‑val, vagy használd a natív fájlformátum tulajdonság API‑kat.

**K: Hogyan kezelem a jelszóval védett dokumentumokat?**  
V: Add meg a jelszót a `Annotator` példány létrehozásakor, például `new Annotator("secure.pdf", new LoadOptions { Password = "pwd" })`.

**K: Van mód dokumentum információk kinyerésére a teljes fájl memóriába töltése nélkül?**  
V: Igen – a `GetDocumentInfo()` csak a fájl fejlécét olvassa, így a memóriahasználat alacsony marad még több száz oldalas PDF-ek esetén is.

**K: Használhatom ezt webalkalmazásban vagy több szálas környezetben?**  
V: Teljesen. A GroupDocs.Annotation szálbiztos; csak kérésenként hozz létre egy új `Annotator`‑t, és gyorsan szabadítsd fel.

## Összegzés és következő lépések

Most már egy teljes, termelésre kész megközelítést birtokolsz a **c# pdf oldal szám**, a fájltípus és a méret kinyerésére a GroupDocs.Annotation segítségével. Megtanultad, hogyan állítsd be a könyvtárat, hogyan szerezd meg a metaadatokat, kezeld a gyakori buktatókat, és optimalizáld a teljesítményt nagy‑léptékű forgatókönyvekhez.

**Következő lépések:**  
1. Klónozd a mintaprojektet, és futtasd a megadott helyettesítőket valós fájlokkal.  
2. Fedezd fel a GroupDocs.Annotation további funkcióit, például az annotáció renderelést és a dokumentum összehasonlítást.  
3. Integráld a metaadat kinyerést a meglévő feltöltési folyamatodba az automatikus osztályozás és validáció érdekében.

Ne feledd, a megbízható dokumentumfeldolgozás a stabil metaadatokkal kezdődik. A GroupDocs.Annotation segítségével okosabb, gyorsabb és skálázhatóbb megoldásokat építhetsz.

---

**Legutóbb frissítve:** 2026-06-01  
**Tesztelve a következővel:** GroupDocs.Annotation 25.4.0 (latest)  
**Szerző:** GroupDocs  

**Alapvető hivatkozások:**  
- **[Dokumentáció](https://docs.groupdocs.com/annotation/net/)**  
- **[API Reference](https://reference.groupdocs.com/annotation/net/)**  
- **[Download Latest Version](https://releases.groupdocs.com/annotation/net/)**  
- **[Purchase Licenses](https://purchase.groupdocs.com/buy)**  
- **[Free Trial Download](https://releases.groupdocs.com/annotation/net/)**  
- **[Temporary License Request](https://purchase.groupdocs.com/temporary-license/)**  
- **[Community Support Forum](https://forum.groupdocs.com/c/annotation/)**  

## Kapcsolódó oktatóanyagok

- **[Dokumentum metaadat kinyerés .NET – Teljes útmutató a GroupDocs.Annotation-hoz](/annotation/net/document-information/)**  
- **[PDF oldal méretek .NET – Szélesség és magasság kinyerése C#-val](/annotation/net/document-information/groupdocs-annotation-net-retrieve-pdf-page-dimensions/)**  
- **[GroupDocs.Annotation .NET oktatóanyag: Specifikus PDF oldalak kinyerése és mentése](/annotation/net/annotation-management/groupdocs-annotation-dotnet-page-range-management/)**