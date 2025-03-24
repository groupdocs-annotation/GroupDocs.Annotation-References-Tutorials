---
title: Přidejte do dokumentu anotaci vodoznaku
linktitle: Přidejte do dokumentu anotaci vodoznaku
second_title: GroupDocs.Annotation .NET API
description: Naučte se, jak snadno přidávat anotace vodoznaku do vašich dokumentů pomocí GroupDocs.Annotation pro .NET. Zvyšte srozumitelnost a bezpečnost dokumentů.
weight: 28
url: /cs/net/unlocking-annotation-power/add-watermark-annotation/
---
## Úvod
V tomto tutoriálu si projdeme proces přidání anotace vodoznaku do dokumentu pomocí GroupDocs.Annotation for .NET. Anotace vodoznaku jsou užitečné pro označení stavu dokumentu, jeho označení jako důvěrného nebo přidání jakýchkoli dalších relevantních informací.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1.  GroupDocs.Annotation for .NET: Můžete si ji stáhnout z[tady](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Ujistěte se, že máte v systému nainstalované Visual Studio.
3. Základní znalost C#: Pro pochopení a implementaci příkladů kódu je nezbytná znalost programovacího jazyka C#.

## Import jmenných prostorů

Než začneme kódovat, importujme potřebné jmenné prostory:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Nyní si rozdělme proces přidávání anotace vodoznaku do několika kroků:

## Krok 1: Definujte výstupní cestu

 Nejprve musíme definovat výstupní cestu, kam se anotovaný dokument uloží. Použijeme`Path` třídy od`System.IO` jmenný prostor pro spojení cesty výstupního adresáře s názvem souboru.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Krok 2: Inicializujte anotátor

Dále inicializujeme anotátor poskytnutím cesty ke vstupnímu dokumentu. To nám umožní přidat do dokumentu anotace.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Sem bude umístěn kód anotace
}
```

## Krok 3: Vytvořte anotaci vodoznaku

Nyní vytvoříme objekt anotace vodoznaku s požadovanými vlastnostmi, jako je úhel, poloha, text, barva písma, neprůhlednost atd.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## Krok 4: Přidejte anotaci vodoznaku

 Nyní přidáme anotaci vodoznaku do dokumentu pomocí`Add` metoda objektu anotátor.

```csharp
annotator.Add(watermark);
```

## Krok 5: Uložte dokument

Nakonec anotovaný dokument uložíme do zadané výstupní cesty.

```csharp
annotator.Save(outputPath);
```

## Závěr

V tomto tutoriálu jsme se naučili, jak přidat anotaci vodoznaku do dokumentu pomocí GroupDocs.Annotation for .NET. Anotace vodoznaku jsou cenným nástrojem pro označování dokumentů relevantními informacemi nebo indikace jejich stavu.

## FAQ

### Otázka: Mohu upravit vzhled anotace vodoznaku?

Odpověď: Ano, můžete přizpůsobit různé vlastnosti, jako je text, velikost písma, barva, neprůhlednost, poloha atd., abyste přizpůsobili vodoznak podle svých požadavků.

### Otázka: Je GroupDocs.Annotation for .NET kompatibilní s různými formáty dokumentů?

Odpověď: Ano, GroupDocs.Annotation podporuje širokou škálu formátů dokumentů včetně PDF, Microsoft Word, Excel, PowerPoint a obrazových formátů.

### Otázka: Mohu k jednomu dokumentu přidat více anotací?

Odpověď: Rozhodně, GroupDocs.Annotation umožňuje přidat více anotací různých typů do jednoho dokumentu, což umožňuje komplexní označení dokumentu.

### Otázka: Poskytuje GroupDocs.Annotation podporu pro společné anotace?

Odpověď: Ano, GroupDocs.Annotation usnadňuje společné anotace tím, že umožňuje uživatelům přidávat komentáře, odpovědi a anotace, čímž podporuje efektivní spolupráci mezi členy týmu.

### Otázka: Je k dispozici zkušební verze pro GroupDocs.Annotation pro .NET?

 Odpověď: Ano, můžete si stáhnout bezplatnou zkušební verzi z[tady](https://releases.groupdocs.com/).