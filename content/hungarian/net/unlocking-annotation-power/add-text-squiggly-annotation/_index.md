---
title: Szövegszerű megjegyzés hozzáadása a dokumentumhoz
linktitle: Szövegszerű megjegyzés hozzáadása a dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Tanulja meg, hogyan adhat könnyedén szöveges, kacskaringós megjegyzéseket a dokumentumokhoz a Groupdocs.Annotation for .NET segítségével. Fokozza az együttműködést és a dokumentum-ellenőrzési folyamatokat.
weight: 25
url: /hu/net/unlocking-annotation-power/add-text-squiggly-annotation/
---

# Szövegszerű megjegyzés hozzáadása a dokumentumhoz

## Bevezetés

Groupdocs.Annotation for .NET egy sokoldalú könyvtár, amely lehetővé teszi a fejlesztők számára, hogy robusztus annotációs képességeket könnyedén integráljanak .NET-alkalmazásaikba. Akár PDF-ekkel, Word-dokumentumokkal vagy más népszerű fájlformátumokkal dolgozik, a Groupdocs.Annotation zökkenőmentes megoldást kínál a megjegyzések készítésére és a dokumentumokkal való együttműködés javítására.

## Előfeltételek

Mielőtt belevágna az oktatóanyagba, győződjön meg arról, hogy a következő előfeltételek teljesülnek:

## Névterek importálása

Ügyeljen arra, hogy importálja a szükséges névtereket a Groupdocs.Annotation for .NET által biztosított funkciók eléréséhez.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Most, hogy megvannak az előfeltételek, bontsuk fel több lépésre a kacskaringós szöveges megjegyzések hozzáadásának folyamatát.

## 1. lépés: Határozza meg a kimeneti útvonalat

Határozza meg az útvonalat, ahová a megjegyzésekkel ellátott dokumentum mentésre kerül.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 2. lépés: Inicializálja az Annotátort

Inicializálja az Annotátor objektumot a bemeneti dokumentum elérési útjának megadásával.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Az annotációs kód ide kerül
}
```

## 3. lépés: Hozzon létre Squiggly annotációt

Hozzon létre egy SquigglyAnnotation objektumot, és adja meg a tulajdonságait.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

Adja hozzá a létrehozott pörgős megjegyzést a dokumentumhoz.

```csharp
annotator.Add(squiggly);
```

## 5. lépés: Mentse el a dokumentumot

Mentse a megjegyzésekkel ellátott dokumentumot a megadott kimeneti útvonalra.

```csharp
annotator.Save(outputPath);
```

## 6. lépés: Megerősítés megjelenítése

Jelenítsen meg egy üzenetet, amely megerősíti a megjegyzésekkel ellátott dokumentum sikeres mentését.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés

Összefoglalva, a Groupdocs.Annotation for .NET robusztus eszközkészletet biztosít a fejlesztők számára a dokumentumfeljegyzések funkcióinak zökkenőmentes integrálásához .NET-alkalmazásaikba. Ennek a lépésről-lépésre szóló útmutatónak a követésével könnyedén adhat hozzá szöveges, kacskaringós megjegyzéseket a dokumentumokhoz, javítva az együttműködést és a dokumentum-ellenőrzési folyamatokat.

## GYIK

### K: Támogathatja-e a Groupdocs.Annotation a megjegyzéseket különféle fájlformátumokon?

V: Igen, a Groupdocs.Annotation támogatja a megjegyzések készítését a fájlformátumok széles skáláján, beleértve a PDF-eket, Word-dokumentumokat, Excel-lapokat és egyebeket.

### K: A Groupdocs.Annotation kompatibilis mind az asztali, mind a webes alkalmazásokkal?

V: Abszolút! A Groupdocs.Annotation zökkenőmentesen integrálható asztali és webes alkalmazásokba is, rugalmasságot és sokoldalúságot kínálva.

### K: Rendelkezésre állnak-e licencelési lehetőségek a Groupdocs.Annotation számára?

V: Igen, a Groupdocs.Annotation rugalmas licencelési lehetőségeket kínál az egyéni vagy vállalati igényekhez igazodva, beleértve az ideiglenes licenceket próba célból.

### K: Testreszabhatók a Groupdocs.Annotation segítségével létrehozott megjegyzések?

V: Természetesen! A Groupdocs.Annotation kiterjedt testreszabási lehetőségeket kínál a megjegyzésekhez, lehetővé téve a fejlesztők számára, hogy a megjegyzéseket saját igényeik szerint szabják.

### K: A Groupdocs.Annotation kínál támogatást és dokumentációt a fejlesztők számára?

A: Valóban! A Groupdocs.Annotation átfogó dokumentációt és dedikált támogatási fórumokat biztosít, hogy segítse a fejlesztőket a funkcióinak hatékony kihasználásában.