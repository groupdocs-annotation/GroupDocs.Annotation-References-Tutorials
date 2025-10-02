---
"description": "Naučte se, jak bezproblémově integrovat funkce anotace dokumentů do vašich .NET aplikací pomocí GroupDocs.Annotation for .NET."
"linktitle": "Generovat náhled bez komentářů"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Generovat náhled bez komentářů"
"url": "/cs/net/advanced-usage/generate-preview-without-comments/"
type: docs
"weight": 14
---

# Generovat náhled bez komentářů

## Zavedení
GroupDocs.Annotation pro .NET je výkonný nástroj, který umožňuje vývojářům bezproblémově začlenit funkce anotací do jejich .NET aplikací. Ať už pracujete na systému pro správu dokumentů, platformě pro spolupráci nebo jakékoli jiné aplikaci vyžadující funkce anotací dokumentů, GroupDocs.Annotation poskytuje komplexní sadu nástrojů pro vylepšení funkčnosti vaší aplikace.
## Předpoklady
Než se pustíte do používání GroupDocs.Annotation pro .NET, ujistěte se, že máte nastaveny následující předpoklady:
### 1. Nainstalujte GroupDocs.Annotation pro .NET
Pro začátek si musíte stáhnout a nainstalovat GroupDocs.Annotation pro .NET. Odkaz ke stažení najdete [zde](https://releases.groupdocs.com/annotation/net/)Pro hladký průběh instalace postupujte podle pokynů k instalaci uvedených v dokumentaci.
### 2. Získejte licenci
GroupDocs.Annotation pro .NET vyžaduje licenci pro komerční použití. Licenci můžete získat od [zde](https://purchase.groupdocs.com/buy) nebo se rozhodnout pro dočasnou licenci [zde](https://purchase.groupdocs.com/temporary-license/) pro účely testování.
### 3. Znalost .NET Frameworku
Základní znalost .NET Frameworku a programovacího jazyka C# je nezbytná pro efektivní využití GroupDocs.Annotation pro .NET.

## Importovat jmenné prostory
Nyní, když jste nastavili předpoklady, importujme potřebné jmenné prostory do vaší aplikace .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

Postupujte podle těchto podrobných pokynů k vygenerování náhledu bez komentářů pomocí nástroje GroupDocs.Annotation pro .NET:
## Krok 1: Inicializace anotátoru
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## Krok 2: Konfigurace možností náhledu
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## Krok 3: Zadejte formát náhledu a čísla stránek
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## Krok 4: Zakázat vykreslování komentářů
```csharp
    previewOptions.RenderComments = false;
```
## Krok 5: Vytvoření náhledu
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
Jakmile budete postupovat podle těchto kroků, vaše aplikace .NET bude schopna vygenerovat náhled zadaných stránek z dokumentu bez vykreslování komentářů.

## Závěr
Začlenění funkcí anotací do vašich .NET aplikací nebylo díky GroupDocs.Annotation pro .NET nikdy snazší. Dodržováním kroků popsaných v tomto tutoriálu můžete bezproblémově integrovat funkce anotací dokumentů do vašich aplikací, a vylepšit tak spolupráci a správu dokumentů.
## Často kladené otázky
### Je GroupDocs.Annotation pro .NET kompatibilní se všemi formáty dokumentů?
GroupDocs.Annotation pro .NET podporuje širokou škálu formátů dokumentů, včetně PDF, DOCX, PPTX, XLSX a dalších.
### Mohu si přizpůsobit vzhled anotací generovaných pomocí GroupDocs.Annotation pro .NET?
Ano, GroupDocs.Annotation pro .NET nabízí rozsáhlé možnosti přizpůsobení, které vám umožňují přizpůsobit vzhled anotací potřebám vaší aplikace.
### Podporuje GroupDocs.Annotation pro .NET spolupráci více uživatelů?
Ano, GroupDocs.Annotation pro .NET nabízí funkce pro spolupráci anotací, které umožňují více uživatelům současně anotovat dokumenty.
### Je k dispozici technická podpora pro GroupDocs.Annotation pro .NET?
Ano, technická podpora pro GroupDocs.Annotation pro .NET je k dispozici prostřednictvím [fórum podpory](https://forum.groupdocs.com/c/annotation/10).
### Mohu si před zakoupením vyzkoušet GroupDocs.Annotation pro .NET zdarma?
Ano, funkce GroupDocs.Annotation pro .NET si můžete prohlédnout stažením bezplatné zkušební verze. [zde](https://releases.groupdocs.com/).