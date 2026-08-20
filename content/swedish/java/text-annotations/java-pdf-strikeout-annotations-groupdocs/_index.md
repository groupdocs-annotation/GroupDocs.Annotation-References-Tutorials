---
categories:
- Java PDF Processing
date: '2026-05-21'
description: Lär dig hur du lägger till strikeout annotations i PDFs i Java med GroupDocs.
  Denna step‑by‑step tutorial täcker setup, code, troubleshooting och performance
  tips.
keywords:
- how to add strikeout
- java pdf strikeout
- groupdocs annotation java
lastmod: '2026-05-21'
linktitle: Java PDF Text Strikeout guide
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
title: Hur man lägger till strikeout annotations i PDFs i Java – Komplett GroupDocs
  guide
type: docs
url: /sv/java/text-annotations/java-pdf-strikeout-annotations-groupdocs/
weight: 1
---

# Hur man lägger till genomstrykna annotationer i PDF-filer i Java

Har du någonsin behövt stryka över text i en PDF programatiskt? Oavsett om du bygger ett dokumentgranskningssystem, skapar ett redigeringsflöde eller bara behöver markera text för borttagning, är **how to add strikeout**-annotationer i Java en praktisk färdighet som sparar tid och minskar manuellt arbete. I den här omfattande guiden kommer du att upptäcka allt du behöver veta för att implementera genomstrykna annotationer med GroupDocs.Annotation för Java, från projektuppsättning till prestandaoptimering.

## Snabba svar
- **Vad är första steget?** Lägg till GroupDocs.Annotation Maven‑beroendet i din `pom.xml`.  
- **Hur skapar jag en genomstrykning?** Instansiera `Annotator`, definiera `StrikeoutAnnotation` med punkter, sätt färg/genomskinlighet och anropa sedan `addAnnotation`.  
- **Kan jag lägga till kommentarer?** Ja, bifoga ett `Comment`‑objekt till annotationen för samarbete.  
- **Vad händer om annotationen är felplacerad?** Justera koordinatpunkterna; PDF använder ett ursprungssystem i nedre vänstra hörnet.  
- **Finns det en gräns för dokumentstorlek?** GroupDocs bearbetar PDF‑filer med flera hundra sidor utan att ladda hela filen i minnet.

## Vad är “how to add strikeout” i PDF‑annotation?
Frasen “how to add strikeout” avser processen att programatiskt rita en linje genom markerad text i ett PDF‑dokument med hjälp av ett annoterings‑API. I Java tillhandahåller GroupDocs.Annotation en dedikerad `StrikeoutAnnotation`‑klass som hanterar rendering, styling och beständighet för genomstrykna markeringar.

## Varför använda GroupDocs för Java PDF‑genomstrykning?
GroupDocs.Annotation stöder **50+ in‑ och utdataformat**—inklusive PDF, DOCX, XLSX, PPTX, HTML och vanliga bildtyper—så att du inte är låst till en enda filtyp. Det erbjuder ett hög‑nivå‑API som abstraherar den lågnivå PDF‑strukturen, automatiskt hanterar teckensnittsinbäddning, sidrendering och annoterings‑beständighet, vilket låter utvecklare fokusera på affärslogik snarare än PDF‑internals.

## Förutsättningar och installationskrav

### Viktiga krav
- **Java Development Kit (JDK):** Version 8 eller senare (JDK 11+ rekommenderas för optimal skräpsamling).  
- **GroupDocs.Annotation for Java:** Integrerad via Maven (se Maven‑snutten nedan).  
- **IDE:** IntelliJ IDEA, Eclipse eller någon Java‑kompatibel editor.

### Maven‑beroendeuppsättning
Add the following dependency block to your `pom.xml`:

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

**Pro Tip:** Verifiera alltid den senaste versionen på GroupDocs‑releasens sida; nyare versioner lägger till funktioner och åtgärdar buggar som kan påverka annoteringsrendering.

### Skaffa din licens i ordning
GroupDocs.Annotation kräver en giltig licens för produktionsanvändning. Du har tre alternativ:

- **Free Trial:** Ladda ner från [GroupDocs Downloads](https://releases.groupdocs.com/annotation/java/)  
- **Temporary License:** Begär en utvecklingsnyckel på [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Full License:** Köp för produktion på [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)

Provanläggningen lägger till ett subtilt vattenmärke, så planera din testning därefter.

## Steg‑för‑steg‑implementeringsguide

### Förstå kärnkomponenterna
Följande definitioner ger dig en snabb mental modell:

- **Annotator:** Det primära API‑objektet som laddar en PDF och exponerar annoteringsmetoder.  
- **StrikeoutAnnotation:** Representerar den visuella genomstrykna linjen och dess stilalternativ.  
- **Point:** Ett koordinatpar (X, Y) som talar om för biblioteket var linjen börjar och slutar.  
- **Comment:** Valfri text bifogad till en annotation för samarbete.

### Steg 1: Ställa in filsökvägar
Definiera platserna för din käll‑PDF och målfilen. Felaktiga sökvägar är en vanlig källa till “File Not Found”-fel.

```java
String inputFilePath = "path/to/your/document/directory/sample.pdf";
String outputPath = "path/to/your/output/directory/AddTextStrikeoutAnnotation_output.pdf";
```

**Common Mistake Alert:** Säkerställ att utdatamappen finns och är skrivbar; GroupDocs kommer inte automatiskt att skapa saknade mappar.

### Steg 2: Initiera Annotator
Skapa en `Annotator`‑instans som laddar PDF‑filen i minnet.

```java
final Annotator annotator = new Annotator(inputFilePath);
```

**What happens here?** Biblioteket analyserar PDF‑strukturen, bygger en intern representation och förbereder en sid‑för‑sid‑annoterings‑canvas. För filer med flera hundra sidor kan detta steg ta några sekunder.

### Steg 3: Lägga till kommentarer (valfritt men rekommenderat)
`Comment` är en klass som representerar en textnotering bifogad till en annotation, vilket låter samarbetspartners förklara orsaken till genomstrykningen.

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = new ArrayList<>();
replies.add(reply1);
```

**Real‑world tip:** Använd kommentarer för att förklara varför text tas bort—detta är särskilt användbart i juridiska eller redaktionella granskningsarbetsflöden.

### Steg 4: Definiera annoteringskoordinater
`Point`‑objekt lagrar X‑Y‑koordinatpar som definierar den exakta placeringen av en annotation på en PDF‑sida.

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
List<Point> points = Arrays.asList(point1, point2);
```

**Coordinate System Explained:** PDF‑koordinater startar i det nedre vänstra hörnet (0,0). Exemplet skapar en horisontell linje från (80,730) till (240,730) på mål‑sidan.

**Finding the Right Coordinates:** Många utvecklare skapar ett hjälpfunktion som konverterar procent av sidans bredd/höjd till absoluta punkter, vilket gör koden robust mot olika sidstorlekar.

### Steg 5: Skapa genomstrykning‑annotation
`StrikeoutAnnotation` kapslar in den visuella linjen, dess stil‑egenskaper såsom färg och genomskinlighet, samt eventuell associerad metadata för en genomstrykning.

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

**Color Values:** `fontColor` använder decimala RGB‑värden (t.ex. 65535 för ljusgul). Använd en online‑konverterare om du behöver varumärkes‑specifika nyanser.

**Opacity Recommendation:** En genomskinlighet på `0.7` (70 %) ger en tydlig visuell ledtråd samtidigt som den underliggande texten förblir läsbar.

### Steg 6: Applicera annotationen
`addAnnotation` är en metod i `Annotator` som registrerar den förberedda annotationen i dokumentet så att den renderas och sparas.

```java
annotator.add(strikeout);
```

### Steg 7: Spara och rensa upp
`dispose()` frigör inhemska resurser som hålls av `Annotator`‑instansen, vilket förhindrar minnesläckor efter att bearbetningen är klar.

```java
annotator.save(outputPath);
annotator.dispose();
```

**Memory Management Note:** Att anropa `dispose()` frigör inhemska resurser och förhindrar minnesläckor när du bearbetar batcher av PDF‑filer.

## Vanliga problem och hur man åtgärdar dem

### Problem 1: “File Not Found”-fel
**Symptoms:** Undantag kastas under `Annotator`‑konstruktion.  
**Solution:** Verifiera både in‑ och ut‑sökvägar och bekräfta att applikationen har läs‑/skrivrättigheter.

```java
// Add this check before creating the Annotator
File inputFile = new File(inputFilePath);
if (!inputFile.exists()) {
    throw new FileNotFoundException("Input file not found: " + inputFilePath);
}
```

### Problem 2: Genomstrykning visas på fel plats
**Symptoms:** Linjen matchar inte den avsedda texten.  
**Solution:** Kom ihåg att PDF‑Y‑koordinater ökar uppåt. Använd ett visuellt felsökningsverktyg eller skriv ut sidans dimensioner för att finjustera punkterna.

```java
// Log your coordinates to understand the positioning
System.out.println("Annotation coordinates: " + point1 + " to " + point2);

// For debugging, try extreme coordinates first
Point debugPoint1 = new Point(0, 0);     // Bottom-left corner
Point debugPoint2 = new Point(100, 100); // Small area from corner
```

### Problem 3: Annotation syns inte
**Symptoms:** Ingen genomstrykning visas efter sparning.  
**Possible Causes & Fixes:**  
- **Opacity too low:** Sätt tillfälligt genomskinlighet till `1.0` för att verifiera synlighet.  
- **Color blending:** Använd en högkontrastfärg som röd (`255`).  
- **Incorrect page index:** Sidnummer är noll‑baserade; säkerställ att du riktar in dig på rätt sida.

### Problem 4: Minnesproblem med stora filer
**Symptoms:** `OutOfMemoryError` eller trög prestanda.  
**Solutions:**  
- Bearbeta dokument i mindre batcher.  
- Använd streaming‑API:t om det finns.  
- Anropa alltid `dispose()` efter varje dokument.

```java
// Increase JVM heap size when running your application
// -Xmx2G for 2GB heap

// Process documents in batches rather than all at once
// Always dispose of Annotator instances promptly
```

## Verkliga tillämpningar och användningsfall

### Juridisk dokumentgranskning
Advokatbyråer annoterar kontrakt med genomstrykningar för att indikera borttagna klausuler samtidigt som de bevarar en revisionsspår.

### Akademisk papperredigering
Professorer använder genomstrykningar för att föreslå borttagningar under kollegial granskning, med originaltexten synlig för kontext.

### Innehållshanteringssystem
Publiceringsplattformar flaggar automatiskt policy‑brottande sektioner med genomstrykningar innan manuell moderering.

### Versionskontroll för dokument
Företag behandlar genomstrykna annotationer som “borttagningsmarkörer” i ett dokument‑centrerat versionskontroll‑arbetsflöde, liknande kod‑diffar.

## Prestandaoptimeringstips

### Batch‑bearbetningsstrategi
När du hanterar många PDF‑filer, återanvänd en enda `Annotator`‑instans där det är möjligt och bearbeta filer i parallella trådar.

```java
// Instead of creating a new Annotator for each document:
// Process multiple annotations per document in one session
List<StrikeoutAnnotation> annotations = prepareAllAnnotations();
for (StrikeoutAnnotation annotation : annotations) {
    annotator.add(annotation);
}
annotator.save(outputPath);
```

### Bästa praxis för minneshantering
- Anropa `dispose()` på varje `Annotator`.  
- Begränsa samtidiga dokumentladdningar för att undvika heap‑belastning.  
- Övervaka JVM‑minnesanvändning med verktyg som VisualVM.

### Koordinat‑cachning
Om du använder samma annoteringslayout över flera filer, cacha `Point`‑objekten för att undvika omräkning.

```java
// Cache commonly used coordinate sets
private static final List<Point> STANDARD_HEADER_STRIKEOUT = 
    Arrays.asList(new Point(50, 750), new Point(300, 750));

// Reuse these coordinates instead of recreating them
strikeout.setPoints(STANDARD_HEADER_STRIKEOUT);
```

## Avancerade anpassningsalternativ

### Dynamisk färgval
Välj färger vid körning baserat på affärsregler (t.ex. röd för kritiska borttagningar, gul för preliminära).

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

### Flerlinjiga genomstrykningar
Skapa en serie av `Point`‑par för att rita en sicksack‑linje som korsar flera textrader.

```java
// Create strikeouts that span multiple lines
List<Point> multiLinePoints = Arrays.asList(
    new Point(80, 730),   // Start of first line
    new Point(400, 730),  // End of first line
    new Point(80, 710),   // Start of second line
    new Point(200, 710)   // End of second line
);
```

## Felsökningschecklista
1. **File Permissions:** Verifiera läs‑/skrivrättigheter.  
2. **Library Version:** Säkerställ att du använder en stödd GroupDocs.Annotation‑release.  
3. **License Status:** Bekräfta att licensfilen refereras korrekt.  
4. **PDF Compatibility:** Kontrollera att PDF‑filen inte är korrupt och ligger inom stödjade storleksgränser.  
5. **Coordinate Validation:** Säkerställ att alla punkter ligger inom sidans gränser.  
6. **Heap Space:** Öka JVM `-Xmx` om du bearbetar mycket stora filer.

## Vanliga frågor

**Q: Kan jag genomstryka text över flera rader?**  
A: Ja. Skapa flera `Point`‑objekt som spårar den önskade vägen; annotationen följer den angivna polylinjen.

**Q: Vad händer om jag anger koordinater utanför sidans gränser?**  
A: Annotationen kommer att beskäras och kan bli osynlig. Validera alltid koordinater mot sidans bredd och höjd.

**Q: Kan jag ta bort genomstrykna annotationer efter att ha lagt till dem?**  
A: Absolut. Använd `removeAnnotation`‑metoden med annotationens ID eller filtrera efter typ för att ta bort dem programatiskt.

**Q: Finns det en gräns för hur många annotationer jag kan lägga till i en enda PDF?**  
A: GroupDocs har ingen hård gräns, men prestandan kan försämras efter tusentals annotationer. Överväg paginering eller sammanfattning av annotationer för mycket stora mängder.

**Q: Hur arbetar jag med lösenordsskyddade PDF‑filer?**  
A: Skicka lösenordet till `Annotator`‑konstruktorn. Biblioteket dekrypterar dokumentet i minnet innan några annotationer appliceras.

**Q: Hur kan jag hantera PDF‑filer med olika sidstorlekar och orienteringar?**  
A: Hämta varje sidas dimensioner via `annotator.getPageInfo(pageNumber)` och beräkna koordinater relativt dessa dimensioner för att säkerställa konsekvent placering.

## Slutsats
Du har nu en komplett, produktionsklar lösning för **how to add strikeout**‑annotationer i PDF‑filer i Java med hjälp av GroupDocs.Annotation. Genom att behärska hantering av filsökvägar, koordinatberäkning och resurshantering kan du integrera denna funktion i dokumentgranskningsverktyg, innehållspipelines eller någon Java‑baserad applikation som behöver exakt visuell återkoppling.

**Next Steps**
1. Klona exempelprojektet och kör det mot en prov‑PDF.  
2. Experimentera med olika färger, genomskinligheter och kommentartexter.  
3. Integrera annoterings‑arbetsflödet i din befintliga dokument‑bearbetningstjänst.  
4. Utforska relaterade annoteringstyper—markeringar, klistriga anteckningar och form‑annotationer—för att bredda ditt PDF‑manipuleringsverktyg.

Redo för mer? Dyka ner i den officiella dokumentationen för djupare API‑insikter.

## Ytterligare resurser
- [GroupDocs documentation](https://docs.groupdocs.com/annotation/java/) - Allmän dokumentation för GroupDocs‑bibliotek  
- [GroupDocs.Annotation Documentation](https://docs.groupdocs.com/annotation/java/) - Fullständig API‑referens  
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/) - Metod‑för‑metod‑detaljer  
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/) - Håll ditt bibliotek uppdaterat  
- [Purchase License](https://purchase.groupdocs.com/buy) - Produktionsklar licensiering  
- [Free Trial Download](https://releases.groupdocs.com/annotation/java/) - Utvärdera innan köp  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/) - Utvecklingstestning  
- [Support Forum](https://forum.groupdocs.com/c/annotation/) - Community‑hjälp och officiell support  

---

**Senast uppdaterad:** 2026-05-21  
**Testad med:** GroupDocs.Annotation 23.12 for Java  
**Författare:** GroupDocs

## Relaterade handledningar
- [Lägg till PDF‑annotation Java – Komplett GroupDocs‑guide](/annotation/java/annotation-management/java-pdf-annotation-groupdocs-java/)
- [Java PDF‑annotationshandledning – Komplett guide för att markera PDF‑filer](/annotation/java/text-annotations/annotate-pdfs-groupdocs-highlight-java/)
- [Hur man lägger till pil i PDF i Java – Komplett GroupDocs‑handledning](/annotation/java/graphical-annotations/annotate-pdf-arrows-groupdocs-java/)