---
title: Ellipszis megjegyzés hozzáadása a dokumentumhoz
linktitle: Ellipszis megjegyzés hozzáadása a dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan adhat ellipszis jelöléseket a .NET-ben található dokumentumokhoz a GroupDocs.Annotation segítségével. Fokozza az együttműködést és a kommunikációt erőfeszítés nélkül.
type: docs
weight: 13
url: /hu/net/unlocking-annotation-power/add-ellipse-annotation/
---
## Bevezetés
Ebből az oktatóanyagból megtudhatja, hogyan adhat hozzá ellipszis megjegyzést egy dokumentumhoz a GroupDocs.Annotation for .NET segítségével. Ez a lépésenkénti útmutató végigvezeti a folyamaton, biztosítva, hogy minden lépést egyértelműen megértsen.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következőkkel:
1.  GroupDocs.Annotation for .NET: Győződjön meg arról, hogy letöltötte és telepítette a GroupDocs.Annotation for .NET programot. Letöltheti innen[itt](https://releases.groupdocs.com/annotation/net/).
2. IDE (Integrated Development Environment): A kód írásához és végrehajtásához telepíteni kell egy IDE-t a rendszeren, például a Visual Studio-t.

## Névterek importálása
Először is importálja a szükséges névtereket a projektbe:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1. lépés: Állítsa be a kimeneti útvonalat
Határozza meg a kimeneti útvonalat, ahová a megjegyzésekkel ellátott dokumentumot menti:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Inicializálja az Annotátort
Inicializálja az annotátort a bemeneti dokumentum elérési útjának megadásával:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 3. lépés: Hozzon létre ellipszis megjegyzést
 Hozzon létre egy példányt a`EllipseAnnotation` osztályt, és állítsa be a tulajdonságait:
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
## 4. lépés: Megjegyzés hozzáadása
Adja hozzá az ellipszis megjegyzést a dokumentumhoz:
```csharp
annotator.Add(ellipse);
```
## 5. lépés: Mentse el a dokumentumot
Mentse el a megjegyzésekkel ellátott dokumentumot a kimeneti útvonalra:
```csharp
annotator.Save(outputPath);
```

## Következtetés
Gratulálunk! Sikeresen hozzáadott egy ellipszis megjegyzést egy dokumentumhoz a GroupDocs.Annotation for .NET segítségével. Mostantól ezt a funkciót integrálhatja .NET-alkalmazásaiba a dokumentumokkal való együttműködés és kommunikáció javítása érdekében.
## GYIK
### Testreszabhatom az ellipszis annotáció megjelenését?
Igen, igényei szerint testreszabhatja a különféle tulajdonságokat, például a háttérszínt, a szegélyszínt, az átlátszatlanságot stb.
### A GroupDocs.Annotation for .NET kompatibilis az összes dokumentumformátummal?
A GroupDocs.Annotation for .NET a dokumentumformátumok széles skáláját támogatja, beleértve a PDF, DOCX, PPTX, XLSX és egyebeket.
### Hozzáadhatok több megjegyzést egyetlen dokumentumhoz?
Igen, egyetlen dokumentumhoz több megjegyzést is hozzáadhat, például ellipsziseket, téglalapokat, szöveget stb.
### Létezik próbaverzió tesztelési célból?
 Igen, letölthet egy ingyenes próbaverziót a webhelyről[itt](https://releases.groupdocs.com/) jellemzőinek értékelésére.
### Hol kaphatok technikai támogatást a GroupDocs.Annotation for .NET-hez?
 Technikai támogatást a GroupDocs.Annotation közösségi fórumon kaphat[itt](https://forum.groupdocs.com/c/annotation/10).