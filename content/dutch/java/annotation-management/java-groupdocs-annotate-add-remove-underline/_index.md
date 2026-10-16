---
date: '2026-10-16'
description: Leer hoe je PDF zonder annotaties opslaat in Java, beheers Java PDF‑geheugenbeheer,
  en onderstreept annotaties toevoegt met GroupDocs.Annotation. Stap‑voor‑stap gids.
keywords:
- save pdf without annotations
- java pdf memory management
- java document review system
- groupdocs annotation tutorial
- underline annotation java
lastmod: '2026-10-16'
linktitle: Java Documentannotatie met GroupDocs
og_description: Leer hoe je PDF zonder annotaties opslaat in Java, beheers Java PDF‑geheugenbeheer,
  en onderstreept annotaties toevoegt met GroupDocs.Annotation. Stap‑voor‑stap gids.
og_image_alt: 'Developer guide: Save PDF without annotations in Java using GroupDocs.Annotation'
og_title: Hoe PDF zonder annotaties opslaan in Java met GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  headline: How to save PDF without annotations in Java using GroupDocs
  type: TechArticle
- description: Learn how to save PDF without annotations in Java, master java pdf
    memory management, and add underline annotations with GroupDocs.Annotation. Step‑by‑step
    guide.
  name: How to save PDF without annotations in Java using GroupDocs
  steps:
  - name: initialize the annotator and load your document
    text: '`Annotator` is the main entry point in GroupDocs.Annotation for loading
      and modifying PDF documents. It abstracts file‑system handling, stream management,
      and native resource allocation. **Pro tip:** Use absolute paths while developing
      to avoid “file not found” errors. In production, consider loadin'
  - name: creating comments and replies (the collaborative part)
    text: '`Comment` objects represent threaded discussion attached to an annotation.
      Each comment can have an author, a timestamp, and optional replies, enabling
      a full conversation around a specific markup. **Real‑world use:** Reviewers
      can discuss a specific clause by adding threaded replies, keeping the co'
  - name: defining annotation coordinates (getting the position right)
    text: '`Point` defines a single coordinate in PDF space (measured in points, where
      72 points = 1 inch). Four points are required for an underline: two for the
      start line and two for the end line. **Coordinate system:** - Points 1 & 2 define
      the top edge of the underline. - Points 3 & 4 define the bottom ed'
  - name: creating and configuring the underline annotation
    text: '`UnderlineAnnotation` is the concrete class that represents an underline
      markup. It inherits from the base `Annotation` class and adds properties specific
      to underlines, such as line thickness and style. **Color & opacity tips:** -
      `FontColor` uses ARGB; `65535` (0x00FFFF) yields bright yellow. - Fo'
  - name: saving your annotated document
    text: '`SaveOptions` lets you control the output format, whether to embed annotations,
      and how to handle metadata. Setting `AnnotationType.NONE` instructs the library
      to strip all annotation objects, which is the key to **save PDF without annotations**.
      **Memory management:** The `dispose()` call releases '
  type: HowTo
- questions:
  - answer: Create several `UnderlineAnnotation` objects with different coordinates
      and add them sequentially using `annotator.add()`.
    question: How do I annotate multiple areas of text in a single operation?
  - answer: Yes. Use the same coordinate system, ensuring the points lie inside the
      image bounds.
    question: Can I annotate images within PDF documents?
  - answer: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), and image formats
      such as JPEG, PNG, TIFF.
    question: What file formats besides PDF does GroupDocs.Annotation support?
  - answer: Process documents one at a time, increase the JVM heap (`-Xmx`), and always
      dispose of `Annotator` instances promptly.
    question: How do I handle very large documents without running out of memory?
  - answer: Yes. Use `annotator.get()` to retrieve all annotations, then filter by
      type, author, or page as needed.
    question: Is it possible to extract existing annotations from a document?
  type: FAQPage
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
- java pdf memory management
title: Hoe PDF zonder annotaties opslaan in Java met GroupDocs
type: docs
url: /nl/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Hoe PDF zonder annotaties opslaan in Java met GroupDocs

Als je **save PDF without annotations** wilt uitvoeren terwijl je toch samenwerkende onderstrepingsnotities kunt toevoegen, ben je hier op het juiste adres. Veel Java‑ontwikkelaars hebben moeite om een schone versie van een document te behouden voor definitieve distributie, vooral wanneer hetzelfde bestand wordt gebruikt voor iteratieve beoordelingen. In deze tutorial leer je hoe je een schone PDF genereert, het geheugen efficiënt beheert en onderstrepingsannotaties met opmerkingen toepast met GroupDocs.Annotation. Aan het einde begrijp je de volledige workflow — van het laden van een PDF tot het produceren van een watermerk‑vrije definitieve kopie — plus best‑practice tips voor het bouwen van een robuust **java document review system**.

## Snelle antwoorden
- **Hoe voeg ik een onderstrepingsannotatie toe?** Gebruik `UnderlineAnnotation` met `annotator.add()` en sla vervolgens het document op.  
- **Hoe kan ik PDF zonder annotaties opslaan?** Laad het geannoteerde bestand, stel `AnnotationType.NONE` in `SaveOptions` in, en sla een nieuwe kopie op.  
- **Welke bibliotheken zijn vereist?** GroupDocs.Annotation v25.2 (of nieuwer) en de bijbehorende Maven‑repository.  
- **Heb ik een licentie nodig voor productie?** Ja — pas een geldige GroupDocs‑licentie toe om watermerken te vermijden.  
- **Kan ik meerdere documenten efficiënt verwerken?** Plaats elke `Annotator` in een try‑with‑resources‑blok en maak deze na elk bestand vrij.

## Hoe sla ik PDF zonder annotaties op in Java?

Laad de bron‑PDF met een `Annotator`, configureer `SaveOptions` om alle annotatietypen uit te sluiten, en roep `save()` aan om een schone kopie te schrijven. Deze bewerking wijzigt het originele bestand niet, zodat je zowel de geannoteerde versie voor beoordelaars als een ongerepte versie voor distributie behoudt. Het proces maakt gebruik van streaming, wat betekent dat het volledige document nooit volledig in het geheugen wordt geladen — cruciaal voor grote PDF‑bestanden.

## Wat is save PDF without annotations?

`save pdf without annotations` verwijst naar het exporteren van een PDF‑document waarbij elk annotatie‑object (highlights, comments, stamps, onderstrepingen, enz.) wordt verwijderd. Het resulterende bestand bevat alleen de originele inhoud en lay‑out, waardoor het geschikt is voor juridische archivering, publieke release of opslag.

## Waarom schone PDF‑bestanden maken in een java document review system?

Een schone versie verwijdert beoordelaars‑markeringen, opmerkingen en highlights, waardoor je een gepolijst document krijgt dat klaar is voor klanten, regelgevers of publieke release. Het verkleint bovendien de bestandsgrootte gemiddeld met tot 30 % en voorkomt per ongeluk lekken van interne notities — kritisch voor juridische en compliance‑processen. GroupDocs.Annotation kan alle annotatie‑objecten in één stap verwijderen, en ondersteunt PDF‑bestanden tot 500 MB zonder het hele bestand in het geheugen te laden.

## Voorvereisten en omgeving configuratie

### Vereisten vóór de start

**Ontwikkelomgeving vereisten**  
- Java Development Kit (JDK) 8 of hoger (JDK 11+ aanbevolen)  
- Maven 3.6+ of Gradle 6.0+ voor dependency‑beheer  
- IDE zoals IntelliJ IDEA, Eclipse, of VS Code met Java‑extensies  
- Minimaal 2 GB beschikbaar RAM (documentverwerking kan geheugenintensief zijn)

**Kennisvoorvereisten**  
Je moet vertrouwd zijn met basis‑Java‑concepten — objectinitialisatie, methode‑aanroepen en Maven‑dependencies. Ervaring met derde‑partij bibliotheken versnelt de adoptie.

**Testdocumenten**  
Zorg voor een paar voorbeeld‑PDF’s. Tekst‑gebaseerde PDF’s werken het beste; gescande afbeeldingen vereisen mogelijk OCR vóór annotatie.

### Maven‑configuratie: GroupDocs in je project opnemen

Voeg de volgende dependency toe aan je `pom.xml`. Deze stap veroorzaakt vaak problemen bij ontwikkelaars omdat de group‑ID en artifact‑ID exact moeten overeenkomen.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-annotation</artifactId>
    <version>25.2</version>
</dependency>
```

**Belangrijk:** Versie 25.2 is de nieuwste stabiele release op het moment van schrijven. Controleer regelmatig de GroupDocs‑repository voor nieuwere versies met bug‑fixes en prestatie‑verbeteringen.

### Licentie‑configuratie (niet overslaan)

**Voor ontwikkeling/testing** – Download de gratis trial van de GroupDocs‑website. De trial bevat alle functies maar voegt een watermerk toe aan verwerkte documenten.

**Voor productie** – Schaf een licentie aan en pas deze toe tijdens de applicatie‑opstart. Zonder een geldige licentie worden productie‑builds beperkt en voorzien van watermerken.

## Implementatie‑gids: onderstrepingsannotaties toevoegen

### Het annotatie‑werkstroom begrijpen

Voordat we in de code duiken, bekijken we de vier‑stappen‑workflow die plaatsvindt wanneer je **annotate PDF in Java**:

1. **Document laden** – `Annotator` leest het bestand in het geheugen.  
2. **Annotatie maken** – Definieer eigenschappen zoals positie, stijl en opmerkingen.  
3. **Annotatie toepassen** – De bibliotheek injecteert de annotatie in de PDF‑structuur.  
4. **Document opslaan** – Sla het gewijzigde bestand op, eventueel met behoud van het origineel.

Het proces is niet‑destructief; het bronbestand blijft onaangeroerd tenzij je het overschrijft.

### Stap 1: initialiseert de annotator en laad je document

`Annotator` is het hoofd‑toegangspunt in GroupDocs.Annotation voor het laden en wijzigen van PDF‑documenten. Het abstraheert bestands‑systeem handling, stream‑beheer en native resource‑allocatie.

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

**Pro tip:** Gebruik absolute paden tijdens ontwikkeling om “file not found” fouten te vermijden. In productie, overweeg resources te laden vanaf het classpath of een cloud‑storage bucket.

### Stap 2: opmerkingen en antwoorden maken (het collaboratieve deel)

`Comment`‑objecten vertegenwoordigen een getagde discussie gekoppeld aan een annotatie. Elke opmerking kan een auteur, een tijdstempel en optionele antwoorden hebben, waardoor een volledige conversatie rond een specifieke markup ontstaat.

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Praktijkvoorbeeld:** Beoordelaars kunnen een specifieke clausule bespreken door getagde antwoorden toe te voegen, waardoor het gesprek gekoppeld blijft aan de exacte annotatie.

### Stap 3: annotatie‑coördinaten definiëren (positie juist krijgen)

`Point` definieert een enkele coördinaat in PDF‑ruimte (gemeten in points, waarbij 72 points = 1 inch). Vier punten zijn vereist voor een onderstreping: twee voor de startlijn en twee voor de eindlijn.

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

**Coördinatensysteem:**  
- Punt 1 & 2 definiëren de bovenrand van de onderstreping.  
- Punt 3 & 4 definiëren de onderrand.  
- Het Y‑verschil (730 vs 650) bepaalt de dikte.

### Stap 4: onderstrepingsannotatie maken en configureren

`UnderlineAnnotation` is de concrete klasse die een onderstrepings‑markup vertegenwoordigt. Het erft van de basis‑`Annotation`‑klasse en voegt eigenschappen toe die specifiek zijn voor onderstrepingen, zoals lijndikte en stijl.

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

**Kleur‑ en doorzichtigheidstips:**  
- `FontColor` gebruikt ARGB; `65535` (0x00FFFF) geeft fel geel.  
- Voor rood, gebruik `16711680` (0xFF0000); voor blauw, `255` (0x0000FF).  
- Doorzichtigheidswaarden tussen 0.5 en 0.8 zorgen voor goede leesbaarheid zonder de tekst te verbergen.

### Stap 5: je geannoteerde document opslaan

`SaveOptions` laat je het uitvoerformaat bepalen, of annotaties worden ingebed, en hoe metadata wordt behandeld. Het instellen van `AnnotationType.NONE` instrueert de bibliotheek om alle annotatie‑objecten te strippen, wat de sleutel is voor **save PDF without annotations**.

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

**Geheugenbeheer:** De `dispose()`‑aanroep vrijgeeft native resources en voorkomt geheugenlekken — cruciaal bij het batch‑verwerken van veel bestanden.

## Annotaties verwijderen: schone documentversies maken

Soms heb je een versie van de PDF **zonder enige annotaties** nodig — bijvoorbeeld bij het leveren van het definitieve goedgekeurde contract. GroupDocs maakt dit eenvoudig.

### Annotatie‑verwijderingsopties begrijpen

Je kunt:  
- Alle annotaties verwijderen (**meest gebruikelijk**)  
- Specifieke typen verwijderen (bijv. alleen highlights)  
- Annotaties verwijderen op basis van auteur of pagina  

### Stapsgewijze annotatie‑verwijdering

**Stap 1: laad het eerder geannoteerde document**

`Annotator` fungeert opnieuw als loader; hij leest het bestand dat nog annotatie‑objecten bevat.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Stap 2: configureer save‑opties voor een schone output**

`SaveOptions` biedt een fluent API om aan te geven dat er geen annotatietypen naar het uitvoerbestand moeten worden geschreven.

```java
Annotator annotator = new Annotator(outputPath);
```

**Stap 3: sla de schone versie op**

Het aanroepen van `save()` met de geconfigureerde opties schrijft een PDF die alleen de originele inhoud bevat.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

Dit levert een **clean PDF** bestand op dat geen annotatie‑objecten bevat, perfect voor definitieve distributie.

## Veelvoorkomende problemen en oplossingen

### Probleem 1: “Document not found” fouten

Zorg ervoor dat het bestandspad correct is en dat de applicatie leesrechten heeft. Het gebruik van `Path.of()` met absolute paden elimineert de meeste ambiguïteiten.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

### Probleem 2: Annotaties verschijnen op verkeerde locaties

De PDF‑coördinaat‑origin ligt in de linker‑onderhoek. Controleer of je Y‑waarden omhoog toenemen en houd rekening met paginaverschuiving.

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

### Probleem 3: Geheugenproblemen met grote documenten

GroupDocs.Annotation streamt inhoud en laadt het volledige bestand nooit in de heap‑geheugen. Je moet echter nog steeds `dispose()` aanroepen en overwegen de JVM‑heap (`-Xmx`) te verhogen voor bestanden groter dan 200 MB.

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Probleem 4: Licentieproblemen in productie

Als het licentiebestand ontbreekt of het pad onjuist is, valt de bibliotheek terug op trial‑modus en voegt een watermerk toe aan elke pagina. Plaats het licentiebestand op een locatie die op het classpath staat en laad het vroeg in de levenscyclus van je applicatie.

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

## Prestatie‑best practices voor productie‑applicaties

### Strategieën voor geheugenbeheer

GroupDocs.Annotation verwerkt PDF’s in een streaming‑modus, waardoor het bestanden tot 500 MB kan aan—handelen zonder het volledige document in het geheugen te laden. Volg desalniettemin deze richtlijnen:

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

```java
try (Annotator annotator = new Annotator("input.pdf")) {
    // Your annotation logic
    annotator.save("output.pdf");
} // Annotator is automatically disposed here
```

### Overwegingen voor threading

GroupDocs.Annotation is **niet thread‑safe** standaard. Als je applicatie documenten gelijktijdig verwerkt:

- **Deel nooit** een `Annotator`‑instantie tussen threads.  
- **Synchroniseer** bestands‑toegang of gebruik een lock‑mechanisme.  
- Overweeg een **pool** van `Annotator`‑objecten bij hoge doorvoer.

### Caching‑strategieën

- Cache vaak gebruikte annotatie‑templates.  
- Hergebruik `Point`‑collecties voor gemeenschappelijke coördinaat‑sets.  
- Houd een **template PDF** in het geheugen als je herhaaldelijk hetzelfde basisdocument annoteert.

## Java PDF geheugenbeheer best practices

Efficiënt geheugen‑gebruik is essentieel bij het verwerken van grote PDF’s of het batch‑verwerken van vele bestanden. Hier zijn enkele praktische aanbevelingen:

- **Gebruik try‑with‑resources** voor elke `Annotator` om gegarandeerde vrijgave te verzekeren.  
- **Verhoog de JVM‑heap** (`-Xmx`) alleen indien nodig; monitor gebruik met profiling‑tools.  
- **Verwerk documenten sequentieel** wanneer mogelijk, en maak geheugen vrij na elk bestand.  
- **Vermijd het meerdere keren laden van dezelfde PDF**; hergebruik dezelfde stream indien je het herhaaldelijk moet lezen.

Het toepassen van deze praktijken houdt je applicatie responsief en voorkomt out‑of‑memory crashes tijdens zware annotatie‑workloads.

## Praktische toepassingen en use cases

### Document review systemen

- **Juridische review:** Onderstreep contractclausules en voeg opmerkingen toe over risico’s.  
- **Compliance‑audits:** Markeer problematische secties in financiële verslagen.  
- **Academische peer review:** Professoren onderstrepen passages die verduidelijking behoeven.

### Educatieve platforms

- **Student‑annotatietools:** Laat leerlingen sleutelconcepten onderstrepen in e‑books.  
- **Docent‑feedback:** Bied inline commentaren direct op ingediende opdrachten.

### Kwaliteits‑garantie workflows

- **Technische documentatie review:** Ingenieurs onderstrepen secties die bijgewerkt moeten worden.  
- **Standaard operationele procedures:** Veiligheidsfunctionarissen markeren kritieke stappen.

### Content management systemen

- **Redactionele workflow:** Editors onderstrepen tekst die gecontroleerd moet worden.  
- **Versiebeheer:** Volg annotatie‑geschiedenis over document‑revisies heen.

## Geavanceerde tips voor professionele implementatie

### Aangepaste annotatiestijlen

Je kunt het visuele uiterlijk van een onderstreping uitbreiden door aangepaste dash‑patronen, line caps en doorzichtigheidsniveaus in te stellen. Dit is handig wanneer je verschillende beoordelaars‑rollen wilt onderscheiden (bijv. juridisch vs. technisch).

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

### Annotatie‑metadata voor tracking

Elke annotatie kan een door de gebruiker gedefinieerde metadata‑dictionary bevatten. Sla ID’s, tijdstempels of workflow‑status op om te integreren met externe tracking‑systemen.

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Integratie met gebruikers‑beheersystemen

Koppel de `author`‑eigenschap van een `Comment` aan de gebruikers‑ID’s van je applicatie. Dit maakt rol‑gebaseerde styling en audit‑trail generatie mogelijk.

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

## Problemen oplossen in productie

### Prestatie‑monitoring

Houd deze metrics in de gaten in productie:  
- **Heap‑gebruik** – zorg dat `dispose()` wordt aangeroepen.  
- **Verwerkingstijd per document** – log timestamps vóór/na `annotator.save()`.  
- **Foutpercentage** – registreer uitzonderingen en categoriseer ze.

### Veelvoorkomende productie‑valkuilen

- **Bestandsvergrendeling** – zorg dat geüploade bestanden gesloten zijn vóór annotatie.  
- **Gelijktijdige bewerkingen** – implementeer optimistische vergrendeling of versie‑checks.  
- **Grote bestanden (> 50 MB)** – verhoog JVM‑timeout en overweeg streaming‑API’s.

### Best practices voor foutafhandeling

Omring alle annotatie‑aanroepen met try‑catch‑blokken, log de volledige stack‑trace en gooi een aangepaste `AnnotationException` met een gebruiksvriendelijke boodschap opnieuw. Dit patroon vereenvoudigt debuggen en biedt duidelijke feedback aan API‑consumenten.

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

## Veelgestelde vragen

**Q: Hoe annoteer ik meerdere tekstgebieden in één bewerking?**  
A: Maak meerdere `UnderlineAnnotation`‑objecten met verschillende coördinaten en voeg ze achtereenvolgens toe via `annotator.add()`.

**Q: Kan ik afbeeldingen binnen PDF‑documenten annoteren?**  
A: Ja. Gebruik hetzelfde coördinatensysteem en zorg dat de punten binnen de afbeeldingsgrenzen liggen.

**Q: Welke bestandsformaten naast PDF ondersteunt GroupDocs.Annotation?**  
A: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) en beeldformaten zoals JPEG, PNG, TIFF.

**Q: Hoe ga ik om met zeer grote documenten zonder geheugen op te raken?**  
A: Verwerk documenten één voor één, verhoog de JVM‑heap (`-Xmx`) en maak `Annotator`‑instanties altijd snel vrij.

**Q: Is het mogelijk om bestaande annotaties uit een document te extraheren?**  
A: Ja. Gebruik `annotator.get()` om alle annotaties op te halen en filter vervolgens op type, auteur of pagina.

---

**Laatst bijgewerkt:** 2026-10-16  
**Getest met:** GroupDocs.Annotation 25.2  
**Auteur:** GroupDocs  

---

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

## Gerelateerde tutorials

- [Create Clean PDF Java: Underline Annotations with GroupDocs](/annotation/java/annotation-management/java-groupdocs-annotate-add-remove-underline/)
- [Edit PDF Annotations Java - Complete GroupDocs Tutorial](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)
- [Annotate Pdfs Groupdocs Annotation Java](/annotation/java/annotation-management/annotate-pdfs-groupdocs-annotation-java/)