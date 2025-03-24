---
title: Přidejte do dokumentu anotaci křivky
linktitle: Přidejte do dokumentu anotaci křivky
second_title: GroupDocs.Annotation .NET API
description: Naučte se přidávat anotace křivek do dokumentů pomocí GroupDocs.Annotation for .NET. Vylepšete spolupráci a procesy kontroly dokumentů bez námahy.
weight: 18
url: /cs/net/unlocking-annotation-power/add-polyline-annotation/
---
## Úvod
GroupDocs.Annotation for .NET je výkonný nástroj, který umožňuje vývojářům programově anotovat dokumenty PDF a Microsoft Office. Mezi jeho funkce patří schopnost přidávat k dokumentům anotace křivek, což zlepšuje spolupráci a procesy kontroly dokumentů.
## Předpoklady
Než budete pokračovat v tomto tutoriálu, ujistěte se, že máte následující:
- Visual Studio nainstalované ve vašem systému.
- Základní znalost programovacího jazyka C#.
-  Nainstalovaná knihovna GroupDocs.Annotation pro .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/annotation/net/).

## Import jmenných prostorů
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Definujte výstupní cestu
Nejprve definujte výstupní cestu, kam bude dokument s poznámkami uložen.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Inicializujte anotátor
Inicializujte anotátor zadáním názvu vstupního dokumentu.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 3: Vytvořte objekt poznámky křivky
Vytvořte objekt anotace křivky a nastavte jeho vlastnosti, jako je poloha, zpráva, krytí, barva pera, styl pera a šířka pera.
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
## Krok 4: Přidejte anotaci křivky
Přidejte do dokumentu anotaci křivky pomocí objektu anotátoru.
```csharp
annotator.Add(polyline);
```
## Krok 5: Uložte dokument
Uložte dokument s poznámkami do zadané výstupní cesty.
```csharp
annotator.Save(outputPath);
```
## Krok 6: Zobrazte zprávu o úspěchu
Zobrazte zprávu potvrzující úspěšné uložení dokumentu.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
tomto tutoriálu jsme se naučili, jak přidat anotaci křivky do dokumentu pomocí GroupDocs.Annotation for .NET. Tato funkce zlepšuje spolupráci a procesy kontroly dokumentů a usnadňuje uživatelům efektivně sdělovat zpětnou vazbu a návrhy.
## FAQ
### Je GroupDocs.Annotation for .NET kompatibilní se všemi formáty dokumentů?
GroupDocs.Annotation for .NET podporuje oblíbené formáty dokumentů, jako jsou PDF a formáty Microsoft Office včetně Wordu, Excelu a PowerPointu.
### Mohu upravit vzhled anotací?
Ano, můžete přizpůsobit různé vlastnosti anotací, jako je barva, neprůhlednost, styl a šířka, aby vyhovovaly vašim požadavkům.
### Nabízí GroupDocs.Annotation for .NET bezplatnou zkušební verzi?
 Ano, můžete využít bezplatnou zkušební verzi GroupDocs.Annotation pro .NET návštěvou[tento odkaz](https://releases.groupdocs.com/).
### Kde najdu dokumentaci k GroupDocs.Annotation pro .NET?
 Můžete najít dokumentaci pro GroupDocs.Annotation pro .NET[tady](https://tutorials.groupdocs.com/annotation/net/).
### Jak mohu získat podporu pro jakékoli problémy nebo dotazy související s GroupDocs.Annotation pro .NET?
 Podporu můžete získat návštěvou fóra GroupDocs.Annotation[tady](https://forum.groupdocs.com/c/annotation/10).