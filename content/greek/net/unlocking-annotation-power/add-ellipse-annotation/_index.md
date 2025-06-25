---
"description": "Μάθετε πώς να προσθέτετε σχολιασμούς σε έγγραφα στο .NET χρησιμοποιώντας το GroupDocs.Annotation. Βελτιώστε τη συνεργασία και την επικοινωνία χωρίς κόπο."
"linktitle": "Προσθήκη σχολίου έλλειψης σε έγγραφο"
"second_title": "API .NET του GroupDocs.Annotation"
"title": "Προσθήκη σχολίου έλλειψης σε έγγραφο"
"url": "/el/net/unlocking-annotation-power/add-ellipse-annotation/"
"weight": 13
---

# Προσθήκη σχολίου έλλειψης σε έγγραφο

## Εισαγωγή
Σε αυτό το σεμινάριο, θα μάθετε πώς να προσθέσετε μια σχολίαση σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Αυτός ο οδηγός βήμα προς βήμα θα σας καθοδηγήσει στη διαδικασία, διασφαλίζοντας ότι κατανοείτε με σαφήνεια κάθε βήμα.
## Προαπαιτούμενα
Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε τα εξής:
1. GroupDocs.Annotation για .NET: Βεβαιωθείτε ότι έχετε κατεβάσει και εγκαταστήσει το GroupDocs.Annotation για .NET. Μπορείτε να το κατεβάσετε από [εδώ](https://releases.groupdocs.com/annotation/net/).
2. IDE (Ολοκληρωμένο Περιβάλλον Ανάπτυξης): Θα χρειαστείτε ένα IDE εγκατεστημένο στο σύστημά σας, όπως το Visual Studio, για να γράψετε και να εκτελέσετε τον κώδικα.

## Εισαγωγή χώρων ονομάτων
Αρχικά, εισαγάγετε τους απαραίτητους χώρους ονομάτων στο έργο σας:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Βήμα 1: Ορισμός διαδρομής εξόδου
Ορίστε τη διαδρομή εξόδου όπου θα αποθηκευτεί το σχολιασμένο έγγραφο:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Βήμα 2: Αρχικοποίηση σχολιαστή
Αρχικοποιήστε τον σχολιαστή παρέχοντας τη διαδρομή εισόδου του εγγράφου:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Βήμα 3: Δημιουργία σχολίου ελλειπτικού
Δημιουργήστε μια παρουσία του `EllipseAnnotation` κλάση και ορίστε τις ιδιότητές της:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    }
};
```
## Βήμα 4: Προσθήκη σχολίου
Προσθέστε την σχολίαση με αποσιώπηση στο έγγραφο:
```csharp
annotator.Add(ellipse);
```
## Βήμα 5: Αποθήκευση εγγράφου
Αποθηκεύστε το σχολιασμένο έγγραφο στη διαδρομή εξόδου:
```csharp
annotator.Save(outputPath);
```

## Σύναψη
Συγχαρητήρια! Προσθέσατε με επιτυχία μια σχολίαση σε σχήμα έλλειψης σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Τώρα μπορείτε να ενσωματώσετε αυτήν τη λειτουργικότητα στις εφαρμογές .NET που διαθέτετε για να βελτιώσετε τη συνεργασία και την επικοινωνία σε έγγραφα.
## Συχνές ερωτήσεις
### Μπορώ να προσαρμόσω την εμφάνιση της σχολίασης με αποσιώπηση;
Ναι, μπορείτε να προσαρμόσετε διάφορες ιδιότητες όπως χρώμα φόντου, χρώμα περιγράμματος, αδιαφάνεια κ.λπ., ανάλογα με τις απαιτήσεις σας.
### Είναι το GroupDocs.Annotation για .NET συμβατό με όλες τις μορφές εγγράφων;
Το GroupDocs.Annotation για .NET υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, όπως PDF, DOCX, PPTX, XLSX και πολλά άλλα.
### Μπορώ να προσθέσω πολλαπλές σχολιασμοί σε ένα μόνο έγγραφο;
Ναι, μπορείτε να προσθέσετε πολλαπλές σχολιασμοί, όπως ελλείψεις, ορθογώνια, κείμενο κ.λπ., σε ένα μόνο έγγραφο.
### Υπάρχει διαθέσιμη δοκιμαστική έκδοση για δοκιμαστικούς σκοπούς;
Ναι, μπορείτε να κατεβάσετε μια δωρεάν δοκιμαστική έκδοση από [εδώ](https://releases.groupdocs.com/) να αξιολογήσει τα χαρακτηριστικά του.
### Πού μπορώ να λάβω τεχνική υποστήριξη για το GroupDocs.Annotation για .NET;
Μπορείτε να λάβετε τεχνική υποστήριξη από το φόρουμ της κοινότητας GroupDocs.Annotation [εδώ](https://forum.groupdocs.com/c/annotation/10).