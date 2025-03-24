---
title: Přidání bodové anotace do dokumentu
linktitle: Přidání bodové anotace do dokumentu
second_title: GroupDocs.Annotation .NET API
description: Naučte se, jak přidat bodové anotace do PDF pomocí GroupDocs.Annotation pro .NET. Podrobný průvodce pro bezproblémovou integraci.
weight: 17
url: /cs/net/unlocking-annotation-power/add-point-annotation/
---

# Přidání bodové anotace do dokumentu

## Úvod
GroupDocs.Annotation for .NET je výkonný nástroj, který umožňuje vývojářům přidávat různé typy anotací do dokumentů programově. V tomto tutoriálu se zaměříme na přidání bodové anotace do dokumentu pomocí C#.
## Předpoklady
Než začneme, ujistěte se, že máte následující:
1. Základní znalost programovacího jazyka C#.
2. Visual Studio nainstalované ve vašem systému.
3.  Nainstalovaná knihovna GroupDocs.Annotation pro .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/annotation/net/).

## Import nezbytných jmenných prostorů
Chcete-li začít, musíte do svého projektu C# importovat požadované jmenné prostory:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Definujte výstupní cestu
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
V tomto kroku definujeme výstupní cestu, kam se anotovaný dokument uloží.
## Krok 2: Inicializujte anotátor
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Zde inicializujeme`Annotator` objekt se vstupním dokumentem ("vstup.pdf").
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
 V tomto kroku vytvoříme a`PointAnnotation` objekt a zadejte jeho vlastnosti, jako je pozice, zpráva, číslo stránky a odpovědi.
## Krok 4: Přidejte anotaci
```csharp
annotator.Add(point);
```
Zde do dokumentu přidáme vytvořenou bodovou anotaci.
## Krok 5: Uložte dokument
```csharp
annotator.Save(outputPath);
```
Nakonec anotovaný dokument uložíme do zadané výstupní cesty.

## Závěr
V tomto tutoriálu jsme se naučili, jak přidat bodovou anotaci do dokumentu pomocí GroupDocs.Annotation pro .NET. Pomocí této výkonné knihovny můžete vylepšit své aplikace pro správu dokumentů začleněním funkcí anotací.
## FAQ
### Je GroupDocs.Annotation for .NET kompatibilní se všemi formáty dokumentů?
Ano, GroupDocs.Annotation for .NET podporuje širokou škálu formátů dokumentů včetně PDF, Microsoft Word, Excel, PowerPoint a dalších.
### Mohu upravit vzhled anotací?
Absolutně! GroupDocs.Annotation for .NET poskytuje rozsáhlé možnosti pro přizpůsobení vzhledu anotací tak, aby vyhovovaly potřebám vaší aplikace.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Annotation pro .NET?
 Ano, můžete využít bezplatnou zkušební verzi od[tady](https://releases.groupdocs.com/).
### Jak mohu získat podporu pro jakékoli problémy nebo dotazy související s GroupDocs.Annotation pro .NET?
 Podporu můžete získat na fóru GroupDocs.Annotation[tady](https://forum.groupdocs.com/c/annotation/10).
### Mohu získat dočasnou licenci pro testovací účely?
 Ano, můžete získat dočasnou licenci od[tady](https://purchase.groupdocs.com/temporary-license/).