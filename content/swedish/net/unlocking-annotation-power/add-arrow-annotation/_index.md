---
title: Lägg till pilkommentar i dokumentet
linktitle: Lägg till pilkommentar i dokumentet
second_title: GroupDocs.Annotation .NET API
description: Lär dig hur du lägger till pilkommentarer till dina dokument med GroupDocs.Annotation för .NET. Förbättra dokumentets tydlighet och interaktivitet utan ansträngning.
weight: 11
url: /sv/net/unlocking-annotation-power/add-arrow-annotation/
---
## Introduktion
I den här handledningen guidar vi dig genom processen att lägga till pilkommentarer till dina dokument med GroupDocs.Annotation för .NET. Pilkommentarer är användbara för att indikera riktning eller peka ut specifika element i ett dokument.
## Förutsättningar
Innan du börjar, se till att du har följande:
1.  GroupDocs.Annotation for .NET: Installera GroupDocs.Annotation-biblioteket för .NET. Du kan ladda ner den från[här](https://releases.groupdocs.com/annotation/net/).
2. Utvecklingsmiljö: Se till att du har en utvecklingsmiljö inställd för .NET-utveckling, inklusive Visual Studio eller någon annan föredragen IDE.

## Importera namnområden
Först måste du importera de nödvändiga namnområdena för att komma åt de obligatoriska klasserna och metoderna för anteckning.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Steg 1: Initiera Annotator
Initiera annotatorn genom att ange sökvägen till indatadokumentets fil.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Steg 2: Skapa pilkommentar
Skapa en instans av klassen ArrowAnnotation och definiera dess egenskaper som position, meddelande, opacitet, pennfärg, stil, bredd, etc.
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
## Steg 3: Lägg till anteckning
 Lägg till pilkommentaren till dokumentet med hjälp av`Add` annotatorns metod.
```csharp
	annotator.Add(arrow);
```
## Steg 4: Spara dokument
Spara det kommenterade dokumentet till den angivna utmatningsvägen.
```csharp
	annotator.Save(outputPath);
}
```
## Steg 5: Visa bekräftelse
Visa ett bekräftelsemeddelande som indikerar att dokumentet har sparats.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Nu har du framgångsrikt lagt till en pilkommentar till ditt dokument med GroupDocs.Annotation för .NET.

## Slutsats
den här handledningen har vi täckt processen att lägga till pilkommentarer till dokument med GroupDocs.Annotation för .NET. Genom att följa dessa steg kan du förbättra dina dokument med tydliga riktningsindikatorer, vilket gör dem mer informativa och engagerande.
## FAQ's
### Kan jag anpassa utseendet på pilkommentaren?
Ja, du kan anpassa olika egenskaper som färg, stil, bredd och opacitet för att passa dina preferenser och dokumentkrav.
### Är GroupDocs.Annotation kompatibel med alla dokumentformat?
GroupDocs.Annotation stöder ett brett utbud av dokumentformat inklusive PDF, DOCX, PPTX, XLSX och mer.
### Kan jag lägga till kommentarer programmatiskt med GroupDocs.Annotation?
Ja, GroupDocs.Annotation tillhandahåller API:er som låter dig lägga till, redigera och ta bort anteckningar från dokument programmatiskt.
### Erbjuder GroupDocs.Annotation en gratis provperiod?
 Ja, du kan prova GroupDocs.Annotation gratis genom att ladda ner den från[här](https://releases.groupdocs.com/).
### Var kan jag få teknisk support för GroupDocs.Annotation?
För teknisk support och hjälp kan du besöka forumet GroupDocs.Annotation[här](https://forum.groupdocs.com/c/annotation/10).