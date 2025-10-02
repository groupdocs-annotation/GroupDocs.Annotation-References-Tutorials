---
"description": "Naučte se, jak snadno přidávat vodoznaky do dokumentů pomocí nástroje GroupDocs.Annotation pro .NET. Zlepšete přehlednost a zabezpečení dokumentů."
"linktitle": "Přidání anotace vodoznaku do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Přidání anotace vodoznaku do dokumentu"
"url": "/cs/net/unlocking-annotation-power/add-watermark-annotation/"
type: docs
"weight": 28
---

# Přidání anotace vodoznaku do dokumentu

## Zavedení
tomto tutoriálu si projdeme procesem přidání anotace vodoznaku do dokumentu pomocí GroupDocs.Annotation pro .NET. Anotace vodoznaku jsou užitečné pro označení stavu dokumentu, jeho označení jako důvěrného nebo přidání dalších relevantních informací.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1. GroupDocs.Annotation pro .NET: Můžete si ji stáhnout z [zde](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Ujistěte se, že máte v systému nainstalované Visual Studio.
3. Základní znalost jazyka C#: Znalost programovacího jazyka C# je nezbytná pro pochopení a implementaci příkladů kódu.

## Importovat jmenné prostory

Než začneme s kódováním, importujme potřebné jmenné prostory:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Nyní si rozdělme proces přidání anotace vodoznaku do několika kroků:

## Krok 1: Definování výstupní cesty

Nejprve musíme definovat výstupní cestu, kam bude uložen anotovaný dokument. Použijeme `Path` třída z `System.IO` jmenný prostor pro kombinování výstupní cesty k adresáři s názvem souboru.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Krok 2: Inicializace anotátoru

Dále inicializujeme anotátor zadáním cesty ke vstupnímu dokumentu. To nám umožní do dokumentu přidávat anotace.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Sem bude vložen kód anotace
}
```

## Krok 3: Vytvořte anotaci vodoznaku

Nyní si vytvořme objekt anotace vodoznaku s požadovanými vlastnostmi, jako je úhel, pozice, text, barva písma, neprůhlednost atd.

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

## Krok 4: Přidání anotace vodoznaku

Nyní přidáme do dokumentu anotaci vodoznaku pomocí `Add` metoda objektu anotátoru.

```csharp
annotator.Add(watermark);
```

## Krok 5: Uložení dokumentu

Nakonec uložíme anotovaný dokument do zadané výstupní cesty.

```csharp
annotator.Save(outputPath);
```

## Závěr

V tomto tutoriálu jsme se naučili, jak přidat anotaci vodoznaku do dokumentu pomocí GroupDocs.Annotation pro .NET. Anotace vodoznaku jsou cenným nástrojem pro označení dokumentů relevantními informacemi nebo pro indikaci jejich stavu.

## Často kladené otázky

### Otázka: Mohu si přizpůsobit vzhled anotace vodoznaku?

A: Ano, můžete si upravit různé vlastnosti, jako je text, velikost písma, barva, krytí, umístění atd., abyste vodoznak přizpůsobili svým požadavkům.

### Otázka: Je GroupDocs.Annotation pro .NET kompatibilní s různými formáty dokumentů?

A: Ano, GroupDocs.Annotation podporuje širokou škálu formátů dokumentů, včetně PDF, Microsoft Word, Excel, PowerPoint a obrazových formátů.

### Otázka: Mohu do jednoho dokumentu přidat více anotací?

A: Rozhodně, GroupDocs.Annotation umožňuje přidat do jednoho dokumentu více anotací různých typů, což umožňuje komplexní značkování dokumentů.

### Otázka: Poskytuje GroupDocs.Annotation podporu pro kolaborativní anotace?

A: Ano, GroupDocs.Annotation usnadňuje spolupráci při vytváření anotací tím, že umožňuje uživatelům přidávat komentáře, odpovědi a poznámky, což podporuje efektivní spolupráci mezi členy týmu.

### Otázka: Je k dispozici zkušební verze pro GroupDocs.Annotation pro .NET?

A: Ano, můžete si stáhnout bezplatnou zkušební verzi z [zde](https://releases.groupdocs.com/).