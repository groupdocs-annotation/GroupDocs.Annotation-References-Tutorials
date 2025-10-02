---
"description": "Leer hoe u tekstredactieannotaties aan PDF-documenten toevoegt met GroupDocs.Annotation voor .NET. Bescherm gevoelige informatie moeiteloos."
"linktitle": "Tekstredactie-annotatie toevoegen aan document"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "Tekstredactie-annotatie toevoegen aan document"
"url": "/nl/net/unlocking-annotation-power/add-text-redaction-annotation/"
type: docs
"weight": 23
---

# Tekstredactie-annotatie toevoegen aan document

## Invoering
Het toevoegen van een tekstredactieannotatie aan een document kan een cruciale stap zijn in het veilig beheren van gevoelige informatie. GroupDocs.Annotation voor .NET biedt een robuuste oplossing om dit naadloos te realiseren. In deze tutorial begeleiden we u stap voor stap door het proces van het toevoegen van een tekstredactieannotatie aan uw document.
## Vereisten
Voordat we beginnen, moet u ervoor zorgen dat u aan de volgende voorwaarden voldoet:
1. GroupDocs.Annotation voor .NET: Zorg ervoor dat u de GroupDocs.Annotation voor .NET-bibliotheek hebt geïnstalleerd. U kunt deze downloaden van de [website](https://releases.groupdocs.com/annotation/net/).
2. Ontwikkelomgeving: Stel een ontwikkelomgeving in met een .NET-compatibele IDE, zoals Visual Studio.

## Naamruimten importeren
Laten we eerst de benodigde naamruimten naar ons project importeren:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Stap 1: Uitvoerpad definiëren
Definieer het uitvoerpad waar u het geannoteerde document wilt opslaan. Zorg ervoor dat het toegankelijk en beschrijfbaar is.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Stap 2: Annotator initialiseren
Initialiseer de annotator met het invoerdocumentpad. Vervang `"input.pdf"` met het pad naar uw document.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Annotatiecode komt hier
}
```
## Stap 3: Tekstredactie-annotatie maken
Maak een `TextRedactionAnnotation` object met de vereiste eigenschappen zoals `PageNumber`, `FontColor`, En `Points`Pas de annotatie aan uw wensen aan.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
## Stap 4: Annotatie toevoegen en opslaan
Voeg de gemaakte annotatie toe aan het document met behulp van de annotator en sla het geannoteerde document op in het opgegeven uitvoerpad.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Stap 5: Controleer de uitvoer
Controleer ten slotte of het document succesvol is opgeslagen in het opgegeven uitvoerpad.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusie
In deze tutorial hebben we het proces doorlopen van het toevoegen van een tekstredactieannotatie aan een document met behulp van GroupDocs.Annotation voor .NET. Met deze stappen kunt u nu vertrouwelijke informatie in uw documenten veilig beheren.
## Veelgestelde vragen
### Kan ik het uiterlijk van de tekstredactieannotatie aanpassen?
Ja, u kunt verschillende eigenschappen, zoals lettertypekleur, opvulkleur en dekking, naar wens aanpassen.
### Is er een proefversie beschikbaar voordat u tot aankoop overgaat?
Ja, u kunt een gratis proefversie openen via de [website](https://releases.groupdocs.com/).
### Hoe kan ik ondersteuning krijgen als ik problemen ondervind?
U kunt ondersteuning krijgen via het GroupDocs.Annotation communityforum [hier](https://forum.groupdocs.com/c/annotation/10).
### Heb ik een tijdelijke licentie nodig voor testdoeleinden?
Ja, u kunt een tijdelijke vergunning verkrijgen bij de [aankooppagina](https://purchase.groupdocs.com/temporary-license/) voor testen.
### Kan ik meerdere aantekeningen aan één document toevoegen?
Jazeker, met GroupDocs.Annotation kunt u verschillende typen annotaties en meerdere instanties aan één document toevoegen.