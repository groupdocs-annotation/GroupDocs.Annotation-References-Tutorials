---
title: Vízjel megjegyzés hozzáadása a dokumentumhoz
linktitle: Vízjel megjegyzés hozzáadása a dokumentumhoz
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET segítségével megtudhatja, hogyan adhat hozzá könnyedén vízjel megjegyzéseket dokumentumaihoz. Növelje a dokumentumok átláthatóságát és biztonságát.
type: docs
weight: 28
url: /hu/net/unlocking-annotation-power/add-watermark-annotation/
---
## Bevezetés
Ebben az oktatóanyagban a GroupDocs.Annotation for .NET segítségével vízjel megjegyzés hozzáadásának folyamatát mutatjuk be. A vízjel megjegyzések hasznosak egy dokumentum állapotának jelzésére, bizalmasként való megjelölésére vagy bármilyen más releváns információ hozzáadására.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következőkkel:

1.  GroupDocs.Annotation for .NET: Letöltheti innen[itt](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Győződjön meg arról, hogy a Visual Studio telepítve van a rendszeren.
3. Alapvető C# ismerete: A kódpéldák megértéséhez és megvalósításához a C# programozási nyelv ismerete szükséges.

## Névterek importálása

A kódolás megkezdése előtt importáljuk a szükséges névtereket:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Most bontsuk le a vízjel megjegyzés hozzáadásának folyamatát több lépésre:

## 1. lépés: Határozza meg a kimeneti útvonalat

 Először is meg kell határoznunk a kimeneti útvonalat, ahová a megjegyzésekkel ellátott dokumentumot elmentjük. Használjuk a`Path` osztályból`System.IO` névtér a kimeneti könyvtár elérési útjának a fájlnévvel való kombinálásához.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## 2. lépés: Inicializálja az Annotátort

Ezután inicializáljuk az annotátort a bemeneti dokumentum elérési útjának megadásával. Ez lehetővé teszi számunkra, hogy megjegyzéseket adjunk a dokumentumhoz.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ide kerül a kommentár kódja
}
```

## 3. lépés: Vízjel-annotáció létrehozása

Most hozzunk létre egy vízjel annotációs objektumot a kívánt tulajdonságokkal, például szöggel, pozícióval, szöveggel, betűszínnel, átlátszatlansággal stb.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## 4. lépés: Vízjel megjegyzés hozzáadása

 Most hozzáadjuk a vízjel megjegyzést a dokumentumhoz a segítségével`Add` az annotátor objektum metódusa.

```csharp
annotator.Add(watermark);
```

## 5. lépés: Mentse el a dokumentumot

Végül elmentjük a megjegyzésekkel ellátott dokumentumot a megadott kimeneti útvonalra.

```csharp
annotator.Save(outputPath);
```

## Következtetés

Ebben az oktatóanyagban megtanultuk, hogyan adhatunk vízjel megjegyzést egy dokumentumhoz a GroupDocs.Annotation for .NET segítségével. A vízjel megjegyzések értékes eszközt jelentenek a dokumentumok releváns információkkal való megjelölésére vagy állapotuk jelzésére.

## GYIK

### K: Testreszabhatom a vízjel megjegyzés megjelenését?

V: Igen, testreszabhat különféle tulajdonságokat, például szöveget, betűméretet, színt, átlátszatlanságot, pozíciót stb., hogy a vízjelet az Ön igényei szerint szabja.

### K: A GroupDocs.Annotation for .NET kompatibilis a különböző dokumentumformátumokkal?

V: Igen, a GroupDocs.Annotation a dokumentumformátumok széles skáláját támogatja, beleértve a PDF, Microsoft Word, Excel, PowerPoint és képformátumokat.

### K: Hozzáadhatok több megjegyzést egyetlen dokumentumhoz?

V: Természetesen a GroupDocs.Annotation lehetővé teszi több különböző típusú megjegyzés hozzáadását egyetlen dokumentumhoz, lehetővé téve az átfogó dokumentumjelölést.

### K: A GroupDocs.Annotation támogatja az együttműködésen alapuló annotációt?

V: Igen, a GroupDocs.Annotation megkönnyíti az együttműködésen alapuló megjegyzések készítését azáltal, hogy lehetővé teszi a felhasználók számára megjegyzések, válaszok és megjegyzések hozzáadását, elősegítve a csapattagok közötti hatékony együttműködést.

### K: Elérhető a GroupDocs.Annotation próbaverziója .NET-hez?

 V: Igen, letölthet egy ingyenes próbaverziót a webhelyről[itt](https://releases.groupdocs.com/).