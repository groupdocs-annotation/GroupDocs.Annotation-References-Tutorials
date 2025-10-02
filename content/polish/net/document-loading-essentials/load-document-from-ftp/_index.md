---
"description": "Ulepsz swoje aplikacje .NET dzięki GroupDocs.Annotation, aby zapewnić bezproblemową adnotację dokumentów. Dołączono samouczek krok po kroku."
"linktitle": "Załaduj dokument z FTP"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Załaduj dokument z FTP"
"url": "/pl/net/document-loading-essentials/load-document-from-ftp/"
type: docs
"weight": 12
---

# Załaduj dokument z FTP

## Wstęp
GroupDocs.Annotation for .NET to wszechstronna biblioteka zaprojektowana w celu ułatwienia możliwości adnotacji dokumentów w aplikacjach .NET bez wysiłku. Niezależnie od tego, czy masz do czynienia z plikami PDF, dokumentami Microsoft Office, obrazami czy innymi formatami, ta biblioteka zapewnia ujednolicone rozwiązanie do dodawania adnotacji, takich jak komentarze, wyróżnienia i kształty, w celu usprawnienia współpracy i zarządzania dokumentami.
## Wymagania wstępne
Zanim przejdziesz do samouczka, upewnij się, że spełnione są następujące wymagania wstępne:
1. Znajomość języka C#: Znajomość języka programowania C# jest niezbędna do zrozumienia i implementacji przykładów kodu przedstawionych w tym samouczku.
2. GroupDocs.Annotation dla .NET: Upewnij się, że pobrano i zainstalowano GroupDocs.Annotation dla .NET z [link do pobrania](https://releases.groupdocs.com/annotation/net/). Postępuj zgodnie z instrukcjami instalacji, aby pomyślnie zintegrować bibliotekę z projektem .NET.
## Importuj przestrzenie nazw
Aby wykorzystać GroupDocs.Annotation dla funkcjonalności .NET, musisz zaimportować wymagane przestrzenie nazw do swojego projektu C#. Wykonaj następujące kroki:

W projekcie C# umieść niezbędne przestrzenie nazw na początku pliku kodu:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```

Teraz przyjrzyjmy się bliżej procesowi ładowania dokumentu z FTP i dodawania do niego adnotacji za pomocą GroupDocs.Annotation dla platformy .NET.
## Krok 1: Zdefiniuj ścieżkę wyjściową
Określ ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Załaduj dokument z FTP
Pobierz dokument z serwera FTP korzystając z podanej ścieżki dostępu.
```csharp
string filePath = "sample.pdf";
using (Annotator annotator = new Annotator(GetFileFromFtp(filePath)))
{
    // Tutaj zostanie dodany kod adnotacji
}
```
## Krok 3: Dodaj adnotację
Zdefiniuj i dodaj do dokumentu żądaną adnotację, np. adnotację obszaru.
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
Pobierz strumień plików z odpowiedzi FTP.
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
Podsumowując, GroupDocs.Annotation dla .NET umożliwia deweloperom bezproblemową integrację funkcji adnotacji dokumentów z aplikacjami .NET. Postępując zgodnie z przewodnikiem krok po kroku opisanym w tym samouczku, możesz sprawnie ładować dokumenty z FTP i łatwo dodawać adnotacje, usprawniając współpracę i zarządzanie dokumentami w swoich aplikacjach.
## Najczęściej zadawane pytania
### Czy GroupDocs.Annotation dla platformy .NET jest kompatybilny ze wszystkimi formatami dokumentów?
Tak, GroupDocs.Annotation dla platformy .NET obsługuje szeroką gamę formatów dokumentów, w tym pliki PDF, dokumenty pakietu Microsoft Office, obrazy i inne.
### Czy mogę dostosować wygląd adnotacji dodawanych za pomocą GroupDocs.Annotation dla platformy .NET?
Zdecydowanie, GroupDocs.Annotation dla platformy .NET oferuje rozbudowane opcje dostosowywania wyglądu adnotacji, w tym kolorów, stylów i kształtów.
### Czy GroupDocs.Annotation dla platformy .NET zapewnia obsługę usług przechowywania danych w chmurze?
Tak, GroupDocs.Annotation dla platformy .NET płynnie integruje się z popularnymi usługami przechowywania danych w chmurze, umożliwiając ładowanie i zapisywanie dokumentów z usług takich jak Dropbox, Google Drive i OneDrive.
### Czy jest dostępna wersja próbna GroupDocs.Annotation dla .NET?
Tak, możesz zapoznać się z funkcjami GroupDocs.Annotation dla platformy .NET, pobierając bezpłatną wersję próbną ze strony [strona wydania](https://releases.groupdocs.com/).
### W jaki sposób mogę uzyskać pomoc techniczną lub wsparcie dla GroupDocs.Annotation dla platformy .NET?
Aby uzyskać pomoc techniczną, rozwiązać problemy lub zadać ogólne pytania, odwiedź witrynę GroupDocs.Annotation for .NET [forum wsparcia](https://forum.groupdocs.com/c/annotation/10).