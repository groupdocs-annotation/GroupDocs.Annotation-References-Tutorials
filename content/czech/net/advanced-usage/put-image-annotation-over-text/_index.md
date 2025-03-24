---
title: Umístěte poznámku obrázku přes text
linktitle: Umístěte poznámku obrázku přes text
second_title: GroupDocs.Annotation .NET API
description: Naučte se přidávat obrázkové anotace přes text v .NET pomocí GroupDocs.Annotation pro efektivní správu dokumentů a spolupráci.
weight: 21
url: /cs/net/advanced-usage/put-image-annotation-over-text/
---

# Umístěte poznámku obrázku přes text

## Úvod
Ve světě vývoje .NET nabízí GroupDocs.Annotation výkonné řešení pro přidávání anotací k dokumentům, což zefektivňuje spolupráci a správu dokumentů. Jedním společným požadavkem je vkládání poznámek k obrázkům přes text, což lze hladce provést pomocí GroupDocs.Annotation pro .NET.
## Předpoklady
Než se ponoříte do procesu vkládání anotací obrázků přes text pomocí GroupDocs.Annotation for .NET, ujistěte se, že máte následující:
1.  GroupDocs.Annotation for .NET Library: Stáhněte a nainstalujte knihovnu z[tady](https://releases.groupdocs.com/annotation/net/).
2. Vývojové prostředí: Nastavte vhodné vývojové prostředí, jako je Visual Studio nebo jakékoli jiné .NET IDE.
3. Soubory dokumentů a obrázků: Připravte soubor dokumentu (PDF, DOCX atd.) a soubor obrázku, který chcete použít pro poznámky.
4. Základní porozumění C#: Pro implementaci úryvků kódu uvedených v tomto kurzu je nezbytná znalost programovacího jazyka C#.

## Import jmenných prostorů
Než budete pokračovat v procesu anotace, ujistěte se, že jste do svého projektu C# importovali potřebné jmenné prostory:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Krok 1: Definujte výstupní cestu
Nejprve definujte výstupní cestu, kam bude dokument s poznámkami uložen:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Krok 2: Inicializujte anotátor
 Inicializujte`Annotator` objekt poskytnutím cesty vstupního dokumentu:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Sem bude umístěn kód anotace
}
```
## Krok 3: Vytvořte poznámku k obrázku
 Vytvořit`ImageAnnotation` objekt s požadovanými vlastnostmi, jako jsou rozměry rámečku, neprůhlednost, číslo stránky, cesta k obrázku a z-index:
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
## Krok 4: Přidejte anotaci
 Přidejte do dokumentu anotaci obrázku pomocí`Add` metoda`Annotator` objekt:
```csharp
annotator.Add(image);
```
## Krok 5: Uložte dokument s poznámkami
Uložte anotovaný dokument do zadané výstupní cesty:
```csharp
annotator.Save(outputPath);
```
## Krok 6: Zobrazte zprávu o úspěchu
Zobrazte zprávu o úspěchu s cestou k anotovanému dokumentu:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
Závěrem lze říci, že přidávání anotací obrázků přes text v aplikacích .NET pomocí GroupDocs.Annotation je jednoduchý proces. Podle podrobného průvodce poskytnutého v tomto kurzu můžete efektivně anotovat dokumenty a zlepšit možnosti spolupráce a správy dokumentů ve svých projektech .NET.
## FAQ
### Mohu anotovat jiné dokumenty než PDF?
Ano, GroupDocs.Annotation podporuje různé formáty dokumentů, jako je DOCX, XLSX, PPTX a další.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Annotation?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[tady](https://releases.groupdocs.com/).
### Jak mohu získat podporu pro GroupDocs.Annotation?
 Podporu můžete získat na fóru komunity GroupDocs.Annotation[tady](https://forum.groupdocs.com/c/annotation/10).
### Potřebuji dočasnou licenci pro testovací účely?
 Ano, můžete získat dočasnou licenci od[tady](https://purchase.groupdocs.com/temporary-license/) pro testovací účely.
### Mohu upravit vzhled anotací?
Ano, GroupDocs.Annotation poskytuje různé možnosti přizpůsobení vzhledu anotací, jako je barva, neprůhlednost, velikost písma atd.