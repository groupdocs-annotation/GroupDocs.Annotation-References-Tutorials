---
"description": "Μάθετε πώς να προσθέτετε σχολιασμούς διαγραφής κειμένου σε έγγραφα χρησιμοποιώντας το GroupDocs.Annotation για .NET. Βελτιώστε αποτελεσματικά τη συνεργασία και τις διαδικασίες αναθεώρησης εγγράφων."
"linktitle": "Προσθήκη σχολίου διαγραφής κειμένου σε έγγραφο"
"second_title": "API .NET του GroupDocs.Annotation"
"title": "Προσθήκη σχολίου διαγραφής κειμένου σε έγγραφο"
"url": "/el/net/unlocking-annotation-power/add-text-strikeout-annotation/"
"weight": 26
---

# Προσθήκη σχολίου διαγραφής κειμένου σε έγγραφο

## Εισαγωγή
Σε αυτό το σεμινάριο, θα εξερευνήσουμε πώς να προσθέσετε μια σχολίαση διακριτής διαγραφής κειμένου σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Αυτή η βιβλιοθήκη παρέχει ισχυρά εργαλεία για την προσθήκη σχολίων σε διάφορους τύπους εγγράφων, βελτιώνοντας τη συνεργασία και τις διαδικασίες αναθεώρησης εγγράφων.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:
1. GroupDocs.Annotation για .NET: Εγκαταστήστε τη βιβλιοθήκη. Μπορείτε να την κατεβάσετε από [εδώ](https://releases.groupdocs.com/annotation/net/).
2. Περιβάλλον Ανάπτυξης: Δημιουργήστε ένα κατάλληλο περιβάλλον ανάπτυξης για ανάπτυξη .NET.
3. Έγγραφο: Να έχετε ένα έγγραφο έτοιμο για σχολιασμό, όπως ένα αρχείο PDF.

## Εισαγωγή χώρων ονομάτων
Αρχικά, εισαγάγετε τους απαραίτητους χώρους ονομάτων για να αποκτήσετε πρόσβαση στις λειτουργίες του GroupDocs.Annotation:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Τώρα, ας αναλύσουμε τη διαδικασία προσθήκης μιας σχολίασης διαγραφής κειμένου σε πολλά βήματα:
## Βήμα 1: Ορισμός διαδρομής εξόδου
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Εδώ, ορίζουμε τη διαδρομή εξόδου όπου θα αποθηκευτεί το σχολιασμένο έγγραφο.
## Βήμα 2: Αρχικοποίηση σχολιαστή
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Αρχικοποιήστε το αντικείμενο Annotator παρέχοντας τη διαδρομή προς το έγγραφο εισόδου (αρχείο PDF σε αυτήν την περίπτωση).
## Βήμα 3: Δημιουργία σχολίου διαγραφής
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
Δημιουργήστε ένα αντικείμενο StrikeoutAnnotation με τις επιθυμητές ιδιότητες όπως μήνυμα, αδιαφάνεια, αριθμό σελίδας, χρώμα φόντου, σημεία (συντεταγμένες) και απαντήσεις.
## Βήμα 4: Προσθήκη σχολίου
```csharp
annotator.Add(strikeout);
```
Προσθέστε τη δημιουργημένη σχολίαση διαγραφής στο έγγραφο.
## Βήμα 5: Αποθήκευση εγγράφου
```csharp
annotator.Save(outputPath);
```
Αποθηκεύστε το σχολιασμένο έγγραφο στην καθορισμένη διαδρομή εξόδου.

## Σύναψη
Σε αυτό το σεμινάριο, μάθαμε πώς να προσθέτουμε μια σχολίαση διακριτής διαγραφής κειμένου σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Αυτή η ισχυρή βιβλιοθήκη επιτρέπει την αποτελεσματική σχολίαση εγγράφων, ενισχύοντας τη συνεργασία και τις διαδικασίες αναθεώρησης εγγράφων.
## Συχνές ερωτήσεις
### Είναι το GroupDocs.Annotation συμβατό με διάφορες μορφές εγγράφων;
Ναι, το GroupDocs.Annotation υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, όπως PDF, Word, Excel, PowerPoint και άλλα.
### Μπορώ να προσαρμόσω την εμφάνιση των σχολιασμών;
Απολύτως, μπορείτε να προσαρμόσετε τις ιδιότητες σχολιασμού όπως το χρώμα, την αδιαφάνεια, το μέγεθος γραμματοσειράς και άλλα ανάλογα με τις απαιτήσεις σας.
### Παρέχει το GroupDocs.Annotation λειτουργίες συνεργασίας;
Ναι, το GroupDocs.Annotation διευκολύνει τη συνεργασία επιτρέποντας στους χρήστες να προσθέτουν σχόλια, απαντήσεις και σχολιασμούς σε έγγραφα.
### Υπάρχει διαθέσιμη δωρεάν δοκιμαστική περίοδος;
Ναι, μπορείτε να επωφεληθείτε από μια δωρεάν δοκιμή από [εδώ](https://releases.groupdocs.com/).
### Πού μπορώ να λάβω υποστήριξη για το GroupDocs.Annotation;
Μπορείτε να λάβετε υποστήριξη από το [Φόρουμ GroupDocs.Annotation](https://forum.groupdocs.com/c/annotation/10).