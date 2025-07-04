---
"description": "Scopri come aggiungere annotazioni di redazione del testo ai documenti PDF utilizzando GroupDocs.Annotation per .NET. Proteggi le informazioni sensibili senza sforzo."
"linktitle": "Aggiungi annotazione di redazione del testo al documento"
"second_title": "API .NET di GroupDocs.Annotation"
"title": "Aggiungi annotazione di redazione del testo al documento"
"url": "/it/net/unlocking-annotation-power/add-text-redaction-annotation/"
"weight": 23
---

# Aggiungi annotazione di redazione del testo al documento

## Introduzione
Aggiungere un'annotazione di redazione del testo a un documento può essere un passaggio cruciale per la gestione sicura delle informazioni sensibili. GroupDocs.Annotation per .NET offre una soluzione affidabile per raggiungere questo obiettivo senza problemi. In questo tutorial, ti guideremo passo dopo passo attraverso il processo di aggiunta di un'annotazione di redazione del testo al tuo documento.
## Prerequisiti
Prima di iniziare, assicurati di avere i seguenti prerequisiti:
1. GroupDocs.Annotation per .NET: assicurati di aver installato la libreria GroupDocs.Annotation per .NET. Puoi scaricarla da [sito web](https://releases.groupdocs.com/annotation/net/).
2. Ambiente di sviluppo: configurare un ambiente di sviluppo con un IDE compatibile con .NET, come Visual Studio.

## Importazione di spazi dei nomi
Per prima cosa, importiamo gli spazi dei nomi necessari nel nostro progetto:
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
## Passaggio 2: inizializzare l'annotatore
Inizializza l'annotatore con il percorso del documento di input. Sostituisci `"input.pdf"` con il percorso al tuo documento.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Il codice di annotazione andrà qui
}
```
## Passaggio 3: creare un'annotazione di redazione del testo
Crea un `TextRedactionAnnotation` oggetto con le proprietà richieste come `PageNumber`, `FontColor`, E `Points`Personalizza l'annotazione in base alle tue esigenze.
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
Aggiungere l'annotazione creata al documento utilizzando l'annotatore e salvare il documento annotato nel percorso di output specificato.
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## Passaggio 5: verifica dell'output
Infine, verificare che il documento sia stato salvato correttamente nel percorso di output specificato.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione
In questo tutorial, abbiamo illustrato come aggiungere un'annotazione di redazione del testo a un documento utilizzando GroupDocs.Annotation per .NET. Con questi passaggi, ora puoi gestire in modo sicuro le informazioni sensibili all'interno dei tuoi documenti.
## Domande frequenti
### Posso personalizzare l'aspetto dell'annotazione di redazione del testo?
Sì, puoi personalizzare varie proprietà, come il colore del carattere, il colore di riempimento e l'opacità, in base alle tue esigenze.
### È disponibile una versione di prova prima dell'acquisto?
Sì, puoi accedere a una versione di prova gratuita da [sito web](https://releases.groupdocs.com/).
### Come posso ottenere assistenza se riscontro qualche problema?
Puoi ottenere supporto dal forum della community GroupDocs.Annotation [Qui](https://forum.groupdocs.com/c/annotation/10).
### Ho bisogno di una licenza temporanea per scopi di prova?
Sì, puoi ottenere una licenza temporanea dall' [pagina di acquisto](https://purchase.groupdocs.com/temporary-license/) per effettuare i test.
### Posso aggiungere più annotazioni a un singolo documento?
Certamente, GroupDocs.Annotation consente di aggiungere vari tipi di annotazioni e più istanze a un singolo documento.