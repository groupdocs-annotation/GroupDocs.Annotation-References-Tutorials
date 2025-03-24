---
title: Aggiungi annotazione collegamento al documento
linktitle: Aggiungi annotazione collegamento al documento
second_title: API GroupDocs.Annotation .NET
description: Scopri come aggiungere annotazioni di collegamento ai documenti utilizzando Groupdocs.Annotation per .NET. Migliora la collaborazione e l'interattività senza sforzo.
weight: 16
url: /it/net/unlocking-annotation-power/add-link-annotation/
---

# Aggiungi annotazione collegamento al documento

## introduzione
Groupdocs.Annotation per .NET è una potente libreria che consente agli sviluppatori di integrare facilmente funzionalità di annotazione complete nelle loro applicazioni .NET. Una delle funzionalità principali che offre è la possibilità di aggiungere annotazioni di collegamento ai documenti, migliorando la collaborazione e l'interattività.
## Prerequisiti
Prima di immergerti nel processo di aggiunta delle annotazioni dei collegamenti, assicurati di possedere i seguenti prerequisiti:
- Conoscenza base del linguaggio di programmazione C#.
- Groupdocs.Annotation installato per la libreria .NET.
- Accedi a un documento che desideri annotare.

## Importa spazi dei nomi
Innanzitutto, devi importare gli spazi dei nomi necessari per utilizzare Groupdocs.Annotation per le funzionalità .NET. Ciò consente alla tua applicazione di accedere alle classi e ai metodi richiesti per annotare i documenti.
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
## Passaggio 2: inizializza Annotatore
 Crea un'istanza di`Annotator` class fornendo il percorso del documento che desideri annotare.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Il codice di annotazione andrà qui
}
```
## Passaggio 3: crea l'annotazione del collegamento
 Definire a`LinkAnnotation` oggetto e specificarne le proprietà quali messaggio, opacità, numero di pagina, colore di sfondo, punti, risposte e URL.
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
## Passaggio 4: aggiungi annotazione
 Aggiungi l'annotazione del collegamento creato al documento utilizzando il file`Add` metodo dell'istanza dell'annotatore.
```csharp
annotator.Add(link);
```
## Passaggio 5: salva il documento
Salva il documento annotato nel percorso di output specificato.
```csharp
annotator.Save(outputPath);
```
## Passaggio 6: Visualizza il messaggio di successo
Informare l'utente del corretto salvataggio del documento annotato.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione
In conclusione, seguendo i passaggi precedenti, puoi aggiungere facilmente annotazioni di collegamento ai documenti utilizzando Groupdocs.Annotation per .NET. Ciò migliora la collaborazione sui documenti e fornisce agli utenti funzionalità interattive.
## Domande frequenti
### Groupdocs.Annotation per .NET è compatibile con tutti i tipi di documenti?
Groupdocs.Annotation per .NET supporta un'ampia gamma di formati di documenti tra cui PDF, Word, Excel e altri.
### Posso personalizzare l'aspetto delle annotazioni?
Sì, puoi personalizzare varie proprietà delle annotazioni come colore, opacità e dimensione in base alle tue esigenze.
### Groupdocs.Annotation per .NET offre funzionalità di collaborazione in tempo reale?
Sì, Groupdocs.Annotation per .NET fornisce funzionalità di collaborazione in tempo reale che consentono a più utenti di annotare documenti contemporaneamente.
### È disponibile supporto tecnico per i prodotti Groupdocs?
 Sì, il supporto tecnico per i prodotti Groupdocs è disponibile tramite il forum e il supporto[Qui](https://forum.groupdocs.com/c/annotation/10).
### Posso provare Groupdocs.Annotation per .NET prima dell'acquisto?
Sì, puoi usufruire di una prova gratuita di Groupdocs.Annotation for .NET per esplorarne le funzionalità prima di effettuare un acquisto[Qui](https://purchase.groupdocs.com/temporary-license/).