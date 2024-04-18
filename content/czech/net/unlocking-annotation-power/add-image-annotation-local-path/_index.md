---
title: Přidat k dokumentu poznámku obrázku (místní cesta)
linktitle: Přidat k dokumentu poznámku obrázku (místní cesta)
second_title: GroupDocs.Annotation .NET API
description: Naučte se přidávat popisky obrázků do dokumentů pomocí GroupDocs.Annotation for .NET. Snadno vylepšete možnosti zpracování dokumentů.
type: docs
weight: 14
url: /cs/net/unlocking-annotation-power/add-image-annotation-local-path/
---
## Úvod
GroupDocs.Annotation for .NET je výkonná knihovna, která umožňuje vývojářům přidávat do dokumentů různé typy anotací programově. V tomto tutoriálu se naučíme, jak přidat do dokumentu anotace obrázků pomocí místní cesty.
## Předpoklady
Než začneme, ujistěte se, že máte následující předpoklady:
1. Základní znalost programovacího jazyka C#.
2. Visual Studio nainstalované ve vašem systému.
3. GroupDocs.Annotation pro knihovnu .NET nainstalovanou nebo odkazovanou ve vašem projektu.
4. Vstupní dokument (např. PDF) a soubor obrázku pro anotaci.
## Import jmenných prostorů
Nejprve musíte do souboru C# importovat potřebné jmenné prostory. Tyto jmenné prostory poskytují přístup ke třídám a metodám potřebným pro práci s GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Krok 1: Definujte výstupní cestu
Definujte výstupní cestu, kam bude dokument s poznámkami uložen.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Inicializujte anotátor
Inicializujte anotátor zadáním cesty ke vstupnímu dokumentu.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Zde je kód anotace
}
```
## Krok 3: Vytvořte poznámku k obrázku
 Vytvořte instanci souboru`ImageAnnotation`třídy a zadejte její vlastnosti, jako je poloha, krytí, číslo stránky a cesta k obrázku.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## Krok 4: Přidejte anotaci
 Přidejte vytvořenou anotaci obrázku do dokumentu pomocí`Add` metoda anotátora.
```csharp
annotator.Add(image);
```
## Krok 5: Uložte dokument
Uložte dokument s poznámkami do výstupní cesty.
```csharp
annotator.Save(outputPath);
```
## Krok 6: Zobrazte výstupní cestu
Zobrazte zprávu o úspěšném uložení dokumentu a umístění výstupního souboru.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
V tomto tutoriálu jsme se naučili, jak přidat do dokumentu anotace obrázků pomocí GroupDocs.Annotation for .NET. Pomocí těchto jednoduchých kroků můžete vylepšit možnosti zpracování dokumentů pomocí výkonných funkcí anotací.
## FAQ
### Mohu anotovat jiné dokumenty než PDF?
Ano, GroupDocs.Annotation podporuje různé formáty dokumentů včetně Wordu, Excelu, PowerPointu a dalších.
### Je GroupDocs.Annotation kompatibilní s .NET Core?
Ano, GroupDocs.Annotation je kompatibilní s .NET Framework i .NET Core.
### Mohu upravit vzhled anotací?
Vzhled, velikost, barvu a další vlastnosti anotací si můžete samozřejmě přizpůsobit podle svých požadavků.
### Poskytuje GroupDocs.Annotation podporu pro společné anotace?
Ano, GroupDocs.Annotation nabízí funkce pro spolupráci anotací, které umožňují více uživatelům anotovat dokumenty současně.
### Kde najdu další pomoc nebo podporu?
Pomoc a podporu od komunity můžete získat na fóru GroupDocs.Annotation.