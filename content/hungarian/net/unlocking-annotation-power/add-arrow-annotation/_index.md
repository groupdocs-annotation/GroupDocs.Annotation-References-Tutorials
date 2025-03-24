---
title: Nyíl megjegyzés hozzáadása a dokumentumhoz
linktitle: Nyíl megjegyzés hozzáadása a dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan adhat hozzá nyilakkal ellátott megjegyzéseket a dokumentumokhoz a GroupDocs.Annotation for .NET segítségével. Fokozatmentesen fokozza a dokumentumok tisztaságát és interaktivitását.
weight: 11
url: /hu/net/unlocking-annotation-power/add-arrow-annotation/
---
## Bevezetés
Ebben az oktatóanyagban végigvezetjük Önt a nyilas megjegyzések hozzáadásának folyamatán a GroupDocs.Annotation for .NET segítségével. A nyíl megjegyzések hasznosak az irány jelzésére vagy a dokumentumon belüli meghatározott elemek kijelzésére.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következőkkel:
1.  GroupDocs.Annotation for .NET: Telepítse a GroupDocs.Annotation könyvtárat .NET-hez. Letöltheti innen[itt](https://releases.groupdocs.com/annotation/net/).
2. Fejlesztési környezet: Győződjön meg arról, hogy be van állítva egy fejlesztői környezet a .NET-fejlesztéshez, beleértve a Visual Studio-t vagy bármely más preferált IDE-t.

## Névterek importálása
Először is importálnia kell a szükséges névtereket, hogy hozzáférjen a megjegyzésekhez szükséges osztályokhoz és metódusokhoz.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1. lépés: Inicializálja az Annotátort
Inicializálja az annotátort a bemeneti dokumentumfájl elérési útjának megadásával.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 2. lépés: Nyíl megjegyzés létrehozása
Hozzon létre egy példányt az ArrowAnnotation osztályból, és határozza meg tulajdonságait, például pozíciót, üzenetet, átlátszatlanságot, tollszínt, stílust, szélességet stb.
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
## 3. lépés: Megjegyzés hozzáadása
 Adja hozzá a nyíl megjegyzést a dokumentumhoz a gombbal`Add` az annotátor módszere.
```csharp
	annotator.Add(arrow);
```
## 4. lépés: Mentse el a dokumentumot
Mentse a megjegyzésekkel ellátott dokumentumot a megadott kimeneti útvonalra.
```csharp
	annotator.Save(outputPath);
}
```
## 5. lépés: Megerősítés megjelenítése
Megerősítő üzenet megjelenítése, amely jelzi a dokumentum sikeres mentését.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Sikeresen hozzáadott egy nyíl megjegyzést a dokumentumhoz a GroupDocs.Annotation for .NET segítségével.

## Következtetés
Ebben az oktatóanyagban bemutattuk azt a folyamatot, amikor a GroupDocs.Annotation for .NET segítségével nyíllal ellátott megjegyzéseket adunk a dokumentumokhoz. Ha követi ezeket a lépéseket, akkor egyértelmű irányjelzőkkel javíthatja dokumentumait, amelyek informatívabbá és vonzóbbá teszik őket.
## GYIK
### Testreszabhatom a nyíl megjegyzés megjelenését?
Igen, testreszabhat különféle tulajdonságokat, például színt, stílust, szélességet és átlátszatlanságot, hogy megfeleljenek az Ön preferenciáinak és dokumentumkövetelményeinek.
### A GroupDocs.Annotation kompatibilis az összes dokumentumformátummal?
A GroupDocs.Annotation a dokumentumformátumok széles skáláját támogatja, beleértve a PDF, DOCX, PPTX, XLSX és egyebeket.
### Hozzáadhatok megjegyzéseket programozottan a GroupDocs.Annotation használatával?
Igen, a GroupDocs.Annotation API-kat biztosít, amelyek lehetővé teszik megjegyzések programozott hozzáadását, szerkesztését és eltávolítását a dokumentumokból.
### A GroupDocs.Annotation ingyenes próbaverziót kínál?
 Igen, ingyenesen kipróbálhatja a GroupDocs.Annotation alkalmazást, ha letölti a webhelyről[itt](https://releases.groupdocs.com/).
### Hol kaphatok technikai támogatást a GroupDocs.Annotation-hoz?
Technikai támogatásért és segítségért keresse fel a GroupDocs.Annotation fórumot[itt](https://forum.groupdocs.com/c/annotation/10).