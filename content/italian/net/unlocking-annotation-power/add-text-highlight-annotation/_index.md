---
title: Aggiungi annotazione di evidenziazione del testo al documento
linktitle: Aggiungi annotazione di evidenziazione del testo al documento
second_title: API GroupDocs.Annotation .NET
description: Scopri come aggiungere annotazioni di evidenziazione del testo ai documenti utilizzando GroupDocs.Annotation per .NET. Migliora la collaborazione e la produttività con questa soluzione completa.
weight: 22
url: /it/net/unlocking-annotation-power/add-text-highlight-annotation/
---

# Aggiungi annotazione di evidenziazione del testo al documento

## introduzione
Nell'ambito della gestione e della collaborazione dei documenti, GroupDocs.Annotation per .NET emerge come una soluzione solida, che consente agli sviluppatori di integrare perfettamente le annotazioni di evidenziazione del testo nelle loro applicazioni. Questa esercitazione funge da guida completa per aggiungere annotazioni di evidenziazione del testo ai documenti utilizzando GroupDocs.Annotation per .NET. Attraverso istruzioni passo passo e spiegazioni dettagliate, acquisirai competenza nello sfruttare le capacità di questa potente libreria.
## Prerequisiti
Prima di approfondire l'implementazione delle annotazioni di evidenziazione del testo, assicurati di disporre dei seguenti prerequisiti:
1. Configurazione dell'ambiente: disporre di un ambiente di sviluppo adatto configurato per lo sviluppo .NET.
2.  Installazione di GroupDocs.Annotation per .NET: scaricare e installare GroupDocs.Annotation per .NET dal sito fornito[Link per scaricare](https://releases.groupdocs.com/annotation/net/).
3. Familiarità con C#: Conoscenza di base del linguaggio di programmazione C#.
4. Documento da annotare: prepara un documento (ad esempio PDF) che intendi annotare.

## Importa spazi dei nomi
Per iniziare, importa gli spazi dei nomi necessari nel codice C# per utilizzare le funzionalità di GroupDocs.Annotation per .NET:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#Ora, suddividiamo il processo di aggiunta delle annotazioni di evidenziazione del testo in più passaggi:
## Passaggio 1: definire il percorso di output
Specificare il percorso di output in cui verrà salvato il documento annotato:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Passaggio 2: inizializza Annotatore
 Crea un'istanza di`Annotator` class, passando il nome del file del documento come parametro:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## Passaggio 3: crea l'annotazione di evidenziazione
 Istanziare a`HighlightAnnotation` oggetto e configurarne le proprietà:
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
Aggiungi l'annotazione di evidenziazione creata al documento:
```csharp
annotator.Add(highlight);
```
## Passaggio 5: salva il documento con annotazioni
Salva il documento annotato nel percorso di output specificato:
```csharp
annotator.Save(outputPath);
```

## Conclusione
In conclusione, GroupDocs.Annotation per .NET offre un approccio semplificato per incorporare annotazioni di evidenziazione del testo nei documenti. Seguendo i passaggi descritti in questo tutorial, gli sviluppatori possono migliorare facilmente la collaborazione sui documenti e la produttività all'interno delle loro applicazioni.
## Domande frequenti
### GroupDocs.Annotation per .NET è compatibile con tutti i formati di documenti?
GroupDocs.Annotation per .NET supporta vari formati di documenti, tra cui PDF, Word, Excel e altri. Fare riferimento alla documentazione per l'elenco completo.
### Le annotazioni possono essere personalizzate in base a requisiti specifici?
Sì, gli sviluppatori hanno il pieno controllo sulle proprietà e sull'aspetto delle annotazioni, consentendone la personalizzazione per soddisfare le diverse esigenze.
### È disponibile una prova gratuita per GroupDocs.Annotation per .NET?
 Sì, puoi esplorare le funzionalità di GroupDocs.Annotation per .NET accedendo alla prova gratuita dal sito fornito[collegamento](https://releases.groupdocs.com/).
### Come posso ottenere supporto per eventuali problemi o domande relative a GroupDocs.Annotation per .NET?
 Per supporto e assistenza, è possibile visitare il forum GroupDocs.Annotation[Qui](https://forum.groupdocs.com/c/annotation/10).
### Quali opzioni di licenza sono disponibili per GroupDocs.Annotation per .NET?
 GroupDocs.Annotation per .NET offre varie opzioni di licenza, comprese licenze temporanee a scopo di test e licenze commerciali per ambienti di produzione. Visita la pagina di acquisto[Qui](https://purchase.groupdocs.com/buy) per ulteriori dettagli.