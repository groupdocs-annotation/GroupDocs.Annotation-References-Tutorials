---
title: Otáčení dokumentů PDF
linktitle: Otáčení dokumentů PDF
second_title: GroupDocs.Annotation .NET API
description: Naučte se, jak snadno otáčet dokumenty PDF pomocí Groupdocs.Annotation pro .NET. Zlepšete efektivitu správy dokumentů.
type: docs
weight: 22
url: /cs/net/advanced-usage/rotating-pdf-documents/
---
## Úvod
Otáčení dokumentů PDF může být zásadním úkolem při práci se soubory, které je třeba prohlížet nebo zpracovávat jinak. V tomto tutoriálu prozkoumáme, jak otáčet dokumenty PDF krok za krokem pomocí Groupdocs.Annotation pro .NET.
## Předpoklady
Než se pustíte do výukového programu, ujistěte se, že máte následující předpoklady:
1.  Groupdocs.Annotation for .NET Library: Ujistěte se, že jste si stáhli a nainstalovali knihovnu Groupdocs.Annotation for .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/annotation/net/).
2. Základní znalost programování v C#: Tento tutoriál předpokládá, že máte základní znalosti programovacího jazyka C# a jak pracovat s knihovnami .NET.

## Import jmenných prostorů
Nejprve musíte do svého projektu C# importovat potřebné jmenné prostory, abyste získali přístup k funkcím, které poskytuje knihovna Groupdocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Krok 1: Načtěte dokument PDF
 Začněte načtením dokumentu PDF, který chcete otočit, pomocí`Annotator` třída.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Krok 2: Nastavte rotaci a zpracování stránek
Zadejte úhel otočení a stránky, které chcete otočit. V tomto příkladu otočíme první stránku o 90 stupňů ve směru hodinových ručiček.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Krok 3: Uložte otočený dokument
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
Otáčení dokumentů PDF je základní operací as Groupdocs.Annotation pro .NET se stává jednoduchým a efektivním. Podle kroků uvedených v tomto tutoriálu můžete snadno otáčet soubory PDF podle svých požadavků.
## FAQ
### Mohu otočit více stránek v dokumentu PDF pomocí Groupdocs.Annotation pro .NET?
 Ano, můžete určit více stránek k otočení úpravou`ProcessPages` majetek podle toho.
### Je Groupdocs.Annotation for .NET kompatibilní se všemi verzemi .NET frameworku?
Groupdocs.Annotation for .NET podporuje širokou škálu verzí .NET frameworku, což zajišťuje kompatibilitu pro většinu vývojových prostředí.
### Poskytuje Groupdocs.Annotation for .NET možnosti pro otáčení dokumentů PDF v různých směrech?
Ano, dokumenty PDF můžete otáčet po směru, proti směru hodinových ručiček nebo ve vlastních úhlech podle vašich požadavků.
### Mohu integrovat Groupdocs.Annotation for .NET do svého stávajícího systému správy dokumentů?
Rozhodně, Groupdocs.Annotation for .NET nabízí bezproblémové možnosti integrace, což vám umožní bez námahy vylepšit možnosti správy dokumentů.
### Je k dispozici zkušební verze pro Groupdocs.Annotation pro .NET?
 Ano, můžete získat bezplatnou zkušební verzi od[tady](https://releases.groupdocs.com/).