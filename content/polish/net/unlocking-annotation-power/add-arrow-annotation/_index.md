---
"description": "Dowiedz się, jak dodawać adnotacje strzałek do dokumentów za pomocą GroupDocs.Annotation dla .NET. Zwiększ przejrzystość i interaktywność dokumentu bez wysiłku."
"linktitle": "Dodaj adnotację strzałki do dokumentu"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Dodaj adnotację strzałki do dokumentu"
"url": "/pl/net/unlocking-annotation-power/add-arrow-annotation/"
type: docs
"weight": 11
---

# Dodaj adnotację strzałki do dokumentu

## Wstęp
W tym samouczku przeprowadzimy Cię przez proces dodawania adnotacji strzałek do dokumentów za pomocą GroupDocs.Annotation dla .NET. Adnotacje strzałek są przydatne do wskazywania kierunku lub wskazywania określonych elementów w dokumencie.
## Wymagania wstępne
Zanim zaczniesz, upewnij się, że masz następujące rzeczy:
1. GroupDocs.Annotation dla .NET: Zainstaluj bibliotekę GroupDocs.Annotation dla .NET. Możesz ją pobrać z [Tutaj](https://releases.groupdocs.com/annotation/net/).
2. Środowisko programistyczne: Upewnij się, że masz przygotowane środowisko programistyczne do tworzenia aplikacji .NET, w tym Visual Studio lub inne preferowane środowisko IDE.

## Importuj przestrzenie nazw
Najpierw należy zaimportować niezbędne przestrzenie nazw, aby uzyskać dostęp do wymaganych klas i metod adnotacji.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Zainicjuj Adnotator
Zainicjuj adnotator, podając ścieżkę do pliku dokumentu wejściowego.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 2: Utwórz adnotację strzałki
Utwórz instancję klasy ArrowAnnotation i zdefiniuj jej właściwości, takie jak pozycja, komunikat, krycie, kolor pióra, styl, szerokość itp.
```csharp
	ArrowAnnotation arrow = new ArrowAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		CreatedOn = DateTime.Now,
		Message = "This is arrow annotation",
		Opacity = 0.7,
		PageNumber = 0,
		PenColor = 65535,
		PenStyle = PenStyle.Dot,
		PenWidth = 3,
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
		}
	};
```
## Krok 3: Dodaj adnotację
Dodaj adnotację strzałki do dokumentu za pomocą `Add` metoda adnotatora.
```csharp
	annotator.Add(arrow);
```
## Krok 4: Zapisz dokument
Zapisz dokument z adnotacjami w określonej ścieżce wyjściowej.
```csharp
	annotator.Save(outputPath);
}
```
## Krok 5: Wyświetl potwierdzenie
Wyświetl komunikat potwierdzający pomyślne zapisanie dokumentu.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Teraz dodałeś adnotację strzałki do dokumentu za pomocą GroupDocs.Annotation dla platformy .NET.

## Wniosek
W tym samouczku omówiliśmy proces dodawania adnotacji strzałek do dokumentów za pomocą GroupDocs.Annotation dla .NET. Wykonując te kroki, możesz wzbogacić swoje dokumenty o wyraźne wskaźniki kierunkowe, dzięki czemu będą bardziej informacyjne i angażujące.
## Najczęściej zadawane pytania
### Czy mogę dostosować wygląd adnotacji strzałki?
Tak, możesz dostosować różne właściwości, takie jak kolor, styl, szerokość i krycie, aby spełnić wymagania Twojego samouczka i dokumentu.
### Czy GroupDocs.Annotation jest kompatybilny ze wszystkimi formatami dokumentów?
GroupDocs.Annotation obsługuje szeroką gamę formatów dokumentów, w tym PDF, DOCX, PPTX, XLSX i inne.
### Czy mogę dodawać adnotacje programowo, używając GroupDocs.Annotation?
Tak, GroupDocs.Annotation udostępnia interfejsy API, które umożliwiają programowe dodawanie, edytowanie i usuwanie adnotacji z dokumentów.
### Czy GroupDocs.Annotation oferuje bezpłatny okres próbny?
Tak, możesz wypróbować GroupDocs.Annotation bezpłatnie, pobierając go ze strony [Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę uzyskać pomoc techniczną dotyczącą GroupDocs.Annotation?
Aby uzyskać pomoc techniczną i wsparcie, możesz odwiedzić forum GroupDocs.Annotation [Tutaj](https://forum.groupdocs.com/c/annotation/10).