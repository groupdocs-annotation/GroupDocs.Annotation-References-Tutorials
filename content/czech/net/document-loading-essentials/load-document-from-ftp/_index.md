---
"description": "Vylepšete své .NET aplikace pomocí GroupDocs.Annotation pro bezproblémové anotace dokumentů. Součástí je podrobný návod."
"linktitle": "Načíst dokument z FTP"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Načíst dokument z FTP"
"url": "/cs/net/document-loading-essentials/load-document-from-ftp/"
type: docs
"weight": 12
---

# Načíst dokument z FTP

## Zavedení
GroupDocs.Annotation pro .NET je všestranná knihovna navržená pro snadné usnadnění anotací dokumentů v aplikacích .NET. Ať už pracujete s PDF, dokumenty Microsoft Office, obrázky nebo jinými formáty, tato knihovna poskytuje jednotné řešení pro přidávání anotací, jako jsou komentáře, zvýraznění a tvary, pro zlepšení spolupráce a správy dokumentů.
## Předpoklady
Než se pustíte do tutoriálu, ujistěte se, že máte splněny následující předpoklady:
1. Znalost jazyka C#: Znalost programovacího jazyka C# je nezbytná pro pochopení a implementaci příkladů kódu uvedených v tomto tutoriálu.
2. GroupDocs.Annotation pro .NET: Ujistěte se, že jste si stáhli a nainstalovali GroupDocs.Annotation pro .NET z [odkaz ke stažení](https://releases.groupdocs.com/annotation/net/)Postupujte podle pokynů k instalaci a úspěšně integrujte knihovnu do svého projektu .NET.
## Importovat jmenné prostory
Abyste mohli využívat funkce GroupDocs.Annotation pro .NET, musíte importovat požadované jmenné prostory do svého projektu C#. Postupujte takto:

V rámci projektu v C# uveďte potřebné jmenné prostory na začátek souboru s kódem:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Nyní se ponoříme do procesu načítání dokumentu z FTP a přidávání anotací k němu pomocí GroupDocs.Annotation pro .NET.
## Krok 1: Definování výstupní cesty
Zadejte výstupní cestu, kam bude uložen anotovaný dokument.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Načtení dokumentu z FTP
Načtěte dokument z FTP serveru pomocí zadané cesty k souboru.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Zde bude přidán kód anotace
}
```
## Krok 3: Přidání anotace
Definujte a přidejte do dokumentu požadovanou anotaci, například anotaci oblasti.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Krok 4: Uložení anotovaného dokumentu
Uložte anotovaný dokument do zadané výstupní cesty.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Krok 5: Načtení souboru z FTP
Implementujte metodu pro načtení souboru z FTP serveru.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## Krok 6: Vytvoření FTP požadavku
Vygenerujte FTP požadavek pro stažení souboru.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Krok 7: Získejte souborový stream
Načíst datový proud souborů z odpovědi FTP.
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
## Závěr
Závěrem lze říci, že GroupDocs.Annotation pro .NET umožňuje vývojářům bezproblémově integrovat funkce anotace dokumentů do jejich .NET aplikací. Dodržováním podrobných pokynů uvedených v tomto tutoriálu můžete efektivně načítat dokumenty z FTP a snadno přidávat anotace, což vylepší spolupráci a správu dokumentů ve vašich aplikacích.
## Často kladené otázky
### Je GroupDocs.Annotation pro .NET kompatibilní se všemi formáty dokumentů?
Ano, GroupDocs.Annotation pro .NET podporuje širokou škálu formátů dokumentů, včetně PDF, dokumentů Microsoft Office, obrázků a dalších.
### Mohu si přizpůsobit vzhled anotací přidaných pomocí GroupDocs.Annotation pro .NET?
Rozhodně, GroupDocs.Annotation pro .NET nabízí rozsáhlé možnosti přizpůsobení vzhledu anotací, včetně barev, stylů a tvarů.
### Poskytuje GroupDocs.Annotation pro .NET podporu pro cloudové úložné služby?
Ano, GroupDocs.Annotation pro .NET se bezproblémově integruje s oblíbenými cloudovými úložišti, což vám umožňuje načítat a ukládat dokumenty ze služeb, jako jsou Dropbox, Disk Google a OneDrive.
### Je k dispozici zkušební verze pro GroupDocs.Annotation pro .NET?
Ano, funkce GroupDocs.Annotation pro .NET si můžete prohlédnout stažením bezplatné zkušební verze z [stránka s vydáním](https://releases.groupdocs.com/).
### Jak mohu získat technickou pomoc nebo podporu pro GroupDocs.Annotation pro .NET?
Pro technickou pomoc, řešení problémů nebo obecné dotazy můžete navštívit stránku GroupDocs.Annotation for .NET. [fórum podpory](https://forum.groupdocs.com/c/annotation/10).