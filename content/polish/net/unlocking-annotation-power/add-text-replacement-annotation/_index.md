---
title: Dodaj adnotację zastępującą tekst do dokumentu
linktitle: Dodaj adnotację zastępującą tekst do dokumentu
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak bez wysiłku dodawać adnotacje zastępujące tekst do dokumentów .NET, korzystając z GroupDocs.Annotation dla .NET. Zwiększ swoje możliwości manipulowania dokumentami.
type: docs
weight: 24
url: /pl/net/unlocking-annotation-power/add-text-replacement-annotation/
---
## Wstęp
W tym samouczku przeprowadzimy Cię przez proces dodawania adnotacji zastępującej tekst do dokumentów za pomocą GroupDocs.Annotation dla .NET. Ta potężna biblioteka pozwala programistom programowo manipulować i dodawać adnotacje do różnych typów dokumentów. Pod koniec tego samouczka będziesz wyposażony w wiedzę niezbędną do bezproblemowej integracji adnotacji zastępujących tekst z aplikacjami .NET.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz zainstalowane następujące wymagania wstępne:
### 1. Zainstalowany .NET Framework
Upewnij się, że na komputerze programistycznym zainstalowano platformę .NET Framework. Można go pobrać ze strony internetowej Microsoft.
### 2. Adnotacja GroupDocs dla biblioteki .NET
 Pobierz i zainstaluj bibliotekę GroupDocs.Annotation for .NET z pliku[strona internetowa](https://releases.groupdocs.com/annotation/net/). Biblioteka ta zapewnia niezbędne narzędzia i funkcjonalności do pracy z adnotacjami w różnych formatach dokumentów.
### 3. Konfiguracja środowiska programistycznego
Skonfiguruj preferowane środowisko programistyczne, takie jak Visual Studio, aby tworzyć i uruchamiać aplikacje .NET.

## Importuj przestrzenie nazw
Zanim zagłębimy się w kodowanie, zaimportujmy niezbędne przestrzenie nazw wymagane do pracy z GroupDocs.Annotation for .NET:
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
## Krok 2: Zainicjuj adnotator
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kod adnotacji zostanie umieszczony tutaj
}
```
Inicjujemy obiekt Annotator poprzez określenie dokumentu wejściowego („input.pdf”) w bloku using, aby zapewnić prawidłowe dysponowanie zasobami.
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
Tutaj tworzymy obiekt ZastąpienieAnnotacji z różnymi właściwościami, takimi jak data utworzenia, kolor czcionki, wiadomość, krycie, numer strony, kolor tła, punkty (współrzędne), odpowiedzi (komentarze) i tekst do zastąpienia.
## Krok 4: Dodaj adnotację
```csharp
annotator.Add(replacement);
```
Do adnotatora dodajemy utworzoną adnotację zastępczą.
## Krok 5: Zapisz dokument
```csharp
annotator.Save(outputPath);
```
Na koniec zapisujemy dokument z adnotacjami w określonej ścieżce wyjściowej.
## Krok 6: Wyświetl komunikat o powodzeniu
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Zostanie wyświetlony komunikat o powodzeniu, wskazujący, że dokument został pomyślnie zapisany.

## Wniosek
W tym samouczku omówiliśmy proces dodawania adnotacji zastępujących tekst do dokumentów przy użyciu programu GroupDocs.Annotation dla platformy .NET. Postępując zgodnie z przewodnikiem krok po kroku i rozumiejąc wymagania wstępne, można łatwo zintegrować tę funkcjonalność z aplikacjami .NET.
## Często zadawane pytania
### Czy mogę dodawać adnotacje do dokumentów w różnych formatach za pomocą GroupDocs.Annotation for .NET?
Tak, GroupDocs.Annotation dla .NET obsługuje dodawanie adnotacji do różnych formatów dokumentów, takich jak PDF, DOCX, PPTX, XLSX i innych.
### Czy GroupDocs.Annotation for .NET nadaje się zarówno do aplikacji komputerowych, jak i internetowych?
Tak, GroupDocs.Annotation for .NET może być używany zarówno w aplikacjach komputerowych, jak i internetowych, zapewniając programistom elastyczność.
### Czy mogę dostosować wygląd adnotacji dodanych przy użyciu GroupDocs.Annotation dla .NET?
Oczywiście możesz dostosować wygląd adnotacji, modyfikując właściwości, takie jak kolor, krycie, czcionka itp.
### Czy GroupDocs.Annotation for .NET oferuje obsługę funkcji wspólnych adnotacji?
Tak, GroupDocs.Annotation dla .NET udostępnia funkcje wspólnego dodawania adnotacji, umożliwiając wielu użytkownikom jednoczesne dodawanie adnotacji do dokumentów.
### Czy dostępna jest bezpłatna wersja próbna programu GroupDocs.Annotation dla platformy .NET?
Tak, możesz skorzystać z bezpłatnej wersji próbnej GroupDocs.Annotation dla .NET w witrynie[strona internetowa](https://releases.groupdocs.com/).