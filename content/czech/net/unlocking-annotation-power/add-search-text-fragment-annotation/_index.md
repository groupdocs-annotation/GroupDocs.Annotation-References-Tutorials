---
title: Přidejte do dokumentu anotaci fragmentu vyhledávacího textu
linktitle: Přidejte do dokumentu anotaci fragmentu vyhledávacího textu
second_title: GroupDocs.Annotation .NET API
description: Prozkoumejte sílu GroupDocs.Annotation pro .NET a bez námahy přidejte do svých aplikací možnosti anotací dokumentů.
weight: 20
url: /cs/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---
## Úvod
V oblasti vývoje .NET GroupDocs.Annotation vyniká jako výkonný nástroj pro bezproblémové anotování dokumentů. Ať už jste ostřílený vývojář nebo teprve vstupujete do světa .NET, tento obsáhlý tutoriál vás provede základy používání GroupDocs.Annotation pro .NET, od importu jmenných prostorů až po zvládnutí složitostí přidávání anotací fragmentů vyhledávacího textu do vašich dokumenty.
## Úvod
GroupDocs.Annotation for .NET umožňuje vývojářům bez námahy začlenit možnosti anotací dokumentů do svých aplikací. Díky intuitivnímu rozhraní API a robustním funkcím mohou vývojáři anotovat různé formáty dokumentů, včetně PDF, dokumentů Microsoft Office, obrázků a dalších.
## Předpoklady
Než se ponoříte do GroupDocs.Annotation pro .NET, ujistěte se, že máte splněny následující předpoklady:

## Import jmenných prostorů
Nejprve naimportujte potřebné jmenné prostory pro přístup ke třídám a metodám GroupDocs.Annotation ve vašem projektu .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Definujte výstupní cestu
Začněte definováním výstupní cesty, kam bude dokument s poznámkami uložen:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Inicializujte anotátor
 Dále inicializujte instanci souboru`Annotator` třídy zadáním cesty k dokumentu, který chcete anotovat:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 3: Vytvořte anotaci fragmentu vyhledávacího textu
 Vytvořit`SearchTextFragment` objekt s požadovanými vlastnostmi, jako je text k vyhledávání, velikost písma, rodina písem, barva písma a barva pozadí:
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
## Krok 4: Přidejte anotaci
 Přidejte vytvořenou anotaci fragmentu hledaného textu do dokumentu pomocí`Add` metoda anotátora:
```csharp
annotator.Add(searchText);
```
## Krok 5: Uložte dokument s poznámkami
Uložte anotovaný dokument do zadané výstupní cesty:
```csharp
annotator.Save(outputPath);
```
## Krok 6: Zobrazte zprávu o úspěchu
Informujte uživatele, že dokument byl úspěšně uložen:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
Na závěr, GroupDocs.Annotation for .NET zjednodušuje proces přidávání anotací k dokumentům, zlepšuje spolupráci a procesy kontroly dokumentů. Podle kroků uvedených v této příručce můžete bez problémů integrovat možnosti anotací dokumentů do aplikací .NET.
## FAQ
### Je GroupDocs.Annotation kompatibilní se všemi formáty dokumentů?
Ano, GroupDocs.Annotation podporuje širokou škálu formátů dokumentů, včetně PDF, dokumentů Microsoft Office, obrázků a dalších.
### Mohu upravit vzhled anotací?
Absolutně! GroupDocs.Annotation poskytuje rozsáhlé možnosti přizpůsobení pro anotace, což vám umožňuje upravit vlastnosti, jako je velikost písma, barva a styl.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Annotation?
 Ano, před nákupem máte přístup k bezplatné zkušební verzi GroupDocs.Annotation a prozkoumejte její funkce a možnosti[tady](https://releases.groupdocs.com/)..
### Kde najdu podporu pro GroupDocs.Annotation?
 Pro podporu a pomoc s GroupDocs.Annotation můžete navštívit GroupDocs[Fórum](https://forum.groupdocs.com/c/annotation/10) věnované dotazům a diskusím souvisejícím s anotací.
### Jak získám dočasnou licenci pro GroupDocs.Annotation?
 Prostřednictvím GroupDocs můžete získat dočasnou licenci pro GroupDocs.Annotation[webová stránka](https://purchase.groupdocs.com/temporary-license/), což vám umožní plně ohodnotit produkt.