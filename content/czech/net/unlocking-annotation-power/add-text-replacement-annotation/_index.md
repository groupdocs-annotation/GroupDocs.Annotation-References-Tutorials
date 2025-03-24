---
title: Přidejte do dokumentu anotaci nahrazující text
linktitle: Přidejte do dokumentu anotaci nahrazující text
second_title: GroupDocs.Annotation .NET API
description: Naučte se, jak do dokumentů .NET snadno přidávat anotace nahrazující text pomocí GroupDocs.Annotation for .NET. Vylepšete své možnosti manipulace s dokumenty.
weight: 24
url: /cs/net/unlocking-annotation-power/add-text-replacement-annotation/
---

# Přidejte do dokumentu anotaci nahrazující text

## Úvod
V tomto tutoriálu vás provedeme procesem přidávání anotace nahrazování textu do vašich dokumentů pomocí GroupDocs.Annotation for .NET. Tato výkonná knihovna umožňuje vývojářům programově manipulovat a anotovat různé typy dokumentů. Na konci tohoto kurzu budete vybaveni znalostmi pro bezproblémovou integraci anotací nahrazujících text do vašich aplikací .NET.
## Předpoklady
Než začneme, ujistěte se, že máte nainstalované následující předpoklady:
### 1. .NET Framework nainstalováno
Ujistěte se, že máte na vývojovém počítači nainstalováno rozhraní .NET Framework. Můžete si jej stáhnout z webu společnosti Microsoft.
### 2. GroupDocs.Anotation for .NET Library
 Stáhněte a nainstalujte knihovnu GroupDocs.Annotation for .NET z[webová stránka](https://releases.groupdocs.com/annotation/net/). Tato knihovna poskytuje potřebné nástroje a funkce pro práci s anotacemi v různých formátech dokumentů.
### 3. Nastavení vývojového prostředí
Nastavte své preferované vývojové prostředí, jako je Visual Studio, pro vytváření a spouštění aplikací .NET.

## Import jmenných prostorů
Než se ponoříme do kódovací části, importujme potřebné jmenné prostory potřebné pro práci s GroupDocs.Annotation pro .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## Krok 1: Definujte výstupní cestu
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Zde definujeme výstupní cestu, kam bude anotovaný dokument uložen.
## Krok 2: Inicializujte anotátor
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Zde bude umístěn kód anotace
}
```
Objekt Annotator inicializujeme zadáním vstupního dokumentu ("vstup.pdf") v bloku use, abychom zajistili správnou likvidaci zdrojů.
## Krok 3: Vytvořte náhradní anotaci
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
    },
    TextToReplace = "replaced text"
};
```
Zde vytvoříme objekt ReplacementAnnotation s různými vlastnostmi, jako je datum vytvoření, barva písma, zpráva, neprůhlednost, číslo stránky, barva pozadí, body (souřadnice), odpovědi (komentáře) a text, který se má nahradit.
## Krok 4: Přidejte anotaci
```csharp
annotator.Add(replacement);
```
Vytvořenou náhradní anotaci přidáme do anotátoru.
## Krok 5: Uložte dokument
```csharp
annotator.Save(outputPath);
```
Nakonec anotovaný dokument uložíme do zadané výstupní cesty.
## Krok 6: Zobrazte zprávu o úspěchu
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Zobrazí se zpráva o úspěchu označující, že dokument byl úspěšně uložen.

## Závěr
V tomto tutoriálu jsme se zabývali procesem přidávání anotací nahrazujících text do dokumentů pomocí GroupDocs.Annotation pro .NET. Pokud budete postupovat podle podrobného průvodce a porozumíte předpokladům, můžete tuto funkci snadno integrovat do svých aplikací .NET.
## FAQ
### Mohu anotovat dokumenty různých formátů pomocí GroupDocs.Annotation for .NET?
Ano, GroupDocs.Annotation for .NET podporuje anotování různých formátů dokumentů, jako jsou PDF, DOCX, PPTX, XLSX a další.
### Je GroupDocs.Annotation for .NET vhodný pro desktopové i webové aplikace?
Ano, GroupDocs.Annotation for .NET lze použít v desktopových i webových aplikacích, což poskytuje flexibilitu vývojářům.
### Mohu upravit vzhled anotací přidaných pomocí GroupDocs.Annotation for .NET?
Vzhled anotací můžete samozřejmě přizpůsobit úpravou vlastností, jako je barva, krytí, písmo atd.
### Nabízí GroupDocs.Annotation for .NET podporu pro funkce kolaborativní anotace?
Ano, GroupDocs.Annotation for .NET poskytuje funkce pro kolaborativní anotaci, která umožňuje více uživatelům anotovat dokumenty současně.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Annotation pro .NET?
Ano, můžete využít bezplatnou zkušební verzi GroupDocs.Annotation pro .NET z webu[webová stránka](https://releases.groupdocs.com/).