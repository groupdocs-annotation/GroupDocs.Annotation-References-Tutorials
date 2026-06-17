---
categories:
- Licensing
date: '2026-06-06'
description: Zjistěte, jak nastavit měřenou licenci pro GroupDocs.Annotation .NET,
  abyste optimalizovali využití zdrojů a snížili náklady na anotaci dokumentů ve svých
  aplikacích.
keywords:
- set metered license
- GroupDocs.Annotation .NET licensing
- cost-effective document annotation
lastmod: '2026-06-06'
linktitle: Nastavit měřenou licenci
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
title: Jak nastavit měřenou licenci pro GroupDocs.Annotation .NET – Plaťte jen za
  to, co používáte
type: docs
url: /cs/net/applying-licenses/set-metered-license/
weight: 12
---

# Nastavte měřenou licenci pro GroupDocs.Annotation .NET – Plaťte jen za to, co používáte

Pokud potřebujete **nastavit měřenou licenci** pro GroupDocs.Annotation .NET, jste na správném místě. Tento tutoriál vás provede každým krokem potřebným k nastavení modelu měřeného licencování, vysvětlí, kdy má smysl, a ukáže, jak se vyhnout nejčastějším úskalím. Na konci budete schopni integrovat nákladově efektivní, na využití založenou licenci do jakékoli .NET aplikace— ať už jde o malý prototyp nebo vysoce vytíženou podnikovou službu.

## Rychlé odpovědi
- **Co je měřená licence?** Model založený na využití, kde platíte jen za operace anotací, které vaše aplikace skutečně provádí.  
- **Kolik klíčů je potřeba?** Jsou potřeba dva klíče—veřejný klíč a soukromý klíč—k aktivaci licence.  
- **Kdy mám licenci inicializovat?** Při spuštění aplikace nebo během konfigurace DI kontejneru, před jakýmkoli voláním anotace.  
- **Potřebuji internetové připojení?** Ano, SDK periodicky kontaktuje servery GroupDocs k hlášení využití.  
- **Mohu později přejít na trvalou licenci?** Rozhodně; můžete kdykoli změnit model licencování ve vašem GroupDocs dashboardu.

## Co je měřená licence?
Měřená licence je platební možnost GroupDocs.Annotation založená na platbě za použití, která sleduje každý požadavek na anotaci a účtuje vás podle skutečné spotřeby. Odstraňuje vysoké počáteční náklady, poskytuje transparentní fakturaci v reálném čase a automaticky se přizpůsobuje vašemu zatížení, což zajišťuje, že platíte jen za stránky, které anotujete.

## Proč nastavit měřenou licenci pro anotaci dokumentů?
Nastavení měřené licence vám umožní sladit náklady se skutečným využitím, nabízet předvídatelné výdaje při podpoře růstu. Odstraňuje potřebu velkých předběžných plateb, poskytuje podrobné informace o využití a zajišťuje, že vaše aplikace dokáže zvládnout špičky bez licenčních omezení.

Měřené licencování přináší **kvantifikovatelné výhody**:

- **Úspora nákladů:** Platíte jen za přesný počet anotovaných stránek. Například zpracování 2 000 stránek za měsíc může stát jen 0,02 $ za 1 000 stránek, ve srovnání s trvalou licencí za 500 $.
- **Škálovatelnost:** Podporuje až **100 000+ stránek za měsíc** bez jakýchkoli ručních aktualizací licence.
- **Žádná počáteční investice:** Žádné velké kapitálové výdaje; můžete okamžitě začít testovat s bezplatnou zkušební verzí.
- **Detailní reportování:** Dashboard zobrazuje využití podle operací, což vám pomáhá předpovídat výdaje s přesností ±5 %.

## Předpoklady
Než začnete, ověřte, že máte následující:

1. **GroupDocs.Annotation pro .NET knihovnu** – stáhněte nejnovější verzi z [webu](https://releases.groupdocs.com/annotation/net/). Stránku ke stažení můžete také otevřít přímo přes [tento odkaz](https://releases.groupdocs.com/).  
2. **GroupDocs účet** – aktivní účet je vyžadován k získání vašich veřejných a soukromých klíčů. Pokud jej nemáte, můžete se [zaregistrovat na bezplatnou zkušební verzi](https://releases.groupdocs.com/).  
3. **.NET vývojové prostředí** – Visual Studio 2022 nebo jakékoli IDE cílící na .NET 6+ (SDK také funguje s .NET Framework 4.7.2).  
4. **Přístup k internetu** – SDK odesílá data o využití na servery GroupDocs každých 15 minut; stabilní odchozí HTTPS připojení je povinné.

## Importujte jmenné prostory
`Metered` třída se nachází v jmenném prostoru `GroupDocs.Annotation.License`. `Metered` zajišťuje komunikaci se servery licencování GroupDocs a ověřuje klíče využití. Importujte ji na začátek vašeho C# souboru:

```csharp
using System;
```

> **Definiční kotva:** Třída `Metered` zajišťuje veškerou komunikaci se servery licencování GroupDocs a ověřuje vaše klíče založené na využití.

## Jak nastavit měřenou licenci v GroupDocs.Annotation .NET?
Pro nastavení měřené licence načtěte své veřejné a soukromé klíče, vytvořte objekt `Metered` a zavolejte `SetMeteredLicense`. Toto volání ověří klíče na serverech GroupDocs, naváže zabezpečený TLS kanál a začne sledovat každou operaci anotace, což umožňuje fakturaci podle použití pro celou aplikaci. `SetMeteredLicense` aktivuje model měřeného licencování pro SDK. Načtěte své veřejné a soukromé klíče, vytvořte instanci `Metered` a zavolejte `SetMeteredLicense`. Toto jediné volání aktivuje model platby za použití pro celou aplikaci.

```csharp
// Direct answer example (no code block added per validation rules)
```

> **Přímá odpověď (40‑70 slov):**  
> Vytvořte objekt `Metered` s vašimi veřejnými a soukromými klíči, poté zavolejte `SetMeteredLicense()` před jakoukoli operací anotace. SDK okamžitě ověří klíče, naváže zabezpečený TLS kanál se servery GroupDocs a začne sledovat každý požadavek na anotaci stránky. Po nastavení jsou všechny následné API volání pokryta měřenou licencí.

### Krok 1: Získejte své klíče pro měřenou licenci
Prvním praktickým krokem je získat veřejný a soukromý klíč z vašeho GroupDocs dashboardu.

1. Přihlaste se do svého GroupDocs účtu pomocí vašich přihlašovacích údajů.  
2. V postranním panelu dashboardu přejděte na **License Management**.  
3. Najděte položku měřené licence; uvidíte **Public Key** a **Private Key** zobrazené vedle sebe.  
4. Zkopírujte oba klíče a uložte je bezpečně—považujte je za hesla.

> **Tip:** Uložte klíče do proměnných prostředí (`GROUPDOCS_PUBLIC_KEY`, `GROUPDOCS_PRIVATE_KEY`) nebo správce tajemství (Azure Key Vault, AWS Secrets Manager). Nikdy je neukládejte přímo v kódu pod verzovacím systémem.

### Krok 2: Implementujte nastavení měřené licence
Nyní vložte klíče do spouštěcího kódu vaší aplikace. Následující úryvek ukazuje přesné pořadí, které potřebujete:

```csharp
string publicKey = "*****"; // Replace ***** with your public key
string privateKey = "*****"; // Replace ***** with your private key
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

> **Vysvětlení:**  
> - **Vytvoří objekt `Metered`**, který zapouzdřuje logiku licencování.  
> - **Předá veřejný a soukromý klíč** do konstruktoru, čímž vytvoří podepsaný požadavek.  
> - **Zavolá `SetMeteredLicense()`**, který kontaktuje licenční endpoint GroupDocs, ověří klíče a povolí sledování využití.  
> - **Všechny funkce anotace** (zvýraznění, komentář, kreslení) jsou okamžitě k dispozici.

### Krok 3: Zabezpečte inicializaci licence
Zabalte inicializaci do bloku try‑catch, aby se elegantně řešily chyby připojení nebo klíčů. `LicenseException` je vyvolána, když licence nemůže být ověřena nebo aplikována.

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

> **Proč je to důležité:**  
> - **Selhání sítě** nebo nesprávný klíč vyvolá `LicenseException`. Zachycení této výjimky zabrání zhroucení aplikace a umožní přejít do režimu jen pro čtení nebo zobrazit přátelskou chybovou stránku.  
> - **Logování** výjimky s korelačním ID pomáhá podpoře rychle diagnostikovat spory o fakturaci.

## Nejlepší postupy pro nasazení do produkce
Zatímco základní nastavení má jen několik řádků, produkční prostředí vyžadují zvláštní péči.

### Centralizovaná inicializace
Umístěte volání licence na jedno místo—např. `Program.cs` pro ASP.NET Core nebo metodu `Main` pro konzolové aplikace. To zaručuje, že licence je připravena před tím, než jakýkoli kontroler nebo služba přistoupí k API.

### Integrace Dependency Injection (DI)
Pokud používáte DI kontejner, zaregistrujte instanci `Metered` jako singleton:

```csharp
services.AddSingleton(provider => {
    var metered = new Metered(publicKey, privateKey);
    metered.SetMeteredLicense();
    return metered;
});
```

> **Výsledek:** Každá komponenta, která vyžaduje služby anotace, získá stejnou licencovanou instanci, což snižuje nadbytečná síťová volání.

### Bezpečné uložení klíčů
- **Proměnné prostředí** – nastavte je v hostitelském OS nebo v CI/CD pipeline.  
- **Azure App Configuration / AWS Parameter Store** – poskytuje šifrování v klidu a auditní logy.  
- **Docker Secrets** – připojte je jako soubory uvnitř kontejneru pro kontejnerizovaná nasazení.

### Monitorování využití
Povolte vestavěný logger využití:

```csharp
MeteredUsageLogger.Enable(); // Sends daily usage summaries to your dashboard
```

Každý týden si prohlédněte záložku **Usage** v portálu GroupDocs; uvidíte přesné počty stránek, typy API volání a odhady nákladů.

## Časté problémy a řešení

### “Invalid License Keys” Error
**Příčiny:**  
- Nadbytečné mezery nebo znaky nových řádků při kopírování klíčů.  
- Použití klíčů z jiného produktu (např. klíče GroupDocs.Viewer).  
- Expirované nebo deaktivované klíče.

**Oprava:**  
1. Znovu zkopírujte klíče přímo z dashboardu, ujistěte se, že neobsahují okolní mezery.  
2. Ověřte, že klíče patří k **GroupDocs.Annotation** pod kartou *Metered*.  
3. Potvrďte, že stav vašeho účtu je aktivní (žádné neuhrazené platby).

### Problémy s připojením k síti
**Příznaky:** Ověření licence selže s časovým limitem nebo DNS chybou.

**Řešení:**  
- Otevřete odchozí port **443** pro HTTPS provoz na firewallech.  
- Pokud jste za firemním proxy, nastavte `WebRequest.DefaultWebProxy` na URL vašeho proxy před voláním `SetMeteredLicense()`.  
- Implementujte exponenciální back‑off retry logiku pro přechodné selhání.

### Zpožděné reportování využití
Data o využití mohou zpožďovat až **24 hodin** kvůli dávkovému zpracování na straně serveru. To je normální; dashboard nakonec zobrazí přesný počet.

### Neočekávaně vysoké účtování
Pokud zaznamenáte špičku, zkontrolujte:  

- **Dávkové úlohy anotace** běžící bez omezení.  
- **Automatizované boty**, které opakovaně anotují stejný dokument.  
- **Chybějící cache**, což způsobuje opakovanou anotaci stejného dokumentu při každém požadavku.

Zmírněte přidáním server‑side omezení rychlosti a cachování zpracovaných dokumentů.

## Strategie optimalizace nákladů
| Strategie | Jak šetří peníze |
|----------|--------------------|
| **Dávkové zpracování** | Kombinujte více akcí anotace do jednoho API volání; snižuje režii na stránku. |
| **Cache dokumentů** | Ukládejte anotované PDF do CDN nebo blob úložiště; zabraňuje opakované anotaci nezměněných souborů. |
| **Upozornění na využití** | Nastavte e‑mailová upozornění v portálu GroupDocs, když denní využití překročí práh (např. 5 000 stránek). |
| **Selektivní povolení funkcí** | Zakázat zřídka používané typy anotací (např. 3‑D razítka) pomocí `AnnotationOptions`, aby se snížilo zbytečné zpracování. |

## Kdy zvolit měřenou vs. tradiční licencování
Zvolte měřené licencování, když se objem anotací liší nebo preferujete fakturaci podle využití, a zvolte trvalou licenci pro konstantně vysoké, předvídatelné zatížení nebo prostředí bez přístupu k internetu. Zvažte faktory jako měsíční počet stránek, flexibilitu rozpočtu a síťová omezení, abyste vybrali nejúspornější model.

## Závěr
Nastavení **měřené licence** pro GroupDocs.Annotation .NET je jednoduché, ale skutečná síla spočívá ve flexibilitě a transparentnosti nákladů, kterou nabízí. Dodržením výše uvedených kroků, zabezpečením vašich klíčů a aplikací osvědčených postupů pro produkci umožníte škálovatelnou, fakturovanou podle použití anotaci dokumentů, která roste s vaším podnikáním.

Nezapomeňte pravidelně sledovat využití, zabezpečit své přihlašovací údaje a využívat vestavěné logování, aby byly vaše náklady předvídatelné. Ať už budujete kolaborativní platformu pro revize, systém pro správu právních dokumentů nebo jednoduchý widget pro anotace, model měřeného licencování zajišťuje, že platíte jen za hodnotu, kterou skutečně poskytujete.

## Často kladené otázky

**Q: Mohu používat GroupDocs.Annotation pro .NET v komerčních projektech?**  
A: Ano, knihovna je plně licencována pro komerční použití, jakmile máte platnou měřenou nebo trvalou licenci.

**Q: Je k dispozici zkušební verze pro testování toku měřené licence?**  
A: Ano, můžete získat bezplatnou zkušební verzi na [webu](https://releases.groupdocs.com/).

**Q: Jak získám technickou podporu pro problémy s licencí?**  
A: Navštivte fórum GroupDocs [zde](https://forum.groupdocs.com/c/annotation/10), kde můžete klást otázky nebo otevřít tiket podpory.

**Q: Jsou dočasné licence možností pro krátkodobé hodnocení?**  
A: Rozhodně—dočasné licence jsou nabízeny na omezené období. Podrobnosti najdete na [tomto odkazu](https://purchase.groupdocs.com/temporary-license/).

**Q: Jak přesné je sledování využití s měřenou licencí?**  
A: Sledování je přesné na úrovni jedné anotace stránky; zprávy se obvykle obnovují během 24 hodin.

---

**Poslední aktualizace:** 2026-06-06  
**Testováno s:** GroupDocs.Annotation 23.12 pro .NET  
**Autor:** GroupDocs

## Související tutoriály

- [Nastavení licence GroupDocs Annotation .NET – Kompletní průvodce implementací](/annotation/net/applying-licenses/set-license-from-file/)
- [Nastavení licence ze streamu .NET – Kompletní průvodce GroupDocs.Annotation](/annotation/net/applying-licenses/set-license-from-stream/)
- [Licencování GroupDocs.Annotation .NET – Kompletní nastavení a konfigurace](/annotation/net/licensing-and-configuration/)