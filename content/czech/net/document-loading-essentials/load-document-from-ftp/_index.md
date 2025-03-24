---
title: Načíst dokument z FTP
linktitle: Načíst dokument z FTP
second_title: GroupDocs.Annotation .NET API
description: Vylepšete své aplikace .NET pomocí GroupDocs.Annotation pro bezproblémové anotování dokumentů. Včetně návodu krok za krokem.
weight: 12
url: /cs/net/document-loading-essentials/load-document-from-ftp/
---

# Načíst dokument z FTP

## Úvod
GroupDocs.Annotation for .NET je všestranná knihovna navržená k usnadnění anotací dokumentů v aplikacích .NET bez námahy. Ať už pracujete s PDF, dokumenty Microsoft Office, obrázky nebo jinými formáty, tato knihovna poskytuje jednotné řešení pro přidávání anotací, jako jsou komentáře, zvýraznění a tvary, pro zlepšení spolupráce a správy dokumentů.
## Předpoklady
Než se ponoříte do výukového programu, ujistěte se, že máte splněny následující předpoklady:
1. Znalost C#: Znalost programovacího jazyka C# je nezbytná pro pochopení a implementaci příkladů kódu uvedených v tomto tutoriálu.
2.  GroupDocs.Annotation for .NET: Ujistěte se, že jste si stáhli a nainstalovali GroupDocs.Annotation for .NET z webu[odkaz ke stažení](https://releases.groupdocs.com/annotation/net/). Pro úspěšnou integraci knihovny do vašeho projektu .NET postupujte podle pokynů k instalaci.
## Import jmenných prostorů
Abyste mohli využívat funkce GroupDocs.Annotation pro .NET, musíte do svého projektu C# importovat požadované jmenné prostory. Následuj tyto kroky:

V rámci projektu C# zahrňte na začátek souboru kódu potřebné jmenné prostory:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Nyní se pojďme ponořit do procesu načítání dokumentu z FTP a přidávání anotací k němu pomocí GroupDocs.Annotation for .NET.
## Krok 1: Definujte výstupní cestu
Zadejte výstupní cestu, kam bude dokument s poznámkami uložen.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Načtěte dokument z FTP
Načtěte dokument ze serveru FTP pomocí zadané cesty k souboru.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Zde bude přidán kód anotace
}
```
## Krok 3: Přidejte anotaci
Definujte a přidejte požadovanou anotaci, jako je oblastní anotace, do dokumentu.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Krok 4: Uložte dokument s poznámkami
Uložte dokument s poznámkami do zadané výstupní cesty.
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
## Krok 6: Vytvořte požadavek FTP
Vygenerujte požadavek FTP ke stažení souboru.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Krok 7: Získejte Stream souborů
Načtěte datový proud souboru z odpovědi FTP.
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
Na závěr, GroupDocs.Annotation for .NET umožňuje vývojářům bezproblémově integrovat funkce anotací dokumentů do jejich aplikací .NET. Podle podrobného průvodce popsaného v tomto tutoriálu můžete efektivně načítat dokumenty z FTP a snadno přidávat anotace, čímž se zlepší spolupráce a správa dokumentů v rámci vašich aplikací.
## FAQ
### Je GroupDocs.Annotation for .NET kompatibilní se všemi formáty dokumentů?
Ano, GroupDocs.Annotation for .NET podporuje širokou škálu formátů dokumentů, včetně PDF, dokumentů Microsoft Office, obrázků a dalších.
### Mohu upravit vzhled anotací přidaných pomocí GroupDocs.Annotation for .NET?
GroupDocs.Annotation for .NET samozřejmě nabízí rozsáhlé možnosti přizpůsobení vzhledu anotací, včetně barev, stylů a tvarů.
### Poskytuje GroupDocs.Annotation for .NET podporu pro služby cloudového úložiště?
Ano, GroupDocs.Annotation for .NET se bez problémů integruje s oblíbenými službami cloudového úložiště, což vám umožňuje načítat a ukládat dokumenty ze služeb jako Dropbox, Google Drive a OneDrive.
### Je k dispozici zkušební verze pro GroupDocs.Annotation pro .NET?
 Ano, funkce GroupDocs.Annotation for .NET můžete prozkoumat stažením bezplatné zkušební verze z webu[stránka vydání](https://releases.groupdocs.com/).
### Jak mohu získat technickou pomoc nebo podporu pro GroupDocs.Annotation pro .NET?
 Pro technickou pomoc, řešení problémů nebo obecné dotazy můžete navštívit GroupDocs.Annotation for .NET[Fórum podpory](https://forum.groupdocs.com/c/annotation/10).