---
"date": "2025-05-06"
"description": "Ismerje meg, hogyan mentheti hatékonyan a PDF-fájlok csak annotált oldalait a .NET-hez készült GroupDocs.Annotation segítségével. Fejlessze a dokumentumkezelést és az együttműködést ezzel a részletes útmutatóval."
"title": "Jegyzetekkel ellátott oldalak mentése PDF-ben a GroupDocs.Annotation for .NET használatával"
"url": "/hu/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
"weight": 1
---

# Jegyzetekkel ellátott oldalak mentése PDF-ben a GroupDocs.Annotation for .NET használatával

## Bevezetés

Nehezen tud menteni bizonyos, jegyzetekkel ellátott oldalakat PDF-dokumentumaiból? Ez az átfogó útmutató bemutatja, hogyan érheti el ezt hatékonyan a GroupDocs.Annotation for .NET használatával. A jegyzetelési képességek kihasználásával egyszerűsítheti a dokumentumkezelést és javíthatja az együttműködést a releváns tartalomra összpontosítva.

Ebben az oktatóanyagban a következőket fogod megtanulni:
- Fejlesztői környezet beállítása a GroupDocs.Annotation segítségével
- Különböző típusú megjegyzések hozzáadása
- Csak annotált oldalak hatékony mentése

Készen állsz a kezdésre? Győződjünk meg róla, hogy minden elő van készítve.

### Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy a következőkkel rendelkezik:
- **.NET keretrendszer** (4.6-os vagy újabb verzió) vagy **.NET Core/5+**
- Egy kódszerkesztő, mint például a Visual Studio
- C# és .NET projektbeállítási alapismeretek

## A GroupDocs.Annotation beállítása .NET-hez

A GroupDocs.Annotation használatának megkezdéséhez telepítse a NuGet-en keresztül.

**NuGet csomagkezelő konzol**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET parancssori felület**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Licencszerzés

A GroupDocs ingyenes próbaverziót kínál, amellyel teljes mértékben megismerkedhetsz a szoftverükkel. Hosszabb távú használathoz vásárolj licencet, vagy kérj ideigleneset:
- **Ingyenes próbaverzió**: Fedezze fel a funkciókat korlátozások nélkül egy kezdeti időszakban.
- **Ideiglenes engedély**: A GroupDocs.Annotation ideiglenes használata éles környezetben.
- **Vásárlás**Biztosítsa hosszú távú igényeit kereskedelmi licenccel.

A telepítés után inicializálja a könyvtárat az alábbiak szerint:

```csharp
using GroupDocs.Annotation;

// Alapvető beállítások dokumentumok betöltéséhez és megjegyzésekkel való ellátásához
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## Megvalósítási útmutató

### Jegyzetek hozzáadása

#### Áttekintés

A jegyzetek segítenek kiemelni a dokumentum fontos területeit. Nézzük meg, hogyan adhatunk hozzá egyet. `AreaAnnotation` és egy `EllipseAnnotation`.

**1. lépés: Területi megjegyzés létrehozása**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// Területjelölés meghatározása
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Pozíció és méret
    BackgroundColor = 65535,                // ARGB színérték a kiemeléshez
    PageNumber = 1                          // Adott oldalszám
};
```

A `AreaAnnotation` kiemel egy téglalap alakú területet a dokumentumon. Testreszabhatja a pozícióját (`Box`) és a háttérszín.

**2. lépés: Ellipszis annotáció létrehozása**

```csharp
// Az ellipszis annotáció definiálása
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Pozíció és méret
    BackgroundColor = 123456,                // ARGB színérték a kiemeléshez
    PageNumber = 1                           // Adott oldalszám
};
```

A `EllipseAnnotation` lehetővé teszi ovális alakzat rajzolását a dokumentumra. Állítsa be a pozíciót és a méreteket a `Box` ingatlan.

**3. lépés: Megjegyzések hozzáadása**

```csharp
// Megjegyzések hozzáadása az Annotator példányhoz
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

A `Add` módszer, több típusú annotációt is tartalmazzon. Ez a lépés hozzáadja mind a `AreaAnnotation` és `EllipseAnnotation`.

### Csak jegyzetekkel ellátott oldalak mentése

#### Áttekintés

Ha csak a jegyzeteket tartalmazó oldalakat szeretné menteni, ennek megfelelően konfigurálja a mentési beállításokat.

**4. lépés: Jegyzetekkel ellátott oldalak mentése**

```csharp
using GroupDocs.Annotation.Options;

// Mentési beállítások beállítása úgy, hogy csak annotált oldalak kerüljenek mentésre
annotator.Save("path/to/output/document.pdf\