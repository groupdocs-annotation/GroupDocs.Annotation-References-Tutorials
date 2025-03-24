---
title: Távolság megjegyzés hozzáadása a dokumentumhoz
linktitle: Távolság megjegyzés hozzáadása a dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan adhat hozzá távolságjegyzeteket a dokumentumokhoz a GroupDocs.Annotation for .NET segítségével. Fokozza az együttműködést és a kommunikációt erőfeszítés nélkül.
weight: 12
url: /hu/net/unlocking-annotation-power/add-distance-annotation/
---
## Bevezetés
Ebből az oktatóanyagból megtudhatja, hogyan adhat hozzá távolsági megjegyzést egy dokumentumhoz a GroupDocs.Annotation for .NET segítségével. A feladat végrehajtásához kövesse az alábbi lépéseket:
## Előfeltételek

A folytatás előtt győződjön meg arról, hogy a következő előfeltételek teljesülnek:

-  GroupDocs.Annotation for .NET Library: Töltse le és telepítse a GroupDocs.Annotation for .NET könyvtárat innen:[ez a link](https://releases.groupdocs.com/annotation/net/).
- Annotálandó dokumentum: Készítse elő azt a dokumentumot (pl. PDF), amelyhez a távolság megjegyzését hozzá kívánja adni.
- Fejlesztési környezet: Állítsa be fejlesztői környezetét a Visual Studio vagy bármely más választott IDE segítségével.

## Névterek importálása

Mielőtt elkezdené, győződjön meg arról, hogy a szükséges névtereket tartalmazza a kódban. Ezek a névterek elengedhetetlenek a szükséges osztályok és metódusok eléréséhez.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## 1. lépés: Inicializálja az Annotátort

 Kezdje a`Annotator` objektumot a megjegyzésekkel ellátni kívánt dokumentum elérési útjával.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ide kerül a kommentár kódja
}
```

## 2. lépés: Hozzon létre távolsági megjegyzést

 Most hozzon létre a`DistanceAnnotation` objektumot, és konfigurálja tulajdonságait, például a doboz méreteit, üzenetét, átlátszatlanságát, tollszínét stb.

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

## 3. lépés: Megjegyzés hozzáadása

 Adja hozzá a létrehozott távolság megjegyzést a dokumentumhoz a`Add` az annotátor objektum metódusa.

```csharp
annotator.Add(distance);
```

## 4. lépés: Mentse el a dokumentumot

Mentse el a megjegyzésekkel ellátott dokumentumot a rendszer kívánt helyére.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## 5. lépés: Megerősítés megjelenítése

Végül jelenítsen meg egy üzenetet, amely megerősíti a megjegyzésekkel ellátott dokumentum sikeres mentését.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés

A távolsági megjegyzések hozzáadása a dokumentumokhoz a GroupDocs.Annotation for .NET segítségével egyszerű folyamat. Az ebben az oktatóanyagban vázolt lépések követésével értékes megjegyzésekkel bővítheti dokumentumait, megkönnyítve az együttműködést és a kommunikációt.

## GYIK

### K: Testreszabhatom a távolság megjegyzésének megjelenését?

V: Igen, testreszabhat különféle tulajdonságokat, például színt, átlátszatlanságot, vonalstílust stb., hogy megfeleljen az Ön igényeinek.

### K: A GroupDocs.Annotation támogatja a megjegyzéseket a különböző típusú dokumentumokon?

V: Igen, a GroupDocs.Annotation támogatja a megjegyzéseket a dokumentumformátumok széles skáláján, beleértve a PDF, Word, Excel, PowerPoint és egyebeket.

### K: Van ingyenes próbaverzió a GroupDocs.Annotation számára?

 V: Igen, elérheti a GroupDocs.Annotation ingyenes próbaverzióját innen[ez a link](https://releases.groupdocs.com/).

### K: Hol találom a GroupDocs.Annotation for .NET dokumentációját?

 V: Tekintse meg a rendelkezésre álló részletes dokumentációt[itt](https://tutorials.groupdocs.com/annotation/net/).

### K: Hogyan kaphatok támogatást vagy segítséget a GroupDocs.Annotation-hoz?

 V: Támogatást és segítséget kérhet a GroupDocs.Annotation közösségi fórumtól[itt](https://forum.groupdocs.com/c/annotation/10).