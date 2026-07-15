---
categories:
- PDF Processing
date: '2026-05-26'
description: Μάθετε πώς να δημιουργήσετε σύστημα ανασκόπησης εγγράφων χρησιμοποιώντας
  το GroupDocs Annotation for .NET. Ένας βήμα‑βήμα οδηγός καλύπτει τη ρύθμιση, τους
  τύπους σχολιασμού, τη βελτιστοποίηση απόδοσης και την αντιμετώπιση προβλημάτων για
  προγραμματιστές C#.
keywords:
- create document review system
- PDF annotation .NET
- GroupDocs annotation tutorial
lastmod: '2026-05-26'
linktitle: Οδηγός PDF Annotation .NET
schemas:
- author: GroupDocs
  dateModified: '2026-05-26'
  description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  headline: 'Create Document Review System: PDF Annotation .NET Guide'
  type: TechArticle
- description: Learn how to create document review system using GroupDocs Annotation
    for .NET. Step‑by‑step tutorial covers setup, annotation types, performance tuning,
    and troubleshooting for C# developers.
  name: 'Create Document Review System: PDF Annotation .NET Guide'
  steps:
  - name: Create an AreaAnnotation
    text: '`AreaAnnotation` represents a rectangular highlight area on a PDF page.'
  - name: Create an EllipseAnnotation
    text: '`EllipseAnnotation` represents an elliptical shape annotation on a PDF
      page.'
  - name: Add Annotations in Bulk
    text: '**Pro Tip:** Adding annotations in a list and calling `Add` once reduces
      I/O overhead, especially when you need to insert dozens of marks across many
      pages.'
  type: HowTo
- questions:
  - answer: GroupDocs automatically reads each page’s dimensions. When positioning
      annotations, always query `annotator.GetPageInfo(pageNumber)` and calculate
      coordinates based on that page’s width and height.
    question: How do I handle PDFs with different page sizes?
  - answer: Yes. Use the `LoadOptions` constructor that accepts a password string,
      e.g., `new LoadOptions { Password = "secret" }`, and pass it to the `Annotator`
      constructor.
    question: Can I annotate password‑protected PDFs?
  - answer: There is no hard limit, but performance degrades after a few thousand
      annotations. For very large annotation sets, group them into logical sections
      and process each section separately.
    question: What is the maximum number of annotations I can add to a single PDF?
  - answer: Retrieve the annotation’s `Id` via `GetAnnotations()`, then call `Delete(id)`
      or create a `SaveOptions` instance that excludes the unwanted `AnnotationType`.
    question: How do I remove specific annotations programmatically?
  - answer: Absolutely. You can set opacity, border thickness, dash style, and even
      embed custom SVG icons for stamp annotations.
    question: Can I customize annotation appearance beyond colors?
  type: FAQPage
tags:
- pdf-annotation
- groupdocs
- dotnet
- csharp
- document-processing
title: 'Δημιουργία Συστήματος Ανασκόπησης Εγγράφων: PDF Annotation .NET Οδηγός'
type: docs
url: /el/net/annotation-management/annotate-pdfs-groupdocs-annotation-net/
weight: 1
---

# Δημιουργία Συστήματος Ανασκόπησης Εγγράφων: Οδηγός PDF Σχόλιου .NET

Αν χρειάζεστε **σύστημα ανασκόπησης εγγράφων** που επιτρέπει στους χρήστες να προσθέτουν σχόλια, επισημάνσεις και σχήματα σε PDF απευθείας από μια εφαρμογή .NET, βρίσκεστε στο σωστό μέρος. Το GroupDocs.Annotation για .NET αφαιρεί τον κόπο της χαμηλού επιπέδου διαχείρισης PDF ενώ σας δίνει λεπτομερή έλεγχο σε κάθε τύπο σημείωσης. Σε αυτόν τον οδηγό θα δείτε πώς να ρυθμίσετε τη βιβλιοθήκη, να προσθέσετε σημειώσεις περιοχής, έλλειψης και κειμένου, να φιλτράρετε τι αποθηκεύεται και να διατηρήσετε την απόδοση γρήγορη ακόμη και με αρχεία πολλών εκατοντάδων σελίδων.

## Γρήγορες Απαντήσεις
- **Ποια βιβλιοθήκη διαχειρίζεται τις σημειώσεις PDF σε .NET;** GroupDocs.Annotation για .NET.  
- **Μπορώ να προσθέσω επισημάνσεις, κύκλους και σχόλια προγραμματιστικά;** Ναι – χρησιμοποιήστε τα αντικείμενα AreaAnnotation, EllipseAnnotation και TextAnnotation.  
- **Απαιτείται άδεια για παραγωγή;** Μια έγκυρη άδεια GroupDocs είναι υποχρεωτική για οποιαδήποτε παραγωγική ανάπτυξη.  
- **Πόσο μεγάλο PDF μπορεί να επεξεργαστεί;** Έως 500 MB μπορεί να διαχειριστεί χωρίς να φορτωθεί ολόκληρο το αρχείο στη μνήμη.  
- **Θα με βοηθήσει αυτό να δημιουργήσω σύστημα ανασκόπησης εγγράφων;** Απόλυτα – μπορείτε να αποθηκεύετε μαζικά, να φιλτράρετε και να εκδοθείτε εκδόσεις σημειώσεων για τους αξιολογητές.

## Τι είναι ένα σύστημα ανασκόπησης εγγράφων;
Ένα **σύστημα ανασκόπησης εγγράφων** είναι μια λογισμική λύση που επιτρέπει σε πολλούς ενδιαφερόμενους να σημειώνουν, να σχολιάζουν και να εγκρίνουν αρχεία PDF σε συντονισμένη ροή εργασίας. Κεντρικοποιεί τα σχόλια, παρακολουθεί τις αλλαγές και συχνά εξάγει μια καθαρή έκδοση για τελική έγκριση.

## Γιατί να χρησιμοποιήσετε το GroupDocs Annotation για .NET για τη δημιουργία ενός συστήματος ανασκόπησης εγγράφων;
Το GroupDocs Annotation υποστηρίζει **30+ τύπους σημειώσεων**, επεξεργάζεται PDF έως **500 MB** σε μέγεθος και λειτουργεί σε **.NET Framework 4.6.1+**, **.NET Core 2.0+** και **.NET 6+**. Το API του σας επιτρέπει να προσθέτετε, να αφαιρείτε και να φιλτράρετε σημειώσεις χωρίς να αγγίζετε τη δομή του PDF, κάτι που επιταχύνει την ανάπτυξη και μειώνει τα σφάλματα.

## Προαπαιτούμενα και Ρύθμιση Περιβάλλοντος

Πριν γράψετε κώδικα, βεβαιωθείτε ότι το περιβάλλον ανάπτυξής σας πληροί τα παρακάτω κριτήρια:

- **IDE:** Visual Studio 2019 ή νεότερο, ή VS Code με την επέκταση C#.  
- **Στόχος Πλαισίου:** .NET Framework 4.6.1 + ή .NET Core 2.0 + (συνιστούμε .NET 6 για νέα έργα).  
- **Πρόσβαση NuGet:** Δυνατότητα εγκατάστασης πακέτων από nuget.org.  
- **Δείγματα PDF:** Τουλάχιστον ένα πολυσελίδα PDF για δοκιμή τοποθέτησης σημειώσεων.  
- **Μνήμη & Δίσκος:** Ελάχιστη μνήμη 4 GB RAM και επαρκής ελεύθερος χώρος δίσκου για προσωρινά αρχεία (η επεξεργασία σημειώσεων μπορεί να δημιουργήσει προσωρινές ροές).

### Συνιστώμενες Πρακτικές Ανάπτυξης
- Κρατήστε το έργο σας υπό έλεγχο πηγαίου κώδικα (Git) ώστε να μπορείτε να επαναφέρετε αλλαγές σχετικές με σημειώσεις.  
- Χρησιμοποιήστε έναν αφιερωμένο φάκελο **Annotations** στο έργο σας για αποθήκευση αρχείων ρυθμίσεων και κλειδιών άδειας.  
- Ενεργοποιήστε **nullable reference types** (`<Nullable>enable</Nullable>`) για να εντοπίζετε πιθανά σφάλματα null‑reference νωρίς.

## Έναρξη: Εγκατάσταση GroupDocs.Annotation

### Μέθοδοι Εγκατάστασης

**Επιλογή 1: NuGet Package Manager Console**  
Εκτελέστε την παρακάτω εντολή στο Package Manager Console:  

`Install-Package GroupDocs.Annotation`

**Επιλογή 2: .NET CLI (συνιστάται για ανάπτυξη πολλαπλών πλατφορμών)**  
Εκτελέστε σε τερματικό:  

`dotnet add package GroupDocs.Annotation`

**Επιλογή 3: Visual Studio Package Manager UI**  
- Κάντε δεξί‑κλικ στο έργο → **Manage NuGet Packages**  
- Αναζητήστε **GroupDocs.Annotation**  
- Κάντε κλικ **Install** στην πιο πρόσφατη σταθερή έκδοση  

Οι τρεις μέθοδοι εγκαθιστούν το ίδιο δυαδικό αρχείο· επιλέξτε αυτή που ταιριάζει στη ροή εργασίας σας.

### Ρύθμιση Άδειας

Το GroupDocs απαιτεί έγκυρη άδεια για οποιαδήποτε παραγωγική χρήση. Έχετε τρεις επιλογές:

- **Δωρεάν Δοκιμή:** 30‑ήμερη αξιολόγηση με πλήρες σύνολο λειτουργιών.  
- **Προσωρινή Άδεια:** Εκτεταμένη αξιολόγηση για ανάπτυξη και δοκιμές.  
- **Εμπορική Άδεια:** Απεριόριστη χρήση σε παραγωγικά περιβάλλοντα.

Η κλάση `License` φορτώνει και εφαρμόζει ένα αρχείο άδειας GroupDocs για πλήρη λειτουργικότητα. Μπορείτε να αποκτήσετε άδεια από τη [σελίδα αγοράς του GroupDocs](https://purchase.groupdocs.com/buy). Μετά τη λήψη του αρχείου `.lic`, τοποθετήστε το σε φάκελο που η εφαρμογή σας μπορεί να διαβάσει και δείξτε στην κλάση `License` τη διαδρομή του κατά την εκκίνηση.

### Επαλήθευση Αρχικής Ρύθμισης

Δημιουργήστε ένα μικρό πρόγραμμα κονσόλας που φορτώνει ένα PDF και γράφει τον αριθμό σελίδων στην κονσόλα. Αν το πρόγραμμα εκτελεστεί χωρίς εξαίρεση, η βιβλιοθήκη είναι σωστά εγκατεστημένη και αδειοδοτημένη.

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;

var annotator = new Annotator("sample.pdf");
var info = annotator.GetDocumentInfo();
Console.WriteLine($"Pages: {info.PageCount}");
```

> **Σημείωση:** Ο παραπάνω κώδικας είναι μόνο για illustration· δεν χρειάζεται να προσθέσετε fenced code block στο τελικό άρθρο, αλλά το ενσωματωμένο snippet δείχνει τη σωστή χρήση του API.

Αν δείτε τον αριθμό σελίδων εκτυπωμένο, είστε έτοιμοι να ξεκινήσετε την προσθήκη πραγματικών σημειώσεων.

## Κύρια Υλοποίηση: Προσθήκη Σημειώσεων σε PDF

### Ορισμός Άγκυρας – Annotator
Η κλάση `Annotator` είναι το σημείο εισόδου για όλες τις λειτουργίες σημειώσεων PDF στο GroupDocs.Annotation για .NET. Φορτώνει ένα PDF στη μνήμη, εκθέτει μεθόδους για προσθήκη, επεξεργασία και ανάκτηση σημειώσεων, και διαχειρίζεται την αποθήκευση του τροποποιημένου εγγράφου.

### Πώς να προσθέσετε σημειώσεις περιοχής και έλλειψης;
Φορτώστε το PDF με `new Annotator(...)`, δημιουργήστε αντικείμενα `AreaAnnotation` και `EllipseAnnotation`, ορίστε τις συντεταγμένες τους και προσθέστε τα στη συλλογή του annotator. Τέλος, καλέστε `Save` για να αποθηκεύσετε τις αλλαγές. Αυτή η ροή εργασίας σας επιτρέπει να επισημαίνετε τμήματα (area) ή να περιβάλλετε σημαντικά γραφικά με έναν ενιαίο, ατομικό βήμα.

#### Βήμα 1: Αρχικοποίηση του Annotator
```csharp
var annotator = new Annotator("input.pdf");
```

#### Βήμα 2: Δημιουργία AreaAnnotation
`AreaAnnotation` αντιπροσωπεύει μια ορθογώνια περιοχή επισημάνσεως σε μια σελίδα PDF.  
```csharp
var area = new AreaAnnotation
{
    PageNumber = 0,
    Box = new RectangleF(100, 150, 200, 50),
    Color = Color.Yellow,
    Opacity = 0.4f,
    Text = "Review this paragraph"
};
```

#### Βήμα 3: Δημιουργία EllipseAnnotation
`EllipseAnnotation` αντιπροσωπεύει μια ελλειπτική σχήμα σημείωσης σε μια σελίδα PDF.  
```csharp
var ellipse = new EllipseAnnotation
{
    PageNumber = 2,
    Box = new RectangleF(300, 400, 120, 80),
    Color = Color.Red,
    Opacity = 0.6f,
    Text = "Check this figure"
};
```

#### Βήμα 4: Προσθήκη Σημειώσεων Μαζικά
```csharp
annotator.Add(new List<AnnotationBase> { area, ellipse });
annotator.Save("output.pdf");
```

**Pro Tip:** Η προσθήκη σημειώσεων σε λίστα και η κλήση `Add` μία φορά μειώνει το I/O overhead, ειδικά όταν χρειάζεται να εισάγετε δεκάδες σημεία σε πολλές σελίδες.

### Πώς να αποθηκεύσετε επιλεκτικές σημειώσεις;
Το `SaveOptions` διαμορφώνει τον τρόπο αποθήκευσης του σημειωμένου PDF, συμπεριλαμβανομένων των τύπων σημειώσεων που θα συμπεριληφθούν. Το GroupDocs.Annotation σας επιτρέπει να φιλτράρετε ποιοι τύποι σημειώσεων γράφονται στο αρχείο εξόδου. Δημιουργήστε μια παρουσία `SaveOptions`, ορίστε τη συλλογή `AnnotationTypes` στους τύπους που θέλετε να διατηρήσετε και περάστε τις επιλογές στο `Save`. Αυτό είναι ιδανικό για δημιουργία PDF μόνο για αξιολογητές ή αφαίρεση προσωρινών σημειώσεων πριν την αρχειοθέτηση.

```csharp
var saveOptions = new SaveOptions
{
    AnnotationTypes = new[] { AnnotationType.Text, AnnotationType.Area }
};
annotator.Save("filtered.pdf", saveOptions);
```

## Σενάρια Υλοποίησης στον Πραγματικό Κόσμο

### Σενάριο 1: Ροή Εργασίας Ανασκόπησης Εγγράφων
Πολλοί αξιολογητές προσθέτουν **Area**, **Ellipse** και **Text** σημειώσεις. Μετά τον κύκλο ανασκόπησης, δημιουργείτε τρία PDF:
1. Πλήρης έκδοση με όλα τα σχόλια.  
2. Έκδοση μόνο για αξιολογητές (φιλτράρει εσωτερικές σημειώσεις).  
3. Καθαρή έκδοση για τελική έγκριση (διατηρεί μόνο επισημάνσεις).

### Σενάριο 2: Αυτόματη Δημιουργία Αναφορών
Το backend σας επεξεργάζεται καθημερινές αναφορές πωλήσεων, επισημαίνοντας αυτόματα βασικά μετρικά με area annotations και περιβάλλοντας εκτός ορίων γραφήματα με ellipse annotations. Τα παραγόμενα PDF αποστέλλονται μέσω email σε ενδιαφερόμενους χωρίς ανθρώπινη παρέμβαση.

### Σενάριο 3: Συνεργατικά Νομικά Έγγραφα
Τα νομικά γραφεία συχνά χρειάζονται διαχωρισμό σχολίων συνεργατών από σημειώσεις νεότερων συνεργατών. Με την επισήμανση σημειώσεων με προσαρμοσμένα μεταδεδομένα και τη χρήση επιλεκτικής αποθήκευσης, μπορείτε να παράγετε PDF για συνεργάτες που κρύβει τις σημειώσεις των νεότερων, απλοποιώντας τον έλεγχο εκδόσεων.

## Βελτιστοποίηση Απόδοσης για Παραγωγική Χρήση

### Πώς να διαχειριστείτε τη μνήμη όταν σημειώνετε μεγάλα PDF;
Το `LoadOptions` σας επιτρέπει να καθορίσετε πώς φορτώνεται ένα PDF, όπως εύρος σελίδων ή κωδικούς πρόσβασης. Όταν ένα PDF υπερβαίνει τα 100 MB, αποφύγετε τη φόρτωση ολόκληρου του αρχείου χρησιμοποιώντας τον κατασκευαστή `LoadOptions` που δέχεται εύρος σελίδων. Επεξεργαστείτε τις σελίδες σε παρτίδες, απελευθερώστε κάθε παρουσία `Annotator` με ένα `using` block και καθαρίστε τα προσωρινά αρχεία μετά από κάθε παρτίδα. Αυτή η προσέγγιση διατηρεί τη μέγιστη χρήση μνήμης κάτω από 200 MB ακόμη και για έγγραφα 500 σελίδων.

```csharp
using (var annotator = new Annotator("large.pdf", new LoadOptions { PageNumbers = new[] { 0, 1, 2 } }))
{
    // annotate first three pages
}
```

### Καλές Πρακτικές Διαχείρισης Μνήμης
- **Πάντα τυλίξτε το `Annotator` σε δήλωση `using`** για να εγγυηθείτε την απελευθέρωση μη διαχειριζόμενων πόρων.  
- **Μαζική επεξεργασία σημειώσεων:** συλλέξτε όλες τις σημειώσεις για ένα έγγραφο, στη συνέχεια καλέστε `Add` μία φορά.  
- **Αποφύγετε τη φόρτωση ολόκληρων PDF:** όταν χρειάζεται να τροποποιήσετε μόνο ένα υποσύνολο σελίδων, χρησιμοποιήστε `LoadOptions.PageNumbers`.

### Στρατηγικές Διαχείρισης Μεγάλων Αρχείων
1. **Επεξεργασία ανά σελίδα** – Φορτώστε, σημειώστε και αποθηκεύστε μία σελίδα τη φορά.  
2. **Ροή εξόδου streaming** – Κατευθύνετε τη μέθοδο `Save` σε `MemoryStream` για να αποφύγετε ενδιάμεσες εγγραφές στο δίσκο.  
3. **Καθαρισμός προσωρινών αρχείων** – Διαγράψτε τυχόν προσωρινά αρχεία που δημιουργεί ο annotator μετά από κάθε λειτουργία.

### Σκέψεις για Συγχρονική Επεξεργασία
- **Ασφάλεια νήματος:** Οι παρουσίες `Annotator` δεν είναι thread‑safe. Δημιουργήστε ξεχωριστή παρουσία ανά νήμα.  
- **Περιορισμός πόρων:** Περιορίστε τις ταυτόχρονες εργασίες στον αριθμό των πυρήνων CPU για να αποτρέψετε την υπερφόρτωση.  
- **Async API:** Η `SaveAsync` αποθηκεύει το σημειωμένο έγγραφο ασύγχρονα, επιστρέφοντας ένα Task, χρήσιμο σε περιβάλλοντα ASP.NET Core.

## Επίλυση Συνηθισμένων Προβλημάτων

### Πρόβλημα 1: Σφάλματα “File Not Found”
**Άμεση απάντηση:** Επαληθεύστε ότι η διαδρομή αρχείου που περνάτε στο `new Annotator(...)` είναι απόλυτη ή σωστά σχετική με το εκτελούμενο assembly, και βεβαιωθείτε ότι η διεργασία της εφαρμογής έχει δικαιώματα ανάγνωσης για αυτήν τη θέση. Αν το αρχείο βρίσκεται σε δικτυακό κοινόχρηστο φάκελο, χαρτογραφήστε το ή χρησιμοποιήστε UNC διαδρομές.

**Τυπικές διορθώσεις:**  
- Χρησιμοποιήστε `Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "Docs", "sample.pdf")`.  
- Παραχωρήστε στην ταυτότητα του application pool του IIS δικαιώματα ανάγνωσης/εγγραφής στο φάκελο.

### Πρόβλημα 2: Οι σημειώσεις εμφανίζονται σε λανθασμένες θέσεις
**Άμεση απάντηση:** Βεβαιωθείτε ότι χρησιμοποιείτε το ίδιο σύστημα συντεταγμένων (αρχή πάνω‑αριστερά) και ότι το DPI της σελίδας ταιριάζει με τις τιμές που παρέχετε. Ανακτήστε το μέγεθος σελίδας μέσω `annotator.GetPageInfo(pageNumber)` και υπολογίστε τις συντεταγμένες σχετικά με αυτό το μέγεθος.

**Τυπικές διορθώσεις:**  
- Πολλαπλασιάστε τις συντεταγμένες με τον συντελεστή κλίμακας της σελίδας αν το PDF δημιουργήθηκε με μη‑τυπικό DPI.  
- Ελέγξτε ότι δεν αναμειγνύετε μονάδες σημείων (1/72 ίντσας) με pixels.

### Πρόβλημα 3: Προβλήματα απόδοσης με μεγάλα αρχεία
**Άμεση απάντηση:** Μεταβείτε σε φόρτωση εύρους σελίδων, επεξεργαστείτε σημειώσεις σε παρτίδες και απελευθερώστε άμεσα κάθε παρουσία `Annotator`. Ενεργοποιήστε επίσης την επιλογή `MemoryCache` στο `LoadOptions` για επαναχρησιμοποίηση buffers μεταξύ λειτουργιών.

**Τυπικές διορθώσεις:**  
- Ορίστε `LoadOptions.UseMemoryCache = true`.  
- Επεξεργαστείτε αρχεία ασύγχρονα με `await annotator.SaveAsync(...)`.

### Πρόβλημα 4: Σφάλματα σχετιζόμενα με την άδεια
**Άμεση απάντηση:** Τοποθετήστε το αρχείο `.lic` σε φάκελο που η εφαρμογή μπορεί να διαβάσει και καλέστε `License license = new License(); license.SetLicense("path/to/license.lic");` πριν από οποιαδήποτε κλήση GroupDocs. Επαληθεύστε ότι η έκδοση της άδειας ταιριάζει με την έκδοση της βιβλιοθήκης που χρησιμοποιείτε.

**Τυπικές διορθώσεις:**  
- Ελέγξτε ότι το αρχείο άδειας δεν είναι κατεστραμμένο (συγκρίνετε το μέγεθος αρχείου).  
- Βεβαιωθείτε ότι δεν αναμειγνύετε δοκιμαστική άδεια με εμπορική στο ίδιο περιβάλλον.

## Προχωρημένες Συμβουλές και Καλές Πρακτικές

### Διαχείριση Χρωμάτων
Συνεπή χρώματα βελτιώνουν την αναγνωσιμότητα για τους αξιολογητές. Ορίστε μια παλέτα (π.χ., Κίτρινο για επισημάνσεις, Κόκκινο για κρίσιμα ζητήματα) και αποθηκεύστε την σε στατική βοηθητική κλάση. Χρησιμοποιήστε χρώματα υψηλής αντίθεσης για προσβασιμότητα και προσθέστε μια σελίδα υπομνήματος στο PDF για αναφορά.

### Μοτίβα Διαχείρισης Σφαλμάτων
Τυλίξτε όλες τις κλήσεις σημειώσεων σε μπλοκ try‑catch που παγιδεύουν ειδικά `GroupDocs.Annotation.Exceptions.AnnotationException`. Καταγράψτε το μήνυμα εξαίρεσης, το stack trace και το όνομα του PDF για να διευκολύνετε τον εντοπισμό σφαλμάτων.

### Στρατηγικές Δοκιμών
- **Μονάδες Δοκιμών:** Χρησιμοποιήστε ένα μικρό PDF με γνωστές διαστάσεις, προσθέστε μια σημείωση και ελέγξτε ότι το `GetAnnotations()` επιστρέφει τις αναμενόμενες συντεταγμένες.  
- **Δοκιμές Ενσωμάτωσης:** Εκτελέστε την πλήρη ροή εργασίας σε PDF από 1 σελίδα έως 200 σελίδες και βεβαιωθείτε ότι ο χρόνος επεξεργασίας παραμένει κάτω από 5 δευτερόλεπτα για αρχεία κάτω από 50 MB.  
- **Δοκιμές Φόρτου:** Προσομοιώστε 50 ταυτόχρονες αιτήσεις σημειώσεων χρησιμοποιώντας εργαλείο όπως k6 ή Apache JMeter και παρακολουθήστε CPU/μνήμη.

## Συχνές Ερωτήσεις

**Ε: Πώς διαχειρίζομαι PDF με διαφορετικά μεγέθη σελίδας;**  
Α: Το GroupDocs διαβάζει αυτόματα τις διαστάσεις κάθε σελίδας. Κατά την τοποθέτηση σημειώσεων, πάντα ερωτήστε `annotator.GetPageInfo(pageNumber)` και υπολογίστε τις συντεταγμένες βάσει του πλάτους και του ύψους της συγκεκριμένης σελίδας.

**Ε: Μπορώ να σημειώσω PDF προστατευμένα με κωδικό;**  
Α: Ναι. Χρησιμοποιήστε τον κατασκευαστή `LoadOptions` που δέχεται κωδικό πρόσβασης, π.χ., `new LoadOptions { Password = "secret" }`, και περάστε το στον κατασκευαστή `Annotator`.

**Ε: Ποιος είναι ο μέγιστος αριθμός σημειώσεων που μπορώ να προσθέσω σε ένα PDF;**  
Α: Δεν υπάρχει σκληρό όριο, αλλά η απόδοση μειώνεται μετά από μερικές χιλιάδες σημειώσεις. Για πολύ μεγάλα σύνολα, ομαδοποιήστε τις σε λογικές ενότητες και επεξεργαστείτε κάθε ενότητα ξεχωριστά.

**Ε: Πώς να αφαιρέσω συγκεκριμένες σημειώσεις προγραμματιστικά;**  
Α: Ανακτήστε το `Id` της σημείωσης μέσω `GetAnnotations()`, στη συνέχεια καλέστε `Delete(id)` ή δημιουργήστε μια `SaveOptions` που εξαιρεί τον ανεπιθύμητο `AnnotationType`.

**Ε: Μπορώ να προσαρμόσω την εμφάνιση των σημειώσεων πέρα από τα χρώματα;**  
Α: Απόλυτα. Μπορείτε να ορίσετε διαφάνεια, πάχος περιγράμματος, στυλ διακεκομμένων γραμμών και ακόμη να ενσωματώσετε προσαρμοσμένα SVG εικονίδια για σημειώσεις τύπου stamp.

**Ε: Τι συμβαίνει αν προσπαθήσω να σημειώσω ένα σκαναρισμένο (εικονο‑βάση) PDF;**  
Α: Οι σημειώσεις θα αποδοθούν ως αντικείμενα επικάλυψης πάνω στην εικόνα της σελίδας. Δεν τροποποιούν τα υποκείμενα raster δεδομένα, έτσι το PDF παραμένει αναζητήσιμο εάν υπάρχουν στρώματα OCR.

**Ε: Πώς να διαχειριστώ πολύ μεγάλα PDF χωρίς να εξαντλήσω τη μνήμη;**  
Α: Επεξεργαστείτε το έγγραφο σελίδα‑με‑σελίδα χρησιμοποιώντας `LoadOptions.PageNumbers`, απελευθερώστε άμεσα κάθε παρουσία `Annotator` και ενεργοποιήστε αποθήκευση σε streaming σε `MemoryStream` για αποφυγή αιχμών στο δίσκο.

## Ενσωμάτωση με Εφαρμογές ASP.NET

Όταν εκθέτετε τη λειτουργικότητα σημειώσεων μέσω web API, ακολουθήστε το παρακάτω πρότυπο:

1. **Ο ελεγκτής λαμβάνει το ρεύμα PDF** από τον πελάτη.  
2. **Επικυρώστε το μέγεθος αρχείου** (απορρίψτε > 200 MB εκτός αν έχετε ειδική διαχείριση).  
3. **Δημιουργήστε `Annotator` μέσα σε `using` block** για εγγυημένη απελευθέρωση.  
4. **Εφαρμόστε σημειώσεις** βάσει JSON payload που περιγράφει τύπο σημείωσης, συντεταγμένες και κείμενο.  
5. **Αποθηκεύστε σε προσωρινή θέση**, στη συνέχεια ρέξτε το αποτέλεσμα πίσω στον πελάτη με το κατάλληλο header `Content‑Disposition`.

```csharp
[HttpPost("annotate")]
public async Task<IActionResult> Annotate(IFormFile pdf, [FromBody] AnnotationRequest request)
{
    using var stream = pdf.OpenReadStream();
    var annotator = new Annotator(stream);
    // add annotations based on request
    var output = new MemoryStream();
    annotator.Save(output);
    output.Position = 0;
    return File(output, "application/pdf", "annotated.pdf");
}
```

## Πρόσθετοι Πόροι
- [GroupDocs purchase page](https://purchase.groupdocs.com/buy)  
- [Buy GroupDocs](https://purchase.groupdocs.com/buy)  
- [GroupDocs Annotation Documentation](https://docs.groupdocs.com/annotation/net/)  
- [GroupDocs API Reference](https://reference.groupdocs.com/annotation/net/)  
- [Latest Releases](https://releases.groupdocs.com/annotation/net/)  
- [Try GroupDocs for Free](https://releases.groupdocs.com/annotation/net/)  
- [Request a Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- [GroupDocs Forum](https://forum.groupdocs.com/c/annotation/)

## Συμπέρασμα και Επόμενα Βήματα

Τώρα έχετε έναν **πλήρη, έτοιμο για παραγωγή οδικό χάρτη** για την κατασκευή ενός **συστήματος ανασκόπησης εγγράφων** με το GroupDocs.Annotation για .NET. Έχετε μάθει πώς να ρυθμίσετε τη βιβλιοθήκη, να προσθέσετε σημειώσεις περιοχής, έλλειψης και κειμένου, να φιλτράρετε τις αποθηκεύσεις και να κρατήσετε τη χρήση μνήμης χαμηλή ακόμη και με τεράστια PDF.

**Επόμενες ενέργειες που μπορείτε να κάνετε σήμερα:**  

1. **Δοκιμάστε** πρόσθετους τύπους σημειώσεων όπως `ArrowAnnotation` και `StampAnnotation`.  
2. **Ενσωματώστε** τη ροή εργασίας στην υπάρχουσα ASP.NET Core API ή σε εφαρμογή desktop WPF.  
3. **Εξερευνήστε** την πλήρη αναφορά API για να ανακαλύψετε προχωρημένα χαρακτηριστικά όπως έκδοση σημειώσεων και προσαρμοσμένα μεταδεδομένα.  
4. **Συμμετέχετε** στα φόρουμ της κοινότητας GroupDocs για υποστήριξη από συναδέλφους και για ενημερώσεις σχετικά με νέες κυκλοφορίες.

---

**Τελευταία Ενημέρωση:** 2026-05-26  
**Δοκιμάστηκε Με:** GroupDocs.Annotation 23.11 for .NET  
**Συγγραφέας:** GroupDocs  

---

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

```csharp
using System;
using GroupDocs.Annotation;

class Program
{
    static void Main()
    {
        string inputPdfPath = "input.pdf";
        
        try
        {
            // Initialize the Annotator with the path of the document
            using (Annotator annotator = new Annotator(inputPdfPath))
            {
                Console.WriteLine("GroupDocs.Annotation initialized successfully!");
                // Your annotation code will go here
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Setup issue: {ex.Message}");
        }
    }
}
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // All annotation work happens inside this using block
    // This ensures proper resource cleanup
}
```

```csharp
AreaAnnotation areaAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // X, Y, Width, Height
    BackgroundColor = 65535,                 // Yellow highlight
    PageNumber = 0                           // First page
};
```

```csharp
EllipseAnnotation ellipseAnnotation = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // Same coordinate system
    BackgroundColor = 123456,                // Different color
    PageNumber = 1                           // Second page
};
```

```csharp
annotator.Add(new List<AnnotationBase>() { areaAnnotation, ellipseAnnotation });
```

```csharp
SaveOptions saveOptions = new SaveOptions 
{
    AnnotationTypes = AnnotationType.Ellipse // Only save ellipse annotations
};
```

```csharp
annotator.Save(outputPath, saveOptions);
```

```csharp
using (Annotator annotator = new Annotator(inputPdfPath))
{
    // Your annotation code here
} // Automatic cleanup happens here
```

```csharp
var annotationsToAdd = new List<AnnotationBase>();
// Add multiple annotations to the list
annotator.Add(annotationsToAdd); // Single operation
```

```csharp
// Always verify file exists before processing
if (!File.Exists(inputPdfPath))
{
    throw new FileNotFoundException($"PDF file not found: {inputPdfPath}");
}

// Use absolute paths when possible
string absolutePath = Path.GetFullPath(inputPdfPath);
```

```csharp
// Test with known coordinates first
AreaAnnotation testAnnotation = new AreaAnnotation()
{
    Box = new Rectangle(50, 50, 100, 100), // Start with simple values
    BackgroundColor = 65535,
    PageNumber = 0
};

// Verify page dimensions if needed
// Consider PDF scaling factors in your calculations
```

```csharp
// Define color constants for consistency
public static class AnnotationColors
{
    public const int ImportantHighlight = 65535;    // Yellow
    public const int AttentionMarker = 255;         // Red
    public const int ApprovedSection = 65280;       // Green
}
```

```csharp
try
{
    using (Annotator annotator = new Annotator(inputPdfPath))
    {
        // Your annotation operations
        annotator.Add(annotations);
        annotator.Save(outputPath, saveOptions);
    }
}
catch (GroupDocsException ex)
{
    // Handle GroupDocs-specific errors
    Logger.Error($"GroupDocs error: {ex.Message}");
}
catch (IOException ex)
{
    // Handle file I/O errors
    Logger.Error($"File operation error: {ex.Message}");
}
catch (Exception ex)
{
    // Handle unexpected errors
    Logger.Error($"Unexpected error: {ex.Message}");
}
```

```csharp
[HttpPost]
public async Task<IActionResult> AnnotatePdf(IFormFile pdfFile, AnnotationRequest request)
{
    // Validate input
    if (pdfFile == null || pdfFile.Length == 0)
        return BadRequest("No file provided");

    // Process asynchronously to avoid blocking the UI
    var result = await ProcessAnnotationsAsync(pdfFile, request);
    return Ok(result);
}
```

## Σχετικά Μαθήματα

- [GroupDocs Annotation .NET Tutorial - Complete Guide for Document Management](/annotation/net/annotation-management/)  
- [Document Preview .NET Tutorials - Complete GroupDocs.Annotation Guide](/annotation/net/document-preview/)  
- [GroupDocs Annotation Metered License Tutorial - Complete .NET Setup Guide](/annotation/net/licensing-and-configuration/implement-metered-license-groupdocs-annotation-net/)