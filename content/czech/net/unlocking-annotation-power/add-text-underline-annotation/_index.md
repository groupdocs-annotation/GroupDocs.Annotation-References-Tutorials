---
"description": "Naučte se, jak přidávat podtržené textové poznámky do dokumentů pomocí GroupDocs.Annotation pro .NET. Vylepšete spolupráci a komunikaci bez námahy."
"linktitle": "Přidat do dokumentu podtržený text"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Přidat do dokumentu podtržený text"
"url": "/cs/net/unlocking-annotation-power/add-text-underline-annotation/"
type: docs
"weight": 27
---

# Přidat do dokumentu podtržený text

## Zavedení
tomto tutoriálu si projdeme procesem přidání podtržené textové anotace do dokumentu pomocí nástroje GroupDocs.Annotation pro .NET. Podtržené textové anotace mohou být užitečné pro zdůraznění konkrétních částí dokumentu, jako jsou důležité pasáže nebo klíčové body.
## Předpoklady
Než začneme, ujistěte se, že máte nainstalovány následující předpoklady:
1. GroupDocs.Annotation pro .NET: Stáhněte a nainstalujte GroupDocs.Annotation pro .NET z [zde](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Ujistěte se, že máte v systému nainstalovaný .NET Framework.

## Import jmenných prostorů
Nejprve si do našeho projektu importujme potřebné jmenné prostory:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Nyní si příklad rozdělme do několika kroků:
## Krok 1: Definování výstupní cesty
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
V tomto kroku definujeme výstupní cestu, kam bude uložen anotovaný dokument.
## Krok 2: Inicializace anotátoru
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Zde inicializujeme instanci třídy `Annotator` třídu zadáním cesty ke vstupnímu dokumentu.
## Krok 3: Vytvořte podtrženou anotaci
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // funguje pouze s podporou dokumentů Word a PDF
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
Tento krok zahrnuje vytvoření `UnderlineAnnotation` objekt s různými vlastnostmi, jako je barva písma, zpráva, neprůhlednost, číslo stránky, barva pozadí, barva podtržení, body a odpovědi.
## Krok 4: Přidání anotace do dokumentu
```csharp
annotator.Add(underline);
```
Zde do dokumentu přidáme podtrženou anotaci.
## Krok 5: Uložení anotovaného dokumentu
```csharp
annotator.Save(outputPath);
```
Nakonec uložíme anotovaný dokument do zadané výstupní cesty.

## Závěr
V tomto tutoriálu jsme se naučili, jak přidat do dokumentu anotaci s podtržením textu pomocí knihovny GroupDocs.Annotation pro .NET. Tato výkonná knihovna nabízí různé možnosti anotací pro zlepšení spolupráce a komunikace v oblasti dokumentů.
## Často kladené otázky
### Mohu si přizpůsobit vzhled podtržené poznámky?
Ano, vlastnosti, jako je barva, krytí a poloha, si můžete přizpůsobit podle svých požadavků.
### Je GroupDocs.Annotation kompatibilní s různými formáty dokumentů?
Ano, GroupDocs.Annotation podporuje širokou škálu formátů dokumentů včetně Wordu a PDF.
### Mohu do jednoho dokumentu přidat více anotací?
Rozhodně, GroupDocs.Annotation umožňuje přidat do dokumentu více anotací různých typů.
### Je k dispozici bezplatná zkušební verze GroupDocs.Annotation?
Ano, k bezplatné zkušební verzi máte přístup z [zde](https://releases.groupdocs.com/).
### Kde mohu získat podporu pro GroupDocs.Annotation?
Podporu můžete získat na komunitním fóru GroupDocs.Annotation. [zde](https://forum.groupdocs.com/c/annotation/10).