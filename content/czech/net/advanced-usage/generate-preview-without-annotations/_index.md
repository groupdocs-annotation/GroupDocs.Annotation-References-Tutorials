---
title: Generovat náhled bez poznámek
linktitle: Generovat náhled bez poznámek
second_title: GroupDocs.Annotation .NET API
description: Vylepšete spolupráci na dokumentech a anotaci v rámci aplikací .NET pomocí GroupDocs.Annotation pro .NET. Pomocí této výkonné knihovny můžete snadno anotovat, označovat a kontrolovat dokumenty.
type: docs
weight: 13
url: /cs/net/advanced-usage/generate-preview-without-annotations/
---
## Úvod
dnešní digitální době je efektivní spolupráce na dokumentech klíčem k produktivitě a úspěchu. Ať už pracujete na projektu se členy týmu roztroušenými po celém světě nebo spolupracujete s klienty na důležitých smlouvách, schopnost bezproblémově anotovat a revidovat dokumenty je zásadní. S GroupDocs.Annotation for .NET můžete posunout spolupráci na dokumentech na další úroveň, což umožňuje snadnou anotaci, označování a kontrolu přímo ve vašich aplikacích .NET.
## Předpoklady
Než se ponoříte do světa anotací dokumentů pomocí GroupDocs.Annotation pro .NET, musíte mít splněno několik předpokladů:
### 1. Nainstalujte GroupDocs.Annotation for .NET
 V první řadě si budete muset stáhnout a nainstalovat GroupDocs.Annotation for .NET. Odkaz ke stažení najdete[tady](https://releases.groupdocs.com/annotation/net/). Postupujte podle pokynů k instalaci a nastavte knihovnu ve vašem prostředí .NET.
### 2. Získejte licenci (volitelné)
Přestože GroupDocs.Annotation for .NET nabízí bezplatnou zkušební verzi, možná budete chtít zvážit získání licence pro plný přístup k jejím funkcím. Můžete si zakoupit licenci[tady](https://purchase.groupdocs.com/buy) nebo požádat o dočasnou licenci[tady](https://purchase.groupdocs.com/temporary-license/) pro testovací účely.
### 3. Znalost C# a .NET Development
Chcete-li co nejlépe využít GroupDocs.Annotation pro .NET, je užitečné mít základní znalosti o vývoji C# a .NET. To vám umožní bezproblémově integrovat knihovnu do vašich stávajících aplikací a pracovních postupů.
### 4. Nainstalujte prohlížeč PDF
Vzhledem k tomu, že GroupDocs.Annotation for .NET pracuje s dokumenty PDF, budete potřebovat prohlížeč PDF nainstalovaný ve vašem systému, abyste si mohli prohlédnout anotované dokumenty. Postačí Adobe Acrobat Reader nebo jakýkoli jiný prohlížeč PDF.

## Import jmenných prostorů
Než budete moci začít anotovat dokumenty, budete muset do svého projektu .NET importovat potřebné jmenné prostory. To vám umožní přístup ke třídám a metodám poskytovaným GroupDocs.Annotation pro .NET.

```csharp
using System.IO;
using GroupDocs.Annotation.Options;
```

Nyní, když máte vše nastaveno, vygenerujeme náhled dokumentu bez jakýchkoli poznámek. Chcete-li to provést, postupujte takto:
## Krok 1: Inicializujte anotátor
 Nejprve vytvořte instanci souboru`Annotator` třídy, předání cesty k dokumentu, který chcete anotovat.
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
```
## Krok 2: Nakonfigurujte možnosti náhledu
Dále nakonfigurujte možnosti náhledu podle vašich požadavků. Můžete určit čísla stránek, která chcete zahrnout do náhledu, formát náhledu (např. PNG) a zda se mají vykreslit anotace.
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] {1, 2, 3, 4, 5, 6};
    previewOptions.RenderAnnotations = false;
```
## Krok 3: Vygenerujte náhled
 Nakonec vygenerujte náhled pomocí`GeneratePreview` metoda`Document` třídy a předá nakonfigurované možnosti náhledu.
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
Pomocí těchto jednoduchých kroků můžete pomocí GroupDocs.Annotation for .NET vygenerovat náhled dokumentu bez anotací.

## Závěr
Na závěr, GroupDocs.Annotation for .NET poskytuje výkonné řešení pro spolupráci na dokumentech a anotaci v rámci aplikací .NET. Podle kroků uvedených v tomto kurzu můžete do svých projektů bez problémů integrovat možnosti anotací dokumentů a zlepšit tak spolupráci a produktivitu.
## FAQ
### Otázka: Mohu použít GroupDocs.Annotation pro .NET s jinými formáty dokumentů kromě PDF?
Ano, GroupDocs.Annotation for .NET podporuje různé formáty dokumentů, včetně DOCX, XLSX, PPTX a dalších.
### Otázka: Je GroupDocs.Annotation for .NET kompatibilní s .NET Core?
Ano, GroupDocs.Annotation for .NET je kompatibilní s prostředím .NET Framework i .NET Core.
### Otázka: Nabízí GroupDocs.Annotation for .NET přizpůsobitelné nástroje pro poznámky?
Ano, GroupDocs.Annotation for .NET poskytuje řadu nástrojů pro poznámky, které lze přizpůsobit tak, aby vyhovovaly vašim specifickým požadavkům.
### Otázka: Mohu integrovat GroupDocs.Annotation for .NET do svých webových aplikací?
Ano, GroupDocs.Annotation for .NET lze integrovat do desktopových i webových aplikací a poskytuje bezproblémovou spolupráci na dokumentech.
### Otázka: Existuje komunitní fórum, kde mohu získat podporu a pomoc s GroupDocs.Annotation pro .NET?
 Ano, podporu a pomoc najdete na fóru GroupDocs.Annotation[tady](https://forum.groupdocs.com/c/annotation/10).