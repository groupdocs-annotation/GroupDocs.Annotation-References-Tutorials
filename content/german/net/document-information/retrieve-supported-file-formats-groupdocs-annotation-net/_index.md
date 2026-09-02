---
categories:
- .NET Development
date: '2026-06-26'
description: Erfahren Sie, wie Sie mit GroupDocs.Annotation für .NET Formate abrufen,
  Probleme mit nicht unterstützten Dateiformaten beheben und bewährte Validierungspraktiken
  anwenden.
keywords:
- how to retrieve formats
- troubleshoot unsupported file format
- GroupDocs.Annotation .NET
lastmod: '2026-06-26'
linktitle: Unterstützte Dateiformate abrufen .NET
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  headline: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete
    Guide
  type: TechArticle
- description: Learn how to retrieve formats with GroupDocs.Annotation for .NET, troubleshoot
    unsupported file format issues, and apply best‑practice validation.
  name: How to Retrieve Formats in .NET Using GroupDocs.Annotation – Complete Guide
  steps:
  - name: Verify installation
    text: Run `dotnet list package` or check the NuGet console output for any warnings.
  - name: Check license status
    text: Ensure `License.SetLicense("path/to/license.json")` executes before any
      API call.
  - name: Diagnose environment constraints
    text: '- Confirm .NET runtime version matches the library’s requirements. - Verify
      the process has read/write permissions for the temporary folder used by GroupDocs.Annotation.'
  type: HowTo
- questions:
  - answer: The library supports **over 50 formats**, including PDF, DOCX, XLSX, PPTX,
      JPEG, PNG, TIFF, and many others. Run the sample code to retrieve the exact
      list for your license.
    question: What file formats does GroupDocs.Annotation actually support?
  - answer: This usually points to a licensing issue—either an expired trial or an
      incorrectly loaded license file. Re‑apply a valid license and restart the app.
    question: Why am I getting fewer supported formats than expected?
  - answer: No direct “IsSupported” method exists; the recommended approach is to
      cache the full list once and query it locally for fast lookups.
    question: Can I check a single format without pulling the whole list?
  - answer: Initialise the format cache at application startup (e.g., in `ConfigureServices`)
      and store it in a static or singleton service. This eliminates per‑request overhead.
    question: How should I handle format checking in a high‑traffic web app?
  - answer: Exceptions typically stem from licensing or corrupted installations. Verify
      the package integrity, re‑install if needed, and ensure the license file is
      accessible.
    question: What if GetSupportedFileTypes() throws an exception?
  type: FAQPage
tags:
- GroupDocs.Annotation
- file-formats
- document-processing
- dotnet-tutorial
title: Wie man Formate in .NET mit GroupDocs.Annotation abruft – Vollständige Anleitung
type: docs
url: /de/net/document-information/retrieve-supported-file-formats-groupdocs-annotation-net/
weight: 1
---

# Wie man Formate in .NET mit GroupDocs.Annotation abruft

## Einführung

Haben Sie sich jemals gefragt, welche Dateiformate Ihre .NET‑Anwendung tatsächlich für die Dokumentenannotation verarbeiten kann? **How to retrieve formats** ist eine Frage, die viele Entwickler stellen, wenn sie Benutzer‑Uploads validieren oder dynamische UI‑Filter erstellen müssen. Genau zu wissen, welche Dateiformate Ihre GroupDocs.Annotation‑Implementierung unterstützt, ist nicht nur hilfreich – es ist essenziell, um robuste Anwendungen zu bauen, die nie wegen eines unerwarteten Dateityps abstürzen.

In diesem Leitfaden lernen Sie, wie Sie programmgesteuert unterstützte Dateiformate mit GroupDocs.Annotation für .NET abrufen und validieren können. Wir gehen die grundlegende Implementierung durch, zeigen Ihnen, wie Sie die rohe Liste in ein sauberes Dropdown für End‑Benutzer verwandeln, und behandeln praxisnahe Fehlersuche‑Tipps, sodass Sie jedes Dokument‑Format‑Szenario mit Zuversicht handhaben können.

**Was Sie am Ende wissen werden**

- Ein kristallklares Verständnis der Dateiformat‑Fähigkeiten von GroupDocs.Annotation  
- Fertig‑einsetzbarer Code, der jedes unterstützte Format abruft und anzeigt  
- Bewährte Strategien für Caching, Fehlerbehandlung und Lizenz‑Edge‑Cases  
- Empfehlungen nach Best‑Practice für produktionsreife Dateityp‑Validierung  

Lassen Sie uns eintauchen und dieses Dateiformat‑Puzzle ein für alle Mal lösen.

## Schnelle Antworten
- **Was bedeutet „how to retrieve formats“?** Es ist der programmgesteuerte Weg, GroupDocs.Annotation zu fragen, welche Erweiterungen es annotieren kann.  
- **Welche primären Formate werden standardmäßig unterstützt?** Über 50, darunter PDF, DOCX, XLSX, PPTX, JPEG, PNG und TIFF.  
- **Benötige ich eine Lizenz, um die vollständige Liste zu erhalten?** Ja – eine aktive kommerzielle oder Test‑Lizenz schaltet den kompletten Katalog frei.  
- **Wird empfohlen, die Formatliste zu cachen?** Absolut; Caching vermeidet unnötige Aufrufe und verbessert die Reaktionszeit.  
- **Wie kann ich einen Upload gegen die Liste validieren?** Vergleichen Sie die Dateierweiterung mit der zwischengespeicherten Sammlung unterstützter Erweiterungen.

## Was bedeutet „how to retrieve formats“?
**How to retrieve formats** bezieht sich auf den Vorgang, die API von GroupDocs.Annotation aufzurufen, um eine Sammlung aller Dateitypen zu erhalten, die die Bibliothek annotieren kann. Dieser Vorgang liefert eine schreibgeschützte Liste von `FileType`‑Objekten, die sowohl die Dateierweiterung als auch eine benutzerfreundliche Beschreibung enthalten.

## Warum GroupDocs.Annotation für die Format‑Erkennung verwenden?
GroupDocs.Annotation unterstützt **mehr als 50 Eingabe‑ und Ausgabeformate** – darunter PDF, Microsoft Office (Word, Excel, PowerPoint) und gängige Bildtypen – und verarbeitet mehrseitige Dokumente, ohne die gesamte Datei in den Speicher zu laden. Diese quantifizierte Fähigkeit macht es zu einer zuverlässigen Wahl für Annotation‑Pipelines im Unternehmensmaßstab.

## Voraussetzungen und Umgebungseinrichtung

### Was Sie benötigen
- **IDE:** Visual Studio 2019 oder neuer (Community‑Edition funktioniert einwandfrei)  
- **Ziel‑Framework:** .NET Framework 4.6.1 + oder .NET Core 2.0 +   
- **C#‑Grundlagen:** Wenn Sie eine „Hello World“-App schreiben können, sind Sie bereit  

### Installation von GroupDocs.Annotation
Der einfachste Weg ist über NuGet. Wählen Sie die Methode, die zu Ihrem Workflow passt:

**Option 1: Package‑Manager‑Konsole**  
```shell
Install-Package GroupDocs.Annotation -Version 25.4.0
```  

**Option 2: .NET CLI**  
```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```  

**Pro‑Tipp:** In eingeschränkten Unternehmensumgebungen laden Sie das Paket manuell von [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/) herunter und referenzieren die DLL lokal.

### Lizenzierung einfach gemacht
- **Entwicklung & Test:** Beginnen Sie mit der kostenlosen Testversion für volle Funktionalität.  
- **Erweiterte Evaluation:** Holen Sie sich eine [temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/) (ausgestellt in ~5 Minuten).  
- **Produktion:** Kaufen Sie eine kommerzielle Lizenz über [GroupDocs Purchase](https://purchase.groupdocs.com/buy); eine Lizenz deckt alle Bereitstellungsszenarien ab.

## Wie man unterstützte Dateiformate programmgesteuert abruft

Laden Sie die unterstützten Formate mit einem einzigen Aufruf von `FileType.GetSupportedFileTypes()` und transformieren Sie das Ergebnis in eine benutzerfreundliche Liste, die in UI‑Steuerelementen angezeigt oder zur Validierung verwendet werden kann. Die Methode gibt eine schreibgeschützte Sammlung von `FileType`‑Objekten zurück, von denen jedes eine Erweiterung und Beschreibung enthält, was die Weiterverarbeitung erleichtert.

```csharp
var supported = FileType.GetSupportedFileTypes()
                         .OrderBy(f => f.Extension)
                         .Select(f => new { f.Extension, f.Description })
                         .ToList();
```

Der obige Code fragt die internen Metadaten von GroupDocs.Annotation ab, sortiert die Erweiterungen alphabetisch und gibt eine leichte Sammlung zurück, die Sie an UI‑Steuerelemente binden oder zur Validierung nutzen können.

### Definitionsanker: FileType‑Klasse
Die `FileType`‑Klasse ist die Darstellung von GroupDocs.Annotation für ein einzelnes Dokumentformat und stellt Eigenschaften wie `Extension` und `Description` bereit.  

### Schritt‑für‑Schritt‑Durchlauf
1. **Add the namespace** – `using GroupDocs.Annotation;` am Anfang Ihrer Datei.  
2. **Call the static method** – `FileType.GetSupportedFileTypes()` liefert ein `IEnumerable<FileType>`.  
3. **Sort and project** – Verwenden Sie LINQs `OrderBy` und `Select`, um die Daten für die Anzeige aufzubereiten.  
4. **Render** – Durchlaufen Sie die Liste in einer Konsole, MVC‑View oder WinForms‑Dropdown.

```csharp
using System;
using System.Linq;
using GroupDocs.Annotation; // This is where the FileType class lives
```  

## Wie man die Formatliste für den Produktionseinsatz cached

Caching eliminiert wiederholte Metadaten‑Abfragen und garantiert Sub‑Millisekunden‑Antwortzeiten für jede Anforderung, was in stark frequentierten Anwendungen kritisch ist. Durch das Speichern der Formatliste in einem statischen Feld und das lazy Laden beim ersten Zugriff stellen Sie sicher, dass die Daten nur einmal abgerufen und dann effizient über den gesamten Anwendungslebenszyklus hinweg wiederverwendet werden.

```csharp
public static class FormatCache
{
    private static IReadOnlyList<FileType> _cachedFormats;

    public static IReadOnlyList<FileType> SupportedFormats =>
        _cachedFormats ??= FileType.GetSupportedFileTypes()
                                    .OrderBy(f => f.Extension)
                                    .ToList();
}
```

```csharp
public static void RunGetSupportedFileFormats()
{
    // Retrieve collection of supported file types, ordered by their extension
    IEnumerable<FileType> fileTypes = FileType.GetSupportedFileTypes().OrderBy(fileType => fileType.Extension);

    // Iterate through each FileType object and output its details to the console
    foreach (FileType fileType in fileTypes)
        Console.WriteLine($"{fileType.Extension} - {fileType.Name}");
}
```  

**Warum cachen?** Das unterstützte Formatset ändert sich zur Laufzeit nie, sodass ein einziger Ladevorgang beim Anwendungsstart CPU‑Zyklen spart und potenzielle Lizenzprüfungen bei jedem Aufruf vermeidet.

## Häufige Probleme und Lösungen

### Problem 1: „GroupDocs.Annotation not found“ Compiler‑Fehler
**Direkte Antwort:** Vergewissern Sie sich, dass das NuGet‑Paket korrekt installiert ist, reinigen und bauen Sie die Lösung neu, und stellen Sie sicher, dass Ihr Ziel‑Framework mit den unterstützten Versionen des Pakets übereinstimmt.  

**Ursachenanalyse** – Fehlende Referenz, inkompatibles Framework oder Unternehmens‑Package‑Source‑Einschränkungen.

### Problem 2: Leere oder unvollständige Formatliste
**Direkte Antwort:** Eine abgelaufene oder falsch konfigurierte Lizenz schneidet die Liste häufig ab; wenden Sie eine gültige Lizenzdatei an und starten Sie die Anwendung neu.  

**Mögliche Ursachen:**  
- Lizenzdatei nicht geladen (`License.SetLicense("license.json")` fehlt)  
- Beschädigtes NuGet‑Paket  
- Fehlende native Abhängigkeiten  

**Schnelle Lösung:**  
```csharp
public static void DiagnoseFormatIssues()
{
    try
    {
        var formats = FileType.GetSupportedFileTypes();
        Console.WriteLine($"Found {formats.Count()} supported formats");
        
        if (formats.Count() < 10) // GroupDocs supports many more formats
        {
            Console.WriteLine("Warning: Fewer formats than expected. Check your license.");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Cannot retrieve formats: {ex.Message}");
        // This usually indicates a licensing or installation issue
    }
}
```  

### Problem 3: Leistungsprobleme durch häufige Aufrufe
**Direkte Antwort:** Cachen Sie das Ergebnis wie im Abschnitt „Wie man cached“ gezeigt; nachfolgende Aufrufe werden zu O(1).  

**Implementierungstipp:** Speichern Sie die Liste in `MemoryCache` oder einem statischen Feld und aktualisieren Sie sie nur, wenn Sie die Bibliothek upgraden.

```csharp
public static class FileFormatCache
{
    private static List<FileType> _cachedFormats;
    
    public static IEnumerable<FileType> GetSupportedFormats()
    {
        if (_cachedFormats == null)
        {
            _cachedFormats = FileType.GetSupportedFileTypes().ToList();
        }
        return _cachedFormats;
    }
}
```  

## Praktische Anwendungen und Anwendungsfälle

### Wie man Datei‑Uploads mit der gecachten Liste validiert
Wenn ein Benutzer ein Dokument übermittelt, extrahieren Sie die Dateierweiterung und vergleichen Sie sie mit der zwischengespeicherten Sammlung:

```csharp
bool IsSupported(string fileName)
{
    var ext = Path.GetExtension(fileName).ToLowerInvariant();
    return FormatCache.SupportedFormats.Any(f => f.Extension.Equals(ext, StringComparison.OrdinalIgnoreCase));
}
```

```csharp
public bool IsFileSupported(string fileName)
{
    var extension = Path.GetExtension(fileName).ToLowerInvariant();
    var supportedExtensions = GetSupportedExtensions();
    return supportedExtensions.Contains(extension);
}
```  

### Wie man einen dynamischen Dateifilter für einen OpenFileDialog erzeugt
Füllen Sie die Filterzeichenfolge des Dialogs aus den gecachten Erweiterungen, sodass die UI stets die Fähigkeiten der Bibliothek widerspiegelt:

```csharp
var filter = string.Join(";", FormatCache.SupportedFormats.Select(f => $"*{f.Extension}"));
openFileDialog.Filter = $"Supported Files ({filter})|{filter}";
```

```csharp
public string GenerateFileFilter()
{
    var extensions = GetSupportedExtensions();
    var filterParts = extensions.Select(ext => $"*{ext}");
    return $"Supported Documents|{string.Join(";", filterParts)}";
}
```  

### Wie man nicht unterstützte Dateien bei einem Batch‑Ordnerscan überspringt
Durchlaufen Sie ein Verzeichnis, prüfen Sie jede Datei mit `IsSupported` und verarbeiten Sie nur die gültigen:

```csharp
foreach (var file in Directory.EnumerateFiles(folderPath))
{
    if (IsSupported(file))
    {
        // Process with GroupDocs.Annotation
    }
}
```

```csharp
public void ProcessDirectory(string directoryPath)
{
    var supportedExtensions = GetSupportedExtensions();
    var files = Directory.GetFiles(directoryPath)
        .Where(file => supportedExtensions.Contains(Path.GetExtension(file).ToLowerInvariant()));
    
    foreach (var file in files)
    {
        // Process each supported file
        ProcessAnnotationFile(file);
    }
}
```  

## Leistungsüberlegungen und bewährte Praktiken

- **Cache einmal, überall wiederverwenden** – Initialisieren Sie `FormatCache` beim Anwendungsstart (z. B. in `Program.cs` oder `Startup.cs`).  
- **Lazy loading** – Die statische Eigenschaft sorgt dafür, dass die Liste nur beim ersten Bedarf geladen wird, wodurch unnötiger Start‑Overhead vermieden wird.  
- **Thread safety** – Der Null‑Coalescing‑Operator (`??=`) ist für die meisten Single‑Thread‑Szenarien sicher; bei hochgradig nebenläufigen Apps wickeln Sie den Cache in ein `Lazy<IReadOnlyList<FileType>>`.  
- **Dispose annotation objects** – Während die Formatliste selbst keiner Entsorgung bedarf, sollten alle von Ihnen erstellten `Annotation`‑Instanzen in `using`‑Blöcken gekapselt werden, um native Ressourcen freizugeben.  

### Fehlerbehandlungsmuster für Lizenzprobleme
Umwickeln Sie das Abrufen der Formate mit einem try‑catch‑Block, der gezielt nach `LicenseException` sucht und eine klare Meldung protokolliert:

```csharp
try
{
    var formats = FileType.GetSupportedFileTypes();
}
catch (LicenseException ex)
{
    // Log and fallback to a hard‑coded minimal list
}
```

```csharp
public static class RobustFormatRetrieval
{
    public static IEnumerable<FileType> GetSupportedFormatsWithFallback()
    {
        try
        {
            return FileType.GetSupportedFileTypes();
        }
        catch (LicenseException)
        {
            // Handle licensing issues gracefully
            LogWarning("License issue detected. Using basic format list.");
            return GetBasicFormatList();
        }
        catch (Exception ex)
        {
            LogError($"Unexpected error retrieving formats: {ex}");
            return Enumerable.Empty<FileType>();
        }
    }
    
    private static IEnumerable<FileType> GetBasicFormatList()
    {
        // Return a hardcoded list of common formats as fallback
        // This ensures your app doesn't break completely
        return new[] { FileType.Pdf, FileType.Docx, FileType.Xlsx };
    }
}
```  

## Fehlerbehebungs‑Leitfaden

### Schritt 1: Installation überprüfen
Führen Sie `dotnet list package` aus oder prüfen Sie die NuGet‑Konsolenausgabe auf Warnungen.  

```csharp
public static void VerifyInstallation()
{
    try
    {
        var version = typeof(FileType).Assembly.GetName().Version;
        Console.WriteLine($"GroupDocs.Annotation version: {version}");
        
        var formatCount = FileType.GetSupportedFileTypes().Count();
        Console.WriteLine($"Supported formats: {formatCount}");
        
        if (formatCount > 50) // Expected range
        {
            Console.WriteLine("✓ Installation looks good!");
        }
        else
        {
            Console.WriteLine("⚠ Possible installation or licensing issue");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"✗ Installation problem: {ex.Message}");
    }
}
```  

### Schritt 2: Lizenzstatus prüfen
Stellen Sie sicher, dass `License.SetLicense("path/to/license.json")` vor jedem API‑Aufruf ausgeführt wird.  

### Schritt 3: Umgebungseinschränkungen diagnostizieren
- Bestätigen Sie, dass die .NET‑Runtime‑Version den Anforderungen der Bibliothek entspricht.  
- Vergewissern Sie sich, dass der Prozess Lese‑/Schreibrechte für den temporären Ordner hat, den GroupDocs.Annotation verwendet.  

## Häufig gestellte Fragen

**Q: Welche Dateiformate unterstützt GroupDocs.Annotation tatsächlich?**  
A: Die Bibliothek unterstützt **über 50 Formate**, darunter PDF, DOCX, XLSX, PPTX, JPEG, PNG, TIFF und viele weitere. Führen Sie den Beispielcode aus, um die genaue Liste für Ihre Lizenz abzurufen.

**Q: Warum erhalte ich weniger unterstützte Formate als erwartet?**  
A: Das weist in der Regel auf ein Lizenzproblem hin – entweder ein abgelaufener Test oder eine falsch geladene Lizenzdatei. Laden Sie eine gültige Lizenz erneut und starten Sie die Anwendung neu.

**Q: Kann ich ein einzelnes Format prüfen, ohne die gesamte Liste zu holen?**  
A: Es gibt keine direkte „IsSupported“-Methode; der empfohlene Ansatz ist, die vollständige Liste einmal zu cachen und lokal für schnelle Lookups abzufragen.

**Q: Wie sollte ich die Formatprüfung in einer stark frequentierten Web‑App handhaben?**  
A: Initialisieren Sie den Format‑Cache beim Anwendungsstart (z. B. in `ConfigureServices`) und speichern Sie ihn in einem statischen oder Singleton‑Service. Das eliminiert den Overhead pro Anfrage.

**Q: Was passiert, wenn GetSupportedFileTypes() eine Ausnahme wirft?**  
A: Ausnahmen resultieren typischerweise aus Lizenz‑ oder beschädigten Installationen. Prüfen Sie die Paket‑Integrität, installieren Sie ggf. neu und stellen Sie sicher, dass die Lizenzdatei zugänglich ist.

## Fazit

Sie verfügen nun über eine vollständige, produktionsreife Strategie für **how to retrieve formats** mit GroupDocs.Annotation in .NET. Von dem einzeiligen API‑Aufruf über robustes Caching, Fehlerbehandlung bis hin zur UI‑Integration können Sie Uploads sicher validieren, dynamische Dateifilter erzeugen und skalierbare Annotation‑Pipelines aufbauen.

**Nächste Schritte:**  
- Erkunden Sie die [GroupDocs.Annotation API Reference](https://reference.groupdocs.com/annotation/net/) für tiefere Annotation‑Funktionen.  
- Treten Sie der Community im [Support Forum](https://forum.groupdocs.com/c/annotation/) bei, falls Sie Randfall‑Szenarien begegnen.  
- Experimentieren Sie mit der Kombination von Formatvalidierung und benutzerdefinierten Geschäftsregeln (z. B. Größenlimits, Sicherheits‑Scans), um Ihren Dokumenten‑Workflow weiter zu härten.

## Ressourcen
- [GroupDocs Releases](https://releases.groupdocs.com/annotation/net/)
- [Neueste Version herunterladen](https://releases.groupdocs.com/annotation/net/)
- [Kostenlose Testversion](https://releases.groupdocs.com/annotation/net/)
- [temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/)
- [Temporäre Lizenz](https://purchase.groupdocs.com/temporary-license/)
- [GroupDocs Kauf](https://purchase.groupdocs.com/buy)
- [Lizenzkauf](https://purchase.groupdocs.com/buy)
- [Dokumentation](https://docs.groupdocs.com/annotation/net/)
- [API‑Referenz](https://reference.groupdocs.com/annotation/net/)
- [GroupDocs.Annotation API‑Referenz](https://reference.groupdocs.com/annotation/net/)
- [Support‑Forum](https://forum.groupdocs.com/c/annotation/)
- [Community‑Support](https://forum.groupdocs.com/c/annotation/)

**Zuletzt aktualisiert:** 2026-06-26  
**Getestet mit:** GroupDocs.Annotation 25.4.0 for .NET  
**Autor:** GroupDocs  

```csharp
public static List<string> GetSupportedExtensions()
{
    try
    {
        var supportedExtensions = FileType.GetSupportedFileTypes()
            .Select(ft => ft.Extension.ToLowerInvariant())
            .OrderBy(ext => ext)
            .ToList();
        
        return supportedExtensions;
    }
    catch (Exception ex)
    {
        // Log the error appropriately in your application
        Console.WriteLine($"Error retrieving supported formats: {ex.Message}");
        return new List<string>();
    }
}
```

## Verwandte Tutorials

- [Dokument‑Metadaten‑Extraktion .NET – Vollständiger Leitfaden zu GroupDocs.Annotation](/annotation/net/document-information/)
- [PDF von URL laden .NET – Vollständiger Leitfaden mit GroupDocs.Annotation](/annotation/net/document-loading-essentials/load-document-from-url/)
- [Dokument‑Vorschau .NET Tutorials – Vollständiger GroupDocs.Annotation‑Leitfaden](/annotation/net/document-preview/)