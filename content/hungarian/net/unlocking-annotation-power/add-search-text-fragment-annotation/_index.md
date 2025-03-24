---
title: Keresési szövegtöredék megjegyzés hozzáadása a dokumentumhoz
linktitle: Keresési szövegtöredék megjegyzés hozzáadása a dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Fedezze fel a GroupDocs.Annotation for .NET erejét, és könnyedén adjon hozzá dokumentumjegyzetelési képességeket alkalmazásaihoz.
weight: 20
url: /hu/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---

# Keresési szövegtöredék megjegyzés hozzáadása a dokumentumhoz

## Bevezetés
A .NET fejlesztés területén a GroupDocs.Annotation hatékony eszköz a dokumentumok zökkenőmentes annotálásához. Akár tapasztalt fejlesztő, akár csak a .NET világába lép be, ez az átfogó oktatóanyag végigvezeti Önt a GroupDocs.Annotation for .NET használatának alapjain, a névterek importálásától egészen a keresési szövegtöredékek megjegyzéseinek hozzáadásának bonyolultságáig. dokumentumokat.
## Bevezetés
A GroupDocs.Annotation for .NET lehetővé teszi a fejlesztők számára, hogy könnyedén beépítsék alkalmazásaikba a dokumentumjegyzetelési képességeket. Intuitív API-jával és robusztus funkcióival a fejlesztők különféle dokumentumformátumokhoz megjegyzéseket fűzhetnek, beleértve a PDF-eket, Microsoft Office dokumentumokat, képeket és még sok mást.
## Előfeltételek
Mielőtt belevágna a GroupDocs.Annotation for .NET-be, győződjön meg arról, hogy a következő előfeltételek teljesülnek:

## Névterek importálása
Először is importálja a szükséges névtereket a GroupDocs.Annotation osztályok és metódusok eléréséhez a .NET-projektben:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1. lépés: Határozza meg a kimeneti útvonalat
Kezdje a kimeneti útvonal meghatározásával, ahová a megjegyzésekkel ellátott dokumentum mentésre kerül:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Inicializálja az Annotátort
 Ezután inicializálja a`Annotator` osztályba a megjegyzésekkel ellátni kívánt dokumentum elérési útjának megadásával:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 3. lépés: Keresési szövegtöredék-annotáció létrehozása
 Hozzon létre egy`SearchTextFragment` objektum a kívánt tulajdonságokkal, például keresendő szöveggel, betűmérettel, betűcsaláddal, betűszínnel és háttérszínnel:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## 4. lépés: Megjegyzés hozzáadása
 Adja hozzá a létrehozott keresési szövegrészlet megjegyzést a dokumentumhoz a segítségével`Add` az annotátor módszere:
```csharp
annotator.Add(searchText);
```
## 5. lépés: Mentse el a megjegyzésekkel ellátott dokumentumot
Mentse el a megjegyzésekkel ellátott dokumentumot a megadott kimeneti útvonalra:
```csharp
annotator.Save(outputPath);
```
## 6. lépés: Jelenítse meg a sikeres üzenetet
Tájékoztassa a felhasználót, hogy a dokumentumot sikeresen elmentette:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés
Összefoglalva, a GroupDocs.Annotation for .NET leegyszerűsíti a megjegyzések dokumentumokhoz való hozzáadásának folyamatát, javítva az együttműködést és a dokumentum-ellenőrzési folyamatokat. Az ebben az útmutatóban vázolt lépések követésével zökkenőmentesen integrálhatja a dokumentum megjegyzések funkcióit .NET-alkalmazásaiba.
## GYIK
### A GroupDocs.Annotation kompatibilis az összes dokumentumformátummal?
Igen, a GroupDocs.Annotation a dokumentumformátumok széles skáláját támogatja, beleértve a PDF-eket, Microsoft Office dokumentumokat, képeket és egyebeket.
### Testreszabhatom a kommentárok megjelenését?
Teljesen! A GroupDocs.Annotation kiterjedt testreszabási lehetőségeket biztosít a megjegyzésekhez, lehetővé téve az olyan tulajdonságok beállítását, mint a betűméret, a szín és a stílus.
### Van ingyenes próbaverzió a GroupDocs.Annotation számára?
 Igen, hozzáférhet a GroupDocs.Annotation ingyenes próbaverziójához, hogy a vásárlás előtt felfedezze szolgáltatásait és képességeit[itt](https://releases.groupdocs.com/)..
### Hol találok támogatást a GroupDocs.Annotation számára?
 A GroupDocs.Annotation támogatásért és segítségért látogassa meg a GroupDocs webhelyet[fórum](https://forum.groupdocs.com/c/annotation/10) az annotációkkal kapcsolatos lekérdezéseknek és vitáknak szentelve.
### Hogyan szerezhetek ideiglenes licencet a GroupDocs.Annotation számára?
 Ideiglenes licencet szerezhet a GroupDocs.Annotation számára a GroupDocs-on keresztül[weboldal](https://purchase.groupdocs.com/temporary-license/), amely lehetővé teszi a termék teljes körű értékelését.