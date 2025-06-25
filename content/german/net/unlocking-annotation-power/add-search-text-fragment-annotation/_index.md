---
"description": "Entdecken Sie die Leistungsfähigkeit von GroupDocs.Annotation für .NET und fügen Sie Ihren Anwendungen mühelos Funktionen zur Dokumentanmerkung hinzu."
"linktitle": "Hinzufügen einer Suchtextfragmentanmerkung zum Dokument"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Hinzufügen einer Suchtextfragmentanmerkung zum Dokument"
"url": "/de/net/unlocking-annotation-power/add-search-text-fragment-annotation/"
"weight": 20
---

# Hinzufügen einer Suchtextfragmentanmerkung zum Dokument

## Einführung
Im Bereich der .NET-Entwicklung ist GroupDocs.Annotation ein leistungsstarkes Tool für die nahtlose Kommentierung von Dokumenten. Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst in die Welt von .NET einsteigen, dieses umfassende Tutorial führt Sie durch die Grundlagen der Verwendung von GroupDocs.Annotation für .NET, vom Importieren von Namespaces bis hin zum Beherrschen der Feinheiten beim Hinzufügen von Suchtextfragment-Annotationen zu Ihren Dokumenten.
## Einführung
GroupDocs.Annotation für .NET ermöglicht Entwicklern die mühelose Integration von Dokumentannotationsfunktionen in ihre Anwendungen. Dank der intuitiven API und der robusten Funktionen können Entwickler verschiedene Dokumentformate kommentieren, darunter PDFs, Microsoft Office-Dokumente, Bilder und mehr.
## Voraussetzungen
Bevor Sie sich in GroupDocs.Annotation für .NET vertiefen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

## Namespaces importieren
Importieren Sie zunächst die erforderlichen Namespaces, um auf die Klassen und Methoden von GroupDocs.Annotation in Ihrem .NET-Projekt zuzugreifen:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Schritt 1: Ausgabepfad definieren
Definieren Sie zunächst den Ausgabepfad, in dem das kommentierte Dokument gespeichert wird:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Annotator initialisieren
Als nächstes initialisieren Sie eine Instanz des `Annotator` Klasse, indem Sie den Pfad zu dem Dokument angeben, das Sie mit Anmerkungen versehen möchten:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Schritt 3: Erstellen einer Annotation für Suchtextfragmente
Erstellen Sie ein `SearchTextFragment` Objekt mit den gewünschten Eigenschaften, wie z. B. zu suchender Text, Schriftgröße, Schriftfamilie, Schriftfarbe und Hintergrundfarbe:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## Schritt 4: Anmerkung hinzufügen
Fügen Sie die erstellte Suchtextfragment-Annotation dem Dokument hinzu, indem Sie `Add` Methode des Annotators:
```csharp
annotator.Add(searchText);
```
## Schritt 5: Kommentiertes Dokument speichern
Speichern Sie das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad:
```csharp
annotator.Save(outputPath);
```
## Schritt 6: Erfolgsmeldung anzeigen
Informieren Sie den Benutzer, dass das Dokument erfolgreich gespeichert wurde:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Abschluss
Zusammenfassend lässt sich sagen, dass GroupDocs.Annotation für .NET das Hinzufügen von Anmerkungen zu Dokumenten vereinfacht und so die Zusammenarbeit und die Dokumentenprüfung verbessert. Mit den in diesem Handbuch beschriebenen Schritten können Sie Dokumentanmerkungsfunktionen nahtlos in Ihre .NET-Anwendungen integrieren.
## Häufig gestellte Fragen
### Ist GroupDocs.Annotation mit allen Dokumentformaten kompatibel?
Ja, GroupDocs.Annotation unterstützt eine Vielzahl von Dokumentformaten, darunter PDFs, Microsoft Office-Dokumente, Bilder und mehr.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen?
Absolut! GroupDocs.Annotation bietet umfangreiche Anpassungsmöglichkeiten für Anmerkungen, sodass Sie Eigenschaften wie Schriftgröße, Farbe und Stil anpassen können.
### Gibt es eine kostenlose Testversion für GroupDocs.Annotation?
Ja, Sie können auf eine kostenlose Testversion von GroupDocs.Annotation zugreifen, um die Funktionen und Möglichkeiten zu erkunden, bevor Sie einen Kauf tätigen. [Hier](https://releases.groupdocs.com/)..
### Wo finde ich Unterstützung für GroupDocs.Annotation?
Für Unterstützung und Hilfe mit GroupDocs.Annotation können Sie die GroupDocs besuchen [Forum](https://forum.groupdocs.com/c/annotation/10) gewidmet annotationsbezogenen Fragen und Diskussionen.
### Wie erhalte ich eine temporäre Lizenz für GroupDocs.Annotation?
Sie können eine temporäre Lizenz für GroupDocs.Annotation über die GroupDocs-Website erwerben. [Webseite](https://purchase.groupdocs.com/temporary-license/), sodass Sie das Produkt umfassend bewerten können.