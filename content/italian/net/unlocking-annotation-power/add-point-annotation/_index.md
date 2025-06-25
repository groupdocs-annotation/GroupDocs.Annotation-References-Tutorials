---
"description": "Scopri come aggiungere annotazioni puntuali ai PDF utilizzando GroupDocs.Annotation per .NET. Guida passo passo per un'integrazione perfetta."
"linktitle": "Aggiungi annotazione punto al documento"
"second_title": "API .NET di GroupDocs.Annotation"
"title": "Aggiungi annotazione punto al documento"
"url": "/it/net/unlocking-annotation-power/add-point-annotation/"
"weight": 17
---

# Aggiungi annotazione punto al documento

## Introduzione
GroupDocs.Annotation per .NET è un potente strumento che consente agli sviluppatori di aggiungere vari tipi di annotazioni ai documenti tramite codice. In questo tutorial, ci concentreremo sull'aggiunta di un'annotazione puntuale a un documento utilizzando C#.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
1. Conoscenza di base del linguaggio di programmazione C#.
2. Visual Studio installato sul tuo sistema.
3. Libreria GroupDocs.Annotation per .NET installata. Puoi scaricarla da [Qui](https://releases.groupdocs.com/annotation/net/).

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
In questo passaggio definiamo il percorso di output in cui verrà salvato il documento annotato.
## Passaggio 2: inizializzare l'annotatore
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
Qui, inizializziamo il `Annotator` oggetto con il documento di input ("input.pdf").
## Passaggio 3: creare annotazioni di punti
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
In questo passaggio creiamo un `PointAnnotation` oggetto e specificarne le proprietà quali posizione, messaggio, numero di pagina e risposte.
## Passaggio 4: aggiungere annotazioni
```csharp
annotator.Add(point);
```
Qui aggiungiamo l'annotazione del punto creato al documento.
## Passaggio 5: Salva il documento
```csharp
annotator.Save(outputPath);
```
Infine, salviamo il documento annotato nel percorso di output specificato.

## Conclusione
In questo tutorial abbiamo imparato come aggiungere un'annotazione puntuale a un documento utilizzando GroupDocs.Annotation per .NET. Con questa potente libreria, puoi migliorare le tue applicazioni di gestione documentale integrando funzionalità di annotazione.
## Domande frequenti
### GroupDocs.Annotation per .NET è compatibile con tutti i formati di documento?
Sì, GroupDocs.Annotation per .NET supporta un'ampia gamma di formati di documenti, tra cui PDF, Microsoft Word, Excel, PowerPoint e altri.
### Posso personalizzare l'aspetto delle annotazioni?
Assolutamente sì! GroupDocs.Annotation per .NET offre ampie opzioni per personalizzare l'aspetto delle annotazioni in base alle esigenze della tua applicazione.
### È disponibile una versione di prova gratuita di GroupDocs.Annotation per .NET?
Sì, puoi usufruire di una prova gratuita da [Qui](https://releases.groupdocs.com/).
### Come posso ottenere supporto per eventuali problemi o domande relativi a GroupDocs.Annotation per .NET?
Puoi ottenere supporto dal forum GroupDocs.Annotation [Qui](https://forum.groupdocs.com/c/annotation/10).
### Posso ottenere una licenza temporanea per scopi di prova?
Sì, puoi ottenere una licenza temporanea da [Qui](https://purchase.groupdocs.com/temporary-license/).