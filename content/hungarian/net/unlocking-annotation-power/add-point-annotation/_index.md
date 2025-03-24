---
title: Pontos megjegyzés hozzáadása a dokumentumhoz
linktitle: Pontos megjegyzés hozzáadása a dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan adhat hozzá pontjegyzeteket PDF-fájlokhoz a GroupDocs.Annotation for .NET segítségével. Lépésről lépésre útmutató a zökkenőmentes integrációhoz.
weight: 17
url: /hu/net/unlocking-annotation-power/add-point-annotation/
---

# Pontos megjegyzés hozzáadása a dokumentumhoz

## Bevezetés
A GroupDocs.Annotation for .NET egy hatékony eszköz, amely lehetővé teszi a fejlesztők számára, hogy különféle típusú megjegyzéseket adhassanak a dokumentumokhoz programozottan. Ebben az oktatóanyagban arra fogunk összpontosítani, hogy pont megjegyzést adjunk egy dokumentumhoz C# használatával.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következőkkel:
1. A C# programozási nyelv alapvető ismerete.
2. A Visual Studio telepítve van a rendszerére.
3.  GroupDocs.Annotation for .NET könyvtár telepítve. Letöltheti innen[itt](https://releases.groupdocs.com/annotation/net/).

## A szükséges névterek importálása
A kezdéshez importálnia kell a szükséges névtereket a C# projektbe:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1. lépés: Határozza meg a kimeneti útvonalat
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Ebben a lépésben meghatározzuk a kimeneti útvonalat, ahová a megjegyzésekkel ellátott dokumentumot el kell menteni.
## 2. lépés: Inicializálja az Annotátort
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Itt inicializáljuk a`Annotator` objektumot a bemeneti dokumentummal ("input.pdf").
## 3. lépés: Pontjegyzet létrehozása
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
 Ebben a lépésben létrehozzuk a`PointAnnotation` objektumot, és adja meg tulajdonságait, például pozíciót, üzenetet, oldalszámot és válaszokat.
## 4. lépés: Megjegyzés hozzáadása
```csharp
annotator.Add(point);
```
Itt hozzáadjuk a létrehozott pontjegyzetet a dokumentumhoz.
## 5. lépés: Mentse el a dokumentumot
```csharp
annotator.Save(outputPath);
```
Végül elmentjük a jegyzett dokumentumot a megadott kimeneti útvonalra.

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk hozzá pontjegyzetet egy dokumentumhoz a GroupDocs.Annotation for .NET használatával. Ezzel a nagy teljesítményű könyvtárral a jegyzetkezelési funkciók beépítésével javíthatja dokumentumkezelő alkalmazásait.
## GYIK
### A GroupDocs.Annotation for .NET kompatibilis az összes dokumentumformátummal?
Igen, a GroupDocs.Annotation for .NET a dokumentumformátumok széles skáláját támogatja, beleértve a PDF, Microsoft Word, Excel, PowerPoint és egyebeket.
### Testreszabhatom a kommentárok megjelenését?
Teljesen! A GroupDocs.Annotation for .NET kiterjedt lehetőségeket kínál a megjegyzések megjelenésének testreszabására az alkalmazás igényei szerint.
### Elérhető ingyenes próbaverzió a GroupDocs.Annotation for .NET számára?
 Igen, igénybe veheti az ingyenes próbaverziót innen[itt](https://releases.groupdocs.com/).
### Hogyan kaphatok támogatást a GroupDocs.Annotation for .NET-hez kapcsolódó problémákhoz vagy lekérdezésekhez?
 Támogatást a GroupDocs.Annotation fórumon kaphat[itt](https://forum.groupdocs.com/c/annotation/10).
### Kaphatok ideiglenes licencet tesztelési célból?
 Igen, ideiglenes engedélyt szerezhetsz innen[itt](https://purchase.groupdocs.com/temporary-license/).