---
title: Προσθήκη σχολιασμού επεξεργασίας κειμένου στο έγγραφο
linktitle: Προσθήκη σχολιασμού επεξεργασίας κειμένου στο έγγραφο
second_title: GroupDocs.Annotation .NET API
description: Μάθετε πώς να προσθέτετε σχολιασμούς επεξεργασίας κειμένου σε έγγραφα PDF χρησιμοποιώντας το GroupDocs.Annotation για .NET. Προστατέψτε τις ευαίσθητες πληροφορίες χωρίς κόπο.
weight: 23
url: /el/net/unlocking-annotation-power/add-text-redaction-annotation/
---
## Εισαγωγή
Η προσθήκη ενός σχολιασμού επεξεργασίας κειμένου σε ένα έγγραφο μπορεί να είναι ένα κρίσιμο βήμα για την ασφαλή διαχείριση ευαίσθητων πληροφοριών. Το GroupDocs.Annotation για .NET παρέχει μια ισχυρή λύση για την απρόσκοπτη επίτευξη αυτού του στόχου. Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στη διαδικασία προσθήκης ενός σχολιασμού επεξεργασίας κειμένου στο έγγραφό σας βήμα προς βήμα.
## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:
1.  GroupDocs.Annotation για .NET: Βεβαιωθείτε ότι έχετε εγκαταστήσει τη βιβλιοθήκη GroupDocs.Annotation για .NET. Μπορείτε να το κατεβάσετε από το[δικτυακός τόπος](https://releases.groupdocs.com/annotation/net/).
2. Περιβάλλον ανάπτυξης: Ρυθμίστε ένα περιβάλλον ανάπτυξης με ένα IDE συμβατό με .NET, όπως το Visual Studio.

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
## Βήμα 1: Καθορίστε τη διαδρομή εξόδου
Καθορίστε τη διαδρομή εξόδου όπου θέλετε να αποθηκεύσετε το σχολιασμένο έγγραφο. Βεβαιωθείτε ότι είναι προσβάσιμο και εγγράψιμο.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Βήμα 2: Εκκίνηση του Annotator
 Αρχικοποιήστε τον σχολιαστή με τη διαδρομή εγγράφου εισόδου. Αντικαθιστώ`"input.pdf"` με τη διαδρομή προς το έγγραφό σας.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Ο κωδικός σχολιασμού θα πάει εδώ
}
```
## Βήμα 3: Δημιουργήστε σχολιασμό επεξεργασίας κειμένου
 Δημιουργώ ένα`TextRedactionAnnotation`αντικείμενο με τις απαιτούμενες ιδιότητες όπως`PageNumber`, `FontColor` , και`Points`. Προσαρμόστε τον σχολιασμό σύμφωνα με τις απαιτήσεις σας.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## Βήμα 4: Προσθήκη σχολιασμού και αποθήκευση
Προσθέστε τον σχολιασμό που δημιουργήθηκε στο έγγραφο χρησιμοποιώντας τον σχολιαστή και αποθηκεύστε το σχολιασμένο έγγραφο στην καθορισμένη διαδρομή εξόδου.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Βήμα 5: Ελέγξτε την έξοδο
Τέλος, επιβεβαιώστε ότι το έγγραφο έχει αποθηκευτεί με επιτυχία στην καθορισμένη διαδρομή εξόδου.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## συμπέρασμα
Σε αυτό το σεμινάριο, ακολουθήσαμε τη διαδικασία προσθήκης ενός σχολιασμού επεξεργασίας κειμένου σε ένα έγγραφο χρησιμοποιώντας το GroupDocs.Annotation για .NET. Με αυτά τα βήματα, μπορείτε πλέον να διαχειρίζεστε με ασφάλεια ευαίσθητες πληροφορίες στα έγγραφά σας.
## Συχνές ερωτήσεις
### Μπορώ να προσαρμόσω την εμφάνιση του σχολιασμού επεξεργασίας κειμένου;
Ναι, μπορείτε να προσαρμόσετε διάφορες ιδιότητες όπως το χρώμα γραμματοσειράς, το χρώμα πλήρωσης και την αδιαφάνεια για να ταιριάζουν στις απαιτήσεις σας.
### Υπάρχει διαθέσιμη δοκιμαστική έκδοση πριν την αγορά;
 Ναι, μπορείτε να αποκτήσετε πρόσβαση σε μια δωρεάν δοκιμαστική έκδοση από το[δικτυακός τόπος](https://releases.groupdocs.com/).
### Πώς μπορώ να λάβω υποστήριξη εάν αντιμετωπίζω προβλήματα;
 Μπορείτε να λάβετε υποστήριξη από το φόρουμ της κοινότητας GroupDocs.Annotation[εδώ](https://forum.groupdocs.com/c/annotation/10).
### Χρειάζομαι μια προσωρινή άδεια για σκοπούς δοκιμής;
 Ναι, μπορείτε να αποκτήσετε προσωρινή άδεια από το[σελίδα αγοράς](https://purchase.groupdocs.com/temporary-license/)για δοκιμή.
### Μπορώ να προσθέσω πολλαπλούς σχολιασμούς σε ένα μόνο έγγραφο;
Οπωσδήποτε, το GroupDocs.Annotation σάς επιτρέπει να προσθέτετε διάφορους τύπους σχολιασμών και πολλαπλές παρουσίες σε ένα μόνο έγγραφο.