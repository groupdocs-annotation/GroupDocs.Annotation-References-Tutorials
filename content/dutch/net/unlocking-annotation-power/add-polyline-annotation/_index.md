---
"description": "Leer hoe u polylijnannotaties aan documenten toevoegt met GroupDocs.Annotation voor .NET. Verbeter moeiteloos samenwerkings- en documentbeoordelingsprocessen."
"linktitle": "Polylijnannotatie toevoegen aan document"
"second_title": "GroupDocs.Annotatie .NET API"
"title": "Polylijnannotatie toevoegen aan document"
"url": "/nl/net/unlocking-annotation-power/add-polyline-annotation/"
type: docs
"weight": 18
---

# Polylijnannotatie toevoegen aan document

## Invoering
GroupDocs.Annotation voor .NET is een krachtige tool waarmee ontwikkelaars programmatisch PDF- en Microsoft Office-documenten kunnen annoteren. Een van de functies is de mogelijkheid om polylijnannotaties aan documenten toe te voegen, wat de samenwerking en de beoordeling van documenten verbetert.
## Vereisten
Voordat u met deze tutorial verdergaat, moet u ervoor zorgen dat u over het volgende beschikt:
- Visual Studio op uw systeem geïnstalleerd.
- Basiskennis van de programmeertaal C#.
- GroupDocs.Annotation voor .NET-bibliotheek geïnstalleerd. U kunt het downloaden van [hier](https://releases.groupdocs.com/annotation/net/).

## Naamruimten importeren
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Stap 1: Uitvoerpad definiëren
Definieer eerst het uitvoerpad waar het geannoteerde document wordt opgeslagen.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Stap 2: Annotator initialiseren
Initialiseer de annotator door de naam van het invoerdocument op te geven.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Stap 3: Polylijn-annotatieobject maken
Maak een polylijn-annotatieobject en stel de eigenschappen ervan in, zoals positie, bericht, dekking, penkleur, penstijl en penbreedte.
```csharp
PolylineAnnotation polyline = new PolylineAnnotation
{
    Box = new Rectangle(250, 35, 102, 12),
    CreatedOn = DateTime.Now,
    Message = "This is polyline annotation",
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
    },
    SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.698685
4460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
};
```
## Stap 4: Polylijnannotatie toevoegen
Voeg de polylijnannotatie toe aan het document met behulp van het annotatorobject.
```csharp
annotator.Add(polyline);
```
## Stap 5: Document opslaan
Sla het geannoteerde document op in het opgegeven uitvoerpad.
```csharp
annotator.Save(outputPath);
```
## Stap 6: Succesbericht weergeven
Er wordt een bericht weergegeven waarin wordt bevestigd dat het document succesvol is opgeslagen.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusie
In deze tutorial hebben we geleerd hoe je een polylijnannotatie aan een document toevoegt met GroupDocs.Annotation voor .NET. Deze functie verbetert de samenwerking en het reviewproces van documenten, waardoor gebruikers gemakkelijker feedback en suggesties kunnen geven.
## Veelgestelde vragen
### Is GroupDocs.Annotation voor .NET compatibel met alle documentformaten?
GroupDocs.Annotation voor .NET ondersteunt populaire documentindelingen zoals PDF en Microsoft Office-indelingen, waaronder Word, Excel en PowerPoint.
### Kan ik het uiterlijk van annotaties aanpassen?
Ja, u kunt diverse eigenschappen van annotaties, zoals kleur, dekking, stijl en breedte, naar wens aanpassen.
### Biedt GroupDocs.Annotation voor .NET een gratis proefperiode aan?
Ja, u kunt een gratis proefversie van GroupDocs.Annotation voor .NET gebruiken door naar [deze link](https://releases.groupdocs.com/).
### Waar kan ik documentatie vinden voor GroupDocs.Annotation voor .NET?
De documentatie voor GroupDocs.Annotation voor .NET vindt u hier [hier](https://tutorials.groupdocs.com/annotation/net/).
### Hoe kan ik ondersteuning krijgen voor problemen of vragen met betrekking tot GroupDocs.Annotation voor .NET?
U kunt ondersteuning krijgen door het GroupDocs.Annotation-forum te bezoeken [hier](https://forum.groupdocs.com/c/annotation/10).