---
title: Načíst dokument z Azure
linktitle: Načíst dokument z Azure
second_title: GroupDocs.Annotation .NET API
description: Naučte se, jak anotovat dokumenty v .NET pomocí GroupDocs.Annotation. Podrobný kurz pro bezproblémovou integraci s Azure Blob Storage.
type: docs
weight: 11
url: /cs/net/document-loading-essentials/load-document-from-azure/
---
## Úvod
V oblasti správy dokumentů a spolupráce se GroupDocs.Annotation for .NET ukazuje jako robustní řešení, které umožňuje bezproblémové funkce anotací a značek v aplikacích .NET. Tento výukový program se ponoří do složitosti využití GroupDocs.Annotation pro .NET k anotaci dokumentů a nabízí podrobné pokyny od nezbytných předpokladů až po pokročilé použití.
## Předpoklady
Než se ponoříte do GroupDocs.Annotation pro .NET, ujistěte se, že máte splněny následující předpoklady:
1. Instalace .NET Framework: GroupDocs.Annotation pro .NET vyžaduje kompatibilní běhové prostředí .NET. Ujistěte se, že máte v systému nainstalované rozhraní .NET Framework.
2. Přístup ke knihovně GroupDocs.Annotation: Získejte přístup ke knihovně GroupDocs.Annotation for .NET buď jejím stažením z webu nebo prostřednictvím správců balíčků, jako je NuGet.
3. Dokument k anotaci: Připravte dokument (např. PDF), který chcete anotovat. Ujistěte se, že je dokument přístupný buď místně, nebo prostřednictvím služby cloudového úložiště, jako je Azure Blob Storage.

## Import jmenných prostorů
Chcete-li začít anotovat dokumenty pomocí GroupDocs.Annotation for .NET, importujte do svého projektu potřebné jmenné prostory. Tento krok zajistí, že budete mít přístup k požadovaným třídám a funkcím.
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using Microsoft.WindowsAzure.Storage;
using Microsoft.WindowsAzure.Storage.Auth;
using Microsoft.WindowsAzure.Storage.Blob;
using System;
using System.IO;
```

## Načíst dokument z Azure
Chcete-li anotovat dokument uložený v Azure Blob Storage, postupujte takto:
### Krok 1: Nastavte výstupní cestu
Definujte výstupní cestu, kam bude dokument s poznámkami uložen.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Krok 2: Stáhněte si dokument
 Načtěte dokument z Azure Blob Storage vyvoláním`DownloadFile` metoda.
```csharp
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
    // Logika anotace
    annotator.Save(outputPath);
}
```
## Stáhněte soubor z Azure Blob Storage
 Chcete-li stáhnout dokument z Azure Blob Storage, implementujte`DownloadFile` metoda.
### Krok 1: Načtěte objekt Blob
Otevřete kontejner Azure Blob Storage a načtěte požadovaný objekt blob.
```csharp
CloudBlobContainer container = GetContainer();
CloudBlob blob = container.GetBlobReference(blobName);
```
### Krok 2: Stáhněte si obsah blob
Stáhněte si obsah blob do paměťového streamu.
```csharp
MemoryStream memoryStream = new MemoryStream();
blob.DownloadToStream(memoryStream);
memoryStream.Position = 0;
return memoryStream;
```
## Získejte Azure Blob Storage Container
 Chcete-li komunikovat s Azure Blob Storage, implementujte`GetContainer` metoda.
### Krok 1: Inicializujte přihlašovací údaje úložiště
Poskytněte potřebné přihlašovací údaje k účtu a informace o koncovém bodu.
```csharp
string accountName = "***";
string accountKey = "***";
string endpoint = $"https://{accountName}.blob.core.windows.net/";
```
### Krok 2: Vytvořte Blob Client
Vytvořte klienta pro interakci s Azure Blob Storage.
```csharp
CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(storageCredentials, new Uri(endpoint), null, null, null);
CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
```
### Krok 3: Načtěte odkaz na kontejner
Získejte odkaz na určený kontejner.
```csharp
CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
```
### Krok 4: Vytvořte kontejner, pokud neexistuje
Ujistěte se, že kontejner existuje, a pokud ne, vytvořte jej.
```csharp
container.CreateIfNotExists();
```

## Závěr
GroupDocs.Annotation for .NET umožňuje vývojářům robustní možnosti anotací dokumentů, které lze hladce integrovat do aplikací .NET. Podle kroků uvedených v tomto kurzu můžete efektivně využít funkce GroupDocs.Annotation k anotaci dokumentů uložených v Azure Blob Storage.
#### FAQ
### Je GroupDocs.Annotation for .NET kompatibilní se všemi formáty dokumentů?
GroupDocs.Annotation podporuje širokou škálu formátů dokumentů, včetně PDF, DOCX, PPTX a dalších.
### Lze poznámky upravit podle konkrétních požadavků?
Ano, GroupDocs.Annotation nabízí rozsáhlé možnosti přizpůsobení pro anotace, což uživatelům umožňuje upravovat vzhled, chování a metadata.
### Je GroupDocs.Annotation vhodný pro společné anotace dokumentů?
Absolutně! GroupDocs.Annotation usnadňuje společné anotace dokumentů tím, že umožňuje více uživatelům přidávat, upravovat a recenzovat anotace současně.
### Nabízí GroupDocs.Annotation kompatibilitu napříč platformami?
Ano, GroupDocs.Annotation je navržena tak, aby bezproblémově fungovala na různých platformách, včetně Windows, Linuxu a macOS.
### Je pro uživatele GroupDocs.Annotation k dispozici technická podpora?
Ano, GroupDocs poskytuje komplexní technickou podporu prostřednictvím svých fór a vyhrazených kanálů podpory.