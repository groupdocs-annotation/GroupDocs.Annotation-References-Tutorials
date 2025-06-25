---
"description": "Scopri come annotare i documenti PDF tramite codice utilizzando GroupDocs.Annotation per .NET. Tutorial passo passo con esempi di codice."
"linktitle": "Carica documento da URL"
"second_title": "API .NET di GroupDocs.Annotation"
"title": "Carica documento da URL"
"url": "/it/net/document-loading-essentials/load-document-from-url/"
"weight": 15
---

# Carica documento da URL

## Introduzione
GroupDocs.Annotation per .NET è una libreria ricca di funzionalità che consente agli sviluppatori di aggiungere funzionalità di annotazione alle proprie applicazioni .NET senza sforzo. Con GroupDocs.Annotation, è possibile annotare i documenti PDF a livello di codice, consentendo agli utenti di evidenziare il testo, aggiungere commenti, disegnare forme e altro ancora. Questo tutorial vi guiderà attraverso i passaggi per caricare un documento da un URL, aggiungere annotazioni e salvare il documento annotato utilizzando GroupDocs.Annotation per .NET.
## Prerequisiti
Prima di iniziare, assicurati di disporre dei seguenti prerequisiti:
1. Visual Studio: assicurati che Visual Studio sia installato sul tuo computer di sviluppo.
2. GroupDocs.Annotation per .NET: Scarica e installa GroupDocs.Annotation per .NET da [sito web](https://releases.groupdocs.com/annotation/net/).
3. Conoscenza di base di C#: familiarizzare con il linguaggio di programmazione C#.
4. Connessione Internet: per accedere alle risorse esterne e scaricare i file di esempio è necessaria una connessione Internet.

## Importa spazi dei nomi
Per prima cosa, importiamo gli spazi dei nomi necessari nel tuo progetto C#:
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## Passaggio 1: carica il documento dall'URL
Per annotare un documento PDF da un URL, segui questi passaggi:
### Passaggio 1.1: definire il percorso di output
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### Passaggio 1.2: specificare l'URL
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### Passaggio 1.3: Carica documento
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // Aggiungi annotazioni qui
    annotator.Save(outputPath);
}
```
## Passaggio 2: aggiungere annotazioni
Ora aggiungiamo annotazioni al documento caricato. In questo esempio, aggiungeremo un'annotazione di area:
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## Passaggio 3: Salva il documento annotato
Infine, salva il documento annotato nel percorso di output specificato:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione
In questo tutorial abbiamo imparato come annotare i documenti PDF utilizzando GroupDocs.Annotation per .NET. Seguendo la guida passo passo, è possibile integrare perfettamente la funzionalità di annotazione nelle applicazioni .NET, consentendo agli utenti di collaborare efficacemente sui file PDF.

## Domande frequenti
### GroupDocs.Annotation per .NET è compatibile con tutti i framework .NET?
Sì, GroupDocs.Annotation per .NET è compatibile con vari framework .NET, tra cui .NET Framework, .NET Core e .NET Standard.
### Posso personalizzare l'aspetto delle annotazioni?
Assolutamente sì! GroupDocs.Annotation per .NET offre ampie opzioni di personalizzazione, consentendo di modificare l'aspetto e il comportamento delle annotazioni in base alle proprie esigenze.
### È disponibile una versione di prova gratuita di GroupDocs.Annotation per .NET?
Sì, puoi scaricare una versione di prova gratuita di GroupDocs.Annotation per .NET da [sito web](https://releases.groupdocs.com/).
### Come posso ottenere supporto tecnico per GroupDocs.Annotation per .NET?
Se riscontri problemi tecnici o hai domande su GroupDocs.Annotation per .NET, puoi richiedere assistenza a [forum di supporto](https://forum.groupdocs.com/c/annotation/10).
### Dove posso acquistare una licenza per GroupDocs.Annotation per .NET?
È possibile acquistare una licenza per GroupDocs.Annotation per .NET da [pagina di acquisto](https://purchase.groupdocs.com/buy).