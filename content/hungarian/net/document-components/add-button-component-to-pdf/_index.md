---
title: Gombkomponens hozzáadása a PDF-dokumentumhoz
linktitle: Gombkomponens hozzáadása a PDF-dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Bővítse PDF-dokumentumait interaktív gombelemekkel a Groupdocs.Annotation for .NET segítségével. Kövesse lépésről lépésre bemutató oktatóanyagunkat a zökkenőmentes integráció érdekében.
type: docs
weight: 10
url: /hu/net/document-components/add-button-component-to-pdf/
---
## Bevezetés
Ebben az oktatóanyagban végigvezetjük Önt egy gombkomponens PDF-dokumentumhoz való hozzáadásának folyamatán a Groupdocs.Annotation for .NET segítségével. Ez a lépésenkénti útmutató biztosítja, hogy ezt a funkciót könnyedén beépíthesse projektjébe.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételeket teljesítette:
1.  Groupdocs.Annotation for .NET: Győződjön meg arról, hogy telepítette a Groupdocs.Annotation for .NET könyvtárat. Letöltheti innen[itt](https://releases.groupdocs.com/annotation/net/).
2. Fejlesztői környezet: Egy megfelelő fejlesztői környezetet kell beállítani .NET keretrendszerrel.

## Névterek importálása
A folytatás előtt importálja a szükséges névtereket a projektbe:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
## 1. lépés: Inicializálja a kimeneti útvonalat
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Gombkomponens hozzáadása
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100),
        PenColor = 65535,
        Style = BorderStyle.Dashed,
        BorderWidth = 0,
        BorderColor = 0,
        AlternateName = "Name",
        PartialName = "Patial Name",
        NormalCaption = "Caption",
        ButtonColor = 16761035,
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
    annotator.Add(button);
    annotator.Save("result.pdf");
}
```
## 3. lépés: Kimeneti útvonal megjelenítése
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Gratulálunk! Sikeresen hozzáadott egy gombkomponenst egy PDF-dokumentumhoz a Groupdocs.Annotation for .NET segítségével.

## Következtetés
Ebben az oktatóanyagban bemutattuk, hogyan építhet be gombösszetevőket PDF dokumentumokba a Groupdocs.Annotation for .NET segítségével. Az alábbi lépések követésével interaktív funkciókkal bővítheti PDF-dokumentumait.
## GYIK
### Testreszabhatom a gomb megjelenését?
Igen, igényei szerint testreszabhatja a gombkomponens különféle tulajdonságait, például méretét, színét és stílusát.
### A Groupdocs.Annotation for .NET kompatibilis az összes PDF-verzióval?
A Groupdocs.Annotation for .NET a PDF-verziók széles skáláját támogatja, biztosítva a kompatibilitást a legtöbb dokumentummal.
### Hozzáadhatok több gombösszetevőt egyetlen PDF dokumentumhoz?
A Groupdocs.Annotation for .NET segítségével természetesen tetszőleges számú gombelemet adhat hozzá egy PDF-dokumentumhoz.
### A Groupdocs.Annotation for .NET támogat más fájlformátumokat?
Igen, a PDF-en kívül a Groupdocs.Annotation for .NET számos más dokumentumformátumot is támogat, beleértve a DOCX, PPTX és XLSX-et.
### Létezik próbaverzió tesztelési célból?
 Igen, elérheti a Groupdocs.Annotation ingyenes próbaverzióját a .NET-hez innen[itt](https://releases.groupdocs.com/).