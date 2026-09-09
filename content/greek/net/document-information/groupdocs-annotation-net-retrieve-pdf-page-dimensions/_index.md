---
categories:
- Document Processing
date: '2026-06-16'
description: Μάθετε πώς να λαμβάνετε το μέγεθος σελίδας pdf σε .NET χρησιμοποιώντας
  το GroupDocs.Annotation. Εξαγωγή πλάτους και ύψους σελίδας pdf, ανάκτηση πλάτους
  και ύψους pdf, και αποτελεσματική διαχείριση διαστάσεων σελίδας pdf σε c#.
keywords: pdf page dimensions .net, groupdocs.annotation tutorial, pdf metadata extraction
  c#, .net document processing, retrieve pdf dimensions programmatically
lastmod: '2026-06-16'
linktitle: PDF Page Dimensions .NET Οδηγός
schemas:
- author: GroupDocs
  dateModified: '2026-06-16'
  description: Learn how to get pdf page size in .NET using GroupDocs.Annotation.
    Extract pdf page width height, retrieve pdf width height, and handle c# pdf page
    dimensions efficiently.
  headline: PDF Page Dimensions .NET - Extract Width & Height with C#
  type: TechArticle
- description: Learn how to get pdf page size in .NET using GroupDocs.Annotation.
    Extract pdf page width height, retrieve pdf width height, and handle c# pdf page
    dimensions efficiently.
  name: PDF Page Dimensions .NET - Extract Width & Height with C#
  steps:
  - name: Initialize the Annotator with Your PDF
    text: Create an `Annotator` instance pointing to your PDF file. Always wrap it
      in a `using` block so the file handle is released promptly. **Pro Tip:** Proper
      disposal prevents memory leaks, especially when processing dozens of large PDFs
      in a batch job.
  - name: Retrieve Document Information
    text: '`DocumentInfo` is an object that holds overall PDF metadata such as total
      page count and a collection of `PageInfo` objects for each page. GroupDocs.Annotation
      makes metadata extraction a one‑liner: The returned `DocumentInfo` object gives
      you: - Total page count - File format details - A `Pages` li'
  - name: Validate the Retrieved Data
    text: Before you start looping over pages, confirm the document info isn’t null
      and that the page collection contains entries. This defensive check avoids null‑reference
      exceptions and provides early feedback if the PDF is corrupted.
  - name: Extract Width and Height for Each Page
    text: '`PageInfo` represents a single page’s properties, including its width,
      height, and rotation angle. Iterate through the `Pages` collection and read
      `Width` and `Height`. Remember that the values are expressed in **points** (1
      point = 1/72 inch). **Key Points** - Width appears first, then height. - Pa'
  type: HowTo
- questions:
  - answer: Yes. The free trial version supports basic dimension extraction, though
      it may impose a limit on the number of pages processed per session.
    question: Can I extract PDF page dimensions without a license?
  - answer: GroupDocs.Annotation returns dimensions in **points** (1 point = 1/72
      inch). Convert to inches by dividing by 72, or to millimeters by multiplying
      by 0.352778.
    question: What units are the width and height measurements in?
  - answer: 'Pass the password via `LoadOptions` when constructing the `Annotator`:
      `new Annotator(path, new LoadOptions { Password = "your‑password" })`.'
    question: How do I handle password‑protected PDFs?
  - answer: Yes. Download the file to a local `Stream` first, then use the stream‑based
      `Annotator` constructor to avoid intermediate files.
    question: Can this work with PDFs stored in cloud storage like Azure or AWS?
  - answer: GroupDocs.Annotation reads only the PDF’s cross‑reference table and page
      dictionaries, so most PDFs under 100 MB are processed in under 1 second on typical
      server hardware.
    question: What is the performance impact of extracting dimensions from large PDFs?
  type: FAQPage
tags:
- pdf-processing
- dotnet
- groupdocs
- document-metadata
title: PDF Page Dimensions .NET - Εξαγωγή Πλάτους & Ύψους με C#
type: docs
url: /el/net/document-information/groupdocs-annotation-net-retrieve-pdf-page-dimensions/
weight: 1
---

# Διαστάσεις Σελίδας PDF .NET - Εξαγωγή Πλάτους & Ύψους με C#

## Εισαγωγή

Έχετε βρεθεί ποτέ να παλεύετε με έγγραφα PDF στην εφαρμογή σας .NET, χρειάζοντας να **get pdf page size** για κάθε σελίδα; Δεν είστε μόνοι. Είτε δημιουργείτε προβολέα εγγράφων, είτε σχεδιάζετε εκτυπώσεις, είτε επεξεργάζεστε φόρμες, οι ακριβείς διαστάσεις της σελίδας είναι η βάση μιας άψογης εμπειρίας χρήστη.

Σε αυτόν τον ολοκληρωμένο οδηγό, θα σας καθοδηγήσουμε στη διαδικασία εξαγωγής διαστάσεων σελίδας PDF χρησιμοποιώντας το **GroupDocs.Annotation for .NET**—μια από τις πιο αξιόπιστες βιβλιοθήκες για αυτήν την εργασία. Στο τέλος, θα έχετε λειτουργικό κώδικα που ανακτά το πλάτος, το ύψος και άλλα βασικά μεταδεδομένα από οποιοδήποτε έγγραφο PDF.

### Γρήγορες Απαντήσεις
- **Πώς μπορώ να λάβω το μέγεθος σελίδας pdf σε .NET;** Use `Annotator.GetDocumentInfo()` and read `PageInfo.Width` / `PageInfo.Height`.
- **Ποια βιβλιοθήκη υποστηρίζει την εξαγωγή πλάτους και ύψους σελίδας pdf;** GroupDocs.Annotation for .NET (v25.4.0+).
- **Χρειάζομαι άδεια για βασική εξαγωγή διαστάσεων;** A free trial works; a commercial license is required for production.
- **Σε ποιες μονάδες επιστρέφονται;** Points (1/72 inch); convert to inches or millimeters as needed.
- **Μπορώ να επεξεργαστώ μεγάλα PDF αποδοτικά;** Yes—GroupDocs.Annotation reads metadata without loading the full file into memory.

### Τι είναι το **get pdf page size**;
**Get pdf page size** αναφέρεται στην προγραμματιστική ανάκτηση του πλάτους και του ύψους μιας σελίδας PDF. Αυτή η λειτουργία είναι απαραίτητη για υπολογισμούς διάταξης, προετοιμασία εκτύπωσης και τοποθέτηση πεδίων φόρμας σε εφαρμογές .NET.

## Γιατί οι Διαστάσεις Σελίδας PDF Είναι Σημαντικές στην Ανάπτυξη .NET

Πριν περάσουμε στον κώδικα, ας εξετάσουμε γιατί η γνώση του **pdf page width height** είναι σημαντική. Αυτοί οι αριθμοί δεν είναι απλώς τυχαία στοιχεία—οδηγούν πραγματικές λειτουργίες:

- **Διαχείριση Διάταξης** – Οι προσαρμοστικοί προβολείς μπορούν να κλιμακώσουν αυτόματα με βάση το ακριβές μέγεθος της σελίδας, εξαλείφοντας άβολες γραμμές κύλισης.
- **Βελτιστοποίηση Εκτύπωσης** – Ακριβείς διαστάσεις αποτρέπουν σπατάλη χαρτιού και λανθασμένες εκτυπώσεις σε εμπορικές ροές εργασίας.
- **Επεξεργασία Φορμών** – Οι συντεταγμένες εξαγωγής εξαρτώνται από ακριβές μέγεθος σελίδας· ένα σφάλμα 2 mm μπορεί να διακόψει τη λήψη δεδομένων.
- **Σχεδιασμός Πόρων** – Μεγάλα PDF με διαφορετικά μεγέθη απαιτούν διαφορετικές στρατηγικές μνήμης· η έγκαιρη γνώση του μεγέθους επιτρέπει πιο έξυπνη ομαδοποίηση.

## Προαπαιτούμενα

### Απαιτούμενες Βιβλιοθήκες και Εκδόσεις
- **GroupDocs.Annotation for .NET** (Version 25.4.0 or later). This version supports **50+ input and output formats** and can handle multi‑hundred‑page PDFs without loading the entire file into memory.
- .NET Framework 4.6.1+ **or** .NET Core 2.0+

### Απαιτήσεις Ρύθμισης Περιβάλλοντος
- Visual Studio 2019 or later (Community edition works perfectly)
- A test PDF file (we’ll show you how to handle different types)
- Basic familiarity with `using` statements and object disposal in C#

### Προαπαιτούμενες Γνώσεις
Χρειάζεστε μόνο:
- C# fundamentals
- NuGet package management basics
- Simple file I/O in .NET

Έχετε όλα έτοιμα; Τέλεια—ας ρυθμίσουμε τη βιβλιοθήκη.

## Ρύθμιση του GroupDocs.Annotation για .NET

Η εγκατάσταση του GroupDocs.Annotation είναι απλή, αλλά υπάρχουν μερικοί τρόποι ανάλογα με τη ροή εργασίας σας.

### Μέθοδος 1: Χρήση του NuGet Package Manager Console
Ανοίξτε το Package Manager Console στο Visual Studio και εκτελέστε:

```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```

### Μέθοδος 2: Χρήση του .NET CLI
Αν προτιμάτε εργαλεία γραμμής εντολών:

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### Μέθοδος 3: Visual Package Manager
1. Κάντε δεξί κλικ στο έργο σας στο Solution Explorer  
2. Επιλέξτε **Manage NuGet Packages**  
3. Αναζητήστε **GroupDocs.Annotation**  
4. Κάντε κλικ στο **Install**

#### Επιλογές Άδειας (Επιλέξτε Ό,τι Σας Ταιριάζει)
- **Free Trial** – Core features, including dimension extraction, are available with minor usage caps—perfect for proof‑of‑concept work.  
- **Temporary License** – Request a 30‑day temporary key for full functionality during evaluation.  
- **Commercial License** – Required for production deployments; pricing scales with developer count and deployment model.

### Γρήγορη Επαλήθευση Ρύθμισης
Ακολουθεί ένα απλό τεστ για να επιβεβαιώσετε ότι όλα είναι σωστά συνδεδεμένα:

```csharp
using GroupDocs.Annotation;

// This should compile without errors if installation succeeded
using (Annotator annotator = new Annotator(@"path\to\your\test.pdf"))
{
    Console.WriteLine("GroupDocs.Annotation is ready to use!");
}
```

Αν αυτός ο κώδικας μεταγλωττιστεί και εκτελεστεί χωρίς εξαιρέσεις, είστε έτοιμοι να εξάγετε τα μεγέθη των σελίδων.

## Τι είναι η κλάση **Annotator**;
Η κλάση `Annotator` είναι το βασικό αντικείμενο του GroupDocs.Annotation που αντιπροσωπεύει ένα έγγραφο PDF στη μνήμη και παρέχει μεθόδους για ανάγνωση μεταδεδομένων, προσθήκη σχολίων και εξαγωγή πληροφοριών σελίδας. Περιλαμβάνει τη διαχείριση αρχείων, υποστηρίζει φόρτωση από ροές και εξασφαλίζει ότι όλες οι επόμενες λειτουργίες περνούν μέσω ενός αντικειμένου `Annotator`, απλοποιώντας τη διαχείριση της ροής εργασίας.

## Πώς να **get pdf page size** χρησιμοποιώντας το GroupDocs.Annotation;
`GetDocumentInfo()` επιστρέφει ένα αντικείμενο `DocumentInfo` που περιέχει συνολικά μεταδεδομένα PDF, συμπεριλαμβανομένου του αριθμού σελίδων και μιας συλλογής λεπτομερειών σελίδας. Φορτώστε το PDF σας με `new Annotator("file.pdf")` και καλέστε αυτή τη μέθοδο· κάθε `PageInfo` στη συλλογή `Pages` περιέχει `Width` και `Height`. Αυτή η διπλή προσέγγιση παρέχει τις διαστάσεις σε points αμέσως, χωρίς να χρειάζεται ανάλυση ολόκληρου του αρχείου.

## Οδηγός Υλοποίησης Βήμα‑βήμα

### Βήμα 1: Αρχικοποίηση του Annotator με το PDF σας
Δημιουργήστε ένα αντικείμενο `Annotator` που δείχνει στο αρχείο PDF σας. Πάντα να το τυλίγετε σε ένα μπλοκ `using` ώστε η διαχείριση του αρχείου να απελευθερώνεται άμεσα.

```csharp
using (Annotator annotator = new Annotator(@"YOUR_DOCUMENT_DIRECTORY\INPUT_PDF"))
{
    // All our dimension extraction magic happens here
}
```

**Pro Tip:** Η σωστή απελευθέρωση αποτρέπει διαρροές μνήμης, ειδικά όταν επεξεργάζεστε δεκάδες μεγάλα PDF σε μια παρτίδα εργασίας.

### Βήμα 2: Ανάκτηση Πληροφοριών Εγγράφου
`DocumentInfo` είναι ένα αντικείμενο που κρατά τα συνολικά μεταδεδομένα PDF όπως ο συνολικός αριθμός σελίδων και μια συλλογή αντικειμένων `PageInfo` για κάθε σελίδα.  

Το GroupDocs.Annotation κάνει την εξαγωγή μεταδεδομένων σε μία γραμμή:

```csharp
IDocumentInfo info = annotator.Document.GetDocumentInfo();
```

Το επιστρεφόμενο αντικείμενο `DocumentInfo` σας παρέχει:
- Συνολικό αριθμό σελίδων  
- Λεπτομέρειες μορφής αρχείου  
- Μια λίστα `Pages` όπου κάθε στοιχείο περιέχει πλάτος, ύψος, περιστροφή και άλλα

### Βήμα 3: Επικύρωση των Ανακτηθέντων Δεδομένων
Πριν ξεκινήσετε την επανάληψη στις σελίδες, επιβεβαιώστε ότι το `DocumentInfo` δεν είναι null και ότι η συλλογή σελίδων περιέχει στοιχεία.

```csharp
if (info.PagesInfo != null && info.PagesInfo.Count > 0)
{
    Console.WriteLine($"\t Document info: Type {info.FileType}, size = {info.Size}, pages = {info.PageCount}");
}
else
{
    Console.WriteLine("No page information available - check your PDF file");
    return;
}
```

Αυτός ο έλεγχος αποτρέπει εξαιρέσεις null‑reference και παρέχει έγκαιρη ανατροφοδότηση εάν το PDF είναι κατεστραμμένο.

### Βήμα 4: Εξαγωγή Πλάτους και Ύψους για Κάθε Σελίδα
`PageInfo` αντιπροσωπεύει τις ιδιότητες μιας μεμονωμένης σελίδας, συμπεριλαμβανομένου του πλάτους, του ύψους και της γωνίας περιστροφής.  

Διατρέξτε τη συλλογή `Pages` και διαβάστε τα `Width` και `Height`. Θυμηθείτε ότι οι τιμές εκφράζονται σε **points** (1 point = 1/72 inch).

```csharp
foreach (var page in info.PagesInfo)
{
    Console.WriteLine($"\t\t page #{page.PageNumber}: {page.Width}x{page.Height}");
}
```

**Key Points**  
- Το πλάτος εμφανίζεται πρώτο, μετά το ύψος.  
- Οι αριθμοί σελίδων είναι 1‑based, ταιριάζοντας με αυτά που βλέπουν οι χρήστες στους προβολείς.  
- Οι πληροφορίες περιστροφής είναι επίσης διαθέσιμες αν χρειαστεί να προσαρμόσετε τις συντεταγμένες.

### Πλήρες Παράδειγμα Εργασίας (Μέθοδος)
Μπορείτε να ενσωματώσετε τα παραπάνω βήματα σε μια επαναχρησιμοποιήσιμη μέθοδο:

```csharp
using GroupDocs.Annotation;
using System;

public void ExtractPdfPageDimensions(string pdfPath)
{
    try
    {
        using (Annotator annotator = new Annotator(pdfPath))
        {
            IDocumentInfo info = annotator.Document.GetDocumentInfo();
            
            if (info.PagesInfo != null && info.PagesInfo.Count > 0)
            {
                Console.WriteLine($"Document: {info.FileType}, {info.Size} bytes, {info.PageCount} pages");
                
                foreach (var page in info.PagesInfo)
                {
                    Console.WriteLine($"Page {page.PageNumber}: {page.Width} x {page.Height} points");
                }
            }
            else
            {
                Console.WriteLine("Could not retrieve page information");
            }
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error processing PDF: {ex.Message}");
    }
}
```

## Συνηθισμένα Πιθανά Σφάλματα και Πώς να τα Αποφύγετε
Ακόμη και με απλό κώδικα, οι προγραμματιστές αντιμετωπίζουν προβλέψιμα ζητήματα. Παρακάτω είναι οι πιο συνηθισμένες παγίδες και οι αποδεδειγμένες λύσεις.

### Προβλήματα Διαδρομής Αρχείου
**Issue:** Σφάλματα “File not found” κατά την ανάπτυξη.  
**Solution:** Χρησιμοποιήστε απόλυτες διαδρομές κατά τη δοκιμή και πάντα επαληθεύετε ότι το αρχείο υπάρχει πριν δημιουργήσετε το `Annotator`.

```csharp
if (!File.Exists(pdfPath))
{
    throw new FileNotFoundException($"PDF file not found: {pdfPath}");
}
```

### Προβλήματα Δικαιωμάτων
**Issue:** Η εφαρμογή δεν έχει πρόσβαση ανάγνωσης στο αρχείο PDF, ειδικά σε web servers.  
**Solution:** Χορηγήστε τα κατάλληλα δικαιώματα ανάγνωσης στην ταυτότητα του application pool ή χρησιμοποιήστε impersonation για περιορισμένους φακέλους.

### Διαχείριση Κατεστραμμένων PDF
**Issue:** Κάποια PDF είναι μερικώς κατεστραμμένα ή χρησιμοποιούν μη‑τυπικά χαρακτηριστικά.  
**Solution:** Περιβάλλετε τη λογική εξαγωγής σε μπλοκ `try‑catch` και εμφανίστε ένα σαφές μήνυμα σφάλματος. Το GroupDocs.Annotation θα ρίξει ένα `DocumentException` για μη‑υποστηριζόμενες δομές.

### Διαρροές Μνήμης με Μεγάλα Αρχεία
**Issue:** Η επεξεργασία πολλών μεγάλων PDF χωρίς απελευθέρωση των αντικειμένων `Annotator` οδηγεί σε καταρρεύσεις μνήμης.  
**Solution:** Πάντα να χρησιμοποιείτε δηλώσεις `using` και να εξετάζετε την επεξεργασία αρχείων σε μικρότερες παρτίδες ή σε λειτουργία streaming.

### Συμβατότητα Εκδόσεων
**Issue:** Η ανάμειξη διαφορετικών εκδόσεων της βιβλιοθήκης GroupDocs μπορεί να προκαλέσει ασυμφωνίες τύπων.  
**Solution:** Ενσωματώστε μια ενιαία έκδοση σε όλη τη λύση και ενημερώστε όλα τα σχετικά πακέτα μαζί.

## Πραγματικές Εφαρμογές
Η κατανόηση του **retrieve pdf width height** ανοίγει ισχυρά σενάρια:

### Εφαρμογές Προβολής Εγγράφων
Οι προσαρμοστικοί προβολείς μπορούν αυτόματα να ορίσουν το αρχικό επίπεδο ζουμ βάσει των διαστάσεων της σελίδας, παρέχοντας μια εμπειρία “προσαρμοσμένη στην οθόνη” χωρίς χειροκίνητες ρυθμίσεις.

```csharp
// Example: Calculate optimal zoom for viewport
double optimalZoom = Math.Min(viewportWidth / pageWidth, viewportHeight / pageHeight);
```

### Αυτόματη Δημιουργία Αναφορών
Κατά τη συγχώνευση πολλαπλών PDF σε μια ενιαία αναφορά, η γνώση του μεγέθους κάθε σελίδας εξασφαλίζει συνεπή κλιμάκωση και αποτρέπει απροσδόκητες διακοπές σελίδας.

### Συστήματα Διαχείρισης Εκτύπωσης
Οι ακριβείς διαστάσεις σας επιτρέπουν να υπολογίσετε τη βέλτιστη χρήση χαρτιού, να εντοπίσετε προσανατολισμό πορτραίτου ή τοπίου, και να προετοιμάσετε τα έγγραφα πριν τα στείλετε σε εμπορικούς εκτυπωτές.

### Λύσεις Επεξεργασίας Φορμών
Ακριβείς συντεταγμένες που προέρχονται από το μέγεθος της σελίδας επιτρέπουν αξιόπιστη εξαγωγή πλαισίων ελέγχου, υπογραφών και πεδίων κειμένου σε PDF με διαφορετικές διατάξεις.

### Διαχείριση Ψηφιακών Περιουσιακών Στοιχείων
Ετικετοποιήστε τα PDF με μεταδεδομένα μεγέθους για να διευκολύνετε γρήγορες αναζητήσεις (π.χ., “εμφάνιση όλων των εγγράφων μεγέθους A4”) και να βελτιώσετε την αποδοτικότητα της κατηγοριοποίησης.

## Συμβουλές Βελτιστοποίησης Απόδοσης
Όταν προχωράτε από ένα πρωτότυπο στην παραγωγή, η απόδοση γίνεται κρίσιμη.

### Στρατηγική Επεξεργασίας σε Παρτίδες
Ομαδοποιήστε παρόμοιες λειτουργίες για να μειώσετε το κόστος. Για παράδειγμα, διαβάστε τα μεταδεδομένα για μια παρτίδα αρχείων, αποθηκεύστε τα αποτελέσματα, και στη συνέχεια επεξεργαστείτε τα σχόλια σε δεύτερο πέρασμα.

```csharp
var results = new List<PageDimensionResult>();
foreach (var pdfFile in pdfFiles.Take(10)) // Process in batches of 10
{
    // Extract dimensions and add to results
}
```

### Caching Συχνά Πρόσβασης Διαστάσεων
Αν τα ίδια PDF ερωτώνται επανειλημμένα, αποθηκεύστε τα αντικείμενα `DocumentInfo` σε ένα thread‑safe dictionary. Θυμηθείτε να ακυρώνετε την cache όταν το αρχείο πηγής αλλάζει.

```csharp
private static readonly Dictionary<string, IDocumentInfo> _dimensionCache = 
    new Dictionary<string, IDocumentInfo>();
```

### Ασύγχρονη Επεξεργασία για Μεγάλα Αρχεία
Εκμεταλλευτείτε τα πρότυπα `async/await` για να διατηρήσετε τα νήματα UI ανταποκρινόμενα ενώ το GroupDocs.Annotation διαβάζει τα μεταδεδομένα στο παρασκήνιο.

```csharp
public async Task<List<PageInfo>> ExtractDimensionsAsync(string pdfPath)
{
    return await Task.Run(() => {
        // Your dimension extraction code here
    });
}
```

### Καλές Πρακτικές Διαχείρισης Μνήμης
- Απελευθερώστε άμεσα κάθε αντικείμενο `Annotator`.
- Επεξεργαστείτε μεγάλες συλλογές σε τμήματα των 20–50 αρχείων για να διατηρήσετε το αποτύπωμα μνήμης χαμηλό.
- Παρακολουθήστε τη χρήση μνήμης με μετρητές απόδοσης ή εργαλεία profiling.
- Χρησιμοποιήστε weak references για αντικείμενα στην cache εάν αναμένετε υψηλή κυκλοφορία.

## Προχωρημένες Περιπτώσεις Χρήσης
Μόλις εξοικειωθείτε με την βασική εξαγωγή, εξερευνήστε αυτά τα προχωρημένα σενάρια.

### Διαχείριση Εγγράφων Μικτής-Διαστάσεων
Κάποια PDF περιέχουν σελίδες διαφορετικών μεγεθών (π.χ., εξώφυλλο σε A4 ακολουθούμενο από εσωτερικές σελίδες A5). Ανιχνεύστε αλλαγές μεγέθους συγκρίνοντας διαδοχικές τιμές `PageInfo.Width`/`Height` και εφαρμόστε λογική υπό συνθήκη.

```csharp
var pageSizes = info.PagesInfo.Select(p => new { p.PageNumber, p.Width, p.Height }).ToList();
var uniqueSizes = pageSizes.Select(p => new { p.Width, p.Height }).Distinct().Count();

if (uniqueSizes > 1)
{
    Console.WriteLine("Document contains multiple page sizes");
}
```

### Ανίχνευση Προσανατολισμού
Καθορίστε πορτραίτο ή τοπίο συγκρίνοντας πλάτος και ύψος. Αυτό είναι χρήσιμο για αυτόματη περιστροφή σελίδων σε προβολείς ή για δημιουργία μικρογραφιών με γνώση του προσανατολισμού.

```csharp
foreach (var page in info.PagesInfo)
{
    string orientation = page.Width > page.Height ? "Landscape" : "Portrait";
    Console.WriteLine($"Page {page.PageNumber}: {orientation}");
}
```

### Ενσωμάτωση με Άλλες Λειτουργίες του GroupDocs
Συνδυάστε την εξαγωγή διαστάσεων με τα API σχολίων για να τοποθετήσετε σφραγίδες ακριβώς, ή με τα API μετατροπής για να δημιουργήσετε εικόνες που σέβονται το αρχικό μέγεθος σελίδας.

## Συχνές Ερωτήσεις

**Q: Μπορώ να εξάγω τις διαστάσεις σελίδας PDF χωρίς άδεια;**  
A: Ναι. Η έκδοση δωρεάν δοκιμής υποστηρίζει βασική εξαγωγή διαστάσεων, αν και μπορεί να επιβάλει όριο στον αριθμό σελίδων που επεξεργάζονται ανά συνεδρία.

**Q: Σε ποιες μονάδες είναι οι μετρήσεις του πλάτους και του ύψους;**  
A: Το GroupDocs.Annotation επιστρέφει διαστάσεις σε **points** (1 point = 1/72 inch). Μετατρέψτε σε ίντσες διαιρώντας με 72, ή σε χιλιοστά πολλαπλασιάζοντας με 0.352778.

**Q: Πώς να διαχειριστώ PDF με προστασία κωδικού;**  
A: Περνάτε τον κωδικό μέσω `LoadOptions` κατά τη δημιουργία του `Annotator`: `new Annotator(path, new LoadOptions { Password = "your‑password" })`.

**Q: Μπορεί αυτό να λειτουργήσει με PDF αποθηκευμένα σε cloud storage όπως Azure ή AWS;**  
A: Ναι. Κατεβάστε το αρχείο σε ένα τοπικό `Stream` πρώτα, έπειτα χρησιμοποιήστε τον κατασκευαστή `Annotator` που βασίζεται σε stream για να αποφύγετε ενδιάμεσα αρχεία.

**Q: Ποιος είναι ο αντίκτυπος στην απόδοση όταν εξάγονται διαστάσεις από μεγάλα PDF;**  
A: Το GroupDocs.Annotation διαβάζει μόνο τον πίνακα cross‑reference και τα dictionaries των σελίδων του PDF, έτσι τα περισσότερα PDF κάτω από 100 MB επεξεργάζονται σε κάτω από 1 δευτερόλεπτο σε τυπικό εξοπλισμό διακομιστή.

**Q: Πώς να διαχειριστώ PDF με περιστρεφόμενες σελίδες;**  
A: Η ιδιότητα `PageInfo.Rotation` υποδεικνύει τη γωνία περιστροφής. Εάν μια σελίδα είναι περιστραμμένη 90° ή 270°, ανταλλάξτε τις τιμές πλάτους και ύψους για να λάβετε τις εμφανιζόμενες διαστάσεις.

**Q: Μπορώ να εξάγω διαστάσεις μόνο από συγκεκριμένες σελίδες;**  
A: Ναι. Μετά την κλήση του `GetDocumentInfo()`, φιλτράρετε τη συλλογή `Pages` με βάση το `PageNumber` για να στοχεύσετε μεμονωμένες σελίδες.

**Q: Λειτουργεί αυτό με έγγραφα μορφής PDF/A;**  
A: Απόλυτα. Το GroupDocs.Annotation υποστηρίζει πλήρως τα πρότυπα PDF/A‑1, PDF/A‑2 και PDF/A‑3.

**Q: Πώς να αντιμετωπίσω σφάλματα “Unable to load document”;**  
A: Επαληθεύστε τα δικαιώματα αρχείου, βεβαιωθείτε ότι το αρχείο δεν είναι κατεστραμμένο ανοίγοντάς το σε έναν PDF reader, και επιβεβαιώστε ότι χρησιμοποιείτε υποστηριζόμενη έκδοση PDF (1.4–2.0).

**Q: Μπορώ να λάβω διαστάσεις σε pixel αντί για points;**  
A: Μετατρέψτε χειροκίνητα: `pixels = points * DPI / 72`. Για τυπικό DPI οθόνης 96, πολλαπλασιάστε τα points με 1.3333.

## Απαραίτητα Πόροι

- **Τεκμηρίωση**: [GroupDocs Annotation Documentation](https://docs.groupdocs.com/annotation/net/)
- **API Reference**: [GroupDocs Annotation API Reference](https://reference.groupdocs.com/annotation/net/)
- **Λήψη**: [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/)
- **Αγορά**: [Buy GroupDocs](https://purchase.groupdocs.com/buy)
- **Free Trial**: [Try Free Version](https://releases.groupdocs.com/annotation/net/)
- **Temporary License**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Υποστήριξη**: [GroupDocs Forum](https://forum.groupdocs.com/c/annotation/)

---

**Τελευταία Ενημέρωση:** 2026-06-16  
**Δοκιμάστηκε Με:** GroupDocs.Annotation 25.4.0 for .NET  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Εξαγωγή Μεταδεδομένων Εγγράφου .NET - Πλήρης Οδηγός για GroupDocs.Annotation](/annotation/net/document-information/)
- [Φόρτωση PDF από URL .NET - Πλήρης Οδηγός με GroupDocs.Annotation](/annotation/net/document-loading-essentials/load-document-from-url/)
- [Δημιουργία Προεπισκόπησης Εγγράφου .NET - Πλήρης Οδηγός με GroupDocs.Annotation](/annotation/net/advanced-usage/generate-document-pages-preview/)