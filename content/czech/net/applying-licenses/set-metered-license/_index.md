---
"description": "Naučte se, jak nastavit měřenou licenci pro GroupDocs.Annotation .NET pro využití zdrojů a možnosti anotací dokumentů ve vašich aplikacích .NET."
"linktitle": "Nastavení měřené licence"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Nastavení měřené licence"
"url": "/cs/net/applying-licenses/set-metered-license/"
"weight": 12
---

# Nastavení měřené licence

## Zavedení
GroupDocs.Annotation pro .NET je výkonná knihovna, která vývojářům umožňuje bez námahy přidávat do jejich .NET aplikací funkce pro anotaci dokumentů. Ať už vytváříte systém pro správu dokumentů, platformu pro spolupráci nebo jakoukoli aplikaci, která zahrnuje kontrolu a označování dokumentů, GroupDocs.Annotation pro .NET poskytuje komplexní sadu nástrojů pro zefektivnění celého procesu.
V tomto tutoriálu se ponoříme do procesu nastavení měřené licence pro GroupDocs.Annotation .NET. Měřená licence vám umožňuje platit pouze za zdroje, které spotřebujete, což z ní činí cenově efektivní řešení pro projekty jakéhokoli rozsahu. Dodržením níže uvedených kroků budete moci bezproblémově integrovat GroupDocs.Annotation do vaší aplikace .NET a zároveň optimalizovat využití zdrojů a udržet si kontrolu nad rozpočtem.
## Předpoklady
Než se pustíte do tutoriálu, ujistěte se, že máte následující předpoklady:
1. GroupDocs.Annotation pro knihovnu .NET: Stáhněte si knihovnu z [webové stránky](https://releases.groupdocs.com/annotation/net/).
2. Přístup k účtu GroupDocs: Budete potřebovat účet GroupDocs, abyste získali veřejné a soukromé klíče potřebné k nastavení měřené licence. Pokud ještě nemáte účet, můžete se zaregistrovat k bezplatné zkušební verzi. [zde](https://releases.groupdocs.com/).
3. Základní znalost jazyka C# a .NET Framework: Znalost programovacího jazyka C# a .NET Frameworku bude přínosem pro implementaci kroků popsaných v tomto tutoriálu.

## Importovat jmenné prostory
Nejprve se ujistěte, že jste do svého projektu v C# importovali potřebné jmenné prostory. Tyto jmenné prostory jsou nezbytné pro interakci s funkcí GroupDocs.Annotation.
```csharp
using System;
```
## Krok 1: Získejte veřejné a soukromé klíče
Před nastavením měřené licence je nutné získat veřejný a soukromý klíč z řídicího panelu účtu GroupDocs.
1. Přihlaste se ke svému účtu GroupDocs.
2. Přejděte do sekce správy licencí.
3. Zkopírujte si veřejné a soukromé klíče poskytnuté službou GroupDocs.
## Krok 2: Nastavení měřené licence
Jakmile získáte veřejné a soukromé klíče, můžete ve své aplikaci .NET nastavit měřenou licenci.
```csharp
string publicKey = "*****"; // Nahraďte ***** svým veřejným klíčem
string privateKey = "*****"; // Nahraďte ***** svým soukromým klíčem
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Závěr
Závěrem lze říci, že nastavení měřené licence pro GroupDocs.Annotation .NET je přímočarý proces, který zajišťuje efektivní využití zdrojů a nákladovou efektivitu pro vaše projekty anotací dokumentů. Dodržením kroků popsaných v tomto tutoriálu můžete bezproblémově integrovat GroupDocs.Annotation do vaší aplikace .NET a vylepšit možnosti spolupráce a kontroly dokumentů.
## Často kladené otázky
### Mohu použít GroupDocs.Annotation pro .NET v komerčních projektech?
Ano, GroupDocs.Annotation pro .NET lze použít v komerčních i nekomerčních projektech. Musíte si však zakoupit příslušnou licenci na základě požadavků vašeho projektu.
### Je k dispozici zkušební verze pro GroupDocs.Annotation pro .NET?
Ano, můžete využít bezplatnou zkušební verzi GroupDocs.Annotation pro .NET na adrese [tento odkaz](https://releases.groupdocs.com/).
### Jak mohu získat technickou podporu pro GroupDocs.Annotation pro .NET?
Technickou podporu můžete vyhledat na fóru GroupDocs. [zde](https://forum.groupdocs.com/c/annotation/10).
### Existují nějaké možnosti dočasné licence?
Ano, od GroupDocs můžete získat dočasnou licenci pro krátkodobé použití nebo zkušební účely. Navštivte [tento odkaz](https://purchase.groupdocs.com/temporary-license/) pro více informací.
### Mohu si přizpůsobit funkce anotací podle požadavků mého projektu?
Ano, GroupDocs.Annotation pro .NET nabízí rozsáhlé možnosti přizpůsobení, které vám umožňují přizpůsobit funkce anotací specifickým potřebám vašeho projektu.