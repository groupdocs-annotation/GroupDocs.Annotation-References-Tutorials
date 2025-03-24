---
title: Szövegmező megjegyzés hozzáadása a dokumentumhoz
linktitle: Szövegmező megjegyzés hozzáadása a dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan integrálhatja zökkenőmentesen szövegmezős megjegyzéseket .NET-alkalmazásaiba a Groupdocs.Annotation for .NET segítségével.
weight: 21
url: /hu/net/unlocking-annotation-power/add-text-field-annotation/
---

# Szövegmező megjegyzés hozzáadása a dokumentumhoz

## Bevezetés
Groupdocs.Annotation for .NET egy hatékony eszköz, amely lehetővé teszi a fejlesztők számára, hogy annotációs funkciókat könnyedén adják hozzá .NET-alkalmazásaikhoz. Függetlenül attól, hogy dokumentumkezelő rendszeren, együttműködési platformon vagy bármely olyan alkalmazáson dolgozik, ahol elengedhetetlen a dokumentumok megjegyzése, a Groupdocs.Annotation leegyszerűsíti a folyamatot átfogó szolgáltatáskészletével és intuitív API-jával.
Ebben az oktatóanyagban a Groupdocs.Annotation for .NET egyik alapvető funkciójával foglalkozunk: szövegmező-annotáció hozzáadása a dokumentumhoz. Ennek a lépésenkénti útmutatónak a követésével megtanulhatja, hogyan integrálhatja zökkenőmentesen a szövegmezős megjegyzéseket .NET-alkalmazásaiba, javítva a felhasználói élményt és az együttműködési lehetőségeket.
## Előfeltételek
Mielőtt belemerülne a megvalósításba, győződjön meg arról, hogy a következő előfeltételekkel rendelkezik:
### 1. A Groupdocs.Annotation telepítése .NET-hez
 Mindenekelőtt le kell töltenie és telepítenie kell a Groupdocs.Annotation for .NET programot. A letöltési linket megtalálod[itt](https://releases.groupdocs.com/annotation/net/) . Kövesse a dokumentációban található telepítési utasításokat[itt](https://tutorials.groupdocs.com/annotation/net/) a könyvtár helyes beállításához.
### 2. Fejlesztői környezet beállítása
Győződjön meg arról, hogy be van állítva egy fejlesztői környezet a .NET fejlesztéshez. Ez magában foglalja a kompatibilis IDE, például a Visual Studio és a .NET-keretrendszer telepítését a rendszeren.
### 3. A C# programozás alapjai
Ismerkedjen meg a C# programozási nyelv alapjaival, mivel ebben az oktatóanyagban C# kódot kell írni a szövegmezők megjegyzéseinek integrálásához.

## Névterek importálása
A C# projektben kezdje a szükséges névterek importálásával a Groupdocs.Annotation funkciók használatához.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Most folytassuk egy szövegmezős megjegyzés hozzáadásával egy dokumentumhoz a Groupdocs.Annotation for .NET segítségével.
## 1. lépés: Határozza meg a kimeneti útvonalat
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Inicializálja az Annotátort
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 3. lépés: Hozzon létre TextFieldAnnotation objektumot
```csharp
TextFieldAnnotation textField = new TextFieldAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Text = "Some text",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is text field annotation",
    Opacity = 0.7,
    PageNumber = 0,
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
## 4. lépés: Megjegyzés hozzáadása a dokumentumhoz
```csharp
annotator.Add(textField);
```
## 5. lépés: Mentse el a dokumentumot megjegyzéssel
```csharp
annotator.Save(outputPath);
```
## 6. lépés: Jelenítse meg a sikeres üzenetet
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés
Összefoglalva, a szövegmezős megjegyzések integrálása a .NET-alkalmazásokba a Groupdocs.Annotation for .NET használatával egyszerű folyamat. Az oktatóanyagban ismertetett lépések követésével zökkenőmentesen javíthatja a dokumentumokkal való együttműködést és a felhasználói interakciót az alkalmazásokon belül.
## GYIK
### Testreszabhatom a szövegmezős megjegyzések megjelenését?
Igen, igényei szerint testreszabhatja a különféle attribútumokat, például a háttérszínt, a betűméretet, az átlátszatlanságot stb.
### A Groupdocs.Annotation for .NET kompatibilis a különböző dokumentumformátumokkal?
Igen, a Groupdocs.Annotation a dokumentumformátumok széles skáláját támogatja, beleértve a PDF, DOCX, PPTX, XLSX és egyebeket.
### Hozzáadhatok több megjegyzést ugyanahhoz a dokumentumhoz?
Természetesen több különböző típusú megjegyzést is hozzáadhat ugyanahhoz a dokumentumhoz, lehetővé téve a dokumentumok gazdag interakcióját.
### Létezik próbaverzió a Groupdocs.Annotation for .NET számára?
 Igen, felfedezheti a Groupdocs.Annotation szolgáltatásait, ha belép az ingyenes próbaverzióba[itt](https://releases.groupdocs.com/).
### Hol találok támogatást a Groupdocs.Annotation for .NET számára?
 A Groupdocs.Annotation fórumon segítséget találhat és kapcsolatba léphet a közösséggel[itt](https://forum.groupdocs.com/c/annotation/10).