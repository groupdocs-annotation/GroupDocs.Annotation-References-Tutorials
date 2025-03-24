---
title: Aggiungi annotazione punto al documento
linktitle: Aggiungi annotazione punto al documento
second_title: API GroupDocs.Annotation .NET
description: Scopri come aggiungere annotazioni puntuali ai PDF utilizzando GroupDocs.Annotation per .NET. Guida passo passo per un'integrazione perfetta.
weight: 17
url: /it/net/unlocking-annotation-power/add-point-annotation/
---

# Aggiungi annotazione punto al documento

## introduzione
GroupDocs.Annotation per .NET è un potente strumento che consente agli sviluppatori di aggiungere vari tipi di annotazioni ai documenti a livello di codice. In questo tutorial ci concentreremo sull'aggiunta di un'annotazione punto a un documento utilizzando C#.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
1. Conoscenza base del linguaggio di programmazione C#.
2. Visual Studio installato nel sistema.
3.  GroupDocs.Annotation per la libreria .NET installata. Puoi scaricarlo da[Qui](https://releases.groupdocs.com/annotation/net/).

## Importazione degli spazi dei nomi necessari
Per iniziare, devi importare gli spazi dei nomi richiesti nel tuo progetto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Passaggio 1: definire il percorso di output
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
In questo passaggio, definiamo il percorso di output in cui verrà salvato il documento annotato.
## Passaggio 2: inizializza Annotatore
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Qui inizializziamo il file`Annotator` oggetto con il documento di input ("input.pdf").
## Passaggio 3: creazione dell'annotazione del punto
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
 In questo passaggio creiamo un file`PointAnnotation` oggetto e specificarne le proprietà quali posizione, messaggio, numero di pagina e risposte.
## Passaggio 4: aggiungi annotazione
```csharp
annotator.Add(point);
```
Qui aggiungiamo l'annotazione del punto creato al documento.
## Passaggio 5: salva il documento
```csharp
annotator.Save(outputPath);
```
Infine, salviamo il documento annotato nel percorso di output specificato.

## Conclusione
In questo tutorial abbiamo imparato come aggiungere un'annotazione punto a un documento utilizzando GroupDocs.Annotation per .NET. Con questa potente libreria puoi migliorare le tue applicazioni di gestione dei documenti incorporando funzionalità di annotazione.
## Domande frequenti
### GroupDocs.Annotation per .NET è compatibile con tutti i formati di documenti?
Sì, GroupDocs.Annotation per .NET supporta un'ampia gamma di formati di documenti tra cui PDF, Microsoft Word, Excel, PowerPoint e altri.
### Posso personalizzare l'aspetto delle annotazioni?
Assolutamente! GroupDocs.Annotation per .NET fornisce ampie opzioni per personalizzare l'aspetto delle annotazioni in base alle esigenze della tua applicazione.
### È disponibile una prova gratuita per GroupDocs.Annotation per .NET?
 Sì, puoi usufruire di una prova gratuita da[Qui](https://releases.groupdocs.com/).
### Come posso ottenere supporto per eventuali problemi o domande relative a GroupDocs.Annotation per .NET?
 Puoi ottenere supporto dal forum GroupDocs.Annotation[Qui](https://forum.groupdocs.com/c/annotation/10).
### Posso ottenere una licenza temporanea a scopo di test?
 Sì, puoi ottenere una licenza temporanea da[Qui](https://purchase.groupdocs.com/temporary-license/).