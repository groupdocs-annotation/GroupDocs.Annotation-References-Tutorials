---
title: Přidejte do dokumentu klikatou textovou anotaci
linktitle: Přidejte do dokumentu klikatou textovou anotaci
second_title: GroupDocs.Annotation .NET API
description: Naučte se, jak bez námahy přidávat do dokumentů klikaté textové anotace pomocí Groupdocs.Annotation pro .NET. Zlepšete spolupráci a procesy kontroly dokumentů.
weight: 25
url: /cs/net/unlocking-annotation-power/add-text-squiggly-annotation/
---

# Přidejte do dokumentu klikatou textovou anotaci

## Úvod

Groupdocs.Annotation for .NET je všestranná knihovna, která umožňuje vývojářům bez námahy integrovat robustní možnosti anotací do jejich aplikací .NET. Ať už pracujete s PDF, dokumenty Wordu nebo jinými oblíbenými formáty souborů, Groupdocs.Annotation poskytuje bezproblémové řešení pro přidávání poznámek a zlepšování spolupráce na dokumentech.

## Předpoklady

Než se ponoříte do výukového programu, ujistěte se, že máte splněny následující předpoklady:

## Import jmenných prostorů

Ujistěte se, že jste importovali potřebné jmenné prostory pro přístup k funkcím poskytovaným Groupdocs.Annotation pro .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Nyní, když máme pokryty předpoklady, pojďme si rozdělit proces přidávání klikatých textových anotací do několika kroků.

## Krok 1: Definujte výstupní cestu

Definujte cestu, kam bude dokument s poznámkami uložen.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Krok 2: Inicializujte anotátor

Inicializujte objekt Annotator zadáním cesty vstupního dokumentu.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Zde je kód anotace
}
```

## Krok 3: Vytvořte klikatou anotaci

Vytvořte objekt SquigglyAnnotation a zadejte jeho vlastnosti.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

Přidejte do dokumentu vytvořenou klikatou anotaci.

```csharp
annotator.Add(squiggly);
```

## Krok 5: Uložte dokument

Uložte dokument s poznámkami do zadané výstupní cesty.

```csharp
annotator.Save(outputPath);
```

## Krok 6: Zobrazení potvrzení

Zobrazte zprávu potvrzující úspěšné uložení anotovaného dokumentu.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr

Na závěr, Groupdocs.Annotation for .NET poskytuje vývojářům robustní sadu nástrojů pro bezproblémovou integraci funkcí anotací dokumentů do jejich aplikací .NET. Podle tohoto podrobného průvodce můžete bez námahy přidávat do dokumentů klikaté textové anotace, což zlepšuje spolupráci a procesy kontroly dokumentů.

## FAQ

### Otázka: Může Groupdocs.Annotation podporovat anotaci v různých formátech souborů?

Odpověď: Ano, Groupdocs.Annotation podporuje anotaci v široké škále formátů souborů, včetně PDF, dokumentů Word, listů Excelu a dalších.

### Otázka: Je Groupdocs.Annotation kompatibilní s desktopovými i webovými aplikacemi?

A: Rozhodně! Groupdocs.Annotation lze bez problémů integrovat do desktopových i webových aplikací a nabízí flexibilitu a všestrannost.

### Otázka: Jsou pro Groupdocs.Annotation k dispozici nějaké možnosti licencování?

Odpověď: Ano, Groupdocs.Annotation nabízí flexibilní možnosti licencování přizpůsobené individuálním nebo podnikovým potřebám, včetně dočasných licencí pro zkušební účely.

### Otázka: Lze poznámky vytvořené pomocí Groupdocs.Annotation přizpůsobit?

A: Určitě! Groupdocs.Annotation poskytuje rozsáhlé možnosti přizpůsobení pro anotace, což umožňuje vývojářům přizpůsobit anotace jejich specifickým požadavkům.

### Otázka: Nabízí Groupdocs.Annotation podporu a dokumentaci pro vývojáře?

A: Opravdu! Groupdocs.Annotation poskytuje komplexní dokumentaci a vyhrazená fóra podpory, která vývojářům pomáhají efektivně využívat jeho funkce.