---
"date": "2025-05-06"
"description": "Lär dig hur du skapar koncisa och relevanta dokumentförhandsvisningar från specifika kalkylbladskolumner med GroupDocs.Annotation för .NET. Perfekt för att effektivisera arbetsflöden inom dataanalys och IT-hantering."
"title": "Generera riktade förhandsvisningar av Excel-ark med GroupDocs.Annotation .NET"
"url": "/sv/net/document-preview/groupdocs-annotation-net-create-previews-worksheet-columns/"
"weight": 1
---

# Generera riktade förhandsvisningar av Excel-ark med GroupDocs.Annotation .NET
## Guide för förhandsgranskning av dokument
### Introduktion
Vill du förbättra tydligheten i din dokumentbehandling genom att fokusera på specifika datapunkter? Oavsett om du är en utvecklare som skapar dataanalysverktyg, en IT-proffs som hanterar dokument eller någon annan som är intresserad av att effektivisera arbetsflöden, kan riktade dokumentförhandsgranskningar spara tid och förbättra effektiviteten. Den här handledningen guidar dig genom att använda GroupDocs.Annotation för .NET för att generera förhandsgranskningar från valda kalkylbladskolumner, vilket säkerställer att dina resultat är koncisa och relevanta.

#### Vad du kommer att lära dig:
- Så här konfigurerar du GroupDocs.Annotation för .NET
- Generera förhandsvisningar med angivna kalkylbladskolumner
- Konfigurera förhandsgranskningsalternativ för optimal utdata
- Praktiska tillämpningar av den här funktionen i verkliga scenarier

Låt oss börja med att granska de nödvändiga förutsättningarna innan du börjar implementera den här lösningen.
## Förkunskapskrav
Innan du börjar implementera, se till att du har följande:

### Nödvändiga bibliotek och versioner:
- **GroupDocs.Annotation för .NET**Version 25.4.0 eller senare krävs.

### Krav för miljöinstallation:
- En utvecklingsmiljö med .NET Framework eller .NET Core installerat.

### Kunskapsförkunskapskrav:
- Grundläggande förståelse för C#-programmering
- Bekantskap med fil-I/O-operationer i .NET
## Konfigurera GroupDocs.Annotation för .NET
För att komma igång behöver du installera biblioteket GroupDocs.Annotation. Så här gör du med olika pakethanterare:

**NuGet-pakethanterarkonsolen**
```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET CLI**
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Steg för att förvärva licens:
- **Gratis provperiod**Ladda ner en testversion från [GroupDocs webbplats](https://releases.groupdocs.com/annotation/net/) för att testa funktioner.
- **Tillfällig licens**Skaffa en tillfällig licens för fullständig åtkomst under utvecklingen på [Sida för tillfällig licens](https://purchase.groupdocs.com/temporary-license/).
- **Köpa**För produktionsbruk, köp en licens via [GroupDocs köpsida](https://purchase.groupdocs.com/buy).
### Grundläggande initialisering och installation med C#:
Så här kan du konfigurera din miljö för att börja arbeta med GroupDocs.Annotation för .NET.
```csharp
using System;
using GroupDocs.Annotation;
// Initiera Annotator-objektet med en dokumentsökväg.
string inputFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.xlsx";
Annotator annotator = new Annotator(inputFilePath);
```
Nu när du är klar kan vi gå vidare till att generera förhandsvisningar från specifika kalkylbladskolumner.
## Implementeringsguide
Den här guiden guidar dig genom implementeringen av funktionen för att generera dokumentförhandsgranskningar med angivna kalkylbladskolumner. Varje avsnitt fokuserar på en specifik aspekt av implementeringsprocessen.
### Generera dokumentförhandsvisningar från specifika kalkylbladskolumner
**Översikt**Den här funktionen låter utvecklare skapa dokumentförhandsgranskningar som bara inkluderar valda kolumner från ett Excel-kalkylblad, vilket förbättrar både prestanda och relevans.
#### Steg 1: Definiera förhandsgranskningsalternativ
Börja med att ställa in din `PreviewOptions`Detta avgör hur och var dina förhandsgranskningsfiler sparas.
```csharp
using System.IO;
using GroupDocs.Annotation.Options;
string outputDirectoryPath = "YOUR_OUTPUT_DIRECTORY";
PreviewOptions previewOptions = new PreviewOptions(pageNumber => 
    new FileStream(Path.Combine(outputDirectoryPath, $"cells_page{pageNumber}.png"), FileMode.Create),
    (number, stream) => stream.Dispose());
```
**Förklaring**: Den `PreviewOptions` Konstruktorn tar två delegater. Den första anger filsökvägen för varje sidas förhandsgranskningsbild. Den andra säkerställer att strömmar kasseras korrekt efter användning.
#### Steg 2: Ange kalkylbladskolumner
Välj vilka kolumner från ditt kalkylblad du vill inkludera i förhandsgranskningarna genom att lägga till dem i `WorksheetColumns`.
```csharp
// Inkludera specifika kolumner från Ark1.
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1\