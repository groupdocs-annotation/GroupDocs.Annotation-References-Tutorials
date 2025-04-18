---
title: Κατάργηση σχολιασμών κατά αναγνωριστικό
linktitle: Κατάργηση σχολιασμών κατά αναγνωριστικό
second_title: GroupDocs.Annotation .NET API
description: Μάθετε πώς να αφαιρείτε σχολιασμούς κατά αναγνωριστικό χρησιμοποιώντας το GroupDocs.Annotation για .NET. Βελτιώστε τη ροή εργασιών του εγγράφου σας αποτελεσματικά.
weight: 11
url: /el/net/removing-annotations/remove-annotations-by-id/
---

# Κατάργηση σχολιασμών κατά αναγνωριστικό

## Εισαγωγή
Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στη διαδικασία κατάργησης των σχολιασμών με βάση τα αναγνωριστικά τους χρησιμοποιώντας το GroupDocs.Annotation για .NET. Οι σχολιασμοί μπορεί να γεμίσουν τα έγγραφά σας και η επιλεκτική κατάργησή τους μπορεί να βελτιώσει τη ροή εργασίας σας. Θα σας καθοδηγήσουμε βήμα προς βήμα, διασφαλίζοντας ότι κατανοείτε με σαφήνεια κάθε στάδιο.
## Προαπαιτούμενα
Πριν προχωρήσετε σε αυτό το σεμινάριο, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:
1.  GroupDocs.Annotation για .NET: Βεβαιωθείτε ότι έχετε εγκαταστήσει τη βιβλιοθήκη GroupDocs.Annotation για .NET. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.groupdocs.com/annotation/net/).
2. Πρόσβαση σε σχολιασμένο έγγραφο: Έχετε ένα έγγραφο σχολιασμένο με GroupDocs.Annotation. Εάν δεν έχετε, μπορείτε να ακολουθήσετε τα προηγούμενα σεμινάρια μας για να σχολιάσετε ένα έγγραφο.
3. Βασικές γνώσεις C#: Απαιτείται εξοικείωση με τη γλώσσα προγραμματισμού C# για την κατανόηση των παραδειγμάτων κώδικα.

## Εισαγωγή χώρων ονομάτων
Πριν ξεκινήσουμε την κωδικοποίηση, ας εισάγουμε τους απαραίτητους χώρους ονομάτων:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```

## Βήμα 1: Καθορίστε τη διαδρομή εξόδου
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Ορίζουμε τη διαδρομή εξόδου όπου θα αποθηκευτεί το έγγραφο με τους σχολιασμούς που έχουν αφαιρεθεί.
## Βήμα 2: Εκκίνηση του Annotator
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
```
 Εδώ, αρχικοποιούμε το`Annotator` αντικείμενο με τη διαδρομή προς το σχολιασμένο έγγραφο PDF.
## Βήμα 3: Καταργήστε τους σχολιασμούς
```csharp
annotator.Remove(0);
```
 Καταργούμε τους σχολιασμούς προσδιορίζοντας τα αναγνωριστικά τους. Σε αυτό το παράδειγμα, αφαιρούμε τον σχολιασμό με αναγνωριστικό`0` . Μπορείτε να αντικαταστήσετε`0` με το αναγνωριστικό του σχολιασμού που θέλετε να καταργήσετε.
## Βήμα 4: Αποθήκευση εγγράφου
```csharp
annotator.Save(outputPath);
```
Αφού αφαιρέσουμε τους σχολιασμούς, αποθηκεύουμε το τροποποιημένο έγγραφο στη διαδρομή εξόδου που καθορίστηκε προηγουμένως.
## Βήμα 5: Εμφάνιση μηνύματος επιτυχίας
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Τέλος, εμφανίζουμε ένα μήνυμα επιτυχίας μαζί με τη διαδρομή όπου αποθηκεύεται το τροποποιημένο έγγραφο.

## συμπέρασμα
Σε αυτό το σεμινάριο, μάθαμε πώς να αφαιρούμε τους σχολιασμούς από τα αναγνωριστικά τους χρησιμοποιώντας το GroupDocs.Annotation για .NET. Αυτή η λειτουργία βοηθά στην πιο αποτελεσματική διαχείριση των σχολιασμένων εγγράφων αφαιρώντας επιλεκτικά τους σχολιασμούς.
## Συχνές ερωτήσεις
### Μπορώ να αφαιρέσω πολλούς σχολιασμούς ταυτόχρονα;
 Ναι, μπορείτε να αφαιρέσετε πολλούς σχολιασμούς προσδιορίζοντας τα αναγνωριστικά τους στο`Remove` μέθοδος.
### Υπάρχει τρόπος να αναιρέσετε την κατάργηση των σχολιασμών;
Όχι, αφού αφαιρεθούν οι σχολιασμοί, δεν μπορούν να αναιρεθούν. Φροντίστε να δημιουργήσετε αντίγραφα ασφαλείας του εγγράφου σας πριν αφαιρέσετε τους σχολιασμούς.
### Μπορώ να αφαιρέσω σχολιασμούς από έγγραφα εκτός από αρχεία PDF;
Ναι, το GroupDocs.Annotation υποστηρίζει διάφορες μορφές εγγράφων, συμπεριλαμβανομένων των DOCX, XLSX, PPTX και άλλων.
### Υπάρχουν περιορισμοί στον αριθμό των σχολιασμών που μπορούν να αφαιρεθούν;
Όχι, μπορείτε να αφαιρέσετε οποιονδήποτε αριθμό σχολιασμών από ένα έγγραφο, αρκεί να καθορίσετε σωστά τα αναγνωριστικά τους.
### Υπάρχει διαθέσιμη τεχνική υποστήριξη εάν αντιμετωπίσω προβλήματα;
 Ναι, μπορείτε να λάβετε τεχνική υποστήριξη από το φόρουμ GroupDocs.Annotation[εδώ](https://forum.groupdocs.com/c/annotation/10).