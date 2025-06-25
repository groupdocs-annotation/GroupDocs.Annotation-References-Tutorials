---
"description": "Dowiedz się, jak dodawać adnotacje graficzne do tekstu w środowisku .NET za pomocą GroupDocs.Annotation, aby zapewnić efektywne zarządzanie dokumentami i współpracę."
"linktitle": "Umieść adnotację obrazu nad tekstem"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Umieść adnotację obrazu nad tekstem"
"url": "/pl/net/advanced-usage/put-image-annotation-over-text/"
"weight": 21
---

# Umieść adnotację obrazu nad tekstem

## Wstęp
W świecie rozwoju .NET GroupDocs.Annotation oferuje potężne rozwiązanie do dodawania adnotacji do dokumentów, dzięki czemu współpraca i zarządzanie dokumentami są bardziej wydajne. Jednym z powszechnych wymagań jest umieszczanie adnotacji obrazów nad tekstem, co można bezproblemowo osiągnąć za pomocą GroupDocs.Annotation dla .NET.
## Wymagania wstępne
Zanim rozpoczniesz proces dodawania adnotacji do obrazów za pomocą GroupDocs.Annotation dla platformy .NET, upewnij się, że masz następujące elementy:
1. GroupDocs.Annotation dla biblioteki .NET: Pobierz i zainstaluj bibliotekę z [Tutaj](https://releases.groupdocs.com/annotation/net/).
2. Środowisko programistyczne: Skonfiguruj odpowiednie środowisko programistyczne, takie jak Visual Studio lub inne środowisko IDE .NET.
3. Pliki dokumentów i obrazów: Przygotuj plik dokumentu (PDF, DOCX itp.) i plik obrazu, którego chcesz użyć do adnotacji.
4. Podstawowa znajomość języka C#: Znajomość języka programowania C# jest konieczna do zaimplementowania fragmentów kodu udostępnionych w tym samouczku.

## Importuj przestrzenie nazw
Zanim przejdziesz do procesu adnotacji, upewnij się, że zaimportowałeś niezbędne przestrzenie nazw do swojego projektu C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Krok 1: Zdefiniuj ścieżkę wyjściową
Najpierw zdefiniuj ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Krok 2: Zainicjuj Adnotator
Zainicjuj `Annotator` obiekt, podając ścieżkę do dokumentu wejściowego:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kod adnotacji będzie tutaj
}
```
## Krok 3: Utwórz adnotację obrazu
Utwórz `ImageAnnotation` obiekt o pożądanych właściwościach, takich jak wymiary pola, krycie, numer strony, ścieżka obrazu i indeks Z:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## Krok 4: Dodaj adnotację
Dodaj adnotację obrazu do dokumentu za pomocą `Add` metoda `Annotator` obiekt:
```csharp
annotator.Add(image);
```
## Krok 5: Zapisz dokument z adnotacjami
Zapisz dokument z adnotacjami w określonej ścieżce wyjściowej:
```csharp
annotator.Save(outputPath);
```
## Krok 6: Wyświetl komunikat o powodzeniu
Wyświetl komunikat o powodzeniu zawierający ścieżkę do dokumentu z adnotacjami:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek
Podsumowując, dodawanie adnotacji obrazu do tekstu w aplikacjach .NET przy użyciu GroupDocs.Annotation to prosty proces. Postępując zgodnie z przewodnikiem krok po kroku zawartym w tym samouczku, możesz sprawnie adnotować dokumenty i zwiększyć możliwości współpracy i zarządzania dokumentami w swoich projektach .NET.
## Najczęściej zadawane pytania
### Czy mogę dodawać adnotacje do dokumentów innych niż pliki PDF?
Tak, GroupDocs.Annotation obsługuje różne formaty dokumentów, takie jak DOCX, XLSX, PPTX i inne.
### Czy jest dostępna bezpłatna wersja próbna GroupDocs.Annotation?
Tak, możesz pobrać bezpłatną wersję próbną ze strony [Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę uzyskać pomoc techniczną dotyczącą GroupDocs.Annotation?
Możesz uzyskać pomoc na forum społeczności GroupDocs.Annotation [Tutaj](https://forum.groupdocs.com/c/annotation/10).
### Czy potrzebuję tymczasowej licencji do celów testowych?
Tak, możesz uzyskać tymczasową licencję od [Tutaj](https://purchase.groupdocs.com/temporary-license/) w celach testowych.
### Czy mogę dostosować wygląd adnotacji?
Tak, GroupDocs.Annotation oferuje różne opcje umożliwiające dostosowanie wyglądu adnotacji, takie jak kolor, krycie, rozmiar czcionki itp.