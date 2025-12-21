---
categories:
- Java Development
date: '2025-12-21'
description: Erfahren Sie, wie Sie saubere PDF‑Java‑Dateien erstellen und PDFs in
  Java mit GroupDocs.Annotation annotieren, inklusive vollständiger Codebeispiele
  und Tipps zur Fehlerbehebung.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2025-12-21'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'Erstelle ein sauberes PDF in Java: Unterstreichungs‑Anmerkungen mit GroupDocs'
type: docs
url: /de/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Saubere PDF‑Java-Dateien erstellen: Unterstreichungs‑Anmerkungen mit GroupDocs

## Einleitung

Haben Sie Schwierigkeiten mit Dokumentenverwaltung und Zusammenarbeit in Ihren Java‑Anwendungen? Sie sind nicht allein. Viele Entwickler stehen vor der Herausforderung, robuste Dokument‑Anmerkungs‑Funktionen zu implementieren, die zuverlässig über verschiedene Dateiformate hinweg funktionieren.

In diesem Leitfaden **erstellen Sie saubere PDF‑Java‑Dateien** und lernen, wie Sie **PDF in Java annotieren** mit GroupDocs.Annotation. Am Ende dieses Tutorials wissen Sie genau, wie Sie Unterstreichungs‑Anmerkungen mit Kommentaren hinzufügen, vorhandene Anmerkungen entfernen und diese Funktionen nahtlos in Ihre Projekte integrieren.

**Was Sie in diesem Leitfaden beherrschen werden:**
- GroupDocs.Annotation in Ihrem Java‑Projekt einrichten (auf die richtige Weise)  
- Unterstreichungs‑Anmerkungen mit benutzerdefinierten Kommentaren und Styling hinzufügen  
- Alle Anmerkungen entfernen, um saubere Dokumentversionen zu erzeugen  
- Häufige Probleme, denen Entwickler begegnen, beheben  
- Leistung für Produktionsanwendungen optimieren  

Egal, ob Sie ein Dokument‑Review‑System, eine Lernplattform oder ein kollaboratives Bearbeitungstool bauen – dieses Tutorial liefert Ihnen praxisnahe, getestete Code‑Beispiele.

## Schnelle Antworten
- **Wie füge ich eine Unterstreichungs‑Anmerkung hinzu?** Verwenden Sie `UnderlineAnnotation` und `annotator.add()`, dann speichern Sie das Dokument.  
- **Wie erstelle ich eine saubere PDF‑Java‑Datei?** Laden Sie die annotierte Datei, setzen Sie `AnnotationType.NONE` in `SaveOptions` und speichern Sie eine neue Kopie.  
- **Welche Bibliotheken werden benötigt?** GroupDocs.Annotation v25.2 (oder neuer) und das zugehörige Maven‑Repository.  
- **Benötige ich eine Lizenz für die Produktion?** Ja – wenden Sie eine gültige GroupDocs‑Lizenz an, um Wasserzeichen zu vermeiden.  
- **Kann ich mehrere Dokumente effizient verarbeiten?** Verpacken Sie jedes `Annotator`‑Objekt in einen try‑with‑resources‑Block und geben Sie es nach jeder Datei frei.

## Wie man saubere PDF‑Java‑Dateien erstellt
Eine saubere PDF‑Java‑Datei zu erstellen bedeutet, eine Version des Dokuments **ohne jegliche Anmerkungen** zu erzeugen, während der ursprüngliche Inhalt erhalten bleibt. Das ist nützlich für die endgültige Verteilung, Archivierung oder wenn Sie nach einem Review‑Durchlauf eine „saubere“ Kopie teilen möchten.

GroupDocs.Annotation macht das unkompliziert: Laden Sie die annotierte Datei, konfigurieren Sie `SaveOptions`, um alle Anmerkungstypen auszuschließen, und speichern Sie das Ergebnis. Die Schritte werden später im Abschnitt **Anmerkungen entfernen** veranschaulicht.

## Wie man PDF in Java mit GroupDocs annotiert
GroupDocs.Annotation bietet eine umfangreiche API für **PDF in Java annotieren**. Sie unterstützt eine Vielzahl von Anmerkungstypen, darunter Hervorhebungen, Stempel und Unterstreichungen. In diesem Tutorial konzentrieren wir uns auf Unterstreichungs‑Anmerkungen, da sie häufig zum Hervorheben von Text verwendet werden und gleichzeitig Thread‑Kommentare ermöglichen.

## Voraussetzungen und Umgebungseinrichtung

### Was Sie vor dem Start benötigen

**Entwicklungsumgebungs‑Anforderungen:**
- Java Development Kit (JDK) 8 oder höher (JDK 11+ empfohlen)  
- Maven 3.6+ oder Gradle 6.0+ für das Abhängigkeits‑Management  
- IDE wie IntelliJ IDEA, Eclipse oder VS Code mit Java‑Erweiterungen  
- Mindestens 2 GB verfügbarer RAM (Dokumentenverarbeitung kann speicherintensiv sein)

**Wissens‑Voraussetzungen:**
Sie sollten mit grundlegenden Java‑Konzepten vertraut sein – Objektinitialisierung, Methodenaufrufe und Maven‑Abhängigkeiten. Erfahrung mit Drittanbieter‑Bibliotheken beschleunigt die Einarbeitung.

**Testdokumente:**
Halten Sie ein paar Beispiel‑PDFs bereit. Textbasierte PDFs funktionieren am besten; gescannte Bilder benötigen ggf. OCR vor der Annotation.

### Maven‑Einrichtung: GroupDocs in Ihr Projekt einbinden

So konfigurieren Sie Ihr Maven‑Projekt korrekt (dies verwirrt viele Entwickler beim ersten Versuch):

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

**Wichtig:** Version 25.2 ist zum Zeitpunkt des Schreibens die neueste stabile Veröffentlichung. Prüfen Sie das GroupDocs‑Repository regelmäßig auf neuere Versionen mit Fehlerbehebungen und Leistungsverbesserungen.

### Lizenz‑Einrichtung (nicht überspringen)

**Für Entwicklung/Test:**  
Laden Sie die kostenlose Testversion von der GroupDocs‑Website herunter. Der Test enthält alle Funktionen, fügt jedoch ein Wasserzeichen zu verarbeiteten Dokumenten hinzu.

**Für Produktion:**  
Kaufen Sie eine Lizenz und wenden Sie sie beim Anwendungsstart an. Ohne gültige Lizenz sind Produktions‑Builds eingeschränkt.

## Implementierungs‑Leitfaden: Unterstreichungs‑Anmerkungen hinzufügen

### Verständnis des Anmerkungs‑Workflows

Bevor wir zum Code kommen, betrachten wir den vier‑stufigen Workflow, der abläuft, wenn Sie **PDF in Java annotieren**:

1. **Dokumenten‑Laden** – `Annotator` liest die Datei in den Speicher.  
2. **Anmerkungs‑Erstellung** – Eigenschaften wie Position, Stil und Kommentare festlegen.  
3. **Anmerkungs‑Anwendung** – Die Bibliothek fügt die Anmerkung in die PDF‑Struktur ein.  
4. **Dokumenten‑Speichern** – Die modifizierte Datei persistieren, optional das Original erhalten.

Der Prozess ist nicht destruktiv; die Quelldatei bleibt unverändert, solange Sie sie nicht überschreiben.

### Schritt 1: Annotator initialisieren und Dokument laden

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Pro‑Tipp:** Verwenden Sie absolute Pfade während der Entwicklung, um „Datei nicht gefunden“-Fehler zu vermeiden. In der Produktion sollten Sie Ressourcen aus dem Klassenpfad oder einem Cloud‑Speicher‑Bucket laden.

### Schritt 2: Kommentare und Antworten erstellen (der kollaborative Teil)

```java
import com.groupdocs.annotation.models.Reply;
import java.util.Calendar;
import java.util.ArrayList;
import java.util.List;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```

**Praxisbeispiel:** Reviewer können einen bestimmten Absatz diskutieren, indem sie Thread‑Antworten hinzufügen, die das Gespräch an die jeweilige Anmerkung binden.

### Schritt 3: Anmerkungs‑Koordinaten festlegen (Position exakt bestimmen)

```java
import com.groupdocs.annotation.models.Point;

Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = new ArrayList<>();
points.add(point1);
points.add(point2);
points.add(point3);
points.add(point4);
```

**Koordinatensystem:**  
- Punkte 1 & 2 definieren die obere Kante der Unterstreichung.  
- Punkte 3 & 4 definieren die untere Kante.  
- Der Y‑Unterschied (730 vs 650) steuert die Dicke.

### Schritt 4: Unterstreichungs‑Anmerkung erstellen und konfigurieren

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Yellow in ARGB format
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**Farb‑ & Transparenz‑Tipps:**  
- `FontColor` verwendet ARGB; `65535` (0x00FFFF) ergibt ein helles Gelb.  
- Für Rot verwenden Sie `16711680` (0xFF0000); für Blau `255` (0x0000FF).  
- Transparenzwerte zwischen 0.5 und 0.8 bieten gute Lesbarkeit, ohne den Text zu verdecken.

### Schritt 5: Annotiertes Dokument speichern

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Speicher‑Management:** Der Aufruf `dispose()` gibt native Ressourcen frei und verhindert Speicherlecks – entscheidend, wenn viele Dateien stapelweise verarbeitet werden.

## Anmerkungen entfernen: Saubere Dokumentversionen erzeugen

Manchmal benötigen Sie eine PDF‑Version **ohne Anmerkungen** – etwa wenn Sie den final genehmigten Vertrag ausliefern. GroupDocs macht das einfach.

### Verständnis der Optionen zum Entfernen von Anmerkungen

Sie können:
- **Alle** Anmerkungen entfernen (am häufigsten)  
- Bestimmte Typen entfernen (z. B. nur Hervorhebungen)  
- Anmerkungen nach Autor oder Seite entfernen  

### Schritt‑für‑Schritt‑Anleitung zum Entfernen von Anmerkungen

**Schritt 1: Zuvor annotiertes Dokument laden**

```java
Annotator annotator = new Annotator(outputPath);
```

**Schritt 2: Save‑Optionen für eine saubere Ausgabe konfigurieren**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Schritt 3: Saubere Version speichern**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

Damit entsteht eine **saubere PDF‑Java‑Datei**, die keine Anmerkungs‑Objekte enthält – ideal für die endgültige Verteilung.

## Häufige Probleme und Lösungen

### Problem 1: „Datei nicht gefunden“-Fehler

```java
File inputFile = new File("path/to/your/document.pdf");
if (!inputFile.exists()) {
    throw new IllegalArgumentException("Document not found: " + inputFile.getAbsolutePath());
}
if (!inputFile.canRead()) {
    throw new IllegalArgumentException("Cannot read document: " + inputFile.getAbsolutePath());
}

Annotator annotator = new Annotator(inputFile.getAbsolutePath());
```

### Problem 2: Anmerkungen erscheinen an falschen Positionen

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Problem 3: Speicherprobleme bei großen Dokumenten

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### Problem 4: Lizenzprobleme in der Produktion

```java
try {
    License license = new License();
    license.setLicense("path/to/your/license.lic");
    System.out.println("License loaded successfully");
} catch (Exception e) {
    System.err.println("License loading failed: " + e.getMessage());
    // Handle the error appropriately
}
```

## Leistungs‑Best Practices für Produktionsanwendungen

### Strategien zum Speicher‑Management

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

```java
List<String> documentPaths = Arrays.asList("doc1.pdf", "doc2.pdf", "doc3.pdf");

for (String docPath : documentPaths) {
    try (Annotator annotator = new Annotator(docPath)) {
        // Process one document at a time
        annotator.add(createAnnotation());
        annotator.save(getOutputPath(docPath));
    }
    // Memory is freed after each iteration
}
```

### Thread‑Überlegungen

GroupDocs.Annotation ist **standardmäßig nicht thread‑sicher**. Wenn Ihre Anwendung Dokumente parallel verarbeitet:

- **Teilen Sie niemals** eine `Annotator`‑Instanz über Threads hinweg.  
- **Synchronisieren** Sie den Dateizugriff oder verwenden Sie ein Sperr‑Mechanismus.  
- Erwägen Sie einen **Pool** von `Annotator`‑Objekten, wenn Sie hohen Durchsatz benötigen.

### Caching‑Strategien

- Häufig genutzte Anmerkungs‑Templates cachen.  
- `Point`‑Sammlungen für gängige Koordinatensätze wiederverwenden.  
- Ein **Template‑PDF** im Speicher behalten, wenn Sie wiederholt dasselbe Basisdokument annotieren.

## Praxisbeispiele und Anwendungsfälle

### Dokument‑Review‑Systeme

- **Rechtsprüfung:** Vertragsklauseln unterstreichen und Kommentare zum Risiko hinzufügen.  
- **Compliance‑Audits:** Problematische Abschnitte in Finanzberichten hervorheben.  
- **Akademisches Peer‑Review:** Professoren unterstreichen Passagen, die Klärung benötigen.

### Lernplattformen

- **Studenten‑Annotationstools:** Lernende können Schlüsselkonzepte in E‑Books unterstreichen.  
- **Lehrer‑Feedback:** Inline‑Kommentare direkt zu eingereichten Aufgaben geben.

### Qualitätssicherungs‑Workflows

- **Technische Dokumentations‑Reviews:** Ingenieure unterstreichen Abschnitte, die aktualisiert werden müssen.  
- **Standard‑Operating‑Procedures:** Sicherheitsbeauftragte heben kritische Schritte hervor.

### Content‑Management‑Systeme

- **Redaktioneller Workflow:** Redakteure unterstreichen Text, der einer Faktenprüfung bedarf.  
- **Versionskontrolle:** Anmerkungs‑Historie über Dokumentrevisionen hinweg nachverfolgen.

## Fortgeschrittene Tipps für die professionelle Implementierung

### Benutzerdefinierte Anmerkungs‑Stile

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Anmerkungs‑Metadaten zur Nachverfolgung

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### Integration mit Benutzermanagement‑Systemen

```java
// Assume you have a method that returns the current authenticated user
String currentUser = getCurrentUser();
String userRole = getUserRole(currentUser);

// Apply role‑based styling
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedBy(currentUser);
underline.setFontColor(getRoleColor(userRole));
underline.setMessage(String.format("[%s] %s", userRole.toUpperCase(), commentText));
```

## Fehlersuche in der Produktion

### Leistungs‑Monitoring

Beobachten Sie diese Kennzahlen in der Produktion:
- **Heap‑Nutzung** – stellen Sie sicher, dass `dispose()` aufgerufen wird.  
- **Verarbeitungszeit pro Dokument** – protokollieren Sie Zeitstempel vor und nach `annotator.save()`.  
- **Fehlerrate** – erfassen Sie Ausnahmen und kategorisieren Sie sie.

### Häufige Stolperfallen in der Produktion

- **Dateisperren** – stellen Sie sicher, dass hochgeladene Dateien vor der Annotation geschlossen sind.  
- **Gleichzeitige Bearbeitungen** – implementieren Sie optimistisches Sperren oder Versionsprüfungen.  
- **Große Dateien (> 50 MB)** – erhöhen Sie das JVM‑Timeout und erwägen Sie Streaming‑APIs.

### Best Practices für Fehlerbehandlung

```java
try (Annotator annotator = new Annotator(documentPath)) {
    UnderlineAnnotation annotation = createAnnotation();
    annotator.add(annotation);
    annotator.save(outputPath);
    
} catch (Exception e) {
    logger.error("Annotation failed for document: " + documentPath, e);
    // Implement appropriate error recovery
    throw new DocumentProcessingException("Failed to annotate document", e);
}
```

## Fazit

Sie verfügen nun über alles, was Sie benötigen, um **saubere PDF‑Java‑Dateien** zu **erstellen** und **PDF in Java** mit Unterstreichungs‑Anmerkungen mittels GroupDocs.Annotation zu **annotieren**. Denken Sie daran:

- Ressourcen mit try‑with‑resources oder explizitem `dispose()` verwalten.  
- Koordinaten frühzeitig validieren, um Fehlplatzierungen zu vermeiden.  
- Robuste Fehlerbehandlung für Produktionsstabilität implementieren.  
- Rollenbasierte Stile und Metadaten nutzen, um Ihren Workflow zu unterstützen.

Nächste Schritte? Fügen Sie weitere Anmerkungs‑Typen hinzu – Hervorhebungen, Stempel oder Text‑Ersetzungen – und bauen Sie eine vollwertige Dokument‑Review‑Lösung.

## Häufig gestellte Fragen

**F: Wie annotiere ich mehrere Textbereiche in einem einzigen Vorgang?**  
A: Erstellen Sie mehrere `UnderlineAnnotation`‑Objekte mit unterschiedlichen Koordinaten und fügen Sie sie nacheinander mittels `annotator.add()` hinzu.

**F: Kann ich Bilder innerhalb von PDF‑Dokumenten annotieren?**  
A: Ja. Verwenden Sie dasselbe Koordinatensystem und stellen Sie sicher, dass die Punkte innerhalb der Bildgrenzen liegen.

**F: Welche Dateiformate neben PDF unterstützt GroupDocs.Annotation?**  
A: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) und Bildformate wie JPEG, PNG, TIFF.

**F: Wie gehe ich mit sehr großen Dokumenten um, ohne den Speicher zu erschöpfen?**  
A: Verarbeiten Sie Dokumente einzeln, erhöhen Sie den JVM‑Heap (`-Xmx`) und geben Sie `Annotator`‑Instanzen stets sofort frei.

**F: Ist es möglich, vorhandene Anmerkungen aus einem Dokument zu extrahieren?**  
A: Ja. Nutzen Sie `annotator.get()`, um alle Anmerkungen abzurufen, und filtern Sie nach Typ, Autor oder Seite.

---

**Zuletzt aktualisiert:** 2025-12-21  
**Getestet mit:** GroupDocs.Annotation 25.2  
**Autor:** GroupDocs  

---