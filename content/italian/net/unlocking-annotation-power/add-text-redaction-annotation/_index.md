---
title: Aggiungi annotazione di redazione testo al documento
linktitle: Aggiungi annotazione di redazione testo al documento
second_title: API GroupDocs.Annotation .NET
description: Scopri come aggiungere annotazioni di redazione del testo ai documenti PDF utilizzando GroupDocs.Annotation per .NET. Proteggi le informazioni sensibili senza sforzo.
type: docs
weight: 23
url: /it/net/unlocking-annotation-power/add-text-redaction-annotation/
---
## introduzione
L'aggiunta di un'annotazione di oscuramento del testo a un documento può essere un passaggio cruciale nella gestione sicura delle informazioni sensibili. GroupDocs.Annotation per .NET fornisce una soluzione solida per raggiungere questo obiettivo senza problemi. In questo tutorial ti guideremo passo dopo passo attraverso il processo di aggiunta di un'annotazione di redazione del testo al tuo documento.
## Prerequisiti
Prima di iniziare, assicurati di disporre dei seguenti prerequisiti:
1.  GroupDocs.Annotation per .NET: assicurati di aver installato la libreria GroupDocs.Annotation per .NET. Puoi scaricarlo da[sito web](https://releases.groupdocs.com/annotation/net/).
2. Ambiente di sviluppo: configura un ambiente di sviluppo con un IDE compatibile con .NET come Visual Studio.

## Importazione di spazi dei nomi
Innanzitutto, importiamo gli spazi dei nomi necessari nel nostro progetto:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Passaggio 1: definire il percorso di output
Definisci il percorso di output in cui desideri salvare il documento annotato. Assicurati che sia accessibile e scrivibile.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Passaggio 2: inizializza Annotatore
 Inizializza l'annotatore con il percorso del documento di input. Sostituire`"input.pdf"` con il percorso del documento.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Il codice di annotazione andrà qui
}
```
## Passaggio 3: creare un'annotazione di redazione del testo
 Creare un`TextRedactionAnnotation`oggetto con le proprietà richieste come`PageNumber`, `FontColor` , E`Points`. Personalizza l'annotazione secondo le tue esigenze.
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## Passaggio 4: aggiungi annotazione e salva
Aggiungi l'annotazione creata al documento utilizzando l'annotatore e salva il documento annotato nel percorso di output specificato.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Passaggio 5: controllare l'output
Infine, conferma che il documento è stato salvato correttamente nel percorso di output specificato.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione
In questo tutorial, abbiamo esaminato il processo di aggiunta di un'annotazione di redazione del testo a un documento utilizzando GroupDocs.Annotation per .NET. Con questi passaggi ora puoi gestire in modo sicuro le informazioni sensibili all'interno dei tuoi documenti.
## Domande frequenti
### Posso personalizzare l'aspetto dell'annotazione di redazione del testo?
Sì, puoi personalizzare varie proprietà come il colore del carattere, il colore di riempimento e l'opacità in base alle tue esigenze.
### È disponibile una versione di prova prima dell'acquisto?
 Sì, puoi accedere a una versione di prova gratuita da[sito web](https://releases.groupdocs.com/).
### Come posso ottenere supporto in caso di problemi?
 Puoi ottenere supporto dal forum della community GroupDocs.Annotation[Qui](https://forum.groupdocs.com/c/annotation/10).
### Ho bisogno di una licenza temporanea a scopo di test?
 Sì, puoi ottenere una licenza temporanea da[pagina di acquisto](https://purchase.groupdocs.com/temporary-license/)per i test.
### Posso aggiungere più annotazioni a un singolo documento?
Assolutamente, GroupDocs.Annotation ti consente di aggiungere vari tipi di annotazioni e più istanze a un singolo documento.