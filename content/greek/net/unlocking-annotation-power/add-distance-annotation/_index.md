---
"description": "Μάθετε πώς να προσθέτετε σχολιασμούς απόστασης σε έγγραφα χρησιμοποιώντας το GroupDocs.Annotation για .NET. Βελτιώστε τη συνεργασία και την επικοινωνία χωρίς κόπο."
"linktitle": "Προσθήκη σχολίου απόστασης στο έγγραφο"
"second_title": "API .NET του GroupDocs.Annotation"
"title": "Προσθήκη σχολίου απόστασης στο έγγραφο"
"url": "/el/net/unlocking-annotation-power/add-distance-annotation/"
type: docs
"weight": 12
---

# Προσθήκη σχολίου απόστασης στο έγγραφο

## Εισαγωγή
Σε αυτό το σεμινάριο, θα μάθετε πώς να προσθέσετε μια σχολίαση απόστασης σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Ακολουθήστε τα παρακάτω βήματα για να ολοκληρώσετε την εργασία:
## Προαπαιτούμενα

Βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις πριν προχωρήσετε:

- GroupDocs.Annotation για τη βιβλιοθήκη .NET: Κατεβάστε και εγκαταστήστε τη βιβλιοθήκη GroupDocs.Annotation για .NET από [αυτός ο σύνδεσμος](https://releases.groupdocs.com/annotation/net/).
- Έγγραφο προς σχολιασμό: Προετοιμάστε το έγγραφο (π.χ., PDF) στο οποίο θέλετε να προσθέσετε την σχολίαση απόστασης.
- Περιβάλλον Ανάπτυξης: Ρυθμίστε το περιβάλλον ανάπτυξής σας με το Visual Studio ή οποιοδήποτε άλλο IDE της επιλογής σας.

## Εισαγωγή χώρων ονομάτων

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε συμπεριλάβει τους απαραίτητους χώρους ονομάτων στον κώδικά σας. Αυτοί οι χώροι ονομάτων είναι απαραίτητοι για την πρόσβαση στις απαιτούμενες κλάσεις και μεθόδους.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Βήμα 1: Αρχικοποίηση σχολιαστή

Ξεκινήστε αρχικοποιώντας το `Annotator` αντικείμενο με τη διαδρομή προς το έγγραφο στο οποίο θέλετε να προσθέσετε σχόλια.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ο κώδικας σχολιασμού θα τοποθετηθεί εδώ
}
```

## Βήμα 2: Δημιουργία σχολιασμού απόστασης

Τώρα, δημιουργήστε ένα `DistanceAnnotation` αντικείμενο και να διαμορφώσετε τις ιδιότητές του, όπως διαστάσεις πλαισίου, μήνυμα, αδιαφάνεια, χρώμα πένας κ.λπ.

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

## Βήμα 3: Προσθήκη σχολίου

Προσθέστε την σχολίαση απόστασης που δημιουργήθηκε στο έγγραφο χρησιμοποιώντας το `Add` μέθοδος του αντικειμένου σχολιαστή.

```csharp
annotator.Add(distance);
```

## Βήμα 4: Αποθήκευση εγγράφου

Αποθηκεύστε το σχολιασμένο έγγραφο στην επιθυμητή θέση στο σύστημά σας.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Βήμα 5: Εμφάνιση επιβεβαίωσης

Τέλος, εμφανίστε ένα μήνυμα που επιβεβαιώνει την επιτυχή αποθήκευση του σχολιασμένου εγγράφου.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Σύναψη

Η προσθήκη σχολίων απόστασης σε έγγραφα χρησιμοποιώντας το GroupDocs.Annotation για .NET είναι μια απλή διαδικασία. Ακολουθώντας τα βήματα που περιγράφονται σε αυτό το σεμινάριο, μπορείτε να βελτιώσετε τα έγγραφά σας με πολύτιμες σχολιασμούς, διευκολύνοντας την καλύτερη συνεργασία και επικοινωνία.

## Συχνές ερωτήσεις

### Ε: Μπορώ να προσαρμόσω την εμφάνιση της σχολίασης απόστασης;

Α: Ναι, μπορείτε να προσαρμόσετε διάφορες ιδιότητες όπως χρώμα, αδιαφάνεια, στυλ γραμμής κ.λπ., ώστε να ταιριάζουν στις απαιτήσεις σας.

### Ε: Υποστηρίζει το GroupDocs.Annotation σχολιασμούς σε διαφορετικούς τύπους εγγράφων;

Α: Ναι, το GroupDocs.Annotation υποστηρίζει σχολιασμούς σε ένα ευρύ φάσμα μορφών εγγράφων, όπως PDF, Word, Excel, PowerPoint και άλλα.

### Ε: Υπάρχει διαθέσιμη δωρεάν δοκιμαστική έκδοση για το GroupDocs.Annotation;

Α: Ναι, μπορείτε να αποκτήσετε πρόσβαση σε μια δωρεάν δοκιμαστική έκδοση του GroupDocs.Annotation από [αυτός ο σύνδεσμος](https://releases.groupdocs.com/).

### Ε: Πού μπορώ να βρω την τεκμηρίωση για το GroupDocs.Annotation για .NET;

Α: Μπορείτε να ανατρέξετε στην λεπτομερή διαθέσιμη τεκμηρίωση [εδώ](https://tutorials.groupdocs.com/annotation/net/).

### Ε: Πώς μπορώ να λάβω υποστήριξη ή βοήθεια με το GroupDocs.Annotation;

Α: Μπορείτε να ζητήσετε υποστήριξη και βοήθεια από το φόρουμ της κοινότητας GroupDocs.Annotation [εδώ](https://forum.groupdocs.com/c/annotation/10).