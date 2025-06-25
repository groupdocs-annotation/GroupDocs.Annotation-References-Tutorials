---
"description": "Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET mühelos Wasserzeichen zu Ihren Dokumenten hinzufügen. Verbessern Sie die Übersichtlichkeit und Sicherheit Ihrer Dokumente."
"linktitle": "Wasserzeichenanmerkung zum Dokument hinzufügen"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Wasserzeichenanmerkung zum Dokument hinzufügen"
"url": "/de/net/unlocking-annotation-power/add-watermark-annotation/"
"weight": 28
---

# Wasserzeichenanmerkung zum Dokument hinzufügen

## Einführung
In diesem Tutorial erfahren Sie, wie Sie mithilfe von GroupDocs.Annotation für .NET ein Wasserzeichen zu einem Dokument hinzufügen. Wasserzeichen sind nützlich, um den Status eines Dokuments anzuzeigen, es als vertraulich zu kennzeichnen oder andere relevante Informationen hinzuzufügen.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1. GroupDocs.Annotation für .NET: Sie können es herunterladen von [Hier](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: Stellen Sie sicher, dass Visual Studio auf Ihrem System installiert ist.
3. Grundkenntnisse in C#: Um die Codebeispiele zu verstehen und umzusetzen, sind Kenntnisse der Programmiersprache C# erforderlich.

## Namespaces importieren

Bevor wir mit dem Codieren beginnen, importieren wir die erforderlichen Namespaces:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Lassen Sie uns nun den Vorgang des Hinzufügens einer Wasserzeichenanmerkung in mehrere Schritte unterteilen:

## Schritt 1: Ausgabepfad definieren

Zuerst müssen wir den Ausgabepfad definieren, in dem das kommentierte Dokument gespeichert wird. Wir verwenden den `Path` Klasse von `System.IO` Namespace, um den Ausgabeverzeichnispfad mit dem Dateinamen zu kombinieren.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Schritt 2: Annotator initialisieren

Als Nächstes initialisieren wir den Annotator, indem wir den Pfad des Eingabedokuments angeben. Dadurch können wir dem Dokument Anmerkungen hinzufügen.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Der Anmerkungscode wird hier eingefügt
}
```

## Schritt 3: Wasserzeichenanmerkung erstellen

Erstellen wir nun ein Wasserzeichen-Anmerkungsobjekt mit den gewünschten Eigenschaften wie Winkel, Position, Text, Schriftfarbe, Deckkraft usw.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## Schritt 4: Wasserzeichenanmerkung hinzufügen

Nun fügen wir dem Dokument die Wasserzeichenanmerkung hinzu, indem wir `Add` Methode des Annotatorobjekts.

```csharp
annotator.Add(watermark);
```

## Schritt 5: Dokument speichern

Abschließend speichern wir das kommentierte Dokument im angegebenen Ausgabepfad.

```csharp
annotator.Save(outputPath);
```

## Abschluss

In diesem Tutorial haben wir gelernt, wie man mit GroupDocs.Annotation für .NET ein Wasserzeichen zu einem Dokument hinzufügt. Wasserzeichen sind ein wertvolles Werkzeug, um Dokumente mit relevanten Informationen zu kennzeichnen oder ihren Status anzuzeigen.

## Häufig gestellte Fragen

### F: Kann ich das Erscheinungsbild der Wasserzeichenanmerkung anpassen?

A: Ja, Sie können verschiedene Eigenschaften wie Text, Schriftgröße, Farbe, Deckkraft, Position usw. anpassen, um das Wasserzeichen Ihren Anforderungen entsprechend anzupassen.

### F: Ist GroupDocs.Annotation für .NET mit verschiedenen Dokumentformaten kompatibel?

A: Ja, GroupDocs.Annotation unterstützt eine breite Palette von Dokumentformaten, darunter PDF, Microsoft Word, Excel, PowerPoint und Bildformate.

### F: Kann ich einem einzelnen Dokument mehrere Anmerkungen hinzufügen?

A: Auf jeden Fall. Mit GroupDocs.Annotation können Sie einem einzelnen Dokument mehrere Anmerkungen unterschiedlichen Typs hinzufügen und so eine umfassende Dokumentmarkierung ermöglichen.

### F: Bietet GroupDocs.Annotation Unterstützung für die gemeinsame Kommentierung?

A: Ja, GroupDocs.Annotation erleichtert die gemeinsame Kommentierung, indem es Benutzern ermöglicht, Kommentare, Antworten und Anmerkungen hinzuzufügen und so die effektive Zusammenarbeit zwischen den Teammitgliedern zu fördern.

### F: Gibt es eine Testversion von GroupDocs.Annotation für .NET?

A: Ja, Sie können eine kostenlose Testversion herunterladen von [Hier](https://releases.groupdocs.com/).