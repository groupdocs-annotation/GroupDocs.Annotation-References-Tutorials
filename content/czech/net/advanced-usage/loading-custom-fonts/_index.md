---
title: Načítání vlastních písem
linktitle: Načítání vlastních písem
second_title: GroupDocs.Annotation .NET API
description: Naučte se, jak plynule načítat vlastní písma v GroupDocs.Annotation pro .NET, abyste vylepšili anotace dokumentů. Pro snadnou integraci postupujte podle našich pokynů krok za krokem.
weight: 20
url: /cs/net/advanced-usage/loading-custom-fonts/
---
## Úvod
GroupDocs.Annotation for .NET je výkonná knihovna, která umožňuje vývojářům snadno přidávat funkce anotací do jejich aplikací .NET. Jednou z klíčových funkcí, které nabízí, je schopnost načítat vlastní písma, což umožňuje lepší přizpůsobení a flexibilitu v anotacích dokumentů.
## Předpoklady
Než budete pokračovat ve výukovém programu, ujistěte se, že máte následující předpoklady:
1.  GroupDocs.Annotation for .NET Library: Stáhněte a nainstalujte knihovnu z[tady](https://releases.groupdocs.com/annotation/net/).
2. Vývojové prostředí .NET: Ujistěte se, že máte nastavené pracovní prostředí pro vývoj .NET.
3. Přístup k vlastním písmům: Připravte si vlastní písma, která chcete načíst do aplikace.

## Import jmenných prostorů
Ve svém projektu .NET importujte potřebné jmenné prostory pro využití GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Krok 1: Vytvořte instanci objektu anotátoru
 Vytvořte instanci souboru`Annotator` třídy poskytnutím cesty ke vstupnímu dokumentu PDF spolu s vlastními adresáři písem:
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    // Zde bude váš kód pro další operace
}
```
## Krok 2: Nakonfigurujte možnosti náhledu
Definujte možnosti náhledu a určete, jak se budou generovat náhledy dokumentů. Můžete nastavit možnosti, jako je formát náhledu, čísla stránek atd.:
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_with_font_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
```
## Krok 3: Vygenerujte náhledy dokumentů
 Využijte`GeneratePreview` metoda`Document` vlastnost pro generování náhledů s vlastními fonty:
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## Krok 4: Zobrazte výstupní cestu
Nakonec zobrazte zprávu o úspěšném vygenerování náhledů dokumentů spolu s cestou k výstupnímu adresáři:
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## Závěr
Závěrem lze říci, že načítání vlastních písem v GroupDocs.Annotation for .NET poskytuje vývojářům flexibilitu při přizpůsobení anotací dokumentů podle jejich požadavků. Podle kroků uvedených v tomto kurzu můžete bez problémů integrovat vlastní písma do aplikací .NET a vylepšit uživatelům práci s poznámkami.
## FAQ
### Mohu načíst více vlastních písem současně?
 Ano, při vytváření instance můžete zadat více adresářů písem`Annotator` objekt.
### Existují nějaká omezení ohledně podporovaných typů písem?
GroupDocs.Annotation for .NET podporuje širokou škálu typů písem, včetně písem TrueType (.ttf) a OpenType (.otf).
### Mohu dynamicky měnit načtená písma za běhu?
Ano, můžete dynamicky upravovat adresáře písem a podle potřeby znovu načítat anotace dokumentu.
### Podporuje GroupDocs.Annotation vkládání písem do výstupních dokumentů?
Ano, do výstupních dokumentů můžete vložit vlastní písma, abyste zajistili konzistentní vykreslování na různých platformách.
### Existuje způsob, jak zvládnout licencování písem v rámci aplikace?
GroupDocs.Annotation poskytuje možnosti pro správu licencování písem, včetně dočasných licencí pro účely hodnocení.