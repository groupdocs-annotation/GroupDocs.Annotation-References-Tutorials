---
"description": "Naučte se, jak přidávat elipsové anotace do dokumentů v .NET pomocí GroupDocs.Annotation. Vylepšete spolupráci a komunikaci bez námahy."
"linktitle": "Přidání elipsovité anotace do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Přidání elipsovité anotace do dokumentu"
"url": "/cs/net/unlocking-annotation-power/add-ellipse-annotation/"
type: docs
"weight": 13
---

# Přidání elipsovité anotace do dokumentu

## Zavedení
V tomto tutoriálu se naučíte, jak přidat do dokumentu anotaci ve tvaru elipsy pomocí nástroje GroupDocs.Annotation pro .NET. Tento podrobný návod vás provede celým procesem a zajistí, že každému kroku jasně porozumíte.
## Předpoklady
Než začnete, ujistěte se, že máte následující:
1. GroupDocs.Annotation pro .NET: Ujistěte se, že jste si stáhli a nainstalovali GroupDocs.Annotation pro .NET. Můžete si ho stáhnout z [zde](https://releases.groupdocs.com/annotation/net/).
2. IDE (integrované vývojové prostředí): Pro napsání a spuštění kódu budete potřebovat nainstalované IDE, například Visual Studio.

## Importovat jmenné prostory
Nejprve importujte potřebné jmenné prostory do projektu:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Nastavení výstupní cesty
Definujte výstupní cestu, kam bude uložen anotovaný dokument:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Inicializace anotátoru
Inicializujte anotátor zadáním vstupní cesty k dokumentu:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 3: Vytvořte anotaci elipsy
Vytvořte instanci `EllipseAnnotation` třídu a nastavte její vlastnosti:
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
## Krok 4: Přidání anotace
Přidejte do dokumentu anotaci elipsy:
```csharp
annotator.Add(ellipse);
```
## Krok 5: Uložení dokumentu
Uložte anotovaný dokument do výstupní cesty:
```csharp
annotator.Save(outputPath);
```

## Závěr
Gratulujeme! Úspěšně jste přidali elipsovitou anotaci do dokumentu pomocí GroupDocs.Annotation pro .NET. Nyní můžete tuto funkci integrovat do svých .NET aplikací a vylepšit tak spolupráci a komunikaci v oblasti dokumentů.
## Často kladené otázky
### Mohu si přizpůsobit vzhled anotace elipsy?
Ano, můžete si přizpůsobit různé vlastnosti, jako je barva pozadí, barva ohraničení, neprůhlednost atd., podle svých požadavků.
### Je GroupDocs.Annotation pro .NET kompatibilní se všemi formáty dokumentů?
GroupDocs.Annotation pro .NET podporuje širokou škálu formátů dokumentů, včetně PDF, DOCX, PPTX, XLSX a dalších.
### Mohu do jednoho dokumentu přidat více anotací?
Ano, do jednoho dokumentu můžete přidat více anotací, včetně elips, obdélníků, textu atd.
### Je k dispozici zkušební verze pro testovací účely?
Ano, můžete si stáhnout bezplatnou zkušební verzi z [zde](https://releases.groupdocs.com/) aby zhodnotili jeho vlastnosti.
### Kde mohu získat technickou podporu pro GroupDocs.Annotation pro .NET?
Technickou podporu můžete získat na komunitním fóru GroupDocs.Annotation. [zde](https://forum.groupdocs.com/c/annotation/10).