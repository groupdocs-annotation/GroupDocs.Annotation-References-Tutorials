---
"description": "Lär dig hur du konfigurerar en mätt licens för GroupDocs.Annotation .NET för att resursanvändning och dokumentannoteringsfunktioner i dina .NET-applikationer."
"linktitle": "Ställ in uppmätt licens"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Ställ in uppmätt licens"
"url": "/sv/net/applying-licenses/set-metered-license/"
"weight": 12
---

# Ställ in uppmätt licens

## Introduktion
GroupDocs.Annotation för .NET är ett kraftfullt bibliotek som gör det möjligt för utvecklare att enkelt lägga till dokumentannoteringsfunktioner i sina .NET-applikationer. Oavsett om du bygger ett dokumenthanteringssystem, en samarbetsplattform eller någon annan applikation som involverar dokumentgranskning och markup, tillhandahåller GroupDocs.Annotation för .NET en omfattande uppsättning verktyg för att effektivisera processen.
I den här handledningen går vi in på processen att konfigurera en mätad licens för GroupDocs.Annotation .NET. En mätad licens låter dig bara betala för de resurser du förbrukar, vilket gör den till en kostnadseffektiv lösning för projekt av alla storlekar. Genom att följa stegen nedan kan du sömlöst integrera GroupDocs.Annotation i din .NET-applikation samtidigt som du optimerar resursanvändningen och bibehåller budgetkontroll.
## Förkunskapskrav
Innan du börjar med handledningen, se till att du har följande förkunskaper:
1. GroupDocs.Annotation för .NET-biblioteket: Ladda ner biblioteket från [webbplats](https://releases.groupdocs.com/annotation/net/).
2. Åtkomst till GroupDocs-konto: Du behöver ett GroupDocs-konto för att få de offentliga och privata nycklar som krävs för att konfigurera den uppmätta licensen. Om du inte har ett konto än kan du registrera dig för en gratis provperiod. [här](https://releases.groupdocs.com/).
3. Grundläggande förståelse för C# och .NET Framework: Bekantskap med programmeringsspråket C# och .NET Framework är fördelaktigt för att implementera stegen som beskrivs i den här handledningen.

## Importera namnrymder
Börja med att importera de nödvändiga namnrymderna till ditt C#-projekt. Dessa namnrymder är viktiga för att interagera med GroupDocs.Annotation-funktionen.
```csharp
using System;
```
## Steg 1: Hämta offentliga och privata nycklar
Innan du konfigurerar den uppmätta licensen måste du hämta dina offentliga och privata nycklar från instrumentpanelen för ditt GroupDocs-konto.
1. Logga in på ditt GroupDocs-konto.
2. Navigera till avsnittet för licenshantering.
3. Kopiera dina offentliga och privata nycklar som tillhandahålls av GroupDocs.
## Steg 2: Ställ in licensmätning
När du har fått dina publika och privata nycklar kan du konfigurera den uppmätta licensen i ditt .NET-program.
```csharp
string publicKey = "*****"; // Ersätt ***** med din publika nyckel
string privateKey = "*****"; // Ersätt ***** med din privata nyckel
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Slutsats
Sammanfattningsvis är det en enkel process att konfigurera en mätlicens för GroupDocs.Annotation .NET som säkerställer effektivt resursutnyttjande och kostnadseffektivitet för dina dokumentannoteringsprojekt. Genom att följa stegen som beskrivs i den här handledningen kan du sömlöst integrera GroupDocs.Annotation i din .NET-applikation och förbättra funktionerna för dokumentsamarbete och granskning.
## Vanliga frågor
### Kan jag använda GroupDocs.Annotation för .NET i kommersiella projekt?
Ja, GroupDocs.Annotation för .NET kan användas i både kommersiella och icke-kommersiella projekt. Du måste dock skaffa en lämplig licens baserat på dina projektkrav.
### Finns det en testversion tillgänglig för GroupDocs.Annotation för .NET?
Ja, du kan få en gratis provversion av GroupDocs.Annotation för .NET genom att besöka [den här länken](https://releases.groupdocs.com/).
### Hur kan jag få teknisk support för GroupDocs.Annotation för .NET?
Du kan söka teknisk support genom att besöka GroupDocs-forumet. [här](https://forum.groupdocs.com/c/annotation/10).
### Finns det några alternativ för tillfälliga licenser?
Ja, du kan få en tillfällig licens från GroupDocs för kortvarig användning eller utvärdering. Besök [den här länken](https://purchase.groupdocs.com/temporary-license/) för mer information.
### Kan jag anpassa anteckningsfunktionerna efter mitt projekts krav?
Ja, GroupDocs.Annotation för .NET erbjuder omfattande anpassningsalternativ, vilket gör att du kan skräddarsy annoteringsfunktionerna efter dina specifika projektbehov.