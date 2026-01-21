---
categories:
- Java Development
date: '2025-12-21'
description: Leer hoe je schone PDF‑Java‑bestanden maakt en PDF’s annoteert in Java
  met GroupDocs.Annotation, met volledige codevoorbeelden en tips voor probleemoplossing.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2025-12-21'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'Maak een schone PDF in Java - Onderstreep annotaties met GroupDocs'
type: docs
url: /nl/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Maak schone PDF Java: Onderstrepingsannotaties met GroupDocs

## Introductie

Worstelt u met documentbeheer en samenwerking in uw Java‑toepassingen? U bent niet de enige. Veel ontwikkelaars staan voor de uitdaging om robuuste documentannotatiefuncties te implementeren die betrouwbaar werken over verschillende bestandsformaten.

In deze gids **maakt u schone PDF Java**‑bestanden en leert u hoe u **PDF in Java kunt annoteren** met GroupDocs.Annotation. Aan het einde van deze tutorial weet u precies hoe u onderstrepingsannotaties met opmerkingen kunt toevoegen, bestaande annotaties kunt verwijderen en deze functies naadloos in uw projecten kunt integreren.

**Wat u in deze gids onder de knie krijgt:**
- GroupDocs.Annotation in uw Java‑project instellen (op de juiste manier)  
- Onderstrepingsannotaties toevoegen met aangepaste opmerkingen en styling  
- Alle annotaties verwijderen om schone documentversies te maken  
- Veelvoorkomende problemen die ontwikkelaars tegenkomen oplossen  
- Prestaties optimaliseren voor productie‑applicaties  

Of u nu een document‑review‑systeem, een educatief platform of een tool voor collaboratieve bewerking bouwt, deze tutorial biedt u praktische, geteste code‑voorbeelden.

## Snelle antwoorden
- **Hoe voeg ik een onderstrepingsannotatie toe?** Gebruik `UnderlineAnnotation` en `annotator.add()` en sla vervolgens het document op.  
- **Hoe maak ik een schone PDF Java‑file?** Laad het geannoteerde bestand, stel `AnnotationType.NONE` in `SaveOptions` in, en sla een nieuwe kopie op.  
- **Welke bibliotheken zijn vereist?** GroupDocs.Annotation v25.2 (of nieuwer) en de bijbehorende Maven‑repository.  
- **Heb ik een licentie nodig voor productie?** Ja—pas een geldige GroupDocs‑licentie toe om watermerken te vermijden.  
- **Kan ik meerdere documenten efficiënt verwerken?** Plaats elke `Annotator` in een try‑with‑resources‑blok en maak deze na elk bestand vrij.

## Hoe u schone PDF Java‑bestanden maakt
Een schone PDF Java‑file maken betekent een versie van het document **zonder enige annotaties** genereren, terwijl de oorspronkelijke inhoud behouden blijft. Dit is nuttig voor definitieve distributie, archivering, of wanneer u een “schone” kopie wilt delen na een review‑cyclus.

GroupDocs.Annotation maakt dit eenvoudig: laad het geannoteerde bestand, configureer `SaveOptions` om alle annotatietypen uit te sluiten, en sla het resultaat op. De stappen worden later geïllustreerd in de sectie **Annotaties verwijderen**.

## Hoe u PDF in Java kunt annoteren met GroupDocs
GroupDocs.Annotation biedt een rijke API voor **PDF in Java annoteren**. Het ondersteunt een breed scala aan annotatietypen, waaronder markeringen, stempels en onderstrepingen. In deze tutorial richten we ons op onderstrepingsannotaties omdat ze vaak worden gebruikt om tekst te benadrukken terwijl ze threaded comments mogelijk maken.

## Voorvereisten en omgeving configuratie

### Wat u nodig heeft voordat u begint

**Vereisten voor de ontwikkelomgeving:**
- Java Development Kit (JDK) 8 of hoger (JDK 11+ aanbevolen)  
- Maven 3.6+ of Gradle 6.0+ voor dependency‑beheer  
- IDE zoals IntelliJ IDEA, Eclipse, of VS Code met Java‑extensies  
- Minimaal 2 GB beschikbaar RAM (documentverwerking kan veel geheugen vragen)

**Kennisvoorvereisten:**
U moet vertrouwd zijn met basisconcepten van Java—objectinitialisatie, methoden aanroepen en Maven‑dependencies. Ervaring met externe bibliotheken versnelt de adoptie.

**Testdocumenten:**
Zorg voor een paar voorbeeld‑PDF’s. Tekst‑gebaseerde PDF’s werken het beste; gescande afbeeldingen kunnen OCR vereisen vóór annotatie.

### Maven‑configuratie: GroupDocs in uw project opnemen

Zo configureert u uw Maven‑project correct (dit struikelt veel ontwikkelaars bij hun eerste poging):

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

**Belangrijk:** Versie 25.2 is de nieuwste stabiele release op het moment van schrijven. Controleer regelmatig de GroupDocs‑repository voor nieuwere versies met bug‑fixes en prestatie‑verbeteringen.

### Licentie‑configuratie (niet overslaan)

**Voor ontwikkeling/testing:**  
Download de gratis proefversie van de GroupDocs‑website. De proefversie bevat alle functies maar voegt een watermerk toe aan verwerkte documenten.

**Voor productie:**  
Koop een licentie en pas deze toe tijdens het opstarten van de applicatie. Zonder geldige licentie zijn productiebouws beperkt.

## Implementatie‑gids: Onderstrepingsannotaties toevoegen

### Het annotatie‑werkproces begrijpen

Voordat we in de code duiken, bekijken we de vier‑stappen‑workflow die plaatsvindt wanneer u **PDF in Java annoteren**:

1. **Document laden** – `Annotator` leest het bestand in het geheugen.  
2. **Annotatie maken** – Definieer eigenschappen zoals positie, stijl en opmerkingen.  
3. **Annotatie toepassen** – De bibliotheek injecteert de annotatie in de PDF‑structuur.  
4. **Document opslaan** – Sla het gewijzigde bestand op, eventueel met behoud van het origineel.

Het proces is niet‑destructief; het bronbestand blijft onaangeroerd tenzij u het overschrijft.

### Stap 1: De Annotator initialiseren en uw document laden

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Pro‑tip:** Gebruik absolute paden tijdens ontwikkeling om “bestand niet gevonden”‑fouten te vermijden. In productie kunt u overwegen resources te laden vanaf het classpath of een cloud‑storage‑bucket.

### Stap 2: Opmerkingen en antwoorden maken (het collaboratieve deel)

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

**Praktijkvoorbeeld:** Reviewers kunnen een specifieke clausule bespreken door threaded replies toe te voegen, waardoor het gesprek gekoppeld blijft aan de exacte annotatie.

### Stap 3: Annotatie‑coördinaten definiëren (de juiste positie bepalen)

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

**Coördinatensysteem:**  
- Punten 1 & 2 definiëren de bovenrand van de onderstreping.  
- Punten 3 & 4 definiëren de onderrand.  
- Het Y‑verschil (730 vs 650) bepaalt de dikte.

### Stap 4: De onderstrepingsannotatie maken en configureren

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

**Kleur‑ en doorzichtigheidstips:**  
- `FontColor` gebruikt ARGB; `65535` (0x00FFFF) levert fel geel op.  
- Voor rood gebruikt u `16711680` (0xFF0000); voor blauw `255` (0x0000FF).  
- Doorzichtigheidswaarden tussen 0.5 en 0.8 geven goede leesbaarheid zonder de tekst te verbergen.

### Stap 5: Uw geannoteerde document opslaan

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Geheugenbeheer:** De `dispose()`‑aanroep vrijgeeft native resources en voorkomt geheugenlekken—cruciaal bij het batch‑verwerken van veel bestanden.

## Annotaties verwijderen: schone documentversies maken

Soms heeft u een versie van de PDF **zonder enige annotaties** nodig—bijvoorbeeld bij het leveren van het definitieve goedgekeurde contract. GroupDocs maakt dit eenvoudig.

### Annotatie‑verwijderopties begrijpen

U kunt:
- **Alle** annotaties verwijderen (meest gebruikelijk)  
- Specifieke typen verwijderen (bijv. alleen markeringen)  
- Annotaties verwijderen op basis van auteur of pagina  

### Stapsgewijze annotatie‑verwijdering

**Stap 1: Het eerder geannoteerde document laden**

```java
Annotator annotator = new Annotator(outputPath);
```

**Stap 2: Save‑options configureren voor een schone output**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Stap 3: De schone versie opslaan**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

Dit levert een **schone PDF Java**‑file op die geen annotatie‑objecten bevat, perfect voor definitieve distributie.

## Veelvoorkomende problemen en oplossingen

### Probleem 1: “Document not found”‑fouten

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

### Probleem 2: Annotaties verschijnen op verkeerde locaties

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Probleem 3: Geheugenproblemen bij grote documenten

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### Probleem 4: Licentieproblemen in productie

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

## Prestatietips voor productie‑applicaties

### Strategieën voor geheugenbeheer

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

### Overwegingen voor threading

GroupDocs.Annotation is **standaard niet thread‑safe**. Als uw applicatie documenten gelijktijdig verwerkt:

- **Deel geen** `Annotator`‑instantie tussen threads.  
- **Synchroniseer** bestands‑toegang of gebruik een lock‑mechanisme.  
- Overweeg een **pool** van `Annotator`‑objecten als u een hoge doorvoer nodig heeft.

### Caching‑strategieën

- Cache vaak gebruikte annotatiesjablonen.  
- Hergebruik `Point`‑collecties voor gemeenschappelijke coördinaten.  
- Houd een **sjabloon‑PDF** in het geheugen als u steeds hetzelfde basisedocument annoteert.

## Praktische toepassingen en use‑cases

### Document‑review‑systemen

- **Juridische review:** Onderstreep contractclausules en voeg opmerkingen over risico’s toe.  
- **Compliance‑audits:** Markeer problematische secties in financiële verslagen.  
- **Academische peer‑review:** Docenten onderstrepen passages die verduidelijking behoeven.

### Educatieve platforms

- **Studenten‑annotatietools:** Laat leerlingen sleutelconcepten onderstrepen in e‑books.  
- **Docentfeedback:** Geef inline‑commentaren direct op ingediende opdrachten.

### Kwaliteits‑garantie‑workflows

- **Technische documentatie‑review:** Ingenieurs onderstrepen secties die bijgewerkt moeten worden.  
- **Standaard operationele procedures:** Veiligheidsfunctionarissen markeren kritieke stappen.

### Content‑management‑systemen

- **Redactionele workflow:** Editors onderstrepen tekst die fact‑checking vereist.  
- **Versiebeheer:** Volg annotatie‑geschiedenis over documentrevisies heen.

## Geavanceerde tips voor professionele implementatie

### Aangepaste annotatiestijlen

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Annotatiemetadata voor tracking

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### Integratie met gebruikers‑beheersystemen

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

## Problemen oplossen in productie

### Prestatiemonitoring

Houd de volgende metrics in de gaten in productie:
- **Heap‑gebruik** – zorg dat `dispose()` wordt aangeroepen.  
- **Verwerkingstijd per document** – log tijdstempels vóór/na `annotator.save()`.  
- **Foutpercentage** – vang uitzonderingen op en categoriseer ze.

### Veelvoorkomende productie‑valkuilen

- **Bestandsvergrendeling** – zorg dat geüploade bestanden gesloten zijn vóór annotatie.  
- **Gelijktijdige bewerkingen** – implementeer optimistic locking of versie‑controles.  
- **Grote bestanden (> 50 MB)** – verhoog de JVM‑timeout en overweeg streaming‑API’s.

### Best practices voor foutafhandeling

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

## Conclusie

U beschikt nu over alles wat nodig is om **schone PDF Java**‑bestanden te **maken** en **PDF in Java te annoteren** met onderstrepingsannotaties via GroupDocs.Annotation. Vergeet niet om:

- Resources te beheren met try‑with‑resources of expliciete `dispose()`.  
- Coördinaten vroegtijdig te valideren om verkeerd geplaatste onderstrepingen te voorkomen.  
- Robuuste foutafhandeling te implementeren voor productie‑stabiliteit.  
- Rollen‑gebaseerde styling en metadata te benutten om in uw workflow te passen.

Volgende stap? Voeg andere annotatietypen toe—highlights, stempels of tekstvervangingen—om een volledige document‑review‑oplossing te bouwen.

## Veelgestelde vragen

**Q: Hoe annoteer ik meerdere tekstgebieden in één bewerking?**  
A: Maak meerdere `UnderlineAnnotation`‑objecten met verschillende coördinaten en voeg ze achtereenvolgens toe met `annotator.add()`.

**Q: Kan ik afbeeldingen binnen PDF‑documenten annoteren?**  
A: Ja. Gebruik hetzelfde coördinatensysteem, zorg ervoor dat de punten binnen de afbeeldingsgrenzen liggen.

**Q: Welke bestandsformaten ondersteunt GroupDocs.Annotation naast PDF?**  
A: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) en beeldformaten zoals JPEG, PNG, TIFF.

**Q: Hoe ga ik om met zeer grote documenten zonder geheugen‑tekorten?**  
A: Verwerk documenten één voor één, vergroot de JVM‑heap (`-Xmx`) en maak `Annotator`‑instanties altijd direct vrij.

**Q: Is het mogelijk bestaande annotaties uit een document te extraheren?**  
A: Ja. Gebruik `annotator.get()` om alle annotaties op te halen en filter vervolgens op type, auteur of pagina.

---

**Laatst bijgewerkt:** 2025-12-21  
**Getest met:** GroupDocs.Annotation 25.2  
**Auteur:** GroupDocs  

---