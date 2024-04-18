---
title: Přidejte do dokumentu anotaci úpravy textu
linktitle: Přidejte do dokumentu anotaci úpravy textu
second_title: GroupDocs.Annotation .NET API
description: Naučte se přidávat textové redigované anotace do dokumentů PDF pomocí GroupDocs.Annotation for .NET. Chraňte citlivé informace bez námahy.
type: docs
weight: 23
url: /cs/net/unlocking-annotation-power/add-text-redaction-annotation/
---
## Úvod
Přidání textové anotace do dokumentu může být zásadním krokem v bezpečné správě citlivých informací. GroupDocs.Annotation for .NET poskytuje robustní řešení, jak toho dosáhnout. V tomto tutoriálu vás krok za krokem provedeme procesem přidání anotace textové redakce do vašeho dokumentu.
## Předpoklady
Než začneme, ujistěte se, že máte splněny následující předpoklady:
1.  GroupDocs.Annotation for .NET: Ujistěte se, že jste nainstalovali knihovnu GroupDocs.Annotation for .NET. Můžete si jej stáhnout z[webová stránka](https://releases.groupdocs.com/annotation/net/).
2. Vývojové prostředí: Nastavte vývojové prostředí s .NET kompatibilním IDE, jako je Visual Studio.

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
## Krok 1: Definujte výstupní cestu
Definujte výstupní cestu, kam chcete uložit dokument s poznámkami. Ujistěte se, že je přístupný a zapisovatelný.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Inicializujte anotátor
 Inicializujte anotátor se vstupní cestou k dokumentu. Nahradit`"input.pdf"` s cestou k vašemu dokumentu.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Sem bude umístěn kód anotace
}
```
## Krok 3: Vytvořte textovou anotaci
 Vytvořit`TextRedactionAnnotation`objekt s požadovanými vlastnostmi jako např`PageNumber`, `FontColor` , a`Points`. Upravte anotaci podle svých požadavků.
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
## Krok 4: Přidejte anotaci a uložte
Přidejte vytvořenou anotaci do dokumentu pomocí anotátoru a uložte anotovaný dokument do zadané výstupní cesty.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Krok 5: Zkontrolujte výstup
Nakonec potvrďte, že dokument byl úspěšně uložen do zadané výstupní cesty.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
V tomto tutoriálu jsme prošli procesem přidání anotace textové redakce do dokumentu pomocí GroupDocs.Annotation for .NET. Pomocí těchto kroků nyní můžete bezpečně spravovat citlivé informace ve svých dokumentech.
## FAQ
### Mohu přizpůsobit vzhled anotace textové redakce?
Ano, můžete přizpůsobit různé vlastnosti, jako je barva písma, barva výplně a krytí, aby vyhovovaly vašim požadavkům.
### Je před zakoupením k dispozici zkušební verze?
 Ano, máte přístup k bezplatné zkušební verzi z[webová stránka](https://releases.groupdocs.com/).
### Jak mohu získat podporu, pokud narazím na nějaké problémy?
 Podporu můžete získat na fóru komunity GroupDocs.Annotation[tady](https://forum.groupdocs.com/c/annotation/10).
### Potřebuji dočasnou licenci pro testovací účely?
 Ano, můžete získat dočasnou licenci od[nákupní stránku](https://purchase.groupdocs.com/temporary-license/)pro testování.
### Mohu k jednomu dokumentu přidat více anotací?
Rozhodně vám GroupDocs.Annotation umožňuje přidávat různé typy anotací a více instancí do jednoho dokumentu.