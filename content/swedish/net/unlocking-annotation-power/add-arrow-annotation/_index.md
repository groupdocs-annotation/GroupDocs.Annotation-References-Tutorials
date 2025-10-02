---
"description": "Lär dig hur du lägger till pilanteckningar i dina dokument med GroupDocs.Annotation för .NET. Förbättra dokumentens tydlighet och interaktivitet utan ansträngning."
"linktitle": "Lägg till pilanteckning i dokumentet"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Lägg till pilanteckning i dokumentet"
"url": "/sv/net/unlocking-annotation-power/add-arrow-annotation/"
type: docs
"weight": 11
---

# Lägg till pilanteckning i dokumentet

## Introduktion
I den här handledningen guidar vi dig genom processen att lägga till pilannoteringar i dina dokument med GroupDocs.Annotation för .NET. Pilannoteringar är användbara för att indikera riktning eller peka ut specifika element i ett dokument.
## Förkunskapskrav
Innan du börjar, se till att du har följande:
1. GroupDocs.Annotation för .NET: Installera GroupDocs.Annotation-biblioteket för .NET. Du kan ladda ner det från [här](https://releases.groupdocs.com/annotation/net/).
2. Utvecklingsmiljö: Se till att du har en utvecklingsmiljö konfigurerad för .NET-utveckling, inklusive Visual Studio eller annan föredragen IDE.

## Importera namnrymder
Först måste du importera de namnrymder som behövs för att komma åt de klasser och metoder som krävs för annotering.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Steg 1: Initiera annotatorn
Initiera annotatorn genom att ange sökvägen till indatadokumentet.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Steg 2: Skapa pilannotering
Skapa en instans av ArrowAnnotation-klassen och definiera dess egenskaper såsom position, meddelande, opacitet, pennfärg, stil, bredd etc.
```csharp
	ArrowAnnotation arrow = new ArrowAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		CreatedOn = DateTime.Now,
		Message = "This is arrow annotation",
		Opacity = 0.7,
		PageNumber = 0,
		PenColor = 65535,
		PenStyle = PenStyle.Dot,
		PenWidth = 3,
		Replies = new List<Reply>
		{
			new Reply
			{
				Comment = "First comment",
				RepliedOn = DateTime.Now
			},
			new Reply
			{
				Comment = "Second comment",
				RepliedOn = DateTime.Now
			}
		}
	};
```
## Steg 3: Lägg till annotering
Lägg till pilanteckningen i dokumentet med hjälp av `Add` annotatorns metod.
```csharp
	annotator.Add(arrow);
```
## Steg 4: Spara dokument
Spara det kommenterade dokumentet till den angivna utdatasökvägen.
```csharp
	annotator.Save(outputPath);
}
```
## Steg 5: Visa bekräftelse
Visa ett bekräftelsemeddelande som anger att dokumentet har sparats.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Nu har du lagt till en pilannotering i ditt dokument med GroupDocs.Annotation för .NET.

## Slutsats
I den här handledningen har vi gått igenom processen att lägga till pilanteckningar i dokument med GroupDocs.Annotation för .NET. Genom att följa dessa steg kan du förbättra dina dokument med tydliga riktningsindikatorer, vilket gör dem mer informativa och engagerande.
## Vanliga frågor
### Kan jag anpassa utseendet på pilannoteringen?
Ja, du kan anpassa olika egenskaper som färg, stil, bredd och opacitet för att passa dina handledningar och dokumentkrav.
### Är GroupDocs.Annotation kompatibel med alla dokumentformat?
GroupDocs.Annotation stöder ett brett utbud av dokumentformat, inklusive PDF, DOCX, PPTX, XLSX med flera.
### Kan jag lägga till annoteringar programmatiskt med GroupDocs.Annotation?
Ja, GroupDocs.Annotation tillhandahåller API:er som låter dig programmatiskt lägga till, redigera och ta bort anteckningar från dokument.
### Erbjuder GroupDocs.Annotation en gratis provperiod?
Ja, du kan prova GroupDocs.Annotation gratis genom att ladda ner det från [här](https://releases.groupdocs.com/).
### Var kan jag få teknisk support för GroupDocs.Annotation?
För teknisk support och hjälp kan du besöka forumet GroupDocs.Annotation. [här](https://forum.groupdocs.com/c/annotation/10).