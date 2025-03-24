---
title: Přidejte do dokumentu anotaci se zvýrazněním textu
linktitle: Přidejte do dokumentu anotaci se zvýrazněním textu
second_title: GroupDocs.Annotation .NET API
description: Zjistěte, jak přidat poznámky ke zvýraznění textu do dokumentů pomocí GroupDocs.Annotation for .NET. Vylepšete spolupráci a produktivitu s tímto komplexním řešením.
weight: 22
url: /cs/net/unlocking-annotation-power/add-text-highlight-annotation/
---

# Přidejte do dokumentu anotaci se zvýrazněním textu

## Úvod
oblasti správy dokumentů a spolupráce se GroupDocs.Annotation for .NET ukazuje jako robustní řešení, které umožňuje vývojářům bezproblémově integrovat poznámky se zvýrazněním textu do svých aplikací. Tento výukový program slouží jako komplexní průvodce přidáváním textových zvýrazněných anotací do dokumentů pomocí GroupDocs.Annotation pro .NET. Prostřednictvím podrobných pokynů a podrobných vysvětlení získáte odbornost ve využívání schopností této výkonné knihovny.
## Předpoklady
Než se ponoříte do implementace anotací zvýraznění textu, ujistěte se, že máte splněny následující předpoklady:
1. Nastavení prostředí: Mějte nakonfigurováno vhodné vývojové prostředí pro vývoj .NET.
2.  Instalace GroupDocs.Annotation pro .NET: Stáhněte a nainstalujte GroupDocs.Annotation pro .NET z poskytnutého[odkaz ke stažení](https://releases.groupdocs.com/annotation/net/).
3. Znalost C#: Základní znalost programovacího jazyka C#.
4. Dokument k anotaci: Připravte dokument (např. PDF), který chcete anotovat.

## Import jmenných prostorů
Chcete-li začít, importujte potřebné jmenné prostory do kódu C#, abyste mohli využívat funkce GroupDocs.Annotation pro .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Nyní si proces přidávání anotací se zvýrazněním textu rozdělíme do několika kroků:
## Krok 1: Definujte výstupní cestu
Zadejte výstupní cestu, kam bude dokument s poznámkami uložen:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Inicializujte anotátor
 Vytvořte instanci souboru`Annotator` třídy, předáním názvu souboru dokumentu jako parametru:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Krok 3: Vytvořte anotaci zvýraznění
 Instantovat a`HighlightAnnotation` objekt a nakonfigurujte jeho vlastnosti:
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
## Krok 4: Přidejte anotaci
Přidejte do dokumentu vytvořenou anotaci zvýraznění:
```csharp
annotator.Add(highlight);
```
## Krok 5: Uložte dokument s poznámkami
Uložte anotovaný dokument do zadané výstupní cesty:
```csharp
annotator.Save(outputPath);
```

## Závěr
Na závěr, GroupDocs.Annotation for .NET nabízí zjednodušený přístup k začlenění anotací se zvýrazněním textu do dokumentů. Dodržením kroků uvedených v tomto kurzu mohou vývojáři bezproblémově zlepšit spolupráci na dokumentech a produktivitu v rámci svých aplikací.
## FAQ
### Je GroupDocs.Annotation for .NET kompatibilní se všemi formáty dokumentů?
GroupDocs.Annotation for .NET podporuje různé formáty dokumentů, včetně PDF, Wordu, Excelu a dalších. Úplný seznam naleznete v dokumentaci.
### Lze poznámky upravit podle konkrétních požadavků?
Ano, vývojáři mají plnou kontrolu nad vlastnostmi a vzhledem anotací, což umožňuje přizpůsobení různým potřebám.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Annotation pro .NET?
 Ano, můžete prozkoumat funkce GroupDocs.Annotation pro .NET přístupem k bezplatné zkušební verzi z poskytnutého[odkaz](https://releases.groupdocs.com/).
### Jak mohu získat podporu pro jakékoli problémy nebo dotazy související s GroupDocs.Annotation pro .NET?
 Pro podporu a pomoc můžete navštívit fórum GroupDocs.Annotation[tady](https://forum.groupdocs.com/c/annotation/10).
### Jaké možnosti licencování jsou k dispozici pro GroupDocs.Annotation pro .NET?
 GroupDocs.Annotation for .NET nabízí různé možnosti licencování, včetně dočasných licencí pro testovací účely a komerčních licencí pro produkční prostředí. Navštivte stránku nákupu[tady](https://purchase.groupdocs.com/buy) Více podrobností.