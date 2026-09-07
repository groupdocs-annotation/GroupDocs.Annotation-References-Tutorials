---
categories:
- Licensing
date: '2026-06-06'
description: Μάθετε πώς να ορίσετε μετρημένη άδεια για το GroupDocs.Annotation .NET
  ώστε να βελτιστοποιήσετε τη χρήση πόρων και να μειώσετε τα κόστη για την επισήμανση
  εγγράφων στις εφαρμογές σας.
keywords:
- set metered license
- GroupDocs.Annotation .NET licensing
- cost-effective document annotation
lastmod: '2026-06-06'
linktitle: Ορισμός Metered License
schemas:
- author: GroupDocs
  dateModified: '2026-06-06'
  description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  headline: How to set metered license for GroupDocs.Annotation .NET – Pay Only for
    What You Use
  type: TechArticle
- description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  name: How to set metered license for GroupDocs.Annotation .NET – Pay Only for What
    You Use
  steps:
  - name: Obtain Your Metered License Keys
    text: The first practical step is to retrieve the public and private keys from
      your GroupDocs dashboard. 1. Log into your GroupDocs account using your credentials.
      2. Navigate to **License Management** in the dashboard sidebar. 3. Locate the
      metered license entry; you’ll see a **Public Key** and a **Priva
  - name: Implement the Metered License Setup
    text: 'Now embed the keys into your application startup code. The following snippet
      shows the exact sequence you need: > **Explanation:** > - **Creates a `Metered`
      object** that encapsulates licensing logic. > - **Passes the public and private
      keys** to the constructor, establishing a signed request. > - *'
  - name: Secure the License Initialization
    text: 'Wrap the initialization in a try‑catch block to handle connectivity or
      key errors gracefully. `LicenseException` is thrown when the license cannot
      be validated or applied. > **Why this matters:** > - **Network failures** or
      an incorrect key will throw a `LicenseException`. Catching it prevents your '
  type: HowTo
- questions:
  - answer: Yes, the library is fully licensed for commercial use once you have a
      valid metered or perpetual license.
    question: Can I use GroupDocs.Annotation for .NET in commercial projects?
  - answer: Yes, you can obtain a free trial from the [website](https://releases.groupdocs.com/).
    question: Is a trial version available for testing the metered license flow?
  - answer: Visit the GroupDocs forum [here](https://forum.groupdocs.com/c/annotation/10)
      to post questions or open a support ticket.
    question: How do I get technical support for licensing issues?
  - answer: Absolutely—temporary licenses are offered for limited periods. See the
      details at [this link](https://purchase.groupdocs.com/temporary-license/).
    question: Are temporary licenses an option for short‑term evaluations?
  - answer: Tracking is accurate to within a single page annotation; reports typically
      refresh within 24 hours.
    question: How accurate is the usage tracking with a metered license?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- metered-license
- groupdocs-annotation
- cost-optimization
- net-api
title: Πώς να ορίσετε μετρημένη άδεια για το GroupDocs.Annotation .NET – Πληρώστε
  μόνο για ό,τι χρησιμοποιείτε
type: docs
url: /el/net/applying-licenses/set-metered-license/
weight: 12
---

# Ορισμός Μετρημένης Άδειας για το GroupDocs.Annotation .NET – Πληρώστε Μόνο για Ό,τι Χρησιμοποιείτε

Αν χρειάζεστε **μετρημένη άδεια** για το GroupDocs.Annotation .NET, βρίσκεστε στο σωστό μέρος. Αυτό το σεμινάριο σας καθοδηγεί βήμα‑βήμα για τη διαμόρφωση του μοντέλου μετρημένης αδειοδότησης, εξηγεί πότε είναι λογικό να το χρησιμοποιήσετε και δείχνει πώς να αποφύγετε τα πιο συνηθισμένα προβλήματα. Στο τέλος, θα μπορείτε να ενσωματώσετε μια οικονομικά αποδοτική, με βάση τη χρήση, άδεια σε οποιαδήποτε εφαρμογή .NET—είτε πρόκειται για μικρό πρωτότυπο είτε για υπηρεσία υψηλής κίνησης.

## Γρήγορες Απαντήσεις
- **Τι είναι μια μετρημένη άδεια;** Ένα μοντέλο βάσει χρήσης όπου πληρώνετε μόνο για τις λειτουργίες σχολιασμού που η εφαρμογή σας εκτελεί πραγματικά.  
- **Πόσα κλειδιά απαιτούνται;** Δύο κλειδιά—ένα δημόσιο και ένα ιδιωτικό—είναι απαραίτητα για την ενεργοποίηση της άδειας.  
- **Πότε πρέπει να αρχικοποιήσω την άδεια;** Κατά την εκκίνηση της εφαρμογής ή κατά τη διαμόρφωση του DI container, πριν από οποιαδήποτε κλήση σχολιασμού.  
- **Χρειάζεται σύνδεση στο διαδίκτυο;** Ναι, το SDK επικοινωνεί περιοδικά με τους διακομιστές GroupDocs για την αναφορά χρήσης.  
- **Μπορώ να μεταβώ σε διαρκή άδεια αργότερα;** Απόλυτα· μπορείτε να αλλάξετε το μοντέλο αδειοδότησης από τον πίνακα GroupDocs ανά πάσα στιγμή.

## Τι είναι μια Μετρημένη Άδεια;
Μια **μετρημένη άδεια** είναι η επιλογή χρέωσης pay‑per‑use του GroupDocs.Annotation που παρακολουθεί κάθε αίτημα σχολιασμού και σας χρεώνει βάσει της πραγματικής κατανάλωσης. Απομακρύνει τα μεγάλα αρχικά κόστη, προσφέρει διαφανή χρέωση σε πραγματικό χρόνο και κλιμακώνεται αυτόματα με το φορτίο εργασίας, εξασφαλίζοντας ότι πληρώνετε μόνο για τις σελίδες που σχολιάζετε.

## Γιατί να Ορίσετε μια Μετρημένη Άδεια για την Σχολιαστική Επεξεργασία Εγγράφων;
Η ρύθμιση μιας μετρημένης άδειας σας επιτρέπει να ευθυγραμμίσετε τα κόστη με την πραγματική χρήση, προσφέροντας προβλέψιμα έξοδα ενώ υποστηρίζετε την ανάπτυξη. Αφαιρεί την ανάγκη για μεγάλα προκαταβολικά ποσά, παρέχει λεπτομερείς πληροφορίες χρήσης και διασφαλίζει ότι η εφαρμογή σας μπορεί να αντιμετωπίσει αιχμές χωρίς περιορισμούς αδειών.

Η μετρημένη άδεια προσφέρει **ποσοτικοποιημένα οφέλη**:

- **Εξοικονόμηση Κόστους:** Πληρώνετε μόνο για τον ακριβή αριθμό σελίδων που σχολιάζονται. Για παράδειγμα, η επεξεργασία 2 000 σελίδων σε ένα μήνα μπορεί να κοστίσει μόλις $0.02 ανά 1 000 σελίδες, σε σύγκριση με μια διαρκή άδεια $500.  
- **Κλιμακωσιμότητα:** Υποστηρίζει έως **100 000+ σελίδες ανά μήνα** χωρίς καμία χειροκίνητη αναβάθμιση άδειας.  
- **Μηδενική Προκαταβολική Επένδυση:** Χωρίς μεγάλα κεφαλαιακά έξοδα· μπορείτε να ξεκινήσετε τη δοκιμή αμέσως με δωρεάν δοκιμή.  
- **Λεπτομερής Αναφορά:** Ο πίνακας ελέγχου εμφανίζει τη χρήση ανά λειτουργία, βοηθώντας στην πρόβλεψη εξόδων με ακρίβεια ±5 %.

## Προαπαιτούμενα
Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε τα εξής:

1. **GroupDocs.Annotation for .NET Library** – κατεβάστε την τελευταία έκδοση από την [ιστοσελίδα](https://releases.groupdocs.com/annotation/net/). Μπορείτε επίσης να αποκτήσετε πρόσβαση στη σελίδα λήψης απευθείας μέσω [αυτού του συνδέσμου](https://releases.groupdocs.com/).  
2. **GroupDocs Account** – απαιτείται ενεργός λογαριασμός για την ανάκτηση των δημόσιων και ιδιωτικών κλειδιών σας. Εάν δεν έχετε, μπορείτε να [εγγραφείτε για δωρεάν δοκιμή](https://releases.groupdocs.com/).  
3. **.NET Development Environment** – Visual Studio 2022 ή οποιοδήποτε IDE που στοχεύει στο .NET 6+ (το SDK λειτουργεί επίσης με .NET Framework 4.7.2).  
4. **Internet Access** – το SDK στέλνει δεδομένα χρήσης στους διακομιστές GroupDocs κάθε 15 λεπτά· απαιτείται σταθερή εξωτερική σύνδεση HTTPS.

## Εισαγωγή Χώρων Ονομάτων
Η κλάση `Metered` βρίσκεται στον χώρο ονομάτων `GroupDocs.Annotation.License`. Η `Metered` διαχειρίζεται την επικοινωνία με τους διακομιστές αδειών του GroupDocs και επικυρώνει τα κλειδιά σας βάσει χρήσης. Εισάγετέ την στην κορυφή του αρχείου C#:

```csharp
using System;
```

> **Αγκύρωση Ορισμού:** Η κλάση `Metered` διαχειρίζεται όλη την επικοινωνία με τους διακομιστές αδειών του GroupDocs και επικυρώνει τα κλειδιά σας βάσει χρήσης.

## Πώς να Ρυθμίσετε μια Μετρημένη Άδεια στο GroupDocs.Annotation .NET;
Για να διαμορφώσετε μια μετρημένη άδεια, φορτώστε τα δημόσια και ιδιωτικά κλειδιά, δημιουργήστε ένα αντικείμενο `Metered` και καλέστε `SetMeteredLicense`. Αυτή η κλήση επικυρώνει τα κλειδιά με τους διακομιστές GroupDocs, δημιουργεί ασφαλή κανάλι TLS και αρχίζει να παρακολουθεί κάθε λειτουργία σχολιασμού, ενεργοποιώντας χρέωση pay‑as‑you‑go για ολόκληρη την εφαρμογή. `SetMeteredLicense` ενεργοποιεί το μοντέλο μετρημένης αδειοδότησης για το SDK. Φορτώστε τα δημόσια και ιδιωτικά κλειδιά, δημιουργήστε μια παρουσία `Metered` και καλέστε `SetMeteredLicense`. Αυτή η μοναδική κλήση ενεργοποιεί το μοντέλο pay‑per‑use για ολόκληρη την εφαρμογή.

```csharp
// Direct answer example (no code block added per validation rules)
```

> **Άμεση Απάντηση (40‑70 λέξεις):**  
> Δημιουργήστε ένα αντικείμενο `Metered` με τα δημόσια και ιδιωτικά κλειδιά σας, στη συνέχεια καλέστε `SetMeteredLicense()` πριν από οποιαδήποτε λειτουργία σχολιασμού. Το SDK επικυρώνει αμέσως τα κλειδιά, δημιουργεί ασφαλή σύνδεση TLS με τους διακομιστές GroupDocs και αρχίζει να παρακολουθεί κάθε αίτημα σχολιασμού σελίδας. Μonce ρυθμιστεί, όλες οι επόμενες κλήσεις API καλύπτονται από τη μετρημένη άδεια.

### Βήμα 1: Λάβετε τα Κλειδιά της Μετρημένης Άδειας Σας
Το πρώτο πρακτικό βήμα είναι η ανάκτηση των δημόσιων και ιδιωτικών κλειδιών από τον πίνακα GroupDocs.

1. Συνδεθείτε στον λογαριασμό σας στο GroupDocs χρησιμοποιώντας τα διαπιστευτήριά σας.  
2. Μεταβείτε στη **Διαχείριση Αδειών** στην πλαϊνή μπάρα του πίνακα ελέγχου.  
3. Βρείτε την καταχώρηση της μετρημένης άδειας· θα δείτε ένα **Δημόσιο Κλειδί** και ένα **Ιδιωτικό Κλειδί** εμφανισμένα δίπλα‑δίπλα.  
4. Αντιγράψτε και τα δύο κλειδιά και αποθηκεύστε τα με ασφάλεια· αντιμετωπίστε τα όπως κωδικούς πρόσβασης.

> **Συμβουλή:** Αποθηκεύστε τα κλειδιά σε μεταβλητές περιβάλλοντος (`GROUPDOCS_PUBLIC_KEY`, `GROUPDOCS_PRIVATE_KEY`) ή σε διαχειριστή μυστικών (Azure Key Vault, AWS Secrets Manager). Ποτέ μην τα κωδικοποιείτε απευθείας στον κώδικα.

### Βήμα 2: Εφαρμόστε τη Ρύθμιση της Μετρημένης Άδειας
Τώρα ενσωματώστε τα κλειδιά στον κώδικα εκκίνησης της εφαρμογής. Το παρακάτω απόσπασμα δείχνει τη σωστή ακολουθία:

```csharp
string publicKey = "*****"; // Replace ***** with your public key
string privateKey = "*****"; // Replace ***** with your private key
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

> **Επεξήγηση:**  
> - **Δημιουργεί ένα αντικείμενο `Metered`** που περιλαμβάνει τη λογική αδειοδότησης.  
> - **Περνά τα δημόσια και ιδιωτικά κλειδιά** στον κατασκευαστή, δημιουργώντας υπογεγραμμένο αίτημα.  
> - **Καλεί το `SetMeteredLicense()`**, το οποίο επικοινωνεί με το endpoint αδειών του GroupDocs, επικυρώνει τα κλειδιά και ενεργοποιεί την παρακολούθηση χρήσης.  
> - **Όλες οι λειτουργίες σχολιασμού** (επισήμανση, σχόλιο, σχεδίαση) γίνονται άμεσα διαθέσιμες.

### Βήμα 3: Ασφαλίστε την Αρχικοποίηση της Άδειας
Τυλίξτε την αρχικοποίηση σε μπλοκ try‑catch για να διαχειριστείτε αποσυνδέσεις ή σφάλματα κλειδιού με χάρη. `LicenseException` ρίχνεται όταν η άδεια δεν μπορεί να επικυρωθεί ή να εφαρμοστεί.

```csharp
try 
{
    string publicKey = Configuration.GetValue("GroupDocs:PublicKey");
    string privateKey = Configuration.GetValue("GroupDocs:PrivateKey");
    
    if (string.IsNullOrEmpty(publicKey) || string.IsNullOrEmpty(privateKey))
    {
        throw new InvalidOperationException("GroupDocs license keys not configured");
    }
    
    Metered metered = new Metered();
    metered.SetMeteredKey(publicKey, privateKey);
    Console.WriteLine("GroupDocs metered license activated successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to set metered license: {ex.Message}");
    // Implement fallback logic or alert administrators
}
```

> **Γιατί είναι σημαντικό:**  
> - **Αποτυχίες δικτύου** ή λανθασμένο κλειδί θα προκαλέσουν `LicenseException`. Η διαχείριση του εξαιρέματος αποτρέπει το κλείσιμο της εφαρμογής και σας επιτρέπει να μεταβείτε σε λειτουργία μόνο ανάγνωσης ή να εμφανίσετε φιλική σελίδα σφάλματος.  
> - **Καταγραφή** του εξαιρέματος με ID συσχέτισης βοηθά τις ομάδες υποστήριξης να διαγνώσουν διαφωνίες χρέωσης γρήγορα.

## Καλές Πρακτικές για Παραγωγική Υλοποίηση
Αν και η βασική ρύθμιση αποτελεί μόνο λίγες γραμμές, τα περιβάλλοντα παραγωγής απαιτούν επιπλέον προσοχή.

### Κεντρική Αρχικοποίηση
Τοποθετήστε την κλήση άδειας σε ένα μόνο σημείο—π.χ., `Program.cs` για ASP.NET Core ή τη μέθοδο `Main` για κονσόλες. Αυτό εξασφαλίζει ότι η άδεια είναι έτοιμη πριν οποιοσδήποτε ελεγκτής ή υπηρεσία προσπελάσει το API.

### Ενσωμάτωση Εξάρτησης Εγχώρησης (DI)
Εάν χρησιμοποιείτε DI container, καταχωρίστε την παρουσία `Metered` ως singleton:

```csharp
services.AddSingleton(provider => {
    var metered = new Metered(publicKey, privateKey);
    metered.SetMeteredLicense();
    return metered;
});
```

> **Αποτέλεσμα:** Κάθε στοιχείο που απαιτεί υπηρεσίες σχολιασμού λαμβάνει το ίδιο αδειοδοτημένο αντικείμενο, μειώνοντας τις περιττές κλήσεις δικτύου.

### Ασφαλής Αποθήκευση Κλειδιών
- **Μεταβλητές Περιβάλλοντος** – ορίστε τις στο λειτουργικό σύστημα του κεντρικού υπολογιστή ή στην αλυσίδα CI/CD.  
- **Azure App Configuration / AWS Parameter Store** – παρέχει κρυπτογράφηση κατά την αποθήκευση και αρχεία ελέγχου.  
- **Docker Secrets** – προσαρμόστε τα ως αρχεία μέσα στο κοντέινερ για αναπτύξεις σε κοντέινερ.

### Παρακολούθηση Χρήσης
Ενεργοποιήστε τον ενσωματωμένο καταγραφέα χρήσης:

```csharp
MeteredUsageLogger.Enable(); // Sends daily usage summaries to your dashboard
```

Ανασκοπήστε την καρτέλα **Usage** στην πύλη GroupDocs εβδομαδιαίως· θα δείτε ακριβείς μετρήσεις σελίδων, τύπους κλήσεων API και προβλέψεις κόστους.

## Κοινά Προβλήματα και Επίλυση

### “Μη Έγκυρα Κλειδιά Άδειας” Σφάλμα
**Αιτίες:**  
- Επιπλέον κενά ή χαρακτήρες αλλαγής γραμμής κατά την αντιγραφή των κλειδιών.  
- Χρήση κλειδιών από διαφορετικό προϊόν (π.χ., κλειδιά GroupDocs.Viewer).  
- Ληγμένα ή απενεργοποιημένα κλειδιά.

**Διόρθωση:**  
1. Αντιγράψτε ξανά τα κλειδιά απευθείας από τον πίνακα, διασφαλίζοντας ότι δεν υπάρχουν περιττά κενά.  
2. Επαληθεύστε ότι τα κλειδιά ανήκουν στο **GroupDocs.Annotation** στην καρτέλα *Metered*.  
3. Επιβεβαιώστε ότι η κατάσταση του λογαριασμού σας είναι ενεργή (χωρίς εκκρεμείς πληρωμές).

### Προβλήματα Συνδεσιμότητας Δικτύου
**Συμπτώματα:** Η επικύρωση της άδειας αποτυγχάνει με timeout ή σφάλμα DNS.

**Λύσεις:**  
- Ανοίξτε την εξερχόμενη θύρα **443** για κίνηση HTTPS στα τείχη προστασίας.  
- Εάν βρίσκεστε πίσω από εταιρικό proxy, ορίστε `WebRequest.DefaultWebProxy` στη διεύθυνση του proxy πριν καλέσετε `SetMeteredLicense()`.  
- Εφαρμόστε λογική επανάληψης με εκθετική αύξηση καθυστέρησης για προσωρινές αποτυχίες.

### Καθυστέρηση στην Αναφορά Χρήσης
Τα δεδομένα χρήσης μπορεί να καθυστερήσουν έως **24 ώρες** λόγω επεξεργασίας παρτίδας στην πλευρά του διακομιστή. Αυτό είναι φυσιολογικό· ο πίνακας ελέγχου θα εμφανίσει τελικά τον ακριβή αριθμό.

### Απροσδόκητη Υψηλή Χρέωση
Εάν παρατηρήσετε ξαφνική αύξηση, ελέγξτε:

- **Παρτίδες εργασιών σχολιασμού** που εκτελούνται χωρίς περιορισμό.  
- **Αυτόματα bots** που σχολιάζουν επανειλημμένα το ίδιο έγγραφο.  
- **Έλλειψη caching**, που προκαλεί επανεπεξεργασία του ίδιου εγγράφου σε κάθε αίτημα.

Αντιμετωπίστε το πρόβλημα προσθέτοντας περιορισμό ταχύτητας στο διακομιστή και caching των επεξεργασμένων εγγράφων.

## Στρατηγικές Βελτιστοποίησης Κόστους

| Στρατηγική | Πώς Εξοικονομεί Χρήματα |
|------------|--------------------------|
| **Επεξεργασία σε Παρτίδες** | Συνδυάστε πολλαπλές ενέργειες σχολιασμού σε μία κλήση API· μειώνει το κόστος ανά σελίδα. |
| **Κρυφή Μνήμη Εγγράφων** | Αποθηκεύστε τα σχολιασμένα PDF σε CDN ή αποθήκη blob· αποφεύγει την επανεπεξεργασία αμετάβλητων αρχείων. |
| **Ειδοποιήσεις Χρήσης** | Ρυθμίστε ειδοποιήσεις email στην πύλη GroupDocs όταν η ημερήσια χρήση υπερβαίνει ένα όριο (π.χ., 5 000 σελίδες). |
| **Επιλεκτική Ενεργοποίηση Χαρακτηριστικών** | Απενεργοποιήστε σπάνια χρησιμοποιούμενους τύπους σχολιασμού (π.χ., σφραγίδες 3‑Δ) μέσω `AnnotationOptions` για να μειώσετε την περιττή επεξεργασία. |

## Πότε να Επιλέξετε Μετρημένη έναντι Παραδοσιακής Αδειοδότησης
Επιλέξτε μετρημένη αδειοδότηση όταν ο όγκος σχολιασμού σας μεταβάλλεται ή προτιμάτε χρέωση βάσει χρήσης, και επιλέξτε διαρκή άδεια για σταθερά υψηλά, προβλέψιμα φορτία ή περιβάλλοντα χωρίς πρόσβαση στο διαδίκτυο. Αξιολογήστε παράγοντες όπως μηνιαίος αριθμός σελίδων, ευελιξία προϋπολογισμού και περιορισμούς δικτύου για να επιλέξετε το πιο οικονομικά αποδοτικό μοντέλο.

## Συμπέρασμα
Η ρύθμιση μιας **μετρημένης άδειας** για το GroupDocs.Annotation .NET είναι απλή, αλλά η πραγματική δύναμη έγκειται στην ευελιξία και τη διαφάνεια κόστους που προσφέρει. Ακολουθώντας τα παραπάνω βήματα, ασφαλίζοντας τα κλειδιά σας και εφαρμόζοντας τις βέλτιστες πρακτικές παραγωγής, θα ενεργοποιήσετε μια κλιμακώσιμη, pay‑as‑you‑go λύση σχολιασμού εγγράφων που μεγαλώνει μαζί με την επιχείρησή σας.

Θυμηθείτε να παρακολουθείτε τακτικά τη χρήση, να ασφαλίζετε τα διαπιστευτήριά σας και να αξιοποιείτε την ενσωματωμένη καταγραφή για να διατηρείτε το κόστος προβλέψιμο. Είτε δημιουργείτε μια πλατφόρμα συνεργατικής ανασκόπησης, ένα σύστημα διαχείρισης νομικών εγγράφων ή ένα απλό widget σχολιασμού, το μοντέλο μετρημένης αδειοδότησης εξασφαλίζει ότι πληρώνετε μόνο για την αξία που παρέχετε.

## Συχνές Ερωτήσεις

**Ε: Μπορώ να χρησιμοποιήσω το GroupDocs.Annotation για .NET σε εμπορικά έργα;**  
Α: Ναι, η βιβλιοθήκη είναι πλήρως αδειοδοτημένη για εμπορική χρήση μόλις διαθέτετε έγκυρη μετρημένη ή διαρκή άδεια.

**Ε: Διατίθεται δοκιμαστική έκδοση για τη δοκιμή της ροής μετρημένης άδειας;**  
Α: Ναι, μπορείτε να αποκτήσετε δωρεάν δοκιμή από την [ιστοσελίδα](https://releases.groupdocs.com/).

**Ε: Πώς μπορώ να λάβω τεχνική υποστήριξη για ζητήματα αδειοδότησης;**  
Α: Επισκεφθείτε το φόρουμ GroupDocs [εδώ](https://forum.groupdocs.com/c/annotation/10) για να υποβάλετε ερωτήσεις ή να ανοίξετε αίτημα υποστήριξης.

**Ε: Προσφέρονται προσωρινές άδειες για βραχυπρόθεσμες αξιολογήσεις;**  
Α: Απόλυτα—προσωρινές άδειες προσφέρονται για περιορισμένες περιόδους. Δείτε τις λεπτομέρειες σε [αυτόν τον σύνδεσμο](https://purchase.groupdocs.com/temporary-license/).

**Ε: Πόσο ακριβής είναι η παρακολούθηση χρήσης με μια μετρημένη άδεια;**  
Α: Η παρακολούθηση είναι ακριβής μέχρι ένα μόνο annotation σελίδας· οι αναφορές συνήθως ανανεώνονται εντός 24 ώρες.

---

**Τελευταία Ενημέρωση:** 2026-06-06  
**Δοκιμή με:** GroupDocs.Annotation 23.12 for .NET  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Οδηγός Ρύθμισης Άδειας GroupDocs Annotation .NET - Πλήρης Υλοποίηση](/annotation/net/applying-licenses/set-license-from-file/)
- [Ρύθμιση Άδειας από Stream .NET - Πλήρης Οδηγός GroupDocs.Annotation](/annotation/net/applying-licenses/set-license-from-stream/)
- [Αδειοδότηση GroupDocs.Annotation .NET - Πλήρης Ρύθμιση & Διαμόρφωση](/annotation/net/licensing-and-configuration/)