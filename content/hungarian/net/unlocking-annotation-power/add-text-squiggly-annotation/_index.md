---
"description": "Tanulja meg, hogyan adhat könnyedén hullámos szöveges jegyzeteket a dokumentumokhoz a Groupdocs.Annotation for .NET segítségével. Javítsa az együttműködési és dokumentum-ellenőrzési folyamatokat."
"linktitle": "Szöveges hullámos jegyzet hozzáadása a dokumentumhoz"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Szöveges hullámos jegyzet hozzáadása a dokumentumhoz"
"url": "/hu/net/unlocking-annotation-power/add-text-squiggly-annotation/"
"weight": 25
---

# Szöveges hullámos jegyzet hozzáadása a dokumentumhoz

## Bevezetés

A Groupdocs.Annotation for .NET egy sokoldalú könyvtár, amely lehetővé teszi a fejlesztők számára, hogy robusztus annotációs képességeket integráljanak .NET alkalmazásaikba. Akár PDF-ekkel, Word-dokumentumokkal vagy más népszerű fájlformátumokkal dolgozik, a Groupdocs.Annotation zökkenőmentes megoldást kínál a dokumentumokkal való együttműködés annotálására és javítására.

## Előfeltételek

Mielőtt belemerülnél az oktatóanyagba, győződj meg róla, hogy a következő előfeltételek teljesülnek:

## Névterek importálása

Győződjön meg róla, hogy importálja a szükséges névtereket a Groupdocs.Annotation for .NET által biztosított funkciók eléréséhez.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Most, hogy az előfeltételekkel tisztában vagyunk, bontsuk le a szöveges hullámos jegyzetek hozzáadásának folyamatát több lépésre.

## 1. lépés: Kimeneti útvonal meghatározása

Adja meg az elérési utat, ahová a jegyzetekkel ellátott dokumentum mentésre kerül.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 2. lépés: Annotátor inicializálása

Inicializálja az Annotator objektumot a bemeneti dokumentum elérési útjának megadásával.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ide kerül a megjegyzéskód
}
```

## 3. lépés: Hozz létre hullámos jegyzetet

Hozz létre egy SquigglyAnnotation objektumot, és add meg a tulajdonságait.

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

## 4. lépés: Jegyzet hozzáadása

Adja hozzá a létrehozott hullámos jegyzetet a dokumentumhoz.

```csharp
annotator.Add(squiggly);
```

## 5. lépés: Dokumentum mentése

Mentse el a jegyzetekkel ellátott dokumentumot a megadott kimeneti elérési útra.

```csharp
annotator.Save(outputPath);
```

## 6. lépés: Megerősítés megjelenítése

Jelenítsen meg egy üzenetet, amely megerősíti a jegyzetekkel ellátott dokumentum sikeres mentését.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés

Összefoglalva, a Groupdocs.Annotation for .NET robusztus eszközkészletet biztosít a fejlesztőknek a dokumentum-annotációs funkciók zökkenőmentes integrálásához .NET alkalmazásaikba. Ezt a lépésről lépésre szóló útmutatót követve könnyedén hozzáadhat szöveges, hullámos annotációkat a dokumentumaihoz, javítva az együttműködést és a dokumentum-ellenőrzési folyamatokat.

## GYIK

### K: A Groupdocs.Annotation támogatja a különféle fájlformátumokon lévő jegyzetek készítését?

V: Igen, a Groupdocs.Annotation számos fájlformátumon támogatja a jegyzetelést, beleértve a PDF-eket, Word-dokumentumokat, Excel-táblázatokat és egyebeket.

### K: A Groupdocs.Annotation kompatibilis mind asztali, mind webes alkalmazásokkal?

V: Teljesen biztos! A Groupdocs.Annotation zökkenőmentesen integrálható mind az asztali, mind a webes alkalmazásokba, rugalmasságot és sokoldalúságot biztosítva.

### K: Vannak-e elérhető licencelési lehetőségek a Groupdocs.Annotation-höz?

V: Igen, a Groupdocs.Annotation rugalmas licencelési lehetőségeket kínál, amelyek az egyéni vagy vállalati igényekhez igazodnak, beleértve az ideiglenes licenceket próbaverziókhoz.

### K: Testreszabhatók a Groupdocs.Annotation segítségével létrehozott annotációk?

V: Természetesen! A Groupdocs.Annotation széleskörű testreszabási lehetőségeket kínál az annotációkhoz, lehetővé téve a fejlesztők számára, hogy a saját igényeikhez igazítsák azokat.

### K: A Groupdocs.Annotation kínál-e támogatást és dokumentációt fejlesztők számára?

V: Valóban! A Groupdocs.Annotation átfogó dokumentációt és dedikált támogatási fórumokat biztosít, hogy segítse a fejlesztőket a funkcióinak hatékony kihasználásában.