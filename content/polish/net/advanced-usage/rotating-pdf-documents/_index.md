---
"description": "Dowiedz się, jak bez wysiłku obracać dokumenty PDF za pomocą Groupdocs.Annotation dla platformy .NET. Zwiększ efektywność zarządzania dokumentami."
"linktitle": "Obracanie dokumentów PDF"
"second_title": "GroupDocs.Annotation .NET API"
"title": "Obracanie dokumentów PDF"
"url": "/pl/net/advanced-usage/rotating-pdf-documents/"
type: docs
"weight": 22
---

# Obracanie dokumentów PDF

## Wstęp
Obracanie dokumentów PDF może być kluczowym zadaniem w przypadku plików, które muszą być wyświetlane lub przetwarzane inaczej. W tym samouczku pokażemy, jak obracać dokumenty PDF krok po kroku za pomocą Groupdocs.Annotation dla .NET.
## Wymagania wstępne
Zanim przejdziesz do samouczka, upewnij się, że spełniasz następujące wymagania wstępne:
1. Groupdocs.Annotation for .NET Library: Upewnij się, że pobrałeś i zainstalowałeś bibliotekę Groupdocs.Annotation for .NET. Możesz ją pobrać z [Tutaj](https://releases.groupdocs.com/annotation/net/).
2. Podstawowa wiedza z zakresu programowania w języku C#: W tym samouczku założono, że posiadasz podstawową wiedzę z zakresu programowania w języku C# i potrafisz pracować z bibliotekami .NET.

## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw do swojego projektu C#, aby uzyskać dostęp do funkcjonalności udostępnianej przez bibliotekę Groupdocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Krok 1: Załaduj dokument PDF
Zacznij od załadowania dokumentu PDF, który chcesz obrócić, za pomocą `Annotator` klasa.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Krok 2: Ustaw obrót i strony procesu
Określ kąt obrotu i strony, które chcesz obrócić. W tym przykładzie obrócimy pierwszą stronę o 90 stopni zgodnie z ruchem wskazówek zegara.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Krok 3: Zapisz obrócony dokument
Zapisz obrócony dokument PDF ze wskazanymi zmianami.
```csharp
annotator.Save("result.pdf");
```
## Krok 4: Wyświetl potwierdzenie
Poinformuj użytkownika, że dokument został pomyślnie obrócony.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Wniosek
Obracanie dokumentów PDF jest podstawową operacją, a dzięki Groupdocs.Annotation dla .NET staje się proste i wydajne. Postępując zgodnie z krokami opisanymi w tym samouczku, możesz łatwo obracać pliki PDF zgodnie ze swoimi wymaganiami.
## Najczęściej zadawane pytania
### Czy mogę obracać wiele stron w dokumencie PDF za pomocą Groupdocs.Annotation dla platformy .NET?
Tak, możesz określić wiele stron do obrócenia, dostosowując `ProcessPages` odpowiednio nieruchomość.
### Czy Groupdocs.Annotation dla platformy .NET jest kompatybilny ze wszystkimi wersjami platformy .NET?
Groupdocs.Annotation dla platformy .NET obsługuje szeroką gamę wersji platformy .NET, zapewniając zgodność z większością środowisk programistycznych.
### Czy Groupdocs.Annotation dla platformy .NET udostępnia opcje obracania dokumentów PDF w różnych kierunkach?
Tak, możesz obracać dokumenty PDF zgodnie z ruchem wskazówek zegara, przeciwnie do ruchu wskazówek zegara lub pod niestandardowymi kątami, zależnie od swoich potrzeb.
### Czy mogę zintegrować Groupdocs.Annotation dla platformy .NET z moim istniejącym systemem zarządzania dokumentami?
Zdecydowanie, Groupdocs.Annotation dla platformy .NET oferuje opcje płynnej integracji, dzięki którym możesz bez wysiłku udoskonalić możliwości zarządzania dokumentami.
### Czy jest dostępna wersja próbna Groupdocs.Annotation dla platformy .NET?
Tak, możesz otrzymać bezpłatną wersję próbną [Tutaj](https://releases.groupdocs.com/).