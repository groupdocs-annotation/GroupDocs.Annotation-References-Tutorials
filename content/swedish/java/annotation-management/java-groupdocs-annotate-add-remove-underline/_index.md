---
"date": "2025-05-06"
"description": "Lär dig hur du lägger till och tar bort understrykningar i Java-dokument med GroupDocs.Annotation. Förbättra din dokumenthantering med den här detaljerade guiden."
"title": "Lägga till och ta bort understrykningsannoteringar i Java med GroupDocs – en omfattande guide"
"url": "/sv/java/annotation-management/java-groupdocs-annotate-add-remove-underline/"
type: docs
"weight": 1
---

# Hur man implementerar Java: Lägg till och ta bort understrykningsannoteringar med GroupDocs

## Introduktion

Förbättrar du ditt dokumenthanteringssystem genom att lägga till eller ta bort anteckningar programmatiskt? Den här handledningen guidar dig genom hur du använder det kraftfulla GroupDocs.Annotation-biblioteket i Java för att lägga till understrykningsanteckningar och ta bort dem från dokument som PDF-filer.

**Vad du kommer att lära dig:**
- Initiera Annotator-klassen.
- Lägg till en understrykningsanteckning med kommentarer med GroupDocs.Annotation för Java.
- Ta bort alla anteckningar från ett dokument.
- Konfigurera din miljö för att använda GroupDocs.Annotation effektivt.

Låt oss utforska hur dessa funktioner kan utnyttjas i dina projekt. Se till att du har de nödvändiga förutsättningarna uppfyllda innan du börjar.

## Förkunskapskrav

### Obligatoriska bibliotek och beroenden
För att följa den här handledningen effektivt, se till att du har:
- **GroupDocs.Annotation för Java**Version 25.2 eller senare rekommenderas.
- **Java-utvecklingspaket (JDK)**Version 8 eller senare krävs.

### Krav för miljöinstallation
Se till att din utvecklingsmiljö inkluderar en IDE som IntelliJ IDEA eller Eclipse och ett byggverktyg som Maven.

### Kunskapsförkunskaper
Grundläggande förståelse för Java-programmering, särskilt att arbeta med bibliotek via Maven, är meriterande.

## Konfigurera GroupDocs.Annotation för Java

För att börja använda GroupDocs.Annotation i dina Java-projekt, följ dessa installationssteg:

**Maven-konfiguration:**
Lägg till följande konfiguration till din `pom.xml` fil att ladda ner och integrera GroupDocs.Annotation.

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

**Licensförvärv:**
Börja med att ladda ner en gratis provversion eller skaffa en tillfällig licens från GroupDocs för att utforska deras biblioteks fulla möjligheter. För produktionsanvändning krävs det att man köper en licens.

## Implementeringsguide

### Funktion 1: Initiera annotatorn och lägg till understrykningsannotering

Det här avsnittet guidar dig genom initieringen av `Annotator` klass och lägga till en understrykningsanteckning i ditt dokument.

#### Översikt
Att lägga till anteckningar hjälper till att markera specifika delar av ett dokument. Här fokuserar vi på att stryka under text med kommentarer för förtydligande eller feedback.

#### Steg-för-steg-implementering

**1. Initiera annotatorn**
Skapa en `Annotator` objektet och ladda din PDF-fil.

```java
import com.groupdocs.annotation.Annotator;

// Ladda dokumentet du vill kommentera
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```

**2. Skapa kommentarer med svar**
Definiera kommentarer som är associerade med understrykningsannoteringen.

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

**3. Definiera punkter för understrykningsannotering**
Ange koordinater för att avgöra var understrykningen ska visas.

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

**4. Skapa och konfigurera understrykningsannotering**
Skapa understrykningsanteckningen och ange dess egenskaper som färg, opacitet och kommentarer.

```java
import com.groupdocs.annotation.models.annotationmodels.UnderlineAnnotation;

UnderlineAnnotation underline = new UnderlineAnnotation();
underline.setCreatedOn(Calendar.getInstance().getTime());
underline.setFontColor(65535); // Gul i ARGB-format
underline.setMessage("This is an underline annotation");
underline.setOpacity(0.7f);
underline.setPageNumber(0);
underline.setPoints(points);
underline.setReplies(replies);

annotator.add(underline);
```

**5. Spara det kommenterade dokumentet**
Spara dina ändringar i en ny fil.

```java
String outputPath = "YOUR_OUTPUT_DIRECTORY/output.pdf";
annotator.save(outputPath);
annotator.dispose();
```

#### Felsökningstips
- Se till att alla koordinater för punkter ligger inom dokumentets gränser.
- Verifiera att `outputPath` Katalogen finns och är skrivbar.

### Funktion 2: Spara dokument utan anteckningar

Det här avsnittet beskriver hur man tar bort alla anteckningar från ett tidigare annoterat dokument.

#### Översikt
Du kan behöva spara en ren version av ditt dokument utan några anteckningar för delning eller arkivering.

#### Steg-för-steg-implementering

**1. Initiera Annotator med det kommenterade dokumentet**
Ladda dokumentet som har befintliga anteckningar.

```java
Annotator annotator = new Annotator(outputPath);
```

**2. Konfigurera sparalternativ för att ta bort anteckningar**
Ange att inga anteckningar ska sparas i utdatafilen.

```java
import com.groupdocs.annotation.options.export.AnnotationType;
import com.groupdocs.annotation.options.export.SaveOptions;

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.NONE);
```

**3. Spara dokumentet utan anteckningar**
Definiera sökvägen för det rensade dokumentet och spara det.

```java
String noneAnnotationPath = Paths.get(outputPath).resolveSibling("none-annotation.pdf").toString();
annotator.save(noneAnnotationPath, saveOptions);
annotator.dispose();
```

## Praktiska tillämpningar

Här är några verkliga scenarier där dessa funktioner kan vara fördelaktiga:
1. **Dokumentgranskning**Markera och kommentera avsnitt i ett kontrakt eller en rapport för granskning.
2. **Utbildningsverktyg**Kommentera läroböcker med anteckningar eller rättelser för elever.
3. **Samarbetsredigering**Dela kommenterade utkast mellan teammedlemmar för feedback.
4. **Juridisk dokumentation**Understrykning av viktiga klausuler i juridiska dokument under diskussioner.
5. **Marknadsföringsmaterial**Markera viktig information i broschyrer före distribution.

## Prestandaöverväganden
När du arbetar med GroupDocs.Annotation, överväg dessa tips för att optimera prestandan:
- **Minneshantering**Kassera på rätt sätt `Annotator` objekt för att frigöra resurser.
- **Batchbearbetning**Om du antecknar flera dokument, bearbeta dem i omgångar för att hantera systembelastningen effektivt.
- **Resursallokering**Se till att din miljö har tillräckligt med minne och processorkraft för att hantera stora filer.

## Slutsats
Du har lärt dig hur du lägger till och tar bort understrykningsannoteringar med GroupDocs.Annotation för Java. Den här handledningen behandlade initiering av Annotator-klassen, konfigurering av annoteringar med kommentarer och sparande av dokument utan annoteringar. 

För ytterligare utforskning, överväg att integrera dessa funktioner i dina befintliga dokumenthanteringssystem eller experimentera med andra anteckningstyper som tillhandahålls av GroupDocs.

## FAQ-sektion
1. **Hur konfigurerar jag flera understrykningsannoteringar i en enda körning?**
   - Skapa flera `UnderlineAnnotation` objekt och lägg till dem i följd med hjälp av `annotator.add()` metod.
2. **Kan jag kommentera bilder i PDF-filer med hjälp av det här biblioteket?**
   - Ja, GroupDocs.Annotation har stöd för att kommentera bilder i dokument som PDF-filer.
3. **Vilka filformat stöds av GroupDocs.Annotation?**
   - Den stöder olika dokumentformat, inklusive PDF, Word, Excel och mer.