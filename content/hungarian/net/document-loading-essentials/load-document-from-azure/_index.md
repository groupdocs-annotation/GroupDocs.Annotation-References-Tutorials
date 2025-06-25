---
"description": "Ismerje meg, hogyan láthat el jegyzetekkel dokumentumokat .NET-ben a GroupDocs.Annotation használatával. Lépésről lépésre bemutató az Azure Blob Storage-szal való zökkenőmentes integrációhoz."
"linktitle": "Dokumentum betöltése az Azure-ból"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dokumentum betöltése az Azure-ból"
"url": "/hu/net/document-loading-essentials/load-document-from-azure/"
"weight": 11
---

# Dokumentum betöltése az Azure-ból

## Bevezetés
A dokumentumkezelés és az együttműködés területén a GroupDocs.Annotation for .NET robusztus megoldást kínál, amely zökkenőmentes annotációs és jelölési funkciókat tesz lehetővé a .NET alkalmazásokon belül. Ez az oktatóanyag a GroupDocs.Annotation for .NET dokumentumok annotálására való felhasználásának bonyolultságait ismerteti, lépésről lépésre útmutatást nyújtva az előfeltételektől a haladó használatig.
## Előfeltételek
Mielőtt belemerülnénk a GroupDocs.Annotation for .NET használatába, győződjünk meg arról, hogy a következő előfeltételek teljesülnek:
1. .NET-keretrendszer telepítése: A GroupDocs.Annotation for .NET használatához kompatibilis .NET futtatókörnyezet szükséges. Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a rendszerén.
2. Hozzáférés a GroupDocs.Annotation könyvtárhoz: A GroupDocs.Annotation for .NET könyvtárhoz hozzáférhet letöltéssel a weboldalról, vagy csomagkezelőkön, például a NuGeten keresztül.
3. Jegyzetekkel ellátandó dokumentum: Készítse elő a jegyzetekkel ellátni kívánt dokumentumot (pl. PDF). Győződjön meg arról, hogy a dokumentum elérhető helyben vagy egy felhőalapú tárolási szolgáltatáson, például az Azure Blob Storage-on keresztül.

## Névterek importálása
A GroupDocs.Annotation for .NET használatával dokumentumok annotálásának megkezdéséhez importálja a szükséges névtereket a projektbe. Ez a lépés biztosítja, hogy hozzáférjen a szükséges osztályokhoz és funkciókhoz.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Dokumentum betöltése az Azure-ból
Az Azure Blob Storage-ban tárolt dokumentumok jegyzetekkel való ellátásához kövesse az alábbi lépéseket:
### 1. lépés: Kimeneti útvonal beállítása
Adja meg a kimeneti elérési utat, ahová a jegyzetekkel ellátott dokumentum mentésre kerül.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### 2. lépés: Dokumentum letöltése
A dokumentum lekérése az Azure Blob Storage-ból a következő meghívásával: `DownloadFile` módszer.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Annotációs logika
    annotator.Save(outputPath);
}
```
## Fájl letöltése az Azure Blob Storage-ból
A dokumentum Azure Blob Storage-ból való letöltéséhez implementálja a következőt: `DownloadFile` módszer.
### 1. lépés: Blob lekérése
Nyissa meg az Azure Blob Storage tárolót, és kérje le a kívánt blobot.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### 2. lépés: Blob-tartalom letöltése
Töltse le a blob tartalmát egy memória-streambe.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Azure Blob Storage-tároló beszerzése
Az Azure Blob Storage-szal való interakcióhoz implementálja a `GetContainer` módszer.
### 1. lépés: Tároló hitelesítő adatainak inicializálása
Adja meg a szükséges fiók hitelesítő adatait és a végpont adatait.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{fiókNeve}.blob.core.windows.net/";
```
### 2. lépés: Blob-ügyfél létrehozása
Hozzon létre egy klienst az Azure Blob Storage-szal való interakcióhoz.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### 3. lépés: Konténerhivatkozás lekérése
Szerezzen be egy oktatóanyagot a megadott tárolóhoz.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### 4. lépés: Hozz létre egy konténert, ha nem létezik
Győződjön meg róla, hogy a konténer létezik, és hozza létre, ha nem.
```csharp
container.CreateIfNotExists();
```

## Következtetés
A GroupDocs.Annotation for .NET robusztus dokumentum-annotációs képességeket biztosít a fejlesztőknek, zökkenőmentesen integrálódva a .NET alkalmazásokba. Az ebben az oktatóanyagban ismertetett lépéseket követve hatékonyan kihasználhatja a GroupDocs.Annotation funkcióit az Azure Blob Storage-ban tárolt dokumentumok annotálásához.
#### GYIK
### A GroupDocs.Annotation for .NET kompatibilis az összes dokumentumformátummal?
A GroupDocs.Annotation számos dokumentumformátumot támogat, beleértve a PDF, DOCX, PPTX és egyebeket.
### Testreszabhatók-e a megjegyzések az adott igényeknek megfelelően?
Igen, a GroupDocs.Annotation széleskörű testreszabási lehetőségeket kínál a jegyzetekhez, lehetővé téve a felhasználók számára a megjelenés, a viselkedés és a metaadatok módosítását.
### Alkalmas a GroupDocs.Annotation közös dokumentum-annotációk készítésére?
Abszolút! A GroupDocs.Annotation megkönnyíti a közös dokumentum-annotációkat azáltal, hogy lehetővé teszi több felhasználó számára, hogy egyszerre adjon hozzá, szerkesszen és tekintsen át annotációkat.
### A GroupDocs.Annotation platformfüggetlen kompatibilitást kínál?
Igen, a GroupDocs.Annotation úgy lett kialakítva, hogy zökkenőmentesen működjön különböző platformokon, beleértve a Windows, Linux és macOS rendszereket.
### Elérhető a technikai támogatás a GroupDocs.Annotation felhasználók számára?
Igen, a GroupDocs átfogó technikai támogatást nyújt a fórumain és dedikált támogatási csatornáin keresztül.