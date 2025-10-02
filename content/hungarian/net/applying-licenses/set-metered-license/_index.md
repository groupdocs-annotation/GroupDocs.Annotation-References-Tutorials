---
"description": "Ismerje meg, hogyan állíthat be mért licencet a GroupDocs.Annotation .NET-hez az erőforrás-felhasználáshoz és a dokumentumok annotálási képességeihez a .NET-alkalmazásaiban."
"linktitle": "Mért licenc beállítása"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Mért licenc beállítása"
"url": "/hu/net/applying-licenses/set-metered-license/"
type: docs
"weight": 12
---

# Mért licenc beállítása

## Bevezetés
GroupDocs.Annotation for .NET egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára, hogy könnyedén dokumentum-annotációs funkciókat adjanak hozzá .NET alkalmazásaikhoz. Akár dokumentumkezelő rendszert, együttműködési platformot vagy bármilyen olyan alkalmazást épít, amely dokumentumok áttekintését és jelölését is magában foglalja, a GroupDocs.Annotation for .NET átfogó eszközkészletet biztosít a folyamat egyszerűsítéséhez.
Ebben az oktatóanyagban részletesen bemutatjuk a GroupDocs.Annotation .NET mért licencének beállítását. A mért licenc lehetővé teszi, hogy csak a felhasznált erőforrásokért fizessen, így költséghatékony megoldást kínál bármilyen méretű projekthez. Az alábbi lépéseket követve zökkenőmentesen integrálhatja a GroupDocs.Annotationt .NET alkalmazásába, miközben optimalizálja az erőforrás-felhasználást és fenntartja a költségvetési ellenőrzést.
## Előfeltételek
Mielőtt belevágnál az oktatóanyagba, győződj meg róla, hogy a következő előfeltételekkel rendelkezel:
1. GroupDocs.Annotation .NET könyvtárhoz: Töltse le a könyvtárat a következő helyről: [weboldal](https://releases.groupdocs.com/annotation/net/).
2. Hozzáférés a GroupDocs fiókhoz: A mért licenc beállításához szükséges nyilvános és privát kulcsok beszerzéséhez GroupDocs fiókra lesz szüksége. Ha még nincs fiókja, regisztrálhat egy ingyenes próbaverzióra. [itt](https://releases.groupdocs.com/).
3. C# és .NET keretrendszer alapismeretek: A C# programozási nyelv és a .NET keretrendszer ismerete előnyös lesz az ebben az oktatóanyagban vázolt lépések megvalósításához.

## Névterek importálása
Kezdésként importáld a szükséges névtereket a C# projektedbe. Ezek a névterek elengedhetetlenek a GroupDocs.Annotation funkcióval való interakcióhoz.
```csharp
using System;
```
## 1. lépés: Nyilvános és privát kulcsok beszerzése
A mért licenc beállítása előtt be kell szereznie a nyilvános és a privát kulcsait a GroupDocs-fiók irányítópultjáról.
1. Jelentkezzen be GroupDocs-fiókjába.
2. Navigáljon a licenckezelési részhez.
3. Másold le a GroupDocs által biztosított nyilvános és privát kulcsaidat.
## 2. lépés: Mért licenc beállítása
Miután megszerezte a nyilvános és a privát kulcsokat, beállíthatja a mért licencet a .NET-alkalmazásában.
```csharp
string publicKey = "*****"; // Cserélje ki a ***** részt a nyilvános kulcsára
string privateKey = "*****"; // Cserélje ki a *****-t a privát kulcsával
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Következtetés
Összefoglalva, a GroupDocs.Annotation .NET mért licencének beállítása egy egyszerű folyamat, amely hatékony erőforrás-kihasználást és költséghatékonyságot biztosít a dokumentum-annotációs projektekhez. Az ebben az oktatóanyagban ismertetett lépéseket követve zökkenőmentesen integrálhatja a GroupDocs.Annotationt .NET alkalmazásába, és javíthatja a dokumentumok együttműködési és áttekintési képességeit.
## GYIK
### Használhatom a GroupDocs.Annotation for .NET-et kereskedelmi projektekben?
Igen, a GroupDocs.Annotation for .NET használható mind kereskedelmi, mind nem kereskedelmi projektekben. Azonban a projekt igényei alapján megfelelő licencet kell beszereznie.
### Van elérhető próbaverzió a GroupDocs.Annotation for .NET-hez?
Igen, igénybe veheti a GroupDocs.Annotation for .NET ingyenes próbaverzióját a következő címen: [ezt a linket](https://releases.groupdocs.com/).
### Hogyan kaphatok technikai támogatást a GroupDocs.Annotation for .NET-hez?
Technikai támogatást kérhet a GroupDocs fórumon. [itt](https://forum.groupdocs.com/c/annotation/10).
### Vannak ideiglenes engedélyek?
Igen, beszerezhet ideiglenes licencet a GroupDocs-tól rövid távú használatra vagy kiértékelési célokra. Látogassa meg a következőt: [ezt a linket](https://purchase.groupdocs.com/temporary-license/) további információkért.
### Testreszabhatom a jegyzetelési funkciókat a projektem követelményeinek megfelelően?
Igen, a GroupDocs.Annotation for .NET széleskörű testreszabási lehetőségeket kínál, lehetővé téve, hogy a jegyzetelési funkciókat az adott projekt igényeihez igazítsa.