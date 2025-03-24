---
title: Állítsa be a mért licencet
linktitle: Állítsa be a mért licencet
second_title: GroupDocs.Annotation .NET API
description: Ismerje meg, hogyan állíthat be mérőszámos licencet a GroupDocs.Annotation .NET számára az erőforrás-használathoz és a .NET-alkalmazások dokumentumfeljegyzési képességeinek biztosításához.
weight: 12
url: /hu/net/applying-licenses/set-metered-license/
---

# Állítsa be a mért licencet

## Bevezetés
GroupDocs.Annotation for .NET egy hatékony könyvtár, amely felhatalmazza a fejlesztőket arra, hogy .NET-alkalmazásaikat könnyedén adják hozzá dokumentumjegyzetelési képességeket. Függetlenül attól, hogy dokumentumkezelő rendszert, együttműködési platformot vagy bármilyen dokumentum-ellenőrzést és -jelölést igénylő alkalmazást épít, a GroupDocs.Annotation for .NET átfogó eszközkészletet kínál a folyamat egyszerűsítésére.
Ebben az oktatóanyagban a GroupDocs.Annotation .NET mérőszámos licencének beállításának folyamatát mutatjuk be. A mért licenc lehetővé teszi, hogy csak a felhasznált erőforrásokért fizessen, így költséghatékony megoldást jelent bármilyen méretű projekthez. Az alábbiakban vázolt lépések követésével zökkenőmentesen integrálhatja a GroupDocs.Annotationt .NET-alkalmazásába, miközben optimalizálja az erőforrás-felhasználást és fenntartja a költségvetés ellenőrzését.
## Előfeltételek
Mielőtt belevágna az oktatóanyagba, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:
1.  GroupDocs.Annotation for .NET Library: Töltse le a könyvtárat a[weboldal](https://releases.groupdocs.com/annotation/net/).
2. Hozzáférés a GroupDocs-fiókhoz: GroupDocs-fiókra lesz szüksége, hogy megszerezze a mérőszámos licenc beállításához szükséges nyilvános és privát kulcsokat. Ha még nincs fiókja, regisztrálhat egy ingyenes próbaverzióra[itt](https://releases.groupdocs.com/).
3. A C# és a .NET-keretrendszer alapvető ismerete: A C# programozási nyelv és a .NET-keretrendszer ismerete előnyös lesz az oktatóanyagban vázolt lépések végrehajtásához.

## Névterek importálása
A kezdéshez feltétlenül importálja a szükséges névtereket a C# projektbe. Ezek a névterek elengedhetetlenek a GroupDocs.Annotation funkcióval való együttműködéshez.
```csharp
using System;
```
## 1. lépés: szerezzen be nyilvános és privát kulcsokat
A mért licenc beállítása előtt be kell szereznie nyilvános és privát kulcsait GroupDocs-fiókjának irányítópultjáról.
1. Jelentkezzen be GroupDocs-fiókjába.
2. Navigáljon a licenckezelés szakaszhoz.
3. Másolja ki a GroupDocs által biztosított nyilvános és privát kulcsokat.
## 2. lépés: Állítsa be a mért licencet
Miután megszerezte nyilvános és privát kulcsait, beállíthatja a mért licencet a .NET alkalmazásban.
```csharp
string publicKey = "*****"; // Cserélje ki a *****-t a nyilvános kulcsával
string privateKey = "*****"; // Cserélje ki a *****-t privát kulcsával
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Következtetés
Összefoglalva, a mérőszámos licenc beállítása a GroupDocs.Annotation .NET számára egy egyszerű folyamat, amely hatékony erőforrás-felhasználást és költséghatékonyságot biztosít dokumentumannotációs projektjei számára. Az oktatóanyagban ismertetett lépések követésével zökkenőmentesen integrálhatja a GroupDocs.Annotationt .NET-alkalmazásába, és javíthatja a dokumentumok együttműködését és áttekintését.
## GYIK
### Használhatom a GroupDocs.Annotation for .NET-et kereskedelmi projektekben?
Igen, a GroupDocs.Annotation for .NET használható kereskedelmi és nem kereskedelmi projektekben is. A projekt követelményei alapján azonban megfelelő licencet kell beszereznie.
### Elérhető a GroupDocs.Annotation próbaverziója a .NET-hez?
 Igen, igénybe veheti a GroupDocs.Annotation ingyenes próbaverzióját .NET-hez, ha felkeresi[ez a link](https://releases.groupdocs.com/).
### Hogyan szerezhetek technikai támogatást a GroupDocs.Annotation for .NET-hez?
 Technikai támogatást kérhet a GroupDocs fórumon[itt](https://forum.groupdocs.com/c/annotation/10).
### Vannak ideiglenes licencelési lehetőségek?
 Igen, ideiglenes licencet szerezhet a GroupDocs-tól rövid távú használatra vagy értékelési célokra. Látogatás[ez a link](https://purchase.groupdocs.com/temporary-license/) további információért.
### Testreszabhatom a kommentárokat a projekt követelményei szerint?
Igen, a GroupDocs.Annotation for .NET kiterjedt testreszabási lehetőségeket kínál, amelyek lehetővé teszik a jegyzetelési funkciók testreszabását az adott projekt igényeihez.