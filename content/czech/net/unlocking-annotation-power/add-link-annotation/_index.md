---
title: Přidejte do dokumentu anotaci odkazu
linktitle: Přidejte do dokumentu anotaci odkazu
second_title: GroupDocs.Annotation .NET API
description: Zjistěte, jak přidat anotace odkazů do dokumentů pomocí Groupdocs.Annotation pro .NET. Vylepšete spolupráci a interaktivitu bez námahy.
type: docs
weight: 16
url: /cs/net/unlocking-annotation-power/add-link-annotation/
---
## Úvod
Groupdocs.Annotation for .NET je výkonná knihovna, která umožňuje vývojářům bez námahy integrovat komplexní funkce anotací do jejich aplikací .NET. Jednou z klíčových funkcí, které nabízí, je možnost přidávat k dokumentům anotace odkazů, což zlepšuje spolupráci a interaktivitu.
## Předpoklady
Než se ponoříte do procesu přidávání anotací odkazů, ujistěte se, že máte následující předpoklady:
- Základní znalost programovacího jazyka C#.
- Nainstalovaná Groupdocs.Annotation pro knihovnu .NET.
- Přístup k dokumentu, který chcete anotovat.

## Import jmenných prostorů
Nejprve musíte importovat potřebné jmenné prostory, abyste mohli využívat funkce Groupdocs.Annotation pro .NET. To umožňuje vaší aplikaci přístup ke třídám a metodám potřebným pro anotaci dokumentů.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Nastavte výstupní cestu
Definujte cestu, kam chcete uložit dokument s poznámkami.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Inicializujte anotátor
 Vytvořte instanci souboru`Annotator` třídy zadáním cesty k dokumentu, který chcete anotovat.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Sem bude umístěn kód anotace
}
```
## Krok 3: Vytvořte anotaci odkazu
 Definujte a`LinkAnnotation` objekt a zadejte jeho vlastnosti, jako je zpráva, neprůhlednost, číslo stránky, barva pozadí, body, odpovědi a URL.
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
    Url = "https://www.google.com"
};
```
## Krok 4: Přidejte anotaci
 Přidejte vytvořenou anotaci odkazu do dokumentu pomocí`Add` metoda instance anotátoru.
```csharp
annotator.Add(link);
```
## Krok 5: Uložte dokument
Uložte dokument s poznámkami do zadané výstupní cesty.
```csharp
annotator.Save(outputPath);
```
## Krok 6: Zobrazte zprávu o úspěchu
Informovat uživatele o úspěšném uložení anotovaného dokumentu.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr
Závěrem lze říci, že provedením výše uvedených kroků můžete bez problémů přidávat anotace odkazů k dokumentům pomocí Groupdocs.Annotation for .NET. To zlepšuje spolupráci na dokumentech a poskytuje uživatelům interaktivní funkce.
## FAQ
### Je Groupdocs.Annotation for .NET kompatibilní se všemi typy dokumentů?
Groupdocs.Annotation for .NET podporuje širokou škálu formátů dokumentů včetně PDF, Wordu, Excelu a dalších.
### Mohu upravit vzhled anotací?
Ano, můžete přizpůsobit různé vlastnosti anotací, jako je barva, neprůhlednost a velikost, aby vyhovovaly vašim požadavkům.
### Nabízí Groupdocs.Annotation for .NET funkce pro spolupráci v reálném čase?
Ano, Groupdocs.Annotation for .NET poskytuje funkce spolupráce v reálném čase, které umožňují více uživatelům anotovat dokumenty současně.
### Je pro produkty Groupdocs k dispozici technická podpora?
 Ano, technická podpora pro produkty Groupdocs je k dispozici prostřednictvím fóra a podpory[tady](https://forum.groupdocs.com/c/annotation/10).
### Mohu vyzkoušet Groupdocs.Annotation pro .NET před nákupem?
Ano, můžete využít bezplatnou zkušební verzi Groupdocs.Annotation for .NET a prozkoumat její funkce před nákupem[tady](https://purchase.groupdocs.com/temporary-license/).