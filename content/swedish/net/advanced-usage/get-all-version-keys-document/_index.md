---
"description": "Lär dig hur du hämtar alla versionsnycklar för ett dokument med GroupDocs.Annotation för .NET. Förbättra dina dokumenthanteringsfunktioner med denna omfattande guide."
"linktitle": "Hämta alla versionsnycklar i dokumentet"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Hämta alla versionsnycklar i dokumentet"
"url": "/sv/net/advanced-usage/get-all-version-keys-document/"
type: docs
"weight": 16
---

# Hämta alla versionsnycklar i dokumentet

## Introduktion
dagens snabba digitala värld är effektiv dokumenthantering avgörande för både företag och privatpersoner. Oavsett om du samarbetar i projekt, granskar kontrakt eller helt enkelt organiserar dina filer kan rätt verktyg göra hela skillnaden. GroupDocs.Annotation för .NET erbjuder en omfattande lösning för att kommentera och manipulera dokument i .NET-applikationer. I den här handledningen utforskar vi hur man använder GroupDocs.Annotation för .NET för att hämta alla versionsnycklar i ett dokument.
## Förkunskapskrav
Innan vi går in i handledningen, se till att du har följande förkunskaper:
### 1. Installera GroupDocs.Annotation för .NET
För att komma igång behöver du ladda ner och installera GroupDocs.Annotation för .NET. Du kan hämta den senaste versionen från [nedladdningslänk](https://releases.groupdocs.com/annotation/net/).
### 2. Skaffa API-autentiseringsuppgifter
Se till att du har nödvändiga API-inloggningsuppgifter för att få åtkomst till GroupDocs.Annotation för .NET-funktioner.

## Importera nödvändiga namnrymder
Innan du fortsätter, se till att importera de namnrymder som krävs till ditt projekt:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
```

Låt oss dela upp processen för att hämta alla versionsnycklar i ett dokument i enkla steg:
## Steg 1: Initiera annotatorobjektet
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf"))
{
    // Koden går hit
}
```
Initiera `Annotator` objekt med sökvägen till dokumentet du vill arbeta med.
## Steg 2: Hämta versionsnycklar
```csharp
List<object> versionKeys = annotator.GetVersionsList();
```
Anropa `GetVersionsList()` metod på `Annotator` objekt för att hämta alla versionsnycklar som är associerade med dokumentet. Den här metoden returnerar en lista över versionsnycklar.

## Slutsats
GroupDocs.Annotation för .NET förenklar dokumentannotering och manipulationsuppgifter i .NET-applikationer. Genom att följa den här handledningen har du lärt dig hur du hämtar alla versionsnycklar för ett dokument med GroupDocs.Annotation för .NET. Integrera den här funktionen i dina projekt för att förbättra dokumenthanteringsfunktionerna.
## Vanliga frågor
### Är GroupDocs.Annotation för .NET kompatibel med alla dokumentformat?
GroupDocs.Annotation för .NET stöder en mängd olika dokumentformat, inklusive PDF, DOCX, XLSX, PPTX med flera.
### Kan jag prova GroupDocs.Annotation för .NET innan jag köper?
Ja, du kan utforska funktionerna i GroupDocs.Annotation för .NET genom att använda den kostnadsfria testversionen som finns tillgänglig. [här](https://releases.groupdocs.com/).
### Hur kan jag få support för GroupDocs.Annotation för .NET?
Du kan söka hjälp och interagera med gemenskapen via supportforumet [här](https://forum.groupdocs.com/c/annotation/10).
### Finns det tillfälliga licenser tillgängliga för GroupDocs.Annotation för .NET?
Ja, tillfälliga licenser finns tillgängliga för utvärderingsändamål. Du kan få en från [här](https://purchase.groupdocs.com/temporary-license/).
### Var kan jag köpa GroupDocs.Annotation för .NET?
Du kan köpa GroupDocs.Annotation för .NET från webbplatsen [här](https://purchase.groupdocs.com/buy).