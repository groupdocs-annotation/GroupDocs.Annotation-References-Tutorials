---
"description": "Ismerje meg, hogyan adhat hozzá pontszerű megjegyzéseket PDF-ekhez a GroupDocs.Annotation for .NET segítségével. Lépésről lépésre útmutató a zökkenőmentes integrációhoz."
"linktitle": "Pontjegyzet hozzáadása a dokumentumhoz"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Pontjegyzet hozzáadása a dokumentumhoz"
"url": "/hu/net/unlocking-annotation-power/add-point-annotation/"
type: docs
"weight": 17
---

# Pontjegyzet hozzáadása a dokumentumhoz

## Bevezetés
A GroupDocs.Annotation for .NET egy hatékony eszköz, amely lehetővé teszi a fejlesztők számára, hogy programozottan adjanak hozzá különféle típusú annotációkat a dokumentumokhoz. Ebben az oktatóanyagban a C# használatával hozzáadott Point annotációkra fogunk összpontosítani.
## Előfeltételek
Mielőtt elkezdenénk, győződjünk meg róla, hogy a következőkkel rendelkezünk:
1. C# programozási nyelv alapismeretek.
2. Visual Studio telepítve a rendszeredre.
3. A GroupDocs.Annotation for .NET könyvtár telepítve van. Letöltheti innen: [itt](https://releases.groupdocs.com/annotation/net/).

## Szükséges névterek importálása
A kezdéshez importálnia kell a szükséges névtereket a C# projektjébe:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1. lépés: Kimeneti útvonal meghatározása
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Ebben a lépésben meghatározzuk a kimeneti elérési utat, ahová a jegyzetekkel ellátott dokumentum mentésre kerül.
## 2. lépés: Annotátor inicializálása
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Itt inicializáljuk a `Annotator` objektum a bemeneti dokumentummal ("input.pdf").
## 3. lépés: Pontjelölés létrehozása
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
Ebben a lépésben létrehozunk egy `PointAnnotation` objektumot, és adja meg a tulajdonságait, például a pozíciót, az üzenetet, az oldalszámot és a válaszokat.
## 4. lépés: Jegyzet hozzáadása
```csharp
annotator.Add(point);
```
Itt adjuk hozzá a létrehozott pontjegyzetet a dokumentumhoz.
## 5. lépés: Dokumentum mentése
```csharp
annotator.Save(outputPath);
```
Végül a jegyzetekkel ellátott dokumentumot a megadott kimeneti útvonalra mentjük.

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk hozzá pontszerű megjegyzéseket egy dokumentumhoz a GroupDocs.Annotation for .NET használatával. Ezzel a hatékony könyvtárral annotációs funkciók beépítésével fejlesztheti dokumentumkezelő alkalmazásait.
## GYIK
### A GroupDocs.Annotation for .NET kompatibilis az összes dokumentumformátummal?
Igen, a GroupDocs.Annotation for .NET számos dokumentumformátumot támogat, beleértve a PDF, Microsoft Word, Excel, PowerPoint és egyebeket.
### Testreszabhatom a megjegyzések megjelenését?
Abszolút! A GroupDocs.Annotation for .NET széleskörű lehetőségeket kínál a megjegyzések megjelenésének testreszabására az alkalmazás igényeinek megfelelően.
### Van ingyenes próbaverzió a GroupDocs.Annotation for .NET-hez?
Igen, igénybe vehet egy ingyenes próbaverziót a következő címen: [itt](https://releases.groupdocs.com/).
### Hogyan kaphatok támogatást a GroupDocs.Annotation for .NET-tel kapcsolatos problémákkal vagy kérdésekkel kapcsolatban?
Támogatást kaphatsz a GroupDocs.Annotation fórumon. [itt](https://forum.groupdocs.com/c/annotation/10).
### Szerezhetek ideiglenes jogosítványt tesztelési célokra?
Igen, ideiglenes jogosítványt szerezhet be. [itt](https://purchase.groupdocs.com/temporary-license/).