---
"description": "Ismerje meg, hogyan adhat hozzá képaláírásokat dokumentumokhoz a GroupDocs.Annotation for .NET segítségével. Javítsa a dokumentumkezelést hatékony annotációs képességekkel."
"linktitle": "Képhozzáfűzés hozzáadása a dokumentumhoz (távoli elérési út)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Képhozzáfűzés hozzáadása a dokumentumhoz (távoli elérési út)"
"url": "/hu/net/unlocking-annotation-power/add-image-annotation-remote-path/"
"weight": 15
---

# Képhozzáfűzés hozzáadása a dokumentumhoz (távoli elérési út)

## Bevezetés
Ebben az oktatóanyagban bemutatjuk, hogyan adhatunk képaláírásokat egy dokumentumhoz a GroupDocs.Annotation for .NET használatával. Ez a függvénytár hatékony eszközöket biztosít különféle típusú dokumentumok programozott annotációjához.
## Előfeltételek
Mielőtt elkezdenénk, győződjünk meg róla, hogy a következőkkel rendelkezünk:
1. GroupDocs.Annotation .NET-hez: Töltse le és telepítse a könyvtárat innen: [itt](https://releases.groupdocs.com/annotation/net/).
2. Fejlesztői környezet: Győződjön meg arról, hogy rendelkezik egy működő fejlesztői környezettel a .NET fejlesztéshez.
3. Dokumentum: Készítse elő a jegyzetekkel ellátni kívánt dokumentumot. Ebben az oktatóanyagban feltételezzük, hogy van egy PDF-dokumentuma, amelynek neve `input.pdf`.
4. Jegyzethez tartozó kép: Válassza ki a jegyzethez használni kívánt képet. Győződjön meg róla, hogy a kép URL-címe vagy helyi elérési útja készen áll.

## Névterek importálása
Mielőtt elkezdenénk a kódolást, importáljuk a szükséges névtereket:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## 1. lépés: Kimeneti útvonal beállítása
Először is határozza meg a kimeneti elérési utat, ahová a jegyzetekkel ellátott dokumentum mentésre kerül.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Annotátor inicializálása
Hozz létre egy példányt a `Annotator` osztályt, és adja meg a bemeneti dokumentumot.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ide fog kerülni a megjegyzéskód
}
```
## 3. lépés: Képhozzáfűzés hozzáadása
Most adjuk hozzá a képhez tartozó megjegyzést a dokumentumhoz. Megadjuk a képhez tartozó megjegyzés tulajdonságait, például a pozíciót, az átlátszóságot, az oldalszámot és a kép elérési útját.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Adja meg a megjegyzés pozícióját
    CreatedOn = DateTime.Now, // Állítsa be a létrehozási dátumot
    Opacity = 0.7, // Átlátszatlanság beállítása (0-tól 1-ig)
    PageNumber = 0, // Adja meg az oldalszámot
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Adja meg a kép URL-címét
};
annotator.Add(image); // Képhez tartozó megjegyzés hozzáadása
```
## 4. lépés: Dokumentum mentése
Mentse el a jegyzetekkel ellátott dokumentumot a megadott kimeneti elérési útra.
```csharp
annotator.Save(outputPath);
```
## 5. lépés: Kimeneti útvonal megjelenítése
Tájékoztassa a felhasználót a sikeres dokumentummentési műveletről, és jelenítse meg a kimeneti elérési utat.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk hozzá képaláírásokat egy dokumentumhoz a GroupDocs.Annotation for .NET használatával. Ezeket a lépéseket követve hatékony annotációs képességekkel bővítheti dokumentumkezelő alkalmazásait.
## GYIK
### Használható a GroupDocs.Annotation a PDF-en kívül más dokumentumformátumokkal is?
Igen, a GroupDocs.Annotation számos dokumentumformátumot támogat, beleértve a Wordöt, az Excelt, a PowerPointot és egyebeket.
### Kompatibilis a GroupDocs.Annotation a .NET Core-ral?
Igen, a GroupDocs.Annotation kompatibilis mind a .NET Framework, mind a .NET Core rendszerrel.
### Testreszabhatom a megjegyzések megjelenését?
Igen, testreszabhatja a megjegyzések megjelenését, például a színét, az átlátszóságát és a méretét.
### A GroupDocs.Annotation támogatja az együttműködésen alapuló annotációs funkciókat?
Igen, a GroupDocs.Annotation közös annotációs funkciókat kínál a dokumentumokon valós idejű együttműködéshez.
### Van elérhető próbaverzió tesztelésre?
Igen, ingyenes próbaverziót kaphat a GroupDocs.Annotation szolgáltatásból innen: [itt](https://releases.groupdocs.com/).