---
title: Få alla versionsnycklar på dokument
linktitle: Få alla versionsnycklar på dokument
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du hämtar alla versionsnycklar på ett dokument med GroupDocs.Annotation för .NET. Förbättra dina dokumenthanteringsmöjligheter med detta omfattande.
weight: 16
url: /sv/net/advanced-usage/get-all-version-keys-document/
---
## Introduktion
I dagens snabba digitala värld är effektiv dokumenthantering avgörande för både företag och privatpersoner. Oavsett om du samarbetar i projekt, granskar kontrakt eller helt enkelt organiserar dina filer, kan ha rätt verktyg göra stor skillnad. GroupDocs.Annotation för .NET erbjuder en omfattande lösning för att kommentera och manipulera dokument i .NET-applikationer. I den här handledningen kommer vi att undersöka hur man kan utnyttja GroupDocs.Annotation för .NET för att hämta alla versionsnycklar på ett dokument.
## Förutsättningar
Innan vi dyker in i handledningen, se till att du har följande förutsättningar:
### 1. Installera GroupDocs.Annotation för .NET
 För att komma igång måste du ladda ner och installera GroupDocs.Annotation för .NET. Du kan hämta den senaste versionen från[nedladdningslänk](https://releases.groupdocs.com/annotation/net/).
### 2. Skaffa API-uppgifter
Se till att du har de nödvändiga API-uppgifterna för att komma åt GroupDocs.Annotation för .NET-funktioner.

## Importera nödvändiga namnområden
Innan du fortsätter, se till att importera de nödvändiga namnrymden till ditt projekt:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
```

Låt oss dela upp processen för att få alla versionsnycklar på ett dokument i enkla steg:
## Steg 1: Initiera annotatorobjektet
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf"))
{
    // Koden går här
}
```
 Initiera`Annotator` objekt med sökvägen till dokumentet du vill arbeta med.
## Steg 2: Hämta versionsnycklar
```csharp
List<object> versionKeys = annotator.GetVersionsList();
```
 Åberopa`GetVersionsList()` metod på`Annotator` objekt för att hämta alla versionsnycklar som är associerade med dokumentet. Denna metod returnerar en lista med versionsnycklar.

## Slutsats
GroupDocs.Annotation för .NET förenklar dokumentkommentarer och manipuleringsuppgifter inom .NET-applikationer. Genom att följa denna handledning har du lärt dig hur du hämtar alla versionsnycklar på ett dokument med GroupDocs.Annotation för .NET. Inkludera den här funktionen i dina projekt för att förbättra dokumenthanteringskapaciteten.
## FAQ's
### Är GroupDocs.Annotation for .NET kompatibelt med alla dokumentformat?
GroupDocs.Annotation for .NET stöder ett brett utbud av dokumentformat, inklusive PDF, DOCX, XLSX, PPTX och mer.
### Kan jag prova GroupDocs.Annotation för .NET innan jag köper?
 Ja, du kan utforska funktionerna i GroupDocs.Annotation för .NET genom att få tillgång till den kostnadsfria testversionen[här](https://releases.groupdocs.com/).
### Hur kan jag få support för GroupDocs.Annotation för .NET?
 Du kan söka hjälp och engagera dig i samhället via supportforumet[här](https://forum.groupdocs.com/c/annotation/10).
### Finns det tillfälliga licenser tillgängliga för GroupDocs.Annotation för .NET?
 Ja, tillfälliga licenser är tillgängliga för utvärderingssyften. Du kan få en från[här](https://purchase.groupdocs.com/temporary-license/).
### Var kan jag köpa GroupDocs.Annotation för .NET?
 Du kan köpa GroupDocs.Annotation för .NET från webbplatsen[här](https://purchase.groupdocs.com/buy).