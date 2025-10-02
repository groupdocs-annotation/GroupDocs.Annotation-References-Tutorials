---
"description": "Fedezze fel a GroupDocs.Annotation for .NET erejét, és könnyedén adjon dokumentumokhoz megjegyzéskészítési lehetőségeket alkalmazásaihoz."
"linktitle": "Keresési szövegrészlet megjegyzésének hozzáadása a dokumentumhoz"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Keresési szövegrészlet megjegyzésének hozzáadása a dokumentumhoz"
"url": "/hu/net/unlocking-annotation-power/add-search-text-fragment-annotation/"
type: docs
"weight": 20
---

# Keresési szövegrészlet megjegyzésének hozzáadása a dokumentumhoz

## Bevezetés
A .NET fejlesztés területén a GroupDocs.Annotation kiemelkedően hatékony eszköz a dokumentumok zökkenőmentes annotálásához. Akár tapasztalt fejlesztő vagy, akár csak most lépsz be a .NET világába, ez az átfogó oktatóanyag végigvezet a GroupDocs.Annotation .NET-es használatának alapjain, a névterek importálásától kezdve a keresési szövegrészletek annotációinak dokumentumokhoz való hozzáadásának bonyolultságáig.
## Bevezetés
A GroupDocs.Annotation for .NET lehetővé teszi a fejlesztők számára, hogy könnyedén beépítsenek dokumentumok annotálási funkcióit alkalmazásaikba. Intuitív API-jának és robusztus funkcióinak köszönhetően a fejlesztők különféle dokumentumformátumokat, például PDF-eket, Microsoft Office dokumentumokat, képeket és egyebeket annotálhatnak.
## Előfeltételek
Mielőtt belemerülnénk a GroupDocs.Annotation for .NET használatába, győződjünk meg arról, hogy a következő előfeltételek teljesülnek:

## Névterek importálása
Először importáld a szükséges névtereket a GroupDocs.Annotation osztályok és metódusok eléréséhez a .NET projektedben:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## 1. lépés: Kimeneti útvonal meghatározása
Kezdje azzal, hogy meghatározza a kimeneti elérési utat, ahová a jegyzetekkel ellátott dokumentum mentésre kerül:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## 2. lépés: Annotátor inicializálása
Ezután inicializálja a(z) egy példányát `Annotator` osztályt a jegyzetelni kívánt dokumentum elérési útjának megadásával:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## 3. lépés: Keresési szövegrészlet megjegyzésének létrehozása
Hozz létre egy `SearchTextFragment` objektum a kívánt tulajdonságokkal, például a keresendő szöveggel, betűmérettel, betűcsaláddal, betűszínnel és háttérszínnel:
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
## 4. lépés: Jegyzet hozzáadása
Adja hozzá a létrehozott keresési szövegrészlet megjegyzését a dokumentumhoz a `Add` az annotátor módszere:
```csharp
annotator.Add(searchText);
```
## 5. lépés: Jegyzetekkel ellátott dokumentum mentése
Mentse el a jegyzetekkel ellátott dokumentumot a megadott kimeneti útvonalra:
```csharp
annotator.Save(outputPath);
```
## 6. lépés: Sikeres üzenet megjelenítése
Értesítse a felhasználót a dokumentum sikeres mentéséről:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Következtetés
Összefoglalva, a GroupDocs.Annotation for .NET leegyszerűsíti a dokumentumokhoz fűzött megjegyzések hozzáadásának folyamatát, javítva az együttműködést és a dokumentumok felülvizsgálatának folyamatát. Az útmutatóban ismertetett lépéseket követve zökkenőmentesen integrálhatja a dokumentumok megjegyzéskészítési funkcióit .NET alkalmazásaiba.
## GYIK
### A GroupDocs.Annotation kompatibilis az összes dokumentumformátummal?
Igen, a GroupDocs.Annotation számos dokumentumformátumot támogat, beleértve a PDF-eket, a Microsoft Office dokumentumokat, a képeket és egyebeket.
### Testreszabhatom a megjegyzések megjelenését?
Abszolút! A GroupDocs.Annotation széleskörű testreszabási lehetőségeket kínál a jegyzetekhez, lehetővé téve olyan tulajdonságok módosítását, mint a betűméret, a szín és a stílus.
### Van ingyenes próbaverzió a GroupDocs.Annotation-höz?
Igen, hozzáférhet a GroupDocs.Annotation ingyenes próbaverziójához, hogy megismerkedhessen a funkcióival és képességeivel a vásárlás előtt. [itt](https://releases.groupdocs.com/)..
### Hol találok támogatást a GroupDocs.Annotation-höz?
A GroupDocs.Annotation dokumentummal kapcsolatos támogatásért és segítségért látogassa meg a GroupDocs weboldalát. [fórum](https://forum.groupdocs.com/c/annotation/10) annotációkkal kapcsolatos kérdéseknek és megbeszéléseknek szentelve.
### Hogyan szerezhetek ideiglenes licencet a GroupDocs.Annotation-hoz?
Ideiglenes licencet szerezhet a GroupDocs.Annotationhoz a GroupDocs oldalon keresztül. [weboldal](https://purchase.groupdocs.com/temporary-license/), lehetővé téve a termék teljes körű értékelését.