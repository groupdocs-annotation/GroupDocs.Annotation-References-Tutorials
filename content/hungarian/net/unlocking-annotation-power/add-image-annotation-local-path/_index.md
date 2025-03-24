---
title: Képannotáció hozzáadása a dokumentumhoz (helyi elérési út)
linktitle: Képannotáció hozzáadása a dokumentumhoz (helyi elérési út)
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan adhat hozzá képes megjegyzéseket a dokumentumokhoz a GroupDocs.Annotation for .NET segítségével. Fokozza könnyedén a dokumentumfeldolgozási képességeket.
weight: 14
url: /hu/net/unlocking-annotation-power/add-image-annotation-local-path/
---
## Bevezetés
A GroupDocs.Annotation for .NET egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára, hogy különféle típusú megjegyzéseket adhassanak a dokumentumokhoz programozottan. Ebben az oktatóanyagban megtanuljuk, hogyan adhatunk képjegyzeteket egy dokumentumhoz helyi elérési út használatával.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:
1. C# programozási nyelv alapismerete.
2. A Visual Studio telepítve van a rendszerére.
3. GroupDocs.Annotation for .NET könyvtár telepítve vagy hivatkozva a projektben.
4. Egy bemeneti dokumentum (pl. PDF) és egy képfájl megjegyzésekhez.
## Névterek importálása
Először is importálnia kell a szükséges névtereket a C# fájlba. Ezek a névterek hozzáférést biztosítanak a GroupDocs.Annotation használatához szükséges osztályokhoz és metódusokhoz.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## 1. lépés: Határozza meg a kimeneti útvonalat
Határozza meg a kimeneti útvonalat, ahová a megjegyzésekkel ellátott dokumentum mentésre kerül.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Inicializálja az Annotátort
Inicializálja az annotátort a bemeneti dokumentum elérési útjának megadásával.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Az annotációs kód ide kerül
}
```
## 3. lépés: Képannotáció létrehozása
 Hozzon létre egy példányt a`ImageAnnotation`osztályt, és adja meg tulajdonságait, például pozíciót, átlátszatlanságot, oldalszámot és képútvonalat.
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
## 4. lépés: Megjegyzés hozzáadása
 Adja hozzá a létrehozott képannotációt a dokumentumhoz a`Add` az annotátor módszere.
```csharp
annotator.Add(image);
```
## 5. lépés: Mentse el a dokumentumot
Mentse a megjegyzésekkel ellátott dokumentumot a kimeneti útvonalra.
```csharp
annotator.Save(outputPath);
```
## 6. lépés: Kimeneti útvonal megjelenítése
Jelenítsen meg egy üzenetet, amely jelzi a dokumentum sikeres mentését és a kimeneti fájl helyét.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk képjegyzeteket egy dokumentumhoz a GroupDocs.Annotation for .NET segítségével. Ha követi ezeket az egyszerű lépéseket, akkor hatékony annotációs funkciókkal bővítheti dokumentumfeldolgozási képességeit.
## GYIK
### A PDF-en kívül más dokumentumokhoz is fűzhetek megjegyzéseket?
Igen, a GroupDocs.Annotation különféle dokumentumformátumokat támogat, beleértve a Word, Excel, PowerPoint és egyebeket.
### A GroupDocs.Annotation kompatibilis a .NET Core programmal?
Igen, a GroupDocs.Annotation kompatibilis a .NET-keretrendszerrel és a .NET Core-al is.
### Testreszabhatom a kommentárok megjelenését?
Természetesen testreszabhatja a megjegyzések megjelenését, méretét, színét és egyéb tulajdonságait igényei szerint.
### A GroupDocs.Annotation támogatja-e az együttműködésen alapuló annotációt?
Igen, a GroupDocs.Annotation olyan együttműködési jegyzetelési szolgáltatásokat kínál, amelyek lehetővé teszik több felhasználó számára, hogy egyidejűleg megjegyzéseket fűzzenek a dokumentumokhoz.
### Hol találhatok további segítséget vagy támogatást?
Látogassa meg a GroupDocs.Annotation fórumot a közösség segítségéért és támogatásáért.