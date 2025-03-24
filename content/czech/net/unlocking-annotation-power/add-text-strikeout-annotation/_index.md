---
title: Přidejte do dokumentu poznámku s přeškrtnutím textu
linktitle: Přidejte do dokumentu poznámku s přeškrtnutím textu
second_title: GroupDocs.Annotation .NET API
description: Naučte se přidávat textové přeškrtnuté anotace do dokumentů pomocí GroupDocs.Annotation pro .NET. Zlepšete spolupráci a procesy kontroly dokumentů efektivně.
weight: 26
url: /cs/net/unlocking-annotation-power/add-text-strikeout-annotation/
---
## Úvod
tomto tutoriálu prozkoumáme, jak přidat anotaci s přeškrtnutím textu do dokumentu pomocí GroupDocs.Annotation pro .NET. Tato knihovna poskytuje výkonné nástroje pro anotaci různých typů dokumentů, zlepšuje spolupráci a procesy kontroly dokumentů.
## Předpoklady
Než začneme, ujistěte se, že máte následující předpoklady:
1.  GroupDocs.Annotation for .NET: Nainstalujte knihovnu. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/annotation/net/).
2. Vývojové prostředí: Nastavte vhodné vývojové prostředí pro vývoj .NET.
3. Dokument: Připravte si dokument k anotaci, například soubor PDF.

## Import jmenných prostorů
Nejprve importujte potřebné jmenné prostory pro přístup k funkcím GroupDocs. Anotace:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Nyní si proces přidávání anotace přeškrtnutím textu rozdělíme do několika kroků:
## Krok 1: Definujte výstupní cestu
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Zde definujeme výstupní cestu, kam bude anotovaný dokument uložen.
## Krok 2: Inicializujte anotátor
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Inicializujte objekt Annotator poskytnutím cesty ke vstupnímu dokumentu (v tomto případě soubor PDF).
## Krok 3: Vytvořte přeškrtnutou anotaci
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
## Krok 4: Přidejte anotaci
```csharp
annotator.Add(strikeout);
```
Přidejte do dokumentu vytvořenou přeškrtnutou anotaci.
## Krok 5: Uložte dokument
```csharp
annotator.Save(outputPath);
```
Uložte dokument s poznámkami do zadané výstupní cesty.

## Závěr
V tomto tutoriálu jsme se naučili, jak přidat anotaci s přeškrtnutím textu do dokumentu pomocí GroupDocs.Annotation for .NET. Tato výkonná knihovna umožňuje efektivní anotaci dokumentů, zlepšuje spolupráci a procesy kontroly dokumentů.
## FAQ
### Je GroupDocs.Annotation kompatibilní s různými formáty dokumentů?
Ano, GroupDocs.Annotation podporuje širokou škálu formátů dokumentů včetně PDF, Word, Excel, PowerPoint a dalších.
### Mohu upravit vzhled anotací?
Vlastnosti anotace, jako je barva, neprůhlednost, velikost písma a další, si můžete samozřejmě přizpůsobit podle svých požadavků.
### Poskytuje GroupDocs.Annotation funkce pro spolupráci?
Ano, GroupDocs.Annotation usnadňuje spolupráci tím, že umožňuje uživatelům přidávat komentáře, odpovědi a anotace k dokumentům.
### Je k dispozici bezplatná zkušební verze?
 Ano, můžete využít bezplatnou zkušební verzi od[tady](https://releases.groupdocs.com/).
### Kde mohu získat podporu pro GroupDocs.Annotation?
 Můžete získat podporu od[GroupDocs.Anotační fórum](https://forum.groupdocs.com/c/annotation/10).