---
title: Usuń adnotacje za pomocą opcji zapisywania w .NET
linktitle: Usuń adnotacje za pomocą opcji zapisywania w .NET
second_title: GroupDocs.Adnotacja .NET API
description: Dowiedz się, jak usuwać adnotacje z plików PDF i innych dokumentów w platformie .NET za pomocą GroupDocs.Annotation. Przewodnik krok po kroku z przykładami kodu.
type: docs
weight: 14
url: /pl/net/removing-annotations/remove-annotations-using-save-options/
---
## Wstęp

GroupDocs.Annotation dla .NET to potężne narzędzie, które umożliwia programistom łatwe dodawanie funkcji adnotacji do aplikacji .NET. Niezależnie od tego, czy pracujesz w systemie zarządzania dokumentami, platformie współpracy, czy innej aplikacji wymagającej przetwarzania dokumentów, GroupDocs.Annotation zapewnia kompleksowy zestaw funkcji umożliwiających bezproblemowe dodawanie adnotacji do plików PDF i innych formatów dokumentów.

## Warunki wstępne

Zanim zagłębisz się w świat dodawania adnotacji do dokumentów za pomocą GroupDocs.Annotation dla .NET, upewnij się, że spełnione są następujące wymagania wstępne:

### 1. Zainstaluj GroupDocs.Annotation dla .NET

 Rozpocznij od pobrania i zainstalowania GroupDocs.Annotation dla .NET. Najnowszą wersję można pobrać ze strony[download page](https://releases.groupdocs.com/annotation/net/).

## Importowanie przestrzeni nazw

Aby rozpocząć korzystanie z GroupDocs.Annotation w projekcie .NET, musisz zaimportować niezbędne przestrzenie nazw. Oto przestrzenie nazw, których będziesz często używać:

```csharp
using GroupDocs.Annotation.Options;
using System;
using System.IO;
```


Przyjrzyjmy się teraz procesowi usuwania adnotacji z dokumentu za pomocą funkcji Zapisz opcje w .NET:

## Krok 1: Zdefiniuj ścieżkę wyjściową

Najpierw określ ścieżkę wyjściową, w której zostanie zapisany dokument z usuniętymi adnotacjami. Możesz skorzystać z`Path.Combine` metoda połączenia ścieżki katalogu z nazwą pliku wyjściowego.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Krok 2: Zainicjuj adnotator

 Następnie zainicjuj instancję`Annotator` class podając ścieżkę do dokumentu zawierającego adnotacje.

```csharp
using (Annotator annotator = new Annotator("annotated.pdf"))
{
    // Tutaj zostanie umieszczony kod usuwania adnotacji
}
```

## Krok 3: Zapisz dokument z usunięciem adnotacji

 Teraz skorzystaj z`Save` metoda`Annotator` klasa wraz z`SaveOptions` , aby zapisać dokument z usuniętymi adnotacjami. w`SaveOptions` , Ustaw`AnnotationTypes` własność do`AnnotationType.None` , aby usunąć wszystkie adnotacje.

```csharp
annotator.Save(outputPath, new SaveOptions() { AnnotationTypes = AnnotationType.None });
```

## Krok 4: Wyświetl komunikat o powodzeniu

Na koniec wyświetl komunikat o powodzeniu wskazujący, że dokument został pomyślnie zapisany z usuniętymi adnotacjami.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek

Podsumowując, GroupDocs.Annotation dla .NET upraszcza proces usuwania adnotacji z dokumentów. Postępując zgodnie ze szczegółowym przewodnikiem opisanym powyżej, programiści mogą bezproblemowo zintegrować funkcję usuwania adnotacji ze swoimi aplikacjami .NET.

## Często zadawane pytania

### P: Czy GroupDocs.Annotation może usuwać adnotacje z dokumentów w innych formatach niż PDF?

O: GroupDocs.Annotation obsługuje różne formaty dokumentów, w tym PDF, Word, Excel i PowerPoint, umożliwiając usuwanie adnotacji z szerokiej gamy dokumentów.

### P: Czy GroupDocs.Annotation można łatwo zintegrować z istniejącymi projektami .NET?

O: Tak, GroupDocs.Annotation zapewnia prosty interfejs API i obszerną dokumentację, ułatwiając programistom integrację funkcji adnotacji z aplikacjami .NET.

### P: Czy GroupDocs.Annotation obsługuje selektywne usuwanie adnotacji?

O: Tak, GroupDocs.Annotation pozwala programistom określić, jakie typy adnotacji mają zostać usunięte, co daje im elastyczność w zarządzaniu adnotacjami w dokumentach.

### P: Czy mogę bezpłatnie wypróbować GroupDocs.Annotation przed zakupem?

 O: Tak, możesz pobrać bezpłatną wersję próbną GroupDocs.Annotation z witryny[strona z wydaniami](https://releases.groupdocs.com/) aby zapoznać się z jego funkcjami przed podjęciem decyzji o zakupie.

### P: Gdzie mogę uzyskać pomoc dotyczącą GroupDocs.Annotation?

 O: Aby uzyskać pomoc techniczną i wsparcie społeczności, możesz odwiedzić stronę[Forum GroupDocs.Adnotacje](https://forum.groupdocs.com/c/annotation/10).