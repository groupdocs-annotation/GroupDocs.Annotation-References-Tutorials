---
title: Nastavte měřenou licenci
linktitle: Nastavte měřenou licenci
second_title: GroupDocs.Annotation .NET API
description: Naučte se, jak nastavit měřenou licenci pro GroupDocs.Annotation .NET pro využití zdrojů a možnosti anotací dokumentů ve vašich aplikacích .NET.
weight: 12
url: /cs/net/applying-licenses/set-metered-license/
---

# Nastavte měřenou licenci

## Úvod
GroupDocs.Annotation for .NET je výkonná knihovna, která umožňuje vývojářům snadno přidávat možnosti anotací dokumentů do jejich aplikací .NET. Ať už vytváříte systém správy dokumentů, platformu pro spolupráci nebo jakoukoli aplikaci, která zahrnuje kontrolu a označování dokumentů, GroupDocs.Annotation for .NET poskytuje komplexní sadu nástrojů pro zefektivnění procesu.
V tomto tutoriálu se ponoříme do procesu nastavení měřené licence pro GroupDocs.Annotation .NET. Měřená licence vám umožňuje platit pouze za zdroje, které spotřebováváte, což z ní činí nákladově efektivní řešení pro projekty jakéhokoli rozsahu. Podle níže uvedených kroků budete schopni bezproblémově integrovat GroupDocs.Annotation do vaší aplikace .NET a zároveň optimalizovat využití zdrojů a udržovat kontrolu nad rozpočtem.
## Předpoklady
Než se pustíte do výukového programu, ujistěte se, že máte následující předpoklady:
1.  GroupDocs.Annotation for .NET Library: Stáhněte si knihovnu z[webová stránka](https://releases.groupdocs.com/annotation/net/).
2. Přístup k účtu GroupDocs: K získání veřejných a soukromých klíčů potřebných pro nastavení měřené licence budete potřebovat účet GroupDocs. Pokud ještě nemáte účet, můžete se zaregistrovat k bezplatné zkušební verzi[tady](https://releases.groupdocs.com/).
3. Základní porozumění C# a .NET Framework: Znalost programovacího jazyka C# a .NET Framework bude přínosem pro implementaci kroků uvedených v tomto kurzu.

## Import jmenných prostorů
Chcete-li začít, nezapomeňte importovat potřebné jmenné prostory do svého projektu C#. Tyto jmenné prostory jsou nezbytné pro interakci s funkcí GroupDocs.Annotation.
```csharp
using System;
```
## Krok 1: Získejte veřejný a soukromý klíč
Před nastavením měřené licence musíte získat své veřejné a soukromé klíče z řídicího panelu účtu GroupDocs.
1. Přihlaste se ke svému účtu GroupDocs.
2. Přejděte do sekce správy licencí.
3. Zkopírujte své veřejné a soukromé klíče poskytnuté GroupDocs.
## Krok 2: Nastavte měřenou licenci
Jakmile získáte své veřejné a soukromé klíče, můžete nastavit měřenou licenci ve své aplikaci .NET.
```csharp
string publicKey = "*****"; // Nahraďte ***** svým veřejným klíčem
string privateKey = "*****"; // Nahraďte ***** svým soukromým klíčem
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Závěr
Závěrem lze říci, že nastavení měřené licence pro GroupDocs.Annotation .NET je přímočarý proces, který zajišťuje efektivní využití zdrojů a nákladovou efektivitu pro vaše projekty anotací dokumentů. Podle kroků uvedených v tomto kurzu můžete bez problémů integrovat GroupDocs.Annotation do své aplikace .NET a zlepšit možnosti spolupráce a kontroly dokumentů.
## FAQ
### Mohu použít GroupDocs.Annotation pro .NET v komerčních projektech?
Ano, GroupDocs.Annotation for .NET lze použít v komerčních i nekomerčních projektech. Musíte si však pořídit příslušnou licenci na základě požadavků vašeho projektu.
### Je k dispozici zkušební verze pro GroupDocs.Annotation pro .NET?
 Ano, můžete využít bezplatnou zkušební verzi GroupDocs.Annotation pro .NET návštěvou[tento odkaz](https://releases.groupdocs.com/).
### Jak mohu získat technickou podporu pro GroupDocs.Annotation pro .NET?
 Technickou podporu můžete vyhledat na fóru GroupDocs[tady](https://forum.groupdocs.com/c/annotation/10).
### Jsou k dispozici nějaké dočasné licenční možnosti?
 Ano, můžete získat dočasnou licenci od GroupDocs pro krátkodobé použití nebo pro účely hodnocení. Návštěva[tento odkaz](https://purchase.groupdocs.com/temporary-license/) Pro více informací.
### Mohu přizpůsobit funkce poznámek podle požadavků mého projektu?
Ano, GroupDocs.Annotation for .NET nabízí rozsáhlé možnosti přizpůsobení, které vám umožní přizpůsobit funkce anotací tak, aby vyhovovaly vašim specifickým potřebám projektu.