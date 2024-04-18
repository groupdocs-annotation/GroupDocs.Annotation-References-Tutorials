---
title: Aggiungi annotazione di testo ondulata al documento
linktitle: Aggiungi annotazione di testo ondulata al documento
second_title: API GroupDocs.Annotation .NET
description: Scopri come aggiungere facilmente annotazioni di testo ondulate ai documenti utilizzando Groupdocs.Annotation per .NET. Migliorare la collaborazione e i processi di revisione dei documenti.
type: docs
weight: 25
url: /it/net/unlocking-annotation-power/add-text-squiggly-annotation/
---
## introduzione

Groupdocs.Annotation per .NET è una libreria versatile che consente agli sviluppatori di integrare facilmente robuste funzionalità di annotazione nelle proprie applicazioni .NET. Che tu stia lavorando con PDF, documenti Word o altri formati di file popolari, Groupdocs.Annotation fornisce una soluzione perfetta per annotare e migliorare la collaborazione sui documenti.

## Prerequisiti

Prima di immergerti nel tutorial, assicurati di disporre dei seguenti prerequisiti:

## Importa spazi dei nomi

Assicurati di importare gli spazi dei nomi necessari per accedere alle funzionalità fornite da Groupdocs.Annotation per .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Ora che abbiamo coperto i prerequisiti, suddividiamo il processo di aggiunta di annotazioni ondulate al testo in più passaggi.

## Passaggio 1: definire il percorso di output

Definire il percorso in cui verrà salvato il documento annotato.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Passaggio 2: inizializza Annotatore

Inizializza l'oggetto Annotator fornendo il percorso del documento di input.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Il codice di annotazione va qui
}
```

## Passaggio 3: crea un'annotazione ondulata

Crea un oggetto SquigglyAnnotation e specifica le sue proprietà.

```csharp
SquigglyAnnotation squiggly = new SquigglyAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is squiggly annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    SquigglyColor = 1422623,
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
    }
};
```

## Passaggio 4: aggiungi annotazione

Aggiungi l'annotazione ondulata creata al documento.

```csharp
annotator.Add(squiggly);
```

## Passaggio 5: salva il documento

Salva il documento annotato nel percorso di output specificato.

```csharp
annotator.Save(outputPath);
```

## Passaggio 6: Visualizza conferma

Visualizza un messaggio che conferma il corretto salvataggio del documento annotato.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione

In conclusione, Groupdocs.Annotation per .NET fornisce agli sviluppatori un robusto set di strumenti per integrare perfettamente le funzionalità di annotazione dei documenti nelle loro applicazioni .NET. Seguendo questa guida passo passo, puoi aggiungere facilmente annotazioni di testo ondulate ai tuoi documenti, migliorando la collaborazione e i processi di revisione dei documenti.

## Domande frequenti

### D: Groupdocs.Annotation può supportare l'annotazione su vari formati di file?

R: Sì, Groupdocs.Annotation supporta l'annotazione su un'ampia gamma di formati di file, inclusi PDF, documenti Word, fogli Excel e altro.

### D: Groupdocs.Annotation è compatibile sia con le applicazioni desktop che con quelle web?

R: Assolutamente! Groupdocs.Annotation può essere perfettamente integrato sia nelle applicazioni desktop che in quelle web, offrendo flessibilità e versatilità.

### D: Sono disponibili opzioni di licenza per Groupdocs.Annotation?

R: Sì, Groupdocs.Annotation offre opzioni di licenza flessibili su misura per soddisfare le esigenze individuali o aziendali, comprese licenze temporanee a scopo di prova.

### D: È possibile personalizzare le annotazioni create utilizzando Groupdocs.Annotation?

R: Certamente! Groupdocs.Annotation fornisce ampie opzioni di personalizzazione per le annotazioni, consentendo agli sviluppatori di adattare le annotazioni ai loro requisiti specifici.

### D: Groupdocs.Annotation offre supporto e documentazione per gli sviluppatori?

R: Infatti! Groupdocs.Annotation fornisce documentazione completa e forum di supporto dedicati per assistere gli sviluppatori nell'utilizzo efficace delle sue funzionalità.