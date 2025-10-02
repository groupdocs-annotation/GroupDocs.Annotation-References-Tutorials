---
"description": "Scopri come aggiungere annotazioni di collegamento ai documenti utilizzando Groupdocs.Annotation per .NET. Migliora la collaborazione e l'interattività senza sforzo."
"linktitle": "Aggiungi annotazione di collegamento al documento"
"second_title": "API .NET di GroupDocs.Annotation"
"title": "Aggiungi annotazione di collegamento al documento"
"url": "/it/net/unlocking-annotation-power/add-link-annotation/"
type: docs
"weight": 16
---

# Aggiungi annotazione di collegamento al documento

## Introduzione
Groupdocs.Annotation per .NET è una potente libreria che consente agli sviluppatori di integrare facilmente funzionalità di annotazione complete nelle loro applicazioni .NET. Una delle funzionalità principali è la possibilità di aggiungere annotazioni di collegamento ai documenti, migliorando la collaborazione e l'interattività.
## Prerequisiti
Prima di iniziare il processo di aggiunta di annotazioni ai link, assicurati di disporre dei seguenti prerequisiti:
- Conoscenza di base del linguaggio di programmazione C#.
- Installato Groupdocs.Annotation per la libreria .NET.
- Accesso a un documento che si desidera annotare.

## Importa spazi dei nomi
Innanzitutto, è necessario importare gli spazi dei nomi necessari per utilizzare Groupdocs.Annotation per le funzionalità .NET. Questo consente all'applicazione di accedere alle classi e ai metodi necessari per l'annotazione dei documenti.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Passaggio 1: impostare il percorso di output
Definisci il percorso in cui desideri salvare il documento annotato.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Passaggio 2: inizializzare l'annotatore
Crea un'istanza di `Annotator` classe specificando il percorso del documento che si desidera annotare.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Il codice di annotazione andrà qui
}
```
## Passaggio 3: creare un'annotazione di collegamento
Definisci un `LinkAnnotation` oggetto e specificarne le proprietà quali messaggio, opacità, numero di pagina, colore di sfondo, punti, risposte e URL.
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
    },
    Url = "https://www.google.com"
};
```
## Passaggio 4: aggiungere annotazioni
Aggiungere l'annotazione del collegamento creato al documento utilizzando `Add` metodo dell'istanza dell'annotatore.
```csharp
annotator.Add(link);
```
## Passaggio 5: Salva il documento
Salva il documento annotato nel percorso di output specificato.
```csharp
annotator.Save(outputPath);
```
## Passaggio 6: visualizzare il messaggio di successo
Informare l'utente dell'avvenuto salvataggio del documento annotato.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione
In conclusione, seguendo i passaggi precedenti, è possibile aggiungere facilmente annotazioni di collegamento ai documenti utilizzando Groupdocs.Annotation per .NET. Questo migliora la collaborazione sui documenti e offre agli utenti funzionalità interattive.
## Domande frequenti
### Groupdocs.Annotation per .NET è compatibile con tutti i tipi di documenti?
Groupdocs.Annotation per .NET supporta un'ampia gamma di formati di documenti, tra cui PDF, Word, Excel e altri.
### Posso personalizzare l'aspetto delle annotazioni?
Sì, puoi personalizzare varie proprietà delle annotazioni, come colore, opacità e dimensione, in base alle tue esigenze.
### Groupdocs.Annotation per .NET offre funzionalità di collaborazione in tempo reale?
Sì, Groupdocs.Annotation per .NET offre funzionalità di collaborazione in tempo reale che consentono a più utenti di annotare documenti contemporaneamente.
### È disponibile supporto tecnico per i prodotti Groupdocs?
Sì, il supporto tecnico per i prodotti Groupdocs è disponibile tramite il forum e il supporto [Qui](https://forum.groupdocs.com/c/annotation/10).
### Posso provare Groupdocs.Annotation per .NET prima di acquistarlo?
Sì, puoi usufruire di una prova gratuita di Groupdocs.Annotation per .NET per esplorare le sue funzionalità prima di effettuare un acquisto[Qui](https://purchase.groupdocs.com/temporary-license/).