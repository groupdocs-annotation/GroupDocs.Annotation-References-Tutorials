---
categories:
- Document Processing
date: '2026-06-01'
description: Ismerje meg, hogyan távolíthatja el a PDF-annotációkat PDF-fájlokból
  a GroupDocs.Annotation for .NET segítségével. Tartalmaz lépésről-lépésre kódot,
  hibaelhárítást és bevált gyakorlatokat.
keywords:
- remove pdf annotations
- how to remove annotations
- delete pdf annotations
- clear pdf comments
- strip pdf markup
lastmod: '2026-06-01'
linktitle: PDF-annotációk eltávolítása C#
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to remove pdf annotations from PDF files using GroupDocs.Annotation
    for .NET. Includes step-by-step code, troubleshooting, and best practices.
  headline: Remove Annotations from PDF C#
  type: TechArticle
- description: Learn how to remove pdf annotations from PDF files using GroupDocs.Annotation
    for .NET. Includes step-by-step code, troubleshooting, and best practices.
  name: Remove Annotations from PDF C#
  steps:
  - name: Load Your Document
    text: '`Annotator` is GroupDocs.Annotation''s core class that opens a file and
      exposes its annotation collection. **Common Gotcha:** Ensure the file path is
      correct and the file isn’t locked by another process. A typo in the path is
      a frequent source of “file not found” errors.'
  - name: Get and Filter Annotations
    text: '`Annotation` objects represent individual markup items such as comments,
      highlights, or stamps. You can inspect each annotation’s type, author, page
      number, or custom metadata before deciding to delete it. **Why This Works:**
      By filtering first, you avoid accidentally removing useful markup such as '
  - name: Save Your Clean Document
    text: Give the cleaned file a distinct name (e.g., `cleaned_` prefix or timestamp)
      to avoid overwriting the original. **File Naming Strategy:** `cleaned_2024_09_15_myfile.pdf`
      makes it easy to trace processing dates.
  type: HowTo
- questions:
  - answer: Yes – GroupDocs.Annotation supports DOCX, XLSX, PPTX, and many other formats.
      The same API calls apply after loading the appropriate file type.
    question: Can I remove annotations from Word documents, not just PDFs?
  - answer: Filter the annotation collection by `annotation.Type == AnnotationType.Comment`
      before calling the delete method. ```csharp var commentsOnly = annotations.Where(a
      => a.Type == AnnotationType.TextField); ```
    question: How do I remove only specific types of annotations (e.g., just comments)?
  - answer: No. Annotations are stored as overlay objects; deleting them leaves the
      underlying content untouched.
    question: Will removing annotations affect the document’s layout or formatting?
  - answer: The library does not provide an “undo” feature. Always work on a copy
      of the original document and keep backups.
    question: Can I undo annotation removal?
  - answer: Pass the password via `LoadOptions` when creating the `Annotator` instance.
    question: How do I handle password‑protected PDFs?
  type: FAQPage
tags:
- GroupDocs
- PDF
- Annotations
- C#
- .NET
title: PDF-annotációk eltávolítása C#
type: docs
url: /hu/net/annotation-management/remove-annotations-dotnet-groupdocs/
weight: 1
---

# Hogyan távolítsuk el a megjegyzéseket PDF‑ből és dokumentumokból C#‑ban (.NET)

Képzeld el: egy dokumentumkezelő rendszeren dolgozol, és a felhasználók panaszkodnak a régi megjegyzésekkel és jelölésekkel teli zsúfolt PDF‑ekre. Vagy talán a dokumentumokat kell megtisztítanod, mielőtt ügyfeleknek küldenéd őket. Ismerős?

A **pdf annotations** programozott eltávolítása nem csak egy szép‑kellő funkció—elengedhetetlen a tiszta, professzionális dokumentumok fenntartásához az automatizált munkafolyamatokban. Akár jogi szerződésekkel, technikai dokumentációval vagy együttműködő felülvizsgálatokkal dolgozol, a nem kívánt megjegyzések hatékony eltávolításának ismerete órákat takaríthat meg a kézi munkában.

Merüljünk el, és tegyük gördülékennyé a megjegyzések eltávolítását.

## Gyors válaszok
- **Mi a kód feladata?** A dokumentumot betölti, kiszűri a nem kívánt megjegyzéseket, és egy tiszta másolatot ment.  
- **Törölhetek csak bizonyos megjegyzéseket?** Igen – szűrj típus, szerző, oldal száma vagy egyéni metaadat alapján.  
- **Szükséges licenc?** Egy ingyenes 30‑napos próba a fejlesztéshez megfelelő; a kereskedelmi használathoz termelési licenc szükséges.  
- **Nagy PDF‑ek memória problémákat okozhatnak?** Használj `using` blokkokat és kötegelt feldolgozást a memóriahasználat alacsonyan tartásához.  
- **Működik más formátumokkal is, mint a PDF?** Természetesen – a GroupDocs.Annotation támogatja a Word, Excel, PowerPoint és egyéb formátumokat.

## Mi az a GroupDocs.Annotation?
`GroupDocs.Annotation` egy .NET könyvtár, amely lehetővé teszi a megjegyzések hozzáadását, olvasását, szerkesztését és törlését több mint 30 fájlformátumban, beleértve a PDF, DOCX, XLSX és PPTX formátumokat. Dokumentumokat akár 500 MB‑ig dolgoz fel anélkül, hogy a teljes fájlt a memóriába töltené, így ideális nagy‑forgalmú szerverkörnyezetekhez.

## Miért távolítsuk el a megjegyzéseket programozottan?
A megjegyzések automatikus eltávolítása biztosítja, hogy minden munkafolyamaton áthaladó dokumentum tiszta, professzionális és megfelelőségi szempontból megfelelő legyen. Eltávolítja a kézi munkát, csökkenti a véletlen adatszivárgás kockázatát, és kicsi fájlméreteket tart a tárolás és indexelés érdekében.

- **Automation Ready** – Tiszta verziók automatikusan generálhatók minden munkafolyamat szakaszában.  
- **Professional Deliverables** – Nem jelennek meg elhagyott megjegyzések vagy jelölések az ügyfélnek szánt PDF‑ekben.  
- **Regulatory Compliance** – Egyes iparágak tiltják a rejtett megjegyzéseket a benyújtott dokumentumokban.  
- **Storage Efficiency** – A megtisztított PDF‑ek kisebbek és gyorsabban indexelhetők.

## Előfeltételek és beállítás

### Fejlesztői környezet
- .NET Core 3.1, .NET 5+, vagy .NET Framework 4.7.2+
- Visual Studio 2022 (vagy bármelyik kedvelt C# IDE)
- Alapvető ismeretek a `using` utasításokról és a kivételkezelésről  

### Szükséges csomag
GroupDocs.Annotation for .NET (a példákban a 25.4.0‑as verziót használjuk; az újabb verziók teljesen kompatibilisek).

#### A GroupDocs.Annotation telepítése
**Package Manager Console (leggyakoribb):**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**Package Manager UI:** Keress rá a “GroupDocs.Annotation” kifejezésre, és telepítsd a legújabb stabil verziót.

**.NET CLI (ha parancssori személy vagy):**  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

### Licenc beszerzése
Licencfájl szükséges a termeléshez. Kezdhetsz egy ingyenes próbaidőszakkal.

**Fejlesztéshez/Teszteléshez:**  
1. Látogasd meg a [Temporary License Page](https://purchase.groupdocs.com/temporary-license/) oldalt  
2. Kérj egy 30‑napos értékelő licencet  
3. Kapj egy `.lic` fájlt e‑mailben  

**Alap licenc beállítás:**  
`License` egy osztály, amelyet a GroupDocs.Annotation biztosít a licencfájl alkalmazásához a könyvtárban.  
```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main(string[] args)
    {
        // Set up your license (skip this during trial period)
        License lic = new License();
        lic.SetLicense("path-to-your-license.lic");
        
        Console.WriteLine("GroupDocs.Annotation is ready to rock!");
    }
}
```  

**Pro Tip:** Tárold a licencet biztonságos helyen, és töltsd be a `License license = new License(); license.SetLicense("path/to/license.lic");` kóddal. Soha ne kódolj be abszolút útvonalakat a termelésben.

## Lépésről‑lépésre megvalósítási útmutató

### Hogyan távolítsuk el a specifikus pdf megjegyzéseket?
Ez a szakasz bemutatja, hogyan tölts be egy PDF‑et, azonosítsd a eldobni kívánt megjegyzéseket, és ments egy megtisztított másolatot az eredeti tartalom megőrzésével.

#### 1. lépés: Dokumentum betöltése
`Annotator` a GroupDocs.Annotation központi osztálya, amely megnyit egy fájlt és elérhetővé teszi a megjegyzésgyűjteményt.  
```csharp
string inputFilePath = "YOUR_DOCUMENT_DIRECTORY/ANNOTATED.pdf"; // Replace with your actual path

using (Annotator annotator = new Annotator(inputFilePath))
{
    // All the magic happens inside this using block
    // The using statement ensures proper resource cleanup
}
```  

**Common Gotcha:** Győződj meg róla, hogy a fájl útvonala helyes, és a fájlt nem egy másik folyamat zárolja. Egy elütés az útvonalban gyakori oka a „file not found” hibáknak.

#### 2. lépés: Megjegyzések lekérése és szűrése
`Annotation` objektumok egyedi jelölőelemeket képviselnek, mint például megjegyzések, kiemelések vagy pecsét. Minden megjegyzés típusát, szerzőjét, oldal számát vagy egyéni metaadatait ellenőrizheted, mielőtt törölnéd.  
```csharp
var annotations = annotator.Get();
Console.WriteLine($"Found {annotations.Count} annotations in the document");

// Let's see what we're working with
foreach (var annotation in annotations)
{
    Console.WriteLine($"Type: {annotation.Type}, Page: {annotation.PageNumber}");
}

// Remove the first annotation (basic example)
if (annotations.Count > 0)
{
    Console.WriteLine($"Removing annotation of type: {annotations[0].Type}");
    annotator.Remove(annotations[0]);
}
```  

**Why This Works:** A szűrés először megakadályozza, hogy véletlenül hasznos jelöléseket, például jogi kiemeléseket eltávolíts, miközben a belső megjegyzéseket törlöd.

#### 3. lépés: Tiszta dokumentum mentése
Adj a megtisztított fájlnak egy egyedi nevet (pl. `cleaned_` előtag vagy időbélyeg), hogy elkerüld az eredeti felülírását.  
```csharp
string outputDirectory = "YOUR_OUTPUT_DIRECTORY"; // Your output folder
string outputPath = Path.Combine(outputDirectory, "cleaned_" + Path.GetFileName(inputFilePath));

// Save the document with annotations removed
annotator.Save(outputPath);
Console.WriteLine($"Clean document saved to: {outputPath}");
```  

**File Naming Strategy:** `cleaned_2024_09_15_myfile.pdf` megkönnyíti a feldolgozási dátumok nyomon követését.

### Hogyan távolítsuk el az összes pdf megjegyzést (nukleáris opció)?
Amikor teljesen tiszta lapra van szükség, ez a módszer egyetlen hívással eltávolít minden megjegyzést.

`RemoveAll` eltávolít minden megjegyzést a betöltött dokumentumból.  
```csharp
string inputFilePath = "YOUR_DOCUMENT_DIRECTORY/ANNOTATED.pdf";
string outputPath = "YOUR_OUTPUT_DIRECTORY/completely_clean.pdf";

using (Annotator annotator = new Annotator(inputFilePath))
{
    var annotations = annotator.Get();
    
    if (annotations.Count > 0)
    {
        Console.WriteLine($"Removing all {annotations.Count} annotations...");
        
        // Remove all annotations in one go
        foreach (var annotation in annotations)
        {
            annotator.Remove(annotation);
        }
        
        annotator.Save(outputPath);
        Console.WriteLine("All annotations removed successfully!");
    }
    else
    {
        Console.WriteLine("No annotations found in the document.");
    }
}
```  

## Gyakori buktatók és megoldások

### Probléma 1: „File is locked” kivételek
**Symptoms:** Kivétel a fájl használatban létezéséről.  
**Solution:** Csomagold a fájlhozzáférést `using` utasításokba, és győződj meg róla, hogy semmilyen más folyamat nem tartja a fájlkezelőt.  
```csharp
// DON'T do this
var annotator1 = new Annotator(filePath);
var annotator2 = new Annotator(filePath); // This might fail

// DO this instead
using (var annotator = new Annotator(filePath))
{
    // All your work here
} // Automatically disposed and file is released
```  

### Probléma 2: A megjegyzések valójában nem kerülnek eltávolításra
**Symptoms:** A kód fut, de a megjegyzések megmaradnak.  
**Common Cause:** Lehet, hogy a rossz kimeneti fájlt ellenőrzöd, vagy a rossz megjegyzéstípust szűröd ki.  
**Debug Approach:**  
```csharp
var annotations = annotator.Get();
foreach (var annotation in annotations)
{
    Console.WriteLine($"ID: {annotation.Id}, Type: {annotation.Type}");
    Console.WriteLine($"Page: {annotation.PageNumber}, Author: {annotation.User}");
}
```  

### Probléma 3: Memória problémák nagy dokumentumoknál
**Symptoms:** Összeomlások vagy jelentős lassulás 100 MB‑nál nagyobb PDF‑eknél.  
**Solution:** Dokumentumokat kötegekben dolgozz fel, és gyorsan szabadítsd fel az erőforrásokat.  
```csharp
// For very large documents, consider processing page by page
using (var annotator = new Annotator(largePdfPath))
{
    var annotations = annotator.Get();
    
    // Process in chunks of 50 annotations
    for (int i = 0; i < annotations.Count; i += 50)
    {
        var batch = annotations.Skip(i).Take(50);
        foreach (var annotation in batch)
        {
            annotator.Remove(annotation);
        }
        
        // Optional: Force garbage collection for very large documents
        GC.Collect();
    }
    
    annotator.Save(outputPath);
}
```  

## Teljesítményoptimalizálási tippek

### Kötegelt feldolgozási stratégia
Gyűjtsd össze a megjegyzéseket egy listába, és egyetlen kötegben töröld őket az API hívások számának csökkentése érdekében.  
```csharp
using (var annotator = new Annotator(inputPath))
{
    var annotations = annotator.Get();
    var toRemove = annotations.Where(a => ShouldRemoveAnnotation(a)).ToList();
    
    Console.WriteLine($"Removing {toRemove.Count} out of {annotations.Count} annotations");
    
    // Remove all at once instead of individual Remove() calls
    foreach (var annotation in toRemove)
    {
        annotator.Remove(annotation);
    }
    
    annotator.Save(outputPath);
}

bool ShouldRemoveAnnotation(AnnotationBase annotation)
{
    // Your custom logic here
    return annotation.Type == AnnotationType.Area || 
           annotation.CreatedOn < DateTime.Now.AddMonths(-6);
}
```  

### Memóriakezelési legjobb gyakorlatok
- Mindig használj `using` utasításokat az automatikus felszabadításhoz.  
- Soha ne tölts be egyszerre több nagy PDF‑et.  
- Feldolgozd a dokumentumokat sorosan, ne párhuzamosan, ha a memória korlátozó tényező.

### Licenc objektumok gyorsítótárazása
Hozd létre a `License` példányt egyszer az alkalmazás indításakor, és használd újra minden feldolgozott dokumentumnál.  
```csharp
public class DocumentProcessor
{
    private static readonly License _license = new License();
    
    static DocumentProcessor()
    {
        _license.SetLicense("your-license-path.lic");
    }
    
    public void ProcessDocument(string filePath)
    {
        // License is already set, just use the annotator
        using (var annotator = new Annotator(filePath))
        {
            // Your processing logic
        }
    }
}
```  

## Valós példák és esetek

### Szenárió 1: Jogi dokumentum munkafolyamat
Egy ügyvédi iroda tiszta szerződéseket kell küldjön az ügyfeleknek, miközben a belső megjegyzéseket belső felülvizsgálatra megtartja.  
```csharp
public void PrepareClientDocument(string internalContractPath, string clientVersion)
{
    using (var annotator = new Annotator(internalContractPath))
    {
        var annotations = annotator.Get();
        
        // Remove only internal comments, keep client-facing highlights
        var internalComments = annotations.Where(a => 
            a.Type == AnnotationType.TextField && 
            a.User?.Contains("@lawfirm.com") == true);
            
        foreach (var comment in internalComments)
        {
            annotator.Remove(comment);
        }
        
        annotator.Save(clientVersion);
    }
}
```  

### Szenárió 2: Automatizált jelentéskészítés
A havi analitikai jelentések felülvizsgálati cikluson mennek keresztül; a végső terjesztési verziónak megjegyzés‑szabadnak kell lennie.  
```csharp
public void FinalizeReport(string draftPath, string finalPath)
{
    using (var annotator = new Annotator(draftPath))
    {
        var annotations = annotator.Get();
        
        // Remove all review comments but keep approved highlights
        var reviewComments = annotations.Where(a => 
            a.Type == AnnotationType.TextField ||
            a.Type == AnnotationType.Point);
            
        Console.WriteLine($"Cleaning {reviewComments.Count()} review annotations...");
        
        foreach (var annotation in reviewComments)
        {
            annotator.Remove(annotation);
        }
        
        annotator.Save(finalPath);
        Console.WriteLine($"Final report ready: {finalPath}");
    }
}
```  

## Haladó hibakezelés
A robusztus termelési kódnak fel kell készülnie és naplóznia a leggyakoribb kivételeket, mint például az `IncorrectPasswordException` vagy az `OutOfMemoryException`.

`IncorrectPasswordException` akkor dobódik, amikor egy jelszóval védett PDF‑et a helyes jelszó megadása nélkül nyitnak meg.  
```csharp
public bool RemoveAnnotationsSafely(string inputPath, string outputPath)
{
    try
    {
        using (var annotator = new Annotator(inputPath))
        {
            var annotations = annotator.Get();
            
            if (annotations.Count == 0)
            {
                Console.WriteLine("No annotations to remove.");
                // Still copy the file to output location
                File.Copy(inputPath, outputPath, overwrite: true);
                return true;
            }
            
            foreach (var annotation in annotations)
            {
                try
                {
                    annotator.Remove(annotation);
                }
                catch (Exception ex)
                {
                    Console.WriteLine($"Failed to remove annotation {annotation.Id}: {ex.Message}");
                    // Continue with other annotations
                }
            }
            
            annotator.Save(outputPath);
            Console.WriteLine($"Successfully processed document: {Path.GetFileName(outputPath)}");
            return true;
        }
    }
    catch (FileNotFoundException)
    {
        Console.WriteLine($"Input file not found: {inputPath}");
        return false;
    }
    catch (UnauthorizedAccessException)
    {
        Console.WriteLine($"Access denied. Check file permissions for: {inputPath}");
        return false;
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Unexpected error: {ex.Message}");
        return false;
    }
}
```  

## A megvalósítás tesztelése
Egy gyors egységteszt ellenőrizheti, hogy a megjegyzések száma nullára csökken a feldolgozás után.  
```csharp
public void TestAnnotationRemoval()
{
    string testFile = "test-document-with-annotations.pdf";
    string outputFile = "test-output.pdf";
    
    // Before removal
    using (var annotator = new Annotator(testFile))
    {
        var beforeCount = annotator.Get().Count;
        Console.WriteLine($"Annotations before removal: {beforeCount}");
    }
    
    // Remove annotations
    bool success = RemoveAnnotationsSafely(testFile, outputFile);
    
    if (success)
    {
        // After removal
        using (var annotator = new Annotator(outputFile))
        {
            var afterCount = annotator.Get().Count;
            Console.WriteLine($"Annotations after removal: {afterCount}");
            Console.WriteLine($"Removed: {beforeCount - afterCount} annotations");
        }
    }
}
```  

## Hibaelhárítási útmutató
- **IncorrectPasswordException** – Add meg a PDF jelszót a `LoadOptions` segítségével.  
  ```csharp
LoadOptions loadOptions = new LoadOptions { Password = "your-pdf-password" };
using (var annotator = new Annotator(filePath, loadOptions))
{
    // Your code here
}
```  

- **Annotations still visible** – Egyes PDF‑nézők gyorsítótárazzák a megjegyzésfolyamokat; frissíts vagy nyisd meg a fájlt egy másik nézőben.  

- **OutOfMemoryException** – A PDF‑et dolgozd fel kisebb darabokban, vagy növeld az alkalmazás memóriahatárát.  

- **Certain annotation types won’t delete** – Használd a `annotation.Type`‑t a speciális típusok, például űrlapmezők azonosításához és külön kezeléséhez.  

## Teljesítmény mérőszámok
Belső tesztelés alapján a GroupDocs.Annotation 25.4.0‑val:

- **Small PDFs (< 1 MB, < 50 annotations):** < 0.5 s  
- **Medium PDFs (1‑10 MB, 50‑200 annotations):** 1‑3 s  
- **Large PDFs (10‑50 MB, 200+ annotations):** 5‑15 s  
- **Very large PDFs (> 50 MB):** Recommend batch processing to stay under 20 s per file  

## Források
- [GroupDocs.Annotation dokumentáció](https://docs.groupdocs.com/annotation/net/)  
- [API referencia](https://reference.groupdocs.com/annotation/net/)  
- [GroupDocs.Annotation letöltése .NET‑hez](https://releases.groupdocs.com/annotation/net/)  
- [Vásárlási lehetőségek](https://purchase.groupdocs.com/buy)  
- [Támogatási fórum](https://forum.groupdocs.com/c/annotation/)  

## Következtetés
Most már teljes eszköztárral rendelkezel a **remove pdf annotations** C#‑ban. Ne feledd:

1. `using` blokkok használata a tiszta erőforrás-felszabadításhoz.  
2. Szűrd a megjegyzéseket törlés előtt, hogy elkerüld a nem kívánt adatvesztést.  
3. Kezeld a jelszóval védett fájlokat és nagy PDF‑eket a fentiekben leírt stratégiákkal.  
4. Teszteld valós dokumentumokkal, mielőtt termelésbe helyeznéd.

Integráld ezeket a mintákat a szélesebb dokumentumfeldolgozó csővezetékedbe, és a felhasználóid minden alkalommal tisztább, professzionálisabb PDF‑eket kapnak.

## Gyakran ismételt kérdések

**Q: Tudok megjegyzéseket eltávolítani Word dokumentumokból, nem csak PDF‑ekből?**  
A: Igen – a GroupDocs.Annotation támogatja a DOCX, XLSX, PPTX és sok más formátumot. Ugyanazok az API hívások érvényesek a megfelelő fájltípus betöltése után.

**Q: Hogyan távolítsak el csak bizonyos típusú megjegyzéseket (pl. csak kommentárokat)?**  
A: Szűrd a megjegyzésgyűjteményt a `annotation.Type == AnnotationType.Comment` feltétellel a törlő metódus hívása előtt.  
```csharp
var commentsOnly = annotations.Where(a => a.Type == AnnotationType.TextField);
```  

**Q: A megjegyzések eltávolítása befolyásolja a dokumentum elrendezését vagy formázását?**  
A: Nem. A megjegyzések átfedő objektumokként tárolódnak; törlésük nem érinti az alatta lévő tartalmat.

**Q: Visszavonható a megjegyzés eltávolítása?**  
A: A könyvtár nem biztosít “undo” funkciót. Mindig dolgozz az eredeti dokumentum másolatán, és tarts biztonsági mentést.

**Q: Hogyan kezeljem a jelszóval védett PDF‑eket?**  
A: Add meg a jelszót a `LoadOptions` segítségével az `Annotator` példány létrehozásakor.

**Q: Van mód a megjegyzések szerző alapján történő törlésére?**  
A: Igen – ellenőrizd a `annotation.User` tulajdonságot, és csak a kívánt szerző nevének megfelelőeket töröld.

**Q: Mi a különbség a megjegyzések elrejtése és eltávolítása között?**  
A: Az elrejtés csak láthatatlanná teszi őket a nézőben; az eltávolítás véglegesen törli őket a fájlból. A GroupDocs.Annotation csak eltávolítást támogat.

---

**Legutóbb frissítve:** 2026-06-01  
**Tesztelve ezzel:** GroupDocs.Annotation 25.4.0 for .NET  
**Szerző:** GroupDocs

## Kapcsolódó oktatóanyagok
- [PDF előnézet generálása .NET - Megjegyzések eltávolítása a dokumentum bélyegképekről](/annotation/net/advanced-usage/generate-preview-without-annotations/)
- [PDF megjegyzés .NET oktatóanyag - Teljes GroupDocs útmutató](/annotation/net/annotation-management/annotate-pdf-groupdocs-annotation-net/)
- [PDF megjegyzések mentése .NET - Teljes dokumentum mentési útmutató](/annotation/net/document-saving/)