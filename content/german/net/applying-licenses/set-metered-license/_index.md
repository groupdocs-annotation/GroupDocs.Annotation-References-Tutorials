---
"description": "Erfahren Sie, wie Sie eine mengengeregelte Lizenz für GroupDocs.Annotation .NET einrichten, um die Ressourcennutzung zu steuern und die Annotationsfunktionen in Ihren .NET-Anwendungen zu dokumentieren."
"linktitle": "Gemessene Lizenz festlegen"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Gemessene Lizenz festlegen"
"url": "/de/net/applying-licenses/set-metered-license/"
type: docs
"weight": 12
---

# Gemessene Lizenz festlegen

## Einführung
GroupDocs.Annotation für .NET ist eine leistungsstarke Bibliothek, mit der Entwickler ihren .NET-Anwendungen mühelos Dokumentannotationsfunktionen hinzufügen können. Egal, ob Sie ein Dokumentenmanagementsystem, eine Kollaborationsplattform oder eine andere Anwendung zur Dokumentprüfung und -markierung entwickeln – GroupDocs.Annotation für .NET bietet umfassende Tools zur Optimierung des Prozesses.
In diesem Tutorial erfahren Sie, wie Sie eine nutzungsabhängige Lizenz für GroupDocs.Annotation .NET einrichten. Mit einer nutzungsabhängigen Lizenz zahlen Sie nur für die tatsächlich genutzten Ressourcen und sind somit eine kostengünstige Lösung für Projekte jeder Größenordnung. Mit den folgenden Schritten können Sie GroupDocs.Annotation nahtlos in Ihre .NET-Anwendung integrieren und gleichzeitig die Ressourcennutzung optimieren und die Budgetkontrolle behalten.
## Voraussetzungen
Bevor Sie mit dem Lernprogramm beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1. GroupDocs.Annotation für .NET-Bibliothek: Laden Sie die Bibliothek herunter von der [Webseite](https://releases.groupdocs.com/annotation/net/).
2. Zugriff auf das GroupDocs-Konto: Sie benötigen ein GroupDocs-Konto, um die öffentlichen und privaten Schlüssel für die Einrichtung der gebührenpflichtigen Lizenz zu erhalten. Falls Sie noch kein Konto haben, können Sie sich für eine kostenlose Testversion anmelden. [Hier](https://releases.groupdocs.com/).
3. Grundlegende Kenntnisse von C# und .NET Framework: Kenntnisse der Programmiersprache C# und des .NET Frameworks sind für die Implementierung der in diesem Lernprogramm beschriebenen Schritte von Vorteil.

## Namespaces importieren
Importieren Sie zunächst die erforderlichen Namespaces in Ihr C#-Projekt. Diese Namespaces sind für die Interaktion mit der GroupDocs.Annotation-Funktionalität unerlässlich.
```csharp
using System;
```
## Schritt 1: Öffentliche und private Schlüssel erhalten
Bevor Sie die gemessene Lizenz einrichten, müssen Sie Ihre öffentlichen und privaten Schlüssel von Ihrem GroupDocs-Konto-Dashboard abrufen.
1. Melden Sie sich bei Ihrem GroupDocs-Konto an.
2. Navigieren Sie zum Abschnitt Lizenzverwaltung.
3. Kopieren Sie Ihre von GroupDocs bereitgestellten öffentlichen und privaten Schlüssel.
## Schritt 2: Gemessene Lizenz festlegen
Sobald Sie Ihre öffentlichen und privaten Schlüssel erhalten haben, können Sie die gemessene Lizenz in Ihrer .NET-Anwendung einrichten.
```csharp
string publicKey = "*****"; // Ersetzen Sie ***** durch Ihren öffentlichen Schlüssel
string privateKey = "*****"; // Ersetzen Sie ***** durch Ihren privaten Schlüssel
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Abschluss
Zusammenfassend lässt sich sagen, dass die Einrichtung einer mengenabhängigen Lizenz für GroupDocs.Annotation .NET ein unkomplizierter Prozess ist, der eine effiziente Ressourcennutzung und Kosteneffizienz für Ihre Dokumentannotationsprojekte gewährleistet. Mit den in diesem Tutorial beschriebenen Schritten können Sie GroupDocs.Annotation nahtlos in Ihre .NET-Anwendung integrieren und die Funktionen für die Zusammenarbeit und Überprüfung von Dokumenten verbessern.
## Häufig gestellte Fragen
### Kann ich GroupDocs.Annotation für .NET in kommerziellen Projekten verwenden?
Ja, GroupDocs.Annotation für .NET kann sowohl in kommerziellen als auch in nicht-kommerziellen Projekten eingesetzt werden. Sie benötigen jedoch eine entsprechende Lizenz, die Ihren Projektanforderungen entspricht.
### Gibt es eine Testversion für GroupDocs.Annotation für .NET?
Ja, Sie können eine kostenlose Testversion von GroupDocs.Annotation für .NET nutzen, indem Sie [dieser Link](https://releases.groupdocs.com/).
### Wie erhalte ich technischen Support für GroupDocs.Annotation für .NET?
Sie können technischen Support erhalten, indem Sie das GroupDocs-Forum besuchen [Hier](https://forum.groupdocs.com/c/annotation/10).
### Gibt es Optionen für temporäre Lizenzen?
Ja, Sie können von GroupDocs eine temporäre Lizenz für die kurzfristige Nutzung oder zu Testzwecken erhalten. Besuchen Sie [dieser Link](https://purchase.groupdocs.com/temporary-license/) für weitere Informationen.
### Kann ich die Anmerkungsfunktionen entsprechend meinen Projektanforderungen anpassen?
Ja, GroupDocs.Annotation für .NET bietet umfangreiche Anpassungsoptionen, sodass Sie die Anmerkungsfunktionen an Ihre spezifischen Projektanforderungen anpassen können.