---
"description": "Naučte se, jak snadno přidávat do dokumentů vlnité textové anotace pomocí Groupdocs.Annotation pro .NET. Vylepšete spolupráci a procesy kontroly dokumentů."
"linktitle": "Přidat do dokumentu vlnovku textu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Přidat do dokumentu vlnovku textu"
"url": "/cs/net/unlocking-annotation-power/add-text-squiggly-annotation/"
"weight": 25
---

# Přidat do dokumentu vlnovku textu

## Zavedení

Groupdocs.Annotation pro .NET je všestranná knihovna, která umožňuje vývojářům bez námahy integrovat robustní funkce pro anotaci do jejich .NET aplikací. Ať už pracujete s PDF, dokumenty Word nebo jinými oblíbenými formáty souborů, Groupdocs.Annotation poskytuje bezproblémové řešení pro anotaci a vylepšení spolupráce na dokumentech.

## Předpoklady

Než se pustíte do tutoriálu, ujistěte se, že máte splněny následující předpoklady:

## Importovat jmenné prostory

Pro přístup k funkcím poskytovaným souborem Groupdocs.Annotation pro .NET nezapomeňte importovat potřebné jmenné prostory.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Nyní, když máme pokryty předpoklady, pojďme si rozdělit proces přidávání vlnovek textu do několika kroků.

## Krok 1: Definování výstupní cesty

Definujte cestu, kam bude uložen anotovaný dokument.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Krok 2: Inicializace anotátoru

Inicializujte objekt Annotator zadáním vstupní cesty k dokumentu.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Sem se vkládá kód anotace
}
```

## Krok 3: Vytvořte vlnovku

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

## Krok 4: Přidání anotace

Přidejte do dokumentu vytvořenou vlnovku.

```csharp
annotator.Add(squiggly);
```

## Krok 5: Uložení dokumentu

Uložte anotovaný dokument do zadané výstupní cesty.

```csharp
annotator.Save(outputPath);
```

## Krok 6: Zobrazení potvrzení

Zobrazit zprávu potvrzující úspěšné uložení anotovaného dokumentu.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr

Závěrem lze říci, že Groupdocs.Annotation pro .NET poskytuje vývojářům robustní sadu nástrojů pro bezproblémovou integraci funkcí anotací dokumentů do jejich .NET aplikací. Dodržováním tohoto podrobného návodu můžete snadno přidávat textové anotace do svých dokumentů, což vylepší spolupráci a procesy kontroly dokumentů.

## Často kladené otázky

### Otázka: Může soubor Groupdocs.Annotation podporovat anotace v různých formátech souborů?

A: Ano, Groupdocs.Annotation podporuje anotace v široké škále formátů souborů, včetně PDF, dokumentů Word, tabulek Excel a dalších.

### Otázka: Je Groupdocs.Annotation kompatibilní s desktopovými i webovými aplikacemi?

A: Rozhodně! Groupdocs.Annotation lze bez problémů integrovat do desktopových i webových aplikací, což nabízí flexibilitu a všestrannost.

### Otázka: Existují nějaké možnosti licencování pro Groupdocs.Annotation?

A: Ano, Groupdocs.Annotation nabízí flexibilní možnosti licencování přizpůsobené individuálním nebo podnikovým potřebám, včetně dočasných licencí pro zkušební účely.

### Otázka: Lze přizpůsobit anotace vytvořené pomocí Groupdocs.Annotation?

A: Jistě! Groupdocs.Annotation nabízí rozsáhlé možnosti přizpůsobení anotací, což vývojářům umožňuje přizpůsobit anotace jejich specifickým požadavkům.

### Otázka: Nabízí Groupdocs.Annotation podporu a dokumentaci pro vývojáře?

A: Ano! Groupdocs.Annotation poskytuje komplexní dokumentaci a specializovaná fóra podpory, která pomáhají vývojářům efektivně využívat jeho funkce.