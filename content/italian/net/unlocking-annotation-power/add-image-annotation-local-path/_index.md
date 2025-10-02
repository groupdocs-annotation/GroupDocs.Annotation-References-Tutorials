---
"description": "Scopri come aggiungere annotazioni alle immagini dei documenti utilizzando GroupDocs.Annotation per .NET. Migliora le funzionalità di elaborazione dei documenti con facilità."
"linktitle": "Aggiungi annotazione immagine al documento (percorso locale)"
"second_title": "API .NET di GroupDocs.Annotation"
"title": "Aggiungi annotazione immagine al documento (percorso locale)"
"url": "/it/net/unlocking-annotation-power/add-image-annotation-local-path/"
type: docs
"weight": 14
---

# Aggiungi annotazione immagine al documento (percorso locale)

## Introduzione
GroupDocs.Annotation per .NET è una potente libreria che consente agli sviluppatori di aggiungere vari tipi di annotazioni ai documenti tramite codice. In questo tutorial, impareremo come aggiungere annotazioni di immagini a un documento utilizzando un percorso locale.
## Prerequisiti
Prima di iniziare, assicurati di avere i seguenti prerequisiti:
1. Conoscenza di base del linguaggio di programmazione C#.
2. Visual Studio installato sul tuo sistema.
3. GroupDocs.Annotation per la libreria .NET installata o tutorialsd nel tuo progetto.
4. Un documento di input (ad esempio, PDF) e un file immagine per l'annotazione.
## Importa spazi dei nomi
Per prima cosa, devi importare gli spazi dei nomi necessari nel tuo file C#. Questi spazi dei nomi forniscono l'accesso alle classi e ai metodi necessari per lavorare con GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Passaggio 1: definire il percorso di output
Definire il percorso di output in cui verrà salvato il documento annotato.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Passaggio 2: inizializzare l'annotatore
Inizializzare l'annotatore fornendo il percorso al documento di input.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Il codice di annotazione va qui
}
```
## Passaggio 3: creare annotazioni sull'immagine
Crea un'istanza di `ImageAnnotation` classe e specificarne le proprietà quali posizione, opacità, numero di pagina e percorso dell'immagine.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## Passaggio 4: aggiungere annotazioni
Aggiungere l'annotazione dell'immagine creata al documento utilizzando `Add` metodo dell'annotatore.
```csharp
annotator.Add(image);
```
## Passaggio 5: Salva il documento
Salvare il documento annotato nel percorso di output.
```csharp
annotator.Save(outputPath);
```
## Passaggio 6: visualizzare il percorso di output
Visualizza un messaggio che indica il salvataggio riuscito del documento e la posizione del file di output.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione
In questo tutorial abbiamo imparato come aggiungere annotazioni alle immagini di un documento utilizzando GroupDocs.Annotation per .NET. Seguendo questi semplici passaggi, è possibile migliorare le capacità di elaborazione dei documenti con potenti funzionalità di annotazione.
## Domande frequenti
### Posso annotare documenti diversi dal PDF?
Sì, GroupDocs.Annotation supporta vari formati di documenti, tra cui Word, Excel, PowerPoint e altri.
### GroupDocs.Annotation è compatibile con .NET Core?
Sì, GroupDocs.Annotation è compatibile sia con .NET Framework che con .NET Core.
### Posso personalizzare l'aspetto delle annotazioni?
Certamente, puoi personalizzare l'aspetto, le dimensioni, il colore e altre proprietà delle annotazioni in base alle tue esigenze.
### GroupDocs.Annotation fornisce supporto per l'annotazione collaborativa?
Sì, GroupDocs.Annotation offre funzionalità di annotazione collaborativa che consentono a più utenti di annotare i documenti contemporaneamente.
### Dove posso trovare ulteriore aiuto o supporto?
Puoi visitare il forum GroupDocs.Annotation per ricevere assistenza e supporto dalla community.