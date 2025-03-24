---
title: Generovat náhled bez komentářů
linktitle: Generovat náhled bez komentářů
second_title: GroupDocs.Annotation .NET API
description: Naučte se, jak bezproblémově integrovat možnosti anotací dokumentů do vašich aplikací .NET pomocí GroupDocs.Annotation for .NET.
weight: 14
url: /cs/net/advanced-usage/generate-preview-without-comments/
---

# Generovat náhled bez komentářů

## Úvod
GroupDocs.Annotation for .NET je výkonný nástroj, který umožňuje vývojářům bezproblémově začlenit funkce anotací do jejich aplikací .NET. Ať už pracujete na systému správy dokumentů, platformě pro spolupráci nebo jakékoli jiné aplikaci vyžadující možnosti anotací dokumentů, GroupDocs.Annotation poskytuje komplexní sadu nástrojů pro vylepšení funkčnosti vaší aplikace.
## Předpoklady
Než se pustíte do používání GroupDocs.Annotation pro .NET, ujistěte se, že máte nastaveny následující předpoklady:
### 1. Nainstalujte GroupDocs.Annotation for .NET
 Chcete-li začít, musíte si stáhnout a nainstalovat GroupDocs.Annotation for .NET. Odkaz ke stažení najdete[tady](https://releases.groupdocs.com/annotation/net/). Pro hladký průběh instalace postupujte podle pokynů k instalaci uvedených v dokumentaci.
### 2. Získejte licenci
 GroupDocs.Annotation for .NET vyžaduje licenci pro komerční použití. Licenci můžete získat od[tady](https://purchase.groupdocs.com/buy) nebo zvolit dočasnou licenci[tady](https://purchase.groupdocs.com/temporary-license/) pro testovací účely.
### 3. Seznámení s .NET Framework
Základní znalost .NET Framework a programovacího jazyka C# je nezbytná pro efektivní využití GroupDocs.Annotation pro .NET.

## Import jmenných prostorů
Nyní, když jste nastavili předpoklady, pojďme importovat potřebné jmenné prostory do vaší .NET aplikace.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

Chcete-li pomocí GroupDocs.Annotation pro .NET vygenerovat náhled bez komentářů, postupujte podle těchto podrobných pokynů:
## Krok 1: Inicializujte anotátor
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## Krok 2: Nakonfigurujte možnosti náhledu
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
## Krok 4: Zakažte vykreslování komentářů
```csharp
    previewOptions.RenderComments = false;
```
## Krok 5: Vygenerujte náhled
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
Jakmile provedete tyto kroky, vaše aplikace .NET bude schopna generovat náhled zadaných stránek z dokumentu bez vykreslování komentářů.

## Závěr
Začlenění anotačních funkcí do vašich aplikací .NET nebylo nikdy jednodušší díky GroupDocs.Annotation pro .NET. Podle kroků uvedených v tomto kurzu můžete bez problémů integrovat možnosti anotací dokumentů do svých aplikací, čímž se zlepší spolupráce a správa dokumentů.
## FAQ
### Je GroupDocs.Annotation for .NET kompatibilní se všemi formáty dokumentů?
GroupDocs.Annotation for .NET podporuje širokou škálu formátů dokumentů, včetně PDF, DOCX, PPTX, XLSX a dalších.
### Mohu upravit vzhled anotací generovaných pomocí GroupDocs.Annotation for .NET?
Ano, GroupDocs.Annotation for .NET poskytuje rozsáhlé možnosti přizpůsobení, které vám umožní upravit vzhled anotací tak, aby vyhovovaly potřebám vaší aplikace.
### Podporuje GroupDocs.Annotation for .NET spolupráci více uživatelů?
Ano, GroupDocs.Annotation for .NET nabízí funkce pro spolupráci anotací, které umožňují více uživatelům anotovat dokumenty současně.
### Je k dispozici technická podpora pro GroupDocs.Annotation pro .NET?
 Ano, technická podpora pro GroupDocs.Annotation pro .NET je k dispozici prostřednictvím[Fórum podpory](https://forum.groupdocs.com/c/annotation/10).
### Mohu GroupDocs.Annotation for .NET vyzkoušet zdarma před nákupem?
 Ano, můžete prozkoumat funkce GroupDocs.Annotation pro .NET stažením bezplatné zkušební verze[tady](https://releases.groupdocs.com/).