---
title: Προσθήκη σχολιασμού Strikeout κειμένου στο έγγραφο
linktitle: Προσθήκη σχολιασμού Strikeout κειμένου στο έγγραφο
second_title: GroupDocs.Annotation .NET API
description: Μάθετε πώς να προσθέτετε σχολιασμούς διαγραφής κειμένου σε έγγραφα χρησιμοποιώντας το GroupDocs.Annotation για .NET. Βελτιώστε τη συνεργασία και τις διαδικασίες ελέγχου εγγράφων αποτελεσματικά.
weight: 26
url: /el/net/unlocking-annotation-power/add-text-strikeout-annotation/
---

# Προσθήκη σχολιασμού Strikeout κειμένου στο έγγραφο

## Εισαγωγή
Σε αυτό το σεμινάριο, θα διερευνήσουμε πώς να προσθέσετε έναν σχολιασμό διαγραφής κειμένου σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Αυτή η βιβλιοθήκη παρέχει ισχυρά εργαλεία για τον σχολιασμό διαφόρων τύπων εγγράφων, τη βελτίωση της συνεργασίας και των διαδικασιών αναθεώρησης εγγράφων.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:
1.  GroupDocs.Annotation για .NET: Εγκαταστήστε τη βιβλιοθήκη. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.groupdocs.com/annotation/net/).
2. Περιβάλλον ανάπτυξης: Ρυθμίστε ένα κατάλληλο περιβάλλον ανάπτυξης για την ανάπτυξη .NET.
3. Έγγραφο: Έχετε ένα έγγραφο έτοιμο για σχολιασμό, όπως ένα αρχείο PDF.

## Εισαγωγή χώρων ονομάτων
Αρχικά, εισαγάγετε τους απαραίτητους χώρους ονομάτων για πρόσβαση στις λειτουργίες του GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Τώρα, ας αναλύσουμε τη διαδικασία προσθήκης ενός σχολιασμού διαγραφής κειμένου σε πολλά βήματα:
## Βήμα 1: Καθορίστε τη διαδρομή εξόδου
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Εδώ, ορίζουμε τη διαδρομή εξόδου όπου θα αποθηκευτεί το σχολιασμένο έγγραφο.
## Βήμα 2: Εκκίνηση του Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Αρχικοποιήστε το αντικείμενο Annotator παρέχοντας τη διαδρομή προς το έγγραφο εισόδου (αρχείο PDF σε αυτήν την περίπτωση).
## Βήμα 3: Δημιουργήστε σχολιασμό Strikeout
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
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
Δημιουργήστε ένα αντικείμενο StrikeoutAnnotation με επιθυμητές ιδιότητες όπως μήνυμα, αδιαφάνεια, αριθμό σελίδας, χρώμα φόντου, σημεία (συντεταγμένες) και απαντήσεις.
## Βήμα 4: Προσθήκη σχολιασμού
```csharp
annotator.Add(strikeout);
```
Προσθέστε τον σχολιασμό διαγραφής που δημιουργήθηκε στο έγγραφο.
## Βήμα 5: Αποθήκευση εγγράφου
```csharp
annotator.Save(outputPath);
```
Αποθηκεύστε το σχολιασμένο έγγραφο στην καθορισμένη διαδρομή εξόδου.

## συμπέρασμα
Σε αυτό το σεμινάριο, μάθαμε πώς να προσθέτουμε έναν σχολιασμό διαγραφής κειμένου σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Αυτή η ισχυρή βιβλιοθήκη επιτρέπει τον αποτελεσματικό σχολιασμό εγγράφων, ενισχύοντας τη συνεργασία και τις διαδικασίες αναθεώρησης εγγράφων.
## Συχνές ερωτήσεις
### Είναι το GroupDocs.Annotation συμβατό με διάφορες μορφές εγγράφων;
Ναι, το GroupDocs.Annotation υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, όπως PDF, Word, Excel, PowerPoint και άλλα.
### Μπορώ να προσαρμόσω την εμφάνιση των σχολιασμών;
Αναμφίβολα, μπορείτε να προσαρμόσετε τις ιδιότητες σχολιασμού, όπως το χρώμα, την αδιαφάνεια, το μέγεθος γραμματοσειράς και άλλα σύμφωνα με τις απαιτήσεις σας.
### Το GroupDocs.Annotation παρέχει δυνατότητες συνεργασίας;
Ναι, το GroupDocs.Annotation διευκολύνει τη συνεργασία επιτρέποντας στους χρήστες να προσθέτουν σχόλια, απαντήσεις και σχολιασμούς σε έγγραφα.
### Υπάρχει δωρεάν δοκιμή διαθέσιμη;
 Ναι, μπορείτε να επωφεληθείτε από μια δωρεάν δοκιμή από[εδώ](https://releases.groupdocs.com/).
### Πού μπορώ να λάβω υποστήριξη για το GroupDocs.Annotation;
 Μπορείτε να λάβετε υποστήριξη από το[Φόρουμ GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation/10).