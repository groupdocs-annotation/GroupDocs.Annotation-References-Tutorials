---
"description": "Tanulja meg, hogyan adhat nyíljegyzeteket dokumentumaihoz a GroupDocs.Annotation for .NET segítségével. Könnyedén javíthatja a dokumentumok érthetőségét és interaktivitását."
"linktitle": "Nyíljegyzet hozzáadása a dokumentumhoz"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Nyíljegyzet hozzáadása a dokumentumhoz"
"url": "/hu/net/unlocking-annotation-power/add-arrow-annotation/"
"weight": 11
---

# Nyíljegyzet hozzáadása a dokumentumhoz

## Bevezetés
Ebben az oktatóanyagban végigvezetjük Önt a nyíljegyzetek dokumentumaihoz való hozzáadásának folyamatán a GroupDocs.Annotation for .NET használatával. A nyíljegyzetek hasznosak az irány jelzésére vagy a dokumentumon belüli adott elemek kiemelésére.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy a következőkkel rendelkezik:
1. GroupDocs.Annotation .NET-hez: Telepítse a GroupDocs.Annotation .NET-hez készült könyvtárat. Letöltheti innen: [itt](https://releases.groupdocs.com/annotation/net/).
2. Fejlesztői környezet: Győződjön meg arról, hogy rendelkezik egy .NET fejlesztéshez beállított fejlesztői környezettel, beleértve a Visual Studio-t vagy bármely más előnyben részesített IDE-t.

## Névterek importálása
Először is importálnia kell a szükséges névtereket az annotációhoz szükséges osztályok és metódusok eléréséhez.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1. lépés: Annotátor inicializálása
Inicializálja az annotátort a bemeneti dokumentumfájl elérési útjának megadásával.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 2. lépés: Nyíljelölés létrehozása
Hozz létre egy példányt az ArrowAnnotation osztályból, és definiáld a tulajdonságait, mint például a pozíció, az üzenet, az átlátszóság, a toll színe, a stílus, a szélesség stb.
```csharp
	ArrowAnnotation arrow = new ArrowAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		CreatedOn = DateTime.Now,
		Message = "This is arrow annotation",
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
## 3. lépés: Jegyzet hozzáadása
Adja hozzá a nyílhoz tartozó megjegyzést a dokumentumhoz a `Add` az annotátor módszere.
```csharp
	annotator.Add(arrow);
```
## 4. lépés: Dokumentum mentése
Mentse el a jegyzetekkel ellátott dokumentumot a megadott kimeneti elérési útra.
```csharp
	annotator.Save(outputPath);
}
```
## 5. lépés: Megerősítés megjelenítése
Megjelenít egy megerősítő üzenetet, amely jelzi a dokumentum sikeres mentését.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Most sikeresen hozzáadott egy nyíljegyzetet a dokumentumához a GroupDocs.Annotation for .NET használatával.

## Következtetés
Ebben az oktatóanyagban a GroupDocs.Annotation for .NET használatával a dokumentumokhoz nyílaláírások hozzáadásának folyamatát ismertettük. A következő lépéseket követve egyértelmű irányjelzőkkel gazdagíthatja dokumentumait, így informatívabbá és lebilincselőbbé teheti azokat.
## GYIK
### Testreszabhatom a nyíllal jelölt megjegyzések megjelenését?
Igen, testreszabhatja a különböző tulajdonságokat, például a színt, a stílust, a szélességet és az átlátszóságot, hogy megfeleljenek az oktatóanyagai és a dokumentum követelményeinek.
### A GroupDocs.Annotation kompatibilis az összes dokumentumformátummal?
A GroupDocs.Annotation számos dokumentumformátumot támogat, beleértve a PDF, DOCX, PPTX, XLSX és egyebeket.
### Hozzáadhatok annotációkat programozottan a GroupDocs.Annotation használatával?
Igen, a GroupDocs.Annotation API-kat biztosít, amelyek lehetővé teszik a dokumentumokhoz tartozó jegyzetek programozott hozzáadását, szerkesztését és eltávolítását.
### Ingyenes próbaverziót kínál a GroupDocs.Annotation?
Igen, ingyenesen kipróbálhatja a GroupDocs.Annotation alkalmazást a következő címről: [itt](https://releases.groupdocs.com/).
### Hol kaphatok technikai támogatást a GroupDocs.Annotation-höz?
Technikai támogatásért és segítségért látogassa meg a GroupDocs.Annotation fórumot. [itt](https://forum.groupdocs.com/c/annotation/10).