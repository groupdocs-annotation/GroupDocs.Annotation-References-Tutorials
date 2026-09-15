---
categories:
- Java PDF Processing
date: '2026-05-21'
description: Erfahren Sie, wie Sie mit GroupDocs Durchstreichungs‑Anmerkungen zu PDFs
  in Java hinzufügen. Dieses Schritt‑für‑Schritt‑Tutorial behandelt Einrichtung, Code,
  Fehlersuche und Leistungstipps.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Java PDF Text Durchstreichungs‑Leitfaden
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  headline: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs
    Guide
  type: TechArticle
- description: Learn how to add strikeout annotations to PDFs in Java using GroupDocs.
    This step‑by‑step tutorial covers setup, code, troubleshooting, and performance
    tips.
  name: How to Add Strikeout Annotations to PDFs in Java – Complete GroupDocs Guide
  steps:
  - name: Setting Up File Paths
    text: Define the locations of your source PDF and the destination file. Incorrect
      paths are a common source of “File Not Found” errors. **Common Mistake Alert:**
      Ensure the output directory exists and is writable; GroupDocs will not auto‑create
      missing folders.
  - name: Initialize the Annotator
    text: Create an `Annotator` instance that loads the PDF into memory. **What happens
      here?** The library parses the PDF structure, builds an internal representation,
      and prepares a page‑wise annotation canvas. For multi‑hundred‑page files this
      step may take a few seconds.
  - name: Adding Comments (Optional but Recommended)
    text: '`Comment` is a class that represents a textual note attached to an annotation,
      allowing collaborators to explain the reason for the strikeout. **Real‑world
      tip:** Use comments to explain why text is being removed—this is especially
      useful in legal or editorial review workflows.'
  - name: Defining Annotation Coordinates
    text: '`Point` objects store X‑Y coordinate pairs that define the exact location
      of an annotation on a PDF page. **Coordinate System Explained:** PDF coordinates
      start at the bottom‑left corner (0,0). The example creates a horizontal line
      from (80,730) to (240,730) on the target page. **Finding the Right C'
  - name: Creating the Strikeout Annotation
    text: '`StrikeoutAnnotation` encapsulates the visual line, its style properties
      such as color and opacity, and any associated metadata for a strikeout mark.
      **Color Values:** The `fontColor` uses decimal RGB values (e.g., 65535 for bright
      yellow). Use an online converter if you need brand‑specific shades. '
  - name: Apply the Annotation
    text: '`addAnnotation` is a method of the `Annotator` that registers the prepared
      annotation with the document so it will be rendered and saved.'
  - name: Save and Clean Up
    text: '`dispose()` releases native resources held by the `Annotator` instance,
      preventing memory leaks after processing is complete. **Memory Management Note:**
      Calling `dispose()` frees native resources and prevents memory leaks when processing
      batches of PDFs.'
  type: HowTo
- questions:
  - answer: Yes. Create several `Point` objects that trace the desired path; the annotation
      will follow the supplied polyline.
    question: Can I strikeout text across multiple lines?
  - answer: The annotation will be clipped and may become invisible. Always validate
      coordinates against the page’s width and height.
    question: What happens if I specify coordinates outside the page boundaries?
  - answer: Absolutely. Use the `removeAnnotation` method with the annotation’s ID
      or filter by type to delete them programmatically.
    question: Can I remove strikeout annotations after adding them?
  - answer: GroupDocs does not impose a hard cap, but performance may degrade after
      thousands of annotations. Consider pagination or summarizing annotations for
      very large sets.
    question: Is there a limit to how many annotations I can add to a single PDF?
  - answer: Pass the password to the `Annotator` constructor. The library will decrypt
      the document in memory before applying any annotations.
    question: How do I work with password‑protected PDFs?
  type: FAQPage
tags:
- java-pdf
- annotations
- groupdocs
- document-processing
title: Wie man Durchstreichungs‑Anmerkungen zu PDFs in Java hinzufügt – Vollständiger
  GroupDocs‑Leitfaden
type: docs
url: /de/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# Wie man Durchstreichungs‑Anmerkungen zu PDFs in Java hinzufügt

Haben Sie jemals Text in einem PDF programmgesteuert durchstreichen müssen? Egal, ob Sie ein Dokument‑Review‑System bauen, einen Bearbeitungs‑Workflow erstellen oder einfach Text zum Löschen markieren müssen, **how to add strikeout**‑Annotationen in Java sind eine praktische Fähigkeit, die Zeit spart und manuellen Aufwand reduziert. In diesem umfassenden Leitfaden erfahren Sie alles, was Sie wissen müssen, um Durchstreichungs‑Annotationen mit GroupDocs.Annotation für Java zu implementieren – von der Projekt‑Einrichtung bis zur Leistungsoptimierung.

## Schnelle Antworten
- **Was ist der erste Schritt?** Fügen Sie die GroupDocs.Annotation Maven‑Abhängigkeit zu Ihrer `pom.xml` hinzu.  
- **Wie erstelle ich ein Durchstreichungs‑Annotation?** Instanziieren Sie `Annotator`, definieren Sie `StrikeoutAnnotation` mit Punkten, setzen Sie Farbe/Transparenz und rufen Sie dann `addAnnotation` auf.  
- **Kann ich Kommentare hinzufügen?** Ja, hängen Sie ein `Comment`‑Objekt an die Annotation für die Zusammenarbeit an.  
- **Was ist, wenn die Annotation falsch platziert ist?** Passen Sie die Koordinatenpunkte an; PDF verwendet ein Ursprungssystem unten‑links.  
- **Gibt es ein Limit für die Dokumentgröße?** GroupDocs verarbeitet PDFs mit mehreren hundert Seiten, ohne die gesamte Datei in den Speicher zu laden.

## Was bedeutet „how to add strikeout“ in PDF‑Anmerkungen?
Der Ausdruck „how to add strikeout“ bezieht sich auf den Vorgang, programmgesteuert eine Linie durch ausgewählten Text innerhalb eines PDF‑Dokuments zu zeichnen, indem eine Annotations‑API verwendet wird. In Java stellt GroupDocs.Annotation eine dedizierte `StrikeoutAnnotation`‑Klasse bereit, die das Rendern, Stylen und die Persistenz von Durchstreichungs‑Markierungen übernimmt.

## Warum GroupDocs für Java PDF‑Durchstreichungen verwenden?
GroupDocs.Annotation unterstützt **50+ Eingabe‑ und Ausgabeformate** — einschließlich PDF, DOCX, XLSX, PPTX, HTML und gängige Bildtypen — so dass Sie nicht auf einen einzigen Dateityp festgelegt sind. Es bietet eine High‑Level‑API, die die Low‑Level‑PDF‑Struktur abstrahiert, automatisch Schrift‑Einbettung, Seiten‑Rendering und Annotations‑Persistenz handhabt, sodass Entwickler sich auf die Geschäftslogik statt auf PDF‑Interna konzentrieren können.

## Voraussetzungen und Setup‑Anforderungen

### Wesentliche Anforderungen
- **Java Development Kit (JDK):** Version 8 oder höher (JDK 11+ empfohlen für optimale Garbage‑Collection).  
- **GroupDocs.Annotation für Java:** Integriert über Maven (siehe das Maven‑Snippet unten).  
- **IDE:** IntelliJ IDEA, Eclipse oder ein beliebiger Java‑kompatibler Editor.

### Maven‑Abhängigkeits‑Setup
Fügen Sie den folgenden Abhängigkeits‑Block zu Ihrer `pom.xml` hinzu:

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/annotation/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>25.2</version>
    </dependency>
</dependencies>
```

**Pro Tip:** Überprüfen Sie stets die neueste Version auf der GroupDocs‑Release‑Seite; neuere Releases fügen Funktionen hinzu und beheben Fehler, die das Rendering von Annotationen beeinflussen können.

### Lizenzbeschaffung
GroupDocs.Annotation erfordert für die Produktion eine gültige Lizenz. Sie haben drei Optionen:

- **Kostenlose Testversion:** Herunterladen von [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)
- **Temporäre Lizenz:** Fordern Sie einen Entwicklungsschlüssel an unter [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Vollständige Lizenz:** Kaufen Sie für die Produktion unter [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

Die Testversion fügt ein dezentes Wasserzeichen hinzu, planen Sie Ihre Tests entsprechend.

## Schritt‑für‑Schritt Implementierungs‑Leitfaden

### Verständnis der Kernkomponenten
Die folgenden Definitionen geben Ihnen ein schnelles mentales Modell:

- **Annotator:** Das primäre API‑Objekt, das ein PDF lädt und Annotationsmethoden bereitstellt.  
- **StrikeoutAnnotation:** Stellt die visuelle Durchstreichungs‑Linie und deren Stiloptionen dar.  
- **Point:** Ein Koordinatenpaar (X, Y), das der Bibliothek sagt, wo die Linie beginnt und endet.  
- **Comment:** Optionaler Text, der einer Annotation für die Zusammenarbeit angehängt wird.

### Schritt 1: Dateipfade einrichten
Definieren Sie die Orte Ihrer Quell‑PDF und der Zieldatei. Falsche Pfade sind eine häufige Ursache für „File Not Found“-Fehler.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Common Mistake Alert:** Stellen Sie sicher, dass das Ausgabeverzeichnis existiert und beschreibbar ist; GroupDocs erstellt fehlende Ordner nicht automatisch.

### Schritt 2: Annotator initialisieren
Erstellen Sie eine `Annotator`‑Instanz, die das PDF in den Speicher lädt.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**What happens here?** Die Bibliothek parsed die PDF‑Struktur, baut eine interne Repräsentation auf und bereitet eine seitenweise Annotations‑Canvas vor. Bei PDFs mit mehreren hundert Seiten kann dieser Schritt einige Sekunden dauern.

### Schritt 3: Kommentare hinzufügen (optional aber empfohlen)
`Comment` ist eine Klasse, die eine textuelle Notiz darstellt, die einer Annotation angehängt ist, sodass Mitwirkende den Grund für die Durchstreichung erklären können.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Real‑world tip:** Verwenden Sie Kommentare, um zu erklären, warum Text entfernt wird — dies ist besonders nützlich in rechtlichen oder redaktionellen Review‑Workflows.

### Schritt 4: Annotationskoordinaten definieren
`Point`‑Objekte speichern X‑Y‑Koordinatenpaare, die den genauen Ort einer Annotation auf einer PDF‑Seite festlegen.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Coordinate System Explained:** PDF‑Koordinaten beginnen in der unteren linken Ecke (0,0). Das Beispiel erstellt eine horizontale Linie von (80,730) bis (240,730) auf der Ziel‑Seite.

**Finding the Right Coordinates:** Viele Entwickler erstellen einen Helfer, der Prozentsätze der Seitenbreite/Höhe in absolute Punkte umwandelt, wodurch der Code gegenüber unterschiedlichen Seitengrößen robust wird.

### Schritt 5: Durchstreichungs‑Annotation erstellen
`StrikeoutAnnotation` kapselt die visuelle Linie, ihre Stil‑Eigenschaften wie Farbe und Transparenz sowie alle zugehörigen Metadaten für eine Durchstreichungs‑Markierung.

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535); // Yellow
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0); 
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

**Color Values:** Der `fontColor` verwendet dezimale RGB‑Werte (z. B. 65535 für helles Gelb). Nutzen Sie einen Online‑Konverter, wenn Sie markenspezifische Farbtöne benötigen.

**Opacity Recommendation:** Eine Transparenz von `0.7` (70 %) bietet einen klaren visuellen Hinweis, während der zugrunde liegende Text lesbar bleibt.

### Schritt 6: Annotation anwenden
`addAnnotation` ist eine Methode des `Annotator`, die die vorbereitete Annotation im Dokument registriert, sodass sie gerendert und gespeichert wird.

```java
annotator.add(strikeout);
```

### Schritt 7: Speichern und Aufräumen
`dispose()` gibt native Ressourcen frei, die von der `Annotator`‑Instanz gehalten werden, und verhindert Speicherlecks nach Abschluss der Verarbeitung.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Memory Management Note:** Der Aufruf von `dispose()` befreit native Ressourcen und verhindert Speicherlecks beim Verarbeiten von PDF‑Stapeln.

## Häufige Probleme und deren Behebung

### Problem 1: „File Not Found“-Fehler
**Symptoms:** Ausnahme während der `Annotator`‑Konstruktion geworfen.  
**Solution:** Überprüfen Sie sowohl Eingabe‑ als auch Ausgabepfade und bestätigen Sie, dass die Anwendung Lese‑/Schreibrechte hat.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### Problem 2: Durchstreichung erscheint an falscher Stelle
**Symptoms:** Die Linie stimmt nicht mit dem beabsichtigten Text überein.  
**Solution:** Denken Sie daran, dass PDF‑Y‑Koordinaten nach oben zunehmen. Nutzen Sie ein visuelles Debug‑Tool oder geben Sie die Seitendimensionen aus, um die Punkte fein abzustimmen.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### Problem 3: Annotation nicht sichtbar
**Symptoms:** Nach dem Speichern wird keine Durchstreichung angezeigt.  
**Possible Causes & Fixes:**
- **Transparenz zu niedrig:** Setzen Sie vorübergehend die Transparenz auf `1.0`, um die Sichtbarkeit zu prüfen.  
- **Farbmischung:** Verwenden Sie eine kontrastreiche Farbe wie Rot (`255`).  
- **Falscher Seitenindex:** Seitenzahlen beginnen bei Null; stellen Sie sicher, dass Sie die richtige Seite anvisieren.

### Problem 4: Speicherprobleme bei großen Dateien
**Symptoms:** `OutOfMemoryError` oder langsame Performance.  
**Solutions:**
- Dokumente in kleineren Stapeln verarbeiten.  
- Verwenden Sie die Streaming‑API, falls verfügbar.  
- Rufen Sie immer `dispose()` nach jedem Dokument auf.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## Praxisanwendungen und Anwendungsfälle

### Rechtliche Dokumentenprüfung
Anwaltskanzleien annotieren Verträge mit Durchstreichungen, um gelöschte Klauseln zu kennzeichnen und gleichzeitig eine Prüfspur zu erhalten.

### Wissenschaftliche Arbeiten bearbeiten
Professoren nutzen Durchstreichungen, um Entfernungen während des Peer‑Reviews vorzuschlagen, wobei der Originaltext für Kontext erhalten bleibt.

### Content‑Management‑Systeme
Veröffentlichungsplattformen markieren automatisch policy‑verletzende Abschnitte mit Durchstreichungen, bevor eine manuelle Moderation erfolgt.

### Versionskontrolle für Dokumente
Unternehmen behandeln Durchstreichungs‑Annotationen als „Lösch‑Marker“ in einem dokument‑zentrierten Versions‑Control‑Workflow, ähnlich wie Code‑Diffs.

## Tipps zur Leistungsoptimierung

### Stapelverarbeitungs‑Strategie
Beim Umgang mit vielen PDFs, nach Möglichkeit eine einzelne `Annotator`‑Instanz wiederverwenden und Dateien in parallelen Threads verarbeiten.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### Best Practices für Speicherverwaltung
- Rufen Sie `dispose()` für jeden `Annotator` auf.  
- Begrenzen Sie gleichzeitige Dokumentladungen, um den Heap‑Druck zu vermeiden.  
- Überwachen Sie den JVM‑Speicherverbrauch mit Tools wie VisualVM.

### Koordinaten‑Caching
Wenn Sie dasselbe Annotations‑Layout über mehrere Dateien hinweg anwenden, cachen Sie die `Point`‑Objekte, um Neukalkulation zu vermeiden.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## Erweiterte Anpassungsoptionen

### Dynamische Farbauswahl
Wählen Sie Farben zur Laufzeit basierend auf Geschäftsregeln (z. B. Rot für kritische Löschungen, Gelb für vorläufige).

```java
// Choose colors based on annotation type or user
int colorByPriority = getPriorityColor(annotationType);
strikeout.setFontColor(colorByPriority);

private int getPriorityColor(String type) {
    switch(type) {
        case "HIGH": return 255;    // Red
        case "MEDIUM": return 65535; // Yellow  
        case "LOW": return 65280;   // Green
        default: return 0;          // Black
    }
}
```

### Mehrzeilige Durchstreichungen
Erstellen Sie eine Reihe von `Point`‑Paaren, um eine Zick‑Zack‑Linie zu zeichnen, die mehrere Textzeilen kreuzt.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## Checkliste zur Fehlersuche
1. **Dateiberechtigungen:** Lesen/Schreiben‑Zugriff prüfen.  
2. **Bibliotheksversion:** Stellen Sie sicher, dass Sie eine unterstützte GroupDocs.Annotation‑Version verwenden.  
3. **Lizenzstatus:** Bestätigen Sie, dass die Lizenzdatei korrekt referenziert wird.  
4. **PDF‑Kompatibilität:** Prüfen Sie, ob das PDF nicht beschädigt ist und innerhalb der unterstützten Größenbeschränkungen liegt.  
5. **Koordinatenvalidierung:** Stellen Sie sicher, dass alle Punkte innerhalb der Seitenränder liegen.  
6. **Heap‑Speicher:** Erhöhen Sie das JVM‑Argument `-Xmx`, wenn Sie sehr große Dateien verarbeiten.

## Häufig gestellte Fragen

**F: Kann ich Text über mehrere Zeilen hinweg durchstreichen?**  
**A:** Ja. Erstellen Sie mehrere `Point`‑Objekte, die den gewünschten Pfad nachzeichnen; die Annotation folgt dem angegebenen Polyline.

**F: Was passiert, wenn ich Koordinaten außerhalb der Seitenränder angebe?**  
**A:** Die Annotation wird beschnitten und kann unsichtbar werden. Validieren Sie stets die Koordinaten gegenüber der Seitenbreite und -höhe.

**F: Kann ich Durchstreichungs‑Annotationen nach dem Hinzufügen entfernen?**  
**A:** Absolut. Verwenden Sie die Methode `removeAnnotation` mit der ID der Annotation oder filtern Sie nach Typ, um sie programmgesteuert zu löschen.

**F: Gibt es ein Limit, wie viele Annotationen ich zu einem einzelnen PDF hinzufügen kann?**  
**A:** GroupDocs legt keine harte Obergrenze fest, aber die Performance kann nach Tausenden von Annotationen abnehmen. Erwägen Sie Paginierung oder Zusammenfassung von Annotationen bei sehr großen Mengen.

**F: Wie gehe ich mit passwortgeschützten PDFs um?**  
**A:** Übergeben Sie das Passwort dem `Annotator`‑Konstruktor. Die Bibliothek entschlüsselt das Dokument im Speicher, bevor Annotationen angewendet werden.

**F: Wie kann ich PDFs mit unterschiedlichen Seitengrößen und -orientierungen handhaben?**  
**A:** Rufen Sie für jede Seite die Dimensionen über `annotator.getPageInfo(pageNumber)` ab und berechnen Sie die Koordinaten relativ zu diesen Dimensionen, um eine konsistente Platzierung sicherzustellen.

## Fazit
Sie haben nun eine vollständige, produktionsreife Lösung für **how to add strikeout**‑Annotationen zu PDFs in Java mit GroupDocs.Annotation. Durch das Beherrschen von Dateipfaden, Koordinatenberechnung und Ressourcenverwaltung können Sie diese Fähigkeit in Dokument‑Review‑Tools, Content‑Pipelines oder jede Java‑basierte Anwendung einbetten, die präzises visuelles Feedback benötigt.

**Nächste Schritte**
1. Klonen Sie das Beispielprojekt und führen Sie es mit einer Beispiel‑PDF aus.  
2. Experimentieren Sie mit verschiedenen Farben, Transparenzen und Kommentartexten.  
3. Integrieren Sie den Annotations‑Workflow in Ihren bestehenden Dokument‑Verarbeitungs‑Service.  
4. Erkunden Sie verwandte Annotationsarten — Hervorhebungen, Haftnotizen und Form‑Annotationen — um Ihr PDF‑Manipulations‑Toolkit zu erweitern.

Bereit für mehr? Tauchen Sie in die offizielle Dokumentation ein, um tiefere API‑Einblicke zu erhalten.

## Zusätzliche Ressourcen

- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - Allgemeine Dokumentation für GroupDocs‑Bibliotheken
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - Vollständige API‑Referenz  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - Methoden‑für‑Methoden‑Details  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - Halten Sie Ihre Bibliothek auf dem neuesten Stand  
- [Purchase License](https://purchase.groupdocs.com/buy) - Produktionsbereite Lizenzierung  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - Vor dem Kauf evaluieren  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - Entwicklungstests  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - Community‑Hilfe und offizieller Support  

---

**Last Updated:** 2026-05-21  
**Tested With:** GroupDocs.Annotation 23.12 for Java  
**Author:** GroupDocs

## Verwandte Tutorials

- [Add PDF Annotation Java – Complete GroupDocs Guide](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)
- [Java PDF Annotation Tutorial - Complete Guide to Highlighting PDFs](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)
- [How to Add Arrow to PDF in Java – Complete GroupDocs Tutorial](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)