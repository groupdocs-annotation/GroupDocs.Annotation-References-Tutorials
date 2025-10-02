---
"description": "Lär dig hur du sömlöst laddar anpassade teckensnitt i GroupDocs.Annotation för .NET för att förbättra dokumentannotering. Följ våra steg-för-steg-anvisningar för enkel integration."
"linktitle": "Laddar anpassade teckensnitt"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Laddar anpassade teckensnitt"
"url": "/sv/net/advanced-usage/loading-custom-fonts/"
type: docs
"weight": 20
---

# Laddar anpassade teckensnitt

## Introduktion
GroupDocs.Annotation för .NET är ett kraftfullt bibliotek som gör det möjligt för utvecklare att enkelt lägga till annoteringsfunktioner i sina .NET-applikationer. En av de viktigaste funktionerna är möjligheten att ladda anpassade teckensnitt, vilket möjliggör förbättrad anpassning och flexibilitet i dokumentannotering.
## Förkunskapskrav
Innan du fortsätter med handledningen, se till att du har följande förkunskaper:
1. GroupDocs.Annotation för .NET-biblioteket: Ladda ner och installera biblioteket från [här](https://releases.groupdocs.com/annotation/net/).
2. .NET-utvecklingsmiljö: Se till att du har en arbetsmiljö konfigurerad för .NET-utveckling.
3. Åtkomst till anpassade teckensnitt: Förbered de anpassade teckensnitt som du vill ladda in i ditt program.

## Importera namnrymder
Importera de namnrymder som krävs för att använda GroupDocs i ditt .NET-projekt.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Steg 1: Instansiera annotatorobjekt
Skapa en instans av `Annotator` klassen genom att ange sökvägen till indata-PDF-dokumentet tillsammans med de anpassade teckensnittskatalogerna:
```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions { FontDirectories = new List<string> { Constants.GetFontDirectory() } }))
{
    // Din kod för vidare operationer kommer att placeras här
}
```
## Steg 2: Konfigurera förhandsgranskningsalternativ
Definiera förhandsgranskningsalternativen för att ange hur dokumentförhandsgranskningarna ska genereras. Du kan ställa in alternativ som förhandsgranskningsformat, sidnummer etc.:
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine("Your Document Directory", $"result_with_font_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
```
## Steg 3: Generera dokumentförhandsvisningar
Använd `GeneratePreview` metod för `Document` egenskap för att generera förhandsvisningar med anpassade teckensnitt:
```csharp
annotator.Document.GeneratePreview(previewOptions);
```
## Steg 4: Visa utdataväg
Slutligen, visa ett meddelande som anger att dokumentförhandsgranskningarna har genererats tillsammans med sökvägen till utdatakatalogen:
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {"Your Document Directory"}.");
```

## Slutsats
Sammanfattningsvis ger laddning av anpassade teckensnitt i GroupDocs.Annotation för .NET utvecklare flexibiliteten att anpassa dokumentannoteringar efter sina behov. Genom att följa stegen som beskrivs i den här handledningen kan du sömlöst integrera anpassade teckensnitt i dina .NET-applikationer och förbättra annoteringsupplevelsen för användarna.
## Vanliga frågor
### Kan jag ladda flera anpassade teckensnitt samtidigt?
Ja, du kan ange flera teckensnittskataloger när du instansierar `Annotator` objekt.
### Finns det några begränsningar för vilka typer av teckensnitt som stöds?
GroupDocs.Annotation för .NET stöder ett brett utbud av teckensnitt, inklusive TrueType-teckensnitt (.ttf) och OpenType-teckensnitt (.otf).
### Kan jag dynamiskt ändra de laddade teckensnitten under körning?
Ja, du kan dynamiskt ändra teckensnittskatalogerna och ladda om dokumentanteckningarna efter behov.
### Har GroupDocs.Annotation stöd för inbäddning av teckensnitt i utdatadokument?
Ja, du kan bädda in anpassade teckensnitt i utdatadokumenten för att säkerställa enhetlig rendering på olika plattformar.
### Finns det något sätt att hantera typsnittslicenser i applikationen?
GroupDocs.Annotation erbjuder alternativ för att hantera typsnittslicenser, inklusive tillfälliga licenser för utvärderingsändamål.