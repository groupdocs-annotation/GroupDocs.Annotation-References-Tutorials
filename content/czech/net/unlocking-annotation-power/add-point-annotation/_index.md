---
"description": "Naučte se, jak přidat bodové anotace do PDF souborů pomocí GroupDocs.Annotation pro .NET. Podrobný návod pro bezproblémovou integraci."
"linktitle": "Přidat bodovou anotaci do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Přidat bodovou anotaci do dokumentu"
"url": "/cs/net/unlocking-annotation-power/add-point-annotation/"
"weight": 17
---

# Přidat bodovou anotaci do dokumentu

## Zavedení
GroupDocs.Annotation pro .NET je výkonný nástroj, který umožňuje vývojářům programově přidávat do dokumentů různé typy anotací. V tomto tutoriálu se zaměříme na přidání bodové anotace do dokumentu pomocí C#.
## Předpoklady
Než začneme, ujistěte se, že máte následující:
1. Základní znalost programovacího jazyka C#.
2. Visual Studio nainstalované ve vašem systému.
3. Je nainstalována knihovna GroupDocs.Annotation pro .NET. Můžete si ji stáhnout z [zde](https://releases.groupdocs.com/annotation/net/).

## Import nezbytných jmenných prostorů
Chcete-li začít, musíte importovat požadované jmenné prostory do svého projektu C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Definování výstupní cesty
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
V tomto kroku definujeme výstupní cestu, kam bude uložen anotovaný dokument.
## Krok 2: Inicializace anotátoru
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Zde inicializujeme `Annotator` objekt se vstupním dokumentem („input.pdf“).
## Krok 3: Vytvořte bodovou anotaci
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
V tomto kroku vytvoříme `PointAnnotation` objekt a specifikovat jeho vlastnosti, jako je pozice, zpráva, číslo stránky a odpovědi.
## Krok 4: Přidání anotace
```csharp
annotator.Add(point);
```
Zde přidáme do dokumentu vytvořenou bodovou anotaci.
## Krok 5: Uložení dokumentu
```csharp
annotator.Save(outputPath);
```
Nakonec uložíme anotovaný dokument do zadané výstupní cesty.

## Závěr
V tomto tutoriálu jsme se naučili, jak přidat bodovou anotaci do dokumentu pomocí GroupDocs.Annotation pro .NET. S touto výkonnou knihovnou můžete vylepšit své aplikace pro správu dokumentů začleněním funkcí anotací.
## Často kladené otázky
### Je GroupDocs.Annotation pro .NET kompatibilní se všemi formáty dokumentů?
Ano, GroupDocs.Annotation pro .NET podporuje širokou škálu formátů dokumentů, včetně PDF, Microsoft Word, Excel, PowerPoint a dalších.
### Mohu si přizpůsobit vzhled anotací?
Rozhodně! GroupDocs.Annotation pro .NET nabízí rozsáhlé možnosti pro přizpůsobení vzhledu anotací potřebám vaší aplikace.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Annotation pro .NET?
Ano, můžete využít bezplatnou zkušební verzi od [zde](https://releases.groupdocs.com/).
### Jak mohu získat podporu pro jakékoli problémy nebo dotazy týkající se GroupDocs.Annotation pro .NET?
Podporu můžete získat na fóru GroupDocs.Annotation. [zde](https://forum.groupdocs.com/c/annotation/10).
### Mohu získat dočasnou licenci pro účely testování?
Ano, můžete získat dočasnou licenci od [zde](https://purchase.groupdocs.com/temporary-license/).