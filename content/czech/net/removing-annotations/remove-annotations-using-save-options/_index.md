---
title: Odebrat anotace pomocí možností uložení v .NET
linktitle: Odebrat anotace pomocí možností uložení v .NET
second_title: GroupDocs.Annotation .NET API
description: Přečtěte si, jak odstranit anotace z PDF a dalších dokumentů v .NET pomocí GroupDocs.Annotation. Podrobný průvodce s příklady kódu.
weight: 14
url: /cs/net/removing-annotations/remove-annotations-using-save-options/
---
## Úvod

GroupDocs.Annotation for .NET je výkonný nástroj, který umožňuje vývojářům snadno přidávat funkce anotací do jejich aplikací .NET. Ať už pracujete na systému správy dokumentů, platformě pro spolupráci nebo jakékoli jiné aplikaci, která zahrnuje zpracování dokumentů, GroupDocs.Annotation poskytuje komplexní sadu funkcí pro bezproblémové anotování PDF a dalších formátů dokumentů.

## Předpoklady

Než se ponoříte do světa anotací dokumentů pomocí GroupDocs.Annotation pro .NET, ujistěte se, že máte splněny následující předpoklady:

### 1. Nainstalujte GroupDocs.Annotation for .NET

 Začněte stažením a instalací GroupDocs.Annotation for .NET. Nejnovější verzi si můžete stáhnout z[download page](https://releases.groupdocs.com/annotation/net/).

## Import jmenných prostorů

Chcete-li začít používat GroupDocs.Annotation ve svém projektu .NET, musíte importovat potřebné jmenné prostory. Zde jsou jmenné prostory, které běžně používáte:

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


Nyní si projdeme proces odstraňování anotací z dokumentu pomocí funkce Save Options v .NET:

## Krok 1: Definujte výstupní cestu

Nejprve definujte výstupní cestu, kam bude dokument s odstraněnými anotacemi uložen. Můžete použít`Path.Combine` metoda pro kombinaci cesty k adresáři s názvem výstupního souboru.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Krok 2: Inicializujte anotátor

 Dále inicializujte instanci souboru`Annotator` třídy poskytnutím cesty k dokumentu obsahujícímu anotace.

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    // Sem bude umístěn kód pro odstranění anotace
}
```

## Krok 3: Uložte dokument s odstraněním anotace

 Nyní použijte`Save` metoda`Annotator` třída spolu s`SaveOptions` pro uložení dokumentu s odstraněnými anotacemi. V`SaveOptions` , nastav`AnnotationTypes` majetek do`AnnotationType.None` k odstranění všech poznámek.

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## Krok 4: Zobrazte zprávu o úspěchu

Nakonec zobrazte zprávu o úspěchu, která označuje, že dokument byl úspěšně uložen s odstraněnými anotacemi.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr

Na závěr, GroupDocs.Annotation for .NET zjednodušuje proces odstraňování anotací z dokumentů. Podle výše popsaného podrobného průvodce mohou vývojáři bezproblémově integrovat funkci odstraňování anotací do svých aplikací .NET.

## FAQ

### Otázka: Může GroupDocs.Annotation odstranit anotace z jiných formátů dokumentů kromě PDF?

Odpověď: GroupDocs.Annotation podporuje různé formáty dokumentů, včetně PDF, Wordu, Excelu a PowerPointu, což vám umožňuje odstraňovat anotace z celé řady dokumentů.

### Otázka: Lze GroupDocs.Annotation snadno integrovat do stávajících projektů .NET?

Odpověď: Ano, GroupDocs.Annotation poskytuje jednoduché API a komplexní dokumentaci, což vývojářům usnadňuje integraci funkcí anotací do jejich aplikací .NET.

### Otázka: Podporuje GroupDocs.Annotation selektivní odstranění anotací?

Odpověď: Ano, GroupDocs.Annotation umožňuje vývojářům určit, které typy anotací mají odstranit, což jim poskytuje flexibilitu při správě anotací v jejich dokumentech.

### Otázka: Mohu GroupDocs.Annotation před nákupem vyzkoušet zdarma?

 Odpověď: Ano, bezplatnou zkušební verzi GroupDocs.Annotation si můžete stáhnout z webu[stránka vydání](https://releases.groupdocs.com/) prozkoumat jeho vlastnosti před rozhodnutím o koupi.

### Otázka: Kde mohu získat podporu pro GroupDocs.Annotation?

 Odpověď: Pro technickou pomoc a podporu komunity můžete navštívit stránku[GroupDocs.Anotační fórum](https://forum.groupdocs.com/c/annotation/10).