---
categories:
- Java Development
date: '2025-12-21'
description: Lär dig hur du skapar rena PDF‑filer i Java och kommenterar PDF i Java
  med GroupDocs.Annotation, med kompletta kodexempel och felsökningstips.
keywords: java document annotation library, groupdocs annotation tutorial, add underline
  annotation java, java pdf annotation, how to annotate pdf documents in java
lastmod: '2025-12-21'
linktitle: Java Document Annotation with GroupDocs
tags:
- groupdocs
- document-annotation
- java-tutorial
- pdf-manipulation
title: 'Skapa ren PDF Java: Understrykningsanteckningar med GroupDocs'
type: docs
url: /sv/java/annotation-management/java-groupdocs-annotate-add-remove-underline/
weight: 1
---

# Skapa ren PDF Java: Understrykningar med GroupDocs

## Introduktion

Kämpar du med dokumenthantering och samarbete i dina Java‑applikationer? Du är inte ensam. Många utvecklare står inför utmaningen att implementera robusta dokumentanteckningsfunktioner som fungerar pålitligt över olika filformat.

I den här guiden kommer du att **create clean PDF Java**‑filer och lära dig hur du **annotate PDF in Java** med GroupDocs.Annotation. I slutet av tutorialen kommer du exakt att veta hur du lägger till understrykningar med kommentarer, tar bort befintliga anteckningar och integrerar dessa funktioner sömlöst i dina projekt.

**Vad du kommer att behärska i den här guiden:**
- Installera GroupDocs.Annotation i ditt Java‑projekt (på rätt sätt)  
- Lägga till understrykningar med anpassade kommentarer och stil  
- Ta bort alla anteckningar för att skapa rena dokumentversioner  
- Felsöka vanliga problem som utvecklare stöter på  
- Optimera prestanda för produktionsapplikationer  

Oavsett om du bygger ett dokumentgranskningssystem, en utbildningsplattform eller ett verktyg för samarbetsredigering, så har den här tutorialen dig täckt med praktiska, testade kodexempel.

## Snabba svar
- **Hur lägger jag till en understrykning?** Använd `UnderlineAnnotation` och `annotator.add()` och spara sedan dokumentet.  
- **Hur kan jag skapa en ren PDF Java‑fil?** Ladda den annoterade filen, sätt `AnnotationType.NONE` i `SaveOptions` och spara en ny kopia.  
- **Vilka bibliotek krävs?** GroupDocs.Annotation v25.2 (eller nyare) och dess Maven‑arkiv.  
- **Behöver jag en licens för produktion?** Ja—applicera en giltig GroupDocs‑licens för att undvika vattenstämplar.  
- **Kan jag behandla flera dokument effektivt?** Inslut varje `Annotator` i ett try‑with‑resources‑block och disponera efter varje fil.

## Hur man skapar rena PDF Java‑filer
Att skapa en ren PDF Java‑fil innebär att generera en version av dokumentet **utan några anteckningar** samtidigt som originalinnehållet bevaras. Detta är användbart för slutdistribution, arkivering eller när du behöver dela en “ren” kopia efter en granskningscykel.

GroupDocs.Annotation gör detta enkelt: ladda den annoterade filen, konfigurera `SaveOptions` för att exkludera alla anteckningstyper och spara resultatet. Stegen illustreras senare i avsnittet **Removing Annotations**.

## Hur man annoterar PDF i Java med GroupDocs
GroupDocs.Annotation erbjuder ett rikt API för **annotate PDF in Java**. Det stöder ett brett spektrum av anteckningstyper, inklusive markeringar, stämplar och understrykningar. I den här tutorialen fokuserar vi på understrykningar eftersom de ofta används för att betona text samtidigt som trådade kommentarer möjliggörs.

## Förutsättningar och miljöinställning

### Vad du behöver innan du börjar

**Krav på utvecklingsmiljö:**
- Java Development Kit (JDK) 8 eller högre (JDK 11+ rekommenderas)  
- Maven 3.6+ eller Gradle 6.0+ för beroendehantering  
- IDE såsom IntelliJ IDEA, Eclipse eller VS Code med Java‑tillägg  
- Minst 2 GB tillgängligt RAM (dokumentbehandling kan vara minnesintensiv)

**Kunskapsförutsättningar:**
Du bör vara bekväm med grundläggande Java‑koncept—objektinitiering, metodanrop och Maven‑beroenden. Tidigare erfarenhet av tredjepartsbibliotek kommer att påskynda adoptionen.

**Testdokument:**
Ha några exempel‑PDF‑filer redo. Textbaserade PDF‑filer fungerar bäst; skannade bilder kan kräva OCR innan annotering.

### Maven‑inställning: Så får du in GroupDocs i ditt projekt

Så här konfigurerar du korrekt ditt Maven‑projekt (detta får många utvecklare att snubbla på första försöket):

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

**Viktigt:** Version 25.2 är den senaste stabila releasen vid skrivtillfället. Kontrollera GroupDocs‑arkivet regelbundet för nyare versioner som innehåller buggfixar och prestandaförbättringar.

### Licensinställning (Hoppa inte över detta)

**För utveckling/testning:**
Ladda ner gratisprovan från GroupDocs‑webbplatsen. Provan inkluderar alla funktioner men lägger till en vattenstämpel på bearbetade dokument.

**För produktion:**
Köp en licens och applicera den under applikationens start. Utan en giltig licens kommer produktionsbyggen att vara begränsade.

## Implementeringsguide: Lägga till understrykningar

### Förstå arbetsflödet för anteckningar

Innan vi dyker in i koden, låt oss gå igenom det fyrastegs arbetsflöde som sker när du **annotate PDF in Java**:

1. **Dokumentladdning** – `Annotator` läser filen till minnet.  
2. **Skapande av anteckning** – Definiera egenskaper som position, stil och kommentarer.  
3. **Tillämpning av anteckning** – Biblioteket injicerar anteckningen i PDF‑strukturen.  
4. **Dokumentsparning** – Spara den modifierade filen, eventuellt bevara originalet.  

Processen är icke‑destruktiv; källfilen förblir orörd om du inte skriver över den.

### Steg 1: Initiera Annotator och ladda ditt dokument

```java
import com.groupdocs.annotation.Annotator;

// Load the document you want to annotate
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**Proffstips:** Använd absoluta sökvägar under utveckling för att undvika “file not found”-fel. I produktion, överväg att ladda resurser från classpath eller en molnlagringsbucket.

### Steg 2: Skapa kommentarer och svar (Den samarbetsdel)

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

**Verklig användning:** Granskare kan diskutera en specifik klausul genom att lägga till trådade svar, vilket håller konversationen knuten till den exakta anteckningen.

### Steg 3: Definiera anteckningskoordinater (Få rätt position)

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

**Koordinatsystem:**
- Punkterna 1 & 2 definierar den övre kanten av understrykningen.  
- Punkterna 3 & 4 definierar den nedre kanten.  
- Y‑skillnaden (730 vs 650) styr tjockleken.

### Steg 4: Skapa och konfigurera understrykning

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

**Tips för färg och opacitet:**
- `FontColor` använder ARGB; `65535` (0x00FFFF) ger ljusgul.  
- För röd, använd `16711680` (0xFF0000); för blå, `255` (0x0000FF).  
- Opacitetsvärden mellan 0.5 och 0.8 ger god läsbarhet utan att dölja texten.

### Steg 5: Spara ditt annoterade dokument

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

**Minneshantering:** Anropet `dispose()` frigör inhemska resurser och förhindrar minnesläckor—kritiskt när man bearbetar många filer i en batch.

## Ta bort anteckningar: Skapa rena dokumentversioner

Ibland behöver du en version av PDF‑filen **utan några anteckningar**—till exempel när du levererar det slutgiltiga godkända kontraktet. GroupDocs gör detta enkelt.

### Förstå alternativ för borttagning av anteckningar

Du kan:
- Ta bort **alla** anteckningar (vanligast)  
- Ta bort specifika typer (t.ex. bara markeringar)  
- Ta bort anteckningar efter författare eller sida  

### Steg‑för‑steg borttagning av anteckningar

**Steg 1: Ladda det tidigare annoterade dokumentet**

```java
Annotator annotator = new Annotator(outputPath);
```

**Steg 2: Konfigurera Save Options för en ren utdata**

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**Steg 3: Spara den rena versionen**

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

Detta skapar en **clean PDF Java**-fil som inte innehåller några anteckningsobjekt, perfekt för slutdistribution.

## Vanliga problem och lösningar

### Problem 1: “Document not found”-fel

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

### Problem 2: Anteckningar visas på fel plats

```java
// Test with a simple rectangle in the top‑left corner
Point point1 = new Point(10, 10);   // Top‑left
Point point2 = new Point(100, 10);  // Top‑right  
Point point3 = new Point(10, 30);   // Bottom‑left
Point point4 = new Point(100, 30);  // Bottom‑right
```

### Problem 3: Minnesproblem med stora dokument

```java
// Increase JVM heap size when launching the app, e.g., -Xmx2g
try (Annotator annotator = new Annotator("document.pdf")) {
    // Annotation logic here
    annotator.save("output.pdf");
}
```

### Problem 4: Licensproblem i produktion

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

## Prestandabästa praxis för produktionsapplikationer

### Strategier för minneshantering

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

### Trådningsöverväganden

GroupDocs.Annotation är **inte trådsäker** som standard. Om din applikation bearbetar dokument samtidigt:

- **Dela aldrig** en `Annotator`‑instans över trådar.  
- **Synkronisera** filåtkomst eller använd en låsmekanism.  
- Överväg en **pool** av `Annotator`‑objekt om du behöver hög genomströmning.

### Cache‑strategier

- Cacha ofta använda anteckningsmallar.  
- Återanvänd `Point`‑samlingar för vanliga koordinatuppsättningar.  
- Behåll en **template PDF** i minnet om du upprepade gånger annoterar samma grunddokument.

## Verkliga tillämpningar och användningsfall

### Dokumentgranskningssystem

- **Juridisk granskning:** Understryk kontraktsklausuler och lägg till kommentarer om risk.  
- **Efterlevnadsrevisioner:** Markera problematiska avsnitt i finansiella rapporter.  
- **Akademisk kollegial granskning:** Professorer understryker passager som behöver förtydligas.

### Utbildningsplattformar

- **Studentverktyg för annotering:** Låt elever understryka nyckelkoncept i e‑böcker.  
- **Lärarfeedback:** Ge inline‑kommentarer direkt på inlämnade uppgifter.

### Kvalitetssäkringsarbetsflöden

- **Granskning av teknisk dokumentation:** Ingenjörer understryker avsnitt som behöver uppdateras.  
- **Standardarbetsinstruktioner:** Säkerhetsansvariga markerar kritiska steg.

### Innehållshanteringssystem

- **Redaktionellt arbetsflöde:** Redaktörer understryker text som kräver faktakontroll.  
- **Versionskontroll:** Spåra anteckningshistorik över dokumentrevisioner.

## Avancerade tips för professionell implementering

### Anpassade anteckningsstilar

```java
UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setFontColor(16711680);      // Red for urgent items
underline.setOpacity(0.5f);            // Subtle highlighting
underline.setFontSize(12);             // Consistent sizing
underline.setMessage("URGENT REVIEW REQUIRED");
```

### Anteckningsmetadata för spårning

```java
underline.setCreatedBy("john.doe@company.com");
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setMessage("Legal review required - Contract clause 4.2");
```

### Integration med användarhanteringssystem

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

## Felsökning av produktionsproblem

### Prestandaövervakning

Övervaka dessa mätvärden i produktion:

- **Heap‑användning** – säkerställ att `dispose()` anropas.  
- **Bearbetningstid per dokument** – logga tidsstämplar före/efter `annotator.save()`.  
- **Felfrekvens** – fånga undantag och kategorisera dem.

### Vanliga fallgropar i produktion

- **Fil‑låsning** – säkerställ att uppladdade filer är stängda innan annotering.  
- **Samtidiga redigeringar** – implementera optimistisk låsning eller versionskontroller.  
- **Stora filer (> 50 MB)** – öka JVM‑timeout och överväg streaming‑API:er.

### Bästa praxis för felhantering

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

## Slutsats

Du har nu allt du behöver för att **create clean PDF Java**‑filer och **annotate PDF in Java** med understrykningar med hjälp av GroupDocs.Annotation. Kom ihåg att:

- Hantera resurser med try‑with‑resources eller explicit `dispose()`.  
- Validera koordinater tidigt för att undvika felplacerade understrykningar.  
- Implementera robust felhantering för produktionsstabilitet.  
- Utnyttja rollbaserad stil och metadata för att passa ditt arbetsflöde.

Nästa steg? Prova att lägga till andra anteckningstyper—markeringar, stämplar eller textutbyten—för att bygga en fullutrustad dokumentgranskningslösning.

## Vanliga frågor och svar

**Q: Hur annoterar jag flera textområden i en enda operation?**  
A: Skapa flera `UnderlineAnnotation`‑objekt med olika koordinater och lägg till dem sekventiellt med `annotator.add()`.

**Q: Kan jag annotera bilder i PDF‑dokument?**  
A: Ja. Använd samma koordinatsystem och se till att punkterna ligger inom bildens gränser.

**Q: Vilka filformat förutom PDF stöder GroupDocs.Annotation?**  
A: Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) och bildformat som JPEG, PNG, TIFF.

**Q: Hur hanterar jag mycket stora dokument utan att få slut på minne?**  
A: Bearbeta dokument ett i taget, öka JVM‑heapen (`-Xmx`) och disponera alltid `Annotator`‑instanser omedelbart.

**Q: Är det möjligt att extrahera befintliga anteckningar från ett dokument?**  
A: Ja. Använd `annotator.get()` för att hämta alla anteckningar och filtrera sedan efter typ, författare eller sida vid behov.

---

**Senast uppdaterad:** 2025-12-21  
**Testad med:** GroupDocs.Annotation 25.2  
**Författare:** GroupDocs