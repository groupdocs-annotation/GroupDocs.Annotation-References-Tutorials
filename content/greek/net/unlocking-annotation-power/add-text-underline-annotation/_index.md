---
"description": "Μάθετε πώς να προσθέτετε υπογραμμισμένες σημειώσεις κειμένου σε έγγραφα χρησιμοποιώντας το GroupDocs.Annotation για .NET. Βελτιώστε τη συνεργασία και την επικοινωνία χωρίς κόπο."
"linktitle": "Προσθήκη σχολίου υπογράμμισης κειμένου σε έγγραφο"
"second_title": "API .NET του GroupDocs.Annotation"
"title": "Προσθήκη σχολίου υπογράμμισης κειμένου σε έγγραφο"
"url": "/el/net/unlocking-annotation-power/add-text-underline-annotation/"
"weight": 27
---

# Προσθήκη σχολίου υπογράμμισης κειμένου σε έγγραφο

## Εισαγωγή
Σε αυτό το σεμινάριο, θα περιηγηθούμε στη διαδικασία προσθήκης μιας σχολίασης υπογράμμισης κειμένου σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Οι σχολιασμοί υπογράμμισης κειμένου μπορούν να είναι χρήσιμοι για την έμφαση σε συγκεκριμένα μέρη ενός εγγράφου, όπως σημαντικά αποσπάσματα ή βασικά σημεία.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε εγκαταστήσει τις ακόλουθες προϋποθέσεις:
1. GroupDocs.Annotation για .NET: Λήψη και εγκατάσταση του GroupDocs.Annotation για .NET από [εδώ](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Βεβαιωθείτε ότι έχετε εγκαταστήσει το .NET Framework στο σύστημά σας.

## Εισαγωγή χώρων ονομάτων
Αρχικά, ας εισαγάγουμε τους απαραίτητους χώρους ονομάτων στο έργο μας:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Τώρα, ας αναλύσουμε το παράδειγμα σε πολλά βήματα:
## Βήμα 1: Ορισμός διαδρομής εξόδου
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Σε αυτό το βήμα, ορίζουμε τη διαδρομή εξόδου όπου θα αποθηκευτεί το σχολιασμένο έγγραφο.
## Βήμα 2: Αρχικοποίηση σχολιαστή
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Εδώ, αρχικοποιούμε μια παρουσία του `Annotator` κλάση παρέχοντας τη διαδρομή του εγγράφου εισόδου.
## Βήμα 3: Δημιουργία υπογραμμισμένης σχολίασης
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // Υποστηρίζονται μόνο έγγραφα Word και PDF
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
Αυτό το βήμα περιλαμβάνει τη δημιουργία ενός `UnderlineAnnotation` αντικείμενο με διάφορες ιδιότητες όπως χρώμα γραμματοσειράς, μήνυμα, αδιαφάνεια, αριθμό σελίδας, χρώμα φόντου, χρώμα υπογράμμισης, σημεία και απαντήσεις.
## Βήμα 4: Προσθήκη σχολίου στο έγγραφο
```csharp
annotator.Add(underline);
```
Εδώ, προσθέτουμε την υπογραμμισμένη σχολίαση στο έγγραφο.
## Βήμα 5: Αποθήκευση σχολιασμένου εγγράφου
```csharp
annotator.Save(outputPath);
```
Τέλος, αποθηκεύουμε το σχολιασμένο έγγραφο στην καθορισμένη διαδρομή εξόδου.

## Σύναψη
Σε αυτό το σεμινάριο, μάθαμε πώς να προσθέτουμε μια υπογράμμιση κειμένου σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Αυτή η ισχυρή βιβλιοθήκη παρέχει διάφορες επιλογές σχολιασμού για την ενίσχυση της συνεργασίας και της επικοινωνίας στα έγγραφα.
## Συχνές ερωτήσεις
### Μπορώ να προσαρμόσω την εμφάνιση της υπογραμμισμένης σχολίασης;
Ναι, μπορείτε να προσαρμόσετε ιδιότητες όπως το χρώμα, την αδιαφάνεια και τη θέση σύμφωνα με τις απαιτήσεις σας.
### Είναι το GroupDocs.Annotation συμβατό με διαφορετικές μορφές εγγράφων;
Ναι, το GroupDocs.Annotation υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, συμπεριλαμβανομένων των Word και PDF.
### Μπορώ να προσθέσω πολλαπλές σχολιασμοί σε ένα μόνο έγγραφο;
Απολύτως, το GroupDocs.Annotation σάς επιτρέπει να προσθέσετε πολλαπλές σχολιασμοί διαφορετικών τύπων σε ένα έγγραφο.
### Υπάρχει διαθέσιμη δωρεάν δοκιμαστική έκδοση για το GroupDocs.Annotation;
Ναι, μπορείτε να αποκτήσετε πρόσβαση στη δωρεάν δοκιμαστική έκδοση από [εδώ](https://releases.groupdocs.com/).
### Πού μπορώ να λάβω υποστήριξη για το GroupDocs.Annotation;
Μπορείτε να λάβετε υποστήριξη από το φόρουμ της κοινότητας GroupDocs.Annotation [εδώ](https://forum.groupdocs.com/c/annotation/10).