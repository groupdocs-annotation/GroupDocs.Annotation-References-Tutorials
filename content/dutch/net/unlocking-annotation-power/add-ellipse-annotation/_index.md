---
"description": "Leer hoe u ellips-annotaties toevoegt aan documenten in .NET met GroupDocs.Annotation. Verbeter moeiteloos samenwerking en communicatie."
"linktitle": "Ellips-annotatie toevoegen aan document"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "Ellips-annotatie toevoegen aan document"
"url": "/nl/net/unlocking-annotation-power/add-ellipse-annotation/"
"weight": 13
---

# Ellips-annotatie toevoegen aan document

## Invoering
In deze tutorial leer je hoe je een ellips-annotatie aan een document toevoegt met GroupDocs.Annotation voor .NET. Deze stapsgewijze handleiding leidt je door het proces, zodat je elke stap duidelijk begrijpt.
## Vereisten
Voordat u begint, moet u ervoor zorgen dat u het volgende heeft:
1. GroupDocs.Annotation voor .NET: Zorg ervoor dat je GroupDocs.Annotation voor .NET hebt gedownload en geïnstalleerd. Je kunt het downloaden van [hier](https://releases.groupdocs.com/annotation/net/).
2. IDE (Integrated Development Environment): U hebt een IDE nodig die op uw systeem is geïnstalleerd, bijvoorbeeld Visual Studio, om de code te schrijven en uit te voeren.

## Naamruimten importeren
Importeer eerst de benodigde naamruimten naar uw project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Stap 1: Uitvoerpad instellen
Definieer het uitvoerpad waar het geannoteerde document wordt opgeslagen:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Stap 2: Annotator initialiseren
Initialiseer de annotator door het pad naar het invoerdocument op te geven:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Stap 3: Ellips-annotatie maken
Maak een exemplaar van de `EllipseAnnotation` klasse en stel de eigenschappen ervan in:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
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
## Stap 4: Annotatie toevoegen
Voeg de ellips-annotatie toe aan het document:
```csharp
annotator.Add(ellipse);
```
## Stap 5: Document opslaan
Sla het geannoteerde document op in het uitvoerpad:
```csharp
annotator.Save(outputPath);
```

## Conclusie
Gefeliciteerd! U hebt met succes een ellips-annotatie aan een document toegevoegd met GroupDocs.Annotation voor .NET. U kunt deze functionaliteit nu integreren in uw .NET-applicaties om de samenwerking en communicatie aan documenten te verbeteren.
## Veelgestelde vragen
### Kan ik het uiterlijk van de ellips-annotatie aanpassen?
Ja, u kunt verschillende eigenschappen, zoals achtergrondkleur, randkleur, dekking, enz., aanpassen aan uw wensen.
### Is GroupDocs.Annotation voor .NET compatibel met alle documentformaten?
GroupDocs.Annotation voor .NET ondersteunt een breed scala aan documentindelingen, waaronder PDF, DOCX, PPTX, XLSX en meer.
### Kan ik meerdere aantekeningen aan één document toevoegen?
Ja, u kunt meerdere aantekeningen, zoals ellipsen, rechthoeken, tekst, enz., aan één document toevoegen.
### Is er een proefversie beschikbaar voor testdoeleinden?
Ja, u kunt een gratis proefversie downloaden van [hier](https://releases.groupdocs.com/) om de kenmerken ervan te evalueren.
### Waar kan ik technische ondersteuning krijgen voor GroupDocs.Annotation voor .NET?
U kunt technische ondersteuning krijgen via het GroupDocs.Annotation communityforum [hier](https://forum.groupdocs.com/c/annotation/10).