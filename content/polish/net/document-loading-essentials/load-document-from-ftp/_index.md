---
title: Załaduj dokument z FTP
linktitle: Załaduj dokument z FTP
second_title: GroupDocs.Adnotacja .NET API
description: Ulepsz swoje aplikacje .NET za pomocą GroupDocs.Annotation, aby móc bezproblemowo dodawać adnotacje do dokumentów. W zestawie tutorial krok po kroku.
weight: 12
url: /pl/net/document-loading-essentials/load-document-from-ftp/
---
## Wstęp
GroupDocs.Annotation dla .NET to wszechstronna biblioteka zaprojektowana w celu ułatwienia możliwości dodawania adnotacji do dokumentów w aplikacjach .NET. Niezależnie od tego, czy masz do czynienia z plikami PDF, dokumentami Microsoft Office, obrazami czy innymi formatami, ta biblioteka zapewnia ujednolicone rozwiązanie do dodawania adnotacji, takich jak komentarze, wyróżnienia i kształty, w celu usprawnienia współpracy i zarządzania dokumentami.
## Warunki wstępne
Zanim przejdziesz do samouczka, upewnij się, że spełniasz następujące wymagania wstępne:
1. Znajomość języka C#: Biegłość w języku programowania C# jest niezbędna do zrozumienia i wdrożenia przykładów kodu podanych w tym samouczku.
2.  GroupDocs.Annotation dla .NET: Pamiętaj, aby pobrać i zainstalować GroupDocs.Annotation dla .NET ze strony[link do pobrania](https://releases.groupdocs.com/annotation/net/). Postępuj zgodnie z instrukcjami instalacji, aby pomyślnie zintegrować bibliotekę z projektem .NET.
## Importuj przestrzenie nazw
Aby móc korzystać z funkcjonalności GroupDocs.Annotation for .NET, musisz zaimportować wymagane przestrzenie nazw do swojego projektu C#. Wykonaj następujące kroki:

W projekcie C# umieść niezbędne przestrzenie nazw na początku pliku kodu:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Teraz przyjrzyjmy się procesowi ładowania dokumentu z FTP i dodawania do niego adnotacji za pomocą GroupDocs.Annotation for .NET.
## Krok 1: Zdefiniuj ścieżkę wyjściową
Określ ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Załaduj dokument z FTP
Pobierz dokument z serwera FTP, korzystając z podanej ścieżki pliku.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Kod adnotacji zostanie dodany tutaj
}
```
## Krok 3: Dodaj adnotację
Zdefiniuj i dodaj żądaną adnotację, np. adnotację obszaru, do dokumentu.
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Krok 4: Zapisz dokument z adnotacjami
Zapisz dokument z adnotacjami w określonej ścieżce wyjściowej.
```csharp
annotator.Save(outputPath);
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
## Krok 5: Pobierz plik z FTP
Zaimplementuj metodę pobierania pliku z serwera FTP.
```csharp
private static Stream GetFileFromFtp(string filePath)
{
    Uri uri = new Uri(filePath);
    FtpWebRequest request = CreateRequest(uri);
    using (WebResponse response = request.GetResponse())
        return GetFileStream(response);
}
```
## Krok 6: Utwórz żądanie FTP
Wygeneruj żądanie FTP w celu pobrania pliku.
```csharp
private static FtpWebRequest CreateRequest(Uri uri)
{
    FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
    request.Method = WebRequestMethods.Ftp.DownloadFile;
    return request;
}
```
## Krok 7: Pobierz strumień plików
Pobierz strumień pliku z odpowiedzi FTP.
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
## Wniosek
Podsumowując, GroupDocs.Annotation dla .NET umożliwia programistom bezproblemową integrację funkcji adnotacji w dokumentach z aplikacjami .NET. Postępując zgodnie ze szczegółowym przewodnikiem opisanym w tym samouczku, możesz efektywnie ładować dokumenty z FTP i z łatwością dodawać adnotacje, usprawniając współpracę i zarządzanie dokumentami w swoich aplikacjach.
## Często zadawane pytania
### Czy GroupDocs.Annotation for .NET jest kompatybilny ze wszystkimi formatami dokumentów?
Tak, GroupDocs.Annotation dla .NET obsługuje szeroką gamę formatów dokumentów, w tym PDF, dokumenty Microsoft Office, obrazy i inne.
### Czy mogę dostosować wygląd adnotacji dodanych przy użyciu GroupDocs.Annotation dla .NET?
Oczywiście GroupDocs.Annotation dla .NET oferuje szerokie opcje dostosowywania wyglądu adnotacji, w tym kolorów, stylów i kształtów.
### Czy GroupDocs.Annotation for .NET zapewnia obsługę usług przechowywania w chmurze?
Tak, GroupDocs.Annotation dla .NET bezproblemowo integruje się z popularnymi usługami przechowywania w chmurze, umożliwiając ładowanie i zapisywanie dokumentów z usług takich jak Dropbox, Google Drive i OneDrive.
### Czy dostępna jest wersja próbna programu GroupDocs.Annotation dla platformy .NET?
 Tak, możesz poznać funkcje GroupDocs.Annotation dla .NET, pobierając bezpłatną wersję próbną ze strony[strona wydania](https://releases.groupdocs.com/).
### Jak mogę uzyskać pomoc techniczną lub wsparcie dla GroupDocs.Annotation dla .NET?
 Aby uzyskać pomoc techniczną, rozwiązywanie problemów lub zadać ogólne pytania, możesz odwiedzić GroupDocs.Adnotation for .NET[forum wsparcia](https://forum.groupdocs.com/c/annotation/10).