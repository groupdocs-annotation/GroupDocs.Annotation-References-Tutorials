---
title: Carica documento dal disco locale
linktitle: Carica documento dal disco locale
second_title: API GroupDocs.Annotation .NET
description: Sfrutta tutta la potenza dell'annotazione dei documenti con GroupDocs.Annotation per .NET. Integra perfettamente le funzionalità di annotazione nelle tue applicazioni .NET.
type: docs
weight: 13
url: /it/net/document-loading-essentials/load-document-from-local-disk/
---
## introduzione
Sfruttare il potenziale dell'annotazione dei documenti non è mai stato così facile con GroupDocs.Annotation per .NET. Questo potente strumento consente agli sviluppatori di integrare perfettamente funzionalità di annotazione robuste nelle loro applicazioni .NET. In questa guida completa, ti guideremo attraverso il processo di utilizzo di GroupDocs.Annotation per .NET per annotare i documenti passo dopo passo. Che tu sia uno sviluppatore esperto o che tu abbia appena iniziato, questo tutorial ti fornirà le conoscenze per migliorare la collaborazione sui documenti e semplificare il tuo flusso di lavoro.
## Prerequisiti
Prima di approfondire l'annotazione dei documenti con GroupDocs.Annotation per .NET, assicurati di disporre dei seguenti prerequisiti:
1. Conoscenza di base di C#: la familiarità con i fondamenti del linguaggio di programmazione C# è essenziale.
2. Installazione di GroupDocs.Annotation per .NET: scaricare e installare GroupDocs.Annotation per .NET da[Qui](https://releases.groupdocs.com/annotation/net/).
3. Ambiente di sviluppo: configura un ambiente di sviluppo con Visual Studio o qualsiasi IDE compatibile.

## Importa spazi dei nomi
Per iniziare ad annotare i documenti con GroupDocs.Annotation per .NET, importa gli spazi dei nomi necessari nel tuo progetto:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Passaggio 1: caricare il documento dal disco locale
Innanzitutto, devi caricare il documento dal tuo disco locale. Utilizza il seguente snippet di codice:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Passaggio 2: definire l'area di annotazione
Successivamente, definire l'area di annotazione. In questo esempio creeremo un'AreaAnnotation:
```csharp
    AreaAnnotation area = new AreaAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
    };
    annotator.Add(area);
```
## Passaggio 3: salva il documento con annotazioni
Dopo aver annotato il documento, salvalo con le annotazioni:
```csharp
    annotator.Save(outputPath);
}
```
## Passaggio 4: Visualizza il messaggio di successo
Infine, visualizza un messaggio di successo con il percorso di output:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione
In conclusione, GroupDocs.Annotation per .NET fornisce una soluzione solida per integrare le funzionalità di annotazione dei documenti nelle applicazioni .NET. Seguendo questa guida passo passo, puoi annotare facilmente i documenti e migliorare la collaborazione nei tuoi progetti.
## Domande frequenti
### Posso provare GroupDocs.Annotation per .NET prima dell'acquisto?
 Sì, puoi scaricare una versione di prova gratuita da[Qui](https://releases.groupdocs.com/).
### Dove posso trovare la documentazione per GroupDocs.Annotation per .NET?
 È possibile accedere alla documentazione[Qui](https://reference.groupdocs.com/annotation/net/).
### Come posso ottenere una licenza temporanea per GroupDocs.Annotation per .NET?
 È possibile ottenere una licenza temporanea da[Qui](https://purchase.groupdocs.com/temporary-license/).
### È disponibile il supporto per GroupDocs.Annotation per .NET?
 Sì, puoi trovare supporto sul forum GroupDocs[Qui](https://forum.groupdocs.com/c/annotation/10).
### Dove posso acquistare GroupDocs.Annotation per .NET?
 È possibile acquistare GroupDocs.Annotation per .NET[Qui](https://purchase.groupdocs.com/buy).