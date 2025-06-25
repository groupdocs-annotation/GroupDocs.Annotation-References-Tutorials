---
"description": "Naučte se, jak přidávat anotace s přeškrtnutím textu do dokumentů pomocí nástroje GroupDocs.Annotation pro .NET. Zefektivněte spolupráci a procesy kontroly dokumentů."
"linktitle": "Přidat do dokumentu anotaci přeškrtnutého textu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Přidat do dokumentu anotaci přeškrtnutého textu"
"url": "/cs/net/unlocking-annotation-power/add-text-strikeout-annotation/"
"weight": 26
---

# Přidat do dokumentu anotaci přeškrtnutého textu

## Zavedení
tomto tutoriálu se podíváme na to, jak do dokumentu přidat anotaci s přeškrtnutým textem pomocí knihovny GroupDocs.Annotation pro .NET. Tato knihovna poskytuje výkonné nástroje pro anotaci různých typů dokumentů, což vylepšuje spolupráci a procesy kontroly dokumentů.
## Předpoklady
Než začneme, ujistěte se, že máte následující předpoklady:
1. GroupDocs.Annotation pro .NET: Nainstalujte knihovnu. Můžete si ji stáhnout z [zde](https://releases.groupdocs.com/annotation/net/).
2. Vývojové prostředí: Nastavte vhodné vývojové prostředí pro vývoj v .NET.
3. Dokument: Mějte připravený dokument k anotaci, například soubor PDF.

## Import jmenných prostorů
Nejprve importujte potřebné jmenné prostory pro přístup k funkcím GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Nyní si rozdělme proces přidání anotace s přeškrtnutým textem do několika kroků:
## Krok 1: Definování výstupní cesty
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Zde definujeme výstupní cestu, kam bude uložen anotovaný dokument.
## Krok 2: Inicializace anotátoru
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Inicializujte objekt Annotator zadáním cesty ke vstupnímu dokumentu (v tomto případě PDF soubor).
## Krok 3: Vytvořte anotaci přeškrtnutí
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
Vytvořte objekt StrikeoutAnnotation s požadovanými vlastnostmi, jako je zpráva, neprůhlednost, číslo stránky, barva pozadí, body (souřadnice) a odpovědi.
## Krok 4: Přidání anotace
```csharp
annotator.Add(strikeout);
```
Přidejte do dokumentu vytvořenou anotaci s přeškrtnutím.
## Krok 5: Uložení dokumentu
```csharp
annotator.Save(outputPath);
```
Uložte anotovaný dokument do zadané výstupní cesty.

## Závěr
V tomto tutoriálu jsme se naučili, jak do dokumentu přidat anotaci s přeškrtnutým textem pomocí knihovny GroupDocs.Annotation pro .NET. Tato výkonná knihovna umožňuje efektivní anotaci dokumentů, vylepšuje spolupráci a procesy kontroly dokumentů.
## Často kladené otázky
### Je GroupDocs.Annotation kompatibilní s různými formáty dokumentů?
Ano, GroupDocs.Annotation podporuje širokou škálu formátů dokumentů, včetně PDF, Word, Excel, PowerPoint a dalších.
### Mohu si přizpůsobit vzhled anotací?
Samozřejmě si můžete přizpůsobit vlastnosti anotací, jako je barva, neprůhlednost, velikost písma a další, podle svých požadavků.
### Poskytuje GroupDocs.Annotation funkce pro spolupráci?
Ano, GroupDocs.Annotation usnadňuje spolupráci tím, že umožňuje uživatelům přidávat do dokumentů komentáře, odpovědi a anotace.
### Je k dispozici bezplatná zkušební verze?
Ano, můžete využít bezplatnou zkušební verzi od [zde](https://releases.groupdocs.com/).
### Kde mohu získat podporu pro GroupDocs.Annotation?
Podporu můžete získat od [Fórum GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation/10).