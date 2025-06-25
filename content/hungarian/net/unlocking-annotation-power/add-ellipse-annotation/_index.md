---
"description": "Tanulja meg, hogyan adhat ellipszis alakú jegyzeteket a .NET dokumentumokhoz a GroupDocs.Annotation segítségével. Könnyedén javíthatja az együttműködést és a kommunikációt."
"linktitle": "Ellipszis jegyzet hozzáadása a dokumentumhoz"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Ellipszis jegyzet hozzáadása a dokumentumhoz"
"url": "/hu/net/unlocking-annotation-power/add-ellipse-annotation/"
"weight": 13
---

# Ellipszis jegyzet hozzáadása a dokumentumhoz

## Bevezetés
Ebben az oktatóanyagban megtudhatja, hogyan adhat hozzá ellipszis alakú jegyzeteket egy dokumentumhoz a GroupDocs.Annotation for .NET használatával. Ez a lépésenkénti útmutató végigvezeti Önt a folyamaton, biztosítva, hogy minden lépést világosan megértsen.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy a következőkkel rendelkezik:
1. GroupDocs.Annotation for .NET: Győződjön meg róla, hogy letöltötte és telepítette a GroupDocs.Annotation for .NET fájlt. Letöltheti innen: [itt](https://releases.groupdocs.com/annotation/net/).
2. IDE (Integrált fejlesztői környezet): A kód írásához és végrehajtásához telepíteni kell egy IDE-t a rendszeredre, például a Visual Studio-t.

## Névterek importálása
Először importáld a szükséges névtereket a projektedbe:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1. lépés: Kimeneti útvonal beállítása
Adja meg a kimeneti elérési utat, ahová a jegyzetekkel ellátott dokumentum mentésre kerül:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Annotátor inicializálása
Inicializálja az annotátort a bemeneti dokumentum elérési útjának megadásával:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 3. lépés: Ellipszis annotáció létrehozása
Hozz létre egy példányt a `EllipseAnnotation` osztály és állítsd be a tulajdonságait:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    }
};
```
## 4. lépés: Jegyzet hozzáadása
Adja hozzá az ellipszis annotációt a dokumentumhoz:
```csharp
annotator.Add(ellipse);
```
## 5. lépés: Dokumentum mentése
Mentse el a jegyzetekkel ellátott dokumentumot a kimeneti útvonalra:
```csharp
annotator.Save(outputPath);
```

## Következtetés
Gratulálunk! Sikeresen hozzáadott egy ellipszis alakú jegyzetet egy dokumentumhoz a GroupDocs.Annotation for .NET használatával. Mostantól integrálhatja ezt a funkciót a .NET alkalmazásaiba a dokumentumokkal való együttműködés és kommunikáció javítása érdekében.
## GYIK
### Testreszabhatom az ellipszis annotáció megjelenését?
Igen, testreszabhatja a különböző tulajdonságokat, például a háttérszínt, a szegély színét, az átlátszóságot stb., az igényei szerint.
### A GroupDocs.Annotation for .NET kompatibilis az összes dokumentumformátummal?
A GroupDocs.Annotation for .NET számos dokumentumformátumot támogat, beleértve a PDF, DOCX, PPTX, XLSX és egyebeket.
### Hozzáadhatok több megjegyzést egyetlen dokumentumhoz?
Igen, több megjegyzést is hozzáadhat egyetlen dokumentumhoz, beleértve a kihagyásokat, téglalapokat, szöveget stb.
### Van elérhető próbaverzió tesztelési célokra?
Igen, letölthet egy ingyenes próbaverziót innen [itt](https://releases.groupdocs.com/) hogy értékelje a tulajdonságait.
### Hol kaphatok technikai támogatást a GroupDocs.Annotation for .NET-hez?
Technikai támogatást a GroupDocs.Annotation közösségi fórumon kaphat. [itt](https://forum.groupdocs.com/c/annotation/10).