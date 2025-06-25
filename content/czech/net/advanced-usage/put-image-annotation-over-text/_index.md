---
"description": "Naučte se, jak přidávat anotace obrázků přes text v .NET pomocí GroupDocs.Annotation pro efektivní správu dokumentů a spolupráci."
"linktitle": "Vložení obrázkové anotace přes text"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Vložení obrázkové anotace přes text"
"url": "/cs/net/advanced-usage/put-image-annotation-over-text/"
"weight": 21
---

# Vložení obrázkové anotace přes text

## Zavedení
Ve světě vývoje v .NET nabízí GroupDocs.Annotation výkonné řešení pro přidávání anotací do dokumentů, což zefektivňuje spolupráci a správu dokumentů. Jedním z běžných požadavků je vkládání obrázkových anotací přes text, čehož lze bez problémů dosáhnout pomocí GroupDocs.Annotation pro .NET.
## Předpoklady
Než se pustíte do procesu vkládání obrázkových anotací přes text pomocí GroupDocs.Annotation pro .NET, ujistěte se, že máte následující:
1. GroupDocs.Annotation pro knihovnu .NET: Stáhněte a nainstalujte knihovnu z [zde](https://releases.groupdocs.com/annotation/net/).
2. Vývojové prostředí: Nastavte vhodné vývojové prostředí, například Visual Studio nebo jakékoli jiné .NET IDE.
3. Soubory dokumentů a obrázků: Připravte soubor dokumentu (PDF, DOCX atd.) a soubor obrázku, který chcete použít pro anotace.
4. Základní znalost jazyka C#: Znalost programovacího jazyka C# je nezbytná pro implementaci úryvků kódu uvedených v tomto tutoriálu.

## Importovat jmenné prostory
Než budete pokračovat v procesu anotace, ujistěte se, že jste do projektu C# importovali potřebné jmenné prostory:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Krok 1: Definování výstupní cesty
Nejprve definujte výstupní cestu, kam bude uložen anotovaný dokument:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Krok 2: Inicializace anotátoru
Inicializujte `Annotator` objekt zadáním vstupní cesty k dokumentu:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Sem bude vložen kód anotace
}
```
## Krok 3: Vytvořte anotaci obrázku
Vytvořte `ImageAnnotation` objekt s požadovanými vlastnostmi, jako jsou rozměry rámečku, neprůhlednost, číslo stránky, cesta k obrázku a z-index:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## Krok 4: Přidání anotace
Přidejte do dokumentu anotaci obrázku pomocí `Add` metoda `Annotator` objekt:
```csharp
annotator.Add(image);
```
## Krok 5: Uložení anotovaného dokumentu
Uložte anotovaný dokument do zadané výstupní cesty:
```csharp
annotator.Save(outputPath);
```
## Krok 6: Zobrazení zprávy o úspěchu
Zobrazit zprávu o úspěchu s cestou k anotovanému dokumentu:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
Závěrem lze říci, že přidávání obrázkových anotací přes text v aplikacích .NET pomocí GroupDocs.Annotation je jednoduchý proces. Dodržováním podrobných pokynů uvedených v tomto tutoriálu můžete efektivně anotovat dokumenty a vylepšit možnosti spolupráce a správy dokumentů ve vašich projektech .NET.
## Často kladené otázky
### Mohu anotovat i jiné dokumenty než PDF?
Ano, GroupDocs.Annotation podporuje různé formáty dokumentů, jako například DOCX, XLSX, PPTX a další.
### Je k dispozici bezplatná zkušební verze GroupDocs.Annotation?
Ano, můžete si stáhnout bezplatnou zkušební verzi z [zde](https://releases.groupdocs.com/).
### Jak mohu získat podporu pro GroupDocs.Annotation?
Podporu můžete získat na komunitním fóru GroupDocs.Annotation. [zde](https://forum.groupdocs.com/c/annotation/10).
### Potřebuji pro účely testování dočasnou licenci?
Ano, můžete získat dočasnou licenci od [zde](https://purchase.groupdocs.com/temporary-license/) pro účely testování.
### Mohu si přizpůsobit vzhled anotací?
Ano, GroupDocs.Annotation nabízí různé možnosti pro přizpůsobení vzhledu anotací, jako je barva, neprůhlednost, velikost písma atd.