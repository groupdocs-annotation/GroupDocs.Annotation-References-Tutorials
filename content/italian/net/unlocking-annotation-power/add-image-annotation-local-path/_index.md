---
title: Aggiungi annotazione immagine al documento (percorso locale)
linktitle: Aggiungi annotazione immagine al documento (percorso locale)
second_title: API GroupDocs.Annotation .NET
description: Scopri come aggiungere annotazioni di immagini ai documenti utilizzando GroupDocs.Annotation per .NET. Migliora facilmente le capacità di elaborazione dei documenti.
weight: 14
url: /it/net/unlocking-annotation-power/add-image-annotation-local-path/
---
## introduzione
GroupDocs.Annotation per .NET è una potente libreria che consente agli sviluppatori di aggiungere vari tipi di annotazioni ai documenti a livello di codice. In questo tutorial impareremo come aggiungere annotazioni immagine a un documento utilizzando un percorso locale.
## Prerequisiti
Prima di iniziare, assicurati di avere i seguenti prerequisiti:
1. Conoscenza base del linguaggio di programmazione C#.
2. Visual Studio installato nel sistema.
3. Libreria GroupDocs.Annotation per .NET installata o a cui si fa riferimento nel progetto.
4. Un documento di input (ad esempio PDF) e un file di immagine per l'annotazione.
## Importa spazi dei nomi
Innanzitutto, devi importare gli spazi dei nomi necessari nel file C#. Questi spazi dei nomi forniscono l'accesso alle classi e ai metodi richiesti per lavorare con GroupDocs.Annotation.
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
## Passaggio 2: inizializza Annotatore
Inizializza l'annotatore fornendo il percorso del documento di input.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // Il codice di annotazione va qui
}
```
## Passaggio 3: crea un'annotazione sull'immagine
 Crea un'istanza di`ImageAnnotation`classe e specificarne le proprietà come posizione, opacità, numero di pagina e percorso dell'immagine.
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
## Passaggio 4: aggiungi annotazione
 Aggiungi l'annotazione dell'immagine creata al documento utilizzando il file`Add` metodo dell'annotatore.
```csharp
annotator.Add(image);
```
## Passaggio 5: salva il documento
Salvare il documento annotato nel percorso di output.
```csharp
annotator.Save(outputPath);
```
## Passaggio 6: Visualizza il percorso di output
Visualizza un messaggio che indica il salvataggio riuscito del documento e la posizione del file di output.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione
In questo tutorial, abbiamo imparato come aggiungere annotazioni immagine a un documento utilizzando GroupDocs.Annotation per .NET. Seguendo questi semplici passaggi, puoi migliorare le tue capacità di elaborazione dei documenti con potenti funzionalità di annotazione.
## Domande frequenti
### Posso annotare documenti diversi dai PDF?
Sì, GroupDocs.Annotation supporta vari formati di documenti tra cui Word, Excel, PowerPoint e altri.
### GroupDocs.Annotation è compatibile con .NET Core?
Sì, GroupDocs.Annotation è compatibile sia con .NET Framework che con .NET Core.
### Posso personalizzare l'aspetto delle annotazioni?
Assolutamente, puoi personalizzare l'aspetto, la dimensione, il colore e altre proprietà delle annotazioni in base alle tue esigenze.
### GroupDocs.Annotation fornisce supporto per l'annotazione collaborativa?
Sì, GroupDocs.Annotation offre funzionalità di annotazione collaborativa che consentono a più utenti di annotare documenti contemporaneamente.
### Dove posso trovare ulteriore aiuto o supporto?
Puoi visitare il forum GroupDocs.Annotation per ricevere assistenza e supporto da parte della community.