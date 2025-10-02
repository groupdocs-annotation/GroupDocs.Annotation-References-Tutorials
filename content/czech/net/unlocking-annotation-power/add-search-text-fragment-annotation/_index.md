---
"description": "Prozkoumejte sílu GroupDocs.Annotation pro .NET a snadno přidejte do svých aplikací funkce pro anotaci dokumentů."
"linktitle": "Přidat anotaci fragmentu hledaného textu do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Přidat anotaci fragmentu hledaného textu do dokumentu"
"url": "/cs/net/unlocking-annotation-power/add-search-text-fragment-annotation/"
type: docs
"weight": 20
---

# Přidat anotaci fragmentu hledaného textu do dokumentu

## Zavedení
V oblasti vývoje v .NET vyniká GroupDocs.Annotation jako výkonný nástroj pro bezproblémové anotace dokumentů. Ať už jste zkušený vývojář, nebo teprve vstupujete do světa .NET, tento komplexní tutoriál vás provede základy používání GroupDocs.Annotation pro .NET, od importu jmenných prostorů až po zvládnutí složitostí přidávání anotací fragmentů hledaného textu do vašich dokumentů.
## Zavedení
GroupDocs.Annotation pro .NET umožňuje vývojářům snadno začlenit funkce anotace dokumentů do svých aplikací. Díky intuitivnímu API a robustním funkcím mohou vývojáři anotovat různé formáty dokumentů, včetně PDF, dokumentů Microsoft Office, obrázků a dalších.
## Předpoklady
Než se ponoříte do GroupDocs.Annotation pro .NET, ujistěte se, že máte splněny následující předpoklady:

## Importovat jmenné prostory
Nejprve importujte potřebné jmenné prostory pro přístup ke třídám a metodám GroupDocs.Annotation ve vašem projektu .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Definování výstupní cesty
Začněte definováním výstupní cesty, kam bude uložen anotovaný dokument:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Inicializace anotátoru
Dále inicializujte instanci `Annotator` třídu zadáním cesty k dokumentu, který chcete anotovat:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 3: Vytvořte anotaci fragmentu vyhledávacího textu
Vytvořte `SearchTextFragment` objekt s požadovanými vlastnostmi, jako je text k vyhledávání, velikost písma, rodina písma, barva písma a barva pozadí:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## Krok 4: Přidání anotace
Přidejte do dokumentu vytvořenou anotaci fragmentu hledaného textu pomocí `Add` metoda anotátora:
```csharp
annotator.Add(searchText);
```
## Krok 5: Uložení anotovaného dokumentu
Uložte anotovaný dokument do zadané výstupní cesty:
```csharp
annotator.Save(outputPath);
```
## Krok 6: Zobrazení zprávy o úspěchu
Informujte uživatele, že dokument byl úspěšně uložen:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
Závěrem lze říci, že GroupDocs.Annotation pro .NET zjednodušuje proces přidávání anotací do dokumentů, čímž vylepšuje spolupráci a procesy kontroly dokumentů. Dodržováním kroků uvedených v této příručce můžete bezproblémově integrovat funkce anotací dokumentů do svých aplikací .NET.
## Často kladené otázky
### Je GroupDocs.Annotation kompatibilní se všemi formáty dokumentů?
Ano, GroupDocs.Annotation podporuje širokou škálu formátů dokumentů, včetně PDF, dokumentů Microsoft Office, obrázků a dalších.
### Mohu si přizpůsobit vzhled anotací?
Rozhodně! GroupDocs.Annotation nabízí rozsáhlé možnosti přizpůsobení anotací, které vám umožňují upravit vlastnosti, jako je velikost písma, barva a styl.
### Je k dispozici bezplatná zkušební verze GroupDocs.Annotation?
Ano, máte přístup k bezplatné zkušební verzi GroupDocs.Annotation, abyste si před nákupem mohli prohlédnout její funkce a možnosti. [zde](https://releases.groupdocs.com/)..
### Kde najdu podporu pro GroupDocs.Annotation?
Pro podporu a pomoc s GroupDocs.Annotation můžete navštívit GroupDocs [forum](https://forum.groupdocs.com/c/annotation/10) věnované dotazům a diskusím týkajícím se anotací.
### Jak získám dočasnou licenci pro GroupDocs.Annotation?
Dočasnou licenci pro GroupDocs.Annotation můžete získat prostřednictvím GroupDocs [webové stránky](https://purchase.groupdocs.com/temporary-license/), což vám umožní produkt plně vyhodnotit.