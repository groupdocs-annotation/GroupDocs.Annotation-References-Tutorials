---
title: Obracanie dokumentów PDF
linktitle: Obracanie dokumentów PDF
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak łatwo obracać dokumenty PDF za pomocą Groupdocs.Annotation dla .NET. Popraw efektywność zarządzania dokumentami.
weight: 22
url: /pl/net/advanced-usage/rotating-pdf-documents/
---

# Obracanie dokumentów PDF

## Wstęp
Obracanie dokumentów PDF może być kluczowym zadaniem w przypadku plików, które należy przeglądać lub przetwarzać w inny sposób. W tym samouczku omówimy krok po kroku, jak obracać dokumenty PDF za pomocą Groupdocs.Annotation dla .NET.
## Warunki wstępne
Zanim przejdziesz do samouczka, upewnij się, że spełniasz następujące wymagania wstępne:
1.  Biblioteka Groupdocs.Annotation dla .NET: Upewnij się, że pobrałeś i zainstalowałeś bibliotekę Groupdocs.Annotation dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/annotation/net/).
2. Podstawowa wiedza na temat programowania w języku C#: W tym samouczku założono, że masz podstawową wiedzę na temat języka programowania C# i sposobu pracy z bibliotekami .NET.

## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw do projektu C#, aby uzyskać dostęp do funkcji udostępnianych przez bibliotekę Groupdocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## Krok 1: Załaduj dokument PDF
 Rozpocznij od załadowania dokumentu PDF, który chcesz obrócić, za pomocą`Annotator` klasa.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Krok 2: Ustaw strony rotacji i przetwarzania
Określ kąt obrotu i strony, które chcesz obrócić. W tym przykładzie obrócimy pierwszą stronę o 90 stopni w prawo.
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## Krok 3: Zapisz obrócony dokument
Zapisz obrócony dokument PDF z określonymi zmianami.
```csharp
annotator.Save("result.pdf");
```
## Krok 4: Wyświetl potwierdzenie
Poinformuj użytkownika, że dokument został pomyślnie obrócony.
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## Wniosek
Obracanie dokumentów PDF to podstawowa operacja, a dzięki Groupdocs.Annotation dla .NET staje się ona prosta i wydajna. Wykonując kroki opisane w tym samouczku, możesz łatwo obracać pliki PDF zgodnie ze swoimi wymaganiami.
## Często zadawane pytania
### Czy mogę obracać wiele stron w dokumencie PDF za pomocą Groupdocs.Annotation dla .NET?
 Tak, możesz określić wiele stron do obracania, dostosowując opcję`ProcessPages` odpowiednio własność.
### Czy Groupdocs.Annotation for .NET jest kompatybilny ze wszystkimi wersjami platformy .NET?
Groupdocs.Annotation for .NET obsługuje szeroką gamę wersji platformy .NET, zapewniając zgodność z większością środowisk programistycznych.
### Czy Groupdocs.Annotation dla .NET udostępnia opcje obracania dokumentów PDF w różnych kierunkach?
Tak, możesz obracać dokumenty PDF zgodnie z ruchem wskazówek zegara, przeciwnie do ruchu wskazówek zegara lub pod niestandardowym kątem, w zależności od wymagań.
### Czy mogę zintegrować Groupdocs.Annotation for .NET z moim istniejącym systemem zarządzania dokumentami?
Absolutnie Groupdocs.Annotation dla .NET oferuje opcje płynnej integracji, dzięki czemu możesz bez wysiłku zwiększyć możliwości zarządzania dokumentami.
### Czy dostępna jest wersja próbna programu Groupdocs.Annotation dla platformy .NET?
 Tak, możesz pobrać bezpłatną wersję próbną[Tutaj](https://releases.groupdocs.com/).