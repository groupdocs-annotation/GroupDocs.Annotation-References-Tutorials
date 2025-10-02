---
"description": "Ismerje meg, hogyan adhat hozzá jelölőnégyzet-összetevőt PDF-dokumentumokhoz a Groupdocs.Annotation for .NET használatával. Javítsa PDF-fájljait interaktív elemekkel."
"linktitle": "Jelölőnégyzet-összetevő hozzáadása PDF dokumentumhoz"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Jelölőnégyzet-összetevő hozzáadása PDF dokumentumhoz"
"url": "/hu/net/document-components/add-checkbox-component-to-pdf/"
type: docs
"weight": 11
---

# Jelölőnégyzet-összetevő hozzáadása PDF dokumentumhoz

## Bevezetés
Ebben az oktatóanyagban végigvezetünk egy jelölőnégyzet-összetevő PDF-dokumentumhoz való hozzáadásának folyamatán a Groupdocs.Annotation for .NET használatával.
## Előfeltételek
Mielőtt elkezdenénk, győződjünk meg arról, hogy a következőkkel rendelkezünk:
1. Groupdocs.Annotation .NET SDK-hoz: Letöltheti innen: [itt](https://releases.groupdocs.com/annotation/net/).
2. Fejlesztői környezet: Győződjön meg róla, hogy van beállítva egy .NET fejlesztői környezet.

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
Most bontsuk a példát több lépésre:
## 1. lépés: Kimeneti útvonal meghatározása
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Itt definiáljuk a kimeneti elérési utat, ahová a módosított PDF dokumentum mentésre kerül.
## 2. lépés: Annotátor inicializálása
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Inicializálja a `Annotator` objektum a bemeneti PDF dokumentum elérési útjának átadásával.
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
Hozz létre egy `CheckBoxComponent` objektum és testreszabhatja a tulajdonságait, például `Checked`, `Box` méretek, `PenColor`, `Style`, és adj hozzá néhány választ.
## 4. lépés: Jelölőnégyzet-összetevő hozzáadása
```csharp
annotator.Add(checkBox);
```
Adja hozzá a létrehozott jelölőnégyzet-összetevőt a PDF dokumentumhoz.
## 5. lépés: Dokumentum mentése
```csharp
annotator.Save("result.pdf");
```
Mentse el a módosított PDF dokumentumot a jelölőnégyzet komponenssel.
## 6. lépés: Kimeneti útvonal megjelenítése
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Jelenítse meg a módosított PDF dokumentum mentési útvonalát.

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk hozzá jelölőnégyzet-összetevőt egy PDF-dokumentumhoz a Groupdocs.Annotation for .NET használatával. Ezzel a tudással interaktív elemekkel gazdagíthatjuk PDF-dokumentumainkat.
## GYIK
### Testreszabhatom a jelölőnégyzet megjelenését?
Igen, testreszabhatja a különböző tulajdonságokat, például a színt, a stílust és a méretet az igényei szerint.
### Alkalmas kereskedelmi használatra a Groupdocs.Annotation for .NET?
Igen, a Groupdocs.Annotation for .NET kereskedelmi licenceket kínál vállalkozások számára.
### Kipróbálhatom a Groupdocs.Annotation for .NET-et vásárlás előtt?
Igen, igénybe vehet egy ingyenes próbaverziót a következő címen: [itt](https://releases.groupdocs.com/).
### Hol találok támogatást a Groupdocs.Annotation for .NET-hez?
Támogatást és forrásokat találhatsz a következő címen: [Groupdocs fórum](https://forum.groupdocs.com/c/annotation/10).
### Szükségem van ideiglenes jogosítványra tesztelési célokra?
Ideiglenes tesztelési engedélyt szerezhet be a következő címen: [itt](https://purchase.groupdocs.com/temporary-license/).