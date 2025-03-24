---
title: Területi megjegyzés hozzáadása a dokumentumhoz
linktitle: Területi megjegyzés hozzáadása a dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Fokozza a dokumentumok együttműködését a Groupdocs.Annotation for .NET segítségével. Ismerje meg lépésről lépésre, hogyan adhat hozzá megjegyzéseket a területhez.
weight: 10
url: /hu/net/unlocking-annotation-power/add-area-annotation/
---
## Bevezetés
Ebben az oktatóanyagban végigvezetjük a Groupdocs.Annotation for .NET használatával területi megjegyzések hozzáadásának folyamatán. A területi megjegyzések értékes funkció, amely lehetővé teszi a felhasználók számára, hogy kiemeljék a dokumentum bizonyos területeit, egyértelművé és kontextusba helyezve a tartalmat.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:
1.  Groupdocs.Annotation for .NET: Győződjön meg arról, hogy a szükséges könyvtárak és függőségek telepítve vannak. Letöltheti őket a[weboldal](https://releases.groupdocs.com/annotation/net/).
2. Fejlesztői környezet: A .NET fejlesztéshez megfelelő fejlesztői környezetet kell beállítani.

## Névterek importálása
Kezdésként importálja a szükséges névtereket a projektbe. Ezek a névterek a megjegyzésekkel való munkavégzéshez szükséges osztályokat és metódusokat tartalmazzák.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

## 1. lépés: Inicializálja a kimeneti útvonalat
Határozza meg a kimeneti útvonalat, ahová a megjegyzésekkel ellátott dokumentum mentésre kerül.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Inicializálja az Annotátort
 Hozzon létre egy példányt a`Annotator` osztályba a dokumentum elérési útjának paraméterként való átadásával.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ide kerül a kommentár kódja
}
```
## 3. lépés: Területi megjegyzés létrehozása
Határozza meg a terület megjegyzésének tulajdonságait, például a háttér színét, pozícióját, üzenetét, átlátszatlanságát stb.
```csharp
AreaAnnotation area = new AreaAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is area annotation",
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
## 4. lépés: Megjegyzés hozzáadása
 Adja hozzá a terület megjegyzését a dokumentumhoz a gombbal`Add` módszere a`Annotator` példa.
```csharp
annotator.Add(area);
```
## 5. lépés: Mentse el a dokumentumot
Mentse a megjegyzésekkel ellátott dokumentumot a megadott kimeneti útvonalra.
```csharp
annotator.Save(outputPath);
```
## 6. lépés: Jelenítse meg a sikeres üzenetet
Tájékoztassa a felhasználót, hogy a dokumentumot sikeresen feljegyezték és elmentették.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk területi megjegyzéseket a dokumentumokhoz a Groupdocs.Annotation for .NET használatával. A lépésenkénti útmutató követésével könnyedén javíthatja dokumentumait értékes megjegyzésekkel, javítva az együttműködést és a megértést.
## GYIK
### Testreszabhatom a terület megjegyzésének megjelenését?
Igen, testreszabhat különféle szempontokat, például a háttérszínt, az átlátszatlanságot, a toll stílusát stb., hogy megfeleljen az Ön preferenciáinak.
### A Groupdocs.Annotation kompatibilis más dokumentumformátumokkal?
Igen, a Groupdocs.Annotation különféle dokumentumformátumokat támogat, beleértve a PDF, DOCX, PPTX és egyebeket.
### Hozzáadhatok több megjegyzést ugyanahhoz a dokumentumhoz?
Természetesen szükség szerint több különböző típusú megjegyzést is hozzáadhat ugyanahhoz a dokumentumhoz.
### A Groupdocs.Annotation kínál platformok közötti kompatibilitást?
Igen, a Groupdocs.Annotation kompatibilis a .NET keretrendszerrel, így alkalmas Windows, Linux és macOS fejlesztői környezetekhez.
### Létezik próbaverzió tesztelési célból?
 Igen, elérheti az ingyenes próbaverziót a[weboldal](https://releases.groupdocs.com/).