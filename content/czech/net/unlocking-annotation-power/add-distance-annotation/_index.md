---
title: Přidejte do dokumentu anotaci vzdálenosti
linktitle: Přidejte do dokumentu anotaci vzdálenosti
second_title: GroupDocs.Annotation .NET API
description: Zjistěte, jak přidat poznámky vzdálenosti k dokumentům pomocí GroupDocs.Annotation for .NET. Vylepšete spolupráci a komunikaci bez námahy.
weight: 12
url: /cs/net/unlocking-annotation-power/add-distance-annotation/
---

# Přidejte do dokumentu anotaci vzdálenosti

## Úvod
V tomto tutoriálu se naučíte, jak přidat anotaci vzdálenosti k dokumentu pomocí GroupDocs.Annotation for .NET. Chcete-li provést úkol, postupujte takto:
## Předpoklady

Než budete pokračovat, ujistěte se, že máte splněny následující předpoklady:

-  GroupDocs.Annotation for .NET Library: Stáhněte a nainstalujte si knihovnu GroupDocs.Annotation for .NET z[tento odkaz](https://releases.groupdocs.com/annotation/net/).
- Dokument k anotaci: Připravte dokument (např. PDF), ke kterému chcete přidat anotaci vzdálenosti.
- Vývojové prostředí: Nastavte své vývojové prostředí pomocí sady Visual Studio nebo jakéhokoli jiného IDE podle vašeho výběru.

## Import jmenných prostorů

Než začnete, nezapomeňte do kódu zahrnout potřebné jmenné prostory. Tyto jmenné prostory jsou nezbytné pro přístup k požadovaným třídám a metodám.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Krok 1: Inicializujte anotátor

 Začněte inicializací`Annotator` objekt s cestou k dokumentu, který chcete anotovat.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Sem bude umístěn kód anotace
}
```

## Krok 2: Vytvořte anotaci vzdálenosti

 Nyní vytvořte a`DistanceAnnotation` objektu a nakonfigurujte jeho vlastnosti, jako jsou rozměry krabice, zpráva, neprůhlednost, barva pera atd.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
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
    }
};
```

## Krok 3: Přidejte anotaci

 Přidejte vytvořenou anotaci vzdálenosti do dokumentu pomocí`Add` metoda objektu anotátor.

```csharp
annotator.Add(distance);
```

## Krok 4: Uložte dokument

Uložte anotovaný dokument na požadované místo ve vašem systému.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Krok 5: Zobrazení potvrzení

Nakonec zobrazte zprávu potvrzující úspěšné uložení anotovaného dokumentu.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Závěr

Přidávání distančních anotací k dokumentům pomocí GroupDocs.Annotation for .NET je jednoduchý proces. Dodržováním kroků uvedených v tomto kurzu můžete své dokumenty vylepšit cennými anotacemi, což usnadní spolupráci a komunikaci.

## FAQ

### Otázka: Mohu upravit vzhled poznámky vzdálenosti?

Odpověď: Ano, můžete přizpůsobit různé vlastnosti, jako je barva, neprůhlednost, styl čáry atd., aby vyhovovaly vašim požadavkům.

### Otázka: Podporuje GroupDocs.Annotation anotace v různých typech dokumentů?

Odpověď: Ano, GroupDocs.Annotation podporuje poznámky v široké řadě formátů dokumentů včetně PDF, Word, Excel, PowerPoint a dalších.

### Otázka: Je k dispozici bezplatná zkušební verze pro GroupDocs.Annotation?

 Odpověď: Ano, máte přístup k bezplatné zkušební verzi GroupDocs.Annotation z[tento odkaz](https://releases.groupdocs.com/).

### Otázka: Kde najdu dokumentaci k GroupDocs.Annotation pro .NET?

 Odpověď: Můžete se podívat na podrobnou dostupnou dokumentaci[tady](https://tutorials.groupdocs.com/annotation/net/).

### Otázka: Jak mohu získat podporu nebo pomoc s GroupDocs.Annotation?

 Odpověď: Podporu a pomoc můžete vyhledat na fóru komunity GroupDocs.Annotation[tady](https://forum.groupdocs.com/c/annotation/10).