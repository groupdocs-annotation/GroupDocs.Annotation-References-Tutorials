---
"description": "Naučte se, jak přidávat anotace s úpravami textu do dokumentů PDF pomocí nástroje GroupDocs.Annotation pro .NET. Chraňte citlivé informace bez námahy."
"linktitle": "Přidání anotace redigování textu do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Přidání anotace redigování textu do dokumentu"
"url": "/cs/net/unlocking-annotation-power/add-text-redaction-annotation/"
type: docs
"weight": 23
---

# Přidání anotace redigování textu do dokumentu

## Zavedení
Přidání anotace s redigováním textu do dokumentu může být klíčovým krokem k bezpečné správě citlivých informací. GroupDocs.Annotation pro .NET poskytuje robustní řešení, jak toho bezproblémově dosáhnout. V tomto tutoriálu vás krok za krokem provedeme procesem přidání anotace s redigováním textu do dokumentu.
## Předpoklady
Než začneme, ujistěte se, že máte splněny následující předpoklady:
1. GroupDocs.Annotation pro .NET: Ujistěte se, že máte nainstalovanou knihovnu GroupDocs.Annotation pro .NET. Můžete si ji stáhnout z [webové stránky](https://releases.groupdocs.com/annotation/net/).
2. Vývojové prostředí: Nastavte vývojové prostředí s IDE kompatibilním s .NET, jako je Visual Studio.

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
## Krok 1: Definování výstupní cesty
Definujte výstupní cestu, kam chcete uložit anotovaný dokument. Ujistěte se, že je přístupná a zapisovatelná.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Inicializace anotátoru
Inicializujte anotátor vstupní cestou k dokumentu. Nahraďte `"input.pdf"` s cestou k vašemu dokumentu.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Sem bude vložen kód anotace
}
```
## Krok 3: Vytvořte anotaci redigování textu
Vytvořte `TextRedactionAnnotation` objekt s požadovanými vlastnostmi, jako například `PageNumber`, `FontColor`a `Points`Upravte si anotaci podle svých požadavků.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## Krok 4: Přidání anotace a uložení
Přidejte vytvořenou anotaci do dokumentu pomocí anotátoru a uložte anotovaný dokument do zadané výstupní cesty.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Krok 5: Zkontrolujte výstup
Nakonec ověřte, že byl dokument úspěšně uložen do zadané výstupní cesty.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
V tomto tutoriálu jsme si prošli procesem přidání anotace s redigováním textu do dokumentu pomocí nástroje GroupDocs.Annotation pro .NET. Díky těmto krokům nyní můžete bezpečně spravovat citlivé informace ve svých dokumentech.
## Často kladené otázky
### Mohu si přizpůsobit vzhled anotace redigovaného textu?
Ano, můžete si přizpůsobit různé vlastnosti, jako je barva písma, barva výplně a neprůhlednost, aby vyhovovaly vašim požadavkům.
### Je k dispozici zkušební verze před zakoupením?
Ano, můžete si zdarma vyzkoušet zkušební verzi z [webové stránky](https://releases.groupdocs.com/).
### Jak mohu získat podporu, pokud narazím na nějaké problémy?
Podporu můžete získat na komunitním fóru GroupDocs.Annotation. [zde](https://forum.groupdocs.com/c/annotation/10).
### Potřebuji pro účely testování dočasnou licenci?
Ano, můžete získat dočasnou licenci od [stránka nákupu](https://purchase.groupdocs.com/temporary-license/) pro testování.
### Mohu do jednoho dokumentu přidat více anotací?
Rozhodně, GroupDocs.Annotation umožňuje přidávat do jednoho dokumentu různé typy anotací a více instancí.