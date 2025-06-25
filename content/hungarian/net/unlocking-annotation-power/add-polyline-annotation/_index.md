---
"description": "Tanulja meg, hogyan adhat hozzá vonallánc-megjegyzéseket dokumentumokhoz a GroupDocs.Annotation for .NET segítségével. Könnyedén javíthatja az együttműködési és dokumentum-ellenőrzési folyamatokat."
"linktitle": "Vonallánc-megjegyzés hozzáadása a dokumentumhoz"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Vonallánc-megjegyzés hozzáadása a dokumentumhoz"
"url": "/hu/net/unlocking-annotation-power/add-polyline-annotation/"
"weight": 18
---

# Vonallánc-megjegyzés hozzáadása a dokumentumhoz

## Bevezetés
GroupDocs.Annotation for .NET egy hatékony eszköz, amely lehetővé teszi a fejlesztők számára, hogy programozottan lássanak el jegyzeteket PDF és Microsoft Office dokumentumokban. Funkciói között szerepel a vonalláncok hozzáadásának lehetősége a dokumentumokhoz, ami javítja az együttműködést és a dokumentumok áttekintésének folyamatait.
## Előfeltételek
Mielőtt folytatná ezt az oktatóanyagot, győződjön meg arról, hogy rendelkezik a következőkkel:
- Visual Studio telepítve a rendszeredre.
- C# programozási nyelv alapismerete.
- A GroupDocs.Annotation for .NET könyvtár telepítve van. Letöltheti innen: [itt](https://releases.groupdocs.com/annotation/net/).

## Névterek importálása
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1. lépés: Kimeneti útvonal meghatározása
Először is határozza meg a kimeneti elérési utat, ahová a jegyzetekkel ellátott dokumentum mentésre kerül.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Annotátor inicializálása
Inicializálja az annotátort a bemeneti dokumentum nevének megadásával.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 3. lépés: Vonallánc-feliratozási objektum létrehozása
Hozzon létre egy vonallánc-feliratozási objektumot, és állítsa be a tulajdonságait, például a pozíciót, az üzenetet, az átlátszóságot, a toll színét, a toll stílusát és a toll szélességét.
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
## 4. lépés: Vonallánc-felirat hozzáadása
Adja hozzá a vonallánc-megjegyzést a dokumentumhoz az annotátor objektum segítségével.
```csharp
annotator.Add(polyline);
```
## 5. lépés: Dokumentum mentése
Mentse el a jegyzetekkel ellátott dokumentumot a megadott kimeneti elérési útra.
```csharp
annotator.Save(outputPath);
```
## 6. lépés: Sikeres üzenet megjelenítése
Jelenítsen meg egy üzenetet, amely megerősíti a dokumentum sikeres mentését.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan adhatunk hozzá vonallánc-megjegyzéseket egy dokumentumhoz a GroupDocs.Annotation for .NET használatával. Ez a funkció javítja az együttműködést és a dokumentumok áttekintési folyamatait, megkönnyítve a felhasználók számára a visszajelzések és javaslatok hatékony közlését.
## GYIK
### A GroupDocs.Annotation for .NET kompatibilis az összes dokumentumformátummal?
A GroupDocs.Annotation for .NET támogatja a népszerű dokumentumformátumokat, például a PDF-et és a Microsoft Office formátumokat, beleértve a Wordöt, az Excelt és a PowerPointot.
### Testreszabhatom a megjegyzések megjelenését?
Igen, testreszabhatja a megjegyzések különböző tulajdonságait, például a színt, az átlátszóságot, a stílust és a szélességet az igényeinek megfelelően.
### Ingyenes próbaverziót kínál a GroupDocs.Annotation for .NET?
Igen, igénybe veheti a GroupDocs.Annotation for .NET ingyenes próbaverzióját a következő címen: [ezt a linket](https://releases.groupdocs.com/).
### Hol találok dokumentációt a GroupDocs.Annotation for .NET fájlhoz?
A GroupDocs.Annotation for .NET dokumentációját itt találja: [itt](https://tutorials.groupdocs.com/annotation/net/).
### Hogyan kaphatok támogatást a GroupDocs.Annotation for .NET-tel kapcsolatos problémákkal vagy kérdésekkel kapcsolatban?
Segítséget a GroupDocs.Annotation fórumon kaphatsz. [itt](https://forum.groupdocs.com/c/annotation/10).