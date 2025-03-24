---
title: Προσθήκη σχολιασμού αντικατάστασης κειμένου στο έγγραφο
linktitle: Προσθήκη σχολιασμού αντικατάστασης κειμένου στο έγγραφο
second_title: GroupDocs.Annotation .NET API
description: Μάθετε πώς να προσθέτετε σχολιασμούς αντικατάστασης κειμένου στα έγγραφά σας .NET χωρίς κόπο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Βελτιώστε τις δυνατότητες χειρισμού εγγράφων σας.
weight: 24
url: /el/net/unlocking-annotation-power/add-text-replacement-annotation/
---
## Εισαγωγή
Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στη διαδικασία προσθήκης σχολιασμού αντικατάστασης κειμένου στα έγγραφά σας χρησιμοποιώντας το GroupDocs.Annotation για .NET. Αυτή η ισχυρή βιβλιοθήκη επιτρέπει στους προγραμματιστές να χειρίζονται και να σχολιάζουν διάφορους τύπους εγγράφων μέσω προγραμματισμού. Μέχρι το τέλος αυτού του σεμιναρίου, θα έχετε τη γνώση για την απρόσκοπτη ενσωμάτωση σχολιασμών αντικατάστασης κειμένου στις εφαρμογές σας .NET.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε εγκαταστήσει τις ακόλουθες προϋποθέσεις:
### 1. Εγκαταστάθηκε το .NET Framework
Βεβαιωθείτε ότι έχετε εγκαταστήσει το .NET Framework στο μηχάνημα ανάπτυξης. Μπορείτε να το κατεβάσετε από τον ιστότοπο της Microsoft.
### 2. GroupDocs.Annotation για .NET Library
 Κατεβάστε και εγκαταστήστε τη βιβλιοθήκη GroupDocs.Annotation για .NET από το[δικτυακός τόπος](https://releases.groupdocs.com/annotation/net/). Αυτή η βιβλιοθήκη παρέχει τα απαραίτητα εργαλεία και λειτουργίες για την εργασία με σχολιασμούς σε διάφορες μορφές εγγράφων.
### 3. Ρύθμιση περιβάλλοντος ανάπτυξης
Ρυθμίστε το περιβάλλον ανάπτυξης που προτιμάτε, όπως το Visual Studio, για τη δημιουργία και εκτέλεση εφαρμογών .NET.

## Εισαγωγή χώρων ονομάτων
Πριν προχωρήσουμε στο τμήμα κωδικοποίησης, ας εισαγάγουμε τους απαραίτητους χώρους ονομάτων που απαιτούνται για την εργασία με το GroupDocs.Annotation για .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## Βήμα 1: Καθορίστε τη διαδρομή εξόδου
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Εδώ, ορίζουμε τη διαδρομή εξόδου όπου θα αποθηκευτεί το σχολιασμένο έγγραφο.
## Βήμα 2: Εκκίνηση του Annotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ο κωδικός σχολιασμού θα τοποθετηθεί εδώ
}
```
Αρχικοποιούμε το αντικείμενο Annotator καθορίζοντας το έγγραφο εισόδου ("input.pdf") μέσα σε ένα μπλοκ χρήσης για να διασφαλίσουμε τη σωστή διάθεση των πόρων.
## Βήμα 3: Δημιουργία σχολιασμού αντικατάστασης
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
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
    },
    TextToReplace = "replaced text"
};
```
Εδώ, δημιουργούμε ένα αντικείμενο ReplacementAnnotation με διάφορες ιδιότητες όπως ημερομηνία δημιουργίας, χρώμα γραμματοσειράς, μήνυμα, αδιαφάνεια, αριθμός σελίδας, χρώμα φόντου, σημεία (συντεταγμένες), απαντήσεις (σχόλια) και το κείμενο προς αντικατάσταση.
## Βήμα 4: Προσθήκη σχολιασμού
```csharp
annotator.Add(replacement);
```
Προσθέτουμε τον σχολιασμό αντικατάστασης που δημιουργήθηκε στον σχολιαστή.
## Βήμα 5: Αποθήκευση εγγράφου
```csharp
annotator.Save(outputPath);
```
Τέλος, αποθηκεύουμε το σχολιασμένο έγγραφο στην καθορισμένη διαδρομή εξόδου.
## Βήμα 6: Εμφάνιση μηνύματος επιτυχίας
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Εμφανίζεται ένα μήνυμα επιτυχίας που υποδεικνύει ότι το έγγραφο αποθηκεύτηκε με επιτυχία.

## συμπέρασμα
Σε αυτό το σεμινάριο, καλύψαμε τη διαδικασία προσθήκης σχολιασμών αντικατάστασης κειμένου σε έγγραφα χρησιμοποιώντας GroupDocs.Annotation για .NET. Ακολουθώντας τον οδηγό βήμα προς βήμα και κατανοώντας τις προϋποθέσεις, μπορείτε εύκολα να ενσωματώσετε αυτήν τη λειτουργία στις εφαρμογές σας .NET.
## Συχνές ερωτήσεις
### Μπορώ να σχολιάσω έγγραφα διαφορετικών μορφών χρησιμοποιώντας το GroupDocs.Annotation για .NET;
Ναι, το GroupDocs.Annotation για .NET υποστηρίζει τον σχολιασμό διαφόρων μορφών εγγράφων όπως PDF, DOCX, PPTX, XLSX και άλλα.
### Είναι το GroupDocs.Annotation για .NET κατάλληλο τόσο για επιτραπέζιους υπολογιστές όσο και για εφαρμογές web;
Ναι, το GroupDocs.Annotation για .NET μπορεί να χρησιμοποιηθεί τόσο σε επιτραπέζιους υπολογιστές όσο και σε εφαρμογές web, παρέχοντας ευελιξία στους προγραμματιστές.
### Μπορώ να προσαρμόσω την εμφάνιση των σχολιασμών που προστέθηκαν χρησιμοποιώντας το GroupDocs.Annotation για .NET;
Οπωσδήποτε, μπορείτε να προσαρμόσετε την εμφάνιση των σχολιασμών τροποποιώντας ιδιότητες όπως χρώμα, αδιαφάνεια, γραμματοσειρά κ.λπ.
### Το GroupDocs.Annotation για .NET προσφέρει υποστήριξη για συνεργατικές λειτουργίες σχολιασμού;
Ναι, το GroupDocs.Annotation για .NET παρέχει δυνατότητες για συνεργατικό σχολιασμό, επιτρέποντας σε πολλούς χρήστες να σχολιάζουν έγγραφα ταυτόχρονα.
### Υπάρχει διαθέσιμη δωρεάν δοκιμή για το GroupDocs.Annotation για το .NET;
Ναι, μπορείτε να επωφεληθείτε από μια δωρεάν δοκιμή του GroupDocs.Annotation για .NET από το[δικτυακός τόπος](https://releases.groupdocs.com/).