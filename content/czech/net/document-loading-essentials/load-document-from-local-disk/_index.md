---
title: Načíst dokument z místního disku
linktitle: Načíst dokument z místního disku
second_title: GroupDocs.Annotation .NET API
description: Odemkněte sílu anotací dokumentů s GroupDocs.Annotation pro .NET. Bezproblémově integrujte funkce anotací do svých aplikací .NET.
weight: 13
url: /cs/net/document-loading-essentials/load-document-from-local-disk/
---
## Úvod
Odemknutí potenciálu anotací dokumentů nebylo nikdy snazší s GroupDocs.Annotation pro .NET. Tento výkonný nástroj umožňuje vývojářům bezproblémově integrovat robustní anotační funkce do jejich aplikací .NET. V tomto komplexním průvodci vás provedeme procesem využití GroupDocs.Annotation pro .NET k anotaci dokumentů krok za krokem. Ať už jste zkušený vývojář nebo teprve začínáte, tento výukový program vás vybaví znalostmi pro zlepšení spolupráce na dokumentech a zefektivnění vašeho pracovního postupu.
## Předpoklady
Než se ponoříte do anotací dokumentů pomocí GroupDocs.Annotation for .NET, ujistěte se, že máte následující předpoklady:
1. Základní znalost C#: Znalost základů programovacího jazyka C# je nezbytná.
2. Instalace GroupDocs.Annotation pro .NET: Stáhněte a nainstalujte GroupDocs.Annotation pro .NET z[tady](https://releases.groupdocs.com/annotation/net/).
3. Vývojové prostředí: Nastavte vývojové prostředí pomocí sady Visual Studio nebo jakéhokoli kompatibilního IDE.

## Import jmenných prostorů
Chcete-li začít anotovat dokumenty pomocí GroupDocs.Annotation for .NET, importujte do svého projektu potřebné jmenné prostory:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Krok 1: Načtěte dokument z místního disku
Nejprve musíte načíst dokument z místního disku. Použijte následující fragment kódu:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 2: Definujte oblast poznámek
Dále definujte oblast poznámek. V tomto příkladu vytvoříme AreaAnnotation:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Krok 3: Uložte dokument s poznámkami
Po anotování dokumentu jej uložte s poznámkami:
```csharp
    annotator.Save(outputPath);
}
```
## Krok 4: Zobrazte zprávu o úspěchu
Nakonec zobrazte zprávu o úspěchu s výstupní cestou:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
Na závěr, GroupDocs.Annotation for .NET poskytuje robustní řešení pro integraci možností anotací dokumentů do vašich aplikací .NET. Podle tohoto podrobného průvodce můžete snadno anotovat dokumenty a zlepšit spolupráci na svých projektech.
## FAQ
### Mohu GroupDocs.Annotation for .NET vyzkoušet před nákupem?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[tady](https://releases.groupdocs.com/).
### Kde najdu dokumentaci k GroupDocs.Annotation pro .NET?
 Máte přístup k dokumentaci[tady](https://tutorials.groupdocs.com/annotation/net/).
### Jak mohu získat dočasnou licenci pro GroupDocs.Annotation pro .NET?
 Dočasnou licenci můžete získat od[tady](https://purchase.groupdocs.com/temporary-license/).
### Je k dispozici podpora pro GroupDocs.Annotation pro .NET?
 Ano, podporu najdete na fóru GroupDocs[tady](https://forum.groupdocs.com/c/annotation/10).
### Kde si mohu zakoupit GroupDocs.Annotation pro .NET?
 Můžete si zakoupit GroupDocs.Annotation pro .NET[tady](https://purchase.groupdocs.com/buy).