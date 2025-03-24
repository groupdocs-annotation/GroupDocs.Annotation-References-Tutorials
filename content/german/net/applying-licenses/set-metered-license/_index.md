---
title: Legen Sie die gemessene Lizenz fest
linktitle: Legen Sie die gemessene Lizenz fest
second_title: GroupDocs.Annotation .NET-API
description: Erfahren Sie, wie Sie eine getaktete Lizenz für GroupDocs.Annotation .NET für die Ressourcennutzung und Dokumentanmerkungsfunktionen in Ihren .NET-Anwendungen einrichten.
weight: 12
url: /de/net/applying-licenses/set-metered-license/
---

# Legen Sie die gemessene Lizenz fest

## Einführung
GroupDocs.Annotation für .NET ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, ihren .NET-Anwendungen mühelos Dokumentanmerkungsfunktionen hinzuzufügen. Unabhängig davon, ob Sie ein Dokumentenverwaltungssystem, eine Plattform für die Zusammenarbeit oder eine andere Anwendung erstellen, die die Überprüfung und Markierung von Dokumenten umfasst, bietet GroupDocs.Annotation für .NET einen umfassenden Satz an Tools zur Optimierung des Prozesses.
In diesem Tutorial befassen wir uns mit dem Prozess der Einrichtung einer getakteten Lizenz für GroupDocs.Annotation .NET. Mit einer gebührenpflichtigen Lizenz zahlen Sie nur für die Ressourcen, die Sie verbrauchen, was sie zu einer kostengünstigen Lösung für Projekte jeder Größenordnung macht. Wenn Sie die unten beschriebenen Schritte befolgen, können Sie GroupDocs.Annotation nahtlos in Ihre .NET-Anwendung integrieren und gleichzeitig die Ressourcennutzung optimieren und die Budgetkontrolle beibehalten.
## Voraussetzungen
Bevor Sie mit dem Tutorial beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1.  GroupDocs.Annotation für .NET-Bibliothek: Laden Sie die Bibliothek von herunter[Webseite](https://releases.groupdocs.com/annotation/net/).
2. Zugriff auf das GroupDocs-Konto: Sie benötigen ein GroupDocs-Konto, um die öffentlichen und privaten Schlüssel zu erhalten, die zum Einrichten der gemessenen Lizenz erforderlich sind. Wenn Sie noch kein Konto haben, können Sie sich für eine kostenlose Testversion anmelden[Hier](https://releases.groupdocs.com/).
3. Grundlegende Kenntnisse von C# und .NET Framework: Vertrautheit mit der Programmiersprache C# und dem .NET Framework ist für die Implementierung der in diesem Tutorial beschriebenen Schritte von Vorteil.

## Namespaces importieren
Stellen Sie zunächst sicher, dass Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren. Diese Namespaces sind für die Interaktion mit der GroupDocs.Annotation-Funktionalität unerlässlich.
```csharp
using System;
```
## Schritt 1: Erhalten Sie öffentliche und private Schlüssel
Bevor Sie die gemessene Lizenz einrichten, müssen Sie Ihre öffentlichen und privaten Schlüssel von Ihrem GroupDocs-Konto-Dashboard erhalten.
1. Melden Sie sich bei Ihrem GroupDocs-Konto an.
2. Navigieren Sie zum Abschnitt Lizenzverwaltung.
3. Kopieren Sie Ihre von GroupDocs bereitgestellten öffentlichen und privaten Schlüssel.
## Schritt 2: Festlegen der gemessenen Lizenz
Sobald Sie Ihre öffentlichen und privaten Schlüssel erhalten haben, können Sie die gemessene Lizenz in Ihrer .NET-Anwendung einrichten.
```csharp
string publicKey = "*****"; // Ersetzen Sie ***** durch Ihren öffentlichen Schlüssel
string privateKey = "*****"; // Ersetzen Sie ***** durch Ihren privaten Schlüssel
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Abschluss
Zusammenfassend lässt sich sagen, dass die Einrichtung einer getakteten Lizenz für GroupDocs.Annotation .NET ein unkomplizierter Prozess ist, der eine effiziente Ressourcennutzung und Kosteneffizienz für Ihre Dokumentanmerkungsprojekte gewährleistet. Wenn Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie GroupDocs.Annotation nahtlos in Ihre .NET-Anwendung integrieren und die Funktionen für die Zusammenarbeit und Überprüfung von Dokumenten verbessern.
## FAQs
### Kann ich GroupDocs.Annotation für .NET in kommerziellen Projekten verwenden?
Ja, GroupDocs.Annotation für .NET kann sowohl in kommerziellen als auch nichtkommerziellen Projekten verwendet werden. Sie müssen jedoch eine entsprechende Lizenz erwerben, die Ihren Projektanforderungen entspricht.
### Gibt es eine Testversion für GroupDocs.Annotation für .NET?
 Ja, Sie können eine kostenlose Testversion von GroupDocs.Annotation für .NET nutzen, indem Sie hier klicken[dieser Link](https://releases.groupdocs.com/).
### Wie erhalte ich technischen Support für GroupDocs.Annotation für .NET?
 Sie können technischen Support anfordern, indem Sie das GroupDocs-Forum besuchen[Hier](https://forum.groupdocs.com/c/annotation/10).
### Gibt es temporäre Lizenzoptionen?
 Ja, Sie können bei GroupDocs eine temporäre Lizenz für kurzfristige Nutzung oder Evaluierungszwecke erwerben. Besuchen[dieser Link](https://purchase.groupdocs.com/temporary-license/) für mehr Informationen.
### Kann ich die Anmerkungsfunktionen entsprechend meinen Projektanforderungen anpassen?
Ja, GroupDocs.Annotation für .NET bietet umfangreiche Anpassungsoptionen, sodass Sie die Anmerkungsfunktionen an Ihre spezifischen Projektanforderungen anpassen können.