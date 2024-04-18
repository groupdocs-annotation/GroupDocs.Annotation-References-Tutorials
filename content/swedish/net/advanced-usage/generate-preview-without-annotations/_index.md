---
title: Skapa förhandsgranskning utan anteckningar
linktitle: Skapa förhandsgranskning utan anteckningar
second_title: GroupDocs.Annotation .NET API
description: Förbättra dokumentsamarbete och anteckningar inom .NET-applikationer med GroupDocs.Annotation för .NET. Kommentera, markera och granska enkelt dokument med detta kraftfulla bibliotek.
type: docs
weight: 13
url: /sv/net/advanced-usage/generate-preview-without-annotations/
---
## Introduktion
dagens digitala tidsålder är effektivt samarbete kring dokument nyckeln till produktivitet och framgång. Oavsett om du arbetar med ett projekt med teammedlemmar utspridda över hela världen eller samarbetar med kunder i viktiga kontrakt, är förmågan att kommentera och granska dokument sömlöst avgörande. Med GroupDocs.Annotation för .NET kan du ta ditt dokumentsamarbete till nästa nivå, vilket möjliggör enkel anteckning, markering och granskning direkt i dina .NET-applikationer.
## Förutsättningar
Innan du dyker in i världen av dokumentkommentarer med GroupDocs.Annotation för .NET, finns det några förutsättningar som du måste ha på plats:
### 1. Installera GroupDocs.Annotation för .NET
 Först och främst måste du ladda ner och installera GroupDocs.Annotation för .NET. Du hittar nedladdningslänken[här](https://releases.groupdocs.com/annotation/net/). Följ installationsinstruktionerna för att ställa in biblioteket i din .NET-miljö.
### 2. Skaffa en licens (valfritt)
Medan GroupDocs.Annotation för .NET erbjuder en gratis provperiod, kanske du vill överväga att skaffa en licens för full tillgång till dess funktioner. Du kan köpa en licens[här](https://purchase.groupdocs.com/buy) eller begära en tillfällig licens[här](https://purchase.groupdocs.com/temporary-license/) för teständamål.
### 3. Kännedom om C# och .NET-utveckling
För att få ut det mesta av GroupDocs.Annotation för .NET är det bra att ha en grundläggande förståelse för C#- och .NET-utveckling. Detta gör att du kan integrera biblioteket sömlöst i dina befintliga applikationer och arbetsflöden.
### 4. Installera en PDF Viewer
Eftersom GroupDocs.Annotation for .NET fungerar med PDF-dokument, behöver du en PDF-visare installerad på ditt system för att förhandsgranska kommenterade dokument. Adobe Acrobat Reader eller någon annan PDF-läsare räcker.

## Importera namnområden
Innan du kan börja kommentera dokument måste du importera de nödvändiga namnområdena till ditt .NET-projekt. Detta ger dig tillgång till klasserna och metoderna som tillhandahålls av GroupDocs.Annotation för .NET.

```csharp
using System.IO;
using GroupDocs.Annotation.Options;
```

Nu när du har allt inställt, låt oss skapa en förhandsgranskning av ett dokument utan några anteckningar. Följ dessa steg för att uppnå detta:
## Steg 1: Initiera Annotator
 Skapa först en instans av`Annotator` klass och skickar sökvägen till dokumentet du vill kommentera.
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
```
## Steg 2: Konfigurera förhandsgranskningsalternativ
Konfigurera sedan förhandsgranskningsalternativen enligt dina krav. Du kan ange sidnumren som du vill inkludera i förhandsgranskningen, förhandsgranskningsformatet (t.ex. PNG) och om anteckningar ska renderas.
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
## Steg 3: Skapa förhandsgranskning
 Till sist, generera förhandsvisningen med hjälp av`GeneratePreview` metod för`Document` klass, passerar de konfigurerade förhandsgranskningsalternativen.
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
Genom att följa dessa enkla steg kan du generera en förhandsvisning av ett dokument utan anteckningar med GroupDocs.Annotation för .NET.

## Slutsats
Sammanfattningsvis tillhandahåller GroupDocs.Annotation for .NET en kraftfull lösning för dokumentsamarbete och annotering inom .NET-applikationer. Genom att följa stegen som beskrivs i denna handledning kan du sömlöst integrera funktioner för dokumentkommentarer i dina projekt, vilket förbättrar samarbetet och produktiviteten.
## FAQ's
### F: Kan jag använda GroupDocs.Annotation för .NET med andra dokumentformat än PDF?
Ja, GroupDocs.Annotation för .NET stöder en mängd olika dokumentformat, inklusive DOCX, XLSX, PPTX och mer.
### F: Är GroupDocs.Annotation for .NET kompatibelt med .NET Core?
Ja, GroupDocs.Annotation för .NET är kompatibel med både .NET Framework- och .NET Core-miljöer.
### F: Erbjuder GroupDocs.Annotation for .NET anpassningsbara anteckningsverktyg?
Ja, GroupDocs.Annotation för .NET tillhandahåller en rad anteckningsverktyg som kan anpassas för att passa dina specifika krav.
### F: Kan jag integrera GroupDocs.Annotation för .NET i mina webbapplikationer?
Ja, GroupDocs.Annotation för .NET kan integreras i både skrivbords- och webbapplikationer, vilket ger sömlösa dokumentsamarbetsmöjligheter.
### F: Finns det ett communityforum där jag kan få support och hjälp med GroupDocs.Annotation för .NET?
 Ja, du kan hitta support och hjälp på forumet GroupDocs.Annotation[här](https://forum.groupdocs.com/c/annotation/10).