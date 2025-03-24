---
title: Szövegkiemelés megjegyzés hozzáadása a dokumentumhoz
linktitle: Szövegkiemelés megjegyzés hozzáadása a dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan adhat szövegkiemeléseket a dokumentumokhoz a GroupDocs.Annotation for .NET segítségével. Növelje az együttműködést és a termelékenységet ezzel az átfogóval.
weight: 22
url: /hu/net/unlocking-annotation-power/add-text-highlight-annotation/
---
## Bevezetés
dokumentumkezelés és az együttműködés területén a GroupDocs.Annotation for .NET robusztus megoldásként jelenik meg, amely lehetővé teszi a fejlesztők számára, hogy zökkenőmentesen integrálják a szövegkiemeléseket az alkalmazásaikba. Ez az oktatóanyag átfogó útmutatóként szolgál szövegkiemelési megjegyzések hozzáadásához a dokumentumokhoz a GroupDocs.Annotation for .NET használatával. A lépésről lépésre szóló utasítások és részletes magyarázatok révén jártasságot szerezhet ennek a nagy teljesítményű könyvtárnak a képességeinek kiaknázásában.
## Előfeltételek
Mielőtt belevágna a szövegkiemelési megjegyzések megvalósításába, győződjön meg arról, hogy a következő előfeltételek teljesülnek:
1. Környezet beállítása: rendelkezzen megfelelő fejlesztői környezettel a .NET fejlesztéshez.
2.  A GroupDocs.Annotation for .NET telepítése: Töltse le és telepítse a GroupDocs.Annotation for .NET programot a biztosított[letöltési link](https://releases.groupdocs.com/annotation/net/).
3. C# ismerete: A C# programozási nyelv alapvető ismerete.
4. Annotálandó dokumentum: Készítsen egy dokumentumot (pl. PDF), amelyet megjegyzésekkel kíván ellátni.

## Névterek importálása
Kezdésként importálja a szükséges névtereket a C# kódba, hogy kihasználhassa a GroupDocs.Annotation for .NET funkcióit:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Most bontsuk fel a szövegkiemelési megjegyzések hozzáadásának folyamatát több lépésre:
## 1. lépés: Határozza meg a kimeneti útvonalat
Adja meg a kimeneti útvonalat, ahová a megjegyzésekkel ellátott dokumentumot menti:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Inicializálja az Annotátort
 Hozzon létre egy példányt a`Annotator` osztály, paraméterként adja át a dokumentum fájlnevét:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## 3. lépés: Kiemelési megjegyzés létrehozása
 Példányosítás a`HighlightAnnotation` objektumot, és konfigurálja a tulajdonságait:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
## 4. lépés: Megjegyzés hozzáadása
Adja hozzá a létrehozott kiemelő megjegyzést a dokumentumhoz:
```csharp
annotator.Add(highlight);
```
## 5. lépés: Mentse el a megjegyzésekkel ellátott dokumentumot
Mentse el a megjegyzésekkel ellátott dokumentumot a megadott kimeneti útvonalra:
```csharp
annotator.Save(outputPath);
```

## Következtetés
Összefoglalva, a GroupDocs.Annotation for .NET egy egyszerűsített megközelítést kínál a szövegkiemelési megjegyzések dokumentumokba való beépítésére. Az oktatóanyagban ismertetett lépések követésével a fejlesztők zökkenőmentesen javíthatják a dokumentumokkal való együttműködést és a produktivitást alkalmazásaikban.
## GYIK
### A GroupDocs.Annotation for .NET kompatibilis az összes dokumentumformátummal?
A GroupDocs.Annotation for .NET különféle dokumentumformátumokat támogat, beleértve a PDF, Word, Excel és egyebeket. A teljes listát a dokumentációban találja.
### Testreszabhatók-e a kommentárok az egyedi követelményeknek megfelelően?
Igen, a fejlesztők teljes mértékben felügyelhetik a megjegyzések tulajdonságait és megjelenését, lehetővé téve a testreszabást a különféle igényeknek megfelelően.
### Elérhető ingyenes próbaverzió a GroupDocs.Annotation for .NET számára?
 Igen, felfedezheti a GroupDocs.Annotation for .NET szolgáltatásait, ha eléri az ingyenes próbaverziót a biztosított[link](https://releases.groupdocs.com/).
### Hogyan kaphatok támogatást a GroupDocs.Annotation for .NET-hez kapcsolódó problémákhoz vagy lekérdezésekhez?
 Támogatásért és segítségért keresse fel a GroupDocs.Annotation fórumot[itt](https://forum.groupdocs.com/c/annotation/10).
### Milyen licencelési lehetőségek állnak rendelkezésre a GroupDocs.Annotation for .NET számára?
 A GroupDocs.Annotation for .NET különféle licencelési lehetőségeket kínál, beleértve az ideiglenes licenceket tesztelési célokra és a kereskedelmi licenceket éles környezetekhez. Látogassa meg a vásárlási oldalt[itt](https://purchase.groupdocs.com/buy) további részletekért.