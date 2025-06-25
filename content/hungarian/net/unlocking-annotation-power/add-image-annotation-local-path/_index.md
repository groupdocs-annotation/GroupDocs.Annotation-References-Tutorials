---
"description": "Ismerje meg, hogyan adhat hozzá képaláírásokat dokumentumokhoz a GroupDocs.Annotation for .NET segítségével. Bővítse dokumentumfeldolgozási képességeit könnyedén."
"linktitle": "Képhozzáfűzés hozzáadása a dokumentumhoz (helyi elérési út)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Képhozzáfűzés hozzáadása a dokumentumhoz (helyi elérési út)"
"url": "/hu/net/unlocking-annotation-power/add-image-annotation-local-path/"
"weight": 14
---

# Képhozzáfűzés hozzáadása a dokumentumhoz (helyi elérési út)

## Bevezetés
A GroupDocs.Annotation for .NET egy hatékony függvénykönyvtár, amely lehetővé teszi a fejlesztők számára, hogy programozottan adjanak hozzá különféle típusú megjegyzéseket a dokumentumokhoz. Ebben az oktatóanyagban megtanuljuk, hogyan adhatunk hozzá képannotációkat egy dokumentumhoz egy helyi elérési út használatával.
## Előfeltételek
Mielőtt elkezdenénk, győződjünk meg arról, hogy a következő előfeltételek teljesülnek:
1. C# programozási nyelv alapismerete.
2. Visual Studio telepítve a rendszeredre.
3. A GroupDocs.Annotation for .NET könyvtár telepítve van, vagy a tutorialsd fájl a projektedben van.
4. Egy bemeneti dokumentum (pl. PDF) és egy képfájl annotációhoz.
## Névterek importálása
Először importálnod kell a szükséges névtereket a C# fájlodba. Ezek a névterek hozzáférést biztosítanak a GroupDocs.Annotation használatához szükséges osztályokhoz és metódusokhoz.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## 1. lépés: Kimeneti útvonal meghatározása
Adja meg a kimeneti elérési utat, ahová a jegyzetekkel ellátott dokumentum mentésre kerül.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Annotátor inicializálása
Inicializálja az annotátort a bemeneti dokumentum elérési útjának megadásával.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ide kerül a megjegyzéskód
}
```
## 3. lépés: Képhozzáfűzés létrehozása
Hozz létre egy példányt a `ImageAnnotation` osztályt, és adja meg a tulajdonságait, például a pozíciót, az átlátszóságot, az oldalszámot és a kép elérési útját.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## 4. lépés: Jegyzet hozzáadása
Adja hozzá a létrehozott képjegyzetet a dokumentumhoz a `Add` az annotátor módszere.
```csharp
annotator.Add(image);
```
## 5. lépés: Dokumentum mentése
Mentse el a jegyzetekkel ellátott dokumentumot a kimeneti útvonalra.
```csharp
annotator.Save(outputPath);
```
## 6. lépés: Kimeneti útvonal megjelenítése
Jelenítsen meg egy üzenetet, amely jelzi a dokumentum sikeres mentését és a kimeneti fájl helyét.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk hozzá képaláírásokat egy dokumentumhoz a GroupDocs.Annotation for .NET használatával. Ezeket az egyszerű lépéseket követve hatékony annotációs funkciókkal bővítheti dokumentumfeldolgozási képességeit.
## GYIK
### PDF-en kívül más dokumentumokat is elláthatok jegyzetekkel?
Igen, a GroupDocs.Annotation számos dokumentumformátumot támogat, beleértve a Wordöt, az Excelt, a PowerPointot és egyebeket.
### Kompatibilis a GroupDocs.Annotation a .NET Core-ral?
Igen, a GroupDocs.Annotation kompatibilis mind a .NET Framework, mind a .NET Core rendszerrel.
### Testreszabhatom a megjegyzések megjelenését?
Természetesen testreszabhatja a megjegyzések megjelenését, méretét, színét és egyéb tulajdonságait az igényei szerint.
### A GroupDocs.Annotation támogatja az együttműködésen alapuló annotációkat?
Igen, a GroupDocs.Annotation közös annotációs funkciókat kínál, amelyek lehetővé teszik, hogy több felhasználó egyszerre lásson el jegyzeteket a dokumentumokban.
### Hol találok további segítséget vagy támogatást?
közösség segítségét és támogatását a GroupDocs.Annotation fórumon találod.