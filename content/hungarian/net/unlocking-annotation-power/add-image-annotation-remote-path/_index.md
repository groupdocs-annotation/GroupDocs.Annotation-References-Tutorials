---
title: Képannotáció hozzáadása a dokumentumhoz (távoli elérési út)
linktitle: Képannotáció hozzáadása a dokumentumhoz (távoli elérési út)
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan adhat hozzá képes megjegyzéseket a dokumentumokhoz a GroupDocs.Annotation for .NET segítségével. Javítsa a dokumentumkezelést hatékony annotációs képességekkel.
type: docs
weight: 15
url: /hu/net/unlocking-annotation-power/add-image-annotation-remote-path/
---
## Bevezetés
Ebben az oktatóanyagban a GroupDocs.Annotation for .NET segítségével képjegyzetek dokumentumhoz való hozzáadásának folyamatát mutatjuk be. Ez a könyvtár hatékony eszközöket biztosít a különféle típusú dokumentumok programozott megjegyzéseinek rögzítéséhez.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következőkkel:
1.  GroupDocs.Annotation for .NET: Töltse le és telepítse a könyvtárat innen[itt](https://releases.groupdocs.com/annotation/net/).
2. Fejlesztési környezet: Győződjön meg arról, hogy működő fejlesztői környezetet állított be a .NET fejlesztéshez.
3.  Dokumentum: Készítse elő a megjegyzéssel ellátni kívánt dokumentumot. Ebben az oktatóanyagban feltételezzük, hogy van egy elnevezett PDF-dokumentum`input.pdf`.
4. Kép annotációhoz: Válassza ki a megjegyzéshez használni kívánt képet. Győződjön meg arról, hogy készen áll a kép URL-címe vagy helyi elérési útja.

## Névterek importálása
A kódolás megkezdése előtt importáljuk a szükséges névtereket:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## 1. lépés: Állítsa be a kimeneti útvonalat
Először határozza meg a kimeneti útvonalat, ahová a megjegyzésekkel ellátott dokumentum mentésre kerül.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Inicializálja az Annotátort
 Hozzon létre egy példányt a`Annotator` osztályt, és adja meg a bemeneti dokumentumot.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ide kerül a kommentár kódja
}
```
## 3. lépés: Képannotáció hozzáadása
Most adjuk hozzá a kép megjegyzését a dokumentumhoz. Megadjuk a képfeljegyzés tulajdonságait, például pozíciót, átlátszatlanságot, oldalszámot és képútvonalat.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Adja meg a megjegyzés pozícióját
    CreatedOn = DateTime.Now, // Állítsa be a létrehozás dátumát
    Opacity = 0.7, // Átlátszatlanság beállítása (0-tól 1-ig)
    PageNumber = 0, // Adja meg az oldalszámot
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Adja meg a kép URL-jét
};
annotator.Add(image); // Adja hozzá a kép megjegyzését
```
## 4. lépés: Mentse el a dokumentumot
Mentse a megjegyzésekkel ellátott dokumentumot a megadott kimeneti útvonalra.
```csharp
annotator.Save(outputPath);
```
## 5. lépés: Kimeneti útvonal megjelenítése
Tájékoztassa a felhasználót a sikeres dokumentummentési műveletről, és jelenítse meg a kimeneti útvonalat.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk képjegyzeteket egy dokumentumhoz a GroupDocs.Annotation for .NET használatával. Ha követi ezeket a lépéseket, dokumentumkezelő alkalmazásait hatékony jegyzetelési képességekkel bővítheti.
## GYIK
### A GroupDocs.Annotation használható a PDF-en kívül más dokumentumformátumokkal is?
Igen, a GroupDocs.Annotation különféle dokumentumformátumokat támogat, beleértve a Word, Excel, PowerPoint és egyebeket.
### A GroupDocs.Annotation kompatibilis a .NET Core programmal?
Igen, a GroupDocs.Annotation kompatibilis a .NET-keretrendszerrel és a .NET Core-al is.
### Testreszabhatom a kommentárok megjelenését?
Igen, testreszabhatja a megjegyzések megjelenését, például a színt, az átlátszatlanságot és a méretet.
### Támogatja a GroupDocs.Annotation az együttműködési jegyzetelési funkciókat?
Igen, a GroupDocs.Annotation együttműködési jegyzetelési szolgáltatásokat kínál a dokumentumokon való valós idejű együttműködéshez.
### Létezik próbaverzió tesztelésre?
 Igen, ingyenes próbaverziót kaphat a GroupDocs.Annotation webhelyen[itt](https://releases.groupdocs.com/).