---
"description": "Scopri come aggiungere facilmente annotazioni di testo ondulate ai documenti utilizzando Groupdocs.Annotation per .NET. Migliora la collaborazione e i processi di revisione dei documenti."
"linktitle": "Aggiungi annotazioni ondulate al testo del documento"
"second_title": "API .NET di GroupDocs.Annotation"
"title": "Aggiungi annotazioni ondulate al testo del documento"
"url": "/it/net/unlocking-annotation-power/add-text-squiggly-annotation/"
"weight": 25
---

# Aggiungi annotazioni ondulate al testo del documento

## Introduzione

Groupdocs.Annotation per .NET è una libreria versatile che consente agli sviluppatori di integrare facilmente funzionalità di annotazione affidabili nelle loro applicazioni .NET. Che si lavori con PDF, documenti Word o altri formati di file diffusi, Groupdocs.Annotation offre una soluzione completa per annotare e migliorare la collaborazione sui documenti.

## Prerequisiti

Prima di immergerti nel tutorial, assicurati di avere i seguenti prerequisiti:

## Importa spazi dei nomi

Assicuratevi di importare gli spazi dei nomi necessari per accedere alle funzionalità fornite da Groupdocs.Annotation per .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

Ora che abbiamo chiarito i prerequisiti, scomponiamo il processo di aggiunta di annotazioni di testo ondulate in più passaggi.

## Passaggio 1: definire il percorso di output

Definisci il percorso in cui verrà salvato il documento annotato.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Passaggio 2: inizializzare l'annotatore

Inizializzare l'oggetto Annotator fornendo il percorso del documento di input.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Il codice di annotazione va qui
}
```

## Passaggio 3: creare un'annotazione ondulata

Crea un oggetto SquigglyAnnotation e specificane le proprietà.

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

## Passaggio 4: aggiungere annotazioni

Aggiungere l'annotazione ondulata creata al documento.

```csharp
annotator.Add(squiggly);
```

## Passaggio 5: Salva il documento

Salva il documento annotato nel percorso di output specificato.

```csharp
annotator.Save(outputPath);
```

## Passaggio 6: conferma della visualizzazione

Visualizza un messaggio di conferma dell'avvenuto salvataggio del documento annotato.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione

In conclusione, Groupdocs.Annotation per .NET offre agli sviluppatori un solido set di strumenti per integrare perfettamente le funzionalità di annotazione dei documenti nelle loro applicazioni .NET. Seguendo questa guida passo passo, potrete aggiungere senza sforzo annotazioni di testo ondulate ai vostri documenti, migliorando la collaborazione e i processi di revisione dei documenti.

## Domande frequenti

### D: Groupdocs.Annotation può supportare l'annotazione su vari formati di file?

R: Sì, Groupdocs.Annotation supporta l'annotazione su un'ampia gamma di formati di file, tra cui PDF, documenti Word, fogli Excel e altro ancora.

### D: Groupdocs.Annotation è compatibile sia con le applicazioni desktop che con quelle web?

R: Assolutamente! Groupdocs.Annotation può essere integrato perfettamente sia nelle applicazioni desktop che in quelle web, offrendo flessibilità e versatilità.

### D: Sono disponibili opzioni di licenza per Groupdocs.Annotation?

R: Sì, Groupdocs.Annotation offre opzioni di licenza flessibili, pensate su misura per soddisfare le esigenze individuali o aziendali, tra cui licenze temporanee per scopi di prova.

### D: È possibile personalizzare le annotazioni create utilizzando Groupdocs.Annotation?

R: Certamente! Groupdocs.Annotation offre ampie opzioni di personalizzazione per le annotazioni, consentendo agli sviluppatori di adattarle alle proprie esigenze specifiche.

### D: Groupdocs.Annotation offre supporto e documentazione per gli sviluppatori?

R: Certo! Groupdocs.Annotation fornisce una documentazione completa e forum di supporto dedicati per aiutare gli sviluppatori a utilizzare le sue funzionalità in modo efficace.