---
title: Dodaj adnotację ze strzałką do dokumentu
linktitle: Dodaj adnotację ze strzałką do dokumentu
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak dodawać adnotacje ze strzałkami do dokumentów za pomocą GroupDocs.Annotation dla .NET. Bez wysiłku zwiększ przejrzystość i interaktywność dokumentów.
type: docs
weight: 11
url: /pl/net/unlocking-annotation-power/add-arrow-annotation/
---
## Wstęp
W tym samouczku przeprowadzimy Cię przez proces dodawania adnotacji strzałkowych do dokumentów za pomocą GroupDocs.Annotation dla .NET. Adnotacje ze strzałkami są przydatne do wskazywania kierunku lub wskazywania określonych elementów w dokumencie.
## Warunki wstępne
Zanim zaczniesz, upewnij się, że masz następujące elementy:
1.  GroupDocs.Annotation dla .NET: Zainstaluj bibliotekę GroupDocs.Annotation dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/annotation/net/).
2. Środowisko programistyczne: Upewnij się, że masz środowisko programistyczne skonfigurowane do programowania .NET, w tym Visual Studio lub inne preferowane IDE.

## Importuj przestrzenie nazw
Po pierwsze, musisz zaimportować niezbędne przestrzenie nazw, aby uzyskać dostęp do wymaganych klas i metod adnotacji.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Krok 1: Zainicjuj adnotator
Zainicjuj adnotator, podając ścieżkę pliku dokumentu wejściowego.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 2: Utwórz adnotację ze strzałką
Utwórz instancję klasy ArrowAnnotation i zdefiniuj jej właściwości, takie jak położenie, komunikat, przezroczystość, kolor pisaka, styl, szerokość itp.
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
 Dodaj adnotację ze strzałką do dokumentu za pomocą`Add` metoda adnotatora.
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
Pomyślnie dodałeś adnotację ze strzałką do swojego dokumentu za pomocą GroupDocs.Annotation for .NET.

## Wniosek
tym samouczku omówiliśmy proces dodawania adnotacji strzałek do dokumentów przy użyciu GroupDocs.Annotation dla .NET. Wykonując poniższe kroki, możesz wzbogacić swoje dokumenty o wyraźne wskaźniki kierunkowe, dzięki czemu będą bardziej informacyjne i wciągające.
## Często zadawane pytania
### Czy mogę dostosować wygląd adnotacji ze strzałką?
Tak, możesz dostosować różne właściwości, takie jak kolor, styl, szerokość i przezroczystość, aby dopasować je do swoich preferencji i wymagań dokumentu.
### Czy GroupDocs.Annotation jest kompatybilny ze wszystkimi formatami dokumentów?
GroupDocs.Annotation obsługuje szeroką gamę formatów dokumentów, w tym PDF, DOCX, PPTX, XLSX i inne.
### Czy mogę programowo dodawać adnotacje przy użyciu GroupDocs.Annotation?
Tak, GroupDocs.Annotation udostępnia interfejsy API umożliwiające programowe dodawanie, edytowanie i usuwanie adnotacji z dokumentów.
### Czy GroupDocs.Annotation oferuje bezpłatną wersję próbną?
 Tak, możesz bezpłatnie wypróbować GroupDocs.Annotation, pobierając go ze strony[Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę uzyskać pomoc techniczną dotyczącą GroupDocs.Annotation?
Aby uzyskać pomoc techniczną i pomoc, odwiedź forum GroupDocs.Annotation[Tutaj](https://forum.groupdocs.com/c/annotation/10).