---
"date": "2025-05-06"
"description": "Lär dig hur du effektivt sparar endast kommenterade sidor i en PDF med GroupDocs.Annotation för .NET. Förbättra dokumenthantering och samarbete med den här detaljerade guiden."
"title": "Hur man sparar kommenterade sidor i PDF med GroupDocs.Annotation för .NET"
"url": "/sv/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
type: docs
"weight": 1
---

# Hur man sparar kommenterade sidor i PDF med GroupDocs.Annotation för .NET

## Introduktion

Har du svårt att spara specifika kommenterade sidor från dina PDF-dokument? Den här omfattande guiden visar hur du effektivt kan uppnå detta med GroupDocs.Annotation för .NET. Genom att utnyttja annoteringsfunktioner kan du effektivisera dokumenthanteringen och förbättra samarbetet genom att fokusera på relevant innehåll.

den här handledningen lär du dig:
- Konfigurera din utvecklingsmiljö med GroupDocs.Annotation
- Lägga till olika typer av anteckningar
- Spara endast kommenterade sidor effektivt

Redo att börja? Låt oss se till att du har allt klart.

### Förkunskapskrav

Innan du börjar, se till att du har följande:
- **.NET Framework** (version 4.6 eller senare) eller **.NET Core/5+**
- En kodredigerare som Visual Studio
- Grundläggande kunskaper om projektuppsättning i C# och .NET

## Konfigurera GroupDocs.Annotation för .NET

För att börja använda GroupDocs.Annotation, installera det via NuGet.

**NuGet-pakethanterarkonsolen**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET CLI**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Licensförvärv

GroupDocs erbjuder en gratis provperiod för att utforska deras programvara fullt ut. För längre tids användning, köp en licens eller begär en tillfällig:
- **Gratis provperiod**Utforska funktioner utan begränsningar under en inledande period.
- **Tillfällig licens**Använd GroupDocs.Annotation tillfälligt i produktion.
- **Köpa**Säkra dina långsiktiga behov med en kommersiell licens.

När biblioteket är installerat, initiera det enligt följande:

```csharp
using GroupDocs.Annotation;

// Grundläggande inställningar för att ladda och kommentera dokument
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## Implementeringsguide

### Lägga till anteckningar

#### Översikt

Anteckningar hjälper till att markera viktiga områden i ditt dokument. Låt oss utforska att lägga till en `AreaAnnotation` och en `EllipseAnnotation`.

**Steg 1: Skapa områdesannotering**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// Definiera områdesannoteringen
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Position och storlek
    BackgroundColor = 65535,                // ARGB-färgvärde för högdagrar
    PageNumber = 1                          // Specifikt sidnummer
};
```

De `AreaAnnotation` markerar ett rektangulärt område i dokumentet. Anpassa dess position (`Box`) och bakgrundsfärg.

**Steg 2: Skapa ellipsannotering**

```csharp
// Definiera ellipsannoteringen
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Position och storlek
    BackgroundColor = 123456,                // ARGB-färgvärde för högdagrar
    PageNumber = 1                           // Specifikt sidnummer
};
```

De `EllipseAnnotation` låter dig rita en oval form på dokumentet. Justera position och dimensioner med hjälp av `Box` egendom.

**Steg 3: Lägg till anteckningar**

```csharp
// Lägga till anteckningar i Annotator-instansen
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

Använda `Add` metod, inkludera flera typer av annoteringar. Detta steg lägger till både `AreaAnnotation` och `EllipseAnnotation`.

### Spara endast kommenterade sidor

#### Översikt

Om du bara vill spara sidor som innehåller anteckningar, konfigurera dina sparalternativ därefter.

**Steg 4: Spara kommenterade sidor**

```csharp
using GroupDocs.Annotation.Options;

// Konfigurera sparalternativ för att endast inkludera kommenterade sidor
annotator.Save("path/to/output/document.pdf\