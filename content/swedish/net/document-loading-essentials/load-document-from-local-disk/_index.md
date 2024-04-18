---
title: Ladda dokument från lokal disk
linktitle: Ladda dokument från lokal disk
second_title: GroupDocs.Annotation .NET API
description: Lås upp kraften i dokumentkommentarer med GroupDocs.Annotation för .NET. Integrera annoteringsfunktioner sömlöst i dina .NET-applikationer.
type: docs
weight: 13
url: /sv/net/document-loading-essentials/load-document-from-local-disk/
---
## Introduktion
Att låsa upp potentialen för dokumentkommentarer har aldrig varit enklare med GroupDocs.Annotation för .NET. Detta kraftfulla verktyg ger utvecklare möjlighet att integrera robusta annoteringsfunktioner sömlöst i sina .NET-applikationer. I den här omfattande guiden går vi igenom processen att använda GroupDocs.Annotation för .NET för att kommentera dokument steg för steg. Oavsett om du är en erfaren utvecklare eller precis har börjat, kommer den här handledningen att utrusta dig med kunskapen för att förbättra dokumentsamarbetet och effektivisera ditt arbetsflöde.
## Förutsättningar
Innan du dyker in i dokumentkommentarer med GroupDocs.Annotation för .NET, se till att du har följande förutsättningar:
1. Grundläggande kunskaper i C#: Bekantskap med C# programmeringsspråkets grunder är avgörande.
2. Installation av GroupDocs.Annotation for .NET: Ladda ner och installera GroupDocs.Annotation for .NET från[här](https://releases.groupdocs.com/annotation/net/).
3. Utvecklingsmiljö: Konfigurera en utvecklingsmiljö med Visual Studio eller någon kompatibel IDE.

## Importera namnområden
För att börja kommentera dokument med GroupDocs.Annotation for .NET, importera de nödvändiga namnrymden till ditt projekt:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Steg 1: Ladda dokument från lokal disk
Först måste du ladda dokumentet från din lokala disk. Använd följande kodavsnitt:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Steg 2: Definiera anteckningsområde
Därefter definierar du anteckningsområdet. I det här exemplet skapar vi en AreaAnnotation:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Steg 3: Spara dokument med anteckningar
När du har kommenterat dokumentet sparar du det med anteckningarna:
```csharp
    annotator.Save(outputPath);
}
```
## Steg 4: Visa framgångsmeddelande
Visa slutligen ett framgångsmeddelande med utdatasökvägen:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Slutsats
Sammanfattningsvis erbjuder GroupDocs.Annotation för .NET en robust lösning för att integrera funktioner för dokumentkommentarer i dina .NET-applikationer. Genom att följa denna steg-för-steg-guide kan du enkelt kommentera dokument och förbättra samarbetet i dina projekt.
## FAQ's
### Kan jag prova GroupDocs.Annotation för .NET innan jag köper?
 Ja, du kan ladda ner en gratis testversion från[här](https://releases.groupdocs.com/).
### Var kan jag hitta dokumentation för GroupDocs.Annotation för .NET?
 Du kan komma åt dokumentationen[här](https://reference.groupdocs.com/annotation/net/).
### Hur kan jag få en tillfällig licens för GroupDocs.Annotation för .NET?
 Du kan få en tillfällig licens från[här](https://purchase.groupdocs.com/temporary-license/).
### Finns stöd tillgängligt för GroupDocs.Annotation för .NET?
 Ja, du kan hitta support på GroupDocs-forumet[här](https://forum.groupdocs.com/c/annotation/10).
### Var kan jag köpa GroupDocs.Annotation för .NET?
 Du kan köpa GroupDocs.Annotation för .NET[här](https://purchase.groupdocs.com/buy).