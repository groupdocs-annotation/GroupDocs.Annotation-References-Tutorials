---
title: Szöveg áthúzott megjegyzés hozzáadása a dokumentumhoz
linktitle: Szöveg áthúzott megjegyzés hozzáadása a dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan adhat szöveges áthúzott megjegyzéseket a dokumentumokhoz a GroupDocs.Annotation for .NET használatával. Hatékonyan fokozza az együttműködést és a dokumentum-ellenőrzési folyamatokat.
weight: 26
url: /hu/net/unlocking-annotation-power/add-text-strikeout-annotation/
---

# Szöveg áthúzott megjegyzés hozzáadása a dokumentumhoz

## Bevezetés
Ebben az oktatóanyagban megvizsgáljuk, hogyan adhatunk áthúzott szöveges megjegyzést egy dokumentumhoz a GroupDocs.Annotation for .NET segítségével. Ez a könyvtár hatékony eszközöket biztosít a különféle dokumentumtípusok megjegyzéseihez, az együttműködés és a dokumentum-ellenőrzési folyamatok javításához.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:
1.  GroupDocs.Annotation for .NET: Telepítse a könyvtárat. Letöltheti innen[itt](https://releases.groupdocs.com/annotation/net/).
2. Fejlesztői környezet: Állítson be megfelelő fejlesztői környezetet a .NET fejlesztéshez.
3. Dokumentum: Készítsen jegyzetekkel ellátott dokumentumot, például PDF-fájlt.

## Névterek importálása
Először is importálja a szükséges névtereket a GroupDocs funkcióinak eléréséhez.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Most bontsuk fel több lépésre a szöveges áthúzásos megjegyzés hozzáadásának folyamatát:
## 1. lépés: Határozza meg a kimeneti útvonalat
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Itt határozzuk meg a kimeneti útvonalat, ahová a megjegyzésekkel ellátott dokumentum mentésre kerül.
## 2. lépés: Inicializálja az Annotátort
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Inicializálja az Annotátor objektumot a bemeneti dokumentum elérési útjának megadásával (ebben az esetben PDF fájl).
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
Hozzon létre egy StrikeoutAnnotation objektumot a kívánt tulajdonságokkal, például üzenet, átlátszatlanság, oldalszám, háttérszín, pontok (koordináták) és válaszok.
## 4. lépés: Megjegyzés hozzáadása
```csharp
annotator.Add(strikeout);
```
Adja hozzá a létrehozott áthúzott megjegyzést a dokumentumhoz.
## 5. lépés: Mentse el a dokumentumot
```csharp
annotator.Save(outputPath);
```
Mentse a megjegyzésekkel ellátott dokumentumot a megadott kimeneti útvonalra.

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk áthúzott szöveges megjegyzést egy dokumentumhoz a GroupDocs.Annotation for .NET segítségével. Ez a hatékony könyvtár lehetővé teszi a hatékony dokumentumjegyzetek készítését, javítva az együttműködést és a dokumentum-ellenőrzési folyamatokat.
## GYIK
### A GroupDocs.Annotation kompatibilis a különböző dokumentumformátumokkal?
Igen, a GroupDocs.Annotation a dokumentumformátumok széles skáláját támogatja, beleértve a PDF, Word, Excel, PowerPoint és egyebeket.
### Testreszabhatom a kommentárok megjelenését?
Természetesen testreszabhatja a megjegyzések tulajdonságait, például a színt, az átlátszatlanságot, a betűméretet és egyebeket az igényei szerint.
### A GroupDocs.Annotation biztosít együttműködési szolgáltatásokat?
Igen, a GroupDocs.Annotation megkönnyíti az együttműködést azáltal, hogy a felhasználók megjegyzéseket, válaszokat és megjegyzéseket adhatnak a dokumentumokhoz.
### Van ingyenes próbaverzió?
 Igen, igénybe veheti az ingyenes próbaverziót innen[itt](https://releases.groupdocs.com/).
### Hol kaphatok támogatást a GroupDocs.Annotation-hoz?
 Támogatást kaphat a[GroupDocs.Annotation fórum](https://forum.groupdocs.com/c/annotation/10).