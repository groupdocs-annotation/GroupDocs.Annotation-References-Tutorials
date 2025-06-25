---
"description": "Tanulja meg, hogyan adhat hozzá távolságmegjegyzéseket dokumentumokhoz a GroupDocs.Annotation for .NET segítségével. Könnyedén javíthatja az együttműködést és a kommunikációt."
"linktitle": "Távolság megjegyzés hozzáadása a dokumentumhoz"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Távolság megjegyzés hozzáadása a dokumentumhoz"
"url": "/hu/net/unlocking-annotation-power/add-distance-annotation/"
"weight": 12
---

# Távolság megjegyzés hozzáadása a dokumentumhoz

## Bevezetés
Ebben az oktatóanyagban megtanulod, hogyan adhatsz hozzá távolságmegjegyzést egy dokumentumhoz a GroupDocs.Annotation for .NET használatával. A feladat végrehajtásához kövesd az alábbi lépéseket:
## Előfeltételek

A folytatás előtt győződjön meg arról, hogy a következő előfeltételek teljesülnek:

- GroupDocs.Annotation for .NET könyvtár: Töltse le és telepítse a GroupDocs.Annotation for .NET könyvtárat innen: [ezt a linket](https://releases.groupdocs.com/annotation/net/).
- Jegyzetelendő dokumentum: Készítse elő a dokumentumot (pl. PDF), amelyhez a távolságjegyzetet hozzá szeretné adni.
- Fejlesztői környezet: Állítsa be fejlesztői környezetét a Visual Studio vagy bármely más, Ön által választott IDE segítségével.

## Névterek importálása

Mielőtt elkezdenéd, győződj meg róla, hogy a kódodban szerepelnek a szükséges névterek. Ezek a névterek elengedhetetlenek a szükséges osztályok és metódusok eléréséhez.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## 1. lépés: Annotátor inicializálása

Kezdje az inicializálással `Annotator` objektumot a jegyzettel ellátni kívánt dokumentum elérési útjával.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ide fog kerülni a megjegyzéskód
}
```

## 2. lépés: Távolságjelölés létrehozása

Most hozz létre egy `DistanceAnnotation` objektumot, és konfigurálja a tulajdonságait, például a doboz méreteit, az üzenetet, az átlátszóságot, a toll színét stb.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
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

## 3. lépés: Jegyzet hozzáadása

Adja hozzá a létrehozott távolságmegjegyzést a dokumentumhoz a `Add` az annotátor objektum metódusa.

```csharp
annotator.Add(distance);
```

## 4. lépés: Dokumentum mentése

Mentse el a jegyzetekkel ellátott dokumentumot a rendszer kívánt helyére.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## 5. lépés: Megerősítés megjelenítése

Végül jelenítsen meg egy üzenetet, amely megerősíti a jegyzetekkel ellátott dokumentum sikeres mentését.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés

GroupDocs.Annotation for .NET használatával távolságmegjegyzések hozzáadása dokumentumokhoz egyszerű folyamat. Az ebben az oktatóanyagban ismertetett lépéseket követve értékes megjegyzésekkel gazdagíthatja dokumentumait, elősegítve a jobb együttműködést és kommunikációt.

## GYIK

### K: Testreszabhatom a távolságmegjegyzés megjelenését?

V: Igen, testreszabhatja a különböző tulajdonságokat, például a színt, az átlátszóságot, a vonalstílust stb. az igényeinek megfelelően.

### K: A GroupDocs.Annotation támogatja a különböző típusú dokumentumokon lévő jegyzeteket?

V: Igen, a GroupDocs.Annotation számos dokumentumformátumban támogatja a jegyzetek készítését, beleértve a PDF, Word, Excel, PowerPoint és egyebeket.

### K: Van elérhető ingyenes próbaverzió a GroupDocs.Annotation-höz?

V: Igen, hozzáférhet a GroupDocs.Annotation ingyenes próbaverziójához innen: [ezt a linket](https://releases.groupdocs.com/).

### K: Hol találom a GroupDocs.Annotation for .NET dokumentációját?

V: A részletes dokumentációt megtekintheti [itt](https://tutorials.groupdocs.com/annotation/net/).

### K: Hogyan kaphatok támogatást vagy segítséget a GroupDocs.Annotationhoz?

V: Támogatást és segítséget kérhet a GroupDocs.Annotation közösségi fórumon. [itt](https://forum.groupdocs.com/c/annotation/10).