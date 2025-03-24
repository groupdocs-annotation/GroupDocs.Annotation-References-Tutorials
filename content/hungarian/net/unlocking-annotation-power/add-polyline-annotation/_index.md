---
title: Vonallánc megjegyzés hozzáadása a dokumentumhoz
linktitle: Vonallánc megjegyzés hozzáadása a dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan adhat hozzá vonallánc megjegyzéseket a dokumentumokhoz a GroupDocs.Annotation for .NET segítségével. Fokozza az együttműködést és a dokumentum-ellenőrzési folyamatokat könnyedén.
weight: 18
url: /hu/net/unlocking-annotation-power/add-polyline-annotation/
---

# Vonallánc megjegyzés hozzáadása a dokumentumhoz

## Bevezetés
A GroupDocs.Annotation for .NET egy hatékony eszköz, amellyel a fejlesztők programozottan megjegyzéseket fűzhetnek PDF és Microsoft Office dokumentumokhoz. Jellemzői közé tartozik az a képesség, hogy vonalláncos megjegyzéseket adjon a dokumentumokhoz, javítva az együttműködést és a dokumentum-ellenőrzési folyamatokat.
## Előfeltételek
Mielőtt folytatná ezt az oktatóanyagot, győződjön meg arról, hogy rendelkezik a következőkkel:
- A Visual Studio telepítve van a rendszerére.
- C# programozási nyelv alapismerete.
-  GroupDocs.Annotation for .NET könyvtár telepítve. Letöltheti innen[itt](https://releases.groupdocs.com/annotation/net/).

## Névterek importálása
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1. lépés: Határozza meg a kimeneti útvonalat
Először határozza meg a kimeneti útvonalat, ahová a megjegyzésekkel ellátott dokumentum mentésre kerül.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Inicializálja az Annotátort
Inicializálja az annotátort a bemeneti dokumentum nevének megadásával.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 3. lépés: Vonallánc megjegyzés objektum létrehozása
Hozzon létre egy vonallánc megjegyzés objektumot, és állítsa be tulajdonságait, például pozíciót, üzenetet, átlátszatlanságot, tollszínt, tollstílust és tollszélességet.
```csharp
PolylineAnnotation polyline = new PolylineAnnotation
{
    Box = new Rectangle(250, 35, 102, 12),
    CreatedOn = DateTime.Now,
    Message = "This is polyline annotation",
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
    },
    SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.698685
4460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
};
```
## 4. lépés: Vonallánc megjegyzés hozzáadása
Adja hozzá a vonallánc megjegyzést a dokumentumhoz az annotátor objektum segítségével.
```csharp
annotator.Add(polyline);
```
## 5. lépés: Mentse el a dokumentumot
Mentse a megjegyzésekkel ellátott dokumentumot a megadott kimeneti útvonalra.
```csharp
annotator.Save(outputPath);
```
## 6. lépés: Jelenítse meg a sikeres üzenetet
Jelenítsen meg egy üzenetet, amely megerősíti a dokumentum sikeres mentését.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk vonallánc megjegyzést egy dokumentumhoz a GroupDocs.Annotation for .NET segítségével. Ez a funkció javítja az együttműködési és a dokumentum-ellenőrzési folyamatokat, megkönnyítve a felhasználók számára a visszajelzések és javaslatok hatékony kommunikációját.
## GYIK
### A GroupDocs.Annotation for .NET kompatibilis az összes dokumentumformátummal?
A GroupDocs.Annotation for .NET támogatja az olyan népszerű dokumentumformátumokat, mint a PDF és a Microsoft Office formátumok, köztük a Word, az Excel és a PowerPoint.
### Testreszabhatom a kommentárok megjelenését?
Igen, testreszabhatja a megjegyzések különféle tulajdonságait, például színt, átlátszatlanságot, stílust és szélességet az igényeinek megfelelően.
### A GroupDocs.Annotation for .NET ingyenes próbaverziót kínál?
 Igen, igénybe veheti a GroupDocs.Annotation ingyenes próbaverzióját .NET-hez, ha felkeresi[ez a link](https://releases.groupdocs.com/).
### Hol találom a GroupDocs.Annotation for .NET dokumentációját?
 A GroupDocs.Annotation for .NET dokumentációja megtalálható[itt](https://tutorials.groupdocs.com/annotation/net/).
### Hogyan kaphatok támogatást a GroupDocs.Annotation for .NET-hez kapcsolódó problémákhoz vagy lekérdezésekhez?
 Támogatást kaphat a GroupDocs.Annotation fórumon[itt](https://forum.groupdocs.com/c/annotation/10).