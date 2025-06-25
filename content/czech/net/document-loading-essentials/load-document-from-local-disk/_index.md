---
"description": "Odemkněte sílu anotací dokumentů s GroupDocs.Annotation pro .NET. Bezproblémově integrujte funkce anotací do svých .NET aplikací."
"linktitle": "Načíst dokument z lokálního disku"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Načíst dokument z lokálního disku"
"url": "/cs/net/document-loading-essentials/load-document-from-local-disk/"
"weight": 13
---

# Načíst dokument z lokálního disku

## Zavedení
Využití potenciálu anotací dokumentů s nástrojem GroupDocs.Annotation pro .NET nebylo nikdy snazší. Tento výkonný nástroj umožňuje vývojářům bezproblémově integrovat robustní funkce anotací do svých .NET aplikací. V této komplexní příručce vás krok za krokem provedeme procesem využití GroupDocs.Annotation pro .NET k anotaci dokumentů. Ať už jste zkušený vývojář, nebo teprve začínáte, tento tutoriál vás vybaví znalostmi pro zlepšení spolupráce na dokumentech a zefektivnění vašeho pracovního postupu.
## Předpoklady
Než se pustíte do anotace dokumentů pomocí GroupDocs.Annotation pro .NET, ujistěte se, že máte následující předpoklady:
1. Základní znalost C#: Znalost základů programovacího jazyka C# je nezbytná.
2. Instalace GroupDocs.Annotation pro .NET: Stáhněte a nainstalujte GroupDocs.Annotation pro .NET z [zde](https://releases.groupdocs.com/annotation/net/).
3. Vývojové prostředí: Nastavte vývojové prostředí pomocí Visual Studia nebo jakéhokoli kompatibilního IDE.

## Importovat jmenné prostory
Chcete-li začít s anotací dokumentů pomocí GroupDocs.Annotation pro .NET, importujte do projektu potřebné jmenné prostory:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Krok 1: Načtení dokumentu z lokálního disku
Nejprve je třeba načíst dokument z lokálního disku. Použijte následující úryvek kódu:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 2: Definování oblasti anotací
Dále definujte oblast anotace. V tomto příkladu vytvoříme anotaci oblasti (AreaAnnotation):
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Krok 3: Uložení dokumentu s anotacemi
Po anotaci dokumentu jej uložte s anotacemi:
```csharp
    annotator.Save(outputPath);
}
```
## Krok 4: Zobrazení zprávy o úspěchu
Nakonec zobrazte zprávu o úspěchu s výstupní cestou:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
Závěrem lze říci, že GroupDocs.Annotation pro .NET poskytuje robustní řešení pro integraci funkcí anotace dokumentů do vašich .NET aplikací. Dodržováním tohoto podrobného návodu můžete bez námahy anotovat dokumenty a vylepšit spolupráci na vašich projektech.
## Často kladené otázky
### Mohu si před zakoupením vyzkoušet GroupDocs.Annotation pro .NET?
Ano, můžete si stáhnout bezplatnou zkušební verzi z [zde](https://releases.groupdocs.com/).
### Kde najdu dokumentaci k GroupDocs.Annotation pro .NET?
Dokumentaci si můžete prohlédnout [zde](https://tutorials.groupdocs.com/annotation/net/).
### Jak mohu získat dočasnou licenci pro GroupDocs.Annotation pro .NET?
Dočasné povolení můžete získat od [zde](https://purchase.groupdocs.com/temporary-license/).
### Je k dispozici podpora pro GroupDocs.Annotation pro .NET?
Ano, podporu najdete na fóru GroupDocs. [zde](https://forum.groupdocs.com/c/annotation/10).
### Kde si mohu zakoupit GroupDocs.Annotation pro .NET?
Můžete si zakoupit GroupDocs.Annotation pro .NET [zde](https://purchase.groupdocs.com/buy).