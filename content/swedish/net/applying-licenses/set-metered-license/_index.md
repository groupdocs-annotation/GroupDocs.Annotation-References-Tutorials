---
title: Ställ in mätlicens
linktitle: Ställ in mätlicens
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du ställer in en uppmätt licens för GroupDocs.Annotation .NET för resursanvändning och dokumentera anteckningsfunktioner i dina .NET-applikationer.
weight: 12
url: /sv/net/applying-licenses/set-metered-license/
---
## Introduktion
GroupDocs.Annotation for .NET är ett kraftfullt bibliotek som ger utvecklare möjlighet att lägga till dokumentkommentarfunktioner till sina .NET-applikationer utan ansträngning. Oavsett om du bygger ett dokumenthanteringssystem, en samarbetsplattform eller någon applikation som involverar dokumentgranskning och uppmärkning, tillhandahåller GroupDocs.Annotation för .NET en omfattande uppsättning verktyg för att effektivisera processen.
I den här handledningen kommer vi att fördjupa oss i processen för att ställa in en uppmätt licens för GroupDocs.Annotation .NET. En mätlicens tillåter dig att endast betala för de resurser du förbrukar, vilket gör det till en kostnadseffektiv lösning för projekt av alla skala. Genom att följa stegen som beskrivs nedan kommer du att sömlöst kunna integrera GroupDocs.Annotation i din .NET-applikation samtidigt som du optimerar resursanvändningen och bibehåller budgetkontrollen.
## Förutsättningar
Innan du dyker in i handledningen, se till att du har följande förutsättningar:
1.  GroupDocs.Annotation for .NET Library: Ladda ner biblioteket från[hemsida](https://releases.groupdocs.com/annotation/net/).
2. Åtkomst till GroupDocs-konto: Du behöver ett GroupDocs-konto för att få de offentliga och privata nycklar som krävs för att ställa in den uppmätta licensen. Om du inte har ett konto ännu kan du registrera dig för en gratis provperiod[här](https://releases.groupdocs.com/).
3. Grundläggande förståelse för C# och .NET Framework: Bekantskap med programmeringsspråket C# och .NET Framework kommer att vara fördelaktigt för att implementera stegen som beskrivs i denna handledning.

## Importera namnområden
För att börja, se till att importera de nödvändiga namnrymden till ditt C#-projekt. Dessa namnutrymmen är viktiga för att interagera med GroupDocs.Annotation-funktionalitet.
```csharp
using System;
```
## Steg 1: Skaffa offentliga och privata nycklar
Innan du ställer in mätlicensen måste du skaffa dina offentliga och privata nycklar från instrumentpanelen för ditt GroupDocs-konto.
1. Logga in på ditt GroupDocs-konto.
2. Navigera till avsnittet för licenshantering.
3. Kopiera dina offentliga och privata nycklar från GroupDocs.
## Steg 2: Ställ in mätlicens
När du har skaffat dina offentliga och privata nycklar kan du ställa in mätlicensen i din .NET-applikation.
```csharp
string publicKey = "*****"; // Ersätt ***** med din publika nyckel
string privateKey = "*****"; // Ersätt ***** med din privata nyckel
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Slutsats
Sammanfattningsvis, att sätta upp en uppmätt licens för GroupDocs.Annotation .NET är en enkel process som säkerställer ett effektivt resursutnyttjande och kostnadseffektivitet för dina dokumentkommentarsprojekt. Genom att följa stegen som beskrivs i den här handledningen kan du sömlöst integrera GroupDocs.Annotation i din .NET-applikation och förbättra dokumentsamarbete och granskningsmöjligheter.
## FAQ's
### Kan jag använda GroupDocs.Annotation för .NET i kommersiella projekt?
Ja, GroupDocs.Annotation för .NET kan användas i både kommersiella och icke-kommersiella projekt. Du måste dock skaffa en lämplig licens baserat på dina projektkrav.
### Finns det en testversion tillgänglig för GroupDocs.Annotation för .NET?
 Ja, du kan använda en gratis provversion av GroupDocs.Annotation för .NET genom att besöka[den här länken](https://releases.groupdocs.com/).
### Hur kan jag få teknisk support för GroupDocs.Annotation för .NET?
 Du kan söka teknisk support genom att besöka GroupDocs-forumet[här](https://forum.groupdocs.com/c/annotation/10).
### Finns det några tillfälliga licensalternativ tillgängliga?
 Ja, du kan få en tillfällig licens från GroupDocs för kortvarig användning eller utvärderingsändamål. Besök[den här länken](https://purchase.groupdocs.com/temporary-license/) för mer information.
### Kan jag anpassa anteckningsfunktionerna enligt mina projektkrav?
Ja, GroupDocs.Annotation för .NET erbjuder omfattande anpassningsalternativ, så att du kan skräddarsy anteckningsfunktionerna för att passa dina specifika projektbehov.