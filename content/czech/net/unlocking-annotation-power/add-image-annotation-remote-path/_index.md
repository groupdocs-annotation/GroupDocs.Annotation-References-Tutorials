---
"description": "Naučte se, jak přidávat anotace obrázků do dokumentů pomocí nástroje GroupDocs.Annotation pro .NET. Vylepšete správu dokumentů pomocí výkonných funkcí pro anotace."
"linktitle": "Přidat anotaci obrázku do dokumentu (vzdálená cesta)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Přidat anotaci obrázku do dokumentu (vzdálená cesta)"
"url": "/cs/net/unlocking-annotation-power/add-image-annotation-remote-path/"
type: docs
"weight": 15
---

# Přidat anotaci obrázku do dokumentu (vzdálená cesta)

## Zavedení
V tomto tutoriálu si projdeme procesem přidávání anotací obrázků do dokumentu pomocí knihovny GroupDocs.Annotation pro .NET. Tato knihovna poskytuje výkonné nástroje pro programovou anotaci různých typů dokumentů.
## Předpoklady
Než začneme, ujistěte se, že máte následující:
1. GroupDocs.Annotation pro .NET: Stáhněte a nainstalujte knihovnu z [zde](https://releases.groupdocs.com/annotation/net/).
2. Vývojové prostředí: Ujistěte se, že máte nastavené funkční vývojové prostředí pro vývoj v .NET.
3. Dokument: Připravte si dokument, do kterého chcete vložit poznámky. V tomto tutoriálu budeme předpokládat, že máte dokument PDF s názvem `input.pdf`.
4. Obrázek pro anotaci: Vyberte obrázek, který chcete použít pro anotaci. Ujistěte se, že máte připravenou URL adresu obrázku nebo lokální cestu.

## Importovat jmenné prostory
Než začneme s kódováním, importujme potřebné jmenné prostory:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Krok 1: Nastavení výstupní cesty
Nejprve definujte výstupní cestu, kam bude uložen anotovaný dokument.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Inicializace anotátoru
Vytvořte instanci `Annotator` třídu a specifikujte vstupní dokument.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Sem bude vložen kód anotace
}
```
## Krok 3: Přidání anotace k obrázku
Nyní přidáme do dokumentu anotaci obrázku. Určíme vlastnosti anotace obrázku, jako je pozice, neprůhlednost, číslo stránky a cesta k obrázku.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Zadejte pozici anotace
    CreatedOn = DateTime.Now, // Nastavte datum vytvoření
    Opacity = 0.7, // Nastavení neprůhlednosti (0 až 1)
    PageNumber = 0, // Zadejte číslo stránky
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Zadejte URL adresu obrázku
};
annotator.Add(image); // Přidat anotaci k obrázku
```
## Krok 4: Uložení dokumentu
Uložte anotovaný dokument do zadané výstupní cesty.
```csharp
annotator.Save(outputPath);
```
## Krok 5: Zobrazení výstupní cesty
Informovat uživatele o úspěšném uložení dokumentu a zobrazit výstupní cestu.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
V tomto tutoriálu jsme se naučili, jak přidat anotace obrázků do dokumentu pomocí nástroje GroupDocs.Annotation pro .NET. Dodržením těchto kroků můžete vylepšit své aplikace pro správu dokumentů o výkonné funkce pro tvorbu anotací.
## Často kladené otázky
### Lze GroupDocs.Annotation použít s jinými formáty dokumentů než PDF?
Ano, GroupDocs.Annotation podporuje různé formáty dokumentů, včetně Wordu, Excelu, PowerPointu a dalších.
### Je GroupDocs.Annotation kompatibilní s .NET Core?
Ano, GroupDocs.Annotation je kompatibilní s .NET Framework i .NET Core.
### Mohu si přizpůsobit vzhled anotací?
Ano, vzhled anotací, jako je barva, neprůhlednost a velikost, si můžete přizpůsobit.
### Podporuje GroupDocs.Annotation funkce pro spolupráci v oblasti anotací?
Ano, GroupDocs.Annotation nabízí funkce pro spolupráci na dokumentech v reálném čase.
### Je k dispozici zkušební verze pro testování?
Ano, můžete získat bezplatnou zkušební verzi GroupDocs.Annotation od [zde](https://releases.groupdocs.com/).