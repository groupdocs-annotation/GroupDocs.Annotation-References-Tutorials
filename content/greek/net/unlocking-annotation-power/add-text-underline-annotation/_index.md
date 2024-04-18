---
title: Προσθήκη σχολιασμού υπογράμμισης κειμένου στο έγγραφο
linktitle: Προσθήκη σχολιασμού υπογράμμισης κειμένου στο έγγραφο
second_title: GroupDocs.Annotation .NET API
description: Μάθετε πώς να προσθέτετε σχολιασμούς με υπογράμμιση κειμένου σε έγγραφα χρησιμοποιώντας το GroupDocs.Annotation για .NET. Ενισχύστε τη συνεργασία και την επικοινωνία χωρίς κόπο.
type: docs
weight: 27
url: /el/net/unlocking-annotation-power/add-text-underline-annotation/
---
## Εισαγωγή
Σε αυτό το σεμινάριο, θα ακολουθήσουμε τη διαδικασία προσθήκης ενός σχολιασμού υπογράμμισης κειμένου σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Οι σχολιασμοί με υπογράμμιση κειμένου μπορεί να είναι χρήσιμοι για την έμφαση σε συγκεκριμένα μέρη ενός εγγράφου, όπως σημαντικά αποσπάσματα ή βασικά σημεία.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε εγκαταστήσει τις ακόλουθες προϋποθέσεις:
1.  GroupDocs.Annotation για .NET: Λήψη και εγκατάσταση του GroupDocs.Annotation για .NET από[εδώ](https://releases.groupdocs.com/annotation/net/).
2. .NET Framework: Βεβαιωθείτε ότι έχετε εγκαταστήσει το .NET Framework στο σύστημά σας.

## Εισαγωγή χώρων ονομάτων
Αρχικά, ας εισάγουμε τους απαραίτητους χώρους ονομάτων στο έργο μας:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Τώρα, ας αναλύσουμε το παράδειγμα σε πολλά βήματα:
## Βήμα 1: Καθορίστε τη διαδρομή εξόδου
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Σε αυτό το βήμα, ορίζουμε τη διαδρομή εξόδου όπου θα αποθηκευτεί το σχολιασμένο έγγραφο.
## Βήμα 2: Εκκίνηση του Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Εδώ, αρχικοποιούμε ένα στιγμιότυπο του`Annotator` κλάση παρέχοντας τη διαδρομή του εγγράφου εισόδου.
## Βήμα 3: Δημιουργήστε σχολιασμό υπογράμμισης
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // έργα υποστηρίζονται μόνο έγγραφα Word και PDF
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
 Αυτό το βήμα περιλαμβάνει τη δημιουργία ενός`UnderlineAnnotation`αντικείμενο με διάφορες ιδιότητες όπως χρώμα γραμματοσειράς, μήνυμα, αδιαφάνεια, αριθμός σελίδας, χρώμα φόντου, χρώμα υπογράμμισης, σημεία και απαντήσεις.
## Βήμα 4: Προσθήκη σχολιασμού στο έγγραφο
```csharp
annotator.Add(underline);
```
Εδώ, προσθέτουμε τον υπογραμμισμένο σχολιασμό στο έγγραφο.
## Βήμα 5: Αποθήκευση σχολιασμένου εγγράφου
```csharp
annotator.Save(outputPath);
```
Τέλος, αποθηκεύουμε το σχολιασμένο έγγραφο στην καθορισμένη διαδρομή εξόδου.

## συμπέρασμα
Σε αυτό το σεμινάριο, μάθαμε πώς να προσθέτουμε έναν σχολιασμό υπογράμμισης κειμένου σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Αυτή η ισχυρή βιβλιοθήκη παρέχει διάφορες επιλογές σχολιασμού για τη βελτίωση της συνεργασίας και της επικοινωνίας εγγράφων.
## Συχνές ερωτήσεις
### Μπορώ να προσαρμόσω την εμφάνιση του υπογραμμισμένου σχολιασμού;
Ναι, μπορείτε να προσαρμόσετε ιδιότητες όπως το χρώμα, την αδιαφάνεια και τη θέση σύμφωνα με τις απαιτήσεις σας.
### Είναι το GroupDocs.Annotation συμβατό με διαφορετικές μορφές εγγράφων;
Ναι, το GroupDocs.Annotation υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, συμπεριλαμβανομένων των Word και PDF.
### Μπορώ να προσθέσω πολλαπλούς σχολιασμούς σε ένα μόνο έγγραφο;
Οπωσδήποτε, το GroupDocs.Annotation σάς επιτρέπει να προσθέτετε πολλαπλούς σχολιασμούς διαφορετικών τύπων σε ένα έγγραφο.
### Υπάρχει διαθέσιμη δωρεάν δοκιμή για το GroupDocs.Annotation;
 Ναι, μπορείτε να έχετε πρόσβαση στη δωρεάν δοκιμαστική έκδοση από[εδώ](https://releases.groupdocs.com/).
### Πού μπορώ να λάβω υποστήριξη για το GroupDocs.Annotation;
 Μπορείτε να λάβετε υποστήριξη από το φόρουμ της κοινότητας GroupDocs.Annotation[εδώ](https://forum.groupdocs.com/c/annotation/10).