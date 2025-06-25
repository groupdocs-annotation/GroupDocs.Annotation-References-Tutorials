---
"description": "Tanulja meg, hogyan adhat hozzá szöveges kihagyási megjegyzéseket PDF dokumentumokhoz a GroupDocs.Annotation for .NET segítségével. Védje meg bizalmas adatait könnyedén."
"linktitle": "Szövegkihagyási jegyzet hozzáadása a dokumentumhoz"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Szövegkihagyási jegyzet hozzáadása a dokumentumhoz"
"url": "/hu/net/unlocking-annotation-power/add-text-redaction-annotation/"
"weight": 23
---

# Szövegkihagyási jegyzet hozzáadása a dokumentumhoz

## Bevezetés
szöveges kivonási megjegyzések hozzáadása egy dokumentumhoz kulcsfontosságú lépés lehet a bizalmas információk biztonságos kezelésében. A GroupDocs.Annotation for .NET robusztus megoldást kínál ennek zökkenőmentes megvalósítására. Ebben az oktatóanyagban lépésről lépésre végigvezetjük Önt a szöveges kivonási megjegyzések dokumentumhoz való hozzáadásának folyamatán.
## Előfeltételek
Mielőtt elkezdenénk, győződjünk meg arról, hogy a következő előfeltételek teljesülnek:
1. GroupDocs.Annotation for .NET: Győződjön meg róla, hogy telepítette a GroupDocs.Annotation for .NET könyvtárat. Letöltheti innen: [weboldal](https://releases.groupdocs.com/annotation/net/).
2. Fejlesztői környezet: Hozz létre egy fejlesztői környezetet egy .NET-kompatibilis IDE-vel, például a Visual Studio-val.

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
## 1. lépés: Kimeneti útvonal meghatározása
Adja meg a kimeneti elérési utat, ahová a jegyzetekkel ellátott dokumentumot menteni szeretné. Győződjön meg arról, hogy hozzáférhető és írható.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Annotátor inicializálása
Inicializálja az annotátort a bemeneti dokumentum elérési útjával. Cserélje ki `"input.pdf"` a dokumentum elérési útjával.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ide fog kerülni a megjegyzéskód
}
```
## 3. lépés: Szövegkihagyási jegyzet létrehozása
Hozz létre egy `TextRedactionAnnotation` objektum a szükséges tulajdonságokkal, mint például `PageNumber`, `FontColor`, és `Points`. Szabja testre a jegyzeteket az igényei szerint.
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
## 4. lépés: Jegyzet hozzáadása és mentés
Adja hozzá a létrehozott jegyzetet a dokumentumhoz a jegyzetelő segítségével, és mentse el a jegyzetekkel ellátott dokumentumot a megadott kimeneti elérési útra.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## 5. lépés: Ellenőrizze a kimenetet
Végül erősítse meg, hogy a dokumentum sikeresen mentésre került a megadott kimeneti elérési útra.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés
Ebben az oktatóanyagban végigvezettük a szöveges kihagyási jegyzetek dokumentumhoz való hozzáadásának folyamatán a GroupDocs.Annotation for .NET használatával. Ezekkel a lépésekkel mostantól biztonságosan kezelheti a dokumentumokban található bizalmas információkat.
## GYIK
### Testreszabhatom a szövegkihagyási megjegyzés megjelenését?
Igen, testreszabhatja a különböző tulajdonságokat, például a betűszínt, a kitöltőszínt és az átlátszóságot az igényeinek megfelelően.
### Van próbaverzió elérhető vásárlás előtt?
Igen, hozzáférhet egy ingyenes próbaverzióhoz a következő címen: [weboldal](https://releases.groupdocs.com/).
### Hogyan kaphatok támogatást, ha bármilyen problémába ütközöm?
Támogatást kaphatsz a GroupDocs.Annotation közösségi fórumon. [itt](https://forum.groupdocs.com/c/annotation/10).
### Szükségem van ideiglenes jogosítványra tesztelési célokra?
Igen, ideiglenes jogosítványt szerezhet be a [vásárlási oldal](https://purchase.groupdocs.com/temporary-license/) teszteléshez.
### Hozzáadhatok több megjegyzést egyetlen dokumentumhoz?
Természetesen a GroupDocs.Annotation lehetővé teszi különféle típusú annotációk és több példány hozzáadását egyetlen dokumentumhoz.