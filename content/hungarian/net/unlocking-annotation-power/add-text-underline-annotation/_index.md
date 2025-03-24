---
title: Szöveg aláhúzás megjegyzés hozzáadása a dokumentumhoz
linktitle: Szöveg aláhúzás megjegyzés hozzáadása a dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan adhat szöveges aláhúzás megjegyzéseket a dokumentumokhoz a GroupDocs.Annotation for .NET segítségével. Fokozza az együttműködést és a kommunikációt erőfeszítés nélkül.
weight: 27
url: /hu/net/unlocking-annotation-power/add-text-underline-annotation/
---

# Szöveg aláhúzás megjegyzés hozzáadása a dokumentumhoz

## Bevezetés
Ebben az oktatóanyagban a GroupDocs.Annotation for .NET használatával szöveges aláhúzás megjegyzések hozzáadásának folyamatát mutatjuk be. A szöveg aláhúzott megjegyzései hasznosak lehetnek a dokumentum bizonyos részei, például a fontos részek vagy kulcspontok kiemelésére.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételek telepítve vannak:
1.  GroupDocs.Annotation for .NET: Töltse le és telepítse a GroupDocs.Annotation for .NET webhelyet[itt](https://releases.groupdocs.com/annotation/net/).
2. .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a rendszeren.

## Névterek importálása
Először is importáljuk a szükséges névtereket a projektünkbe:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Most bontsuk fel a példát több lépésre:
## 1. lépés: Határozza meg a kimeneti útvonalat
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Ebben a lépésben meghatározzuk a kimeneti útvonalat, ahová a megjegyzésekkel ellátott dokumentumot el kell menteni.
## 2. lépés: Inicializálja az Annotátort
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Itt inicializáljuk a`Annotator` osztályba a bemeneti dokumentum elérési útjának megadásával.
## 3. lépés: Aláhúzott megjegyzés létrehozása
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // csak Word és PDF dokumentumokat támogat
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
 Ez a lépés egy`UnderlineAnnotation`objektum különféle tulajdonságokkal, például betűszín, üzenet, átlátszatlanság, oldalszám, háttérszín, aláhúzás színe, pontok és válaszok.
## 4. lépés: Megjegyzés hozzáadása a dokumentumhoz
```csharp
annotator.Add(underline);
```
Itt az aláhúzott megjegyzést adjuk a dokumentumhoz.
## 5. lépés: Mentse el a megjegyzésekkel ellátott dokumentumot
```csharp
annotator.Save(outputPath);
```
Végül elmentjük a jegyzett dokumentumot a megadott kimeneti útvonalra.

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk aláhúzott szöveges megjegyzést egy dokumentumhoz a GroupDocs.Annotation for .NET segítségével. Ez a nagy teljesítményű könyvtár különféle megjegyzési lehetőségeket kínál a dokumentumokkal való együttműködés és kommunikáció javításához.
## GYIK
### Testreszabhatom az aláhúzott megjegyzés megjelenését?
Igen, igényei szerint testreszabhatja az olyan tulajdonságokat, mint a szín, az átlátszatlanság és a pozíció.
### A GroupDocs.Annotation kompatibilis a különböző dokumentumformátumokkal?
Igen, a GroupDocs.Annotation a dokumentumformátumok széles skáláját támogatja, beleértve a Word-t és a PDF-t.
### Hozzáadhatok több megjegyzést egyetlen dokumentumhoz?
Természetesen a GroupDocs.Annotation lehetővé teszi több különböző típusú megjegyzés hozzáadását egy dokumentumhoz.
### Van ingyenes próbaverzió a GroupDocs.Annotation számára?
 Igen, elérheti az ingyenes próbaverziót innen[itt](https://releases.groupdocs.com/).
### Hol kaphatok támogatást a GroupDocs.Annotation-hoz?
 Támogatást a GroupDocs.Annotation közösségi fórumtól kaphat[itt](https://forum.groupdocs.com/c/annotation/10).