---
title: Přidat textovou podtrženou poznámku do dokumentu
linktitle: Přidat textovou podtrženou poznámku do dokumentu
second_title: GroupDocs.Annotation .NET API
description: Naučte se přidávat textové podtržené anotace do dokumentů pomocí GroupDocs.Annotation for .NET. Vylepšete spolupráci a komunikaci bez námahy.
weight: 27
url: /cs/net/unlocking-annotation-power/add-text-underline-annotation/
---
## Úvod
V tomto tutoriálu si projdeme proces přidávání textové podtržené anotace do dokumentu pomocí GroupDocs.Annotation for .NET. Textové podtržené anotace mohou být užitečné pro zdůraznění konkrétních částí dokumentu, jako jsou důležité pasáže nebo klíčové body.
## Předpoklady
Než začneme, ujistěte se, že máte nainstalované následující předpoklady:
1.  GroupDocs.Annotation pro .NET: Stáhněte a nainstalujte GroupDocs.Annotation pro .NET z[tady](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Ujistěte se, že máte v systému nainstalované rozhraní .NET Framework.

## Import jmenných prostorů
Nejprve importujme potřebné jmenné prostory do našeho projektu:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Nyní si příklad rozdělíme do několika kroků:
## Krok 1: Definujte výstupní cestu
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
V tomto kroku definujeme výstupní cestu, kam se anotovaný dokument uloží.
## Krok 2: Inicializujte anotátor
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Zde inicializujeme instanci`Annotator` třídy poskytnutím cesty vstupního dokumentu.
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
    UnderlineColor = 1422623, // podporuje pouze dokumenty Word a PDF
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
 Tento krok zahrnuje vytvoření`UnderlineAnnotation`objekt s různými vlastnostmi, jako je barva písma, zpráva, neprůhlednost, číslo stránky, barva pozadí, barva podtržení, body a odpovědi.
## Krok 4: Přidejte do dokumentu anotaci
```csharp
annotator.Add(underline);
```
Zde přidáme do dokumentu anotaci podtržení.
## Krok 5: Uložte dokument s poznámkami
```csharp
annotator.Save(outputPath);
```
Nakonec anotovaný dokument uložíme do zadané výstupní cesty.

## Závěr
V tomto tutoriálu jsme se naučili, jak přidat textovou podtrženou anotaci do dokumentu pomocí GroupDocs.Annotation for .NET. Tato výkonná knihovna poskytuje různé možnosti anotací pro zlepšení spolupráce a komunikace na dokumentech.
## FAQ
### Mohu upravit vzhled podtržené anotace?
Ano, vlastnosti, jako je barva, neprůhlednost a poloha, si můžete přizpůsobit podle svých požadavků.
### Je GroupDocs.Annotation kompatibilní s různými formáty dokumentů?
Ano, GroupDocs.Annotation podporuje širokou škálu formátů dokumentů včetně Wordu a PDF.
### Mohu k jednomu dokumentu přidat více anotací?
Rozhodně, GroupDocs.Annotation umožňuje přidat do dokumentu více anotací různých typů.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Annotation?
 Ano, máte přístup k bezplatné zkušební verzi z[tady](https://releases.groupdocs.com/).
### Kde mohu získat podporu pro GroupDocs.Annotation?
 Podporu můžete získat na fóru komunity GroupDocs.Annotation[tady](https://forum.groupdocs.com/c/annotation/10).