---
categories:
- Java Development
date: '2026-06-16'
description: Μάθετε πώς να προσθέσετε μέτρηση σε εικόνα και άλλες μετρήσεις εγγράφων
  σε Java χρησιμοποιώντας το GroupDocs.Annotation. Πλήρης οδηγός με παραδείγματα κώδικα,
  συμβουλές αντιμετώπισης προβλημάτων και βέλτιστες πρακτικές.
keywords:
- how to add measurement
- distance annotation Java
- measure image Java
- GroupDocs annotation tutorial
- Java document measurement
lastmod: '2026-06-16'
linktitle: Οδηγός Java Distance Annotations
schemas:
- author: GroupDocs
  dateModified: '2026-06-16'
  description: Learn how to add measurement to image and other document measurements
    in Java using GroupDocs.Annotation. Complete tutorial with code examples, troubleshooting
    tips, and best practices.
  headline: 'Java Distance Annotation Tutorial: How to add measurement to image with
    GroupDocs'
  type: TechArticle
- description: Learn how to add measurement to image and other document measurements
    in Java using GroupDocs.Annotation. Complete tutorial with code examples, troubleshooting
    tips, and best practices.
  name: 'Java Distance Annotation Tutorial: How to add measurement to image with GroupDocs'
  steps:
  - name: Create Interactive Replies (Optional But Recommended)
    text: Replies let collaborators attach comments directly to a measurement, turning
      a simple ruler into a discussion thread. java import com.groupdocs.annotation.models.Reply;
      import java.util.ArrayList; import java.util.Calendar; Reply reply1 = new Reply();
      reply1.setComment("First comment"); reply1.setRe
  - name: Configure Your Distance Annotation
    text: The `DistanceAnnotation` class is GroupDocs.Annotation's top‑level object
      that represents a ruler measurement. You can customize its geometry, visual
      style, and attached message. `Rectangle` defines the annotation's bounding box
      on the page. `PenStyle` enumerates line styles such as solid, dash, and
  - name: Apply the Annotation and Save
    text: Once the annotation is ready, add it to the document and persist the changes.
      java annotator.add(distance); annotator.save("YOUR_OUTPUT_DIRECTORY/output.pdf");
      annotator.dispose(); **Important:** Always invoke `dispose()` after saving,
      especially when processing many documents in a batch job.
  type: HowTo
- questions:
  - answer: GroupDocs.Annotation supports PDFs, Word documents, PowerPoint presentations,
      Excel spreadsheets, and common image formats (PNG, JPEG, TIFF, BMP). The feature
      works consistently across all 50+ supported formats.
    question: What document formats support distance annotations?
  - answer: Absolutely! You have full control over pen color, line style (solid, dotted,
      dashed), line width, and opacity. You can also define custom end‑cap symbols
      for specialized engineering standards.
    question: Can I customize the appearance of measurement lines?
  - answer: The annotation itself displays the text you set in the `message` property.
      Perform any unit conversion (e.g., inches ↔ millimeters) in your Java code before
      assigning the message.
    question: How do I handle measurements in different units?
  - answer: Yes. In compatible viewers (GroupDocs.Viewer, Adobe Acrobat, or your own
      web viewer), users can click, drag, and edit the ruler. Replies and comments
      remain attached to the measurement for collaborative review.
    question: Can users interact with distance annotations after they're added?
  - answer: Adding up to several hundred annotations per document has a negligible
      impact (< 5 % CPU overhead). When you exceed 1,000 annotations, loading times
      may increase modestly, but the library remains stable and responsive.
    question: What's the performance impact of adding many annotations?
  type: FAQPage
tags:
- GroupDocs
- document-annotation
- Java-tutorial
- PDF-processing
title: 'Java Distance Annotation Tutorial: Πώς να προσθέσετε μέτρηση σε εικόνα με
  GroupDocs'
type: docs
url: /el/java/graphical-annotations/add-distance-annotations-java-groupdocs-annotation/
weight: 1
---

# Java Distance Annotation Tutorial: Πώς να προσθέσετε μέτρηση σε εικόνα με το GroupDocs

Σε αυτόν τον ολοκληρωμένο οδηγό θα ανακαλύψετε **πώς να προσθέσετε μέτρηση** σε εικόνες, PDF και άλλους τύπους εγγράφων χρησιμοποιώντας το GroupDocs.Annotation για Java. Είτε δημιουργείτε έναν προβολέα CAD, ένα εργαλείο αρχιτεκτονικής ανασκόπησης ή μια πλατφόρμα τεχνικής τεκμηρίωσης, οι αποστάσεις σημειώσεων παρέχουν στους χρήστες σας ένα σαφές, διαδραστικό χάρακα στον οποίο μπορούν να βασιστούν. Στο τέλος του οδηγού θα έχετε μια λύση έτοιμη για παραγωγή που σχεδιάζει ακριβείς μετρήσεις, προσαρμόζει την εμφάνισή τους και ενσωματώνεται ομαλά με τον υπάρχοντα κώδικα Java.

## Πώς να προσθέσετε μέτρηση σε εικόνα σε Java;

Φορτώστε το στόχο εγγράφου με `Annotator`, δημιουργήστε ένα `DistanceAnnotation`, διαμορφώστε τις οπτικές του ιδιότητες, προσθέστε το στην επιθυμητή σελίδα και τέλος αποθηκεύστε το αρχείο. Σε μόνο τέσσερις γραμμές κώδικα λαμβάνετε έναν πλήρως λειτουργικό χάρακα που μπορεί να επεξεργαστεί από τους τελικούς χρήστες σε οποιονδήποτε συμβατό προβολέα. Αυτή η προσέγγιση λειτουργεί για PDF, αρχεία Word, παρουσιάσεις PowerPoint, φύλλα Excel και κοινές μορφές εικόνας όπως PNG, JPEG και TIFF.

## Γρήγορες Απαντήσεις
- **Ποιος είναι ο πιο εύκολος τρόπος να προσθέσετε μέτρηση σε εικόνα σε Java;** Χρησιμοποιήστε την κλάση `DistanceAnnotation` του GroupDocs.Annotation.  
- **Ποια μορφότυπα υποστηρίζονται;** PDFs, Word, PowerPoint, Excel, και κοινά τύπους εικόνων (PNG, JPEG, TIFF).  
- **Χρειάζομαι άδεια για ανάπτυξη;** Μια δωρεάν δοκιμή ή προσωρινή άδεια λειτουργεί για δοκιμές· απαιτείται εμπορική άδεια για παραγωγή.  
- **Μπορώ να προσαρμόσω την εμφάνιση της γραμμής του χάρακα;** Ναι – μπορείτε να ορίσετε χρώμα, στυλ, πλάτος και διαφάνεια.  
- **Πώς να αποφύγω διαρροές μνήμης;** Πάντα απελευθερώστε την παρουσία `Annotator` ή χρησιμοποιήστε try‑with‑resources.

## Τι είναι οι Distance Annotations (και γιατί τις χρειάζεστε);

Οι distance annotations είναι διαδραστικά οπτικά στοιχεία που εμφανίζουν το μετρημένο μήκος μεταξύ δύο σημείων σε ένα έγγραφο. Λειτουργούν όπως ψηφιακοί χάρακες που μπορούν να τοποθετηθούν οπουδήποτε, να σύρουν και να επεξεργαστούν σε πραγματικό χρόνο, παρέχοντας στους χρήστες άμεση οπτική ανάδραση χωρίς χειροκίνητους υπολογισμούς.

Αυτές οι σημειώσεις προσφέρουν **οπτική σαφήνεια**, **διαδραστική ανάδραση** και **επαγγελματική εμφάνιση** σε οποιοδήποτε τεχνικό έγγραφο. Είναι ιδιαίτερα πολύτιμες για αρχιτεκτονικά σχέδια, μηχανικά σχήματα, ιατρικές απεικονίσεις και σχέδια δαπέδων ακινήτων, όπου οι ακριβείς διαστάσεις είναι κρίσιμες.

## Βέλτιστες Πρακτικές Μέτρησης Εγγράφων

Πριν ξεκινήσετε τον κώδικα, κρατήστε αυτές τις αποδεδειγμένες πρακτικές στο μυαλό:

1. **Αρίθμηση σελίδων με βάση το μηδέν** – `pageNumber = 0` αναφέρεται στην πρώτη σελίδα, που ταιριάζει με το εσωτερικό μοντέλο του GroupDocs.Annotation.  
2. **Χρώματα υψηλής αντίθεσης** – Επιλέξτε χρώματα χάρακα που ξεχωρίζουν από το φόντο του εγγράφου (π.χ., φωτεινό κίτρινο σε σκοτεινά σχέδια).  
3. **Ρύθμιση διαφάνειας** – Μια διαφάνεια `0.7` ισορροπεί την ορατότητα και τις υποκείμενες λεπτομέρειες· αυξήστε σε `1.0` για κρίσιμες μετρήσεις.  
4. **Ομαδοποίηση σχετικών σχολίων** – Χρησιμοποιήστε απαντήσεις ή σχόλια για να διατηρήσετε τις συζητήσεις οργανωμένες γύρω από μια συγκεκριμένη μέτρηση.  
5. **Άμεση απελευθέρωση** – Πάντα καλέστε `annotator.dispose()` ή χρησιμοποιήστε try‑with‑resources για να ελευθερώσετε τη φυσική μνήμη, ειδικά όταν επεξεργάζεστε μεγάλα αρχεία.

## Προαπαιτούμενα: Τι Θα Χρειαστείτε Πριν Ξεκινήσετε

### Απαιτήσεις Περιβάλλοντος Ανάπτυξης
- **Java Development Kit (JDK)**: Έκδοση 8 ή υψηλότερη (συνιστάται JDK 11+).  
- **Maven ή Gradle**: Τα παραδείγματα χρησιμοποιούν Maven, αλλά οι ίδιες εξαρτήσεις λειτουργούν με Gradle.  
- **IDE**: Οποιοδήποτε Java IDE (IntelliJ IDEA, Eclipse, VS Code κ.λπ.) είναι αποδεκτό.

### Προαπαιτούμενες Γνώσεις
Θα πρέπει ήδη να είστε άνετοι με:

- Βασικές έννοιες Java (κλάσεις, αντικείμενα, μέθοδοι).  
- Προσθήκη εξωτερικών βιβλιοθηκών μέσω Maven/Gradle.  
- Βασική διαχείριση αρχείων I/O και διαδρομών.

### Δοκιμαστικά Έγγραφα
Προετοιμάστε μερικά δείγματα αρχείων:
- Μία ή περισσότερες σελίδες PDF.  
- Εικόνες PNG/JPEG/TIFF για δοκιμές raster.  
- Προαιρετικά αρχεία CAD αν θέλετε να πειραματιστείτε με τεχνικά σχέδια.

## Ρύθμιση GroupDocs.Annotation για Java

Η ενσωμάτωση του GroupDocs.Annotation είναι παιχνιδάκι. Παρακάτω δείχνουμε τις συντεταγμένες Maven που πρέπει να προσθέσετε στο έργο σας.

### Ενσωμάτωση Maven

Προσθέστε την παρακάτω διαμόρφωση στο αρχείο `pom.xml` σας:

```xml
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
```

### Κατανόηση των Απαιτήσεων Άδειας

Το GroupDocs.Annotation προσφέρει τρία μοντέλα αδειοδότησης:

1. **Δωρεάν Δοκιμή** – Ιδανική για αξιολόγηση· περιλαμβάνει όλες τις λειτουργίες με μικρούς περιορισμούς χρήσης.  
2. **Προσωρινή Άδεια** – Αφαιρεί τους περιορισμούς της δοκιμής για ανάπτυξη και δοκιμές.  
3. **Εμπορική Άδεια** – Πλήρης λειτουργικότητα, έτοιμη για παραγωγή, χωρίς περιορισμούς.

Ξεκινήστε με τη δωρεάν δοκιμή, έπειτα αναβαθμίστε όταν είστε έτοιμοι για παραγωγή.

### Βασική Αρχικοποίηση

Η κλάση `Annotator` είναι το σημείο εισόδου για όλες τις λειτουργίες σημειώσεων. Φορτώνει ένα έγγραφο, παρέχει API επεξεργασίας και γράφει το αποτέλεσμα πίσω στο δίσκο.

```java
```java
import com.groupdocs.annotation.Annotator;

// Initialize annotator with the input file path
final Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/input.pdf");
```
```

**Pro Tip:** Τυλίξτε το `Annotator` σε ένα μπλοκ try‑with‑resources ή καλέστε ρητά `dispose()` για να αποφύγετε διαρροές φυσικής μνήμης.

## Οδηγός Υλοποίησης Βήμα‑Βήμα

Τώρα ας περάσουμε από μια πλήρη, έτοιμη για παραγωγή ροή εργασίας για την προσθήκη distance annotations.

### Βήμα 1: Δημιουργία Διαδραστικών Απαντήσεων (Προαιρετικό αλλά Συνιστάται)

Οι απαντήσεις επιτρέπουν στους συνεργάτες να επισυνάπτουν σχόλια απευθείας σε μια μέτρηση, μετατρέποντας έναν απλό χάρακα σε νήμα συζήτησης.

```java
```java
import com.groupdocs.annotation.models.Reply;
import java.util.ArrayList;
import java.util.Calendar;

Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

ArrayList<Reply> replies = new ArrayList<>();
replies.add(reply1);
replies.add(reply2);
```
```

**When to use replies:** Σε κύκλους ανασκόπησης πολλαπλών χρηστών, όταν χρειάζεται να εξηγήσετε γιατί επιλέχθηκε μια διάσταση ή να ζητήσετε διευκρινίσεις από έναν συνεργάτη.

### Βήμα 2: Διαμόρφωση του Distance Annotation

Η κλάση `DistanceAnnotation` είναι το κορυφαίο αντικείμενο του GroupDocs.Annotation που αντιπροσωπεύει μια μέτρηση χάρακα. Μπορείτε να προσαρμόσετε τη γεωμετρία του, το οπτικό στυλ και το επισυναπτόμενο μήνυμα.

`Rectangle` ορίζει το ορθογώνιο περιγράμματος της σημείωσης στη σελίδα. `PenStyle` απαριθμεί τα στυλ γραμμής όπως solid, dash και dot.

```java
```java
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.PenStyle;
import com.groupdocs.annotation.models.annotationmodels.DistanceAnnotation;

DistanceAnnotation distance = new DistanceAnnotation();
distance.setBox(new Rectangle(200, 150, 200, 30)); // Set the annotation's position and size
distance.setCreatedOn(Calendar.getInstance().getTime()); 
distance.setMessage("This is a distance annotation");
distance.setOpacity(0.7);
distance.setPageNumber(0); 
distance.setPenColor(65535);
distance.setPenStyle(PenStyle.DOT);
distance.setPenWidth((byte) 3);

distance.setReplies(replies); // Attach replies
```
```

**Key configuration options**  
- `setBox()` – Ορίζει το ορθογώνιο περιγράμματος της σημείωσης στη σελίδα.  
- `setOpacity()` – Ελέγχει τη διαφάνεια (`0.0` = αόρατο, `1.0` = πλήρως αδιαφανές).  
- `setPenColor()` – RGB χρώμα για τη γραμμή μέτρησης.  
- `setPenStyle()` – Στυλ γραμμής (`DOT`, `DASH`, `SOLID`).  
- `setPenWidth()` – Πάχος της γραμμής σε points.

### Βήμα 3: Εφαρμογή της Σημείωσης και Αποθήκευση

Μόλις η σημείωση είναι έτοιμη, προσθέστε την στο έγγραφο και διατηρήστε τις αλλαγές.

```java
```java
annotator.add(distance);
annotator.save("YOUR_OUTPUT_DIRECTORY/output.pdf");
annotator.dispose();
```
```

**Important:** Πάντα καλέστε `dispose()` μετά την αποθήκευση, ειδικά όταν επεξεργάζεστε πολλά έγγραφα σε παρτίδα.

## Πλήρες Παράδειγμα Εργασίας

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι ένα πλήρες παράδειγμα end‑to‑end που φορτώνει ένα PDF, προσθέτει μια distance annotation και αποθηκεύει το αποτέλεσμα.

```java
```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.models.Reply;
import com.groupdocs.annotation.models.Rectangle;
import com.groupdocs.annotation.models.PenStyle;
import com.groupdocs.annotation.models.annotationmodels.DistanceAnnotation;
import java.util.ArrayList;
import java.util.Calendar;

public class DistanceAnnotationExample {
    public static void main(String[] args) {
        try (Annotator annotator = new Annotator("input.pdf")) {
            // Create replies for the annotation
            ArrayList<Reply> replies = new ArrayList<>();
            Reply reply = new Reply();
            reply.setComment("Measurement verified by engineering team");
            reply.setRepliedOn(Calendar.getInstance().getTime());
            replies.add(reply);

            // Configure the distance annotation
            DistanceAnnotation distance = new DistanceAnnotation();
            distance.setBox(new Rectangle(100, 100, 300, 50));
            distance.setCreatedOn(Calendar.getInstance().getTime());
            distance.setMessage("Wall length: 12 feet");
            distance.setOpacity(0.8);
            distance.setPageNumber(0);
            distance.setPenColor(0xFF0000); // Red color
            distance.setPenStyle(PenStyle.SOLID);
            distance.setPenWidth((byte) 2);
            distance.setReplies(replies);

            // Add and save
            annotator.add(distance);
            annotator.save("output_with_distance_annotation.pdf");
            
            System.out.println("Distance annotation added successfully!");
        } catch (Exception e) {
            System.err.println("Error adding distance annotation: " + e.getMessage());
        }
    }
}
```
```

Εκτελέστε το απόσπασμα, ανοίξτε το αρχείο εξόδου σε οποιονδήποτε προβολέα PDF που υποστηρίζει σημειώσεις, και θα δείτε έναν πλήρως λειτουργικό χάρακα έτοιμο για αλληλεπίδραση.

## Κοινές Περιπτώσεις Χρήσης και Πραγματικές Εφαρμογές

Κατανοώντας πού διακρίνονται οι distance annotations, μπορείτε να αποφασίσετε πώς να τις ενσωματώσετε στο προϊόν σας.

### Τεχνική Τεκμηρίωση και Εγχειρίδια
- Επισήμανση διαστάσεων εξαρτημάτων σε οδηγούς συναρμολόγησης.  
- Εμφάνιση ζωνών ελευθέρωσης σε εγχειρίδια εγκατάστασης.  
- Παροχή γρήγορων μετρήσεων αναφοράς για λίστες ελέγχου ποιότητας.

### Αρχιτεκτονικά και Μηχανικά Έργα
- Εμφάνιση μεγεθών δωματίων σε σχέδια δαπέδων.  
- Καθορισμός αποστάσεων δομικών στοιχείων.  
- Σήμανση αποστάσεων γραμμών υποδομών και ασφαλών αποστάσεων.

### Ιατρικές και Επιστημονικές Εφαρμογές
- Μέτρηση ανατομικών δομών σε ακτινολογικές εικόνες.  
- Προσθήκη γραμμών κλίμακας σε μικροσκοπικές διαφάνειες.  
- Καταγραφή διαστάσεων δειγμάτων σε ερευνητικές αναφορές.

### Ακίνητα και Διαχείριση Ακινήτων
- Οπτικοποίηση ορίων οικοπέδων και γραμμών ιδιοκτησίας.  
- Εμφάνιση διαστάσεων δωματίων για καταχωρίσεις.  
- Σήμανση μεγεθών χώρων στάθμευσης και μετρήσεων τοπίου.

## Αντιμετώπιση Συνηθισμένων Προβλημάτων

Ακόμη και ένα καλά γραμμένο παράδειγμα μπορεί να αντιμετωπίσει δυσκολίες. Παρακάτω είναι τα πιο συχνά προβλήματα και πώς να τα επιλύσετε.

### Πρόβλημα: "File not found" ή Προβλήματα Διαδρομής
**Symptoms:** Μία εξαίρεση ρίχνεται κατά τη δημιουργία του `Annotator`.  
**Solution:** Χρησιμοποιήστε απόλυτη διαδρομή κατά την ανάπτυξη, επαληθεύστε ότι το αρχείο υπάρχει και βεβαιωθείτε ότι η διαδικασία έχει δικαιώματα ανάγνωσης.

```java
```java
// Better path handling
String inputPath = new File("documents/input.pdf").getAbsolutePath();
final Annotator annotator = new Annotator(inputPath);
```
```

### Πρόβλημα: Η Σημείωση Δεν Εμφανίζεται
**Symptoms:** Ο κώδικας εκτελείται χωρίς σφάλματα, αλλά δεν εμφανίζεται κανένας χάρακας.  
**Common causes:** Λάθος δείκτης σελίδας (θυμηθείτε ότι οι σελίδες ξεκινούν από 0), η σημείωση τοποθετείται εκτός του ορατού καμβά ή η διαφάνεια είναι πολύ χαμηλή.

**Quick fixes:**

```java
```java
distance.setPageNumber(0); // First page
distance.setOpacity(1.0);  // Fully opaque
distance.setBox(new Rectangle(50, 50, 200, 30)); // Visible position
```
```

### Πρόβλημα: Προβλήματα Μνήμης με Μεγάλα Έγγραφα
**Symptoms:** `OutOfMemoryError` ή αργή απόδοση σε αρχεία με εκατοντάδες σελίδες.  
**Solutions:**  
- Απελευθερώστε κάθε παρουσία `Annotator` μόλις τελειώσετε.  
- Επεξεργαστείτε τα έγγραφα διαδοχικά αντί να τα φορτώνετε όλα ταυτόχρονα.  
- Αυξήστε τη μνήμη heap του JVM (`-Xmx4g` ή περισσότερο) για πολύ μεγάλα αρχεία.

```java
```java
// Good practice - use try-with-resources
try (Annotator annotator = new Annotator("large-document.pdf")) {
    // Your annotation code here
} // Automatic disposal
```
```

### Πρόβλημα: Σφάλματα Σχετικά με την Άδεια
**Symptoms:** Προειδοποιήσεις σχετικά με περιορισμούς δοκιμής ή αποτυχίες επικύρωσης άδειας.  
**Solutions:**  
- Επιβεβαιώστε ότι η διαδρομή του αρχείου άδειας είναι σωστή και το αρχείο είναι αναγνώσιμο.  
- Βεβαιωθείτε ότι η έκδοση της άδειας ταιριάζει με την έκδοση της βιβλιοθήκης GroupDocs.Annotation που χρησιμοποιείτε.  
- Ελέγξτε ότι η προσωρινή άδεια δεν έχει λήξει.

## Συμβουλές Βελτιστοποίησης Απόδοσης

Όταν μεταβαίνετε από πρωτότυπο σε παραγωγή, κρατήστε αυτές τις παραμέτρους απόδοσης στο μυαλό.

### Βέλτιστες Πρακτικές Διαχείρισης Μνήμης
- **Πάντα απελευθερώστε**: Προτιμήστε try‑with‑resources ή ρητή κλήση `dispose()`.  
- **Λειτουργίες παρτίδας**: Ομαδοποιήστε πολλαπλές αλλαγές σημειώσεων σε μία συνεδρία `Annotator` για μείωση του κόστους.  
- **Προφίλ**: Χρησιμοποιήστε προφίλ Java (VisualVM, YourKit) για παρακολούθηση χρήσης φυσικής μνήμης.

### Βελτιστοποίηση Επεξεργασίας Αρχείων
- **Cache** συχνά προσπελαζόμενα έγγραφα στη μνήμη όταν είναι μόνο για ανάγνωση.  
- **Προτιμήστε PDF** αντί για εικόνες υψηλής ανάλυσης για ταχύτερη απόδοση· τα PDF είναι κατά μέσο όρο 30‑40 % μικρότερα για το ίδιο οπτικό περιεχόμενο.  
- **Ρύθμιση ανάλυσης εικόνας**: Μειώστε τις πηγές εικόνων σε μέγιστο 150 DPI εκτός εάν απαιτείται υψηλότερη πιστότητα.

### Σκέψεις για Συγχρονική Επεξεργασία
Αν η υπηρεσία σας επεξεργάζεται πολλά αρχεία παράλληλα, ακολουθήστε αυτούς τους κανόνες:

```java
```java
// Example of efficient batch processing
public void processMultipleDocuments(List<String> filePaths) {
    for (String path : filePaths) {
        try (Annotator annotator = new Annotator(path)) {
            // Add multiple annotations per document
            addDistanceAnnotation(annotator, config1);
            addDistanceAnnotation(annotator, config2);
            // Save once with all annotations
            annotator.save(getOutputPath(path));
        }
    }
}
```
```

- Κάθε νήμα πρέπει να δημιουργεί τη δική του παρουσία `Annotator`.  
- Χρησιμοποιήστε περιορισμένο thread pool για να αποφύγετε την εξάντληση των πόρων του συστήματος.  
- Παρακολουθήστε τη χρήση CPU και heap υπό φορτίο· κλιμακώστε οριζόντια αν χρειάζεται.

## Προχωρημένες Επιλογές Διαμόρφωσης

Αφού κυριαρχήσετε τα βασικά, εξερευνήστε αυτές τις προχωρημένες δυνατότητες για να βελτιώσετε τις σημειώσεις σας.

### Προσαρμοσμένες Επιλογές Στυλ

```java
```java
// Advanced pen styling
distance.setPenStyle(PenStyle.DASH_DOT);
distance.setPenWidth((byte) 4);
distance.setPenColor(0x00FF00); // Hex color codes work too

// Custom opacity for different emphasis levels
distance.setOpacity(0.6); // Subtle background measurements
// vs
distance.setOpacity(1.0); // Prominent foreground measurements
```
```

Μπορείτε να ορίσετε ένα προσαρμοσμένο αντικείμενο `Pen`, να εφαρμόσετε διαβαθμίσεις χρώματος ή ακόμη και να ενσωματώσετε δείκτες SVG στα άκρα της γραμμής του χάρακα.

### Δυναμική Τοποθέτηση

```java
```java
// Calculate position based on document dimensions or content
Rectangle dynamicBox = calculateOptimalPosition(documentWidth, documentHeight);
distance.setBox(dynamicBox);
```
```

Εκμεταλλευτείτε τις συντεταγμένες σχετικές με τη σελίδα ώστε η σημείωση να επανατοποθετείται αυτόματα όταν το έγγραφο ζουμάρεται ή περιστρέφεται.

### Υπό Συνθήκες Σημειώσεις

```java
```java
// Add annotations based on document content or user preferences
if (document.getType() == DocumentType.ARCHITECTURAL_PLAN) {
    distance.setMessage("Room dimension");
    distance.setPenStyle(PenStyle.SOLID);
} else if (document.getType() == DocumentType.ENGINEERING_DRAWING) {
    distance.setMessage("Component spacing");
    distance.setPenStyle(PenStyle.DOT);
}
```
```

Προσθέστε λογική που δημιουργεί μια distance annotation μόνο όταν πληρούται μια συγκεκριμένη προϋπόθεση (π.χ., όταν ένα στοιχείο υπερβαίνει ένα όριο ανοχής).

## Ενσωμάτωση με Άλλα Συστήματα

Οι distance annotations δεν είναι απομονωμένες· ταιριάζουν φυσικά σε ευρύτερα οικοσυστήματα διαχείρισης εγγράφων.

### Ενσωμάτωση Βάσης Δεδομένων

Το `AnnotationRecord` είναι ένα προσαρμοσμένο μοντέλο δεδομένων για την αποθήκευση μεταδεδομένων σημειώσεων σε μια βάση δεδομένων.

```java
```java
// Save annotation details to database
AnnotationRecord record = new AnnotationRecord();
record.setDocumentId(documentId);
record.setAnnotationType("distance");
record.setMeasurement(distance.getMessage());
record.setCreatedDate(distance.getCreatedOn());
```
```

Αποθηκεύστε τα μεταδεδομένα της σημείωσης (συγγραφέας, χρονική σήμανση, τιμή μέτρησης) σε μια σχεσιακή βάση δεδομένων για αναφορές και αναζήτηση.

### Ενσωμάτωση Web Εφαρμογής

Το `DistanceAnnotationRequest` είναι ένα DTO που μεταφέρει τις παραμέτρους της σημείωσης από τον πελάτη στον διακομιστή.

```java
```java
@PostMapping("/documents/{id}/annotations/distance")
public ResponseEntity<String> addDistanceAnnotation(
    @PathVariable String id,
    @RequestBody DistanceAnnotationRequest request) {
    // Process the annotation request
    // Return success/failure response
}
```
```

Αποκτήστε ένα REST endpoint που δέχεται αρχείο, προσθέτει μια distance annotation βάσει του JSON payload και επιστρέφει το σημειωμένο έγγραφο.

### Ενσωμάτωση Αποθήκευσης στο Cloud

```java
```java
// Download from cloud, process, upload result
byte[] documentBytes = cloudStorageService.download(documentPath);
// Process with GroupDocs.Annotation
byte[] annotatedDocument = processAnnotations(documentBytes);
cloudStorageService.upload(outputPath, annotatedDocument);
```
```

Διαβάστε και γράψτε αρχεία απευθείας από AWS S3, Azure Blob Storage ή Google Cloud Storage χρησιμοποιώντας τα αντίστοιχα SDKs, στη συνέχεια περάστε τα streams στο `Annotator`.

## Συχνές Ερωτήσεις

**Q: Ποιοι τύποι εγγράφων υποστηρίζουν distance annotations;**  
A: Το GroupDocs.Annotation υποστηρίζει PDF, έγγραφα Word, παρουσιάσεις PowerPoint, φύλλα Excel και κοινές μορφές εικόνας (PNG, JPEG, TIFF, BMP). Η λειτουργία λειτουργεί σταθερά σε όλες τις 50+ υποστηριζόμενες μορφές.

**Q: Μπορώ να προσαρμόσω την εμφάνιση των γραμμών μέτρησης;**  
A: Απόλυτα! Έχετε πλήρη έλεγχο πάνω στο χρώμα του πενά, το στυλ γραμμής (solid, dotted, dashed), το πλάτος γραμμής και τη διαφάνεια. Μπορείτε επίσης να ορίσετε προσαρμοσμένα σύμβολα άκρων για εξειδικευμένα πρότυπα μηχανικής.

**Q: Πώς να διαχειριστώ μετρήσεις σε διαφορετικές μονάδες;**  
A: Η σημείωση εμφανίζει το κείμενο που ορίζετε στην ιδιότητα `message`. Εκτελέστε οποιαδήποτε μετατροπή μονάδων (π.χ., ίντσες ↔ χιλιοστά) στον κώδικα Java πριν ορίσετε το μήνυμα.

**Q: Μπορούν οι χρήστες να αλληλεπιδράσουν με τις distance annotations μετά την προσθήκη τους;**  
A: Ναι. Σε συμβατούς προβολείς (GroupDocs.Viewer, Adobe Acrobat ή το δικό σας web viewer), οι χρήστες μπορούν να κάνουν κλικ, σύρσιμο και επεξεργασία του χάρακα. Οι απαντήσεις και τα σχόλια παραμένουν συνδεδεμένα με τη μέτρηση για συνεργατική ανασκόπηση.

**Q: Ποιος είναι ο αντίκτυπος στην απόδοση όταν προστίθενται πολλές σημειώσεις;**  
A: Η προσθήκη έως μερικές εκατοντάδες σημειώσεων ανά έγγραφο έχει αμελητέο αντίκτυπο (< 5 % CPU overhead). Όταν ξεπεράσετε τις 1 000 σημειώσεις, οι χρόνοι φόρτωσης μπορεί να αυξηθούν ελαφρώς, αλλά η βιβλιοθήκη παραμένει σταθερή και ανταποκρίνεται.

## Συμπέρασμα και Επόμενα Βήματα

Τώρα έχετε έναν πλήρη, έτοιμο για παραγωγή οδικό χάρτη για **πώς να προσθέσετε μέτρηση** σε εικόνες και άλλα έγγραφα σε Java χρησιμοποιώντας το GroupDocs.Annotation. Εκμεταλλευόμενοι τις distance annotations μπορείτε να μετατρέψετε στατικά σχέδια σε διαδραστικά, πλούσια σε δεδομένα στοιχεία που βελτιώνουν τη συνεργασία και μειώνουν τα σφάλματα.

**Key takeaways**
- Οι distance annotations παρέχουν ακριβείς, οπτικές μετρήσεις σε πάνω από 50 τύπους αρχείων.  
- Η υλοποίηση είναι σύντομη: φόρτωση, διαμόρφωση, προσθήκη, αποθήκευση.  
- Η απόδοση είναι αξιόπιστη για έγγραφα μεσαίου μεγέθους· ακολουθήστε τις συμβουλές διαχείρισης μνήμης για μεγάλα αρχεία.  
- Τα σημεία ενσωμάτωσης (DB, REST, cloud) σας επιτρέπουν να ενσωματώσετε τις σημειώσεις σε οποιαδήποτε ροή εργασίας.

### Συνιστώμενα Επόμενα Βήματα
1. **Πρωτότυπο**: Κλωνοποιήστε το πλήρες παράδειγμα, εκτελέστε το με τα δικά σας PDF ή εικόνες, και επαληθεύστε ότι ο χάρακας εμφανίζεται όπως αναμένεται.  
2. **Εξερευνήστε άλλους τύπους σημειώσεων**: Οι σημειώσεις επισήμανσης, κειμένου και σφραγίδας μπορούν να συμπληρώσουν τις distance measurements.  
3. **Δημιουργήστε UI**: Σχεδιάστε διεπαφή drag‑and‑drop που επιτρέπει στους τελικούς χρήστες να τοποθετούν χάρακες απευθείας στον περιηγητή ή στην επιφάνεια εργασίας.  
4. **Σχεδιάστε για κλίμακα**: Αν αναμένετε χιλιάδες ταυτόχρονους χρήστες, εφαρμόστε στρατηγική thread‑pool και παρακολουθήστε τη χρήση heap όπως περιγράφεται στην ενότητα απόδοσης.

**Last Updated:** 2026-06-16  
**Tested With:** GroupDocs.Annotation 25.2 for Java  
**Author:** GroupDocs  

**Related Resources:**  
- [Τεκμηρίωση GroupDocs.Annotation](https://docs.groupdocs.com/annotation/java/) - Πλήρης τεκμηρίωση API  
- [Αναφορά API](https://reference.groupdocs.com/annotation/java/) - Λεπτομερείς αναφορές μεθόδων και κλάσεων  
- [Σελίδα Λήψης](https://releases.groupdocs.com/annotation/java/) - Τελευταίες εκδόσεις και σημειώσεις έκδοσης  
- [Φόρουμ Υποστήριξης](https://forum.groupdocs.com/c/annotation/) - Υποστήριξη κοινότητας και συζητήσεις  
- [Επιλογές Αγοράς](https://purchase.groupdocs.com/buy) - Πληροφορίες εμπορικής άδειας  
- [Δωρεάν Δοκιμή](https://releases.groupdocs.com/annotation/java/) - Δοκιμάστε πριν αγοράσετε  
- [Προσωρινή Άδεια](https://purchase.groupdocs.com/temporary-license/) - Επέκταση άδειας αξιολόγησης  

## Σχετικά Μαθήματα

- [Πώς να προσθέσετε βέλος σε PDF με Java – Πλήρης Οδηγός & Καλές Πρακτικές](/annotation/java/graphical-annotations/add-arrow-annotations-java-groupdocs/)  
- [Java PDF Image Annotation - Πλήρης Οδηγός GroupDocs](/annotation/java/image-annotations/annotate-pdfs-java-groupdocs-image-annotations/)  
- [Επεξεργασία PDF Annotations Java - Πλήρης Οδηγός GroupDocs](/annotation/java/annotation-management/groupdocs-annotation-java-modify-pdf-annotations/)