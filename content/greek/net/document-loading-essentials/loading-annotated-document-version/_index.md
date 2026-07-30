---
categories:
- Document Processing
date: '2026-07-30'
description: Μάθετε πώς να ανακτάτε σχόλια από εκδόσεις εγγράφων χρησιμοποιώντας το
  GroupDocs.Annotation για .NET. Οδηγός βήμα-βήμα με αποσπάσματα κώδικα, συμβουλές
  απόδοσης και αντιμετώπιση προβλημάτων.
keywords:
- retrieve annotations from document
- GroupDocs annotation version loading
- .NET document annotation tutorial
- annotated PDF version handling
- load annotated document versions
lastmod: '2026-07-30'
linktitle: Φόρτωση Εκδοχής Ανασχολιασμένου Εγγράφου
og_description: Ανακτήστε σχόλια από εκδόσεις εγγράφων με το GroupDocs.Annotation
  για .NET. Αυτός ο οδηγός δείχνει πώς να φορτώνετε, να συγκρίνετε και να αποθηκεύετε
  συγκεκριμένες εκδόσεις σχολίων αποδοτικά.
og_image_alt: Guide to loading annotated document versions in .NET using GroupDocs.Annotation
og_title: Ανάκτηση Σχολίων από Έγγραφο – Φόρτωση Εκδόσεων σε .NET
schemas:
- author: GroupDocs
  dateModified: '2026-07-30'
  description: Learn how to retrieve annotations from document versions using GroupDocs.Annotation
    for .NET. Step-by-step guide with code snippets, performance tips, and troubleshooting.
  headline: Retrieve Annotations from Document – Load Versions in .NET
  type: TechArticle
- description: Learn how to retrieve annotations from document versions using GroupDocs.Annotation
    for .NET. Step-by-step guide with code snippets, performance tips, and troubleshooting.
  name: Retrieve Annotations from Document – Load Versions in .NET
  steps:
  - name: Define Output Path
    text: We use `Path.Combine` to build a cross‑platform file path and preserve the
      original extension with `Path.GetExtension`.
  - name: Specify Load Options
    text: 'The `LoadOptions` object configures how the document and its annotations
      are loaded, including version selection. The `Version` property selects which
      annotation set to load. Acceptable values are: - `"FIRST"` – the earliest annotation
      version. - `"LAST"` – the most recent annotation version. - Any '
  - name: Initialize Annotator
    text: The `using` statement guarantees that the `Annotator` instance is disposed,
      freeing file handles and unmanaged resources.
  - name: Retrieve Annotations
    text: '`Get()` returns the collection of annotation objects for the loaded version.
      You can iterate, modify, or export them as needed.'
  - name: Save Document with Annotations
    text: '`Save()` writes the current annotations back to a file, optionally preserving
      the original format.'
  - name: Display Confirmation Message
    text: Providing user feedback (e.g., console output, UI toast) improves the overall
      experience.
  type: HowTo
- questions:
  - answer: Yes, the library supports over 30 formats, including PDF, DOCX, PPTX,
      XLSX, and many image types.
    question: Can I annotate documents of various formats with GroupDocs.Annotation
      for .NET?
  - answer: Yes, you can download a fully‑featured trial from [here](https://releases.groupdocs.com/).
    question: Is there a free trial available for GroupDocs.Annotation for .NET?
  - answer: The complete docs are available [here](https://tutorials.groupdocs.com/annotation/net/).
    question: Where can I find official documentation for GroupDocs.Annotation for
      .NET?
  - answer: Request a temporary key from [this link](https://purchase.groupdocs.com/temporary-license/).
    question: How do I obtain a temporary license for development?
  - answer: The community forum is the best place—visit it [here](https://forum.groupdocs.com/c/annotation/10).
    question: Where can I ask technical questions or get support?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- retrieve annotations
- GroupDocs.Annotation
- .NET document processing
- annotation versioning
- C# PDF annotations
title: Ανάκτηση Σχολίων από Έγγραφο – Φόρτωση Εκδόσεων σε .NET
type: docs
---

# Ανάκτηση Σχόλια από Έγγραφο – Φόρτωση Εκδόσεων σε .NET

## Εισαγωγή

Αν χρειάζεστε **ανάκτηση σχολίων από έγγραφο** εκδόσεων γρήγορα και αξιόπιστα, βρίσκεστε στο σωστό μέρος. Είτε δημιουργείτε μια πύλη νομικής ανασκόπησης, ένα συνεργατικό σύστημα σχεδίασης, είτε έναν πίνακα ελέγχου καταγραφής ελέγχων, η διαχείριση πολλαπλών εκδόσεων σχολίων είναι βασική απαίτηση. Το GroupDocs.Annotation για .NET σας παρέχει ένα καθαρό API για τη φόρτωση οποιασδήποτε έκδοσης σχολίων—είτε είναι το πρώτο προσχέδιο, η τελευταία ανασκόπηση ή οποιοδήποτε ενδιάμεσο σημείο ελέγχου.

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία, από την εγκατάσταση της βιβλιοθήκης μέχρι την αποθήκευση ενός εγγράφου συγκεκριμένης έκδοσης, και θα προσθέσουμε πρακτικές συμβουλές ώστε να αποφύγετε τα συνηθισμένα προβλήματα.

## Γρήγορες Απαντήσεις
- **Τι σημαίνει “ανάκτηση σχολίων από έγγραφο”;** Σημαίνει τη φόρτωση μόνο των δεδομένων σχολίων που είναι συνδεδεμένα με μια συγκεκριμένη αναθεώρηση ενός αρχείου.  
- **Ποια βιβλιοθήκη υποστηρίζει αυτό;** Το GroupDocs.Annotation για .NET, το οποίο διαχειρίζεται πάνω από 30 μορφές αρχείων.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για δοκιμές· απαιτείται εμπορική άδεια για παραγωγή.  
- **Μπορώ να φορτώσω μόνο την πρώτη ή την τελευταία έκδοση;** Ναι—χρησιμοποιήστε την επιλογή `Version` με τιμές `"FIRST"` ή `"LAST"`.  
- **Είναι ασφαλές για μεγάλα PDF;** Ναι—η χρήση μνήμης παραμένει κάτω από 200 MB για PDF 500 σελίδων όταν φορτώνεται μια μόνο έκδοση.

## Πότε να Χρησιμοποιήσετε Αυτό το Χαρακτηριστικό

Πριν βυθιστείτε στον κώδικα, σκεφτείτε σενάρια όπου η φόρτωση μιας συγκεκριμένης έκδοσης σχολίων είναι απαραίτητη:

- **Ροές Εργασίας Ανασκόπησης Εγγράφων** – Συγκρίνετε τα σχόλια από διαφορετικούς κύκλους ανασκόπησης.  
- **Συμμόρφωση & Έλεγχος** – Διατηρήστε ένα αμετάβλητο αρχείο κάθε συνόλου σχολίων για τους ρυθμιστικούς φορείς.  
- **Συνεργατική Επεξεργασία** – Επιτρέψτε στους χρήστες να εναλλάσσουν μεταξύ των επιπέδων σχολίων “πρόχειρο” και “τελικό”.  
- **Σενάρια Επαναφοράς** – Επιστρέψτε σε μια γνωστή-καλή κατάσταση σχολίων εάν μια μεταγενέστερη επεξεργασία εισάγει σφάλματα.

## Προαπαιτούμενα

1. **Εγκατάσταση GroupDocs.Annotation για .NET**  
   Κατεβάστε το πακέτο από τη [σελίδα εκδόσεων](https://releases.groupdocs.com/annotation/net/). Μπορείτε επίσης να επισκεφθείτε τον κύριο ιστότοπο εκδόσεων [εδώ](https://releases.groupdocs.com/). Ακολουθήστε τον οδηγό εγκατάστασης για το IDE σας.  

   **Pro Tip**: Εάν προτιμάτε το NuGet, εκτελέστε την παρακάτω εντολή στο Package Manager Console:  
   ```
Install-Package GroupDocs.Annotation
```

2. **Αποκτήστε ένα Έγγραφο με Σχόλια**  
   Χρησιμοποιήστε PDF, DOCX ή οποιαδήποτε από τις 30+ υποστηριζόμενες μορφές που ήδη περιέχει πολλαπλές εκδόσεις σχολίων. Δημιουργήστε μερικές εκδόσεις χειροκίνητα εάν δοκιμάζετε για πρώτη φορά.

## Εισαγωγή Namespaces

Τα namespaces `GroupDocs.Annotation` σας δίνουν πρόσβαση σε βασικά αντικείμενα και επιλογές φόρτωσης.  
Η κλάση `Annotator` είναι το κύριο σημείο εισόδου για τη φόρτωση και τη διαχείριση σχολίων εγγράφου.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

*Αγκύρωση ορισμού*: `Annotator` είναι η κύρια κλάση που ανοίγει ένα αρχείο, εφαρμόζει επιλογές φόρτωσης και εκθέτει μεθόδους για την ανάκτηση ή αποθήκευση σχολίων.

## Υλοποίηση Βήμα‑προς‑Βήμα

Παρακάτω είναι η ακριβής ακολουθία που θα ακολουθήσετε για να φορτώσετε μια συγκεκριμένη έκδοση σχολίων.

### Βήμα 1: Ορισμός Διαδρομής Εξόδου
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

Χρησιμοποιούμε το `Path.Combine` για να δημιουργήσουμε μια διαδρομή αρχείου δια-πλατφόρμας και διατηρούμε την αρχική επέκταση με το `Path.GetExtension`.

### Βήμα 2: Καθορισμός Επιλογών Φόρτωσης
```csharp
LoadOptions loadOptions = new LoadOptions { Version = "FIRST" };
```

Το αντικείμενο `LoadOptions` ρυθμίζει πώς φορτώνεται το έγγραφο και τα σχόλιά του, συμπεριλαμβανομένης της επιλογής έκδοσης. Η ιδιότητα `Version` επιλέγει ποιο σύνολο σχολίων θα φορτωθεί. Αποδεκτές τιμές είναι:

- `"FIRST"` – η πιο πρώιμη έκδοση σχολίων.  
- `"LAST"` – η πιο πρόσφατη έκδοση σχολίων.  
- Οποιοσδήποτε προσαρμοσμένος αναγνωριστικό έκδοσης που έχετε αποθηκεύσει στα μεταδεδομένα του εγγράφου.

### Βήμα 3: Αρχικοποίηση Annotator
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf", loadOptions))
```

Η δήλωση `using` εγγυάται ότι η παρουσία `Annotator` αποδεσμεύεται, απελευθερώνοντας χειριστές αρχείων και μη διαχειριζόμενους πόρους.

### Βήμα 4: Ανάκτηση Σχολίων
```csharp
var annotations = annotator.Get();
```

`Get()` επιστρέφει τη συλλογή αντικειμένων σχολίων για τη φορτωμένη έκδοση. Μπορείτε να τα διατρέξετε, τροποποιήσετε ή εξάγετε όπως χρειάζεται.

### Βήμα 5: Αποθήκευση Εγγράφου με Σχόλια
```csharp
annotator.Save(outputPath);
```

`Save()` γράφει τα τρέχοντα σχόλια πίσω σε ένα αρχείο, διατηρώντας προαιρετικά την αρχική μορφή.

### Βήμα 6: Εμφάνιση Μηνύματος Επιβεβαίωσης
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

Η παροχή ανατροφοδότησης στον χρήστη (π.χ., έξοδος κονσόλας, UI toast) βελτιώνει τη συνολική εμπειρία.

## Πώς να φορτώσω μια συγκεκριμένη έκδοση σχολίων;

Φορτώστε ένα έγγραφο με `new Annotator(filePath, loadOptions)` όπου το `loadOptions.Version` έχει οριστεί στον επιθυμητό αναγνωριστικό, στη συνέχεια καλέστε `annotator.Get()` για να λάβετε τα σχόλια αυτής της έκδοσης. Αυτή η προσέγγιση μίας γραμμής απομονώνει την έκδοση που χρειάζεστε χωρίς να επηρεάσει άλλες αναθεωρήσεις. Μπορείτε επίσης να καθορίσετε την έκδοση χρησιμοποιώντας σταθερές όπως `Version.First` ή `Version.Last` για ευκολία, εξασφαλίζοντας ότι θα λάβετε ακριβώς το επιθυμητό σύνολο σχολίων.

## Τι είναι η κλάση Annotator;

`Annotator` είναι η κλάση πύλης του GroupDocs.Annotation που ανοίγει ένα αρχείο, εφαρμόζει `LoadOptions` και εκθέτει μεθόδους όπως `Get()`, `Save()` και `GetVersionsList()`. Όλες οι λειτουργίες σχολίων διέρχονται μέσω αυτού του αντικειμένου. Διαχειρίζεται τον κύκλο ζωής του εγγράφου, χειρίζεται τον καθαρισμό πόρων και παρέχει ασφαλή πρόσβαση σε δεδομένα σχολίων, καθιστώντας το κατάλληλο για εφαρμογές επιφάνειας εργασίας και web.

## Συνηθισμένα Προβλήματα και Επίλυση

### Σφάλμα Μη Βρέθηκε Έκδοση
**Πρόβλημα**: Εξαίρεση όταν ο ζητούμενος αναγνωριστικός αριθμός έκδοσης δεν υπάρχει.  
**Λύση**: Καλέστε πρώτα `annotator.GetVersionsList()` για να εμφανίσετε τις διαθέσιμες εκδόσεις, στη συνέχεια επιλέξτε έναν έγκυρο αναγνωριστικό.

### Κενή Συλλογή Σχολίων
**Πρόβλημα**: Το `Get()` επιστρέφει μια κενή λίστα.  
**Λύση**: Επαληθεύστε ότι η επιλεγμένη έκδοση περιέχει πράγματι σχόλια και ότι το αρχείο προέλευσης δεν έχει αφαιρεθεί από τα μεταδεδομένα σχολίων κατά την προηγούμενη αποθήκευση.

### Προβλήματα Απόδοσης με Μεγάλα Έγγραφα
**Πρόβλημα**: Η φόρτωση διαρκεί αρκετά δευτερόλεπτα για PDF 500 σελίδων με χιλιάδες σχόλια.  
**Λύση**:  
- Φιλτράρετε κατά τύπο σχολίου (`LoadOptions.AnnotationTypes`).  
- Εφαρμόστε σελιδοποίηση χρησιμοποιώντας `annotator.Get(pageIndex, pageSize)`.  
- Κρατήστε στην μνήμη τις συχνά προσπελάσιμες εκδόσεις εάν η ροή εργασίας σας το επιτρέπει.

### Προβλήματα Διαδρομής Αρχείου
**Πρόβλημα**: Σφάλματα “File not found” ή πρόσβασης-απαγορεύεται.  
**Λύση**:  
- Χρησιμοποιήστε απόλυτες διαδρομές κατά την ανάπτυξη.  
- Βεβαιωθείτε ότι ο λογαριασμός υπηρεσίας της εφαρμογής έχει δικαιώματα ανάγνωσης/εγγραφής σε φακέλους προέλευσης και προορισμού.  
- Δημιουργήστε τον φάκελο εξόδου εκ των προτέρων εάν μπορεί να μην υπάρχει.

## Σκέψεις Απόδοσης

- **Αποτύπωμα Μνήμης**: Η φόρτωση μιας μόνο έκδοσης διατηρεί τη χρήση μνήμης κάτω από 200 MB για τυπικά PDF 500 σελίδων.  
- **Βελτιστοποίηση I/O**: Επεξεργαστείτε σε παρτίδες έγγραφα με κοινό pool `Annotator` για να μειώσετε το κόστος ανοίγματος αρχείων.  
- **Καθυστέρηση Δικτύου**: Όταν τα αρχεία βρίσκονται σε αποθήκευση cloud, τυλίξτε τις κλήσεις σε λογική επανάληψης και σκεφτείτε τη ροή του αρχείου σε τοπικό φάκελο προσωρινής αποθήκευσης πριν τη φόρτωση.

## Καλές Πρακτικές

### Συμφωνίες Ονοματοδοσίας Εκδόσεων
Υιοθετήστε ένα σαφές σύστημα ονοματοδοσίας όπως `v1.0`, `v1.1-review` ή σήματα ημερομηνίας ISO (`2025-01-02`) ώστε η επιλογή έκδοσης να είναι διαισθητική για τους τελικούς χρήστες.

### Διαχείριση Σφαλμάτων
Τυλίξτε όλο τον κώδικα σχολίων σε μπλοκ try‑catch και καταγράψτε λεπτομερείς πληροφορίες σφάλματος.

```csharp
try 
{
    using (Annotator annotator = new Annotator(documentPath, loadOptions))
    {
        var annotations = annotator.Get();
        // Process annotations
    }
}
catch (Exception ex)
{
    // Log error and provide user-friendly message
    Console.WriteLine($"Error loading annotations: {ex.Message}");
}
```

### Διαχείριση Πόρων
Επειδή το `Annotator` υλοποιεί το `IDisposable`, χρησιμοποιείτε πάντα μια δήλωση `using` ή καλέστε ρητά το `Dispose()` για να ελευθερώσετε άμεσα τους χειριστές αρχείων.

## Ενσωμάτωση με Υφιστάμενες Ροές Εργασίας

- **Συστήματα Διαχείρισης Εγγράφων** – Εκθέστε ένα API endpoint που δέχεται ένα αναγνωριστικό έκδοσης και επιστρέφει το αντίστοιχο αρχείο με σχόλια.  
- **Υπηρεσίες RESTful** – Επιστρέψτε τη συλλογή σχολίων ως JSON για απόδοση στο front‑end.  
- **Εργασίες Υπόβαθρου** – Προγραμματίστε νυχτερινές εργασίες που εξάγουν τα σχόλια κάθε έκδοσης για αναφορές συμμόρφωσης.  
- **Διεπαφές Χρήστη** – Συμπληρώστε ένα dropdown με `annotator.GetVersionsList()` ώστε οι χρήστες να επιλέγουν την έκδοση που θέλουν να δουν.

## Συμπέρασμα

Τώρα έχετε ένα πλήρες, έτοιμο για παραγωγή πρότυπο για **ανάκτηση σχολίων από εκδόσεις εγγράφου** χρησιμοποιώντας το GroupDocs.Annotation για .NET. Θυμηθείτε:

1. Ορίστε τη σωστή `Version` στα `LoadOptions`.  
2. Αποδεσμεύστε σωστά το `Annotator`.  
3. Διαχειριστείτε μεγάλα αρχεία με φιλτράρισμα ή σελιδοποίηση.  

Με αυτά τα βήματα, μπορείτε να δημιουργήσετε ισχυρά χαρακτηριστικά σχολίων με γνώση έκδοσης που ενδυναμώνουν τη συνεργασία, την δυνατότητα ελέγχου και την απρόσκοπτη επαναφορά.

---

**Τελευταία Ενημέρωση:** 2026-07-30  
**Δοκιμάστηκε Με:** GroupDocs.Annotation 2.3.0 for .NET  
**Συγγραφέας:** GroupDocs  

## Συχνές Ερωτήσεις

**Q: Μπορώ να σχολιάσω έγγραφα διαφόρων μορφών με το GroupDocs.Annotation για .NET;**  
A: Ναι, η βιβλιοθήκη υποστηρίζει πάνω από 30 μορφές, συμπεριλαμβανομένων PDF, DOCX, PPTX, XLSX και πολλών τύπων εικόνων.

**Q: Υπάρχει δωρεάν δοκιμή διαθέσιμη για το GroupDocs.Annotation για .NET;**  
A: Ναι, μπορείτε να κατεβάσετε μια πλήρως εξοπλισμένη δοκιμή από [εδώ](https://releases.groupdocs.com/).

**Q: Πού μπορώ να βρω την επίσημη τεκμηρίωση για το GroupDocs.Annotation για .NET;**  
A: Η πλήρης τεκμηρίωση είναι διαθέσιμη [εδώ](https://tutorials.groupdocs.com/annotation/net/).

**Q: Πώς μπορώ να αποκτήσω προσωρινή άδεια για ανάπτυξη;**  
A: Ζητήστε ένα προσωρινό κλειδί από [αυτόν τον σύνδεσμο](https://purchase.groupdocs.com/temporary-license/).

**Q: Πού μπορώ να θέσω τεχνικές ερωτήσεις ή να λάβω υποστήριξη;**  
A: Το φόρουμ κοινότητας είναι το καλύτερο μέρος—επισκεφθείτε το [εδώ](https://forum.groupdocs.com/c/annotation/10).

**Q: Πώς μπορώ να εμφανίσω όλες τις εκδόσεις σχολίων σε ένα έγγραφο;**  
A: Χρησιμοποιήστε `annotator.GetVersionsList()`· επιστρέφει κάθε αναγνωριστικό έκδοσης που είναι αποθηκευμένο στο αρχείο.

**Q: Η φόρτωση μιας συγκεκριμένης έκδοσης επηρεάζει άλλες εκδόσεις;**  
A: Όχι—η φόρτωση είναι μόνο για ανάγνωση. Οι άλλες εκδόσεις παραμένουν αμετάβλητες εκτός εάν τις τροποποιήσετε και τις αποθηκεύσετε ρητά.

## Σχετικές Εκπαιδεύσεις

- [GroupDocs.Annotation .NET Λήψη Σχολίων - Οδηγός Πλήρους Κλειδιού Έκδοσης](/annotation/net/advanced-usage/get-list-annotations-version-key/)
- [Διαχείριση Έκδοσης Εγγράφου .NET - Πλήρης Οδηγός GroupDocs.Annotation](/annotation/net/version-control/load-specific-versions-groupdocs-annotation-net/)
- [Διαχείριση Έκδοσης Εγγράφου .NET - Πλήρης Οδηγός Παρακολούθησης Εκδόσεων Εγγράφου](/annotation/net/advanced-usage/get-all-version-keys-document/)