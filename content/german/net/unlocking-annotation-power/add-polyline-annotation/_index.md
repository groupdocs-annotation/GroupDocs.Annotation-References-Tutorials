---
"description": "Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET Polylinienanmerkungen zu Dokumenten hinzufügen. Verbessern Sie mühelos die Zusammenarbeit und die Dokumentenprüfung."
"linktitle": "Polylinienanmerkung zum Dokument hinzufügen"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Polylinienanmerkung zum Dokument hinzufügen"
"url": "/de/net/unlocking-annotation-power/add-polyline-annotation/"
"weight": 18
---

# Polylinienanmerkung zum Dokument hinzufügen

## Einführung
GroupDocs.Annotation für .NET ist ein leistungsstarkes Tool, mit dem Entwickler PDF- und Microsoft Office-Dokumente programmgesteuert kommentieren können. Zu seinen Funktionen gehört das Hinzufügen von Polylinienanmerkungen zu Dokumenten, was die Zusammenarbeit und die Dokumentenprüfung verbessert.
## Voraussetzungen
Bevor Sie mit diesem Lernprogramm fortfahren, stellen Sie sicher, dass Sie über Folgendes verfügen:
- Visual Studio ist auf Ihrem System installiert.
- Grundkenntnisse der Programmiersprache C#.
- GroupDocs.Annotation für .NET-Bibliothek installiert. Sie können es herunterladen von [Hier](https://releases.groupdocs.com/annotation/net/).

## Namespaces importieren
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Schritt 1: Ausgabepfad definieren
Definieren Sie zunächst den Ausgabepfad, in dem das kommentierte Dokument gespeichert wird.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Annotator initialisieren
Initialisieren Sie den Annotator, indem Sie den Namen des Eingabedokuments angeben.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Schritt 3: Polylinien-Anmerkungsobjekt erstellen
Erstellen Sie ein Polylinien-Anmerkungsobjekt und legen Sie seine Eigenschaften wie Position, Nachricht, Deckkraft, Stiftfarbe, Stiftstil und Stiftbreite fest.
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
## Schritt 4: Polylinienanmerkung hinzufügen
Fügen Sie dem Dokument mithilfe des Annotatorobjekts die Polylinienanmerkung hinzu.
```csharp
annotator.Add(polyline);
```
## Schritt 5: Dokument speichern
Speichern Sie das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad.
```csharp
annotator.Save(outputPath);
```
## Schritt 6: Erfolgsmeldung anzeigen
Zeigt eine Meldung an, die das erfolgreiche Speichern des Dokuments bestätigt.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Annotation für .NET einem Dokument eine Polylinienanmerkung hinzufügt. Diese Funktion verbessert die Zusammenarbeit und die Dokumentprüfung und erleichtert Benutzern die effektive Kommunikation von Feedback und Vorschlägen.
## Häufig gestellte Fragen
### Ist GroupDocs.Annotation für .NET mit allen Dokumentformaten kompatibel?
GroupDocs.Annotation für .NET unterstützt gängige Dokumentformate wie PDF und Microsoft Office-Formate, darunter Word, Excel und PowerPoint.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen?
Ja, Sie können verschiedene Eigenschaften von Anmerkungen wie Farbe, Deckkraft, Stil und Breite an Ihre Anforderungen anpassen.
### Bietet GroupDocs.Annotation für .NET eine kostenlose Testversion an?
Ja, Sie können eine kostenlose Testversion von GroupDocs.Annotation für .NET nutzen, indem Sie [dieser Link](https://releases.groupdocs.com/).
### Wo finde ich Dokumentation für GroupDocs.Annotation für .NET?
Die Dokumentation für GroupDocs.Annotation für .NET finden Sie [Hier](https://tutorials.groupdocs.com/annotation/net/).
### Wie erhalte ich Support bei Problemen oder Fragen zu GroupDocs.Annotation für .NET?
Sie erhalten Unterstützung im GroupDocs.Annotation-Forum. [Hier](https://forum.groupdocs.com/c/annotation/10).