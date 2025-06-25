---
"description": "Μάθετε πώς να προσθέτετε σχολιασμό σημείων σε PDF χρησιμοποιώντας το GroupDocs.Annotation για .NET. Οδηγός βήμα προς βήμα για απρόσκοπτη ενσωμάτωση."
"linktitle": "Προσθήκη σχολίου σημείου στο έγγραφο"
"second_title": "API .NET του GroupDocs.Annotation"
"title": "Προσθήκη σχολίου σημείου στο έγγραφο"
"url": "/el/net/unlocking-annotation-power/add-point-annotation/"
"weight": 17
---

# Προσθήκη σχολίου σημείου στο έγγραφο

## Εισαγωγή
Το GroupDocs.Annotation για .NET είναι ένα ισχυρό εργαλείο που επιτρέπει στους προγραμματιστές να προσθέτουν διάφορους τύπους σχολιασμών σε έγγραφα μέσω προγραμματισμού. Σε αυτό το σεμινάριο, θα επικεντρωθούμε στην προσθήκη σχολίων σημείων σε ένα έγγραφο χρησιμοποιώντας C#.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:
1. Βασική κατανόηση της γλώσσας προγραμματισμού C#.
2. Το Visual Studio είναι εγκατεστημένο στο σύστημά σας.
3. Το GroupDocs.Annotation για τη βιβλιοθήκη .NET είναι εγκατεστημένο. Μπορείτε να το κατεβάσετε από [εδώ](https://releases.groupdocs.com/annotation/net/).

## Εισαγωγή απαραίτητων χώρων ονομάτων
Για να ξεκινήσετε, πρέπει να εισαγάγετε τους απαιτούμενους χώρους ονομάτων στο έργο σας σε C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Βήμα 1: Ορισμός διαδρομής εξόδου
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Σε αυτό το βήμα, ορίζουμε τη διαδρομή εξόδου όπου θα αποθηκευτεί το σχολιασμένο έγγραφο.
## Βήμα 2: Αρχικοποίηση σχολιαστή
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Εδώ, αρχικοποιούμε το `Annotator` αντικείμενο με το έγγραφο εισόδου ("input.pdf").
## Βήμα 3: Δημιουργία σχολίου σημείου
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
Σε αυτό το βήμα, δημιουργούμε ένα `PointAnnotation` αντικείμενο και να καθορίσετε τις ιδιότητές του, όπως θέση, μήνυμα, αριθμό σελίδας και απαντήσεις.
## Βήμα 4: Προσθήκη σχολίου
```csharp
annotator.Add(point);
```
Εδώ, προσθέτουμε την σχολίαση σημείου που δημιουργήσαμε στο έγγραφο.
## Βήμα 5: Αποθήκευση εγγράφου
```csharp
annotator.Save(outputPath);
```
Τέλος, αποθηκεύουμε το σχολιασμένο έγγραφο στην καθορισμένη διαδρομή εξόδου.

## Σύναψη
Σε αυτό το σεμινάριο, μάθαμε πώς να προσθέτουμε μια σχολιασμό σημείων σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Με αυτήν την ισχυρή βιβλιοθήκη, μπορείτε να βελτιώσετε τις εφαρμογές διαχείρισης εγγράφων σας ενσωματώνοντας λειτουργίες σχολιασμού.
## Συχνές ερωτήσεις
### Είναι το GroupDocs.Annotation για .NET συμβατό με όλες τις μορφές εγγράφων;
Ναι, το GroupDocs.Annotation για .NET υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, όπως PDF, Microsoft Word, Excel, PowerPoint και άλλα.
### Μπορώ να προσαρμόσω την εμφάνιση των σχολιασμών;
Απολύτως! Το GroupDocs.Annotation για .NET παρέχει εκτεταμένες επιλογές για την προσαρμογή της εμφάνισης των σχολιασμών ώστε να ταιριάζουν στις ανάγκες της εφαρμογής σας.
### Υπάρχει διαθέσιμη δωρεάν δοκιμαστική έκδοση για το GroupDocs.Annotation για .NET;
Ναι, μπορείτε να επωφεληθείτε από μια δωρεάν δοκιμή από [εδώ](https://releases.groupdocs.com/).
### Πώς μπορώ να λάβω υποστήριξη για τυχόν προβλήματα ή ερωτήσεις που σχετίζονται με το GroupDocs.Annotation για .NET;
Μπορείτε να λάβετε υποστήριξη από το φόρουμ GroupDocs.Annotation [εδώ](https://forum.groupdocs.com/c/annotation/10).
### Μπορώ να λάβω προσωρινή άδεια για σκοπούς δοκιμών;
Ναι, μπορείτε να λάβετε προσωρινή άδεια από [εδώ](https://purchase.groupdocs.com/temporary-license/).