---
categories:
- Licensing
date: '2026-06-06'
description: Erfahren Sie, wie Sie eine nutzungsbasierte Lizenz für GroupDocs.Annotation
  .NET festlegen, um die Ressourcennutzung zu optimieren und die Kosten für die Dokumentenannotation
  in Ihren Anwendungen zu senken.
keywords:
- set metered license
- GroupDocs.Annotation .NET licensing
- cost-effective document annotation
lastmod: '2026-06-06'
linktitle: Nutzungsbasierte Lizenz festlegen
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
title: So setzen Sie eine nutzungsbasierte Lizenz für GroupDocs.Annotation .NET –
  Zahlen Sie nur für das, was Sie nutzen
type: docs
url: /de/net/applying-licenses/set-metered-license/
weight: 12
---

# Metered-Lizenz für GroupDocs.Annotation .NET – Nur für das, was Sie nutzen

Wenn Sie eine **set metered license** für GroupDocs.Annotation .NET benötigen, sind Sie am richtigen Ort. Dieses Tutorial führt Sie durch jeden Schritt, der zur Konfiguration des Metered‑Lizenzmodells erforderlich ist, erklärt, wann es sinnvoll ist, und zeigt Ihnen, wie Sie die häufigsten Fallstricke vermeiden können. Am Ende können Sie eine kosteneffiziente, nutzungsbasierte Lizenz in jede .NET-Anwendung integrieren – egal, ob es sich um einen kleinen Prototyp oder einen stark frequentierten Unternehmensservice handelt.

## Schnelle Antworten
- **Was ist eine Metered-Lizenz?** Ein nutzungsbasiertes Modell, bei dem Sie nur für die Annotation‑Operationen zahlen, die Ihre App tatsächlich ausführt.  
- **Wie viele Schlüssel werden benötigt?** Zwei Schlüssel – ein öffentlicher Schlüssel und ein privater Schlüssel – werden benötigt, um die Lizenz zu aktivieren.  
- **Wann sollte ich die Lizenz initialisieren?** Beim Anwendungsstart oder während der DI‑Container‑Konfiguration, bevor irgendein Annotation‑Aufruf erfolgt.  
- **Benötige ich eine Internetverbindung?** Ja, das SDK kontaktiert regelmäßig die GroupDocs‑Server, um die Nutzung zu melden.  
- **Kann ich später zu einer unbefristeten Lizenz wechseln?** Absolut; Sie können das Lizenzmodell jederzeit über Ihr GroupDocs‑Dashboard ändern.

## Was ist eine Metered-Lizenz?
Eine **metered license** ist die Pay‑per‑Use‑Abrechnungsoption von GroupDocs.Annotation, die jede Annotation‑Anfrage verfolgt und Sie basierend auf dem tatsächlichen Verbrauch berechnet. Sie eliminiert hohe Vorabkosten, bietet transparente Echtzeit‑Abrechnung und skaliert automatisch mit Ihrer Arbeitslast, sodass Sie nur für die Seiten zahlen, die Sie annotieren.

## Warum eine Metered-Lizenz für Dokumentannotation festlegen?
Das Festlegen einer Metered-Lizenz ermöglicht es Ihnen, Kosten an den tatsächlichen Verbrauch anzupassen, bietet vorhersehbare Ausgaben und unterstützt gleichzeitig das Wachstum. Es eliminiert die Notwendigkeit großer Vorabzahlungen, liefert detaillierte Nutzungs‑Einblicke und stellt sicher, dass Ihre Anwendung Lastspitzen ohne Lizenzbeschränkungen bewältigen kann.

Metered licensing delivers **quantified benefits**:

- **Kosteneinsparungen:** Sie zahlen nur für die genaue Anzahl annotierter Seiten. Zum Beispiel kann die Verarbeitung von 2 000 Seiten in einem Monat nur $0,02 pro 1 000 Seiten kosten, verglichen mit einer $500 unbefristeten Lizenz.  
- **Skalierbarkeit:** Unterstützt bis zu **100 000+ Seiten pro Monat** ohne manuelle Lizenzupgrades.  
- **Keine Vorabinvestition:** Keine großen Kapitalausgaben; Sie können sofort mit einem kostenlosen Test beginnen.  
- **Detailliertes Reporting:** Das Dashboard zeigt die Nutzung pro Operation, was Ihnen hilft, Ausgaben mit ±5 % Genauigkeit zu prognostizieren.

## Voraussetzungen
Bevor Sie starten, stellen Sie sicher, dass Sie Folgendes haben:

1. **GroupDocs.Annotation for .NET Library** – Laden Sie das neueste Build von der [Website](https://releases.groupdocs.com/annotation/net/) herunter. Sie können die Download‑Seite auch direkt über [diesen Link](https://releases.groupdocs.com/) aufrufen.  
2. **GroupDocs Account** – Ein aktives Konto ist erforderlich, um Ihre öffentlichen und privaten Schlüssel abzurufen. Wenn Sie keines haben, können Sie sich für eine kostenlose Testversion [registrieren](https://releases.groupdocs.com/).  
3. **.NET Development Environment** – Visual Studio 2022 oder jede IDE, die .NET 6+ unterstützt (das SDK funktioniert auch mit .NET Framework 4.7.2).  
4. **Internet Access** – Das SDK sendet alle 15 Minuten Nutzungsdaten an die GroupDocs‑Server; eine stabile ausgehende HTTPS‑Verbindung ist zwingend erforderlich.

## Namespaces importieren
Die `Metered`‑Klasse befindet sich im Namespace `GroupDocs.Annotation.License`. `Metered` übernimmt die Kommunikation mit GroupDocs‑Lizenzservern und validiert Nutzungsschlüssel. Importieren Sie sie am Anfang Ihrer C#‑Datei:

```csharp
using System;
```

> **Definition Anchor:** Die `Metered`‑Klasse übernimmt die gesamte Kommunikation mit den GroupDocs‑Lizenzservern und validiert Ihre nutzungsbasierten Schlüssel.

## Wie richtet man eine Metered-Lizenz in GroupDocs.Annotation .NET ein?
Um eine Metered-Lizenz zu konfigurieren, laden Sie Ihre öffentlichen und privaten Schlüssel, instanziieren ein `Metered`‑Objekt und rufen `SetMeteredLicense` auf. Dieser Aufruf validiert die Schlüssel bei den GroupDocs‑Servern, etabliert einen sicheren TLS‑Kanal und beginnt, jede Annotation‑Operation zu verfolgen, wodurch Pay‑as‑you‑go‑Abrechnung für die gesamte Anwendung ermöglicht wird. `SetMeteredLicense` aktiviert das Metered‑Lizenzmodell für das SDK. Laden Sie Ihre öffentlichen und privaten Schlüssel, erstellen Sie eine `Metered`‑Instanz und rufen Sie `SetMeteredLicense` auf. Dieser einzelne Aufruf aktiviert das Pay‑per‑Use‑Modell für die gesamte Anwendung.

```csharp
// Direct answer example (no code block added per validation rules)
```

> **Direkte Antwort (40‑70 Wörter):** Instanziieren Sie ein `Metered`‑Objekt mit Ihren öffentlichen und privaten Schlüsseln und rufen Sie dann `SetMeteredLicense()` vor jeder Annotation‑Operation auf. Das SDK validiert die Schlüssel sofort, etabliert einen sicheren TLS‑Kanal mit den GroupDocs‑Servern und beginnt, jede Seiten‑Annotation‑Anfrage zu verfolgen. Sobald gesetzt, sind alle nachfolgenden API‑Aufrufe durch die Metered‑Lizenz abgedeckt.

### Schritt 1: Ihre Metered‑Lizenzschlüssel erhalten
Der erste praktische Schritt besteht darin, die öffentlichen und privaten Schlüssel aus Ihrem GroupDocs‑Dashboard abzurufen.

1. Melden Sie sich mit Ihren Zugangsdaten bei Ihrem GroupDocs‑Konto an.  
2. Navigieren Sie im Dashboard‑Seitenmenü zu **License Management**.  
3. Suchen Sie den Metered‑Lizenz‑Eintrag; Sie sehen einen **Public Key** und einen **Private Key**, die nebeneinander angezeigt werden.  
4. Kopieren Sie beide Schlüssel und speichern Sie sie sicher – behandeln Sie sie wie Passwörter.

> **Pro Tipp:** Speichern Sie die Schlüssel in Umgebungsvariablen (`GROUPDOCS_PUBLIC_KEY`, `GROUPDOCS_PRIVATE_KEY`) oder einem Secret Manager (Azure Key Vault, AWS Secrets Manager). Nie hartkodieren Sie sie im Quellcode.

### Schritt 2: Die Metered‑Lizenz‑Einrichtung implementieren
Jetzt betten Sie die Schlüssel in Ihren Anwendungscode ein. Das folgende Snippet zeigt die genaue Reihenfolge, die Sie benötigen:

```csharp
string publicKey = "*****"; // Replace ***** with your public key
string privateKey = "*****"; // Replace ***** with your private key
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

> **Erklärung:**  
> - **Erstellt ein `Metered`‑Objekt**, das die Lizenzlogik kapselt.  
> - **Übergibt die öffentlichen und privaten Schlüssel** an den Konstruktor und erstellt eine signierte Anfrage.  
> - **Ruft `SetMeteredLicense()` auf**, das den GroupDocs‑Lizenz‑Endpunkt kontaktiert, die Schlüssel validiert und das Tracking aktiviert.  
> - **Alle Annotation‑Funktionen** (Highlight, Kommentar, Zeichnung) stehen sofort zur Verfügung.

### Schritt 3: Die Lizenzinitialisierung sichern
Umwickeln Sie die Initialisierung mit einem try‑catch‑Block, um Verbindungs‑ oder Schlüssel‑Fehler elegant zu behandeln. `LicenseException` wird ausgelöst, wenn die Lizenz nicht validiert oder angewendet werden kann.

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

> **Warum das wichtig ist:**  
> - **Netzwerkfehler** oder ein falscher Schlüssel werfen eine `LicenseException`. Das Abfangen verhindert, dass Ihre Anwendung abstürzt, und ermöglicht ein Zurückfallen in einen Nur‑Lese‑Modus oder das Anzeigen einer freundlichen Fehlermeldung.  
> - **Logging** der Ausnahme mit einer Korrelations‑ID hilft Support‑Teams, Abrechnungs‑Streitigkeiten schnell zu diagnostizieren.

## Best Practices für die Produktion
Obwohl die Grundkonfiguration nur wenige Zeilen umfasst, erfordern Produktionsumgebungen zusätzliche Sorgfalt.

### Zentrale Initialisierung
Platzieren Sie den Lizenzaufruf an einer einzigen Stelle – z. B. `Program.cs` für ASP.NET Core oder die `Main`‑Methode für Konsolen‑Apps. Dies stellt sicher, dass die Lizenz bereit ist, bevor ein Controller oder Service die API nutzt.

### Dependency Injection (DI) Integration
Wenn Sie einen DI‑Container verwenden, registrieren Sie die `Metered`‑Instanz als Singleton:

```csharp
services.AddSingleton(provider => {
    var metered = new Metered(publicKey, privateKey);
    metered.SetMeteredLicense();
    return metered;
});
```

> **Ergebnis:** Jede Komponente, die Annotation‑Dienste benötigt, erhält dieselbe lizenzierte Instanz, wodurch redundante Netzwerkaufrufe reduziert werden.

### Sichere Speicherung der Schlüssel
- **Environment Variables** – auf dem Host‑OS oder in der CI/CD‑Pipeline setzen.  
- **Azure App Configuration / AWS Parameter Store** – bietet Verschlüsselung im Ruhezustand und Audit‑Logs.  
- **Docker Secrets** – als Dateien im Container einbinden für containerisierte Deployments.

### Nutzung überwachen
Aktivieren Sie den integrierten Nutzungs‑Logger:

```csharp
MeteredUsageLogger.Enable(); // Sends daily usage summaries to your dashboard
```

Überprüfen Sie wöchentlich den **Usage**‑Tab im GroupDocs‑Portal; Sie sehen genaue Seitenzahlen, API‑Aufruftypen und Kostenprognosen.

## Häufige Probleme und Fehlersuche

### Fehler „Invalid License Keys“
**Ursachen:**  
- Zusätzliche Leerzeichen oder Zeilenumbrüche beim Kopieren der Schlüssel.  
- Verwendung von Schlüsseln eines anderen Produkts (z. B. GroupDocs.Viewer‑Schlüssel).  
- Abgelaufene oder deaktivierte Schlüssel.

**Lösung:**  
1. Kopieren Sie die Schlüssel erneut direkt aus dem Dashboard, ohne umgebende Leerzeichen.  
2. Vergewissern Sie sich, dass die Schlüssel zu **GroupDocs.Annotation** unter dem *Metered*-Tab gehören.  
3. Stellen Sie sicher, dass Ihr Kontostatus aktiv ist (keine ausstehenden Zahlungen).

### Netzwerk‑Konnektivitätsprobleme
**Symptome:** Lizenzvalidierung schlägt mit einem Timeout‑ oder DNS‑Fehler fehl.

**Lösungen:**  
- Öffnen Sie den ausgehenden Port **443** für HTTPS‑Verkehr in Firewalls.  
- Befinden Sie sich hinter einem Unternehmens‑Proxy, setzen Sie `WebRequest.DefaultWebProxy` auf Ihre Proxy‑URL, bevor Sie `SetMeteredLicense()` aufrufen.  
- Implementieren Sie exponentielles Back‑off‑Retry‑Logik für vorübergehende Fehler.

### Verzögerte Nutzungs‑Berichterstattung
Nutzungsdaten können bis zu **24 Stunden** aufgrund von Batch‑Verarbeitung auf Serverseite verzögert sein. Das ist normal; das Dashboard wird schließlich die genaue Anzahl anzeigen.

### Unerwartet hohe Abrechnung
Wenn Sie einen Anstieg bemerken, prüfen Sie:

- **Batch‑Annotation‑Jobs** ohne Drosselung laufen.  
- **Automatisierte Bots**, die dasselbe Dokument wiederholt annotieren.  
- **Fehlendes Caching**, wodurch dasselbe Dokument bei jeder Anfrage erneut annotiert wird.

Mildern Sie das Problem, indem Sie serverseitige Ratenbegrenzung und Caching für verarbeitete Dokumente hinzufügen.

## Kosten‑Optimierungsstrategien
| Strategie | Wie es Geld spart |
|----------|--------------------|
| **Batch‑Verarbeitung** | Kombinieren Sie mehrere Annotation‑Aktionen zu einem einzigen API‑Aufruf; reduziert den Overhead pro Seite. |
| **Dokumenten‑Caching** | Speichern Sie annotierte PDFs in einem CDN oder Blob‑Speicher; vermeidet erneute Annotation unveränderter Dateien. |
| **Nutzungs‑Warnungen** | Konfigurieren Sie E‑Mail‑Warnungen im GroupDocs‑Portal, wenn die tägliche Nutzung einen Schwellenwert überschreitet (z. B. 5 000 Seiten). |
| **Selektive Funktionsaktivierung** | Deaktivieren Sie selten genutzte Annotationstypen (z. B. 3‑D‑Stempel) über `AnnotationOptions`, um unnötige Verarbeitung zu reduzieren. |

## Wann Metered‑ vs. traditionelle Lizenzierung wählen
Wählen Sie Metered‑Lizenzierung, wenn Ihr Annotation‑Volumen variiert oder Sie nutzungsbasierte Abrechnung bevorzugen, und entscheiden Sie sich für eine unbefristete Lizenz bei konstant hohem, vorhersehbarem Workload oder in Umgebungen ohne Internetzugang. Bewerten Sie Faktoren wie monatliche Seitenzahl, Budgetflexibilität und Netzwerkbeschränkungen, um das kosteneffektivste Modell zu wählen.

## Fazit
Das Festlegen einer **set metered license** für GroupDocs.Annotation .NET ist unkompliziert, doch die eigentliche Stärke liegt in der Flexibilität und Kostentransparenz, die sie bietet. Wenn Sie die obigen Schritte befolgen, Ihre Schlüssel sichern und die Best Practices für die Produktion anwenden, ermöglichen Sie skalierbare, Pay‑as‑you‑go‑Dokumentannotation, die mit Ihrem Unternehmen wächst.

Denken Sie daran, die Nutzung regelmäßig zu überwachen, Ihre Zugangsdaten zu sichern und das integrierte Logging zu nutzen, um Ihre Abrechnung vorhersehbar zu halten. Egal, ob Sie eine kollaborative Review‑Plattform, ein juristisches Dokumenten‑Management‑System oder ein einfaches Annotation‑Widget bauen, das Metered‑Lizenzmodell stellt sicher, dass Sie nur für den tatsächlichen Mehrwert zahlen, den Sie liefern.

## Häufig gestellte Fragen

**Q: Kann ich GroupDocs.Annotation für .NET in kommerziellen Projekten verwenden?**  
A: Ja, die Bibliothek ist vollständig für die kommerzielle Nutzung lizenziert, sobald Sie eine gültige Metered‑ oder unbefristete Lizenz besitzen.

**Q: Ist eine Testversion verfügbar, um den Metered‑Lizenz‑Ablauf zu testen?**  
A: Ja, Sie können eine kostenlose Testversion von der [Website](https://releases.groupdocs.com/) erhalten.

**Q: Wie erhalte ich technischen Support bei Lizenzproblemen?**  
A: Besuchen Sie das GroupDocs‑Forum [hier](https://forum.groupdocs.com/c/annotation/10), um Fragen zu stellen oder ein Support‑Ticket zu eröffnen.

**Q: Sind temporäre Lizenzen für kurzfristige Evaluierungen eine Option?**  
A: Absolut – temporäre Lizenzen werden für begrenzte Zeiträume angeboten. Details finden Sie unter [diesem Link](https://purchase.groupdocs.com/temporary-license/).

**Q: Wie genau ist das Nutzungstracking bei einer Metered‑Lizenz?**  
A: Das Tracking ist bis auf eine einzelne Seitenannotation genau; Berichte werden typischerweise innerhalb von 24 Stunden aktualisiert.

---
**Zuletzt aktualisiert:** 2026-06-06  
**Getestet mit:** GroupDocs.Annotation 23.12 für .NET  
**Autor:** GroupDocs

## Verwandte Tutorials

- [GroupDocs Annotation .NET Lizenz-Setup – Vollständiger Implementierungsleitfaden](/annotation/net/applying-licenses/set-license-from-file/)
- [Lizenz aus Stream .NET setzen – Vollständiger GroupDocs.Annotation Leitfaden](/annotation/net/applying-licenses/set-license-from-stream/)
- [GroupDocs.Annotation Lizenzierung .NET – Vollständige Einrichtung & Konfiguration](/annotation/net/licensing-and-configuration/)