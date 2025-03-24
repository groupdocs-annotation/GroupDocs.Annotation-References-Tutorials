---
title: Aggiungi annotazione polilinea al documento
linktitle: Aggiungi annotazione polilinea al documento
second_title: API GroupDocs.Annotation .NET
description: Scopri come aggiungere annotazioni di polilinee ai documenti utilizzando GroupDocs.Annotation per .NET. Migliora facilmente la collaborazione e i processi di revisione dei documenti.
weight: 18
url: /it/net/unlocking-annotation-power/add-polyline-annotation/
---
## introduzione
GroupDocs.Annotation per .NET è un potente strumento che consente agli sviluppatori di annotare a livello di codice documenti PDF e Microsoft Office. Tra le sue funzionalità c'è la possibilità di aggiungere annotazioni di polilinee ai documenti, migliorando la collaborazione e i processi di revisione dei documenti.
## Prerequisiti
Prima di procedere con questo tutorial, assicurati di avere quanto segue:
- Visual Studio installato nel sistema.
- Conoscenza base del linguaggio di programmazione C#.
-  GroupDocs.Annotation per la libreria .NET installata. Puoi scaricarlo da[Qui](https://releases.groupdocs.com/annotation/net/).

## Importa spazi dei nomi
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Passaggio 1: definire il percorso di output
Innanzitutto, definisci il percorso di output in cui verrà salvato il documento annotato.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Passaggio 2: inizializza Annotatore
Inizializza l'annotatore fornendo il nome del documento di input.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Passaggio 3: creare un oggetto di annotazione polilinea
Crea un oggetto di annotazione polilinea e imposta le sue proprietà come posizione, messaggio, opacità, colore penna, stile penna e larghezza penna.
```csharp
PolylineAnnotation polyline = new PolylineAnnotation
{
    Box = new Rectangle(250, 35, 102, 12),
    CreatedOn = DateTime.Now,
    Message = "This is polyline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
    SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.698685
4460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
};
```
## Passaggio 4: aggiungi annotazione polilinea
Aggiungi l'annotazione della polilinea al documento utilizzando l'oggetto annotatore.
```csharp
annotator.Add(polyline);
```
## Passaggio 5: salva il documento
Salva il documento annotato nel percorso di output specificato.
```csharp
annotator.Save(outputPath);
```
## Passaggio 6: Visualizza il messaggio di successo
Visualizza un messaggio che conferma il corretto salvataggio del documento.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusione
In questo tutorial, abbiamo imparato come aggiungere un'annotazione di polilinea a un documento utilizzando GroupDocs.Annotation per .NET. Questa funzionalità migliora i processi di collaborazione e revisione dei documenti, rendendo più semplice per gli utenti comunicare feedback e suggerimenti in modo efficace.
## Domande frequenti
### GroupDocs.Annotation per .NET è compatibile con tutti i formati di documenti?
GroupDocs.Annotation per .NET supporta i formati di documenti più diffusi come PDF e formati Microsoft Office, inclusi Word, Excel e PowerPoint.
### Posso personalizzare l'aspetto delle annotazioni?
Sì, puoi personalizzare varie proprietà delle annotazioni come colore, opacità, stile e larghezza in base alle tue esigenze.
### GroupDocs.Annotation per .NET offre una prova gratuita?
 Sì, puoi usufruire di una prova gratuita di GroupDocs.Annotation per .NET visitando[questo link](https://releases.groupdocs.com/).
### Dove posso trovare la documentazione per GroupDocs.Annotation per .NET?
 È possibile trovare la documentazione per GroupDocs.Annotation per .NET[Qui](https://tutorials.groupdocs.com/annotation/net/).
### Come posso ottenere supporto per eventuali problemi o domande relative a GroupDocs.Annotation per .NET?
 Puoi ottenere supporto visitando il forum GroupDocs.Annotation[Qui](https://forum.groupdocs.com/c/annotation/10).