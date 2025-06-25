---
"description": "Naučte se, jak přidávat anotace křivek do dokumentů pomocí GroupDocs.Annotation pro .NET. Bez námahy vylepšete spolupráci a procesy kontroly dokumentů."
"linktitle": "Přidání anotace křivky do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Přidání anotace křivky do dokumentu"
"url": "/cs/net/unlocking-annotation-power/add-polyline-annotation/"
"weight": 18
---

# Přidání anotace křivky do dokumentu

## Zavedení
GroupDocs.Annotation pro .NET je výkonný nástroj, který umožňuje vývojářům programově anotovat dokumenty PDF a Microsoft Office. Mezi jeho funkce patří možnost přidávat do dokumentů anotace křivkami, což vylepšuje spolupráci a procesy kontroly dokumentů.
## Předpoklady
Než budete pokračovat v tomto tutoriálu, ujistěte se, že máte následující:
- Visual Studio nainstalované ve vašem systému.
- Základní znalost programovacího jazyka C#.
- Je nainstalována knihovna GroupDocs.Annotation pro .NET. Můžete si ji stáhnout z [zde](https://releases.groupdocs.com/annotation/net/).

## Importovat jmenné prostory
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Definování výstupní cesty
Nejprve definujte výstupní cestu, kam bude uložen anotovaný dokument.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Inicializace anotátoru
Inicializujte anotátor zadáním názvu vstupního dokumentu.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 3: Vytvoření objektu anotace křivky
Vytvořte objekt anotace křivky a nastavte jeho vlastnosti, jako je poloha, zpráva, neprůhlednost, barva pera, styl pera a šířka pera.
```csharp
PolylineAnnotation polyline = new PolylineAnnotation
{
    Box = new Rectangle(250, 35, 102, 12),
    CreatedOn = DateTime.Now,
    Message = "This is polyline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
    SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.698685
4460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
};
```
## Krok 4: Přidání anotace křivky
Přidejte do dokumentu anotaci křivky pomocí objektu anotátoru.
```csharp
annotator.Add(polyline);
```
## Krok 5: Uložení dokumentu
Uložte anotovaný dokument do zadané výstupní cesty.
```csharp
annotator.Save(outputPath);
```
## Krok 6: Zobrazení zprávy o úspěchu
Zobrazit zprávu potvrzující úspěšné uložení dokumentu.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
V tomto tutoriálu jsme se naučili, jak přidat do dokumentu anotaci křivky pomocí GroupDocs.Annotation pro .NET. Tato funkce vylepšuje procesy spolupráce a kontroly dokumentů a usnadňuje uživatelům efektivní sdělování zpětné vazby a návrhů.
## Často kladené otázky
### Je GroupDocs.Annotation pro .NET kompatibilní se všemi formáty dokumentů?
GroupDocs.Annotation pro .NET podporuje oblíbené formáty dokumentů, jako je PDF a formáty Microsoft Office, včetně Wordu, Excelu a PowerPointu.
### Mohu si přizpůsobit vzhled anotací?
Ano, můžete si přizpůsobit různé vlastnosti anotací, jako je barva, neprůhlednost, styl a šířka, aby vyhovovaly vašim požadavkům.
### Nabízí GroupDocs.Annotation pro .NET bezplatnou zkušební verzi?
Ano, můžete využít bezplatnou zkušební verzi GroupDocs.Annotation pro .NET na adrese [tento odkaz](https://releases.groupdocs.com/).
### Kde najdu dokumentaci k GroupDocs.Annotation pro .NET?
Dokumentaci k souboru GroupDocs.Annotation pro .NET naleznete v [zde](https://tutorials.groupdocs.com/annotation/net/).
### Jak mohu získat podporu pro jakékoli problémy nebo dotazy týkající se GroupDocs.Annotation pro .NET?
Podporu můžete získat na fóru GroupDocs.Annotation. [zde](https://forum.groupdocs.com/c/annotation/10).