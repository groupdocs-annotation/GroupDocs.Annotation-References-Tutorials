---
"description": "Naučte se, jak přidávat anotace obrázků do dokumentů pomocí nástroje GroupDocs.Annotation pro .NET. Snadno vylepšete možnosti zpracování dokumentů."
"linktitle": "Přidat anotaci obrázku do dokumentu (lokální cesta)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Přidat anotaci obrázku do dokumentu (lokální cesta)"
"url": "/cs/net/unlocking-annotation-power/add-image-annotation-local-path/"
"weight": 14
---

# Přidat anotaci obrázku do dokumentu (lokální cesta)

## Zavedení
GroupDocs.Annotation pro .NET je výkonná knihovna, která umožňuje vývojářům programově přidávat do dokumentů různé typy anotací. V tomto tutoriálu se naučíme, jak přidat anotace obrázků do dokumentu pomocí lokální cesty.
## Předpoklady
Než začneme, ujistěte se, že máte následující předpoklady:
1. Základní znalost programovacího jazyka C#.
2. Visual Studio nainstalované ve vašem systému.
3. GroupDocs.Annotation pro knihovnu .NET nainstalovanou nebo tutorialsd ve vašem projektu.
4. Vstupní dokument (např. PDF) a obrazový soubor pro anotaci.
## Importovat jmenné prostory
Nejprve je třeba importovat potřebné jmenné prostory do souboru C#. Tyto jmenné prostory poskytují přístup ke třídám a metodám potřebným pro práci s GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Krok 1: Definování výstupní cesty
Definujte výstupní cestu, kam bude uložen anotovaný dokument.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Inicializace anotátoru
Inicializujte anotátor zadáním cesty ke vstupnímu dokumentu.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Sem se vkládá kód anotace
}
```
## Krok 3: Vytvořte anotaci obrázku
Vytvořte instanci `ImageAnnotation` třídu a specifikujte její vlastnosti, jako je pozice, neprůhlednost, číslo stránky a cesta k obrázku.
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
## Krok 4: Přidání anotace
Přidejte do dokumentu anotaci vytvořeného obrázku pomocí `Add` metoda anotátora.
```csharp
annotator.Add(image);
```
## Krok 5: Uložení dokumentu
Uložte anotovaný dokument do výstupní cesty.
```csharp
annotator.Save(outputPath);
```
## Krok 6: Zobrazení výstupní cesty
Zobrazit zprávu o úspěšném uložení dokumentu a umístění výstupního souboru.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
tomto tutoriálu jsme se naučili, jak přidat anotace obrázků do dokumentu pomocí GroupDocs.Annotation pro .NET. Dodržením těchto jednoduchých kroků můžete vylepšit své možnosti zpracování dokumentů pomocí výkonných funkcí pro anotace.
## Často kladené otázky
### Mohu anotovat i jiné dokumenty než PDF?
Ano, GroupDocs.Annotation podporuje různé formáty dokumentů, včetně Wordu, Excelu, PowerPointu a dalších.
### Je GroupDocs.Annotation kompatibilní s .NET Core?
Ano, GroupDocs.Annotation je kompatibilní s .NET Framework i .NET Core.
### Mohu si přizpůsobit vzhled anotací?
Vzhled, velikost, barvu a další vlastnosti anotací si samozřejmě můžete přizpůsobit podle svých požadavků.
### Poskytuje GroupDocs.Annotation podporu pro kolaborativní anotace?
Ano, GroupDocs.Annotation nabízí funkce pro spolupráci v oblasti anotací, které umožňují více uživatelům současně anotovat dokumenty.
### Kde mohu najít další pomoc nebo podporu?
Pro pomoc a podporu od komunity můžete navštívit fórum GroupDocs.Annotation.