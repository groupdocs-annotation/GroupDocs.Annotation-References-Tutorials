---
title: Załaduj dokument z dysku lokalnego
linktitle: Załaduj dokument z dysku lokalnego
second_title: GroupDocs.Adnotacja .NET API
description: Odblokuj moc adnotacji w dokumentach dzięki GroupDocs.Annotation dla .NET. Bezproblemowo integruj funkcje adnotacji z aplikacjami .NET.
type: docs
weight: 13
url: /pl/net/document-loading-essentials/load-document-from-local-disk/
---
## Wstęp
Uwolnienie potencjału adnotacji w dokumentach nigdy nie było łatwiejsze dzięki GroupDocs.Annotation dla .NET. To potężne narzędzie umożliwia programistom bezproblemową integrację niezawodnych funkcji adnotacji z aplikacjami .NET. W tym obszernym przewodniku przeprowadzimy Cię krok po kroku przez proces wykorzystania GroupDocs.Annotation dla .NET do dodawania adnotacji do dokumentów. Niezależnie od tego, czy jesteś doświadczonym programistą, czy dopiero zaczynasz, ten samouczek wyposaży Cię w wiedzę niezbędną do usprawnienia współpracy nad dokumentami i usprawnienia przepływu pracy.
## Warunki wstępne
Zanim zagłębisz się w adnotacje do dokumentów za pomocą GroupDocs.Annotation dla .NET, upewnij się, że spełniasz następujące wymagania wstępne:
1. Podstawowa znajomość języka C#: Znajomość podstaw języka programowania C# jest niezbędna.
2. Instalacja GroupDocs.Annotation dla .NET: Pobierz i zainstaluj GroupDocs.Annotation dla .NET z[Tutaj](https://releases.groupdocs.com/annotation/net/).
3. Środowisko programistyczne: skonfiguruj środowisko programistyczne w programie Visual Studio lub dowolnym zgodnym środowisku IDE.

## Importuj przestrzenie nazw
Aby rozpocząć dodawanie adnotacji do dokumentów za pomocą GroupDocs.Annotation for .NET, zaimportuj niezbędne przestrzenie nazw do swojego projektu:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Krok 1: Załaduj dokument z dysku lokalnego
Najpierw musisz załadować dokument z dysku lokalnego. Użyj następującego fragmentu kodu:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Krok 2: Zdefiniuj obszar adnotacji
Następnie zdefiniuj obszar adnotacji. W tym przykładzie utworzymy AreaAnnotation:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Krok 3: Zapisz dokument z adnotacjami
Po dokonaniu adnotacji dokument zapisz go z adnotacjami:
```csharp
    annotator.Save(outputPath);
}
```
## Krok 4: Wyświetl komunikat o powodzeniu
Na koniec wyświetl komunikat o powodzeniu ze ścieżką wyjściową:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Wniosek
Podsumowując, GroupDocs.Annotation dla .NET zapewnia solidne rozwiązanie umożliwiające integrację funkcji adnotacji w dokumentach z aplikacjami .NET. Postępując zgodnie z tym szczegółowym przewodnikiem, możesz bez wysiłku dodawać adnotacje do dokumentów i usprawniać współpracę w swoich projektach.
## Często zadawane pytania
### Czy przed zakupem mogę wypróbować GroupDocs.Annotation dla .NET?
 Tak, możesz pobrać bezpłatną wersję próbną ze strony[Tutaj](https://releases.groupdocs.com/).
### Gdzie mogę znaleźć dokumentację GroupDocs.Annotation dla .NET?
 Można uzyskać dostęp do dokumentacji[Tutaj](https://reference.groupdocs.com/annotation/net/).
### Jak mogę uzyskać tymczasową licencję na GroupDocs.Annotation dla .NET?
 Licencję tymczasową można uzyskać od[Tutaj](https://purchase.groupdocs.com/temporary-license/).
### Czy dostępna jest obsługa GroupDocs.Annotation dla platformy .NET?
 Tak, pomoc można znaleźć na forum GroupDocs[Tutaj](https://forum.groupdocs.com/c/annotation/10).
### Gdzie mogę kupić GroupDocs.Annotation dla .NET?
 Możesz kupić GroupDocs.Annotation dla .NET[Tutaj](https://purchase.groupdocs.com/buy).