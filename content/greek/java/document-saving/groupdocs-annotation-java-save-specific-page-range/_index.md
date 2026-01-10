---
categories:
- Java Development
date: '2026-01-10'
description: Μάθετε πώς να χρησιμοποιείτε το try‑with‑resources στη Java για να αποθηκεύετε
  συγκεκριμένες σελίδες από σχολιασμένα έγγραφα με το GroupDocs.Annotation. Περιλαμβάνει
  παράδειγμα υπηρεσίας εγγράφων Spring Boot.
keywords: save specific pages Java annotation, GroupDocs annotation page range, Java
  document annotation tutorial, selective PDF page saving Java, extract annotated
  pages
lastmod: '2026-01-10'
linktitle: Save Specific Pages Java Annotation
tags:
- groupdocs
- java-annotation
- document-processing
- pdf-manipulation
title: Δοκιμή με πόρους Java – Αποθήκευση συγκεκριμένων σελίδων από επισημασμένα έγγραφα
type: docs
url: /el/java/document-saving/groupdocs-annotation-java-save-specific-page-range/
weight: 1
---

# Πώς να Αποθηκεύσετε Συγκεκριμένες Σελίδες από Ανασκοπημένα Έγγραφα σε Java

## Εισαγωγή

Σας έχει συμβεί ποτέ να βυθίζεστε σε τεράστια ανασκοπημένα έγγραφα όταν χρειάζεστε μόνο μερικές συγκεκριμένες σελίδες; Με το **try with resources java**, μπορείτε να εξάγετε αποδοτικά μόνο τις σελίδες που χρειάζεστε χρησιμοποιώντας το GroupDocs.Annotation. Είτε διαχειρίζεστε νομικά συμβόλαια, τεχνικά εγχειρίδια ή ερευνητικές εργασίες, η εξαγωγή μόνο των σχετικών σελίδων εξοικονομεί χώρο αποθήκευσης, επιταχύνει την επεξεργασία και διατηρεί τη ροή εργασίας σας οργανωμένη.

Σε αυτόν τον οδηγό, θα περάσουμε από όλα όσα χρειάζεται να ξέρετε – από τη ρύθμιση της βιβλιοθήκης μέχρι προχωρημένες τεχνικές βελτιστοποίησης που διατηρούν την εφαρμογή Java σας σε άψογη λειτουργία.

**Τι θα μάθετε στο τέλος:**
- Ρύθμιση του GroupDocs.Annotation στο έργο Java σας (με τον σωστό τρόπο)  
- Υλοποίηση αποθήκευσης επιλεγμένων σελίδων με καθαρό, συντηρήσιμο κώδικα  
- Αποφυγή κοινών παγίδων που παρεμποδίζουν τους περισσότερους προγραμματιστές  
- Βελτιστοποίηση απόδοσης για επεξεργασία μεγάλων εγγράφων  
- Επίλυση προβλημάτων πριν γίνουν ενοχλητικά  

## Γρήγορες Απαντήσεις
- **Τι κάνει το “try with resources java”;** Κλείνει αυτόματα τον Annotator, αποτρέποντας κλειδώσεις αρχείων και διαρροές μνήμης.  
- **Ποια βιβλιοθήκη διαχειρίζεται την αποθήκευση περιοχής σελίδων;** Η `GroupDocs.Annotation` παρέχει `SaveOptions` με `setFirstPage`/`setLastPage`.  
- **Μπορώ να το χρησιμοποιήσω σε υπηρεσία Spring Boot;** Ναι – δείτε την ενότητα “Spring Boot Document Service Integration”.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για ανάπτυξη· απαιτείται πλήρης άδεια για παραγωγή.  
- **Είναι ασφαλές για μεγάλα PDF (1000+ σελίδες);** Χρησιμοποιήστε `load‑only‑annotated‑pages` και επεξεργασία σε παρτίδες για χαμηλή χρήση μνήμης.  

## Γιατί να Αποθηκεύετε Συγκεκριμένες Σελίδες; (Πραγματικό Πλαίσιο)

Πριν βουτήξουμε στην τεχνική πλευρά, ας δούμε γιατί αυτή η δυνατότητα είναι καθοριστική:

**Αποδοτικότητα Αποθήκευσης**: Ένα εγχειρίδιο 500 σελίδων με σημειώσεις μόνο σε 20 σελίδες; Γιατί να αποθηκεύσετε όλες τις 500 όταν μπορείτε να εξάγετε τις 20 σχετικές και να μειώσετε το μέγεθος του αρχείου κατά 96 %;

**Ταχύτερη Επεξεργασία**: Τα μικρότερα αρχεία σημαίνουν ταχύτερα ανεβάσματα, λήψεις και επεξεργασία. Οι χρήστες σας (και οι διακομιστές σας) θα το εκτιμήσουν.

**Καλύτερη Εμπειρία Χρήστη**: Κανείς δεν θέλει να κάνει κύλιση σε εκατοντάδες σελίδες για να βρει τις σημειωμένες ενότητες. Δώστε τους ακριβώς ό,τι χρειάζονται.

**Συμμόρφωση και Ασφάλεια**: Σε κανονιστικές βιομηχανίες, μπορεί να επιτρέπεται η κοινή χρήση μόνο συγκεκριμένων τμημάτων εγγράφων. Η επιλεκτική αποθήκευση διευκολύνει τη συμμόρφωση.  

## Προαπαιτούμενα και Ρύθμιση

### Τι Θα Χρειαστείτε

- **Java Development Kit (JDK)**: Έκδοση 8 ή νεότερη (συνιστάται JDK 11+)  
- **Maven ή Gradle**: Για διαχείριση εξαρτήσεων  
- **GroupDocs.Annotation for Java**: Έκδοση 25.2 ή νεότερη  
- **Βασικές γνώσεις Java**: Κατανόηση I/O αρχείων και OOP  

### Ρύθμιση του GroupDocs.Annotation για Java

#### Διαμόρφωση Maven

Προσθέστε αυτό στο `pom.xml` (προσπαθήστε‑και‑επικολλήστε):

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

#### Ρύθμιση Gradle (Αν Είστε Ομάδα Gradle)

```gradle
repositories {
    maven {
        url "https://releases.groupdocs.com/annotation/java/"
    }
}

dependencies {
    implementation 'com.groupdocs:groupdocs-annotation:25.2'
}
```

### Απόκτηση Άδειας

Αυτό που δεν λένε τα περισσότερα tutorials: **ξεκινήστε με τη δωρεάν δοκιμή**. Σοβαρά. Μην περιπλέκετε τα πράγματα.

- **Δωρεάν Δοκιμή**: Ιδανική για δοκιμές και ανάπτυξη – κατεβάστε την από [GroupDocs releases](https://releases.groupdocs.com/annotation/java/)  
- **Προσωρινή Άδεια**: Χρειάζεστε περισσότερο χρόνο για αξιολόγηση; Πάρτε μια [προσωρινή άδεια](https://purchase.groupdocs.com/temporary-license/)  
- **Πλήρης Άδεια**: Έτοιμοι για παραγωγή; [Αγοράστε εδώ](https://purchase.groupdocs.com/buy)

Συμβουλή: Η δοκιμαστική έκδοση έχει κάποιους περιορισμούς, αλλά είναι περισσότερο από αρκετή για να ακολουθήσετε αυτό το tutorial και να δημιουργήσετε ένα proof of concept.  

## Κύρια Υλοποίηση: Αποθήκευση Συγκεκριμένων Περιοχών Σελίδων

### Η Βασική Προσέγγιση (Ξεκινήστε Εδώ)

Ας αρχίσουμε με την πιο απλή υλοποίηση. Αυτό είναι ό,τι χρειάζονται το 90 % των περιπτώσεων:

#### Βήμα 1: Διαχείριση Διαδρομών Αρχείων

Πρώτα, δημιουργήστε μια βοηθητική κλάση για τη διαχείριση διαδρομών αρχείων (θα σας ευχαριστήσει αργότερα όταν χρειαστεί να αλλάξετε καταλόγους):

```java
import org.apache.commons.io.FilenameUtils;

public class FilePathConfiguration {
    public String getOutputFilePath(String inputFile) {
        return "YOUR_OUTPUT_DIRECTORY/SavingSpecificPageRange" + "." + FilenameUtils.getExtension(inputFile);
    }
}
```

**Γιατί αυτή η προσέγγιση;** Κεντρίζει τη λογική διαδρομών σε ένα κεντρικό σημείο και κάνει τις δοκιμές πιο εύκολες. Η χρήση του `FilenameUtils` διασφαλίζει ότι διατηρείται αυτόματα η αρχική επέκταση αρχείου.

#### Βήμα 2: Υλοποίηση Αποθήκευσης Περιοχής Σελίδων

Εδώ συμβαίνει η μαγεία:

```java
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

**Τι συμβαίνει εδώ:**
- Χρησιμοποιούμε ένα **try‑with‑resources java** block (`try ( … )`) ώστε ο `Annotator` να κλείνει αυτόματα, εξαλείφοντας προβλήματα κλειδώματος αρχείων.  
- `setFirstPage(2)` και `setLastPage(4)` ορίζουν το περιεχόμενο μας (σελίδες 2‑4).  
- Η περιοχή είναι **συμπεριλαμβανομένη** και στα δύο άκρα – λεπτομέρεια που παρερμηνεύουν πολλοί προγραμματιστές.  

### Προχωρημένη Διαμόρφωση Διαδρομών Αρχείων

Για παραγωγικές εφαρμογές, θα θέλετε πιο ευέλικτη διαχείριση διαδρομών:

```java
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

Τώρα μπορείτε να δημιουργείτε ονόματα όπως `contract_pages_2-4.pdf` αυτόματα.  

## Συνηθισμένες Παγίδες και Πώς να τις Αποφύγετε

### Παγίδα #1: Σύγχυση Δεικτών Σελίδων

**Το Πρόβλημα**: Υποθέτετε ότι οι αριθμοί σελίδων ξεκινούν από 0 (δεν είναι έτσι στο GroupDocs.Annotation).

**Η Λύση**: Η αρίθμηση σελίδων ξεκινά από 1, όπως στα πραγματικά έγγραφα. Η σελίδα 1 είναι η πρώτη, όχι η σελίδα 0.

```java
// Wrong - this tries to start from page 0 (doesn't exist)
saveOptions.setFirstPage(0);

// Right - this starts from the actual first page
saveOptions.setFirstPage(1);
```

### Παγίδα #2: Διαρροές Πόρων

**Το Πρόβλημα**: Ξεχάτε να κλείσετε σωστά τον Annotator, προκαλώντας κλειδώσεις αρχείων και διαρροές μνήμης.

**Η Λύση**: Χρησιμοποιείτε πάντα **try‑with‑resources java** ή κλείσιμο με ρητό τρόπο:

```java
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

### Παγίδα #3: Μη Έγκυρες Περιοχές Σελίδων

**Το Πρόβλημα**: Καθορίζετε περιοχές σελίδων που δεν υπάρχουν στο έγγραφο.

**Η Λύση**: Επικυρώστε πρώτα τις περιοχές σας:

```java
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

## Συμβουλές Βελτιστοποίησης Απόδοσης

### Διαχείριση Μνήμης για Μεγάλα Έγγραφα

Όταν επεξεργάζεστε μεγάλα έγγραφα (100 + σελίδες), η χρήση μνήμης γίνεται κρίσιμη:

```java
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

**Βασικές στρατηγικές βελτιστοποίησης**
- `setLoadOnlyAnnotatedPages(true)` μειώνει το αποτύπωμα μνήμης.  
- `setAnnotationsOnly(true)` δημιουργεί ελαφρύ αρχείο που περιέχει μόνο το επίπεδο σημειώσεων.  
- Επεξεργαστείτε έγγραφα σε παρτίδες εάν έχετε πολλά αρχεία.  

### Επεξεργασία Πολλαπλών Εγγράφων σε Παρτίδες

Για παραγωγικά σενάρια όπου επεξεργάζεστε πολλά έγγραφα:

```java
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

## Ενσωμάτωση με Δημοφιλή Frameworks

### Ενσωμάτωση Υπηρεσίας Εγγράφων Spring Boot

Ακολουθεί ένα απλό Spring Boot service για αποθήκευση περιοχής σελίδων (σημειώστε τη φράση **spring boot document service**):

```java
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

## Πρακτικές Εφαρμογές και Περιπτώσεις Χρήσης

### Επεξεργασία Νομικών Εγγράφων

Τα νομικά γραφεία συχνά χρειάζονται να εξάγουν συγκεκριμένα τμήματα συμβάσεων ή δικαστικών εγγράφων:

```java
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

### Διαχείριση Εκπαιδευτικού Περιεχομένου

Καθηγητές που εξάγουν συγκεκριμένα κεφάλαια από βιβλία για εργασίες μαθητών:

```java
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

### Ανασκοπήσεις Ποιοτικού Ελέγχου

Εξαγωγή μόνο των σελίδων με σχόλια ελέγχου για εστιασμένη αναθεώρηση:

```java
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

## Σύνοψη Καλών Πρακτικών

1. **Πάντα επικυρώνετε τις παραμέτρους εισόδου** – ελέγξτε τις περιοχές σελίδων πριν την επεξεργασία.  
2. **Χρησιμοποιείτε try‑with‑resources java** – αποτρέπει διαρροές πόρων και κλειδώματα αρχείων.  
3. **Εφαρμόζετε σωστή διαχείριση σφαλμάτων** – μην αφήνετε ένα κακό αρχείο να καταρρίψει ολόκληρη τη παρτίδα.  
4. **Λαμβάνετε υπόψη τη χρήση μνήμης** – χρησιμοποιήστε `setLoadOnlyAnnotatedPages(true)` για μεγάλα έγγραφα.  
5. **Δοκιμάζετε με διάφορους τύπους αρχείων** – PDF, Word, PowerPoint μπορεί να συμπεριφέρονται διαφορετικά.  
6. **Παρακολουθείτε την απόδοση** – ελέγξτε χρόνους επεξεργασίας και μνήμη σε παραγωγή.  

## Επίλυση Συχνών Προβλημάτων

### Πρόβλημα: Σφάλμα “File is locked”

**Συμπτώματα**: Εξαίρεση κατά την αποθήκευση, με αναφορά σε κλειδώματα αρχείου.  

**Αιτίες**:  
- Ο Annotator δεν κλείστηκε σωστά από προηγούμενη λειτουργία.  
- Το αρχείο είναι ανοιχτό σε άλλη εφαρμογή.  
- Ανεπαρκή δικαιώματα.  

**Λύσεις**:

```java
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

### Πρόβλημα: Σφάλματα Έλλειψης Μνήμης

**Συμπτώματα**: `OutOfMemoryError` κατά την επεξεργασία μεγάλων εγγράφων.  

**Λύσεις**:  
1. Αυξήστε το μέγεθος heap της JVM, π.χ. `-Xmx2g`.  
2. Χρησιμοποιήστε τις βελτιστοποιημένες επιλογές φόρτωσης που εμφανίστηκαν νωρίτερα.  
3. Επεξεργαστείτε τα έγγραφα σε μικρότερες παρτίδες.  

### Πρόβλημα: Οι Σημειώσεις Δεν Διατηρούνται

**Συμπτώματα**: Το αρχείο εξόδου δεν περιέχει τις αρχικές σημειώσεις.  

**Λύση**: Βεβαιωθείτε ότι δεν αφαιρείτε τις σημειώσεις:

```java
SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationsOnly(false); // Keep both content and annotations
saveOptions.setFirstPage(firstPage);
saveOptions.setLastPage(lastPage);
```

## Συχνές Ερωτήσεις

**Ε: Μπορώ να αποθηκεύσω μη συνεχόμενες σελίδες (π.χ. 1, 3, 7);**  
Α: Δεν είναι δυνατόν με μία μόνο λειτουργία. Πρέπει να εκτελέσετε ξεχωριστές αποθηκεύσεις για κάθε περιοχή ή να συνδυάσετε τα αποτελέσματα αργότερα.

**Ε: Λειτουργεί με έγγραφα προστατευμένα με κωδικό;**  
Α: Ναι, αλλά πρέπει να παρέχετε τον κωδικό κατά τη δημιουργία του `Annotator`: `new Annotator(inputFile, loadOptions.setPassword("your_password"))`.

**Ε: Ποιοι τύποι αρχείων υποστηρίζονται;**  
Α: PDF, Microsoft Word, Excel, PowerPoint και πολλοί άλλοι. Δείτε την [επίσημη τεκμηρίωση](https://docs.groupdocs.com/annotation/java/) για την πλήρη λίστα.

**Ε: Μπορώ να αποθηκεύσω μόνο τις σημειώσεις χωρίς το αρχικό περιεχόμενο;**  
Α: Απόλυτα – ορίστε `saveOptions.setAnnotationsOnly(true)` για να δημιουργήσετε αρχείο μόνο με σημειώσεις.

**Ε: Πώς διαχειρίζομαι πολύ μεγάλα έγγραφα (1000+ σελίδες);**  
Α: Χρησιμοποιήστε `setLoadOnlyAnnotatedPages(true)`, επεξεργαστείτε σε τμήματα και εξετάστε την αύξηση του heap της JVM.

**Ε: Υπάρχει τρόπος να προεπισκοπήσετε τις σελίδες πριν την αποθήκευση;**  
Α: Το GroupDocs.Annotation εστιάζει στην επεξεργασία παρά στην προβολή, αλλά μπορείτε να ανακτήσετε πληροφορίες εγγράφου (αριθμός σελίδων, θέσεις σημειώσεων) για να αποφασίσετε ποιες περιοχές θα εξάγετε.  

## Πόροι

- **Τεκμηρίωση**: [GroupDocs.Annotation for Java Docs](https://docs.groupdocs.com/annotation/java/)  
- **Αναφορά API**: [Complete API Documentation](https://reference.groupdocs.com/annotation/java/)  
- **Λήψη**: [Latest Releases](https://releases.groupdocs.com/annotation/java/)  
- **Αγορά**: [License Options](https://purchase.groupdocs.com/buy)  
- **Δωρεάν Δοκιμή**: [Try It Now](https://releases.groupdocs.com/annotation/java/)  
- **Προσωρινή Άδεια**: [Get Evaluation License](https://purchase.groupdocs.com/temporary-license/)  
- **Υποστήριξη**: [Community Forum](https://forum.groupdocs.com/c/annotation/)  

---

**Τελευταία Ενημέρωση:** 2026-01-10  
**Δοκιμασμένο Με:** GroupDocs.Annotation 25.2 (Java)  
**Συγγραφέας:** GroupDocs