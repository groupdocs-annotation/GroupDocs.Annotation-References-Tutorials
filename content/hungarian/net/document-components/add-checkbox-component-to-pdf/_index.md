---
title: Jelölőnégyzet-összetevő hozzáadása a PDF-dokumentumhoz
linktitle: Jelölőnégyzet-összetevő hozzáadása a PDF-dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan adhat hozzá jelölőnégyzet-összetevőt PDF-dokumentumokhoz a Groupdocs.Annotation for .NET segítségével. Növelje PDF-fájljait interaktív elemekkel.
type: docs
weight: 11
url: /hu/net/document-components/add-checkbox-component-to-pdf/
---
## Bevezetés
Ebben az oktatóanyagban végigvezetjük a jelölőnégyzet-összetevő PDF-dokumentumhoz való hozzáadásának folyamatán a Groupdocs.Annotation for .NET segítségével.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:
1.  Groupdocs.Annotation for .NET SDK: Letöltheti innen[itt](https://releases.groupdocs.com/annotation/net/).
2. Fejlesztői környezet: Győződjön meg arról, hogy be van állítva .NET fejlesztői környezet.

## Névterek importálása
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
Most bontsuk fel a példát több lépésre:
## 1. lépés: Határozza meg a kimeneti útvonalat
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Itt határozzuk meg a kimeneti útvonalat, ahová a módosított PDF-dokumentum mentésre kerül.
## 2. lépés: Inicializálja az Annotátort
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Inicializálja a`Annotator` objektumot a bemeneti PDF dokumentum elérési útjának átadásával.
## 3. lépés: Jelölőnégyzet-összetevő létrehozása
```csharp
CheckBoxComponent checkBox = new CheckBoxComponent
{
    Checked = true,
    Box = new Rectangle(100, 100, 100, 100),
    PenColor = 65535,
    Style = BoxStyle.Star,
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
 Hozzon létre egy`CheckBoxComponent` objektumot, és testreszabhatja annak tulajdonságait, mint pl`Checked`, `Box` méretek,`PenColor`, `Style`és adj hozzá néhány választ.
## 4. lépés: Adjon hozzá jelölőnégyzet-összetevőt
```csharp
annotator.Add(checkBox);
```
Adja hozzá a létrehozott jelölőnégyzet összetevőt a PDF-dokumentumhoz.
## 5. lépés: Mentse el a dokumentumot
```csharp
annotator.Save("result.pdf");
```
Mentse el a módosított PDF dokumentumot a jelölőnégyzet összetevővel.
## 6. lépés: Kimeneti útvonal megjelenítése
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Jelenítse meg a módosított PDF-dokumentum mentési útvonalát.

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk jelölőnégyzet-összetevőt PDF-dokumentumhoz a Groupdocs.Annotation for .NET használatával. Ezzel a tudással interaktív elemekkel bővítheti PDF dokumentumait.
## GYIK
### Testreszabhatom a jelölőnégyzet megjelenését?
Igen, igényei szerint testreszabhatja a különféle tulajdonságokat, például színt, stílust és méretet.
### A Groupdocs.Annotation for .NET alkalmas kereskedelmi használatra?
Igen, a Groupdocs.Annotation for .NET kereskedelmi licenceket kínál a vállalkozások számára.
### Kipróbálhatom a Groupdocs.Annotation for .NET-et vásárlás előtt?
 Igen, igénybe veheti az ingyenes próbaverziót innen[itt](https://releases.groupdocs.com/).
### Hol találok támogatást a Groupdocs.Annotation for .NET számára?
 Támogatást és forrásokat találhat a[Groupdocs fórum](https://forum.groupdocs.com/c/annotation/10).
### Szükségem van ideiglenes licencre tesztelés céljából?
 Ideiglenes engedélyt a teszteléshez szerezhet be[itt](https://purchase.groupdocs.com/temporary-license/).