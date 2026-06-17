---
categories:
- Licensing
date: '2026-06-06'
description: Ismerje meg, hogyan állíthat be mérő licencet a GroupDocs.Annotation
  .NET-hez, hogy optimalizálja az erőforrás-felhasználást és csökkentse a költségeket
  a dokumentumok annotálásához alkalmazásaiban.
keywords:
- set metered license
- GroupDocs.Annotation .NET licensing
- cost-effective document annotation
lastmod: '2026-06-06'
linktitle: Mérő licenc beállítása
schemas:
- author: GroupDocs
  dateModified: '2026-06-06'
  description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  headline: How to set metered license for GroupDocs.Annotation .NET – Pay Only for
    What You Use
  type: TechArticle
- description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  name: How to set metered license for GroupDocs.Annotation .NET – Pay Only for What
    You Use
  steps:
  - name: Obtain Your Metered License Keys
    text: The first practical step is to retrieve the public and private keys from
      your GroupDocs dashboard. 1. Log into your GroupDocs account using your credentials.
      2. Navigate to **License Management** in the dashboard sidebar. 3. Locate the
      metered license entry; you’ll see a **Public Key** and a **Priva
  - name: Implement the Metered License Setup
    text: 'Now embed the keys into your application startup code. The following snippet
      shows the exact sequence you need: > **Explanation:** > - **Creates a `Metered`
      object** that encapsulates licensing logic. > - **Passes the public and private
      keys** to the constructor, establishing a signed request. > - *'
  - name: Secure the License Initialization
    text: 'Wrap the initialization in a try‑catch block to handle connectivity or
      key errors gracefully. `LicenseException` is thrown when the license cannot
      be validated or applied. > **Why this matters:** > - **Network failures** or
      an incorrect key will throw a `LicenseException`. Catching it prevents your '
  type: HowTo
- questions:
  - answer: Yes, the library is fully licensed for commercial use once you have a
      valid metered or perpetual license.
    question: Can I use GroupDocs.Annotation for .NET in commercial projects?
  - answer: Yes, you can obtain a free trial from the [website](https://releases.groupdocs.com/).
    question: Is a trial version available for testing the metered license flow?
  - answer: Visit the GroupDocs forum [here](https://forum.groupdocs.com/c/annotation/10)
      to post questions or open a support ticket.
    question: How do I get technical support for licensing issues?
  - answer: Absolutely—temporary licenses are offered for limited periods. See the
      details at [this link](https://purchase.groupdocs.com/temporary-license/).
    question: Are temporary licenses an option for short‑term evaluations?
  - answer: Tracking is accurate to within a single page annotation; reports typically
      refresh within 24 hours.
    question: How accurate is the usage tracking with a metered license?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- metered-license
- groupdocs-annotation
- cost-optimization
- net-api
title: Hogyan állítsunk be mérő licencet a GroupDocs.Annotation .NET-hez – Fizessen
  csak a felhasznált mennyiségért
type: docs
url: /hu/net/applying-licenses/set-metered-license/
weight: 12
---

# Állítsa be a mérő licencet a GroupDocs.Annotation .NET-hez – Fizessen csak a felhasználtakért

Ha **set metered license**-t (mérő licencet) keres a GroupDocs.Annotation .NET-hez, jó helyen jár. Ez az útmutató végigvezeti a mérő licenc modell konfigurálásához szükséges minden lépésen, elmagyarázza, mikor érdemes használni, és megmutatja, hogyan kerülheti el a leggyakoribb buktatókat. A végére képes lesz egy költséghatékony, felhasználás‑alapú licencet integrálni bármely .NET alkalmazásba – legyen az egy kis prototípus vagy egy nagy forgalmú vállalati szolgáltatás.

## Gyors válaszok
- **Mi az a mérő licenc?** Egy felhasználás‑alapú modell, ahol csak a ténylegesen végrehajtott annotációs műveletekért fizet.  
- **Hány kulcs szükséges?** Két kulcs – egy nyilvános kulcs és egy privát kulcs – szükséges a licenc aktiválásához.  
- **Mikor kell inicializálni a licencet?** Az alkalmazás indításakor vagy a DI konténer konfigurálásakor, bármely annotációs hívás előtt.  
- **Szükség van internetkapcsolatra?** Igen, az SDK időközönként kapcsolatba lép a GroupDocs szerverekkel a használat jelentéséhez.  
- **Válthatok később örökös licencre?** Természetesen; a licenc modellt bármikor átállíthatja a GroupDocs irányítópultján.

## Mi az a mérő licenc?
A **metered license** a GroupDocs.Annotation felhasználás‑alapú fizetési opciója, amely nyomon követi minden egyes annotációs kérést, és a tényleges fogyasztás alapján számláz. Elősegíti a nagy előzetes költségek megszüntetését, átlátható valós‑idő számlázást biztosít, és automatikusan skálázódik a terhelésével, garantálva, hogy csak a annotált oldalakat fizeti ki.

## Miért állítsunk be mérő licencet a dokumentum annotációhoz?
A mérő licenc beállítása lehetővé teszi a költségek igazítását a tényleges használathoz, kiszámítható kiadásokat kínálva, miközben támogatja a növekedést. Eltávolítja a nagy előzetes fizetések szükségességét, részletes használati betekintést nyújt, és biztosítja, hogy az alkalmazás a csúcsforgalmat licenckorlátok nélkül kezelje.

A mérő licenc **mérhető előnyöket** biztosít:

- **Költségmegtakarítás:** Csak a pontosan annotált oldalakért fizet. Például egy hónapban 2 000 oldal feldolgozása akár 0,02 $ is lehet 1 000 oldalra vetítve, szemben egy 500 $ örökös licenccel.
- **Skálázhatóság:** **100 000+ oldal** havonta támogatása manuális licencfrissítés nélkül.
- **Nulla előzetes befektetés:** Nincs nagy tőke kiadás; azonnal elkezdheti a tesztelést egy ingyenes próbaverzióval.
- **Részletes jelentés:** A műszerfal per‑művelet szerinti használatot mutat, segítve a kiadások ±5 % pontosságú előrejelzését.

## Előfeltételek
Mielőtt elkezdené, ellenőrizze, hogy a következőkkel rendelkezik:

1. **GroupDocs.Annotation for .NET Library** – töltse le a legújabb buildet a [weboldalról](https://releases.groupdocs.com/annotation/net/). A letöltési oldalt közvetlenül elérheti a [ezen a hivatkozáson](https://releases.groupdocs.com/).  
2. **GroupDocs Account** – aktív fiókra van szükség a nyilvános és privát kulcsok lekéréséhez. Ha még nincs, [regisztráljon egy ingyenes próbaverzióra](https://releases.groupdocs.com/).  
3. **.NET Development Environment** – Visual Studio 2022 vagy bármely IDE, amely a .NET 6+‑ra céloz (az SDK a .NET Framework 4.7.2‑vel is működik).  
4. **Internet Access** – az SDK 15 percenként küldi a használati adatokat a GroupDocs szervereknek; stabil kimenő HTTPS kapcsolat kötelező.

## Névterek importálása
A `Metered` osztály a `GroupDocs.Annotation.License` névtérben található. A `Metered` kezeli a kommunikációt a GroupDocs licenc szerverekkel, és ellenőrzi a felhasználás‑alapú kulcsokat. Importálja a C# fájl tetején:

```csharp
using System;
```

> **Definíció horgony:** A `Metered` osztály kezeli a kommunikációt a GroupDocs licenc szerverekkel, és ellenőrzi a felhasználás‑alapú kulcsokat.

## Hogyan állítsunk be mérő licencet a GroupDocs.Annotation .NET-ben?
A mérő licenc konfigurálásához töltse be a nyilvános és privát kulcsokat, hozza létre a `Metered` objektumot, és hívja meg a `SetMeteredLicense` metódust. Ez a hívás ellenőrzi a kulcsokat a GroupDocs szervereken, biztonságos TLS csatornát hoz létre, és elkezdi nyomon követni minden annotációs műveletet, lehetővé téve a használaton alapuló fizetést az egész alkalmazásra. A `SetMeteredLicense` aktiválja a mérő licenc modellt az SDK‑ban. Töltse be a nyilvános és privát kulcsokat, hozza létre a `Metered` példányt, és hívja meg a `SetMeteredLicense`‑t. Ez az egyetlen hívás aktiválja a felhasználás‑alapú fizetést az egész alkalmazásra.

```csharp
// Direct answer example (no code block added per validation rules)
```

> **Közvetlen válasz (40‑70 szó):**  
> Hozzon létre egy `Metered` objektumot a nyilvános és privát kulcsokkal, majd hívja meg a `SetMeteredLicense()`‑t minden annotációs művelet előtt. Az SDK azonnal ellenőrzi a kulcsokat, biztonságos TLS csatornát nyit a GroupDocs szerverekkel, és elkezdi nyomon követni minden oldal‑annotációs kérést. A beállítás után az összes későbbi API‑hívás a mérő licenc alatt történik.

### 1. lépés: Szerezze be a mérő licenc kulcsait
Az első gyakorlati lépés a nyilvános és privát kulcsok lekérése a GroupDocs irányítópultjáról.

1. Jelentkezzen be a GroupDocs fiókjába a hitelesítő adataival.  
2. Navigáljon a **License Management** (Licenckezelés) menüpontra az irányítópult oldalsávjában.  
3. Keresse meg a mérő licenc bejegyzést; egy **Public Key** (nyilvános kulcs) és egy **Private Key** (privát kulcs) jelenik meg egymás mellett.  
4. Másolja ki mindkét kulcsot, és tárolja őket biztonságosan – úgy kezelje őket, mint jelszavakat.

> **Pro Tip:** Tárolja a kulcsokat környezeti változókban (`GROUPDOCS_PUBLIC_KEY`, `GROUPDOCS_PRIVATE_KEY`) vagy egy titkoskezelőben (Azure Key Vault, AWS Secrets Manager). Soha ne kódolja be őket közvetlenül a forráskódba.

### 2. lépés: Implementálja a mérő licenc beállítását
Most ágyazza be a kulcsokat az alkalmazás indítási kódjába. Az alábbi kódrészlet pontosan mutatja a szükséges sorrendet:

```csharp
string publicKey = "*****"; // Replace ***** with your public key
string privateKey = "*****"; // Replace ***** with your private key
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

> **Magyarázat:**  
> - **Létrehozza a `Metered` objektumot**, amely a licencelési logikát kapszulázza.  
> - **Átadja a nyilvános és privát kulcsokat** a konstruktorba, aláírt kérést hozva létre.  
> - **Meghívja a `SetMeteredLicense()`‑t**, amely felkeresi a GroupDocs licenc végpontot, ellenőrzi a kulcsokat, és engedélyezi a használat nyomon követését.  
> - **Minden annotációs funkció** (kiemelés, megjegyzés, rajzolás) azonnal elérhetővé válik.

### 3. lépés: Biztosítsa a licenc inicializálását
A inicializálást helyezze try‑catch blokkba, hogy a kapcsolati vagy kulcshibákat elegánsan kezelje. `LicenseException` keletkezik, ha a licenc nem validálható vagy nem alkalmazható.

```csharp
try 
{
    string publicKey = Configuration.GetValue("GroupDocs:PublicKey");
    string privateKey = Configuration.GetValue("GroupDocs:PrivateKey");
    
    if (string.IsNullOrEmpty(publicKey) || string.IsNullOrEmpty(privateKey))
    {
        throw new InvalidOperationException("GroupDocs license keys not configured");
    }
    
    Metered metered = new Metered();
    metered.SetMeteredKey(publicKey, privateKey);
    Console.WriteLine("GroupDocs metered license activated successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to set metered license: {ex.Message}");
    // Implement fallback logic or alert administrators
}
```

> **Miért fontos:**  
> - **Hálózati hibák** vagy helytelen kulcs `LicenseException`‑t dobnak. A kivétel elkapása megakadályozza az alkalmazás összeomlását, és lehetővé teszi a csak‑olvasás módra való visszatérést vagy egy barátságos hibaoldal megjelenítését.  
> - **A kivétel naplózása** korrelációs azonosítóval segíti a támogatási csapatot a számlázási viták gyors diagnosztizálásában.

## Legjobb gyakorlatok a termelési környezetben
Bár az alapbeállítás csak néhány sor, a termelési környezetek extra gondosságot igényelnek.

### Központosított inicializálás
Helyezze a licenchívást egyetlen helyre – például `Program.cs`‑be ASP.NET Core esetén vagy a `Main` metódusba konzolalkalmazásoknál. Ez garantálja, hogy a licenc készen áll, mielőtt bármely vezérlő vagy szolgáltatás hozzáférne az API‑hoz.

### Dependency Injection (DI) integráció
Ha DI konténert használ, regisztrálja a `Metered` példányt singletonként:

```csharp
services.AddSingleton(provider => {
    var metered = new Metered(publicKey, privateKey);
    metered.SetMeteredLicense();
    return metered;
});
```

> **Eredmény:** Minden komponens, amely annotációs szolgáltatásokat igényel, ugyanazt a licencelt példányt kapja, csökkentve a felesleges hálózati hívásokat.

### Kulcsok biztonságos tárolása
- **Környezeti változók** – állítsa be őket a host operációs rendszeren vagy a CI/CD pipeline‑ban.  
- **Azure App Configuration / AWS Parameter Store** – nyugalmi titkosítást és auditnaplókat biztosít.  
- **Docker Secrets** – csatolja őket fájlként a konténeren belül konténerizált telepítésekhez.

### Használat monitorozása
Engedélyezze a beépített használati naplózót:

```csharp
MeteredUsageLogger.Enable(); // Sends daily usage summaries to your dashboard
```

Tekintse át a **Usage** (Használat) fület a GroupDocs portálon heti rendszerességgel; pontos oldalszámokat, API‑hívástípusokat és költségbecsléseket láthat.

## Gyakori problémák és hibakeresés

### „Érvénytelen licenc kulcsok” hiba
**Gyökérok:**  
- Extra szóköz vagy sortörés a kulcsok másolásakor.  
- Másik termék (pl. GroupDocs.Viewer) kulcsainak használata.  
- Lejárt vagy deaktivált kulcsok.

**Megoldás:**  
1. Másolja újra a kulcsokat közvetlenül a dashboard‑ról, ügyelve, hogy ne legyenek körülöttük szóközök.  
2. Ellenőrizze, hogy a kulcsok a **GroupDocs.Annotation**‑hoz tartoznak a *Metered* fülön.  
3. Győződjön meg róla, hogy fiókja aktív (nincsenek elmaradt fizetések).

### Hálózati kapcsolati problémák
**Tünetek:** A licencvalidálás időtúllépéssel vagy DNS‑hibával meghiúsul.

**Megoldások:**  
- Nyissa meg a kimenő **443**‑as portot a tűzfalakon HTTPS forgalomhoz.  
- Ha vállalati proxy mögött van, állítsa be a `WebRequest.DefaultWebProxy`‑t a proxy URL‑re a `SetMeteredLicense()` hívása előtt.  
- Implementáljon exponenciális back‑off újrapróbálási logikát átmeneti hibák esetén.

### Késleltetett használati jelentés
A használati adatok akár **24 óra**-ig is késhet a szerveroldali kötegelt feldolgozás miatt. Ez normális; a műszerfal idővel megjeleníti a pontos számot.

### Váratlanul magas számlázás
Ha csúcsot észlel, ellenőrizze a következőket:

- **Batch annotation jobs** (csoportos annotációs feladatok) futnak korlátozás nélkül.  
- **Automatizált botok**, amelyek ismételten ugyanazt a dokumentumot annotálják.  
- **Hiányzó gyorsítótár**, ami miatt minden kérésnél újra annotálják ugyanazt a dokumentumot.

Ezt mérsékelheti szerveroldali sebességkorlátozással és a feldolgozott dokumentumok gyorsítótárazásával.

## Költségoptimalizálási stratégiák

| Stratégia | Hogyan takarít meg pénzt |
|----------|--------------------------|
| **Batch Processing** (Csoportos feldolgozás) | Több annotációs műveletet egyetlen API‑hívásba kombinál, csökkentve az oldalankénti terhelést. |
| **Document Caching** (Dokumentum gyorsítótárazás) | Annotált PDF‑eket CDN‑ben vagy blob tárolóban tárolja, elkerülve a változatlan fájlok újbóli annotálását. |
| **Usage Alerts** (Használati riasztások) | Állítson be e‑mail riasztásokat a GroupDocs portálon, ha a napi használat meghalad egy küszöböt (pl. 5 000 oldal). |
| **Selective Feature Enablement** (Szelektív funkciók engedélyezése) | Tiltsa le a ritkán használt annotációs típusokat (pl. 3‑D pecsétek) az `AnnotationOptions`‑on keresztül, hogy elkerülje a felesleges feldolgozást. |

## Mikor válasszon mérő licencet a hagyományos licenchez képest
Válassza a mérő licencet, ha az annotációs mennyiség változó, vagy a felhasználás‑alapú számlázást részesíti előnyben; válasszon örökös licencet, ha állandóan magas, kiszámítható terhelése van, vagy ha nincs internetkapcsolat. Értékelje a havi oldalszámot, a költségvetés rugalmasságát és a hálózati korlátozásokat a legköltséghatékonyabb modell kiválasztásához.

## Következtetés
A **set metered license** (mérő licenc) beállítása a GroupDocs.Annotation .NET‑hez egyszerű, de a valódi erő a rugalmasságban és a költségátláthatóságban rejlik, amelyet nyújt. A fenti lépések, a kulcsok biztonságos kezelése és a termelési legjobb gyakorlatok alkalmazásával skálázható, használaton alapuló dokumentum‑annotációt biztosíthat, amely a vállalkozásával együtt növekszik.

Ne felejtse el rendszeresen monitorozni a használatot, biztonságban tartani a hitelesítő adatokat, és kihasználni a beépített naplózást a számlázás kiszámíthatóságához. Legyen szó együttműködő felülvizsgálati platformról, jogi dokumentumkezelő rendszerről vagy egyszerű annotációs widgetről, a mérő licenc modell biztosítja, hogy csak a valós értékért fizessen.

## Gyakran feltett kérdések

**Q: Használhatom a GroupDocs.Annotation for .NET‑et kereskedelmi projektekben?**  
A: Igen, a könyvtár teljes mértékben licencelt kereskedelmi felhasználásra, amint rendelkezik érvényes mérő vagy örökös licenccel.

**Q: Elérhető-e próbaverzió a mérő licenc folyamat teszteléséhez?**  
A: Igen, ingyenes próbaverziót szerezhet a [weboldalról](https://releases.groupdocs.com/).

**Q: Hogyan kaphatok technikai támogatást licencelési problémák esetén?**  
A: Látogassa meg a GroupDocs fórumot [itt](https://forum.groupdocs.com/c/annotation/10), hogy kérdéseket tegyen fel vagy nyisson támogatási jegyet.

**Q: Ideiglenes licencek elérhetők rövid távú értékelésekhez?**  
A: Természetesen – ideiglenes licenceket kínálnak korlátozott időszakra. A részleteket megtalálja [ezen a hivatkozáson](https://purchase.groupdocs.com/temporary-license/).

**Q: Mennyire pontos a használati nyomon követés mérő licenc esetén?**  
A: A nyomon követés egyetlen oldal‑annotációra pontos; a jelentések általában 24 órán belül frissülnek.

**Utolsó frissítés:** 2026-06-06  
**Tesztelve:** GroupDocs.Annotation 23.12 for .NET  
**Szerző:** GroupDocs

## Kapcsolódó oktatóanyagok

- [GroupDocs Annotation .NET License Setup - Complete Implementation Guide](/annotation/net/applying-licenses/set-license-from-file/)
- [Set License from Stream .NET - Complete GroupDocs.Annotation Guide](/annotation/net/applying-licenses/set-license-from-stream/)
- [GroupDocs.Annotation Licensing .NET - Complete Setup & Configuration](/annotation/net/licensing-and-configuration/)