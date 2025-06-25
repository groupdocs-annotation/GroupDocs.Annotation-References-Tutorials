---
"description": "Dowiedz się, jak dodawać adnotacje obrazów do dokumentów za pomocą GroupDocs.Annotation dla .NET. Z łatwością rozszerz możliwości przetwarzania dokumentów."
"linktitle": "Dodaj adnotację obrazu do dokumentu (ścieżka lokalna)"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dodaj adnotację obrazu do dokumentu (ścieżka lokalna)"
"url": "/pl/net/unlocking-annotation-power/add-image-annotation-local-path/"
"weight": 14
---

# Dodaj adnotację obrazu do dokumentu (ścieżka lokalna)

## Wstęp
GroupDocs.Annotation for .NET to potężna biblioteka, która umożliwia programistom programowe dodawanie różnych typów adnotacji do dokumentów. W tym samouczku nauczymy się, jak dodawać adnotacje obrazów do dokumentu za pomocą ścieżki lokalnej.
## Wymagania wstępne
Zanim zaczniemy, upewnij się, że spełniasz następujące wymagania wstępne:
1. Podstawowa znajomość języka programowania C#.
2. Program Visual Studio zainstalowany w systemie.
3. Biblioteka GroupDocs.Annotation for .NET jest zainstalowana lub ma tutorialsd w projekcie.
4. Dokument wejściowy (np. PDF) i plik obrazu do adnotacji.
## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw do pliku C#. Te przestrzenie nazw zapewniają dostęp do klas i metod wymaganych do pracy z GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Krok 1: Zdefiniuj ścieżkę wyjściową
Zdefiniuj ścieżkę wyjściową, w której zostanie zapisany dokument z adnotacjami.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Krok 2: Zainicjuj Adnotator
Zainicjuj adnotator, podając ścieżkę do dokumentu wejściowego.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Kod adnotacji wpisz tutaj
}
```
## Krok 3: Utwórz adnotację obrazu
Utwórz instancję `ImageAnnotation` klasę i określ jej właściwości, takie jak pozycja, krycie, numer strony i ścieżka do obrazu.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## Krok 4: Dodaj adnotację
Dodaj utworzoną adnotację obrazu do dokumentu za pomocą `Add` metoda adnotatora.
```csharp
annotator.Add(image);
```
## Krok 5: Zapisz dokument
Zapisz dokument z adnotacjami w ścieżce wyjściowej.
```csharp
annotator.Save(outputPath);
```
## Krok 6: Wyświetl ścieżkę wyjściową
Wyświetl komunikat informujący o pomyślnym zapisaniu dokumentu i lokalizacji pliku wyjściowego.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek
tym samouczku nauczyliśmy się, jak dodawać adnotacje obrazów do dokumentu za pomocą GroupDocs.Annotation dla .NET. Postępując zgodnie z tymi prostymi krokami, możesz zwiększyć możliwości przetwarzania dokumentów dzięki zaawansowanym funkcjom adnotacji.
## Najczęściej zadawane pytania
### Czy mogę dodawać adnotacje do dokumentów innych niż PDF?
Tak, GroupDocs.Annotation obsługuje różne formaty dokumentów, w tym Word, Excel, PowerPoint i inne.
### Czy GroupDocs.Annotation jest kompatybilny z .NET Core?
Tak, GroupDocs.Annotation jest kompatybilny zarówno z .NET Framework, jak i .NET Core.
### Czy mogę dostosować wygląd adnotacji?
Oczywiście, możesz dostosować wygląd, rozmiar, kolor i inne właściwości adnotacji według swoich wymagań.
### Czy GroupDocs.Annotation obsługuje wspólne adnotacje?
Tak, GroupDocs.Annotation oferuje funkcje wspólnego adnotowania, dzięki którym wielu użytkowników może jednocześnie adnotować dokumenty.
### Gdzie mogę znaleźć dodatkową pomoc i wsparcie?
Aby uzyskać pomoc i wsparcie społeczności, odwiedź forum GroupDocs.Annotation.