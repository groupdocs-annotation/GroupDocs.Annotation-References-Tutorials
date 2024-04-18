---
title: Προσθήκη σχολιασμού επισήμανσης κειμένου στο έγγραφο
linktitle: Προσθήκη σχολιασμού επισήμανσης κειμένου στο έγγραφο
second_title: GroupDocs.Annotation .NET API
description: Μάθετε πώς να προσθέτετε σχολιασμούς επισήμανσης κειμένου σε έγγραφα χρησιμοποιώντας το GroupDocs.Annotation για .NET. Βελτιώστε τη συνεργασία και την παραγωγικότητα με αυτό το ολοκληρωμένο.
type: docs
weight: 22
url: /el/net/unlocking-annotation-power/add-text-highlight-annotation/
---
## Εισαγωγή
Στον τομέα της διαχείρισης και της συνεργασίας εγγράφων, το GroupDocs.Annotation για .NET αναδεικνύεται ως μια ισχυρή λύση, δίνοντας τη δυνατότητα στους προγραμματιστές να ενσωματώνουν απρόσκοπτα τους σχολιασμούς με τονισμό κειμένου στις εφαρμογές τους. Αυτό το σεμινάριο χρησιμεύει ως ένας περιεκτικός οδηγός για την προσθήκη σχολιασμών επισήμανσης κειμένου σε έγγραφα χρησιμοποιώντας το GroupDocs.Annotation για .NET. Μέσα από οδηγίες βήμα προς βήμα και λεπτομερείς εξηγήσεις, θα αποκτήσετε επάρκεια στην αξιοποίηση των δυνατοτήτων αυτής της ισχυρής βιβλιοθήκης.
## Προαπαιτούμενα
Πριν εμβαθύνετε στην εφαρμογή των σχολιασμών επισήμανσης κειμένου, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:
1. Environment Setup: Έχετε ένα κατάλληλο περιβάλλον ανάπτυξης διαμορφωμένο για ανάπτυξη .NET.
2.  Εγκατάσταση του GroupDocs.Annotation για .NET: Κατεβάστε και εγκαταστήστε το GroupDocs.Annotation για .NET από το παρεχόμενο[σύνδεσμος λήψης](https://releases.groupdocs.com/annotation/net/).
3. Εξοικείωση με την C#: Βασική κατανόηση της γλώσσας προγραμματισμού C#.
4. Έγγραφο προς σχολιασμό: Προετοιμάστε ένα έγγραφο (π.χ. PDF) που σκοπεύετε να σχολιάσετε.

## Εισαγωγή χώρων ονομάτων
Για να ξεκινήσετε, εισαγάγετε τους απαραίτητους χώρους ονομάτων στον κώδικα C# για να χρησιμοποιήσετε τις λειτουργίες του GroupDocs.Annotation για .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Τώρα, ας αναλύσουμε τη διαδικασία προσθήκης σχολιασμών επισήμανσης κειμένου σε πολλά βήματα:
## Βήμα 1: Καθορίστε τη διαδρομή εξόδου
Καθορίστε τη διαδρομή εξόδου όπου θα αποθηκευτεί το σχολιασμένο έγγραφο:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Βήμα 2: Εκκίνηση του Annotator
 Δημιουργήστε ένα παράδειγμα του`Annotator` class, μεταβιβάζοντας το όνομα αρχείου του εγγράφου ως παράμετρο:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Βήμα 3: Δημιουργήστε σχολιασμό επισήμανσης
 Στιγμιότυπο α`HighlightAnnotation` αντικείμενο και ρυθμίστε τις ιδιότητές του:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
## Βήμα 4: Προσθήκη σχολιασμού
Προσθέστε τον σχολιασμό επισήμανσης που δημιουργήθηκε στο έγγραφο:
```csharp
annotator.Add(highlight);
```
## Βήμα 5: Αποθήκευση σχολιασμένου εγγράφου
Αποθηκεύστε το σχολιασμένο έγγραφο στην καθορισμένη διαδρομή εξόδου:
```csharp
annotator.Save(outputPath);
```

## συμπέρασμα
Συμπερασματικά, το GroupDocs.Annotation για .NET προσφέρει μια βελτιωμένη προσέγγιση για την ενσωμάτωση σχολιασμών επισήμανσης κειμένου σε έγγραφα. Ακολουθώντας τα βήματα που περιγράφονται σε αυτό το σεμινάριο, οι προγραμματιστές μπορούν να βελτιώσουν απρόσκοπτα τη συνεργασία και την παραγωγικότητα των εγγράφων στις εφαρμογές τους.
## Συχνές ερωτήσεις
### Είναι το GroupDocs.Annotation για .NET συμβατό με όλες τις μορφές εγγράφων;
Το GroupDocs.Annotation για .NET υποστηρίζει διάφορες μορφές εγγράφων, συμπεριλαμβανομένων των PDF, Word, Excel και άλλων. Ανατρέξτε στην τεκμηρίωση για την πλήρη λίστα.
### Μπορούν οι σχολιασμοί να προσαρμοστούν σύμφωνα με συγκεκριμένες απαιτήσεις;
Ναι, οι προγραμματιστές έχουν τον πλήρη έλεγχο των ιδιοτήτων και της εμφάνισης των σχολιασμών, επιτρέποντας την προσαρμογή για την κάλυψη διαφορετικών αναγκών.
### Υπάρχει διαθέσιμη δωρεάν δοκιμή για το GroupDocs.Annotation για το .NET;
 Ναι, μπορείτε να εξερευνήσετε τις δυνατότητες του GroupDocs.Annotation για .NET αποκτώντας πρόσβαση στη δωρεάν δοκιμή από το παρεχόμενο[Σύνδεσμος](https://releases.groupdocs.com/).
### Πώς μπορώ να λάβω υποστήριξη για τυχόν ζητήματα ή ερωτήματα που σχετίζονται με το GroupDocs.Annotation για .NET;
 Για υποστήριξη και βοήθεια, μπορείτε να επισκεφτείτε το φόρουμ GroupDocs.Annotation[εδώ](https://forum.groupdocs.com/c/annotation/10).
### Ποιες επιλογές αδειοδότησης είναι διαθέσιμες για το GroupDocs.Annotation για .NET;
 Το GroupDocs.Annotation για .NET προσφέρει διάφορες επιλογές αδειοδότησης, συμπεριλαμβανομένων προσωρινών αδειών για δοκιμαστικούς σκοπούς και εμπορικών αδειών για περιβάλλοντα παραγωγής. Επισκεφθείτε τη σελίδα αγοράς[εδώ](https://purchase.groupdocs.com/buy) Για περισσότερες πληροφορίες.