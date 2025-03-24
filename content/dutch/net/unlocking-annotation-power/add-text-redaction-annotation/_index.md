---
title: Voeg tekstredactieannotatie toe aan document
linktitle: Voeg tekstredactieannotatie toe aan document
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u tekstredactieannotaties aan PDF-documenten kunt toevoegen met GroupDocs.Annotation voor .NET. Beveilig gevoelige informatie moeiteloos.
weight: 23
url: /nl/net/unlocking-annotation-power/add-text-redaction-annotation/
---
## Invoering
Het toevoegen van een annotatie voor tekstredactie aan een document kan een cruciale stap zijn bij het veilig beheren van gevoelige informatie. GroupDocs.Annotation voor .NET biedt een robuuste oplossing om dit naadloos te bereiken. In deze zelfstudie begeleiden we u stap voor stap bij het toevoegen van een annotatie voor tekstredactie aan uw document.
## Vereisten
Voordat we beginnen, zorg ervoor dat u aan de volgende vereisten voldoet:
1.  GroupDocs.Annotation voor .NET: Zorg ervoor dat u de GroupDocs.Annotation voor .NET-bibliotheek hebt geïnstalleerd. Je kunt het downloaden van de[website](https://releases.groupdocs.com/annotation/net/).
2. Ontwikkelomgeving: Zet een ontwikkelomgeving op met een .NET-compatibele IDE zoals Visual Studio.

## Naamruimten importeren
Laten we eerst de benodigde naamruimten in ons project importeren:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Stap 1: Definieer het uitvoerpad
Definieer het uitvoerpad waar u het geannoteerde document wilt opslaan. Zorg ervoor dat het toegankelijk en beschrijfbaar is.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Stap 2: Initialiseer Annotator
 Initialiseer de annotator met het invoerdocumentpad. Vervangen`"input.pdf"` met het pad naar uw document.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // De annotatiecode komt hier terecht
}
```
## Stap 3: Maak een annotatie voor tekstredactie
 Maak een`TextRedactionAnnotation`object met de vereiste eigenschappen, zoals`PageNumber`, `FontColor` , En`Points`. Pas de annotatie aan volgens uw vereisten.
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
## Stap 4: annotatie toevoegen en opslaan
Voeg de gemaakte annotatie toe aan het document met behulp van de annotator en sla het geannoteerde document op in het opgegeven uitvoerpad.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Stap 5: Controleer de uitvoer
Bevestig ten slotte dat het document met succes is opgeslagen in het opgegeven uitvoerpad.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusie
In deze zelfstudie hebben we het proces doorlopen van het toevoegen van een annotatie voor tekstredactie aan een document met behulp van GroupDocs.Annotation voor .NET. Met deze stappen kunt u nu veilig gevoelige informatie in uw documenten beheren.
## Veelgestelde vragen
### Kan ik het uiterlijk van de tekstredactieannotatie aanpassen?
Ja, u kunt verschillende eigenschappen, zoals de kleur van het lettertype, de opvulkleur en de dekking, aanpassen aan uw wensen.
### Is er een proefversie beschikbaar voordat u deze aanschaft?
 Ja, u kunt toegang krijgen tot een gratis proefversie van de[website](https://releases.groupdocs.com/).
### Hoe kan ik ondersteuning krijgen als ik problemen tegenkom?
 U kunt ondersteuning krijgen van het GroupDocs.Annotation-communityforum[hier](https://forum.groupdocs.com/c/annotation/10).
### Heb ik een tijdelijke licentie nodig voor testdoeleinden?
 Ja, u kunt een tijdelijke licentie verkrijgen bij de[aankooppagina](https://purchase.groupdocs.com/temporary-license/)om uit te proberen.
### Kan ik meerdere annotaties aan één document toevoegen?
Absoluut, met GroupDocs.Annotation kunt u verschillende soorten annotaties en meerdere exemplaren aan één document toevoegen.