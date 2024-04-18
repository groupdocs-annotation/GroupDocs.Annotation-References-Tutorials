---
title: Φόρτωση εγγράφου από FTP
linktitle: Φόρτωση εγγράφου από FTP
second_title: GroupDocs.Annotation .NET API
description: Βελτιώστε τις εφαρμογές σας .NET με GroupDocs.Annotation για απρόσκοπτο σχολιασμό εγγράφων. Περιλαμβάνεται σεμινάριο βήμα προς βήμα.
type: docs
weight: 12
url: /el/net/document-loading-essentials/load-document-from-ftp/
---
## Εισαγωγή
Το GroupDocs.Annotation για .NET είναι μια ευέλικτη βιβλιοθήκη που έχει σχεδιαστεί για να διευκολύνει τις δυνατότητες σχολιασμού εγγράφων στις εφαρμογές .NET χωρίς κόπο. Είτε έχετε να κάνετε με PDF, έγγραφα του Microsoft Office, εικόνες ή άλλες μορφές, αυτή η βιβλιοθήκη παρέχει μια ενοποιημένη λύση για την προσθήκη σχολιασμών, όπως σχόλια, επισημάνσεις και σχήματα, για τη βελτίωση της συνεργασίας και της διαχείρισης εγγράφων.
## Προαπαιτούμενα
Πριν βουτήξετε στο σεμινάριο, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:
1. Γνώση C#: Η επάρκεια στη γλώσσα προγραμματισμού C# είναι απαραίτητη για την κατανόηση και την υλοποίηση των παραδειγμάτων κώδικα που παρέχονται σε αυτό το σεμινάριο.
2.  GroupDocs.Annotation για .NET: Φροντίστε να πραγματοποιήσετε λήψη και εγκατάσταση του GroupDocs.Annotation για .NET από το[σύνδεσμος λήψης](https://releases.groupdocs.com/annotation/net/). Ακολουθήστε τις οδηγίες εγκατάστασης για να ενσωματώσετε τη βιβλιοθήκη στο έργο σας .NET με επιτυχία.
## Εισαγωγή χώρων ονομάτων
Για να χρησιμοποιήσετε το GroupDocs.Annotation για λειτουργίες .NET, πρέπει να εισαγάγετε τους απαιτούμενους χώρους ονομάτων στο έργο σας C#. Ακολουθήστε αυτά τα βήματα:

Στο έργο σας C#, συμπεριλάβετε τους απαραίτητους χώρους ονομάτων στην αρχή του αρχείου κώδικα:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Τώρα, ας εμβαθύνουμε στη διαδικασία φόρτωσης ενός εγγράφου από το FTP και προσθήκης σχολιασμών σε αυτό χρησιμοποιώντας το GroupDocs.Annotation για .NET.
## Βήμα 1: Καθορίστε τη διαδρομή εξόδου
Καθορίστε τη διαδρομή εξόδου όπου θα αποθηκευτεί το σχολιασμένο έγγραφο.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Βήμα 2: Φόρτωση εγγράφου από FTP
Ανακτήστε το έγγραφο από τον διακομιστή FTP χρησιμοποιώντας την παρεχόμενη διαδρομή αρχείου.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Ο κωδικός σχολιασμού θα προστεθεί εδώ
}
```
## Βήμα 3: Προσθήκη σχολιασμού
Ορίστε και προσθέστε τον επιθυμητό σχολιασμό, όπως έναν σχολιασμό περιοχής, στο έγγραφο.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Βήμα 4: Αποθήκευση σχολιασμένου εγγράφου
Αποθηκεύστε το σχολιασμένο έγγραφο στην καθορισμένη διαδρομή εξόδου.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Βήμα 5: Ανάκτηση αρχείου από FTP
Εφαρμόστε τη μέθοδο ανάκτησης του αρχείου από τον διακομιστή FTP.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## Βήμα 6: Δημιουργία αιτήματος FTP
Δημιουργήστε ένα αίτημα FTP για λήψη του αρχείου.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Βήμα 7: Λήψη ροής αρχείων
Ανακτήστε τη ροή του αρχείου από την απόκριση FTP.
```csharp
private static Stream GetFileStream(WebResponse response)
{
    MemoryStream fileStream = new MemoryStream();
    using (Stream responseStream = response.GetResponseStream())
        responseStream.CopyTo(fileStream);
    fileStream.Position = 0;
    return fileStream;
}
```
## συμπέρασμα
Συμπερασματικά, το GroupDocs.Annotation για .NET δίνει τη δυνατότητα στους προγραμματιστές να ενσωματώνουν απρόσκοπτα τις λειτουργίες σχολιασμού εγγράφων στις εφαρμογές τους .NET. Ακολουθώντας τον οδηγό βήμα προς βήμα που περιγράφεται σε αυτό το σεμινάριο, μπορείτε να φορτώνετε αποτελεσματικά έγγραφα από το FTP και να προσθέτετε σχολιασμούς με ευκολία, βελτιώνοντας τη συνεργασία και τη διαχείριση εγγράφων στις εφαρμογές σας.
## Συχνές ερωτήσεις
### Είναι το GroupDocs.Annotation για .NET συμβατό με όλες τις μορφές εγγράφων;
Ναι, το GroupDocs.Annotation για .NET υποστηρίζει ένα ευρύ φάσμα μορφών εγγράφων, συμπεριλαμβανομένων των PDF, εγγράφων του Microsoft Office, εικόνων και άλλων.
### Μπορώ να προσαρμόσω την εμφάνιση των σχολιασμών που προστέθηκαν χρησιμοποιώντας το GroupDocs.Annotation για .NET;
Οπωσδήποτε, το GroupDocs.Annotation για .NET προσφέρει εκτενείς επιλογές προσαρμογής για την εμφάνιση σχολιασμών, συμπεριλαμβανομένων χρωμάτων, στυλ και σχημάτων.
### Το GroupDocs.Annotation για .NET παρέχει υποστήριξη για υπηρεσίες αποθήκευσης cloud;
Ναι, το GroupDocs.Annotation για .NET ενσωματώνεται απρόσκοπτα με δημοφιλείς υπηρεσίες αποθήκευσης cloud, επιτρέποντάς σας να φορτώνετε και να αποθηκεύετε έγγραφα από υπηρεσίες όπως το Dropbox, το Google Drive και το OneDrive.
### Υπάρχει διαθέσιμη δοκιμαστική έκδοση για το GroupDocs.Annotation για .NET;
 Ναι, μπορείτε να εξερευνήσετε τις δυνατότητες του GroupDocs.Annotation για .NET κατεβάζοντας τη δωρεάν δοκιμαστική έκδοση από το[σελίδα έκδοσης](https://releases.groupdocs.com/).
### Πώς μπορώ να λάβω τεχνική βοήθεια ή υποστήριξη για το GroupDocs.Annotation για .NET;
 Για τεχνική βοήθεια, αντιμετώπιση προβλημάτων ή γενικές ερωτήσεις, μπορείτε να επισκεφτείτε το GroupDocs.Annotation για .NET[φόρουμ υποστήριξης](https://forum.groupdocs.com/c/annotation/10).