---
title: Szövegszerkesztési megjegyzés hozzáadása a dokumentumhoz
linktitle: Szövegszerkesztési megjegyzés hozzáadása a dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan adhat hozzá szövegszerkesztő megjegyzéseket PDF-dokumentumokhoz a GroupDocs.Annotation for .NET segítségével. Könnyedén megvédheti az érzékeny információkat.
weight: 23
url: /hu/net/unlocking-annotation-power/add-text-redaction-annotation/
---

# Szövegszerkesztési megjegyzés hozzáadása a dokumentumhoz

## Bevezetés
Szövegszerkesztő megjegyzés hozzáadása a dokumentumhoz kulcsfontosságú lépés lehet a bizalmas információk biztonságos kezelésében. A GroupDocs.Annotation for .NET robusztus megoldást kínál ennek zökkenőmentes elérésére. Ebben az oktatóanyagban lépésről lépésre végigvezetjük Önt a szövegszerkesztő megjegyzések dokumentumához való hozzáadásának folyamatán.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételek teljesülnek:
1.  GroupDocs.Annotation for .NET: Győződjön meg arról, hogy telepítette a GroupDocs.Annotation for .NET könyvtárat. Letöltheti a[weboldal](https://releases.groupdocs.com/annotation/net/).
2. Fejlesztési környezet: Hozzon létre egy fejlesztői környezetet .NET-kompatibilis IDE-vel, például a Visual Studio-val.

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
## 1. lépés: Határozza meg a kimeneti útvonalat
Határozza meg a kimeneti útvonalat, ahová a megjegyzésekkel ellátott dokumentumot menteni kívánja. Győződjön meg róla, hogy elérhető és írható.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Inicializálja az Annotátort
 Inicializálja az annotátort a bemeneti dokumentum elérési útjával. Cserélje ki`"input.pdf"` a dokumentum elérési útjával.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ide kerül a kommentár kódja
}
```
## 3. lépés: Szövegszerkesztési megjegyzés létrehozása
 Hozzon létre egy`TextRedactionAnnotation`objektum a szükséges tulajdonságokkal, mint pl`PageNumber`, `FontColor` , és`Points`. Szabja testre a kommentárt igényei szerint.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## 4. lépés: Megjegyzés hozzáadása és mentése
Adja hozzá a létrehozott megjegyzést a dokumentumhoz a jegyző segítségével, és mentse a jegyzett dokumentumot a megadott kimeneti útvonalra.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## 5. lépés: Ellenőrizze a kimenetet
Végül győződjön meg arról, hogy a dokumentumot sikeresen elmentette a megadott kimeneti útvonalra.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés
Ebben az oktatóanyagban végigvezettük azt a folyamatot, amikor a GroupDocs.Annotation for .NET segítségével szövegszerkesztő megjegyzést adunk egy dokumentumhoz. Ezekkel a lépésekkel mostantól biztonságosan kezelheti a dokumentumokon belüli bizalmas információkat.
## GYIK
### Testreszabhatom a szövegszerkesztési megjegyzés megjelenését?
Igen, testreszabhatja a különféle tulajdonságokat, például a betűszínt, a kitöltési színt és az átlátszatlanságot az igényeinek megfelelően.
### Vásárlás előtt van próbaverzió?
 Igen, elérheti az ingyenes próbaverziót a[weboldal](https://releases.groupdocs.com/).
### Hogyan kaphatok támogatást, ha bármilyen problémám van?
 Támogatást a GroupDocs.Annotation közösségi fórumtól kaphat[itt](https://forum.groupdocs.com/c/annotation/10).
### Szükségem van ideiglenes licencre tesztelés céljából?
 Igen, ideiglenes engedélyt kaphat a[vásárlási oldal](https://purchase.groupdocs.com/temporary-license/)tesztelésre.
### Hozzáadhatok több megjegyzést egyetlen dokumentumhoz?
Természetesen a GroupDocs.Annotation lehetővé teszi különböző típusú megjegyzések és több példány hozzáadását egyetlen dokumentumhoz.