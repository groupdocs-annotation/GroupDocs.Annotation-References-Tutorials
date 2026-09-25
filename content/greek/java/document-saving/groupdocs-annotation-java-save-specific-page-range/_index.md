---
categories:
- Java Development
date: '2026-09-25'
description: Μάθετε πώς να αποθηκεύσετε συγκεκριμένες σελίδες pdf χρησιμοποιώντας
  try resources στη Java με GroupDocs.Annotation. Περιλαμβάνει παράδειγμα υπηρεσίας
  Spring Boot και συμβουλές απόδοσης.
keywords:
- save specific pdf pages
- try with resources java
- remove unused pdf pages
- use try resources
lastmod: '2026-09-25'
linktitle: Αποθήκευση Συγκεκριμένων Σελίδων Java Annotation
og_description: Μάθετε πώς να αποθηκεύσετε συγκεκριμένες σελίδες pdf χρησιμοποιώντας
  try resources στη Java με GroupDocs.Annotation. Οδηγός βήμα προς βήμα, συμβουλές
  απόδοσης και ενσωμάτωση Spring Boot.
og_image_alt: Guide to saving specific PDF pages in Java using GroupDocs.Annotation
  and try resources
og_title: Πώς να αποθηκεύσετε συγκεκριμένες σελίδες pdf με try resources στη Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-25'
  description: Learn how to save specific pdf pages using try resources in Java with
    GroupDocs.Annotation. Includes Spring Boot service example and performance tips.
  headline: How to save specific pdf pages with try resources in Java
  type: TechArticle
- questions:
  - answer: Not with a single `SaveOptions` call. Run separate saves for each range
      and merge the results afterward.
    question: Can I save non‑consecutive pages (e.g., 1, 3, 7)?
  - answer: 'Yes—provide the password when constructing the `Annotator`: `new Annotator(inputFile,
      loadOptions.setPassword("your_password"))`.'
    question: Does this work with password‑protected documents?
  - answer: PDF, Microsoft Word, Excel, PowerPoint, and many others. See the [official
      documentation](https://docs.groupdocs.com/annotation/java/) for the full list.
    question: What file formats are supported?
  - answer: Absolutely—set `saveOptions.setAnnotationsOnly(true)` to create an annotation‑only
      file.
    question: Can I save just the annotations without the original content?
  - answer: Use `setLoadOnlyAnnotatedPages(true)`, process in chunks, and consider
      increasing the JVM heap size.
    question: How do I handle very large documents (1000+ pages)?
  type: FAQPage
tags:
- save specific pdf pages
- groupdocs
- java annotation
- document processing
- pdf manipulation
title: Πώς να αποθηκεύσετε συγκεκριμένες σελίδες pdf με try resources στη Java
type: docs
url: /el/java/document-saving/groupdocs-annotation-java-save-specific-page-range/
weight: 1
---

# Πώς να αποθηκεύσετε συγκεκριμένες σελίδες pdf από σχολιασμένα έγγραφα σε Java

Όταν χρειάζεται να **αποθηκεύσετε συγκεκριμένες σελίδες pdf** από ένα μεγάλο, σχολιασμένο αρχείο, η χρήση του προτύπου *try with resources* της Java μαζί με το GroupDocs.Annotation σας παρέχει μια ασφαλή, αποδοτική σε μνήμη λύση. Αυτό το tutorial σας δείχνει πώς να ρυθμίσετε τη βιβλιοθήκη, να εξάγετε ένα εύρος σελίδων και να ενσωματώσετε τη λογική σε μια υπηρεσία Spring Boot — όλα ενώ διατηρείτε τον κώδικά σας καθαρό και τους πόρους σας σωστά απελευθερωμένους.

## Εισαγωγή

`Annotator` είναι η κύρια κλάση στο GroupDocs.Annotation που φορτώνει ένα έγγραφο και παρέχει μεθόδους για διαχείριση και αποθήκευση σχολίων.  
Σε πολλές επιχειρηματικές περιπτώσεις—νομικές συμβάσεις, τεχνικά εγχειρίδια ή ερευνητικές εργασίες—συχνά χρειάζεστε μόνο λίγες σελίδες που περιέχουν τα σχετικά σχόλια. Η εξαγωγή μόνο αυτών των σελίδων μειώνει το κόστος αποθήκευσης έως και 96 %, επιταχύνει την επεξεργασία downstream και σας βοηθά να παραμείνετε συμμορφωμένοι μοιράζοντας μόνο τα επιτρεπόμενα τμήματα.

**Τι θα μάθετε μέχρι το τέλος αυτού του οδηγού:**  
- Εγκατάσταση και αδειοδότηση του GroupDocs.Annotation για Java  
- Χρήση του `try with resources` για ασφαλή αποθήκευση εύρους σελίδων  
- Διαχείριση μεγάλων PDF με χαμηλό φορτίο μνήμης  
- Ενσωμάτωση της λογικής σε μια υπηρεσία εγγράφων Spring Boot  
- Επίλυση κοινών προβλημάτων όπως κλειδωμένα αρχεία και σφάλματα έλλειψης μνήμης  

## Σύντομες απαντήσεις
- **Τι κάνει το “try with resources java”;** Κλείνει αυτόματα το `Annotator`, αποτρέποντας κλειδώματα αρχείων και διαρροές μνήμης.  
- **Ποια βιβλιοθήκη διαχειρίζεται την αποθήκευση εύρους σελίδων;** Η `GroupDocs.Annotation` παρέχει `SaveOptions` με `setFirstPage`/`setLastPage`. Το `SaveOptions` σας επιτρέπει να καθορίσετε ρυθμίσεις εξόδου όπως το εύρος σελίδων και αν θα συμπεριληφθούν μόνο τα σχόλια.  
- **Μπορώ να το χρησιμοποιήσω σε υπηρεσία Spring Boot;** Ναι – δείτε την ενότητα “Spring Boot document service integration”.  
- **Χρειάζομαι άδεια;** Η δωρεάν δοκιμή λειτουργεί για ανάπτυξη· απαιτείται πλήρης άδεια για παραγωγή.  
- **Είναι ασφαλές για μεγάλα PDF (1000+ σελίδες);** Χρησιμοποιήστε τη φόρτωση μόνο σχολιασμένων σελίδων και επεξεργασία σε παρτίδες για να κρατήσετε τη χρήση μνήμης χαμηλή.  

## Τι είναι η αποθήκευση συγκεκριμένων σελίδων pdf;

Η λειτουργία **save specific pdf pages** εξάγει ένα καθορισμένο διάστημα σελίδων από ένα πηγαίο έγγραφο διατηρώντας όλα τα σχόλια σε αυτές τις σελίδες. Δημιουργεί ένα νέο, μικρότερο PDF που περιέχει μόνο τις επιλεγμένες σελίδες, κάτι ιδανικό για στοχευμένη κοινοποίηση ή αρχειοθέτηση.

## Γιατί να χρησιμοποιήσετε try with resources για την αποθήκευση σελίδων;

Η χρήση του `try with resources` εγγυάται ότι η παρουσία `Annotator` διαγράφεται αμέσως μόλις λήξει το μπλοκ. Αυτός ο καθοριστικός καθαρισμός αποτρέπει την κοινή εξαίρεση “file is locked” και διατηρεί το αποτύπωμα της στοίβας της JVM προβλέψιμο—ιδιαίτερα σημαντικό όταν επεξεργάζεστε δεκάδες μεγάλα PDF παράλληλα.

## Προαπαιτούμενα και ρύθμιση

### Τι θα χρειαστείτε
- **JDK 8+** (συνιστάται JDK 11+)  
- **Maven** ή **Gradle** για διαχείριση εξαρτήσεων  
- **GroupDocs.Annotation for Java** — έκδοση 25.2 ή νεότερη (υποστηρίζει 50+ μορφές)  
- Βασική εξοικείωση με Java I/O και OOP  

### Ρύθμιση του GroupDocs.Annotation για Java

#### Διαμόρφωση Maven

Προσθέστε την εξάρτηση στο `pom.xml` σας (η αντιγραφή‑επικόλληση είναι χρήσιμη εδώ):

```xml
<!-- ```xml
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
``` -->
```

#### Ρύθμιση Gradle (αν προτιμάτε Gradle)

```groovy
// ```gradle
repositories {
    maven {
        url "https://releases.groupdocs.com/annotation/java/"
    }
}

dependencies {
    implementation 'com.groupdocs:groupdocs-annotation:25.2'
}
```
```

### Απόκτηση της άδειας

Ξεκινήστε με τη δωρεάν δοκιμή, μετά προχωρήστε σε προσωρινή ή πλήρη άδεια ανάλογα με τις ανάγκες.

- **Δωρεάν δοκιμή:** Ιδανική για δοκιμές και ανάπτυξη – κατεβάστε την από [GroupDocs releases](https://releases.groupdocs.com/annotation/java/)  
- **Προσωρινή άδεια:** Χρειάζεστε περισσότερο χρόνο για αξιολόγηση; Αποκτήστε μια [temporary license](https://purchase.groupdocs.com/temporary-license/)  
- **Πλήρης άδεια:** Έτοιμοι για παραγωγή; [Purchase here](https://purchase.groupdocs.com/buy)  

> **Συμβουλή:** Η δοκιμαστική έκδοση αφαιρεί μόνο μερικές προχωρημένες λειτουργίες, κάτι που είναι περισσότερο από αρκετό για να ακολουθήσετε αυτό το tutorial και να δημιουργήσετε ένα proof of concept.

## Πώς λειτουργεί το try with resources στη Java;

Το `try` `with` `resources` καλεί αυτόματα το `close()` σε οποιοδήποτε αντικείμενο που υλοποιεί το `AutoCloseable` στο τέλος του μπλοκ. Όταν τυλίγετε μια παρουσία `Annotator` σε αυτή τη δομή, η βιβλιοθήκη απελευθερώνει τους χειριστές αρχείων και καθαρίζει εσωτερικές μνήμες χωρίς επιπλέον κώδικα, εξαλείφοντας τον κίνδυνο παραμένων κλειδωμάτων.

## Κύρια υλοποίηση: αποθήκευση συγκεκριμένων εύρους σελίδων

### Η άγκυρα ορισμού `Annotator`

`Annotator` είναι η κύρια κλάση του GroupDocs.Annotation για φόρτωση, επεξεργασία και αποθήκευση σχολιασμένων εγγράφων. Παρέχει μεθόδους για πρόσβαση σε σχόλια, τροποποίηση σελίδων και εξαγωγή αποτελεσμάτων.

### Βήμα 1: ρύθμιση βοηθητικών λειτουργιών διαδρομής αρχείων

Δημιουργήστε έναν μικρό βοηθό που δημιουργεί διαδρομές εξόδου με συνέπεια:

```java
// ```java
import org.apache.commons.io.FilenameUtils;

public class FilePathConfiguration {
    public String getOutputFilePath(String inputFile) {
        return "YOUR_OUTPUT_DIRECTORY/SavingSpecificPageRange" + "." + FilenameUtils.getExtension(inputFile);
    }
}
```
```

Η κεντρικοποίηση της λογικής διαδρομών καθιστά εύκολο το μεταγενέστερο αλλαγή καταλόγων και διατηρεί τον κώδικά σας δοκιμαστικό.

### Βήμα 2: υλοποίηση αποθήκευσης εύρους σελίδων

Το παρακάτω απόσπασμα δείχνει τη βασική λογική. Χρησιμοποιεί `try with resources` για να εγγυηθεί τον καθαρισμό:

```java
// ```java
import com.groupdocs.annotation.Annotator;
import com.groupdocs.annotation.options.export.SaveOptions;

public class SaveSpecificPageRange {
    public void run(String inputFile) {
        String outputPath = new FilePathConfiguration().getOutputFilePath(inputFile);
        
        try (final Annotator annotator = new Annotator(inputFile)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(2);  // Start from page 2
            saveOptions.setLastPage(4);   // End at page 4
            
            annotator.save(outputPath, saveOptions);
        }
    }
}
```
```

- `setFirstPage(2)` και `setLastPage(4)` ορίζουν ένα **συμπεριλαμβανόμενο** εύρος (σελίδες 2‑4).  
- Το `Annotator` κλείνει αυτόματα όταν το μπλοκ ολοκληρωθεί, αποτρέποντας προβλήματα κλειδώματος αρχείων.

### Προχωρημένη διαμόρφωση διαδρομής αρχείων

Για παραγωγή μπορεί να θέλετε δυναμική ονομασία:

```java
// ```java
public class FilePathConfiguration {
    private final String baseOutputDirectory;
    
    public FilePathConfiguration(String baseOutputDirectory) {
        this.baseOutputDirectory = baseOutputDirectory;
    }
    
    public String getInputFilePath(String filename) {
        return "YOUR_DOCUMENT_DIRECTORY/" + filename;
    }
    
    public String getOutputFilePath(String inputFile, String suffix) {
        String baseName = FilenameUtils.getBaseName(inputFile);
        String extension = FilenameUtils.getExtension(inputFile);
        return String.format("%s/%s_%s.%s", baseOutputDirectory, baseName, suffix, extension);
    }
}
```
```

Τώρα το αρχείο εξόδου θα ονομάζεται κάτι όπως `contract_pages_2-4.pdf`, καθιστώντας σαφές ποιες σελίδες εξήχθησαν.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

### Παγίδα #1: σύγχυση δεικτών σελίδας

**Πρόβλημα:** Υποθέτετε ότι οι αριθμοί σελίδων ξεκινούν από 0.  
**Λύση:** Η αρίθμηση σελίδων στο GroupDocs.Annotation ξεκινά από 1, ταιριάζοντας με αυτό που βλέπουν οι χρήστες στους προβολείς PDF.

```java
// ```java
// Wrong - this tries to start from page 0 (doesn't exist)
saveOptions.setFirstPage(0);

// Right - this starts from the actual first page
saveOptions.setFirstPage(1);
```
```

### Παγίδα #2: διαρροές πόρων

**Πρόβλημα:** Η παράλειψη κλεισίματος του `Annotator` οδηγεί σε κλειδωμένα αρχεία.  
**Λύση:** Πάντα τυλίξτε το `Annotator` σε ένα μπλοκ `try with resources` ή καλέστε το `close()` ρητά.

```java
// ```java
// Good - automatic resource management
try (final Annotator annotator = new Annotator(inputFile)) {
    // your code here
} // automatically closes

// Also acceptable - manual closing
Annotator annotator = null;
try {
    annotator = new Annotator(inputFile);
    // your code here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
```

### Παγίδα #3: μη έγκυρα εύρη σελίδων

**Πρόβλημα:** Καθορισμός εύρους που υπερβαίνει τον αριθμό σελίδων του εγγράφου.  
**Λύση:** Επικυρώστε το εύρος έναντι του `annotator.getDocumentInfo().getPagesCount()` πριν την αποθήκευση.

```java
// ```java
public void savePageRangeWithValidation(String inputFile, int firstPage, int lastPage) {
    try (final Annotator annotator = new Annotator(inputFile)) {
        // Get document info to check page count
        DocumentInfo documentInfo = annotator.getDocument().getDocumentInfo();
        int totalPages = documentInfo.getPageCount();
        
        // Validate range
        if (firstPage < 1 || firstPage > totalPages) {
            throw new IllegalArgumentException("First page out of range: " + firstPage);
        }
        if (lastPage < firstPage || lastPage > totalPages) {
            throw new IllegalArgumentException("Last page out of range: " + lastPage);
        }
        
        SaveOptions saveOptions = new SaveOptions();
        saveOptions.setFirstPage(firstPage);
        saveOptions.setLastPage(lastPage);
        
        String outputPath = new FilePathConfiguration().getOutputFilePath(inputFile);
        annotator.save(outputPath, saveOptions);
    }
}
```
```

## Συμβουλές βελτιστοποίησης απόδοσης

### Διαχείριση μνήμης για μεγάλα έγγραφα

Κατά την επεξεργασία PDF με 100 + σελίδες, ενεργοποιήστε τη φόρτωση μόνο σχολιασμένων σελίδων για να κρατήσετε τη στοίβα χαμηλή:

```java
// ```java
public class OptimizedPageRangeSaver {
    public void saveWithOptimization(String inputFile, int firstPage, int lastPage) {
        // Configure for lower memory usage
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setLoadOnlyAnnotatedPages(true); // Only load pages with annotations
        
        try (final Annotator annotator = new Annotator(inputFile, loadOptions)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(firstPage);
            saveOptions.setLastPage(lastPage);
            
            // Optional: Enable compression for smaller output files
            saveOptions.setAnnotationsOnly(false); // Set to true if you only want annotations
            
            String outputPath = new FilePathConfiguration().getOutputFilePath(inputFile);
            annotator.save(outputPath, saveOptions);
        }
    }
}
```
```

Κύριες στρατηγικές:
- `setLoadOnlyAnnotatedPages(true)` μειώνει τη χρήση μνήμης φορτώνοντας μόνο τις σελίδες που περιέχουν σχόλια.  
- `setAnnotationsOnly(true)` δημιουργεί ένα ελαφρύ αρχείο που αποθηκεύει μόνο το επίπεδο σχολίων.  
- Η επεξεργασία σε παρτίδες με σταθερό thread pool αποτρέπει την εξάντληση των πόρων του συστήματος.

### Επεξεργασία σε παρτίδες πολλαπλών εγγράφων

Για σενάρια υψηλής απόδοσης, επεξεργαστείτε αρχεία σε παρτίδες:

```java
// ```java
public class BatchPageRangeSaver {
    public void processBatch(List<String> inputFiles, int firstPage, int lastPage) {
        for (String inputFile : inputFiles) {
            try {
                savePageRangeWithValidation(inputFile, firstPage, lastPage);
                System.out.println("Successfully processed: " + inputFile);
            } catch (Exception e) {
                System.err.println("Failed to process " + inputFile + ": " + e.getMessage());
                // Log the error and continue with next file
            }
        }
    }
}
```
```

## Ενσωμάτωση με δημοφιλή πλαίσια

### Ενσωμάτωση υπηρεσίας εγγράφων Spring Boot

Παρακάτω υπάρχει μια ελάχιστη υπηρεσία Spring Boot που λαμβάνει ένα PDF, εξάγει ένα εύρος σελίδων και επιστρέφει το νέο αρχείο ως byte array.

```java
// ```java
@Service
public class DocumentPageRangeService {
    
    @Value("${app.document.output-directory}")
    private String outputDirectory;
    
    public String savePageRange(String inputFile, int firstPage, int lastPage) {
        try (final Annotator annotator = new Annotator(inputFile)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(firstPage);
            saveOptions.setLastPage(lastPage);
            
            String outputPath = generateOutputPath(inputFile, firstPage, lastPage);
            annotator.save(outputPath, saveOptions);
            
            return outputPath;
        } catch (Exception e) {
            throw new DocumentProcessingException("Failed to save page range", e);
        }
    }
    
    private String generateOutputPath(String inputFile, int firstPage, int lastPage) {
        String baseName = FilenameUtils.getBaseName(inputFile);
        String extension = FilenameUtils.getExtension(inputFile);
        return String.format("%s/%s_pages_%d-%d.%s", 
                            outputDirectory, baseName, firstPage, lastPage, extension);
    }
}
```
```

Η υπηρεσία χρησιμοποιεί injection κατασκευής για το `AnnotatorFactory`, διατηρώντας τον ελεγκτή ελαφρύ και δοκιμαστικό.

## Πρακτικές εφαρμογές και περιπτώσεις χρήσης

### Επεξεργασία νομικών εγγράφων

Τα νομικά γραφεία συχνά χρειάζονται να μοιραστούν μόνο τις ρήτρες που έχουν ελεγχθεί. Η εξαγωγή αυτών των σελίδων μειώνει τον κίνδυνο αποκάλυψης εμπιστευτικών τμημάτων.

```java
// ```java
public class LegalDocumentProcessor {
    public void extractEvidencePages(String caseFile, List<Integer> evidencePages) {
        // Group consecutive pages for efficient processing
        List<PageRange> ranges = groupConsecutivePages(evidencePages);
        
        for (PageRange range : ranges) {
            String outputFile = String.format("evidence_%d_%d-to-%d.pdf", 
                                            getCaseNumber(caseFile), range.start, range.end);
            savePageRange(caseFile, range.start, range.end, outputFile);
        }
    }
}
```
```

### Διαχείριση εκπαιδευτικού περιεχομένου

Οι δάσκαλοι μπορούν να εξάγουν μόνο τα σχολιασμένα κεφάλαια που χρειάζονται οι μαθητές για μια εργασία, μειώνοντας το μέγεθος λήψης και βελτιώνοντας τη συγκέντρωση.

```java
// ```java
public class EducationalContentExtractor {
    public void createAssignmentPacket(String textbook, int chapterStart, int chapterEnd) {
        try (final Annotator annotator = new Annotator(textbook)) {
            SaveOptions saveOptions = new SaveOptions();
            saveOptions.setFirstPage(chapterStart);
            saveOptions.setLastPage(chapterEnd);
            
            String assignmentFile = generateAssignmentFileName(textbook, chapterStart, chapterEnd);
            annotator.save(assignmentFile, saveOptions);
        }
    }
}
```
```

### Ανασκοπήσεις διασφάλισης ποιότητας

Οι ομάδες QA μπορούν να απομονώσουν σελίδες με σχόλια ελεγκτών, επιτρέποντας ταχύτερους κύκλους επανάληψης.

```java
// ```java
public class QAReviewExtractor {
    public void extractReviewedPages(String document) {
        try (final Annotator annotator = new Annotator(document)) {
            // Get pages with annotations
            List<Integer> annotatedPages = getAnnotatedPageNumbers(annotator);
            
            if (!annotatedPages.isEmpty()) {
                int firstPage = Collections.min(annotatedPages);
                int lastPage = Collections.max(annotatedPages);
                
                SaveOptions saveOptions = new SaveOptions();
                saveOptions.setFirstPage(firstPage);
                saveOptions.setLastPage(lastPage);
                
                String reviewFile = document.replace(".pdf", "_review_comments.pdf");
                annotator.save(reviewFile, saveOptions);
            }
        }
    }
}
```
```

## Σύνοψη βέλτιστων πρακτικών

1. **Επικυρώστε τους αριθμούς σελίδων** πριν καλέσετε τη λειτουργία αποθήκευσης.  
2. **Πάντα χρησιμοποιείτε `try with resources`** για να εγγυηθείτε ότι το `Annotator` κλείνει.  
3. **Ενεργοποιήστε `setLoadOnlyAnnotatedPages(true)`** για μεγάλα PDF ώστε να διατηρείτε τη χρήση μνήμης υπό έλεγχο.  
4. **Δοκιμάστε σε όλα τα υποστηριζόμενα μορφότυπα**—το GroupDocs.Annotation υποστηρίζει πάνω από 50 τύπους εισόδου και εξόδου, συμπεριλαμβανομένων PDF, DOCX, XLSX, PPTX και αρχείων εικόνας.  
5. **Παρακολουθείτε τη στοίβα JVM** και προσαρμόστε το `-Xmx` όπως χρειάζεται για εργασίες σε παρτίδες.  

## Επίλυση κοινών προβλημάτων

### Πρόβλημα: σφάλμα “File is locked”

**Συμπτώματα:** Μία εξαίρεση που αναφέρει κλειδωμένο αρχείο εμφανίζεται κατά το `save()`.  
**Αιτίες:**  
- Μια προηγούμενη παρουσία `Annotator` δεν κλείστηκε.  
- Το αρχείο είναι ανοιχτό σε άλλη εφαρμογή.  
- Ανεπαρκή δικαιώματα συστήματος αρχείων.  

**Λύση:** Βεβαιωθείτε ότι κάθε `Annotator` τυλίγεται σε `try with resources` και ελέγξτε τα κλειδώματα αρχείων σε επίπεδο λειτουργικού συστήματος.

```java
// ```java
// Ensure proper cleanup
try (final Annotator annotator = new Annotator(inputFile)) {
    // ... your code ...
} // Automatically releases file handles

// Verify file accessibility before processing
File file = new File(inputFile);
if (!file.canRead()) {
    throw new IllegalArgumentException("Cannot read input file: " + inputFile);
}
if (!file.getParentFile().canWrite()) {
    throw new IllegalArgumentException("Cannot write to output directory");
}
```
```

### Πρόβλημα: σφάλματα έλλειψης μνήμης

**Συμπτώματα:** `OutOfMemoryError` κατά την επεξεργασία μεγάλων PDF.  
**Λύσεις:**  
1. Αυξήστε τη στοίβα JVM (`-Xmx2g` ή μεγαλύτερη).  
2. Χρησιμοποιήστε `setLoadOnlyAnnotatedPages(true)` και `setAnnotationsOnly(true)`.  
3. Επεξεργαστείτε έγγραφα σε μικρότερες παρτίδες.

### Πρόβλημα: τα σχόλια δεν διατηρούνται

**Συμπτώματα:** Το αρχείο εξόδου δεν περιέχει την αρχική σήμανση.  
**Λύση:** Μην ενεργοποιήσετε κατά λάθος το `setAnnotationsOnly(false)`· διατηρήστε την προεπιλογή για να διατηρηθούν τα σχόλια.

```java
// ```java
SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationsOnly(false); // Keep both content and annotations
saveOptions.setFirstPage(firstPage);
saveOptions.setLastPage(lastPage);
```
```

## Συχνές ερωτήσεις

- **Ε: Μπορώ να αποθηκεύσω μη διαδοχικές σελίδες (π.χ., 1, 3, 7);**  
  Α: Δεν είναι δυνατόν με μία κλήση `SaveOptions`. Εκτελέστε ξεχωριστές αποθηκεύσεις για κάθε εύρος και συγχωνεύστε τα αποτελέσματα μετά.

- **Ε: Λειτουργεί αυτό με έγγραφα προστατευμένα με κωδικό;**  
  Α: Ναι—παρέχετε τον κωδικό κατά τη δημιουργία του `Annotator`: `new Annotator(inputFile, loadOptions.setPassword("your_password"))`.

- **Ε: Ποιοι τύποι αρχείων υποστηρίζονται;**  
  Α: PDF, Microsoft Word, Excel, PowerPoint και πολλοί άλλοι. Δείτε την [official documentation](https://docs.groupdocs.com/annotation/java/) για την πλήρη λίστα.

- **Ε: Μπορώ να αποθηκεύσω μόνο τα σχόλια χωρίς το αρχικό περιεχόμενο;**  
  Α: Απόλυτα—ορίστε `saveOptions.setAnnotationsOnly(true)` για να δημιουργήσετε ένα αρχείο μόνο με σχόλια.

- **Ε: Πώς να διαχειριστώ πολύ μεγάλα έγγραφα (1000+ σελίδες);**  
  Α: Χρησιμοποιήστε `setLoadOnlyAnnotatedPages(true)`, επεξεργαστείτε σε τμήματα και σκεφτείτε την αύξηση του μεγέθους της στοίβας JVM.

- **Ε: Υπάρχει τρόπος προεπισκόπησης των σελίδων πριν την αποθήκευση;**  
  Α: Το GroupDocs.Annotation εστιάζει στην επεξεργασία, αλλά μπορείτε να λάβετε τον αριθμό σελίδων και τις θέσεις σχολίων μέσω `annotator.getDocumentInfo()` για να αποφασίσετε ποια εύρη θα εξάγετε.

## Πρόσθετοι πόροι

- Τεκμηρίωση: [GroupDocs.Annotation for Java Docs](https://docs.groupdocs.com/annotation/java/)  
- Επίσημη τεκμηρίωση: [official documentation](https://docs.groupdocs.com/annotation/java/)  
- Αναφορά API: [Complete API Documentation](https://reference.groupdocs.com/annotation/java/)  
- Λήψη: [Latest Releases](https://releases.groupdocs.com/annotation/java/)  
- Εκδόσεις GroupDocs: [GroupDocs releases](https://releases.groupdocs.com/annotation/java/)  
- Επιλογές άδειας: [License Options](https://purchase.groupdocs.com/buy)  
- Αγορά εδώ: [Purchase here](https://purchase.groupdocs.com/buy)  
- Δωρεάν δοκιμή: [Try It Now](https://releases.groupdocs.com/annotation/java/)  
- Προσωρινή άδεια: [Get Evaluation License](https://purchase.groupdocs.com/temporary-license/)  
- Υποστήριξη: [Community Forum](https://forum.groupdocs.com/c/annotation/)  

**Τελευταία ενημέρωση:** 2026-09-25  
**Δοκιμάστηκε με:** GroupDocs.Annotation 25.2 (Java)  
**Συγγραφέας:** GroupDocs

## Σχετικά μαθήματα

- [Μείωση μεγέθους PDF Java με GroupDocs.Annotation – Πλήρης Οδηγός](/annotation/java/document-saving/)  
- [Αποθήκευση σχολιασμένου PDF χρησιμοποιώντας GroupDocs Java & Azure Blob](/annotation/java/document-loading/download-annotate-azure-blob-groupdocs-java/)  
- [Φόρτωση PDF με κωδικό πρόσβασης με GroupDocs.Annotation Java](/annotation/java/advanced-features/load-protected-pdf-groupdocs-java/)