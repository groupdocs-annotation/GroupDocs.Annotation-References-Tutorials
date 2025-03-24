---
title: Přidejte do dokumentu anotaci se šipkou
linktitle: Přidejte do dokumentu anotaci se šipkou
second_title: GroupDocs.Annotation .NET API
description: Naučte se přidávat do dokumentů anotace pomocí šipek pomocí GroupDocs.Annotation for .NET. Vylepšete přehlednost dokumentů a interaktivitu bez námahy.
weight: 11
url: /cs/net/unlocking-annotation-power/add-arrow-annotation/
---
## Úvod
V tomto tutoriálu vás provedeme procesem přidávání anotací šipek do dokumentů pomocí GroupDocs.Annotation for .NET. Šipkové anotace jsou užitečné pro určování směru nebo ukazování na konkrétní prvky v dokumentu.
## Předpoklady
Než začnete, ujistěte se, že máte následující:
1.  GroupDocs.Annotation for .NET: Nainstalujte knihovnu GroupDocs.Annotation pro .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/annotation/net/).
2. Vývojové prostředí: Ujistěte se, že máte vývojové prostředí nastavené pro vývoj .NET, včetně sady Visual Studio nebo jakéhokoli jiného preferovaného IDE.

## Import jmenných prostorů
Nejprve musíte importovat potřebné jmenné prostory pro přístup k požadovaným třídám a metodám pro anotaci.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Inicializujte anotátor
Inicializujte anotátor zadáním cesty k souboru vstupního dokumentu.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 2: Vytvořte anotaci se šipkou
Vytvořte instanci třídy ArrowAnnotation a definujte její vlastnosti, jako je poloha, zpráva, neprůhlednost, barva pera, styl, šířka atd.
```csharp
	ArrowAnnotation arrow = new ArrowAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		CreatedOn = DateTime.Now,
		Message = "This is arrow annotation",
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
 Přidejte do dokumentu anotaci šipky pomocí`Add` metoda anotátora.
```csharp
	annotator.Add(arrow);
```
## Krok 4: Uložte dokument
Uložte dokument s poznámkami do zadané výstupní cesty.
```csharp
	annotator.Save(outputPath);
}
```
## Krok 5: Zobrazení potvrzení
Zobrazte potvrzovací zprávu o úspěšném uložení dokumentu.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Nyní jste úspěšně přidali anotaci šipky do dokumentu pomocí GroupDocs.Annotation for .NET.

## Závěr
tomto tutoriálu jsme se zabývali procesem přidávání anotací šipek do dokumentů pomocí GroupDocs.Annotation pro .NET. Dodržením těchto kroků můžete své dokumenty vylepšit pomocí jasných směrových ukazatelů, díky nimž budou informativnější a poutavější.
## FAQ
### Mohu přizpůsobit vzhled anotace šipky?
Ano, můžete přizpůsobit různé vlastnosti, jako je barva, styl, šířka a neprůhlednost, aby vyhovovaly vašim preferencím a požadavkům na dokument.
### Je GroupDocs.Annotation kompatibilní se všemi formáty dokumentů?
GroupDocs.Annotation podporuje širokou škálu formátů dokumentů včetně PDF, DOCX, PPTX, XLSX a dalších.
### Mohu přidávat anotace programově pomocí GroupDocs.Annotation?
Ano, GroupDocs.Annotation poskytuje rozhraní API, která umožňují programově přidávat, upravovat a odstraňovat anotace z dokumentů.
### Nabízí GroupDocs.Annotation bezplatnou zkušební verzi?
 Ano, můžete si GroupDocs.Annotation vyzkoušet zdarma stažením z[tady](https://releases.groupdocs.com/).
### Kde mohu získat technickou podporu pro GroupDocs.Annotation?
Pro technickou podporu a pomoc můžete navštívit fórum GroupDocs.Annotation[tady](https://forum.groupdocs.com/c/annotation/10).