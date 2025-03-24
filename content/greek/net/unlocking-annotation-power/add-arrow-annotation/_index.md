---
title: Προσθήκη σχολιασμού βέλους στο έγγραφο
linktitle: Προσθήκη σχολιασμού βέλους στο έγγραφο
second_title: GroupDocs.Annotation .NET API
description: Μάθετε πώς να προσθέτετε σχολιασμούς με βέλη στα έγγραφά σας χρησιμοποιώντας το GroupDocs.Annotation για .NET. Βελτιώστε τη σαφήνεια και τη διαδραστικότητα των εγγράφων χωρίς κόπο.
weight: 11
url: /el/net/unlocking-annotation-power/add-arrow-annotation/
---
## Εισαγωγή
Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στη διαδικασία προσθήκης σχολιασμών με βέλη στα έγγραφά σας χρησιμοποιώντας το GroupDocs.Annotation για .NET. Οι σχολιασμοί βέλους είναι χρήσιμοι για την ένδειξη κατεύθυνσης ή την επισήμανση συγκεκριμένων στοιχείων μέσα σε ένα έγγραφο.
## Προαπαιτούμενα
Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε τα ακόλουθα:
1.  GroupDocs.Annotation για .NET: Εγκαταστήστε τη βιβλιοθήκη GroupDocs.Annotation για .NET. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.groupdocs.com/annotation/net/).
2. Περιβάλλον ανάπτυξης: Βεβαιωθείτε ότι έχετε ρυθμίσει ένα περιβάλλον ανάπτυξης για ανάπτυξη .NET, συμπεριλαμβανομένου του Visual Studio ή οποιουδήποτε άλλου προτιμώμενου IDE.

## Εισαγωγή χώρων ονομάτων
Αρχικά, πρέπει να εισαγάγετε τους απαραίτητους χώρους ονομάτων για πρόσβαση στις απαιτούμενες κλάσεις και μεθόδους για σχολιασμό.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Βήμα 1: Εκκίνηση του Annotator
Αρχικοποιήστε τον σχολιαστή παρέχοντας τη διαδρομή αρχείου εγγράφου εισόδου.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Βήμα 2: Δημιουργήστε σχολιασμό βέλους
Δημιουργήστε μια παρουσία της κλάσης ArrowAnnotation και ορίστε τις ιδιότητές της όπως θέση, μήνυμα, αδιαφάνεια, χρώμα στυλό, στυλ, πλάτος κ.λπ.
```csharp
	ArrowAnnotation arrow = new ArrowAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		CreatedOn = DateTime.Now,
		Message = "This is arrow annotation",
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
 Προσθέστε τον σχολιασμό βέλους στο έγγραφο χρησιμοποιώντας το`Add` μέθοδος του σχολιαστή.
```csharp
	annotator.Add(arrow);
```
## Βήμα 4: Αποθήκευση εγγράφου
Αποθηκεύστε το σχολιασμένο έγγραφο στην καθορισμένη διαδρομή εξόδου.
```csharp
	annotator.Save(outputPath);
}
```
## Βήμα 5: Επιβεβαίωση εμφάνισης
Εμφανίστε ένα μήνυμα επιβεβαίωσης που υποδεικνύει την επιτυχή αποθήκευση του εγγράφου.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Τώρα προσθέσατε με επιτυχία έναν σχολιασμό βέλους στο έγγραφό σας χρησιμοποιώντας το GroupDocs.Annotation για .NET.

## συμπέρασμα
Σε αυτό το σεμινάριο, καλύψαμε τη διαδικασία προσθήκης σχολιασμών με βέλη σε έγγραφα χρησιμοποιώντας το GroupDocs.Annotation για .NET. Ακολουθώντας αυτά τα βήματα, μπορείτε να βελτιώσετε τα έγγραφά σας με σαφείς δείκτες κατεύθυνσης, καθιστώντας τα πιο ενημερωτικά και ελκυστικά.
## Συχνές ερωτήσεις
### Μπορώ να προσαρμόσω την εμφάνιση του σχολιασμού του βέλους;
Ναι, μπορείτε να προσαρμόσετε διάφορες ιδιότητες, όπως το χρώμα, το στυλ, το πλάτος και την αδιαφάνεια, ώστε να ταιριάζουν στις προτιμήσεις και τις απαιτήσεις εγγράφων σας.
### Είναι το GroupDocs.Annotation συμβατό με όλες τις μορφές εγγράφων;
Το GroupDocs.Annotation υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, συμπεριλαμβανομένων των PDF, DOCX, PPTX, XLSX και άλλων.
### Μπορώ να προσθέσω σχολιασμούς μέσω προγραμματισμού χρησιμοποιώντας το GroupDocs.Annotation;
Ναι, το GroupDocs.Annotation παρέχει API που σας επιτρέπουν να προσθέτετε, να επεξεργάζεστε και να αφαιρείτε μέσω προγραμματισμού σχολιασμούς από έγγραφα.
### Το GroupDocs.Annotation προσφέρει δωρεάν δοκιμή;
 Ναι, μπορείτε να δοκιμάσετε το GroupDocs.Annotation δωρεάν κατεβάζοντάς το από[εδώ](https://releases.groupdocs.com/).
### Πού μπορώ να λάβω τεχνική υποστήριξη για το GroupDocs.Annotation;
Για τεχνική υποστήριξη και βοήθεια, μπορείτε να επισκεφτείτε το φόρουμ GroupDocs.Annotation[εδώ](https://forum.groupdocs.com/c/annotation/10).