---
title: Προσθήκη σχολιασμού Ellipse στο έγγραφο
linktitle: Προσθήκη σχολιασμού Ellipse στο έγγραφο
second_title: GroupDocs.Annotation .NET API
description: Μάθετε πώς να προσθέτετε σχολιασμούς ελλείψεων σε έγγραφα στο .NET χρησιμοποιώντας GroupDocs.Annotation. Ενισχύστε τη συνεργασία και την επικοινωνία χωρίς κόπο.
weight: 13
url: /el/net/unlocking-annotation-power/add-ellipse-annotation/
---
## Εισαγωγή
Σε αυτό το σεμινάριο, θα μάθετε πώς να προσθέτετε έναν σχολιασμό έλλειψης σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Αυτός ο οδηγός βήμα προς βήμα θα σας καθοδηγήσει στη διαδικασία, διασφαλίζοντας ότι κατανοείτε με σαφήνεια κάθε βήμα.
## Προαπαιτούμενα
Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε τα ακόλουθα:
1.  GroupDocs.Annotation για .NET: Βεβαιωθείτε ότι έχετε κατεβάσει και εγκαταστήσει το GroupDocs.Annotation για .NET. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.groupdocs.com/annotation/net/).
2. IDE (Integrated Development Environment): Θα χρειαστείτε ένα IDE εγκατεστημένο στο σύστημά σας, όπως το Visual Studio, για να γράψετε και να εκτελέσετε τον κώδικα.

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
Καθορίστε τη διαδρομή εξόδου όπου θα αποθηκευτεί το σχολιασμένο έγγραφο:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Βήμα 2: Εκκίνηση του Annotator
Αρχικοποιήστε τον σχολιαστή παρέχοντας τη διαδρομή του εγγράφου εισόδου:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Βήμα 3: Δημιουργία σχολιασμού Ellipse
 Δημιουργήστε ένα παράδειγμα του`EllipseAnnotation` κλάση και ορίστε τις ιδιότητές της:
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
## Βήμα 4: Προσθήκη σχολιασμού
Προσθέστε τον σχολιασμό έλλειψης στο έγγραφο:
```csharp
annotator.Add(ellipse);
```
## Βήμα 5: Αποθήκευση εγγράφου
Αποθηκεύστε το σχολιασμένο έγγραφο στη διαδρομή εξόδου:
```csharp
annotator.Save(outputPath);
```

## συμπέρασμα
Συγχαρητήρια! Προσθέσατε με επιτυχία έναν σχολιασμό έλλειψης σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Τώρα μπορείτε να ενσωματώσετε αυτήν τη λειτουργία στις εφαρμογές σας .NET για να βελτιώσετε τη συνεργασία και την επικοινωνία των εγγράφων.
## Συχνές ερωτήσεις
### Μπορώ να προσαρμόσω την εμφάνιση του σχολιασμού της έλλειψης;
Ναι, μπορείτε να προσαρμόσετε διάφορες ιδιότητες, όπως χρώμα φόντου, χρώμα περιγράμματος, αδιαφάνεια κ.λπ., σύμφωνα με τις απαιτήσεις σας.
### Είναι το GroupDocs.Annotation για .NET συμβατό με όλες τις μορφές εγγράφων;
Το GroupDocs.Annotation για .NET υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, συμπεριλαμβανομένων των PDF, DOCX, PPTX, XLSX και άλλων.
### Μπορώ να προσθέσω πολλαπλούς σχολιασμούς σε ένα μόνο έγγραφο;
Ναι, μπορείτε να προσθέσετε πολλαπλούς σχολιασμούς, όπως ελλείψεις, ορθογώνια, κείμενο κ.λπ., σε ένα μόνο έγγραφο.
### Υπάρχει διαθέσιμη δοκιμαστική έκδοση για δοκιμαστικούς σκοπούς;
 Ναι, μπορείτε να κάνετε λήψη μιας δωρεάν δοκιμαστικής έκδοσης από[εδώ](https://releases.groupdocs.com/) να αξιολογήσει τα χαρακτηριστικά του.
### Πού μπορώ να λάβω τεχνική υποστήριξη για το GroupDocs.Annotation για .NET;
 Μπορείτε να λάβετε τεχνική υποστήριξη από το φόρουμ της κοινότητας GroupDocs.Annotation[εδώ](https://forum.groupdocs.com/c/annotation/10).