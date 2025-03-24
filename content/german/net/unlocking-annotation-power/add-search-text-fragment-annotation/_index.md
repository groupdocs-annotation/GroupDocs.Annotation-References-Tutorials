---
title: Fügen Sie dem Dokument eine Suchtextfragment-Anmerkung hinzu
linktitle: Fügen Sie dem Dokument eine Suchtextfragment-Anmerkung hinzu
second_title: GroupDocs.Annotation .NET-API
description: Entdecken Sie die Leistungsfähigkeit von GroupDocs.Annotation für .NET und fügen Sie Ihren Anwendungen mühelos Dokumentanmerkungsfunktionen hinzu.
weight: 20
url: /de/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---

# Fügen Sie dem Dokument eine Suchtextfragment-Anmerkung hinzu

## Einführung
Im Bereich der .NET-Entwicklung zeichnet sich GroupDocs.Annotation als leistungsstarkes Tool zum nahtlosen Kommentieren von Dokumenten aus. Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst in die Welt von .NET eintauchen, dieses umfassende Tutorial führt Sie durch die Grundlagen der Verwendung von GroupDocs.Annotation für .NET, vom Importieren von Namespaces bis hin zum Beherrschen der Feinheiten des Hinzufügens von Suchtextfragmentanmerkungen zu Ihrem Unterlagen.
## Einführung
GroupDocs.Annotation für .NET ermöglicht Entwicklern die mühelose Integration von Dokumentanmerkungsfunktionen in ihre Anwendungen. Mit seiner intuitiven API und den robusten Funktionen können Entwickler verschiedene Dokumentformate mit Anmerkungen versehen, darunter PDFs, Microsoft Office-Dokumente, Bilder und mehr.
## Voraussetzungen
Bevor Sie sich mit GroupDocs.Annotation für .NET befassen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

## Namespaces importieren
Importieren Sie zunächst die erforderlichen Namespaces, um auf GroupDocs.Annotation-Klassen und -Methoden in Ihrem .NET-Projekt zuzugreifen:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Schritt 1: Ausgabepfad definieren
Beginnen Sie mit der Definition des Ausgabepfads, in dem das mit Anmerkungen versehene Dokument gespeichert wird:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Schritt 2: Annotator initialisieren
 Als nächstes initialisieren Sie eine Instanz von`Annotator` Klasse, indem Sie den Pfad zu dem Dokument angeben, das Sie mit Anmerkungen versehen möchten:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Schritt 3: Erstellen Sie eine Suchtextfragment-Anmerkung
 Ein ... kreieren`SearchTextFragment` Objekt mit den gewünschten Eigenschaften, wie z. B. zu suchender Text, Schriftgröße, Schriftfamilie, Schriftfarbe und Hintergrundfarbe:
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
 Fügen Sie die erstellte Suchtextfragment-Anmerkung mithilfe von zum Dokument hinzu`Add` Methode des Annotators:
```csharp
annotator.Add(searchText);
```
## Schritt 5: Kommentiertes Dokument speichern
Speichern Sie das mit Anmerkungen versehene Dokument im angegebenen Ausgabepfad:
```csharp
annotator.Save(outputPath);
```
## Schritt 6: Erfolgsmeldung anzeigen
Informieren Sie den Benutzer darüber, dass das Dokument erfolgreich gespeichert wurde:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Abschluss
Zusammenfassend lässt sich sagen, dass GroupDocs.Annotation für .NET den Prozess des Hinzufügens von Anmerkungen zu Dokumenten vereinfacht und so die Zusammenarbeit und Dokumentüberprüfungsprozesse verbessert. Wenn Sie die in diesem Leitfaden beschriebenen Schritte befolgen, können Sie Dokumentanmerkungsfunktionen nahtlos in Ihre .NET-Anwendungen integrieren.
## FAQs
### Ist GroupDocs.Annotation mit allen Dokumentformaten kompatibel?
Ja, GroupDocs.Annotation unterstützt eine Vielzahl von Dokumentformaten, darunter PDFs, Microsoft Office-Dokumente, Bilder und mehr.
### Kann ich das Erscheinungsbild von Anmerkungen anpassen?
Absolut! GroupDocs.Annotation bietet umfangreiche Anpassungsoptionen für Anmerkungen, sodass Sie Eigenschaften wie Schriftgröße, Farbe und Stil anpassen können.
### Gibt es eine kostenlose Testversion für GroupDocs.Annotation?
 Ja, Sie können auf eine kostenlose Testversion von GroupDocs.Annotation zugreifen, um die Funktionen und Möglichkeiten zu erkunden, bevor Sie einen Kauf tätigen[Hier](https://releases.groupdocs.com/)..
### Wo finde ich Unterstützung für GroupDocs.Annotation?
 Für Unterstützung und Hilfe bei GroupDocs.Annotation können Sie GroupDocs besuchen[Forum](https://forum.groupdocs.com/c/annotation/10) ist für annotationsbezogene Fragen und Diskussionen vorgesehen.
### Wie erhalte ich eine temporäre Lizenz für GroupDocs.Annotation?
 Über GroupDocs können Sie eine temporäre Lizenz für GroupDocs.Annotation erwerben[Webseite](https://purchase.groupdocs.com/temporary-license/), sodass Sie das Produkt vollständig bewerten können.