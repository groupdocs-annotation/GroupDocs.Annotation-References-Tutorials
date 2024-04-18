---
title: Přidejte do dokumentu anotaci elipsy
linktitle: Přidejte do dokumentu anotaci elipsy
second_title: GroupDocs.Annotation .NET API
description: Naučte se přidávat elipsové anotace do dokumentů v .NET pomocí GroupDocs.Annotation. Vylepšete spolupráci a komunikaci bez námahy.
type: docs
weight: 13
url: /cs/net/unlocking-annotation-power/add-ellipse-annotation/
---
## Úvod
V tomto kurzu se naučíte, jak přidat elipsovou anotaci do dokumentu pomocí GroupDocs.Annotation for .NET. Tento průvodce vás krok za krokem provede celým procesem a zajistí, že každému kroku jasně porozumíte.
## Předpoklady
Než začnete, ujistěte se, že máte následující:
1.  GroupDocs.Annotation pro .NET: Ujistěte se, že jste si stáhli a nainstalovali GroupDocs.Annotation pro .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/annotation/net/).
2. IDE (Integrated Development Environment): K zápisu a spuštění kódu budete potřebovat IDE nainstalované ve vašem systému, jako je Visual Studio.

## Import jmenných prostorů
Nejprve do projektu importujte potřebné jmenné prostory:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Nastavte výstupní cestu
Definujte výstupní cestu, kam bude dokument s poznámkami uložen:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Inicializujte anotátor
Inicializujte anotátor zadáním cesty vstupního dokumentu:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 3: Vytvořte elipsovou anotaci
 Vytvořte instanci souboru`EllipseAnnotation` třídy a nastavte její vlastnosti:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
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
## Krok 4: Přidejte anotaci
Přidejte do dokumentu anotaci elipsy:
```csharp
annotator.Add(ellipse);
```
## Krok 5: Uložte dokument
Uložte dokument s poznámkami do výstupní cesty:
```csharp
annotator.Save(outputPath);
```

## Závěr
Gratulujeme! Úspěšně jste přidali elipsovou anotaci do dokumentu pomocí GroupDocs.Annotation for .NET. Tuto funkci nyní můžete integrovat do svých aplikací .NET a zlepšit tak spolupráci na dokumentech a komunikaci.
## FAQ
### Mohu upravit vzhled elipsové anotace?
Ano, můžete přizpůsobit různé vlastnosti, jako je barva pozadí, barva ohraničení, neprůhlednost atd., podle vašich požadavků.
### Je GroupDocs.Annotation for .NET kompatibilní se všemi formáty dokumentů?
GroupDocs.Annotation for .NET podporuje širokou škálu formátů dokumentů včetně PDF, DOCX, PPTX, XLSX a dalších.
### Mohu k jednomu dokumentu přidat více anotací?
Ano, do jednoho dokumentu můžete přidat více anotací včetně elips, obdélníků, textu atd.
### Je k dispozici zkušební verze pro účely testování?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[tady](https://releases.groupdocs.com/) zhodnotit jeho vlastnosti.
### Kde mohu získat technickou podporu pro GroupDocs.Annotation pro .NET?
 Technickou podporu můžete získat na fóru komunity GroupDocs.Annotation[tady](https://forum.groupdocs.com/c/annotation/10).