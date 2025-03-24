---
title: Szövegcsere megjegyzés hozzáadása a dokumentumhoz
linktitle: Szövegcsere megjegyzés hozzáadása a dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan adhat hozzá könnyedén szöveghelyettesítő megjegyzéseket .NET-dokumentumaihoz a GroupDocs.Annotation for .NET segítségével. Növelje dokumentumkezelési képességeit.
weight: 24
url: /hu/net/unlocking-annotation-power/add-text-replacement-annotation/
---
## Bevezetés
Ebben az oktatóanyagban végigvezetjük Önt a GroupDocs.Annotation for .NET segítségével szöveghelyettesítő megjegyzés hozzáadásának folyamatán. Ez a hatékony könyvtár lehetővé teszi a fejlesztők számára, hogy programozottan kezeljék és megjegyzésekkel láthassák el a különféle típusú dokumentumokat. Ennek az oktatóanyagnak a végére olyan ismeretekkel rendelkezik, amelyek segítségével zökkenőmentesen integrálhatja a szöveghelyettesítő megjegyzéseket .NET-alkalmazásaiba.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételek telepítve vannak:
### 1. .NET-keretrendszer telepítve
Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a fejlesztőgépen. Letöltheti a Microsoft webhelyéről.
### 2. GroupDocs.Annotation for .NET Library
 Töltse le és telepítse a GroupDocs.Annotation for .NET könyvtárat a[weboldal](https://releases.groupdocs.com/annotation/net/). Ez a könyvtár biztosítja a szükséges eszközöket és funkciókat a különböző dokumentumformátumú megjegyzésekkel való munkához.
### 3. Fejlesztői környezet beállítása
Állítsa be a kívánt fejlesztői környezetet, például a Visual Studio-t .NET-alkalmazások létrehozásához és futtatásához.

## Névterek importálása
Mielőtt belemerülnénk a kódolási részbe, importáljuk a GroupDocs-szal való munkához szükséges névtereket. Annotation for .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## 1. lépés: Határozza meg a kimeneti útvonalat
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Itt határozzuk meg a kimeneti útvonalat, ahová a megjegyzésekkel ellátott dokumentum mentésre kerül.
## 2. lépés: Inicializálja az Annotátort
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // A kommentár kódja itt lesz elhelyezve
}
```
Az Annotator objektumot úgy inicializáljuk, hogy megadjuk a bemeneti dokumentumot ("input.pdf") egy felhasználási blokkon belül, hogy biztosítsuk az erőforrások megfelelő selejtezését.
## 3. lépés: Csere megjegyzés létrehozása
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
    TextToReplace = "replaced text"
};
```
Itt létrehozunk egy ReplacementAnnotation objektumot különféle tulajdonságokkal, mint például a létrehozás dátuma, betűszín, üzenet, átlátszatlanság, oldalszám, háttérszín, pontok (koordináták), válaszok (megjegyzések) és a cserélendő szöveg.
## 4. lépés: Megjegyzés hozzáadása
```csharp
annotator.Add(replacement);
```
A létrehozott helyettesítő megjegyzést hozzáadjuk az annotátorhoz.
## 5. lépés: Mentse el a dokumentumot
```csharp
annotator.Save(outputPath);
```
Végül elmentjük a jegyzett dokumentumot a megadott kimeneti útvonalra.
## 6. lépés: Jelenítse meg a sikeres üzenetet
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Megjelenik egy sikeres üzenet, amely jelzi, hogy a dokumentumot sikeresen elmentették.

## Következtetés
Ebben az oktatóanyagban a GroupDocs.Annotation for .NET segítségével szöveghelyettesítő megjegyzések hozzáadásának folyamatát ismertettük. A lépésenkénti útmutató követésével és az előfeltételek megértésével könnyedén integrálhatja ezt a funkciót .NET-alkalmazásaiba.
## GYIK
### A GroupDocs.Annotation for .NET segítségével megjegyzéseket fűzhetek különböző formátumú dokumentumokhoz?
Igen, a GroupDocs.Annotation for .NET támogatja a különféle dokumentumformátumok, például a PDF, DOCX, PPTX, XLSX és egyebek megjegyzéseit.
### A GroupDocs.Annotation for .NET alkalmas asztali és webes alkalmazásokhoz is?
Igen, a GroupDocs.Annotation for .NET használható asztali és webes alkalmazásokban is, rugalmasságot biztosítva a fejlesztők számára.
### Testreszabhatom a GroupDocs.Annotation for .NET segítségével hozzáadott megjegyzések megjelenését?
Természetesen testreszabhatja a megjegyzések megjelenését az olyan tulajdonságok módosításával, mint a szín, az átlátszatlanság, a betűtípus stb.
### Támogatja-e a GroupDocs.Annotation for .NET az együttműködési jegyzetelési funkciókat?
Igen, a GroupDocs.Annotation for .NET olyan funkciókat biztosít az együttműködésen alapuló annotációhoz, amely lehetővé teszi több felhasználó számára, hogy egyidejűleg megjegyzéseket fűzzenek a dokumentumokhoz.
### Elérhető ingyenes próbaverzió a GroupDocs.Annotation for .NET számára?
Igen, igénybe veheti a GroupDocs.Annotation ingyenes próbaverzióját a .NET-hez a[weboldal](https://releases.groupdocs.com/).