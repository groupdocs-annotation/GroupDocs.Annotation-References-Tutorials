---
"description": "Naučte se, jak programově anotovat PDF dokumenty pomocí GroupDocs.Annotation pro .NET. Podrobný návod s příklady kódu."
"linktitle": "Načíst dokument z URL adresy"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Načíst dokument z URL adresy"
"url": "/cs/net/document-loading-essentials/load-document-from-url/"
type: docs
"weight": 15
---

# Načíst dokument z URL adresy

## Zavedení
GroupDocs.Annotation pro .NET je knihovna bohatá na funkce, která vývojářům umožňuje bez námahy přidávat do jejich .NET aplikací možnosti anotací. S GroupDocs.Annotation můžete programově anotovat dokumenty PDF, což uživatelům umožňuje zvýrazňovat text, přidávat komentáře, kreslit tvary a provádět další akce. Tento tutoriál vás provede kroky načtení dokumentu z URL adresy, přidání anotací a uložení anotovaného dokumentu pomocí GroupDocs.Annotation pro .NET.
## Předpoklady
Než začnete, ujistěte se, že máte následující předpoklady:
1. Visual Studio: Ujistěte se, že máte na vývojovém počítači nainstalované Visual Studio.
2. GroupDocs.Annotation pro .NET: Stáhněte a nainstalujte GroupDocs.Annotation pro .NET z [webové stránky](https://releases.groupdocs.com/annotation/net/).
3. Základní znalost C#: Seznamte se s programovacím jazykem C#.
4. Připojení k internetu: Pro přístup k externím zdrojům a stahování ukázkových souborů budete potřebovat připojení k internetu.

## Importovat jmenné prostory
Nejprve si do vašeho projektu v C# importujme potřebné jmenné prostory:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## Krok 1: Načtení dokumentu z URL adresy
Chcete-li anotovat dokument PDF z adresy URL, postupujte takto:
### Krok 1.1: Definování výstupní cesty
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Krok 1.2: Zadejte URL
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### Krok 1.3: Načtení dokumentu
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // Přidejte sem anotace
    annotator.Save(outputPath);
}
```
## Krok 2: Přidání anotací
Nyní přidáme do načteného dokumentu anotace. V tomto příkladu přidáme anotaci oblasti:
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Krok 3: Uložení anotovaného dokumentu
Nakonec uložte anotovaný dokument do zadané výstupní cesty:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
V tomto tutoriálu jsme se naučili, jak anotovat dokumenty PDF pomocí GroupDocs.Annotation pro .NET. Dodržováním podrobného návodu můžete bezproblémově integrovat funkci anotací do svých aplikací .NET a umožnit uživatelům efektivně spolupracovat na souborech PDF.

## Často kladené otázky
### Je GroupDocs.Annotation pro .NET kompatibilní se všemi .NET frameworky?
Ano, GroupDocs.Annotation pro .NET je kompatibilní s různými frameworky .NET, včetně .NET Framework, .NET Core a .NET Standard.
### Mohu si přizpůsobit vzhled anotací?
Rozhodně! GroupDocs.Annotation pro .NET nabízí rozsáhlé možnosti přizpůsobení, které vám umožňují upravit vzhled a chování anotací podle vašich požadavků.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Annotation pro .NET?
Ano, můžete si stáhnout bezplatnou zkušební verzi GroupDocs.Annotation pro .NET z [webové stránky](https://releases.groupdocs.com/).
### Jak mohu získat technickou podporu pro GroupDocs.Annotation pro .NET?
Pokud narazíte na jakékoli technické problémy nebo máte dotazy ohledně GroupDocs.Annotation pro .NET, můžete požádat o pomoc [fórum podpory](https://forum.groupdocs.com/c/annotation/10).
### Kde si mohu zakoupit licenci pro GroupDocs.Annotation pro .NET?
Licenci pro GroupDocs.Annotation pro .NET si můžete zakoupit od [stránka nákupu](https://purchase.groupdocs.com/buy).