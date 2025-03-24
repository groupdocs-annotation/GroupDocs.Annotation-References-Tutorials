---
title: Προσθήκη Κειμένου Squiggly Annotation στο έγγραφο
linktitle: Προσθήκη Κειμένου Squiggly Annotation στο έγγραφο
second_title: GroupDocs.Annotation .NET API
description: Μάθετε πώς να προσθέτετε αβίαστα σχολιασμούς κειμένου σε έγγραφα χρησιμοποιώντας το Groupdocs.Annotation για .NET. Βελτιώστε τη συνεργασία και τις διαδικασίες αναθεώρησης εγγράφων.
weight: 25
url: /el/net/unlocking-annotation-power/add-text-squiggly-annotation/
---
## Εισαγωγή

Το Groupdocs.Annotation για .NET είναι μια ευέλικτη βιβλιοθήκη που επιτρέπει στους προγραμματιστές να ενσωματώνουν ισχυρές δυνατότητες σχολιασμού στις εφαρμογές τους .NET χωρίς κόπο. Είτε εργάζεστε με αρχεία PDF, έγγραφα Word ή άλλες δημοφιλείς μορφές αρχείων, το Groupdocs.Annotation παρέχει μια απρόσκοπτη λύση για τον σχολιασμό και τη βελτίωση της συνεργασίας εγγράφων.

## Προαπαιτούμενα

Πριν βουτήξετε στο σεμινάριο, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:

## Εισαγωγή χώρων ονομάτων

Βεβαιωθείτε ότι έχετε εισαγάγει τους απαραίτητους χώρους ονομάτων για πρόσβαση στις λειτουργίες που παρέχονται από το Groupdocs.Annotation για .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Τώρα που έχουμε καλύψει τις προϋποθέσεις, ας αναλύσουμε τη διαδικασία προσθήκης σχολιασμών κειμένου σε πολλά βήματα.

## Βήμα 1: Καθορίστε τη διαδρομή εξόδου

Καθορίστε τη διαδρομή όπου θα αποθηκευτεί το σχολιασμένο έγγραφο.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Βήμα 2: Εκκίνηση του Annotator

Εκκινήστε το αντικείμενο Annotator παρέχοντας τη διαδρομή του εγγράφου εισόδου.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ο κώδικας σχολιασμού πηγαίνει εδώ
}
```

## Βήμα 3: Δημιουργήστε Squiggly Annotation

Δημιουργήστε ένα αντικείμενο SquigglyAnnotation και καθορίστε τις ιδιότητές του.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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

Προσθέστε το δημιουργημένο squiggly σχολιασμό στο έγγραφο.

```csharp
annotator.Add(squiggly);
```

## Βήμα 5: Αποθήκευση εγγράφου

Αποθηκεύστε το σχολιασμένο έγγραφο στην καθορισμένη διαδρομή εξόδου.

```csharp
annotator.Save(outputPath);
```

## Βήμα 6: Επιβεβαίωση εμφάνισης

Εμφανίστε ένα μήνυμα που επιβεβαιώνει την επιτυχή αποθήκευση του σχολιασμένου εγγράφου.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## συμπέρασμα

Εν κατακλείδι, το Groupdocs.Annotation για .NET παρέχει στους προγραμματιστές ένα ισχυρό σύνολο εργαλείων για την απρόσκοπτη ενσωμάτωση λειτουργιών σχολιασμού εγγράφων στις εφαρμογές τους .NET. Ακολουθώντας αυτόν τον οδηγό βήμα προς βήμα, μπορείτε να προσθέσετε αβίαστα σχολιασμούς κειμένου στα έγγραφά σας, βελτιώνοντας τη συνεργασία και τις διαδικασίες ελέγχου εγγράφων.

## Συχνές ερωτήσεις

### Ε: Μπορεί το Groupdocs.Annotation να υποστηρίξει σχολιασμό σε διάφορες μορφές αρχείων;

Α: Ναι, το Groupdocs.Annotation υποστηρίζει σχολιασμούς σε ένα ευρύ φάσμα μορφών αρχείων, συμπεριλαμβανομένων αρχείων PDF, εγγράφων Word, φύλλων Excel και άλλων.

### Ε: Είναι το Groupdocs.Annotation συμβατό τόσο με εφαρμογές επιτραπέζιου υπολογιστή όσο και με εφαρμογές web;

Α: Απολύτως! Το Groupdocs.Annotation μπορεί να ενσωματωθεί απρόσκοπτα τόσο σε επιτραπέζιους υπολογιστές όσο και σε εφαρμογές web, προσφέροντας ευελιξία και ευελιξία.

### Ε: Υπάρχουν διαθέσιμες επιλογές αδειοδότησης για το Groupdocs.Annotation;

Α: Ναι, το Groupdocs.Annotation προσφέρει ευέλικτες επιλογές αδειοδότησης προσαρμοσμένες στις ατομικές ή εταιρικές ανάγκες, συμπεριλαμβανομένων των προσωρινών αδειών για δοκιμαστικούς σκοπούς.

### Ε: Μπορούν οι σχολιασμοί που δημιουργούνται με χρήση του Groupdocs.Annotation να προσαρμοστούν;

Α: Σίγουρα! Το Groupdocs.Annotation παρέχει εκτενείς επιλογές προσαρμογής για σχολιασμούς, επιτρέποντας στους προγραμματιστές να προσαρμόσουν τους σχολιασμούς στις συγκεκριμένες απαιτήσεις τους.

### Ε: Το Groupdocs.Annotation προσφέρει υποστήριξη και τεκμηρίωση για προγραμματιστές;

Α: Πράγματι! Το Groupdocs.Annotation παρέχει ολοκληρωμένη τεκμηρίωση και ειδικά φόρουμ υποστήριξης για να βοηθήσει τους προγραμματιστές να χρησιμοποιήσουν αποτελεσματικά τις δυνατότητές του.