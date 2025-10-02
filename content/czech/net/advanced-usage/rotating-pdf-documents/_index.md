---
"description": "Naučte se, jak snadno otáčet PDF dokumenty pomocí Groupdocs.Annotation pro .NET. Zlepšete efektivitu správy dokumentů."
"linktitle": "Otáčení PDF dokumentů"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Otáčení PDF dokumentů"
"url": "/cs/net/advanced-usage/rotating-pdf-documents/"
type: docs
"weight": 22
---

# Otáčení PDF dokumentů

## Zavedení
Otáčení PDF dokumentů může být klíčovým úkolem při práci se soubory, které je třeba zobrazit nebo zpracovat odlišným způsobem. V tomto tutoriálu si krok za krokem ukážeme, jak otáčet PDF dokumenty pomocí Groupdocs.Annotation pro .NET.
## Předpoklady
Než se pustíte do tutoriálu, ujistěte se, že máte následující předpoklady:
1. Knihovna Groupdocs.Annotation pro .NET: Ujistěte se, že jste si stáhli a nainstalovali knihovnu Groupdocs.Annotation pro .NET. Můžete si ji stáhnout z [zde](https://releases.groupdocs.com/annotation/net/).
2. Základní znalosti programování v jazyce C#: Tento tutoriál předpokládá, že máte základní znalosti programovacího jazyka C# a práce s knihovnami .NET.

## Importovat jmenné prostory
Nejprve je třeba importovat potřebné jmenné prostory do projektu C#, abyste měli přístup k funkcím poskytovaným knihovnou Groupdocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Krok 1: Načtěte dokument PDF
Začněte načtením dokumentu PDF, který chcete otočit, pomocí `Annotator` třída.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Krok 2: Nastavení rotace a zpracování stránek
Zadejte úhel otočení a stránky, které chcete otočit. V tomto příkladu otočíme první stránku o 90 stupňů ve směru hodinových ručiček.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Krok 3: Uložení otočeného dokumentu
Uložte otočený dokument PDF se zadanými změnami.
```csharp
annotator.Save("result.pdf");
```
## Krok 4: Zobrazení potvrzení
Informujte uživatele, že dokument byl úspěšně otočen.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Závěr
Otáčení PDF dokumentů je základní operace a s Groupdocs.Annotation pro .NET se stává jednoduchou a efektivní. Dodržováním kroků popsaných v tomto tutoriálu můžete snadno otáčet PDF soubory podle svých požadavků.
## Často kladené otázky
### Mohu otočit více stránek v dokumentu PDF pomocí Groupdocs.Annotation pro .NET?
Ano, můžete zadat více stránek, které se mají otočit, úpravou `ProcessPages` majetek odpovídajícím způsobem.
### Je Groupdocs.Annotation pro .NET kompatibilní se všemi verzemi frameworku .NET?
Groupdocs.Annotation pro .NET podporuje širokou škálu verzí frameworku .NET, což zajišťuje kompatibilitu s většinou vývojových prostředí.
### Nabízí Groupdocs.Annotation pro .NET možnosti otáčení PDF dokumentů v různých směrech?
Ano, dokumenty PDF můžete otáčet ve směru hodinových ručiček, proti směru hodinových ručiček nebo v libovolných úhlech podle vašich požadavků.
### Mohu integrovat Groupdocs.Annotation pro .NET do svého stávajícího systému pro správu dokumentů?
Rozhodně, Groupdocs.Annotation pro .NET nabízí bezproblémové možnosti integrace, které vám umožní bez námahy vylepšit funkce správy dokumentů.
### Je k dispozici zkušební verze pro Groupdocs.Annotation pro .NET?
Ano, můžete získat bezplatnou zkušební verzi od [zde](https://releases.groupdocs.com/).