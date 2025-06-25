---
"description": "Naučte se, jak přidávat anotace s zvýrazněním textu do dokumentů pomocí nástroje GroupDocs.Annotation pro .NET. Vylepšete spolupráci a produktivitu s tímto komplexním nástrojem."
"linktitle": "Přidat anotaci zvýraznění textu do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Přidat anotaci zvýraznění textu do dokumentu"
"url": "/cs/net/unlocking-annotation-power/add-text-highlight-annotation/"
"weight": 22
---

# Přidat anotaci zvýraznění textu do dokumentu

## Zavedení
oblasti správy dokumentů a spolupráce se GroupDocs.Annotation pro .NET jeví jako robustní řešení, které vývojářům umožňuje bezproblémově integrovat anotace s zvýrazňováním textu do jejich aplikací. Tento tutoriál slouží jako komplexní průvodce přidáváním anotací s zvýrazňováním textu do dokumentů pomocí GroupDocs.Annotation pro .NET. Prostřednictvím podrobných pokynů a podrobného vysvětlení získáte dovednosti v používání možností této výkonné knihovny.
## Předpoklady
Než se ponoříte do implementace anotací s zvýrazňováním textu, ujistěte se, že máte splněny následující předpoklady:
1. Nastavení prostředí: Mějte nakonfigurované vhodné vývojové prostředí pro vývoj v .NET.
2. Instalace GroupDocs.Annotation pro .NET: Stáhněte a nainstalujte GroupDocs.Annotation pro .NET z dodaného [odkaz ke stažení](https://releases.groupdocs.com/annotation/net/).
3. Znalost C#: Základní znalost programovacího jazyka C#.
4. Dokument k anotaci: Připravte si dokument (např. PDF), který chcete anotovat.

## Importovat jmenné prostory
Pro začátek importujte potřebné jmenné prostory do kódu C#, abyste mohli využívat funkce GroupDocs.Annotation pro .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Nyní si rozdělme proces přidávání anotací se zvýrazněním textu do několika kroků:
## Krok 1: Definování výstupní cesty
Zadejte výstupní cestu, kam bude uložen anotovaný dokument:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Inicializace anotátoru
Vytvořte instanci `Annotator` třída s předáním názvu souboru dokumentu jako parametru:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Krok 3: Vytvořte anotaci zvýraznění
Vytvořte instanci `HighlightAnnotation` objekt a nakonfigurujte jeho vlastnosti:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    }
};
```
## Krok 4: Přidání anotace
Přidejte do dokumentu vytvořenou anotaci zvýraznění:
```csharp
annotator.Add(highlight);
```
## Krok 5: Uložení anotovaného dokumentu
Uložte anotovaný dokument do zadané výstupní cesty:
```csharp
annotator.Save(outputPath);
```

## Závěr
Závěrem lze říci, že GroupDocs.Annotation pro .NET nabízí efektivní přístup k začlenění anotací s zvýrazněním textu do dokumentů. Dodržováním kroků popsaných v tomto tutoriálu mohou vývojáři bezproblémově vylepšit spolupráci na dokumentech a produktivitu ve svých aplikacích.
## Často kladené otázky
### Je GroupDocs.Annotation pro .NET kompatibilní se všemi formáty dokumentů?
GroupDocs.Annotation pro .NET podporuje různé formáty dokumentů, včetně PDF, Wordu, Excelu a dalších. Úplný seznam naleznete v dokumentaci.
### Lze anotace přizpůsobit podle specifických požadavků?
Ano, vývojáři mají plnou kontrolu nad vlastnostmi a vzhledem anotací, což umožňuje přizpůsobení dle rozmanitých potřeb.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Annotation pro .NET?
Ano, funkce GroupDocs.Annotation pro .NET si můžete vyzkoušet s bezplatnou zkušební verzí z poskytnuté [odkaz](https://releases.groupdocs.com/).
### Jak mohu získat podporu pro jakékoli problémy nebo dotazy týkající se GroupDocs.Annotation pro .NET?
Pro podporu a pomoc můžete navštívit fórum GroupDocs.Annotation [zde](https://forum.groupdocs.com/c/annotation/10).
### Jaké možnosti licencování jsou k dispozici pro GroupDocs.Annotation pro .NET?
GroupDocs.Annotation pro .NET nabízí různé možnosti licencování, včetně dočasných licencí pro testovací účely a komerčních licencí pro produkční prostředí. Navštivte stránku pro nákup. [zde](https://purchase.groupdocs.com/buy) pro více informací.