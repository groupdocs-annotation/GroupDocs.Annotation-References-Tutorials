---
title: Helyezze a kép megjegyzést a szöveg fölé
linktitle: Helyezze a kép megjegyzést a szöveg fölé
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan adhat hozzá képjegyzeteket szöveghez a .NET-ben a GroupDocs.Annotation segítségével a hatékony dokumentumkezelés és együttműködés érdekében.
weight: 21
url: /hu/net/advanced-usage/put-image-annotation-over-text/
---

# Helyezze a kép megjegyzést a szöveg fölé

## Bevezetés
.NET-fejlesztés világában a GroupDocs.Annotation hatékony megoldást kínál megjegyzések hozzáadására a dokumentumokhoz, így hatékonyabbá téve az együttműködést és a dokumentumkezelést. Az egyik gyakori követelmény a képfeljegyzések szöveg fölé helyezése, amely zökkenőmentesen megvalósítható a GroupDocs.Annotation for .NET használatával.
## Előfeltételek
Mielőtt belemerülne abba a folyamatba, hogy a GroupDocs.Annotation for .NET segítségével képfeljegyzéseket helyezzen el a szöveg felett, győződjön meg arról, hogy rendelkezik a következőkkel:
1.  GroupDocs.Annotation for .NET Library: Töltse le és telepítse a könyvtárat innen[itt](https://releases.groupdocs.com/annotation/net/).
2. Fejlesztői környezet: Állítson be megfelelő fejlesztői környezetet, például a Visual Studio-t vagy bármely más .NET IDE-t.
3. Dokumentum- és képfájlok: Készítse elő a dokumentumfájlt (PDF, DOCX stb.) és a megjegyzésekhez használni kívánt képfájlt.
4. A C# alapvető ismerete: A C# programozási nyelv ismerete szükséges az oktatóanyagban található kódrészletek megvalósításához.

## Névterek importálása
Mielőtt folytatná az annotációs folyamatot, győződjön meg róla, hogy importálja a szükséges névtereket a C# projektbe:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## 1. lépés: Határozza meg a kimeneti útvonalat
Először határozza meg a kimeneti útvonalat, ahová a megjegyzésekkel ellátott dokumentumot menti:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## 2. lépés: Inicializálja az Annotátort
 Inicializálja a`Annotator` objektum a bemeneti dokumentum elérési útjának megadásával:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ide kerül a kommentár kódja
}
```
## 3. lépés: Képannotáció létrehozása
 Hozzon létre egy`ImageAnnotation` objektum a kívánt tulajdonságokkal, például dobozméretekkel, átlátszatlansággal, oldalszámmal, képútvonallal és z-indexszel:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## 4. lépés: Megjegyzés hozzáadása
 Adja hozzá a képjegyzetet a dokumentumhoz a gombbal`Add` módszere a`Annotator` tárgy:
```csharp
annotator.Add(image);
```
## 5. lépés: Mentse el a megjegyzésekkel ellátott dokumentumot
Mentse el a megjegyzésekkel ellátott dokumentumot a megadott kimeneti útvonalra:
```csharp
annotator.Save(outputPath);
```
## 6. lépés: Jelenítse meg a sikeres üzenetet
Jelenítse meg a sikeres üzenetet a megjegyzésekkel ellátott dokumentum elérési útjával:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés
Összefoglalva, a képfeljegyzések hozzáadása a szöveghez a .NET-alkalmazásokban a GroupDocs.Annotation használatával egyszerű folyamat. Az ebben az oktatóanyagban található, lépésenkénti útmutatót követve hatékonyan fűzhet megjegyzéseket a dokumentumokhoz, valamint javíthatja az együttműködési és dokumentumkezelési képességeket .NET-projektjeiben.
## GYIK
### PDF-eken kívül más dokumentumokhoz is fűzhetek megjegyzéseket?
Igen, a GroupDocs.Annotation különféle dokumentumformátumokat támogat, például DOCX, XLSX, PPTX stb.
### Van ingyenes próbaverzió a GroupDocs.Annotation számára?
 Igen, letölthet egy ingyenes próbaverziót a webhelyről[itt](https://releases.groupdocs.com/).
### Hogyan kaphatok támogatást a GroupDocs.Annotation programhoz?
 Támogatást a GroupDocs.Annotation közösségi fórumtól kaphat[itt](https://forum.groupdocs.com/c/annotation/10).
### Szükségem van ideiglenes licencre tesztelés céljából?
 Igen, ideiglenes engedélyt szerezhetsz innen[itt](https://purchase.groupdocs.com/temporary-license/) tesztelési célokra.
### Testreszabhatom a kommentárok megjelenését?
Igen, a GroupDocs.Annotation számos lehetőséget kínál a megjegyzések megjelenésének testreszabására, például színre, átlátszatlanságra, betűméretre stb.