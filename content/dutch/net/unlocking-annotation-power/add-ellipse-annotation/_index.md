---
title: Voeg ellipsannotatie toe aan document
linktitle: Voeg ellipsannotatie toe aan document
second_title: GroupDocs.Annotation .NET API
description: Leer hoe u ellipsannotaties toevoegt aan documenten in .NET met behulp van GroupDocs.Annotation. Verbeter moeiteloos de samenwerking en communicatie.
type: docs
weight: 13
url: /nl/net/unlocking-annotation-power/add-ellipse-annotation/
---
## Invoering
In deze zelfstudie leert u hoe u een ellipsannotatie aan een document kunt toevoegen met GroupDocs.Annotation voor .NET. Deze stapsgewijze handleiding leidt u door het proces en zorgt ervoor dat u elke stap duidelijk begrijpt.
## Vereisten
Zorg ervoor dat u over het volgende beschikt voordat u begint:
1.  GroupDocs.Annotation voor .NET: Zorg ervoor dat u GroupDocs.Annotation voor .NET hebt gedownload en geïnstalleerd. Je kunt het downloaden van[hier](https://releases.groupdocs.com/annotation/net/).
2. IDE (Integrated Development Environment): U hebt een IDE nodig die op uw systeem is geïnstalleerd, zoals Visual Studio, om de code te schrijven en uit te voeren.

## Naamruimten importeren
Importeer eerst de benodigde naamruimten in uw project:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Stap 1: Stel het uitvoerpad in
Definieer het uitvoerpad waar het geannoteerde document zal worden opgeslagen:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Stap 2: Initialiseer Annotator
Initialiseer de annotator door het invoerdocumentpad op te geven:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Stap 3: Maak een ellipsannotatie
 Maak een exemplaar van de`EllipseAnnotation` klasse en stel de eigenschappen in:
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
Voeg de ellipsannotatie toe aan het document:
```csharp
annotator.Add(ellipse);
```
## Stap 5: Document opslaan
Sla het geannoteerde document op in het uitvoerpad:
```csharp
annotator.Save(outputPath);
```

## Conclusie
Gefeliciteerd! U hebt met succes een ellipsannotatie aan een document toegevoegd met GroupDocs.Annotation voor .NET. U kunt deze functionaliteit nu integreren in uw .NET-applicaties om de samenwerking en communicatie aan documenten te verbeteren.
## Veelgestelde vragen
### Kan ik het uiterlijk van de ellipsannotatie aanpassen?
Ja, u kunt verschillende eigenschappen, zoals achtergrondkleur, randkleur, dekking, enz., aanpassen aan uw wensen.
### Is GroupDocs.Annotation voor .NET compatibel met alle documentformaten?
GroupDocs.Annotation voor .NET ondersteunt een breed scala aan documentformaten, waaronder PDF, DOCX, PPTX, XLSX en meer.
### Kan ik meerdere annotaties aan één document toevoegen?
Ja, u kunt meerdere annotaties, waaronder ellipsen, rechthoeken, tekst, enz., aan één document toevoegen.
### Is er een proefversie beschikbaar voor testdoeleinden?
 Ja, u kunt een gratis proefversie downloaden van[hier](https://releases.groupdocs.com/) om de kenmerken ervan te evalueren.
### Waar kan ik technische ondersteuning krijgen voor GroupDocs.Annotation voor .NET?
 U kunt technische ondersteuning krijgen van het GroupDocs.Annotation-communityforum[hier](https://forum.groupdocs.com/c/annotation/10).