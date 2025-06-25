---
"description": "Tanulja meg, hogyan adhat hozzá szöveges áthúzott megjegyzéseket dokumentumokhoz a GroupDocs.Annotation for .NET segítségével. Hatékonyan javítsa az együttműködési és dokumentum-ellenőrzési folyamatokat."
"linktitle": "Szöveg áthúzott megjegyzés hozzáadása a dokumentumhoz"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Szöveg áthúzott megjegyzés hozzáadása a dokumentumhoz"
"url": "/hu/net/unlocking-annotation-power/add-text-strikeout-annotation/"
"weight": 26
---

# Szöveg áthúzott megjegyzés hozzáadása a dokumentumhoz

## Bevezetés
Ebben az oktatóanyagban azt vizsgáljuk meg, hogyan adhatunk hozzá szöveges áthúzott jegyzeteket egy dokumentumhoz a GroupDocs.Annotation for .NET használatával. Ez a könyvtár hatékony eszközöket biztosít különféle dokumentumtípusok jegyzeteléséhez, az együttműködés és a dokumentumok áttekintésének folyamatainak javításához.
## Előfeltételek
Mielőtt elkezdenénk, győződjünk meg arról, hogy a következő előfeltételekkel rendelkezünk:
1. GroupDocs.Annotation .NET-hez: Telepítse a könyvtárat. Letöltheti innen: [itt](https://releases.groupdocs.com/annotation/net/).
2. Fejlesztői környezet: Hozzon létre egy megfelelő fejlesztői környezetet a .NET fejlesztéséhez.
3. Dokumentum: Készítsen elő egy jegyzeteléshez előkészített dokumentumot, például egy PDF-fájlt.

## Névterek importálása
Először importálja a szükséges névtereket a GroupDocs.Annotation funkcióinak eléréséhez:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Most bontsuk le a szöveges áthúzott jegyzet hozzáadásának folyamatát több lépésre:
## 1. lépés: Kimeneti útvonal meghatározása
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Itt definiáljuk a kimeneti elérési utat, ahová a jegyzetekkel ellátott dokumentum mentésre kerül.
## 2. lépés: Annotátor inicializálása
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Inicializálja az Annotator objektumot a bemeneti dokumentum (jelen esetben PDF fájl) elérési útjának megadásával.
## 3. lépés: Áthúzott megjegyzés létrehozása
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
Hozz létre egy StrikeoutAnnotation objektumot a kívánt tulajdonságokkal, például üzenettel, átlátszósággal, oldalszámmal, háttérszínnel, pontokkal (koordinátákkal) és válaszokkal.
## 4. lépés: Jegyzet hozzáadása
```csharp
annotator.Add(strikeout);
```
Adja hozzá a létrehozott áthúzott megjegyzést a dokumentumhoz.
## 5. lépés: Dokumentum mentése
```csharp
annotator.Save(outputPath);
```
Mentse el a jegyzetekkel ellátott dokumentumot a megadott kimeneti elérési útra.

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk hozzá szöveges áthúzott jegyzeteket egy dokumentumhoz a GroupDocs.Annotation for .NET használatával. Ez a hatékony könyvtár lehetővé teszi a hatékony dokumentum-jegyzetelést, javítva az együttműködést és a dokumentum-áttekintési folyamatokat.
## GYIK
### Kompatibilis a GroupDocs.Annotation különböző dokumentumformátumokkal?
Igen, a GroupDocs.Annotation számos dokumentumformátumot támogat, beleértve a PDF, Word, Excel, PowerPoint és egyebeket.
### Testreszabhatom a megjegyzések megjelenését?
Természetesen testreszabhatja a megjegyzések tulajdonságait, például a színt, az átlátszóságot, a betűméretet és egyebeket az igényei szerint.
### A GroupDocs.Annotation biztosít együttműködési funkciókat?
Igen, a GroupDocs.Annotation megkönnyíti az együttműködést azáltal, hogy lehetővé teszi a felhasználók számára, hogy megjegyzéseket, válaszokat és jegyzeteket fűzzenek a dokumentumokhoz.
### Van elérhető ingyenes próbaverzió?
Igen, igénybe vehet egy ingyenes próbaverziót a következő címen: [itt](https://releases.groupdocs.com/).
### Hol kaphatok támogatást a GroupDocs.Annotation-höz?
Támogatást kaphatsz a [GroupDocs.Annotation fórum](https://forum.groupdocs.com/c/annotation/10).