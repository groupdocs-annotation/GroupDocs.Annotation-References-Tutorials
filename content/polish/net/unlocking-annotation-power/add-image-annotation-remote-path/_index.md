---
"description": "Dowiedz się, jak dodawać adnotacje obrazów do dokumentów za pomocą GroupDocs.Annotation dla .NET. Ulepsz zarządzanie dokumentami dzięki zaawansowanym możliwościom adnotacji."
"linktitle": "Dodaj adnotację obrazu do dokumentu (ścieżka zdalna)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dodaj adnotację obrazu do dokumentu (ścieżka zdalna)"
"url": "/pl/net/unlocking-annotation-power/add-image-annotation-remote-path/"
type: docs
"weight": 15
---

# Dodaj adnotację obrazu do dokumentu (ścieżka zdalna)

## Wstęp
W tym samouczku przejdziemy przez proces dodawania adnotacji obrazów do dokumentu przy użyciu GroupDocs.Annotation dla .NET. Ta biblioteka zapewnia potężne narzędzia do adnotacji różnych typów dokumentów programowo.
## Wymagania wstępne
Zanim zaczniemy, upewnij się, że masz następujące rzeczy:
1. GroupDocs.Annotation dla .NET: Pobierz i zainstaluj bibliotekę z [Tutaj](https://releases.groupdocs.com/annotation/net/).
2. Środowisko programistyczne: Upewnij się, że masz przygotowane działające środowisko programistyczne do tworzenia oprogramowania .NET.
3. Dokument: Przygotuj dokument, który chcesz adnotować. W tym samouczku założymy, że masz dokument PDF o nazwie `input.pdf`.
4. Obraz do adnotacji: Wybierz obraz, którego chcesz użyć do adnotacji. Upewnij się, że masz gotowy adres URL obrazu lub ścieżkę lokalną.

## Importuj przestrzenie nazw
Zanim zaczniemy kodować, zaimportujmy niezbędne przestrzenie nazw:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Krok 1: Ustaw ścieżkę wyjściową
Najpierw zdefiniuj ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Zainicjuj Adnotator
Utwórz instancję `Annotator` klasę i określ dokument wejściowy.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kod adnotacji będzie tutaj
}
```
## Krok 3: Dodaj adnotację do obrazu
Teraz dodajmy adnotację obrazu do dokumentu. Określimy właściwości adnotacji obrazu, takie jak pozycja, krycie, numer strony i ścieżka obrazu.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Określ położenie adnotacji
    CreatedOn = DateTime.Now, // Ustaw datę utworzenia
    Opacity = 0.7, // Ustaw krycie (od 0 do 1)
    PageNumber = 0, // Podaj numer strony
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Podaj adres URL obrazu
};
annotator.Add(image); // Dodaj adnotację do obrazu
```
## Krok 4: Zapisz dokument
Zapisz dokument z adnotacjami w określonej ścieżce wyjściowej.
```csharp
annotator.Save(outputPath);
```
## Krok 5: Wyświetl ścieżkę wyjściową
Poinformuj użytkownika o pomyślnym zapisaniu dokumentu i wyświetl ścieżkę wyjściową.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek
W tym samouczku nauczyliśmy się, jak dodawać adnotacje obrazów do dokumentu za pomocą GroupDocs.Annotation dla .NET. Wykonując te kroki, możesz ulepszyć swoje aplikacje do zarządzania dokumentami dzięki potężnym możliwościom adnotacji.
## Najczęściej zadawane pytania
### Czy GroupDocs.Annotation można używać z innymi formatami dokumentów niż PDF?
Tak, GroupDocs.Annotation obsługuje różne formaty dokumentów, w tym Word, Excel, PowerPoint i inne.
### Czy GroupDocs.Annotation jest kompatybilny z .NET Core?
Tak, GroupDocs.Annotation jest kompatybilny zarówno z .NET Framework, jak i .NET Core.
### Czy mogę dostosować wygląd adnotacji?
Tak, możesz dostosować wygląd adnotacji, np. kolor, krycie i rozmiar.
### Czy GroupDocs.Annotation obsługuje funkcje wspólnych adnotacji?
Tak, GroupDocs.Annotation oferuje funkcje wspólnego tworzenia adnotacji, umożliwiające wspólną pracę nad dokumentami w czasie rzeczywistym.
### Czy jest dostępna wersja próbna do przetestowania?
Tak, możesz otrzymać bezpłatną wersję próbną GroupDocs.Annotation od [Tutaj](https://releases.groupdocs.com/).