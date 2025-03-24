---
title: Načíst dokument z adresy URL
linktitle: Načíst dokument z adresy URL
second_title: GroupDocs.Annotation .NET API
description: Naučte se, jak programově anotovat dokumenty PDF pomocí GroupDocs.Annotation pro .NET. Výukový program krok za krokem s příklady kódu.
weight: 15
url: /cs/net/document-loading-essentials/load-document-from-url/
---
## Úvod
GroupDocs.Annotation for .NET je knihovna s bohatými funkcemi, která umožňuje vývojářům bez námahy přidávat možnosti anotací do jejich aplikací .NET. Pomocí GroupDocs.Annotation můžete programově anotovat dokumenty PDF, což uživatelům umožňuje zvýrazňovat text, přidávat komentáře, kreslit tvary a další. Tento výukový program vás provede kroky načítání dokumentu z adresy URL, přidáváním anotací a ukládáním anotovaného dokumentu pomocí GroupDocs.Annotation for .NET.
## Předpoklady
Než začnete, ujistěte se, že máte následující předpoklady:
1. Visual Studio: Ujistěte se, že máte na vývojovém počítači nainstalované Visual Studio.
2.  GroupDocs.Annotation for .NET: Stáhněte a nainstalujte GroupDocs.Annotation for .NET z webu[webová stránka](https://releases.groupdocs.com/annotation/net/).
3. Základní znalost C#: Seznamte se s programovacím jazykem C#.
4. Připojení k internetu: Pro přístup k externím zdrojům a stahování ukázkových souborů budete potřebovat připojení k internetu.

## Import jmenných prostorů
Nejprve importujme potřebné jmenné prostory do vašeho projektu C#:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## Krok 1: Načtěte dokument z adresy URL
Chcete-li anotovat dokument PDF z adresy URL, postupujte takto:
### Krok 1.1: Definujte výstupní cestu
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Krok 1.2: Zadejte adresu URL
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### Krok 1.3: Načtěte dokument
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // Zde přidejte anotace
    annotator.Save(outputPath);
}
```
## Krok 2: Přidejte poznámky
Nyní k načtenému dokumentu přidáme anotace. V tomto příkladu přidáme anotaci oblasti:
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Krok 3: Uložte dokument s poznámkami
Nakonec uložte anotovaný dokument do zadané výstupní cesty:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
V tomto tutoriálu jsme se naučili, jak anotovat dokumenty PDF pomocí GroupDocs.Annotation pro .NET. Dodržováním tohoto podrobného průvodce můžete bezproblémově integrovat funkce anotací do svých aplikací .NET a umožnit uživatelům efektivně spolupracovat na souborech PDF.

## FAQ
### Je GroupDocs.Annotation for .NET kompatibilní se všemi frameworky .NET?
Ano, GroupDocs.Annotation for .NET je kompatibilní s různými frameworky .NET, včetně .NET Framework, .NET Core a .NET Standard.
### Mohu upravit vzhled anotací?
Absolutně! GroupDocs.Annotation for .NET poskytuje rozsáhlé možnosti přizpůsobení, které vám umožňují upravit vzhled a chování anotací podle vašich požadavků.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Annotation pro .NET?
 Ano, můžete si stáhnout bezplatnou zkušební verzi GroupDocs.Annotation pro .NET z webu[webová stránka](https://releases.groupdocs.com/).
### Jak mohu získat technickou podporu pro GroupDocs.Annotation pro .NET?
 Pokud narazíte na nějaké technické problémy nebo máte dotazy ohledně GroupDocs.Annotation pro .NET, můžete požádat o pomoc[Fórum podpory](https://forum.groupdocs.com/c/annotation/10).
### Kde si mohu zakoupit licenci pro GroupDocs.Annotation pro .NET?
 Licenci pro GroupDocs.Annotation pro .NET si můžete zakoupit na webu[nákupní stránku](https://purchase.groupdocs.com/buy).