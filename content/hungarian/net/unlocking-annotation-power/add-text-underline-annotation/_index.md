---
"description": "Tanulja meg, hogyan adhat hozzá szöveges aláhúzásos megjegyzéseket a dokumentumokhoz a GroupDocs.Annotation for .NET segítségével. Könnyedén javíthatja az együttműködést és a kommunikációt."
"linktitle": "Szöveg aláhúzott jegyzet hozzáadása a dokumentumhoz"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Szöveg aláhúzott jegyzet hozzáadása a dokumentumhoz"
"url": "/hu/net/unlocking-annotation-power/add-text-underline-annotation/"
"weight": 27
---

# Szöveg aláhúzott jegyzet hozzáadása a dokumentumhoz

## Bevezetés
Ebben az oktatóanyagban bemutatjuk, hogyan adhatunk szöveges aláhúzásos megjegyzéseket egy dokumentumhoz a GroupDocs.Annotation for .NET használatával. A szöveges aláhúzásos megjegyzések hasznosak lehetnek a dokumentum bizonyos részeinek, például fontos részleteknek vagy kulcsfontosságú pontoknak a kiemelésére.
## Előfeltételek
Mielőtt elkezdenénk, győződjünk meg arról, hogy a következő előfeltételek telepítve vannak:
1. GroupDocs.Annotation for .NET: Töltse le és telepítse a GroupDocs.Annotation for .NET fájlt innen: [itt](https://releases.groupdocs.com/annotation/net/).
2. .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a rendszerén.

## Névterek importálása
Először importáljuk a szükséges névtereket a projektünkbe:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Most bontsuk a példát több lépésre:
## 1. lépés: Kimeneti útvonal meghatározása
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Ebben a lépésben meghatározzuk a kimeneti elérési utat, ahová a jegyzetekkel ellátott dokumentum mentésre kerül.
## 2. lépés: Annotátor inicializálása
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Itt inicializáljuk a következő egy példányát: `Annotator` osztály a bemeneti dokumentum elérési útjának megadásával.
## 3. lépés: Aláhúzott jegyzet létrehozása
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // csak a Word és PDF dokumentumokat támogatja
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
Ez a lépés magában foglalja egy `UnderlineAnnotation` objektum különféle tulajdonságokkal, például betűszínnel, üzenettel, átlátszósággal, oldalszámmal, háttérszínnel, aláhúzás színével, pontokkal és válaszokkal.
## 4. lépés: Jegyzet hozzáadása a dokumentumhoz
```csharp
annotator.Add(underline);
```
Itt adjuk hozzá az aláhúzásos megjegyzést a dokumentumhoz.
## 5. lépés: Jegyzetekkel ellátott dokumentum mentése
```csharp
annotator.Save(outputPath);
```
Végül a jegyzetekkel ellátott dokumentumot a megadott kimeneti útvonalra mentjük.

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk hozzá szöveges aláhúzásos megjegyzést egy dokumentumhoz a GroupDocs.Annotation for .NET használatával. Ez a hatékony könyvtár különféle megjegyzésbeállításokat kínál a dokumentumokkal való együttműködés és kommunikáció javítása érdekében.
## GYIK
### Testreszabhatom az aláhúzott megjegyzés megjelenését?
Igen, testreszabhatja az olyan tulajdonságokat, mint a szín, az átlátszóság és a pozíció, az igényei szerint.
### Kompatibilis a GroupDocs.Annotation különböző dokumentumformátumokkal?
Igen, a GroupDocs.Annotation számos dokumentumformátumot támogat, beleértve a Wordöt és a PDF-et is.
### Hozzáadhatok több megjegyzést egyetlen dokumentumhoz?
Természetesen a GroupDocs.Annotation lehetővé teszi több különböző típusú annotáció hozzáadását egy dokumentumhoz.
### Van ingyenes próbaverzió a GroupDocs.Annotation-höz?
Igen, hozzáférhetsz az ingyenes próbaverzióhoz innen: [itt](https://releases.groupdocs.com/).
### Hol kaphatok támogatást a GroupDocs.Annotation-höz?
Támogatást kaphatsz a GroupDocs.Annotation közösségi fórumon. [itt](https://forum.groupdocs.com/c/annotation/10).