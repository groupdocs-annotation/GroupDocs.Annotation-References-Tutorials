---
title: Προσθήκη σχολιασμού απόστασης στο έγγραφο
linktitle: Προσθήκη σχολιασμού απόστασης στο έγγραφο
second_title: GroupDocs.Annotation .NET API
description: Μάθετε πώς να προσθέτετε σχολιασμούς απόστασης σε έγγραφα χρησιμοποιώντας το GroupDocs.Annotation για .NET. Ενισχύστε τη συνεργασία και την επικοινωνία χωρίς κόπο.
weight: 12
url: /el/net/unlocking-annotation-power/add-distance-annotation/
---

# Προσθήκη σχολιασμού απόστασης στο έγγραφο

## Εισαγωγή
Σε αυτό το σεμινάριο, θα μάθετε πώς να προσθέτετε έναν σχολιασμό απόστασης σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Ακολουθήστε αυτά τα βήματα για να ολοκληρώσετε την εργασία:
## Προαπαιτούμενα

Βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις πριν προχωρήσετε:

-  GroupDocs.Annotation για .NET Library: Κατεβάστε και εγκαταστήστε τη βιβλιοθήκη GroupDocs.Annotation για .NET από[αυτός ο σύνδεσμος](https://releases.groupdocs.com/annotation/net/).
- Έγγραφο προς σχολιασμό: Προετοιμάστε το έγγραφο (π.χ. PDF) στο οποίο θέλετε να προσθέσετε τον σχολιασμό απόστασης.
- Περιβάλλον ανάπτυξης: Ρυθμίστε το περιβάλλον ανάπτυξης με το Visual Studio ή οποιοδήποτε άλλο IDE της επιλογής σας.

## Εισαγωγή χώρων ονομάτων

Πριν ξεκινήσετε, φροντίστε να συμπεριλάβετε τους απαραίτητους χώρους ονομάτων στον κώδικά σας. Αυτοί οι χώροι ονομάτων είναι απαραίτητοι για την πρόσβαση στις απαιτούμενες κλάσεις και μεθόδους.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Βήμα 1: Εκκίνηση του Annotator

 Ξεκινήστε αρχικοποιώντας το`Annotator` αντικείμενο με τη διαδρομή προς το έγγραφο που θέλετε να σχολιάσετε.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ο κωδικός σχολιασμού θα πάει εδώ
}
```

## Βήμα 2: Δημιουργήστε σχολιασμό απόστασης

 Τώρα, δημιουργήστε ένα`DistanceAnnotation` αντικείμενο και διαμορφώστε τις ιδιότητές του, όπως διαστάσεις πλαισίου, μήνυμα, αδιαφάνεια, χρώμα στυλό κ.λπ.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
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

## Βήμα 3: Προσθήκη σχολιασμού

 Προσθέστε τον σχολιασμό απόστασης που δημιουργήθηκε στο έγγραφο χρησιμοποιώντας το`Add` μέθοδος του αντικειμένου σχολιαστή.

```csharp
annotator.Add(distance);
```

## Βήμα 4: Αποθήκευση εγγράφου

Αποθηκεύστε το σχολιασμένο έγγραφο στην επιθυμητή θέση στο σύστημά σας.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Βήμα 5: Επιβεβαίωση εμφάνισης

Τέλος, εμφανίστε ένα μήνυμα που επιβεβαιώνει την επιτυχή αποθήκευση του σχολιασμένου εγγράφου.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## συμπέρασμα

Η προσθήκη σχολιασμών απόστασης σε έγγραφα χρησιμοποιώντας το GroupDocs.Annotation για .NET είναι μια απλή διαδικασία. Ακολουθώντας τα βήματα που περιγράφονται σε αυτό το σεμινάριο, μπορείτε να βελτιώσετε τα έγγραφά σας με πολύτιμους σχολιασμούς, διευκολύνοντας την καλύτερη συνεργασία και επικοινωνία.

## Συχνές ερωτήσεις

### Ε: Μπορώ να προσαρμόσω την εμφάνιση του σχολιασμού απόστασης;

Α: Ναι, μπορείτε να προσαρμόσετε διάφορες ιδιότητες όπως χρώμα, αδιαφάνεια, στυλ γραμμής κ.λπ., για να ταιριάζουν στις απαιτήσεις σας.

### Ε: Το GroupDocs.Annotation υποστηρίζει σχολιασμούς σε διαφορετικούς τύπους εγγράφων;

Α: Ναι, το GroupDocs.Annotation υποστηρίζει σχολιασμούς σε ένα ευρύ φάσμα μορφών εγγράφων, όπως PDF, Word, Excel, PowerPoint και άλλα.

### Ε: Υπάρχει διαθέσιμη δωρεάν δοκιμή για το GroupDocs.Annotation;

 Α: Ναι, μπορείτε να αποκτήσετε πρόσβαση σε μια δωρεάν δοκιμή του GroupDocs.Annotation από[αυτός ο σύνδεσμος](https://releases.groupdocs.com/).

### Ε: Πού μπορώ να βρω την τεκμηρίωση για το GroupDocs.Annotation για .NET;

 Α: Μπορείτε να ανατρέξετε στη λεπτομερή διαθέσιμη τεκμηρίωση[εδώ](https://tutorials.groupdocs.com/annotation/net/).

### Ε: Πώς μπορώ να λάβω υποστήριξη ή βοήθεια με το GroupDocs.Annotation;

 Α: Μπορείτε να αναζητήσετε υποστήριξη και βοήθεια από το φόρουμ της κοινότητας GroupDocs.Annotation[εδώ](https://forum.groupdocs.com/c/annotation/10).