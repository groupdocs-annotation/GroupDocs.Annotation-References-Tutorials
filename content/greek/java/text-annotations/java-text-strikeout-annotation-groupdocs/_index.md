---
categories:
- Java Development
date: '2026-03-30'
description: Μάθετε πώς να προσθέσετε σημείωση διαγράμμισης σε Java χρησιμοποιώντας
  το GroupDocs.Annotation. Οδηγός βήμα‑προς‑βήμα με παραδείγματα κώδικα, συμβουλές
  αντιμετώπισης προβλημάτων και βέλτιστες πρακτικές για τη σήμανση εγγράφων.
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: Προσθήκη Σημείωσης Διαγράμμισης – Java Tutorial με το GroupDocs
type: docs
url: /el/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# Προσθήκη Σημειώματος Διαγράμμισης Java - Πλήρης Οδηγός GroupDocs

Έχετε βρεθεί ποτέ να κοιτάζετε ένα έγγραφο και να σκέφτεστε: “Πρέπει να διαγράψω αυτό το κείμενο, αλλά δεν μπορώ απλώς να πάρω ένα κόκκινο στυλό”; Δεν είστε μόνοι. Είτε δημιουργείτε σύστημα ανασκόπησης εγγράφων, είτε δημιουργείτε ροή εργασίας επεξεργασίας, είτε απλώς χρειάζεστε να σημειώσετε κείμενο για διαγραφή στην εφαρμογή Java, **add strikeout annotation java** είναι μια απαραίτητη δεξιότητα. Σε αυτό το tutorial θα καλύψουμε όλα όσα πρέπει να γνωρίζετε για την υλοποίηση λειτουργίας διαγράμμισης κειμένου που λειτουργεί πραγματικά σε παραγωγή.

## Γρήγορες Απαντήσεις
- **What library supports strikeout annotations in Java?** GroupDocs.Annotation for Java  
- **Which primary keyword should I target for SEO?** add strikeout annotation java  
- **Do I need a license to run the sample code?** Μια δωρεάν δοκιμή ή προσωρινή άδεια λειτουργεί για ανάπτυξη· απαιτείται πλήρης άδεια για παραγωγή.  
- **Can I use this with PDF, DOCX, and PPTX files?** Ναι – το GroupDocs.Annotation υποστηρίζει όλες τις κύριες μορφές εγγράφων.  
- **What Java version is required?** JDK 8 ή νεότερη (συνιστάται JDK 11+).

## Τι είναι το add strikeout annotation java;
Ένα σημείωμα διαγράμμισης σχεδιάζει μια γραμμή μέσω του επιλεγμένου κειμένου, υποδεικνύοντας οπτικά ότι το περιεχόμενο πρέπει να αφαιρεθεί ή να αγνοηθεί. Είναι ένας μη καταστροφικός τρόπος για να προτείνετε διαγραφές διατηρώντας το αρχικό κείμενο αμετάβλητο για ίχνη ελέγχου ή συνεργατικές ανασκοπήσεις.

## Γιατί να χρησιμοποιήσετε σημειώματα διαγράμμισης σε εφαρμογές Java;
- **Document review workflows** – οι αξιολογητές μπορούν να επισημάνουν ανεπιθύμητο κείμενο χωρίς να τροποποιήσουν την πηγή.  
- **Collaborative editing** – τα μέλη της ομάδας βλέπουν τις προτεινόμενες διαγραφές αμέσως.  
- **Legal and compliance** – διατηρήστε ένα σαφές ίχνος ελέγχου των αλλαγών.  
- **Content migration** – σημειώστε παλαιές ενότητες πριν τη μεταφορά του περιεχομένου μεταξύ συστημάτων.  

## Προαπαιτούμενα και Ρύθμιση Περιβάλλοντος
Θα χρειαστείτε τα παρακάτω πριν βυθιστείτε στον κώδικα:

- **Java Development Kit (JDK)** 8+ (συνιστάται JDK 11+).  
- **Maven or Gradle** για διαχείριση εξαρτήσεων.  
- **IDE** – IntelliJ IDEA, Eclipse ή VS Code με επεκτάσεις Java.  
- **GroupDocs.Annotation library** – θα χρησιμοποιήσουμε την έκδοση 25.2 στα παραδείγματα.  

*Nice to have:* βασικές γνώσεις των Java annotations και της διαχείρισης PDF.

## Ρύθμιση του GroupDocs.Annotation για Java

### Διαμόρφωση Maven που Λειτουργεί Πραγματικά
Προσθέστε το αποθετήριο και την εξάρτηση στο `pom.xml` ακριβώς όπως φαίνεται:

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

### Τακτοποίηση Άδειας Χρήσης
Η GroupDocs προσφέρει διάφορες επιλογές αδειοδότησης:

- **Free trial** – ιδανική για δοκιμές (δεν απαιτείται κάρτα).  
- **Temporary license** – ιδανική για ανάπτυξη και staging.  
- **Full license** – απαιτείται για χρήση σε παραγωγή· δείτε τη [purchase page](https://purchase.groupdocs.com/buy)

> **Pro tip:** Ξεκινήστε με τη δωρεάν δοκιμή για να εξερευνήσετε το API, στη συνέχεια μεταβείτε σε προσωρινή άδεια όταν είστε έτοιμοι να δημιουργήσετε μια πραγματική λειτουργία.

### Γρήγορος Έλεγχος Κατάστασης
Εκτελέστε αυτό το ελάχιστο πρόγραμμα για να επαληθεύσετε ότι η βιβλιοθήκη φορτώνεται σωστά:

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

Εάν η κονσόλα εμφανίσει το μήνυμα επιτυχίας χωρίς σφάλματα, είστε έτοιμοι να προσθέσετε σημειώματα διαγράμμισης.

## Πώς να προσθέσετε σημείωμα διαγράμμισης java

Παρακάτω είναι μια πλήρης, έτοιμη για παραγωγή υλοποίηση χωρισμένη σε σαφή βήματα.

### Βήμα 1 – Αρχικοποίηση του Annotator
Δημιουργήστε μια παρουσία `Annotator` που δείχνει στο πηγαίο έγγραφο:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **Why this matters:** Η χρήση απόλυτης ή σωστά επιλυμένης σχετικής διαδρομής αποτρέπει εξαιρέσεις «αρχείο δεν βρέθηκε».

### Βήμα 2 – (Προαιρετικό) Προετοιμασία Απαντήσεων Σχολίων
Η προσθήκη απαντήσεων κάνει το σημείωμα συνεργατικό:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

Αυτά τα σχόλια εμφανίζονται όταν ο χρήστης περνάει το ποντίκι πάνω από τη διαγράμμιση.

### Βήμα 3 – Ορισμός Περιοχής Διαγράμμισης
Καθορίστε το ορθογώνιο που περιβάλλει το κείμενο που θέλετε να διαγράψετε:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **Coordinate tip:** Η αρχή (0,0) είναι η πάνω‑αριστερή γωνία της σελίδας· το X αυξάνεται προς τα δεξιά, το Y προς τα κάτω. Χρησιμοποιήστε έναν προβολέα PDF που εμφανίζει συντεταγμένες για να ρυθμίσετε ακριβώς αυτές τις τιμές.

### Βήμα 4 – Διαμόρφωση του Σημειώματος Διαγράμμισης
Ορίστε την εμφάνιση, τον αριθμό σελίδας και επισυνάψτε τα σχόλια:

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

*Σημείωση χρώματος:* `65535` αντιστοιχεί στο κίτρινο σε ακέραιο μορφή RGB. Αλλάξτε την τιμή για να χρησιμοποιήσετε άλλα χρώματα.

### Βήμα 5 – Εφαρμογή του Σημειώματος και Αποθήκευση
Προσθέστε το σημείωμα στο έγγραφο και γράψτε το αρχείο εξόδου:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### Βήμα 6 – Καθαρισμός Πόρων (Κρίσιμο!)
Πάντα απελευθερώστε το annotator για να ελευθερώσετε τους εγγενείς πόρους:

```java
if (annotator != null) {
    annotator.dispose();
}
```

Σε παραγωγή, τυλίξτε τη χρήση σε μπλοκ try‑with‑resources ή σε δομή `try/finally`.

## Συχνά Προβλήματα και Πώς να τα Διορθώσετε

| Πρόβλημα | Σύμπτωμα | Διόρθωση |
|----------|----------|----------|
| **File Not Found** | `Annotator` προκαλεί εξαίρεση | Χρησιμοποιήστε απόλυτες διαδρομές, επαληθεύστε τα δικαιώματα ανάγνωσης, βεβαιωθείτε ότι καμία άλλη διεργασία δεν κλειδώνει το αρχείο |
| **Wrong Coordinates** | Η διαγράμμιση εμφανίζεται μακριά από το επιθυμητό κείμενο | Ελέγξτε ξανά το σύστημα συντεταγμένων του προβολέα PDF· προσαρμόστε τα σημεία αναλόγως |
| **Annotation Invisible** | Δεν υπάρχει ορατή διαγράμμιση μετά την αποθήκευση | Αυξήστε την `opacity` (π.χ., `0.9`), επαληθεύστε το `pageNumber` (από 0), βεβαιωθείτε ότι τα σημεία σχηματίζουν σωστό ορθογώνιο |
| **OutOfMemoryError** | Η εφαρμογή καταρρέει σε μεγάλα PDF | Αυξήστε τη μνήμη heap της JVM (`-Xmx2048m`), επεξεργαστείτε τα έγγραφα σε παρτίδες, πάντα καλέστε `dispose()` |

## Καλές Πρακτικές Απόδοσης για Παραγωγή

### Διαχείριση Μνήμης
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

### Στρατηγική Επεξεργασίας σε Παρτίδες
Όταν χρειάζεται να σημειώσετε δεκάδες ή εκατοντάδες αρχεία:

- Επεξεργαστείτε 10‑20 έγγραφα ανά παρτίδα.  
- Καταγράψτε επιτυχία/αποτυχία για κάθε αρχείο.  
- Επαναρχικοποιήστε το `Annotator` για κάθε έγγραφο ώστε να αποφύγετε διαρροές μνήμης.  

### Συμβουλές Caching
- Αποθηκεύστε στην cache πρότυπα εγγράφων που χρησιμοποιούνται συχνά.  
- Αποθηκεύστε προ‑υπολογισμένους χάρτες συντεταγμένων για τυπικές διατάξεις.  

## Πραγματικές Περιπτώσεις Χρήσης

1. **Document Review Systems** – Οι συντάκτες προτείνουν διαγραφές χωρίς να τροποποιούν το αρχικό συμβόλαιο.  
2. **Legal Amendments** – Οι δικηγόροι παρακολουθούν την αφαίρεση ρήρων ενώ διατηρούν την αρχική διατύπωση για έλεγχο.  
3. **Academic Peer Review** – Οι αξιολογητές σημειώνουν ενότητες για αφαίρεση και προσθέτουν ενσωματωμένα σχόλια.  
4. **Content Migration** – Κατά τη διάρκεια μεταναστεύσεων CMS, οι διαγράμμιση επισημαίνουν παλιό κείμενο που χρειάζεται αντικατάσταση.  

## Προχωρημένη Προσαρμογή

### Προσαρμοσμένο Στυλ
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### Προσθήκη Μεταδεδομένων
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## Λίστα Ελέγχου Επίλυσης Προβλημάτων
- ✅ Μπορείτε να ανοίξετε το πηγαίο αρχείο χειροκίνητα;  
- ✅ Υπάρχουν όλες οι εξαρτήσεις GroupDocs στην classpath;  
- ✅ Δημιουργούν τα σημεία έγκυρο ορθογώνιο;  
- ✅ Είναι σωστός ο αριθμός σελίδας (από 0);  
- ✅ Υπάρχει αρκετή μνήμη heap;  
- ✅ Έχετε δικαίωμα εγγραφής στον φάκελο εξόδου;  
- ✅ Υποστηρίζεται η μορφή εγγράφου (PDF, DOCX, PPTX, κλπ);  

## Συχνές Ερωτήσεις

**Q: Μπορώ να χρησιμοποιήσω το GroupDocs.Annotation μέσα σε υπηρεσία Spring Boot;**  
A: Ναι. Προσθέστε την εξάρτηση Maven, ενσωματώστε μια κλάση υπηρεσίας που δημιουργεί το `Annotator`, και διαχειριστείτε τον κύκλο ζωής του με τις περιοχές bean του Spring.

**Q: Ποιες μορφές εγγράφων υποστηρίζουν σημειώματα διαγράμμισης;**  
A: PDF, DOCX, PPTX, και πολλές άλλες μορφές που υποστηρίζονται από το GroupDocs.Annotation. Το PDF προσφέρει τον πιο ακριβή χειρισμό συντεταγμένων.

**Q: Πώς να διαχειριστώ έγγραφα με διαφορετικά μεγέθη σελίδας;**  
A: Ανακτήστε τις διαστάσεις της σελίδας μέσω `annotator.getPageInfo(pageNumber)` και κλιμακώστε τις συντεταγμένες σας αναλόγως.

**Q: Μπορεί να επεξεργαστώ ή να διαγράψω ένα υπάρχον σημείωμα διαγράμμισης;**  
A: Απόλυτα. Χρησιμοποιήστε `annotator.getAnnotations(pageNumber)` για να το ανακτήσετε, στη συνέχεια `annotator.update(updatedAnnotation)` ή `annotator.delete(annotationId)`.

**Q: Ποιος είναι ο αντίκτυπος στην απόδοση όταν προστίθενται πολλά σημειώματα;**  
A: Η προσθήκη εκατοντάδων σημειωμάτων είναι γενικά εντάξει, αλλά παρακολουθήστε τη χρήση μνήμης. Για πολύ μεγάλα σύνολα σημειωμάτων, σκεφτείτε την σελιδοποίηση της προβολής ή τη lazy‑loading των σημειωμάτων κατά απαίτηση.

## Συμπέρασμα
Τώρα έχετε έναν πλήρη, έτοιμο για παραγωγή οδηγό για **add strikeout annotation java** χρησιμοποιώντας το GroupDocs.Annotation. Ξεκινήστε με το απλό παράδειγμα ελέγχου, στη συνέχεια επεκτείνετε σε επεξεργασία σε παρτίδες, προσαρμοσμένο στυλ και εμπλουτισμό μεταδεδομένων. Θυμηθείτε να δοκιμάζετε προσεκτικά τις συντεταγμένες, να διαχειρίζεστε τους πόρους υπεύθυνα και να επιλέγετε το κατάλληλο μοντέλο αδειοδότησης για το περιβάλλον σας.

Έτοιμοι να εξερευνήσετε περισσότερα; Δείτε άλλους τύπους σημειώματος—υπογράμμιση, σημείωση, εικόνα, βέλος και υδατογράφημα—για να δημιουργήσετε μια πλήρη σουίτα συνεργασίας εγγράφων.

---

**Τελευταία Ενημέρωση:** 2026-03-30  
**Δοκιμάστηκε Με:** GroupDocs.Annotation 25.2 for Java  
**Συγγραφέας:** GroupDocs  

**Πρόσθετοι Πόροι**

- [GroupDocs Annotation Documentation](https://docs.groupdocs.com/annotation/java/)
- [API Reference Guide](https://reference.groupdocs.com/annotation/java/)
- [Download Latest Version](https://releases.groupdocs.com/annotation/java/)
- [Purchase Full License](https://purchase.groupdocs.com/buy)
- [Start Free Trial](https://releases.groupdocs.com/annotation/java/)
- [Get Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Community Support Forum](https://forum.groupdocs.com/c/annotation/)