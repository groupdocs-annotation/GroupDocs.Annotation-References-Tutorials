---
title: Προσθήκη σχολιασμού σημείου στο έγγραφο
linktitle: Προσθήκη σχολιασμού σημείου στο έγγραφο
second_title: GroupDocs.Annotation .NET API
description: Μάθετε πώς να προσθέτετε Σημειώσεις σε αρχεία PDF χρησιμοποιώντας το GroupDocs.Annotation για .NET. Οδηγός βήμα προς βήμα για απρόσκοπτη ενσωμάτωση.
weight: 17
url: /el/net/unlocking-annotation-power/add-point-annotation/
---
## Εισαγωγή
Το GroupDocs.Annotation για .NET είναι ένα ισχυρό εργαλείο που επιτρέπει στους προγραμματιστές να προσθέτουν διάφορους τύπους σχολιασμών σε έγγραφα μέσω προγραμματισμού. Σε αυτό το σεμινάριο, θα επικεντρωθούμε στην προσθήκη ενός σχολιασμού σημείου σε ένα έγγραφο χρησιμοποιώντας C#.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:
1. Βασική κατανόηση της γλώσσας προγραμματισμού C#.
2. Το Visual Studio είναι εγκατεστημένο στο σύστημά σας.
3.  Εγκαταστάθηκε το GroupDocs.Annotation για τη βιβλιοθήκη .NET. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.groupdocs.com/annotation/net/).

## Εισαγωγή απαραίτητων χώρων ονομάτων
Για να ξεκινήσετε, πρέπει να εισαγάγετε τους απαιτούμενους χώρους ονομάτων στο έργο σας C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Βήμα 1: Καθορίστε τη διαδρομή εξόδου
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Σε αυτό το βήμα, ορίζουμε τη διαδρομή εξόδου όπου θα αποθηκευτεί το σχολιασμένο έγγραφο.
## Βήμα 2: Εκκίνηση του Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Εδώ, αρχικοποιούμε το`Annotator` αντικείμενο με το έγγραφο εισόδου ("input.pdf").
## Βήμα 3: Δημιουργήστε σχολιασμό σημείου
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
 Σε αυτό το βήμα, δημιουργούμε ένα`PointAnnotation` αντικείμενο και καθορίστε τις ιδιότητές του, όπως θέση, μήνυμα, αριθμό σελίδας και απαντήσεις.
## Βήμα 4: Προσθήκη σχολιασμού
```csharp
annotator.Add(point);
```
Εδώ, προσθέτουμε τον σχολιασμό σημείου που δημιουργήθηκε στο έγγραφο.
## Βήμα 5: Αποθήκευση εγγράφου
```csharp
annotator.Save(outputPath);
```
Τέλος, αποθηκεύουμε το σχολιασμένο έγγραφο στην καθορισμένη διαδρομή εξόδου.

## συμπέρασμα
Σε αυτό το σεμινάριο, μάθαμε πώς να προσθέτουμε έναν σχολιασμό σημείου σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Με αυτήν την ισχυρή βιβλιοθήκη, μπορείτε να βελτιώσετε τις εφαρμογές διαχείρισης εγγράφων σας ενσωματώνοντας λειτουργίες σχολιασμού.
## Συχνές ερωτήσεις
### Είναι το GroupDocs.Annotation για .NET συμβατό με όλες τις μορφές εγγράφων;
Ναι, το GroupDocs.Annotation για .NET υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, όπως PDF, Microsoft Word, Excel, PowerPoint και άλλα.
### Μπορώ να προσαρμόσω την εμφάνιση των σχολιασμών;
Απολύτως! Το GroupDocs.Annotation για .NET παρέχει εκτενείς επιλογές για την προσαρμογή της εμφάνισης των σχολιασμών ανάλογα με τις ανάγκες της εφαρμογής σας.
### Υπάρχει διαθέσιμη δωρεάν δοκιμή για το GroupDocs.Annotation για το .NET;
 Ναι, μπορείτε να επωφεληθείτε από μια δωρεάν δοκιμή από[εδώ](https://releases.groupdocs.com/).
### Πώς μπορώ να λάβω υποστήριξη για τυχόν ζητήματα ή ερωτήματα που σχετίζονται με το GroupDocs.Annotation για .NET;
 Μπορείτε να λάβετε υποστήριξη από το φόρουμ GroupDocs.Annotation[εδώ](https://forum.groupdocs.com/c/annotation/10).
### Μπορώ να αποκτήσω προσωρινή άδεια για σκοπούς δοκιμών;
 Ναι, μπορείτε να αποκτήσετε προσωρινή άδεια από[εδώ](https://purchase.groupdocs.com/temporary-license/).