---
"description": "Dowiedz się, jak bez wysiłku dodawać adnotacje zastępujące tekst do dokumentów .NET, korzystając z GroupDocs.Annotation dla .NET. Zwiększ możliwości manipulowania dokumentami."
"linktitle": "Dodaj adnotację zastępującą tekst do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dodaj adnotację zastępującą tekst do dokumentu"
"url": "/pl/net/unlocking-annotation-power/add-text-replacement-annotation/"
"weight": 24
---

# Dodaj adnotację zastępującą tekst do dokumentu

## Wstęp
W tym samouczku przeprowadzimy Cię przez proces dodawania adnotacji zastępującej tekst do Twoich dokumentów za pomocą GroupDocs.Annotation dla .NET. Ta potężna biblioteka pozwala deweloperom manipulować i adnotować różne typy dokumentów programowo. Pod koniec tego samouczka będziesz wyposażony w wiedzę, aby płynnie integrować adnotacje zastępujące tekst z aplikacjami .NET.
## Wymagania wstępne
Zanim zaczniemy, upewnij się, że masz zainstalowane następujące wymagania wstępne:
### 1. Zainstalowano .NET Framework
Upewnij się, że masz zainstalowany .NET Framework na swoim komputerze deweloperskim. Możesz go pobrać ze strony internetowej Microsoft.
### 2. GroupDocs.Annotation dla biblioteki .NET
Pobierz i zainstaluj bibliotekę GroupDocs.Annotation dla .NET z [strona internetowa](https://releases.groupdocs.com/annotation/net/). Ta biblioteka zapewnia niezbędne narzędzia i funkcjonalności do pracy z adnotacjami w różnych formatach dokumentów.
### 3. Konfiguracja środowiska programistycznego
Skonfiguruj preferowane środowisko programistyczne, takie jak Visual Studio, aby tworzyć i uruchamiać aplikacje .NET.

## Importuj przestrzenie nazw
Zanim przejdziemy do kodowania, zaimportujmy niezbędne przestrzenie nazw wymagane do pracy z GroupDocs.Annotation dla .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## Krok 1: Zdefiniuj ścieżkę wyjściową
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Tutaj definiujemy ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami.
## Krok 2: Zainicjuj Adnotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Tutaj zostanie umieszczony kod adnotacji
}
```
Obiekt Annotator inicjujemy, określając dokument wejściowy („input.pdf”) w bloku using, aby zapewnić prawidłowe dysponowanie zasobami.
## Krok 3: Utwórz adnotację zastępczą
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    },
    TextToReplace = "replaced text"
};
```
Tutaj tworzymy obiekt ReplacementAnnotation z różnymi właściwościami, takimi jak data utworzenia, kolor czcionki, komunikat, krycie, numer strony, kolor tła, punkty (współrzędne), odpowiedzi (komentarze) i tekst do zastąpienia.
## Krok 4: Dodaj adnotację
```csharp
annotator.Add(replacement);
```
Dodajemy utworzoną adnotację zastępczą do adnotatora.
## Krok 5: Zapisz dokument
```csharp
annotator.Save(outputPath);
```
Na koniec zapisujemy dokument z adnotacjami w określonej ścieżce wyjściowej.
## Krok 6: Wyświetl komunikat o powodzeniu
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Wyświetla się komunikat informujący o pomyślnym zapisaniu dokumentu.

## Wniosek
W tym samouczku omówiliśmy proces dodawania adnotacji zastępujących tekst do dokumentów przy użyciu GroupDocs.Annotation dla .NET. Postępując zgodnie z przewodnikiem krok po kroku i rozumiejąc wymagania wstępne, możesz łatwo zintegrować tę funkcjonalność ze swoimi aplikacjami .NET.
## Najczęściej zadawane pytania
### Czy mogę adnotować dokumenty w różnych formatach za pomocą GroupDocs.Annotation dla platformy .NET?
Tak, GroupDocs.Annotation dla platformy .NET obsługuje adnotacje w różnych formatach dokumentów, takich jak PDF, DOCX, PPTX, XLSX i inne.
### Czy GroupDocs.Annotation dla platformy .NET nadaje się zarówno do zastosowań desktopowych, jak i internetowych?
Tak, GroupDocs.Annotation dla platformy .NET można używać zarówno w aplikacjach komputerowych, jak i internetowych, co zapewnia programistom elastyczność.
### Czy mogę dostosować wygląd adnotacji dodawanych za pomocą GroupDocs.Annotation dla platformy .NET?
Oczywiście, możesz dostosować wygląd adnotacji, modyfikując właściwości takie jak kolor, krycie, czcionka itp.
### Czy GroupDocs.Annotation dla platformy .NET obsługuje funkcje wspólnych adnotacji?
Tak, GroupDocs.Annotation dla platformy .NET oferuje funkcje umożliwiające wspólne adnotowanie dokumentów, umożliwiając wielu użytkownikom jednoczesne adnotowanie dokumentów.
### Czy jest dostępna bezpłatna wersja próbna GroupDocs.Annotation dla platformy .NET?
Tak, możesz skorzystać z bezpłatnej wersji próbnej GroupDocs.Annotation dla .NET na stronie [strona internetowa](https://releases.groupdocs.com/).