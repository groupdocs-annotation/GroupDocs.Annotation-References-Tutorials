---
"description": "Naučte se, jak přidávat anotace vzdálenosti do dokumentů pomocí GroupDocs.Annotation pro .NET. Vylepšete spolupráci a komunikaci bez námahy."
"linktitle": "Přidat anotaci vzdálenosti do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Přidat anotaci vzdálenosti do dokumentu"
"url": "/cs/net/unlocking-annotation-power/add-distance-annotation/"
type: docs
"weight": 12
---

# Přidat anotaci vzdálenosti do dokumentu

## Zavedení
V tomto tutoriálu se naučíte, jak přidat anotaci vzdálenosti do dokumentu pomocí nástroje GroupDocs.Annotation pro .NET. Postupujte podle těchto kroků:
## Předpoklady

Než budete pokračovat, ujistěte se, že máte splněny následující předpoklady:

- Knihovna GroupDocs.Annotation pro .NET: Stáhněte a nainstalujte knihovnu GroupDocs.Annotation pro .NET z [tento odkaz](https://releases.groupdocs.com/annotation/net/).
- Dokument k anotaci: Připravte dokument (např. PDF), do kterého chcete přidat anotaci vzdálenosti.
- Vývojové prostředí: Nastavte si vývojové prostředí pomocí Visual Studia nebo jiného IDE dle vašeho výběru.

## Importovat jmenné prostory

Než začnete, ujistěte se, že jste do kódu zahrnuli potřebné jmenné prostory. Tyto jmenné prostory jsou nezbytné pro přístup k požadovaným třídám a metodám.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Krok 1: Inicializace anotátoru

Začněte inicializací `Annotator` objekt s cestou k dokumentu, který chcete anotovat.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Sem bude vložen kód anotace
}
```

## Krok 2: Vytvořte anotaci vzdálenosti

Nyní vytvořte `DistanceAnnotation` objekt a nakonfigurovat jeho vlastnosti, jako jsou rozměry rámečku, zpráva, neprůhlednost, barva pera atd.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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

## Krok 3: Přidání anotace

Přidejte vytvořenou anotaci vzdálenosti do dokumentu pomocí `Add` metoda objektu anotátoru.

```csharp
annotator.Add(distance);
```

## Krok 4: Uložení dokumentu

Uložte anotovaný dokument na požadované místo v systému.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Krok 5: Zobrazení potvrzení

Nakonec zobrazte zprávu potvrzující úspěšné uložení anotovaného dokumentu.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr

Přidávání anotací vzdálenosti do dokumentů pomocí GroupDocs.Annotation pro .NET je jednoduchý proces. Dodržováním kroků popsaných v tomto tutoriálu můžete své dokumenty vylepšit cennými anotacemi, což usnadní spolupráci a komunikaci.

## Často kladené otázky

### Otázka: Mohu si přizpůsobit vzhled anotace vzdálenosti?

A: Ano, můžete si přizpůsobit různé vlastnosti, jako je barva, krytí, styl čáry atd., aby vyhovovaly vašim požadavkům.

### Otázka: Podporuje GroupDocs.Annotation anotace u různých typů dokumentů?

A: Ano, GroupDocs.Annotation podporuje anotace v široké škále formátů dokumentů, včetně PDF, Wordu, Excelu, PowerPointu a dalších.

### Otázka: Je k dispozici bezplatná zkušební verze GroupDocs.Annotation?

A: Ano, můžete si zdarma vyzkoušet GroupDocs.Annotation z [tento odkaz](https://releases.groupdocs.com/).

### Otázka: Kde najdu dokumentaci k souboru GroupDocs.Annotation pro .NET?

A: Můžete se podívat na dostupnou podrobnou dokumentaci [zde](https://tutorials.groupdocs.com/annotation/net/).

### Otázka: Jak mohu získat podporu nebo pomoc s GroupDocs.Annotation?

A: Podporu a pomoc můžete vyhledat na komunitním fóru GroupDocs.Annotation. [zde](https://forum.groupdocs.com/c/annotation/10).