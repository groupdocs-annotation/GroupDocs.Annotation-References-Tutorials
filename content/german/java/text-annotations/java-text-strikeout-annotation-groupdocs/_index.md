---
categories:
- Java Development
date: '2026-03-30'
description: Erfahren Sie, wie Sie in Java eine Durchstreichungs‑Annotation mit GroupDocs.Annotation
  hinzufügen. Schritt‑für‑Schritt‑Anleitung mit Codebeispielen, Tipps zur Fehlerbehebung
  und bewährten Methoden für die Dokumentenmarkierung.
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: Strikeout-Annotation hinzufügen Java‑Tutorial mit GroupDocs
type: docs
url: /de/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# Strikeout-Annotation in Java hinzufügen – Vollständiger GroupDocs-Leitfaden

Haben Sie sich schon einmal dabei erwischt, wie Sie ein Dokument anstarren und denken: „Ich muss diesen Text durchstreichen, aber ich kann nicht einfach einen roten Stift nehmen“? Sie sind nicht allein. Egal, ob Sie ein Dokumenten‑Review‑System bauen, einen Bearbeitungs‑Workflow erstellen oder einfach Text in Ihrer Java‑Anwendung zum Löschen markieren müssen, **add strikeout annotation java** ist eine wesentliche Fähigkeit. In diesem Tutorial führen wir Sie durch alles, was Sie wissen müssen, um eine Text‑Durchstreich‑Funktion zu implementieren, die in der Produktion tatsächlich funktioniert.

## Schnelle Antworten
- **Welche Bibliothek unterstützt Durchstreich‑Annotationen in Java?** GroupDocs.Annotation for Java  
- **Welches primäre Schlüsselwort sollte ich für SEO anvisieren?** add strikeout annotation java  
- **Benötige ich eine Lizenz, um den Beispielcode auszuführen?** Eine kostenlose Testversion oder temporäre Lizenz reicht für die Entwicklung; für die Produktion ist eine Voll‑Lizenz erforderlich.  
- **Kann ich das mit PDF-, DOCX- und PPTX‑Dateien verwenden?** Ja – GroupDocs.Annotation unterstützt alle gängigen Dokumentformate.  
- **Welche Java‑Version wird benötigt?** JDK 8 oder höher (JDK 11+ empfohlen).

## Was ist add strikeout annotation java?
Eine Durchstreich‑Annotation zeichnet eine Linie durch ausgewählten Text und zeigt visuell an, dass der Inhalt entfernt oder ignoriert werden soll. Es ist eine nicht‑destruktive Methode, um Löschungen vorzuschlagen, während der Originaltext für Prüfpfade oder kollaborative Überprüfungen intakt bleibt.

## Warum Durchstreich‑Annotationen in Java‑Anwendungen verwenden?
- **Dokumenten‑Review‑Workflows** – Prüfer können unerwünschten Text markieren, ohne die Quelle zu ändern.  
- **Kollaboratives Bearbeiten** – Teammitglieder sehen vorgeschlagene Löschungen sofort.  
- **Rechtliche und Compliance‑Anforderungen** – Ein klarer Prüfpfad von Änderungen wird erhalten.  
- **Content‑Migration** – Veraltete Abschnitte markieren, bevor Inhalte zwischen Systemen verschoben werden.

## Voraussetzungen und Umgebungseinrichtung
Sie benötigen Folgendes, bevor Sie mit dem Code beginnen:

- **Java Development Kit (JDK)** 8+ (JDK 11+ empfohlen)  
- **Maven oder Gradle** für das Abhängigkeitsmanagement  
- **IDE** – IntelliJ IDEA, Eclipse oder VS Code mit Java‑Erweiterungen  
- **GroupDocs.Annotation‑Bibliothek** – wir verwenden Version 25.2 in den Beispielen  

*Nice to have:* Grundkenntnisse von Java‑Annotationen und PDF‑Verarbeitung.

## GroupDocs.Annotation für Java einrichten

### Maven‑Konfiguration, die tatsächlich funktioniert
Fügen Sie das Repository und die Abhängigkeit zu Ihrer `pom.xml` exakt wie gezeigt hinzu:

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

### Lizenzbeschaffung
GroupDocs bietet mehrere Lizenzierungsoptionen:

- **Kostenlose Testversion** – ideal zum Testen (keine Kreditkarte erforderlich)  
- **Temporäre Lizenz** – ideal für Entwicklung und Staging  
- **Voll‑Lizenz** – für den Produktionseinsatz erforderlich; siehe die [Kaufseite](https://purchase.groupdocs.com/buy)

> **Pro‑Tipp:** Beginnen Sie mit der kostenlosen Testversion, um die API zu erkunden, und wechseln Sie zu einer temporären Lizenz, wenn Sie bereit sind, ein Feature für die reale Welt zu entwickeln.

### Schnell‑Check‑Setup
Führen Sie dieses Minimalprogramm aus, um zu überprüfen, ob die Bibliothek korrekt geladen wird:

```java
import com.groupdocs.annotation.Annotator;

public class DocumentSetup {
    public static void main(String[] args) {
        try {
            Annotator annotator = new Annotator("path/to/your/document.pdf");
            System.out.println("GroupDocs.Annotation is ready to use!");
            annotator.dispose();
        } catch (Exception e) {
            System.out.println("Setup issue: " + e.getMessage());
        }
    }
}
```

Wenn die Konsole die Erfolgsmeldung ohne Fehler ausgibt, sind Sie bereit, Durchstreich‑Annotationen hinzuzufügen.

## Wie man add strikeout annotation java hinzufügt

Unten finden Sie eine vollständige, produktionsreife Implementierung, aufgeteilt in klare Schritte.

### Schritt 1 – Annotator initialisieren
Erstellen Sie eine `Annotator`‑Instanz, die auf das Quelldokument verweist:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **Warum das wichtig ist:** Die Verwendung eines absoluten oder korrekt aufgelösten relativen Pfads verhindert „file not found“-Ausnahmen.

### Schritt 2 – (Optional) Kommentarantworten vorbereiten
Das Hinzufügen von Antworten macht die Annotation kollaborativ:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

Diese Kommentare erscheinen, wenn ein Benutzer über die Durchstreichung fährt.

### Schritt 3 – Durchstreich‑Bereich definieren
Geben Sie das Rechteck an, das den Text umschließt, den Sie durchstreichen möchten:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **Koordinaten‑Tipp:** Ursprung (0,0) ist die obere linke Ecke der Seite; X wächst nach rechts, Y nach unten. Verwenden Sie einen PDF‑Viewer, der Koordinaten anzeigt, um diese Werte fein abzustimmen.

### Schritt 4 – Durchstreich‑Annotation konfigurieren
Legen Sie das Aussehen, die Seitenzahl fest und hängen Sie die Kommentare an:

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535);  // Yellow color
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0);
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

*Hinweis zur Farbe:* `65535` entspricht Gelb im ganzzahligen RGB‑Format. Ändern Sie den Wert, um andere Farben zu verwenden.

### Schritt 5 – Annotation anwenden und speichern
Fügen Sie die Annotation dem Dokument hinzu und schreiben Sie die Ausgabedatei:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### Schritt 6 – Ressourcen bereinigen (Kritisch!)
Entsorgen Sie den Annotator immer, um native Ressourcen freizugeben:

```java
if (annotator != null) {
    annotator.dispose();
}
```

In der Produktion sollten Sie die Verwendung in einem try‑with‑resources‑Block oder einer `try/finally`‑Konstruktion einbetten.

## Häufige Probleme und deren Behebung

| Problem | Symptom | Lösung |
|---------|---------|--------|
| **Datei nicht gefunden** | `Annotator` wirft eine Ausnahme | Verwenden Sie absolute Pfade, prüfen Sie Lese­berechtigungen, stellen Sie sicher, dass kein anderer Prozess die Datei sperrt |
| **Falsche Koordinaten** | Durchstreichung erscheint nicht am vorgesehenen Text | Überprüfen Sie das Koordinatensystem des PDF‑Viewers erneut; passen Sie die Punkte entsprechend an |
| **Annotation unsichtbar** | Keine sichtbare Durchstreichung nach dem Speichern | Erhöhen Sie `opacity` (z. B. `0.9`), prüfen Sie `pageNumber` (0‑basiert), stellen Sie sicher, dass die Punkte ein korrektes Rechteck bilden |
| **OutOfMemoryError** | Anwendung stürzt bei großen PDFs ab | Erhöern Sie den JVM‑Heap (`-Xmx2048m`), verarbeiten Sie Dokumente stapelweise, rufen Sie stets `dispose()` auf |

## Leistungs‑Best Practices für die Produktion

### Speicherverwaltung
```java
// Good: try‑with‑resources (Java 7+)
try (Annotator annotator = new Annotator(documentPath)) {
    // annotation logic here
} // annotator automatically disposed

// Alternative: explicit disposal
Annotator annotator = null;
try {
    annotator = new Annotator(documentPath);
    // annotation logic here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

### Stapelverarbeitungs‑Strategie
Wenn Sie Dutzende oder Hunderte von Dateien annotieren müssen:

- Verarbeiten Sie 10‑20 Dokumente pro Batch.  
- Protokollieren Sie Erfolg/Misserfolg für jede Datei.  
- Initialisieren Sie den `Annotator` für jedes Dokument neu, um Speicherlecks zu vermeiden.  

### Caching‑Tipps
- Häufig verwendete Dokumentvorlagen zwischenspeichern.  
- Vorab berechnete Koordinaten‑Maps für Standard‑Layouts speichern.

## Praxisbeispiele

1. **Dokumenten‑Review‑Systeme** – Redakteure schlagen Löschungen vor, ohne den Originalvertrag zu ändern.  
2. **Rechtliche Änderungen** – Anwälte verfolgen das Entfernen von Klauseln, während die ursprüngliche Formulierung für Audits erhalten bleibt.  
3. **Akademisches Peer‑Review** – Gutachter markieren Abschnitte zur Entfernung und fügen Inline‑Kommentare hinzu.  
4. **Content‑Migration** – Bei CMS‑Migrationen heben Durchstreichungen veraltete Texte hervor, die ersetzt werden müssen.

## Erweiterte Anpassungen

### Benutzerdefiniertes Styling
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### Metadaten hinzufügen
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## Fehlersuch‑Checkliste
- ✅ Können Sie die Quelldatei manuell öffnen?  
- ✅ Sind alle GroupDocs‑Abhängigkeiten im Klassenpfad vorhanden?  
- ✅ Bilden die Punkte ein gültiges Rechteck?  
- ✅ Ist die Seitenzahl korrekt (0‑basiert)?  
- ✅ Gibt es genügend Heap‑Speicher?  
- ✅ Haben Sie Schreibrechte für den Ausgabordner?  
- ✅ Wird das Dokumentformat unterstützt (PDF, DOCX, PPTX usw.)?

## Häufig gestellte Fragen

**F: Kann ich GroupDocs.Annotation in einem Spring‑Boot‑Service verwenden?**  
A: Ja. Fügen Sie die Maven‑Abhängigkeit hinzu, injizieren Sie eine Service‑Klasse, die den `Annotator` erstellt, und verwalten Sie dessen Lebenszyklus mit den Bean‑Scopes von Spring.

**F: Welche Dokumentformate unterstützen Durchstreich‑Annotationen?**  
A: PDF, DOCX, PPTX und viele andere Formate, die von GroupDocs.Annotation unterstützt werden. PDF bietet die präziseste Koordinaten‑Verarbeitung.

**F: Wie gehe ich mit Dokumenten um, die unterschiedliche Seitengrößen haben?**  
A: Rufen Sie die Seitenabmessungen über `annotator.getPageInfo(pageNumber)` ab und skalieren Sie Ihre Koordinaten entsprechend.

**F: Ist es möglich, eine bestehende Durchstreich‑Annotation zu bearbeiten oder zu löschen?**  
A: Ja. Verwenden Sie `annotator.getAnnotations(pageNumber)`, um sie abzurufen, und dann `annotator.update(updatedAnnotation)` bzw. `annotator.delete(annotationId)`.

**F: Welche Auswirkungen hat das Hinzufügen vieler Annotationen auf die Performance?**  
A: Das Hinzufügen von Hunderten von Annotationen ist im Allgemeinen unproblematisch, aber überwachen Sie den Speicherverbrauch. Bei sehr großen Annotationensätzen sollten Sie in Erwägung ziehen, die Ansicht zu paginieren oder Annotationen bei Bedarf lazy zu laden.

## Fazit
Sie haben nun einen vollständigen, produktionsreifen Leitfaden zum **add strikeout annotation java** mit GroupDocs.Annotation. Beginnen Sie mit dem einfachen Schnell‑Check‑Beispiel und skalieren Sie dann zu Stapelverarbeitung, benutzerdefiniertem Styling und Metadaten‑Anreicherung. Denken Sie daran, Koordinaten sorgfältig zu testen, Ressourcen verantwortungsbewusst zu verwalten und das passende Lizenzmodell für Ihre Umgebung zu wählen.

Bereit, mehr zu entdecken? Schauen Sie sich weitere Annotationstypen an – Highlight, Note, Image, Arrow und Watermark – um eine voll ausgestattete Dokument‑Zusammenarbeits‑Suite zu erstellen.

---

**Zuletzt aktualisiert:** 2026-03-30  
**Getestet mit:** GroupDocs.Annotation 25.2 für Java  
**Autor:** GroupDocs  

**Zusätzliche Ressourcen**
- [GroupDocs Annotation Dokumentation](https://docs.groupdocs.com/annotation/java/)
- [API‑Referenzhandbuch](https://reference.groupdocs.com/annotation/java/)
- [Neueste Version herunterladen](https://releases.groupdocs.com/annotation/java/)
- [Vollständige Lizenz kaufen](https://purchase.groupdocs.com/buy)
- [Kostenlose Testversion starten](https://releases.groupdocs.com/annotation/java/)
- [Temporäre Lizenz erhalten](https://purchase.groupdocs.com/temporary-license/)
- [Community‑Support‑Forum](https://forum.groupdocs.com/c/annotation/)