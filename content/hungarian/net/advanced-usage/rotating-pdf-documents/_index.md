---
title: PDF-dokumentumok forgatása
linktitle: PDF-dokumentumok forgatása
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan forgathat könnyedén PDF dokumentumokat a Groupdocs.Annotation for .NET segítségével. A dokumentumkezelés hatékonyságának javítása.
type: docs
weight: 22
url: /hu/net/advanced-usage/rotating-pdf-documents/
---
## Bevezetés
PDF-dokumentumok elforgatása kulcsfontosságú feladat lehet, amikor olyan fájlokat kell kezelni, amelyeket másképp kell megtekinteni vagy feldolgozni. Ebben az oktatóanyagban megvizsgáljuk, hogyan lehet lépésről lépésre elforgatni PDF-dokumentumokat a Groupdocs.Annotation for .NET segítségével.
## Előfeltételek
Mielőtt belevágna az oktatóanyagba, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:
1.  Groupdocs.Annotation for .NET Library: Győződjön meg arról, hogy letöltötte és telepítette a Groupdocs.Annotation for .NET könyvtárat. Letöltheti innen[itt](https://releases.groupdocs.com/annotation/net/).
2. Alapvető ismeretek a C# programozásról: Ez az oktatóanyag feltételezi, hogy rendelkezik alapvető ismeretekkel a C# programozási nyelvről és a .NET-könyvtárak használatáról.

## Névterek importálása
Először is importálnia kell a szükséges névtereket a C# projektbe, hogy elérje a Groupdocs.Annotation könyvtár által biztosított funkciókat.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## 1. lépés: Töltse be a PDF-dokumentumot
 Kezdje a forgatni kívánt PDF-dokumentum betöltésével`Annotator` osztály.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## 2. lépés: Állítsa be a forgatást és a feldolgozási oldalakat
Adja meg az elforgatási szöget és az elforgatni kívánt oldalakat. Ebben a példában az első oldalt az óramutató járásával megegyezően 90 fokkal elforgatjuk.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## 3. lépés: Mentse el az elforgatott dokumentumot
Mentse el az elforgatott PDF dokumentumot a megadott változtatásokkal.
```csharp
annotator.Save("result.pdf");
```
## 4. lépés: Megerősítés megjelenítése
Tájékoztassa a felhasználót, hogy a dokumentumot sikeresen elforgatták.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Következtetés
A PDF-dokumentumok elforgatása alapvető művelet, és a Groupdocs.Annotation for .NET segítségével egyszerűvé és hatékonysá válik. Az oktatóanyagban ismertetett lépések követésével könnyedén elforgathatja a PDF-fájlokat igényei szerint.
## GYIK
### Elforgathatok több oldalt egy PDF-dokumentumban a Groupdocs.Annotation for .NET segítségével?
 Igen, megadhat több oldalt is forgatni a beállításával`ProcessPages` ingatlan ennek megfelelően.
### A Groupdocs.Annotation for .NET kompatibilis a .NET keretrendszer összes verziójával?
A Groupdocs.Annotation for .NET a .NET-keretrendszer-verziók széles skáláját támogatja, biztosítva a kompatibilitást a legtöbb fejlesztői környezettel.
### Groupdocs.Annotation for .NET lehetőséget biztosít a PDF-dokumentumok különböző irányokba történő elforgatására?
Igen, elforgathatja a PDF-dokumentumokat az óramutató járásával megegyezően, az óramutató járásával ellentétes irányban vagy egyéni szögben az igényeinek megfelelően.
### Integrálhatom a Groupdocs.Annotation for .NET-et a meglévő dokumentumkezelő rendszerembe?
Természetesen a Groupdocs.Annotation for .NET zökkenőmentes integrációs lehetőségeket kínál, lehetővé téve a dokumentumkezelési képességek erőfeszítés nélküli bővítését.
### Létezik próbaverzió a Groupdocs.Annotation for .NET számára?
 Igen, ingyenes próbaverziót szerezhet be a webhelyről[itt](https://releases.groupdocs.com/).