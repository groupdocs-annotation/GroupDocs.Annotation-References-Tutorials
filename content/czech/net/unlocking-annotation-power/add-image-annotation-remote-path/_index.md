---
title: Přidat k dokumentu poznámku obrázku (vzdálená cesta)
linktitle: Přidat k dokumentu poznámku obrázku (vzdálená cesta)
second_title: GroupDocs.Annotation .NET API
description: Naučte se přidávat popisky obrázků do dokumentů pomocí GroupDocs.Annotation for .NET. Vylepšete správu dokumentů pomocí výkonných možností anotací.
weight: 15
url: /cs/net/unlocking-annotation-power/add-image-annotation-remote-path/
---

# Přidat k dokumentu poznámku obrázku (vzdálená cesta)

## Úvod
V tomto tutoriálu si projdeme proces přidávání anotací obrázků do dokumentu pomocí GroupDocs.Annotation for .NET. Tato knihovna poskytuje výkonné nástroje pro programové anotování různých typů dokumentů.
## Předpoklady
Než začneme, ujistěte se, že máte následující:
1.  GroupDocs.Annotation for .NET: Stáhněte a nainstalujte knihovnu z[tady](https://releases.groupdocs.com/annotation/net/).
2. Vývojové prostředí: Ujistěte se, že máte funkční vývojové prostředí nastavené pro vývoj .NET.
3.  Dokument: Připravte dokument, který chcete anotovat. Pro tento tutoriál budeme předpokládat, že máte pojmenovaný dokument PDF`input.pdf`.
4. Obrázek pro anotaci: Vyberte obrázek, který chcete použít pro anotaci. Ujistěte se, že máte připravenou adresu URL obrázku nebo místní cestu.

## Import jmenných prostorů
Než začneme kódovat, importujme potřebné jmenné prostory:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Krok 1: Nastavte výstupní cestu
Nejprve definujte výstupní cestu, kam bude dokument s poznámkami uložen.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Inicializujte anotátor
 Vytvořte instanci souboru`Annotator` třídy a zadejte vstupní dokument.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Sem bude umístěn kód anotace
}
```
## Krok 3: Přidejte poznámku k obrázku
Nyní přidáme do dokumentu anotaci obrázku. Určíme vlastnosti anotace obrázku, jako je poloha, krytí, číslo stránky a cesta obrázku.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Určete polohu anotace
    CreatedOn = DateTime.Now, // Nastavte datum vytvoření
    Opacity = 0.7, // Nastavit krytí (0 až 1)
    PageNumber = 0, // Zadejte číslo stránky
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Zadejte adresu URL obrázku
};
annotator.Add(image); // Přidejte anotaci obrázku
```
## Krok 4: Uložte dokument
Uložte dokument s poznámkami do zadané výstupní cesty.
```csharp
annotator.Save(outputPath);
```
## Krok 5: Zobrazte výstupní cestu
Informujte uživatele o úspěšné operaci uložení dokumentu a zobrazte výstupní cestu.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
tomto tutoriálu jsme se naučili, jak přidat do dokumentu anotace obrázků pomocí GroupDocs.Annotation for .NET. Pomocí těchto kroků můžete vylepšit své aplikace pro správu dokumentů o výkonné možnosti anotací.
## FAQ
### Lze GroupDocs.Annotation použít s jinými formáty dokumentů kromě PDF?
Ano, GroupDocs.Annotation podporuje různé formáty dokumentů včetně Wordu, Excelu, PowerPointu a dalších.
### Je GroupDocs.Annotation kompatibilní s .NET Core?
Ano, GroupDocs.Annotation je kompatibilní s .NET Framework i .NET Core.
### Mohu upravit vzhled anotací?
Ano, vzhled anotací, jako je barva, neprůhlednost a velikost, si můžete přizpůsobit.
### Podporuje GroupDocs.Annotation funkce společné anotace?
Ano, GroupDocs.Annotation nabízí funkce pro spolupráci anotací pro spolupráci na dokumentech v reálném čase.
### Je k dispozici zkušební verze pro testování?
 Ano, můžete získat bezplatnou zkušební verzi GroupDocs.Annotation od[tady](https://releases.groupdocs.com/).