---
title: Töltse be a dokumentumot az Azure-ból
linktitle: Töltse be a dokumentumot az Azure-ból
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan fűzhet megjegyzéseket dokumentumokhoz .NET-ben a GroupDocs.Annotation használatával. Lépésről lépésre bemutató oktatóanyag az Azure Blob Storage zökkenőmentes integrációjához.
type: docs
weight: 11
url: /hu/net/document-loading-essentials/load-document-from-azure/
---
## Bevezetés
A dokumentumkezelés és az együttműködés területén a GroupDocs.Annotation for .NET robusztus megoldásként jelenik meg, amely megkönnyíti a zökkenőmentes annotációt és a jelölési funkciókat a .NET-alkalmazásokon belül. Ez az oktatóanyag a GroupDocs.Annotation for .NET használatának bonyolult dokumentumaival foglalkozik, és lépésről lépésre útmutatást nyújt az előfeltételektől a haladó használatig.
## Előfeltételek
Mielőtt belevágna a GroupDocs.Annotation for .NET-be, győződjön meg arról, hogy a következő előfeltételek teljesülnek:
1. A .NET-keretrendszer telepítése: A GroupDocs.Annotation for .NET-hez kompatibilis .NET-futási környezetre van szükség. Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a rendszeren.
2. Hozzáférés a GroupDocs.Annotation Library-hoz: Hozzáférhet a GroupDocs.Annotation for .NET könyvtárhoz, vagy töltse le a webhelyről, vagy olyan csomagkezelőkön keresztül, mint a NuGet.
3. Annotálandó dokumentum: Készítse elő a megjegyzéssel ellátni kívánt dokumentumot (pl. PDF). Győződjön meg arról, hogy a dokumentum elérhető helyileg vagy egy felhőalapú tárolási szolgáltatáson, például az Azure Blob Storage-on keresztül.

## Névterek importálása
A dokumentumok GroupDocs.Annotation for .NET használatával történő megjegyzéseinek megkezdéséhez importálja a szükséges névtereket a projektbe. Ez a lépés biztosítja, hogy hozzáférjen a szükséges osztályokhoz és funkciókhoz.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Töltse be a dokumentumot az Azure-ból
Az Azure Blob Storage-ban tárolt dokumentumok megjegyzéseinek rögzítéséhez kövesse az alábbi lépéseket:
### 1. lépés: Állítsa be a kimeneti útvonalat
Határozza meg a kimeneti útvonalat, ahová a megjegyzésekkel ellátott dokumentum mentésre kerül.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### 2. lépés: Töltse le a dokumentumot
 Töltse le a dokumentumot az Azure Blob Storage szolgáltatásból a következő meghívásával`DownloadFile` módszer.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Annotációs logika
    annotator.Save(outputPath);
}
```
## Töltse le a fájlt az Azure Blob Storage-ból
 A dokumentum Azure Blob Storage webhelyről történő letöltéséhez hajtsa végre a`DownloadFile` módszer.
### 1. lépés: A Blob lekérése
Nyissa meg az Azure Blob Storage-tárolót, és kérje le a kívánt blobot.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### 2. lépés: Töltse le a Blob-tartalmat
Töltse le a blob-tartalmat egy memóriafolyamba.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Szerezze be az Azure Blob Storage Containert
 Az Azure Blob Storage használatához valósítsa meg a`GetContainer` módszer.
### 1. lépés: Inicializálja a tárolási hitelesítő adatokat
Adja meg a szükséges hitelesítő adatokat és a végpontadatokat.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{accountName}.blob.core.windows.net/";
```
### 2. lépés: Blob kliens létrehozása
Hozzon létre egy ügyfelet az Azure Blob Storage használatához.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### 3. lépés: Töltse le a tárolóreferenciát
Szerezzen hivatkozást a megadott tárolóra.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### 4. lépés: Hozzon létre tárolót, ha nem létezik
Győződjön meg arról, hogy a tároló létezik, és ha nem, hozza létre.
```csharp
container.CreateIfNotExists();
```

## Következtetés
A GroupDocs.Annotation for .NET robusztus dokumentumjegyzetelési képességekkel ruházza fel a fejlesztőket, és zökkenőmentesen integrálódik a .NET-alkalmazásokba. Az ebben az oktatóanyagban ismertetett lépések követésével hatékonyan kihasználhatja a GroupDocs.Annotation funkcióit az Azure Blob Storage-ban tárolt dokumentumok megjegyzéseivel.
#### GYIK
### A GroupDocs.Annotation for .NET kompatibilis az összes dokumentumformátummal?
A GroupDocs.Annotation a dokumentumformátumok széles skáláját támogatja, beleértve a PDF, DOCX, PPTX stb.
### Testreszabhatók-e a kommentárok az egyedi követelményeknek megfelelően?
Igen, a GroupDocs.Annotation kiterjedt testreszabási lehetőségeket kínál a megjegyzésekhez, lehetővé téve a felhasználók számára a megjelenés, a viselkedés és a metaadatok módosítását.
### Alkalmas-e a GroupDocs.Annotation együttműködési dokumentum-annotációra?
Teljesen! A GroupDocs.Annotation megkönnyíti az együttműködésen alapuló dokumentumannotációt, mivel lehetővé teszi több felhasználó számára, hogy egyidejűleg megjegyzéseket adjon hozzá, szerkesszen és tekintsen át.
### A GroupDocs.Annotation kínál platformok közötti kompatibilitást?
Igen, a GroupDocs.Annotationt úgy tervezték, hogy zökkenőmentesen működjön különböző platformokon, beleértve a Windows, Linux és macOS rendszert.
### Rendelkezésre áll technikai támogatás a GroupDocs.Annotation felhasználói számára?
Igen, a GroupDocs átfogó technikai támogatást nyújt fórumain és dedikált támogatási csatornáin keresztül.